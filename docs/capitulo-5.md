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

_Listado de colores primarios que se usaran en las aplicaciones de Macetech_

<img src="/assets/img/capitulo-5/style-guidelines/colors/light-mode/primary-color-light-mode.png" alt="Listado de todos los colores primarios que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

El verde es la piedra angular de Macetech porque conecta directamente con la naturaleza, el crecimiento y la salud de las plantas, al mismo tiempo que sugiere innovación tecnológica. Desde el punto de la experiencia del usuario y su percepción, el verde equilibra la respuesta emocional, puesto que relaja la corteza visual y facilita la concentración en los datos de los sensores, reduciendo la fatiga ocular en entornos de uso prolongado (Wang et al., 2025). Asimismo, al seguir las recomendaciones de accesibilidad WCAG 2.1, los tonos escogidos garantizan contraste suficiente para usuarios con baja visión sin sacrificar la riqueza del matiz verde primario (World Wide Web Consortium, 2025). Estos colores no deberían ocupar más del 45% de la pantalla del usuario.

Para mantener coherencia y jerarquía visual, cada tono cumple un rol bien definido. A continuación se describe dónde y por qué se usa cada uno:

###### Tabla 30 y algo

_Descripción de usos y justificación para cada uno de los tonos del color primario de Macetech_

| Nombre       | Hex     | Uso principal                                                    | Porcentaje de uso                              | Justificación técnica                                                                                                                                                                                            |
| ------------ | ------- | ---------------------------------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Verde Bosque | #296244 | Utilizado en la barra de navegación, encabezados, paneles        | 50% con respecto a todos los colores primarios | Ofrece máxima legibilidad y anclaje visual, con un contraste mayor a 7:1 (7.17:1) con el color blanco, el cual se utilizara para la tipografía                                                                   |
| Verde Hoja   | #2A8050 | Utilizado en los botones principales y en los enlaces destacados | 25% con respecto a todos los colores primarios | Es bueno para un acento de interacción, con un contraste de 4.48:1 con respecto al color blanco, lo que cumple WCAG AA para texto normal y WCAG AAA para texto grande o en negrita. Guía la atención sin saturar |
| Verde Brote  | #38865D | Utilizado en iconos y en estados hover/activo                    | 25% con respecto a todos los colores primarios | Otorga un feedback visual y llama la mirada a acciones secundarias manteniendo armonía con las funciones primarias                                                                                               |

- **Jerarquía visual:** el tono más oscuro (“Verde Bosque”) sostiene la estructura, mientras que los más claros indican niveles de interacción para el usuario, reduciendo la carga cognitiva al distinguir zonas estáticas de dinámicas.

- **Consistencia de marca:** los tres verdes comparten la misma temperatura de color, evitando derivaciones que confundan al usuario sobre la identidad de la plataforma (Wheeler y Meyerson, 2024).

- **Accesibilidad:** todos los contrastes han sido validados según WCAG 2.1 para asegurar cumplimiento AA/AAA en texto y elementos interactivos, protegiendo a usuarios con deficiencias visuales .

**Color secundario:**

###### Figura 30 y algo

_Listado de colores secundarios que se usaran en las aplicaciones de Macetech_

<img src="/assets/img/capitulo-5/style-guidelines/colors/light-mode/secondary-color-light-mode.png" alt="Listado de todos los colores secundarios que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

Los colores secundarios en Macetech cumplen la función de “lienzo” y soporte de contenido, al ofrecer un fondo neutro que potencia la legibilidad de los elementos primarios (verdes) y de los indicadores de estado, sin competir visualmente con ellos. El blanco puro garantiza máximo contraste y limpieza, mientras que los tonos grises aportan confort visual y mantienen jerarquía respecto a las barras de navegación y componentes verdes (Westland y Maggio, 2025).

Además, estos tonos neutros facilitan el enfocado en los datos y reducen la fatiga ocular durante sesiones prolongadas, cumpliendo las recomendaciones de accesibilidad WCAG 2.1 (World Wide Web Consortium, 2025). Estos colores secundarios no deberían ocupar más del 40% de la pantalla del usuario.

###### Tabla 30 y algo

_Descripción de usos y justificación para cada uno de los tonos del color secundario de Macetech_

| Nombre        | Hex     | Uso principal                                           | Porcentaje de uso                                  | Justificación técnica                                                                                                                                                   |
| ------------- | ------- | ------------------------------------------------------- | -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Blanco        | #FFFFFF | Utilizado en área de contenido y página base            | 50% con respecto a todos los colores secundarios   | El blanco puro maximiza contraste con los colores primarios y ofrece un ratio mayor a 4.5:1 con texto primario y secundarios                                            |
| Blanco Cálido | #F4F4F5 | Utilizado en tarjetas y paneles secundarios             | 25% con respecto a todos los colores secundarios   | El gris claro mantiene la armonía al separar componentes sin generar excesivo ruido visual para los usuarios                                                            |
| Blanco Frío   | #E4E4E7 | Utilizado en líneas de separación y contornos de inputs | 12.5% con respecto a todos los colores secundarios | Mantiene un tono sutil que cumple con las bases del Non‑Text Contrast (WCAG 1.4.11), puesto que no interfiere con la identificación de componentes, pero define límites |
| Gris Suave    | #6B7280 | Labels, descripciones                                   | 12.5% con respecto a todos los colores secundarios | Proveé un contraste mayor a 4.5:1 sobre sus respectivos fondos, además de garantizar lectura de información de menor jerarquía sin competir con texto principal         |

- **Jerarquía visual:** Los neutrales crean un lienzo donde los verdes primarios destacan con claridad, evitando distracciones y enfocando la atención en la información clave.

- **Consistencia:** Todos los secundarios comparten matices grises con la misma temperatura de color, garantizando que posibles transiciones entre diseños light y dark sea fluida y predecible (Zeldman, 2024).

- **Accesibilidad:** Cada token ha sido validado contra WCAG 2.1 (niveles AA/AAA) para asegurar lectura cómoda y separación de componentes interactivos, protegiendo a usuarios con dificultades visuales.

**Color terciario:**

###### Figura 30 y algo

_Listado de colores terciarios que se usaran en las aplicaciones de Macetech_

<img src="/assets/img/capitulo-5/style-guidelines/colors/light-mode/tertiary-color-light-mode.png" alt="Listado de todos los colores terciarios que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

Para asegurar que los datos de nuestros sensores IoT sean fáciles de interpretar de un vistazo, definimos una paleta de colores terciarios específicamente orientada a la visualización de métricas. Cada tono ha sido elegido no solo por su carácter semántico (asociación intuitiva con humedad, luz, temperatura, pH y salinidad), sino también por su rendimiento en términos de contraste y accesibilidad, tanto en entornos de alta luminosidad como en ambientes oscuros. Esta estrategia refuerza la consistencia de la interfaz y facilita la rápida identificación de cada variable sin necesidad de etiquetas adicionales (Westland y Maggio, 2023).

Su objetivo es garantizar que cada variable sea inmediatamente reconocible, con contrastes validados según WCAG 2.1 y una temperatura de color coherente con nuestros verdes primarios. Aseguramos que las gráficas, barras e indicadores destaquen con claridad, mejorando la experiencia de usuario y la precisión en la lectura de datos. Estos colores terciarios no deberían ocupar más del 10% de la pantalla del usuario.

###### Tabla 30 y algo

_Descripción de usos y justificación para cada uno de los tonos del color terciario de Macetech_

| Métrica                        | Nombre   | Hex     | Uso                                                                                                                                                                                        | Justificación técnica                                                                                                                             |
| ------------------------------ | -------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Humedad y Temperatura Fría     | Azul Mar | #3498DB | Utilizado en barras/áreas de visualización de humedad y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Sigue una base de paleta categórica: azul es convencional para humedad, alto contraste con fondo y consistente con dashboards de las métricas IoT |
| Luz y Alerta Moderada          | Mostaza  | #F1C40F | Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas en un nivel moderada                                     | El amarillo brillante remite al sol, además de ser legible sobre gris oscuro y blanco                                                             |
| Temperatura Media              | Brasas   | #E67E22 | Utilizado para mostrar el rango medio de temperatura                                                                                                                                       | Naranja medio comunica calor moderado, siendo una diferenciación clara entre rangos                                                               |
| Temperatura Alta y Alerta Alta | Tomate   | #E74C3C | Utilizado para mostrar el rango alto de temperatura y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas a un nivel alto                               | Rojo intenso para alertas de calor, puesto que es una semántica cultural de peligro. Asimismo, tiene un contraste AAA con colores blancos         |
| pH                             | Tallo    | #2ECC71 | Utilizado como medidor de acidez/alcalinidad (pH)                                                                                                                                          | Verde para pH neutro/seguro, lo que armoniza con primarios y tiene un contraste 4.5:1.                                                            |
| Salinidad                      | Neblina  | #1ABC9C | Utilizado como medidor de salinidad                                                                                                                                                        | Tonos turquesa evocan agua salada, lo que es distintivo frente a otros sensores.                                                                  |

| Métrica                    | Nombre   | Hex     | Uso                                                                                                                                                                                        | Justificación técnica                                                                                                                             |
| -------------------------- | -------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Humedad y Temperatura Frío | Azul Mar | #3498DB | Utilizado en barras/áreas de visualización de humedad y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Sigue una base de paleta categórica: azul es convencional para humedad, alto contraste con fondo y consistente con dashboards de las métricas IoT |
| Luz                        | Mostaza  | #F1C40F | Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas                                                          | El amarillo brillante remite al sol, además de ser legible sobre gris oscuro y blanco                                                             |
| Temperatura Medio          | Brasas   | #E67E22 | Utilizado para mostrar el rango medio de temperatura                                                                                                                                       | Naranja medio comunica calor moderado, siendo una diferenciación clara entre rangos                                                               |
| Temperatura Alto           | Tomate   | #E74C3C | Utilizado para mostrar el rango alto de temperatura                                                                                                                                        | Rojo intenso para alertas de calor, puesto que es una semántica cultural de peligro. Asimismo, tiene un contraste AAA con colores blancos         |
| pH                         | Tallo    | #2ECC71 | Utilizado como medidor de acidez/alcalinidad (pH)                                                                                                                                          | Verde para pH neutro/seguro, lo que armoniza con primarios y tiene un contraste 4.5:1.                                                            |
| Salinidad                  | Neblina  | #1ABC9C | Utilizado como medidor de salinidad                                                                                                                                                        | Tonos turquesa evocan agua salada, lo que es distintivo frente a otros sensores.                                                                  |

- **Jerarquía visual:** Los neutrales crean un lienzo donde los verdes primarios destacan con claridad, evitando distracciones y enfocando la atención en la información clave.

- **Consistencia:** Todos los secundarios comparten matices grises con la misma temperatura de color, garantizando que la transición entre light y dark sea fluida y predecible.

- **Accesibilidad:** Cada token ha sido validado contra WCAG 2.1 (niveles AA/AAA) para asegurar lectura cómoda y separación de componentes interactivos, protegiendo a usuarios con dificultades visualesl.

**Dark-mode:**

En Dark‑Mode adaptamos cada tono para asegurar contraste, confort visual y consistencia con el fondo gris suave #343541 al que cambiara la pantalla. Siguiendo WCAG 2.1 y prácticas de accesibilidad, evitamos blancos o negros puros y saturaciones excesivas que fatiguen la vista.

<img src="/assets/img/capitulo-5/style-guidelines/colors/dark-mode/primary-color-dark-mode.png" alt="Listado de todos los colores primarios en modo dark que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

###### Tabla 30 y algo

_Descripción de usos y justificación para cada uno de los tonos del color primario de Macetech en Modo Dark_

| Light‑Mode   | Light-Mode Hex | Dark‑Mode    | Dark-Mode Hex | Uso en Dark‑Mode                                                 | Justificación                                                                                                                            |
| ------------ | -------------- | ------------ | ------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Verde Bosque | #296244        | Verde Pino   | #1B3326       | Utilizado en la barra de navegación, encabezados, paneles        | Luminancia reducida para distinguirse de #343541 y mantener contraste AAA (aproximadamente 12:1 contra el color blanco).                 |
| Verde Hoja   | #2A8050        | Verde Casa   | #1E513B       | Utilizado en los botones principales y en los enlaces destacados | Oscurecido aproximadamente en un 25 % para garantizar contraste AAA y evitar problemas de visibilidad en texto blanco, sin perder viveza |
| Verde Brote  | #38865D        | Verde Tierra | #27674A       | Utilizado en iconos y en estados hover/activo                    | Matiz verde profundo que resalta sobre la barra de navegación y el fondo. Presenta un contraste AAA (> 7:1) para feedback claro.         |

<img src="/assets/img/capitulo-5/style-guidelines/colors/dark-mode/secondary-color-dark-mode.png" alt="Listado de todos los colores secundarios en modo dark que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

###### Tabla 30 y algo

_Descripción de usos y justificación para cada uno de los tonos del color secundario de Macetech en Modo Dark_

| Light‑Mode    | Light-Mode Hex | Dark‑Mode    | Dark-Mode Hex | Uso en Dark‑Mode                                        | Justificación                                                                                                                                                                                                                       |
| ------------- | -------------- | ------------ | ------------- | ------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Blanco        | #FFFFFF        | Gris Pizarra | #343541       | Utilizado en área de contenido y página base            | Más oscuro y cómodo visualmente, útil para separar secciones sin recurrir a negro puro. Su contraste con el texto blanco es mayor a 4.5:1                                                                                           |
| Blanco Cálido | #F4F4F5        | Gris Oscuro  | #2E2F38       | Utilizado en tarjetas y paneles secundarios             | Presenta un oscurecimiento leve para jerarquizar contenedores secundarios y cumplir Non‑Text Contrast (1.4.11) al presentar un contraste fácil de distingar para personas con problemas de visión (World Wide Web Consortium, 2025) |
| Blanco Frío   | #E4E4E7        | Gris Fuerte  | #3B3C45       | Utilizado en líneas de separación y contornos de inputs | Tono cercano a superficie, define límites sin crear “rayas blancas” que distraigan al usuario                                                                                                                                       |
| Gris Suave    | #6B7280        | Plata        | #9CA3AF       | Labels, descripciones                                   | Gris medio para legibilidad confortable sobre fondos oscuros. Presenta un contraste mayor a 8.2:1, respetando AAA                                                                                                                   |

<img src="/assets/img/capitulo-5/style-guidelines/colors/dark-mode/tertiary-color-dark-mode.png" alt="Listado de todos los colores terciarios en modo dark que se usaran en las aplicaciones de Macetech en general" width="600" height="300"> <br>

###### Tabla 30 y algo

_Descripción de usos y justificación para cada uno de los tonos del color terciario de Macetech en Modo Dark_

| Métrica                        | Light‑Mode | Light-Mode Hex | Dark‑Mode | Dark-Mode Hex | Uso en Dark‑Mode                                                                                                                                                                           | Justificación                                                                                                                                                   |
| ------------------------------ | ---------- | -------------- | --------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Humedad y Temperatura Fría     | Azul Mar   | #3498DB        | Azul Lago | #2980B9       | Utilizado en barras/áreas de visualización de humedad y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Es un azul moderado, menos saturado para evitar fatiga ocular en los usuarios. Tiene un contraste AAA sobre el color #343541. Mantiene una semántica de frescor |
| Luz y Alerta Moderada          | Mostaza    | #F1C40F        | Dorado    | #F39C12       | Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas                                                          | Se utiliza un amarillo ligeramente atenuado para no deslumbrar ante el cambio de colores. Tiene un contraste AAA contra un fondo oscuro                         |
| Temperatura Media              | Brasas     | #E67E22        | Zanahoria | #D35400       | Utilizado para mostrar el rango medio de temperatura                                                                                                                                       | Se utiliza un naranja oscuro que sigue diferenciando niveles de temperatura. Tiene un contraste AA/AAA con texto blanco y fondos oscuros                        |
| Temperatura Alta y Alerta Alta | Tomate     | #E74C3C        | Cereza    | #C0392B       | Utilizado para mostrar el rango alto de temperatura y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas a un nivel alto                               | El uso de un rojo menos brillante suaviza el impacto, sin perder señal de alerta. Presenta un buen contraste AAA                                                |
| pH                             | #2ECC71    | Tallo          | #27AE60   | Llanura       | Utilizado como medidor de acidez/alcalinidad (pH)                                                                                                                                          | Un verde más oscuro que el primario para no confundirse con elementos estáticos. Presenta un contraste AAA con el color blanco                                  |
| Salinidad                      | #1ABC9C    | Neblina        | #16A085   | Turquesa      | Medidor de salinidad                                                                                                                                                                       | Se usa el color turquesa profundo que evoca agua salada nocturna. Tiene un contraste AAA contra el fondo en modo oscuro                                         |

| Métrica                    | Light‑Mode | Light-Mode Hex | Dark‑Mode | Dark-Mode Hex | Uso en Dark‑Mode                                                                                                                                                                           | Justificación                                                                                                                                                   |
| -------------------------- | ---------- | -------------- | --------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Humedad y Temperatura Frío | Azul Mar   | #3498DB        | Azul Lago | #2980B9       | Utilizado en barras/áreas de visualización de humedad y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Es un azul moderado, menos saturado para evitar fatiga ocular en los usuarios. Tiene un contraste AAA sobre el color #343541. Mantiene una semántica de frescor |
| Luz                        | Mostaza    | #F1C40F        | Dorado    | #F39C12       | Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas                                                          | Se utiliza un amarillo ligeramente atenuado para no deslumbrar ante el cambio de colores. Tiene un contraste AAA contra un fondo oscuro                         |
| Temperatura Medio          | Brasas     | #E67E22        | Zanahoria | #D35400       | Utilizado para mostrar el rango medio de temperatura                                                                                                                                       | Se utiliza un naranja oscuro que sigue diferenciando niveles de temperatura. Tiene un contraste AA/AAA con texto blanco y fondos oscuros                        |
| Temperatura Alto           | Tomate     | #E74C3C        | Cereza    | #C0392B       | Utilizado para mostrar el rango alto de temperatura                                                                                                                                        | El uso de un rojo menos brillante suaviza el impacto, sin perder señal de alerta. Presenta un buen contraste AAA                                                |
| pH                         | #2ECC71    | Tallo          | #27AE60   | Llanura       | Utilizado como medidor de acidez/alcalinidad (pH)                                                                                                                                          | Un verde más oscuro que el primario para no confundirse con elementos estáticos. Presenta un contraste AAA con el color blanco                                  |
| Salinidad                  | #1ABC9C    | Neblina        | #16A085   | Turquesa      | Medidor de salinidad                                                                                                                                                                       | Se usa el color turquesa profundo que evoca agua salada nocturna. Tiene un contraste AAA contra el fondo en modo oscuro                                         |

