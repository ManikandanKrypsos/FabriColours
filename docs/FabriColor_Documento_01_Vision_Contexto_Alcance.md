FABRICOLOR  |  DOCUMENTACIÓN MAESTRA DEL PROYECTO

DOCUMENTO 01 / 05

**FabriColor**

**Visión, contexto y alcance del proyecto**

Web comercial + sistema administrativo conectado

| **Negocio** | FabriColor |
| --- | --- |
| **Ubicación** | Ciudad Bolívar, Venezuela |
| **Posicionamiento** | Tienda especializada en pintura automotriz y materiales asociados |
| **Relación de marca** | FabriColor es agente exclusivo de Goodsif |

**Propósito del documento**

Establecer una fuente de verdad clara y reutilizable para equipos humanos y para asistentes de IA (por ejemplo, ChatGPT o Claude), de forma que el proyecto pueda continuar sin perder las decisiones, restricciones, datos y objetivos ya definidos.

*Estado: Base de proyecto v1.0 · Fecha: 11 de agosto de 2026*

# 1. Resumen ejecutivo

FabriColor es una tienda ubicada en Ciudad Bolívar, Venezuela, especializada en pintura automotriz y materiales relacionados. El proyecto contempla la creación coordinada de dos activos digitales: una web comercial pública y un sistema administrativo privado. Ambos deben compartir información y operar como un único ecosistema, evitando duplicar la gestión de productos, precios, disponibilidad y contenido.

FabriColor actúa como agente exclusivo de Goodsif. El catálogo de trabajo suministrado también incluye productos de Symplex, RapidCure, Kovax y Lake Country. Las listas aportadas contienen códigos, descripciones, presentaciones, precios y datos de disponibilidad que servirán como base para el catálogo maestro y, más adelante, para inventario, compras, ventas y publicación web.

El sistema administrativo se inspira funcionalmente en el tipo de solución de gestión que el usuario ha referenciado mediante FinaPartner, pero FabriColor requiere un diseño propio adaptado a pintura automotriz, venta de mostrador, clientes profesionales, inventario por SKU, mercancía en tránsito y una futura capacidad de formulación de color.

# 2. Objetivo del proyecto

El objetivo general es digitalizar y conectar la operación comercial y administrativa de FabriColor.

Crear una presencia web moderna, profesional y coherente con el negocio físico.

Convertir los catálogos de proveedores en un catálogo maestro estructurado y reutilizable.

Gestionar ventas, clientes, inventario, compras, proveedores, caja, cobros, precios y reportes desde un sistema central.

Conectar la web con el sistema administrativo para que la información se mantenga desde una fuente principal.

Preparar una arquitectura que pueda crecer hacia funcionalidades específicas del sector, especialmente formulación de pintura automotriz.

Mantener trazabilidad de cambios, costes, precios, movimientos de inventario y acciones de usuarios.

# 3. Alcance de la solución

## 3.1 Web comercial pública

La web será el escaparate digital de FabriColor. Debe presentar la empresa, sus marcas y familias de productos, permitir localizar referencias de forma sencilla y facilitar el contacto comercial. La web no se plantea como un catálogo aislado: debe consumir información controlada desde el sistema administrativo.

Catálogo organizado por familias y marcas.

Búsqueda por código, nombre, marca, categoría, presentación y términos relacionados.

Ficha de producto con información comercial y disponibilidad según las reglas que se definan.

Control administrativo para decidir si un producto se publica y si su precio se muestra o queda como 'Consultar'.

Diseño moderno y profesional, sin exceso de elementos decorativos.

## 3.2 Sistema administrativo privado

Será la fuente operativa principal. Su alcance funcional previsto incluye Dashboard, Ventas/POS, Clientes, Inventario, Compras, Proveedores, Laboratorio, Caja, Finanzas, Reportes, gestión de la Web y Configuración.

Ventas de mostrador, presupuestos, pedidos, facturas, pagos, devoluciones y ventas a crédito.

Inventario físico, reservado y disponible; stock mínimo; entradas, salidas, ajustes, devoluciones y productos dañados.

Compras, mercancía en tránsito, recepción y comparación entre pedido y recibido.

Clientes particulares y profesionales, condiciones comerciales, límites y plazos de crédito.

Proveedores, costes, historial de precios y condiciones de compra.

Caja, métodos de pago, cierres, diferencias y trazabilidad.

Usuarios, roles, permisos y registro de auditoría.

Reportes de ventas, margen, inventario, clientes, cobros y operación.

## 3.3 Módulo futuro de laboratorio / formulación

