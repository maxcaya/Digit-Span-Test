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
- Estado: reemplazada parcialmente por D-006 en niveles permitidos y requisito de identificación para Prueba rápida; se mantienen el formato del código y las validaciones del participante normal.
- Decisión: ampliar identificación obligatoria con nivel 5°/6°, letra libre normalizada a mayúscula (una sola letra, sin espacios exteriores) y número de lista entero 1–99, además del colegio. Generar automáticamente SC/LIA/CHS-NIVEL+LETRA-NUMERO de tres dígitos, sin campo manual ni visualización en la pantalla inicial. Conservar los demás datos actuales.
- Motivo: usar posteriormente el mismo código para relacionar Digit Span y YAP-SL sin pedir que el participante lo copie o escriba.
- Alcance implementado: validación en navegador, identificación fijada al comenzar, resumen final, CSV y contenido enviado mediante la integración actual. evaluation_id se mantiene separado para cada evaluación. La prueba rápida de desarrollo usa identificación válida propia y reinicia su ID, conservando su comportamiento de no enviar al finalizar.
- Límites: sin integración con YAP-SL ni revisión del formulario, receptor nuevo, servidor, recuperación, Vercel, commit, push ni publicación. No se resuelven por este cambio falsificación, persistencia ni confirmación remota de guardado. Los códigos pueden repetirse entre años y no prueban identidad; el contexto común de estudio/año se definirá antes de cruzar períodos distintos.
- Decisión reemplazada: amplía y reemplaza parcialmente D-004, que limitaba el cambio a Colegio. Se mantienen aplicación única, ausencia de cuentas, retiro de Observaciones y demás límites. La restricción de D-003 corresponde a la tarea histórica de auditoría.

## D-006 — Presentación guiada y separación de textos de evaluación

- Fecha: 2026-11-03 (Chile).
- Estado: vigente.
- Decisión: añadir bienvenida antes de identificación, instrucciones generales y una introducción independiente por modalidad con explicación, ejemplo e indicador de sección; conservar paleta y diseño sobrio responsive. Mantener el paso existente de preparación entre práctica y prueba real.
- Motivo: experiencia más guiada, formal, académica y fácil de comprender, sin modificar el protocolo ni la lógica de evaluación.
- Implementación: MODE_PRESENTATION separa títulos, instrucciones y ejemplos de las nuevas introducciones de INFO, que conserva las etiquetas y títulos usados por pruebas y resultados. Puntuación, secuencias, prácticas, audio, intentos, criterios de finalización, payload, CSV y guardado real se conservan.
- Ajustes expresamente solicitados: Nivel admite únicamente 4°/5°; Prueba rápida no requiere identificación y mantiene su marca de simulación en el final para impedir envíos. Acceso a Desarrolladores disponible en bienvenida e identificación, sin alterar su mecanismo de acceso ni las demás herramientas.
- Decisión reemplazada: reemplaza parcialmente D-005 en la lista 5°/6° (ahora 4°/5°) y en exigir identificación válida para Prueba rápida. No cambia el formato del código de participante ni las validaciones normales; conserva D-004 en aplicación única y Observaciones fuera de pantalla pública. Historial anterior conservado.
- Alcance Git: nueva rama presentacion-guiada-digit-span desde 589bb4a5b516034a7f1ee4207441dca73d6c5ae1; commit y push autorizados por esta solicitud; sin merge a main ni despliegue manual. Los asuntos de seguridad y la integración con YAP-SL continúan pendientes.

## Pendientes sin decisión definitiva

Selección final de modalidades; correspondencia de menor a mayor con secuenciación; justificación de mayor a menor; incorporación eventual de mano dominante y horas de sueño. El nivel vigente es 4°/5° según D-006, reemplazando 5°/6° de D-005; integración con YAP-SL y contexto de estudio/año siguen pendientes. Consultar CONTEXTO_PROYECTO.md. Los asuntos de SEGURIDAD.md requieren auditoría y no se consideran resueltos.

## Cómo reemplazar una decisión

Conservar la entrada anterior marcándola como reemplazada, enlazar la nueva decisión e indicar fecha y motivo. La nueva entrada debe identificar expresamente qué decisión reemplaza y por qué. Registrar la actualización en ambos registros de cambios.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría local de seguridad documentada sin cambios de funcionamiento; alcance y límites registrados en D-003.
- 2026-11-02 (Chile): Colegio obligatorio, Observaciones retirado de la pantalla pública y pruebas del recorrido actual; decisión D-004.
- 2026-11-02 (Chile): D-005 amplía D-004 con identificación común automática y nivel confirmado, sin integrar YAP-SL.
- 2026-11-03 (Chile): D-006 registra presentación guiada y reemplazo parcial de D-005 en niveles y Prueba rápida.
