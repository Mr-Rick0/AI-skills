---
name: eco-code
description: Enforce repository reuse audits before creating new code. Use when Codex is asked to add, modify, or implement any function, class, type, hook, component, service, utility, helper, validation, parser, mapper, formatter, or business logic in an existing codebase; especially when the request could duplicate existing project behavior.
---

# EcoCode

## Core Rule

Before writing any new function, class, type, hook, component, service, utility, helper, or business logic, audit the current project for existing total or partial solutions. Prefer reuse, extension, parametrization, or small refactors over duplication.

Do not create new logic when existing code covers roughly 80% or more of the requested behavior. Extend the existing implementation instead, unless there is a clear technical incompatibility.

## Mandatory Workflow

### 1. Analyze Intent And Semantics

Identify the exact business objective or technical logic requested by the user.

Derive search terms before searching:

- Direct names from the request.
- Domain synonyms.
- English/Spanish variants when relevant.
- Related data names, types, concepts, and common abbreviations.
- Existing-framework terms, such as hooks, services, stores, adapters, mappers, selectors, validators, serializers, formatters, or utilities.

Example: for "calcular edad", also search for `birthdate`, `birthday`, `age`, `date-utils`, `yearsDiff`, `dateOfBirth`, `fechaNacimiento`, and `edad`.

### 2. Search The Repository Exhaustively

Use fast code search first, preferably `rg` and `rg --files`.

Search broadly across:

- `utils/`, `helpers/`, `lib/`, `shared/`, `common/`, and framework equivalents.
- Services, repositories, clients, adapters, mappers, validators, serializers, and formatters.
- Base classes, shared hooks, generic components, providers, stores, selectors, and composables.
- Types, interfaces, schemas, DTOs, domain models, constants, enums, and test fixtures.
- Tests and stories, because they often reveal intended reusable behavior.

Search by symbol names, file names, comments, tests, route names, UI copy, and domain vocabulary. If the repository has indexing or language-server tools, use them when available.

### 3. Evaluate Match Quality

Compare findings with the user's request:

- **Total Match (100%)**: Existing code already satisfies the behavior.
- **Partial Match (50% - 90%)**: Existing code handles similar logic and can be extended, parametrized, composed, or lightly refactored.
- **No Match (0%)**: The behavior is genuinely new and unique to the business/domain.

Assess API shape, side effects, ownership boundaries, tests, naming, dependencies, and whether extending the current code would make the design clearer or more brittle.

### 4. Report Before New Code

Before generating or editing code that introduces new logic, send this exact Spanish audit format to the user:

```markdown
---
### 🔍 REPORTE DE REUTILIZACIÓN DE CÓDIGO

* **Estado de Hallazgo:** [Coincidencia Total / Coincidencia Parcial / No Encontrado]

* **Código Existente Detectado:**
  - `Nombre de la Función/Clase/Archivo`: [Ruta del archivo]
  - `Lógica que maneja actualmente`: [Breve descripción de 1 frase]

* **Estrategia Recomendada:**
  - [Opción A: Usar directamente lo que ya existe (indicar cómo)]
  - [Opción B: Refactorizar/Extender el código existente (indicar el cambio menor)]
  - [Opción C: Crear desde cero porque el caso de uso es único (justificar técnicamente)]
---
```

Use only the option or options that genuinely apply. If multiple existing candidates are relevant, list them all under "Código Existente Detectado".

## Strict Behavior

- Never duplicate logic when a reusable implementation exists.
- If there is a partial match, propose the smallest extension or refactor that preserves existing callers.
- If creating code from scratch, explicitly justify why similar files or functions found during the audit do not fit.
- Keep implementation changes scoped to the audited strategy.
- If the user asks to skip the audit, still perform a compact audit unless they explicitly accept the duplication risk and the repository context is unavailable.
- If repository access is unavailable, state that the audit cannot be completed and avoid claiming "No Encontrado".
