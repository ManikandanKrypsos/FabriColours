**FABRICOLOR  |  DOCUMENTACIÓN MAESTRA DEL PROYECTO**

**DOCUMENTO 02 / 05**

**FabriColor**

**Especificación funcional del sistema administrativo**

Definición de módulos, flujos, reglas de negocio, permisos, datos y comportamiento esperado.

| **Campo** | **Definición** |
| --- | --- |
| Producto | Sistema administrativo web privado de FabriColor |
| Negocio | FabriColor — Ciudad Bolívar, Venezuela |
| Integración | Conectado con la web comercial y el catálogo maestro |
| Versión documental | 1.0 — 11 de agosto de 2026 |

**Objetivo de este documento. **Servir como especificación funcional de referencia para diseño UX/UI, desarrollo, pruebas y trabajo asistido por ChatGPT, Claude u otra IA. Describe qué debe hacer el sistema; las decisiones técnicas de implementación se documentarán aparte.

# 1. Propósito y principios funcionales

El sistema administrativo será la fuente operativa central de FabriColor. Debe cubrir la operación diaria de tienda, ventas, inventario, compras, clientes, proveedores, caja y control gerencial, manteniendo conexión controlada con la web pública.

Rapidez operativa: una venta de mostrador no debe requerir pasos innecesarios.

Trazabilidad: toda acción sensible debe poder atribuirse a usuario, fecha y hora.

Catálogo separado de inventario: un SKU puede existir con stock cero.

Historial: costes y precios relevantes deben conservar su evolución y no sobrescribirse sin registro.

Datos maestros centralizados: productos, clientes y proveedores se reutilizan entre módulos.

Permisos: cada rol ve y modifica únicamente lo que necesita.

Escalabilidad: preparar la solución para laboratorio/formulación y posibles ampliaciones futuras.

# 2. Mapa funcional del sistema

| **Módulo** | **Función principal** |
| --- | --- |
| Dashboard | Visión ejecutiva y alertas operativas. |
| Ventas / POS | Presupuestos, venta directa, facturación, cobro, crédito y devoluciones. |
| Clientes | Ficha comercial, historial, crédito, deuda y condiciones. |
| Inventario | Existencias, movimientos, reservas, mínimos, ajustes y conteos. |
| Compras | Pedidos, tránsito, recepción, costes y diferencias. |
| Proveedores | Datos, condiciones, historial de compras y precios. |
| Laboratorio | Base futura para fórmulas de color y consumo de tintas. |
| Caja | Apertura, cobros, egresos, cierre y diferencias. |
| Finanzas | Cuentas por cobrar/pagar y visión financiera operativa. |
| Reportes | Análisis de ventas, margen, stock, clientes, compras y caja. |
| Web | Control de publicación de productos y datos comerciales. |
| Configuración | Usuarios, permisos, impuestos, tarifas, reglas y parámetros. |

# 3. Navegación general y búsqueda global

Menú principal previsto: Dashboard | Ventas | Clientes | Inventario | Compras | Proveedores | Laboratorio | Caja | Finanzas | Reportes | Web | Configuración.

## 3.1 Barra superior

Buscador global.

Sucursal o almacén activo cuando aplique.

Notificaciones y alertas.

Usuario conectado.

Acceso rápido a Nueva venta.

## 3.2 Búsqueda global

Debe localizar al menos productos, clientes y documentos. Para productos, la búsqueda no dependerá del nombre exacto.

Buscar por SKU/código, descripción, marca, familia, presentación y términos parciales.

Una consulta como “MF1K32” debe devolver la referencia exacta.

Una consulta como “perla blanca” debe mostrar las referencias relacionadas.

Una consulta como “1200” debe poder encontrar abrasivos P1200 y referencias relacionadas.

Una consulta como “masilla 1kg” debe localizar la presentación correspondiente aunque el usuario no escriba el nombre completo.

# 4. Dashboard

El Dashboard debe permitir comprender en pocos segundos el estado del negocio y las tareas que requieren atención.

## 4.1 Indicadores principales

Ventas de hoy, semana y mes.

Cobrado hoy.

Pendiente por cobrar.

Margen bruto del mes.

