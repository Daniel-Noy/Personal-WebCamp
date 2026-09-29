# US-01: Visualización de Landing Page, Agenda y Ponentes

- **Módulo:** Portal Público
- **Prioridad:** Alta (MVP Core)
- **Spec Técnica Relacionada:** `docs/specs/SPEC-01-public-portal.md`

---

## Descripción

**Como** visitante interesado en DevWebCamp  
**Quiero** consultar la landing page con la información del evento, catálogo de conferencistas, cronograma por días y comparativa de boletos  
**Para** evaluar la oferta del evento y decidir registrarme o comprar un pase.

---

## Criterios de Aceptación (Gherkin)

### Escenario: Navegación de la landing page pública
- **Dado** que soy un visitante anónimo
- **Cuando** accedo a la ruta raíz `/`
- **Entonces** visualizo la fecha del evento, la propuesta de valor y los accesos rápidos a ponentes, agenda y pases.

### Escenario: Exploración de conferencistas
- **Dado** que existen ponentes registrados en el sistema
- **Cuando** visualizo la sección de ponentes
- **Entonces** veo el listado con nombre, fotografía, biografía breve, tags de tecnologías y enlaces a redes sociales.

### Escenario: Consulta de la agenda segmentada
- **Dado** que existen eventos programados para los días Viernes y Sábado
- **Cuando** selecciono la pestaña de un día específico
- **Entonces** observo los eventos agrupados por bloques horarios y categorías (Conferencias / Workshops) con el nombre del ponente asignado.

### Escenario: Comparativa de pases
- **Dado** que visualizo la sección de boletos
- **Cuando** comparo los tipos de acceso
- **Entonces** veo con claridad las diferencias entre Pase Presencial, Pase Virtual y Pase Gratuito junto con sus respectivos llamados a la acción (CTA).
