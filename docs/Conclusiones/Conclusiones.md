# Conclusiones

## Conclusiones y recomendaciones.

A partir del análisis detallado de la especificación, implementación, validación y prácticas DevOps del proyecto Energix, se establecen las siguientes conclusiones:

### Sobre la Especificación de Requerimientos (Capítulo III)
La fase de especificación de requerimientos demuestra un profundo entendimiento de los segmentos objetivos (propietarios y estudiantes que alquilan). Mediante el mapeo de escenarios (To-Be Scenario Mapping) y la adopción de principios de Domain-Driven Design (DDD) y Behavior-Driven Development (BDD), las necesidades del cliente se transformaron en un Product Backlog sólido. Las 20 User Stories están estructuradas con visiones funcionales y técnicas claras, asegurando que el desarrollo priorice el valor de negocio y establezca criterios de aceptación medibles y rigurosos.

### Sobre la Implementación del Producto (Capítulo V)
La implementación refleja una arquitectura robusta y procesos de gestión de la configuración (SCM) altamente estandarizados. La modularización del proyecto en repositorios separados, la aplicación estricta de convenciones de código, GitFlow y Conventional Commits, evidencian un trabajo colaborativo ordenado y profesional. El despliegue de las soluciones bajo un modelo SaaS en infraestructuras cloud modernas (Netlify para la Landing Page, Vercel para el Frontend en Angular, Render y Aiven para el Backend en Spring Boot) resultó en un producto funcional, documentado (Swagger), seguro y escalable.

### Sobre la Verificación y Validación (Capítulo VI)
La estrategia de validación garantiza la alta calidad del sistema mediante la ejecución en múltiples capas de pruebas. La implementación de pruebas unitarias y de integración certifica la robustez de las entidades principales y los endpoints del API. Por otro lado, la ejecución de pruebas orientadas al comportamiento (BDD) y pruebas de sistema, mapeadas una a una con las User Stories (US01 a US20), valida que cada funcionalidad cumple estrictamente con los criterios de aceptación y las expectativas del usuario final.

### Sobre las Prácticas DevOps (Capítulo VII)
La adopción de prácticas DevOps soportadas por GitHub Actions ha madurado el ciclo de vida de desarrollo del software. La automatización de la integración continua (CI) previene la introducción de código con fallas a través de pruebas automatizadas sobre una base de datos real. Asimismo, las fases de entrega y despliegue continuo (CD) permiten empaquetar artefactos inmutables (contenedores Docker en ghcr.io) y desplegarlos automáticamente en producción (Render). Todo esto otorga entregas ágiles, seguras y con trazabilidad exacta entre cada commit y la versión desplegada en producción.
