**FABRICOLOR  |  DOCUMENTACIÓN MAESTRA DEL PROYECTO**

**DOCUMENTO 05 / 05**

**FabriColor**

**Especificación técnica y guía maestra para IA / desarrollo**

Arquitectura propuesta, modelo de datos, APIs, seguridad, entornos, estrategia de implementación y reglas para continuar el proyecto con ChatGPT o Claude.

| **Campo** | **Definición** |
| --- | --- |
| Proyecto | FabriColor — web comercial + sistema administrativo conectado |
| Ubicación del negocio | Ciudad Bolívar, Venezuela |
| Naturaleza de este documento | Blueprint técnico propuesto; las tecnologías concretas requieren aprobación antes de considerarse definitivas |
| Dependencias documentales | Documentos 01, 02, 03 y 04 + Catálogo Maestro FabriColor 2026 |

| **Regla de autoridad. **Cuando exista conflicto, deben prevalecer los datos fuente y la decisión aprobada más reciente. Este documento no autoriza a una IA a inventar requisitos ausentes. |
| --- |

# 1. Propósito

Este documento traduce la visión, requisitos funcionales, reglas de catálogo e interfaz de FabriColor a una arquitectura técnica implementable. Su objetivo es que un equipo de desarrollo o una IA pueda construir el sistema de forma consistente, modular y trazable.

Definir límites claros entre web pública, back office, API, datos y servicios.

Proponer un modelo de datos coherente con ventas, inventario, compras, clientes y caja.

Definir contratos de integración y eventos de negocio.

Establecer requisitos de seguridad, auditoría, respaldo y operación.

Definir una estrategia de desarrollo incremental y verificable.

Proporcionar instrucciones maestras para ChatGPT/Claude y evitar deriva de alcance.

# 2. Estado de las decisiones técnicas

| **Categoría** | **Estado** |
| --- | --- |
| Arquitectura modular web + API + base de datos | Propuesta recomendada. |
| Base de datos relacional | Propuesta recomendada por la naturaleza transaccional del sistema. |
| Stack frontend/backend concreto | Pendiente de aprobación. |
| Proveedor cloud/hosting | Pendiente. |
| Facturación fiscal/electrónica venezolana | Pendiente de requisitos legales y proveedor/integración. |
| Pasarela o integración de pagos | Pendiente. |
| Portal B2B / e-commerce | Fuera de V1 salvo aprobación. |

| **Importante. **Las tecnologías nombradas más adelante son opciones recomendadas, no decisiones históricamente aprobadas. Una IA debe distinguir «arquitectura requerida» de «tecnología sugerida». |
| --- |

# 3. Arquitectura lógica recomendada

WEB PÚBLICA ───────┐
                     ├── API / CAPA DE SERVICIOS ── BASE DE DATOS
BACK OFFICE / POS ───┘              │
                                    ├── Archivos / imágenes
                                    ├── Auditoría
                                    ├── Notificaciones
                                    └── Integraciones futuras

La web pública y el sistema administrativo deben compartir una capa de servicios y datos, pero con permisos, endpoints y exposición diferentes. La web nunca debe consultar directamente tablas internas sensibles.

Frontend público: catálogo, búsqueda, contenido y contacto.

Frontend administrativo: POS, inventario, compras, clientes, caja, reportes y configuración.

API: aplica reglas de negocio y autorización.

Base de datos: fuente transaccional principal.

Almacenamiento de objetos: imágenes, PDFs y documentos generados.

Procesos asíncronos: importaciones, notificaciones, sincronización y tareas pesadas cuando sean necesarias.

# 4. Estrategia de aplicación

Para una primera versión, se recomienda evitar microservicios innecesarios. Un monolito modular bien estructurado puede reducir complejidad y coste, manteniendo dominios separados internamente. Los módulos podrán extraerse posteriormente si la escala lo justifica.

| **Dominio** | **Responsabilidad** |
| --- | --- |
| Identity | Usuarios, roles, permisos, sesiones. |
| Catalog | Productos, marcas, familias, presentaciones, datos web. |
| Pricing | Costes, tarifas, precios, impuestos y reglas comerciales. |
| Inventory | Stock, reservas, movimientos, ubicaciones y conteos. |
| Sales | Presupuestos, pedidos, ventas, devoluciones y líneas. |
| CRM | Clientes, condiciones comerciales y cuenta corriente. |
| Purchasing | Proveedores, pedidos, recepciones y costes. |
| Cash | Cajas, aperturas, cobros, egresos y cierres. |
| Finance | Cuentas por cobrar/pagar y vencimientos operativos. |
| Web Publishing | Proyección de catálogo público. |
| Audit | Registro inmutable/lógico de acciones sensibles. |
| Laboratory | Futuras fórmulas y preparaciones de color. |