- **Contraste accesible:** Oscurecer cada tono Light‑Mode garantiza que el texto blanco y los iconos mantengan un ratio mayor a 4.5:1 (AA). Asimismo, cuando la tipografía en ciertos colores cambia a negro, el contraste pasa a ser mayor a 7:1 (AAA) frente a los nuevos fondos (World Wide Web Consortium 2025).

- **Confort visual:** Evitamos negros y blancos puros para reducir brillos incómodos o bordes luminosos y disminuir la fatiga ocular en entornos de baja luz. Asimismo, se promueve la visibilidad en cualquier momento del día, siendo indiferente a la luz solar o nocturna (World Wide Web Consortium 2025).

- **Consistencia de marca:** Las variantes Dark retienen la temperatura y saturación relativa de sus homólogos Light, preservando la identidad cromática de Macetech en ambos modos.

- **Jerarquía clara:** Al mantener proporciones de uso (50/25/25 % para primarios), el usuario percibe la misma estructura de importancia y navegación tanto en Modo Light como en Modo Dark (Westland y Maggio, 2023).

#### 5.1.1.2. Tipografía:

En Macetech, la tipografía no es solo una herramienta de lectura: es una extensión visual de nuestra identidad. Como señalan estudios como Jay y Lupton (2024), la selección tipográfica genera una respuesta psicológica directa en el usuario, influenciando su percepción de la marca incluso antes de interactuar con el contenido. En nuestro caso, esta elección cumple una función doble: debe comunicar innovación tecnológica con cercanía humana, al tiempo que refuerza el vínculo emocional con quienes utilizan la plataforma.

Una tipografía bien elegida enriquece la experiencia digital, reduce la carga cognitiva y contribuye a la claridad informativa. Para Macetech, que fusiona tecnología IoT con la vida natural de las plantas, es esencial que la fuente transmita modernidad, accesibilidad y confianza sin dejar de ser visualmente armónica con nuestros colores, íconos y componentes de interfaz.

Así, la tipografía en Macetech no solo organiza el contenido, sino que también articula los valores centrales de la marca: innovación sostenible, cercanía digital y precisión confiable. Es un pilar invisible pero esencial para lograr una experiencia coherente, emocionalmente resonante y funcionalmente efectiva (Dopico, 2021).

En el mundo del diseño tipográfico, dos grandes familias destacan: serif y sans-serif. Comprender sus características es esencial para tomar decisiones coherentes con la identidad y la funcionalidad de una marca digital como Macetech:

- **Serif:**

  Las tipografías serif se distinguen por sus terminaciones ornamentales, conocidas como serifas, en los extremos de los trazos. Estos pequeños detalles, tradicionalmente asociados con elegancia y formalidad, han sido durante décadas una opción predilecta para textos impresos, como libros o publicaciones académicas. Su estructura facilita el seguimiento visual de una letra a otra, lo que favorece la lectura fluida en cuerpos de texto extensos (Jay & Lupton, 2024).

  Aunque su presencia se ha mantenido en entornos digitales, en el caso de Macetech no son recomendadas como tipografía principal, ya que su estilo clásico puede entrar en conflicto con la estética tecnológica y limpia que buscamos transmitir. Ejemplos destacados de este estilo incluyen _Times New Roman_ y _Georgia_, tipografías que siguen siendo altamente valoradas por su equilibrio entre legibilidad y tradición.

- **Sans-serif:**

  En contraste, las tipografías sans-serif, carentes de adornos o remates, ofrecen una apariencia más moderna, funcional y accesible. Su trazo uniforme y minimalista mejora significativamente la lectura en pantalla, especialmente en interfaces digitales donde la claridad visual y la distribución de formas son fundamentales para la usabilidad (Jay & Lupton, 2024).

  Dado que Macetech está concebido como un sistema tecnológico de uso cotidiano, con múltiples datos y métricas en pantalla, las tipografías sans-serif constituyen la elección natural. Estas fuentes favorecen una lectura rápida, cómoda y visualmente coherente en contextos digitales. Ejemplos ampliamente reconocidos de esta categoría incluyen _Arial_, _Helvetica_ y _Roboto_, siendo esta última una excelente opción por su diseño optimizado para pantallas y sistemas de interfaz moderna.

###### Figura 32

Comparación entre los tipos de tipografía serif, utilizando Roboto Slab, y sans-serif, utilizando Roboto

<img src="/assets/img/capitulo-5/style-guidelines/general/typography/roboto-font-example.png" alt="
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

<img src="/assets/img/capitulo-5/style-guidelines/general/typography/rubik-font-thickness.png"  alt="
Rubik font thickness models" width="1000" height="580">

**Tipo de Letra Secundaria:**

En su compromiso por garantizar una experiencia de usuario verdaderamente inclusiva y adaptada a un público global, Macetech ha integrado Noto Sans como tipografía secundaria especializada para entornos multilingües. Esta familia tipográfica, resultado de la colaboración entre Google y Monotype, ha sido diseñada bajo estándares rigurosos de calidad tipográfica y cobertura Unicode, permitiendo soportar más de 110 000 glifos y 800 idiomas en más de 100 sistemas de escritura (Google, 2025).

El desarrollo de Noto Sans se fundamenta en dos pilares técnicos clave:

- **Interpolación y hinting avanzados:**

  Mediante algoritmos de interpolación paramétrica, cada glifo conserva su fidelidad geométrica en tamaños pequeños y en pantallas de alta densidad (Retina, 4K), garantizando líneas limpias y contornos nítidos en cualquier resolución (Huang, 2019).

- **Métricas tipográficas uniformes:**

  Con interletrajes y alturas de línea coherentes en toda la familia y en sus diferentes pesos (Light, Regular, Bold), Noto Sans facilita la implementación de sistemas de cuadrícula (CSS Grid/Flex) y bibliotecas de componentes, asegurando que el diseño responsivo se mantenga predecible y sin solapamientos de texto (Jay y Lupton, 2024).

###### Figura 34

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans
<img src="/assets/img/capitulo-5/style-guidelines/general/typography/noto-sans-font-thickness.png"  alt="
Noto Sans font thickness models" width="1000" height="580">

Gracias a esta profundidad de cobertura y precisión técnica, Noto Sans no solo evita problemas de sustitución de caracteres, sino que también permite a Macetech presentar contenido con total consistencia visual y legibilidad, sin importar la configuración regional y/o lingüística del usuario.

- **Soporte multilingüe y consistencia visual**

  Noto Sans abarca más de 800 idiomas y más de 110.000 caracteres, cubriendo más de 100 sistemas de escritura, lo que la convierte en una herramienta esencial para garantizar que el contenido se muestre de manera clara y legible, independientemente de la configuración lingüística o regional. Según Huang (2019), su diseño versátil asegura una presentación uniforme del texto en diversos contextos internacionales, eliminando los problemas comunes de visualización de caracteres desconocidos.

- **Compromiso con la accesibilidad y la inclusividad**

  La implementación de Noto Sans contribuye significativamente a la accesibilidad y la inclusividad, aspectos fundamentales para ofrecer una experiencia de usuario universal. Al utilizar esta tipografía, Macetech no solo garantiza una presentación coherente del contenido en distintos idiomas, sino que también reafirma su compromiso con la adaptabilidad y la consideración de las necesidades globales de sus usuarios (World Wide Web Consortium, 2025).

- **Integración armoniosa con la identidad de Macetech**

  Aunque Rubik es la tipografía principal de Macetech, Noto Sans se integra de manera armoniosa en situaciones donde se requiere soporte multilingüe, asegurando que la identidad visual de la marca se mantenga coherente y profesional en todos los contextos.

###### Figura 35

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Chino Tradicional
<img src="/assets/img/capitulo-5/style-guidelines/general/typography/noto-sans-traditional-chinese.png"  alt="
Noto Sans font thickness models in Traditional Chinese" width="1000" height="580">

###### Figura 36

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Chino Simplificado
<img src="/assets/img/capitulo-5/style-guidelines/general/typography/noto-sans-simplified-chinese.png"  alt="
Noto Sans font thickness models in Simplified Chinese" width="1000" height="580">

###### Figura 37

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Coreano
<img src="/assets/img/capitulo-5/style-guidelines/general/typography/noto-sans-korean.png"  alt="
Noto Sans font thickness models in Korean" width="1000" height="580">

###### Figura 38

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Tailandés
<img src="/assets/img/capitulo-5/style-guidelines/general/typography/noto-sans-thai.png"  alt="
Noto Sans font thickness models in Thai" width="1000" height="580">

###### Figura 39

Modelos de grosor para el tipo de letra secundaria de Macetech, Noto Sans, en Japonés
<img src="/assets/img/capitulo-5/style-guidelines/general/typography/noto-sans-japanese.png"  alt="
Noto Sans font thickness models in Japanese" width="1000" height="580">

**Tipo de Letra Complementaria:**

En aquellos escenarios en los que dependemos exclusivamente de las fuentes instaladas en los dispositivos de los usuarios, por ejemplo, en campañas de correo electrónico, notificaciones SMS o documentos generados localmente, hemos optado por Arial como tipografía complementaria. Arial es una fuente sans-serif de sistema ampliamente disponible en Windows, macOS, Linux y la mayoría de clientes de correo, lo que garantiza que nuestro contenido se renderice de manera uniforme y coherente sin necesidad de descargas adicionales (Jay y Lupton, 2024).

- **Compatibilidad universal:**

  Arial forma parte de la lista de “web-safe fonts” y está preinstalada en prácticamente todos los entornos de usuario, eliminando posibles inconsistencias o caídas a fuentes de sustitución que podrían afectar la legibilidad (Google, 2025).

- **Claridad en pantalla:**

  Su trazo sencillo y proporciones equilibradas favorecen la lectura en tamaños pequeños, típicos de los visores de correo y pantallas de dispositivos móviles, evitando el “aliasing” excesivo y garantizando una experiencia clara incluso con bajos niveles de zoom (Jay y Lupton, 2024).

- **Rendimiento optimizado:**

  Al no requerir la descarga de recursos externos, reduce la latencia de apertura de correos electrónicos y mejora la entrega de mensajes SMS con texto formateado, asegurando que el usuario reciba y vea el contenido de inmediato.

Con esta elección, aseguramos que nuestras comunicaciones críticas lleguen siempre con la máxima fiabilidad tipográfica, sin comprometer la estética ni la claridad del mensaje.

###### Figura 40

_Modelos de grosor para el tipo de letra complementaria de Macetech, Arial_

<img src="/assets/img/capitulo-5/style-guidelines/general/typography/arial-font-thickness.png"  alt=" Arial font thickness models" width="1000" height="580">

#### 5.1.1.3. Espaciado

El espaciado es un pilar imprescindible para garantizar una óptima legibilidad, establecer una jerarquía visual sólida y proporcionar al usuario una experiencia de lectura fluida y confortable en todas las plataformas de Macetech. Con el fin de alcanzar estos objetivos, hemos implementado un sistema modular fundamentado en una unidad base de 8 px y sus múltiplos (8 px, 16 px, 24 px, 32 px, etc.).

**Tono de comunicación y lenguaje aplicado:**

Este enfoque ofrece varias ventajas técnicas y de usabilidad:

- **Consistencia de diseño:** Al ceñirnos a valores uniformes, eliminamos discrepancias arbitrarias entre márgenes y rellenos, logrando divisiones homogéneas en cada vista.

- **Escalabilidad y mantenimiento:** Definir espaciados como variables o tokens facilita la creación de una cuadrícula (CSS Grid) coherente y simplifica futuras ampliaciones o ajustes, reduciendo el tiempo de desarrollo y el riesgo de errores (Wang et al., 2025).

- **Previsibilidad y eficiencia:** Tanto diseñadores como desarrolladores pueden predecir con precisión el impacto de cada valor de espaciado en el conjunto de la interfaz, lo que mejora la productividad y la calidad del código.

- **Optimización de respuesta:** En entornos responsivos, los múltiplos de 8 px permiten adaptar rápidamente los layouts a distintos breakpoints sin comprometer la armonía espacial ni generar cambios bruscos en la composición (Kuleszo, 2024).

- **Reducción de la carga cognitiva:** Un espaciado predecible facilita la navegación y la comprensión del contenido, al crear “vías visuales” claras que guían naturalmente la mirada del usuario (Wang et al., 2025).

Macetech logra una experiencia visualmente equilibrada y técnicamente robusta, manteniendo la coherencia entre tipografía, componentes de UI y distintos contextos de uso.

**Principios Generales de Espaciado**

- **Unidad Base de 8 px**

  Todos los márgenes, rellenos (padding) y gutters del sistema de diseño se establecen en múltiplos exactos de 8 px (8, 16, 24, 32 px, etc.). Esto permite la construcción de una cuadrícula modular uniforme, evitando la proliferación de valores arbitrarios que puedan romper la coherencia visual. Asimismo, simplifica la implementación en CSS mediante variables o design tokens, reduciendo la complejidad del mantenimiento y facilitando ajustes globales de espaciado (Wang et al., 2025).

- **Consistencia Vertical**

  El espaciado vertical que separa bloques de texto, secciones y componentes se rige por la escala de 8 px -> 16 px -> 24 px -> 32 px. Esto establece un ritmo visual coherente que orienta al usuario de manera intuitiva a lo largo del contenido. Además, refuerza la jerarquía de información, diferenciando claramente los niveles de importancia sin recurrir a cambios bruscos de estilo (Kuleszo, 2024).

- **Jerarquía Tipográfica**

  Cada nivel de encabezado (H1, H2, H3 ...) y párrafo aplica un line-height proporcional al tamaño de fuente. Este debe ser entre 1.3× y 1.5× su tamaño base. Esto optimiza la legibilidad al garantizar un espacio vertical suficiente entre líneas, reduciendo la tensión ocular y facilitando la lectura continua.Asimismo, define con precisión los límites de cada bloque de texto, evitando la sensación de agrupamiento excesivo y mejorando la escaneabilidad de la página (Kuleszo, 2024).

**Espaciado Tipográfico**

A continuación se presenta la pauta de espaciado para los distintos elementos de texto en Macetech, optimizada para legibilidad, jerarquía y mantenibilidad. Además del line-height interno, se indica que el espaciado entre bloques de texto (márgenes inferiores) debe ser equivalente a un doble interlineado, garantizando una separación clara y uniforme.

| Elemento              | Tamaño de fuente | Altura de línea | Espacio entre letras | Margen inferior (2× altura de línea) |
| --------------------- | ---------------- | --------------- | -------------------- | ------------------------------------ |
| H1 (Título principal) | 32 px            | 40 px (1.25×)   | –0.5 px              | 80 px                                |
| H2                    | 24 px            | 32 px (1.33×)   | –0.4 px              | 64 px                                |
| H3                    | 20 px            | 28 px (1.4×)    | –0.3 px              | 56 px                                |
| Párrafo (cuerpo)      | 16 px            | 24 px (1.5×)    | 0 px                 | 48 px                                |
| Texto auxiliar        | 14 px            | 20 px (1.43×)   | 0 px                 | 40 px                                |

###### Figura 41

_Distribución de las alturas de línea con el margen inferior para la tipografía de Macetech_

<img src="/assets/img/capitulo-5/style-guidelines/general/spacing/line-heights-distribution-with-bottom-spacing.png"  alt="
Line heights distribution with the bottom spacing" width="1000" height="580">

- **Altura de línea interna (1.5–2.0x)**

  Proporciona suficiente espacio entre líneas para minimizar la tensión ocular y facilitar el seguimiento de la lectura, sin dispersar visualmente cada bloque de texto (Budarina, 2023).

- **Espaciado negativo para letras en encabezados**

  Un espaciado ligeramente negativo ayuda a compensar la menor densidad aparente de los títulos grandes, mejorando la cohesión de las palabras y el bloque tipográfico (Budarina, 2023).

- **Margen inferior es igual al doble de la altura de línea**

  Establecer el espaciado entre bloques de texto al doble de la altura de línea garantiza:

  1. Separación clara de secciones, evitando la acumulación visual de párrafos y encabezados.

  2. Ritmo de lectura coherente, pues la proporción se adapta automáticamente a cada tamaño tipográfico.

  3. Mantenimiento sencillo en CSS, al derivar los márgenes directos de los valores de line-height mediante variables o cálculos.

Con estas directrices, Macetech consigue una estructuración tipográfica técnica y elegante, en la que cada texto se distribuye adecuadamente y la jerarquía de la información resulta inmediatamente evidente.

**Espaciado de Componentes**

En Macetech, el espaciado de los componentes de interfaz se define para garantizar usabilidad, legibilidad y coherencia visual. A continuación se detallan las métricas de padding interno, margen externo vertical y gutter horizontal, así como su justificación:

| Componente               | Padding Interno                       | Margen Externo Vertical | Gutter Horizontal | Justificación                                                                                                                                                                                    |
| ------------------------ | ------------------------------------- | ----------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Botón                    | 12 px (vertical) × 24 px (horizontal) | 8 px                    | -                 | Proveé un área táctil confortable (mínimo 44 × 44 px recomendado por accesibilidad) y otorga una separación adecuada con elementos vecinos para clics precisos (World Wide Web Consortium, 2025) |
| Campo de entrada (Input) | 10 px (vertical) × 16 px (horizontal) | 12 px                   | -                 | Es un espacio interno óptimo para texto y placeholder. Tiene un margen que evita solapamientos en formularios densos y mejora el foco visual para el usuario                                     |
| Tarjeta (Card)           | 16 px                                 | 24 px                   | 16 px             | Otorga un espacio y distribución interna para contenido múltiple. Ocupa un margen generoso para diferenciar cards, junto a un gutter igual al padding para tener un grid coherente               |
| Grid / Container         | -                                     | -                       | 16 px             | Otorga una separación uniforme entre columnas en layouts de varias columnas, mantiene consistencia con el gutter de tarjetas y favorece la lectura escaneable                                    |
| Navbar / Sidebar         | 24 px                                 | -                       | -                 | Otorga un relleno amplio para iconos y etiquetas, además asegura zonas de interacción espaciosas y otorga claridad en la navegación                                                              |

###### Figura 42

_Distribución de los componentes funcionales utilizados en la interfaz de Macetech_

<img src="/assets/img/capitulo-5/style-guidelines/general/spacing/components-distribution-with-padding.png" alt="
Components distribution with padding" width="1000" height="580">

- **Padding interno:** Brindamos un espacio mínimo alrededor del contenido dentro de cada componente, lo que es esencial para que los componentes “respiren” sin comprometer el alineamiento (Zeldman, 2024).

- **Margen externo vertical:** Hay una distancia entre un componente y el siguiente en el flujo de la página, lo que previene la sensación de aglomeración y refuerza la separación semántica (Budarina, 2023).

