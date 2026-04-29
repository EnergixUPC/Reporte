# Capítulo V: Product Implementation

## 5.1. Software Configuration Management.
### 5.1.1. Software Development Environment Configuration.

**Project Management:**

Para la gestión del proyecto Energix, utilizamos WhatsApp como medio principal de comunicación, a través de un grupo grupal en el cual coordinamos tareas, compartimos avances y discutimos decisiones del proyecto en tiempo real. Por otro lado, Discord fue nuestra plataforma para realizar llamadas de voz en equipo, donde organizamos la distribución de responsabilidades entre los integrantes, complementamos ideas y resolvimos dudas de forma síncrona. Asimismo, utilizamos GitHub no solo para el control de versiones, sino también como repositorio centralizado de toda la documentación del proyecto, incluyendo el reporte y la landing page.

**Requirements Management:**

Para la gestión de los requisitos del proyecto Energix, el equipo definió colaborativamente las historias de usuario que representan las principales funcionalidades del sistema. Estas fueron priorizadas y organizadas en el Product Backlog, considerando las necesidades de nuestros segmentos objetivo: propietarios de viviendas y estudiantes que alquilan. El proceso fue participativo, con todos los integrantes del equipo aportando en la identificación y refinamiento de los requerimientos funcionales y no funcionales de la aplicación web.

**Product UX/UI Design:**

Para el diseño de la experiencia de usuario, utilizamos UXPressia, herramienta con la que elaboramos los User Personas, Empathy Maps, Journey Maps e Impact Maps del proyecto Energix. Esto nos permitió adoptar una perspectiva centrada en el usuario y comprender mejor las necesidades de nuestros segmentos objetivo. Para el diseño visual de la aplicación, empleamos Figma como herramienta de diseño colaborativo, a través de la cual creamos los Wireframes, Mock-ups y prototipos tanto de la aplicación web como de la versión móvil, sirviendo como guía previa al desarrollo.

**Software Development:**

Como entornos de desarrollo principales, el equipo utilizó Visual Studio Code y WebStorm. Visual Studio Code fue empleado para la creación del landing page y las aplicaciones web con HTML5, CSS3, JavaScript y TypeScript, mientras que WebStorm fue utilizado para trabajar con el framework Angular. Para el backend, adoptamos Spring Boot Framework, que nos permitió desarrollar servicios web RESTful en Java con una base escalable y robusta. Adicionalmente, LucidChart fue utilizado para la creación de diagramas UML, Wireflows y User Flows, y Structurizr para modelar la arquitectura del software mediante diagramas C4. Todo el código fuente fue gestionado en GitHub aplicando el flujo de trabajo GitFlow y la convención Conventional Commits, lo que garantizó un historial de cambios ordenado y comprensible para todos los integrantes.

**Software Testing:**

Para la validación de los criterios de aceptación del proyecto Energix, utilizamos el lenguaje Gherkin, el cual nos permite describir los escenarios de prueba bajo la estructura Given-When-Then. Esta metodología facilita la identificación de las variables de entrada y salida de cada funcionalidad, y al estar escrita en lenguaje natural, resulta comprensible tanto para el equipo técnico como para los stakeholders. La documentación de estas pruebas se gestionó junto con el resto del proyecto en los repositorios de GitHub, usando Markdown como lenguaje de marcado para los archivos README y la documentación técnica general. Gracias a este enfoque, el equipo garantiza que el software cumpla con los requerimientos definidos y que la calidad del producto final sea consistente con los objetivos del proyecto.


### 5.1.2. Source Code Management.

Usuarios de GitHub

| **Integrante**                 | **Nombre de Usuario** |
|--------------------------------|-----------------------|
| Acuña Corahua, Jonatan Ariel   | JonatanFD             |
| Duran Díaz, Antonio Rodrigo    | Sltcrd                |
| Huaman Olivos, Yeira Shari     | YeiShari              |
| Meza Solórzano, Didier Sebastian | DidierSebas           |
| Teves Samaniego, Joan Fernando | Joan3210              |
| Torres Lavandera, Andrés Rodrigo | AndresTorres202312557 |

La gestión del código fuente es parte fundamental del desarrollo de cualquier
proyecto de software, ya que nos permitirá rastrear cambios, revertir versionas y
coordinar a los diferentes integrantes del equipo a la misma vez. En ENERGIX,
utilizaremos GitHub como plataforma para alojar nuestros repositorios.

**URL de repositorio de Landing Page:** https://github.com/EnergixUPC/Landing-Page

**URL de repositorio de Frontend:** https://github.com/EnergixUPC/Frontend