# 5. Stack tecnológico: opciones recomendadas

La selección final debe hacerse según equipo, presupuesto y hosting. Dos rutas razonables:

| **Capa** | **Opción A** | **Opción B** |
| --- | --- | --- |
| Frontend web/back office | Next.js + TypeScript | React + TypeScript con framework de aplicación equivalente |
| Backend | NestJS / TypeScript | FastAPI / Python |
| Base de datos | PostgreSQL | PostgreSQL |
| ORM | Prisma/TypeORM según stack | SQLAlchemy |
| Archivos | Object storage compatible S3 | Servicio equivalente del proveedor cloud |
| Cache/colas futuras | Redis cuando exista necesidad real | Redis cuando exista necesidad real |
| Contenedores | Docker | Docker |

No se requiere Redis, colas ni arquitectura distribuida desde el primer día si la carga no lo justifica. PostgreSQL se recomienda por consistencia transaccional, relaciones, reportes y capacidad de auditoría.

# 6. Modelo de datos: principios

Usar identificadores internos estables además del SKU visible.

SKU único a nivel de catálogo activo.

Evitar borrar físicamente entidades con historial; utilizar estados.

Separar datos maestros de documentos transaccionales.

Guardar snapshots de precio/coste/descripción cuando una operación histórica lo requiera.

Toda cantidad debe tener unidad y contexto.

Toda cantidad monetaria debe almacenar moneda.

Usar precisión decimal; no usar float binario para dinero.

Fechas de negocio y timestamps de auditoría deben distinguirse cuando sea necesario.

# 7. Entidades principales

| **Entidad** | **Campos/relaciones esenciales** |
| --- | --- |
| Product | id, sku, brand_id, family_id, source_description, commercial_name, presentation, active. |
| Brand | id, name, active. |
| ProductFamily | id, name, parent_id opcional. |
| Supplier | id, datos comerciales, active. |
| SupplierProduct | supplier_id, product_id, supplier_code opcional, pack_size, min_purchase, lead/availability data. |
| CostHistory | product_id, supplier_id, amount, currency, effective_at, source. |
| PriceList | id, name, currency, active. |
| ProductPrice | product_id, price_list_id, amount, effective_at. |
| Customer | id, tipo, datos contacto, price_list_id, credit_limit, credit_days, active. |
| InventoryLocation | id, nombre, sucursal/almacén. |
| InventoryBalance | product_id, location_id, physical_qty, reserved_qty. |
| InventoryMovement | product_id, location_id, type, qty, document_type/id, user_id, timestamp. |
| SalesDocument | id, type, status, customer_id, totals, currency, timestamps. |
| SalesLine | document_id, product_id, qty, unit_price_snapshot, unit_cost_snapshot, discount, tax_snapshot. |
| Payment | id, customer/document, method, amount, currency, timestamp. |
| PurchaseOrder | id, supplier_id, status, expected_date, currency. |
| PurchaseLine | purchase_order_id, product_id, ordered_qty, unit_cost. |
| GoodsReceipt | id, purchase_order_id, received_at, user_id. |
| GoodsReceiptLine | receipt_id, purchase_line_id, received_qty, received_cost. |
| CashSession | id, cash_register, user, opened_at, opening_amount, closed_at. |
| CashMovement | session_id, type, payment_method, amount, source_document. |
| User / Role / Permission | Autenticación y autorización granular. |
| AuditLog | actor, action, entity, entity_id, before/after, timestamp, reason. |

# 8. Relaciones críticas

Product 1:N CostHistory.

Product N:M Supplier mediante SupplierProduct.

Product N:M PriceList mediante ProductPrice.

Customer N:1 PriceList como tarifa predeterminada.

SalesDocument 1:N SalesLine.

PurchaseOrder 1:N PurchaseLine.

PurchaseOrder 1:N GoodsReceipt.

