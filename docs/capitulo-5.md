# Capítulo V: Solution UI/UX Design

## 5.1. Style Guidelines

El Diseño de Producto representa un proceso integral y multidisciplinario que abarca desde la concepción inicial hasta la implementación y comercialización de una solución, combinando principios de ingeniería, diseño centrado en el usuario y estrategia de negocio. Su finalidad es desarrollar productos que no solo sean técnicamente robustos y comercialmente sostenibles, sino también profundamente alineados con las expectativas, hábitos y contextos reales de los usuarios. Este enfoque comienza con un análisis detallado de los problemas, motivaciones y puntos críticos en la experiencia del usuario, y avanza hacia la formulación de soluciones que equilibren funcionalidad, estética, viabilidad técnica y valor percibido. Se diseñan arquitecturas lógicas que conectan requerimientos funcionales con patrones de uso reales, definiendo experiencias intuitivas y eficientes.

En el ámbito digital, esto implica el desarrollo sistemático de la arquitectura de la información, la definición de flujos de interacción optimizados (UX), y la construcción de interfaces gráficas coherentes (UI), considerando principios como accesibilidad, consistencia visual, carga cognitiva y rendimiento del sistema. Según Zeldman (2024), esta integración no solo mejora la navegabilidad y la eficiencia en el consumo de recursos, sino que también garantiza productos escalables, sostenibles y preparados para adaptarse a entornos cambiantes y ciclos de mejora continua.

### 5.1.1. General Style Guidelines

En esta sección se describe el sistema integral de Style Guidelines que abarca todas las plataformas del proyecto: web, móvil (Android e iOS) e interfaces gráficas y modelo físico de dispositivos IoT. Estas guías establecen un marco normativo que garantiza una experiencia de usuario coherente, accesible y visualmente armonizada en todos los entornos, promoviendo la consistencia en la interacción y presentación del sistema.

El diseño se basa en principios de usabilidad, accesibilidad y diseño centrado en el usuario. Se definen paletas cromáticas con jerarquías claras, tipografías legibles con identidad visual y distintos modelos de espaciados, iconografía funcional y componentes reutilizables. Todo ello está alineado bajo una lógica unificada que minimiza la carga cognitiva y mejora la comprensión del usuario, sin elementos gráficos redundantes o distractores.

Más allá del aspecto visual, estas guías fortalecen la escalabilidad y mantenibilidad del sistema. Tal como señala Zeldman (2024), una guía de estilos bien estructurada facilita la colaboración entre diseño y desarrollo, agiliza la evolución del producto y asegura una experiencia consistente, profesional y técnicamente robusta.

#### 5.1.1.1. Colores

El uso del color en el diseño de interfaces va más allá de lo meramente estético y se mantiene como un parámetro estratégico capaz de afinar tanto la eficiencia perceptiva como la respuesta emocional del usuario. Estudios recientes han señalado que los esquemas basados en verdes suaves, en contraste con blancos o grises neutros, optimizan la localización de objetivos y reducen errores de identificación incluso bajo alta carga cognitiva (Westland & Maggio, 2023). 

En MaceTech, la paleta cromática se fundamenta en un verde de baja saturación que refuerza la temática biotecnológica y ecológica de la aplicación. Este verde principal se combina con dos colores neutros estratégicos: el blanco puro, que se utiliza en zonas de descanso visual como espacios informativos y pantallas de lectura, y el gris medio, que organiza los elementos sin llamar demasiado la atención. Esta combinación crea un contraste visual equilibrado que mejora la legibilidad y disminuye la fatiga ocular. Gracias al uso predominante del blanco, el verde resalta como color de barras de navegación, acción en botones, íconos y estados de éxito, lo que puede reducir hasta en un 30 % el tiempo que los usuarios tardan en confirmar tareas importantes (Guo et al., 2025).

Para el modelo hemos seleccionado una paleta base y primaria compuesta por tres tonalidades principales, seleccionadas con precisión para transmitir una identidad visual coherente, moderna y profesional. Además, se ha desarrollado una paleta extendida con cuatro variantes análogas y complementarias para el blanco y gris, que aporta versatilidad para adaptar el diseño a distintos entornos de uso, como plataformas web, aplicaciones móviles y materiales gráficos. Finalmente, hemos agregado otros seis colores adicionales para distintos contextos relacionados a métricas y otras funcionalidades, los cuales brindan soporte al resto de colores al ser intuitivos y llamativos. Este enfoque garantiza una estética consistente, accesible y funcional en todos los puntos de contacto, fortaleciendo la experiencia del usuario e incrementando el reconocimiento visual de la marca.

A continuación, se detallan los colores primarios, secundarios y terciarios definidos para el sistema:

**Color primario:**

###### Figura 30 y algo
*Listado de colores primarios que se usaran en las aplicaciones de Macetech*

<img src="/assets/img/capitulo-5/style-guidelines/colors/light-mode/primary-color-light-mode.png" alt="Listado de todos los colores primarios que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

El verde es la piedra angular de Macetech porque conecta directamente con la naturaleza, el crecimiento y la salud de las plantas, al mismo tiempo que sugiere innovación tecnológica. Desde el punto de la experiencia del usuario y su percepción, el verde equilibra la respuesta emocional, puesto que relaja la corteza visual y facilita la concentración en los datos de los sensores, reduciendo la fatiga ocular en entornos de uso prolongado (Wang et al., 2025). Asimismo, al seguir las recomendaciones de accesibilidad WCAG 2.1, los tonos escogidos garantizan contraste suficiente para usuarios con baja visión sin sacrificar la riqueza del matiz verde primario (World Wide Web Consortium, 2025). Estos colores no deberían ocupar más del 45% de la pantalla del usuario.

Para mantener coherencia y jerarquía visual, cada tono cumple un rol bien definido. A continuación se describe dónde y por qué se usa cada uno:

###### Tabla 30 y algo
*Descripción de usos y justificación para cada uno de los tonos del color primario de Macetech*

