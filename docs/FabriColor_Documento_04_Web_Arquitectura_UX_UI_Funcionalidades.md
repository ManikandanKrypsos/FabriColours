**FABRICOLOR  |  DOCUMENTACIÓN MAESTRA DEL PROYECTO**

**DOCUMENTO 04 / 05**

**FabriColor**

**Web: arquitectura, UX/UI y funcionalidades**

Especificación de la experiencia pública, estructura de contenidos, catálogo, búsqueda e integración con el sistema administrativo.

| **Campo** | **Definición** |
| --- | --- |
| Negocio | FabriColor — Ciudad Bolívar, Venezuela |
| Rol de la web | Escaparate comercial y acceso al catálogo público |
| Relación con el back office | La web consume datos autorizados desde el sistema administrativo |
| Dirección visual | Moderna, profesional, sobria; gris/negro como base |

| **Principio rector. **La web no debe convertirse en una segunda base de datos independiente. Producto, precio y disponibilidad deben administrarse desde el sistema central y publicarse mediante reglas controladas. |
| --- |

# 1. Objetivo de la web

La web de FabriColor debe presentar el negocio con una imagen profesional, facilitar el descubrimiento de productos y marcas, ayudar a clientes particulares y profesionales a encontrar referencias y generar oportunidades comerciales. Debe reflejar la especialización de FabriColor en pintura automotriz y materiales asociados.

Transmitir confianza, especialización y profesionalidad.

Dar protagonismo a Goodsif y comunicar correctamente que FabriColor es agente exclusivo de la marca.

Presentar el resto de marcas y familias del catálogo de forma ordenada.

Permitir encontrar productos por código o necesidad, no solo navegando por marca.

Facilitar contacto y consulta comercial.

Preparar la plataforma para capacidades transaccionales futuras si se aprueban.

# 2. Audiencias

| **Audiencia** | **Necesidad principal** |
| --- | --- |
| Particular | Encontrar productos, entender qué ofrece FabriColor y contactar. |
| Pintor / chapista | Buscar rápidamente referencias, abrasivos, pinturas y complementos. |
| Taller | Consultar catálogo, disponibilidad comercial y condiciones profesionales. |
| Empresa / flota | Conocer oferta y establecer relación comercial. |
| Cliente recurrente | Llegar directamente a productos/categorías y contactar con rapidez. |

La web debe ser comprensible para un usuario no experto, pero suficientemente eficiente para profesionales que conocen códigos, granos o nombres concretos.

# 3. Propuesta de valor y mensajes

Especialización en pintura automotriz y materiales profesionales.

FabriColor como agente exclusivo de Goodsif.

Catálogo complementario de abrasivos, preparación, pulido y detailing.

Atención local en Ciudad Bolívar.

Capacidad de orientar al cliente hacia la referencia adecuada.

| **Pendiente. **Los claims publicitarios definitivos, garantías, tiempos de entrega y promesas comerciales deben aprobarse antes de publicarse. La IA no debe inventarlos. |
| --- |

# 4. Arquitectura de información

Estructura pública propuesta para la primera versión:

| **Nivel principal** | **Contenido** |
| --- | --- |
| Inicio | Propuesta de valor, categorías, Goodsif, marcas, búsqueda y contacto. |
| Productos | Catálogo completo autorizado para publicación. |
| Pintura automotriz | Tintas, aluminios, perlas, poliuretanos, transparentes, fondos y complementos. |
| Preparación y reparación | Masillas, fibra, uretanos, tirro y productos relacionados. |
| Abrasivos | Lijas al agua/seco, Assilex, Buflex, Tolecut y accesorios. |
| Pulido y detailing | Compounds, restauradores, selladores, cerámicos, mopas y accesorios. |
| Marcas | Goodsif, Symplex, RapidCure, Kovax y Lake Country. |
| Profesionales | Información comercial para talleres/profesionales; alcance exacto pendiente. |
| Nosotros | FabriColor, ubicación y posicionamiento. |
| Contacto | Canales, ubicación y formulario/acción de contacto. |

