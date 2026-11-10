# Decisiones

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-03 (Chile, America/Santiago).

## D-001 — Documentación persistente inicial

- Fecha: 2026-11-02 (Chile).
- Estado: vigente.
- Decisión: mantener nueve documentos para instrucciones, contexto, metodología, seguridad, decisiones y cambios, según la configuración solicitada por el usuario.
- Motivo: conservar contexto entre sesiones y permitir que el usuario solicite y comprenda cambios sin conocimientos de programación.
- Alcance: documentación; conservar index.html idéntico. Rama configuracion-codex-inicial, commit y subida autorizados; sin merge a main ni publicación de la aplicación.
- Decisión reemplazada: ninguna registrada en este repositorio. La aprobación previa es referida por el usuario; esta recreación usa el contenido solicitado en esta sesión.

## D-002 — Simplicidad, privacidad y trazabilidad

- Fecha: 2026-11-02 (Chile).
- Estado: vigente.
- Decisión: priorizar seguridad, privacidad, conservación de información y funciones existentes; justificar complejidad adicional y registrar cambios relevantes en ambos registros.
- Motivo: facilitar el mantenimiento con un usuario de conocimientos técnicos básicos y reducir riesgos.
- Decisión reemplazada: ninguna registrada.

## D-003 — Auditoría local documentada antes de implementar soluciones

- Fecha: 2026-11-02 (Chile).
- Estado: vigente para esta tarea.
- Decisión: auditar el código local completo y actualizar solo SEGURIDAD.md, ambos historiales y este registro; conservar index.html intacto. No implementar soluciones, hacer commit, push, merge ni publicar.
- Motivo: solicitud explícita del usuario de validar los antecedentes antes de decidir correcciones y comprender los problemas en lenguaje sencillo.
- Alcance: revisión del navegador y comprobaciones locales ficticias sin red. Las recomendaciones no seleccionan todavía una arquitectura ni autorizan correcciones. La seguridad y permisos del receptor de Google permanecen pendientes; tampoco se afirma que esta copia sea la última remota.
- Decisión reemplazada: ninguna. D-001 se conserva como registro de la configuración inicial; su autorización de commit y subida no se extiende a esta tarea. D-002 continúa vigente.

## D-004 — Colegio obligatorio y cambio controlado de identificación

- Fecha: 2026-11-02 (Chile).
- Estado: ampliada y reemplazada parcialmente por D-005 respecto del alcance de identificación; se conserva el historial y los criterios de aplicación única y Observaciones fuera de pantalla pública.
- Decisión: una única aplicación pública sin cuentas ni separación de usos; conservar nombre, género y fecha de nacimiento, añadir Colegio obligatorio limitado a Santiago College, Lincoln International Academy Chicureo y Craighouse School, y retirar Observaciones de la pantalla pública sin romper su campo interno.
- Implementación autorizada ahora: solo el campo, su validación en el navegador, asociación al iniciar la batería, resultado final, CSV y participant.school en el envío actual; actualizar contexto y ambos historiales. Mantener modalidades, diseño general e integración actual.
- Motivo: identificar el colegio de cada evaluación mediante una selección sencilla y preparar los datos sin mezclar este cambio con la implementación de seguridad.
- Límites: sin servidor nuevo, cambios del receptor de Google, Vercel, recuperación, commit, push, merge ni publicación. El plan de seguridad continúa pendiente; no se afirma guardado real del colegio en Google.
- Decisión reemplazada: ninguna registrada. Las propuestas conversacionales de modos separados e invitaciones se descartan por la instrucción posterior del usuario. D-003 se conserva como antecedente de la tarea de auditoría; su restricción de no modificar index.html no se extiende a este cambio expresamente autorizado. La referencia de auditoría permanece en el commit e9fb6fc7b1c07c9642c9a9c127992fb6664d2f5e.

## D-005 — Identificación común mediante código automático

