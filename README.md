# Dantopia

**Dantopia** es una aventura 2D de pixel art protagonizada por Dante Pixel. Este repositorio contiene la **reconstrucción en Godot** del videojuego original desarrollado con Python/Pygame.

> **Estado (2026-10-13): P0 — Fundación en preparación.** El port completo **no ha comenzado**. La aventura original sigue desarrollándose en [HikariLucy/FlappyDan](https://github.com/HikariLucy/FlappyDan). No confundir documentación o prototipos con funcionalidades terminadas.

## Qué queremos construir

Tres modos diferentes, con las reglas y economías separadas:

| Modo | Experiencia |
| --- | --- |
| **Clásico** | Vuelo endless; puntuación, récords y cosméticos. Sin perks roguelite. |
| **Familiar** | Endless accesible; corazones y recuperación, protección, tienda propia y progresión amable. |
| **Arcade** | Expedición roguelite: TIERRA → PATIO → CASA → BUENAS NOCHES, jefes, mejoras y desenlace familiar. |

La escena final de Arcade conduce a Dante a la cama; **un eventual metroidvania de sueños sería otro videojuego independiente**, fuera del alcance de esta migración.

## Decisión técnica inicial

- **Motor de referencia:** Godot 4.7.2 stable (validar que la instalación local y los export templates coincidan).
- **Lenguaje:** GDScript; priorizar código tipado y recursos configurables.
- **Diseño:** escenas reutilizables, composición, eventos y separación de gameplay/presentación/datos.
- **Objetivos:** Linux y Windows primero; Android y Web mediante pruebas de compatibilidad.
- **Arte:** Aseprite, spritesheets, PNG originales y assets con procedencia documentada.

## Principio de migración

1. Terminar y validar la versión Pygame: F3.4, F3.5, F4 y QA Familiar.
2. Congelar una versión de referencia; registrar reglas, assets y pruebas.
3. Aprender Godot con prototipos aislados y una primera escena de laboratorio.
4. Aprobar un vertical slice jugable de TIERRA antes de portar el juego completo.
5. Solo entonces reconstruir los modos, regiones, jefes, narrativa y distribución.

**No copiar el renderer de Pygame tal cual, no portar errores históricos y no empezar el remaster artístico completo antes de tener una base validada.**

## Documentación

- [ROADMAP.md](ROADMAP.md) — plan **exclusivo de migración Godot P0–P17**, hitos y criterios de aceptación.
- [GAME_DESIGN.md](docs/GAME_DESIGN.md) — visión y reglas de los tres modos.
- [ARCHITECTURE.md](docs/ARCHITECTURE.md) — diseño técnico inicial.
- [MIGRATION_GATES.md](docs/MIGRATION_GATES.md) — puertas formales para migrar.
- [ART_PIPELINE.md](docs/ART_PIPELINE.md) — inventario y producción de sprites.
- [P3_GODOT_LAB.md](docs/P3_GODOT_LAB.md) — primeros ejercicios para aprender Godot.
- [FUTURO_METROIDVANIA.md](docs/FUTURO_METROIDVANIA.md) — semilla narrativa, no un compromiso de desarrollo.
- [CONTRIBUTING.md](CONTRIBUTING.md) — normas de cambios, IA y revisión humana.

## Abrir el proyecto

Cuando la fundación técnica quede incorporada, clonar este repositorio y abrir el directorio que contiene `project.godot` desde el **Godot Project Manager**. La escena de laboratorio es un marcador de posición y **no representa gameplay final**.

## Gobernanza

- No hay aprobación automática de arte, UX ni balance.
- Codex: arquitectura, gameplay, automatización y tests; Claude Code: arte, animación y presentación, siempre con supervisión humana.
- Cambios aislados por rama, revisiones y evidencia reproducible antes del merge.
- Material personal o fotografías familiares **no deben subirse** sin revisión explícita de privacidad y derechos.
- No se publica el código ni se asigna una licencia abierta por defecto: **el repositorio es privado**.

**El desarrollo y el tablero maestro del juego actual están en [FlappyDan/ROADMAP.md](https://github.com/HikariLucy/FlappyDan/blob/main/ROADMAP.md)**. Este repositorio Dantopia se reserva exclusivamente para el port a Godot.