# 5. Navegación principal

La navegación debe ser corta y predecible. Propuesta inicial:

**Inicio  |  Productos  |  Marcas  |  Profesionales  |  Nosotros  |  Contacto**

El acceso a Productos debe permitir desplegar categorías sin saturar el menú.

El buscador debe estar visible en escritorio y fácilmente accesible en móvil.

Contacto debe permanecer a uno o dos toques desde cualquier página.

El menú móvil debe priorizar búsqueda, productos y contacto.

# 6. Página de Inicio

## 6.1 Hero

Identidad FabriColor clara.

Mensaje corto sobre especialización en pintura automotriz.

Llamada principal a explorar productos o buscar una referencia.

Llamada secundaria a contactar.

Visual relacionado con automoción/pintura sin sobrecargar la composición.

## 6.2 Bloques recomendados

Hero principal.

Buscador de productos/referencias.

Categorías principales.

Bloque destacado Goodsif — FabriColor como agente exclusivo.

Marcas disponibles.

Productos o familias destacadas, controlados desde administración.

Sección para profesionales/talleres.

Ubicación y contacto.

Footer completo.

No llenar la portada con cientos de referencias. Su función es orientar al usuario hacia búsqueda, categorías y propuesta de valor.

# 7. Catálogo público

El catálogo público se genera a partir de SKUs autorizados desde el sistema administrativo.

## 7.1 Categorías de navegación

| **Categoría pública** | **Contenido orientativo** |
| --- | --- |
| Pintura automotriz | GOODSIF: tintas poliéster, aluminios, perlas, poliuretanos, transparentes, fondos y complementos. |
| Preparación y reparación | RAPIDCURE y referencias equivalentes futuras. |
| Abrasivos | KOVAX: agua, seco, Assilex, Buflex, Tolecut y accesorios. |
| Pulido y detailing | SYMPLEX y LAKE COUNTRY: compounds, restauración, sellado, cerámico, mopas y platos. |

La taxonomía pública puede ser más amigable que la familia interna, pero debe existir un mapeo explícito entre ambas.

# 8. Búsqueda de productos

La búsqueda es una función central porque muchos usuarios profesionales llegan con un código, granulometría o término parcial.

Código/SKU exacto: MF1K32, R653-1Kg, K-1021200, etc.

Nombre o descripción parcial.

Marca.

Categoría/familia.

Presentación: Gal, 1/4, 1 Kg, 310 ml, etc.

Granulometría o característica: P1200, P1500, K-2000.

Términos naturales: «perla blanca», «masilla 1kg», «aluminio fino», «compound».

## 8.1 Resultados

Imagen si existe.

Nombre comercial/descripcion autorizada.

Marca.

SKU.

Presentación.

Estado público de disponibilidad.

Precio público autorizado o texto «Consultar».

Acción Ver producto / Consultar.

El coste, margen, proveedor y stock interno exacto no deben aparecer en resultados públicos.

# 9. Ficha de producto

| **Bloque** | **Contenido** |
| --- | --- |
| Identificación | Nombre, marca, SKU y categoría. |
| Visual | Imagen(es) del producto cuando estén disponibles. |
| Presentación | Tamaño/formato y atributos relevantes. |
| Descripción | Texto comercial aprobado; conservar internamente la descripción de origen. |
| Disponibilidad | Estado público derivado de reglas del sistema. |
| Precio | Tarifa pública aprobada o «Consultar». |
| Acción | Consultar/contactar; futura compra online solo si se aprueba. |
| Relacionados | Productos de la misma familia o complementarios mediante reglas futuras. |

| **Privacidad comercial. **Nunca publicar automáticamente coste proveedor, coste real, margen, límites de stock, notas internas ni condiciones privadas de clientes. |
| --- |

# 10. Página de marca: Goodsif

