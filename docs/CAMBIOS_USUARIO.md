# Cambios para el usuario

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-03 (Chile, America/Santiago).

## 2026-11-02 — Configuración inicial de documentación

- Qué pidió el usuario: recrear la documentación inicial aprobada, conservar index.html y guardar los documentos en una rama separada en GitHub.
- Por qué: mantener contexto entre chats y trabajar con instrucciones claras, seguras y comprensibles.
- Qué cambió: se crearon nueve documentos con el contexto del seminario, preferencias del usuario, método de trabajo, decisiones y asuntos de seguridad pendientes. Se establecen dos registros obligatorios para los cambios futuros.
- Qué debería notar el usuario: las futuras sesiones podrán consultar estas instrucciones y explicar los cambios en lenguaje sencillo. La aplicación conserva su funcionamiento; esta tarea no modifica ni publica la aplicación y no resuelve los pendientes académicos o de seguridad.

## 2026-11-02 — Auditoría de seguridad sin cambios de funcionamiento

- Qué pidió el usuario: revisar nuevamente la seguridad contra el código actual, explicar los hallazgos sin lenguaje técnico y documentarlos, sin implementar soluciones, commit, push ni publicación.
- Por qué: proteger datos de escolares, evitar pérdidas y contar con resultados confiables antes de decidir correcciones.
- Qué cambió: SEGURIDAD.md ahora registra once hallazgos confirmados en el código, su gravedad, consecuencias, información afectada, evidencia, recomendaciones y orden de atención. DECISIONES.md registra el alcance de esta revisión. Se conservan los antecedentes y se distinguen los permisos de Google todavía no comprobados.
- Qué debería notar el usuario: dispone de un diagnóstico para decidir siguientes pasos. Primero se recomienda proteger acceso y resultados y revisar los permisos de Google; después confirmar y recuperar guardados; luego evitar duplicados y separar pruebas; finalmente reforzar validaciones, exportaciones y audio. La aplicación sigue igual y los riesgos continúan abiertos.
- Comprobación: lectura completa y ocho verificaciones locales con datos ficticios y red simulada; no se enviaron evaluaciones a Google ni se revisó su configuración privada. La última versión remota sigue sin poder confirmarse por el fallo de conexión de la revisión anterior.

## 2026-11-02 — Colegio obligatorio y retirada de Observaciones

- Qué pidió el usuario: añadir un desplegable obligatorio con tres colegios, incluirlo en resultados, CSV y envío actual a Google, y dejar de pedir Observaciones en la pantalla pública. Primero revisar el resultado, sin commit ni push.
- Por qué: asociar cada evaluación al colegio correspondiente con un paso sencillo, manteniendo una sola aplicación pública sin cuentas.
- Qué cambió: el campo comienza en «Selecciona tu colegio» y bloquea el avance hasta elegir Santiago College, Lincoln International Academy Chicureo o Craighouse School. El colegio se conserva durante la batería y se muestra en el resumen; el CSV añade la columna colegio y el contenido de envío incorpora ese dato. Observaciones ya no aparece; nombre, género y fecha de nacimiento se mantienen.
- Qué debería notar el usuario: debe seleccionar un colegio antes de continuar; si falta, aparece «Selecciona tu colegio para continuar.». El aspecto general y las cuatro modalidades se conservan.
- Comprobación: tres baterías completas en Chromium, una por colegio, con prácticas y respuestas simuladas en las cuatro modalidades; se verificaron bloqueo sin colegio o con valor ajeno a la lista, conservación al volver, resultado, CSV y contenido de envío. También se comprobó nueva batería y pantalla de teléfono sin desbordamiento.
- Limitaciones: audio y conexión con Google simulados para no enviar registros ficticios. El campo se incluye en lo que se intenta enviar, pero no se modificó ni verificó el receptor de Google; no se puede confirmar que lo almacene. Tampoco se implementó recuperación ni seguridad de servidor, ni se publicó la aplicación.

## 2026-11-02 — Identificación automática del participante

