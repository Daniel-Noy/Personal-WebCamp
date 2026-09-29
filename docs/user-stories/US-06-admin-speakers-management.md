# US-06: Gestión de Ponentes (Backoffice)

- **Módulo:** Administración (Backoffice)
- **Prioridad:** Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-06-admin-speakers.md`

---

## Descripción

**Como** administrador del sistema  
**Quiero** dar de alta, listar, actualizar y eliminar información de los conferencistas  
**Para** mantener actualizada la nómina de invitados y sus perfiles técnicos en el portal.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Creación de ponente con imagen y redes

- **Dado** que he iniciado sesión con rol de Administrador
- **Cuando** completo el formulario de creación de ponente con nombre, biografía, foto válida, áreas de especialidad y enlaces de redes (GitHub, X/Twitter, etc.)
- **Entonces** el ponente se guarda exitosamente
- **Y** su imagen se almacena de forma optimizada en el storage del servidor
- **Y** el ponente se refleja en el listado del panel y en el portal público.

### Escenario: Validación de campos requeridos

- **Dado** que estoy en el formulario de creación de ponente
- **Cuando** intento guardar omitiendo el nombre o la fotografía
- **Entonces** el sistema detiene el proceso y muestra los errores de validación correspondientes en el formulario.

### Escenario: Modificación de ponente existente

- **Dado** que selecciono un ponente existente para editar
- **Cuando** actualizo sus etiquetas técnicas o biografía
- **Entonces** los cambios se persisten inmediatamente en la base de datos.

### Escenario: Eliminación controlada de ponente

- **Dado** que un ponente no tiene eventos asociados
- **Cuando** confirmo su eliminación
- **Entonces** el registro y sus recursos multimedia asociados se eliminan de forma segura.