Goodsif merece un tratamiento destacado por la relación comercial definida: FabriColor es agente exclusivo de Goodsif. La página debe presentar la marca y permitir navegar por sus familias sin confundir la identidad de FabriColor con la de Goodsif.

Encabezado de marca.

Texto sobre la relación FabriColor–Goodsif aprobado por el negocio.

Acceso a tintas poliéster, aluminios, perlas, poliuretanos, transparentes, fondos y misceláneos.

Buscador/filtro dentro de la marca.

Productos destacados controlados desde administración.

No afirmar características técnicas, certificaciones o prestaciones de Goodsif que no estén soportadas por documentación aprobada.

# 11. Otras páginas de marca

| **Marca** | **Orientación** |
| --- | --- |
| Symplex | Pulido, compounds, restauración, sellado y cerámico. |
| RapidCure | Preparación y reparación. |
| Kovax | Abrasivos profesionales y sistemas Assilex/Buflex/Tolecut. |
| Lake Country | Mopas, platos y accesorios de pulido. |

Cada página debe reutilizar el mismo sistema visual y filtrar el catálogo por marca.

# 12. Sección Profesionales

Se reserva una sección específica para talleres, pintores/chapistas, empresas y flotas.

Presentar la capacidad de FabriColor para atender clientes profesionales.

Formulario o acción de contacto comercial.

Posibilidad futura de acceso/condiciones profesionales si se decide crear un portal de cliente.

No mostrar públicamente tarifas privadas ni límites de crédito.

| **Pendiente. **No está aprobado todavía un portal autenticado B2B ni compra online profesional. La arquitectura debe permitir añadirlo sin asumir que forma parte de la primera versión. |
| --- |

# 13. Nosotros y ubicación

Nombre: FabriColor.

Ubicación: Ciudad Bolívar, Venezuela.

Descripción del negocio y especialización.

Relación de agente exclusivo de Goodsif.

Fotografías reales de la tienda aportadas al proyecto como recurso visual.

Mapa, dirección exacta y horarios únicamente cuando hayan sido confirmados.

En el trabajo visual inicial se aportaron fotografías del establecimiento. Deben preferirse imágenes reales del negocio frente a recursos genéricos cuando sean adecuadas.

# 14. Contacto y conversión

La web debe convertir búsquedas de producto en conversaciones comerciales con el mínimo esfuerzo.

Teléfono y/o WhatsApp cuando los datos oficiales se confirmen.

Formulario de contacto.

Consulta desde una ficha de producto incluyendo automáticamente SKU y nombre.

Ubicación/mapa cuando se confirme la dirección exacta.

Correo comercial cuando se defina.

Los canales concretos no deben inventarse en prototipos destinados a producción.

# 15. Dirección visual

La dirección ya definida es moderna y profesional, sin exageración. La identidad utiliza gris y negro como base. En exploraciones iniciales se han considerado el Puente del Orinoco, una pistola de pintura, latas de pintura y automóviles como referencias visuales para el logo/web.

| **Elemento** | **Dirección** |
| --- | --- |
| Paleta base | Negro, grafito, gris y blanco. |
| Color de acción | Un acento controlado; rojo se ha usado como dirección de interfaz/documentación, pendiente de consolidación de identidad final. |
| Tipografía | Sans serif moderna, legible y profesional. |
| Fotografía | Tienda real, producto y automoción; evitar stock genérico cuando existan recursos propios. |
| Iconografía | Simple, técnica y consistente. |
| Espaciado | Generoso; evitar densidad de ERP en la web pública. |

| **Logo. **Los elementos visuales sugeridos no obligan a incluirlos todos simultáneamente. La prioridad es un logo reconocible y limpio, no una ilustración compleja. |
| --- |

# 16. Responsive y experiencia móvil

Diseño mobile-first o, como mínimo, equivalencia funcional completa en móvil.

Buscador accesible sin abrir múltiples menús.

Filtros de catálogo adaptados a panel/desplegable móvil.

Botones de contacto suficientemente grandes.

