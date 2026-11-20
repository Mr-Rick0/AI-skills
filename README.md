# AI-skills

Colección personal de Agent Skills de [Mr-Rick0](https://github.com/Mr-Rick0), para reutilizar instrucciones en distintos computadores y harnesses compatibles.

## Catálogo

| Skill | Objetivo | Instrucciones |
| --- | --- | --- |
| `eco-code` | Auditar el repositorio y reutilizar soluciones antes de introducir lógica nueva. | [SKILL.md](skills/eco-code/SKILL.md) |

## Instalar en distintos harnesses

Con Node.js 22.20 o posterior, ejecuta:

```sh
npx skills add Mr-Rick0/AI-skills --skill eco-code -g
```

El instalador permite seleccionar los agentes de destino. `-g` instala para el usuario, disponible entre proyectos; omítelo para instalar solo en el proyecto actual.

Consulta los agentes compatibles y sus rutas en la [documentación oficial del instalador](https://github.com/vercel-labs/skills).

La instalación requiere que la skill ya esté publicada en este repositorio. El formato compartido no garantiza que cada harness interprete las instrucciones o tenga las mismas herramientas. `eco-code` menciona Codex en su descripción original; sus instrucciones de auditoría se conservan tal como fueron proporcionadas.

### Alternativa desde Codex

```text
Usa $skill-installer para instalar eco-code desde
https://github.com/Mr-Rick0/AI-skills/tree/main/skills/eco-code
```

### Instalación manual

Copia la carpeta completa `skills/eco-code/` al directorio de skills que indique tu harness. Conserva `SKILL.md` dentro de esa carpeta y sigue las indicaciones de recarga del harness.

## Actualizar

Si instalaste con `npx skills`, puedes comprobar y aplicar actualizaciones con:

```sh
npx skills check
npx skills update
```

Si instalaste manualmente o con otro instalador, actualiza mediante ese mismo mecanismo y conserva cualquier cambio local antes de reemplazar archivos. Guardar cambios en GitHub no actualiza por sí solo las copias instaladas.

## Estructura

```text
AI-skills/
├── README.md
└── skills/
    └── eco-code/
        └── SKILL.md
```

Cada skill tiene una carpeta propia y un `SKILL.md` con encabezado YAML que incluye `name` y `description`. Agrega futuras skills en `skills/<nombre>/SKILL.md` y actualiza el catálogo.

## Publicación inicial

El repositorio de destino es https://github.com/Mr-Rick0/AI-skills.

Sube `README.md` y la carpeta `skills/` a la raíz de la rama `main`. Si descargaste el ZIP, descomprímelo primero y sube su contenido, sin la carpeta contenedora `AI-skills/` y sin subir el ZIP.

## Alcance

Este repositorio es un catálogo instalable desde GitHub; no registra automáticamente un marketplace de plugins en los distintos harnesses.

`eco-code` conserva el contenido original de su autor, con escapes y Markdown normalizados. La validación del paquete comprueba estructura e integridad, no el comportamiento de cada modelo.
