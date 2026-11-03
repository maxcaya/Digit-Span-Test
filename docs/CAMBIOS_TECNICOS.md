# Cambios técnicos

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-03 (Chile, America/Santiago).

## 2026-11-02 — Configuración inicial de documentación

- Archivos: AGENTS.md, README.md, docs/CONTEXTO_USUARIO.md, docs/CONTEXTO_PROYECTO.md, docs/METODOLOGIA_TRABAJO.md, docs/SEGURIDAD.md, docs/DECISIONES.md, docs/CAMBIOS_USUARIO.md y docs/CAMBIOS_TECNICOS.md (todos nuevos).
- Implementación: documentos Markdown con fechas de Chile e historial breve; navegación desde README.md e instrucciones aplicables al repositorio en AGENTS.md. Se separan contexto estable, decisiones, pendientes y registros funcional y técnico.
- Decisiones técnicas: documentación sin dependencias, frameworks, bases de datos ni cambios en index.html. Rama solicitada: configuracion-codex-inicial. No realizar merge ni publicación.
- Riesgos: los asuntos de seguridad existentes permanecen pendientes; documentarlos no los corrige. La referencia al WISC-V no demuestra equivalencia de todas las modalidades.
- Pruebas: comprobar igualdad byte a byte de index.html frente a HEAD y su huella SHA-256 previa; revisar que el conjunto de archivos agregados sea exactamente el solicitado, que existan metadatos e historiales en los nueve documentos, que los enlaces locales sean válidos y que git diff --check no detecte errores de formato. Los resultados se comunican al cerrar la tarea.
- Limitaciones: no se realizó auditoría del código, de Google Sheets ni validación académica; no se ejecutaron evaluaciones con participantes o datos personales. El contenido reconstruye lo solicitado en esta sesión, sin acceso a versiones documentales anteriores.

## 2026-11-02 — Auditoría estática y comprobaciones locales de seguridad

- Archivos modificados: docs/SEGURIDAD.md, docs/DECISIONES.md, docs/CAMBIOS_USUARIO.md y docs/CAMBIOS_TECNICOS.md. Sin modificaciones en index.html.
- Base: rama work, commit 693be4ab0acccf1767850a5be75b03ee207c8bf2. Se leyeron AGENTS.md, README.md y los siete documentos de docs/, además de las 1074 líneas de index.html. No se confirmó actualidad remota por fallo previo de conexión; no se asume sincronización con GitHub.
- Implementación documental: once hallazgos S-01 a S-11 con gravedad, explicación funcional, consecuencia, alcance, evidencia por líneas y solución general. Se preserva el antecedente preliminar y se separa evidencia de cliente de hipótesis condicionadas al receptor. D-003 registra alcance y límites.
- Pruebas: ocho comprobaciones ejecutadas satisfactoriamente mediante Node.js v24.19.0 y vm con DOM mínimo, fetch y descarga simulados: acceso directo a panel sin login; aceptación de fecha futura; parámetros fuera de rango; resumen inconsistente incorporado al payload; aviso positivo y saveCompleted ante respuesta opaca status 0; dos solicitudes consecutivas; prefijo de fórmula sin neutralizar en CSV; normalización de respuestas a dígitos. Script temporal fuera del repositorio, sin datos reales ni solicitudes externas. No son pruebas completas de interfaz o servidor.
- Verificación de alcance: comprobar git diff --check, lista de archivos modificados e igualdad byte a byte de index.html con HEAD y con su SHA-256 previo f0cb7982ce50f061bd4c376040df69b3bf69c37d4f19931fada18f650c973be1.
- Riesgos y limitaciones: ningún hallazgo queda corregido. Apps Script, permisos de Sheets/Drive, deduplicación y validación remotas, cabeceras de alojamiento y almacenamiento real no se inspeccionaron. No se certifica seguridad integral, cumplimiento legal ni validez académica. No se incorporaron secretos ni direcciones de despliegue a la documentación.
- Autorización aplicada: únicamente documentación; sin commit, push, merge ni publicación.

## 2026-11-02 — Campo Colegio en la aplicación actual

