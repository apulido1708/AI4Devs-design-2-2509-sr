# Product Backlog - LTI ATS

## Información General

**Producto**: LTI (Leading Talent Intelligence) - Sistema ATS del Futuro  
**Versión del Backlog**: 1.0  
**Fecha de Creación**: 2024  
**Estado**: Backlog Inicial - Pendiente de Refinamiento y Priorización

---

## Épicas

1. [Autenticación y Gestión de Usuarios](#épica-1-autenticación-y-gestión-de-usuarios)
2. [Gestión de Vacantes](#épica-2-gestión-de-vacantes)
3. [Gestión de Candidatos](#épica-3-gestión-de-candidatos)
4. [Proceso de Selección y Pipeline](#épica-4-proceso-de-selección-y-pipeline)
5. [Entrevistas](#épica-5-entrevistas)
6. [Colaboración y Comunicación](#épica-6-colaboración-y-comunicación)
7. [Automatización e IA](#épica-7-automatización-e-ia)
8. [Ofertas y Contratos](#épica-8-ofertas-y-contratos)
9. [Analytics y Reportes](#épica-9-analytics-y-reportes)
10. [Integraciones Externas](#épica-10-integraciones-externas)

---

## Épica 1: Autenticación y Gestión de Usuarios

### US-001: Inicio de Sesión
**Como** usuario del sistema  
**Quiero** iniciar sesión con mi email y contraseña  
**Para** acceder a la plataforma LTI de forma segura

**Escenarios:**

```gherkin
Escenario: Inicio de sesión exitoso
  Dado que soy un usuario registrado con email "reclutador@empresa.com"
  Y tengo una contraseña válida
  Cuando ingreso mis credenciales en el formulario de login
  Entonces debo ser autenticado correctamente
  Y debo ser redirigido al dashboard principal
  Y debo ver mi nombre y rol en la interfaz

Escenario: Inicio de sesión con credenciales inválidas
  Dado que soy un usuario registrado
  Cuando ingreso credenciales incorrectas
  Entonces debo ver un mensaje de error "Email o contraseña incorrectos"
  Y no debo ser autenticado
  Y debo permanecer en la página de login
```

### US-002: Registro de Nueva Empresa
**Como** administrador de una nueva empresa  
**Quiero** registrar mi empresa en el sistema  
**Para** comenzar a usar LTI con mi organización

**Escenarios:**

```gherkin
Escenario: Registro exitoso de empresa
  Dado que no tengo una cuenta en LTI
  Cuando completo el formulario de registro con:
    | Campo | Valor |
    | Nombre empresa | TechCorp S.L. |
    | CIF | B12345678 |
    | Email contacto | admin@techcorp.com |
    | Nombre usuario | Juan Pérez |
    | Email usuario | juan@techcorp.com |
    | Contraseña | Password123! |
  Entonces la empresa debe ser creada
  Y el usuario administrador debe ser creado
  Y debo recibir un email de confirmación
  Y debo poder iniciar sesión con mis credenciales
```

### US-003: Gestión de Usuarios y Roles
**Como** administrador de empresa  
**Quiero** crear y gestionar usuarios con diferentes roles  
**Para** asignar permisos apropiados a cada miembro del equipo

**Escenarios:**

```gherkin
Escenario: Crear nuevo usuario con rol
  Dado que soy un administrador de empresa
  Cuando creo un nuevo usuario con:
    | Nombre | María García |
    | Email | maria@empresa.com |
    | Rol | RECLUTADOR |
    | Departamento | Recursos Humanos |
  Entonces el usuario debe ser creado
  Y debe recibir un email con instrucciones para activar su cuenta
  Y debe tener los permisos correspondientes a su rol

Escenario: Asignar rol a usuario existente
  Dado que existe un usuario "pedro@empresa.com"
  Cuando cambio su rol de "ENTREVISTADOR" a "MANAGER"
  Entonces sus permisos deben actualizarse
  Y debe poder acceder a las funcionalidades de Manager
```

---

## Épica 2: Gestión de Vacantes

### US-004: Crear Nueva Vacante
**Como** reclutador  
**Quiero** crear una nueva vacante de trabajo  
**Para** publicar oportunidades de empleo en la plataforma

**Escenarios:**

```gherkin
Escenario: Crear vacante completa
  Dado que soy un reclutador autenticado
  Cuando creo una nueva vacante con:
    | Campo | Valor |
    | Título | Desarrollador Full Stack |
    | Descripción | Buscamos desarrollador con experiencia en React y Node.js |
    | Departamento | Tecnología |
    | Salario mínimo | 45000 |
    | Salario máximo | 60000 |
    | Tipo contrato | INDEFINIDO |
    | Modalidad | REMOTO |
    | Ubicación | España |
  Entonces la vacante debe ser guardada en estado "BORRADOR"
  Y debo poder verla en mi lista de vacantes
  Y debo poder editarla antes de publicarla

Escenario: Crear vacante con requisitos
  Dado que estoy creando una nueva vacante
  Cuando agrego requisitos:
    | Requisito | Tipo |
    | 3 años experiencia React | Experiencia |
    | Conocimientos Node.js | Skill |
    | Inglés nivel B2 | Idioma |
  Entonces los requisitos deben ser guardados
  Y el sistema de IA debe poder usarlos para matching
```

### US-005: Generar Descripción Optimizada con IA
**Como** reclutador  
**Quiero** que el sistema genere automáticamente una descripción optimizada de la vacante  
**Para** ahorrar tiempo y mejorar la calidad de las publicaciones

**Escenarios:**

```gherkin
Escenario: Generar descripción optimizada
  Dado que estoy creando una vacante con título "Desarrollador Full Stack"
  Y he ingresado requisitos básicos
  Cuando solicito generar descripción optimizada con IA
  Entonces el sistema debe generar una descripción profesional
  Y la descripción debe incluir los requisitos principales
  Y debo poder editarla antes de guardar
  Y debo poder aceptarla o rechazarla
```

### US-006: Publicar Vacante en Múltiples Canales
**Como** reclutador  
**Quiero** publicar una vacante en múltiples canales simultáneamente  
**Para** maximizar la visibilidad de la oferta de trabajo

**Escenarios:**

```gherkin
Escenario: Publicar en múltiples canales
  Dado que tengo una vacante en estado "BORRADOR"
  Y he configurado los canales disponibles (LinkedIn, Indeed, página web)
  Cuando selecciono los canales "LinkedIn" e "Indeed"
  Y publico la vacante
  Entonces la vacante debe cambiar a estado "PUBLICADA"
  Y debe ser publicada en LinkedIn
  Y debe ser publicada en Indeed
  Y debe aparecer en la página web corporativa
  Y debo recibir confirmación de cada publicación

Escenario: Publicación fallida en un canal
  Dado que estoy publicando en múltiples canales
  Cuando LinkedIn publica exitosamente
  Pero Indeed falla por error de conexión
  Entonces la vacante debe publicarse en LinkedIn
  Y debo recibir notificación del error en Indeed
  Y debo poder reintentar la publicación en Indeed
```

### US-007: Gestionar Estados de Vacante
**Como** reclutador  
**Quiero** cambiar el estado de una vacante (pausar, cerrar, reactivar)  
**Para** controlar el ciclo de vida de las ofertas de trabajo

**Escenarios:**

```gherkin
Escenario: Pausar vacante publicada
  Dado que tengo una vacante en estado "PUBLICADA"
  Cuando cambio el estado a "PAUSADA"
  Entonces la vacante debe ser removida de los canales externos
  Y los candidatos no deben poder aplicar
  Y debo poder reactivarla más tarde

Escenario: Cerrar vacante
  Dado que tengo una vacante activa
  Cuando cambio el estado a "CERRADA"
  Entonces la vacante debe ser removida de todos los canales
  Y el sistema debe notificar a los candidatos en proceso
  Y debo poder ver estadísticas de la vacante cerrada
```

### US-008: Ver Métricas de Vacante
**Como** reclutador  
**Quiero** ver métricas de rendimiento de una vacante  
**Para** evaluar la efectividad de la publicación

**Escenarios:**

```gherkin
Escenario: Ver métricas de vacante
  Dado que tengo una vacante publicada
  Cuando accedo a la vista de métricas
  Entonces debo ver:
    | Métrica | Valor |
    | Total aplicaciones | 45 |
    | Aplicaciones por canal | LinkedIn: 30, Indeed: 15 |
    | Tiempo promedio de aplicación | 2 días |
    | Score promedio de candidatos | 72 |
  Y debo poder exportar estas métricas
```

---

## Épica 3: Gestión de Candidatos

### US-009: Aplicación de Candidato a Vacante
**Como** candidato  
**Quiero** aplicar a una vacante subiendo mi CV  
**Para** ser considerado para el puesto

**Escenarios:**

```gherkin
Escenario: Aplicar con CV exitosamente
  Dado que soy un candidato visitando una vacante publicada
  Cuando completo el formulario de aplicación con:
    | Campo | Valor |
    | Nombre | Carlos López |
    | Email | carlos@email.com |
    | Teléfono | +34 600 123 456 |
    | CV | carlos_cv.pdf |
  Entonces mi aplicación debe ser registrada
  Y el CV debe ser subido al sistema
  Y debo recibir un email de confirmación
  Y debo poder ver el estado de mi aplicación en el portal

Escenario: Aplicación con CV no parseable
  Dado que estoy aplicando a una vacante
  Cuando subo un CV en formato imagen (JPG)
  Entonces el sistema debe intentar parsear el CV
  Y si falla, debo recibir notificación
  Y el sistema debe solicitar que complete un formulario adicional
```

### US-010: Parsing Inteligente de CV
**Como** sistema  
**Quiero** parsear automáticamente CVs en múltiples formatos  
**Para** extraer información estructurada del candidato

**Escenarios:**

```gherkin
Escenario: Parsear CV en PDF
  Dado que un candidato ha subido un CV en formato PDF
  Cuando el sistema procesa el CV
  Entonces debe extraer:
    | Información | Ejemplo |
    | Nombre completo | Carlos López |
    | Email | carlos@email.com |
    | Teléfono | +34 600 123 456 |
    | Experiencia | 5 años como desarrollador |
    | Skills | React, Node.js, Python |
    | Educación | Grado en Ingeniería Informática |
  Y debe almacenar la información estructurada
  Y debe calcular años de experiencia

Escenario: Parsear CV en Word
  Dado que un candidato ha subido un CV en formato DOCX
  Cuando el sistema procesa el CV
  Entonces debe extraer la información de forma similar al PDF
  Y debe manejar diferentes estructuras de CV
```

### US-011: Búsqueda Avanzada de Candidatos
**Como** reclutador  
**Quiero** buscar candidatos usando múltiples filtros  
**Para** encontrar perfiles específicos rápidamente

**Escenarios:**

```gherkin
Escenario: Búsqueda con filtros múltiples
  Dado que tengo candidatos en la base de datos
  Cuando busco candidatos con filtros:
    | Filtro | Valor |
    | Skills | React, Node.js |
    | Experiencia mínima | 3 años |
    | Idioma | Inglés B2 |
    | Ubicación | Madrid |
  Entonces debo ver una lista de candidatos que cumplan todos los criterios
  Y los resultados deben estar ordenados por relevancia
  Y debo poder guardar la búsqueda

Escenario: Búsqueda por texto libre
  Dado que tengo candidatos en la base de datos
  Cuando busco "desarrollador Python con experiencia en Django"
  Entonces el sistema debe buscar en todos los campos del perfil
  Y debe usar búsqueda semántica si está disponible
  Y debo ver resultados relevantes ordenados por score
```

### US-012: Ver Perfil Completo de Candidato
**Como** reclutador o manager  
**Quiero** ver el perfil completo de un candidato  
**Para** evaluar su idoneidad para una vacante

**Escenarios:**

```gherkin
Escenario: Ver perfil completo
  Dado que tengo un candidato en el sistema
  Cuando accedo a su perfil
  Entonces debo ver:
    | Sección | Información |
    | Datos personales | Nombre, email, teléfono, LinkedIn |
    | CV parseado | Experiencia, educación, skills |
    | Historial de aplicaciones | Vacantes a las que ha aplicado |
    | Evaluaciones previas | Scores y comentarios de entrevistas anteriores |
    | Notas del equipo | Comentarios de reclutadores y managers |
  Y debo poder descargar el CV original
```

---

## Épica 4: Proceso de Selección y Pipeline

### US-013: Configurar Pipeline Personalizado
**Como** reclutador  
**Quiero** configurar un pipeline personalizado para una vacante  
**Para** adaptar el proceso de selección a las necesidades específicas

**Escenarios:**

```gherkin
Escenario: Crear pipeline personalizado
  Dado que estoy creando una nueva vacante
  Cuando configuro el pipeline con etapas:
    | Etapa | Orden |
    | Nueva aplicación | 1 |
    | Revisión inicial | 2 |
    | Entrevista telefónica | 3 |
    | Entrevista técnica | 4 |
    | Entrevista cultural | 5 |
    | Oferta | 6 |
    | Contratado | 7 |
  Entonces el pipeline debe ser guardado
  Y los candidatos deben moverse por estas etapas
  Y debo poder reordenar las etapas

Escenario: Usar pipeline por defecto
  Dado que estoy creando una vacante
  Cuando no configuro un pipeline personalizado
  Entonces el sistema debe usar el pipeline por defecto
  Y debo poder modificarlo después
```

### US-014: Asignar Candidato a Manager
**Como** reclutador  
**Quiero** asignar un candidato a un manager para revisión  
**Para** iniciar el proceso de evaluación colaborativa

**Escenarios:**

```gherkin
Escenario: Asignar candidato para revisión
  Dado que tengo un candidato en etapa "EN_REVISION"
  Y tengo managers disponibles en el departamento
  Cuando asigno el candidato al manager "María García"
  Entonces el manager debe recibir una notificación
  Y el candidato debe aparecer en su lista de asignaciones
  Y el estado debe cambiar a "ASIGNADO_A_MANAGER"
  Y debo poder ver el estado de la asignación
```

### US-015: Calcular Score de Matching Automático
**Como** sistema  
**Quiero** calcular automáticamente el score de matching entre candidato y vacante  
**Para** ayudar a los reclutadores a priorizar candidatos

**Escenarios:**

```gherkin
Escenario: Calcular score de matching
  Dado que un candidato ha aplicado a una vacante
  Y el CV ha sido parseado correctamente
  Cuando el sistema calcula el score de matching
  Entonces debe considerar:
    | Factor | Peso |
    | Similitud de skills | 40% |
    | Años de experiencia | 25% |
    | Educación | 15% |
    | Idiomas | 10% |
    | Historial previo | 10% |
  Y debe generar un score entre 0 y 100
  Y el candidato debe aparecer ordenado por score en el pipeline

Escenario: Score bajo - sugerencias
  Dado que un candidato tiene score menor a 60%
  Cuando visualizo el candidato
  Entonces el sistema debe sugerir:
    | Sugerencia |
    | Ampliar criterios de búsqueda |
    | Publicar en canales adicionales |
    | Ajustar requisitos de la vacante |
```

### US-016: Mover Candidato entre Etapas del Pipeline
**Como** reclutador o manager  
**Quiero** mover un candidato entre etapas del pipeline  
**Para** reflejar el progreso en el proceso de selección

**Escenarios:**

```gherkin
Escenario: Avanzar candidato a siguiente etapa
  Dado que tengo un candidato en etapa "EN_REVISION"
  Cuando cambio su estado a "ENTREVISTA"
  Entonces el candidato debe moverse a la nueva etapa
  Y se debe registrar la fecha del cambio
  Y el candidato debe recibir notificación si corresponde
  Y debo poder ver el historial de cambios

Escenario: Rechazar candidato
  Dado que tengo un candidato en cualquier etapa
  Cuando cambio su estado a "RECHAZADO"
  Entonces el candidato debe ser movido fuera del pipeline activo
  Y debo poder agregar una razón de rechazo
  Y el candidato debe recibir notificación de rechazo
```

---

## Épica 5: Entrevistas

### US-017: Programar Entrevista
**Como** reclutador  
**Quiero** programar una entrevista entre candidato y entrevistador  
**Para** coordinar el proceso de evaluación

**Escenarios:**

```gherkin
Escenario: Programar entrevista presencial
  Dado que tengo un candidato asignado para entrevista
  Y tengo un entrevistador disponible
  Cuando programo una entrevista con:
    | Campo | Valor |
    | Tipo | PRESENCIAL |
    | Fecha | 2024-03-15 |
    | Hora | 10:00 |
    | Duración | 60 minutos |
    | Entrevistador | Pedro Martínez |
    | Ubicación | Oficina Central, Sala 3 |
  Entonces la entrevista debe ser creada
  Y el entrevistador debe recibir notificación
  Y el candidato debe recibir invitación con detalles
  Y debe aparecer en los calendarios de ambos

Escenario: Programar entrevista virtual
  Dado que estoy programando una entrevista
  Cuando selecciono tipo "VIDEO"
  Entonces el sistema debe generar un link de video conferencia
  Y debe integrarse con Zoom o Google Meet
  Y el link debe ser enviado a ambos participantes
```

### US-018: Sugerir Entrevistadores Disponibles
**Como** sistema  
**Quiero** sugerir entrevistadores disponibles basado en la vacante  
**Para** facilitar la programación de entrevistas

**Escenarios:**

```gherkin
Escenario: Sugerir entrevistadores
  Dado que estoy programando una entrevista técnica
  Y la vacante es para "Desarrollador Full Stack"
  Cuando solicito sugerencias de entrevistadores
  Entonces el sistema debe sugerir entrevistadores con:
    | Criterio |
    | Skills relacionados con la vacante |
    | Disponibilidad en el horario solicitado |
    | Experiencia previa en entrevistas similares |
    | Pertenecientes al mismo departamento |
  Y debo poder seleccionar de la lista sugerida
```

### US-019: Completar Evaluación de Entrevista
**Como** entrevistador  
**Quiero** completar un formulario de evaluación estructurado después de la entrevista  
**Para** documentar mi evaluación del candidato

**Escenarios:**

```gherkin
Escenario: Evaluar entrevista completa
  Dado que he realizado una entrevista con un candidato
  Cuando completo la evaluación con:
    | Campo | Valor |
    | Score técnico | 8/10 |
    | Score cultural | 7/10 |
    | Score comunicación | 9/10 |
    | Comentarios | Excelente conocimiento técnico, buena comunicación |
    | Recomendación | APROBAR |
  Entonces la evaluación debe ser guardada
  Y el manager debe recibir notificación
  Y la evaluación debe aparecer en el perfil del candidato
  Y debo poder ver todas las evaluaciones del candidato

Escenario: Evaluación con recomendación de segunda opinión
  Dado que he completado una evaluación
  Cuando selecciono recomendación "SEGUNDA_OPINION"
  Entonces el sistema debe sugerir otro entrevistador
  Y debe crear automáticamente una nueva entrevista
  Y el manager debe ser notificado de la necesidad de segunda opinión
```

### US-020: Reprogramar o Cancelar Entrevista
**Como** reclutador o entrevistador  
**Quiero** reprogramar o cancelar una entrevista  
**Para** adaptarme a cambios de agenda

**Escenarios:**

```gherkin
Escenario: Reprogramar entrevista
  Dado que tengo una entrevista programada
  Cuando el candidato solicita cambio de horario
  Entonces debo poder ver horarios alternativos disponibles
  Y debo poder seleccionar un nuevo horario
  Y ambos participantes deben recibir notificación del cambio
  Y los calendarios deben actualizarse automáticamente

Escenario: Cancelar entrevista
  Dado que tengo una entrevista programada
  Cuando cancelo la entrevista
  Entonces ambos participantes deben recibir notificación
  Y la entrevista debe marcarse como "CANCELADA"
  Y debo poder programar una nueva entrevista fácilmente
```

---

## Épica 6: Colaboración y Comunicación

### US-021: Agregar Comentarios en Tiempo Real
**Como** reclutador o manager  
**Quiero** agregar comentarios sobre un candidato en tiempo real  
**Para** colaborar con el equipo en la evaluación

**Escenarios:**

```gherkin
Escenario: Agregar comentario sobre candidato
  Dado que estoy viendo el perfil de un candidato
  Cuando agrego un comentario "Excelente perfil, recomiendo avanzar a entrevista técnica"
  Entonces el comentario debe ser guardado
  Y debe aparecer en tiempo real para otros usuarios viendo el mismo perfil
  Y los miembros del equipo deben recibir notificación
  Y debo poder ver quién comentó y cuándo

Escenario: Responder a comentario
  Dado que hay un comentario existente sobre un candidato
  Cuando respondo al comentario
  Entonces mi respuesta debe aparecer como hilo de conversación
  Y el autor del comentario original debe recibir notificación
  Y debo poder editar mi comentario si es necesario
```

### US-022: Notificaciones Push y Email
**Como** usuario del sistema  
**Quiero** recibir notificaciones sobre eventos importantes  
**Para** estar al día con el proceso de selección

**Escenarios:**

```gherkin
Escenario: Recibir notificación de nueva asignación
  Dado que soy un manager
  Cuando un reclutador me asigna un candidato
  Entonces debo recibir:
    | Tipo notificación | Canal |
    | Push notification | Inmediata |
    | Email | Dentro de 5 minutos |
  Y la notificación debe incluir:
    | Información |
    | Nombre del candidato |
    | Vacante relacionada |
    | Link directo al perfil |
  Y debo poder marcar la notificación como leída

Escenario: Notificación de evaluación completada
  Dado que soy un manager esperando una evaluación
  Cuando un entrevistador completa una evaluación
  Entonces debo recibir notificación inmediata
  Y debo poder acceder directamente a la evaluación
  Y debo ver un resumen del score y recomendación
```

### US-023: Chat Interno entre Miembros del Equipo
**Como** miembro del equipo de reclutamiento  
**Quiero** chatear con otros miembros del equipo  
**Para** comunicarme rápidamente sobre candidatos

**Escenarios:**

```gherkin
Escenario: Iniciar chat con miembro del equipo
  Dado que estoy viendo el perfil de un candidato
  Cuando inicio un chat con otro miembro del equipo
  Entonces debo poder enviar mensajes en tiempo real
  Y los mensajes deben estar vinculados al candidato si corresponde
  Y debo poder ver el historial de conversación
  Y debo recibir notificaciones de nuevos mensajes
```

---

## Épica 7: Automatización e IA

### US-024: Matching Automático Candidato-Vacante
**Como** sistema  
**Quiero** hacer matching automático entre candidatos existentes y nuevas vacantes  
**Para** sugerir candidatos relevantes sin esperar aplicaciones

**Escenarios:**

```gherkin
Escenario: Matching automático al publicar vacante
  Dado que se publica una nueva vacante "Desarrollador React"
  Y existen candidatos en la base de datos
  Cuando el sistema ejecuta matching automático
  Entonces debe escanear todos los candidatos activos
  Y debe calcular score de matching para cada uno
  Y debe mostrar al reclutador los top 20 candidatos con score >70%
  Y los candidatos deben estar ordenados por score descendente
  Y debo poder ver el detalle del matching para cada candidato

Escenario: Sin matches suficientes
  Dado que se ejecuta matching automático
  Cuando hay menos de 5 candidatos con score >70%
  Entonces el sistema debe sugerir:
    | Sugerencia |
    | Ampliar criterios de búsqueda |
    | Considerar candidatos con experiencia transferible |
    | Activar búsqueda activa (headhunting) |
```

### US-025: Generar Mensaje Personalizado con IA
**Como** reclutador  
**Quiero** que el sistema genere un mensaje personalizado para contactar candidatos  
**Para** ahorrar tiempo y mejorar la tasa de respuesta

**Escenarios:**

```gherkin
Escenario: Generar mensaje de contacto
  Dado que he seleccionado un candidato para contactar
  Y tengo información del candidato y la vacante
  Cuando solicito generar mensaje personalizado
  Entonces el sistema debe generar un mensaje que incluya:
    | Elemento |
    | Saludo personalizado con nombre del candidato |
    | Referencia a su experiencia relevante |
    | Descripción breve de la vacante |
    | Invitación a conocer más |
  Y debo poder editar el mensaje antes de enviar
  Y debo poder guardar plantillas personalizadas
```

### US-026: Resumir CV Automáticamente
**Como** reclutador  
**Quiero** que el sistema genere un resumen automático del CV  
**Para** revisar candidatos más rápidamente

**Escenarios:**

```gherkin
Escenario: Generar resumen de CV
  Dado que un candidato ha aplicado con su CV
  Y el CV ha sido parseado
  Cuando accedo al perfil del candidato
  Entonces debo ver un resumen generado por IA que incluya:
    | Sección |
    | Resumen ejecutivo (2-3 líneas) |
    | Experiencia clave (top 3 posiciones) |
    | Skills principales |
    | Logros destacados |
  Y debo poder expandir para ver el CV completo
  Y el resumen debe actualizarse si el CV cambia
```

### US-027: Generar Preguntas de Entrevista Personalizadas
**Como** entrevistador  
**Quiero** que el sistema genere preguntas de entrevista personalizadas  
**Para** evaluar mejor a los candidatos

**Escenarios:**

```gherkin
Escenario: Generar preguntas técnicas
  Dado que estoy preparando una entrevista técnica
  Y tengo el perfil del candidato y los requisitos de la vacante
  Cuando solicito generar preguntas de entrevista
  Entonces el sistema debe generar preguntas que:
    | Característica |
    | Estén basadas en los skills del candidato |
    | Cubran los requisitos de la vacante |
    | Tengan diferentes niveles de dificultad |
    | Incluyan casos prácticos relevantes |
  Y debo poder seleccionar las preguntas que quiero usar
  Y debo poder agregar mis propias preguntas
```

### US-028: Predicción de Éxito del Candidato
**Como** manager  
**Quiero** ver una predicción del éxito del candidato  
**Para** tomar decisiones más informadas

**Escenarios:**

```gherkin
Escenario: Ver predicción de éxito
  Dado que tengo un candidato con evaluaciones completadas
  Cuando visualizo el perfil del candidato
  Entonces debo ver una predicción que incluya:
    | Métrica | Descripción |
    | Probabilidad de aceptar oferta | 85% |
    | Probabilidad de éxito en el rol | 78% |
    | Fit cultural | Alto |
    | Tiempo estimado hasta contratación | 15 días |
  Y la predicción debe basarse en:
    | Factor |
    | Historial de evaluaciones |
    | Comparación con candidatos similares contratados |
    | Análisis de comportamiento en el proceso |
  Y debo poder ver los factores que influyen en la predicción
```

---

## Épica 8: Ofertas y Contratos

### US-029: Generar Oferta de Trabajo
**Como** manager  
**Quiero** generar una oferta de trabajo formal para un candidato aprobado  
**Para** formalizar la propuesta económica

**Escenarios:**

```gherkin
Escenario: Crear oferta completa
  Dado que un candidato ha sido aprobado en todas las etapas
  Cuando creo una oferta con:
    | Campo | Valor |
    | Salario base | 55000 EUR |
    | Bonus | 5000 EUR |
    | Beneficios | Seguro médico, teletrabajo, formación |
    | Fecha inicio | 2024-04-01 |
    | Tipo contrato | INDEFINIDO |
  Entonces la oferta debe ser creada en estado "BORRADOR"
  Y debo poder revisarla antes de enviar
  Y debo poder generar el documento PDF de la oferta

Escenario: Generar oferta con plantilla
  Dado que tengo plantillas de oferta configuradas
  Cuando selecciono una plantilla para generar la oferta
  Entonces el sistema debe pre-llenar campos comunes
  Y debo poder personalizar los campos específicos
  Y debo poder guardar como nueva plantilla
```

### US-030: Aprobar y Enviar Oferta
**Como** manager o administrador  
**Quiero** aprobar y enviar una oferta al candidato  
**Para** iniciar el proceso de negociación

**Escenarios:**

```gherkin
Escenario: Aprobar y enviar oferta
  Dado que tengo una oferta en estado "BORRADOR"
  Cuando apruebo la oferta
  Y la envío al candidato
  Entonces la oferta debe cambiar a estado "ENVIADA"
  Y el candidato debe recibir un email con:
    | Contenido |
    | Mensaje personalizado |
    | Documento PDF de la oferta |
    | Link para aceptar, rechazar o negociar |
  Y el candidato debe poder ver la oferta en su portal
  Y debo recibir notificación cuando el candidato responda

Escenario: Oferta requiere aprobación superior
  Dado que la oferta excede el límite de mi autoridad
  Cuando intento aprobar la oferta
  Entonces debe requerir aprobación de un manager superior
  Y debo poder agregar comentarios para el aprobador
  Y el aprobador debe recibir notificación
```

### US-031: Negociar Oferta
**Como** candidato o manager  
**Quiero** negociar los términos de una oferta  
**Para** llegar a un acuerdo mutuo

**Escenarios:**

```gherkin
Escenario: Candidato negocia oferta
  Dado que he recibido una oferta
  Cuando solicito negociar con:
    | Campo | Valor solicitado |
    | Salario base | 60000 EUR (original: 55000) |
    | Bonus | 8000 EUR (original: 5000) |
  Entonces la oferta debe cambiar a estado "NEGOCIACION"
  Y el manager debe recibir notificación
  Y debo poder ver el historial de versiones
  Y el manager debe poder responder con contrapropuesta

Escenario: Manager acepta negociación
  Dado que un candidato ha solicitado negociar
  Cuando el manager acepta los nuevos términos
  Entonces se debe crear una nueva versión de la oferta
  Y el candidato debe recibir la oferta actualizada
  Y el historial de versiones debe mantenerse
```

### US-032: Generar Contrato Automáticamente
**Como** sistema  
**Quiero** generar un contrato automáticamente cuando se acepta una oferta  
**Para** agilizar el proceso de contratación

**Escenarios:**

```gherkin
Escenario: Generar contrato tras aceptar oferta
  Dado que un candidato ha aceptado una oferta
  Cuando el sistema genera el contrato
  Entonces debe usar la plantilla de contrato configurada
  Y debe incluir todos los términos de la oferta aceptada
  Y debe incluir datos del candidato y la empresa
  Y debe generar un documento PDF listo para firma
  Y el contrato debe estar en estado "PENDIENTE"
  Y ambos partes deben recibir el contrato para revisión

Escenario: Contrato con firma electrónica
  Dado que se ha generado un contrato
  Y la empresa tiene integración con DocuSign
  Cuando envío el contrato para firma
  Entonces debe enviarse a través de DocuSign
  Y ambas partes deben poder firmar electrónicamente
  Y el estado debe actualizarse a "FIRMADO" cuando ambas partes firmen
```

---

## Épica 9: Analytics y Reportes

### US-033: Dashboard Ejecutivo
**Como** administrador o manager  
**Quiero** ver un dashboard con métricas clave del proceso de reclutamiento  
**Para** tener una visión general del rendimiento

**Escenarios:**

```gherkin
Escenario: Ver dashboard ejecutivo
  Dado que soy un administrador
  Cuando accedo al dashboard ejecutivo
  Entonces debo ver métricas en tiempo real:
    | Métrica | Descripción |
    | Vacantes activas | 12 |
    | Candidatos en proceso | 45 |
    | Tiempo medio de contratación | 18 días |
    | Tasa de conversión | 35% |
    | Coste por contratación | 2500 EUR |
    | Fuentes más efectivas | LinkedIn: 40%, Indeed: 30% |
  Y debo poder filtrar por período de tiempo
  Y debo poder exportar los datos

Escenario: Dashboard con predicciones
  Dado que accedo al dashboard
  Cuando visualizo la sección de predicciones
  Entonces debo ver:
    | Predicción |
    | Tiempo estimado para llenar vacantes abiertas |
    | Probabilidad de cumplir objetivos de contratación |
    | Candidatos con alta probabilidad de éxito |
  Y las predicciones deben actualizarse en tiempo real
```

### US-034: Reporte de Tiempo de Contratación
**Como** reclutador o manager  
**Quiero** ver reportes detallados del tiempo de contratación  
**Para** identificar cuellos de botella en el proceso

**Escenarios:**

```gherkin
Escenario: Generar reporte de tiempo de contratación
  Dado que tengo vacantes cerradas en el último trimestre
  Cuando genero un reporte de tiempo de contratación
  Entonces debo ver:
    | Métrica |
    | Tiempo promedio por etapa del pipeline |
    | Tiempo promedio total por vacante |
    | Comparación con períodos anteriores |
    | Vacantes que exceden el tiempo objetivo |
  Y debo poder filtrar por departamento, tipo de vacante, etc.
  Y debo poder exportar el reporte en PDF o Excel
```

### US-035: Análisis de Fuentes de Reclutamiento
**Como** reclutador  
**Quiero** analizar qué fuentes de reclutamiento son más efectivas  
**Para** optimizar la inversión en canales de publicación

**Escenarios:**

```gherkin
Escenario: Ver análisis de fuentes
  Dado que tengo aplicaciones de múltiples canales
  Cuando accedo al análisis de fuentes
  Entonces debo ver:
    | Canal | Aplicaciones | Conversión | Coste | ROI |
    | LinkedIn | 150 | 25% | 2000 EUR | Alto |
    | Indeed | 80 | 15% | 800 EUR | Medio |
    | Web corporativa | 30 | 40% | 0 EUR | Muy Alto |
  Y debo poder ver tendencias temporales
  Y debo poder comparar períodos
  Y el sistema debe sugerir optimizaciones
```

### US-036: Reportes Personalizables
**Como** administrador  
**Quiero** crear reportes personalizados con métricas específicas  
**Para** analizar aspectos particulares del proceso

**Escenarios:**

```gherkin
Escenario: Crear reporte personalizado
  Dado que soy un administrador
  Cuando creo un nuevo reporte personalizado
  Entonces debo poder seleccionar:
    | Opción |
    | Métricas a incluir |
    | Filtros (fecha, departamento, vacante, etc.) |
    | Formato de visualización (gráfico, tabla, etc.) |
    | Frecuencia de generación (diario, semanal, mensual) |
  Y debo poder guardar el reporte
  Y debo poder compartirlo con otros usuarios
  Y debo poder programar envío automático por email
```

---

## Épica 10: Integraciones Externas

### US-037: Integración con LinkedIn
**Como** sistema  
**Quiero** integrarme con la API de LinkedIn  
**Para** publicar vacantes y buscar candidatos

**Escenarios:**

```gherkin
Escenario: Publicar vacante en LinkedIn
  Dado que tengo una vacante lista para publicar
  Y tengo credenciales de LinkedIn configuradas
  Cuando selecciono LinkedIn como canal de publicación
  Entonces la vacante debe publicarse en LinkedIn Jobs
  Y debo recibir confirmación de la publicación
  Y las aplicaciones desde LinkedIn deben llegar al sistema
  Y debo poder ver métricas de LinkedIn en el dashboard

Escenario: Buscar candidatos en LinkedIn
  Dado que tengo integración con LinkedIn activa
  Cuando busco candidatos pasivos en LinkedIn
  Entonces debo poder ver perfiles de LinkedIn
  Y debo poder importar información al sistema
  Y debo poder contactar candidatos desde la plataforma
```

### US-038: Integración con Calendarios
**Como** sistema  
**Quiero** integrarme con Google Calendar y Outlook  
**Para** sincronizar entrevistas automáticamente

**Escenarios:**

```gherkin
Escenario: Sincronizar con Google Calendar
  Dado que un entrevistador tiene Google Calendar conectado
  Cuando programo una entrevista
  Entonces la entrevista debe aparecer en su Google Calendar
  Y los cambios deben sincronizarse bidireccionalmente
  Y si el entrevistador cambia la cita en Google Calendar, debe actualizarse en LTI
  Y el candidato debe recibir invitación de calendario si tiene email configurado
```

### US-039: Integración con Video Conferencia
**Como** sistema  
**Quiero** integrarme con Zoom y Google Meet  
**Para** generar links de video automáticamente

**Escenarios:**

```gherkin
Escenario: Generar link de Zoom para entrevista
  Dado que tengo integración con Zoom configurada
  Cuando programo una entrevista tipo "VIDEO"
  Entonces el sistema debe crear automáticamente una reunión de Zoom
  Y debe generar un link único para la entrevista
  Y el link debe ser enviado a ambos participantes
  Y la reunión debe configurarse con la duración correcta
  Y debe grabarse si está configurado
```

### US-040: Integración con Portales de Empleo
**Como** sistema  
**Quiero** integrarme con múltiples portales de empleo (Indeed, InfoJobs)  
**Para** publicar vacantes automáticamente

**Escenarios:**

```gherkin
Escenario: Publicar en múltiples portales
  Dado que tengo integraciones con Indeed e InfoJobs
  Cuando publico una vacante seleccionando ambos canales
  Entonces la vacante debe publicarse en Indeed
  Y la vacante debe publicarse en InfoJobs
  Y debo recibir confirmación de cada publicación
  Y las aplicaciones de ambos portales deben llegar al sistema
  Y debo poder ver de qué portal viene cada aplicación
```

---

## Notas del Backlog

### Criterios de Aceptación Generales
- Todas las funcionalidades deben ser responsivas (mobile-friendly)
- Todas las acciones deben tener feedback visual al usuario
- Los errores deben mostrarse de forma clara y con mensajes de ayuda
- El sistema debe soportar múltiples idiomas (español, inglés como mínimo)
- Todas las fechas deben respetar zonas horarias

### Dependencias Técnicas
- Autenticación debe estar implementada antes de otras funcionalidades
- Parsing de CVs requiere servicio de IA funcionando
- Integraciones externas requieren configuración de APIs
- Notificaciones en tiempo real requieren WebSockets

### Métricas de Éxito
- Tiempo de contratación reducido en 50%
- Tasa de satisfacción de usuarios > 4.5/5
- Tiempo de procesamiento de CV < 30 segundos
- Uptime del sistema > 99.5%

---

## Próximos Pasos

1. **Refinamiento del Backlog**: Detallar cada user story con criterios de aceptación más específicos
2. **Priorización**: Usar método MoSCoW o Value vs Effort para priorizar
3. **Estimación**: Realizar planning poker para estimar esfuerzo
4. **Sprint Planning**: Organizar user stories en sprints de 2 semanas

---

**Última actualización**: Backlog inicial generado  
**Próxima revisión**: Pendiente de refinamiento con el equipo

