# Pipeline artístico — P0 propuesta

## Principios
El arte original pertenece a Dantopia; Godot debe editar su presentación sin recrear innecesariamente lo que ya produjo Aseprite/PixelLab. El código define **qué ocurre**; los assets y escenas definen **cómo se ve**.

## Flujo propuesto
1. **Fuente**: guardar \`.ase\`/\`.aseprite\` originales por personaje, entorno, objeto, VFX y cinemática.
2. **Exportación**: PNG/spritesheet con transparencia y manifiesto de frames, tags, pivotes y duraciones cuando existan.
3. **Importación Godot**: configurar filtro nearest, escala estable, animaciones y puntos de anclaje; inspeccionar manualmente.
4. **Uso**: escena independiente, colisión validada y eventos visuales desacoplados de la lógica.
5. **QA**: revisar proporciones, clipping, legibilidad, consistencia de paleta, artefactos de escalado y rendimiento.

## Convenciones iniciales
- IDs y nombres de archivo en minúsculas, \`snake_case\`.
- Subcarpetas sugeridas: \`assets/art/dante\`, \`assets/art/bosses\`, \`assets/art/regions\`, \`assets/art/ui\`, \`assets/art/fx\`.
- Prefijos de estado claros: \`idle\`, \`fly\`, \`hurt\`, \`celebrate\`, \`sleep\`.
- No asumir que todos los sprites comparten pivote o tamaño: registrar metadata y probar.
- No iniciar Pixel Art 2.0 final de forma masiva antes de validar TIERRA.

## Inventario obligatorio
Cada asset destinado a distribuirse debe tener:
\`asset_id | categoría | autor/fuente | versión | licencia/permiso | origen editable | export usado | estado QA\`.

## Privacidad
Las fotografías personales usadas como referencia creativa **no se suben** al repositorio por defecto. No publicar imágenes que identifiquen a menores. El material derivado requiere decisión explícita sobre permisos/licencia antes de una publicación pública.

## Herramientas
- Aseprite como fuente editable cuando exista.
- Claude Code puede asistir en producción visual; Codex en tooling de exportación e importación.
- Un cambio de sprite no autoriza cambios de hitbox silenciosos.