- Archivos: index.html, docs/CONTEXTO_PROYECTO.md, docs/DECISIONES.md, docs/CAMBIOS_USUARIO.md y docs/CAMBIOS_TECNICOS.md.
- Implementación: select school con required y opción inicial vacía, tres valores admitidos y comprobación explícita mediante SCHOOLS antes de continuar y de comenzar. state.school captura la selección al iniciar la batería; participant() la usa en resultado final mediante textContent, en participant.school del payload y en cada fila del CSV. La nueva columna colegio se agrega al final para conservar el orden de las columnas anteriores.
- Observaciones: eliminado el campo de la pantalla; participant() tolera su ausencia y conserva notes vacío para compatibilidad con el payload actual. No se alteran modalidades, puntuación, audio, CONFIG ni receptor/destino de Google.
- Decisión: D-004. Mantener una única aplicación y limitar esta implementación al navegador. Se conserva intacto SEGURIDAD.md como auditoría de su versión de referencia, sin presentar sus hallazgos como resueltos.
- Pruebas ejecutadas: Playwright con Chromium real en modo sin ventana, tres baterías (una por colegio), cada una con cuatro prácticas correctas y tres intentos reales por modalidad (un acierto y dos errores), conservando la configuración original. Se verificaron 16 registros por batería y los cuatro resúmenes (span 3, un acierto, dos errores); bloqueo por longitud incorrecta de respuesta; selección inicial vacía, rechazo de colegio ajeno a lista, ida y vuelta a identificación, asociación fija aunque cambie el control tras comenzar, ausencia de notes sin errores, participant.school en payload y POST interceptado, columna colegio en todas las filas del CSV descargado. Sin errores JavaScript observados.
- Pruebas de interfaz: nueva batería restablece selección vacía; vista de 390 × 844 sin desbordamiento horizontal y captura revisada visualmente. Audio y temporizadores simulados para automatizar; todas las solicitudes HTTP se interceptaron, sin envío real a Google. El script y la captura de comprobación se mantienen fuera del repositorio.
- Verificación de alcance: git diff --check y revisión del diff; únicamente los cinco archivos previstos, sin dependencias ni funciones de servidor. Los cambios quedan pendientes de revisión del usuario, sin commit ni push.
- Riesgos y límites: validación solo de navegador, evadible como el resto del código actual. El receptor puede ignorar participant.school; no se ha comprobado almacenamiento remoto. Se mantienen los riesgos de guardado no confirmado, pérdida al recargar y demás hallazgos de la auditoría. No se implementó recuperación, seguridad nueva ni despliegue.

## 2026-11-02 — Código de participante y datos de curso

- Archivos: index.html, docs/CONTEXTO_PROYECTO.md, docs/DECISIONES.md, docs/CAMBIOS_USUARIO.md y docs/CAMBIOS_TECNICOS.md; se preservan los cambios pendientes de Colegio de la tarea anterior.
- Implementación: SCHOOL_CODES fija SC/LIA/CHS; grade admite solo strings 5 o 6; classLetter recorta espacios exteriores, pasa a mayúsculas y normaliza Unicode NFC, validando un carácter de categoría letra (incluye Ñ). No se usa maxlength para evitar truncar silenciosamente entradas de varias letras. listNumber utiliza teclado numérico con inputmode y validación completa de dígitos/entero 1–99; elimina espacios y rechaza formatos como 1e1, +7, 1.5 y texto en lugar de reinterpretarlos. Se usa un campo de texto con teclado numérico para conservar y detectar esos formatos inválidos, sin la conversión implícita de type=number.
- Asociación: identificationFromForm genera participantCode únicamente con identificación válida y rellena el número con padStart(3). state.identification captura school, grade, classLetter, listNumber y participantCode al comenzar; participant() reutiliza esa identificación fija para resultado final, CSV y payload. Validación antes de continuar y antes de comenzar. La prueba rápida también valida/captura identificación y reinicia evaluationId y saveCompleted para no reutilizar otra evaluación.
- Contrato del envío: participant.school (nombre completo), participant.grade (string 5/6), participant.class_letter (mayúscula), participant.list_number (entero 1–99), participant.participant_code (código normalizado). evaluation_id conserva su generación independiente y estabilidad entre llamadas al payload de una misma evaluación. CSV conserva las columnas anteriores y añade nivel, letra, numero_lista y codigo_participante después de colegio; el número de tres dígitos está en el código y la columna numero_lista contiene el entero.
- Decisión: D-005 amplía D-004; código previsto como clave de enlace con YAP-SL, sin implementar ese enlace. Se actualiza el pendiente de nivel educacional, ahora confirmado. No hay cambios en modalidades, CONFIG, cálculo de puntuación, audio ni receptor de Google; SEGURIDAD.md conserva intacta la auditoría del commit de referencia.
- Pruebas ejecutadas: Playwright/Chromium, script temporal /tmp/probar-identificacion.cjs. 72 combinaciones válidas (3 colegios × 2 niveles × 3 letras en diferentes formatos × números 1, 7, 12, 99); espacios y mayúsculas; rechazo por UI de cuatro campos faltantes, letras múltiples/números/símbolos, colegio/nivel ajenos a lista y números inválidos (vacío, cero, negativos, decimales, texto, exponencial, signo positivo y mayores de 99). Se verificó también el bloqueo al comenzar si el dato se invalida después de Continuar.
- Pruebas de regresión: SC-5B-012, LIA-6A-007 y CHS-5C-021 recorrieron las cuatro modalidades con cuatro prácticas y doce intentos reales por batería (un acierto y dos errores por modo). Se comprobaron resúmenes, longitud de respuesta, identificación fija aun si se alteran los controles después de comenzar, resultado final, contenido del POST interceptado y todas las filas del CSV descargado; tres IDs de evaluación distintos y estables dentro de cada evaluación. Nueva batería limpia campos, prueba rápida con ID propio sin envío y sin errores JavaScript. Vistas 1000 × 1050 y 390 × 844, teléfono sin desbordamiento horizontal y capturas para revisión visual.
- Límites de pruebas: datos ficticios; motor de voz y temporizadores simulados, solicitudes HTTP interceptadas sin escribir en Google. Las capturas y script están fuera del repositorio. Sin prueba de audio físico ni almacenamiento remoto.
- Verificación y riesgos: git diff --check y revisión del alcance. Solo navegador; las validaciones siguen siendo evadibles y los riesgos de auditoría permanecen abiertos. No se añade validación de servidor, recuperación, contexto de año escolar, integración de YAP-SL ni despliegue. Sin commit ni push.