| Nombre	| Hex	| Uso principal |	Porcentaje de uso | Justificación técnica |
|---------|-----|---------------|-------------------|----------------------|
| Verde Bosque |	#296244	| Utilizado en la barra de navegación, encabezados, paneles | 50% con respecto a todos los colores primarios | Ofrece máxima legibilidad y anclaje visual, con un contraste mayor a 7:1 (7.17:1) con el color blanco, el cual se utilizara para la tipografía |
| Verde Hoja | #2A8050 |	Utilizado en los botones principales y en los enlaces destacados | 25% con respecto a todos los colores primarios | Es bueno para un acento de interacción, con un contraste de 4.48:1 con respecto al color blanco, lo que cumple WCAG AA para texto normal y WCAG AAA para texto grande o en negrita. Guía la atención sin saturar |
| Verde Brote | #38865D | Utilizado en iconos y en estados hover/activo	| 25% con respecto a todos los colores primarios | Otorga un feedback visual y llama la mirada a acciones secundarias manteniendo armonía con las funciones primarias |

  * **Jerarquía visual:** el tono más oscuro (“Verde Bosque”) sostiene la estructura, mientras que los más claros indican niveles de interacción para el usuario, reduciendo la carga cognitiva al distinguir zonas estáticas de dinámicas.

  * **Consistencia de marca:** los tres verdes comparten la misma temperatura de color, evitando derivaciones que confundan al usuario sobre la identidad de la plataforma (Wheeler y Meyerson, 2024).

  * **Accesibilidad:** todos los contrastes han sido validados según WCAG 2.1 para asegurar cumplimiento AA/AAA en texto y elementos interactivos, protegiendo a usuarios con deficiencias visuales .

**Color secundario:**

###### Figura 30 y algo
*Listado de colores secundarios que se usaran en las aplicaciones de Macetech*

<img src="/assets/img/capitulo-5/style-guidelines/colors/light-mode/secondary-color-light-mode.png" alt="Listado de todos los colores secundarios que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

Los colores secundarios en Macetech cumplen la función de “lienzo” y soporte de contenido, al ofrecer un fondo neutro que potencia la legibilidad de los elementos primarios (verdes) y de los indicadores de estado, sin competir visualmente con ellos. El blanco puro garantiza máximo contraste y limpieza, mientras que los tonos grises aportan confort visual y mantienen jerarquía respecto a las barras de navegación y componentes verdes (Westland y Maggio, 2025). 

Además, estos tonos neutros facilitan el enfocado en los datos y reducen la fatiga ocular durante sesiones prolongadas, cumpliendo las recomendaciones de accesibilidad WCAG 2.1 (World Wide Web Consortium, 2025). Estos colores secundarios no deberían ocupar más del 40% de la pantalla del usuario.

###### Tabla 30 y algo
*Descripción de usos y justificación para cada uno de los tonos del color secundario de Macetech*

| Nombre | Hex | Uso principal | Porcentaje de uso |Justificación técnica |
|--------|-----|---------------|-------------------|----------------------|
| Blanco |	#FFFFFF	| Utilizado en área de contenido y página base | 50% con respecto a todos los colores secundarios | El blanco puro maximiza contraste con los colores primarios y ofrece un ratio mayor a 4.5:1 con texto primario y secundarios | 
| Blanco Cálido | 	#F4F4F5 | Utilizado en tarjetas y paneles secundarios	| 25% con respecto a todos los colores secundarios | El gris claro mantiene la armonía al separar componentes sin generar excesivo ruido visual para los usuarios |
| Blanco Frío |	#E4E4E7	| Utilizado en líneas de separación y contornos de inputs	| 12.5% con respecto a todos los colores secundarios| Mantiene un tono sutil que cumple con las bases del Non‑Text Contrast (WCAG 1.4.11), puesto que no interfiere con la identificación de componentes, pero define límites |
| Gris Suave | #6B7280 | Labels, descripciones	| 12.5% con respecto a todos los colores secundarios| Proveé un contraste mayor a 4.5:1 sobre sus respectivos fondos, además de garantizar lectura de información de menor jerarquía sin competir con texto principal | 

* **Jerarquía visual:** Los neutrales crean un lienzo donde los verdes primarios destacan con claridad, evitando distracciones y enfocando la atención en la información clave.

* **Consistencia:** Todos los secundarios comparten matices grises con la misma temperatura de color, garantizando que posibles transiciones entre diseños light y dark sea fluida y predecible (Zeldman, 2024).

* **Accesibilidad:** Cada token ha sido validado contra WCAG 2.1 (niveles AA/AAA) para asegurar lectura cómoda y separación de componentes interactivos, protegiendo a usuarios con dificultades visuales.

**Color terciario:**

###### Figura 30 y algo
*Listado de colores terciarios que se usaran en las aplicaciones de Macetech*

<img src="/assets/img/capitulo-5/style-guidelines/colors/light-mode/tertiary-color-light-mode.png" alt="Listado de todos los colores terciarios que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

Para asegurar que los datos de nuestros sensores IoT sean fáciles de interpretar de un vistazo, definimos una paleta de colores terciarios específicamente orientada a la visualización de métricas. Cada tono ha sido elegido no solo por su carácter semántico (asociación intuitiva con humedad, luz, temperatura, pH y salinidad), sino también por su rendimiento en términos de contraste y accesibilidad, tanto en entornos de alta luminosidad como en ambientes oscuros. Esta estrategia refuerza la consistencia de la interfaz y facilita la rápida identificación de cada variable sin necesidad de etiquetas adicionales (Westland y Maggio, 2023).

Su objetivo es garantizar que cada variable sea inmediatamente reconocible, con contrastes validados según WCAG 2.1 y una temperatura de color coherente con nuestros verdes primarios. Aseguramos que las gráficas, barras e indicadores destaquen con claridad, mejorando la experiencia de usuario y la precisión en la lectura de datos. Estos colores terciarios no deberían ocupar más del 10% de la pantalla del usuario.

###### Tabla 30 y algo
*Descripción de usos y justificación para cada uno de los tonos del color terciario de Macetech*

