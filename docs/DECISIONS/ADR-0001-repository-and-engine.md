# ADR-0001 — Repositorio separado y Godot como motor

**Fecha:** 2026-10-13  
**Estado:** Aceptada como dirección inicial; sujeta a revisión técnica en P3/P5.

## Contexto
Dantopia nació en Pygame y ahora contiene tres modos, múltiples regiones y lógica visual avanzada. Para editar sprites, animaciones, escenas y cinemáticas de forma más visual se propone un port a motor 2D completo.

## Decisión
- El Legacy continúa en \`HikariLucy/FlappyDan\`.
- La implementación Godot reside en \`HikariLucy/Dantopia\`.
- Se parte de Godot 4.7.2 stable + GDScript para evaluar control visual, Android y Web.
- **P0 y P3 pueden avanzar en paralelo** al cierre del Legacy.
- La migración de gameplay completa depende de G0/G1 y del éxito de G2/G3.
- El metroidvania de sueños será otro juego, no parte de este repositorio.

## Consecuencias
A favor: historial y QA separados, editor visual, animaciones, escena por sistema y exports integrados.  
Costes: reconstrucción de lógica, pruebas de paridad, port de guardados/controles, nueva curva de aprendizaje.

## Reversibilidad
Godot 4.7.2 es un punto de partida, no una promesa de perpetuidad. Decidir actualización del motor mediante issue y smoke multiplataforma. El código Legacy no se elimina.
