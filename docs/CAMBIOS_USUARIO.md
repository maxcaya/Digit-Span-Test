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

## 2026-11-03 — Presentación guiada de Digit Span

- Qué pidió el usuario: bienvenida antes de los datos personales, instrucciones generales claras y explicación independiente antes de cada modalidad; conservar colores y funcionamiento de evaluación. También solicitó niveles únicamente 4°/5° y Prueba rápida sin datos del participante, sin envío a Google.
- Por qué: una experiencia más guiada, formal y académica, comprensible en computador y teléfono.
- Qué cambió: al abrir se ve «Digit Span Test / Evaluación de memoria de trabajo» y «Comenzar evaluación». Luego se completa identificación, se leen instrucciones generales y se continúa a la introducción de cada sección. Cada introducción contiene ejemplos de lo que se escucha y responde y «Sección N de total». Tras completar una modalidad aparecen las instrucciones de la siguiente antes de su práctica.
- Qué se conserva: colores, datos y validaciones (salvo el cambio explícito de niveles), formato automático del código, prácticas, secuencias, audio, puntuación, intentos, finalización, resultados, CSV y envío existente. Las herramientas de Desarrolladores son accesibles desde bienvenida e identificación; Prueba rápida puede finalizar sin completar datos y sin enviar.
- Pruebas: recorrido completo de las cuatro modalidades en Chromium en escritorio y móvil; práctica incorrecta exige repetir, resúmenes y CSV correctos, contenido de envío simulado correcto. Se comprobaron niveles 4°/5°, rechazo de 6°, ejemplos y progreso, nueva batería, acceso al panel y Prueba rápida vacía sin envío incluso al volver a mostrar su resultado. Sin errores JavaScript ni desbordamiento horizontal; capturas revisadas.
- Límites: datos ficticios, voz y temporizadores simulados y solicitudes a Google interceptadas. No se verificó audio físico ni guardado remoto. No se certifica validez académica ni se resuelven los pendientes de seguridad. Se autoriza commit y push de esta rama, sin merge a main ni despliegue manual.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría local de seguridad documentada sin cambios de funcionamiento; alcance y límites registrados en D-003.
- 2026-11-02 (Chile): Colegio obligatorio, Observaciones retirado de la pantalla pública y pruebas del recorrido actual; decisión D-004.
- 2026-11-02 (Chile): identificación común automática, validaciones de curso y lista, datos en resultado/CSV/envío y pruebas; decisión D-005.
- 2026-11-03 (Chile): presentación y navegación guiadas, niveles 4°/5° y Prueba rápida sin identificación; protocolo conservado (D-006).