- Fecha: 2026-11-02 (Chile).
- Estado: reemplazada parcialmente por D-006 únicamente respecto de los niveles permitidos.
- Decisión: ampliar identificación obligatoria con nivel 5°/6°, letra libre normalizada a mayúscula (una sola letra, sin espacios exteriores) y número de lista entero 1–99, además del colegio. Generar automáticamente SC/LIA/CHS-NIVEL+LETRA-NUMERO de tres dígitos, sin campo manual ni visualización en la pantalla inicial. Conservar los demás datos actuales.
- Motivo: usar posteriormente el mismo código para relacionar Digit Span y YAP-SL sin pedir que el participante lo copie o escriba.
- Alcance implementado: validación en navegador, identificación fijada al comenzar, resumen final, CSV y contenido enviado mediante la integración actual. evaluation_id se mantiene separado para cada evaluación. La prueba rápida de desarrollo usa identificación válida propia y reinicia su ID, conservando su comportamiento de no enviar al finalizar.
- Límites: sin integración con YAP-SL ni revisión del formulario, receptor nuevo, servidor, recuperación, Vercel, commit, push ni publicación. No se resuelven por este cambio falsificación, persistencia ni confirmación remota de guardado. Los códigos pueden repetirse entre años y no prueban identidad; el contexto común de estudio/año se definirá antes de cruzar períodos distintos.
- Decisión reemplazada: amplía y reemplaza parcialmente D-004, que limitaba el cambio a Colegio. Se mantienen aplicación única, ausencia de cuentas, retiro de Observaciones y demás límites. La restricción de D-003 corresponde a la tarea histórica de auditoría.

## D-006 — Corrección de niveles del estudio a 4° y 5°

- Fecha: 2026-11-02 (Chile).
- Estado: vigente.
- Decisión: los únicos niveles permitidos en la identificación de participantes son 4° y 5°. Se reemplaza el criterio anterior de 5°/6° definido en D-005.
- Motivo: corrección del nivel escolar de la muestra informado por el usuario.
- Alcance: actualizar las opciones visibles del selector, la validación interna y los ejemplos actuales del código de participante. El formato del código no cambia: COLEGIO-NIVEL+LETRA-NUMERO_LISTA, por ejemplo SC-4B-012 o LIA-5A-007.
- Qué no cambia: colegios, letra, número de lista, formato del código, evaluación, modalidades, puntuación, audio, CSV y estructura del envío.
- Reemplaza: solo la parte de D-005 que establecía 5°/6°; el resto de D-005 continúa vigente.

## Pendientes sin decisión definitiva

Selección final de modalidades; correspondencia de menor a mayor con secuenciación; justificación de mayor a menor; incorporación eventual de mano dominante y horas de sueño. Los niveles vigentes son 4°/5° según D-006; integración con YAP-SL y contexto de estudio/año siguen pendientes. Consultar CONTEXTO_PROYECTO.md. Los asuntos de SEGURIDAD.md requieren auditoría y no se consideran resueltos.

## Cómo reemplazar una decisión

Conservar la entrada anterior marcándola como reemplazada, enlazar la nueva decisión e indicar fecha y motivo. La nueva entrada debe identificar expresamente qué decisión reemplaza y por qué. Registrar la actualización en ambos registros de cambios.

## D-007 — Presentación guiada sin cambios del protocolo

- Fecha: 2026-11-03 (Chile).
- Estado: vigente.
- Decisión: anteponer bienvenida a identificación y presentar instrucciones generales y específicas con ejemplos visuales y progreso discreto antes de cada práctica. Conservar paleta, sobriedad y acceso directo a Desarrolladores.
- Motivo: facilitar comprensión y orientación del participante con una presentación formal y académica.
- Alcance: presentación y navegación; contenido de introducciones separado de INFO para conservar los títulos internos de resultados. Se reutilizan las transiciones existentes de las cuatro modalidades, sin modificar prácticas, secuencias, audio, puntuación, finalización, identificación, payload, CSV ni guardado.
- Reemplaza: ninguna decisión de protocolo. Actualiza la ubicación de la identificación descrita en D-004/D-005: ahora sigue a una bienvenida. D-006 conserva niveles 4°/5°; se mantiene la separación actual de Prueba rápida sin datos ni envío.
- Autorización de esta tarea: modificar index.html y documentación, nueva rama, commit y push; sin merge a main ni despliegue solicitado.

## D-008 — Comprobación de audio antes de iniciar la batería

