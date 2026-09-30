**FABRICOLOR  |  DOCUMENTACIÓN MAESTRA DEL PROYECTO**

**DOCUMENTO 03 / 05**

**FabriColor**

**Catálogo, productos, inventario y reglas comerciales**

Modelo maestro de producto, marcas, familias, abastecimiento, stock, costes, precios y publicación.

| **Campo** | **Definición** |
| --- | --- |
| Base documental | Listas GOODSIF, SYMPLEX/LAKE COUNTRY, RAPIDCURE y KOVAX aportadas por el usuario |
| Proveedor mostrado en las listas | Soldaduras y Revestimientos FOCUS, C.A. · RIF J40798318-0 |
| Catálogo estructurado | FabriColor_Catalogo_Maestro_2026.xlsx |
| Alcance | Reglas de datos y negocio; no sustituye inventario físico ni configuración fiscal definitiva |

| **Uso con IA. **Este documento debe usarse como fuente maestra para interpretar productos y reglas comerciales. Los datos de proveedor son datos de origen; no deben convertirse automáticamente en stock o precio público de FabriColor. |
| --- |

# 1. Objetivo y alcance

Este documento define cómo debe entenderse y gestionarse el universo de productos de FabriColor. Consolida la estructura derivada de las listas de proveedor aportadas y establece las reglas necesarias para convertir esas listas en datos útiles para catálogo, compras, inventario, ventas y web.

Preservar el SKU/código del proveedor como identificador de referencia.

Normalizar marca, familia, descripción, presentación, empaque, coste y disponibilidad.

Separar de forma estricta catálogo, abastecimiento e inventario físico.

Separar coste de proveedor, coste real, impuestos, margen y precio de venta.

Permitir venta por unidad y compra por paquete cuando el producto lo requiera.

Preparar la información para búsqueda rápida en POS y catálogo web.

# 2. Fuentes primarias

| **Fuente** | **Contenido soportado por la fuente** | **Observaciones** |
| --- | --- | --- |
| GOODSIF · Lista 06-07-2026 | Tintas poliéster, aluminios, perlas, poliuretanos, transparentes, fondos y misceláneos. | Lista en USD; leyenda de disponibilidad; nota de precios sin IVA; incluye información de llegada en página 2. |
| SYMPLEX / LAKE COUNTRY · Lista 2026 | Compounds, cerámico, restauradores, selladores, pulido y accesorios. | Lista en USD; leyenda 'Sin Fecha Estimada de Llegada'; precios sin IVA. |
| RAPIDCURE · Lista 2026 | Masillas, fibra preparada, uretano, tirro y misceláneos. | Lista en USD; precios sin IVA; disponibilidad sujeta a cambios. |
| KOVAX · Lista 2026 | Lijas, Super Assilex, Super Buflex, Tolecut y accesorios. | Incluye Paquete (UND) y Precio x UND; compra mínima de un paquete según la nota de la lista. |

La documentación no debe inferir disponibilidad exacta a partir de elementos visuales que no hayan sido estructurados de forma fiable. Cuando el dato no esté confirmado, se marcará para revisión.

# 3. Marcas y familias de producto

| **Marca** | **Familias principales en el proyecto** | **Rol** |
| --- | --- | --- |
| GOODSIF | Tintas Poliéster; Aluminios; Perlas; Poliuretanos; Transparentes; Fondos; Misceláneos. | Núcleo de pintura automotriz. FabriColor es agente exclusivo de Goodsif. |
| SYMPLEX | Rubbing Compound; Cerámico; Restauradores; Selladores; otros productos de detailing/pulido. | Acabado, corrección, restauración y protección. |
| RAPIDCURE | Masilla; Fibra Preparada; Uretano; Tirro; Misceláneos. | Preparación y reparación. |
| KOVAX | Lijas al Agua; Lijas al Seco; Super Assilex; Super Buflex; Tolecut; Accesorios. | Abrasivos profesionales. |
| LAKE COUNTRY | Mopas, platos y accesorios. | Accesorios profesionales de pulido. |

