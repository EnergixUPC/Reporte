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
### 8.2.2. Domain Business Metrics
### 8.2.3. Measures.
### 8.2.4. Conditions.
### 8.2.5. Scale Calculations and Decisions.
### 8.2.6. Methods Selection.
### 8.2.7. Data Analytics: Goals, KPIs and Metrics Selection.
### 8.2.8. Web and Mobile Tracking Plan.

## 8.3. Experimentation
### 8.3.1. To-Be User Stories.
### 8.3.2. To-Be Product Backlog
### 8.3.3. Pipeline-supported, Experiment-Driven To-Be Software Platform Lifecycle
#### 8.3.3.1. To-Be Sprint Backlogs
#### 8.3.3.2. Implemented To-Be Landing Page Evidence
#### 8.3.3.3. Implemented To-Be Frontend-Web Application Evidence
#### 8.3.3.4. Implemented To-Be Native-Mobile Application Evidence
#### 8.3.3.5. Implemented To-Be RESTful API and/or Serverless Backend Evidence
#### 8.3.3.6. Team Collaboration Insights
### 8.3.4. To-Be Validation Interviews
#### 8.3.4.1. Diseño de Entrevistas.
#### 8.3.4.2. Registro de Entrevistas.

## 8.4. Experiment Aftermath & Analysis
### 8.4.1. Analysis and Interpretation of Results
### 8.4.2. Re-scored and Re-prioritized Question Backlog

## 8.5. Continuous Learning
### 8.5.1. Shareback Session Artifacts: Learning Workflow

## 8.6. To-Be Software Platform Pre-launch
### 8.6.1. About-the-Product Intro Video
