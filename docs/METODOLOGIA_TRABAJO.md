# Metodología de trabajo

Creación: 2026-11-02 (Chile, America/Santiago).
Última modificación: 2026-11-02 (Chile, America/Santiago).

## Sesión y documentación persistente

Una sesión puede contener exploraciones, comandos de diagnóstico, propuestas descartadas y detalles temporales que no necesitan conservarse. La memoria del chat no garantiza continuidad entre sesiones.

Deben persistir los objetivos, preferencias estables, requisitos confirmados, dudas que afecten próximas tareas, decisiones, riesgos y cambios relevantes. Al surgir información importante, decidir si debe incorporarse a CONTEXTO_USUARIO.md, CONTEXTO_PROYECTO.md, DECISIONES.md o SEGURIDAD.md. Registrar también el cambio documental en ambos registros de cambios. No persistir secretos ni datos personales reales.

## Flujo de trabajo

1. Leer AGENTS.md y la documentación; revisar el estado del repositorio y preservar trabajo existente.
2. Antes de cambios importantes, entender qué quiere lograr el usuario, por qué y cómo espera que funcione. Resolver las dudas que condicionan la implementación.
3. Delimitar el cambio, sus riesgos para información y funciones existentes, y elegir la solución más simple. Justificar cualquier framework, base de datos o tecnología adicional antes de incorporarla.
4. Implementar dentro del alcance autorizado y verificar el resultado con comprobaciones apropiadas. Usar datos ficticios, nunca datos personales reales.
5. Actualizar CAMBIOS_USUARIO.md y CAMBIOS_TECNICOS.md para todo cambio relevante de código, funcionamiento o documentación. El trabajo no se considera terminado sin ambos registros.
6. Si cambia una decisión, indicar en DECISIONES.md cuál fue reemplazada y por qué, sin borrar el registro anterior.
7. Explicar el resultado funcionalmente y comunicar pruebas, riesgos y limitaciones; realizar commits, push, merge o publicación solo dentro de la autorización de la tarea.

## Mantenimiento documental

Usar fechas de Chile (America/Santiago), conservar la fecha de creación, actualizar la última modificación y añadir un historial breve en cada documento modificado. Distinguir hechos confirmados, información reportada y pendientes de verificación.

CAMBIOS_USUARIO.md registra fecha, pedido, motivo, cambio y efecto perceptible. CAMBIOS_TECNICOS.md registra fecha, archivos, implementación, decisiones técnicas, riesgos, pruebas y limitaciones.

## Historial breve

- 2026-11-02 (Chile): creación de la configuración documental inicial solicitada.
