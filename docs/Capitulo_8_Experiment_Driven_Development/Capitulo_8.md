# Capítulo VIII: Experiment-Driven Development

## 8.1. Experiment Planning
### 8.1.1. As-Is Summary.

Actualmente, la solución propuesta EMS (Energy Management System) se encuentra en una fase inicial de validación basada en supuestos derivados del enfoque Lean UX. La plataforma busca optimizar el consumo energético mediante monitoreo en tiempo real, alertas inteligentes y recomendaciones personalizadas.

En el estado actual, se identifican las siguientes condiciones:

- Los usuarios no cuentan con visibilidad detallada del consumo energético por dispositivo, limitándose a información mensual agregada.
- Existe una baja conciencia sobre hábitos de consumo energético eficiente.
- No se ha validado si los usuarios perciben valor suficiente en soluciones tecnológicas para gestionar su consumo.
- Se desconoce el nivel de disposición a pagar por una solución de monitoreo energético.

Asimismo, se identifican riesgos importantes:

- Resistencia a la adopción por la necesidad de instalar hardware.
- Baja comprensión de métricas energéticas (kWh, consumo por circuito).
- Posible percepción de complejidad del dashboard.
- Desconfianza en la precisión de medición del EMS.

Por ello, se requiere validar estas hipótesis mediante experimentación estructurada, permitiendo tomar decisiones basadas en evidencia.

### 8.1.2. Raw Material: Assumptions, Knowledge Gaps, Ideas, Claims.

**Assumptions:**

- Se asume que los usuarios desean reducir su consumo energético para disminuir costos.
- Se asume que los usuarios están dispuestos a utilizar tecnología para monitorear su consumo.
- Se asume que las alertas en tiempo real pueden influir en el comportamiento del usuario.
- Se asume que las recomendaciones personalizadas generan cambios en los hábitos de consumo.
- Se asume que los usuarios aceptarán un modelo de suscripción.
- Se asume que la instalación del hardware no representa una barrera significativa.

**Knowledge Gaps:**

- Falta información sobre la disposición real de los usuarios a pagar por el servicio.
- Se desconoce qué nivel de ahorro es percibido como significativo.
- No se tiene claridad sobre la facilidad de uso del sistema para usuarios no técnicos.
- Se requiere validar la confianza en los datos proporcionados por el sistema.
- No se conoce el impacto real de las alertas en el comportamiento del usuario.
- Falta evidencia sobre qué funcionalidades son realmente críticas para el usuario.

**Ideas:**

- Implementar encuestas y entrevistas para validar percepciones del usuario.
- Desarrollar una versión demo sin hardware para reducir fricción inicial.
- Implementar una prueba gratuita para evaluar conversión a usuarios pagos.
- Incorporar visualización de ahorro estimado en tiempo real.
- Analizar soluciones similares en el mercado para identificar mejores prácticas.

**Claims:**

- Se afirma que el monitoreo en tiempo real puede reducir el consumo energético.
- Se sostiene que las alertas inteligentes generan cambios en el comportamiento.
- Se afirma que la visualización de datos incrementa la conciencia energética.
- Se sostiene que el valor del ahorro supera el costo del servicio.
- Se afirma que la personalización mejora la retención de usuarios.

### 8.1.3. Experiment-Ready Questions.


| ID | Question                                                                      | Confidence                                            | Risk                        | Impact                                     | Interest            | Total Score |
| -- | ----------------------------------------------------------------------------- | ----------------------------------------------------- | --------------------------- | ------------------------------------------ | ------------------- | ----------- |
| Q1 | ¿La instalación del smart meter reduce la adopción del sistema?               | 8 - Alta fricción percibida por instalación eléctrica | 8 - Alto riesgo de abandono | 10 - Impacto crítico en adquisición        | 9 - Muy relevante   | 35          |
| Q2 | ¿Los usuarios confían en los datos generados por el EMS?                      | 7 - Confianza variable en IoT                         | 7 - Riesgo alto de rechazo  | 10 - Impacto crítico en adopción           | 9 - Alta relevancia | 33          |
| Q3 | ¿Las recomendaciones personalizadas generan reducción de consumo energético?  | 8 - Basado en analítica de datos                      | 6 - Riesgo medio            | 10 - Impacto directo en valor del producto | 9 - Muy relevante   | 33          |
| Q4 | ¿Las alertas de consumo en tiempo real modifican el uso de electrodomésticos? | 8 - Evidencia en apps similares                       | 5 - Riesgo medio            | 9 - Impacto en comportamiento del usuario  | 9 - Muy relevante   | 31          |
| Q5 | ¿Los usuarios entienden el consumo mostrado en kWh y gráficos del EMS?        | 7 - Basado en diseño UX                               | 6 - Riesgo de incomprensión | 9 - Impacto en uso del sistema             | 8 - Alto interés    | 30          |
| Q6 | ¿Un modo demo sin hardware incrementa la intención de uso?                    | 7 - Reduce fricción inicial                           | 4 - Bajo riesgo             | 8 - Impacto en adquisición                 | 8 - Interés alto    | 27          |

### 8.1.4. Question Backlog

| Prioridad (1,2,3,5,8) | ID | Pregunta                                                                      |
| --------------------- | -- | ----------------------------------------------------------------------------- |
| 1                     | Q1 | ¿La instalación del smart meter reduce la adopción del sistema?               |
| 1                     | Q2 | ¿Los usuarios confían en los datos generados por el EMS?                      |
| 2                     | Q3 | ¿Las recomendaciones personalizadas generan reducción de consumo energético?  |
| 3                     | Q4 | ¿Las alertas de consumo en tiempo real modifican el uso de electrodomésticos? |
| 5                     | Q5 | ¿Los usuarios entienden el consumo mostrado en kWh y gráficos del EMS?        |
| 5                     | Q6 | ¿Un modo demo sin hardware incrementa la intención de uso?                    |

### 8.1.5. Experiment Cards

| ID | Question                                                                      | Why                                                                                                                                           | What                                                                                             | Hypothesis                                                                            |
| -- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------- |
| Q1 | ¿La instalación del smart meter reduce la adopción del sistema?               | El smart meter requiere intervención en el sistema eléctrico del hogar, lo cual puede generar rechazo por percepción de riesgo o complejidad. | Realizar test A/B: (A) flujo con instalación obligatoria, (B) acceso a demo sin hardware.        | Se espera que la versión sin hardware incremente la tasa de registro en al menos 25%. |
| Q2 | ¿Los usuarios confían en los datos generados por el EMS?                      | La confianza en la medición es clave para que el usuario tome decisiones basadas en los datos del sistema.                                    | Comparar datos del EMS con recibos eléctricos reales y aplicar encuestas de percepción.          | Se espera que al menos el 70% de usuarios confíe en los datos mostrados.              |
| Q3 | ¿Las recomendaciones personalizadas generan reducción de consumo energético?  | Las recomendaciones son el principal valor agregado del EMS frente a soluciones tradicionales.                                                | Mostrar recomendaciones basadas en patrones de consumo y medir cambios en consumo real.          | Se espera una reducción del consumo total en al menos 20%.                            |
| Q4 | ¿Las alertas de consumo en tiempo real modifican el uso de electrodomésticos? | Las alertas buscan intervenir directamente en el comportamiento del usuario en momentos críticos de consumo.                                  | Enviar alertas cuando se detecten picos de consumo y medir comportamiento posterior.             | Se espera una reducción del 15% en consumo en horas pico.                             |
| Q5 | ¿Los usuarios entienden el consumo mostrado en kWh y gráficos del EMS?        | Si el usuario no entiende los datos, no puede tomar decisiones informadas.                                                                    | Realizar pruebas de usabilidad donde los usuarios interpreten consumo actual, histórico y picos. | Se espera que el 80% de usuarios interprete correctamente los datos sin asistencia.   |
| Q6 | ¿Un modo demo sin hardware incrementa la intención de uso?                    | Reducir la fricción inicial puede mejorar significativamente la captación de usuarios.                                                        | Implementar demo interactivo con datos simulados accesible desde web/app.                        | Se espera un incremento del 30% en la tasa de registro.                               |


