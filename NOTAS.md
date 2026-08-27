# NOTAS

## Agente utilizado
Utilicé Gemini CLI como agente de AI dentro del repositorio del reto. Para configurarlo primero verifiqué Git, Node y npm, instalé Gemini CLI, cloné el repositorio y realicé la autenticación mediante AI Studio con una clave API de Gemini después de tener inconvenientes con la autenticación inicial.

## Qué delegué al agente
Primero le delegué la lectura del repositorio y del README. Después lo utilicé para revisar los archivos de datos y tickets, cruzar usuarios, licencias y logins, preparar la auditoría y proponer las respuestas de los cinco tickets.
También le delegué la actualización del playbook de offboarding y la preparación del caso de prueba.

## Qué tuve que revisar o corregir
No tomé los resultados del agente como definitivos. Verifiqué los hallazgos directamente contra los registros de los CSV y le pedí que mostrara la evidencia antes de modificar archivos.
Por ejemplo, en el caso de Juan Pérez pedí que la duplicidad se tratara como posible hasta validar la identidad. También pedí revisar nuevamente el TICKET-005 porque la información del ticket no coincidía con el estado registrado en `usuarios.csv`, por lo que finalmente quedó escalado.
Durante la Tarea 2 también tuve que cambiar de modelo porque se agotó la cuota del modelo que estaba utilizando.

## Funcionalidades avanzadas
Utilicé un subagente de QA (`codebase_investigator`) para revisar los resultados finales de la Tarea 2 y posteriormente de la Tarea 3. Lo utilicé para comprobar la consistencia de los archivos, las decisiones y las reglas, sin modificar los archivos durante la revisión.

## Qué haría diferente
Con más tiempo, definiría desde el principio una estrategia de verificación más estructurada para los hallazgos y aprovecharía más funcionalidades avanzadas del agente cuando realmente aporten al proceso.