# 4. Ejemplos de referencias verificadas en las listas

## 4.1 GOODSIF

| **Código** | **Descripción de origen** | **Precio lista USD** |
| --- | --- | --- |
| MF1K01 | GOODSIF, Blanco, Gal | 54,00 |
| MF1K03 | GOODSIF, Negro, Gal | 54,00 |
| MF1K32 | GOODSIF, Aluminio Extra Fino Blanco, 1/4 | 17,50 |
| MF1K45 | GOODSIF, Perla Blanca Fina, 1/4 | 15,90 |
| MF1K53-Gal | GOODSIF, Perla Azul, Gal | 57,75 |

## 4.2 RAPIDCURE

| **Código** | **Descripción de origen** | **Precio lista USD** |
| --- | --- | --- |
| R653-0_5Kg | RAPIDCURE, Masilla Plástica, 0,5 Kg | 5,00 |
| R653-1Kg | RAPIDCURE, Masilla Plástica, 1 Kg | 8,00 |
| R653-4Kg | RAPIDCURE, Masilla Plástica, 4 Kg | 22,00 |
| RAP11-310ml | RAPIDCURE, Uretano Negro Parabrisas, 310ml | 5,75 |
| R910-1L | RAPIDCURE, Desengrasante, 1L | 7,00 |

## 4.3 KOVAX

| **Código** | **Descripción de origen** | **Paquete** | **Precio x UND USD** |
| --- | --- | --- | --- |
| K-1010060 | KOVAX SFCC Lija Agua 230x280 - Grano P60 | 100 | 0,42 |
| K-1021200 | KOVAX SFAC Lija Agua 230x280 - Grano P1200 | 100 | 0,60 |
| K-1021500 | KOVAX SFAC Lija Agua 230x280 - Grano P1500 | 100 | 0,60 |
| K-1911532 | KOVAX Super Buflex Verde K-2000 | 25 | 1,50 |
| K-1911526 | KOVAX Tolecut Block 8 Cortes Naranja K-1200 | 25 | 1,20 |

## 4.4 SYMPLEX

| **Código** | **Descripción de origen** | **Precio lista USD** |
| --- | --- | --- |
| S-Classic-1/8 | SYMPLEX, Classic Compound, 1/8 | 13,25 |
| S-Classic-Gal | SYMPLEX, Classic Compound, Galón | 56,50 |
| S-Piranha-1/4 | SYMPLEX, Piranha Compound, 1/4 | 26,00 |
| S-Nitro-Gal | SYMPLEX, Nitro Compound, Galón | 99,00 |
| S-Silex-Ceramic-Kit | SYMPLEX, 9H Recubrimiento Cerámico, Kit | 104,00 |

| **Importante. **Los importes anteriores son precios de las listas suministradas, no precios públicos aprobados de FabriColor. |
| --- |

# 5. Modelo maestro de producto

Cada referencia debe existir una sola vez en el catálogo maestro. El registro de producto debe estructurarse por bloques:

| **Bloque** | **Campos mínimos** |
| --- | --- |
| Identidad | SKU/código; marca; familia; descripción de origen; nombre comercial futuro; estado activo/inactivo. |
| Presentación | Presentación; unidad de medida; contenido; paquete (UND); factor de empaque. |
| Abastecimiento | Proveedor; coste base; moneda; compra mínima; disponibilidad proveedor; fecha prevista de llegada. |
| Inventario | Stock físico; reservado; disponible; mínimo; en tránsito; ubicación. |
| Comercial | Coste real; margen; tarifa(s); impuesto configurable; precio neto; precio final. |
| Web | Publicar Sí/No; mostrar precio Sí/Consultar; descripción pública; imágenes; atributos. |
| Control | Fuente; fecha de actualización; usuario; notas; historial. |

# 6. Identificadores y normalización

SKU/código: conservar exactamente el código de origen siempre que sea posible.

