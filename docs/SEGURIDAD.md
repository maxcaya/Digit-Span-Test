# Seguridad y privacidad

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-02 (Chile, America/Santiago).

Prioridades: proteger información personal y resultados, prevenir pérdidas y conservar funciones existentes. Nunca incluir contraseñas, tokens, API keys ni datos personales reales en documentos, ejemplos, registros de cambios o pruebas. Usar exclusivamente datos ficticios para probar.

## Asuntos actuales pendientes de auditoría

Estos asuntos fueron comunicados por el usuario. Se documentan sin reproducir valores sensibles y sin afirmar que se realizó una auditoría técnica completa.

| Asunto | Revisión pendiente |
| --- | --- |
| Existe una contraseña de acceso a herramientas de desarrollo dentro del código entregado al navegador. | Revisar qué protege y cómo sustituir esa protección; una contraseña enviada al navegador puede ser inspeccionada. |
| Se manejan datos personales y resultados que pueden enviarse a un servicio externo. | Comprobar qué datos salen, destino, permisos de acceso, conservación y medidas de privacidad para escolares. |
| Existe una integración con Google Sheets cuyo funcionamiento real debe revisarse. | Verificar el recorrido de datos, configuración, acceso, confirmación de guardado y manejo de errores sin registrar secretos. |
| Los resultados en curso podrían perderse al cerrar o recargar la página. | Comprobar persistencia, recuperación y comportamiento ante interrupciones antes de prometer que los datos quedan guardados. |

La configuración documental inicial no corrige estos asuntos ni autoriza el envío de información real para verificarlos. Registrar los hallazgos y las decisiones futuras sin datos sensibles; cualquier solución debe seguir la metodología del proyecto.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