Caja esperada y estado del cierre.

## 4.2 Alertas

Productos bajo stock mínimo.

Productos agotados.

Pedidos o mercancía pendientes de recibir.

Facturas/cuentas vencidas.

Diferencias de caja pendientes.

Otras incidencias que se definan posteriormente.

## 4.3 Bloques analíticos

Ventas últimos 30 días.

Productos más vendidos.

Clientes con mayor facturación.

Últimos movimientos de inventario.

Últimas ventas.

Los KPIs deben respetar los permisos del usuario y, si existe multi-sucursal en el futuro, el ámbito de sucursal seleccionado.

# 5. Ventas / POS

Es uno de los módulos críticos. Debe admitir tanto venta rápida de mostrador como un flujo comercial más completo.

## 5.1 Flujos admitidos

Flujo completo de referencia:

**Cliente  →  Presupuesto  →  Pedido  →  Factura/Venta  →  Pago  →  Entrega**

El sistema no obligará a recorrer todas las etapas. Una venta de mostrador puede crearse y cobrarse directamente.

## 5.2 Pantalla POS

Zona de búsqueda y selección de productos.

Carrito con producto, cantidad, precio, descuento y total por línea.

Selección de cliente; por defecto podrá utilizarse Consumidor final.

Subtotal, descuentos, impuestos y total.

Acciones: Guardar presupuesto, Cobrar y Guardar venta a crédito.

Panel rápido del producto sin abandonar la venta.

## 5.3 Reglas de producto en la venta

El vendedor selecciona un SKU existente; no debe crear nombres de producto libres para sustituir el catálogo.

Mostrar stock disponible y estado de disponibilidad.

El precio podrá depender de la tarifa del cliente.

Cambios manuales de precio o descuentos estarán sujetos a permisos.

Cada línea debe guardar el coste vigente en el momento de la venta para calcular posteriormente el margen histórico real.

## 5.4 Cobro

Métodos previstos: efectivo, tarjeta, transferencia, pago móvil, mixto y crédito. La lista final queda pendiente de validación operativa.

Pago mixto: permitir distribuir el total entre varios métodos y validar que la suma coincida con el total.

Al confirmar: registrar venta, cobro, movimiento de caja cuando aplique y movimiento de inventario.

Opciones posteriores: imprimir, generar PDF y compartir por canales habilitados.

## 5.5 Venta a crédito

Solo para clientes habilitados.

Mostrar límite de crédito, deuda actual y crédito disponible.

Permitir plazo de crédito según condiciones del cliente.

Si se supera el límite o una regla de riesgo, requerir autorización de un usuario con permiso.

La venta genera cuenta por cobrar y fecha de vencimiento.

## 5.6 Devoluciones y notas de crédito

Relacionar la devolución con la venta original cuando sea posible.

Registrar motivo y usuario.

Definir si el producto vuelve a stock vendible, stock dañado o no vuelve a inventario.

Ajustar saldo del cliente y/o medio de devolución según la operación.

# 6. Clientes

## 6.1 Tipos

Consumidor final / particular.

Taller.

Chapista o pintor profesional.

Empresa.

Flota u otro cliente corporativo.

## 6.2 Ficha del cliente

Identificación y datos de contacto.

Tipo de cliente.

Historial de presupuestos, ventas, facturas y devoluciones.

Pagos realizados y saldo pendiente.

Límite de crédito y crédito disponible.

Plazo de crédito.

Lista/tarifa de precios asignada.

Descuento habitual, si aplica.

Vendedor asignado, si aplica.

Notas comerciales y estado activo/inactivo.

## 6.3 Cuenta corriente

Debe poder reconstruirse el saldo del cliente a partir de cargos, pagos, notas de crédito y otros movimientos autorizados. No se debe depender de un saldo manual sin detalle.

# 7. Inventario

El inventario utiliza el catálogo maestro, pero añade la dimensión de existencias y movimientos.

## 7.1 Valores de stock