- **Gutter horizontal:** Lo utilizamos como un separador constante entre columnas o tarjetas en un grid. Asegura un ritmo visual uniforme y facilita el escaneo lateral de información (Zeldman, 2024).

Este sistema de espaciado promueve una interfaz equilibrada, accesible y fácil de mantener, alineada con los principios de diseño modular en múltiplos de 8 px.

**Directrices de Agrupamiento, Alineación y Adaptabilidad**

Para maximizar la coherencia visual y la eficiencia en la interpretación de la interfaz de Macetech, se establecen las siguientes pautas de espaciado general, basadas en principios de diseño de sistemas escalables y prácticas de interacción centradas en el usuario.

- **Agrupamiento Semántico:** El agrupamiento semántico consiste en utilizar el espaciado como mecanismo de señalización para definir relaciones lógicas entre elementos:

  - **Márgenes internos reducidos (8 px)**

    Se emplean entre componentes funcionalmente relacionados (por ejemplo, icono con etiqueta, campo de formulario con ayuda contextual) para indicar unidad de pertenencia.

  - **Márgenes externos ampliados (24–32 px)**

    Se reservan para separar secciones independientes (bloques de contenido, paneles de navegación, áreas de análisis de datos), creando zonas abiertas que ayudan al usuario a identificar claramente el inicio y el fin de cada módulo de información.

  El contraste de espacios facilita el agrupamiento perceptivo (Principio de proximidad de Gestalt), reduciendo la carga cognitiva al segmentar visualmente la pantalla en áreas de interés (Zeldman, 2024).

- **Alineación Consistente:** La alineación de todos los elementos de la interfaz se fundamenta en una cuadrícula modular de 8 px, aplicada tanto en ejes verticales(eje y) como horizontales(eje x):

  - **Ejes verticales:** márgenes superiores e inferiores, altura de línea y gutters de contenedores siguen múltiplos de 8 px para asegurar un flujo de lectura fluido.

  - **Ejes horizontales:** gutters entre columnas y padding lateral de contenedores se ajustan a la misma unidad, manteniendo una división homogénea.

  El empleo de un grid consistente optimiza la formalización de CSS Grid, facilita alineaciones responsivas y reduce las discrepancias derivadas de cálculos manuales, mejorando la mantenibilidad del código (Budarina, 2023).

- **Escalado Responsivo:** Para garantizar una experiencia óptima en distintos dispositivos y tamaños de pantalla, el espaciado se adapta mediante breakpoints manteniendo siempre la base de 8 px. Según Zeldman(2024), los breakpoints son los puntos donde el diseño cambia para adaptarse a diferentes tamaños de pantalla y dispositivos. Son las medidas de ancho de pantalla en las que se aplican estilos CSS específicos, creando diferentes layouts para diferentes dispositivos, como móviles, tablets y escritorios:

  - **Móviles (En promedio, menor a 768 px):** se conserva la unidad base de 8 px y sus primeros múltiplos (8, 16, 24 px), optimizando la densidad de información sin sacrificar la claridad.

  - **Tablets y Escritorio (Mayor a 768 px):** se introducen múltiplos superiores (32, 40, 48 px) para incrementar zonas de descanso visual y aprovechar el espacio adicional de forma equitativa para los usuarios. No se invalidan o modifican las reglas de espaciado indicadas en este guía.

  Este enfoque en el que planteamos el diseño principal para móviles primero, aseguramos que la interfaz escale de forma progresiva, evitando saltos abruptos en el layout y manteniendo un ritmo visual coherente a través de los breakpoints definidos.

- **Beneficios del Sistema de Espaciado Modular**

  - **Orden y legibilidad:** cada elemento dispone de espacio suficiente para evitar la sensación de aglomeración.

  - **Accesibilidad:** agrandar márgenes entre secciones reduce el riesgo de errores de interacción táctil y mejora la escaneabilidad para usuarios con baja visión.

  - **Coherencia de marca:** un espaciado uniforme refuerza la identidad visual de Macetech, ofreciendo una experiencia profesional y sólida.

  - **Eficiencia de implementación:** la definición de variables de espaciado simplifica el mantenimiento y posibilita ajustes globales con un mínimo esfuerzo de desarrollo.

Con estas directrices, Macetech garantiza una interfaz ordenada, accesible y cohesiva, en la que cada componente encuentra su espacio natural sin perder armonía ni estructura.

#### 5.1.1.4. Tono de comunicación y lenguaje aplicado

De acuerdo con Smith y Zook (2024), el tono de comunicación es un componente esencial en el diseño de las secciones de una aplicación. No solo moldea la percepción emocional de los usuarios sobre textos e íconos, sino que también contribuye a forjar una identidad de marca coherente y memorable. Un tono bien calibrado genera en el usuario sensaciones de cercanía y confianza, al tiempo que un lenguaje claro y accesible refuerza la visibilidad en buscadores y facilita su navegación interna.

En esta sección detallamos las directrices de Lenguaje Utilizado de Macetech, diseñadas para asegurar una comunicación coherente, efectiva y alineada con nuestra identidad de marca en todos los puntos de contacto. Aquí encontrarás la descripción de nuestra voz de marca y los tonos contextuales que adaptan esa voz a situaciones específicas, desde mensajes de bienvenida hasta alertas críticas y notificaciones rutinarias. Además, incluiremos pautas prácticas sobre vocabulario preferido, estilo gramatical y adaptaciones multicanal, de modo que todos los equipos de contenido y diseño puedan aplicar un lenguaje claro, accesible y emocionalmente resonante para fortalecer la experiencia del usuario en Macetech.

- **Tono y voz:**

  En esta sección vamos a establecer la personalidad y las variaciones de nuestro lenguaje para que cada interacción refuerce la identidad de Macetech, genere confianza y mejore la experiencia de cuidado de plantas.

  La voz de Macetech es la forma consistente en que nos comunicamos en todos los canales. Nuestra voz es:

  - **Cálida y empática:**

    Reconocemos que cada usuario cuida de un ser vivo: hablamos con cercanía y comprensión.

  - **Experta pero accesible:**

    Ofrecemos conocimientos de monitoreo y cuidado basados en datos, pero evitando tecnicismos innecesarios.

  - **Optimista y motivadora:**

    Celebramos cada logro, desde un riego correcto hasta un brote nuevo, para mantener al usuario comprometido.

  El tono adapta nuestra voz al escenario de uso, modulando la energía y formalidad del mensaje:

  | Contexto                  | Objetivo                       | Tono principal          | Tono alternativo |
  | ------------------------- | ------------------------------ | ----------------------- | ---------------- |
  | Onboarding y Bienvenida   | Generar vínculo inicial        | Entusiasta y acogedor   | -                |
  | Éxitos y Recompensas      | Reforzar logros y motivar      | Celebratorio            | -                |
  | Alertas preventivas       | Avisar con urgencia moderada   | Claro y directo         | Empático breve   |
  | Errores críticos          | Informar y guiar solución      | Sobrio y tranquilizador | -                |
  | Consejos                  | Educar y acompañar paso a paso | Amigable y didáctico    | -                |
  | Notificaciones rutinarias | Recordar sin invadir           | Respetuoso & breve      | Cordial breve    |

  Esta estructura de voz y tono garantiza que, sin importar el punto de contacto, ya sea aplicación móvil, correo o aplicación web, Macetech hable con una personalidad única, coherente y alineada a los valores de sostenibilidad, innovación y proximidad que caracterizan nuestra marca.

- **Principios Fundamentales de Comunicación:**

  Estos principios guían cada texto e interacción dentro de Macetech, garantizando claridad, consistencia y conexión emocional:

  - **Claro y conciso:**

    Usa oraciones breves y directas.

    Evita jerga técnica innecesaria; cuando debas introducir un término especializado, acompáñalo de una breve explicación.

  - **Empático y humano:**

    Reconoce las necesidades y emociones del usuario.

    Emplea un lenguaje positivo que refuerce la confianza (“¡Buen trabajo!”, “Sabemos que tus plantas te importan”).

  - **Útil y orientado a la acción:**

    Prioriza la información que ayuda al usuario a resolver tareas o entender pasos (“Para ajustar el nivel de humedad, desliza este control…”).

    Incluye siempre llamadas a la acción (CTAs) claras y concretas.

  - **Consistente y reconocible:**

    Mantén el mismo estilo de redacción (voz activa, estructura de párrafos, longitud de líneas) en toda la plataforma.

    Usa vocabulario y fórmulas de saludo o despedida uniformes para reforzar la identidad de marca.

  - **Accesible e inclusivo:**

    Adapta el lenguaje para ser comprensible por usuarios de distintos niveles de experiencia.

    Asegúrate de que el contraste de texto y color cumpla con las pautas de accesibilidad y que las instrucciones sean claras para todos.

- **Patrones de Uso:**

  A continuación se presentan ejemplos de mensajes antes y después de aplicar nuestro modelo de Voz y Tono, según distintos contextos de interacción:

  | Contexto               | Cuándo usarlo                                 | Ejemplo(antes)                  | Ejemplo(después)                                                                      |
  | ---------------------- | --------------------------------------------- | ------------------------------- | ------------------------------------------------------------------------------------- |
  | Onboarding             | Primera vez que el usuario abre la aplicación | “Bienvenido a la aplicación.”   | “¡Bienvenido a Macetech! Empecemos a cuidar tus plantas juntos.”                      |
  | Mensaje de éxito       | Tras completar una acción de riego            | “Riego completado.”             | “¡Genial! Tu planta acaba de recibir su riego óptimo.”                                |
  | Alerta preventiva      | Nivel de humedad bajo o alto                  | “Nivel de humedad bajo.”        | “Atención: tu planta necesita agua. Ajusta el riego para mantenerla saludable.”       |
  | Error crítico          | Fallo en sensores o guardado de datos         | “Error al guardar datos.”       | “Ups… No pudimos registrar la información. Revisa tu conexión y vuelve a intentarlo.” |
  | Consejo educativo      | Sugerencia de mantenimiento o fertilización   | “Fertiliza tu planta cada mes.” | “Para un crecimiento óptimo, aplica fertilizante ligero una vez al mes.”              |
  | Notificación rutinaria | Recordatorios diarios o semanales de cuidado  | “Recordatorio de cuidado.”      | “¡Hola! No olvides revisar el nivel de humedad de tu planta hoy.”                     |

- **Vocabulario y estilo:**

  Esta sección define las palabras, expresiones y convenciones que refuerzan la identidad de Macetech y aseguran coherencia en todos los textos.

  - **Palabras clave y términos recomendados:**

    Selecciona siempre términos que conecten con el propósito de Macetech y eviten ambigüedades:

    | Categoría            | Términos recomendados                                                                                                    | Por qué                                               |
    | -------------------- | ------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------- |
    | Acciones principales | "Regar", "Monitorear", "Nutrir"                                                                                          | Verboes directos, centran al usuario en la tarea.     |
    | Estados de planta    | “Saludable”, “Sedienta”, “En crecimiento”                                                                                | Palabras concretas que reflejan condiciones reales.   |
    | Logros y motivación  | “¡Perfecto!”, “¡Excelente!”, “Logrado”                                                                                   | Tono positivo que celebra el éxito.                   |
    | Consejos y guías     | “Para optimizar…”, “Te recomendamos…”, “Prueba a…”                                                                       | Introducen recomendaciones de forma suave y empática. |
    | Advertencias         | “Atención:”, “Importante:”, “Precaución:” Llamadas de alerta claras sin incentivar la preocupación excesiva o el pánico. |

  - **Palabras prohibidas:**

    Evita jergas técnicas, modismos regionales o vocabulario que pueda resultar confuso:

    - **Términos excesivamente técnicos:**

      Ejemplos: “conductividad eléctrica”, “osmolaridad”, "gineceo", "solastalgia"

      Solo se pueden usar cuando vayan acompañados de una breve explicación accesible y de fácil comprensión.

    - **Coloquialismos informales:**

      Ejemplos: “chevere”, “buena onda”, “chamba”.

    - **Acrónimos sin definir:**

      Ejemplos: IoT (Internet de las Cosas)

      Si es necesario usarlos, se deben explicar, por lo menos, la primera vez que sean utilizados.

    - **Frases largas y pasivas:**

      Prefiere la voz activa con oraciones de máximo 30 palabras en los mensajes o textos que tenga la aplicación, a menos que estos sean descriptivos o explicativos.

  - **Convenciones de gramática y puntuación:**

    - **Voz activa:**

      Es necesario aplicar una voz activa en todo momento. Utilizar frases como “La app registra la humedad” en lugar de “La humedad es registrada por la app”.

    - **Longitud de línea:**

      Para asegurar legibilidad tanto en móviles como en computadores, es necesario que las línea tengan un máximo de entre 60 y 65 caracteres.

    - **Interlineado:**

      Para evitar la fatiga ocular en los usuarios es necesario que haya un interlineado de entre 1.5 y 2LS.

    - **Uso de listas:**

      Si es necesario el uso de listas, estas deben estar con viñetas para pasos o características, y deben estar enumeradas en caso de procesos secuenciales.

    - **Uso de comillas:**

      Se deben utilizar comillas angulares (« ») o latinas (“ ”) para fragmentos textuales que requieran su uso. Se debe evitar el uso de comillas simples (‘ ’).

  - **Formato y énfasis:**

    - **Negrita:**

      El uso de negrita es solo para resaltar conceptos clave o acciones en los mensajes que presente la aplicación al usuario, como (“**Regar la planta**”).

    - **Cursiva:**

      El uso de cursiva es solo para términos técnicos introducidos, o términos que no tengan traducción directa al idioma que está empleando el usuario, ya sea por anglicismos o matices culturales, como ("_trade-off_")

    - **Mayúsculas:**

      El uso de mayúsculas es solo para nombres propios de la marca o siglas, como ("MACETECH", "IoT").

    - **Emojis:**

      El uso de emojis esta permitido solo en notificaciones informales y mensajes de éxito para reforzar cercanía, como (“¡Listo! 🌱”).

      Los emojis están prohibidos en textos formales (alertas críticas, documentación legal).

  - **Lenguaje accesible:**

    - **Género neutro:**

      Se debe hablar en segunda persona (“tú”) o usar plural inclusivo (“[email protected]”).

    - **Claridad:**

      Se debe evitar dobles negaciones y construcciones complejas.

  - **Accesibilidad:**

    Se debe asegurar de que las etiquetas de botones y enlaces describan claramente la acción (“Ver historial de riego” vs. “Ver más”).

- **Adaptaciones Multicanal:**

  Para asegurar que la voz y el tono de Macetech se mantengan consistentes y efectivos, adaptamos ligeramente el estilo según el canal de interacción:

  - **Aplicación Móvil:**

    - **Mensajes breves y directos:**

      Deben tener una longitud máxima de entre 45 y 55 caracteres. Se debe priorizar la información esencial para no abrumar al usuario.

    - **Notificaciones push:**

      Se debe usar un tono cercano y motivador para entusiasmar o interesar al usuario, como (“¡Hora de regar tu planta! 🌱”)

      Asimismo, siempre se debe incluir una acción clara para el usuario, como (pulsar para abrir la app).

    - **Onboarding in-app:**

      Al iniciar se debe fragmentar el tutorial en pasos cortos.Asimismo, se debe combinar texto conciso con elementos visuales (íconos verdes) y CTA claros (“Siguiente”, “Entendido”).

    - **Errores y alertas:**

      Debe utilizar texto mínimo para describir lo que es el problema y la posible solución en dos líneas. Asimismo, se deben agregar botones de acción ("Reintentar", "Ajustar sensor").

  - **Plataforma Web:**

    - **Textos más extensos:**

      Deben tener una longitud máxima de línea de entre 60 y 65 caracteres. Se debe priorizar la información esencial para no abrumar al usuario.

      Se permite el uso de párrafos de 2–3 oraciones para explicar funcionalidades y beneficios.

    - **Correos electrónicos:**

      Se debe utilizar un encabezado personalizado, como ("Hola, [Nombre del usuario]"). Es necesario utilizar un tono amigable pero informativo; incluyendo enlaces con texto descriptivo (“Ver guía completa de cuidado”).

    - **Centro de ayuda y documentación:**

      Se debe utilizar un formato FAQ: preguntas en negrita y respuestas concisas (1–2 oraciones). Asimismo, se deben ingresar instrucciones paso a paso numeradas junto screenshots con bordes grises para enfocar la atención.

#### 5.1.1.5. Logo

En esta sección se establecen las directrices detalladas para el uso, las variaciones permitidas y las restricciones del logotipo de Macetech, con el propósito de salvaguardar su integridad gráfica, garantizar su óptima legibilidad y mantener una coherencia de marca homogénea en todos los medios, formatos y plataformas (Wheeler y Meyerson, 2024).

**Versión Principal del Logotipo**

La versión principal del logo de Macetech combina un símbolo icónico con la denominación de la marca, garantizando reconocimiento inmediato y coherencia visual.

- **Composición:** Para comprender la esencia de nuestro producto Macetech, cada elemento del logotipo ha sido concebido con un propósito simbólico y funcional:

  - **Símbolo**

    - **Forma:** Una maceta minimalista de líneas suaves que contiene un brote naciente, aludiendo directamente al crecimiento vegetal que obtendran las plantas por usar nuestro producto.

    - **Corazón interno:** Integrado sutilmente en la base del brote, representa el compromiso humano y emocional con el cuidado de las plantas. Su presencia simboliza tanto la pasión de nuestros usuarios como la “inteligencia” tecnológica que Macetech aporta.

    La superposición de naturaleza y tecnología sintetiza la propuesta de valor de Macetech: facilitar un cuidado preciso y afectivo de de las plantas mediante nuestras macetas inteligentes.

  - **Logotipo textual (Wordmark)**

    - **Tipografía:** DynaPuff. Es una fuente sans-serif con trazos redondeados, generosos contrates y terminaciones suaves que evocan cercanía y calidez visual.

    - **Legibilidad:** Sus formas abiertas y claras aseguran lectura instantánea en tamaños reducidos, esencial para interfaces y materiales digitales en los que se usara Macetech.

    - **Personalidad de marca:** Las curvas orgánicas de DynaPuff conectan con el mundo natural de las plantas, aportando un matiz amistoso que reduce la frialdad típica de las tipografías puramente geométricas (Zeldman, 2024).

    - **Coherencia visual:** Combina modernidad y accesibilidad, reflejando la dualidad de Macetech: tecnología avanzada al servicio de la vida vegetal (Zeldman, 2024).

    - **Posicionamiento:** La palabra “MaceTech” se sitúa debajo del símbolo, con un espacio horizontal equivalente al 40 % de la altura del ícono.

  - **Función del espacio**

    - **Jerarquía:** Refuerza la importancia del símbolo como identificador visual mientras mantiene la legibilidad del nombre en todo momento para nuestros usuarios.

    - **Distribución gráfica:** Garantiza un margen suficiente para evitar sensación de aglomeración, facilitando el uso del logotipo en contextos de distintos tamaños sin perder integridad.

    - **Alineación:** La línea de base de la palabra “MaceTech” queda perfectamente alineada con el centro geométrico del símbolo, generando un eje horizontal de equilibrio. Esta alineación transmite estabilidad y unidad, reforzando la confianza del usuario en la marca y su solución tecnológica.

    ###### Figura 43

    _Presentación del logotipo de Macetech_

    <img src="/assets/img/capitulo-5/style-guidelines/general/logo/logo-model-macetech.png" alt="Macetech's Logo" width="1000" height="580">