Marca: usar un catálogo controlado de marcas, evitando variantes tipográficas que fragmenten reportes.

Familia: utilizar familias normalizadas para filtros, reportes, POS y web.

Descripción de origen: conservar el texto del proveedor como referencia trazable.

Nombre comercial: puede crearse posteriormente para mejorar la experiencia del cliente sin borrar la descripción de origen.

Presentación: estructurar Gal/Galón, 1/4, 1/8, Kg, L, ml, dimensiones y otros formatos en campos reutilizables cuando sea viable.

| **Regla de integridad. **No se debe crear un segundo producto solo porque cambie el precio. El precio pertenece al historial comercial del SKU; la identidad del producto permanece. |
| --- |

# 7. Catálogo no es inventario

Esta distinción es obligatoria en toda la solución. El catálogo responde «qué productos conocemos/vendemos»; el inventario responde «cuánto tenemos físicamente y cuánto está comprometido».

| **Situación** | **Catálogo** | **Inventario** |
| --- | --- | --- |
| SKU conocido, sin existencias | Activo | Stock físico 0 |
| Producto comprado y aún no recibido | Activo | Stock físico no aumenta; cantidad en tránsito sí |
| Producto descontinuado | Puede quedar inactivo para nuevas operaciones | Histórico se conserva |
| Proveedor indica disponibilidad | Dato de abastecimiento | No aumenta stock FabriColor |

Nunca convertir una marca visual de disponibilidad del proveedor en stock físico de FabriColor.

# 8. Modelo de inventario

| **Campo** | **Regla** |
| --- | --- |
| Stock físico | Cantidad registrada como existente físicamente. |
| Stock reservado | Cantidad comprometida y todavía no entregada. |
| Stock disponible | Stock físico - stock reservado. |
| Stock mínimo | Umbral configurable que genera alerta. |
| En tránsito | Cantidad pedida/confirmada aún no recibida. |
| Ubicación | Posición física o almacén cuando se implemente. |

## 8.1 Movimientos permitidos

Entrada por recepción de compra.

Salida por venta/entrega.

Reserva y liberación.

Devolución de cliente.

Devolución a proveedor.

Ajuste positivo/negativo autorizado.

Merma, daño o baja.

Transferencia entre ubicaciones si se habilita multi-almacén.

## 8.2 Registro mínimo de movimiento

ID de movimiento.

SKU.

Cantidad y unidad.

Tipo de movimiento.

Fecha/hora.

Usuario.

Documento origen.

Motivo/observación cuando corresponda.

Ubicación origen/destino si aplica.

# 9. Disponibilidad y abastecimiento

Las listas aportadas utilizan una leyenda de disponibilidad e incluyen el estado «Sin fecha estimada de llegada». La disponibilidad está sujeta a cambios sin previo aviso. El sistema debe almacenar esta información como dato del proveedor.

| **Estado interno propuesto** | **Significado** |
| --- | --- |
| Disponible | FabriColor tiene stock disponible según sus propios registros. |
| Stock bajo | Stock disponible igual o inferior al mínimo configurado. |
| Agotado | Stock disponible igual a cero. |
| En tránsito | Existe compra pendiente de recepción. |
| Sin fecha prevista | Existe necesidad/indisponibilidad y no se dispone de fecha estimada válida. |
| Fecha de llegada indicada | El proveedor ha comunicado una fecha concreta; no equivale a mercancía recibida. |

| **Goodsif. **En la lista aportada se identifica información de llegada del 25-09-2026 para el bloque correspondiente de referencias de la página 2. Esta fecha debe conservarse como fecha prevista del proveedor, nunca como recepción automática. |
| --- |

# 10. Compras por paquete y venta por unidad

Kovax introduce una necesidad explícita: la lista contiene columnas «Paquete (UND)» y «Precio x UND». Por tanto, el modelo no puede asumir que unidad de compra y unidad de venta sean siempre iguales.