| Métrica	| Nombre | Hex | Uso	|Justificación técnica |
|---------|--------|-----|------|----------------------|
| Humedad	y Temperatura Frío | Azul Mar |	#3498DB	| Utilizado en barras/áreas de visualización de humedad	y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Sigue una base de paleta categórica: azul es convencional para humedad, alto contraste con fondo y consistente con dashboards de las métricas IoT |
| Luz	| Mostaza |	#F1C40F	|	Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas | El amarillo brillante remite al sol, además de ser legible sobre gris oscuro y blanco |
| Temperatura Medio	| Brasas |	#E67E22	| Utilizado para mostrar el rango medio de temperatura | Naranja medio comunica calor moderado, siendo una diferenciación clara entre rangos |
| Temperatura Alto | Tomate | #E74C3C | Utilizado para mostrar el	rango alto de temperatura	| Rojo intenso para alertas de calor, puesto que es una semántica cultural de peligro. Asimismo, tiene un contraste AAA con colores blancos |
| pH	| Tallo |	#2ECC71	| Utilizado como medidor de acidez/alcalinidad (pH)	| Verde para pH neutro/seguro, lo que armoniza con primarios y tiene un contraste 4.5:1.
| Salinidad |	Neblina |	#1ABC9C	| Utilizado como medidor de salinidad | Tonos turquesa evocan agua salada, lo que es distintivo frente a otros sensores. |

* **Jerarquía visual:** Los neutrales crean un lienzo donde los verdes primarios destacan con claridad, evitando distracciones y enfocando la atención en la información clave.

* **Consistencia:** Todos los secundarios comparten matices grises con la misma temperatura de color, garantizando que la transición entre light y dark sea fluida y predecible.

* **Accesibilidad:** Cada token ha sido validado contra WCAG 2.1 (niveles AA/AAA) para asegurar lectura cómoda y separación de componentes interactivos, protegiendo a usuarios con dificultades visualesl.

**Dark-mode:**

En Dark‑Mode adaptamos cada tono para asegurar contraste, confort visual y consistencia con el fondo gris suave #343541 al que cambiara la pantalla. Siguiendo WCAG 2.1 y prácticas de accesibilidad, evitamos blancos o negros puros y saturaciones excesivas que fatiguen la vista.

<img src="/assets/img/capitulo-5/style-guidelines/colors/dark-mode/primary-color-dark-mode.png" alt="Listado de todos los colores primarios en modo dark que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

###### Tabla 30 y algo
*Descripción de usos y justificación para cada uno de los tonos del color primario de Macetech en Modo Dark*
   
| Light‑Mode | Light-Mode Hex | Dark‑Mode | Dark-Mode Hex | Uso en Dark‑Mode | Justificación |
|------------|----------------|-----------|---------------|------------------|---------------|
| Verde Bosque | #296244 | Verde Pino |	#1B3326	| Utilizado en la barra de navegación, encabezados, paneles |	Luminancia reducida para distinguirse de #343541 y mantener contraste AAA (aproximadamente 12:1 contra el color blanco).
| Verde Hoja | #2A8050	| Verde Casa | #1E513B | Utilizado en los botones principales y en los enlaces destacados | Oscurecido aproximadamente en un 25 % para garantizar contraste AAA y evitar problemas de visibilidad en texto blanco, sin perder viveza |
| Verde Brote | #38865D	| Verde Tierra | #27674A | Utilizado en iconos y en estados hover/activo | Matiz verde profundo que resalta sobre la barra de navegación y el fondo. Presenta un contraste AAA (> 7:1) para feedback claro. |

<img src="/assets/img/capitulo-5/style-guidelines/colors/dark-mode/secondary-color-dark-mode.png" alt="Listado de todos los colores secundarios en modo dark que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

###### Tabla 30 y algo
*Descripción de usos y justificación para cada uno de los tonos del color secundario de Macetech en Modo Dark*

| Light‑Mode | Light-Mode Hex |	Dark‑Mode | Dark-Mode Hex | Uso en Dark‑Mode | Justificación |
|------------|----------------|-----------|---------------|------------------|---------------|
| Blanco |	#FFFFFF |	Gris Pizarra |	#343541	| Utilizado en área de contenido y página base	| Más oscuro y cómodo visualmente, útil para separar secciones sin recurrir a negro puro. Su contraste con el texto blanco es mayor a 4.5:1 |
| Blanco Cálido |	#F4F4F5	| Gris Oscuro |	#2E2F38	| Utilizado en tarjetas y paneles secundarios	| Presenta un oscurecimiento leve para jerarquizar contenedores secundarios y cumplir Non‑Text Contrast (1.4.11) al presentar un contraste fácil de distingar para personas con problemas de visión (World Wide Web Consortium, 2025)|
| Blanco Frío |	#E4E4E7	| Gris Fuerte | #3B3C45 | Utilizado en líneas de separación y contornos de inputs | Tono cercano a superficie, define límites sin crear “rayas blancas” que distraigan al usuario |
| Gris Suave |	#6B7280	| Plata |	#9CA3AF	| Labels, descripciones | Gris medio para legibilidad confortable sobre fondos oscuros. Presenta un contraste mayor a 8.2:1, respetando AAA |

<img src="/assets/img/capitulo-5/style-guidelines/colors/dark-mode/tertiary-color-dark-mode.png" alt="Listado de todos los colores terciarios en modo dark que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

###### Tabla 30 y algo
*Descripción de usos y justificación para cada uno de los tonos del color terciario de Macetech en Modo Dark*

| Métrica	| Light‑Mode| Light-Mode Hex | Dark‑Mode | Dark-Mode Hex	| Uso en Dark‑Mode | Justificación |
|---------|-----------|----------------|-----------|-----|------------------|---------------|
| Humedad y Temperatura Frío | Azul Mar | #3498DB | Azul Lago |	#2980B9	| Utilizado en barras/áreas de visualización de humedad	y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Es un azul moderado, menos saturado para evitar fatiga ocular en los usuarios. Tiene un contraste AAA sobre el color #343541. Mantiene una semántica de frescor |
| Luz | Mostaza | #F1C40F | Dorado |	#F39C12	| Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas	| Se utiliza un amarillo ligeramente atenuado para no deslumbrar ante el cambio de colores. Tiene un contraste AAA contra un fondo oscuro | 
| Temperatura Medio | Brasas | #E67E22 | Zanahoria |	#D35400	| Utilizado para mostrar el rango medio de temperatura | Se utiliza un naranja oscuro que sigue diferenciando niveles de temperatura. Tiene un contraste AA/AAA con texto blanco y fondos oscuros |
| Temperatura Alto | Tomate | #E74C3C | Cereza | #C0392B | Utilizado para mostrar el	rango alto de temperatura | El uso de un rojo menos brillante suaviza el impacto, sin perder señal de alerta. Presenta un buen contraste AAA |
| pH |	#2ECC71 |	Tallo | #27AE60 | Llanura |Utilizado como medidor de acidez/alcalinidad (pH) | Un verde más oscuro que el primario para no confundirse con elementos estáticos. Presenta un contraste AAA con el color blanco |
| Salinidad | #1ABC9C | Neblina | #16A085 | Turquesa | Medidor de salinidad | Se usa el color turquesa profundo que evoca agua salada nocturna. Tiene un contraste AAA contra el fondo en modo oscuro |

