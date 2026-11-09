# Contexto del proyecto

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-03 (Chile, America/Santiago).

El seminario analiza la relación entre actividad física y memoria de trabajo en escolares. La actividad física se evalúa mediante YAP-SL. Digit Span se utiliza para evaluar memoria numérica/memoria de trabajo.

Participantes previstos: escolares de aproximadamente 10 a 12 años, de 4.º y 5.º básico. Actualmente la aplicación es manejada por un evaluador; el objetivo aprobado es una única aplicación pública accesible por enlace, sin cuentas ni inicio de sesión, que también permita uso individual en el futuro.

## Identificación y colegios del seminario

La pantalla de identificación conserva nombre completo, género y fecha de nacimiento, y exige colegio, nivel (4° o 5°), letra de curso y número de lista. Observaciones no se solicita al participante público; se conserva compatibilidad interna mediante un valor vacío.

Los únicos colegios admitidos son:

- Santiago College.
- Lincoln International Academy Chicureo.
- Craighouse School.

Los desplegables comienzan con «Selecciona tu colegio» y «Selecciona tu nivel», sin valor válido. Letra es texto libre obligatorio: se recortan espacios exteriores, se convierte a mayúscula y se comprueba exactamente una letra; números, símbolos y varias letras se rechazan. Número de lista elimina espacios, acepta solo dígitos y debe representar un entero entre 1 y 99; rechaza cero, negativos, decimales y notación exponencial.

Después de validar se genera internamente COLEGIO-NIVEL+LETRA-NUMERO_LISTA: SC para Santiago College, LIA para Lincoln International Academy Chicureo y CHS para Craighouse School; nivel sin °, letra mayúscula y número con tres dígitos. Ejemplos: SC-4B-012, LIA-5A-007 y CHS-4C-021. No hay campo para escribir, copiar ni consultar el código en la pantalla de identificación.

Los cuatro valores y el código quedan fijados al comenzar la batería, aparecen en el resultado final, se incorporan a cada fila del CSV y al objeto participant del envío actual (school, grade, class_letter, list_number y participant_code). evaluation_id continúa siendo un identificador independiente para cada evaluación; el código de participante puede repetirse al evaluar de nuevo a la misma persona.

El código será el identificador común entre Digit Span y YAP-SL para cruzar sus resultados. Todavía no se integra con Google Forms ni se añade un botón de YAP-SL. Se deben revisar sus preguntas, columnas, automatizaciones y permisos antes de definir esa integración. El código no acredita identidad ni pertenencia al colegio; requiere datos consistentes y podría repetirse entre años escolares. Antes de cruzar bases de diferentes períodos se deberá acordar un contexto común de estudio/año.

El cambio actual se limita al navegador. No incorpora validación del servidor, recuperación de evaluaciones, confirmación de guardado, cambios del receptor de Google ni despliegue en Vercel. Esas mejoras siguen pendientes. La inclusión de estos campos en el envío no demuestra que el receptor existente los guarde en columnas.

## Objetivo de despliegue aprobado y alcance actual

Se mantiene una sola aplicación pública, sin separación entre modo público y modo estudio ni invitaciones. El objetivo es identificación, selección de colegio, evaluación y guardado seguro y verificable, usando Vercel como destino y manteniendo una estructura sencilla y Google Sheets mientras sea adecuado. El código actual todavía no implementa ese plan de seguridad y despliegue.

Registra secuencias, respuestas, aciertos y errores, longitud alcanzada, tiempo y span máximo. Las condiciones académicas indicadas a continuación siguen pendientes.

Modalidades actuales:

- Mismo orden.
- Orden inverso.
- Menor a mayor.
- Mayor a menor.

## Referencia y confirmaciones pendientes

La referencia académica es Digit Span / Dígitos del WISC-V. No todas las modalidades actuales pueden asumirse automáticamente como parte estándar del instrumento. Siguen pendientes la selección final de modalidades, la correspondencia de menor a mayor con secuenciación y la justificación de mayor a menor. No afirmar equivalencia, validez ni puntuaciones normativas sin la revisión académica correspondiente.

Nivel educacional (4° y 5°) ya es un requisito confirmado para identificar al participante. Mano dominante y horas de sueño siguen sin confirmación; no incorporarlas por suposición.

No usar datos personales reales para pruebas. Los hallazgos de almacenamiento, envío y recuperación están documentados en SEGURIDAD.md y siguen pendientes de solución; esa auditoría conserva la referencia al código anterior a este cambio.

## Presentación guiada — 2026-11-03

La web abre con una bienvenida (Digit Span Test / Evaluación de memoria de trabajo) antes de solicitar identificación. El recorrido es bienvenida → datos del participante → instrucciones generales → prueba de audio → instrucciones específicas con ejemplo y número de sección → práctica → prueba real → modalidad completada → instrucciones de la siguiente modalidad → resultado final.

