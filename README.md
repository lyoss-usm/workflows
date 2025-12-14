# Workflows Lyoss

Este es el repositorio central de CI/CD estandar para proyectos de Lyoss. Aqui guardamos los flujos de trabajo reutilizables para no configurarlos una y otra vez en cada proyecto.

---

## Catalogo de Workflows

| ¿Que necesitas? | Workflow | Descripcion |
|----------|-------------|-----|
| **Publicar versiones** | `semantic-release.yml` | Genera Tags, Releases y Changelog automatico basado en commits. (principalmente PRs) |
| **Desplegar en GH Pages** | `gh-pages-deploy.yml` | Sube el sitio estatico a GH Pages con Auditoria de SEO con Lighthouse |
| **Configurar labels** | `examples/setup-labels.yml` | Crea las labels estandar para Issues y PRs |

---

## QuickStart

### Paso 1: Hacer el setup de labels
1. Copia el workflow [examples/setup-labels.yml](./examples/setup-labels.yml) a `.github/workflows/setup-labels.yml` en tu proyecto.
2. (opcional) Modifica las labels en el archivo si es necesario.
3. Ejecutalo con el boton manual en la pestaña de Actions.

### Paso 2: Configurar el Changelog
1. Copia la configuracion [examples/release-config.yml](./examples/release-config.yml) a la raiz de tu proyecto.
2. (opcional) Si modificaste las labels en el paso 1, actualiza las categorias en el archivo.

### Paso 3: Conectar Workflows

* **¿Usas Astro?**: [Ver ejemplo](./examples/use-deploy-astro.yml)
* **¿Solo Relase?**: [Ver ejemplo](./examples/use-semantic-release.yml)

> [!TIP]
> Tambien se puede modificar el step `build` del [ejemplo de astro](./examples/use-deploy-astro.yml) para adaptarlo a cualquier framework o generador de sitios estaticos. (pero asegurate de que el output vaya a la carpeta `./dist`)