* **Contraste accesible:** Oscurecer cada tono Light‑Mode garantiza que el texto blanco y los iconos mantengan un ratio mayor a 4.5:1 (AA). Asimismo, cuando la tipografía en ciertos colores cambia a negro, el contraste pasa a ser mayor a 7:1 (AAA) frente a los nuevos fondos (World Wide Web Consortium 2025).

* **Confort visual:** Evitamos negros y blancos puros para reducir brillos incómodos o bordes luminosos y disminuir la fatiga ocular en entornos de baja luz. Asimismo, se promueve la visibilidad en cualquier momento del día, siendo indiferente a la luz solar o nocturna (World Wide Web Consortium 2025).

* **Consistencia de marca:** Las variantes Dark retienen la temperatura y saturación relativa de sus homólogos Light, preservando la identidad cromática de Macetech en ambos modos.

* **Jerarquía clara:** Al mantener proporciones de uso (50/25/25 % para primarios), el usuario percibe la misma estructura de importancia y navegación tanto en Modo Light como en Modo Dark (Westland y Maggio, 2023).

#### Tipografía:

En Macetech, la tipografía no es solo una herramienta de lectura: es una extensión visual de nuestra identidad. Como señalan estudios como Jay y Lupton (2024), la selección tipográfica genera una respuesta psicológica directa en el usuario, influenciando su percepción de la marca incluso antes de interactuar con el contenido. En nuestro caso, esta elección cumple una función doble: debe comunicar innovación tecnológica con cercanía humana, al tiempo que refuerza el vínculo emocional con quienes utilizan la plataforma.

Una tipografía bien elegida enriquece la experiencia digital, reduce la carga cognitiva y contribuye a la claridad informativa. Para Macetech, que fusiona tecnología IoT con la vida natural de las plantas, es esencial que la fuente transmita modernidad, accesibilidad y confianza sin dejar de ser visualmente armónica con nuestros colores, íconos y componentes de interfaz.

Así, la tipografía en Macetech no solo organiza el contenido, sino que también articula los valores centrales de la marca: innovación sostenible, cercanía digital y precisión confiable. Es un pilar invisible pero esencial para lograr una experiencia coherente, emocionalmente resonante y funcionalmente efectiva (Dopico, 2021).

En el mundo del diseño tipográfico, dos grandes familias destacan: serif y sans-serif. Comprender sus características es esencial para tomar decisiones coherentes con la identidad y la funcionalidad de una marca digital como Macetech:

* **Serif:** 

  Las tipografías serif se distinguen por sus terminaciones ornamentales, conocidas como serifas, en los extremos de los trazos. Estos pequeños detalles, tradicionalmente asociados con elegancia y formalidad, han sido durante décadas una opción predilecta para textos impresos, como libros o publicaciones académicas. Su estructura facilita el seguimiento visual de una letra a otra, lo que favorece la lectura fluida en cuerpos de texto extensos (Jay & Lupton, 2024).

  Aunque su presencia se ha mantenido en entornos digitales, en el caso de Macetech no son recomendadas como tipografía principal, ya que su estilo clásico puede entrar en conflicto con la estética tecnológica y limpia que buscamos transmitir. Ejemplos destacados de este estilo incluyen *Times New Roman* y *Georgia*, tipografías que siguen siendo altamente valoradas por su equilibrio entre legibilidad y tradición.

* **Sans-serif:** 
    
  En contraste, las tipografías sans-serif, carentes de adornos o remates, ofrecen una apariencia más moderna, funcional y accesible. Su trazo uniforme y minimalista mejora significativamente la lectura en pantalla, especialmente en interfaces digitales donde la claridad visual y la distribución de formas son fundamentales para la usabilidad (Jay & Lupton, 2024).

  Dado que Macetech está concebido como un sistema tecnológico de uso cotidiano, con múltiples datos y métricas en pantalla, las tipografías sans-serif constituyen la elección natural. Estas fuentes favorecen una lectura rápida, cómoda y visualmente coherente en contextos digitales. Ejemplos ampliamente reconocidos de esta categoría incluyen *Arial*, *Helvetica* y *Roboto*, siendo esta última una excelente opción por su diseño optimizado para pantallas y sistemas de interfaz moderna.

###### Figura 32

Comparación entre los tipos de tipografía serif, utilizando Roboto Slab, y sans-serif, utilizando Roboto

<img src="/assets/img/capitulo-5/style-guidelines/typography/roboto-font-example.png" alt="
The Roboto font compared to the Roboto Slab font, showing how different they are." width="1000" height="580"> 

En el diseño de interfaces digitales, tanto en aplicaciones móviles como en aplicaciones web, la elección tipográfica juega un rol decisivo en la usabilidad, legibilidad y percepción estética del sistema. En este contexto, las tipografías sans-serif representan la opción más funcional y versátil, especialmente cuando se busca optimizar la experiencia en pantallas pequeñas y variadas resoluciones de visualización. Esta preferencia se fundamenta tanto en principios de diseño centrado en el usuario como en criterios técnicos de rendimiento visual. A continuación, se detallan los principales factores que sustentan esta elección:

1. Legibilidad optimizada en pantallas pequeñas

    Las aplicaciones móviles operan en dispositivos con espacio limitado para el contenido visual. Las fuentes sans-serif, al carecer de adornos o serifas, poseen un trazo uniforme y directo que facilita la lectura incluso en cuerpos tipográficos reducidos. Esto minimiza el esfuerzo visual requerido para interpretar información crítica, mejorando la retención y comprensión del contenido en entornos móviles exigentes (Minakata & Beier, 2022).

2. Claridad y consistencia en múltiples resoluciones y densidades de píxeles

    Uno de los desafíos técnicos en el diseño digital contemporáneo es garantizar que los elementos tipográficos mantengan su nitidez en pantallas con diferentes densidades de píxeles (DPI). Como han señalado González-Rodríguez et al. (2024), las tipografías sans-serif presentan una geometría que se rasteriza de forma eficiente, permitiendo una presentación consistente y legible tanto en pantallas de baja resolución como en dispositivos de gama alta, incluidos smartphones 4K y monitores Retina.

