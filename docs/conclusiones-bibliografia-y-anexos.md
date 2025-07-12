# Conclusiones

En esta sección se presentan de manera estructurada las conclusiones generales del proyecto, acompañadas de un análisis detallado sobre los avances alcanzados, los aprendizajes obtenidos y las áreas de mejora identificadas en relación con los objetivos planteados. Asimismo, se incluyen recomendaciones para los siguientes pasos en el desarrollo del producto digital, así como el video “About-The-Team”, que refleja la composición y el compromiso del equipo de trabajo durante todo el proceso.

## Conclusiones y Recomendaciones

En esta sección, el equipo presenta las conclusiones generales del proyecto, contrastando los resultados obtenidos con los Problem Statements iniciales, los supuestos planteados sobre el comportamiento de los usuarios, las hipótesis formuladas y los criterios de éxito definidos en el marco del proceso Lean UX. A partir de los aprendizajes y validaciones alcanzadas, se proponen también una serie de recomendaciones clave para guiar los siguientes pasos del Roadmap, asegurando la evolución sostenida de los productos digitales incluidos en el modelo de negocio.

**1. Ahorro hídrico próximo al objetivo planteado**
Las simulaciones en Wokwi y el análisis de la lógica de riego automático han demostrado que el sistema adapta de forma inteligente la frecuencia y duración de los ciclos de riego según el estado del sustrato. Más allá de la reducción cuantitativa del 25 % - 35 %, los desarrolladores destacaron que el algoritmo evita “riego por inercia”, es decir, ciclos innecesarios destinados únicamente a cumplir horarios predefinidos, y prioriza la lectura real de los sensores. Este enfoque centrado en la necesidad real de la planta constituye la principal palanca para alcanzar el ahorro hídrico más ambicioso del 45–50 %, especialmente una vez se integren fuentes de datos ambientales externos (por ejemplo, previsiones meteorológicas) que permitan desactivar el riego ante pronósticos de lluvia o alta humedad.

**2. Alta confianza en la precisión de los sensores**
Los resultados obtenidos tras distintos tests de los sensores por los desarrolladores demostró que si es posible confiar en las métricas obtenidas por los sensores, con resultados de fallas menores al 5% entre distintas pruebas realizadas y heurísticas monitoreadas. Estas impresiones cualitativas confirman que, en la práctica, los usuarios interiorizan la información como guía confiable para sus decisiones. La claridad de la interfaz, con lecturas agrupadas y representaciones gráficas sencillas, refuerza la propuesta de valor técnico al subsanar la carencia de conocimientos y eliminar la incertidumbre inherente al cuidado tradicional.

**3. Efectividad del onboarding guiado y retención temprana**
Más allá de la métrica de churn, los relatos de los testers reflejan que el recorrido inicial, desde la configuración de la maceta hasta la primera alerta de riego, resulta “acogedor”, “sin fricciones” y “accesible” incluso para quienes nunca habían usado un dispositivo IoT. Esto también es confirmado por los desarrolladores. Las notificaciones contextuales, por ejemplo, explican brevemente por qué el nivel de humedad es bajo y sugieren acciones concretas, lo que genera una experiencia de aprendizaje progresiva. Este acompañamiento paso a paso no solo refuerza la retención temprana, sino que establece un patrón de confianza que prepara al usuario para interactuar de forma autónoma con la plataforma a largo plazo.

**4. Relevancia y rapidez del motor de recomendaciones**
El valor real del motor no reside únicamente en su capacidad para procesar datos en fracciones de segundo, sino en la pertinencia de las sugerencias: consejos como “riega 20 mL menos mañana si persiste la alta humedad” fueron percibidos como “muy útiles” y “personalizados” por los desarrolladores, testers y algunos usuarios entrevistados, no como mensajes genéricos. La cohesión entre el módulo de Data Analytics y el de Service Operation & Monitoring evita solapamientos de lógica e incrementa la agilidad de respuesta. Este nivel de personalización, validado mediante sesiones de feedback, refuerza la promesa de Macetech de actuar como un asistente proactivo y preventivo.

**5. Viabilidad del modelo freemium y proyección de adopción**
Los estudios de mercado y las conversaciones con prospectos señalaron que el umbral de precio propuesto (S/ 29.99/mes) se percibe como “razonable” frente al costo de mantener un jardín tradicional en un contexto urbano (compra de agua, fertilizantes y asesorías puntuales). Adicionalmente, la oferta freemium, con acceso básico a datos sensoriales y recomendaciones limitadas, funciona como gancho para introducir a usuarios reticentes. Este enfoque escalonado permite atraer un segmento amplio y, una vez que experimentan el valor añadido del plan de pago (alertas prioritarias, análisis fitosanitario avanzado), facilita la conversión a suscripciones completas, robusteciendo la sostenibilidad financiera del proyecto.

