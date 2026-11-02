# Seguridad y privacidad

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-02 (Chile, America/Santiago).

Prioridades: proteger información personal y resultados, prevenir pérdidas y conservar funciones existentes. Nunca incluir contraseñas, tokens, API keys ni datos personales reales en documentos, ejemplos, registros de cambios o pruebas. Usar exclusivamente datos ficticios para probar.

## Auditoría del código local — 2026-11-02

Se leyeron AGENTS.md, README.md, todos los documentos de docs/ e index.html completo (1074 líneas), en la rama work, commit 693be4ab0acccf1767850a5be75b03ee207c8bf2. Huella SHA-256 de index.html: f0cb7982ce50f061bd4c376040df69b3bf69c37d4f19931fada18f650c973be1. No se pudo confirmar la actualidad respecto de GitHub: la consulta remota de la revisión previa falló por conexión. Los hallazgos se refieren a esta copia local.

La revisión preliminar queda conservada al final como antecedente. Sus cuatro asuntos se comprobaron de nuevo; no se aceptaron como evidencia por sí solos. Esta auditoría cubre el código del navegador, no certifica la seguridad de Google ni de la publicación.

Gravedad: **alta** cuando puede comprometer resultados, información personal o conservación de evaluaciones; **media** cuando depende de ciertas acciones o afecta principalmente calidad y disponibilidad. La prioridad combina gravedad y consecuencias para este proyecto.

## Orden recomendado

1. Proteger el acceso y verificar quién puede enviar, leer o modificar datos en Google (S-01, S-02, S-03 y S-06). Evitar tratar los resultados actuales como resistentes a manipulación.
2. Asegurar confirmación real de guardado y recuperación ante fallos, recargas o reinicios (S-04 y S-05).
3. Controlar repeticiones de envío y separar pruebas de evaluaciones reales (S-07 y S-10).
4. Validar datos y protocolo, preparar exportaciones seguras y completas, y mejorar recuperación de audio (S-08, S-09 y S-11).

Las recomendaciones son generales y no están implementadas. Antes de escoger una solución de servidor, almacenamiento o identidad se debe delimitar su necesidad, alternativas y consecuencias con el usuario.

## Hallazgos confirmados

### S-01 — El acceso al panel no es una protección real

- **Gravedad:** alta.
- **Explicación sencilla:** la página incluye la contraseña y realiza la comparación en el propio navegador. Cualquier persona que tenga la página puede inspeccionarla o abrir el panel sin pasar por esa comparación.
- **Qué podría ocurrir:** acceder a herramientas, ver respuestas locales y cambiar condiciones del test, aunque no se conozca la contraseña de memoria.
- **Afecta:** panel, configuración, exportación y herramientas de envío de pruebas. No demuestra acceso a todas las evaluaciones de Google.
- **Evidencia:** index.html:608 y 1055–1069; showPage y loadDev (631–634 y 1015–1019) no comprueban una sesión autorizada. Se invocaron en una simulación local sin iniciar sesión.
- **Solución general:** no distribuir secretos como mecanismo de protección; si se requiere acceso restringido, verificar identidad y permisos en un servicio que el visitante no controle. Ocultar botones o cambiar la contraseña incluida no resuelve este problema. Evaluar si la contraseña expuesta fue reutilizada y reemplazarla donde corresponda, sin documentar su valor.

### S-02 — Respuestas, puntuaciones y evaluaciones se pueden fabricar en el navegador

- **Gravedad:** alta.
- **Explicación sencilla:** el mismo navegador conserva las secuencias, calcula la respuesta correcta y prepara los resultados. Las herramientas de desarrollador permiten leer y cambiar ese contenido, ejecutar funciones y alterar tiempos, datos del participante, modos y configuración. Las variables declaradas con let/const no necesitan ser propiedades de window para ser consultables desde la consola de la página.
- **Qué podría ocurrir:** conocer la respuesta antes de contestar, modificar aciertos o span, saltar etapas o preparar una evaluación que nunca se realizó. El envío contiene tanto detalle como resumen, pero el navegador no vuelve a comprobar su concordancia.
- **Afecta:** integridad de respuestas, tiempos, resultados, identidad declarada y protocolo. Requiere control del navegador o acceso a la página; no prueba alteración remota de otros equipos.
- **Evidencia:** estado y configuración (610–616), expected (653–658), submitTest (878–934), finishCurrent (935–962) y payload (984–994). Una prueba local confirmó que un resumen ficticio incongruente se incluye sin recalcular.
- **Solución general:** definir quién puede evaluar; validar sesiones, estructura, secuencias, pasos y coherencia en el receptor, recalcular resultados y conservar trazabilidad. Un servidor puede detectar incoherencias, pero no demostrar por sí solo que un escolar respondió sin ayuda en un dispositivo controlado por otra persona; mantener supervisión del evaluador.

