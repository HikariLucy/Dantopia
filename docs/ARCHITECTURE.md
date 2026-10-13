# Arquitectura técnica — hipótesis inicial P0

## Objetivo
Reconstruir Dantopia en Godot sin concentrar lógica, renderizado, tienda, física y narrativa en una única clase. Las escenas representan composición visual; los recursos son datos configurables y los servicios resuelven reglas comunes.

## Separación de responsabilidades
| Capa | Responsabilidad | Evitar |
| --- | --- | --- |
| Gameplay | Movimiento, choques, daño, recolectables, jefes, eventos | Acceso directo a menús y tienda |
| Modos | Políticas de Clásico, Familiar y Arcade | Reutilizar moneda o perks entre modos |
| Content | Definiciones de poderes, enemigos, cosméticos, patrones | Constantes incrustadas en render |
| Presentación | Sprite, HUD, cámaras, sonido, VFX, escenas narrativas | Calcular economía y progreso |
| Persistencia | Guardados versionados, migraciones, defaults | Cambiar archivos desde UI |
| Plataforma | Input Map, responsive layout, audio/mobile/web | Branches divergentes de gameplay |

## Árbol objetivo (NO implementado aún)
\`\`\`
scenes/
  app/
  characters/
  obstacles/
  bosses/
  regions/{tierra,patio,casa,buenas_noches}/
  modes/{classic,family,arcade}/
  cinematics/
  ui/
scripts/
  core/
  gameplay/
  modes/
  progression/
  save/
  platform/
resources/
  dante/
  perks/
  enemies/
  cosmetics/
  balancing/
assets/
  art/
  audio/
  fonts/
tests/
\`\`\`

## Contratos preliminares
1. **Sesión:** un coordinador posee \`mode_id\`, semilla RNG, estado de ronda y lifecycle; los modos aportan reglas sin alterar el renderizador.
2. **Personaje:** controlador de Dante recibe acciones abstractas (volar/confirmar/pausar), usa física determinista definida por delta o tick; sprites y animaciones escuchan cambios de estado.
3. **Eventos:** señales para \`damage_taken\`, \`collectible_picked\`, \`boss_phase_changed\`, \`run_finished\`, \`currency_earned\`; sin acoplar a nodos globales arbitrarios.
4. **Contenido:** usar recursos tipados cuando convenga, con ID estable, parámetros y referencias artísticas; un poder nuevo no modifica cuatro regiones.
5. **Persistencia:** \`schema_version\`, IDs estables, lectura tolerante de campos nuevos, respaldo/pruebas de corrupción, escritura atómica donde la plataforma lo soporte.
6. **RNG:** fijar semilla y secuencia para simulaciones reproducibles; separar RNG visual de RNG de gameplay.
7. **Física:** medir velocidad, gravedad, límites de daño e hitboxes desde Legacy; no sustituir Pygame por físicas de Godot sin comparar sensación.
8. **Narrativa:** eventos semánticos independientes de la representación; timeline editable en \`AnimationPlayer\` y escenas específicas.
9. **Android/Web:** permisos mínimos, interacción sin teclado físico, autosave y pruebas reales; no asumir que HTML móvil equivale a APK.

## Decisiones de rendimiento
- Usar renderer de compatibilidad mientras se mide soporte web/móvil; cambiar solo por pruebas.
- Evitar interpolación y filtros que destruyan pixel art; medir calidad a distintas escalas.
- Presupuesto de partículas, atlas y caché medido, no arbitrario.

## Antipatrones bloqueados
- Un \`main.gd\` monolítico que gestione TODO.
- Duplicación de las reglas del mismo poder entre escenarios.
- Servicios globales con referencias circulares a cada escena.
- Recursos con rutas de archivos sin inventario ni licencia.
- Mezclar desarrollo del metroidvania futuro con los sistemas del port.

## Estado de decisiones
Estos son **contratos propuestos**. Solo quedan aprobados tras demostración P4/P5 y test humano. No hay todavía código de gameplay.