## 8.2. Experiment Design
### 8.2.1. Hypotheses.

| | **Hypothesis** |
| :--- | :--- |
| **Question** | ¿La instalación del smart meter reduce la adopción del sistema? |
| **Belief** | Creemos que ofrecer una alternativa sin la instalación física de un smart meter aumentará la adopción inicial, ya que se reduce la fricción y la percepción de riesgo por parte del usuario. |
| **Hypothesis** | La implementación de un flujo de registro que incluya una versión demo sin hardware incrementará la tasa de registro de nuevos usuarios en al menos un 25% en comparación con el flujo que exige la instalación obligatoria. |
| **Null Hypothesis** | La opción de un modo demo sin hardware no tendrá un impacto significativo en la tasa de registro de nuevos usuarios. |

| | **Hypothesis** |
| :--- | :--- |
| **Question** | ¿Los usuarios confían en los datos generados por el EMS? |
| **Belief** | Creemos que la transparencia y la validación de los datos son fundamentales para que los usuarios confíen en el sistema y lo utilicen para tomar decisiones sobre su consumo energético. |
| **Hypothesis** | Al comparar los datos del EMS con los recibos eléctricos de los usuarios y demostrar su precisión, al menos el 70% de los usuarios manifestará un alto nivel de confianza en la información proporcionada por el sistema. |
| **Null Hypothesis** | Menos del 70% de los usuarios confiará en los datos mostrados por el EMS, incluso después de la validación con sus recibos eléctricos. |

| | **Hypothesis** |
| :--- | :--- |
| **Question** | ¿Las recomendaciones personalizadas generan reducción de consumo energético? |
| **Belief** | Creemos que proporcionar recomendaciones de ahorro personalizadas y accionables, basadas en los patrones de consumo del usuario, es el principal generador de valor del producto. |
| **Hypothesis** | La implementación de recomendaciones personalizadas basadas en el análisis de patrones de consumo logrará una reducción del consumo energético total de al menos un 20% entre los usuarios que las sigan. |
| **Null Hypothesis** | Las recomendaciones personalizadas no generarán una reducción estadísticamente significativa en el consumo energético de los usuarios. |

| | **Hypothesis** |
| :--- | :--- |
| **Question** | ¿Las alertas de consumo en tiempo real modifican el uso de electrodomésticos? |
| **Belief** | Creemos que las notificaciones instantáneas sobre picos de consumo pueden influir en el comportamiento del usuario en el momento preciso, fomentando un uso más eficiente de la energía. |
| **Hypothesis** | El envío de alertas en tiempo real cuando se detecten picos de consumo provocará una reducción de al menos un 15% en el consumo de energía durante las horas pico. |
| **Null Hypothesis** | Las alertas en tiempo real sobre picos de consumo no modificarán significativamente los hábitos de uso de electrodomésticos ni el consumo en horas pico. |

| | **Hypothesis** |
| :--- | :--- |
| **Question** | ¿Los usuarios entienden el consumo mostrado en kWh y gráficos del EMS? |
| **Belief** | Creemos que una interfaz de usuario clara e intuitiva es crucial para que los usuarios, independientemente de su conocimiento técnico, puedan interpretar los datos de consumo y actuar en consecuencia. |
| **Hypothesis** | Tras realizar pruebas de usabilidad, se espera que al menos el 80% de los usuarios pueda interpretar correctamente los datos de consumo actual, histórico y picos que se muestran en el dashboard sin necesidad de asistencia. |
| **Null Hypothesis** | Menos del 80% de los usuarios podrá interpretar correctamente los datos presentados en el dashboard, indicando problemas de usabilidad y comprensión. |

| | **Hypothesis** |
| :--- | :--- |
| **Question** | ¿Un modo demo sin hardware incrementa la intención de uso? |
| **Belief** | Creemos que permitir a los usuarios explorar las funcionalidades del sistema con datos simulados, sin el compromiso de una instalación, aumentará el interés y la probabilidad de que se registren. |
| **Hypothesis** | La implementación de un modo demo interactivo y accesible desde la web o la aplicación resultará en un incremento del 30% en la tasa de registro de usuarios. |
| **Null Hypothesis** | La disponibilidad de un modo demo no tendrá un impacto significativo en la tasa de registro de nuevos usuarios. |

### 8.2.2. Domain Business Metrics

| Métrica | Descripción | Fórmula de Cálculo | Técnica de Recolección | Meta Deseada |
| :--- | :--- | :--- | :--- | :--- |
| **Tasa de Registro de Usuarios** | Mide el porcentaje de visitantes que completan el proceso de registro. Es un indicador clave de la adquisición de usuarios y la efectividad de la propuesta de valor inicial. | (Número de Usuarios Registrados / Número de Visitantes Únicos) * 100 | Análisis de logs del servidor y plataforma de analítica web/móvil. | Incrementar en un 25-30% |
| **Nivel de Confianza del Usuario** | Evalúa la percepción de los usuarios sobre la precisión y fiabilidad de los datos proporcionados por el sistema EMS. Es fundamental para la retención y el uso continuado de la plataforma. | (Número de Usuarios que califican la confianza como "Alta" o "Muy Alta" / Número Total de Encuestados) * 100 | Encuestas de satisfacción y percepción post-validación de datos. | ≥ 70% |
| **Reducción de Consumo Energético** | Mide la disminución porcentual del consumo de energía (en kWh) de los usuarios activos. Es la métrica principal que demuestra el valor económico y ecológico del producto. | ((Consumo Anterior - Consumo Actual) / Consumo Anterior) * 100 | Datos de consumo recopilados por el sistema EMS a lo largo del tiempo. | ≥ 20% |
| **Reducción de Consumo en Horas Pico** | Mide el cambio en el comportamiento del usuario, específicamente la reducción del consumo durante los períodos de mayor demanda energética. Impacta directamente en la estabilidad de la red y en costos. | ((Consumo en Pico Anterior - Consumo en Pico Actual) / Consumo en Pico Anterior) * 100 | Análisis de datos de consumo del EMS, segmentado por franjas horarias. | ≥ 15% |
| **Tasa de Éxito en Tareas de Usabilidad** | Mide el porcentaje de usuarios que pueden completar tareas clave dentro de la plataforma sin asistencia. Indica la facilidad de uso y la claridad de la interfaz. | (Número de Usuarios que completan la tarea con éxito / Número Total de Usuarios en la prueba) * 100 | Pruebas de usabilidad moderadas y no moderadas. | ≥ 80% |

### 8.2.3. Measures.

| Question | Measure |
| :--- | :--- |
| ¿La instalación del smart meter reduce la adopción del sistema? | Medir y comparar la tasa de conversión de registros entre el grupo de usuarios al que se le ofrece un modo demo (sin hardware) y el grupo al que se le exige la instalación del smart meter. |