### S-03 — Destino de envío visible y solicitudes sin autenticación propia de la aplicación

- **Gravedad:** alta, condicionada por los permisos del receptor aún desconocidos.
- **Explicación sencilla:** el destino de Google Apps Script se entrega con la página. Los envíos incluyen datos y resultados, sin credencial de evaluador ni prueba de autorización propia de la aplicación. Esa dirección permite intentar solicitudes fuera del flujo normal y no debe tratarse como un secreto que autoriza acceso.
- **Qué podría ocurrir:** si el receptor admite solicitudes anónimas sin controles, recibir evaluaciones falsas, basura o repeticiones. No se confirmó que el receptor las acepte, ni que permita leer, borrar o modificar filas existentes.
- **Afecta:** integración de escritura y calidad del conjunto almacenado.
- **Evidencia:** destino en 607, payload en 984–994 y POST en 996–1005 y 1033–1037. No hay código del receptor en los archivos del repositorio revisados. No se reproducen dirección ni identificador de despliegue.
- **Solución general:** inspeccionar Apps Script y sus permisos; exigir autorización adecuada, validar contenido y tamaño, limitar abuso y registrar operaciones. No basta con ocultar la dirección ni con confiar en controles del navegador o CORS.

### S-04 — Enviar no equivale a guardar: el aviso puede ser engañoso

- **Gravedad:** alta.
- **Explicación sencilla:** la página usa un envío cuya respuesta no puede leer (no-cors). Cuando termina la solicitud marca el envío como completado, sin comprobar que exista una fila guardada.
- **Qué podría ocurrir:** mostrar un aviso positivo pese a un rechazo o fallo del servicio. El evaluador podría empezar otra batería creyendo que está respaldada. El catch solo detecta fallos que rechazan la operación de red, no confirma el resultado de almacenamiento.
- **Afecta:** confianza en el aviso, confirmación de envío y conservación.
- **Evidencia:** 996–1005. Una respuesta simulada opaca, con status 0 y ok false, produjo saveCompleted=true y el aviso positivo. Esto reproduce la limitación del cliente, no un fallo real observado en Google.
- **Solución general:** obtener confirmación verificable del receptor vinculada al ID y al guardado; distinguir pendiente, recibido, confirmado y fallido; permitir comprobar y reintentar conservando el mismo ID.

### S-05 — Pérdida de evaluaciones al recargar, cerrar o comenzar otra batería

- **Gravedad:** alta.
- **Explicación sencilla:** respuestas y resúmenes viven en la memoria temporal de la página. No hay guardado recuperable, aviso antes de salir ni respaldo progresivo.
- **Qué podría ocurrir:** perder una evaluación parcial o terminada por cierre, recarga, fallo del dispositivo o pulsar Nueva batería, incluso mientras se envía o después de un fallo. El CSV aparece al final o en el panel; no es una recuperación automática.
- **Afecta:** continuidad, respuestas y resultados todavía no respaldados de manera verificable.
- **Evidencia:** inicialización 612–616; reinicio de listas 1042; Nueva batería llama location.reload en 1053. Lectura completa: no hay persistencia ni manejador de aviso de salida. El envío ocurre al renderizar el final (963–979), no al terminar cada respuesta.
- **Solución general:** diseñar recuperación progresiva con mínima información personal, estado de guardado visible y confirmación antes de descartar; decidir protección, caducidad y borrado de cualquier copia local, especialmente en equipos compartidos.

### S-06 — Datos identificables de escolares y copias sin control desde la aplicación

- **Gravedad:** alta.
- **Explicación sencilla:** se recoge y envía nombre completo, género, fecha de nacimiento, edad, observaciones y detalle de respuestas y tiempos. Las observaciones pueden incluir información delicada. El CSV descarga nombre y fecha de nacimiento junto con el rendimiento. La página no muestra un aviso de privacidad, instrucciones de consentimiento, plazo de conservación ni control de borrado.
- **Qué podría ocurrir:** asociar rendimientos a menores y compartirlos por error mediante la planilla, archivos descargados o un dispositivo compartido. La información permanece accesible en la página abierta; salir del panel no la borra.
- **Afecta:** privacidad de participantes y custodia de datos y exportaciones.
- **Evidencia:** formulario 385–410, participant 643–645, payload 984–994, CSV 1006–1013 y salida del panel 1063.
- **Solución general:** justificar y minimizar cada dato; preferir códigos de participante y separar identidad y resultados cuando sea viable; establecer información y autorizaciones correspondientes para menores, acceso limitado, retención, eliminación y manejo seguro de copias. Revisar permisos de Google y equipos compartidos.
- **Límite:** no se inspeccionaron consentimientos externos, permisos, propietarios, registros ni conservación en Google. La ausencia en la página no demuestra que no existan fuera de ella ni permite concluir incumplimiento legal.