GoodsReceipt 1:N GoodsReceiptLine.

Product + Location 1:1 InventoryBalance lógico.

Cada InventoryMovement referencia, cuando exista, el documento que lo originó.

Payment puede aplicarse a una venta/documento o a una cuenta corriente según diseño final.

# 9. Inventario: consistencia técnica

| **Regla crítica. **El saldo de inventario debe poder reconciliarse con el historial de movimientos. No modificar cantidades sin generar un movimiento trazable. |
| --- |

Una compra confirmada puede aumentar 'en tránsito', pero no stock físico.

Una recepción confirmada genera entrada física.

Una venta/entrega confirmada genera salida según el punto exacto definido en el flujo.

Una devolución decide explícitamente destino: vendible, dañado u otro.

Un ajuste requiere motivo y permisos.

Las operaciones que afecten documento + inventario deben ejecutarse transaccionalmente.

Si una transacción falla, no debe quedar la venta confirmada sin su movimiento de inventario correspondiente, ni viceversa.

# 10. Dinero, moneda e impuestos

Usar tipos DECIMAL/NUMERIC para importes.

Guardar currency_code en documentos y costes/precios cuando corresponda.

No asumir una única moneda futura aunque las listas actuales estén expresadas en USD.

Guardar subtotal, descuento, impuesto y total en documentos confirmados.

Guardar la regla/tasa fiscal aplicada como snapshot suficiente para reconstruir el documento.

La configuración fiscal real queda pendiente y no debe codificarse por suposición.

# 11. Motor de precios

Identificar cliente y tarifa asignada.

Obtener precio vigente del SKU para la tarifa.

Aplicar reglas de descuento autorizadas.

Calcular impuestos configurados.

Mostrar total.

Al confirmar, guardar snapshots de precio, descuento, impuesto y coste histórico.

El motor debe permitir que la política comercial evolucione sin modificar el modelo de producto.

# 12. API: principios

Versionar la API desde el inicio, por ejemplo /api/v1/.

Separar endpoints públicos y administrativos.

Aplicar autorización en backend, no solo ocultar botones en frontend.

Validar payloads con esquemas estrictos.

Paginar listados grandes.

Filtrar y ordenar desde servidor cuando sea necesario.

Usar idempotencia para operaciones sensibles cuando pueda haber reintentos.

No devolver campos internos innecesarios a la web pública.

# 13. API: recursos orientativos

| **Área** | **Endpoints conceptuales** |
| --- | --- |
| Public catalog | GET /public/products, GET /public/products/{slug│sku}, GET /public/brands, GET /public/categories. |
| Products | GET/POST/PATCH /admin/products; historial y publicación. |
| Inventory | GET balances; POST adjustments; GET movements; inventory counts. |
| Sales | POST quotes/sales; add lines; confirm; cancel; return. |
| Customers | CRUD, credit status, statements, payments. |
| Purchasing | purchase-orders, receipts, pending quantities. |
| Cash | open session, movements, close session. |
| Reports | consultas agregadas con permisos. |
| Audit | consulta de auditoría para usuarios autorizados. |

Los nombres exactos de rutas no son contrato definitivo; expresan separación funcional y responsabilidades.

# 14. Publicación web

La API pública debe exponer una proyección segura del producto, no el registro administrativo completo.

| **Puede exponerse** | **No debe exponerse automáticamente** |
| --- | --- |
| SKU público, nombre, marca, categoría, presentación. | Coste proveedor o coste real. |
| Descripción pública e imágenes. | Margen. |
| Precio público cuando Mostrar precio = Sí. | Notas internas. |
| Estado público de disponibilidad. | Cantidad exacta de stock salvo decisión explícita. |
| Atributos aprobados. | Proveedor/condiciones privadas. |

Se recomienda generar slugs web independientes del SKU, conservando el SKU visible para búsquedas profesionales.

# 15. Búsqueda

La primera versión puede utilizar búsqueda de PostgreSQL y campos normalizados antes de incorporar un motor externo.

Índice por SKU.

Índices por marca/familia.

Búsqueda textual sobre nombre/descripción/palabras clave.

Normalización de mayúsculas, espacios y caracteres cuando sea útil.

Soporte de términos como P1200, 1Kg, Gal, perla blanca y códigos exactos.

Registrar búsquedas sin resultados en la web para mejorar catálogo/contenido.