3. Estética alineada con principios de diseño moderno

    La estética visual de interfaces modernas, especialmente en productos tecnológicos como Macetech, privilegia la simplicidad, el orden y la limpieza visual. Las fuentes sans-serif refuerzan estos principios gracias a su estructura sobria y neutral, lo que contribuye a crear interfaces contemporáneas, eficientes y centradas en la funcionalidad, tanto para web y móvil. Su estilo atemporal permite que la identidad visual se mantenga vigente en el tiempo, alineándose con las expectativas del usuario digital actual (Minakata & Beier, 2022).

4. Mejor rendimiento en interfaces dinámicas y responsivas

    En interfaces digitales donde los contenidos cambian constantemente, ya sea por scroll, transiciones animadas o componentes interactivos como sliders o tarjetas, las tipografías sans-serif responden mejor al movimiento, ofreciendo mayor estabilidad visual. Esto evita el desenfoque perceptivo y reduce la fatiga cognitiva, facilitando una navegación continua y fluida (Bhanarkar et al., 2023). Además, su estructura modular mejora la carga y renderización del contenido en sistemas de diseño responsivo tanto móviles como de escritorio.

5. Coherencia entre plataformas móviles y web

    Una aplicación como Macetech, concebida como plataforma multiplataforma, debe mantener una identidad visual coherente tanto en su versión móvil como en su versión web. Las fuentes sans-serif aseguran esta unidad visual sin comprometer la legibilidad ni el rendimiento. Gracias a su versatilidad, pueden ser implementadas fácilmente en frameworks modernos como Vue.js, React o Flutter, sin perder consistencia entre navegadores, sistemas operativos o tamaños de pantalla.

**Tipo de Letra Primaria:**

En el marco del desarrollo de Macetech, una solución tecnológica centrada en la automatización del cuidado de plantas a través de IoT, la elección de una tipografía adecuada resulta esencial para consolidar la identidad visual de la marca y garantizar una experiencia de usuario accesible, moderna y coherente en todos los puntos de contacto. Ya se ha fundamentado previamente la decisión de utilizar una familia sans-serif, debido a su claridad, legibilidad en múltiples resoluciones y alineación con los principios del diseño contemporáneo. A partir de este criterio base, se ha seleccionado la tipografía Rubik como fuente principal del sistema.

Rubik es una fuente sans-serif geométrica con terminaciones suaves y proporciones equilibradas, diseñada originalmente por Philipp Hubert y Sebastian Fischer. Esta fuente se caracteriza por una estética moderna, amigable y ligeramente tecnológica, lo que la convierte en una excelente elección para una marca como Macetech, que busca transmitir simultáneamente confiabilidad, innovación y conexión con la naturaleza (Google, 2025).

1. Geometría funcional y personalidad balanceada

    Rubik presenta una estructura geométrica con ligeras curvas en sus vértices y terminales, lo que le confiere un aspecto visual cálido y accesible, sin sacrificar orden y precisión. Esta combinación de racionalidad visual con suavidad emocional permite que la interfaz de Macetech no resulte ni excesivamente técnica ni completamente informal (Gonzalez-Rodrigueza et al., 2024).

2. Alto rendimiento en pantallas y sistemas responsivos
  
    Rubik está optimizada para su uso en plataformas digitales. Sus proporciones abiertas y espaciado generoso aseguran una legibilidad sobresaliente incluso en dispositivos móviles de baja resolución. Esto la convierte en una fuente ideal para interfaces donde conviven dashboards, datos de sensores, etiquetas y botones, sin generar ruido visual ni comprometer la accesibilidad (Google, 2025).

3. Compatibilidad multiplataforma y optimización web

    Al formar parte de Google Fonts, Rubik cuenta con carga rápida desde CDN, amplia compatibilidad entre navegadores y excelente renderizado tanto en Windows como en sistemas basados en UNIX/macOS. Además, su arquitectura tipográfica admite múltiples pesos (light, regular, medium, bold, extra bold), lo que facilita la creación de una jerarquía visual clara y coherente en todas las secciones de la interfaz (Bhanarkar et al., 2023).

4. Coherencia con la identidad visual de Macetech

    La forma suave pero precisa de Rubik se alinea perfectamente con los valores que Macetech busca proyectar, siendo cuidado, inteligencia y armonía. Frente a otras alternativas sans-serif más neutras (como Open Sans o Lato), Rubik añade un matiz distintivo que refuerza la unicidad de la marca sin caer en lo ornamental (Google, 2025).

5. Soporte multilingüe y cobertura técnica

    Rubik ofrece soporte completo para caracteres latinos extendidos, lo cual es relevante para su despliegue en el mercado hispanohablante, y su estructura modular permite adaptarla fácilmente a sistemas tipográficos escalables dentro de frameworks modernos como Tailwind, Bootstrap, Vue.js o React (Google, 2025).

###### Figura 33

Modelos de grosor para el tipo de letra principal de Macetech, Rubik

<img src="/assets/img/capitulo-5/style-guidelines/typography/rubik-font-thickness.png" alt="
Rubik font thickness models" width="1000" height="580"> 

**Tipo de Letra Secundaria:**

En su compromiso por garantizar una experiencia de usuario verdaderamente inclusiva y adaptada a un público global, Macetech ha integrado Noto Sans como tipografía secundaria especializada para entornos multilingües. Esta familia tipográfica, resultado de la colaboración entre Google y Monotype, ha sido diseñada bajo estándares rigurosos de calidad tipográfica y cobertura Unicode, permitiendo soportar más de 110 000 glifos y 800 idiomas en más de 100 sistemas de escritura (Google, 2025).

El desarrollo de Noto Sans se fundamenta en dos pilares técnicos clave:

* **Interpolación y hinting avanzados:**

    Mediante algoritmos de interpolación paramétrica, cada glifo conserva su fidelidad geométrica en tamaños pequeños y en pantallas de alta densidad (Retina, 4K), garantizando líneas limpias y contornos nítidos en cualquier resolución (Huang, 2019).