**6. Percepción positiva de seguridad y privacidad de datos**
Las sesiones de co‑creación revelaron que los usuarios valoran un trato transparente de sus datos. En sus entrevistas se evidencian el peso de la confianza como factor de decisión, todo en base de los datos personales pertinentes que agreguen debido a que la aplicación los necesita o pide. Estas respuestas cualitativas superan la estadística de rechazo por privacidad, ya que construyen una narrativa de marca responsable: Macetech no solo promete cifrar la información, sino que la comunica de forma clara y accesible, diferenciándose de soluciones opacas y reforzando la relación a largo plazo con la comunidad de usuarios.

**7. Necesidad de avanzar hacia analítica predictiva**
Aunque los InsightReports actuales cubren el qué y el cuándo de los indicadores (historias de consumo, tendencias de humedad), los usuarios demandan escenarios de “qué pasará si…” que les permitan anticipar problemas antes de que ocurran. La evolución hacia pipelines de datos híbridos y modelos de series temporales no solo responde a un deseo tecnológico, sino al requerimiento de un asistente verdaderamente proactivo: sugerencias de riego o alertas elevarán notablemente la propuesta de valor y fortalecerán la adopción de hábitos sostenibles. Se considera que esto puede elevar la aceptación e interés por parte del mercado en un 15%.

**8. Escalabilidad de la infraestructura y cobertura de conectividad**
Más allá de soportar un crecimiento de usuarios mayor a un valor de 10×, la infraestructura debe garantizar la continuidad del servicio en contextos tan diversos como un balcón pequeño en Miraflores o una terraza comunitaria en Villa El Salvador. La combinación de gateways edge para procesamiento local de datos y alternativas de conectividad (4G/5G, LoRaWAN) no se plantea solo como un reto técnico, sino como una garantía de resiliencia operativa que se consiguio de forma parcial: Macetech debería poder desplegarse en zonas con conectividad limitada sin sacrificar la latencia ni la confiabilidad de las recomendaciones, asegurando así la confianza del usuario sin importar su ubicación, aunque consigue esto en un 50% de los valores planteados.

**9. Consolidación de los objetivos fundacionales de SevenSync y Macetech**
La materialización de Macetech bajo el cuidado de SevenSync trasciende el simple lanzamiento de un producto: representa el cumplimiento de la visión de la compañía de democratizar el acceso a soluciones IoT en jardinería urbana, fortalecer las capacidades internas del equipo en IoT, DDD, UX y Data Science, y establecer un referente en innovación sostenible en el Perú. La coordinación interdisciplinaria, desde el diseño de hardware en PyCharm y Wokwi, hasta el desarrollo de frontend en Flutter, Angular y backend en ASP NET Core, ha potenciado las habilidades técnicas y colaborativas de cada miembro. Así, SevenSync no solo crea una maceta inteligente, sino que construye un equipo capaz de afrontar retos complejos, atrayendo talento y estableciendo procesos ágiles y de alta calidad que servirán de base para futuros proyectos.

**10. Reactivación y mejora continua del modelo Lean UX**
Aunque las métricas de ahorro hídrico y retención aún no alcanzan plenamente los objetivos originales, el análisis cualitativo y heurístico sienta las bases para un ciclo iterativo de refinamiento. En fases posteriores, se podrán reactivar las Hypotheses Statements y validar cada criterio con datos de despliegue real. Este enfoque de mejora continua, propio de Lean UX, permitirá replantear experimentos de software, recopilar métricas de campo (consumo hídrico, churn, supervivencia vegetal) y adaptar el software y hardware hasta que todas las hipótesis y Success Criteria se cumplan en su totalidad, cerrando el ciclo de aprendizaje y garantizando la excelencia del producto.

---

**1. Implantación rigurosa de Scrum y gobernanza de proyecto**
Para garantizar un ritmo de trabajo sostenible y una adaptación continua a las prioridades del negocio, es imprescindible formalizar un ciclo Scrum completo en los próximos ciclos y proyectos. Esto implica asignar claramente los roles de Product Owner, Scrum Master y Development Team, y calendarizar reuniones regulares: Sprint Planning para definir objetivos, Daily Stand‑up para identificar y resolver bloqueos, Sprint Review para mostrar avances y Retrospective para ajustar procesos. Asimismo, deben utilizarse tableros visuales (digitales o físicos) que reflejen el estado de cada tarea, promoviendo la transparencia y la responsabilidad compartida.

**2. Estandarización y automatización de la calidad de código**
La coherencia en el estilo y la detección temprana de errores son fundamentales para reducir retrabajos y defectos en producción en proyectos futuros. Recomendamos definir un conjunto único de reglas de linting y formateo para cada tecnología y configurar estas herramientas en el pipeline de CI para que rechacen cualquier build que no cumpla el estándar en un nuevo proyecto. Además, es vital instaurar una política de Pull Requests obligatorios con revisiones cruzadas por al menos dos desarrolladores antes de fusionar cualquier rama, asegurando así la calidad y la consistencia del código.

