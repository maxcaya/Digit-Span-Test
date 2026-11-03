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
- Conservación: niveles 4°/5°, validaciones y código automático oculto durante identificación; mismo protocolo, puntuación, prácticas, secuencias, audio, resultados, CSV y guardado. Desarrolladores permanece accesible desde bienvenida e identificación, y Prueba rápida no requiere datos ni envía a Google.
- Documentación: contexto actualizado y decisión D-007, preservando el historial anterior.
- Pruebas: recorridos completos en Chromium con datos ficticios a 1280, 390 y 320 px; cuatro modalidades y Prueba rápida. Audio y temporizadores simulados; envío interceptado sin escribir en Google. No se prueba audio físico ni almacenamiento remoto.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría local de seguridad documentada sin cambios de funcionamiento; alcance y límites registrados en D-003.
- 2026-11-02 (Chile): Colegio obligatorio, Observaciones retirado de la pantalla pública y pruebas del recorrido actual; decisión D-004.
- 2026-11-02 (Chile): identificación común automática, validaciones de curso y lista, datos en resultado/CSV/envío y pruebas; decisión D-005.
- 2026-11-02 (Chile): niveles corregidos a 4°/5°; decisión D-006.
- 2026-11-03 (Chile): presentación guiada y navegación documentadas; protocolo y lógica de evaluación conservados (D-007).