* **Métricas tipográficas uniformes:**

    Con interletrajes y alturas de línea coherentes en toda la familia y en sus diferentes pesos (Light, Regular, Bold), Noto Sans facilita la implementación de sistemas de cuadrícula (CSS Grid/Flex) y bibliotecas de componentes, asegurando que el diseño responsivo se mantenga predecible y sin solapamientos de texto (Jay y Lupton, 2024).

###### Figura 34

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans
<img src="/assets/img/capitulo-5/style-guidelines/typography/noto-sans-font-thickness.png" alt="
Noto Sans font thickness models" width="1000" height="580"> 

Gracias a esta profundidad de cobertura y precisión técnica, Noto Sans no solo evita problemas de sustitución de caracteres, sino que también permite a Macetech presentar contenido con total consistencia visual y legibilidad, sin importar la configuración regional y/o lingüística del usuario.

* **Soporte multilingüe y consistencia visual**

    Noto Sans abarca más de 800 idiomas y más de 110.000 caracteres, cubriendo más de 100 sistemas de escritura, lo que la convierte en una herramienta esencial para garantizar que el contenido se muestre de manera clara y legible, independientemente de la configuración lingüística o regional. Según Huang (2019), su diseño versátil asegura una presentación uniforme del texto en diversos contextos internacionales, eliminando los problemas comunes de visualización de caracteres desconocidos.

* **Compromiso con la accesibilidad y la inclusividad**

    La implementación de Noto Sans contribuye significativamente a la accesibilidad y la inclusividad, aspectos fundamentales para ofrecer una experiencia de usuario universal. Al utilizar esta tipografía, Macetech no solo garantiza una presentación coherente del contenido en distintos idiomas, sino que también reafirma su compromiso con la adaptabilidad y la consideración de las necesidades globales de sus usuarios (World Wide Web Consortium, 2025).

* **Integración armoniosa con la identidad de Macetech**

    Aunque Rubik es la tipografía principal de Macetech, Noto Sans se integra de manera armoniosa en situaciones donde se requiere soporte multilingüe, asegurando que la identidad visual de la marca se mantenga coherente y profesional en todos los contextos.

###### Figura 35

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Chino Tradicional
<img src="/assets/img/capitulo-5/style-guidelines/typography/noto-sans-traditional-chinese.png" alt="
Noto Sans font thickness models in Traditional Chinese" width="1000" height="580"> 

###### Figura 36

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Chino Simplificado
<img src="/assets/img/capitulo-5/style-guidelines/typography/noto-sans-simplified-chinese.png" alt="
Noto Sans font thickness models in Simplified Chinese" width="1000" height="580"> 

###### Figura 37

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Coreano
<img src="/assets/img/capitulo-5/style-guidelines/typography/noto-sans-korean.png" alt="
Noto Sans font thickness models in Korean" width="1000" height="580"> 

###### Figura 38

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Tailandés
<img src="/assets/img/capitulo-5/style-guidelines/typography/noto-sans-thai.png" alt="
Noto Sans font thickness models in Thai" width="1000" height="580"> 

###### Figura 39 

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Japonés
<img src="/assets/img/capitulo-5/style-guidelines/typography/noto-sans-japanese.png" alt="
Noto Sans font thickness models in Japanese" width="1000" height="580"> 

**Tipo de Letra Complementaria:**

En aquellos escenarios en los que dependemos exclusivamente de las fuentes instaladas en los dispositivos de los usuarios, por ejemplo, en campañas de correo electrónico, notificaciones SMS o documentos generados localmente, hemos optado por Arial como tipografía complementaria. Arial es una fuente sans-serif de sistema ampliamente disponible en Windows, macOS, Linux y la mayoría de clientes de correo, lo que garantiza que nuestro contenido se renderice de manera uniforme y coherente sin necesidad de descargas adicionales (Jay y Lupton, 2024).

* **Compatibilidad universal:** 

    Arial forma parte de la lista de “web-safe fonts” y está preinstalada en prácticamente todos los entornos de usuario, eliminando posibles inconsistencias o caídas a fuentes de sustitución que podrían afectar la legibilidad (Google, 2025).

* **Claridad en pantalla:**

    Su trazo sencillo y proporciones equilibradas favorecen la lectura en tamaños pequeños, típicos de los visores de correo y pantallas de dispositivos móviles, evitando el “aliasing” excesivo y garantizando una experiencia clara incluso con bajos niveles de zoom (Jay y Lupton, 2024).

* **Rendimiento optimizado:**

    Al no requerir la descarga de recursos externos, reduce la latencia de apertura de correos electrónicos y mejora la entrega de mensajes SMS con texto formateado, asegurando que el usuario reciba y vea el contenido de inmediato.

Con esta elección, aseguramos que nuestras comunicaciones críticas lleguen siempre con la máxima fiabilidad tipográfica, sin comprometer la estética ni la claridad del mensaje.


###### Figura 40

*Modelos de grosor para el tipo de letra complementaria de Macetech, Arial*
<img src="/assets/img/capitulo-5/style-guidelines/typography/arial-font-thickness.png" alt="
Arial font thickness models" width="1000" height="580"> 



**Espaciado:**



**Tono de comunicación y lenguaje aplicado:**

De acuerdo con Smith y Zook (2024), el tono de comunicación es un componente esencial en el diseño de las secciones de una aplicación. No solo moldea la percepción emocional de los usuarios sobre textos e íconos, sino que también contribuye a forjar una identidad de marca coherente y memorable. Un tono bien calibrado genera en el usuario sensaciones de cercanía y confianza, al tiempo que un lenguaje claro y accesible refuerza la visibilidad en buscadores y facilita su navegación interna.

En esta sección detallamos las directrices de Lenguaje Utilizado de Macetech, diseñadas para asegurar una comunicación coherente, efectiva y alineada con nuestra identidad de marca en todos los puntos de contacto. Aquí encontrarás la descripción de nuestra voz de marca y los tonos contextuales que adaptan esa voz a situaciones específicas, desde mensajes de bienvenida hasta alertas críticas y notificaciones rutinarias. Además, incluiremos pautas prácticas sobre vocabulario preferido, estilo gramatical y adaptaciones multicanal, de modo que todos los equipos de contenido y diseño puedan aplicar un lenguaje claro, accesible y emocionalmente resonante para fortalecer la experiencia del usuario en Macetech.