| Question | Measure |
| :--- | :--- |
| ¿Los usuarios confían en los datos generados por el EMS? | Realizar encuestas de satisfacción y confianza antes y después de mostrar a los usuarios una comparativa entre los datos del EMS y sus recibos de electricidad. Se medirá el porcentaje de usuarios que califiquen la precisión como "alta" o "muy alta". |

| Question | Measure |
| :--- | :--- |
| ¿Las recomendaciones personalizadas generan reducción de consumo energético? | Analizar el consumo energético (en kWh) de un grupo de usuarios antes y después de la implementación de las recomendaciones personalizadas. Se comparará con un grupo de control que no reciba dichas recomendaciones para aislar el impacto. |

| Question | Measure |
| :--- | :--- |
| ¿Las alertas de consumo en tiempo real modifican el uso de electrodomésticos? | Monitorear y comparar el consumo de energía durante las horas pico para los usuarios que reciben alertas en tiempo real frente a los que no. Se medirá la variación porcentual del consumo en esos períodos. |

| Question | Measure |
| :--- | :--- |
| ¿Los usuarios entienden el consumo mostrado en kWh y gráficos del EMS? | Registrar la tasa de éxito y el tiempo empleado por los usuarios para completar tareas específicas en pruebas de usabilidad, como "identificar el dispositivo de mayor consumo del último mes". Se medirá el porcentaje de usuarios que completen las tareas correctamente sin ayuda. |

| Question | Measure |
| :--- | :--- |
| ¿Un modo demo sin hardware incrementa la intención de uso? | Medir la tasa de clics en el botón de "Registro" o "Probar ahora" en la página de destino. Se comparará la tasa de conversión de la versión que promociona el modo demo interactivo frente a la que no lo hace. |

### 8.2.4. Conditions.

| Question | Condición Experimental | Condición de Control |
| :--- | :--- | :--- |
| ¿La instalación del smart meter reduce la adopción del sistema? | Se espera un incremento de al menos el 25% en la tasa de registro para el grupo de usuarios expuesto al flujo con modo demo (sin hardware). | No se observará una diferencia estadísticamente significativa en la tasa de registro entre el grupo con modo demo y el grupo con instalación obligatoria. |

| Question | Condición Experimental | Condición de Control |
| :--- | :--- | :--- |
| ¿Los usuarios confían en los datos generados por el EMS? | Al menos el 70% de los usuarios expresará un alto nivel de confianza en los datos del EMS después de la validación con sus recibos eléctricos. | Menos del 70% de los usuarios mostrará confianza en los datos del EMS, indicando que la validación no fue suficiente para generar credibilidad. |

| Question | Condición Experimental | Condición de Control |
| :--- | :--- | :--- |
| ¿Las recomendaciones personalizadas generan reducción de consumo energético? | El grupo de usuarios que recibe recomendaciones personalizadas mostrará una reducción de consumo energético de al menos un 20% en comparación con el grupo de control. | No habrá una diferencia estadísticamente significativa en el consumo energético entre el grupo que recibe recomendaciones y el grupo de control. |

| Question | Condición Experimental | Condición de Control |
| :--- | :--- | :--- |
| ¿Las alertas de consumo en tiempo real modifican el uso de electrodomésticos? | Se registrará una reducción del consumo en horas pico de al menos un 15% para el grupo de usuarios que recibe alertas en tiempo real. | El consumo en horas pico no variará significativamente para el grupo que recibe alertas en comparación con el grupo que no las recibe. |

| Question | Condición Experimental | Condición de Control |
| :--- | :--- | :--- |
| ¿Los usuarios entienden el consumo mostrado en kWh y gráficos del EMS? | Al menos el 80% de los usuarios completará con éxito las tareas de interpretación de datos en las pruebas de usabilidad sin requerir asistencia. | Menos del 80% de los usuarios logrará completar las tareas de interpretación de datos, señalando problemas en la claridad de la interfaz. |

| Question | Condición Experimental | Condición de Control |
| :--- | :--- | :--- |
| ¿Un modo demo sin hardware incrementa la intención de uso? | Se observará un aumento del 30% en la tasa de registro para la versión de la página que promociona el modo demo interactivo. | No habrá una diferencia significativa en la tasa de registro entre la versión con promoción del modo demo y la versión sin ella. |

### 8.2.5. Scale Calculations and Decisions.

Este enfoque utiliza métricas para evaluar el cumplimiento de las hipótesis del proyecto. Cada hipótesis se asocia con un indicador de éxito que determina si el resultado es **desfavorable**, **aceptable**, **ideal** o **excelente**.

- **Desfavorable**: La métrica no alcanza el umbral mínimo esperado, lo que indica que la hipótesis probablemente sea incorrecta y requiere una revisión o un pivote.
- **Aceptable**: La métrica se encuentra en un rango que, si bien no es el ideal, muestra un impacto positivo y justifica la implementación.
- **Ideal**: La métrica alcanza el objetivo principal definido en la hipótesis, confirmando el supuesto.
- **Excelente**: La métrica supera significativamente el objetivo ideal (generalmente en un 25% o más), lo que indica un éxito rotundo y una fuerte validación de la hipótesis.

Este marco permite tomar decisiones basadas en datos para validar, ajustar o descartar las hipótesis del proyecto de manera estructurada.

| Scale Calculation | Decision | Factor          |              |          |               |
| :--- | :--- |:----------------|:-------------|:---------|:--------------|
| | | **Desfavorable** | **Aceptable** | **Ideal** | **Excelente** |
| **Q1:** Creemos que ofrecer una alternativa sin instalación de hardware aumentará la adopción. Sabremos que esto es cierto cuando observemos un incremento de al menos el **25%** en la tasa de registro. | Implementar un flujo de registro con una opción de "Modo Demo" para reducir la fricción inicial y permitir a los usuarios explorar la aplicación sin compromiso. |                 |              |          |               |
| **Q2:** Creemos que la transparencia sobre la precisión de los datos genera confianza. Sabremos que esto es cierto cuando al menos el **70%** de los usuarios manifieste un alto nivel de confianza. | Integrar una sección de validación de datos donde los usuarios puedan comparar las mediciones del EMS con sus recibos de electricidad, junto con testimonios y sellos de confianza. |                 |              |          |               |
| **Q3:** Creemos que las recomendaciones personalizadas son un generador de valor clave. Sabremos que esto es cierto cuando observemos una reducción del consumo de al menos un **20%**. | Desarrollar un motor de recomendaciones que analice patrones de consumo y sugiera acciones de ahorro específicas y fáciles de implementar para el usuario. |                 |              |          |               |
| **Q4:** Creemos que las alertas en tiempo real influyen en el comportamiento del usuario. Sabremos que esto es cierto cuando observemos una reducción del **15%** en el consumo durante horas pico. | Implementar un sistema de notificaciones push que alerte a los usuarios sobre picos de consumo inesperados, ofreciendo la opción de apagar dispositivos de forma remota. |                 |              |          |               |
| **Q5:** Creemos que una interfaz clara es crucial para la toma de decisiones. Sabremos que esto es cierto cuando al menos el **80%** de los usuarios interprete los datos correctamente. | Diseñar un dashboard visual e intuitivo, utilizando gráficos claros y un lenguaje sencillo para representar el consumo en kWh, su equivalencia en moneda local y comparativas. |                 |              |          |               |
| **Q6:** Creemos que un modo demo sin compromiso aumenta el registro. Sabremos que esto es cierto cuando observemos un incremento del **30%** en la tasa de registro. | Crear un landing page y campañas de marketing que destaquen la disponibilidad de un modo demo interactivo para atraer a usuarios que aún no están listos para comprar el hardware. |                 |              |          |               |

### 8.2.6. Methods Selection.

