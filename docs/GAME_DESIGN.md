# Game Design Document — Dantopia (borrador P0)

## 1. Premisa
Dante Pixel, un niño rubio, atraviesa espacios cotidianos desde una mirada imaginativa. Dantopia combina accesibilidad, humor y progresión con un cierre emocional: volver con sus padres y dormir. No transformar el mundo familiar en una experiencia hostil u oscura.

**Referencia de comportamiento:** [FlappyDan Legacy](https://github.com/HikariLucy/FlappyDan). Este archivo no sustituye su roadmap ni las evidencias de F3.4/F3.5/F4; su contenido se validará contra la versión congelada.

## 2. Pilares
1. **Control inmediato:** entender cómo volar en segundos, sin tutorial extenso.
2. **Lectura clara:** obstáculos y peligros distinguibles de la decoración; pixel art legible.
3. **Personalidad:** movimientos, reacciones y escenas narrativas de Dante, papá, mamá y jefes.
4. **Tres modos distintos:** mecánicas, economías y dificultad independientes.
5. **Juego familiar:** ayudas de accesibilidad y cero monetización agresiva.
6. **Paridad observable:** el port conserva el comportamiento aprobado; no hereda bugs históricos.

## 3. Modos
### Clásico
- Vuelo endless, puntuación, récords, curva de dificultad progresiva.
- Recompensas moderadas y cosméticos exclusivamente visuales.
- Sin ventajas comprables, sin checkpoint, sin perks roguelite.
- Economía propia. Validar contra F4.0–F4.4 cuando estén aprobadas.

### Familiar
- Vuelo endless seguro, tres corazones iniciales, recuperación limitada, protección y ritmo amable.
- Celebraciones por hitos y cosméticos con moneda propia.
- Accesibilidad y claridad antes que desafío extremo.
- No copiar perks o dinero de Arcade/Clásico. Validar F2.8D con juego real.

### Arcade
- Expedición roguelite de cuatro regiones, con elección de mejoras, builds, encuentros y jefes.
- Ruta narrativa: **TIERRA → PATIO → CASA → BUENAS NOCHES**.
- Jefes: **LOBO → COCHE/BROCHES → DUCHA/TINA → CAMA**.
- Final: Dante encuentra a sus padres, abrazo, se acuesta y duerme.
- Mantener el espíritu de cada encuentro; sincronizar hitboxes, animación, controles y feedback.
- Reglas exactas de probabilidades, costes, duración y progresión se extraen de la versión Legacy congelada, no se inventan aquí.

## 4. Controles y accesibilidad
- Unificar la acción de vuelo y los estados de interfaz bajo Input Map.
- Soportar teclado, mando y toque en pantalla mediante adaptadores, sin duplicar gameplay.
- Comprobar contraste, tamaños de texto, hitboxes táctiles, safe areas y legibilidad a diferentes resoluciones.
- Mantener feedback redundante visual/sonoro cuando sea posible.

## 5. Narrativa y tono
- El juego es íntimo y luminoso, con escenarios familiares fantásticos pero reconocibles.
- No se presume diálogo extenso; la comunicación puede ser visual.
- Las cinemáticas deben ser reproducibles, poder pausar/saltar cuando se defina UX y no bloquear un guardado.
- La futura aventura de sueños será **otra obra**, no un modo nuevo de este proyecto.

## 6. Sin decisiones aún
- Resolución interna final (referencias de Legacy 800×600 y 400×300 a verificar).
- Tablas numéricas de dificultad y recompensas.
- Balance final de tienda y curvas.
- Sistemas de desbloqueo definitivos.
- Estilo visual definitivo de remaster F5.
- Reglas de skip/replay para cinemáticas y exportación web.

Estas decisiones requieren evidencia del Legacy y revisión del vertical slice.