La arquitectura debe reservar un módulo específico para formulación de pintura. La visión funcional es poder relacionar vehículo, marca, modelo, año, código de color, fórmula, tintas Goodsif, cantidades, coste y preparación. La intención futura es que una preparación pueda consumir cantidades reales de materias primas del inventario.

# 4. Contexto comercial y catálogo de marcas

| **Marca** | **Papel dentro del catálogo** |
| --- | --- |
| GOODSIF | Línea principal de pintura automotriz: tintas poliéster, aluminios, perlas, poliuretanos 2K, transparentes, fondos, activadores, reductores y misceláneos. |
| SYMPLEX | Pulido, detailing, compounds, restauradores, selladores y accesorios. |
| RAPIDCURE | Preparación y reparación: masillas, fibra preparada, uretano, tirro, desengrasante y otros complementos. |
| KOVAX | Abrasivos profesionales: lijas al agua, lijas al seco, Super Assilex, Super Buflex, Tolecut y accesorios. |
| LAKE COUNTRY | Mopas, platos y accesorios profesionales de pulido. |

Importante: las listas de proveedor aportadas indican que los precios no incluyen IVA y que la disponibilidad puede cambiar sin previo aviso. En Kovax, además, la lista refleja precio por unidad y una compra mínima de un paquete. En Goodsif se ha identificado también información de llegada futura para determinadas referencias. Estas reglas deben preservarse como datos de origen y no confundirse con el precio público ni con el stock físico de FabriColor.

# 5. Principios de diseño del producto

**Una sola fuente de verdad. **Producto, código, marca y datos maestros se mantienen centralmente y se reutilizan en administración y web.

**Catálogo ≠ inventario. **Una referencia puede existir aunque el stock de FabriColor sea cero. El catálogo describe; el inventario cuantifica existencias.

**Historial, no sobrescritura. **Los cambios de coste y precio deben conservar histórico para poder explicar márgenes y decisiones pasadas.

**Operación rápida. **La venta de mostrador debe ser ágil y no obligar a pasar por pasos innecesarios.

**Permisos por responsabilidad. **Acciones sensibles como cambiar costes, aplicar grandes descuentos o ajustar inventario requieren permisos.

**Trazabilidad. **Cambios relevantes deben registrar usuario, fecha, hora y valor anterior/nuevo cuando aplique.

**Escalabilidad. **La primera versión debe permitir añadir funciones futuras sin rehacer la estructura central.

# 6. Usuarios y clientes objetivo

El sistema debe contemplar dos grupos diferentes:

## 6.1 Usuarios internos

Administrador: acceso completo.

Gerencia: ventas, compras, inventario, clientes y reportes.

Vendedor: clientes, presupuestos y ventas.

Caja: cobros, medios de pago y cierre.

Almacén: recepción, entradas, salidas e inventario.

## 6.2 Clientes comerciales

Consumidor final / particular.

Taller.

Chapista o pintor profesional.

Empresa.

Flota u otro cliente corporativo.

Los clientes profesionales podrán tener, cuando se configure, lista de precios, descuento habitual, vendedor asignado, límite de crédito y plazo de pago.

# 7. Identidad y dirección visual

La identidad visual acordada para FabriColor debe transmitir modernidad y profesionalidad sin exageración. La base cromática planteada es gris y negro, con posibilidad de utilizar un color de acción distintivo en la interfaz. En la exploración de identidad se han indicado como elementos potenciales el Puente del Orinoco, una pistola de pintura, latas de pintura y automóviles. Estos elementos deben utilizarse de forma inteligente y no convertir el logotipo o la web en una composición recargada.

Para el sistema administrativo se ha planteado una interfaz de fondo gris muy claro, sidebar negro/grafito, tarjetas blancas, texto oscuro y color de acción reservado para estados o acciones importantes.

# 8. Relación entre web y sistema administrativo

La web y el sistema administrativo son partes del mismo ecosistema. El sistema administrativo debe actuar como fuente principal para productos y datos comerciales publicados. El objetivo es que un producto se cree o actualice una vez y que la web reciba los campos autorizados.

| **Sistema administrativo** | **Regla de publicación** | **Web FabriColor** | **Cliente** |
| --- | --- | --- | --- |
| Producto / precio / disponibilidad / contenido | Publicar: Sí/No · Mostrar precio: Sí/Consultar | Catálogo y ficha pública | Consulta, contacto o compra futura |

# 9. Requisitos de alto nivel

