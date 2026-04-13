# Workflows Lyoss

Este es el repositorio central de CI/CD estándar para proyectos de Lyoss. Aquí centralizamos la lógica de automatización para mantener la consistencia en todos nuestros proyectos.

---

## Catálogo de Workflows Reutilizables

| ¿Qué necesitas? | Workflow Reusable | Descripción |
|----------|-------------|-----|
| **Publicar versiones** | `semantic-release.yml` | Genera Tags, Releases y Changelog automático basado en commits convencionales. |
| **Desplegar en GH Pages** | `gh-pages-deploy.yml` | Despliegue estático con auditoría de SEO mediante Lighthouse integrada. |
| **Sincronizar Labels** | `sync-labels.yml` | Sincroniza las etiquetas de Issues/PRs desde el estándar lyoss. |
| **Protección de Ramas** | `sync-rulesets.yml` | Aplica Rulesets (Protect main/dev) con restricciones de merge y borrado. |

---

## Guía de Inicio Rápido

### 1. Inicialización del Repositorio (Labels y Rulesets)
Para que tu repo tenga las etiquetas de colores y las ramas `main` y `dev` protegidas automáticamente:

1. Crea el archivo `.github/workflows/repo-setup.yml` en tu proyecto.
2. Copia el contenido de [examples/bootstrap.yml](./examples/bootstrap.yml).
3. Ejecútalo manualmente desde la pestaña **Actions**.

### 2. Configuración de Versiones (Semantic Release)
Para gestionar el versionado automático y el Changelog:

1. Asegúrate de tener el archivo [release-config.yml](./examples/release-config.yml) en la carpeta `.github` de tu proyecto.
2. Crea tu workflow de release llamando a `semantic-release.yml`. [Ver ejemplo](./examples/use-semantic-release.yml).

### 3. Despliegue (Astro u otros)
Si tu proyecto es un sitio estático:

* **¿Usas Astro?**: Utiliza el workflow de despliegue. [Ver ejemplo](./examples/use-deploy-astro.yml)
* **Otros Frameworks**: Puedes usar el mismo ejemplo de Astro pero modificando el comando de `build`, asegurándote de que el output se genere en `./dist`.

---

## Estándares lyoss

Los siguientes archivos en la raíz de este repositorio definen el estándar de Lyoss. Cualquier cambio aquí se replicará en todos los proyectos que ejecuten los sincronizadores:

* [**labels.json**](./labels.json): Definición de nombres, colores y descripciones de etiquetas.
* [**rulesets.json**](./rulesets.json): Reglas de protección para `main` (Merge commit) y `dev` (Squash).

---

> [!TIP]
> **Permisos**: Asegúrate de que tus workflows tengan los permisos necesarios (`issues: write`, `repository-projects: write`, `contents: write`) para que la sincronización funcione correctamente.