## 2026-11-02 — Separación de la prueba rápida del flujo de identificación

- Archivo principal: `index.html`.
- Implementación: el manejador de `quickTest` deja de llamar a `validateIdentification()` y usa un estado de identificación vacío exclusivo para la prueba interna. También deja de modificar los campos públicos `fullName`, `gender` y `birthDate`.
- Resultado final: `renderFinal()` trata la prueba rápida antes de leer los datos del participante y muestra “Prueba interna de desarrollador / Sin datos de participante”. El flujo rápido mantiene la garantía existente de no llamar a `saveToGoogle()`.
- Regresión esperada: el flujo normal conserva `validateParticipant()` y `validateIdentification()`, por lo que Colegio, Nivel, Letra, Número de lista, Nombre, Género y Fecha de nacimiento siguen siendo obligatorios para una evaluación real.

## 2026-11-02 — Niveles permitidos 4°/5°

- Archivo principal: `index.html`.
- Implementación: el selector `grade` cambia de valores 5/6 a 4/5. Tanto `identificationFromForm()` como `validateIdentification()` validan ahora exclusivamente `["4","5"]`.
- Código de participante: no cambia la construcción; el nivel seleccionado se incorpora al mismo formato existente. Ejemplos vigentes: `SC-4B-012`, `LIA-5A-007`, `CHS-4C-021`.
- Documentación: se actualiza CONTEXTO_PROYECTO.md y D-006 registra que esta corrección reemplaza solo la parte de niveles de D-005.
- Regresión esperada: 4° y 5° avanzan con identificación válida; 6° deja de ser una opción y es rechazado si se intenta inyectar manualmente. No se modifican modalidades, puntuación, audio ni estructura del payload.

## 2026-11-03 — Presentación y navegación guiadas