- Qué pidió el usuario: implementar colegio, nivel, letra y número de lista obligatorios y generar internamente el código común previsto para Digit Span y YAP-SL, sin integrar todavía ambos instrumentos.
- Por qué: poder relacionar después las bases sin pedir al participante que escriba o copie un código.
- Qué cambió: se mantienen los tres colegios; se añade nivel 5°/6°, letra libre convertida a mayúscula y número de lista de 1 a 99. Las entradas inválidas o incompletas bloquean el avance con un mensaje sencillo. El código usa las abreviaturas SC, LIA y CHS y tres dígitos para el número (por ejemplo SC-5B-012).
- Qué debería notar el usuario: completa los campos iniciales y continúa; el código no aparece en esa pantalla. Los datos quedan asociados al comenzar y figuran en el resultado, el CSV y el contenido del envío actual. Cada evaluación conserva su propio identificador independiente. Nombre, género y fecha de nacimiento se mantienen, y Observaciones sigue fuera de la pantalla.
- Pruebas: pasaron 72 combinaciones de colegio/nivel/letra/número; rechazo de campos vacíos, letras inválidas y números cero, negativos, decimales, texto y fuera de rango. Pasaron los tres ejemplos solicitados en baterías completas de las cuatro modalidades, y la comprobación del resultado, CSV, envío simulado, nueva batería y prueba rápida. Se revisaron vistas de computador y teléfono.
- Límites: ninguna respuesta real se envió a Google; audio y red simulados. El receptor podría ignorar los campos nuevos y no se ha verificado su guardado. Sin integración con YAP-SL, Vercel, servidor ni recuperación; sin commit, push ni publicación.


## 2026-11-02 — Prueba rápida de desarrollador independiente del participante

- Qué pidió el usuario: poder ejecutar la prueba rápida desde Desarrolladores sin haber seleccionado colegio ni completado la identificación del participante.
- Qué cambió: la prueba rápida ya no valida Colegio, Nivel, Letra ni Número de lista y tampoco rellena Nombre, Género o Fecha de nacimiento con datos ficticios.
- Qué debería notar el usuario: al entrar a Desarrolladores y pulsar “Prueba rápida”, la prueba comienza directamente. Al terminar indica que fue una prueba interna, sin datos de participante y sin envío a Google Sheets.
- Qué no cambió: las evaluaciones reales siguen exigiendo todos los datos obligatorios antes de comenzar.

## 2026-11-02 — Corrección de cursos a 4° y 5°

- Qué pidió el usuario: cambiar las opciones de nivel porque la muestra corresponde a 4° y 5°, no a 5° y 6°.
- Qué cambió: el selector de Nivel ahora ofrece únicamente 4° y 5°. La validación también acepta solo esos dos niveles.
- Qué debería notar el usuario: ya no aparece 6° y ahora puede seleccionar 4°. El código de participante mantiene el mismo formato; por ejemplo, SC-4B-012 o LIA-5A-007.
- Qué no cambió: colegios, letra, número de lista, modalidades de Digit Span, puntuación, audio y guardado.

## 2026-11-03 — Presentación guiada de Digit Span

- Pedido y motivo: orientar al participante con una experiencia formal, académica y fácil de entender, conservando los colores y la evaluación actual.
- Cambio: bienvenida antes de los datos personales; instrucciones generales simplificadas; introducción independiente para cada modalidad con textos solicitados, ejemplos Escuchas/Respondes e indicador Sección 1–4. Los ejemplos se apilan en teléfono para facilitar su lectura.
- Efecto: Comenzar evaluación lleva a identificación; Continuar a instrucciones generales; Entendido, continuar a la primera modalidad. Cada modalidad mantiene práctica, prueba y pantalla de finalización antes de la siguiente introducción.
- Conservación: niveles 4°/5°, validaciones y código automático oculto durante identificación; mismo protocolo, puntuación, prácticas, secuencias, audio, resultados, CSV y guardado. Desarrolladores permanece accesible desde bienvenida e identificación, y Prueba rápida no requiere datos ni envía a Google. Volver/Salir desde Desarrolladores regresa a la pantalla desde la que se ingresó.
- Documentación: contexto actualizado y decisión D-007, preservando el historial anterior.
- Pruebas: recorridos completos en Chromium con datos ficticios a 1280, 390 y 320 px; cuatro modalidades y Prueba rápida. Audio y temporizadores simulados; envío interceptado sin escribir en Google. No se prueba audio físico ni almacenamiento remoto.

## 2026-11-03 — Bienvenida con texto en viñetas

- Cambio: el texto explicativo de la portada se presenta ahora en tres puntos separados para facilitar la lectura.
- Alcance: solo cambia la presentación del texto; no modifica navegación, evaluación, lógica ni guardado.

