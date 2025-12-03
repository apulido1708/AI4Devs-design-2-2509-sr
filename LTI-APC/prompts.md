# Prompts Utilizados para el Backlog.

Actua como un product owner experto en la construcción de productos digitales.

De acuerdo a la siguiente descripción @LTI-APC/LTI-APC.md 

Vamos a generar un backlog con las user stories escritas en formato gherkin.

Para esto vamos a generar el product backlog inicial con el titulo de las historias de usario.

Posterior a eso realizaremos el refinamiento correspondiente y luego la priorización.

Para este paso vas a generar un archivo md con el backlog y las user stories de forma general. 

Resultado: Archivo con backlog generado.

## Prompt para la priorización

# Prompt para Agente – Priorización de Backlog

Actúa como un experto en gestión de producto y priorización de backlogs con experiencia en metodologías Agile, Lean y frameworks de priorización como RICE, WSJF y MoSCoW.

Tu tarea será priorizar una lista de user stories o tareas aplicando los siguientes criterios obligatorios:

## Criterios de Priorización

### 1. Valor del Negocio
- Impacto en objetivos estratégicos  
- Retención de usuarios  
- Atracción de nuevos usuarios  
- Potencial de ingresos  
- Diferenciación frente a la competencia  

### 2. Urgencia
- Necesidad inmediata del mercado  
- Compromisos con stakeholders  
- Deadlines internas o externas  

### 3. Dependencias
- Si desbloquea otras tareas  
- Si está bloqueada por otras  
- Impacto en el flujo lógico de trabajo  

### 4. Coste de Implementación
- Esfuerzo estimado (bajo, medio, alto)  
- Complejidad técnica  
- Recursos humanos o tecnológicos necesarios  

### 5. Riesgos
- Riesgos técnicos  
- Riesgos de producto  
- Obstáculos potenciales  
- Nivel de incertidumbre  

### 6. Feedback de Usuarios
- Frecuencia del feedback  
- Severidad del problema reportado  
- Impacto en la experiencia de usuario  

### 7. Madurez Tecnológica
- Disponibilidad de la tecnología  
- Estabilidad de las soluciones propuestas  
- Nivel de experimentación necesario  

## Output Requerido

### 1. Tabla de evaluación
Genera una tabla para cada user story con:
- Valor del negocio (1–5)  
- Urgencia (1–5)  
- Dependencias (1–5; mayor puntaje = mayor prioridad)  
- Coste (1–5, invertido: 5 = barato, 1 = costoso)  
- Riesgo (1–5, invertido: 5 = bajo riesgo, 1 = alto riesgo)  
- Feedback de usuarios (1–5)  
- Madurez tecnológica (1–5)  
- Puntaje total normalizado  

### 2. Lista priorizada del backlog
Devuelve el backlog ordenado de mayor a menor prioridad.  
Incluye una breve explicación para cada item.

### 3. Justificación general
Incluye un resumen final que explique por qué este orden maximiza valor, minimiza riesgo y ofrece una ejecución más eficiente para el roadmap.

## Formato de entrada
Cuando reciba un backlog como: Archivo de backlog.

Debes devolver la priorización completa siguiendo los criterios anteriores.

## Instrucciones adicionales
- Sé objetivo y explícito.  
- No pidas aclaraciones a menos que la user story sea completamente ambigua.  
- Si falta información, realiza supuestos razonables y menciónalos.  
- Usa un formato claro, profesional y listo para entregar a un equipo de producto.


El resultado de este prompt fue el Backlog priorizado.

# Prompt para Agente – Generación de Tickets de Trabajo desde una Épica

Actúa como un experto en gestión de producto, redacción de tickets y descomposición de épicas en tareas accionables. Tu objetivo es transformar una épica y sus historias asociadas en un conjunto de tickets de trabajo claros, completos y listos para ser usados por un equipo Agile.

## Instrucciones Generales

1. Recibirás:
   - Una épica
   - Una lista de historias priorizadas asociadas a esa épica

2. Tu tarea es:
   - Descomponer cada historia en uno o varios tickets de trabajo
   - Redactar los tickets siguiendo la estructura formal definida más abajo
   - Mantener consistencia en tono, claridad y propósito
   - Evitar ambigüedades y suposiciones tácitas (si algo debe asumirse, indícalo explícitamente)

## Estructura Obligatoria de Cada Ticket

Cada ticket debe incluir:

1. **Título**
   - Claro, conciso y específico  
   - Debe indicar la acción y el componente

2. **Descripción**
   - Propósito de la tarea (por qué existe)
   - Detalles específicos necesarios para su ejecución

3. **Criterios de Aceptación**
   - Condiciones objetivas que deben cumplirse
   - Pruebas o validaciones necesarias

4. **Prioridad**
   - Alta, Media o Baja
   - La prioridad debe alinearse con la historia original y su valor

5. **Estimación de Esfuerzo**
   - En puntos de historia o tiempo estimado según convenga
   - Debe ser coherente con la complejidad

6. **Asignación**
   - Indica el equipo responsable (Backend, Frontend, UX/UI, QA, Arquitectura, etc.)
   - Si no hay información suficiente, sugiere un equipo razonable

7. **Etiquetas / Tags**
   - Tipo: bug, feature, enhancement, research, task
   - Área del producto: backend, frontend, seguridad, UI, etc.
   - Sprint o release (si aplica)

8. **Comentarios**
   - Espacio para notas, riesgos, consideraciones o preguntas relevantes

9. **Enlaces o Referencias**
   - Documentos, diseños, decisiones arquitectónicas o tickets relacionados

10. **Historial de Cambios**
   - Lista con fecha y cambio realizado
   - Iniciar siempre con: "Creado el DD/MM/AAAA por Agente"

## Formato de Salida

La salida debe ser una lista de tickets, cada uno completamente estructurado.  
Si una historia requiere múltiples tickets, sepáralos claramente.

Ejemplo de formato:


Descripción: …

Criterios de Aceptación:
	•	…
	•	…

Prioridad: …

Estimación: …

Asignado a: …

Etiquetas: …

Comentarios: …

Enlaces: …

Historial de Cambios:
	•	Creado el DD/MM/AAAA por equipo de dev

El resultado de este prompt fue el archivo de los tickets de la Epica 1 de autenticación.