- **Proporciones:** Las proporciones del logo tienen una distribución que debe respetarse en todo momento, sin excepción. Las proporciones utilizadas en el logo se ven en el siguiente apartado.

  - **Relación de aspecto:** Relación con respecto a "Altura del ícono : Anchura total", lo que es igual a "1 : 1.2". La configuración del símbolo y la tipografía en relación 1:1.2 promueve una estructura visual equilibrada que refuerza el impacto de marca en cualquier tamaño (Bhanarkar et al., 2023).

  - **Escalado:** Al redimensionar, siempre se debe mantener esta proporción para evitar distorsiones y preservar la legibilidad de la tipografía en todo momento, sin importar el tamaño de la pantalla del dispositivo en el que se presenta.

- **Paleta de Color Autorizada** Usamos un modelo de paleta de color único que se guía de nuestro modelo de colores mencionados anteriormente en esta guía de diseño.

  - **Full Color (predeterminada)**

    - **Maceta y texto:** Verde Bosque #296244. Este refleja la identidad ecológica y tecnológica de Macetech.

    - **Hojas:** degradado vertical de Verde Bosque #38865D (parte superior) a Verde Hoja #2A8050 (parte inferior).

    - **Corazón:** Rojo Tomate #E74C3C. El Rojo Tomate destaca el elemento humano (corazón) y aporta energía visual.

    - **Uso:**

      Sitios web, presentaciones, materiales de marketing y cualquier superficie de marca donde se disponga de color completo de tonalidad verdosa clara.

  - **Versión en Blanco**

    - **Símbolo y texto:** Blanco #FFFFFF

    - **Uso:**

      Sobre fondos oscuros o fotografías de alta complejidad, siempre que el contraste cumpla con WCAG 2.1 AA (mínimo 4.5:1) para garantizar visibilidad (World Wide Web Consortium, 2025).

  - **Versión en Negro**

    - **Símbolo y texto:** Negro #000000

    - **Uso:**

      Aplicaciones monocromas en documentos impresos, grabados o interiores de menor colorido, siempre sobre fondos claros que aseguren legibilidad (World Wide Web Consortium, 2025).

  Las versiones blanca y negra aseguran flexibilidad de uso en contextos de contraste limitado, manteniendo la coherencia y el reconocimiento de la marca.

- **Zona de Protección (Clear Space):** Para preservar la integridad visual y la legibilidad del logotipo de Macetech en cualquier entorno, es imprescindible respetar un área libre de interferencias alrededor de su contorno.

  La zona de protección es el área mínima libre de texto, gráficos, bordes o cualquier otro elemento que pueda competir por la atención del espectador o dificultar la percepción del logotipo. Este espacio garantiza que el logotipo “respire” y mantenga su presencia y jerarquía visual (Zeldman, 2024).

  El valor de la zona de protección se define como el doble de la altura de la letra “M” en la palabra “MaceTech” del logotipo. La “M” es el carácter de mayor ancho y altura dentro de la palabra “MaceTech” y, por tanto, representa la dimensión más restrictiva para asegurar espacio libre. Al basar la distancia en esta medida interna, el área de protección se ajusta automáticamente a cualquier escala del logo sin requerir cálculos adicionales. Dado que la “M” forma parte del propio logotipo, este método funciona con la misma unidad (px, mm, pt) en la que se reproduzca y se puede referenciar con facilidad en CSS para el diseño (Kuleszo, 2024).

  Este valor se aplica uniformemente a los cuatro costados (superior, inferior, izquierdo y derecho). Si la “M” mide h (en mm, px o la unidad correspondiente), la zona de protección será un cuadrado de lado 2h adyacente a cada borde del logotipo.

  Esto nos otorga distintos beneficios, como:

  - **Visibilidad y legibilidad:** Evita que elementos gráficos o tipográficos cercanos distraigan la vista o distorsionen la silueta del logotipo.

  - **Jerarquía de marca:** Mantiene el logotipo como punto focal, asegurando que su reconocimiento no se vea afectado por componentes adyacentes.

  - **Adaptabilidad:** Al basar la medición en la propia geometría del logotipo, la zona de protección escala de forma consistente en todos los usos y formatos.

  ###### Figura 43

  \*Presentación del área de protección indicada para la buena distribución del logo

  <img src="/assets/img/capitulo-5/style-guidelines/general/logo/protection-area-for-logo.png" alt="Macetech's Logo Protection Area" width="1000" height="580">

- **Tamaño Mínimo:** Establecer dimensiones mínimas para el logotipo garantiza que sus detalles, tanto en el símbolo como en la tipografía, se reproduzcan con fidelidad en distintos medios y resoluciones.

  - **Ancho mínimo recomendado: 100 px**

  - Optimizado para pantallas de baja densidad (72 ppi) y alta densidad (Retina).

  - Asegura un espaciado mínimo de píxeles para las líneas del ícono y los contornos de la tipografía, evitando el “pixel snapping” que degrada la forma (Kuleszo, 2024). Por debajo de este umbral, los contornos de la fuente pueden perderse, afectando la legibilidad en dispositivos móviles y navegadores de escritorio.

  - Para tamaños superiores a los mínimos, mantenga la proporción 1:1.2 (altura : anchura) y la zona de protección predeterminada, escalándolas de manera proporcional.

  - En entornos de baja resolución (por ejemplo, pantallas 1×), verifique en mockups reales que el logotipo se perciba con claridad antes de su despliegue masivo.

  Con estas directrices formales y técnicas, se asegura que el logotipo de Macetech conserve su fuerza gráfica y su capacidad de comunicación en cualquier soporte, sin perder legibilidad ni detalle.

- **Usos Incorrectos del Logotipo**

  Para garantizar la integridad visual, coherencia de marca y reconocimiento consistente del logotipo de Macetech, es imprescindible evitar cualquier alteración que comprometa su estructura, colorimetría o legibilidad. A continuación se detallan los usos que están estrictamente prohibidos:

  - **Alteraciones de forma o proporción**

    No se permite estirar, comprimir, distorsionar ni modificar la relación de aspecto del logotipo bajo ninguna circunstancia. El logotipo debe mantenerse en su proporción original (1:1.2 entre ícono y texto) en todas las escalas.

  - **Modificaciones cromáticas no autorizadas**

    Está prohibido modificar los colores institucionales definidos (verde primario, rojo tomate, blanco o negro según fondo). No se deben aplicar degradados arbitrarios, filtros de color, transparencias o esquemas no contemplados en la guía oficial.

  - **Adición de efectos visuales**

    No se permite el uso de sombras paralelas, biseles, relieves, brillos, contornos ni texturas que alteren la apariencia original del logotipo. Estos efectos comprometen la claridad del diseño y afectan la percepción profesional de la marca.

  - **Aplicación sobre fondos inadecuados**

    El logotipo no debe colocarse sobre fondos de bajo contraste, imágenes complejas, patrones ruidosos o superficies que dificulten su visibilidad.

    En tales casos, se debe utilizar la versión blanca o negra del logotipo, según el contraste necesario, o añadir una caja de color de fondo que garantice su legibilidad.

  - **Manipulación del contenido del logotipo**

    Está prohibido rotar, inclinar, recortar, animar parcialmente o reemplazar elementos del logotipo, ya sea el ícono, la tipografía o ambos. No deben integrarse frases, eslóganes ni elementos externos dentro del área de seguridad definida.

    ###### Figura 44

    _Presentación de los usos incorrects del logotipo de Macetech_

    <img src="/assets/img/capitulo-5/style-guidelines/general/logo/logo-incorrect-uses.png" alt="Macetech's Logo Incorrect Uses" width="1000" height="580">

- **Formatos de Archivo del Logotipo**

  Para asegurar su correcta implementación en distintos medios y soportes, el logotipo de Macetech se distribuye en formatos optimizados según el tipo de uso. A continuación se especifican los formatos oficiales autorizados:

  - **Formatos vectoriales (uso escalable y profesional)**

    - **.SVG (Scalable Vector Graphics):** Uso recomendado para entornos digitales responsivos como sitios web, aplicaciones móviles o interfaces UI. Ofrece alta escalabilidad sin pérdida de calidad. Es de peso liviano y es editable por código (Budarina, 2023).

  - **Formatos rasterizados (uso fijo en pantalla o documentos)**

    - **.PNG (Portable Network Graphics):** Formato ideal para presentaciones, interfaces digitales o recursos web. Ofrece un fondo transparente, buena resolución, y tiene un peso moderado (Budarina, 2023).

    - **.PDF (Portable Document Format):** Recomendado para documentación oficial, entregables corporativos, presentaciones o reportes. Es un formato universal con alta fidelidad de reproducción. Proveé una alta integridad gráfica en todos los dispositivos (Budarina, 2023).

  - **Consideraciones generales**

    - No se debe reconstruir manualmente el logotipo ni exportarlo desde capturas de pantalla o plataformas de terceros.

    - Todos los formatos deben obtenerse exclusivamente desde el repositorio oficial de identidad visual de Macetech.

    - Para asegurar la correcta aplicación, se recomienda validar la resolución, contraste y proporción del logotipo en el medio destino antes de su publicación.

#### 5.1.1.6 Iconografía

La iconografía de Macetech es fundamental para transmitir estados, acciones y atributos de forma visual, clara y accesible a todos nuestros usuarios sin excepción. No solo deben ser visualmente atrayentes, sino también rápidamente identificables, intuitivos y correctamente distribuidos. La consistencia en el uso de íconos refuerza la identidad visual de la aplicación y mejora la experiencia del usuario en plataformas Web, iOS y Android (Zeldman, 2024).

**Principios Generales de Iconografía**

| Principio     | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Claridad      | Cada ícono debe transmitir un único concepto reconocible al primer vistazo, evitando cualquier ambigüedad semántica. Para ello, se recomienda emplear metáforas visuales universales y contrastar la silueta con el fondo siguiendo un espaciado mínimo de 1 px alrededor de la forma principal, de modo que la figura no se confunda con elementos vecinos <br><br> Además, los pictogramas deben diseñarse a partir de formas geométricas básicas (círculos, rectángulos, triángulos), simplificando trazos innecesarios para maximizar su legibilidad en tamaños reducidos |
| Consistencia  | El sistema de íconos debe compartir un conjunto homogéneo de parámetros: grosor de trazo constante (2 px en viewport estándar), terminaciones (cap ends) uniformes, ángulos de esquinas (Esquinas redondeadas de radio entre 2 y 4 px) y paleta de rellenos o contornos predefinida <br><br> Este enfoque garantiza que, aunque cada ícono represente conceptos distintos, la familia remita a una misma identidad visual y facilite la percepción de agrupamiento dentro de la interfaz                                                                                      |
| Escalabilidad | Los íconos deben mantener integridad visual desde 16 px hasta 64 px sin pérdida de detalle ni “ruido” gráfico. Para ello, se emplea diseño vectorial (SVG) con hinting en píxel grid cuando sea necesario, ajustando vértices a límites de 1 px para preservar la nitidez en pantallas de baja densidad <br><br>. Además, se definen versiones intermedias (ej. 24 px, 32 px, 48 px) en las que, de ser preciso, se eliminan detalles menores y se refuerzan los trazos principales para optimizar la legibilidad en dispositivos pequeños                                    |
| Accesibilidad | Nunca utilizar un ícono como único recurso informativo ante usuarios con discapacidades visuales; siempre acompañarlo de texto alternativo (atributo aria-label) y/o tooltip descriptivo. <br><br> Se garantiza contraste suficiente entre el ícono y su fondo (ratio mínimo 3:1 para componentes no críticos y 4.5:1 para textos e íconos interactivos) <br><br> Para usuarios de lector de pantalla, cada ícono debe incluir un role="img" y un aria-hidden="false" junto con su etiqueta textual (World Wide Web Consortium, 2025).                                        |

**Detalles de implementación**

Los siguientes detalles siempre deben ser aplicados antes de agregar un ícono en el programa por parte del diseño de experiencia de usuario e interfaz de usuario:

- **Formato:**

  **SVG:** Se recomienda el uso de SVG como formato principal para todos los íconos, exportados sin metadatos innecesarios y optimizados con herramientas como SVGO (v2+) para minimizar peso de archivo.

  **Web Components:** Incluir los íconos como componentes reutilizables que expongan propiedades de tamaño (width, height) y color (fill, stroke) para facilitar tokens de tema.

- **Naming y Organización:**

  Seguir la convención icono-concepto-estado (por ejemplo, icono-humedad-activo, icono-agua-desactivado), agrupando los SVG en carpetas semánticas por dominio funcional (sensores, acciones, estados)

  Mantener un archivo maestro (sprite o símbolo SVG) que permita cargar solo los íconos necesarios y simplifique la gestión de versiones

- **Safe Area y Padding:**

  Definir una “zona segura” interna de 1–2 px (según tamaño) alrededor de cada ícono para evitar clipping en diferentes motores de renderizado (browsers, apps móviles)

  Alinear siempre el centro geométrico del trazo principal con el centro del canvas (viewBox) para asegurar transiciones y animaciones fluidas.

**Estilo de Íconos**
El sistema de iconografía de Macetech adopta un enfoque visual coherente y funcional, fundamentado en principios de diseño minimalista, jerarquía cromática y semiótica contextual. A continuación se describen los elementos fundamentales que definen su estilo gráfico:

- **Estilo Gráfico**

  - **Trazado:**

    Se emplea un estilo lineal (outline) con trazos de grosor uniforme (2 px), lo que facilita la escalabilidad y la consistencia visual en todos los tamaños.
    <br>
    Los extremos de línea (stroke caps) deben ser redondeados para transmitir una estética amigable, alineada con los valores de sostenibilidad y bienestar de la marca.
    <br>
    Las uniones (stroke-linejoin) también deben ser redondeadas para evitar vértices agresivos.

  - **Simplicidad formal:**

    Las figuras deben construirse a partir de formas geométricas básicas y evitar ornamentos o detalles superfluos. Se prioriza la silueta reconocible y la armonía visual con otros elementos de interfaz.

- **Uso de Relleno**

  - **Relleno contextual (semifilled icons):**

    En casos específicos de señalización o alertas, se permite el uso de relleno plano parcial o total para aumentar la notoriedad del ícono y reforzar su carga semántica. Ejemplos incluyen:

    - Íconos de advertencia o estados críticos (por ejemplo, alerta, advertencia de riego) con relleno rojo si es una alerta grave o amarillo si es moderado. Recuerde utilizar los colores asignados según la guía de colores.

    - Indicadores de condición (necesita agua, exceso de luz) con uso combinado de contorno y relleno según el nivel de urgencia.

    El relleno debe seguir el mismo esquema de color institucional y estar limitado a un máximo del 60% del área del ícono, para mantener la legibilidad del contorno principal.

- **Paleta Cromática**

  El color cumple una función semántica y jerárquica, guiando al usuario en la interpretación rápida del estado o función del ícono. La paleta ha sido seleccionada con base en criterios de contraste, accesibilidad (WCAG AA mínimo) y coherencia con la identidad visual de Macetech:

  ###### Tabla 30 y algo

  _Descripción de usos de colores para los íconos de Macetech en modo light_

  | Métrica                        | Nombre   | Hex     | Uso                                                                                                                                                                                        | Justificación técnica                                                                                                                             |
  | ------------------------------ | -------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
  | Humedad y Temperatura Fría     | Azul Mar | #3498DB | Utilizado en barras/áreas de visualización de humedad y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Sigue una base de paleta categórica: azul es convencional para humedad, alto contraste con fondo y consistente con dashboards de las métricas IoT |
  | Luz y Alerta Moderada          | Mostaza  | #F1C40F | Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas en un nivel moderada                                     | El amarillo brillante remite al sol, además de ser legible sobre gris oscuro y blanco                                                             |
  | Temperatura Media              | Brasas   | #E67E22 | Utilizado para mostrar el rango medio de temperatura                                                                                                                                       | Naranja medio comunica calor moderado, siendo una diferenciación clara entre rangos                                                               |
  | Temperatura Alta y Alerta Alta | Tomate   | #E74C3C | Utilizado para mostrar el rango alto de temperatura y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas a un nivel alto                               | Rojo intenso para alertas de calor, puesto que es una semántica cultural de peligro. Asimismo, tiene un contraste AAA con colores blancos         |
  | pH                             | Tallo    | #2ECC71 | Utilizado como medidor de acidez/alcalinidad (pH)                                                                                                                                          | Verde para pH neutro/seguro, lo que armoniza con primarios y tiene un contraste 4.5:1.                                                            |
  | Salinidad                      | Neblina  | #1ABC9C | Utilizado como medidor de salinidad                                                                                                                                                        | Tonos turquesa evocan agua salada, lo que es distintivo frente a otros sensores.                                                                  |

  ###### Tabla 30 y algo

  _Descripción de usos de colores para los íconos de Macetech en modo Dark_

  | Métrica                        | Nombre    | Hex      | Uso                                                                                                                                                                                        | Justificación                                                                                                                                                   |
  | ------------------------------ | --------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
  | Humedad y Temperatura Fría     | Azul Lago | #2980B9  | Utilizado en barras/áreas de visualización de humedad y botones de riego o iconos relacionados a la humedad de la planta. Asimismo, se utiliza para mostrar una barra con baja temperatura | Es un azul moderado, menos saturado para evitar fatiga ocular en los usuarios. Tiene un contraste AAA sobre el color #343541. Mantiene una semántica de frescor |
  | Luz y Alerta Moderada          | Mostaza   | #F39C12  | Utilizado en indicadores de nivel de luz y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas en un nivel moderada                                     | Se utiliza un amarillo ligeramente atenuado para no deslumbrar ante el cambio de colores. Tiene un contraste AAA contra un fondo oscuro                         |
  | Temperatura Media              | Zanahoria | #D35400  | Utilizado para mostrar el rango medio de temperatura                                                                                                                                       | Se utiliza un naranja oscuro que sigue diferenciando niveles de temperatura. Tiene un contraste AA/AAA con texto blanco y fondos oscuros                        |
  | Temperatura Alta y Alerta Alta | Tomate    | #C0392B  | Utilizado para mostrar el rango alto de temperatura y para resaltar plantas que necesitan ser revisadas porque sus métricas no son adecuadas a un nivel alto                               | El uso de un rojo menos brillante suaviza el impacto, sin perder señal de alerta. Presenta un buen contraste AAA                                                |
  | pH                             | #27AE60   | Llanura  | Utilizado como medidor de acidez/alcalinidad (pH)                                                                                                                                          | Un verde más oscuro que el primario para no confundirse con elementos estáticos. Presenta un contraste AAA con el color blanco                                  |
  | Salinidad                      | #16A085   | Turquesa | Medidor de salinidad                                                                                                                                                                       | Se usa el color turquesa profundo que evoca agua salada nocturna. Tiene un contraste AAA contra el fondo en modo oscuro                                         |