## 2026-11-03 — Botón de bienvenida renombrado

- Cambio: el botón de la portada pasa de “Comenzar evaluación” a “Siguiente”.
- Motivo: al pulsarlo todavía no comienza la evaluación; solo se avanza al formulario del participante.
- Alcance: solo cambia el texto del botón, sin modificar navegación ni lógica.

## 2026-11-03 — Continuar solo con datos completos

- Cambio: el botón “Continuar” de Datos del participante permanece deshabilitado hasta que todos los campos obligatorios estén completos y válidos.
- Campos exigidos: nombre completo, género, fecha de nacimiento, colegio, nivel, letra y número de lista.
- Validación: se mantiene además la comprobación al intentar avanzar, por lo que no se modifica el flujo posterior ni la evaluación.

## 2026-11-03 — Velocidad de voz normalizada

- Cambio: la velocidad de pronunciación de los números pasa de 0,9 a 1,0, correspondiente a una velocidad normal de síntesis de voz.
- Se mantiene exactamente la pausa de 250 ms entre números.
- No se modifican secuencias, puntuación, tiempos entre intentos ni lógica de evaluación.

## 2026-11-03 — Prueba de audio antes de la evaluación

- Cambio: después de las instrucciones generales aparece una pantalla de “Prueba de audio” antes de la primera modalidad.
- Funcionamiento: el participante pulsa “Probar audio” y escucha tres números de ejemplo con la misma voz y configuración del test. Puede repetir el audio y ajustar el volumen del dispositivo.
- El botón para continuar se habilita solo después de una reproducción correcta.
- Esta prueba de audio no cuenta como práctica, no genera resultados y no se guarda en Google Sheets.

## 2026-11-03 — Voz latina y pronunciación más pausada

- Cambio: la velocidad de pronunciación de cada número baja de 1,0 a 0,85 para que se escuche más clara y natural.
- La selección de voz deja de priorizar cualquier español y pasa a preferir voces latinoamericanas: primero Latinoamérica (es-419), luego México, español de EE. UU. y otras variantes de América Latina.
- Se evita usar una voz de España (es-ES) como alternativa automática.
- La pausa entre números permanece exactamente en 250 ms.
- La prueba de audio previa utiliza la misma voz y velocidad, por lo que permite comprobar cómo sonará la evaluación real.

## 2026-11-03 — Selector para elegir la voz

- Cambio: en Desarrolladores → Audio aparece un selector con las voces en español disponibles realmente en el dispositivo y un botón “Probar voz seleccionada”.
- Funcionamiento: se puede escuchar 3–8–1 con cada voz y elegir la que resulte más natural. “Automática latina” conserva la selección automática actual.
- Persistencia: la voz elegida se guarda en ese navegador/dispositivo y se usa también en la prueba de audio previa y en toda la evaluación.
- “Restaurar recomendados” vuelve a Automática latina.
- La disponibilidad y nombres de las voces dependen del sistema operativo y navegador.

## 2026-11-03 — Paulina (es-MX) como voz predeterminada

- Cambio: Paulina en español de México (`es-MX`) pasa a ser la voz predeterminada de toda la aplicación.
- Se usa por defecto en la prueba de audio previa, prácticas y evaluación real.
- El selector de Desarrolladores se mantiene: si el evaluador escoge manualmente otra voz, esa elección prevalece en ese dispositivo.
- Si Paulina no está disponible, la aplicación usa primero otra voz `es-MX` y luego una alternativa latinoamericana para evitar fallos de audio.
- Velocidad y pausa se mantienen en 0,85 y 250 ms respectivamente.

## 2026-11-09 — Portal general del estudio, asentimiento y YAP-SL

- La portada deja de presentar únicamente “Digit Span Test” y pasa a “Estudio de Actividad Física y Memoria”.
- Nuevo recorrido inicial: bienvenida → explicación general del estudio → asentimiento del estudiante → datos del participante → panel de actividades.
- El asentimiento aparece antes de solicitar datos personales o mostrar las actividades. “No quiero participar” lleva a una pantalla de cierre y no solicita datos.
- El panel “Tus actividades” contiene dos módulos: cuestionario de actividad física (YAP-SL) y actividad de memoria (Digit Span).
- El YAP-SL abre el Google Form proporcionado por el usuario en una pestaña nueva; al volver, el participante confirma que lo completó.
- El Digit Span conserva su protocolo, prueba de audio, prácticas, modalidades y guardado. Al terminar, vuelve al panel del estudio sin mostrar puntajes al participante.
- El estudio solo puede finalizar cuando ambas actividades están marcadas como completadas.
- Los datos del participante pueden corregirse desde el panel mientras no se haya iniciado ninguna actividad. Al abrir YAP-SL o completar Digit Span quedan fijados para evitar mezclar resultados de personas distintas.
- El formulario YAP-SL todavía no recibe automáticamente el código de participante porque no se conoce el identificador interno de su campo en Google Forms.