| **Concepto** | **Ejemplo funcional** |
| --- | --- |
| Unidad de compra | 1 paquete. |
| Factor de empaque | Ej.: 100 unidades por paquete para determinadas lijas. |
| Coste unitario de lista | Ej.: 0,42 USD por unidad en determinadas referencias. |
| Cantidad pedida | Puede expresarse en paquetes y convertirse a unidades de inventario. |
| Venta interna | FabriColor podrá vender por unidad si su política comercial así lo define. |

La nota de la lista Kovax indica compra mínima de un paquete. El sistema debe validar la compra mínima a nivel de proveedor/SKU sin imponerla necesariamente al cliente final.

# 11. Costes

## 11.1 Capas de coste

**Precio/coste proveedor → gastos adicionales → coste real FabriColor → margen → precio de venta**

Coste proveedor: importe de compra de referencia o recibido.

Gastos adicionales: transporte, importación u otros si FabriColor decide incorporarlos.

Coste real: base para análisis de margen cuando se configure.

El método exacto para distribuir gastos adicionales queda pendiente de decisión.

## 11.2 Historial de costes

Cada actualización de coste debe registrar fecha de vigencia y origen.

No sobrescribir el coste histórico usado por ventas ya confirmadas.

Una recepción puede actualizar el coste vigente y añadir un registro al historial.

El método de valoración de inventario definitivo queda pendiente de decisión.

# 12. Precios, impuestos y márgenes

Las listas de proveedor revisadas indican expresamente que los precios no incluyen IVA.

No añadir una tasa de IVA fija hasta que FabriColor valide la configuración fiscal aplicable.

No publicar automáticamente el coste de proveedor.

Separar precio neto, impuesto y precio final.

Permitir margen objetivo como ayuda de cálculo, pero conservar capacidad de fijar precios manualmente con permisos.

Registrar historial de precio de venta y fecha de vigencia.

## 12.1 Tarifas comerciales previstas

| **Tarifa inicial** | **Uso conceptual** |
| --- | --- |
| Público | Cliente general. |
| Profesional | Profesional recurrente. |
| Taller | Taller con condición comercial. |
| Mayorista | Compra de volumen. |
| Especial | Condición excepcional/autorizada. |

Los nombres y reglas exactas de las tarifas son una propuesta funcional y deberán validarse. Un cliente puede tener una tarifa asignada y, si se permite, descuentos adicionales sujetos a permisos.

# 13. Precio histórico en ventas

| **Regla crítica. **Cada línea de venta confirmada debe guardar el precio vendido y el coste aplicable en ese momento. Los reportes históricos de margen no deben recalcularse con el coste actual. |
| --- |

| **Dato en línea de venta** | **Motivo** |
| --- | --- |
| SKU | Identificar el producto. |
| Descripción snapshot | Preservar cómo se describió en la operación. |
| Cantidad | Calcular volumen. |
| Precio unitario vendido | Preservar la condición comercial real. |
| Descuento | Explicar el precio neto. |
| Impuesto aplicado | Preservar tratamiento fiscal de la operación. |
| Coste histórico unitario | Calcular margen histórico. |

# 14. Búsqueda y descubrimiento de producto

El catálogo debe optimizarse para vendedores y clientes que pueden conocer solo una parte del nombre o la granulometría.

Búsqueda exacta por SKU.

Búsqueda parcial por descripción.

Marca y familia.

Presentación o tamaño.

Granulometría: P60, P1200, P1500, K-2000, etc.

Términos comerciales como «masilla 1kg», «perla blanca», «aluminio fino» o «compound».

Los sinónimos y palabras clave pueden añadirse como campo auxiliar sin modificar la descripción de origen.

# 15. Reglas para la web pública

