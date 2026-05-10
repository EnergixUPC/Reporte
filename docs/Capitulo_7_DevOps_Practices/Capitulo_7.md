# Capítulo VII: DevOps Practices

## 7.1. Continuous Integration

### 7.1.1. Tools and Practices.

La Integración Continua (CI) es la práctica mediante la cual cada cambio introducido al código fuente es verificado de forma automática mediante la construcción del proyecto y la ejecución de un conjunto de pruebas automatizadas. Para el backend de la plataforma —desarrollado en Java 25 con Spring Boot— se utiliza **GitHub Actions** como plataforma de ejecución de pipelines. El pipeline de CI se dispara ante eventos de `push` y `pull_request` dirigidos a las ramas `main` y `develop`, garantizando que ningún cambio sea integrado sin pasar previamente por la suite de verificación automatizada.

A continuación se describen las herramientas y prácticas que componen la etapa de Integración Continua:

| Herramienta | Versión | Propósito en el proyecto |
|---|---|---|
| **GitHub Actions** | — | Plataforma de orquestación de pipelines CI/CD nativa de GitHub. Ejecuta los workflows definidos en `.github/workflows/` ante eventos de repositorio. |
| **actions/checkout** | v4 | Obtiene el código fuente del repositorio dentro del runner para su procesamiento. |
| **actions/setup-java** | v4 | Configura el entorno de ejecución Java 25 (distribución Temurin) con caché de dependencias Maven integrada. |
| **Java 25 (Temurin)** | 25 | JDK de distribución abierta adoptada como entorno de compilación y ejecución del backend Spring Boot. |
| **Apache Maven** | 3.9.11 | Herramienta de gestión y construcción del proyecto Java. Se ejecuta `mvn test -B` en modo no interactivo para compilar el código y ejecutar la suite de pruebas. |
| **JUnit 5** | 5.12.2 | Marco de pruebas unitarias para Java. Permite definir y ejecutar pruebas sobre entidades, servicios y componentes de forma aislada, validando su comportamiento individual. |
| **Mockito** | 5.17.0 | Marco de mocking para Java. Facilita el aislamiento de dependencias externas durante las pruebas unitarias, permitiendo simular el comportamiento de colaboradores sin instanciarlos realmente. |
| **Cucumber** | — | Herramienta de Behavior-Driven Development (BDD). Permite escribir escenarios de prueba en lenguaje Gherkin (`Given / When / Then`), legibles tanto por el equipo técnico como por stakeholders del negocio. Los escenarios describen el comportamiento esperado del sistema desde la perspectiva del usuario, asegurando que el desarrollo esté alineado con las necesidades del negocio. Crea y prueba ejemplos basados en cómo debería comportarse el sistema, garantizando que la implementación esté alineada con los requisitos del negocio. |
| **MySQL 8.4** | 8.4 | Sistema de gestión de base de datos relacional levantado como servicio dentro del runner de GitHub Actions. Las pruebas de integración se ejecutan contra una base de datos real —no simulada— para garantizar la fidelidad del comportamiento en un entorno equivalente a producción. |

**Prácticas adoptadas:**

- **Pipeline disparado por eventos de integración:** El workflow CI se ejecuta ante `push` a `main` o `develop`, y ante `pull_request` hacia dichas ramas, asegurando que todo código candidato a integrarse haya sido verificado.
- **GitFlow como modelo de ramificación:** Las ramas `main` (producción) y `develop` (integración) actúan como puntos de control del pipeline, en coherencia con el flujo GitFlow adoptado por el equipo.
- **Pruebas sobre infraestructura real:** El pipeline levanta un servicio MySQL 8.4 con health checks configurados (`mysqladmin ping`) antes de ejecutar los tests, garantizando que las pruebas de integración se ejecuten contra una base de datos operativa.
- **Fail-fast:** Si alguna prueba falla, el pipeline se detiene y la integración del cambio es bloqueada, protegiendo la integridad de las ramas principales.
- **BDD con Cucumber y Gherkin:** Los escenarios de comportamiento se definen en archivos `.feature` usando el lenguaje Gherkin. Cucumber traduce estos escenarios en pruebas ejecutables, creando un puente directo entre la especificación de negocio y la verificación técnica automatizada.

### 7.1.2. Build & Test Suite Pipeline Components.

A continuación se presentan las evidencias visuales del pipeline de construcción y suite de pruebas ejecutado mediante GitHub Actions.

## 7.2. Continuous Delivery

### 7.2.1. Tools and Practices.

La Entrega Continua (Continuous Delivery) extiende la Integración Continua al automatizar el empaquetado y publicación del artefacto de software, dejándolo en un estado siempre listo para ser desplegado. Para el backend de la plataforma, esta etapa consiste en la construcción de una imagen Docker y su publicación en el registro de contenedores **GitHub Container Registry (ghcr.io)**. El pipeline de CD se dispara exclusivamente ante `push` a la rama `main`, garantizando que únicamente el código integrado y verificado sea entregado como artefacto.