### S-07 — No hay control efectivo de envíos repetidos en el cliente

- **Gravedad:** media; puede ser alta si los duplicados distorsionan el análisis.
- **Explicación sencilla:** existe un ID, pero la función de envío no comprueba si ya hay una solicitud en curso o un guardado confirmado. saveCompleted se escribe y no se usa como barrera.
- **Qué podría ocurrir:** llamadas repetidas a saveToGoogle o renderFinal generan varias solicitudes con el mismo ID; al recomenzar se genera otro. No se puede saber si el receptor deduplica. El recorrido normal de pantalla no implica por sí solo que cada evaluación se envíe dos veces.
- **Afecta:** recuento de participantes, filas y análisis de resultados.
- **Evidencia:** 981–1005 y 1042. Dos llamadas locales consecutivas produjeron dos solicitudes simuladas pese a saveCompleted=true.
- **Solución general:** impedir concurrencia accidental y hacer que el receptor reconozca un ID ya procesado y confirme el mismo registro sin crear otro; conservar el ID para reintentos y definir cómo distinguir una nueva evaluación válida.

### S-08 — Validación insuficiente de participante y configuración

- **Gravedad:** media.
- **Explicación sencilla:** solo se exige que nombre, género y fecha tengan contenido. No se comprueba una edad razonable, una fecha pasada, tamaños máximos ni valores admitidos ante manipulación. Los límites dibujados en los campos de configuración no se verifican al guardar.
- **Qué podría ocurrir:** edades negativas, datos equivocados o excesivos, longitudes o intentos inválidos y evaluaciones poco comparables o bloqueadas. El protocolo se lee al enviar y no queda congelado al comenzar, por lo que una modificación puede cambiar lo que se declara de una evaluación ya realizada.
- **Afecta:** datos del participante, protocolo, cálculo de edad y calidad de resultados.
- **Evidencia:** 635–650, 984–994 y 1020–1025. Simulación: se aceptó una fecha futura, longitud inicial negativa y cero intentos. Las respuestas sí se limitan a dígitos y longitud en el uso normal (659–738, 808–887); esos controles no autentican el resultado y se pueden evitar desde la consola.
- **Solución general:** reglas explícitas de fechas, valores, tamaños y relaciones entre parámetros, comprobadas en cliente y receptor; capturar el protocolo al inicio y validar concordancia con cada intento. Decidir con el usuario el rango de participantes antes de imponerlo.

### S-09 — CSV con fórmulas y respaldo incompleto

- **Gravedad:** media.
- **Explicación sencilla:** las comillas y separadores se escapan, pero una celda que comienza con un signo de fórmula puede interpretarse como una fórmula al abrirla en una hoja de cálculo. Además, el CSV no contiene ID de evaluación, observaciones, configuración ni resúmenes.
- **Qué podría ocurrir:** un nombre preparado puede convertirse en una fórmula al importar, según el programa y sus opciones; una exportación puede perder contexto y no permitir reconstruir o conciliar todo lo enviado. Las secuencias con cero inicial pueden convertirse en números y perder ese cero según la importación.
- **Afecta:** seguridad y fidelidad del archivo exportado. No se demostró ejecución de comandos ni extracción de datos en un programa real.
- **Evidencia:** 1006–1013. Una entrada ficticia con fórmula aritmética conservó su prefijo al exportar en simulación. Las comillas CSV no neutralizan por sí solas fórmulas.
- **Solución general:** exportar texto con tratamiento seguro de prefijos de fórmula y verificarlo con el programa de destino; conservar dígitos como texto; acordar un respaldo completo, con ID y protocolo y sin información personal innecesaria. Revisar también cómo el receptor escribe texto en Sheets: no se confirmó inyección de fórmulas allí sin su código.

### S-10 — Herramientas de prueba pueden contaminar o cambiar evaluaciones posteriores