| Herramienta | Google Analytics | Catchpoint | RedLine13 | Lighthouse |
| :--- | :--- | :--- | :--- | :--- |
| **Precio** | Plan gratuito robusto con opciones de pago (Google Analytics 360). | Basado en suscripción, con pruebas gratuitas. Orientado al mercado empresarial. | Gratuito con limitaciones, con planes de pago para mayor capacidad. | Totalmente gratuito y de código abierto, integrado en las herramientas de desarrollo de Chrome. |
| **Capacidad de Análisis** | Análisis exhaustivo de métricas de adquisición, comportamiento y conversión de usuarios. Ideal para A/B testing y seguimiento de objetivos. | Monitoreo exhaustivo del rendimiento web y la experiencia de usuario desde múltiples ubicaciones geográficas (monitoreo sintético y real). | Análisis orientado a pruebas de carga y rendimiento del backend. Simula un gran número de usuarios para medir la respuesta del servidor. | Análisis orientado a la experiencia de usuario en el lado del cliente. Mide métricas clave de rendimiento, accesibilidad, PWA y SEO. |
| **Sencillez** | Curva de aprendizaje media. La interfaz es potente pero puede ser compleja para nuevos usuarios. Requiere configuración para mediciones personalizadas. | Interfaz avanzada y detallada. Requiere conocimientos técnicos para configurar y analizar los monitores de rendimiento. | Relativamente sencillo para iniciar pruebas de carga básicas, pero la interpretación de resultados requiere conocimientos de rendimiento. | Muy sencillo de usar. Genera un informe resumido y fácil de entender con puntuaciones y recomendaciones claras. |
| **Ventajas** | Excelente para entender el comportamiento del usuario en el sitio, medir tasas de conversión (ej. registros) y realizar segmentación de audiencia. Amplia integración. | Ideal para garantizar la disponibilidad y el rendimiento global de la aplicación, detectando problemas antes de que afecten a los usuarios. | Permite simular tráfico masivo para validar la escalabilidad y robustez de la infraestructura del servidor bajo condiciones de estrés. | Óptimo para auditorías rápidas y mejoras en el frontend. Proporciona acciones concretas para optimizar la velocidad de carga y la accesibilidad. |

### 8.2.7. Data Analytics: Goals, KPIs and Metrics Selection.

Siguiendo el principio de seleccionar la "cosa más simple y útil", se ha elegido **Lighthouse** como el método principal para la evaluación de los experimentos. Esta herramienta, al ser gratuita y estar integrada en el navegador, representa la forma más sencilla y directa de obtener retroalimentación sobre la calidad de la experiencia del usuario. Para la hipótesis sobre la comprensión de los datos (Q5), Lighthouse es fundamental, ya que sus auditorías de accesibilidad y rendimiento aseguran que la interfaz no presente barreras técnicas que impidan la correcta interpretación de los gráficos y cifras. Aunque no mide directamente la conversión, garantiza que la plataforma base sobre la que se ejecutan las pruebas A/B (Q1, Q6) sea performante y accesible, eliminando variables que podrían contaminar los resultados. Su enfoque en métricas claras y accionables lo convierte en la herramienta más eficiente para validar la calidad del front-end de manera rápida y sin costo.

![LightHouse-1.png](../../assets/capitulo-8/LightHouse-1.png)

![LightHouse-2.png](../../assets/capitulo-8/LightHouse-2.png)

![LightHouse-3.png](../../assets/capitulo-8/LightHouse-3.png)

![LightHouse-4.png](../../assets/capitulo-8/LightHouse-4.png)

![LightHouse-5.png](../../assets/capitulo-8/LightHouse-5.png)

![LightHouse-6.png](../../assets/capitulo-8/LightHouse-6.png)

### 8.2.8. Web and Mobile Tracking Plan.

**Nota de alcance:** el plan de tracking descrito a continuación aplica únicamente a la Web Application y el Landing Page. El proyecto Energix no contempla una aplicación móvil nativa en esta fase, por lo que no se define un plan de tracking para Mobile.

Para Energix, nuestro objetivo es validar las hipótesis sobre la adopción, confianza y comportamiento del usuario para optimizar el consumo energético. A medida que ejecutemos los experimentos definidos, estableceremos un plan de seguimiento exhaustivo que nos permitirá evaluar de manera efectiva los resultados.

El monitoreo de las funcionalidades experimentales se llevará a cabo en dos etapas clave:

**1. Implementación Inicial**

Durante esta fase, nos enfocaremos en el lanzamiento de los experimentos (pruebas A/B, encuestas, demos) y en la recolección de datos iniciales para establecer una línea base de rendimiento y comportamiento.

**Recopilación de Datos:**

*   **Métricas de Uso:** Se recopilarán datos sobre el uso de la aplicación, incluyendo el número de registros (para Q1 y Q6), la duración de las sesiones y la frecuencia de uso del dashboard.
*   **Interacciones de los Usuarios:** Se registrarán las interacciones de los usuarios con las funcionalidades clave, como clics en las recomendaciones personalizadas (para Q3), visualización de alertas de consumo (para Q4) y tiempo dedicado a interpretar los gráficos (para Q5).
*   **Feedback de Usuarios:** A través de encuestas y pruebas de usabilidad, se recogerán opiniones sobre la confianza en los datos del sistema (para Q2) y la claridad de la interfaz (para Q5).

**Análisis Comparativo:**

Se compararán los datos obtenidos durante esta fase con los grupos de control definidos. Por ejemplo, se analizará la tasa de registro del grupo con acceso al modo demo frente al grupo sin él (Q1, Q6) para evaluar el impacto inmediato.

**2. Seguimiento Continuo**

Después de la implementación inicial, se establecerá un proceso continuo de seguimiento para evaluar el rendimiento a largo plazo y realizar ajustes según sea necesario.

**Recopilación de Datos:**

*   **Métricas en Tiempo Real:** Se implementarán herramientas de análisis para monitorear el comportamiento de los usuarios en tiempo real, lo que permitirá identificar tendencias y patrones de consumo energético (Q3, Q4).
*   **Segmentación de Usuarios:** Los datos se segmentarán por tipo de usuario (ej. los que siguen recomendaciones vs. los que no) para entender mejor cómo cada grupo interactúa con la plataforma y cuál es el impacto real en su consumo.
*   **Tasa de Retención:** Se medirá la tasa de retención de usuarios a lo largo del tiempo para evaluar si las funcionalidades (recomendaciones, alertas) son efectivas en mantener a los usuarios comprometidos con la plataforma.

**Evaluación y Ajustes:**

*   **Informes Periódicos:** Se generarán informes semanales que resuman los hallazgos de los experimentos, incluyendo recomendaciones para validar o refutar las hipótesis.
*   **Iteración Basada en Datos:** Se realizarán ajustes en la plataforma basados en los datos recopilados y en el feedback de los usuarios, asegurando que Energix evolucione para satisfacer mejor las necesidades de sus usuarios y cumplir su objetivo de ahorro energético.

Este enfoque asegurará que Energix continúe evolucionando en función de los datos y permita tomar decisiones informadas para mejorar la experiencia del usuario y la efectividad de la plataforma.

## 8.3. Experimentation
### 8.3.1. To-Be User Stories.

Las siguientes historias de usuario fueron diseñadas a partir de las hipótesis planteadas en la sección 8.2.1, traduciendo cada pregunta de experimentación (Q1-Q6) en una funcionalidad concreta a implementar en la plataforma.

