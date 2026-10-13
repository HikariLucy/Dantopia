# Dantopia — Resumen ejecutivo del roadmap vivo

**Corte:** 13 de octubre de 2026 · **Estado:** documento de consulta, no registro independiente de tareas.

> **Fuente única de verdad:** [ROADMAP.md, sección K](../ROADMAP.md#k-tablero-vivo-canonico--fuente-unica-de-tareas). Solo allí se modifican casillas, estados, identificadores, decisiones, dependencias y subhitos. Si este resumen diverge del roadmap, manda el roadmap.

## Visión

Dantopia es un videojuego familiar de pixel art protagonizado por Dante. El producto debe resultar atractivo por su personaje, la calidad visual y sonora, la rejugabilidad, la colección y la claridad de sus sistemas. La estrategia prioriza **escritorio (Linux/Windows)** y después **APK Android instalable directamente para familiares**. El desarrollo web está pausado.

Existen **tres modos deliberadamente diferentes**:

| Modo | Promesa de diseño | Límites |
| --- | --- | --- |
| **Clásico** | Endless de habilidad, récord, ritmo y desbloqueos cosméticos | Sin perks roguelite |
| **Familiar** | Endless accesible, relajado y positivo; corazones, recuperación y cosméticos propios | No debe ser únicamente «Clásico más fácil» |
| **Arcade** | Expedición por cuatro regiones, bosses, poderes/builds, hub y cierre familiar | El final ilustrado pertenece solo a Arcade |

## Estado verificado al 13-10-2026

**La base técnica está respaldada, pero todavía no integrada.**

- **F3.4 / Claude:** rama feat/f3.4-claude-design-pass, commit [f4dd697](https://github.com/HikariLucy/FlappyDan/commit/f4dd697d76a3a712430ba7ac63f36ac121cd54c8). Incluye animaciones CAMA 3.0, entorno BUENAS NOCHES, Clásico/Familiar sin jefe y final ilustrado en Arcade. Reporte: **2317 pruebas aprobadas**, sin fallos, antes de la consolidación. **HUMAN PASS integral pendiente**.
- **Roguelite M0–B0 / Codex:** rama feat/roguelite-foundation-m0, commit [6d2ddbb](https://github.com/HikariLucy/FlappyDan/commit/6d2ddbbeac43b983aeaea2eeb0101892db7aade1). Arquitectura del hub, progresión, reglas de economía/guardado y preflight de B1 en módulos aislados. Reporte: **205 pruebas y 560 subtests aprobados**. El hub real y el save owner **no están conectados a Game**.
- Ambas ramas parten de 5c19d05. **No hay suite combinada ni integración aprobada**.
- La secuencia de ocho ilustraciones tiene aprobación artística, pero **los PNG originales siguen siendo privados y excluidos de Git**.
- El proyecto Godot tiene documentación y planificación inicial; **el port de gameplay no ha comenzado**.

## Los cuatro focos de producto que más queremos mejorar

**Modos y diversión.** Hacer que Familiar sea acogedor y rejugable sin simplemente bajar la dificultad; dar a Clásico el atractivo de superar récords; mantener Arcade como la aventura narrada. Exigir playtests, no solo tests unitarios. **IDs MOD, VAR y F35.**

**Economía, fruta y poderes.** Las monedas deben acercar a compras deseables; la fruta debe tener un propósito claro y un feedback distinto. Antes de añadir variedades y nuevas habilidades hay que auditar los comportamientos existentes para no inventar efectos, duplicar monederos ni romper builds. **IDs ECO, FRU, POW y ROG.**

**Dante coleccionable.** La referencia visual aprobada y Dino existe en tres poses; falta validar un sistema completo de skins para los estados reales de juego, sus costes y el selector. **IDs SKIN.**

**HUD/UI con identidad.** Reducir ruido y cajas, establecer una gramática visual única y separar prioridades por modo. Las pantallas deben funcionar en escritorio y futuro móvil. **IDs UI.**

## Próximo camino recomendado

1. **Respaldo y privacidad (GOV-05–GOV-08):** auditar el commit grande F3.4, respaldar originales privados y sincronizar ambas ramas en casa.
2. **Integración (INT-01–INT-06):** rama controlada con F3.4 y los commits Roguelite, suite conjunta, smoke manual y revisión del final.
3. **B1 / persistencia y hub real (ROG-03–ROG-08):** resolver migración de saves, fallos de escritura, monederos y reconciliación antes de activar compras.
4. **Diseño y experiencia en paralelo (MOD, ECO, POW, SKIN, UI):** auditar primero; realizar prototipos acotados y evaluarlos con personas.
5. **Cierre Legacy (F34, F35, VAR, QA):** juego completo, nivel artístico consistente, diversión, accesibilidad y pruebas de regresión.
6. **Ruta de entrega (AND, GOD):** decidir si conviene empaquetado Pygame temporal o Godot; aprender Godot con laboratorio, vertical slice y después reconstruir el juego, con Android como objetivo familiar.

**No iniciar B1** sin integración y preflight actualizados. **No empezar el port masivo a Godot** antes de congelar la experiencia de referencia y validar el vertical slice. El avance puede retroceder si se descubre una regresión: reabrir el hito y añadir un subhito con evidencia.

## Cómo usarlo cada día

- Para cada decisión nueva: buscar un ID en [ROADMAP.md](../ROADMAP.md), añadir subhito con sufijo numérico si hace falta y documentar dependencia, prioridad y aceptación.
- Para cada sesión Codex/Claude: actualizar casillas y pruebas efectivamente realizadas; registrar SHA y observaciones del playtest.
- Para cada hito visual o de balance: «test verde» no equivale a «HUMAN PASS».
- No gestionar listas alternativas de tareas en un HTML, chat, README o issue. Pueden mostrar un resumen o enlazar IDs, pero la edición oficial permanece en ROADMAP.md.

**Consulta directa:** [Abrir y editar el roadmap canónico](../ROADMAP.md#k-tablero-vivo-canonico--fuente-unica-de-tareas).