* **Tono y voz:** 

    En esta sección vamos a establecer la personalidad y las variaciones de nuestro lenguaje para que cada interacción refuerce la identidad de Macetech, genere confianza y mejore la experiencia de cuidado de plantas.

    La voz de Macetech es la forma consistente en que nos comunicamos en todos los canales. Nuestra voz es:

    * **Cálida y empática:**
  
        Reconocemos que cada usuario cuida de un ser vivo: hablamos con cercanía y comprensión.

    * **Experta pero accesible:**

        Ofrecemos conocimientos de monitoreo y cuidado basados en datos, pero evitando tecnicismos innecesarios.

    * **Optimista y motivadora:**

        Celebramos cada logro, desde un riego correcto hasta un brote nuevo, para mantener al usuario comprometido.

    El tono adapta nuestra voz al escenario de uso, modulando la energía y formalidad del mensaje:

    | Contexto | Objetivo | Tono principal | Tono alternativo |
    |----------|----------|----------------|------------------|
    | Onboarding y Bienvenida | Generar vínculo inicial | Entusiasta y acogedor | - |
    | Éxitos y Recompensas | Reforzar logros y motivar | Celebratorio | -
    | Alertas preventivas | Avisar con urgencia moderada | Claro y directo | Empático breve
    | Errores críticos | Informar y guiar solución | Sobrio y tranquilizador | -
    | Consejos | Educar y acompañar paso a paso | Amigable y didáctico | -
    | Notificaciones rutinarias | Recordar sin invadir | Respetuoso & breve | Cordial breve

    Esta estructura de voz y tono garantiza que, sin importar el punto de contacto, ya sea aplicación móvil, correo o aplicación web, Macetech hable con una personalidad única, coherente y alineada a los valores de sostenibilidad, innovación y proximidad que caracterizan nuestra marca.

* **Principios Fundamentales de Comunicación:**

    Estos principios guían cada texto e interacción dentro de Macetech, garantizando claridad, consistencia y conexión emocional:

    * **Claro y conciso:**

        Usa oraciones breves y directas. 
        
        Evita jerga técnica innecesaria; cuando debas introducir un término especializado, acompáñalo de una breve explicación.

    * **Empático y humano:**

        Reconoce las necesidades y emociones del usuario.

        Emplea un lenguaje positivo que refuerce la confianza (“¡Buen trabajo!”, “Sabemos que tus plantas te importan”).

    * **Útil y orientado a la acción:**

        Prioriza la información que ayuda al usuario a resolver tareas o entender pasos (“Para ajustar el nivel de humedad, desliza este control…”).

        Incluye siempre llamadas a la acción (CTAs) claras y concretas.

    * **Consistente y reconocible:**

        Mantén el mismo estilo de redacción (voz activa, estructura de párrafos, longitud de líneas) en toda la plataforma.

        Usa vocabulario y fórmulas de saludo o despedida uniformes para reforzar la identidad de marca.

    * **Accesible e inclusivo:**

        Adapta el lenguaje para ser comprensible por usuarios de distintos niveles de experiencia.

        Asegúrate de que el contraste de texto y color cumpla con las pautas de accesibilidad y que las instrucciones sean claras para todos.

* **Patrones de Uso:**

    A continuación se presentan ejemplos de mensajes antes y después de aplicar nuestro modelo de Voz y Tono, según distintos contextos de interacción:

    | Contexto | Cuándo usarlo | Ejemplo(antes) | Ejemplo(después) | 
    |----------|---------------|----------------|------------|
    | Onboarding | Primera vez que el usuario abre la aplicación | “Bienvenido a la aplicación.” | “¡Bienvenido a Macetech! Empecemos a cuidar tus plantas juntos.” |
    | Mensaje de éxito | Tras completar una acción de riego | “Riego completado.” | “¡Genial! Tu planta acaba de recibir su riego óptimo.” |
    | Alerta preventiva | Nivel de humedad bajo o alto | “Nivel de humedad bajo.” | “Atención: tu planta necesita agua. Ajusta el riego para mantenerla saludable.”
    | Error crítico | Fallo en sensores o guardado de datos | “Error al guardar datos.” | “Ups… No pudimos registrar la información. Revisa tu conexión y vuelve a intentarlo.” |
    | Consejo educativo	| Sugerencia de mantenimiento o fertilización | “Fertiliza tu planta cada mes.”	| “Para un crecimiento óptimo, aplica fertilizante ligero una vez al mes.” |
    | Notificación rutinaria | Recordatorios diarios o semanales de cuidado	| “Recordatorio de cuidado.” | “¡Hola! No olvides revisar el nivel de humedad de tu planta hoy.” |