| **Concepto** | **Definición** |
| --- | --- |
| Stock físico | Unidades físicamente registradas en almacén/tienda. |
| Stock reservado | Unidades comprometidas para pedidos o procesos que se definan. |
| Stock disponible | Stock físico menos stock reservado. |
| Stock mínimo | Umbral configurado para generar alerta. |
| En tránsito | Cantidad comprada todavía no recibida físicamente. |

## 7.2 Movimientos

Entrada por compra/recepción.

Salida por venta.

Reserva y liberación de reserva.

Devolución de cliente.

Devolución a proveedor.

Ajuste positivo o negativo.

Producto dañado o merma.

Transferencia entre ubicaciones/sucursales si se habilita en el futuro.

## 7.3 Reglas

Todo movimiento debe indicar tipo, SKU, cantidad, fecha, usuario y origen documental cuando exista.

Los ajustes manuales requieren motivo; determinados ajustes pueden requerir permiso especial.

El sistema debe permitir consultar el historial cronológico de un SKU.

Los estados visuales previstos son Disponible, Stock bajo, En tránsito, Agotado y Sin fecha prevista.

## 7.4 Inventario físico

Crear sesión de conteo.

Definir ámbito: todos los productos, marca, familia, ubicación u otro filtro.

Capturar cantidad contada.

Comparar cantidad del sistema contra cantidad física.

Revisar diferencias.

Aprobar ajuste con usuario autorizado.

Conservar evidencia del conteo y del ajuste resultante.

# 8. Catálogo maestro y ficha de producto

El catálogo maestro constituye la identidad estable de cada referencia y alimenta ventas, compras, inventario y web.

## 8.1 Campos funcionales mínimos

| **Grupo** | **Campos** |
| --- | --- |
| Identificación | SKU/código, marca, familia, descripción, presentación. |
| Compra | Proveedor, coste base, moneda, compra mínima, unidades por paquete cuando aplique. |
| Comercial | Tarifas/precios de venta, margen, impuestos configurables. |
| Inventario | Stock, reservado, disponible, mínimo, ubicación, estado. |
| Abastecimiento | Disponibilidad de proveedor, fecha prevista de llegada, mercancía en tránsito. |
| Web | Publicar Sí/No, mostrar precio Sí/Consultar, descripción e imágenes futuras. |

## 8.2 Datos de proveedor vs. datos FabriColor

El sistema debe distinguir explícitamente el dato recibido del proveedor del dato operativo de FabriColor. Un precio de lista de proveedor es coste/referencia de compra y no equivale automáticamente al precio público. Una disponibilidad indicada por proveedor tampoco equivale a stock físico de FabriColor.

# 9. Precios, costes y márgenes

## 9.1 Estructura

**Coste proveedor  →  Gastos adicionales  →  Coste real  →  Margen  →  Precio de venta**

Separar coste, impuesto, margen y precio.

Permitir varias tarifas para el mismo SKU: Público, Profesional, Taller, Mayorista y Especial como modelo inicial.

Las tarifas definitivas podrán cambiar sin modificar la estructura.

Mantener histórico de cambios de coste y precio con fecha de vigencia.

Guardar en cada venta el precio y coste utilizados en ese momento.

La política definitiva de margen y redondeo queda pendiente de configuración.

## 9.2 Impuestos

Los catálogos aportados indican precios de proveedor sin IVA. La tasa y reglas fiscales aplicables a FabriColor deben ser configurables y no se fijan en este documento. No se debe inventar una tasa fiscal.

# 10. Compras

Flujo funcional de referencia:

**Pedido proveedor  →  Mercancía en tránsito  →  Recepción  →  Inventario  →  Cuenta por pagar**

## 10.1 Pedido de compra

Proveedor, fecha, referencia externa, moneda y condiciones.

Líneas con SKU, cantidad, coste esperado y presentación/paquete.

Estado: borrador, enviado/confirmado, parcialmente recibido, recibido, cancelado.

Registrar fecha estimada de llegada cuando exista.

## 10.2 Recepción

Comparar cantidad pedida, recibida y pendiente.

Permitir recepción parcial.

Registrar diferencias y observaciones.

Actualizar stock físico solo por la cantidad efectivamente recibida.

Reducir cantidad en tránsito.

Registrar coste recibido y alimentar historial de costes.

## 10.3 Particularidades de catálogo