## 2026-11-09 — Volver desde datos del participante

- Se añade un botón “Volver” en la pantalla de Datos del participante.
- El botón regresa al asentimiento.
- Los datos que ya se hayan escrito permanecen en pantalla si el estudiante vuelve a entrar a Datos del participante.

## 2026-11-09 — Vista previa completa desde Desarrolladores

- En Desarrolladores → Herramientas se añade “Vista previa desde el inicio”.
- La vista previa comienza en la bienvenida y permite recorrer introducción, asentimiento, datos, panel de actividades, YAP-SL y el primer Digit Span.
- Los datos del participante se rellenan automáticamente con información ficticia para no tener que escribirlos.
- Se muestra una franja “Vista previa de desarrollador · No se guardarán datos”.
- El Digit Span de esta vista previa se acorta a Forward, longitud 3 y un intento, para revisar rápidamente el flujo hasta el primer test.
- Ningún resultado de esta vista previa se envía a Google Sheets.
- Dentro de la vista previa se puede volver a los datos aunque se haya abierto YAP-SL, facilitando la revisión de navegación.

## 2026-11-09 — Código de participante antes del asentimiento

- El flujo cambia a: bienvenida → explicación → identificación mínima → código de participante → asentimiento → datos restantes → actividades.
- Antes del asentimiento solo se solicitan colegio, nivel, letra y número de lista, porque son los datos necesarios para generar el código.
- El asentimiento muestra explícitamente el código generado, por ejemplo `SC-4B-007`.
- Al aceptar, se registra en la sesión la fecha/hora del asentimiento y se asocia al mismo código.
- Nombre completo, género y fecha de nacimiento se solicitan después de aceptar.
- El código queda fijo y visible también en Datos del participante y Tus actividades.
- El payload y el CSV de Digit Span incluyen asentimiento, fecha del asentimiento y código de participante.
- YAP-SL sigue siendo un Google Form externo; la página muestra el código para usar el mismo identificador si el Form lo solicita. El prellenado automático sigue pendiente porque no conocemos el `entry id` del campo correspondiente.

## 2026-11-09 — YAP-SL nativo dentro del portal

- Se elimina el Google Form incrustado.
- Las 4 preguntas generales y los 15 ítems del YAP-SL se responden directamente dentro de la página del estudio.
- El cuestionario se presenta una pregunta por pantalla, con progreso visible y el mismo diseño del portal.
- No se vuelven a solicitar código, colegio, nivel, género ni fecha de nacimiento; se reutilizan los datos ya ingresados.
- Las respuestas quedan asociadas al mismo código de participante.
- Al responder la pregunta 19, el YAP-SL se marca automáticamente como completado; no existe un botón manual para saltarse preguntas.
- Una vez completado, el YAP-SL queda bloqueado para evitar cambios posteriores.

## 2026-11-09 — YAP-SL sin salida intermedia

- Una vez iniciado el YAP-SL, se elimina la opción de volver a “Tus actividades”.
- El estudiante sólo puede avanzar o volver a la pregunta anterior.
- En la primera pregunta, “Pregunta anterior” permanece deshabilitado.
- Al completar las 19 preguntas, recién se vuelve automáticamente al panel de actividades.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría local de seguridad documentada sin cambios de funcionamiento; alcance y límites registrados en D-003.
- 2026-11-02 (Chile): Colegio obligatorio, Observaciones retirado de la pantalla pública y pruebas del recorrido actual; decisión D-004.
- 2026-11-02 (Chile): identificación común automática, validaciones de curso y lista, datos en resultado/CSV/envío y pruebas; decisión D-005.
- 2026-11-02 (Chile): niveles corregidos a 4°/5°; decisión D-006.
- 2026-11-03 (Chile): presentación guiada y navegación documentadas; protocolo y lógica de evaluación conservados (D-007).