| Herramienta | Versión | Propósito en el proyecto |
|---|---|---|
| **GitHub Actions** | — | Plataforma de orquestación. Ejecuta el workflow CD de forma automática ante merges a `main`. |
| **actions/checkout** | v4 | Obtiene el código fuente para el proceso de construcción de la imagen. |
| **docker/login-action** | v3 | Autentica el runner de GitHub Actions con GitHub Container Registry usando el token `GITHUB_TOKEN`, sin necesidad de credenciales adicionales. |
| **docker/metadata-action** | v5 | Genera automáticamente las etiquetas (tags) y labels de la imagen Docker. Produce el tag `sha-<commit>` para trazabilidad y `latest` para referencia siempre actualizada. |
| **docker/build-push-action** | v6 | Construye la imagen Docker a partir del `Dockerfile` del repositorio y la publica directamente en `ghcr.io`. Integra soporte nativo para caché de capas. |
| **GitHub Container Registry (ghcr.io)** | — | Registro de contenedores privado asociado al repositorio. Almacena y distribuye las imágenes Docker producidas por el pipeline. |
| **GitHub Actions Cache (GHA Cache)** | — | Mecanismo de caché de capas Docker integrado en el runner (`cache-from: type=gha`, `cache-to: type=gha,mode=max`). Reduce significativamente el tiempo de construcción en ejecuciones sucesivas. |
| **Docker** | — | Motor de contenedores. La imagen construida encapsula el backend Spring Boot junto con todas sus dependencias en un artefacto reproducible e inmutable. |

**Prácticas adoptadas:**

- **Entrega automática al merge en `main`:** Cada vez que un cambio es integrado a la rama principal —habiendo superado previamente el pipeline de CI— se desencadena automáticamente la construcción y publicación de la imagen Docker.
- **Inmutabilidad del artefacto mediante tags por SHA:** Cada imagen publicada lleva el tag `sha-<commit>`, lo que permite trazar con exactitud qué commit originó cada artefacto y revertir a una versión anterior en caso necesario.
- **Tag `latest` como referencia de la versión actual:** Facilita el consumo de la imagen más reciente en entornos de despliegue sin necesidad de conocer el SHA específico.
- **Optimización mediante caché de capas Docker:** El uso de `type=gha` como backend de caché reutiliza las capas de la imagen entre ejecuciones, reduciendo los tiempos de entrega.
- **Separación de responsabilidades CI/CD:** El pipeline CI valida la calidad del código; el pipeline CD empaqueta y entrega el artefacto. Ambos son workflows independientes y complementarios.
- **Principio del menor privilegio:** El pipeline CD utiliza `GITHUB_TOKEN` con permisos mínimos necesarios (`contents: read`, `packages: write`), sin exponer credenciales adicionales.

### 7.2.2. Stages Deployment Pipeline Components.

A continuación se presentan las evidencias visuales del pipeline de entrega continua, incluyendo la construcción y publicación de la imagen Docker en GitHub Container Registry.

**Pipeline CI — Build & Test**

![Backend CI Pipeline](../../assets/capitulo-7/BackendCI-Pipeline.png)

**Pipeline CD — Build & Push Docker Image**

![Backend CD Pipeline](../../assets/capitulo-7/BackendCD-Pipeline.png)

## 7.3. Continuous deployment

### 7.3.1. Tools and Practices.

El Despliegue Continuo (Continuous Deployment) representa la etapa final del pipeline DevOps, en la cual el artefacto verificado y entregado es desplegado de forma automatizada en el entorno de producción. En la arquitectura adoptada, la imagen Docker publicada en `ghcr.io` —con tag `latest` y trazabilidad por SHA de commit— constituye el único artefacto que llega al entorno productivo. El despliegue se realiza extrayendo dicha imagen desde el registro y ejecutándola en el entorno de producción, garantizando que lo que se prueba en CI es exactamente lo que se despliega.

| Herramienta | Versión | Propósito en el proyecto |
|---|---|---|
| **GitHub Container Registry (ghcr.io)** | — | Fuente única de verdad para la imagen Docker lista para producción. El entorno de producción extrae la imagen desde este registro. |
| **Docker** | — | Motor de contenedores en el servidor de producción. Ejecuta la imagen del backend Spring Boot de forma aislada y reproducible. |
| **GitHub Actions** | — | Orquesta el flujo completo: desde el push a `main`, pasando por la verificación en CI, hasta la construcción y publicación de la imagen en CD, dejando el artefacto listo para despliegue. |
| **Imagen Docker (`sha-<commit>` / `latest`)** | — | Artefacto inmutable que encapsula el backend Spring Boot con Java 25. Su tag SHA garantiza la trazabilidad exacta entre el commit en el repositorio y la versión desplegada en producción. |

**Prácticas adoptadas:**

- **Pipeline como única vía de entrega a producción:** Ningún artefacto llega al entorno productivo fuera del flujo automatizado CI → CD → Producción. Esto elimina despliegues manuales inconsistentes.
- **Trazabilidad commit-a-producción:** El tag `sha-<commit>` de la imagen Docker permite identificar con precisión qué estado exacto del código se encuentra ejecutándose en producción en cualquier momento.
- **Rollback controlado:** Ante un fallo en producción, es posible revertir al tag SHA inmediatamente anterior sin necesidad de recompilar el código, ya que las imágenes permanecen disponibles en el registro.
- **Entorno de producción alineado con CI:** La imagen desplegada en producción es el mismo artefacto construido a partir del código que superó las pruebas unitarias, de integración y BDD en el pipeline CI. Esto elimina la brecha entre el entorno de pruebas y el entorno productivo.
- **Separación de ramas por ambiente:** La rama `main` representa el estado de producción. La rama `develop` es el entorno de integración. Solo lo que llega a `main` activa el pipeline de despliegue.

### 7.3.2. Production Deployment Pipeline Components.

A continuación se presentan las evidencias visuales del pipeline de despliegue continuo a producción, incluyendo la extracción de la imagen desde ghcr.io y su ejecución en el entorno productivo.

## 7.4. Continuous Monitoring
### 7.4.1. Tools and Practices
### 7.4.2. Monitoring Pipeline Components
### 7.4.3. Alerting Pipeline Components
### 7.4.4. Notification Pipeline Components.