El modelo debe soportar productos vendidos por unidad pero comprados por paquete. Esto es relevante para referencias como Kovax, cuya lista de origen contempla precio por unidad y compra mínima de un paquete. El sistema debe conservar factor de empaque y regla de compra mínima sin impedir una política interna de venta unitaria.

# 11. Proveedores

Datos fiscales/comerciales y contacto.

Marcas suministradas.

Condiciones de pago.

Pedidos y recepciones.

Cuentas por pagar.

Historial de costes por SKU.

Tiempos de entrega y observaciones.

Estado activo/inactivo.

Proveedor identificado en los catálogos aportados: Soldaduras y Revestimientos FOCUS, C.A. Otros proveedores podrán añadirse posteriormente.

# 12. Caja y medios de pago

## 12.1 Apertura

Usuario/cajero.

Fecha y hora.

Saldo inicial.

Caja o punto de venta asociado cuando exista más de uno.

## 12.2 Movimientos

Cobros de ventas.

Cobros de cuentas pendientes.

Devoluciones/reembolsos.

Ingresos manuales autorizados.

Egresos autorizados.

Otros movimientos configurados.

## 12.3 Cierre

El cierre debe comparar la operación registrada con el importe declarado/contado.

**Ventas y cobros registrados − devoluciones − egresos = caja esperada**

Registrar caja real por medio de pago cuando corresponda.

Calcular diferencia.

Solicitar explicación si existe diferencia.

Conservar usuario, fecha, hora y aprobación cuando aplique.

# 13. Finanzas operativas

Este módulo no se define todavía como contabilidad general completa. Su alcance inicial es el control financiero directamente ligado a la operación.

Cuentas por cobrar de clientes.

Vencimientos y antigüedad de deuda.

Pagos parciales y completos.

Cuentas por pagar derivadas de compras, si se activa.

Consulta de cobros y pagos por período.

Visión de margen bruto basada en coste histórico de venta.

Una integración contable/fiscal completa deberá especificarse cuando se confirme el proceso legal y tributario requerido en Venezuela.

# 14. Laboratorio / formulación de pintura

Módulo reservado desde la arquitectura inicial por su relevancia potencial para el negocio.

| **Entidad futura** | **Función** |
| --- | --- |
| Vehículo | Marca, modelo, año y otros identificadores necesarios. |
| Código de color | Identificación del color del fabricante. |
| Fórmula | Conjunto de componentes y proporciones. |
| Tinta / componente | SKU del catálogo, principalmente tintas Goodsif u otros componentes. |
| Cantidad | Consumo teórico y posteriormente real. |
| Preparación | Trabajo realizado, cantidad final, coste y responsable. |

Una fórmula debe poder relacionarse con SKUs reales.

Una preparación futura podrá descontar cantidades consumidas del inventario.

La fuente de fórmulas y el flujo exacto de trabajo todavía no están definidos.

No inventar fórmulas de color en fases posteriores sin una fuente válida.

# 15. Usuarios, roles y permisos

| **Rol inicial** | **Acceso esperado** |
| --- | --- |
| Administrador | Acceso completo y configuración. |
| Gerencia | Ventas, compras, inventario, clientes, proveedores y reportes. |
| Vendedor | Clientes, presupuestos y ventas según permisos. |
| Caja | Cobros, caja y cierre. |
| Almacén | Recepciones, movimientos e inventario. |

## 15.1 Acciones sensibles

Modificar costes.

Modificar precios o aplicar descuentos superiores al permitido.

Eliminar/anular documentos.

Aprobar venta por encima del límite de crédito.

Realizar ajustes de inventario.

Reabrir o modificar cierres de caja.

Cambiar configuraciones fiscales o comerciales.

Los roles son una base inicial. El sistema debe permitir permisos más granulares que el simple nombre del rol.

# 16. Auditoría

El registro de auditoría debe permitir responder quién hizo qué y cuándo.

Usuario.

Fecha y hora.

Módulo y acción.

Entidad afectada: producto, venta, cliente, pedido, etc.

Valor anterior y nuevo cuando sea relevante.

Motivo cuando la acción lo requiera.