Todos los colores deben cumplir un ratio de contraste mínimo de 4.5:1 sobre fondo blanco o claro para garantizar su legibilidad y accesibilidad (World Wide Web Consortium, 2025).

No se deben utilizar gradientes ni sombras en los íconos para mantener la claridad visual y facilitar la integración en sistemas oscuros o de alto contraste. Los íconos deben mantenerse monocromáticos por defecto, aplicando color mediante propiedades de estilo (stroke, fill) en CSS o mediante tokens de diseño.

De ser necesario, en estados de desactivación o elementos inactivos, se recomienda aplicar una opacidad del 40% al ícono y su color de base.

**Íconos Utilizados en el Dashboard**

La iconografía implementada en el dashboard de Macetech cumple una función clave en la comunicación visual de estados, acciones e interacciones del sistema. Cada ícono ha sido seleccionado y diseñado para maximizar la legibilidad, semántica intuitiva, y coherencia funcional con el ecosistema visual de la plataforma.

A continuación se detalla el conjunto base de íconos con su función específica, estilo requerido y consideraciones de implementación. Primero se mostraran emojis de ejemplo y después se mostrara la hoja con todos los íconos respectivos:

###### Tabla 30 y algo

_Listado de íconos de estado de planta y sensores ambientales utilizados en la aplicación de Macetech, junto a un ejemplo en forma de emoji_

| Emoji de ejemplo  | Uso                                                | Descripción Técnica                                                                                                                                                       |
| ----------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🍃 Hoja           | Indicador general del estado de la planta          | Representación abstracta de la hoja de una planta con bordes suaves. Es grande y abierta. Sirve como ícono de estado de salud de las plantas o resumen del estado vegetal |
| 🌡️ Termómetro     | Temperatura ambiente o del sustrato                | Ícono de termómetro lineal con escala. Se vincula a una métrica numérica y una barra de color que refleja la temperatura                                                  |
| 💧 (dos gotas)    | Humedad del sustrato                               | Conjunto de dos gotas en disposición cercana para indicar nivel de humedad. Estilo lineal, acompañado por barra de progreso y etiqueta textual                            |
| 🌞 Sol            | Nivel de exposición lumínica                       | Sol minimalista de 10 rayos, indica el nivel de luz percibido por el sensor. Se acompaña de lectura numérica e indicador visual                                           |
| 🧪 Ácido (pH)     | Nivel de acidez del sustrato                       | Representación de tubo de ensayo o símbolo de pH. Refleja el nivel ácido-básico, visualizado en escala de color                                                           |
| 🧂 Salinidad      | Nivel de sales en el suelo                         | Ícono representando un cristal o salero simplificado. Asociado a valores de conductividad eléctrica                                                                       |
| ♻️ Proceso activo | Activación de procesos automáticos (como el riego) | Ícono de carga circular o animación de progreso. Se muestra durante la ejecución de tareas automáticas del sistema IoT                                                    |

###### Tabla 30 y algo

_Listado de íconos de alerta utilizados en la aplicación de Macetech, junto a un ejemplo en forma de emoji_

| Emoji de ejemplo                         | Nivel de Alerta | Descripción Técnica                                                                                                         |
| ---------------------------------------- | --------------- | --------------------------------------------------------------------------------------------------------------------------- |
| 🔴 ❗ (Círculo rojo con exclamación)     | Crítica         | Se utiliza cuando múltiples variables de la planta están fuera de los rangos óptimos. Prioriza acción inmediata del usuario |
| 🟡 ❗ (Círculo amarillo con exclamación) | Media           | Indica una sola condición anómala o en advertencia. Permite intervención preventiva                                         |

###### Tabla 30 y algo

_Listado de íconos de interacción y navegación utilizados en la aplicación de Macetech, junto a un ejemplo en forma de emoji_

| Emoji de ejemplo | Uso                | Descripción Técnica                                                                                                   |
| ---------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------- |
| ➕               | Añadir elemento    | Ícono de suma con trazo lineal. Se utiliza en botones para agregar macetas, sensores o programar tareas de riego      |
| 🔔               | Notificaciones     | Campana estilizada, sin relleno. Puede presentar un badge rojo cuando hay alertas pendientes con el número de alertas |
| 👤               | Perfil de usuario  | Ícono de busto humano genérico, se emplea para acceder a opciones de cuenta y configuración personal                  |
| 🪴               | Gestión de macetas | Ícono de maceta cilíndrica, representa el acceso a la vista general de todas las plantas o unidades registradas       |
| 👑               | Membresía          | Corona minimalista de tres puntas. Utilizada para representar planes avanzados del sistema                            |
| ⬅️➡️             | Movimiento         | Flechas dobles horizontales o verticales para representar acciones de navegación o desplazamiento entre vistas        |

###### Figura 45

_Listado de íconos utilizados en las plataformas de Macetech_

<img src="/assets/img/capitulo-5/style-guidelines/general/icons/macetech-icons.png" alt="Macetech's Icon List" width="1000" height="580">

**Adaptaciones a distintos dispositivos**

La iconografía debe adaptarse cuidadosamente a las convenciones de diseño, comportamientos esperados y características técnicas de cada plataforma objetivo. Esto garantiza una experiencia de usuario coherente, accesible y optimizada tanto en entornos móviles como web.

- **Plataforma Móvil (Android / iOS):**

  - **Estándares de diseño por sistema operativo:**

    - **Android:** Se recomienda utilizar la familia de íconos Material Symbols, siguiendo las guías de Material Design 3 (Google, 2025).

    - **iOS:** Para interfaces desarrolladas en entornos Apple, emplear íconos del sistema SF Symbols (versión 4 o superior), respetando las pautas de uso definidas por Human Interface Guidelines (Apple Inc., 2025).

  - **Compatibilidad con modo oscuro:**

    Los íconos deben ser vectoriales y adaptarse automáticamente al modo claro u oscuro, empleando tonos neutros o variantes automáticas (dynamic system colors) en cada sistema. Recordar los colores dark mode revisados en el apartado de colores del Style Guidelines.

  - **Tamaños sugeridos:**

    - **Navegación y barra de herramientas:** 24 px

    - **Íconos destacados o interactivos principales:** 32 px

  - **Ubicación y jerarquía:**

    Acciones primarias (como "Añadir Maceta") deben implementarse como Floating Action Button (FAB), centradas en la parte inferior de la pantalla según patrón de diseño de la plataforma. Se debe asegurar un mínimo de 48×48 dp como área táctil efectiva por ícono interactivo, incluso si el ícono visual mide menos.

- **Plataforma Web:**

  - **Estándares y recursos recomendados:**

    Utilizar íconos vectoriales en formato SVG, optimizados para escalabilidad, contraste y compatibilidad con navegadores modernos. Se debe emplear la biblioteca Angular Material para todo tipo de diseño (Google, 2025).

  - **Tamaños sugeridos:**

    - **Menús de navegación lateral o superior:** 24 px

    - **Paneles principales, tarjetas de contenido o widgets:** 32 px

  - **Tooltips y accesibilidad:**

    Todo ícono interactivo debe mostrar un tooltip contextual al pasar el cursor (hover). Implementar atributos aria-label para garantizar el cumplimiento de pautas WCAG 2.1 y facilitar el acceso mediante lectores de pantalla (World Wide Web Consortium, 2025)

  - **Modo oscuro:**

    Integrar íconos SVG con color dinámico mediante clases de CSS (currentColor) para que se ajusten automáticamente al tema del sistema o preferencia del usuario.

**Buenas Prácticas de Iconografía**

Para garantizar una comunicación visual efectiva, accesible y coherente, es fundamental seguir principios de diseño centrados en la usabilidad, la legibilidad y la consistencia contextual. A continuación se detallan las buenas prácticas para el uso de iconografía en el ecosistema de Macetech:

- **Prácticas no recomendadas:**

  - Evitar el uso de íconos puramente decorativos que no aportan valor semántico o funcional. Estos elementos pueden generar ruido visual, distraer al usuario o aumentar la carga cognitiva innecesariamente.

  - No utilizar íconos genéricos o ambiguos para estados críticos o alertas, como simples signos de exclamación sin contexto visual o semántico. Esto dificulta la interpretación inmediata y puede afectar la respuesta del usuario ante eventos importantes.

- **Prácticas recomendadas:**

  - Acompañar siempre los íconos con etiquetas textuales, especialmente en botones, indicadores de métricas, tarjetas o elementos interactivos. Esto mejora la accesibilidad, apoya la comprensión inmediata del usuario y facilita la navegación, especialmente para usuarios con discapacidades visuales o cognitivas.

  - Personalizar íconos representativos del sistema, como los de humedad, luz o salud vegetal. Su diseño debe reflejar visualmente su funcionalidad específica, manteniendo una identidad visual coherente con la marca. Esto contribuye a generar familiaridad y una curva de aprendizaje más corta.

  - Diseñar íconos con intención semántica, es decir, cada ícono debe representar con claridad la acción, estado o entidad asociada. Evitar simbolismos abstractos o culturalmente ambiguos.

  - Mantener la coherencia visual en cuanto al estilo (lineal, grosor uniforme), proporciones y alineación con los elementos de la interfaz.

### 5.1.2. Web, Mobile and IoT Style Guidelines

El presente apartado establece las directrices de diseño visual y experiencia de usuario (UX/UI) que regirán la implementación coherente de la solución en sus tres plataformas principales: web, móvil e IoT. Estas guías divididas aseguran la armonización estética y funcional de la interfaz en distintos entornos tecnológicos, permitiendo una experiencia de usuario homogénea, eficiente y accesible, independientemente del dispositivo utilizado.

Cada subapartado aborda de forma específica los principios, estilos y restricciones aplicables a su respectiva plataforma, detallando aspectos clave como paleta cromática, tipografía, iconografía, estructura de interacción y criterios de adaptabilidad. Este enfoque modular permite alinear los estándares de diseño con las capacidades técnicas y expectativas de los usuarios en cada contexto operativo.

#### 5.1.2.1. Web Style Guidelines

##### 5.1.2.1.1. Sistema de cuadrícula y espaciado

A continuación se detalla de forma exhaustiva el Sistema de cuadrícula y espaciado para la Web Application de Macetech, con definición de columnas, márgenes, gutters y puntos de quiebre basados en estándares de la industria y mejores prácticas.

El sistema emplea un grid de 12 columnas fluido, márgenes laterales adaptados y gutters uniformes en múltiplos de 8 px, ajustados a tres rangos de breakpoint para garantizar legibilidad y consistencia en pantallas desde móviles hasta escritorio (Google, 2025).

**Columnas**

- **Rejilla de 12 columnas:**

  Cada columna dispone de un ancho equivalente que, al combinarse, permite construir diseños de 4, 8 o 12 fracciones.

  - **Ancho unitario aproximado:**

    - En **escritorio** (≥ 1024 px) cada columna mide un aproximado de 86 px

          (((1366 px – 2×32 px) – 11×24 px) / 12 )

    - En **tableta** (600–1023 px) cada columna mide un aproximado de 80 px

          (((800 px – 2×24 px) – 7×16 px) / 8)

    - En **móvil** (≤ 599 px) el diseño adopta una sola columna adaptable al ancho disponible menos _2×16 px_ de margen lateral.

  - **Ancho máximo de contenedor:**

    Para pantallas muy anchas, el contenedor principal se limita a 1366 px, centrado mediante márgenes automáticos, evitando que el contenido se extienda en exceso y pierda legibilidad.

  La unidad de medida interna emplea _grid-template-columns_, con "repeat(12, 1fr)" en CSS Grid, facilitando la asignación de spans variables a los elementos contenidos. Para diseños centrados, se limita el contenedor principal a un ancho máximo (max-width) de 1366 px, con laterales rellenos (padding-inline) proporcionales para mantener el contenido centrado en pantallas muy anchas.

**Márgenes y Gutters**

Los gutters (espacio entre columnas) se definen en múltiplos de 8 px, recomendando 24 px en escritorio y 16 px en tabletas para mantener un ritmo visual coherente.

- **Escritorio: 24 px**

- **Tableta: 16 px**

- **Móvil: n/a (columna única)**

Márgenes laterales (padding‑inline del contenedor):

- **Móvil: 16 px**

- **Tableta: 24 px**

- **Escritorio: 32 px**

Los márgenes laterales (padding-inline del contenedor) arrancan en 16 px en móviles, suben a 24 px en tabletas y 32 px en escritorio, garantizando que el contenido no quede pegado al borde de la ventana.

Estos valores deben implementarse como variables de espacio (design tokens), garantizando actualización global y coherencia en todos los componentes.

Tanto gutters como márgenes deben definirse mediante la propiedad CSS gap y variables (CSS custom properties o design tokens), favoreciendo la mantenibilidad y adaptabilidad.

**Breakpoints**

El sistema admite tres rangos de anchura, ajustándose en cada caso el número de columnas, gutters y márgenes:

| Rango      | Ancho de pantalla | Columnas | Gutters | Márgenes laterales | Comentario                                                                         |
| ---------- | ----------------- | -------- | ------- | ------------------ | ---------------------------------------------------------------------------------- |
| Móvil      | 0 px – 599 px     | 1        | -       | 16 px              | Contenido apilado verticalmente                                                    |
| Tableta    | 600 px – 1023 px  | 8        | 16 px   | 24 px              | Columnas combinables para secciones principales y secundarias con gutters de 16 px |
| Escritorio | ≥ 1024 px         | 12       | 24 px   | 32 px              | Permite layouts multicolumnas y dashboards complejos                               |

Cada punto de quiebre se define mediante media queries para adaptar la cuadrícula y mantener el ritmo visual en todas las resoluciones.

###### Figura 46?

_Modelo de cuadrícula con columnas, gutters y márgenes laterales utilizados por la aplicación web y su relación en distintos dispositivos_

<img src="/assets/img/capitulo-5/style-guidelines/web/grid/grid-and-spacing-system-for-app.png" alt="Grid and spacing system used for the web app interface" width="1000" height="580">

##### 5.1.2.1.2. Responsividad y Adaptabilidad

**Rangos de Anchura y Puntos de Quiebre**

| Dispositivo     | Ancho de ventana  | Columnas efectivas      | Márgenes | Gutters |
| --------------- | ----------------- | ----------------------- | -------- | ------- |
| XS – Móvil      | 320 px – 599 px   | 1 columna full‑width    | 16 px    | -       |
| SM – Tableta    | 600 px – 767 px   | 4 columnas              | 24 px    | 16 px   |
| MD – Desktop    | 768 px – 1023 px  | 8 columnas              | 24 px    | 16 px   |
| LG – Desktop    | 1024 px – 1365 px | 12 columnas             | 32 px    | 24 px   |
| XL – Ultra‑wide | ≥ 1366 px         | 12 columnas + centering | 32 px    | 24 px   |

- En XS, todo el contenido (tarjetas, formularios, menús) ocupa la única columna disponible, apilándose verticalmente con separaciones de 16 px.

- En SM, las tarjetas de sensores y formularios pueden disponerse en un grid de 2×2 (span de 2 columnas cada una), manteniendo gutters de 16 px.

- En MD y LG, la rejilla de 8 o 12 columnas permite distribuciones más complejas con menús laterales (span ≥ 2 columnas), dashboard principal (span ≥ 6–8 columnas) y paneles secundarios.

- En XL, se mantiene el máximo de 12 columnas pero centrándose el contenedor en un ancho máximo de 1366 px, con márgenes automáticos a izquierda y derecha.

**Comportamiento de Tarjetas, Menús y Formularios**

- **Tarjetas (Cards)**

  - **XS:** full‑width con padding interno de 16 px y margen inferior de 24 px.

  - **SM:** tarjetas apiladas en dos columnas con un total de cálculo de píxeles de:

        ((100% − 2×24 px)/2)

    Usa un gutter de 16 px y padding interno de 16 px.

  - **MD–LG:** tarjetas configurables en grids de 3–4 columnas (span de 2–3 fracciones), con gutter de 24 px en LG. Altura mínima uniforme de 200 px para consistencia.

**Menús de Navegación**

- **XS–SM:** menú colapsable (de tipo hamburger), desplegable full‑width con items apilados y separación vertical de 16 px.

- **MD–LG:** menú horizontal en header, ítems con padding lateral de 16 px y separación de 24 px. En dashboards, sidebar sticky (obligatorio) de span 2–3 columnas con padding interno de 24 px.

**Formularios y Controles**

- **Inputs:** ancho 100% en XS, span de 4–6 columnas en SM–MD, span de 3 columnas en LG. Padding interno de 12 px × 16 px, margen inferior de 16 px entre campos.

- **Selects y Dropdowns:** anchos alineados con inputs, comportamiento full‑width en XS, y agrupados junto a labels en MD–LG con gutter de 16 px.

- **Botones de formulario:** ancho 100% en XS, fit‑content en SM–LG con padding 12 px × 24 px, margen superior de 24 px.

###### Figura 47?

_Modelo de responsividad y adaptabilidad distribuida a las cuadrículas y los puntos de quiebre identificados en la aplicación web_

<img src="/assets/img/capitulo-5/style-guidelines/web/responsibility/responsibility-and-adaptability-grids-and-breakpoints-for-app.png" alt="Responsibility and adaptability gris with breakpoints for Macetech's web app" width="1000" height="580">

##### 5.1.2.1.3. Tipografía Adaptativa

Implementar una tipografía adaptativa no solo mejora la estética del sitio, sino que también fortalece la usabilidad y la percepción de profesionalismo del producto. Este enfoque va más allá del uso de unidades relativas como "em", "rem" o "vw"; implica pensar en escalas tipográficas fluidas, breakpoints estratégicos y una correcta combinación entre tipo y propósito del texto (títulos, párrafos, botones, etc.).