* **Vocabulario y estilo:**
  
    Esta sección define las palabras, expresiones y convenciones que refuerzan la identidad de Macetech y aseguran coherencia en todos los textos.

  * **Palabras clave y términos recomendados:**

    Selecciona siempre términos que conecten con el propósito de Macetech y eviten ambigüedades:

    | Categoría | Términos recomendados | Por qué | 
    |-----------|-----------------------|---------|
    | Acciones principales | "Regar", "Monitorear", "Nutrir" | Verboes directos, centran al usuario en la tarea. |
    | Estados de planta	| “Saludable”, “Sedienta”, “En crecimiento”	| Palabras concretas que reflejan condiciones reales. |
    | Logros y motivación | “¡Perfecto!”, “¡Excelente!”, “Logrado” | Tono positivo que celebra el éxito. |
    | Consejos y guías | “Para optimizar…”, “Te recomendamos…”, “Prueba a…” | Introducen recomendaciones de forma suave y empática. |
    | Advertencias | “Atención:”, “Importante:”, “Precaución:”	Llamadas de alerta claras sin incentivar la preocupación excesiva o el pánico. |

  * **Palabras prohibidas:**
  
    Evita jergas técnicas, modismos regionales o vocabulario que pueda resultar confuso:

      * **Términos excesivamente técnicos:**
  
        Ejemplos: “conductividad eléctrica”, “osmolaridad”, "gineceo", "solastalgia"
        
        Solo se pueden usar cuando vayan acompañados de una breve explicación accesible y de fácil comprensión.

      * **Coloquialismos informales:** 
      
        Ejemplos: “chevere”, “buena onda”, “chamba”.

      * **Acrónimos sin definir:**

        Ejemplos: IoT (Internet de las Cosas)

        Si es necesario usarlos, se deben explicar, por lo menos, la primera vez que sean utilizados.

      * **Frases largas y pasivas:**
  
        Prefiere la voz activa con oraciones de máximo 30 palabras en los mensajes o textos que tenga la aplicación, a menos que estos sean descriptivos o explicativos.

  * **Convenciones de gramática y puntuación:**

    * **Voz activa:** 

        Es necesario aplicar una voz activa en todo momento. Utilizar frases como “La app registra la humedad” en lugar de “La humedad es registrada por la app”.

    * **Longitud de línea:** 

        Para asegurar legibilidad tanto en móviles como en computadores, es necesario que las línea tengan un máximo de entre 60 y 65 caracteres.

    * **Interlineado:** 

        Para evitar la fatiga ocular en los usuarios es necesario que haya un interlineado de entre 1.5 y 2LS.

    * **Uso de listas:**

        Si es necesario el uso de listas, estas deben estar con viñetas para pasos o características, y deben estar enumeradas en caso de procesos secuenciales.

    * **Uso de comillas:**

        Se deben utilizar comillas angulares (« ») o latinas (“ ”) para fragmentos textuales que requieran su uso. Se debe evitar el uso de comillas simples (‘ ’).

  * **Formato y énfasis:**

    * **Negrita:**

      El uso de negrita es solo para resaltar conceptos clave o acciones en los mensajes que presente la aplicación al usuario, como (“**Regar la planta**”).

    * **Cursiva:** 

      El uso de cursiva es solo para términos técnicos introducidos, o términos que no tengan traducción directa al idioma que está empleando el usuario, ya sea por anglicismos o matices culturales, como ("*trade-off*")

    * **Mayúsculas:** 

      El uso de mayúsculas es solo para nombres propios de la marca o siglas, como ("MACETECH", "IoT").

    * **Emojis:**

      El uso de emojis esta permitido solo en notificaciones informales y mensajes de éxito para reforzar cercanía, como (“¡Listo! 🌱”).

      Los emojis están prohibidos en textos formales (alertas críticas, documentación legal).

  * **Lenguaje accesible:**

    * **Género neutro:**
          
        Se debe hablar en segunda persona (“tú”) o usar plural inclusivo (“[email protected]”).

    * **Claridad:** 

        Se debe evitar dobles negaciones y construcciones complejas.

  * **Accesibilidad:**

    Se debe asegurar de que las etiquetas de botones y enlaces describan claramente la acción (“Ver historial de riego” vs. “Ver más”).

* **Adaptaciones Multicanal:**

    Para asegurar que la voz y el tono de Macetech se mantengan consistentes y efectivos, adaptamos ligeramente el estilo según el canal de interacción:

  * **Aplicación Móvil:**

    * **Mensajes breves y directos:**

        Deben tener una longitud máxima de entre 45 y 55 caracteres. Se debe priorizar la información esencial para no abrumar al usuario.

    * **Notificaciones push:**

        Se debe usar un tono cercano y motivador para entusiasmar o interesar al usuario, como (“¡Hora de regar tu planta! 🌱”)

        Asimismo, siempre se debe incluir una acción clara para el usuario, como (pulsar para abrir la app).

    * **Onboarding in-app:**

        Al iniciar se debe fragmentar el tutorial en pasos cortos.Asimismo, se debe combinar texto conciso con elementos visuales (íconos verdes) y CTA claros (“Siguiente”, “Entendido”).

    * **Errores y alertas:**

        Debe utilizar texto mínimo para describir lo que es el problema y la posible solución en dos líneas. Asimismo, se deben agregar botones de acción ("Reintentar", "Ajustar sensor").

  * **Plataforma Web:**

    * **Textos más extensos:**

        Deben tener una longitud máxima de línea de entre 60 y 65 caracteres. Se debe priorizar la información esencial para no abrumar al usuario.

        Se permite el uso de párrafos de 2–3 oraciones para explicar funcionalidades y beneficios.

    * **Correos electrónicos:**

        Se debe utilizar un encabezado personalizado, como ("Hola, [Nombre del usuario]"). Es necesario utilizar un tono amigable pero informativo; incluyendo enlaces con texto descriptivo (“Ver guía completa de cuidado”).

    * **Centro de ayuda y documentación:**

        Se debe utilizar un formato FAQ: preguntas en negrita y respuestas concisas (1–2 oraciones). Asimismo, se deben ingresar instrucciones paso a paso numeradas junto screenshots con bordes grises para enfocar la atención.

**Iconografía:**

**Logo:**

### 5.1.2. Web, Mobile and IoT Style Guidelines

El presente apartado establece las directrices de diseño visual y experiencia de usuario (UX/UI) que regirán la implementación coherente de la solución en sus tres plataformas principales: web, móvil e IoT. Estas guías divididas aseguran la armonización estética y funcional de la interfaz en distintos entornos tecnológicos, permitiendo una experiencia de usuario homogénea, eficiente y accesible, independientemente del dispositivo utilizado.

Cada subapartado aborda de forma específica los principios, estilos y restricciones aplicables a su respectiva plataforma, detallando aspectos clave como paleta cromática, tipografía, iconografía, estructura de interacción y criterios de adaptabilidad. Este enfoque modular permite alinear los estándares de diseño con las capacidades técnicas y expectativas de los usuarios en cada contexto operativo.

#### 5.1.2.1. Web Style Guidelines

#### 5.1.2.2. Mobile Style Guidelines

##### 5.1.2.2.1. Android Style Guidelines

##### 5.1.2.2.2. iOS Style Guidelines

#### 5.1.2.3. IoT Style Guidelines

## 5.2. Information Architecture

### 5.2.1. Organization Systems

### 5.2.2. Labeling Systems

### 5.2.3. SEO Tags and Meta Tags

### 5.2.4. Searching Systems

### 5.2.5. Navigation Systems

## 5.3. Landing Page UI Design

### 5.3.1. Landing Page Wireframe

### 5.3.2. Landing Page Mock-up

## 5.4. Applications UX/UI Design

### 5.4.1. Applications Wireframes

### 5.4.2. Applications Wireflow Diagrams

### 5.4.2. Applications Mock-ups

### 5.4.3. Applications User Flow Diagrams

## 5.5. Applications Prototyping