Un motor como Elasticsearch/OpenSearch/Meilisearch solo debe añadirse si el volumen o calidad de búsqueda lo justifica.

# 16. Importación del catálogo maestro

Leer el archivo estructurado.

Validar columnas obligatorias y tipos.

Normalizar marca/familia/presentación sin destruir el texto de origen.

Detectar SKU nuevo, existente o conflictivo.

Generar vista previa de cambios.

Aplicar altas/actualizaciones aprobadas.

Crear CostHistory cuando cambie coste.

Actualizar datos de proveedor/abastecimiento.

No modificar stock físico.

Registrar archivo, fecha, usuario y resultado de importación.

| **Catálogo inicial. **El archivo maestro generado contiene 255 referencias y debe tratarse como semilla de trabajo. Una carga productiva requiere validación final contra las listas fuente y el inventario real. |
| --- |

# 17. Autenticación y sesiones

Usuarios individuales; evitar cuentas compartidas.

Contraseñas almacenadas con hash seguro mediante biblioteca estándar del framework.

Sesiones/tokens con expiración y revocación adecuada.

Protección contra fuerza bruta y abuso de login.

Recuperación de acceso mediante flujo seguro cuando se implemente.

MFA recomendable para administrador/gerencia si el contexto operativo lo permite.

No almacenar contraseñas en texto plano, archivos de configuración o prompts de IA.

# 18. Autorización

Se recomienda RBAC con permisos granulares.

| **Permiso conceptual** | **Ejemplo** |
| --- | --- |
| sales.create | Crear ventas. |
| sales.discount.override | Superar descuento permitido. |
| pricing.edit | Modificar precios. |
| cost.edit | Modificar costes. |
| inventory.adjust | Ajustar inventario. |
| credit.override | Autorizar exceso de crédito. |
| cash.close | Cerrar caja. |
| cash.reopen | Reabrir cierre. |
| audit.read | Consultar auditoría. |
| settings.manage | Cambiar configuración sensible. |

El frontend puede ocultar acciones no autorizadas, pero el backend debe volver a validar siempre el permiso.

# 19. Auditoría técnica

Registrar actor/user_id.

Timestamp.

Acción.

Entidad y ID.

Valores relevantes antes/después.

Motivo cuando se exige.

Contexto técnico mínimo útil: origen/IP o request id cuando sea apropiado y legal.

El log de auditoría no debe utilizarse como sustituto de los documentos transaccionales. Ambos cumplen funciones diferentes.

# 20. Seguridad de aplicación

Validación de entrada en servidor.

Consultas parametrizadas/ORM seguro.

Protección CSRF cuando la estrategia de autenticación lo requiera.

CORS restrictivo.

Rate limiting en endpoints públicos sensibles.

Cabeceras de seguridad.

Gestión de secretos fuera del repositorio.

Dependencias actualizadas y análisis de vulnerabilidades.

Principio de mínimo privilegio para base de datos y servicios.

Logs sin datos sensibles innecesarios.

# 21. Privacidad y datos

El sistema manejará datos de clientes, usuarios y operaciones. Antes de producción deben definirse las obligaciones legales aplicables en Venezuela y cualquier otra jurisdicción relevante. Este documento no inventa una política jurídica.

Recoger solo datos necesarios.

Controlar acceso a datos personales.

Definir retención y eliminación conforme a obligaciones reales.

Evitar exponer información personal en logs o analítica.

Mantener textos legales y consentimiento web separados de la lógica comercial.

# 22. Archivos e imágenes

Guardar archivos en almacenamiento de objetos, no como blobs masivos en tablas salvo razón específica.

Guardar metadatos y referencia en base de datos.

Validar tipo/tamaño de archivo.

Generar variantes optimizadas para web.

Mantener imágenes originales cuando la política lo requiera.

No permitir ejecución de archivos subidos.

# 23. Notificaciones

La arquitectura debe permitir notificaciones internas y, posteriormente, canales externos.

Stock bajo/agotado.

Pedido con fecha prevista próxima o vencida.

Cuenta por cobrar vencida.

Diferencia de caja.

Acción que requiere autorización.

Email, WhatsApp u otros canales externos requieren integración y credenciales aprobadas; no forman parte automática de la V1.

# 24. Reportes y analítica

Consultas operativas pueden salir de la base transaccional con índices adecuados.