**URL de repositorio de Backend:** https://github.com/EnergixUPC/Backend

**URL de repositorio Mobile:** https://github.com/EnergixUPC/Movil

**URL de repositorio de Reporte:** https://github.com/EnergixUPC/Reporte

Ejemplos de commits

• feat(login): add user authentication module

• fix(payment): resolve payment gateway issue

• docs(README): update setup instructions

Con estas estructuras, ENERGIX se puede gestionar eficientemente el flujo de
trabajo del desarrollo, asegurándonos una integración continua y una organización
clara del código.

### 5.1.3. Source Code Style Guide & Conventions.

En el proyecto Energix, hemos implementado una serie de guías de estilo y convenciones con el objetivo de asegurar que todos los integrantes del equipo de desarrollo sigan una estructura consistente y clara a lo largo de todo el proyecto, facilitando la legibilidad del código, mejorando la colaboración y garantizando que el código sea mantenible a largo plazo.

**Nomenclatura General**

Para asegurar la coherencia en todo el código, seguimos las siguientes directrices:

- Los nombres de variables, funciones y métodos utilizan camelCase.
- Los nombres de clases y componentes siguen la convención PascalCase.
- Para archivos y carpetas, se emplea la convención kebab-case.
- El uso de inglés es obligatorio para todos los identificadores, con el fin de asegurar la comprensión entre los miembros del equipo y seguir las buenas prácticas de la industria.

**HTML/CSS Conventions**

Para el desarrollo del landing page y las vistas de la aplicación web, seguimos las convenciones establecidas por el estándar HTML5 y las guías de estilo de Google para HTML y CSS:

- Los atributos de los elementos HTML se escriben en minúsculas.
- Las clases CSS siguen la convención kebab-case.
- Se evita el uso de estilos en línea; los estilos se definen en archivos .css o .scss separados.

**JavaScript/TypeScript Conventions**

Para el desarrollo con JavaScript y TypeScript, seguimos las guías de estilo de Airbnb y las recomendaciones oficiales de TypeScript:

- Se usa const y let en lugar de var.
- Se declaran los tipos explícitamente en TypeScript para mejorar la legibilidad y evitar errores en tiempo de compilación.
- Se evita el uso de any; en su lugar, se definen interfaces o tipos específicos.

**Angular Conventions**

Para el desarrollo del frontend con Angular, seguimos la Angular Style Guide oficial:

- Los componentes se nombran en PascalCase con el sufijo Component.
- Los servicios llevan el sufijo Service.
- Cada componente tiene su propio directorio con sus archivos .ts, .html y .css correspondientes.

**Spring Boot/Java Conventions**

Para el desarrollo del backend con Spring Boot, seguimos las convenciones estándar de Java y las recomendaciones de Spring:

- Los nombres de paquetes se escriben en minúsculas y de forma jerárquica.
- Las clases de controlador llevan el sufijo Controller.
- Las clases de servicio llevan el sufijo Service.
- Los repositorios llevan el sufijo Repository.
- Se aplican los principios RESTful para el diseño de endpoints, usando sustantivos en plural (ej. /api/v1/users, /api/v1/energy-records).

**Commits Convencionales**

Los tipos utilizados son:

- feat: para nuevas funcionalidades.
- fix: para corrección de errores.
- docs: para cambios en la documentación.
- style: para cambios de formato que no afectan la lógica.
- refactor: para reestructuración de código sin cambio de funcionalidad.
- test: para adición o modificación de pruebas.

### 5.1.4. Software Deployment Configuration.

En esta sección se detalla la configuración utilizada para el despliegue de los productos desarrollados en el proyecto Energix, abarcando la Landing Page, la aplicación web Frontend y el Backend del sistema SEMS.

**Landing Page — Netlify**

Para el despliegue de la landing page se utilizó Netlify. El proceso consistió en autenticarse con GitHub desde la plataforma, buscar la organización del proyecto, seleccionar el repositorio correspondiente y cargar los archivos. Una vez completado el proceso, Netlify generó automáticamente el enlace de publicación.
La landing page está disponible en: https://energixlp.netlify.app

**Frontend — Vercel**

El frontend desarrollado con Angular fue desplegado en Vercel, conectando el repositorio de GitHub para que cada merge a la rama principal genere un despliegue automático.
La aplicación web está disponible en: https://frontend-sems.vercel.app

**Backend — Render**

El backend con Spring Boot fue desplegado en Render, también con integración continua desde GitHub. Para proteger la dirección IP del servidor y evitar exponerla en un repositorio público, se configuró un proxy mediante Cloudflare Tunnel.

