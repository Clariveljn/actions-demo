# Automatización Continua con GitHub Actions

Este proyecto tiene como objetivo introducir la automatización básica de construcción y pruebas en un proyecto Node.js mediante el uso de **GitHub Actions**.  
A través de este ejercicio se va a configurar un flujo de trabajo (workflow) que se ejecuta automáticamente al hacer push, asegurando que el código sea funcional en todo momento.

## 🎯 Objetivos

- Comprender la estructura básica de GitHub Actions.
- Crear un workflow automático que ejecute pruebas al hacer push.
- Usar un archivo YAML para configurar jobs y steps.
- Proteger variables sensibles utilizando `secrets`.

## ❓ Preguntas de reflexión
### ¿Qué ventajas observaste al automatizar pruebas con GitHub Actions?
- Permite detectar errores rápidamente en cada `push` o `pull request`, asegurando la calidad del código de forma continua.
- No requiere instalación adicional, ya que está completamente integrado en GitHub.
- Usa entornos controlados (como ubuntu-latest) asegurando que las pruebas corran de forma consistente.
- Permite definir múltiples jobs y matrices para diferentes versiones de Node.js sin complicaciones.

### 🔍 Comparativa: GitHub Actions vs Jenkins

| Característica             | GitHub Actions                                 | Jenkins                                         |
|---------------------------|--------------------------------------------------|------------------------------------------------|
| **Integración**           | Integrado directamente en GitHub                | Requiere instalación y configuración manual    |
| **Configuración**         | YAML en el propio repositorio                   | Interfaz web o archivos Jenkinsfile            |
| **Facilidad de uso**      | Muy fácil de comenzar, especialmente en proyectos GitHub | Requiere más configuración inicial       |
| **Mantenimiento**         | GitHub se encarga del mantenimiento             | Requiere mantener el servidor y plugins        |
| **Escalabilidad**         | Escala automáticamente con runners de GitHub    | Requiere configurar nodos y agentes            |
| **Plugins/extensiones**   | Limitado, pero suficiente para muchas tareas CI/CD | Amplia biblioteca de plugins                  |
| **Seguridad**             | Usa `secrets` y control nativo de permisos GitHub | Seguridad configurable pero más manual        |                   |
| **Casos ideales**         | Proyectos hospedados en GitHub                  | Proyectos complejos o autoalojados             |

### ¿Qué mejoras podrías agregar a este pipeline?
- Linting automático con ESLint o Prettier.
- Ejecutar pruebas en diferentes versiones de Node.js (matrix build).
- Agregar análisis estático de código con herramientas como SonarQube.
- Cobertura de pruebas con herramientas como jest --coverage
- Enviar notificaciones de fallos (por ejemplo, a Slack o Discord).  

### ¿Qué consideraciones de seguridad aplicarías en proyectos reales?
- No incluir información sensible en el repositorio; usar `secrets` para claves, tokens o entornos.
- Revisar dependencias con herramientas como OWASP Dependency Check (SCA)
- Restringir permisos del workflow, por defecto, los workflows tienen permisos de escritura. Es recomendable reducirlos al mínimo necesario para evitar riesgos de seguridad.
- Limitar la ejecución automática del workflow en ramas inseguras o forks de terceros para proteger el repositorio principal.

## 📌Ideas sobre cómo automatizar otros aspectos del proyecto

- **Auditoría de seguridad:** Añadir un paso para ejecutar `OWASP Dependency-Check` y detectar vulnerabilidades en dependencias automáticamente.
- **Análisis de calidad:** Integrar ESLint para revisar errores y malas prácticas en el código en cada push.
- **Despliegue automático:** Configurar un job que despliegue la app tras pasar las pruebas, agilizando la entrega continua.