Reportes pesados deben evitar bloquear operaciones de POS.

Mantener definiciones de KPIs versionadas/documentadas.

Margen histórico debe usar unit_cost_snapshot de la venta.

No recalcular hechos históricos con valores maestros actuales.

Si el volumen futuro lo requiere, se podrá añadir una capa analítica separada sin cambiar la semántica de negocio.

# 25. Concurrencia y transacciones

Confirmación de venta + movimientos asociados debe ser atómica.

Recepción + actualización de inventario debe ser atómica.

Cierre de caja debe impedir modificaciones incompatibles durante el proceso.

Controlar doble confirmación por doble clic/reintento.

Definir estrategia para evitar sobreventa si múltiples usuarios venden simultáneamente.

| **Regla técnica. **Las operaciones financieras y de inventario deben priorizar consistencia sobre conveniencia de interfaz. |
| --- |

# 26. Rendimiento

Indexar SKU, claves foráneas, fechas de documentos y campos frecuentes de búsqueda.

Paginar productos, clientes, movimientos y documentos.

Evitar cargar el catálogo completo en el navegador.

Optimizar imágenes públicas.

Medir antes de introducir caches complejas.

Objetivo UX: búsqueda y acciones de POS deben sentirse inmediatas en condiciones normales de red local/internet.

# 27. Respaldo y recuperación

Backups automáticos de base de datos.

Política de retención definida antes de producción.

Copia de archivos/imágenes coherente con base de datos.

Pruebas periódicas de restauración.

Separar credenciales de backup de credenciales normales de aplicación.

Documentar RPO/RTO cuando se seleccione hosting y criticidad operativa.

# 28. Entornos

| **Entorno** | **Uso** |
| --- | --- |
| Development | Trabajo local de desarrolladores/IA; datos sintéticos o controlados. |
| Staging | Pruebas integradas, migraciones, UAT y validación antes de producción. |
| Production | Operación real de FabriColor. |

Credenciales distintas por entorno.

No copiar datos personales de producción a desarrollo sin proceso seguro.

Migraciones de base de datos versionadas.

Configuración mediante variables/secret manager, no código hardcoded.

# 29. CI/CD y control de versiones

Repositorio Git.

Ramas/pull requests según tamaño del equipo.

Lint y formato automáticos.

Tests automáticos antes de merge/despliegue.

Migraciones de base de datos revisadas.

Despliegue reproducible.

Tags/releases para versiones productivas.

Rollback documentado para cambios críticos.

# 30. Estrategia de pruebas

| **Nivel** | **Objetivo** |
| --- | --- |
| Unitarias | Reglas de precios, crédito, stock, estados y cálculos. |
| Integración | API + base de datos + transacciones. |
| E2E | Flujos críticos completos desde UI. |
| UAT | Validación por usuarios reales de FabriColor. |
| Regresión | Evitar que nuevas funciones rompan ventas, inventario o caja. |

## 30.1 Casos E2E obligatorios

Venta rápida en efectivo.

Venta con pago mixto.

Venta a crédito dentro del límite.

Intento de crédito sobre límite y autorización.

Compra y recepción total.

Recepción parcial.

Devolución con reintegro a stock.

Ajuste de inventario con auditoría.

Apertura y cierre de caja con diferencia.

Cambio de coste sin alterar margen histórico de ventas pasadas.

Producto No publicar ausente de web.

Producto Consultar sin precio público.

# 31. Observabilidad

Logs estructurados con request/correlation id.

Registro de errores de aplicación.

Métricas básicas: latencia, errores, disponibilidad.

Alertas para fallos críticos.

Separar logs técnicos de auditoría de negocio.

No registrar secretos ni datos sensibles innecesarios.

# 32. Laboratorio / formulación: preparación técnica

No debe construirse el motor de fórmulas hasta definir la fuente y reglas reales, pero el modelo puede reservar entidades:

| **Entidad futura** | **Relación** |
| --- | --- |
| ColorCode | Marca/modelo/año/código cuando se defina la fuente. |
| Formula | Versión de fórmula y rendimiento. |
| FormulaComponent | Product/SKU + proporción/cantidad. |
| MixPreparation | Fórmula usada, cantidad objetivo, operador, fecha. |
| MixConsumption | Cantidad real consumida por SKU. |