| **ID** | **Requisito** |
| --- | --- |
| REQ-01 | Mantener catálogo maestro por SKU. |
| REQ-02 | Separar coste de proveedor, impuestos, margen y precio de venta. |
| REQ-03 | Permitir varias tarifas comerciales para un mismo SKU. |
| REQ-04 | Controlar stock físico, reservado, disponible y mínimo. |
| REQ-05 | Gestionar mercancía en tránsito y fechas previstas de llegada. |
| REQ-06 | Registrar ventas directas y flujos de presupuesto/pedido/factura cuando sean necesarios. |
| REQ-07 | Gestionar clientes a crédito y controlar límites/plazos. |
| REQ-08 | Mantener historial de costes y precios. |
| REQ-09 | Gestionar compras, recepción y diferencias entre pedido y recibido. |
| REQ-10 | Registrar caja y pagos, incluidos pagos mixtos. |
| REQ-11 | Aplicar roles, permisos y auditoría. |
| REQ-12 | Sincronizar de forma controlada el catálogo público con el sistema administrativo. |
| REQ-13 | Preparar la arquitectura para laboratorio/formulación de pintura. |

# 10. Decisiones establecidas vs. asuntos pendientes

| **ESTABLECIDO** | **PENDIENTE DE DEFINIR / VALIDAR** |
| --- | --- |
| • Nombre del negocio: FabriColor. | • Stack tecnológico definitivo y proveedor de hosting. |
| • Ubicación: Ciudad Bolívar, Venezuela. | • Régimen fiscal y configuración tributaria exacta que aplicará FabriColor. |
| • Agente exclusivo de Goodsif. | • Métodos de pago exactos que estarán habilitados en producción. |
| • Proyecto: web + sistema administrativo conectado. | • Política definitiva de márgenes, redondeos y listas de precios. |
| • Catálogo base con Goodsif, Symplex, RapidCure, Kovax y Lake Country. | • Número de sucursales/almacenes iniciales y necesidad de multi-sucursal. |
| • Necesidad de catálogo maestro por SKU. | • Proceso exacto de facturación fiscal/electrónica requerido en Venezuela. |
| • Necesidad de inventario, ventas, compras, clientes, caja, permisos y auditoría. | • Fuente de fórmulas de color y reglas detalladas del módulo Laboratorio. |
| • Dirección visual moderna, sobria y profesional. | • Qué productos y precios serán públicos en la web. |

# 11. Fuentes de información del proyecto

Este documento consolida las decisiones de proyecto definidas en la conversación y los cuatro catálogos de proveedor aportados por el usuario. Los catálogos deben conservarse como fuentes primarias para códigos, descripciones, precios y condiciones visibles en cada lista.

GOODSIF — Lista de Precio con Disponibilidad, 06-07-2026.

SYMPLEX / LAKE COUNTRY — Lista de Precio con Disponibilidad 2026.

RAPIDCURE — Lista de Precio con Disponibilidad 2026.

KOVAX — Lista de Precio con Disponibilidad 2026.

Catálogo Maestro FabriColor 2026 — archivo estructurado generado a partir de las listas anteriores.

# 12. Instrucciones de uso para ChatGPT / Claude

Cuando este documento se utilice como contexto de una IA, debe tratarse como documentación maestra del proyecto. La IA debe conservar las decisiones marcadas como establecidas y no sustituirlas silenciosamente por supuestos.

No cambiar el nombre FabriColor ni su ubicación sin una instrucción explícita.

No confundir FabriColor con Goodsif: FabriColor es la tienda; Goodsif es una marca y FabriColor es su agente exclusivo.

Tratar la web y el sistema administrativo como un único ecosistema conectado.

No considerar el precio del proveedor como precio público de venta.

No asumir que una referencia del catálogo está físicamente disponible en FabriColor.

No inventar reglas fiscales, márgenes, stock, métodos de pago o fórmulas de color que no estén documentados.

Cuando falte una decisión, marcarla como pendiente y proponer alternativas claramente separadas de los hechos establecidos.

Mantener compatibilidad con los documentos maestros posteriores del proyecto; si existe conflicto, solicitar o aplicar la versión más reciente aprobada.

# 13. Criterios de éxito

El personal puede vender y localizar productos rápidamente.

La gerencia conoce ventas, cobros, margen, inventario y alertas desde un único Dashboard.

Los productos se administran una sola vez y se publican de forma controlada en la web.

Los movimientos de inventario y cambios sensibles son trazables.

Los costes y precios conservan histórico.

La solución puede crecer hacia formulación de pintura y otras capacidades sin rehacer el núcleo.

La documentación permite que un nuevo desarrollador o una IA continúe el proyecto sin perder contexto.

# 14. Límites de este documento

Este Documento 01 define visión, contexto, alcance y principios. No sustituye la especificación funcional detallada, el modelo de datos, la arquitectura técnica ni la especificación UX/UI. Esos aspectos se desarrollarán en los documentos maestros siguientes.

**FIN DEL DOCUMENTO 01**

Documento 01 · Visión, contexto y alcance · Agosto 2026