- Fecha: 2026-11-03 (Chile).
- Estado: vigente.
- Decisión: incorporar una prueba de audio obligatoria entre las instrucciones generales y la primera modalidad. El participante debe reproducir un ejemplo antes de poder continuar, y puede repetirlo para ajustar el volumen.
- Motivo: confirmar de forma práctica que la voz se escucha con claridad antes de iniciar una evaluación dependiente del audio.
- Alcance: la comprobación reutiliza la misma síntesis y configuración de voz que la evaluación, pero no cuenta como práctica, intento ni resultado y no se incorpora al guardado.
- No cambia: secuencias evaluadas, puntuación, criterios de finalización, prácticas, payload, CSV ni Google Sheets.

## D-009 — Voz latinoamericana y velocidad 0,85

- Fecha: 2026-11-03 (Chile).
- Estado: vigente.
- Decisión: usar velocidad de síntesis 0,85 y priorizar voces de español latinoamericano instaladas en el dispositivo, comenzando por es-419, es-MX y es-US. No usar es-ES como fallback regional automático.
- Motivo: mejorar claridad y naturalidad de la pronunciación para participantes chilenos/latinoamericanos, evitando una voz percibida como española y una velocidad excesiva.
- Se conserva: pausa fija de 250 ms entre dígitos, volumen, tono, secuencias, puntuación y lógica de evaluación.
- Límite técnico: SpeechSynthesis depende de las voces instaladas por navegador/sistema operativo; si no existe una voz latinoamericana explícita, el navegador puede usar su implementación para es-419.

## D-010 — Voz seleccionable desde Desarrolladores

- Fecha: 2026-11-03 (Chile).
- Estado: vigente.
- Decisión: no fijar una única voz de SpeechSynthesis para todos los dispositivos. Permitir que el evaluador escuche y seleccione desde Desarrolladores una de las voces en español disponibles en el navegador; conservar “Automática latina” como opción predeterminada.
- Motivo: la calidad, timbre y disponibilidad de SpeechSynthesisVoice dependen del navegador y sistema operativo, por lo que una selección automática no garantiza una voz subjetivamente adecuada.
- Persistencia: guardar únicamente el voiceURI seleccionado en localStorage del dispositivo. No contiene datos de participantes.
- Alcance: la voz elegida se usa en prueba de audio, prácticas y evaluación; no modifica velocidad 0,85, pausa 250 ms, secuencias, puntuación ni guardado de resultados.

## D-011 — Paulina (es-MX) como voz predeterminada

- Fecha: 2026-11-03 (Chile).
- Estado: vigente.
- Decisión: usar Paulina con locale es-MX como voz predeterminada para prueba de audio, prácticas y evaluación real.
- Prioridad: una voz elegida manualmente desde Desarrolladores conserva prioridad. Sin selección manual, se busca Paulina es-MX; si no está disponible, se usa otra voz es-MX y luego los fallbacks latinoamericanos definidos.
- Motivo: el usuario seleccionó Paulina es-MX como la voz preferida del proyecto tras comparar las voces disponibles.
- No cambia: velocidad 0,85, pausa de 250 ms, secuencias, puntuación, protocolo ni guardado de resultados.

## D-012 — Portal del estudio, asentimiento previo y YAP-SL como segundo módulo

- Fecha: 2026-11-09 (Chile).
- Estado: vigente.
- Decisión: presentar la aplicación como “Estudio de Actividad Física y Memoria” y ubicar Digit Span y YAP-SL como dos actividades del mismo estudio.
- Flujo aprobado: bienvenida → explicación general → asentimiento del estudiante → identificación → actividades → cierre.
- Asentimiento: ocurre antes de pedir datos y antes de mostrar los tests. Si el estudiante rechaza participar, no se solicitan datos ni se ejecuta guardado.
- YAP-SL: se usa el Google Form ya existente y se abre en una pestaña nueva. Su finalización se confirma manualmente porque el Form no entrega a esta web un callback de envío.
- Digit Span: conserva protocolo, audio, práctica, modalidades, puntuación y guardado. Los resultados resumidos no se muestran al participante real al terminar; permanecen disponibles en el flujo de prueba/desarrollo.
- Pendiente: automatizar el código de participante hacia YAP-SL cuando se disponga del identificador interno de una pregunta compatible/prellenada.
- Reemplaza parcialmente D-007 en la portada y navegación inicial; D-007 sigue vigente para la presentación interna del Digit Span.

## D-013 — Vista previa completa para desarrolladores