Las fórmulas deben ser versionables. Una modificación posterior no debe alterar retrospectivamente una preparación ya realizada.

# 33. Roadmap técnico propuesto

| **Fase** | **Alcance** |
| --- | --- |
| Fase 0 — Fundaciones | Repositorio, entornos, autenticación, permisos, catálogo, importación y modelo base. |
| Fase 1 — Operación núcleo | Productos, clientes, POS/ventas, inventario, caja básica. |
| Fase 2 — Abastecimiento y crédito | Compras, recepciones, proveedores, cuentas por cobrar y pagos. |
| Fase 3 — Gestión y web | Dashboard, reportes, publicación web y catálogo público. |
| Fase 4 — Optimización | Alertas, automatizaciones, analítica y mejoras UX. |
| Fase 5 — Especialización | Laboratorio/formulación y capacidades B2B/e-commerce si se aprueban. |

Este roadmap es una propuesta de implementación, no un calendario contractual. Debe ajustarse tras validar prioridades, usuarios y operación real.

# 34. Definition of Done

Código revisado y versionado.

Tests relevantes pasan.

Migraciones incluidas y probadas.

Permisos verificados.

Auditoría incluida si la acción es sensible.

Estados de error y validaciones implementados.

UI usable en resoluciones objetivo.

Documentación/API actualizada.

No se introducen secretos en código.

Criterios de aceptación funcional del módulo cumplidos.

Probado en staging antes de producción.

# 35. Reglas maestras para ChatGPT / Claude

| **Estas reglas son obligatorias. **Una IA que continúe FabriColor debe actuar como colaborador de ingeniería sobre documentación existente, no como generador libre de un proyecto nuevo. |
| --- |

Leer y respetar los cinco documentos maestros antes de realizar cambios estructurales.

Preservar las decisiones aprobadas. Si propone cambiarlas, indicar explícitamente qué cambia, por qué y qué módulos afecta.

No inventar datos de FabriColor: stock, dirección, teléfono, horarios, impuestos, márgenes, proveedores adicionales, credenciales o fórmulas.

No confundir FabriColor con Goodsif. FabriColor es la tienda; Goodsif es una marca y FabriColor es su agente exclusivo.

Mantener Catálogo ≠ Inventario.

Mantener coste proveedor ≠ precio público.

Mantener disponibilidad proveedor ≠ stock FabriColor.

Mantener snapshots históricos de precio, coste e impuesto en documentos confirmados.

No eliminar auditoría o permisos para simplificar código.

No ampliar V1 a e-commerce/portal B2B/laboratorio completo sin aprobación.

Cuando falte información, marcar el punto como pendiente y proponer opciones; no convertir la opción en hecho.

Antes de crear una tabla/campo nuevo, comprobar si el concepto ya existe en el modelo.

Antes de modificar inventario, identificar el documento/movimiento que lo justifica.

Antes de modificar una operación confirmada, preferir anulación, reverso o documento compensatorio trazable.

Separar código de negocio de presentación UI.

No hardcodear impuestos, márgenes, monedas, roles o estados que deban ser configurables.

Escribir migraciones seguras y mantener compatibilidad de datos.

Añadir tests cuando se implemente una regla de negocio.

Explicar cualquier supuesto técnico que no proceda de los documentos.

Entregar cambios en unidades pequeñas, verificables y con impacto descrito.

# 36. Prompt maestro recomendado para iniciar una sesión de IA

Estás trabajando en el proyecto FabriColor. Usa los Documentos Maestros 01-05 y el Catálogo Maestro como fuente de verdad.

Tu prioridad es preservar las decisiones existentes y construir de forma incremental. No inventes datos comerciales, fiscales, de inventario ni de producto. Distingue siempre entre:
1) hecho procedente de documentación,
2) decisión aprobada,
3) propuesta técnica,
4) dato pendiente.

Antes de implementar una funcionalidad:
- identifica el módulo afectado;
- resume las reglas existentes relevantes;
- identifica dependencias con ventas, inventario, caja, compras, clientes, web y auditoría;
- propone el cambio mínimo coherente;
- define criterios de aceptación y tests.

Reglas críticas:
- Catálogo no es inventario.
- Disponibilidad del proveedor no es stock FabriColor.
- Coste de proveedor no es precio público.
- Las operaciones históricas conservan snapshots de precio/coste/impuesto.
- Las acciones sensibles requieren autorización y auditoría.
- No amplíes el alcance de V1 sin aprobación.

