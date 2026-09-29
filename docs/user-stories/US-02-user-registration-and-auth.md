# US-02: Registro y Autenticación de Asistentes

- **Módulo:** Autenticación y Cuentas
- **Prioridad:** Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-02-auth.md`

---

## Descripción

**Como** participante potencial  
**Quiero** registrar una cuenta con mi nombre, correo y contraseña, e iniciar sesión de forma segura  
**Para** gestionar mis boletos, regalos y reservas dentro de la plataforma.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Registro exitoso de usuario
- **Dado** que soy un visitante no autenticado
- **Cuando** envío el formulario de registro con nombre, apellido, correo no registrado y contraseña válida confirmada
- **Entonces** se crea mi usuario en la base de datos con contraseña hasheada
- **Y** inicio sesión automáticamente o soy redirigido al flujo de bienvenida/verificación según configuración.

### Escenario: Error al registrar correo duplicado
- **Dado** que ya existe un usuario registrado con el correo `test@example.com`
- **Cuando** intento registrarme con dicho correo
- **Entonces** el sistema rechaza la solicitud con un mensaje de validación indicando que el correo ya está en uso
- **Y** no se crea ningún registro duplicado.

### Escenario: Inicio de sesión válido
- **Dado** que tengo una cuenta activa
- **Cuando** ingreso mis credenciales válidas en `/login`
- **Entonces** el sistema inicia mi sesión y me redirige a mi panel de usuario (`/dashboard`).

### Escenario: Cierre de sesión
- **Dado** que tengo una sesión activa
- **Cuando** hago clic en "Cerrar Sesión"
- **Entonces** la sesión se invalida y soy redirigido a la página principal.