| **Campo interno** | **Comportamiento web** |
| --- | --- |
| Publicar en web | Sí permite publicación; No mantiene el SKU solo interno. |
| Mostrar precio | Sí muestra tarifa pública autorizada; Consultar oculta importe y muestra llamada a contacto. |
| Stock interno | No exponer automáticamente la cantidad exacta. |
| Disponibilidad pública | Derivar de una regla aprobada: disponible, consultar, agotado, etc. |
| Coste/margen/proveedor | Información interna; no publicar salvo decisión expresa. |

El sistema administrativo debe ser la fuente principal. La web no debe mantener una segunda copia manual independiente del catálogo.

# 16. Datos de origen y trazabilidad

Guardar archivo/fuente de la que procede cada carga o actualización masiva.

Guardar fecha de actualización.

Permitir distinguir dato importado de dato editado internamente.

Conservar notas del proveedor, como precios sin IVA o compra mínima.

Registrar usuario cuando se modifiquen manualmente campos sensibles.

El Catálogo Maestro 2026 generado para el proyecto contiene 255 referencias estructuradas a partir de las cuatro listas y sirve como semilla inicial; antes de una carga productiva debe validarse contra los documentos fuente y el inventario real de FabriColor.

# 17. Importaciones y actualización de listas

Cargar archivo/lista del proveedor.

Detectar SKU existentes y nuevos.

Comparar descripción, presentación, precio, empaque y disponibilidad.

Mostrar diferencias antes de aplicar cambios.

Crear historial para cambios de coste.

No alterar stock físico por una actualización de catálogo/precios.

Aplicar cambios aprobados y registrar fuente/fecha/usuario.

| **Control recomendado. **Una actualización de precios de proveedor debe poder revisarse antes de afectar el coste vigente. Nunca debe cambiar automáticamente precios públicos sin una regla comercial explícita. |
| --- |

# 18. Reglas de integridad del catálogo

SKU único.

Marca obligatoria.

Descripción de origen conservada.

Moneda explícita para todo coste/precio.

No permitir coste o precio sin indicar su naturaleza.

No mezclar unidad, paquete y presentación en un único número ambiguo.

No eliminar físicamente un SKU con historial transaccional; usar estado inactivo.

No transformar una fecha estimada de proveedor en entrada de inventario.

No transformar disponibilidad del proveedor en disponibilidad física de FabriColor.

# 19. Alertas relacionadas con producto e inventario

Stock disponible <= stock mínimo.

Stock disponible = 0.

Mercancía en tránsito próxima a fecha prevista.

Fecha prevista vencida sin recepción.

Producto con coste actualizado pendiente de revisión comercial.

Producto publicado sin precio/tarifa pública cuando la regla exija precio.

Diferencia de inventario pendiente de aprobación.

# 20. Reportes de catálogo e inventario

| **Reporte** | **Contenido** |
| --- | --- |
| Catálogo por marca/familia | SKUs activos, presentaciones y estado. |
| Existencias | Físico, reservado, disponible, mínimo y tránsito. |
| Bajo stock / agotados | Productos que requieren atención. |
| Movimientos | Kardex/historial por SKU y período. |
| Compras y costes | Evolución de coste por proveedor y SKU. |
| Margen | Precio vendido vs coste histórico. |
| Productos sin movimiento | Referencias con baja rotación según período. |
| Publicación web | Productos publicados, ocultos, con precio o bajo consulta. |

# 21. Ejemplos de reglas de negocio

| **ID** | **Regla** |
| --- | --- |
| CAT-01 | No puede existir más de un producto activo con el mismo SKU. |
| CAT-02 | Cambiar el precio del proveedor no crea un nuevo SKU. |
| INV-01 | Una compra confirmada aumenta tránsito, no stock físico. |
| INV-02 | Una recepción aumenta stock físico por la cantidad efectivamente recibida. |
| INV-03 | Una venta/entrega reduce inventario según el flujo aprobado. |
| PRI-01 | El precio público no se deriva automáticamente del coste sin una regla aprobada. |
| PRI-02 | Una venta confirmada conserva coste y precio históricos. |
| SUP-01 | La disponibilidad del proveedor no equivale a disponibilidad de FabriColor. |
| WEB-01 | Solo se publica un SKU cuando Publicar en web = Sí. |
| KOV-01 | La compra de referencias Kovax debe respetar el paquete mínimo configurado cuando corresponda. |