- **Gravedad:** media.
- **Explicación sencilla:** Probar Google Sheets envía un registro de prueba al mismo destino. Prueba rápida cambia modos y parámetros, rellena datos ficticios si faltan y no restaura automáticamente la configuración al terminar.
- **Qué podría ocurrir:** mezclar pruebas con registros reales o iniciar después una batería reducida creyendo que usa la configuración habitual. La prueba rápida no se envía en su primera finalización, pero renderFinal cambia quick a false; una nueva invocación puede enviarla. Tampoco reinicia evaluationId ni saveCompleted al iniciar la prueba rápida.
- **Afecta:** limpieza de la planilla, configuración y separación entre simulación y evaluación real.
- **Evidencia:** 974–978, 1033–1037, 1042 y 1068. El botón de prueba de audio también pasa a speakSequence un objeto sin style (1067 frente a 759): puede fallar por programación y confundirse con un fallo de audio.
- **Solución general:** separar un entorno o destino de pruebas, identificar y filtrar simulaciones, impedir su envío como evaluación y restaurar o confirmar explícitamente parámetros y participante antes de evaluar.

### S-11 — Fallos de audio pueden dejar la evaluación detenida sin recuperación guiada

- **Gravedad:** media.
- **Explicación sencilla:** los campos se desactivan antes del audio; si este falla se muestra una alerta y la función termina sin ofrecer un botón para recuperar ese intento. No hay un límite de espera si el motor de voz no informa fin o error.
- **Qué podría ocurrir:** necesitar reiniciar y perder respuestas previas, o registrar condiciones diferentes entre dispositivos. El tiempo de respuesta se toma del reloj local de ejecución del navegador y puede alterarse; no acredita por sí solo tiempos auténticos.
- **Afecta:** disponibilidad, conservación y comparabilidad del protocolo y tiempos.
- **Evidencia:** 741–767, 789–807 y 866–876.
- **Solución general:** comprobación previa de audio, tratamiento de interrupciones, tiempo máximo de espera y recuperación que conserve el progreso y documente incidentes; acordar condiciones de aplicación consistentes. No asumir equivalencia académica con WISC-V.

## Alcance adicional y riesgos no demostrados

- No se encontraron credenciales de cuenta de Google, API keys, tokens OAuth, claves privadas ni un identificador explícito de archivo de Sheets/Drive en index.html. Sí hay una contraseña del panel y una URL de despliegue de Apps Script. Su exposición no prueba que toda la cuenta o el Drive sean públicos.
- Desde esta página se observan solicitudes POST de envío. No hay código de consulta de planillas ni de borrado de evaluaciones remotas. No se puede afirmar que un visitante lea o modifique todos los registros sin revisar el receptor y sus permisos. La consola sí permite consultar y alterar la evaluación de su propia página.
- La dirección de envío usa HTTPS. No hay bibliotecas externas ni llamadas explícitas adicionales de red en index.html. El motor de voz depende del dispositivo y no se fuerza una voz local; no se comprobó si usa un servicio remoto. Solo se pasan dígitos a la síntesis, no nombres ni observaciones.
- Hay inserciones con innerHTML (971, 1001, 1030), pero sus valores en el flujo normal provienen de constantes, estado generado o ID interno. No se confirmó una vía desde nombre u observaciones hacia esos puntos. Cambiar el estado con la consola ya requiere controlar esa página; no se presenta como una vulnerabilidad remota adicional demostrada.
- No se evaluaron cabeceras de seguridad del alojamiento, disponibilidad, cuotas de Google, acceso público real, validación o fórmulas del receptor, auditoría de accesos, copias de seguridad o eliminación. Requieren código/configuración del servicio y revisión autorizada; no se enviaron solicitudes a Google durante esta auditoría.

## Comprobaciones y límites

Además de lectura completa se ejecutaron ocho comprobaciones locales con Node.js y un navegador simulado mínimo: acceso directo al panel, fecha futura aceptada, configuración fuera de rango, resumen alterado incluido en payload, falso positivo ante respuesta opaca, dos solicitudes para el mismo estado, prefijo de fórmula conservado en CSV y normalización de dígitos. Red, descargas y mensajes se simularon; únicamente se usaron datos ficticios. No equivalen a pruebas en navegadores reales, en una hoja de cálculo ni en Google Apps Script.

No se modificó index.html ni se implementaron soluciones. Los hallazgos siguen abiertos; documentarlos no los resuelve. La revisión no certifica seguridad integral ni validez académica.

## Antecedente: asuntos comunicados antes de esta auditoría

La configuración documental inicial registró cuatro pendientes sin validación técnica: contraseña incluida en el navegador; datos personales y envío externo; integración con Google Sheets; posible pérdida al cerrar o recargar. Esta auditoría confirma los aspectos visibles en el código mediante S-01 a S-06. Los permisos y funcionamiento interno del receptor siguen pendientes de revisión. Se conserva este antecedente sin reproducir valores sensibles.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría del código local completo; once hallazgos, evidencias, prioridades, límites y comprobaciones sin red; sin correcciones de la aplicación.