| User Story ID | Título | Descripción | Criterios de Aceptación | Relacionado con (Epic ID) |
| :--- | :--- | :--- | :--- | :--- |
| **US20** | Activar modo demo sin hardware | Como usuario potencial, quiero acceder a un modo demo sin necesidad de instalar un smart meter físico, para conocer la plataforma antes de comprometerme con la instalación. | **Escenario 1: Acceso al modo demo**<br>**Given** que el usuario visualiza la opción "Probar sin instalación"<br>**When** hace clic en el botón correspondiente<br>**Then** el sistema le otorga acceso a un dashboard con datos simulados de consumo<br>**And** muestra el mensaje: "Estás explorando una demo con datos de ejemplo"<br><br>**Escenario 2: Conversión de demo a cuenta real**<br>**Given** que el usuario está usando el modo demo<br>**When** decide continuar y registrarse con datos reales<br>**Then** el sistema migra su sesión a una cuenta activa<br>**And** muestra el mensaje: "Tu cuenta ha sido activada correctamente" | EP02 |
| **US21** | Validar precisión de datos del EMS | Como usuario, quiero comparar el consumo mostrado por la plataforma con mi recibo eléctrico real, para confiar en la exactitud de la información que recibo. | **Escenario 1: Carga de recibo para comparación**<br>**Given** que el usuario tiene un recibo eléctrico del mes<br>**When** sube una foto o ingresa el monto de su recibo en la sección "Validar consumo"<br>**Then** el sistema compara el valor con el consumo registrado en la plataforma<br>**And** muestra el porcentaje de coincidencia entre ambos valores<br><br>**Escenario 2: Discrepancia detectada**<br>**Given** que existe una diferencia significativa entre el recibo y los datos del sistema<br>**When** se completa la comparación<br>**Then** el sistema muestra el mensaje: "Detectamos una diferencia, revisa la calibración de tus dispositivos" | EP04 |
| **US22** | Medir impacto de recomendaciones personalizadas | Como usuario, quiero ver el ahorro de consumo logrado tras aplicar las recomendaciones personalizadas, para confirmar el valor real que me brinda la plataforma. | **Escenario 1: Comparación antes/después**<br>**Given** que el usuario ha recibido recomendaciones de ahorro<br>**When** consulta la sección "Impacto de mis recomendaciones"<br>**Then** el sistema muestra el porcentaje de reducción de consumo respecto al periodo anterior<br><br>**Escenario 2: Sin reducción significativa**<br>**Given** que el usuario aplicó recomendaciones pero no redujo su consumo<br>**When** revisa el reporte de impacto<br>**Then** el sistema muestra el mensaje: "Aún no se detecta una reducción significativa, sigue aplicando las recomendaciones" | EP07 |
| **US23** | Configurar alertas en horas pico | Como usuario, quiero recibir alertas específicas durante las horas de mayor demanda eléctrica, para modificar mi uso de electrodomésticos en esos momentos. | **Escenario 1: Activación de alertas en hora pico**<br>**Given** que el usuario configura su horario de hora pico<br>**When** un dispositivo está en uso durante ese rango horario<br>**Then** el sistema envía una alerta indicando el sobrecosto potencial<br>**And** muestra el mensaje: "Estás consumiendo en horario pico, considera posponer el uso"<br><br>**Escenario 2: Resumen de consumo en hora pico**<br>**Given** que finalizó el día<br>**When** el usuario consulta su resumen diario<br>**Then** el sistema muestra el porcentaje de consumo registrado durante las horas pico | EP03 |
| **US24** | Acceder a tutorial interactivo de interpretación de datos | Como usuario, quiero un tutorial interactivo que me explique cómo leer los gráficos en kWh y el consumo histórico, para tomar decisiones informadas sin confusión. | **Escenario 1: Primer acceso al dashboard**<br>**Given** que el usuario ingresa por primera vez al panel de consumo<br>**When** el sistema detecta que no ha completado el tutorial<br>**Then** muestra una guía paso a paso explicando cada gráfico y métrica<br><br>**Escenario 2: Reintentar tutorial**<br>**Given** que el usuario desea repasar la explicación<br>**When** selecciona "Ver tutorial" desde el centro de ayuda<br>**Then** el sistema vuelve a desplegar la guía interactiva | EP02 |
| **US25** | Probar la plataforma desde la Landing Page | Como visitante, quiero acceder a un botón de "Probar ahora" en la landing page, para conocer la plataforma sin necesidad de registrarme con datos reales. | **Escenario 1: Clic en "Probar ahora"**<br>**Given** que el visitante se encuentra en la Landing Page<br>**When** hace clic en el botón "Probar ahora"<br>**Then** el sistema lo redirige al modo demo sin solicitar registro previo<br><br>**Escenario 2: Conversión desde la demo**<br>**Given** que el visitante exploró el modo demo desde la landing<br>**When** decide registrarse<br>**Then** el sistema lo dirige al formulario de registro con sus datos de prueba precargados | EP10 |

### 8.3.2. To-Be Product Backlog
| # Orden | User Story ID | Título | Story Points (1 / 2 / 3 / 5 / 8) |
| :--- | :--- | :--- | :--- |
| 1 | US20 | Activar modo demo sin hardware | 5 |
| 2 | US21 | Validar precisión de datos del EMS | 5 |
| 3 | US22 | Medir impacto de recomendaciones personalizadas | 5 |
| 4 | US23 | Configurar alertas en horas pico | 3 |
| 5 | US24 | Acceder a tutorial interactivo de interpretación de datos | 3 |
| 6 | US25 | Probar la plataforma desde la Landing Page | 2 |
### 8.3.3. Pipeline-supported, Experiment-Driven To-Be Software Platform Lifecycle



#### 8.3.3.1. To-Be Sprint Backlogs

Cada una de las To-Be User Stories definidas en la sección 8.3.1 (US20–US25) fue descompuesta en work items/tasks concretos y planificada dentro del Sprint de experimentación. La estimación de cada tarea (en Story Points) suma exactamente los puntos asignados a su historia en el To-Be Product Backlog (sección 8.3.2), garantizando la trazabilidad entre la hipótesis, la historia y el trabajo ejecutado. Cada historia fue asignada a un integrante del equipo como responsable, permitiendo un desarrollo paralelo de los seis experimentos planteados.

**Sprint 1 — Experimentación (To-Be)**

| User Story ID | User Story Title | Task ID | Task Title | Description | Estimation (Story Points) | Assigned To | Status (To-do / In-Process / To-Review / Done) |
| :--- | :--- | :--- | :--- | :--- | :---: | :--- | :--- |
| **US20** | Activar modo demo sin hardware | TK01 | Diseñar interfaz del modo demo | Construir el dashboard de demostración con datos simulados de consumo y el mensaje "Estás explorando una demo con datos de ejemplo". | 3 | Jonatan Acuña | Done |
| **US23** | Configurar alertas en horas pico | TK07 | Configurar y disparar alertas en hora pico | Permitir definir el rango horario pico y enviar la alerta de sobrecosto durante el uso de dispositivos. | 2 | Antonio Duran | Done |
| **US24** | Acceder a tutorial interactivo de interpretación de datos | TK09 | Desarrollar tutorial interactivo paso a paso | Guía que explica los gráficos en kWh y el consumo histórico en el primer acceso al dashboard. | 2 | Yeira Huaman | Done |
|  |  | TK10 | Habilitar reintento del tutorial | Opción "Ver tutorial" en el centro de ayuda para volver a desplegar la guía interactiva. | 1 | Yeira Huaman | Done |
| **US25** | Probar la plataforma desde la Landing Page | TK11 | Implementar botón "Probar ahora" | Añadir el botón en la Landing Page que redirige al modo demo sin solicitar registro previo. | 1 | Joan Teves | Done |
|  |  | TK12 | Precargar datos de prueba en el registro | Dirigir al formulario de registro con los datos de la demo precargados al convertir la sesión. | 1 | Joan Teves | Done |