La presentación conserva la paleta actual y usa ejemplos separados en Escuchas/Respondes, apilados en teléfono. Antes de la primera modalidad se realiza una comprobación de audio repetible con la misma configuración de voz del test; no cuenta como resultado ni se guarda. La síntesis prioriza voces de español latinoamericano disponibles en el dispositivo, evita es-ES como fallback automático y usa velocidad 0,85 con una pausa fija de 250 ms entre dígitos. La voz predeterminada del proyecto es Paulina (es-MX) cuando está disponible. Desde Desarrolladores se puede elegir y previsualizar manualmente cualquiera de las voces en español que el navegador exponga; la elección queda guardada localmente en ese dispositivo y prevalece sobre Paulina. Si Paulina no existe en el sistema, se usa otra voz es-MX y luego una alternativa latinoamericana. Desarrolladores está disponible desde bienvenida e identificación; su Prueba rápida sigue sin exigir datos ni enviar a Google Sheets. Este cambio modifica presentación y navegación, pero no el protocolo ni la lógica de evaluación, código de participante, resultados, CSV o integración de guardado. Decisión D-007.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): requisito aprobado de una única aplicación pública; tres colegios documentados, Colegio obligatorio y Observaciones retirado de la pantalla inicial.
- 2026-11-02 (Chile): nivel, letra y número de lista obligatorios; código interno común previsto para Digit Span y YAP-SL, con ID independiente por evaluación y sin integrar todavía los instrumentos.
- 2026-11-03 (Chile): presentación guiada y navegación documentadas; protocolo y lógica de evaluación conservados (D-007).


## Portal general del estudio — 2026-11-09

La aplicación deja de ser una portada exclusiva de Digit Span y pasa a presentarse como “Estudio de Actividad Física y Memoria”. El flujo público vigente es: bienvenida → explicación del estudio → asentimiento → identificación → panel de actividades.

El asentimiento del estudiante ocurre antes de solicitar nombre, fecha de nacimiento, colegio u otros datos. Si el estudiante selecciona “No quiero participar”, se muestra una pantalla de cierre y no se ejecuta ningún guardado. El texto está redactado en lenguaje simple para 4° y 5° básico; su versión definitiva debe mantenerse alineada con el protocolo ético aprobado y no sustituye el consentimiento del apoderado cuando corresponda.

Después de aceptar y completar la identificación, “Tus actividades” presenta dos módulos: (1) cuestionario de actividad física YAP-SL mediante el Google Form proporcionado y (2) actividad de memoria mediante el Digit Span existente. El Form se abre en una pestaña nueva para que el participante pueda volver al portal. Como todavía no existe integración de callbacks ni se conoce el entry id del código de participante, la web no puede comprobar por sí sola el envío del Form ni prellenar el código; el participante confirma manualmente su finalización.

Digit Span conserva sus instrucciones, prueba de audio, prácticas, cuatro modalidades, CONFIG, puntuación y guardado. Al finalizar una evaluación real, sus puntajes no se muestran al estudiante; el módulo se marca como completado y se vuelve al panel de actividades. La prueba rápida de Desarrolladores conserva la salida técnica.


## Vista previa de desarrollador — 2026-11-09

El panel de Desarrolladores incluye una “Vista previa desde el inicio” para revisar la experiencia pública sin ingresar datos reales. Este modo comienza en la bienvenida, precarga una identidad ficticia válida y permite recorrer explicación, asentimiento, identificación, panel de actividades, enlace YAP-SL e inicio de Digit Span. Para acelerar la revisión, Digit Span se limita a Forward, longitud 3, un intento. El modo se identifica visualmente y no ejecuta guardado de resultados en Google Sheets. Es distinto de la Prueba rápida de Digit Span, que continúa saltando directamente a la prueba.


## Código y asentimiento — 2026-11-09

El código de participante debe existir antes del asentimiento y ser el identificador común del estudio. El recorrido pasa a ser bienvenida → explicación → identificación mínima (colegio, nivel, letra, número de lista) → generación de código → asentimiento asociado a ese código → datos personales restantes → YAP-SL/Digit Span.

El asentimiento muestra el código y, al aceptar, la aplicación conserva `assentGiven=true` y un timestamp `assentAt`. Nombre, género y fecha de nacimiento se solicitan después. El mismo código se muestra en el panel de actividades para mantener la correspondencia con YAP-SL y Digit Span. El payload de Digit Span contiene un objeto `assent` con código y fecha/hora; como el Apps Script receptor no forma parte del repositorio, debe verificarse/actualizarse aparte si se requiere almacenar esos campos en columnas propias de Google Sheets.