En esta sección se detallan las mejores prácticas, tecnologías recomendadas y criterios de accesibilidad para aplicar una tipografía verdaderamente adaptativa en nuestros productos digitales.

**Unidades Relativas (rem y em)**

Las unidades relativas permiten que todos los tamaños de fuente se comporten de forma proporcional al contexto:

- **"rem (root em)"** toma como referencia el tamaño base definido en el elemento raíz (html), garantizando coherencia global.

- **"em"** se basa en el tamaño de la fuente del propio contenedor, ideal para componentes independientes (botones, modales, tooltips) que requieran escalado interno sin alterar la jerarquía global.

**Métricas a utilizar**

- **Tamaño base:** 16 px (párrafo) → 1 rem (100% en html).

- **Títulos principales (H1–H3):** 2 rem – 1.5 rem - 1.25 rem (32 px - 24 px - 20px).

- **Cuerpo de texto:** 1 rem (16 px).

- **Texto auxiliar (captions, leyendas):** 0.875 rem (14 px).

- **Proporciones de contenedor:**

  En tarjetas o modales, ajustar el texto interno con "em" para mantener márgenes y espaciados proporcionales al tamaño de la fuente local utilizada.

**Uso de la función clamp()**

- **Rango fluido controlado**

  clamp() permite definir tres valores:

  - Un mínimo (fuente legible en móviles)
  - Un ideal (valor intermedio que crece con la pantalla)
  - Un máximo (evitando tipografías excesivamente grandes).

  ###### Tabla 40 y algo

  _Modelo de valores de la función clamp() asignados a cada uno de nuestros tipos de texto y encabezados_

  | Nivel tipográfico | Mínimo           | Ideal (fórmula)   | Máximo            |
  | ----------------- | ---------------- | ----------------- | ----------------- |
  | Texto auxiliar    | 0.75 rem (12 px) | 0.75 rem + 0.2 vw | 0.875 rem (14 px) |
  | Cuerpo de texto   | 1 rem (16 px)    | 1 rem + 0.5 vw    | 1.125 rem (18 px) |
  | H3                | 1.25 rem (20 px) | 1.25 rem + 1 vw   | 1.375 rem (22 px) |
  | H2                | 1.5 rem (24 px)  | 1.5 rem + 1.5 vw  | 1.75 rem (28 px)  |
  | H1                | 2 rem (32 px)    | 2 rem + 2 vw 2.25 |  rem (36 px)      |

- **Texto auxiliar (caption)**

  clamp(0.75 rem, 0.75 rem + 0.2 vw, 0.875 rem). Crece suavemente de 12 px en móviles hasta un máximo de 14 px en desktop, manteniendo claridad en leyendas y notas.

- **Cuerpo de texto**

  clamp(1 rem, 1 rem + 0.5 vw, 1.125 rem). Parte de 16 px en smartphones, escala hasta 18 px en pantallas anchas, asegurando una lectura cómoda sin saturar.

- **Encabezados**

  - **H3:** clamp(1.25 rem, 1.25 rem + 1 vw, 1.375 rem) (20 px a 22 px)

  - **H2:** clamp(1.5 rem, 1.5 rem + 1.5 vw, 1.75 rem) (24 px a 28 px)

  - **H1:** clamp(2 rem, 2 rem + 2 vw, 2.25 rem) (32 px a 36 px)

- **Beneficios**

  - **Sin saltos bruscos:** Los cambios son proporcionales al viewport, evitando “picos” de tamaño al pasar un breakpoint.

  - **Mayor control de jerarquía:** Cada nivel tipográfico mantiene su relación de proporción (Major Third) incluso al escalar.

  - **Legibilidad garantizada:** Los valores mínimos y máximos están dentro de rangos óptimos para lectura continua según estudios de usabilidad tipográfica.

  ###### Figura 48

  _Modelo de responsividad y adaptabilidad distribuida a las cuadrículas y los puntos de quiebre identificados en la aplicación web_

  <img src="/assets/img/capitulo-5/style-guidelines/web/adaptive-typography/adaptive-typography-with-clamp.png" alt="Model of adaptive typography with the clamp() function" width="1000" height="580">

**Líneas base y altura de línea**

La altura de línea y el espaciado entre bloques de texto son tan importantes como el tamaño de la fuente para garantizar una experiencia de lectura cómoda:

- **Altura de línea (line-height):**

  Para cuerpo de texto, emplear un valor entre 1.4× y 1.6× el tamaño de fuente. Esto equivale a 22 px – 24 px cuando la tipografía es de 16 px, y mejora la separación visual entre líneas sin fragmentar el párrafo.

  Para encabezados, se puede reducir ligeramente a 1.2× – 1.3× para reforzar la unidad del bloque.

- **Espacio entre bloques:**

  Definir un margen inferior equivalente a 2× la altura de línea del bloque anterior. Así, un párrafo con line-height: 24px tendrá un margin-bottom: 48px, creando una separación proporcional que facilita la escaneo visual y evita la congestión de texto.

- **Medida óptima de línea (measure):**

  Mantener entre 45 y 75 caracteres por línea para maximizar la legibilidad. Ajustar el ancho de los contenedores o la tipografía si este rango se supera, evitando que las líneas sean demasiado largas o demasiado cortas.

##### 5.1.2.1.4. Accesibilidad Web

Para garantizar que la Web Application de Macetech sea plenamente utilizable por la mayor cantidad de usuarios, incluyendo aquellos con discapacidades visuales, motoras o cognitivas, se implementa un conjunto de métricas cuantitativas y buenas prácticas de diseño alineadas con las pautas WCAG 2.1. A continuación se detallan con rigor técnico y semántico.

**Contraste de color**

El contraste cromático es esencial para la percepción nítida del contenido en pantalla. Se establecen los siguientes umbrales:

###### Tabla 40

_Modelo de contraste crómatico para la percepción nítida de las pantallas de los usuarios de Macetech_

| Tipo de elemento                            | Ratio mínimo                                                                          | Justificación técnica                                                                          |
| ------------------------------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Texto y elementos interactivos pequeños     | 4.5 : 1                                                                               | Asegura legibilidad de letras de hasta 18 pt y componentes táctiles pequeños (≥ 44×44 px).     |
| Texto grande (≥ 18 pt o ≥ 14 pt en negrita) | 3 : 1 Permite que títulos y encabezados destacados sean legibles con menor contraste. |
| Iconografía y bordes                        | 3 : 1                                                                                 | Garantiza que íconos de estado y contornos de cajas se distingan del fondo sin ser intrusivos. |
| Estados de foco                             | 3 : 1                                                                                 | El anillo de foco debe destacarse sobre el fondo y el elemento subyacente para no perderse.    |

- **Herramientas de verificación:**

  - **WebAIM Contrast Checker:** permite validar ratios exactos de la paleta crómatica.

  - **axe DevTools y Lighthouse (extensiones de navegador):** análisis automatizado de accesibilidad.

  - **Flujo de trabajo de diseño:** incorporar pruebas de contraste en etapas tempranas de prototipado (Figma, Sketch) mediante plugins especializados, evitando iteraciones costosas en desarrollo.

**Etiquetado semántico y ARIA**

El empleo de roles y atributos ARIA dota a la interfaz de una estructura semántica comprensible por lectores de pantalla:

###### Tabla 40

_Listado de atributos ARIA con distintas funciones utilizadas en el proyecto de Macetech_

| Componente           | Rol ARIA                              | Atributos adicionales                                                                        |
| -------------------- | ------------------------------------- | -------------------------------------------------------------------------------------------- |
| Íconos e imágenes    | _role="img"_                          | _aria-label="Descripción precisa"_ o _aria-labelledby_ vinculado a texto descriptivo cercano |
| Botones de acción    | _role="button"_                       | _aria-pressed_ para toggles, _aria-expanded_ para menús desplegables                         |
| Navegación principal | _role="navigation"_                   | _aria-label="Menú principal"_                                                                |
| Diálogos / modales   | _role="dialog"_ y _aria-modal="true"_ | _aria-labelledby_ (ID del encabezado del modal), _aria-describedby_ (ID de la descripción)   |
| Tablas de datos      | _role="table"_                        | Encabezados con _role="columnheader"_ y celdas con _role="cell"_                             |

- **Texto alternativo:** todos los iconos que transmiten información o acción deben llevar un _aria-label_ claro (por ejemplo: “Añadir nueva maceta”).

- **Agrupaciones lógicas:** emplear contenedores semánticos (<main>, <aside>, <header>, <footer>) junto con roles ARIA para reforzar jerarquías de contenido.

**Navegación con teclado**

Operar la interfaz íntegramente sin ratón responde a la necesidad de incluir a usuarios con limitaciones motrices, visuales o cognitivas que dependen de teclados, pulsadores adaptados o lectores de pantalla. Según el criterio 2.1.1 de WCAG 2.1 (World Wide Web Consortium, 2025), toda funcionalidad debe ser accesible mediante teclado, lo cual no solo cumple requisitos legales y normativos, sino que además mejora la experiencia de usuarios avanzados y facilita el uso en entornos donde el ratón no está disponible.

- **Objetivos de área de enfoque (hit target):** Mínimo 44 × 44 px por elemento interactivo (botones, enlaces, iconos táctiles). Espaciado adicional de 8 px alrededor para evitar activaciones accidentales.

- **Orden de tabulación lógico:** El índice de tabulación (tabindex) debe seguir el flujo Z patter (de izquierda a derecha, de arriba a abajo), también relativo a la pantalla. Elementos decorativos o informativos (sin acción) deben ser excluidos del tabulado (tabindex="-1").