Ficha de producto con información priorizada y sin tablas anchas innecesarias.

Imágenes optimizadas para redes móviles.

La mayoría de las acciones comerciales clave —buscar, ver producto y contactar— deben poder completarse cómodamente desde un teléfono.

# 17. Estados de disponibilidad públicos

El estado público debe ser más simple que el estado administrativo.

| **Estado interno** | **Posible representación pública** |
| --- | --- |
| Disponible | Disponible / Consultar disponibilidad, según política. |
| Stock bajo | Últimas unidades o Consultar, si se aprueba mostrarlo. |
| Agotado | Agotado / Consultar reposición. |
| En tránsito | Próximamente / Consultar fecha. |
| Sin fecha prevista | Consultar. |
| Fecha de llegada indicada | Próximamente, si la fecha sigue vigente y se decide publicar. |

La tabla anterior propone opciones de UX, no textos comerciales aprobados. La regla exacta se configurará antes de producción.

# 18. Integración con el sistema administrativo

Campos que el back office debe poder controlar para la web:

| **Control administrativo** | **Efecto** |
| --- | --- |
| Publicar en web Sí/No | Incluye o excluye el producto. |
| Mostrar precio Sí/Consultar | Controla la exposición del importe. |
| Tarifa pública | Define qué precio puede consumir la web. |
| Categoría web | Define navegación pública. |
| Descripción web | Texto comercial independiente de la descripción de proveedor. |
| Imágenes | Galería autorizada. |
| Destacado | Permite promociones editoriales sin alterar catálogo. |
| Estado público | Derivado de reglas de disponibilidad aprobadas. |

La implementación técnica de API, caché y sincronización corresponde al Documento 05.

# 19. Funcionalidades excluidas de la V1 salvo aprobación

Checkout/e-commerce completo.

Pago online.

Cuenta autenticada de cliente.

Portal B2B con precios privados.

Reserva online de stock.

Marketplace de terceros.

Formulación de color pública.

Promesas automáticas de fecha de entrega.

La arquitectura no debe bloquear estas funciones futuras, pero tampoco debe aumentar innecesariamente el alcance de la primera versión.

# 20. SEO y contenido estructural

URLs legibles para categorías, marcas y productos.

Título y descripción SEO editables.

Jerarquía correcta de encabezados.

Texto descriptivo propio para categorías/marcas cuando se apruebe.

Datos estructurados de producto cuando sean técnicamente y comercialmente apropiados.

Sitemap y control de indexación.

Rendimiento e imágenes optimizadas.

| **Contenido. **No generar afirmaciones técnicas de productos únicamente para llenar SEO. La información técnica debe provenir de fuentes aprobadas. |
| --- |

# 21. Accesibilidad y calidad

Contraste suficiente.

Navegación por teclado en componentes esenciales.

Etiquetas accesibles en formularios.

Texto alternativo en imágenes significativas.

Mensajes de error comprensibles.

No depender exclusivamente del color para comunicar disponibilidad.

# 22. Analítica y eventos

La herramienta analítica concreta queda pendiente, pero la web debería poder medir:

Búsquedas realizadas.

Búsquedas sin resultados.

Vistas de producto.

Filtros/categorías más usados.

Clics de contacto desde producto.

Clics en teléfono/WhatsApp cuando se habiliten.

Conversión de formularios.

Estos datos pueden ayudar posteriormente a decidir stock, contenido y productos destacados.

# 23. Wireframes funcionales textuales

## 23.1 Inicio

[HEADER: Logo | Productos | Marcas | Profesionales | Nosotros | Contacto | Buscar]
[HERO: mensaje principal + CTA Explorar productos + CTA Contactar]
[BUSCADOR: “Busca por código, producto o marca”]
[CATEGORÍAS: Pintura | Preparación | Abrasivos | Pulido]
[GOODSIF: bloque destacado agente exclusivo]
[MARCAS]
[PRODUCTOS/FAMILIAS DESTACADAS]
[PROFESIONALES]
[UBICACIÓN + CONTACTO]
[FOOTER]

