# Contribuir a Dantopia

## Gobernanza
El alcance, las reglas de juego, la dirección artística y la aceptación final requieren revisión humana. Un resultado de IA, una suite verde o la compilación correcta **no equivalen** a aprobación de gameplay ni arte.

## Flujo Git
1. Crear un issue o vincular el cambio a una fase y criterio de aceptación.
2. Abrir rama \`docs/*\`, \`feat/*\`, \`fix/*\`, \`test/*\` o \`chore/*\`; preferir un worktree independiente por agente.
3. Hacer cambios pequeños, sin introducir contenido de fases posteriores por conveniencia.
4. Documentar alcance, alternativas, posibles regresiones, prueba ejecutada y prueba pendiente.
5. Solicitar revisión humana antes del merge a \`main\`. No hacer merge, tag o release automático sin autorización.
6. Conservar datos de validación y origen de assets. Ningún cambio debe romper Clásico, Familiar o Arcade para mejorar solo uno.

## Roles orientativos
- **Codex:** arquitectura, escenas/sistemas GDScript, persistencia, QA y tooling.
- **Claude Code:** dirección y producción de arte, rig/sprites, animaciones, puesta en escena y pipeline gráfico.
- **Responsable del proyecto:** prioridades, diseño, decisiones de alcance, HUMAN PASS, integración y publicación.

No dar por aprobado material producido por otro agente sin validarlo. Evitar ediciones concurrentes sobre los mismos archivos.

## Validación
- Revisión de archivos cambiados y \`git diff\`.
- Importación en Godot sin errores y ejecución manual de la escena involucrada.
- Tests y smoke headless cuando existan y estén configurados.
- Comparación con Legacy cuando corresponda.
- Prueba visual, de accesibilidad y de usabilidad realizada por una persona.
- Si no se pudo probar en Android o Web, reportar **NO PROBADO**.

## Privacidad y licencias
No subir fotos personales/familiares, ROMs, material licenciado de terceros sin permiso, claves de firma Android, credenciales ni logs sensibles.
Toda imagen/audio/fuente debe contar con autor, procedencia, licencia/permisos y fecha en un registro antes de distribución.
La ausencia de archivo LICENSE es deliberada mientras se define el modelo de distribución; un repositorio privado no concede autorización a terceros.