**3. Fortalecimiento del liderazgo y los canales de comunicación**
La eficacia de un equipo multidisciplinario dentro de uno de nuestros proyectos futuros depende de una comunicación clara y de decisiones oportunas. Para ello, recomendamos elaborar un RACI (Responsable, Aprobador, Consultado, Informado) que detalle las responsabilidades en cada entregable esencial. Complementariamente, se deben utilizar plataformas colaborativas con hilos temáticos bien estructurados y registrar actas de reunión con tareas asignadas y fechas límite. Designar un “enlace de proyecto” por área (frontend, backend, IoT, UX) garantizará un flujo de información continuo y evitará cuellos de botella.

**4. Evolución de la arquitectura y calidad del Back‑End**
Para mejorar la robustez y escalabilidad de la capa de servicio, se aconseja migrar progresivamente hacia microservicios o bounded contexts independientes, cada uno con su propia API versionada. En paralelo, es crítico incorporar pruebas de contrato (Pact) y simulaciones de carga automatizadas en el CI/CD, de manera que cualquier cambio interfiera mínimamente con otros servicios. Finalmente, implantar un sistema de logging centralizado y un dashboard de métricas de salud (latencia, errores, uso de recursos) permitirá detectar y resolver problemas en producción de forma proactiva.

**5. Maduración del Front‑End**
Una experiencia de usuario sólida requiere coherencia visual y rendimiento optimizado. Se propone crear un Design System que reúna componentes reutilizables, estilos tipográficos, paleta de colores y espaciados definidos, sincronizados con herramientas como Storybook, todo para proyectos futuros que requieran una sección front-end, sea mobile o web. Para mejorar el rendimiento, se deben implementar lazy loading y code‑splitting, y evaluar periódicamente con Lighthouse para mantener tiempos de carga óptimos. Adicionalmente, cumplir con WCAG 2.1 AA (atributos ARIA, contraste y navegación por teclado) asegurará accesibilidad y calidad de interacción en todos los dispositivos.

**6. Seguimiento continuo y mejora iterativa**
El cierre constante del ciclo de entrega con datos reales es la mejor garantía de éxito en los proyectos futuros que planeamos. Al término de cada sprint, se deben recopilar métricas cualitativas (feedback de usuarios, hallazgos de tests de usabilidad) y cuantitativas (tasa de churn, tiempos de respuesta del API, cobertura de pruebas y resultados de accesibilidad). Estas métricas deben revisarse en reuniones quincenales de roadmap, donde se revaliden las hipótesis Lean UX y se ajusten los experimentos de campo (p. ej. pruebas piloto en hogares reales). Este enfoque de medición y aprendizaje sistemático permitirá alcanzar y superar las métricas de éxito originales en futuras versiones.

**7. Fortalecimiento del aseguramiento de la calidad (QA) y cobertura de pruebas**
Para garantizar que cada nueva versión mantenga la estabilidad y fiabilidad alcanzadas, es esencial diseñar un plan de QA integral para el próximo ciclo. Esto incluye estandarizar suites de pruebas automatizadas unitarias, de integración y end‑to‑end, así como definir un backlog de defectos que permita priorizar correcciones antes de cada lanzamiento. Además, se recomienda incorporar pruebas de regresión automatizadas en el pipeline de CI/CD para descubrir casos límite, de modo que las futuras versiones superen los umbrales de cobertura y robustez esperados.

**8. Madurez de DevOps y despliegue continuo**
De cara a las siguientes iteraciones, se debe evolucionar la infraestructura de despliegue hacia un modelo DevOps más maduro, que incluya entornos separados de staging y producción, y pipelines de entrega continua con validaciones automáticas. Es recomendable configurar alertas y dashboards en tiempo real que supervisen la salud de la aplicación y permitan reaccionar ante incidentes antes de que impacten a los usuarios finales. Estas prácticas asegurarán que las actualizaciones se publiquen de forma rápida, segura y controlada, y que cualquier problema resulte inmediatamente detectable y remediable.

## Vídeo About-The-Team

La presente sección ofrece una mirada integral al trabajo colaborativo detrás del desarrollo del proyecto, mediante un resumen estructurado del video About-The-Team. Este material audiovisual documenta de forma dinámica y auténtica el proceso vivido por el equipo, combinando imágenes de sesiones reales de trabajo, narración explicativa y testimonios individuales de los integrantes. A través de este formato, se busca reflejar tanto los hitos alcanzados como las competencias desarrolladas a lo largo del proyecto.

El contenido del video se organiza en secciones temporizadas, detallando el minuto y segundo de inicio de cada bloque temático para facilitar su navegación. Asimismo, se incluye una captura representativa del video y los enlaces a las versiones publicadas en Microsoft Stream y YouTube. Esta última fue utilizada también para su integración en el Landing Page del producto. En conjunto, esta pieza audiovisual complementa el informe técnico al destacar el compromiso, esfuerzo y aprendizaje continuo del equipo de desarrollo.

