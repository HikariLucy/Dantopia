# Puertas de migración (gates) — Dantopia Legacy → Godot

**Estado:** ninguna puerta se declara aprobada. Todos los ítems requieren evidencia, responsable y fecha de HUMAN PASS.

## G0 — Cierre funcional de Legacy
- [ ] F3.4: BUENAS NOCHES, CAMA y cinemática del abrazo/sueño integradas, jugadas y aprobadas.
- [ ] F3.5: expedición completa con cuatro regiones, transiciones, bosses y final; curva, XP, builds y rendimiento aceptables.
- [ ] F4.0–F4.4: Clásico 2.0 con simulaciones y balance humano.
- [ ] F2.8D: Familiar Endless validado con runs largas, recuperación, tienda y controles.
- [ ] Regresiones de Clásico, Familiar y Arcade confirmadas.

**Evidencia requerida:** versión/tags/commit de Legacy, vídeos o capturas relevantes, matriz de pruebas, lista de bugs conocidos y decisión humana registrada.

## G1 — Congelación y exportación de referencia
- [ ] Elegir commit/tag Legacy de solo lectura (no mover referencia).
- [ ] Documentar resoluciones, FPS, tiempos, física, hitboxes, eventos y expectativas UX.
- [ ] Inventariar sprites, originales Aseprite, exportaciones, sonidos y tipografías.
- [ ] Clasificar licencias, material personal, archivos no publicables.
- [ ] Inventariar save data y construir corpus de prueba anonimizado.
- [ ] Auditoría Android Legacy: script de build, dependencias, input táctil y permisos; si no es viable, registrar decisión sin bloquear Godot indefinidamente.

**Evidencia:** \`docs/LEGACY_BASELINE.md\`, resultados reproducibles y recursos autorizados.

## G2 — Viabilidad de Godot
- [ ] Godot 4.7.2 y export templates disponibles en el equipo.
- [ ] Abrir escena de laboratorio en Windows/Linux.
- [ ] Importar sprite de Dante, conservar pixel art y animación.
- [ ] Ejecutar prueba de Input Map, colisiones y guardado.
- [ ] Probar APK mínimo en **teléfono físico**, si SDK disponible.
- [ ] Probar exportación Web real con navegador, si es objetivo del release.

**Evidencia:** capturas, logs, versión del editor/plantillas, características del dispositivo; reportar NO PROBADO cuando corresponda.

## G3 — Vertical slice TIERRA
- [ ] Movimiento se siente comparable con Legacy, medido en escenarios de referencia.
- [ ] Obstáculos y colisiones no producen regresiones graves.
- [ ] El encuentro LOBO tiene al menos un ciclo funcional.
- [ ] HUD, pausa, audio y configuración básica funcionan.
- [ ] Modificar sprites, animaciones y parámetros desde el editor resulta viable para el propietario.
- [ ] Tests de lógica, smoke Desktop y HUMAN PASS.

**Decisión:** si falla G3, corregir arquitectura/control y **no** portar PATIO/CASA/BUENAS NOCHES.

## Registro de aprobación
| Gate | Estado | Evidencia | Aprobador | Fecha |
| --- | --- | --- | --- | --- |
| G0 | PENDIENTE | — | — | — |
| G1 | PENDIENTE | — | — | — |
| G2 | PENDIENTE | — | — | — |
| G3 | PENDIENTE | — | — | — |

**Regla:** P0/P3 laboratorios aislados pueden avanzar antes de G0/G1; NO la reconstrucción de producción completa.
