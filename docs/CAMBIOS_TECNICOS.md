# Cambios técnicos

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-02 (Chile, America/Santiago).

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

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
- 2026-11-02 (Chile): auditoría local de seguridad documentada sin cambios de funcionamiento; alcance y límites registrados en D-003.
