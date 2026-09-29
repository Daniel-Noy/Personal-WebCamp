# Spec-Driven Development (SDD) Workflow

Guía metodológica para el desarrollo de funcionalidades: desde la planificación y levantamiento de requerimientos hasta la implementación y pruebas con Laravel, Inertia.js y React.

---

## 1. Planificación y Alcance

1. **Definir el objetivo del MVP:** Identificar el problema central y la propuesta de valor.
2. **Modularización:** Descomponer el sistema en módulos de dominio (ej. Auth, Eventos, Pagos, Notificaciones).
3. **Requerimientos no funcionales:** Definir restricciones de seguridad, rendimiento y arquitectura.

---

## 2. Historias de Usuario (HU)

Redactar historias independientes y testeables siguiendo el formato estándar:

```markdown
### US-[ID]: [Título corto y descriptivo]

**Como** [tipo de usuario]
**Quiero** [acción / capacidad]
**Para** [beneficio / valor de negocio]

#### Criterios de Aceptación (formato Gherkin):

- Escenario: [Nombre del escenario exitoso]
  Dado [estado inicial / precondición]
  Cuando [acción del usuario o evento]
  Entonces [resultado esperado]
  Y [efecto secundario / persistencia / notificación]

- Escenario: [Nombre de escenario de error o caso borde]
  Dado [condición específica]
  Cuando [acción ejecutada]
  Entonces [error o comportamiento defensivo]
```

---

## 3. Especificación Técnica (Spec)

Antes de escribir código de producción, cada Historia de Usuario se traduce en una especificación técnica (almacenada en `docs/specs/[feature-name].md`).

### Estructura de un Spec

1. **Data Model / Schema:**
    - Tablas, campos, tipos, índices y claves foráneas.
2. **Request / Response Contracts:**
    - Endpoints HTTP (rutas con nombre de Laravel).
    - Tipos de TypeScript para Inertia props y payloads.
    - Reglas de validación (`FormRequest`).
3. **Políticas y Autorización:**
    - Permisos y roles requeridos (`Gate` / `Policy`).
4. **Test Specs (Pest):**
    - Lista explícita de tests unitarios y de integración a implementar.

---

## 4. Ciclo de Ejecución (Paso a Paso)

```text
[HU + Criterios] ──> [Spec Técnica] ──> [Tests en Rojo] ──> [Implementación] ──> [Refactor & Pint]
```

1. **Spec:** Crear el archivo de especificación en `docs/specs/`.
2. **Red (Tests):** Escribir tests en Pest (`tests/Feature/...`) reflejando los criterios de aceptación. Los tests deben fallar inicialmente.
3. **Green (Backend):**
    - Crear migración y modelo: `php artisan make:model [Name] -m`
    - Crear FormRequest: `php artisan make:request [Name]Request`
    - Crear controlador y lógica: `php artisan make:controller [Name]Controller`
    - Ejecutar suite de pruebas: `vendor/bin/pest --filter=[FeatureTest]`
4. **UI (Frontend):**
    - Conectar rutas mediante Wayfinder (`@/actions/...` o `@/routes/...`).
    - Crear componentes en `resources/js/pages/` usando Inertia y React.
    - Validar estados de formulario (`processing`, `errors`).
5. **Code Style & Calidad:**
    - Formatear PHP: `vendor/bin/pint --dirty --format agent`
    - Comprobar tipos TypeScript: `npm run types:check`