# 22. Pendientes de definición

Inventario físico inicial de FabriColor por SKU.

Stock mínimo por producto/familia.

Ubicaciones físicas y número de almacenes.

Método de valoración de inventario.

Política de costes adicionales.

Margen objetivo por marca/familia/SKU.

Tarifas definitivas y reglas de descuento.

Configuración fiscal e impuestos.

Política de redondeo.

Productos que se venderán por unidad, paquete o ambas modalidades.

Regla exacta de disponibilidad pública en la web.

Códigos de barras, etiquetado y unidades logísticas.

# 23. Criterios de aceptación

Cada SKU puede identificarse de forma inequívoca por código, marca, familia y descripción.

El sistema distingue stock físico, reservado, disponible y en tránsito.

Actualizar una lista de proveedor no modifica el stock físico.

Una recepción parcial actualiza correctamente recibido, pendiente y tránsito.

Las referencias con empaque pueden manejar factor de paquete y coste unitario.

Los precios de proveedor permanecen separados del precio público.

Una venta histórica conserva su coste y precio aunque cambien posteriormente.

La búsqueda encuentra referencias por código y términos relevantes.

La web solo recibe los productos y campos autorizados.

Todo cambio sensible mantiene trazabilidad suficiente.

# 24. Instrucciones para ChatGPT / Claude

Usar las listas de proveedor y este documento como fuente para datos de producto; no completar precios o códigos de memoria.

No afirmar stock real de FabriColor si no existe un inventario físico actualizado.

No tratar 'sin fecha estimada de llegada' como 'agotado en FabriColor' sin evidencia adicional.

No convertir precios de lista en precios de venta.

No fijar IVA, margen, redondeo o valoración de inventario sin una decisión documentada.

Preservar los códigos de producto y la descripción de origen.

Distinguir siempre hechos de fuente, decisiones aprobadas y propuestas nuevas.

Cuando se proponga una nueva familia/categoría, explicar cómo se mapeará a las referencias existentes.

Si una lista nueva contradice una anterior, conservar el histórico y pedir/aplicar una regla de vigencia; no borrar silenciosamente el dato anterior.

# 25. Relación con los otros documentos maestros

| **Documento** | **Relación** |
| --- | --- |
| 01 — Visión, contexto y alcance | Define negocio, objetivos y alcance global. |
| 02 — Especificación funcional | Define cómo los módulos usan estos productos y reglas. |
| 03 — Catálogo, productos, inventario y reglas comerciales | Este documento: semántica de producto y reglas de datos. |
| 04 — Web y UX/UI | Definirá cómo se presentan y encuentran los productos públicamente. |
| 05 — Especificación técnica y guía IA | Definirá modelo técnico, APIs, seguridad e implementación. |

# 26. Anexo: diccionario funcional resumido

| **Término** | **Definición operativa** |
| --- | --- |
| SKU | Código único de referencia del producto. |
| Presentación | Formato comercial del producto: Gal, 1/4, 1/8, Kg, L, ml, etc. |
| Paquete (UND) | Número de unidades contenido en el paquete de compra cuando aplique. |
| Coste proveedor | Precio de compra/referencia de la lista o recepción. |
| Coste histórico | Coste almacenado para una operación pasada. |
| Stock físico | Cantidad registrada físicamente. |
| Stock reservado | Cantidad comprometida. |
| Stock disponible | Físico menos reservado. |
| En tránsito | Cantidad comprada pendiente de recepción. |
| Tarifa | Conjunto de precios aplicable a un tipo de cliente. |
| Disponibilidad proveedor | Información externa de abastecimiento; no es stock FabriColor. |

**FIN DEL DOCUMENTO 03**

Documento 03 · Catálogo, productos, inventario y reglas comerciales · Agosto 2026