- **Indicadores de foco claramente visibles:** Personalizar el estilo :focus con un outline de al menos 3 px de grosor y un offset de 2 px, usando el color de marca (verde #2A8050) para reforzar la coherencia visual. El contorno debe respetar el contraste mínimo 3 : 1 sobre el fondo y el elemento subyacente.

**Tipografía legible y escalable**

Si bien el apartado de tipografía adaptativa, ya visto en la sección anterior, profundiza en unidades y escalas, aquí recalcamos su papel en la accesibilidad para fomentar su uso y mantenerlo en cada una de nuestra plataformas:

- **Escala de lectura óptima:** garantizar que el cuerpo de texto pueda aumentar hasta un 200 % sin romper el layout, manteniendo líneas de entre 45 y 75 caracteres para evitar fatiga visual.

- **Altura de línea:** mínima de 1.5× para cuerpo de texto y 1.3× para encabezados, asegurando separación suficiente y evitando agrupamientos.

- **Distancias mínimas:** establecer un espaciado interbloque de al menos 24 px entre párrafos y secciones, facilitando la orientación de usuarios con baja visión.

#### 5.1.2.2. Mobile Style Guidelines

##### 5.1.2.2.1 Principios Generales de Interacción Móvil

La aplicación móvil de Macetech debe ofrecer interacciones táctiles naturales, rápidas y predecibles. Para ello, se incorporan métricas precisas de dimensiones de toque y patrones gestuales coherentes con las convenciones de plataforma, garantizando una experiencia cómoda y accesible.

**Tamaños de toque (Touch Targets)**

- **Dimensiones mínimas y áreas seguras:**

  48 × 48 dp es el área de toque mínima recomendada para botones, íconos interactivos y elementos de control. Esta dimensión asegura una zona táctil suficiente para la mayoría de usuarios, incluyendo aquellos con movilidad reducida o dedos de mayor tamaño.

  Siempre que sea posible, ampliar el área activa a 56 × 56 dp o 64 × 64 dp en elementos primarios (por ejemplo, botones de acción flotante, íconos clave del dashboard), aumentando la precisión y reduciendo errores de selección.

- **Padding invisible:**

  Se aconseja aplicar un “padding” interno extendido alrededor del visual del ícono para alcanzar el área mínima, sin alterar su tamaño gráfico.

- **Espaciado entre elementos**

  Mantener un espacio mínimo de 8 dp entre touch targets adyacentes para evitar activaciones accidentales.

  En listas o tarjetas, dejar un margen vertical de 16 dp entre filas, de modo que el usuario perciba claramente cada elemento como una unidad independiente.

  Los elementos críticos (como “Regar ahora” o “Añadir Maceta”) deben situarse en zonas “thumb‑friendly” de la pantalla (esquinas inferiores), considerando un radio de accesibilidad de al menos 90 dp desde los bordes.

###### Figura 30?

_Modelo de áreas de toque y espacios seguros asignados a los distintos elementos de la aplicación móvil de Macetech_

  <img src="/assets/img/capitulo-5/style-guidelines/mobile/gestures/touch-areas-for-mobile-and-safe-space.png" alt="Touch areas and safe space for components in mobile application" width="1000" height="580">

**Gestos y Patrones de Interacción**

- **Tap**

  Acción primaria para seleccionar ítems, abrir detalles o activar comandos inmediatos (p. ej., tocar una tarjeta de planta para ver su historial).

  **Respuesta visual:** cambio de fondo o “ripple” inmediato (< 100 ms) para reforzar la acción.

- **Double‑Tap**

  Reservado para funcionalidades avanzadas (p. ej., hacer “zoom” rápido en un gráfico de sensor). Debe usarse con moderación y siempre ofrecer alternativa de gesto único o botón secundario para accesibilidad.

- **Long‑Press**

  Invoca menús contextuales o acciones adicionales sin sobrecargar la interfaz principal

  **Respuesta visual:** 500 ms de presión constante. Mostrar feedback táctil (vibración breve) y visual (ligero cambio de opacidad) al activar.

- **Swipe horizontal**

  Navegación entre pestañas secundarias (Gráfico -> Historial -> Recomendaciones -> Alertas -> Reportes -> Programación).Debe requerir un desplazamiento de al menos 16 dp y terminar con un rebote suave si se alcanza el límite.

- **Swipe vertical:**

  Actualización de contenido (Pull‑to‑Refresh) en listas de alertas o notificaciones. El umbral de disparo es al arrastrar 60 dp hacia abajo, mostrando indicador de carga a 30 dp.

- **Drag & Drop**

  Uso puntual para reordenar listas de programación de riego o recomendaciones. Elemento arrastrado debe seguir el dedo con un shadow sutil y un scale de 1.05× para indicar estado activo.

###### Figura 30?

_Listado de patrones gestuales disponibles junto a sus directrices para el uso de la aplicación móvil de Macetech_

<img src="/assets/img/capitulo-5/style-guidelines/mobile/gestures/gesture-patterns-and-animations-in-mobile.png" alt="Gesture patterns and animations in Macetech's mobile application" width="1000" height="580">

**Transiciones y Animaciones**

- **Duración estándar:**

  - 200 ms – 300 ms para transiciones de pantalla (push/pull de vistas).

  - 150 ms – 200 ms para microinteracciones (botones, íconos).

- **Curvas de easing:**

  - Material Design recomienda el uso de Cubic‑Bezier(0.4, 0.0, 0.2, 1). Es una función de tiempo de animación CSS que define un ritmo específico para una transición o animación. En este caso, representa una curva de Bézier cúbica que se acelera lentamente al principio y luego acelera rápidamente, dando la impresión de un movimiento que se acelera gradualmente (Google, 2025).

- **Tipos de transiciones**

  - **Push / Pop de vistas**

    - **iOS:** Animación deslizante horizontal (“push” y “pop”) conforme a las Human Interface Guidelines, que simula el apilamiento y desempilamiento de vistas en una navegación jerárquica, reforzando la pila de pantallas (Apple Inc., 2025).

    - **Android:** Animación de “slide-in/out” vertical, característico de Material Design, que otorga una sensación de continuidad desde la parte inferior de la pantalla, acorde a la dirección natural del pulgar en dispositivos móviles (Google, 2025).

  - **Visibilidad de contexto**

    Durante la transición, mantener al menos el 80 % de la vista anterior visible durante el 50 % de la duración de la animación. Esta superposición parcial cumple dos funciones clave:

    - **Orientación espacial:** El usuario percibe simultáneamente el punto de partida y de llegada, reduciendo la sensación de “pérdida” al cambiar de contexto.

    - **Consistencia cognitiva:** Facilita el seguimiento mental del flujo de navegación, reforzando la relación entre las pantallas en términos de progresión de tareas.

    - **Duración recomendada:** 250 ms – 300 ms. Este intervalo se sitúa en el “sweet spot” de las transiciones fluidas (200 ms – 350 ms) identificado por investigaciones en experiencia de usuario, que equilibran rapidez y claridad sin generar sensación de lentitud ni brusquedad (Apple Inc., 2025)

  - **Bottom Sheets**

    - **Desplazamiento inicial:** 30 px de avance antes de soltar el elemento (threshold), siguiendo Material Design, para que el sistema distinga entre un gesto involuntario y la intención de abrir el panel (Google, 2025).

    - **Animación completa:** Deslizamiento hasta cubrir el 100 % de la altura de la zona designada (parcial o total) en 250 ms, optimizando la sensación de ligereza y respuesta inmediata. Esto mejora la relevancia de la información secundaria (programación de riego, historial) sin abandonar la vista subyacente.

  - **Modales centrados**

    - **Efecto de escala:** Crecimiento de 0.95× a 1.0× en 200 ms, complementado con un fade-in de opacidad desde 0 % a 100 %. El ligero “zoom” apela a la percepción táctil de enfoque, atrayendo la atención hacia el contenido modal sin desconectar bruscamente de la pantalla de fondo.

    - **Duración:** 180 ms – 220 ms, rango óptimo para indicar prioridad alta del modal y permitir a la interfaz reaccionar sin demoras perceptibles (Apple Inc., 2025).

  - **Feedback en acciones**

    - **Efecto de “ripple” o tinta**

      Radio inicial de 10 dp, expandiéndose hasta 24 dp en 300 ms con una opacidad máxima de 0.3 después de una interacción. Esto refuerza la certeza de que la pulsación ha sido registrada, aportando un feedback inmediato y localizado.

      Los valores de radio y opacidad reflejan los márgenes y la paleta cromática de Macetech, integrándose armoniosamente con el resto de microinteracciones.

    - **Variantes:**

      Para elementos de alto contraste (alertas, controles críticos), ajustar la opacidad al 0.5 para asegurar visibilidad.

      En modo oscuro, emplear colores invertidos o degradados sutiles para conservar el contraste y la percepción del efecto de tinta.

La navegación en dispositivos móviles debe organizarse de forma clara, predecible y accesible, respetando los patrones de interacción nativa de cada sistema y las limitaciones de espacio táctil. A continuación se desglosan tres componentes esenciales: Bottom Navigation vs. Drawer, Floating Action Buttons (FAB) y Headers Adaptativos, con sus métricas, justificaciones de diseño y recomendaciones de uso en Macetech.

##### 5.1.2.2.2 Jerarquía Visual y Navegación

La navegación en dispositivos móviles debe organizarse de forma clara, predecible y accesible, respetando los patrones de interacción nativa de cada sistema y las limitaciones de espacio táctil. A continuación se desglosan cuatro componentes esenciales: Bottom Navigation, Drawer, Floating Action Buttons (FAB) y Headers Adaptativos, con sus métricas, justificaciones de diseño y recomendaciones de uso en Macetech.

- **Bottom Navigation**

  Es una barra fija en la parte inferior de la pantalla que muestra entre 3 y 5 ítems principales de navegación. Es una opción clásica y adecuada para el desarrollo de aplicaciones móviles entre distintos sistemas operativos. Ocupa un espacio razonable y fomenta de forma activa la navegación con el usuario (Google, 2025).

  - **Altura recomendada:** 56 dp (Material Design) / 50 pt (iOS).

  - **Touch targets:** cada ícono ocupa al menos 48 × 48 dp, con un margen lateral mínimo de 16 dp entre ítems.

  - **Las principales ventajas de usar Bottom Navigation son:**

    - Visibilidad constante de las rutas primarias, reduciendo la carga cognitiva al usuario.

    - Posición “thumb‑friendly”, por lo que es accesible para pulgares en teléfonos de hasta 6.5″.

  - **Usos en la aplicación:**

    - Secciones de alto nivel (p. ej., Dashboard, Macetas, Membresías, Perfil).

    - Ideal para accesos frecuentes: “Mis Macetas”, “Alertas” y “Programación”.

    Según la ley de Fitts, los objetivos cercanos al borde inferior requieren menos tiempo de selección y ofrecen mayor precisión en un pulgar centrado o desviado ligeramente hacia un lado.

- **Navigation Drawer (Hamburger Menu)**

  Es un panel lateral deslizante que muestra rutas secundarias o poco frecuentes.

  - **Ancho mínimo:** 280 dp (Material) / 320 pt (iOS).

  - **Spacing interno:** 16 dp entre ítems, icono-texto 8 dp de separación.

  - **Las principales ventajas de usar Navigation Drawer son:**

    - Permite organizar un mayor número de destinos sin saturar la interfaz principal.

    - Adecuado para funciones avanzadas o configuraciones (p. ej., Ajustes, Ayuda, Términos).

  - **Usos en la aplicación:**

    Aunque es menos visible que la Bottom Navigation, su uso aún puede limitarse a tareas de baja frecuencia.Siempre asegurar un icono de acceso (hamburger) de 32 × 32 dp en la esquina superior izquierda del header.

    - Menús de configuración para datos de macetas o datos de perfil.

    - Menús de reportes para seleccionar distintas métricas para cada tipo de reporte necesario.

**Floating Action Buttons (FAB)**

Son botones circulares que representan la acción principal de la pantalla para el usuario.

- **Diámetro estándar:** 56 dp (Android) / 60 pt (iOS Adaptativo).

- **Área de toque efectivo:** 72 dp (12 dp de padding invisible).

- **Posicionamiento:** Esquinas inferiores, derecha en LTR (Left-To-Right), izquierda en RTL (Right-To-Left), situados a 16 dp del borde y 16 dp por encima de la Bottom Navigation o teclado incrustado. El FAB, al “flotar” sobre el contenido, atrae la atención y comunica prioridad, reduciendo ruido al aislar la acción más relevante para el contexto actual según Material Design Guidelines (Google, 2025).

- **Uso en Macetech:**

  - **Acción destacada:** “Añadir Maceta” o “Regar Ahora”.

  - En vistas de listado, permite agregar nuevos sensores o programaciones.

  * **Variantes:**

  - **Extended FAB:** botón alargado con icono y texto, mínimo 88 dp de ancho, para mejorar la claridad en acciones complejas (p. ej., “Programar Riego”).

**Headers Adaptativos**

Son encabezados flexibles que responden a cambios de contexto, scroll y jerarquía de la pantalla del usuario. Permite maximizar el área de contenido sin perder rastreo de la navegación. La dinámica de expansión y contracción mejora la orientación espacial del usuario y prioriza la información según contexto (Apple Inc., 2025).

- **Dimensiones:**

  - **Altura inicial:** 56 dp (Android) / 44 pt (iOS Safe Area + 44 pt).

  - **Altura contraída al hacer scroll:** reducir a 48 dp–50 dp, optimizando espacio.

- **Componentes habituales:**

  - Icono de navegación (back or menu), título de pantalla, iconos de acción (perfil, notificaciones).

  - **Espaciado interno:** 16 dp de padding horizontal, 8 dp entre iconos, 24 dp entre icono y título.

- **Comportamiento adaptativo:**

  - **Shrink on Scroll:** el header contrae su altura y puede ocultar el subtítulo o buscar, manteniendo solo el título principal.

  - **Collapsing Toolbar:** en pantallas de detalle, el header puede ampliarse para mostrar información adicional (imagen de la planta, nombre científico) antes de contraerse.

###### Figura 30?

_Modelo de jerarquía de componentes aplicados en la interfaz de usuario de la aplicación móvil de Macetech_

  <img src="/assets/img/capitulo-5/style-guidelines/mobile/hierarchy/visual-hierarchy-and-navigation-in-mobile.png" alt="Visual hierarchy and navigation in Macetech's Mobile Application" width="1000" height="580">

**Principios Generales**

- **Consistencia entre plataformas**

  Aunque Material Design y Human Interface Guidelines difieren en detalles, la estructura de navegación debe mantenerse coherente en iOS y Android, adaptando solo los matices de estilo y gestos nativos en todo momento.

- **Claridad en el estado activo**

  En los componentes Bottom Navigation y Drawer, resaltar el ítem activo con un cambio de color de icono y texto (por ejemplo, verde brote #38865D) y un subrayado o fondo semitransparente.

- **Accesibilidad**

  Todos los elementos de navegación deben tener un modelo de focus y cumplir con las áreas de toque mínimas.Se deben proveer etiquetas descriptivas (aria-label, accessibilityLabel) para lectores de pantalla.

- **Pruebas de usabilidad**

  Realizar tests con usuarios en dispositivos reales, evaluando la facilidad para alcanzar elementos y comprender la jerarquía.

##### 5.1.2.2.1. Android Style Guidelines

###### 5.1.2.2.1.1. Uso de Material Components (MDC)

Los Material Components (MDC) son los elementos de interfaz nativos recomendados por Android, diseñados con principios de accesibilidad, jerarquía visual, responsividad y usabilidad.

A continuación se detallan los más relevantes para la aplicación móvil de Macetech:

**Card**

Los Card contienen datos agrupados como tarjetas de plantas, historial de riego, métricas sensoriales. Las Card proveen un marco visual consistente para elementos que deben ser escaneados rápidamente y seleccionados como unidades.

- **Elevación:** elevation = 1dp para agrupaciones neutrales; hasta 8dp si se quiere destacar interacción.

- **Corner Radius:** 12dp en layouts móviles. Adaptativo en tablets.

- **Contenido para los cards:**

  - Icono
  - Título
  - Descripción corta
  - Gráfico embebido (miniatura)
  - Chip o botón secundario.

**FloatingActionButton (FAB)**

Los FAB muestran una acción principal por pantalla, como “Añadir planta”, “Programar riego”. El FAB actúa como affordance visual (sugerencia de uso) y funcional para tareas centrales. Su posición flotante reduce fricción y maximiza la eficiencia de interacción.

- **Tamaño:** normal (56dp) o extended (text + icon) cuando se requiere claridad contextual. "Usar contentDescription" obligatorio para lectores de pantalla.

- **Elevación:** 6dp resting / 12dp pressed.

- **Color:** usar color primario del sistema temático. Contraste mínimo de 4.5:1 con el fondo.

**Snackbar**

Los snackbar brindan retroalimentación no intrusiva tras acciones inmediatas (Por ejemplo “Riego activado”, “Planta añadida”). Usar action solo si es relevante (Por ejemplo “Deshacer”). Snackbar refuerza confianza del usuario sin bloquear el flujo ni requerir confirmación.

- **Tamaño:**

  - LENGTH_SHORT = 2000ms

  - LENGTH_LONG = 3500ms

- **Estética:**

  - Fondo semitransparente (elevationOverlay).

  - Texto de alto contraste.

  - Botón alineado a la derecha (action textColor = secondary color).

**TopAppBar (MDC Toolbar o CenterAlignedTopAppBar)**

El TopAppBar funciona para la navegación principal y contexto por pantalla. La barra superior en Android cumple una función de orientación y acción. Su presencia debe ser clara pero no dominante.

- **Altura estándar:** 64dp (modo móvil), con scroll de desaparición automática en listas largas. Expansión con CollapsingToolbarLayout si hay imágenes destacadas (dashboard de sensores).

- **Iconografía:** usar _start icon_ para navegación, _end icons_ para acciones rápidas (buscador, filtros).

- **Elevación dinámica:** de 0dp a 4dp en scroll para reforzar jerarquía.

###### Tabla 35

_Modelo de Métricas UI/UX recomendadas para los Material Components de Android_

| Componente | Tiempo de feedback visual | Altura mínima táctil | Elevación (reposo) | Elevación (activo) |
| ---------- | ------------------------- | -------------------- | ------------------ | ------------------ |
| Card       | < 100 ms                  | 48 dp                | 1–4 dp             | 6–8 dp             |
| FAB        | < 50 ms                   | 56 dp                | 6 dp               | 12 dp              |
| Snackbar   | 2000–3500 ms              | 48 dp                | 4 dp               | -                  |
| TopAppBar  | Instantáneo               | 64 dp                | 0 dp (scroll)      | 4 dp (sticky)      |

##### 5.1.2.2.2. iOS Style Guidelines

El diseño de interfaces para iOS debe seguir los principios de Human Interface Guidelines (HIG) de Apple, priorizando la claridad, consistencia, interactividad fluida y alineación con el sistema operativo. A continuación se detalla cómo y por qué deben usarse correctamente los componentes nativos de iOS: SF Symbols, UIKit y SwiftUI, con métricas y recomendaciones específicas para diseñadores y desarrolladores.

###### 5.1.2.2.2.1 Uso de SF Symbols: Iconografía universal y responsiva

SF Symbols es el sistema oficial de iconos vectoriales de Apple, integrado en iOS desde iOS 13. Están perfectamente alineados con el sistema visual del sistema operativo. Proporciona una escala perfecta con Dynamic Type y configuraciones de accesibilidad.

- 9 pesos de grosor diferentes (ultralight a black) para alinearse con distintos estilos de contenido.

- Incluye variantes multicolor (palette, hierarchical, multicolor) para distintos modos visuales (claro/oscuro).

- Fácil integración en UIKit y SwiftUI con un systemName.

| Propiedad | Recomendación para iOS | Justificación UX |
Tamaño base (icono) 20–28 pt Claridad en pantallas Retina
Espaciado mínimo 8 pt entre elementos Evita sobrecarga visual
Grosor sugerido regular o semibold Balance entre legibilidad y neutralidad visual
Color Ligado a label, secondaryLabel o paleta de acento (tint) Coherencia visual en modo claro/oscuro

#### 5.1.2.3. IoT Style Guidelines

En los dispositivos IoT de Macetech (módulos de maceta inteligente, estaciones de monitoreo, unidades edge), la interacción primaria se realiza a través de señales físicas: LEDs, vibración y sonidos. Estas señales deben diseñarse como un sistema coherente de patrones sensoriales, con métricas precisas, codificación semántica y comportamientos previsibles que refuercen la usabilidad y la confianza del usuario.

#### 5.1.2.3.1. Retroalimentación mediante LEDs

La retroalimentación visual mediante diodos emisores de luz (LEDs) constituye uno de los mecanismos más eficaces y eficientes para comunicar el estado de un sistema IoT al usuario final. Su bajo consumo energético, alta visibilidad, y capacidad para codificar información a través del color, la intensidad y los patrones de parpadeo, los convierten en un componente esencial en entornos donde la interfaz gráfica no siempre está disponible o el usuario requiere confirmaciones rápidas y tangibles.

**Especificaciones de componentes**

- **Tipo de LED:** LED de alta luminosidad, difuso (“lens diffused”) de 3 mm o 5 mm, según volumen del dispositivo.

- **Ángulo de visión:** mínimo 120 ° para garantizar visibilidad desde distintos ángulos de instalación (mesas, repisas, jardineras).

- **Corriente de operación:** típicamente 10 mA – 20 mA por LED.

- **Brillo (luminous intensity):**

  - **Verde:** ≥ 8 mcd a 20 mA

  - **Amarillo:** ≥ 5 mcd a 20 mA

  - **Rojo:** ≥ 6 mcd a 20 mA

- **Consumo energético:** Aproximadamente 0.06 W por LED. Optimizar los ciclos de parpadeo para reducir consumo en modos activos de larga duración.

**Montaje y óptica**

- **Difusores y lentes:** emplear cubiertas semitransparentes de policarbonato (transmisión mayor o igua a 85 %) con patrón de microestructura para dispersión uniforme de la luz.

- **Protección ambiental:** sellado IP54 en zonas de LED para evitar acumulación de polvo y humedad.

**Retroalimentación háptica (Vibración)**

- **Eccentric Rotating Mass (ERM)**

- **Amplitud:** 0.8 G – 1.2 G

- **Frecuencia de resonancia:** 180 Hz – 250 Hz

- **Tiempo de respuesta:** Menos de 20 ms

**Patrones de vibración**

- **Confirmación de acción:** un pulso único de 200 ms ON / 100 ms OFF.

Alerta crítica: secuencia de 3 pulsos (300 ms ON / 100 ms OFF), repetidos 2 veces, con pausa de 500 ms entre secuencias.

Emparejamiento: pulso breve de 100 ms cada 1 s durante 10 s máximo.

## 5.2. Information Architecture

La arquitectura de información de Macetech se ha diseñado para ofrecer una experiencia intuitiva y accesible tanto en la Landing Page como en las aplicaciones web y móvil, mediante sistemas organizativos jerárquicos y funcionales que guían al usuario desde la exploración inicial hasta la interacción avanzada. El contenido se estructura en categorías como “Mis Macetas”, “Alertas”, “Historial” y “Configuración”, con etiquetas claras y comprensibles validadas con usuarios reales, evitando tecnicismos innecesarios. La navegación será consistente entre plataformas, con un menú superior en web y uno inferior en móvil, y un sistema de búsqueda contextual que permite filtrar por nombre de planta, cliente o estado, especialmente útil para usuarios con múltiples macetas. Para mejorar la visibilidad del producto, se aplicarán etiquetas SEO con términos como “maceta inteligente”, “riego automático” y “monitoreo vegetal”, además de meta descripciones optimizadas para cada sección, asegurando que tanto usuarios domésticos como profesionales encuentren lo que necesitan sin esfuerzo.

### 5.2.1. Organization Systems

Macetech organiza el contenido de manera que los usuarios ya aficionados o profesionales de la jardinería puedan acceder fácilmente a la información y funcionalidades que necesitan. A continuación se describen los sistemas de organización visual y esquemas de categorización aplicados por plataforma:

- **Landing Page**
  | Sistema de Organización Visual | Aplicación Específica |
  | ------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
  | Jerárquica | La información se presenta de lo general a lo específico: _Propuesta de valor_, _Beneficios_, _Funcionalidades_, _Planes_. |
  | Secuencial | En secciones como _¿Cómo funciona?_ se guía al usuario paso a paso en el uso de Macetech. |

- **Web Application**

  | Sistema de Organización Visual | Aplicación Específica                                                                       |
  | ------------------------------ | ------------------------------------------------------------------------------------------- |
  | Jerárquica                     | Panel principal muestra alertas, macetas activas y métricas, seguidas de vistas detalladas. |
  | Matricial                      | Permite al usuario comparar macetas y plantas en tablas y gráficos paralelos.               |

  | Esquema de Categorización | Aplicación Específica                                                            |
  | ------------------------- | -------------------------------------------------------------------------------- |
  | Cronológico               | Historial de riego, alertas y cambios se presentan por fecha descendente.        |
  | Por tópicos               | Macetas, plantas, sensores, configuraciones y reportes se agrupan temáticamente. |

- **App Mobile**

  | Sistema de Organización Visual | Aplicación Específica                                                          |
  | ------------------------------ | ------------------------------------------------------------------------------ |
  | Jerárquica                     | Navegación desde el _Dashboard_ a detalles de cada planta, alerta o historial. |
  | Secuencial                     | Flujo de registro de macetas y configuración de alertas paso a paso.           |

### 5.2.2. Labeling Systems

En esta sección se definen los principios y decisiones de etiquetado que guían la forma en que los usuarios interpretan e interactúan con el contenido en la Landing Page, la App Web y la App Móvil. Se prioriza el uso de un lenguaje claro, consistente y orientado a la acción para facilitar la comprensión inmediata, reducir la carga cognitiva y mejorar la experiencia general de navegación. Las etiquetas han sido adaptadas al perfil de cada tipo de usuario, asegurando coherencia entre plataformas y facilidad de localización de funciones clave.

- **Landing Page**

  | **Conjunto de información**  | **Etiqueta usada**    | **Razonamiento**                                             |
  | ---------------------------- | --------------------- | ------------------------------------------------------------ |
  | Presentación general         | **Inicio**            | Término tradicional y esperado en sitios web.                |
  | Qué es Macetech              | **¿Qué es Macetech?** | Pregunta directa que despierta interés.                      |
  | Funcionalidades del producto | **Funciones**         | Más corto que “funcionalidades”, mantiene claridad.          |
  | Comparación de membresías    | **Planes**            | Término breve y claro que transmite opciones de suscripción. |
  | Información del equipo       | **Equipo**            | Aporta transparencia sin rodeos.                             |
  | Contacto                     | **Contáctanos**       | Familiar y directo.                                          |
  | Descarga de app              | **Descargar App**     | Acción clara que guía la conversión.                         |
  | Soporte / Ayuda              | **FAQs**              | Convención internacional fácil de identificar.               |

- **Web Application**

  | **Conjunto de información** | **Etiqueta usada** | **Razonamiento**                                                              |
  | --------------------------- | ------------------ | ----------------------------------------------------------------------------- |
  | Panel de usuario            | **Dashboard**      | Término estándar y breve que resume todas las métricas y accesos principales. |
  | Gestión de macetas          | **Macetas**        | Claridad inmediata sobre qué se administra en esa sección.                    |
  | Parámetros y sensores       | **Estado**         | Resume en una palabra el monitoreo de variables clave.                        |
  | Historial de acciones       | **Historial**      | Convención clara para acceso a registros previos.                             |
  | Notificaciones              | **Alertas**        | Prioriza el sentido de urgencia y atención inmediata.                         |
  | Configuración de riego      | **Riego**          | Acción clave del sistema, entendible y directa.                               |
  | Perfil del usuario          | **Perfil**         | Identificación directa del usuario con su información.                        |
  | Membresías                  | **Plan**           | Más corto y directo que “membresía”, común en plataformas digitales.          |

- **App Mobile**
  | **Conjunto de información** | **Etiqueta usada** | **Razonamiento** |
  | --------------------------- | ------------------ | -------------------------------------------------------------------------- |
  | Pantalla principal | **Inicio** | Aporta familiaridad; preferido sobre “Dashboard” en apps móviles. |
  | Administración de plantas | **Mis Plantas** | Más personal, adecuado al uso individual. |
  | Control de sensores | **Sensores** | Directo, técnico y reconocible. |
  | Riegos automáticos | **Programación** | Abarca funciones automáticas y manuales. |
  | Historial y reportes | **Registro** | Aglutina historial de riegos, fertilización y alertas en un solo concepto. |
  | Configuración del usuario | **Ajustes** | Etiqueta común en interfaces móviles, fácil de ubicar. |

### 5.2.3. SEO Tags and Meta Tags

Las meta etiquetas nos permiten codificar y especificar metadatos en una página web. Aunque no son visibles para los usuarios, los navegadores y rastreadores web las leen. Estas etiquetas facilitan el análisis de archivos HTML y ayudan en el mantenimiento del contenido. Además, influyen en el posicionamiento de nuestra página en los motores de búsqueda.

- **Landing Page**

  <table>
    <thead>
      <tr>
        <th>Elemento</th>
        <th>Código HTML</th>
        <th>Descripción</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Título (Title)</td>
        <td>
          <code
            >&lt;title&gt;Macetech – Cuida tus plantas con
            inteligencia&lt;/title&gt;</code
          >
        </td>
        <td>
          Se muestra en pestañas del navegador y resultados de búsqueda; ayuda a
          captar la atención inicial.
        </td>
      </tr>
      <tr>
        <td>Codificación</td>
        <td>
          <code>&lt;meta charset="utf-8"&gt;</code>
        </td>
        <td>
          Se emplea UTF-8 por su compatibilidad universal y eficiencia de
          almacenamiento.
        </td>
      </tr>
      <tr>
        <td>Meta Description</td>
        <td>
          <code
            >&lt;meta name="description" content="Descubre Macetech, la solución
            inteligente para cuidar tus plantas. Automatiza el riego y recibe
            alertas personalizadas."&gt;</code
          >
        </td>
        <td>Proporciona un resumen claro y orientado a SEO.</td>
      </tr>
      <tr>
        <td>Keywords</td>
        <td>
          <code
            >&lt;meta name="keywords" content="maceta inteligente, sensores de
            plantas, jardinería digital, riego automático"&gt;</code
          >
        </td>
        <td>Mejora la clasificación de contenido en motores de búsqueda.</td>
      </tr>
      <tr>
        <td>Autor</td>
        <td>
          <code
            >&lt;meta name="author" content="Equipo SevenSync -
            Macetech"&gt;</code
          >
        </td>
        <td>Establece la autoría del sitio.</td>
      </tr>
      <tr>
        <td>Copyright</td>
        <td>
          <code
            >&lt;meta name="copyright" content="Copyright © 2025
            Macetech."&gt;</code
          >
        </td>
        <td>Declara la titularidad legal sobre el contenido.</td>
      </tr>
    </tbody>
  </table>

- **Web Application**

  <table>
    <thead>
      <tr>
        <th>Elemento</th>
        <th>Código HTML</th>
        <th>Descripción</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Título (Title)</td>
        <td>
          <>&lt;title&gt;Panel de Macetech – Gestiona tus plantas fácilmente&lt;/title&gt;</  code>
        </td>
        <td>Título técnico orientado a usuarios activos.</td>
      </tr>
      <tr>
        <td>Codificación</td>
        <td>
          <code>&lt;meta charset="utf-8"&gt;</code>
        </td>
        <td>Permite soporte multilingüe y eficiente visualización de datos.</td>
      </tr>
      <tr>
        <td>Meta Description</td>
        <td>
          <>&lt;meta name="description" content="Gestiona múltiples macetas, visualiza  métricas en tiempo real y optimiza el cuidado de tus plantas con Macetech Web."&gt;</  code>
        </td>
        <td>Clarifica propósito del panel de control, mejora posicionamiento.</td>
      </tr>
      <tr>
        <td>Keywords</td>
        <td>
          <code>&lt;meta name="keywords" content="dashboard plantas, monitoreo vegetal web,   control de riego"&gt;</code>
        </td>
        <td>Palabras clave específicas para usuarios técnicos o avanzados.</td>
      </tr>
      <tr>
        <td>Autor</td>
        <td>
          <code>&lt;meta name="author" content="Equipo SevenSync - Macetech"&gt;</code>
        </td>
        <td>Define el equipo responsable del desarrollo.</td>
      </tr>
      <tr>
        <td>Copyright</td>
        <td>
          <code>&lt;meta name="copyright" content="Copyright © 2025 Macetech."&gt;</code>
        </td>
        <td>Protección intelectual del software web.</td>
      </tr>
    </tbody>
  </table>

- **App Mobile**
  | Elemento | Valor | Descripción |
  | ------------------ | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
  | App Title | **Macetech Móvil – Jardinería inteligente** | Título visible en App Store / Google Play, centrado en el beneficio principal del usuario. |
  | App Subtitle | **Automatiza el cuidado de tus plantas desde tu celular.** | Subtítulo que resume brevemente el valor diferencial. |
  | App Description | **Controla el riego, recibe alertas y monitorea tus macetas en tiempo real con Macetech desde tu smartphone.** | Descripción larga para las tiendas, orientada a beneficios y funcionalidad. |
  | App Keywords | **riego inteligente, plantas, monitoreo de humedad, sensores, jardinería doméstica, cuidado de macetas** | Palabras clave optimizadas para búsquedas dentro de las tiendas de aplicaciones. |
  | Autor / Developer | **Equipo SevenSync – Macetech** | Identificación del equipo desarrollador para reforzar confianza. |
  | Copyright / Rights | **Copyright © 2025 Macetech. Todos los derechos reservados.** | Declaración formal de propiedad intelectual en la ficha de la app. |

### 5.2.4. Searching Systems

Macetech implementa sistemas de búsqueda diseñados para brindar asistencia activa al usuario en la localización de datos clave dentro del producto digital. Estas decisiones buscan evitar que los usuarios se sientan desorientados o saturados por el volumen de información, permitiéndoles encontrar lo que necesitan de manera rápida, intuitiva y contextual. A continuación, se detallan las opciones de búsqueda, filtros disponibles y comportamiento visual de los resultados para cada entorno:

- **Landing Page**
  | Medio de búsqueda | Filtros disponibles | Representación de resultados |
  | ---------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------ |
  | Navegación por anclas (scroll-spy) | Por tópicos como “Servicios”, “Precios”, “Contacto”. | Resalta el bloque activo y ancla visualmente la vista a esa sección automáticamente. |

- **Web Application**
  | Medio de búsqueda | Filtros disponibles | Representación de resultados |
  | ----------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
  | Barra superior persistente | Tipo de planta, nivel de humedad, estado de sensores, nombre de la maceta. | Tabla dinámica o cards con badges visuales de estado y color de prioridad. |
  | Filtros por columna en tablas | Columnas de “Estado”, “Última actualización”, “Ubicación” permiten búsqueda rápida. | Se actualiza el contenido de la tabla según los criterios elegidos. |

- **App Mobile**
  | Medio de búsqueda | Filtros disponibles | Representación de resultados |
  | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------------------------ |
  | Barra de búsqueda local | Secciones específicas como “Macetas”, “Alertas” o “Plantas”. | Lista con tarjetas filtradas en tiempo real según relevancia. |
  | Chips de filtros rápidos | “Críticas”, “Humedad baja”, “Macetas activas”, “Favoritas”. | Resaltado visual de los resultados que coinciden con cada filtro seleccionado. |

Reglas comunes en todos los productos

- Las búsquedas son tolerantes a errores tipográficos (ej. “humedá” devuelve “humedad”).

- Cuando no hay coincidencias, se muestra un mensaje informativo como: “No se encontraron resultados con esos criterios.”

- Los resultados se ordenan por relevancia y, cuando aplica, por fecha de última modificación o prioridad.

- En la aplicación móvil y web, las búsquedas están optimizadas para mostrar resultados visualmente diferenciados mediante íconos, colores o etiquetas según el tipo de contenido.

Estos sistemas están orientados a reducir la carga cognitiva del usuario, permitiendo que se concentre en resolver sus tareas sin necesidad de recorrer manualmente grandes volúmenes de información.

### 5.2.5. Navigation Systems

Macetech emplea un conjunto coherente de patrones de navegación que permiten a los usuarios—tanto domésticos como profesionales—explorar el sistema sin fricción, facilitando tareas como monitorear plantas, registrar macetas, configurar alertas o descargar la app. A continuación, se presentan las decisiones principales divididas por producto:

- **Navegación Global**

  | Plataforma       | Patrón                   | Detalles                                                                                      |
  | ---------------- | ------------------------ | --------------------------------------------------------------------------------------------- |
  | **Landing Page** | Menú superior fijo       | Enlaces a _Inicio, Producto, Beneficios, Precios, FAQ, Contacto_. Uso de scroll anclado.      |
  | **App Web**      | Barra superior + sidebar | En escritorio, barra superior con navegación lateral para secciones clave del dashboard.      |
  | **App Móvil**    | Bottom Tab Bar           | Íconos + texto para secciones principales: Dashboard, Macetas, Alertas, Perfil, Ajustes, etc. |

- **Navegación contextual**

  | Aplicación    | Implementación                                                                 |
  | ------------- | ------------------------------------------------------------------------------ |
  | **App Web**   | Migas de pan visibles en secciones internas (_Dashboard > Macetas > Config._). |
  | **App Móvil** | Enlaces rápidos entre secciones relacionadas                                   |

- **Desplazamiento anclado y scroll-spy**

  | Página           | Técnica aplicada            | Detalle                                                                     |
  | ---------------- | --------------------------- | --------------------------------------------------------------------------- |
  | **Landing Page** | Scroll anclado + scroll-spy | Navegación fluida con resaltado automático de sección activa en el menú.    |
  | **Landing Page** | CTA flotante en móvil       | Botón de “Descargar App” siempre visible en parte inferior al hacer scroll. |

- **Llamadas a la acción (CTAs)**

  - Los botones como “Descargar”, “Registrarse”, “Ver planes” se ubican en:

    - El hero inicial
    - Pies de sección
    - Footer

  - Estilo:

    - Alto contraste
    - Verbos en infinitivo
    - Adaptados para móvil con diseño táctil

- **Selector de idioma**

  | Ubicación | Funcionalidad                                                              |
  | --------- | -------------------------------------------------------------------------- |
  | Header    | Botón ES/EN visible en todas las páginas.                                  |
  | Resultado | Traducción instantánea de menús, botones y CTAs según idioma seleccionado. |

- **Navegación secundaria**

  | Ubicación | Contenido agrupado                                                                                            |
  | --------- | ------------------------------------------------------------------------------------------------------------- |
  | Footer    | Secciones: _Sobre Macetech_, _Soporte_, _Términos y condiciones_, _Política de privacidad_, _Redes sociales_. |

Con este sistema unificado, los usuarios pueden cumplir sus objetivos como monitorear plantas, revisar alertas o modificar datos de riego de forma clara, rápida y sin pérdida de contexto tanto desde web como desde dispositivos móviles.

## 5.3. Landing Page UI Design

### 5.3.1. Landing Page Wireframe

Link de figma: https://www.figma.com/design/xFU95RuqCScZF1lac0c4fk/Macetech-Design?node-id=7-2&t=9QnRawZyBzKLNDDq-1

<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding1.png" alt="WireFrame" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding2.png" alt="WireFrame" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding3.png" alt="WireFrame" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding4.png" alt="WireFrame" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding5.png" alt="WireFrame" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding6.png" alt="WireFrame" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding7.png" alt="WireFrame" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/wireframes/WireFramesLanding8.png" alt="WireFrame" width="600" height="300"> <br>

### 5.3.2. Landing Page Mock-up

<img src="/assets/img/capitulo-5/landing-page/mockups/MockUpLanding1.png" alt="MockUp" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/mockups/MockUpLanding2.png" alt="MockUp" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/mockups/MockUpLanding3.png" alt="MockUp" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/mockups/MockUpLanding4.png" alt="MockUp" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/mockups/MockUpLanding5.png" alt="MockUp" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/mockups/MockUpLanding6.png" alt="MockUp" width="600" height="300"> <br>
<img src="/assets/img/capitulo-5/landing-page/mockups/MockUpLanding7.png" alt="MockUp" width="600" height="300"> <br>

## 5.4. Applications UX/UI Design

Link de figma: https://www.figma.com/design/xFU95RuqCScZF1lac0c4fk/Macetech-Design?node-id=7-2&t=9QnRawZyBzKLNDDq-1

### 5.4.1. Applications Wireframes

### 5.4.2. Applications Wireflow Diagrams

### 5.4.2. Applications Mock-ups

Los siguientes mockups representan las interfaces clave de una plataforma de gestión de macetas inteligentes. Estas vistas han sido diseñadas para facilitar la experiencia del usuario en procesos como el registro e inicio de sesión, visualización del estado de las macetas, gestión de notificaciones, y administración de cuenta y membresía. Cada pantalla refleja una parte esencial del recorrido del usuario, alineada con los objetivos y necesidades definidos para cada User Persona.

<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-1.png" alt="MockUp" width="1000" height="500"> <br>
<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-2.1.png" alt="MockUp" width="1000" height="500"> <br>
<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-2.2.png"  alt="MockUp" width="1000" height="500"> <br>
<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-3.png"  alt="MockUp" width="1000" height="500"> <br>
<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-4.1.png" alt="MockUp" width="1000" height="500"> <br>
<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-4.2.png" alt="MockUp" width="1000" height="500"> <br>
<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-5.1.png" alt="MockUp" width="1000" height="500"> <br>
<img src="/assets/img/capitulo-5/ux-ui-design/mock-ups/web-app/Mockup-5.2.png" alt="MockUp" width="1000" height="500"> <br>

### 5.4.3. Applications User Flow Diagrams

#### 5.4.3.1. Web Applications User Flow Diagrams

Los siguientes User Flows representan los principales recorridos que un usuario puede seguir dentro de la aplicación, desde el acceso inicial hasta la personalización de su experiencia. Cada flujo responde a un objetivo específico del usuario (User Goal) y está basado en los mockups desarrollados. Se abordan procesos clave como el registro e inicio de sesión, la interacción con macetas inteligentes, la actualización de membresía, y la configuración de cuenta y notificaciones, asegurando una experiencia intuitiva, eficiente y centrada en las necesidades del usuario.

- **1. Registro e Inicio de Sesión del Usuario**
  Este flujo describe el proceso que permite a nuevos usuarios registrarse en la plataforma y posteriormente iniciar sesión para acceder a sus funcionalidades. Incluye pasos como completar el formulario de registro, validación de credenciales e ingreso exitoso al sistema.
  <img src="/assets/img/capitulo-5/ux-ui-design/user-flow/userflow_1.png" alt="MockUp" width="1000" height="700"> <br>

- **2. Visualización y Gestión de Macetas Inteligentes**
  Este flujo permite a los usuarios acceder al panel principal donde visualizan todas sus macetas inteligentes, consultar detalles individuales como estado de sensores, historial de riego, recomendaciones, y ejecutar acciones como regar la planta manualmente.
  <img src="/assets/img/capitulo-5/ux-ui-design/user-flow/userflow_2.png" alt="MockUp" width="1000" height="700"> <br>

- **3. Actualización de Membresía y Proceso de Pago**
  Este flujo guía al usuario desde la comparación de planes hasta el proceso de pago para actualizar su cuenta gratuita a una suscripción Premium, permitiéndole acceder a funcionalidades avanzadas como reportes detallados y riego automático programado.
  <img src="/assets/img/capitulo-5/ux-ui-design/user-flow/userflow_3.png" alt="MockUp" width="1000" height="700"> <br>

- **4. Configuración de Cuenta y Preferencias de Notificación**
  Este flujo muestra cómo el usuario puede gestionar su perfil, actualizar sus datos personales y modificar las preferencias de notificación desde la sección de configuración, personalizando la experiencia de uso según sus necesidades.
  <img src="/assets/img/capitulo-5/ux-ui-design/user-flow/userflow_4.png"  alt="MockUp" width="1000" height="700"> <br>

## 5.5. Applications Prototyping

## 5.5.1 Web Applications Prototyping

La presente sección incluye los prototipos interactivos desarrollados para representar el comportamiento funcional de la aplicación web en sus principales vistas. Estos prototipos permiten simular la navegación entre pantallas, validar la lógica de interacción y evaluar la experiencia del usuario antes del desarrollo final. Se han construido a partir de los mockups previamente diseñados, asegurando coherencia visual y funcional con los User Flows definidos.

- **Criterios de interacción seleccionados:**
  - Se utilizó un sistema de navegación lateral persistente que permite moverse fácilmente entre secciones clave como Dashboard, Perfil, Membresías y Notificaciones.
  - Las interacciones siguen un enfoque secuencial y jerárquico, facilitando tareas críticas como registrar una cuenta, revisar el estado de una maceta o actualizar el plan de membresía.
  - Se priorizó la claridad visual con botones de acción directa (“Regar ahora”, “Actualizar plan”, “Guardar cambios”) que reducen la fricción del usuario.
- **Relación con la arquitectura de información:**

  - **Sistema de navegación:** jerárquico en versión escritorio con íconos y etiquetas claras en un menú lateral.
  - **Organización visual:** disposición de contenido en tarjetas, uso de títulos, subtítulos y agrupaciones para mejorar la escaneabilidad.
  - **Tipos de categorización:** por tópicos (Macetas, Membresías, Perfil) y por audiencia (usuarios registrados o premium).

- **Pantallas incluidas en el prototipo:**
  - Registro y Login
  - Dashboard de macetas
  - Detalle de maceta inteligente
  - Panel de membresía y proceso de pago
  - Sección de perfil y notificaciones
- **Screenshot representativo del prototipo en acción:**
  <img src="/assets/img/capitulo-5/ux-ui-design/prototyping/Web_Prototyping.png"  alt="MockUp" width="1000" height="700"> <br>
- **Enlace al video de navegación en Microsoft Stream:**
  [Prototyping_Video](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202213652_upc_edu_pe/EQ1iceHxaeNPlHG_Tx5M8-cBXeJxztrmdvh0jbH8akaVrA?e=YMGrHy&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)