**Total del Sprint:** 23 Story Points (US20: 5 · US21: 5 · US22: 5 · US23: 3 · US24: 3 · US25: 2).

#### 8.3.3.2. Implemented To-Be Landing Page Evidence

**US25 — Probar la plataforma desde la Landing Page**

El botón "Probar ahora" en la Landing Page redirige al visitante al modo demo del Frontend sin solicitar registro previo, cumpliendo el escenario 1 de US25.

![Landing Page con el botón "Probar ahora" en la barra de navegación](../../assets/capitulo-8/us25-landing-probar-ahora.png)

#### 8.3.3.3. Implemented To-Be Frontend-Web Application Evidence

**US20 — Activar modo demo sin hardware**

La ruta pública `/demo` muestra un dashboard con datos de consumo simulados y el aviso "Estás explorando una demo con datos de ejemplo. Crea una cuenta para conectar tus propios dispositivos.", sin requerir sesión iniciada.

![Dashboard de simulación en modo demo público](../../assets/capitulo-8/us20-demo-dashboard.png)

**US21 — Validar precisión de datos del EMS**

En "Validar consumo" el usuario ingresa el monto de su recibo eléctrico y el sistema lo compara contra la factura estimada por la plataforma, mostrando el porcentaje de coincidencia y el mensaje de discrepancia cuando corresponde.

![Resultado de comparar el recibo ingresado contra la factura estimada](../../assets/capitulo-8/us21-validate-consumption.png)

**US22 — Medir impacto de recomendaciones personalizadas**

"Impacto de mis recomendaciones" compara el consumo del periodo actual contra el periodo anterior como aproximación al efecto de las recomendaciones aplicadas, mostrando el mensaje correspondiente cuando aún no hay una reducción significativa.

![Comparación de consumo entre periodo anterior y actual](../../assets/capitulo-8/us22-recommendations-impact.png)

**US23 — Configurar alertas en horas pico**

Desde "Configuración" el usuario define el rango horario de hora pico (y un umbral de alerta opcional) usado para disparar las notificaciones de sobrecosto durante ese horario.

![Editor del horario de hora pico en Configuración](../../assets/capitulo-8/us23-settings-peak-hour.png)

**US24 — Acceder a tutorial interactivo de interpretación de datos**

El tutorial se despliega automáticamente en el primer acceso al dashboard y puede volver a abrirse en cualquier momento desde "Tutoriales y Guías" en el centro de ayuda.

![Tutorial interactivo reabierto desde el centro de ayuda](../../assets/capitulo-8/us24-tutorial-reopened.png)

**US25 — Probar la plataforma desde la Landing Page (conversión de demo a cuenta real)**

Al hacer clic en "Crear cuenta" desde la demo, el formulario de registro muestra un resumen de la sesión simulada (consumo semanal y ahorro potencial) antes de que el visitante complete sus datos reales.

![Formulario de registro con el resumen de la sesión demo precargado](../../assets/capitulo-8/us25-register-demo-banner.png)

#### 8.3.3.4. Implemented To-Be Native-Mobile Application Evidence

**No aplica.** El alcance del producto Energix (Smart Energy Management System) comprende Landing Page, Web Application y RESTful API; no contempla el desarrollo de una aplicación móvil nativa en esta fase del proyecto, por lo que no se presenta evidencia de implementación de las To-Be User Stories en Mobile.

#### 8.3.3.5. Implemented To-Be RESTful API and/or Serverless Backend Evidence

**US25 — Probar la plataforma desde la Landing Page (conversión de demo a cuenta real)**

El endpoint `POST /api/v1/authentication/sign-up` registra al visitante que decide convertir su sesión de demo en una cuenta real, devolviendo el perfil creado con estado `201 Created`.

![Respuesta 201 Created del endpoint sign-up con los datos del usuario registrado](../../assets/capitulo-8/us25-api-signup.png)

El endpoint `POST /api/v1/authentication/sign-in` autentica al usuario recién registrado y retorna su perfil junto con el token JWT.

![Respuesta 200 OK del endpoint sign-in con el perfil del usuario y el token JWT](../../assets/capitulo-8/us25-api-signin.png)

**US21 — Validar precisión de datos del EMS**

El endpoint `POST /api/v1/dashboard/validate-receipt` compara el monto del recibo ingresado por el usuario contra el consumo estimado por la plataforma, retornando el porcentaje de coincidencia y el mensaje de discrepancia cuando corresponde.

![Respuesta del endpoint validate-receipt mostrando la discrepancia entre el recibo ingresado y el consumo estimado](../../assets/capitulo-8/us21-api-validate-receipt.png)

**US22 — Medir impacto de recomendaciones personalizadas**

El endpoint `GET /api/v1/reports/compare` recibe los rangos de fechas de dos periodos y retorna el consumo total y diario de cada uno junto con la diferencia porcentual entre ambos, permitiendo cuantificar el efecto de las recomendaciones aplicadas.

![Respuesta del endpoint compare con el consumo de ambos periodos y la diferencia porcentual](../../assets/capitulo-8/us22-api-compare-consumption.png)

**US23 — Configurar alertas en horas pico**

El endpoint `GET /api/v1/reports/peak-hour-summary` informa si el usuario ya configuró su horario de hora pico.

![Respuesta del endpoint peak-hour-summary indicando que el horario de hora pico aún no fue configurado](../../assets/capitulo-8/us23-api-peak-hour-summary.png)

El endpoint `PUT /api/v1/settings` permite definir dicho horario (rango `peakHourStart`/`peakHourEnd`) junto con el umbral de consumo (`highConsumptionThresholdKwh`) que dispara la alerta.

![Respuesta del endpoint settings tras actualizar el horario de hora pico (18:00–23:00) y el umbral de consumo](../../assets/capitulo-8/us23-api-update-settings.png)

#### 8.3.3.6. Team Collaboration Insights

Se presentan los analíticos de contribución de GitHub para los tres repositorios involucrados en la implementación de las To-Be User Stories (US20–US25), evidenciando la participación del equipo durante el sprint de experimentación.

**Repositorio de Reporte**

![Analíticos de colaboración del repositorio de Reporte: 6 integrantes con commits registrados entre abril y junio](../../assets/capitulo-8/collaboration-insights-reporte.png)

**Repositorio de Backend**

![Analíticos de colaboración del repositorio de Backend: 4 integrantes con commits concentrados entre mayo y julio](../../assets/capitulo-8/collaboration-insights-backend.png)

**Repositorio de Frontend**

![Analíticos de colaboración del repositorio de Frontend: 3 integrantes con commits concentrados en mayo](../../assets/capitulo-8/collaboration-insights-frontend.png)


### 8.3.4. To-Be Validation Interviews
Las entrevistas de validación del Capítulo VIII están diseñadas para evaluar las
nuevas funcionalidades experimentales implementadas a partir de las hipótesis definidas
Las entrevistas están dirigidas a los mismos segmentos objetivo: propietarios de vivienda y estudiantes que alquilan
#### 8.3.4.1. Diseño de Entrevistas.

**Preguntas para Segmento #1: Propietarios de Vivienda**