- Testimonio de Pescorán Angulo, Juan Fabritzzio: 0:00 - 3:25 minutos
- Testimonio de Trigueros Chumacero, Flavio Eduardo: 3:26 - 4:41 minutos
- Testimonio de Paredes Zapata, Luiggi Gianfranco: 4:42 - 6:23 minutos
- Testimonio de Sanchez Zamora, Fabrizio Alessandro: 6:24 - 8:10 minutos
- Testimonio de Mallma Quispe, Rubén Elías: 8:11 - 9:49 minutos
- Testimonio de Yen Cerna, Lucio Heli: 9:50 - 14:10 minutos

###### Figura 187

_Presentación de los endpoints del Back-End de Macetech desplegado mediante la plataforma de Azure_

<img src="/assets/img/capitulo-6/deployment/back-end-deployment-6.png" alt="Evidencia de despliegue en Azure">

El video profundiza en la participación activa de cada integrante a lo largo de las múltiples áreas que conformaron el trabajo final, tales como el diseño de la solución digital, la implementación de funcionalidades clave, la validación de hipótesis mediante Lean UX, la elaboración de artefactos ágiles, la integración de componentes tecnológicos (IoT, edge computing, backend, frontend), y la documentación técnica. Se presentan escenas de sesiones reales de trabajo colaborativo, mostrando momentos de análisis, codificación, revisión de avances, planificación de sprints, pruebas de usabilidad y toma de decisiones estratégicas.

Asimismo, cada miembro reflexiona sobre los principales desafíos encontrados durante el proceso, ya sea en términos de gestión del tiempo, barreras técnicas, diferencias de criterio, integración de herramientas o adaptación al trabajo interdisciplinario. Estas dificultades son abordadas de forma honesta, enfatizando cómo se convirtieron en oportunidades de aprendizaje compartido.

Finalmente, el video cierra con testimonios que evidencian cómo el proceso permitió el desarrollo de competencias clave vinculadas al trabajo en equipo, pensamiento crítico, comunicación efectiva, resolución de problemas y aplicación de conocimientos tecnológicos. Además, se destacan los student outcomes alcanzados, vinculando directamente la experiencia del proyecto con los resultados de aprendizaje esperados al culminar la carrera. El video no solo transmite el esfuerzo técnico y metodológico del grupo, sino también su crecimiento personal y profesional durante el desarrollo del proyecto final.

## Bibliografía

En esta sección se detallan todas las fuentes consultadas durante el desarrollo del proyecto, incluyendo artículos académicos, libros, sitios web especializados y normativas técnicas. Las referencias se presentan en formato APA, garantizando la trazabilidad del contenido citado y respaldando la rigurosidad metodológica del informe.