## 23.2 Catálogo

[HEADER]
[TÍTULO + BUSCADOR]
[FILTROS: Marca | Categoría | Presentación | Disponibilidad]
---------------------------------------------------------
| FILTROS | Producto | Producto | Producto              |
|         | Producto | Producto | Producto              |
---------------------------------------------------------
[PAGINACIÓN / CARGAR MÁS]
[FOOTER]

## 23.3 Producto

[HEADER]
[MIGAS DE PAN]
[GALERÍA]     [Marca]
              [Nombre del producto]
              [SKU + presentación]
              [Estado público]
              [Precio o CONSULTAR]
              [CTA CONSULTAR]
[DESCRIPCIÓN / ATRIBUTOS]
[PRODUCTOS RELACIONADOS]
[FOOTER]

# 24. Reglas de UX

No obligar al usuario a conocer la estructura interna del catálogo.

Mantener búsqueda disponible en todas las páginas de catálogo.

No mostrar filtros sin datos.

No mezclar coste y precio.

No mostrar códigos internos distintos del SKU público sin necesidad.

No ocultar el SKU: para el profesional puede ser el dato más importante.

Una consulta desde producto debe transportar el SKU para evitar ambigüedad.

Cuando no haya precio, usar una acción clara de consulta en lugar de dejar el campo vacío.

# 25. Criterios de aceptación de la web

Un usuario puede llegar desde Inicio a cualquier categoría principal en pocos pasos.

La búsqueda encuentra un producto por SKU exacto.

La búsqueda admite términos parciales y atributos relevantes.

Cada producto público procede de un SKU autorizado por administración.

Un producto configurado como No publicar no aparece públicamente.

Un producto configurado como Consultar no expone un precio.

La web no muestra coste, margen ni información administrativa.

La experiencia esencial funciona correctamente en móvil.

Las consultas desde ficha identifican el producto/SKU.

La información pública de disponibilidad sigue la regla aprobada y no confunde stock interno con disponibilidad de proveedor.

# 26. Contenido pendiente de proporcionar/confirmar

Logo definitivo y variantes.

Dirección física exacta.

Horarios.

Teléfono y WhatsApp oficiales.

Correo comercial.

Redes sociales oficiales.

Textos corporativos definitivos.

Imágenes de producto y permisos de uso.

Política de privacidad, cookies y textos legales aplicables.

Política de precios públicos.

Reglas finales de disponibilidad.

# 27. Instrucciones para ChatGPT / Claude

No rediseñar la arquitectura completa sin explicar qué decisión aprobada se modifica.

No confundir FabriColor con Goodsif.

Mantener a Goodsif como marca destacada por la condición de agente exclusivo.

No inventar dirección, teléfono, horario, redes sociales, claims o datos técnicos.

No convertir la V1 en e-commerce salvo instrucción explícita.

No exponer costes, márgenes, proveedor ni stock interno.

Usar el catálogo maestro y Documento 03 para nombres, códigos y familias.

Cuando proponga copy comercial nuevo, marcarlo como propuesta hasta aprobación.

Priorizar una experiencia moderna, sobria, rápida y profesional.

Diseñar pensando tanto en cliente particular como en profesional que busca por SKU.

# 28. Relación con los demás documentos

| **Documento** | **Responsabilidad** |
| --- | --- |
| 01 — Visión, contexto y alcance | Identidad del negocio y objetivos. |
| 02 — Especificación funcional | Operación del sistema administrativo. |
| 03 — Catálogo, productos e inventario | Fuente de semántica y reglas de producto. |
| 04 — Web, arquitectura y UX/UI | Este documento: experiencia pública. |
| 05 — Especificación técnica y guía IA | Arquitectura técnica, datos, APIs, seguridad y guía de implementación. |

**FIN DEL DOCUMENTO 04**

Documento 04 · Web, arquitectura de información, UX/UI y funcionalidades · Agosto 2026