Si detectas contradicciones entre documentos, no las resuelvas silenciosamente: señala el conflicto y utiliza la decisión aprobada más reciente cuando sea inequívoca.

# 37. Formato recomendado para solicitudes de desarrollo a la IA

| **Bloque** | **Qué debe contener** |
| --- | --- |
| Objetivo | Qué se quiere construir/cambiar. |
| Contexto | Documento/módulo relacionado. |
| Restricciones | Qué no debe cambiar. |
| Datos | Ejemplos o fuentes disponibles. |
| Resultado esperado | Código, diseño, migración, tests, documento, etc. |
| Criterios de aceptación | Cómo saber que está terminado. |

Ejemplo: «Implementa recepción parcial de compras según Documento 02 y Documento 05. No cambies el modelo de catálogo. Debe actualizar tránsito, stock físico, coste histórico y auditoría de forma transaccional.»

# 38. Protocolo para cambios de alcance

Describir la nueva necesidad.

Identificar qué documentos y módulos afecta.

Clasificarla como cambio funcional, comercial, UX o técnico.

Evaluar impacto en datos existentes y migraciones.

Actualizar primero la documentación maestra correspondiente.

Implementar después el cambio.

Añadir/actualizar pruebas.

Registrar versión y decisión.

Este protocolo evita que el código se convierta en la única fuente de verdad y que diferentes sesiones de IA diverjan.

# 39. Matriz de trazabilidad documental

| **Tema** | **Fuente principal** |
| --- | --- |
| Visión, identidad y alcance | Documento 01. |
| Flujos y reglas del sistema administrativo | Documento 02. |
| SKU, catálogo, inventario y reglas comerciales | Documento 03 + catálogos fuente. |
| Web pública y UX/UI | Documento 04. |
| Arquitectura, datos, APIs, seguridad y desarrollo | Documento 05. |
| Referencias estructuradas iniciales | Catálogo Maestro FabriColor 2026. |

Una IA debe consultar la fuente principal del tema antes de asumir una regla desde otro documento de nivel más general.

# 40. Pendientes técnicos antes de producción

Elegir stack definitivo.

Elegir hosting/cloud y región.

Confirmar dominios y certificados.

Definir sucursales, almacenes y cajas iniciales.

Validar inventario inicial real.

Confirmar política de precios y monedas.

Confirmar requisitos fiscales/facturación en Venezuela.

Confirmar métodos de pago.

Definir usuarios iniciales y matriz de permisos.

Confirmar dirección, contactos y textos legales de la web.

Definir política de backups y recuperación.

Ejecutar UAT con usuarios de FabriColor.

# 41. Criterios de aceptación técnica global

Web y back office consumen servicios controlados sin duplicar manualmente el catálogo.

La base de datos mantiene integridad referencial y transacciones en operaciones críticas.

Los importes usan precisión decimal y moneda explícita.

Inventario puede reconciliarse con movimientos.

Ventas históricas mantienen precio y coste snapshot.

Autorización se valida en backend.

Acciones sensibles quedan auditadas.

La API pública no expone información interna.

Importar una lista de proveedor no altera stock físico.

Existen entornos separados y despliegue reproducible.

Los flujos críticos tienen pruebas automatizadas y UAT.

Backups y restauración se prueban antes de depender del sistema en operación real.

# 42. Cierre del paquete documental

Con este Documento 05 se completa el paquete maestro inicial de FabriColor. Los cinco documentos deben evolucionar de forma controlada a medida que se aprueben nuevas decisiones. La documentación no es un entregable estático: funciona como memoria estructurada del proyecto para propietarios, diseñadores, desarrolladores y asistentes de IA.

| **Documento** | **Función** |
| --- | --- |
| 01 | Visión, contexto y alcance. |
| 02 | Especificación funcional del sistema administrativo. |
| 03 | Catálogo, productos, inventario y reglas comerciales. |
| 04 | Web, arquitectura de información, UX/UI y funcionalidades. |
| 05 | Especificación técnica y guía maestra para IA/desarrollo. |

**FIN DEL DOCUMENTO 05**

Documento 05 · Especificación técnica y guía maestra para IA/desarrollo · Agosto 2026