Ejemplo conceptual: «Usuario X cambió el precio del SKU MF1K32 de A a B — fecha/hora».

# 17. Integración con la web FabriColor

El sistema administrativo será la fuente principal de los datos comerciales que se publiquen.

Publicar en web: Sí / No.

Mostrar precio: Sí / Consultar.

Seleccionar qué descripción, categoría, imágenes y atributos se publican.

No exponer coste, margen, stock interno detallado ni información administrativa.

La disponibilidad pública deberá derivarse de una regla controlada y no mostrar necesariamente la cantidad exacta de stock.

El diseño técnico de la sincronización/API se documentará en el Documento 05.

# 18. Reportes

| **Área** | **Reportes previstos** |
| --- | --- |
| Ventas | Por período, vendedor, cliente, marca, familia, SKU y tarifa. |
| Margen | Margen bruto por venta, producto, marca, cliente y período. |
| Inventario | Existencias, bajo mínimo, agotados, valorización, movimientos y ajustes. |
| Compras | Por proveedor, producto, período, coste y estado de recepción. |
| Clientes | Facturación, deuda, vencimientos, frecuencia y principales clientes. |
| Caja | Aperturas, cierres, cobros, egresos y diferencias. |
| Auditoría | Acciones sensibles por usuario, fecha, módulo y entidad. |

Los indicadores definitivos y fórmulas de valorización se validarán antes de desarrollo final.

# 19. Estados funcionales y notificaciones

Producto: Disponible, Stock bajo, En tránsito, Agotado, Sin fecha prevista, Inactivo.

Venta/documento: Borrador, Pendiente, Confirmado, Pagado/Parcial, Anulado u otros estados según documento.

Compra: Borrador, Confirmada, Parcialmente recibida, Recibida, Cancelada.

Cuenta por cobrar: Pendiente, Parcial, Pagada, Vencida.

Los estados deben tener reglas explícitas de transición; no deben utilizarse únicamente como etiquetas visuales.

# 20. Reglas de integridad y controles

No permitir SKU duplicado dentro del catálogo maestro.

No permitir cantidades negativas de forma silenciosa; cualquier excepción debe estar configurada y auditada.

No eliminar físicamente documentos financieros/operativos confirmados cuando una anulación con trazabilidad sea suficiente.

No recalcular ventas históricas usando el coste actual: usar el coste guardado en la línea de venta.

No mezclar disponibilidad del proveedor con stock físico de FabriColor.

No convertir automáticamente el coste del proveedor en precio de venta.

No permitir que un usuario sin permiso cambie precio, coste, crédito o inventario sensible.

Validar totales de pagos mixtos.

Conservar relaciones entre documento origen y movimientos generados.

# 21. UX/UI funcional ya acordada

Interfaz moderna y profesional, sin sobrecarga visual.

Sidebar negro/grafito y fondo general gris muy claro como dirección inicial.

Tarjetas blancas y uso del color de acción principalmente para acciones/estados.

Dashboard orientado a decisiones.

POS dividido entre búsqueda/productos y carrito/cliente.

Ficha rápida de producto en panel lateral sin abandonar la venta.

Inventario en tabla profesional con filtros por marca, familia, stock, proveedor y disponibilidad.

La especificación visual detallada de web y experiencia se documentará separadamente.

# 22. Datos maestros y documentos transaccionales

| **Datos maestros** | **Documentos / movimientos** |
| --- | --- |
| Productos / SKUs | Presupuestos, ventas, devoluciones. |
| Clientes | Cobros, cuentas por cobrar. |
| Proveedores | Pedidos, recepciones, cuentas por pagar. |
| Tarifas / impuestos | Movimientos de caja. |
| Usuarios / permisos | Movimientos y ajustes de inventario. |
| Marcas / familias | Preparaciones de laboratorio futuras. |

La distinción es importante: los datos maestros describen entidades reutilizables; los documentos registran hechos ocurridos y deben conservar trazabilidad histórica.

# 23. Casos de uso prioritarios para la primera versión