1. ¿El botón "Probar ahora" en la Landing Page facilitó que pudieras explorar la plataforma en el modo demo (con datos simulados) de forma inmediata y sin registrarte?
2. ¿Ver el funcionamiento de la plataforma con datos simulados en la demo te convenció para registrarte posteriormente con una cuenta real?
3. ¿Poder ingresar el monto de tu recibo físico en la sección "Validar consumo" y compararlo con el consumo estimado del sistema aumenta tu confianza en la precisión de la plataforma?
4. ¿El gráfico comparativo de la sección "Impacto de recomendaciones" te muestra de forma clara e intuitiva el ahorro que has logrado en soles y kWh?
5. ¿Poder configurar el "Horario de hora punta" (18:00 - 23:00) bajo Configuración y recibir alertas te motivaría a trasladar el uso de tus electrodomésticos a horarios de menor tarifa?
6. ¿El tutorial interactivo "Introducción al sistema" (disponible en Tutoriales y Guías) fue claro y te ayudó a interpretar los gráficos de consumo en kWh sin asistencia técnica?

**Preguntas para Segmento #2: Estudiantes que Alquilan**

1. Como estudiante que alquila, ¿poder probar la plataforma en modo demo (con el botón "Probar ahora" de la Landing) sin instalar un dispositivo físico en tu cuarto fue decisivo para motivarte a usarla?
2. ¿La información y los gráficos simulados de la demo te resultaron útiles y suficientes para comprender el beneficio de la aplicación antes de crear una cuenta?
3. Si compartes gastos con compañeros de cuarto, ¿comparar tu recibo de luz en "Validar consumo" te serviría para hacer una división del cobro más transparente y justa?
4. ¿El gráfico en la sección "Impacto de recomendaciones" te ayuda a visualizar fácilmente si tus esfuerzos de ahorro (como apagar tu laptop o luces) reducen el consumo en kWh?
5. ¿Recibir alertas basadas en el "Horario de hora punta" te convencería de programar el uso de tus dispositivos de estudio o cocina fuera de ese rango de mayor costo?
6. ¿El tutorial "Introducción al sistema" que se abre desde Configuración aclaró tus dudas y te permitió comprender el dashboard de forma autónoma?

#### 8.3.4.2. Registro de Entrevistas.

Link del Video: https://shorturl.at/7BcSC

**ENTREVISTAS SEGMENTO OBJETIVO 1: PROPIETARIOS DE VIVIENDA**

**ENTREVISTA 1**

![TOBEVALIDATION-1-Propietario.png](../../assets/capitulo-8/TOBEVALIDATION-1-Propietario.png)


Inicia: 0 minutos y 0 segundos

Duración: 7 minutos y 5 segundos

Nombre: Martha Araujo

Edad:  52

Distrito: Miraflores

Resumen: La propietaria destacó la velocidad de acceso a la demo interactiva sin registrarse como un acierto para la experiencia de usuario. Mencionó que la comparación del recibo en "Validar consumo" le dio seguridad sobre la precisión del sistema al alinearse con la medición de Enel. Validó positivamente el gráfico de "Impacto de recomendaciones" por su claridad visual. Afirmó que la alerta en el "Horario de hora punta" le resultará muy útil para pausar electrodomésticos grandes como la lavadora y que el tutorial interactivo es directo y resuelve cualquier duda de usabilidad.


**ENTREVISTA 2**

![TOBEVALIDATION-2-Propietario.png](../../assets/capitulo-8/TOBEVALIDATION-2-Propietario.png)

Inicia:  7 minutos y 5 segundos

Duración:  3 minutos y 5 segundos

Nombre: Juan Carlos Mendoza

Edad: 45 años

Distrito: Surco

Resumen: El participante evaluó la facilidad de ingreso a la demo interactiva mediante el botón "Probar ahora", indicando que agiliza la toma de decisiones al eliminar la barrera del registro inicial. Validó positivamente la función "Validar consumo" al notar una correlación del 93% entre el recibo físico y la estimación del sistema. Asimismo, afirmó que el gráfico de "Impacto de recomendaciones" y el "Horario de hora punta" en la sección de alertas son herramientas intuitivas que le motivarían a reordenar el uso de sus dispositivos de alto consumo para ahorrar costos. Destacó que el tutorial de "Introducción al sistema" es claro y evita la necesidad de soporte técnico.

**ENTREVISTAS SEGMENTO OBJETIVO 2: ESTUDIANTES QUE ALQUILAN**

**ENTREVISTA 1**

![TOBEVALIDATION-1-Estudiante.jpeg](../../assets/capitulo-8/TOBEVALIDATION-1-Estudiante.png)


Inicia: 0 minutos y 0 segundos

Duración: 2 minutos y 46 segundos

Nombre: Roberto Flores

Edad: 23

Distrito: Ate

Resumen: El estudiante indicó que la demo sin hardware es excelente para personas que no pueden hacer modificaciones en sus cuartos alquilados. Comentó que la estimación y desglose de consumo por aparatos le permiten visualizar con claridad sus gastos. Validó que la función de "Validar consumo" es de gran utilidad para transparentar la división del recibo con sus compañeros de cuarto. Comentó que el gráfico de "Impacto de recomendaciones" y las alertas del "Horario de hora punta" incentivan la formación de hábitos de ahorro eficientes en sus dispositivos de estudio, y calificó el tutorial como un recurso rápido que resuelve dudas al instante.


**ENTREVISTA 2**

![TOBEVALIDATION-2-Estudiante.jpeg](../../assets/capitulo-8/TOBEVALIDATION-2-Estudiante.png)


Inicia: 2 minutos y 46 segundos

Duración: 5 minutos y 1 segundo

Nombre: Daniela Gómez

Edad: 21

Distrito: San Miguel

Resumen: La participante validó la conveniencia de probar la aplicación mediante la demo sin registros. Indicó que la sección "Validar consumo" le permite contrastar de manera directa el cobro del casero con sus consumos reales, asegurando una división justa con los roomies. Afirmó que el gráfico de "Impacto de recomendaciones" ayuda a medir el ahorro semanal y que las notificaciones del "Horario de hora punta" le facilitarán programar el uso de sus dispositivos de estudio antes de las 18:00 horas. Además, valoró positivamente la brevedad y sencillez del tutorial de inducción.

## 8.4. Experiment Aftermath & Analysis
### 8.4.1. Analysis and Interpretation of Results

Las entrevistas de validación tuvieron como objetivo evaluar la aceptación y efectividad de las nuevas funcionalidades implementadas en la plataforma a partir de las hipótesis planteadas durante el desarrollo del proyecto. Estas entrevistas se realizaron con los dos segmentos objetivo: propietarios de vivienda y estudiantes que alquilan, quienes interactuaron con las nuevas características del sistema y compartieron su percepción sobre su utilidad, facilidad de uso y aporte a la experiencia de usuario.

Las preguntas fueron diseñadas para analizar aspectos relacionados con la accesibilidad de la plataforma, la confianza en las estimaciones de consumo, la claridad de las visualizaciones, la utilidad de las alertas inteligentes y la comprensión del sistema mediante el tutorial interactivo. Los resultados obtenidos permitieron identificar el nivel de aceptación de cada funcionalidad y verificar si estas responden adecuadamente a las necesidades de los usuarios, proporcionando información valiosa para la mejora continua de la plataforma.

### **Preguntas Formuladas**

