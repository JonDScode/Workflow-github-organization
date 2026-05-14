# Tutorial GitHub para el Equipo

Guía práctica para trabajar con nuestra **organización en GitHub**: Issues, Pull Requests y GitHub Projects.

> 📸 **[IMAGEN 0 — Portada]**
> Logo del equipo/organización o screenshot de la página principal de la organización en GitHub (`github.com/nombre-de-la-org`).

---

## Tabla de contenidos

1. [Organización en GitHub](#1-organización-en-github)
2. [Issues](#2-issues)
3. [Pull Requests (PR)](#3-pull-requests-pr)
4. [GitHub Projects](#4-github-projects)
5. [Flujo completo end-to-end](#5-flujo-completo-end-to-end)
6. [GitHub Actions (resumen)](#6-github-actions-resumen)

---

## 1. Organización en GitHub

Una **organización** es un espacio compartido donde el equipo aloja repositorios, gestiona permisos y colabora.

### 1.1 Acceder a la organización

1. Inicia sesión en [github.com](https://github.com).
2. Haz clic en tu avatar (esquina superior derecha) → **Organizations**.

> **[IMAGEN 1.1.a]**
> 
><img width="418" height="577" alt="image" src="https://github.com/user-attachments/assets/5cde5e50-6525-488f-aeeb-090d41d075b6" />

3. Selecciona nuestra organización.


> 📸 **[IMAGEN 1.1.b]**
> Screenshot de la página principal de la organización mostrando: pestañas (Overview, Repositories, Projects, Packages, Teams, People, Settings) y la lista de repositorios.

### 1.2 Roles y equipos

Los miembros tienen roles según su responsabilidad:

- **Owner**: control total (no tocar nada salvo que sepas).
- **Member**: acceso estándar, asignado a uno o varios *teams*.
- **Outside collaborator**: acceso solo a repos puntuales.

Para ver tu rol y a qué equipo perteneces: pestaña **People** o **Teams**.

> 📸 **[IMAGEN 1.2]**
> Screenshot de la pestaña **Teams** mostrando los equipos creados (ej: `frontend`, `backend`, `devops`) con flechas señalando a qué team pertenece cada quién.

### 1.3 Notificaciones (importante)

Configura las notificaciones para no perderte menciones del equipo:

1. Avatar → **Settings** → **Notifications**.
2. En **Watching**, decide si quieres recibir todo, solo participaciones o solo menciones.

> 📸 **[IMAGEN 1.3]**
> Screenshot de **Settings → Notifications** mostrando las opciones de "Participating, @mentions and custom" recomendada.

---

## 2. Issues

Los **Issues** son tickets para registrar tareas, bugs, mejoras o preguntas. Son el **punto de entrada** de todo el trabajo.

### 2.1 Crear un Issue

1. Entra al repositorio.
2. Pestaña **Issues** → botón verde **New issue**.
3. Si hay plantillas configuradas, elige la que corresponda (Bug, Feature, etc.).

> 📸 **[IMAGEN 2.1.a]**
> Screenshot del repo con la pestaña **Issues** y el botón **New issue** resaltados.

> 📸 **[IMAGEN 2.1.b]**
> Screenshot de la pantalla de selección de plantillas (Bug report / Feature request / Custom). Si no tenemos plantillas aún, omitir esta imagen.

### 2.2 Estructura recomendada del Issue

**Título**: corto, claro, en imperativo. Ej:
- ✅ `Fix: el login falla con email en mayúsculas`
- ❌ `no funciona`

**Cuerpo** (usa Markdown):

```markdown
## Descripción
Breve explicación del problema o tarea.

## Pasos para reproducir (si es bug)
1. Ir a /login
2. Ingresar email "USUARIO@MAIL.COM"
3. Hacer clic en "Entrar"

## Comportamiento esperado
El login debería aceptar el email sin importar mayúsculas.

## Comportamiento actual
Devuelve error 400.

## Capturas / logs
(adjuntar imágenes arrastrándolas al cuadro de texto)
```

> 📸 **[IMAGEN 2.2]**
> Screenshot del formulario de nuevo issue con el título y el cuerpo bien rellenados como ejemplo. Resaltar la barra lateral derecha donde se asignan labels, assignees, etc.

### 2.3 Metadatos del Issue (barra lateral derecha)

| Campo | Para qué sirve |
|-------|----------------|
| **Assignees** | Quién es responsable de resolverlo |
| **Labels** | Categorización (`bug`, `feature`, `urgent`, `frontend`...) |
| **Projects** | Vincular al GitHub Project del equipo |
| **Milestone** | Agrupar por release o sprint |
| **Development** | Linkear ramas o PRs relacionados |

> 📸 **[IMAGEN 2.3]**
> Screenshot **zoom** de la barra lateral derecha del issue con todos los campos rellenos, cada uno con una flecha y nombre.

### 2.4 Crear una rama directamente desde el Issue

GitHub permite crear la rama de trabajo **desde el propio issue**, lo que la vincula automáticamente. Es la forma recomendada de empezar a trabajar:

1. Dentro del issue, barra lateral derecha → sección **Development**.
2. Clic en **Create a branch**.
3. GitHub propone un nombre tipo `123-titulo-del-issue` (puedes cambiarlo).
4. Selecciona el repo y la rama base (`main` o `develop`).
5. Clic en **Create branch**.

Después en tu máquina:

```bash
git fetch origin
git checkout 123-titulo-del-issue
```

Ventaja: el PR que abras desde esa rama ya queda enlazado al issue automáticamente.

> 📸 **[IMAGEN 2.4.a]**
> Screenshot de la sección **Development** en la barra lateral del issue con el enlace **Create a branch** resaltado.

> 📸 **[IMAGEN 2.4.b]**
> Screenshot del modal de creación de rama mostrando el nombre sugerido y el selector de rama base.

### 2.5 Comunicación dentro del Issue

- **Mencionar a alguien**: `@nombredeusuario` → le llega notificación.
- **Mencionar a un equipo entero**: `@nombre-org/nombre-team`.
- **Referenciar otro issue/PR**: `#123` se convierte en enlace automático.
- **Cerrar desde un commit/PR**: escribir `Closes #123` o `Fixes #123` en el mensaje.

> 📸 **[IMAGEN 2.5]**
> Screenshot de un issue con un comentario que incluya: una mención `@usuario`, una referencia `#45` y reacciones (👍 ❤️). Resaltar cada elemento.

### 2.6 Estados de un Issue

- **Open** (abierto, sin resolver)
- **Closed → Completed** (resuelto)
- **Closed → Not planned** (descartado, no se va a hacer)

> 📸 **[IMAGEN 2.6]**
> Screenshot del botón **Close issue** mostrando el desplegable con las dos opciones (Completed / Not planned).

### 2.7 Plantillas de Issue (Issue Templates)

Las plantillas estandarizan la información que se pide al crear un issue. Hay **dos formas** de configurarlas:

#### Opción A — desde la interfaz web (rápido)

1. Repo → **Settings** → barra lateral **Features** → sección **Issues** → **Set up templates**.
2. Clic en **Add template** → elegir entre *Bug report*, *Feature request* o *Custom*.
3. Editar y **Propose changes** → se hace commit a `main` automáticamente.

> 📸 **[IMAGEN 2.7.a]**
> Screenshot de **Settings → Features → Set up templates** mostrando el selector de plantillas.

#### Opción B — como archivos YAML en el repo (control total)

Crea la carpeta `.github/ISSUE_TEMPLATE/` y dentro un archivo por cada tipo de issue. Ejemplo de `feature_request.yml`:

```yaml
name: "Feature Request"
description: "Sugiere una nueva funcionalidad"
title: "[FEATURE] "
labels: ["enhancement"]
assignees: []

body:
  - type: markdown
    attributes:
      value: |
        ## Solicitud de funcionalidad
        Por favor completa los siguientes campos para describir la nueva funcionalidad.

  - type: textarea
    id: descripcion
    attributes:
      label: "📄 Descripción"
      description: "¿Qué se quiere implementar?"
      placeholder: "Ej: Un buscador en la parte superior del sitio"
    validations:
      required: true

  - type: textarea
    id: comentarios_adicionales
    attributes:
      label: "📝 Comentarios adicionales"
      description: "¿Consideraciones técnicas, referencias, links, etc.?"
      placeholder: "Ej: Requiere usar una API externa, diseño según Figma..."
    validations:
      required: false
```

Otro ejemplo útil: `bug_report.yml` con campos para *pasos para reproducir*, *comportamiento esperado*, *entorno*, etc.

**Tipos de campos disponibles** en el `body`:

| Tipo | Para qué sirve |
|------|----------------|
| `markdown` | Bloque de texto informativo (no editable) |
| `input` | Campo de una sola línea |
| `textarea` | Campo de texto largo |
| `dropdown` | Selector con opciones predefinidas |
| `checkboxes` | Lista de checkboxes |

Una vez los archivos están en `main`, al pulsar **New issue** aparecerá el selector con todas las plantillas.

> 📸 **[IMAGEN 2.7.b]**
> Screenshot de la estructura de carpetas en el repo mostrando `.github/ISSUE_TEMPLATE/feature_request.yml` y `bug_report.yml`.

> 📸 **[IMAGEN 2.7.c]**
> Screenshot de la pantalla de selección de plantilla al pulsar **New issue**, con las plantillas YAML listadas.

---

## 3. Pull Requests (PR)

Un **Pull Request** es la propuesta de fusionar cambios de una rama a otra (normalmente a `main` o `develop`). Es el momento de la **revisión de código**.

### 3.1 Flujo básico (terminal)

```bash
# 1. Asegúrate de estar en la rama base actualizada
git checkout main
git pull origin main

# 2. Crea una rama para tu tarea (nombre según convención del equipo)
git checkout -b feature/login-mayusculas

# 3. Trabaja, haz commits con mensajes claros
git add .
git commit -m "fix: normaliza email a minúsculas en login (#123)"

# 4. Sube la rama al remoto
git push -u origin feature/login-mayusculas
```

> 💡 **Tip**: incluir el número del issue (`#123`) en el mensaje del commit hace que GitHub enlace automáticamente ese commit al issue. Así, desde el issue se ve todo el progreso sin tener que buscar.

**Convención de nombres de ramas** (sugerida):
- `feature/<descripcion>` — nueva funcionalidad
- `fix/<descripcion>` — corrección de bug
- `chore/<descripcion>` — tareas de mantenimiento
- `docs/<descripcion>` — documentación

### 3.2 Abrir el PR en GitHub

Al subir la rama, GitHub muestra un banner amarillo proponiendo crear el PR.

> 📸 **[IMAGEN 3.2.a]**
> Screenshot del repo justo después de hacer push, mostrando el banner amarillo **"Compare & pull request"** resaltado.

1. Clic en **Compare & pull request** (o pestaña **Pull requests → New pull request**).
2. Verifica las ramas: `base: main` ← `compare: tu-rama`.
3. Rellena título y descripción.

> 📸 **[IMAGEN 3.2.b]**
> Screenshot del formulario de creación de PR con las ramas resaltadas arriba (base ← compare) y el título/descripción rellenos.

### 3.3 Descripción del PR (plantilla sugerida)

```markdown
## Qué hace este PR
Resuelve el problema de login cuando el email viene en mayúsculas.

## Issue relacionado
Closes #123

## Cómo probarlo
1. Hacer checkout de esta rama
2. Ir a /login
3. Probar con "USUARIO@MAIL.COM"

## Checklist
- [x] Tests añadidos
- [x] Documentación actualizada
- [ ] Probado en staging
```

> ⚠️ **Importante**: usar `Closes #123` enlaza el issue al PR. Cuando el PR se mergee, el issue se cierra automáticamente.

> 📸 **[IMAGEN 3.3]**
> Screenshot de un PR ya creado mostrando la descripción con un checklist marcado y la referencia `Closes #123` con tooltip mostrando el issue.

### 3.4 Asignar revisores

En la barra lateral derecha:
- **Reviewers**: personas que deben aprobar el código.
- **Assignees**: quién es el dueño/responsable del PR.
- **Labels / Projects / Milestone**: igual que en issues.

> 📸 **[IMAGEN 3.4]**
> Screenshot de la barra lateral del PR con Reviewers y Assignees asignados, mostrando los avatares.

### 3.5 Code Review (revisar el código de otro)

Si te asignan como reviewer:

1. Abre el PR → pestaña **Files changed**.
2. Lee diff por diff.
3. Para comentar una línea: pasa el ratón sobre el número de línea y haz clic en el **+** azul.
4. Puedes escribir un comentario simple o usar **Suggested change** para proponer código exacto.

> 📸 **[IMAGEN 3.5.a]**
> Screenshot de la pestaña **Files changed** con el icono **+** azul a la izquierda de una línea, resaltado.

> 📸 **[IMAGEN 3.5.b]**
> Screenshot de un comentario con **Suggested change** (bloque que permite proponer código que el autor puede aplicar con un clic).

Al terminar, clic en **Review changes** (arriba a la derecha) y elige:

- **Comment**: feedback general sin aprobar ni bloquear.
- **Approve**: el código está OK, puede mergearse.
- **Request changes**: hay cosas que cambiar antes de mergear.

> 📸 **[IMAGEN 3.5.c]**
> Screenshot del modal **Review changes** con las tres opciones visibles.

### 3.6 Responder a un review (como autor del PR)

- Aplica los cambios solicitados en tu rama local y haz `git push` → el PR se actualiza solo.
- Responde a cada comentario o márcalo como **Resolve conversation** cuando esté solucionado.
- Si discrepas con una sugerencia, explícalo en el hilo — el review es conversación, no orden.

> 📸 **[IMAGEN 3.6]**
> Screenshot de un hilo de conversación dentro del PR con el botón **Resolve conversation** visible.

### 3.7 Mergear el PR

Cuando tenga las aprobaciones necesarias y los checks (CI) estén verdes:

> 📸 **[IMAGEN 3.7.a]**
> Screenshot de la sección final del PR mostrando: ✅ checks pasando, ✅ aprobación de reviewer, botón verde **Merge pull request**.

GitHub ofrece **tres estrategias de merge**:

| Estrategia | Cuándo usarla |
|------------|---------------|
| **Create a merge commit** | Conserva todo el historial de commits + uno extra de merge. Útil para PRs grandes con historial significativo. |
| **Squash and merge** | Junta todos los commits del PR en uno solo. **Recomendado por defecto**: historial limpio. |
| **Rebase and merge** | Aplica los commits uno a uno sobre `main` sin commit de merge. Avanzado. |

> 📸 **[IMAGEN 3.7.b]**
> Screenshot del desplegable del botón **Merge** mostrando las tres opciones.

Tras mergear, **borra la rama** (botón **Delete branch** aparece). En local:

```bash
git checkout main
git pull origin main
git branch -d feature/login-mayusculas
```

### 3.8 Conflictos de merge

Si tu rama tiene conflictos con `main`, GitHub lo avisa. Resolución:

```bash
git checkout feature/login-mayusculas
git pull origin main           # trae los cambios nuevos de main
# resolver conflictos en los archivos marcados con <<<<<<< =======
git add .
git commit -m "merge: resuelve conflictos con main"
git push
```

> 📸 **[IMAGEN 3.8]**
> Screenshot de la sección del PR mostrando el aviso **"This branch has conflicts that must be resolved"** en rojo.

---

## 4. GitHub Projects

GitHub Projects (la versión nueva, **Projects v2**) es un gestor tipo Trello/Jira integrado en GitHub. Permite organizar issues y PRs en tableros, tablas o roadmaps.

### 4.1 Acceder al Project

Desde la organización → pestaña **Projects**, o desde un repo → **Projects**.

> 📸 **[IMAGEN 4.1]**
> Screenshot de la pestaña **Projects** a nivel organización mostrando la lista de proyectos existentes.

#### Crear uno nuevo

1. Clic en **New project**.
2. Elegir una **plantilla** (no empezar de cero salvo que sea necesario):
   - **Kanban** — ideal para empezar, ya trae columnas *Todo / In Progress / Done*.
   - **Team planning** — para equipos pequeños.
   - **Roadmap** — vista temporal.
3. Nombrar el project y crear.

> 📸 **[IMAGEN 4.1.b]**
> Screenshot del selector de plantillas al crear un Project, con la opción **Kanban** resaltada.

> 💡 **Cómo nombrar los Projects**:
> - **Proyecto pequeño** → un solo Project con el nombre general (ej: `Mi Aplicación`).
> - **Proyecto grande con sprints** → un Project por sprint (`Sprint 1`, `Sprint 2`, …) o usar el campo *Iteration* dentro de un único Project.

### 4.2 Vistas del Project

Un project tiene **varias vistas** sobre los mismos datos:

#### Board (tablero kanban)
Columnas por estado: `Todo`, `In Progress`, `In Review`, `Done`. Arrastras tarjetas entre columnas.

> 📸 **[IMAGEN 4.2.a]**
> Screenshot de la vista **Board** con tarjetas distribuidas en las columnas. Resaltar una tarjeta arrastrándose entre dos columnas si es posible.

#### Table (tabla)
Como una hoja de cálculo: cada fila es un issue/PR, columnas configurables.

> 📸 **[IMAGEN 4.2.b]**
> Screenshot de la vista **Table** mostrando columnas como Title, Assignees, Status, Priority, Iteration.

#### Roadmap (línea de tiempo)
Para planificación temporal por fechas o iteraciones.

> 📸 **[IMAGEN 4.2.c]**
> Screenshot de la vista **Roadmap** con barras de tareas distribuidas en un timeline mensual.

### 4.3 Añadir un issue al Project

**Opción A** — desde el Project:
- Clic en **+ Add item** (final de una columna o fila) → escribe `#` y busca el issue.

**Opción B** — desde el issue:
- Barra lateral derecha → **Projects** → selecciona el project.

> 📸 **[IMAGEN 4.3]**
> Screenshot mostrando ambas opciones lado a lado, o solo la opción A con el buscador `#` activo mostrando issues sugeridos.

### 4.4 Custom fields (campos personalizados)

Más allá del título y el status, podemos añadir campos como:
- **Priority** (single select: Low / Medium / High)
- **Estimate** (number, en horas o puntos)
- **Iteration** (sprint actual)
- **Area** (frontend / backend / infra)

Para añadir uno: en cualquier vista → **+** al final de las columnas → **New field**.

> 📸 **[IMAGEN 4.4]**
> Screenshot del menú **New field** mostrando los tipos disponibles (Text, Number, Date, Single select, Iteration).

### 4.5 Workflows automáticos

El project puede actualizarse solo. En **Settings del Project → Workflows**:

- **Item added to project** → status = `Todo`.
- **Pull request opened** → status = `In Review`.
- **Pull request merged** → status = `Done`.
- **Issue closed** → status = `Done`.

> 📸 **[IMAGEN 4.5]**
> Screenshot de la sección **Workflows** del project con los toggles activados (ON en verde).

### 4.6 Filtros y agrupaciones

En cualquier vista, arriba hay una barra de búsqueda donde puedes filtrar:

```
is:open assignee:@me label:bug
```

Y **agrupar** por cualquier campo: status, assignee, priority, iteration…

> 📸 **[IMAGEN 4.6]**
> Screenshot de la barra de filtros activa con un filtro aplicado y resultados filtrados visibles.

---

## 5. Flujo completo end-to-end

Así trabajamos una tarea desde cero hasta producción:

```
1. Se crea un Issue describiendo el trabajo
   └─ se le asignan labels, responsable y se añade al Project
        └─ el Project lo coloca en "Todo" automáticamente

2. El responsable mueve la tarjeta a "In Progress"
   └─ crea una rama: feature/xyz
        └─ trabaja en local y hace commits

3. Push de la rama y apertura de un Pull Request
   └─ descripción del PR incluye "Closes #N"
        └─ el Project mueve la tarjeta a "In Review" automáticamente
             └─ se asignan reviewers

4. Code review → iteraciones → aprobación

5. Merge del PR
   └─ el Issue se cierra automáticamente
        └─ el Project mueve la tarjeta a "Done"
             └─ la rama se borra
```

> 📸 **[IMAGEN 5]**
> Diagrama visual del flujo (puedes crearlo en Excalidraw, Miro o Figma) mostrando estas 5 etapas con iconos.

---

## 6. GitHub Actions (resumen)

**GitHub Actions** automatiza tareas cuando ocurren eventos en el repo: cada push, cada PR, cada release, etc. Es lo que produce los **"checks verdes"** que ves al final de un PR.

Casos típicos en un equipo:

- ✅ Correr **tests automáticos** en cada PR.
- 🎨 Verificar **lint / formato de código**.
- 🚀 **Desplegar** a staging cuando se mergea a `main`.
- 🔒 Escaneo de **vulnerabilidades** en dependencias.

### 6.1 Estructura básica

Los workflows viven en `.github/workflows/<nombre>.yml`. Ejemplo mínimo que corre tests en cada PR:

```yaml
name: CI

on:
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci
      - run: npm test
```

### 6.2 Ver el estado de las Actions

- Pestaña **Actions** del repo → lista todas las ejecuciones.
- Dentro de un PR → sección **Checks** al final.

> 📸 **[IMAGEN 6.2.a]**
> Screenshot de la pestaña **Actions** mostrando un workflow corriendo (amarillo) y otros completados (verde/rojo).

> 📸 **[IMAGEN 6.2.b]**
> Screenshot de la sección **Checks** dentro de un PR mostrando los workflows ejecutándose o completados.

> ⚠️ **Regla del equipo**: si un check está en rojo, no se mergea hasta investigarlo. Aunque el revisor haya aprobado.

---

## Anexo: Buenas prácticas rápidas

- **Un PR = un propósito**. No mezcles refactor + feature + bugfix.
- **Commits pequeños y descriptivos**. Usa [Conventional Commits](https://www.conventionalcommits.org/) si el equipo lo adopta (`feat:`, `fix:`, `docs:`, `chore:`…).
- **Antes de pedir review**: lee tu propio diff y verifica que los tests pasen localmente.
- **Antes de aprobar**: descárgate la rama y pruébala si el cambio es crítico.
- **No mergees PRs ajenos sin permiso del autor**, salvo acuerdo previo.
- **Cierra issues con `Closes #N`** desde el PR — evita olvidos.

---

## Recursos

- [GitHub Docs — Issues](https://docs.github.com/en/issues)
- [GitHub Docs — Pull Requests](https://docs.github.com/en/pull-requests)
- [GitHub Docs — Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [Conventional Commits](https://www.conventionalcommits.org/)

---

*Última actualización: mayo 2026. Si encuentras algo desactualizado, abre un issue 😉*