- Archivos: index.html, docs/CONTEXTO_PROYECTO.md, docs/DECISIONES.md, docs/CAMBIOS_USUARIO.md y docs/CAMBIOS_TECNICOS.md.
- Implementación: welcomePage es la única sección activa inicial; startEvaluation abre participantPage. Nuevo acceso a Desarrolladores en bienvenida; developerReturnPage conserva el origen para que Volver/Salir regrese a welcomePage o participantPage según corresponda. Instrucciones generales y botón actualizados; MODE_PRESENTATION alimenta únicamente fillIntro con títulos, subtítulos, texto y ejemplos solicitados, manteniendo INFO y los títulos de resultados intactos. Progreso usa TEST_ORDER para respetar configuración de Desarrolladores. Ejemplos en dl adaptable de dos columnas a una; misma paleta, espaciado y ancho de lectura acotado.
- Alcance: presentación y navegación exclusivamente; se conservan sin cambios el protocolo, lógica de evaluación, CONFIG, PRACTICE, secuencias, audio, validaciones, código automático, puntuación, criterios de finalización, payload, CSV, Google y funciones de Desarrolladores. Se reutiliza nextMode para mostrar introducciones antes de cada práctica.
- Decisión: D-007. Sin dependencias nuevas en la aplicación.
- Verificación: revisión del diff, git diff --check y comparación del JavaScript previo y posterior retirando únicamente fillIntro, MODE_PRESENTATION y los dos nuevos manejadores de navegación.
- Pruebas: Playwright/Chromium a 1280×900, 390×900 y 320×900; bienvenida sin formulario, bloqueo con identificación incompleta, datos ficticios válidos, instrucciones generales, cuatro introducciones y sus prácticas, prueba real con un acierto y dos errores por modalidad, pantalla completada y resultado. Se comprueban 16 registros, cuatro resúmenes con span 3/un acierto/dos errores, código SC-4B-012 y un envío interceptado. Desde bienvenida se accede al panel mediante login y se completa Prueba rápida con campos vacíos, sin POST ni errores JavaScript. Comprobación de ancho sin desbordamiento en cada pantalla; capturas de escritorio y móvil fuera del repositorio.
- Límites: voz y temporizadores simulados; solicitudes externas interceptadas. Sin prueba de audio físico ni escritura real en Google; riesgos existentes de SEGURIDAD.md permanecen pendientes. No se modifica el receptor ni se realiza merge o despliegue.

## 2026-11-03 — Texto de bienvenida en lista

- Archivo: `index.html`.
- Implementación: el párrafo introductorio de `welcomePage` se reemplaza por una lista de tres elementos reutilizando `generalList`.
- Alcance: cambio únicamente de marcado/presentación, sin modificar JavaScript ni flujo funcional.

## 2026-11-03 — Etiqueta del botón inicial

- Archivo: `index.html`.
- Implementación: se cambia únicamente el texto visible de `#startEvaluation` de “Comenzar evaluación” a “Siguiente”.
- El manejador y destino siguen siendo los mismos: avanzar a `participantPage`.

## 2026-11-03 — Bloqueo de avance con identificación incompleta

- Archivo: `index.html`.
- HTML: `fullName`, `gender` y `birthDate` pasan a declararse `required`; `continueToInstructions` inicia deshabilitado.
- JavaScript: `participantFormComplete()` verifica los siete campos de identificación y `updateParticipantContinueState()` habilita el botón únicamente cuando todos son válidos. Se actualiza en eventos `input` y `change`.
- Seguridad funcional: `validateParticipant()` se conserva como segunda validación antes de navegar a instrucciones.
- Alcance: no se modifican código de participante, evaluación, puntuación, audio, payload, CSV ni Google Sheets.

## 2026-11-03 — Velocidad de voz por defecto a 1,0

- Archivo: `index.html`.
- `CONFIG.rate` cambia de `0.9` a `1.0`.
- El valor inicial de `cfgRate` y “Restaurar recomendados” se actualizan al mismo valor.
- `CONFIG.gap` permanece sin cambios en `250` ms.
- No se modifica `speakSequence()`, la separación entre dígitos ni la lógica del test.

## 2026-11-03 — Comprobación previa de audio

- Archivo principal: `index.html`.
- Nueva pantalla: `audioCheckPage`, ubicada entre instrucciones generales y la introducción de la primera modalidad.
- Reutiliza `speakSequence()` con la secuencia ficticia `[5,0,7]`, por lo que usa exactamente `CONFIG.rate`, `CONFIG.gap`, voz, tono y volumen de la evaluación.
- `audioCheckContinue` permanece deshabilitado hasta que la reproducción termina correctamente; el audio puede repetirse.
- `beginBattery` conserva la fijación de identificación y el reinicio del estado, pero ahora abre `audioCheckPage`; el paso a `introPage` ocurre desde `audioCheckContinue`.
- La prueba de audio no se agrega a `state.results`, no afecta puntuación, prácticas, span, payload, CSV ni guardado.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría local de seguridad documentada sin cambios de funcionamiento; alcance y límites registrados en D-003.
- 2026-11-02 (Chile): Colegio obligatorio, Observaciones retirado de la pantalla pública y pruebas del recorrido actual; decisión D-004.
- 2026-11-02 (Chile): identificación común automática, validaciones de curso y lista, datos en resultado/CSV/envío y pruebas; decisión D-005.
- 2026-11-02 (Chile): niveles permitidos corregidos a 4°/5°; decisión D-006.
- 2026-11-03 (Chile): presentación guiada y navegación documentadas; protocolo y lógica de evaluación conservados (D-007).