- Fecha: 2026-11-09 (Chile).
- Estado: vigente.
- Decisión: permitir revisar el flujo público completo desde Desarrolladores sin ingresar datos reales ni generar registros.
- Inicio: la vista previa parte en la bienvenida y utiliza datos ficticios precargados.
- Alcance: introducción, asentimiento, identificación, panel YAP-SL/Digit Span y primer test de memoria.
- Seguridad de datos: `previewFlow` nunca llama a `saveToGoogle()`.
- Rapidez: la parte de Digit Span se reduce solo dentro de la vista previa a Forward, longitud 3, un intento.
- Diferencia con Prueba rápida: la Prueba rápida sigue siendo una herramienta directa de Digit Span; la Vista previa sirve para revisar navegación y experiencia completa.

## D-014 — Generar el código antes del asentimiento

- Fecha: 2026-11-09 (Chile).
- Estado: vigente.
- Decisión: el asentimiento debe estar directamente asociado al código del participante.
- Flujo: bienvenida → explicación → identificación mínima → código → asentimiento → datos restantes → actividades.
- Identificación mínima: colegio, nivel, letra y número de lista, exclusivamente los datos usados para construir el código `COLEGIO-NIVEL+LETRA-NUMERO_LISTA`.
- Asentimiento: la pantalla muestra el código; al aceptar se registra un timestamp en la sesión y el payload de Digit Span incluye código, aceptación y fecha/hora.
- Integridad: si cambia cualquier componente del código antes de aceptar, se invalida la identificación y cualquier asentimiento previo.
- Datos restantes: nombre, género y fecha de nacimiento se solicitan solo después del “Sí, quiero participar”.
- YAP-SL: se muestra el mismo código en el panel, pero el prellenado del Form continúa pendiente hasta conocer el identificador interno del campo de código.
- Persistencia: el frontend envía el objeto `assent`; el almacenamiento en columnas separadas requiere compatibilidad del Apps Script receptor.

## D-015 — Mantener el Google Form YAP-SL embebido dentro del portal

- Fecha: 2026-11-09 (Chile).
- Estado: vigente.
- Decisión: presentar el Google Form YAP-SL dentro de una pantalla del mismo portal, en lugar de abrirlo en una pestaña nueva.
- Razón: mantener una experiencia continua bajo el mismo enlace y conservar exactamente las preguntas, alternativas y formato ya configurados en Google Forms.
- Implementación: iframe con la URL pública `viewform?embedded=true`, código de participante visible y confirmación manual “Ya envié el cuestionario”.
- Restricción: por aislamiento cross-origin no se inspecciona el contenido del Form ni se detecta automáticamente el envío.
- Pendiente: obtener `entry.*` de un enlace prellenado para autocompletar los datos que el portal ya conoce y eliminar la doble digitación.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría local de seguridad documentada sin cambios de funcionamiento; alcance y límites registrados en D-003.
- 2026-11-02 (Chile): Colegio obligatorio, Observaciones retirado de la pantalla pública y pruebas del recorrido actual; decisión D-004.
- 2026-11-02 (Chile): D-005 amplía D-004 con identificación común automática y nivel confirmado, sin integrar YAP-SL.
- 2026-11-02 (Chile): D-006 corrige los niveles permitidos de 5°/6° a 4°/5°.
- 2026-11-03 (Chile): presentación guiada y navegación documentadas; protocolo y lógica de evaluación conservados (D-007).
- 2026-11-03 (Chile): comprobación de audio previa a la batería incorporada sin afectar resultados (D-008).
- 2026-11-03 (Chile): voz latinoamericana priorizada y velocidad ajustada a 0,85 (D-009).
- 2026-11-03 (Chile): selector manual de voz disponible en Desarrolladores (D-010).
- 2026-11-03 (Chile): Paulina (es-MX) definida como voz predeterminada (D-011).
- 2026-11-09 (Chile): portal general del estudio, asentimiento previo y YAP-SL incorporados como flujo (D-012).
- 2026-11-09 (Chile): vista previa completa del flujo público disponible desde Desarrolladores (D-013).
- 2026-11-09 (Chile): código generado antes del asentimiento y asentimiento asociado al mismo identificador (D-014).
- 2026-11-09 (Chile): YAP-SL embebido dentro del mismo portal usando el Form original (D-015).