La documentación Swagger está en: https://theft-muscles-inner-protection.trycloudflare.com/swagger-ui/index.html

**Base de datos — Aiven**

La base de datos fue alojada en Aiven, con conexión bajo SSL obligatorio para la seguridad de los datos.

## 5.2. Product Implementation & Deployment.
### 5.2.1. Sprint Backlogs.

### Sprint 1

| User Story ID | User Story Title                | Task ID | Task Title                      | Description                                                  | Estimation | Assigned To     | Status |
|---------------|--------------------------------|---------|--------------------------------|--------------------------------------------------------------|------------|------------------|--------|
| US20          | Consultar la propuesta de valor| UT01    | Redactar contenido             | Crear texto sobre beneficios de la plataforma                | 2h         | Jonatan Acuña    | Done   |
|               |                                | UT02    | Diseñar sección                | Implementar diseño en la landing page                        | 3h         | Jonatan Acuña    | Done   |
| US21          | Acceder a FAQ                  | UT03    | Redactar preguntas             | Crear lista de preguntas frecuentes                          | 2h         | Yeira Huaman     | Done   |
|               |                                | UT04    | Implementar FAQ                | Desarrollar componente tipo acordeón                         | 3h         | Yeira Huaman     | Done   |
| US22          | Revisar planes de suscripción  | UT05    | Redactar planes                | Crear contenido de precios y beneficios                      | 3h         | Andrés Torres    | Done   |
|               |                                | UT06    | Diseñar comparación            | Implementar tabla/cards comparativos                         | 3h         | Andrés Torres    | Done   |
| US23          | Cambiar idioma                 | UT07    | Implementar selector idioma    | Permitir cambio entre español e inglés                       | 4h         | Antonio Duran    | Done   |
|               |                                | UT08    | Configurar traducciones        | Mapear textos en ambos idiomas                               | 3h         | Antonio Duran    | Done   |
| US01          | Registro de cuenta             | UT09    | Diseñar formulario             | Crear interfaz con validaciones                              | 3h         | Didier Meza      | Done   |
|               |                                | UT10    | Implementar registro           | Lógica para crear cuentas                                    | 4h         | Didier Meza      | Done   |
| US02          | Inicio de sesión               | UT11    | Diseñar login                  | Crear interfaz de inicio de sesión                           | 2h         | Joan Teves       | Done   |
|               |                                | UT12    | Implementar autenticación      | Validar credenciales                                         | 3h         | Joan Teves       | Done   |

### 5.2.2. Implemented Landing Page Evidence

Como parte de la implementación del producto, se desarrolló y consolidó la Landing Page de Energix, la cual representa el primer punto de interacción entre el usuario y la propuesta de valor del sistema. Esta página fue diseñada considerando criterios de usabilidad, accesibilidad y claridad en la comunicación de beneficios, permitiendo presentar de forma estructurada las funcionalidades principales del producto.

La Landing Page incluye secciones clave como la barra de navegación, pantalla de inicio, descripción de beneficios, presentación del producto, planes de suscripción, información del equipo, preguntas frecuentes y pie de página. Cada una de estas secciones fue implementada siguiendo los diseños previamente definidos en Figma, asegurando coherencia visual y experiencia de usuario.

A continuación, se presentan las evidencias correspondientes a la implementación final de la Landing Page:

![Barra de Navegación](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan0.png?raw=true)
![Inicio](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan1.png?raw=true)
![Beneficios](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan2.png?raw=true)
![Producto](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan3.png?raw=true)
![Suscripciones](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan4.png?raw=true)
![About the Team](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan5.png?raw=true)
![Preguntas Frecuentes](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan6.png?raw=true)
![Footer](https://github.com/EnergixUPC/Reporte/blob/develop/assets/capitulo-5/lan7.png?raw=true)

Adicionalmente, la Landing Page fue desplegada en un entorno productivo, permitiendo su acceso público para validación y retroalimentación continua. El despliegue se realizó mediante integración con el repositorio del proyecto, garantizando que cada actualización refleje de manera automática los cambios implementados por el equipo de desarrollo.

URL de la Landing Page desplegada: https://energixlp.netlify.app
### 5.2.3. Implemented Frontend-Web Application Evidence
### 5.2.4. Acuerdo de Servicio - SaaS
### 5.2.5. Implemented Native-Mobile Application Evidence
### 5.2.6. Implemented RESTful API and/or Serverless Backend Evidence
### 5.2.7. RESTful API documentation
### 5.2.8. Team Collaboration Insights

## 5.3. Video About-the-Product.