- Abofol, T., Erev, I. & Sulitzeanu-Kenan, R. (2023). Conformity and Group Performance. Human Nature, 34. 381–399. https://doi.org/10.1007/s12110-023-09454-2
- Alrawashdeh, T., Alshalabi, I. A., Al-Jaafreh, M. & Alksasbeh, M. (2024). Smart indoor gardening: elevating growth, health, and automation. _Bulletin of Electrical Engineering and Informatics_, _13_(3), 1762–1770. https://doi.org/10.11591/eei.v13i3.7101
- Amir, A., Vinke, C. & van Heijningen, R. (2024). Horti-IoT: a new data framework for Dutch horticulture. _International Food and Agribusiness Management Review_, _27_(5), 858-881. https://brill.com/view/journals/ifam/27/5/article-p858_3.xml
- Andrieu, N., Dedieu, B., Girard, P., Scopel, E., Magaju, C., Dembele, C., Mekuria W. & Coe R. (2025). Methodological challenges in assessing the viability of agroecological practices: lessons from a multi-case study in África. _Agronomy for Sustainable Development_, _45_ (15), 2-17. https://link.springer.com/article/10.1007/s13593-025-01010-9
- Ayala-Rivera, V., Portillo-Domínguez, A. & Pasquale, L. (2024). GDPR compliance via software evolution: Weaving security controls in software design. Journal of Systems and Software, 216, 1-20. https://sciencedirect.upc.elogim.com/science/article/pii/S0164121224001894
- Beavers, A., Ray R., Lacy, K., Coringrato, E., Lavelle Sachs, A., Kelly, Z., Buchenau, H., Decker, E., Fahnestock, L., Quist, P., Hébert, J., Litt, J. & Alaimo, K. (2024). Supporting new gardeners: Perspectives of gardeners and garden leaders. _Journal of Agriculture Food Systems and Community Development_, _14_(1), 309-326. https://doi.org/10.5304/jafscd.2024.141.007
- Bhati, A., Hiran, K. K., Vyas, K. A., Mijwil, M. M., Aljanabi, M., Metwally, A. S., Al-Asad, M. F., Awang, M. K. & Ahmad, H. (2024). Low cost artificial intelligence Internet of Things based water quality monitoring for rural areas. _Internet of Things (Netherlands)_, _27_, 101255. https://doi.org/10.1016/j.iot.2024.101255
- Bieri, D., Joshi, N., Wende, W. & Kleinschroth, F. (2024). Increasing demand for urban community gardening before, during and after the COVID-19 pandemic. _Urban Forestry and Urban Greening_, _92_(128206), 1-10. https://doi.org/10.1016/j.ufug.2024.128206
- Brown, S. (2023). *The C4 model*. Leanpub. https://leanpub.com/visualising-software-architecture
- Budarina, M. (2023). UI Design Systems Mastery (3a ed.). https://es.scribd.com/document/718150434/Marina-Budarina-UI-Design-Systems-Mastery-v3-2023
- Ceño Elie, R. M. (2023). _‘EL JARDÍN DE LOS SENTIDOS’: UN PARQUE SALUDABLE_ [Tesis de maestría, Universidad Politécnica de Madrid]. Archivo Digital de la Universidad Politécnica de Madrid. https://oa.upm.es/76827/3/TFM_ROSA_MARIA_C_ELIE.pdf
- Cherlinka, V. (2025, 10 de marzo). _Enfermedades De Las Plantas: Tipos Y Prevención_. EOS DATA ANALYTICS. Recuperado el 08 de abril de 2025, de https://eos.com/es/blog/enfermedades-de-las-plantas/
- Conventional Commits. (2020). Conventional Commits Specification v1.0.0. Recuperado el día 25 de junio de 2025, de https://www.conventionalcommits.org/en/v1.0.0/ 
- Food and Agriculture Organization of the United Nations. (2024). _Progress on change in water-use efficiency. Mid-term status of SDG Indicator 6.4.1 and acceleration needs, with special focus on food security and climate change_. Organización de las Naciones Unidas. https://www.unwater.org/sites/default/files/2024-12/SDG6_Indicator_Report_641_Progress-on-change-in-water-use_2024_EN.pdf
- Data Bridge Market Research. (2025, enero). _Informe de análisis de tamaño, participación y tendencias del mercado mundial de equipos de jardinería: descripción general de la industria y pronóstico hasta 2032_. Recuperado el día 08 de abril de 2025, de https://www.databridgemarketresearch.com/es/reports/global-gardening-equipment-market
- Departamento de Agricultura de EE. UU., Servicio de Conservación de Recursos Naturales. (2025). PLANTS DATABASE. Recuperado el 5 de julio de 2025, de https://plants.usda.gov/
- Driessen, V. (2010). *A successful Git branching model*. nvie.com. https://nvie.com/posts/a-successful-git-branching-model/
- Eltabbal, A. (2023). The Ultimate SEO Guide. flexiple. https://es.scribd.com/document/650074548/The-Ultimate-SEO-Guide?_gl=1*va5pa1*_gcl_au*NDA3NzI0MDYzLjE3MzIzMjcyMDE
- Evans, E. (2003). *Domain-Driven Design: Tackling Complexity in the Heart of Software* (1a ed.). Addison-Wesley Professional. https://learning.oreilly.com/library/view/domain-driven-design-tackling/0321125215/
- Flewelling, P. (2018). *The Agile Developer's Handbook*, Packt Publishing. https://learning.oreilly.com/library/view/the-agile-developers/9781787280205/
- Ford, N., Richards, M., Sadalage, P. & Dehghani, Z. (2021). *Software Architecture: The Hard Parts*. O'Reilly Media, Inc. https://learning.oreilly.com/library/view/software-architecture-the/9781492086888/ 
- GreenTech. (2022). _CREATING THE FUTURE WITH SUBSTANCE_. GreenTech sustainability report. https://greentech.energy/wp-content/uploads/2022_greentech_SustainabilityReport-2.pdf
- Gulyas, B. Z., Caton, S. J. & Edmonson, J. L. (2024). Quantifying the relationship between gardening and health and well-being in the UK: a survey during the covid-19 pandemic. _BMC Public Health_, _24_(810), 1-14. https://doi.org/10.1186/s12889-024-18249-8
- Guo, J., Song, F., Liu, Y., Wang, W. & Wang, Y. (2025). The Impact of Color Combination on Visual Search Efficiency and User Experience in Human-Machine Interface: A Case Study of Metro Electronic Guide Screen. _International Journal of Human-Computer Interaction_, 1–19. https://doi.org/10.1080/10447318.2025.2450164
- Hair Jr., J., Page, M., Brunsveld, N., Merkle, A. & Cleton, N. (2023). _Essentials of Business Research Methods_ (5a ed.). Routledge. https://learning.oreilly.com/library/view/essentials-of-business/9781000894561/
- Hofer, S. & Schwentner, H. (2021). *Domain Storytelling: A Collaborative, Visual, and Agile Way to Build Domain-Driven Software*. Addison-Wesley Professional. https://learning.oreilly.com/library/view/domain-storytelling-a/9780137458974/ 
- Ibarra-Cabrera, M. J., Estrada Torres, I., Aquino Cruz, M., Rentería Ayquipa, R. A., Ochoa, S. F. & Ochoa, J. M. (2024). Tomato Urban Gardening Supported by an IoT-Based System: A Latin American Experience Report on Technology Adoption. _Sensors_, _24_(23), 7620. https://doi.org/10.3390/s24237620
- Instituto Nacional de Estadística e Informática. (2024). _Perú Anuario de Estadísticas Ambientales 2024_. https://cdn.www.gob.pe/uploads/document/file/7448677/6344095-peru-anuario-de-estadisticas-ambientales-2024.pdf?v=1735913022
- Jain, R. K. (2023). Experimental performance of smart IoT-enabled drip irrigation system using and controlled through web-based applications. _Smart Agricultural Technology_, _4_, 100215. https://doi.org/10.1016/j.atech.2023.100215
- Jarmul, K. (2023). Practical Data Privacy. O'Reilly Media, Inc. https://learning.oreilly.com/library/view/practical-data-privacy/9781098129453/
- Kalbach, J. (2020). *Mapping Experiences* (2a ed.). O'Reilly Media, Inc. https://learning.oreilly.com/library/view/mapping-experiences-2nd/9781492076629/
- Khononov, V. (2021). Learning Domain-Driven Design: Aligning software architecture and business strategy (1st ed.) [Kindle version]. O’Reilly Media. https://www.amazon.com/-/es/Vlad-Khononov-ebook/dp/B09J2CMJZY
- Kuleszo, A. (2024). How to Design Better UI Components (3a ed.). https://es.scribd.com/document/713574649/How-to-Design-Better-UI-Components-3-0-Full-eBook?_gl=1*by3b02*_gcl_au*NDA3NzI0MDYzLjE3MzIzMjcyMDE.
- Li, Y., Luo, J., Liu, Z., Wu, D. & Zhang, C. (2023). A Personalized and Smart Flowerpot Enabled by 3D Printing and Cloud Technology for Ornamental Horticulture. _Sensors_, _23_(13), 6116. https://doi.org/10.3390/s23136116
- Murtagh, N. & Frost, R. (2023). Motivations for urban front gardening: A quantitative analysis. _Landscape and Urban Planning_, _238_(104835). https://doi.org/10.1016/j.landurbplan.2023.104835
- National Institute of Standards of Technology. (2024, octubre). _Internet of Things (IoT) Advisory Board (IoTAB) Report_. https://www.nist.gov/system/files/documents/2024/10/21/The%20IoT%20of%20Things%20Oct%202024%20508%20FINAL_1.pdf
- New York Restoration Project. (2021). _GARDENER'S GUIDE, RESOURCES TO START YOUR GARDEN_ (1a ed.). https://www.nyrp.org/wp-content/uploads/2021/07/NYRP_GG_2021_DIGITAL_FINAL.pdf
- Nielsen, L. (2019). *Personas - User Focused Design* (2a ed.). Springer London. https://doi.org/10.1007/978-1-4471-7427-1
- Nissen, A., Riedl, R. & Schütte, R. (2024). Users’ reactions to website designs: A neuroimaging study based on evolutionary psychology with a focus on color and button shape. _Computers in Human Behavior_, _115_, 108168. https://www.sciencedirect.com/science/article/pii/S0747563224000359
- Paisajismo San Rafael. (2024, 08 de diciembre). _Errores comunes al diseñar un jardín: ¿Qué evitar para obtener el espacio verde de tus sueños?_. Recuperado el 06 de abril de 2025, de https://jardineriasanrafael.com/jardineria/errores-comunes-al-disenar-un-jardin/
- Patel, N. (2021). SEO MADE SIMPLE. The Neil Patel Step-By-Step Guide. https://es.scribd.com/document/558294953/SEO-Made-Simple?_gl=1*1dvgoky*_gcl_au*NDA3NzI0MDYzLjE3MzIzMjcyMDE.
- Patnaik, D. (2017). *Needfinding: Design Research and Planning* (4a ed.). Kindle Direct Publishing. https://www.amazon.com/-/es/Dev-Patnaik-ebook/dp/B074WYGSZQ 
- Patton, J. (2021). *User Story Mapping: Discover the Whole Story, Build the Right Product*. Ascent Audio. https://learning.oreilly.com/videos/user-story-mapping/9781663728661/ 
- Perfect Earth Project. (2024). _Jardinería basada en la naturaleza. Creando jardines ecológicamente hermosos y saludables_. https://perfectearthproject.org/wp-content/uploads/2024/04/Leaflet_24Update_ES_Download_Digital-1.pdf
- Postolache, S., Sebastiao, P., Viegas, V., Postolache, O. & Cercas, F. (2022). IoT-Based Systems for Soil Nutrients Assessment in Horticulture. _Sensors_, _23_(1), 403. https://doi.org/10.3390/s23010403
- Preston-Werner, T. (2013). Semantic Versioning 2.0.0. https://semver.org/ 
- Richards, M. & Ford, N. (2025). *Fundamentals of Software Architecture* (2nd Edition). O'Reilly Media, Inc. https://learning.oreilly.com/library/view/fundamentals-of-software/9781098175504/ 
- Robertson, J., Robertson, S. & Reed, A. (2024). Mastering the Requirements Process (4a ed.). Addison-Wesley Professional. https://learning.oreilly.com/library/view/mastering-the-requirements/9780137969647/
- Royal Horticultural Society. (2024). _RHS Annual Report and Consolidated Financial Statements. For the year ended 31 January 2024_. https://www.rhs.org.uk/about-us/pdfs/about-the-rhs/mission-and-strategy/past-annual-reports/rhs-annual-report-2023-2024.pdf
- Rusfian, E. & Alessandro, J. (2021). The influence of social media’s marketing activity on local brand equity and consumer response: using mix method approach. Linguistics and Culture Review, 5(S1), 767-780. https://doi.org/10.21744/lingcure.v5nS1.1462
- Shore, J. & Warden, S. (2021). *The Art of Agile Development* (2a ed.). O'Reilly Media, Inc. https://learning.oreilly.com/library/view/the-art-of/9781492080688/ 
- Siraparapu, S. R. & Azad, S. M. A. K. (2024). Aqua-stream: an IoT based smart water management system for sustainable living. _Indonesian Journal of Electrical Engineering and Computer Science_, _36_(3), 1460-1469. http://doi.org/10.11591/ijeecs.v36.i3.pp1460-1469
- Smith, P, R. & Zook, Z.(2024). _Marketing Communications: Integrating Online and Offline, Customer Engagement and Digital Technologies_ (8a ed.). Kogan Page. https://www.perlego.com/book/4347991/marketing-communications-integrating-online-and-offline-customer-engagement-and-digital-technologies-pdf?index=prod_BOOKS&gridPosition=1&searchType=title
- Statista Research Department. (2025, 10 de marzo). _Garden & Patio_. Statista. https://www.statista.com/markets/409/topic/628/garden-patio/#overview
- Stevenson, C. (2020). *Effective User Stories: How to write great user stories for software development teams!*. https://www.amazon.com/-/es/Effective-User-Stories-software-development/dp/B085HLBQYZ  
- Tidwell, J., Brewer, C. & Valencia, A. (2019). *Designing Interfaces* (3a ed.). O'Reilly Media, Inc. https://learning.oreilly.com/library/view/designing-interfaces-3rd/9781492051954/ 
- Thormundsson, B. (2024, 16 de septiembre). _Smart home - statistics & facts_. Statista. https://www.statista.com/topics/2430/smart-homes/?utm_source=chatgpt.com#topicOverview
- Tune, N., & Perrin, J.-G. (2024). Architecture Modernization: Socio-technical alignment of software, strategy, and structure. Manning Publications. https://www.amazon.com/-/es/Architecture-Modernization-Socio-technical-alignment-structure/dp/1633438155
- Uzayr, S. (2022). *Mastering UI Mockups and Frameworks: A Beginner's Guide (Mastering Computer Science)*. CRC Press. https://www.amazon.com/Mastering-Ui-Mockups-Frameworks-Beginners/dp/1032103167
- Vernon, V. (2016). Domain-Driven Design Distilled. Addison-Wesley Professional. https://www.amazon.com/-/es/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420
- Walter, S. (2022). *User Journey Mapping*. SitePoint. https://learning.oreilly.com/library/view/user-journey-mapping/9781098140953/ 
- Wang, X., Wang, B., Xu, L. & Yu, L. (2025). Tailored information display: Effects of background colour and line spacing on visual search across different character types – An eye-tracking study. _Displays_, _88_, 103019. https://www.sciencedirect.com/science/article/abs/pii/S0141938225000563
- Westland, S. & Maggio, M. (2025). The Pocket Universal Principles of Color. Rockport Publishers. https://learning.oreilly.com/library/view/the-pocket-universal/9780760393857/
- Wheeler, A. & Meyerson, R. (2024). Designing Brand Identity: A Comprehensive Guide to the World of Brands and Branding. Wiley. https://www.amazon.com/-/es/Alina-Wheeler-ebook/dp/B0CVVNPZWG?ref_=ast_author_mpb
- World Wide Web Consortium (2025, 06 de mayo). _Web Content Accessibility Guidelines (WCAG) 2.1._. Recuperado el día 06 de mayo de 2025, de https://www.w3.org/TR/2025/REC-WCAG21-20250506/
- Zeldman, J. (2024). Web Standards. Zeldman on Web and Interaction Design. Recuperado el 28 de junio de 2025, de https://zeldman.com/category/web-standards/
- Zimarev, A. (2019). Hands-On Domain-Driven Design with .NET Core: Tackling complexity in the heart of software by putting DDD principles into practice. Packt Publishing. https://www.amazon.com/-/es/Hands-Domain-Driven-Design-NET-Core/dp/1788834097