1. ¿El botón "Probar ahora" facilitó explorar la plataforma sin necesidad de registrarse?
2. ¿La experiencia del modo demo motivó el registro posterior en la plataforma?
3. ¿La funcionalidad "Validar consumo" incrementa la confianza en la precisión de las estimaciones del sistema?
4. ¿El gráfico de "Impacto de recomendaciones" permite comprender fácilmente el ahorro obtenido?
5. ¿Las alertas configurables del "Horario de hora punta" incentivarían cambios en los hábitos de consumo eléctrico?
6. ¿El tutorial interactivo "Introducción al sistema" facilita el aprendizaje y comprensión de la plataforma?

Estas preguntas fueron respondidas por cinco participantes pertenecientes a los segmentos objetivo: dos propietarios de vivienda y tres estudiantes que alquilan. A continuación, se presentan los resultados obtenidos.

### **Análisis de Datos Demográficos**

**Distribución de participantes**

Las entrevistas fueron realizadas a cinco usuarios pertenecientes al público objetivo del proyecto.

- **Propietarios de vivienda**: 2 participantes (40%).
- **Estudiantes que alquilan**: 3 participantes (60%).

**Distribución de edades**

Las edades de los participantes oscilaron entre 20 y 52 años.

- 20-23 años: 60%
- 45-52 años: 40%

Los resultados muestran que la plataforma resulta comprensible tanto para usuarios jóvenes como para propietarios con mayor experiencia en la administración de gastos del hogar.

### **Evaluación de Funcionalidades**

**Modo Demo ("Probar ahora")**

La totalidad de los participantes valoró positivamente la posibilidad de acceder al sistema mediante el botón "Probar ahora", destacando que elimina la necesidad de crear una cuenta antes de conocer el funcionamiento de la plataforma.

Los propietarios consideraron que esta característica agiliza la toma de decisiones, mientras que los estudiantes resaltaron que pueden probar el sistema sin instalar dispositivos físicos en una vivienda alquilada.

**Resultado observado**: aceptación del 100%.

**Registro posterior al uso del Demo**

Los participantes indicaron que experimentar previamente las funcionalidades mediante datos simulados incrementa la confianza en el producto y aumenta la intención de registrarse posteriormente con una cuenta real.

Esta funcionalidad reduce la incertidumbre inicial y facilita la adopción de la plataforma.

**Resultado observado**: aceptación del 100%.

**Función "Validar consumo"**

Todos los entrevistados consideraron que comparar el recibo físico con la estimación generada por el sistema incrementa significativamente la confianza en la precisión de los resultados.

Los propietarios destacaron la similitud entre la estimación del sistema y el consumo registrado por la empresa eléctrica, mientras que los estudiantes valoraron esta función como una herramienta útil para realizar una distribución más justa del recibo de electricidad entre compañeros de vivienda.

**Resultado observado**: aceptación del 100%.

**Impacto de recomendaciones**

Los cinco participantes afirmaron que el gráfico comparativo permite visualizar de forma sencilla el ahorro conseguido tanto en consumo energético (kWh) como en costo económico (soles).

Los estudiantes señalaron que el gráfico facilita el seguimiento semanal de sus hábitos de ahorro, mientras que los propietarios destacaron su utilidad para evaluar la efectividad de las recomendaciones ofrecidas por la plataforma.

**Resultado observado**: aceptación del 100%.

**Alertas de Horario de Hora Punta**

Todos los entrevistados indicaron que recibir notificaciones durante el horario de mayor tarifa constituye un incentivo para modificar los hábitos de consumo eléctrico.

Los propietarios manifestaron que reorganizarían el uso de electrodomésticos de alto consumo, como lavadoras y otros equipos eléctricos, mientras que los estudiantes mencionaron que programarían el uso de dispositivos de estudio y cocina fuera del horario punta.

**Resultado observado**: aceptación del 100%.

**Tutorial "Introducción al sistema"**

La totalidad de los participantes calificó positivamente el tutorial interactivo, indicando que facilita la comprensión de los gráficos y del funcionamiento general de la plataforma sin requerir asistencia técnica.

Los entrevistados coincidieron en que la información presentada es breve, clara y suficiente para comenzar a utilizar el sistema.

**Resultado observado**: aceptación del 100%.

### **Recomendaciones de los Usuarios**

Durante las entrevistas también se identificaron aspectos que los participantes consideran especialmente valiosos para futuras versiones de la plataforma:

- Mantener disponible el modo demo sin necesidad de registro.
- Conservar la funcionalidad "Validar consumo", ya que incrementa la confianza en las estimaciones del sistema.
- Continuar mostrando el ahorro mediante gráficos comparativos fáciles de interpretar.
- Mantener las alertas configurables de Horario de Hora Punta para promover hábitos de consumo responsables.
- Ampliar el contenido del tutorial con ejemplos adicionales sobre interpretación de gráficos y recomendaciones de ahorro energético.

### **Conclusión**

Los resultados de las entrevistas de validación evidencian una aceptación muy favorable de las nuevas funcionalidades implementadas en la plataforma. Tanto los propietarios de vivienda como los estudiantes que alquilan coincidieron en que el modo demo facilita la adopción inicial del sistema, mientras que la función "Validar consumo" fortalece la confianza en las estimaciones realizadas.

Asimismo, el gráfico de "Impacto de recomendaciones", las alertas del Horario de Hora Punta y el tutorial interactivo fueron percibidos como herramientas útiles que mejoran la experiencia del usuario y favorecen la adopción de hábitos de consumo energético más eficientes.

En conjunto, los resultados permiten validar las hipótesis planteadas para estas funcionalidades y respaldan su incorporación dentro de la versión final de la plataforma, evidenciando un alto nivel de aceptación por parte de ambos segmentos objetivo.

### 8.4.2. Re-scored and Re-prioritized Question Backlog

| Prioridad (1,2,3,5,8) | ID | Pregunta                                                                      |
|-----------------------| -- | ----------------------------------------------------------------------------- |
| 1                     | Q1 | ¿La instalación del smart meter reduce la adopción del sistema?               |
| 1                     | Q2 | ¿Los usuarios confían en los datos generados por el EMS?                      |
| 2                     | Q3 | ¿Las recomendaciones personalizadas generan reducción de consumo energético?  |
| 3                     | Q4 | ¿Las alertas de consumo en tiempo real modifican el uso de electrodomésticos? |
| 5                     | Q5 | ¿Los usuarios entienden el consumo mostrado en kWh y gráficos del EMS?        |
| 8                     | Q6 | ¿Un modo demo sin hardware incrementa la intención de uso?                    |


## 8.5. Continuous Learning
### 8.5.1. Shareback Session Artifacts: Learning Workflow

## 8.6. To-Be Software Platform Pre-launch
### 8.6.1. About-the-Product Intro Video

El siguiente video presenta EMS, la solución desarrollada por el equipo Energix para transformar la forma en que los hogares gestionan su consumo energético. A través de este video se podrá conocer las principales funcionalidades del producto: el dashboard de consumo eléctrico, el sistema de alertas en horas pico, el motor de recomendaciones personalizadas, la sección de validación de datos frente al recibo eléctrico real, y el modo demo que permite explorar la plataforma sin necesidad de instalar hardware. Todo ello refleja los experimentos validados durante el ciclo de desarrollo, confirmando el valor que EMS genera para sus usuarios.

**Video About the Product - Youtube:** https://www.youtube.com/watch?v=x35kjae2CKE

**Video About the Product - OneDrive:** https://upcedupe-my.sharepoint.com/:v:/g/personal/u202312557_upc_edu_pe/IQBVKiLDyLuqRoNC4OPnXwQaAbi_7Zjs5w9uCaaUzZud3E0?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=cMHeaO

![AboutTheProduct.png](../../assets/capitulo-8/AboutTheProduct.png)