| **Prioridad** | **Caso de uso** |
| --- | --- |
| P0 | Buscar producto y realizar una venta de mostrador. |
| P0 | Cobrar con uno o varios medios de pago. |
| P0 | Descontar inventario y consultar existencias. |
| P0 | Crear/consultar clientes y registrar venta a crédito. |
| P0 | Crear pedido de compra y recibir mercancía. |
| P0 | Consultar cuentas por cobrar y registrar pagos. |
| P0 | Abrir/cerrar caja y detectar diferencias. |
| P0 | Controlar usuarios, permisos y auditoría básica. |
| P1 | Presupuestos y conversión a venta/pedido. |
| P1 | Tarifas múltiples y reglas comerciales avanzadas. |
| P1 | Reportes avanzados y alertas gerenciales. |
| P1 | Publicación controlada hacia la web. |
| P2 | Laboratorio/formulación de color. |

P0/P1/P2 expresan una propuesta de priorización documental para organizar el desarrollo; deberán validarse antes de fijar un roadmap contractual.

# 24. Aspectos pendientes de decisión

Stack tecnológico, base de datos, hosting y arquitectura de despliegue.

Número inicial de sucursales, almacenes y cajas.

Régimen fiscal, tasa(s) de impuesto y requisitos de facturación aplicables.

Métodos de pago exactos y posibles integraciones bancarias/pasarelas.

Política definitiva de precios, márgenes, descuentos y redondeos.

Reglas exactas de reserva de stock y autorización de stock negativo.

Proceso de cuentas por pagar y profundidad del módulo financiero.

Formato de impresión/factura/recibo y dispositivos físicos.

Fuente de datos y flujo detallado del Laboratorio.

Reglas de disponibilidad que se mostrarán al cliente en la web.

Necesidad de códigos de barras, lectores, etiquetas e impresión de etiquetas.

# 25. Criterios de aceptación funcional global

Un usuario autorizado puede localizar un SKU rápidamente y completar una venta sin crear productos manuales.

La venta registra cliente, líneas, cantidades, precio, coste histórico, impuestos, total y pagos.

El inventario refleja los movimientos generados por ventas, compras, devoluciones y ajustes.

Una recepción parcial mantiene correctamente cantidad recibida, pendiente y en tránsito.

Un cliente a crédito muestra deuda, límite y disponibilidad antes de confirmar la operación.

El sistema conserva historial de cambios relevantes y auditoría de acciones sensibles.

El cierre de caja compara valores esperados y reales y registra diferencias.

La web puede recibir únicamente productos autorizados sin exponer datos internos.

Los reportes históricos no cambian retroactivamente porque haya cambiado el coste o precio actual.

# 26. Instrucciones para ChatGPT / Claude

Cuando una IA utilice este documento como contexto del proyecto:

Tratar estas reglas como especificación funcional vigente salvo que exista una versión posterior aprobada.

No inventar procesos fiscales, métodos de pago, márgenes, stock o fórmulas de color.

Separar claramente una propuesta nueva de una decisión ya aprobada.

Mantener el principio Catálogo ≠ Inventario.

Mantener el historial de costes/precios y el coste histórico por línea de venta.

No eliminar trazabilidad para simplificar el desarrollo.

Diseñar flujos de venta rápidos y evitar pasos obligatorios que no aporten control.

Si una nueva funcionalidad afecta ventas, inventario, caja o finanzas, explicar sus efectos en los demás módulos.

Consultar los otros documentos maestros del proyecto para identidad, catálogo, web y arquitectura técnica.

# 27. Relación con el resto de la documentación

| **Documento** | **Responsabilidad** |
| --- | --- |
| 01 — Visión, contexto y alcance | Qué es FabriColor, objetivos, alcance y principios. |
| 02 — Especificación funcional | Qué debe hacer el sistema administrativo. Este documento. |
| 03 — Catálogo, productos e inventario | Datos de producto, estructura comercial y reglas derivadas de catálogos. |
| 04 — Web y UX/UI | Experiencia pública, navegación, fichas y diseño. |
| 05 — Especificación técnica y guía IA | Cómo implementar, integrar y continuar técnicamente el proyecto. |

**FIN DEL DOCUMENTO 02**

Documento 02 · Especificación funcional del sistema administrativo · Agosto 2026