## Anexos

En esta sección se incorporan elementos complementarios al cuerpo principal del informe, tales como tablas extensas, documentos técnicos, gráficos detallados, esquemas de arquitectura, entrevistas u otros insumos relevantes. Su inclusión permite ampliar y sustentar los hallazgos expuestos sin afectar la fluidez del texto principal. Cada anexo se presenta en una nueva página, identificado con una letra mayúscula y un título correspondiente que facilite su localización y consulta.

**Anexo A – Video de exposición del Trabajo Final**
**Descripción:** Presentación general de todo el proyecto de Macetech, sus objetivos, desarrollo, diagramas, diseño, gestión, estructura, integrantes, costos, resultados y lecciones aprendidas.
Enlace:
[Vídeo de Exposición](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202210190_upc_edu_pe/EdN8gBr5zBlDs2cfMQXHuEoBpEzzJV7wx94bLGyIk-gmDA?e=CCoe6b)

**Anexo B – Video “About The Team”**
Descripción: Breve introducción al equipo de la startup de SevenSync, roles y contribuciones de cada miembro en todo el trabajo, además de como consiguieron la competencia de curso.
Enlace:
[About-The-Team](https://www.youtube.com/watch?v=giQ17bSSdpc)

**Anexo C – Video “About The Product”**
Descripción: Demostración de las funcionalidades clave de Macetech, flujos principales y valor para el usuario.
Enlace:
[About-The-Product](https://upcedupe-my.sharepoint.com/:v:/g/personal/u20221c936_upc_edu_pe/EYt5t29wDrRIqEZH6AY51DQBYhJAELOTRAhf5K_BY8VG0w?e=kgwfNZ)

**Anexo D – Grabaciones de entrevistas de usuarios**
Descripción: Sesiones completas de entrevistas cualitativas con usuarios finales, organizadas por segmentos y preguntas guía.
Enlace:
[Entrevistas de Usuario para el Proyecto Macetech – Equipo de SevenSync](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202218996_upc_edu_pe/EcVM5lwBSMdCiN10VPn4zG4BnJzx430mr3skPPjFyVnn6Q?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=VnGTI5)

**Anexo E – Pizarra de EventStorming en Miro**
Descripción: Tablero con fases, eventos de dominio y legendas que ilustran el mapeo colaborativo de flujos de negocio.
Enlace:
[Tablero de EventStorming en Miro](https://miro.com/app/board/uXjVI7RMpGc=/?share_link_id=692821022758)

**Anexo F – Prototipo interactivo en Figma**
Descripción: Diseño de las pantallas web y móviles, componentes UI/UX y flujos de navegación.
Enlace:
[Proyecto de Figma de la Landing Page, Aplicación Web y Aplicación Móvil de Macetech](https://www.figma.com/design/xFU95RuqCScZF1lac0c4fk/Macetech-Design?node-id=7-2&t=9QnRawZyBzKLNDDq-1)

**Anexo G – Product Backlog en Jira Software**
Descripción: Lista completa de User Stories, estimaciones, prioridades y estado actual en el tablero Scrum.
Enlace:
[Product Backlog en Jira Software](https://sevensync.atlassian.net/jira/software/projects/SCRUM/boards/1/timeline?selectedIssue=SCRUM-4)

**Anexo H – Videos de prototipado y navegación**
Descripción: Vídeo de prototipado realizado al diseño UX/UI para revisar como funcionarían los flujos de los usuarios en su recorrido por la aplicación para conseguir sus goals.

[Web Application Prototyping](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202213652_upc_edu_pe/EQ1iceHxaeNPlHG_Tx5M8-cBXeJxztrmdvh0jbH8akaVrA?e=YMGrHy)

[Mobile Application Prototyping](https://www.youtube.com/watch?v=QvU8tuRCMdg)

**Anexo H – Videos de prototipado y navegación**
Descripción: Vídeo de prototipado realizado al diseño UX/UI para revisar como funcionarían los flujos de los usuarios en su recorrido por la aplicación para conseguir sus goals.

[Web Application Prototyping](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202213652_upc_edu_pe/EQ1iceHxaeNPlHG_Tx5M8-cBXeJxztrmdvh0jbH8akaVrA?e=YMGrHy)

[Mobile Application Prototyping](https://www.youtube.com/watch?v=QvU8tuRCMdg)

**Anexo I – Landing Page completa desplegada**
Descripción: Landing Page de Macetech desplegada en la plataforma de Github Pages de forma directa y sencilla. Cuenta con información de interés para los usuarios nuevos a la plataforma.

[Landing Page](https://sevensync.github.io/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page/)

**Anexo J – Página del Swagger del Backend Platform desplegado**
Descripción: Modelo de Swagger con los endpoints completos del Backend Platform de Macetech, la cual ya se encuentra desplegada en la plataforma de Azure.

[Back-End Platform Swagger](https://macetech.azurewebsites.net/swagger/index.html)

**Anexo K – Web Application de Macetech desplegado**
Descripción: La Web Application desplegada de la plataforma de Macetech a través de la plataforma de Microsoft Azure. 

[Web Application](https://macetechsevensync.web.app/login)

