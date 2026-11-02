# Contexto del proyecto

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-02 (Chile, America/Santiago).

El seminario analiza la relación entre actividad física y memoria de trabajo en escolares. La actividad física se evalúa mediante YAP-SL. Digit Span se utiliza para evaluar memoria numérica/memoria de trabajo.

Participantes previstos: escolares de aproximadamente 10 a 12 años, de 5.º y 6.º básico. Actualmente la aplicación es manejada por un evaluador; el objetivo aprobado es una única aplicación pública accesible por enlace, sin cuentas ni inicio de sesión, que también permita uso individual en el futuro.

## Identificación y colegios del seminario

La pantalla inicial conserva nombre completo, género y fecha de nacimiento, y exige colegio, nivel (5° o 6°), letra de curso y número de lista. Observaciones no se solicita al participante público; se conserva compatibilidad interna mediante un valor vacío.

Los únicos colegios admitidos son:

- Santiago College.
- Lincoln International Academy Chicureo.
- Craighouse School.

Los desplegables comienzan con «Selecciona tu colegio» y «Selecciona tu nivel», sin valor válido. Letra es texto libre obligatorio: se recortan espacios exteriores, se convierte a mayúscula y se comprueba exactamente una letra; números, símbolos y varias letras se rechazan. Número de lista elimina espacios, acepta solo dígitos y debe representar un entero entre 1 y 99; rechaza cero, negativos, decimales y notación exponencial.

Después de validar se genera internamente COLEGIO-NIVEL+LETRA-NUMERO_LISTA: SC para Santiago College, LIA para Lincoln International Academy Chicureo y CHS para Craighouse School; nivel sin °, letra mayúscula y número con tres dígitos. Ejemplos: SC-5B-012, LIA-6A-007 y CHS-5C-021. No hay campo para escribir, copiar ni consultar el código en la pantalla inicial.

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

Nivel educacional (5° y 6°) ya es un requisito confirmado para identificar al participante. Mano dominante y horas de sueño siguen sin confirmación; no incorporarlas por suposición.

No usar datos personales reales para pruebas. Los hallazgos de almacenamiento, envío y recuperación están documentados en SEGURIDAD.md y siguen pendientes de solución; esa auditoría conserva la referencia al código anterior a este cambio.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): requisito aprobado de una única aplicación pública; tres colegios documentados, Colegio obligatorio y Observaciones retirado de la pantalla inicial.
- 2026-11-02 (Chile): nivel, letra y número de lista obligatorios; código interno común previsto para Digit Span y YAP-SL, con ID independiente por evaluación y sin integrar todavía los instrumentos.
