# DANTOPIA — ROADMAP MAESTRO DEL PRODUCTO (LEGACY + GODOT)

**Edición:** v1.0 viva — 13-10-2026 (tablero operativo canónico en §K; planificación histórica P0–P17 conservada)  
**Proyecto objetivo:** `HikariLucy/Dantopia` (repositorio creado; fundación P0 en preparación)  
**Referencia Legacy:** `HikariLucy/FlappyDan`  
**Motor inicial propuesto:** Godot **4.7.2 stable**, GDScript  
**Estado:** fuente única de tareas, estado y aprobaciones en §K. Las secciones A–J son especificaciones históricas y gates de migración; sus casillas no representan avance actualizado.  
**Propietario del producto / aceptación:** responsable del proyecto, mediante revisión humana.  
**Implementación asistida:** Codex (sistemas, arquitectura, pruebas), Claude Code (presentación, assets y pipeline artístico), bajo revisión del responsable del proyecto.

> **Decisión central:** abrir ahora un repositorio nuevo, inicialmente privado. Hasta cerrar las puertas de migración del proyecto Pygame, permitir en el nuevo repositorio documentación y prototipos aislados, **no** un segundo juego desarrollado en paralelo.

---

## A. Visión, alcance y reglas de producto

### A.1 Identidad de Dantopia
- Juego 2D de pixel art centrado en Dante Pixel, un pequeño protagonista rubio y su universo familiar.
- **Clásico:** supervivencia endless, puntuación/récord, curva de dificultad y economía exclusivamente cosmética. Sin perks roguelite.
- **Familiar:** endless accesible, corazones recuperables, protección, cosméticos propios y progresión amable. No debe convertirse en Clásico con más vidas.
- **Arcade:** expedición roguelite por TIERRA → PATIO → CASA → BUENAS NOCHES, jefes (LOBO, COCHE/BROCHES, DUCHA/TINA, CAMA), builds, progresión, cierre afectivo con Dante, sus padres y el sueño.
- La versión Godot conservará **el diseño y la intención** del juego Legacy. No se exige reproducir cada defecto de implementación Pygame.
- Metroidvania del mundo de los sueños: **otro videojuego de la franquicia, fuera del alcance de este port**; su planificación se hará por separado.

### A.2 Objetivos medibles de la nueva versión
1. Ejecutar los tres modos sin regresiones sustantivas de diseño.
2. Permitir al creador editar escenas, posiciones, animaciones, colisiones y poderes desde el editor.
3. Contar con una partida Arcade completa, incluido el final narrativo.
4. Exportar Windows/Linux y APK Android instalable; Web sujeto a su propio QA.
5. Respetar licencias, atribuciones y privacidad; no requerir servidor ni inicio de sesión para jugar.
6. Mantener proyecto navegable, probado y con documentación suficiente para retomarlo después de meses.

### A.3 No objetivos del port inicial
- Nuevo modo multijugador, online, rankings en la nube, monetización, gacha ni microtransacciones.
- Agregar una quinta región antes de terminar las cuatro existentes.
- Transformar Clásico o Familiar en roguelite.
- Cambiar a 3D, física realista o un sistema de cámara incompatible con la lectura del gameplay.
- Implementar a la vez el metroidvania de los sueños.
- Reproducir al 100 % código, bugs o estructura de clases del proyecto Pygame.

### A.4 Principios de ingeniería
- Configuración y datos separados de comportamiento y representación.
- Las escenas componen objetos; los recursos tipados configuran valores; las señales comunican eventos relevantes.
- Mínimas dependencias globales y autoloads solo cuando tienen semántica global real.
- Preferir señales/dependencias explícitas a rutas de nodos duras y acoplamiento cruzado.
- Frame de física fijo, RNG sembrado para reproducir incidentes y herramientas de simulación cuando corresponda.
- Un solo propietario de cada regla del juego; UI y rendering no deciden puntuación ni recompensas.
- Todo cambio de motor y exportación se hace sobre una versión fijada y verificada.
- Ninguna IA puede declarar HUMAN PASS, hacer merge, tag o publicación sin aprobación expresa.

---

## B. Estrategia de repositorios, ramas, licencias y releases

### B.1 Repositorios
- `HikariLucy/FlappyDan`: fuente histórica, trabajo vigente F3/F4 y release Legacy. No archivar hasta verificar release y respaldos.
- `HikariLucy/Dantopia`: nueva implementación Godot, no fork, sin trasladar historial ni código de Pygame como base operacional.
- Documentar referencia exacta de Legacy con commit SHA, tag, manifest de assets y checksum de exportaciones. No enlazar únicamente `main` porque cambia.
- GitHub Project/Issues para el tablero de trabajo; cada issue con fase, prioridad, dependencias y criterios de aceptación.

### B.2 Convenciones
- Rama protegida `main`, siempre ejecutable; rama `feat/<id>-descripcion` por cambio; `fix/`, `docs/`, `chore/`.
- PRs pequeños, revisión de diffs, capturas de cambios visuales, evidencia de pruebas, riesgos y plan de revertir.
- Etiquetas sugeridas: `phase:P0..P17`, `type:feature|bug|docs|art|test|ci`, `area:classic|family|arcade|android|story|assets`, `priority:P0|P1|P2|P3`, `status:blocked|ready|review|human-pass`.
- Milestones por fase o entregable; no crear 100 issues sin priorizar.
- Convención de versión semántica: `0.x` prototipos, `1.0.0` Godot listo para familia y desktop si se decide; APK beta `0.x` hasta criterios de lanzamiento.
- Separar el versionado del Legacy (`legacy-v1.0.0`) del nuevo (`v0.1.0` etc.).

### B.3 Archivos de raíz
```
Dantopia/
├── README.md
├── ROADMAP.md
├── CONTRIBUTING.md
├── CHANGELOG.md
├── .editorconfig
├── .gitattributes
├── .gitignore
├── project.godot
├── icon.svg
├── docs/
│   ├── VISION.md
│   ├── LEGACY_BASELINE.md
│   ├── MIGRATION_GATES.md
│   ├── GAME_DESIGN_DOCUMENT.md
│   ├── ARCHITECTURE.md
│   ├── MODES_AND_ECONOMY.md
│   ├── ART_BIBLE.md
│   ├── ASSET_MANIFEST.csv
│   ├── ANDROID_RELEASE.md
│   ├── QA_MATRIX.md
│   ├── DECISIONS/
│   └── PLAYTESTS/
├── game/
│   ├── bootstrap/
│   ├── characters/dante/
│   ├── core/
│   ├── modes/classic/
│   ├── modes/family/
│   ├── modes/arcade/
│   ├── regions/{tierra,patio,casa,buenas_noches}/
│   ├── bosses/{lobo,coche_broches,ducha,cama}/
│   ├── cinematics/
│   ├── ui/
│   ├── audio/
│   └── save/
├── art_source/  # fuentes originales seleccionadas, no volcado indiscriminado
├── tests/
├── tools/
└── .github/workflows/
```
- Agrupar sprites y scripts cerca de la escena propietaria cuando tenga sentido; `art_source/` almacena la fuente editable compartida.
- `.gitignore`: `.godot/`, archivos temporales, builds/APK/AAB, secretos/keystores, respaldos, logs y editor-specific junk. Mantener `.tscn`, `.tres`, `.gd`, manifests, escenas, fuentes originales seleccionadas y export presets sanitizados.
- Git LFS solo para binarios grandes identificados por inventario y coste. No activar LFS masivamente para cada PNG diminuto; evitar reescribir historia tras comenzar.
- **Licencias:** mantener privado hasta decidir licencia del código y confirmar procedencia/derechos sobre música, tipografías, sonidos, fotografías familiares convertidas en sprites y assets generados. No añadir MIT automáticamente a contenido creativo propio.

### B.4 Protección de material familiar
- No incorporar fotos de familiares originales, metadatos EXIF ni referencias personales al repositorio público.
- Preferir sprites derivados y necesarios para el juego con consentimiento de sus titulares.
- Publicar solo lo autorizado; eliminar originales sensibles del directorio de exportación y de los paquetes APK/Web.

---

## C. Fases y puertas de salida

Cada fase contiene: **alcance**, **tareas**, **entregables**, **criterios de aceptación (DoD)** y **bloqueos**. Las duraciones no se estiman aquí; se utilizarán dependencias y evidencia, no fechas inventadas.

### P0 — Fundación de repositorio (INICIAR AHORA)
**Objetivo:** tener lugar propio de planificación y seguimiento sin duplicar el desarrollo activo.

**Tareas**
- [ ] Crear `HikariLucy/Dantopia` privado, descriptivo y enlazado a `HikariLucy/FlappyDan` como referencia histórica.
- [ ] Crear `README.md` con visión, modos, plataformas, estado y decisión de motor.
- [ ] Fijar Godot 4.7.2 stable, GDScript, política de upgrade del motor y licencias.
- [ ] Añadir `ROADMAP.md`, GDD preliminar y lista de puertas de migración.
- [ ] Crear `CONTRIBUTING.md`, plantilla de PR/Issue, etiquetas y milestones.
- [ ] Adoptar `.gitignore`/`.gitattributes` correctos para Godot 4.x.
- [ ] Crear tablero con flujo Backlog → Ready → In Progress → Review → Human QA → Done.
- [ ] Agregar `docs/DECISIONS/ADR-0001-engine.md`: por qué Godot, opciones evaluadas, supuestos revisables.
- [ ] Primer commit sin código jugable obligatorio; opcional `project.godot` vacío solo si abre en el editor.

**Entregables:** repo privado, visión, ADR y tablero priorizado.

**DoD:** README comprensible, reglas de PR definidas, no hay datos sensibles ni claves, `main` limpio, nada de lógica Legacy copiada.

### P1 — Cierre del producto Legacy (TRABAJO EN REPO ORIGINAL)
**Objetivo:** concluir aquello que vamos a reconstruir. Este es el **gate productivo** más importante.

**Tareas**
- [ ] F3.4: cerrar BUENAS NOCHES, jefe CAMA, cámara, abrazo con mamá y papá, acostarse, dormir y final.
- [ ] F3.4: HUMAN PASS para continuidad visual, colisiones, tiempos y accesibilidad de la cinemática.
- [ ] F3.5: partida TIERRA → PATIO → CASA → BUENAS NOCHES, todos los jefes, transiciones, elecciones y victoria.
- [ ] F3.5: balance de dificultad, curvas de XP, builds, duración y persistencia.
- [ ] F4.0: simulación económica de Clásico, escenarios de runs y coste real de cosméticos.
- [ ] F4.1–F4.3: recompensas endless, control de emisión y sumideros, cosméticos sin ventajas de gameplay.
- [ ] F4.4: balance humano de Clásico; revisar también estado Familiar F2.8D.
- [ ] Regresión cruzada de los tres modos en PC y navegador.
- [ ] Auditar empaquetado Android Legacy: script con lista fija de archivos y `buildozer.spec`; intentar APK solo si el costo técnico está acotado.
- [ ] Crear release candidata Pygame; guardar capturas, videos y versiones de prueba.

**Entregables:** `Legacy Release Candidate`, build reproducible y bitácora de errores.

**DoD:** se puede terminar Arcade; los tres modos son coherentes; no hay blockers P0/P1; todas las pruebas automatizadas elegidas pasan; revisión manual documentada; versión referenciable por tag y SHA.

**Bloqueos:** no liberar la migración de gameplay sin el gate P1+P2. El APK Pygame es deseable pero **no requisito absoluto** si la toolchain resulta desproporcionadamente costosa.

### P2 — Auditoría y baseline ejecutable
**Objetivo:** convertir Pygame en una especificación verificable, no en código para copiar a ciegas.

**Tareas**
- [ ] Congelar la revisión Legacy de referencia (`tag`, commit SHA, inventario de dependencias).
- [ ] Mapear `main.py` y módulos a sistemas: input, movimiento, colisiones, física, UI, audio, RNG, jefes, regiones, economía, guardado.
- [ ] Inventariar inputs: teclado, ratón, gamepad, touch y acciones contextuales.
- [ ] Documentar la física observada: FPS de simulación, gravedad, impulso, caída, límites, invulnerabilidad y colisiones.
- [ ] Documentar unidades de coordenadas, anclas, proporciones y dimensiones del gameplay.
- [ ] Capturar fixtures de simulación con semillas RNG fijas, inputs registrados y eventos esperados.
- [ ] Capturar 10 escenarios de referencia por modo (arranque, daño, compra, pausa, game over, retry, reanudación, etc.).
- [ ] Capturar recorrido de cada boss con fases/patrones, telegraphs, tiempos y condiciones de victoria.
- [ ] Mapear save Legacy, versiones, comportamiento ante corrupción y datos personales.
- [ ] Exportar balance tables y catálogos de perks/cosméticos a un formato legible, preservando identidad por modo.
- [ ] Catalogar fuentes de audio, imágenes, tipografías y archivos Aseprite con atribución y licencia.
- [ ] Documentar discrepancias conocidas en lugar de legitimarlas como requisitos.

**Entregables:** `LEGACY_BASELINE.md`, `ASSET_MANIFEST.csv`, fixtures y matriz de paridad.

**DoD:** cada comportamiento crítico tiene regla documentada y caso de prueba; fuente congelada; no se exige igualdad pixel a pixel de renderer.

### P3 — Aprendizaje del editor y prueba de compatibilidad multiplataforma
**Objetivo:** confirmar que Godot es conveniente para TU flujo, antes de comprometer toda la migración.

**Tareas**
- [ ] Instalar editor oficial Godot 4.7.2 en Windows y Linux, con export templates de la misma versión.
- [ ] Explorar Scene dock, Inspector, Node2D, CanvasLayer, Control, AnimationPlayer, AnimatedSprite2D, señales y recursos.
- [ ] Crear escena `sandbox_dante.tscn` sin afectar baseline: imagen de Dante que se mueve con input.
- [ ] Probar pixel snapping, sampler nearest, zoom, cámaras y movimiento sin shimmer.
- [ ] Evaluar renderizadores y compatibilidad Android/Web con la configuración más sencilla que cumpla el arte.
- [ ] POC de Windows/Linux/Web y APK **vacío o mínimo**, para descubrir barreras de toolchain temprano.
- [ ] Probar importación de `.aseprite` mediante exportación PNG + spritesheet/metadata; no instalar plugins sin evaluar mantenimiento.
- [ ] Confirmar qué puede ajustar el creador sin tocar código: sprites, hitboxes, velocidades, claves de animación, UI y layouts.
- [ ] Documentar los resultados y, si hay blocker real, reconsiderar el alcance técnico.

**Entregables:** escena sandbox ejecutable, informe de decisión técnica y primer APK de prueba de Godot.

**DoD:** proyecto abre en Windows y Linux, editor permite modificar elementos clave, no se ha asumido compatibilidad Android sin probarla.

### P4 — Arquitectura, convenciones y contratos de juego
**Objetivo:** preparar una base extensible sin caer en el nuevo `main.py` gigante.

**Tareas**
- [ ] Definir `GameRoot`, `ModeController`, `RunState`, `PlayerController`, `SaveService`, `AudioService`, `SceneTransition`.
- [ ] Definir interface/contratos de modo. Clásico, Familiar y Arcade deben gestionar reglas sin condicionales globales omnipresentes.
- [ ] Modelar componentes de movimiento, salud, invulnerabilidad, colisiones, obtención de objetos y estado de juego.
- [ ] Contratos de eventos: `run_started`, `player_damaged`, `boss_phase_changed`, `reward_granted`, `run_finished`.
- [ ] Definir datos tipados: `PowerDefinition`, `CosmeticDefinition`, `ObstacleDefinition`, `BossPatternDefinition`, `RegionDefinition`.
- [ ] Decidir qué config vive en `.tres`, qué vive en JSON y cómo se versiona sin romper referencias.
- [ ] RNG sembrado por run; registrar semilla y eventos de debugging; sin depender del orden de render para generar gameplay.
- [ ] Establecer FPS de física y método de integración a validar contra Pygame; evitar física de delta variable para lógica sensible.
- [ ] Inventariar autoloads mínimos (config, audio, saves) y no crear un `EventBus` global para todo sin necesidad.
- [ ] Crear reglas de código GDScript, error handling, logging, naming y comentarios.
- [ ] CI mínimo: validación de apertura/importación headless, tests sin display y comprobación de ausencia de archivos sensibles.
- [ ] Test de ciclo completo: menú → comenzar → pausar → morir → reintentar → salir, con escenas placeholder.

**Entregables:** diagrama de escenas/sistemas, prototipo funcional estructurado y ADRs.

**DoD:** estructura permite agregar un modo o un obstáculo sin modificar un megaarchivo central; prueba headless reproducible.

### P5 — Primer vertical slice de TIERRA (GO / NO-GO)
**Objetivo:** demostrar que sabemos portar gameplay + arte + boss + UX antes de reconstruir las cuatro regiones.

**Tareas**
- [ ] Dante Pixel con input, caída, impulso, muerte y feedback; implementar estado en script y animación aparte.
- [ ] Obstáculos representativos de TIERRA, colisiones y recolección.
- [ ] Fondo día/noche, cámara estable, efecto de velocidad y parallax discreto.
- [ ] HUD mínimo, pausa, reinicio y menú.
- [ ] Spawn determinista con semilla; comparar 3–5 casos con Legacy.
- [ ] LOBO: una fase real representativa con telegraph, patrón, golpe y cierre de estado.
- [ ] Animaciones de vuelo, caída y daño importadas desde un set aprobado.
- [ ] Sonido, música y volumen básico.
- [ ] Probar el slice en Windows y Linux, y un dispositivo Android antes de escalar.
- [ ] Revisión lado a lado Legacy/Godot: sensación de control, hitboxes, legibilidad, ritmo, feedback y rendimiento.
- [ ] Primer HUMAN PASS de Godot; decisión GO / RETRABAJAR / NO-GO documentada.

**Entregables:** `vertical-slice-tierra` jugable y video comparativo.

**DoD:** el jugador puede terminar el slice sin fallos; el control se siente equivalente o mejor; arte legible; escena editable por el creador; no se ocultan dificultades técnicas.

**Gate:** si falla, no portar aún Patio/Casa/Buenas Noches. Resolver fundamento primero.

### P6 — Núcleo común y selección de modos
**Objetivo:** preparar menú completo, sesiones, UI, configuración, inputs y reglas compartidas.

**Tareas**
- [ ] Boot/splash Dantopia, identidad visual, menú de modos y retorno seguro.
- [ ] Configurar `InputMap`: salto/interacción, pausa, navegación, confirmar/atrás, mando y táctil.
- [ ] Perfiles de control distintos por modo si afectan reglas; no duplicar polling crudo.
- [ ] Estado de run, checkpoints de interfaz (no necesariamente checkpoints de gameplay), resumen de sesión.
- [ ] Sistema de HUD responsive y componentes UI reutilizables, tooltips, paneles.
- [ ] Preferencias persistentes: audio, controles, accesibilidad, visuales.
- [ ] Eventos de pausa, game over, retry, reanudar y cambio de escena.
- [ ] Audio buses `Master`, `Music`, `SFX`, sliders y suspensión/reanudación de audio.
- [ ] Pantalla para diagnóstico, versión de build, FPS y logging en builds de prueba.

**Entregables:** shell de aplicación con 3 modos seleccionables y runtime común.

**DoD:** flujo íntegro de navegación para mouse/teclado/gamepad/touch previsto; no hay economía mezclada entre modos.

### P7 — Port Clásico 2.0
**Objetivo:** reproducir el bucle endless puro definido en F4.

**Tareas**
- [ ] Obstáculos, variantes, dificultad dinámica, score y récord.
- [ ] Reglas de muerte/reintento sin checkpoints ni perks.
- [ ] Ganancia de monedas y premios de hitos según simulación cerrada de F4.
- [ ] Tienda cosmética y previews, compras, exclusividad de economía.
- [ ] Guardado de progreso/recompensas y récordes; integridad ante caída de aplicación.
- [ ] Pruebas con runs de 30/60/90/150/300+ obstáculos y perfiles de recolección.
- [ ] Pruebas de rendimiento y QA de HUD con variedad de ratios.

**Entregables:** Clásico completo de paridad Legacy.

**DoD:** progresión económica medible y consistente; sin ventaja jugable vendida; humano valida diversión y ritmo.

### P8 — Port Familiar Endless 2.0
**Objetivo:** juego amable y accesible que no herede por error la dificultad de Clásico.

**Tareas**
- [ ] 3 corazones iniciales, daño, protección y recuperación según balance final Legacy.
- [ ] Hitos infinitos cada 30 obstáculos, celebración sin interrupción de run.
- [ ] Escalada suave de dificultad con techo seguro.
- [ ] Lógica de pity/cooldown para recuperación; pruebas reproducibles de RNG.
- [ ] Huevo, turbo y su interacción con daño/invulnerabilidad.
- [ ] Tienda familiar completa, cosméticos propios y visual preview.
- [ ] Accesibilidad, feedback sin sobrecarga, contraste y alternativas para estímulos intensos.
- [ ] Runs largas y casos límite de corazones completos, hitos simultáneos y fin de run.

**Entregables:** Familiar completo.

**DoD:** corazón nunca supera máximo, economía no cruza Clásico, la experiencia es perceptiblemente más accesible, QA humano aprobado.

### P9 — Núcleo roguelite de Arcade
**Objetivo:** convertir los sistemas de progresión y builds de Legacy en recursos desacoplados.

**Tareas**
- [ ] Orquestador de expedición y transición entre regiones sin estados huérfanos.
- [ ] XP, niveles, 8 elecciones normales y 3 decisiones especiales según diseño definitivo.
- [ ] Catálogo de perks de movilidad, defensa, recolección y control.
- [ ] Reglas de sinergia/evolución (con mecanismos sin ventajas indebidas fuera de Arcade).
- [ ] Recompensas, metaprogresión y Taller, según aceptación Legacy.
- [ ] Eventos de boss, reward, elección y transición; integración de UI.
- [ ] Simulación de 1000 runs con semillas deterministas para encontrar duplicaciones, estados inválidos y economía extrema.
- [ ] Instrumentación de debug para inyectar perks y navegar a jefes solo en builds de desarrollo.

**Entregables:** arcade run core completamente jugable con placeholders más fixtures.

**DoD:** 8+3 elecciones según reglas, RNG reproducible, persistencia coherente y cero contaminación entre economías.

### P10 — Regiones y jefes completos
**Objetivo:** conseguir la aventura completa en Godot, reutilizando P9 y P5.

**Orden obligatorio**

**P10.1 — TIERRA / LOBO**
- [ ] Todos los obstáculos y variantes finales de la región.
- [ ] Ciclo diurno, atmósfera, escalado y transición a Patio.
- [ ] LOBO completo con animaciones, señales previas, fases y recompensa.
- [ ] QA de velocidad, habilidad de recuperación y estados de daño.

**P10.2 — PATIO / COCHE + BROCHES**
- [ ] Jardín, ropa, obstáculos y composición de profundidad.
- [ ] Encuentro con coche, broches, patrones de correas, legibilidad y recompensa.
- [ ] Conector Patio → Casa y continuidad visual.

**P10.3 — CASA / DUCHA / TINA**
- [ ] Living, pasillo, baño y reglas de colisión propias.
- [ ] DUCHA/TINA: llaves, peligros de agua, patrones, feedback y victoria.
- [ ] Transición narrativo-visual al anochecer.

**P10.4 — BUENAS NOCHES / CAMA**
- [ ] Living nocturno, recorrido al dormitorio, ambientación tranquila.
- [ ] CAMA: encuentro final, telegraphs amables y resultado.
- [ ] Trigger de cinemática F3.4 sin cambio accidental del modo de juego.

**P10.5 — QA de expedición integrada**
- [ ] Ejecutar una run completa sin debug, usando entradas reales.
- [ ] Validar duración y pacing, cargas/transiciones, audio y memoria.
- [ ] Regresión de perks en bosses, daño durante cambios de escena, abortar/reintentar y guardar.
- [ ] Verificación de que una región no requiere assets/scripts privados de otra.

**Entregables:** Arcade end-to-end Godot.

**DoD:** HUMAN PASS de una run completa, cuatro regiones y cuatro encuentros finales, sin salto de estados narrativos.

### P11 — Persistencia, progresión y seguridad de datos
**Objetivo:** tener guardados fiables y evolutivos entre actualizaciones.

**Tareas**
- [ ] Esquema `save_version`, perfiles, configuración, monedas separadas, registros y cosméticos.
- [ ] Transacciones sencillas de recompensa/compra que no dupliquen monedas si se repite el evento.
- [ ] Escritura atómica (temporal + reemplazo según plataforma); respaldos razonables y recuperación de corrupción.
- [ ] Tests de carga de saves nuevos/antiguos y de campos ausentes.
- [ ] Verificar rutas `user://` Desktop, Android y Web: las plataformas tienen sandbox diferente.
- [ ] Decidir **si** se importa progreso Legacy. Desktop: importador explícito con backup. Android: no prometer importación automática entre aplicaciones, firmas y sandboxes diferentes.
- [ ] Definir política de actualización, reinstalación y posible desinstalación.
- [ ] No guardar PII ni telemetría remota por defecto.

**Entregables:** servicio de guardado versionado y procedimientos de recuperación.

**DoD:** tests adversariales de corrupción y actualización; no hay pérdida silenciosa de progreso.

### P12 — Remaster visual F5 sobre Godot
**Objetivo:** alcanzar el estilo final usando el editor y assets originales, sin duplicar el esfuerzo en Pygame.

**Tareas**
- [ ] Aprobar Art Bible: proporciones Dante/familia, paletas, tamaños, outlines, contraste, pixel density, animación.
- [ ] Definir spritesheet/atlas, convención de nombres, tags, pivotes, frames, duraciones y animaciones.
- [ ] Crear pipeline reproducible Aseprite → PNG/metadata → Godot, sin dependencias opacas.
- [ ] Remaster TIERRA primero (vertical slice artístico), HUMAN PASS antes de propagar estilo.
- [ ] Dante animaciones: idle, impulso, vuelo, caída, daño, recuperación, celebración, abrazo, sueño.
- [ ] Jefes y obstáculos: telegraph, contacto, feedback, derrota amable, recompensa.
- [ ] Cielos multicapa, vegetación, suelos, casa, baño, dormitorio y luz nocturna.
- [ ] UI coherente, tienda, HUD, Taller, tarjetas de perks, transición y feedback.
- [ ] Evaluar pixel-art nearest, parallax, escalado y sombra; desactivar efectos que sacrifiquen claridad o FPS.
- [ ] Revisión de color/legibilidad, fotos comparativas y capturas del mismo estado lógico.
- [ ] Optimización: atlas cuando aporte, límites de partículas, evitar cargas duplicadas y texturas desmedidas.

**Entregables:** F5 remaster en todas las regiones y modos.

**DoD:** estilo consistente, sin pérdidas de lectura ni rendimiento, editable desde Godot/Aseprite.

### P13 — Narrativa y cinemáticas
**Objetivo:** pasar de una secuencia codificada rígida a un pipeline narrativo reutilizable.

**Tareas**
- [ ] Documentar beats del final de F3.4 y sus requisitos emocionales, sonidos y cámara.
- [ ] Timeline de `AnimationPlayer`: aparición, acercamiento, abrazo, corazones, caminata, cama, manta, luz, sueño, fade.
- [ ] Crear escena separada de familia, cámara, iluminación, overlay y audio, sin contaminar física de Arcade.
- [ ] Definir contratos `CinematicDirector.play(id)` y señales `finished`, `skip_requested`, `skip_finished`.
- [ ] Permitir saltar cinemáticas cuando sea apropiado, con destino de estado idéntico al final normal.
- [ ] Manejar gamepad, teclado y touch; desactivar input de gameplay mientras corre la cinemática.
- [ ] Sincronizar cues de sonido y efectos con marcas de tiempo editables.
- [ ] Verificar reproducción con resoluciones distintas y pérdida temporal de foco.
- [ ] Tests del estado final incluso si el usuario salta la escena o minimiza la aplicación.
- [ ] Crear una herramienta o convención para futuras escenas narrativas sin desarrollar un editor visual propio.

**Entregables:** ending cinematic en Godot y sistema reutilizable de secuencias.

**DoD:** storyboard aprobado, no se pierden guardados/recompensas, cinematografía legible, HUMAN PASS.

### P14 — QA integral Desktop y rendimiento
**Objetivo:** lograr calidad de release antes de exponer familias a bugs que se pueden detectar automáticamente.

**Matriz mínima**
- [ ] Windows y Linux: arranque limpio, menú, los 3 modos, game over, retry, cierre.
- [ ] Resolución lógica 400×300 como referencia de QA Legacy; dimensionamiento de ventana, zoom, 16:9 y 4:3.
- [ ] Teclado, mouse y gamepad; desconexión de mando durante la partida.
- [ ] Pérdida de foco, alt-tab, suspensión del sistema, pausa y música.
- [ ] Memoria y FPS en runs largas, efectos máximos, jefes, transiciones y tienda.
- [ ] Audio en sistemas sin dispositivo disponible, dispositivos desconectados y mute.
- [ ] Pruebas de assets ausentes, archivos corruptos y permisos restringidos.
- [ ] Textos legibles y UI accesible en layouts pequeños.
- [ ] Golden fixtures de física, RNG, builds y economía.
- [ ] Revisión de errores P0/P1, capturas comparativas y playtest humano completo.

**Objetivos iniciales de rendimiento (ajustables tras baseline real)**
- 60 FPS objetivo de gameplay en hardware de referencia; degradación visual elegante antes de comprometer lógica.
- Cero crash, softlock o pérdida de guardado en recorridos de aceptación.
- Ninguna regresión importante del gameplay frente a Legacy sin una decisión documentada.

**Entregables:** informe QA, RC Desktop, matriz de dispositivos/software.

**DoD:** todas las pruebas bloqueantes pasan; cada excepción está registrada y aceptada.

### P15 — Android / APK familiar
**Objetivo:** primera versión Godot instalable fuera de Google Play.

**Tareas**
- [ ] Instalar SDK Android/OpenJDK apropiados para la versión del motor y sus export templates.
- [ ] Elegir `application_id` definitivo; distinguirlo del APK Legacy y documentar la consecuencia sobre guardados/actualizaciones.
- [ ] Exportar APK debug, instalar por ADB y recoger logs.
- [ ] Diseñar controles táctiles: zona grande de salto, input sin dobles pulsaciones, navegación y pausa.
- [ ] Orientación landscape, safe areas de notch/cámara y navegación del sistema.
- [ ] Decidir viewport: preservar jugabilidad/hitboxes base; usar letterboxing o contenido extra lateral cuando esté diseñado. **No estirar personajes** para llenar una pantalla ultrapanorámica.
- [ ] Integrar escalado pixel art y UI con anclajes adaptables.
- [ ] Verificar suspensión, home/back, llamadas/notificaciones, bloqueo de pantalla y reanudación.
- [ ] Verificar audio, FPS, consumo energético básico, thermal throttling y memoria.
- [ ] Testear en al menos 2 teléfonos Android distintos cuando sea posible y 3 tamaños/aspect ratios.
- [ ] Crear keystore release y respaldarla fuera del repositorio, junto con credenciales seguras.
- [ ] Firmar APK release; verificar instalación, upgrades con la misma firma, reinstalación y guardados.
- [ ] Verificar tamaño final del paquete, manifiesto, íconos, nombre visible Dantopia y permisos mínimos.
- [ ] Redactar instructivo familiar claro de instalación fuera de la Play Store y canales de feedback.

**Entregables:** APK firmado `Dantopia-Android-beta`, QA Android y guía familiar.

**DoD:** instala en dispositivos objetivos, no crashea en recorridos de aceptación, controles son cómodos, guardado funciona, firma y keystore respaldadas.

**Nota:** APK Legacy es un hito independiente en P1; este P15 es el APK del port Godot.

### P16 — Beta familiar, corrección y exportación Web
**Objetivo:** escuchar jugadores reales sin imponer carga excesiva.

**Tareas**
- [ ] Distribución controlada de la beta Android, no publicación abierta.
- [ ] Playtest sin instrucciones del desarrollador y otro con guía breve; observar si entienden modos/controles.
- [ ] Recoger reportes: dispositivo, versión, modo, pasos, capturas y severidad; no pedir datos personales innecesarios.
- [ ] Medir cualitativamente diversión, dificultad, claridad del abrazo final, audio y confort táctil.
- [ ] Priorizar bugs reales antes de nuevas ideas.
- [ ] Crear canal de feedback sencillo (formulario o issue privado), con seguimiento.
- [ ] Exportar Web desde Godot, validar WebAssembly/WebGL2 en navegadores reales compatibles.
- [ ] Comprobar persistencia en navegador, tamaño de descarga, audio por gesto del usuario y focus/input.
- [ ] Repetir regresiones tras correcciones y congelar release candidata.

**Entregables:** informe de beta, backlog de fixes, RC Web y RC Android.

**DoD:** no hay incidencias bloqueantes abiertas, prueba familiar positiva, métricas de estabilidad aceptables.

### P17 — Publicación pública (OPCIONAL, DECISIÓN POSTERIOR)
**Objetivo:** preparar lanzamiento si la beta valida el producto y decides compartirlo con más personas.

**Tareas**
- [ ] Elegir si distribución gratuita, privada o pública; revisar nombre y material de marca.
- [ ] Auditar derechos de sprites, sonidos, fuentes, material familiar y uso de imágenes generadas.
- [ ] Si Google Play: cuenta de desarrollador, aplicación creada, AAB firmado, requisitos de API, verificación de identidad y testing cerrado que corresponda al tipo de cuenta y reglas vigentes.
- [ ] Preparar ficha, capturas reales, íconos, descripción, políticas de privacidad y sección de seguridad de datos.
- [ ] Clasificación por edades, público objetivo, publicidad (idealmente ninguna) y permisos mínimos.
- [ ] Definir plan de soporte de errores, actualización de Android y pérdida de compatibilidad.
- [ ] Preparar lanzamiento de Windows/Linux/Web según QA; descargas firmadas/checksums donde aplique.
- [ ] Tag de release y changelog; monitoreo inicial de issues, sin SDK invasivos por defecto.

**Entregables:** publicación opcional y plan de mantenimiento.

**DoD:** decisiones legales y familiares aprobadas; QA compatible con requisitos actuales de tiendas, release sin secretos ni archivos privados.

---

## D. Camino crítico y paralelización sin conflictos

```
              [P0 repositorio/documentación]
                         │
                [P3 aprendizaje POC]
                         │
                         ├───────────────┐
                         │               │
[P1 finalizar Legacy] → [P2 baseline]   [P4 convención/pipeline]
                         │               │
                         └───────┬───────┘
                                 ▼
                         [P5 vertical slice]
                                 │
                          [GO / NO-GO]
                                 │
                        [P6 núcleo común]
                          │      │      │
                         P7     P8     P9
                          └──────┴──────┤
                                        P10 regiones/bosses
                                            │
                                        P11 guardado
                                            │
                                  P12 arte + P13 narrativa
                                            │
                                        P14 Desktop QA
                                            │
                                        P15 Android
                                            │
                                     P16 beta y Web
                                            │
                                     P17 público (optativo)
```

**Solapamiento autorizado:** P0, P3 exploratorio y P4 documental pueden ejecutarse mientras se finaliza P1.  
**Solapamiento prohibido sin decisión humana:** desarrollo completo de Arcade Godot antes del baseline y GO del vertical slice.  
**No impedir QA temprano Android:** P3 prueba export mínima y P5 prueba un slice en dispositivo real.

---

## E. Backlog inicial propuesto para GitHub Issues

**Gobierno (P0–P2)**
- `DAN-001` Crear repositorio privado y README.
- `DAN-002` Fijar motor y ADR inicial.
- `DAN-003` Plantillas y etiquetas de PR/issues + protección `main`.
- `DAN-004` Crear GDD y reglas de modo.
- `DAN-005` Aprobación de gates Legacy.
- `DAN-006` Congelar SHA/tag baseline.
- `DAN-007` Inventariar assets y licencias.
- `DAN-008` Extraer fixtures de física/input/RNG.
- `DAN-009` Especificar guardados Legacy.
- `DAN-010` Documentar comportamiento de bosses y cinematics.

**Motor/pipeline (P3–P5)**
- `DAN-011` Instalar Godot estable y templates Windows/Linux.
- `DAN-012` POC Android y Web mínimo.
- `DAN-013` POC de Dante, input y sprites en editor.
- `DAN-014` Proyecto base con import headless CI.
- `DAN-015` Contratos de escenas/eventos y recursos.
- `DAN-016` Pipeline de spritesheets Aseprite.
- `DAN-017` Físicas/control de Dante + tests.
- `DAN-018` Obstáculos TIERRA + hitboxes.
- `DAN-019` LOBO representative encounter.
- `DAN-020` QA GO/NO-GO de vertical slice.

**Modos / contenido (P6–P11)**
- `DAN-021` Menú, selección de modos, config y pausa.
- `DAN-022` InputMap unificado y gamepad/touch abstraídos.
- `DAN-023` Audio bus y volumen persistente.
- `DAN-024` Clásico endless base, score, récord.
- `DAN-025` Clásico economía y cosméticos.
- `DAN-026` Familiar corazones y recuperación.
- `DAN-027` Familiar endless y cosméticos.
- `DAN-028` Arcade XP/build/perks/elecciones.
- `DAN-029` Arcade Taller, recompensas y meta.
- `DAN-030` TIERRA/LOBO completos.
- `DAN-031` PATIO/COCHE-BROCHES completos.
- `DAN-032` CASA/DUCHA completos.
- `DAN-033` BUENAS NOCHES/CAMA completos.
- `DAN-034` QA de run Arcade end-to-end.
- `DAN-035` SaveService versionado con tests de corrupción.
- `DAN-036` Decisión e importador opcional de saves Legacy.

**Arte y narrativa (P12–P13)**
- `DAN-037` Art Bible F5.
- `DAN-038` Remaster TIERRA piloto.
- `DAN-039` Rig/animaciones finales de Dante.
- `DAN-040` Remaster PATIO/CASA/BUENAS NOCHES.
- `DAN-041` Arte final de 4 jefes y telegraphs.
- `DAN-042` UI/HUD/tienda/Taller remaster.
- `DAN-043` Pipeline de cámara/AnimationPlayer cinematics.
- `DAN-044` Ending familiar completo y QA de skip.

**Lanzamiento (P14–P17)**
- `DAN-045` Matriz desktop y performance regression.
- `DAN-046` Android orientación/input/safe areas.
- `DAN-047` Android suspensión/reanudación/save.
- `DAN-048` Keystore, firmado, upgrades y versionado.
- `DAN-049` APK familiar y guía de instalación.
- `DAN-050` Playtest familiar y triage.
- `DAN-051` Exportación Web y persistencia browser.
- `DAN-052` RC multi-plataforma y cierre de blockers.
- `DAN-053` Decisión Play Store y requisitos vigentes.
- `DAN-054` Material de tienda, licencia y privacidad.

*Los IDs son sugeridos para el backlog; no son números de issues creados ni una promesa de estado.*

---

## F. Políticas de pruebas, calidad y definición de terminado

### F.1 Pirámide de pruebas
1. **Datos:** esquema de recursos, límites de estadísticas, precios, compatibilidad save.
2. **Unidades:** daño, física, recuperación, selección, RNG y cálculo de monedas.
3. **Integración:** escenas/jefes/tiendas/guardado/flujo de modo, sin necesidad de windowing cuando sea posible.
4. **Golden fixtures:** semilla y entradas del Legacy comparadas a eventos/estados observables, con tolerancias acordadas.
5. **Smoke visual:** capturas y QA de composición, hitboxes y edición visual en engine.
6. **Dispositivo real:** Android, consumo de recursos, audio, controles y reinstalación.
7. **Humana:** personas juegan sin ayuda del desarrollador; observaciones y bugs registrados.

### F.2 Definition of Done de cada issue
- [ ] Alcance/criterios claros antes de codificar.
- [ ] Código y datos con responsabilidad definida; sin nuevos acoplamientos injustificados.
- [ ] Pruebas útiles, no tests cosméticos solo para inflar el contador.
- [ ] CI verde y diff revisado.
- [ ] Evidencia visual para cambios de escena/asset.
- [ ] Sin archivos sensibles ni binarios innecesarios.
- [ ] Documentación/ADR actualizada cuando corresponde.
- [ ] HUMAN PASS para cambios artísticos, ritmo, UX y sensaciones del control.
- [ ] Merge y tag únicamente tras permiso explícito del responsable.

### F.3 Matriz esencial de aceptación
| Área | Contrato mínimo |
| --- | --- |
| Clásico | endless + puntuación/récord + cosméticos; no perks |
| Familiar | 3 corazones, recuperación acotada, pacing amable |
| Arcade | 4 regiones, 4 bosses, build/XP/elecciones, ending |
| Guardados | versión, resiliencia y economías separadas |
| Animación | estados de Dante legibles y eventos sincronizados |
| UI | legible a escala base, mouse/gamepad/táctil donde proceda |
| Desktop | inicia/cierra/reintenta sin softlock |
| Android | instalación, pantalla táctil, orientación, suspensión, audio, saves |
| Web | arranque, input/audio, persistencia y memoria medidos |
| Derechos | solo contenidos con procedencia y permiso de distribución |

---

## G. Riesgos principales y mitigaciones

| Riesgo | Impacto | Mitigación |
| --- | --- | --- |
| Migrar con Arcade inestable | Duplicación de diseño y bugs | Gate P1/P2 y baseline SHA |
| Convertir Godot en un `main.py` nuevo | Mantenimiento difícil | Escenas pequeñas, recursos tipados, PR arquitectónico |
| Rehacer arte antes de validar físicas | Retrabajo | Vertical slice P5 con placeholders aprobados |
| Pixel art distorsionado en móvil | Jugabilidad y calidad | Viewport diseñado; no estirar sprites; QA ratio |
| Touch se siente peor que PC | Frustración familiar | POC en teléfono temprano y P15 específico |
| Guardados Legacy incompatibles | Pérdida de progreso | Política de saves e importador opt-in cuando sea posible |
| Fotos/recursos familiares en GitHub | Riesgo de privacidad | Repo privado, manifest y revisión de material |
| Licencias de terceros ambiguas | Bloqueo de publicación | Manifest por asset y auditoría pre-publicación |
| Expansión infinita de scope | Nunca publicar | No objetivos, gates, cambio de alcance documentado |
| Cambios de Godot durante desarrollo | Regresiones de motor | Pin 4.7.2 y upgrade como hito independiente |
| IA edita base incorrecta o hace merge | Pérdida/confusión de cambios | Worktrees aislados, SHA y autorización manual |
| CI pasa pero el juego falla a mano | Falsa seguridad | Human QA obligatoria y build real por plataforma |

---

## H. Decisiones abiertas que requieren prueba o aprobación

- Resolución base: preservar 400×300 para paridad o migrar a un viewport 16:9 manteniendo físicas/hitboxes; **no está decidido**.
- Motor/renderizador: verificar en WebGL2 y Android antes de seleccionar efectos visuales definitivos.
- Identidad Android definitiva y continuidad respecto al APK Pygame.
- Importación de partidas Legacy a Godot, especialmente en Android.
- Licencia del código y tipo de publicación de sprites/audio.
- Política de control táctil y si la orientación será siempre landscape.
- Orden final de los remasters cuando se tenga la Art Bible.
- Disponibilidad y compatibilidad de teléfono(s) de prueba.
- Publicación pública / Google Play vs distribución exclusivamente familiar.

---

## I. Primer sprint sugerido en el nuevo repositorio (sin implementar gameplay)

1. `DAN-001`: crear repo **privado** `HikariLucy/Dantopia`, rama `main`, README y descripción.
2. `DAN-002`: agregar `docs/DECISIONS/ADR-0001-engine.md`, fijar Godot 4.7.2 stable y razones de la elección.
3. `DAN-003`: copiar/adaptar este roadmap a `ROADMAP.md` y abrir milestones P0–P5 solamente.
4. `DAN-004`: crear GDD inicial de 3 modos y 4 regiones sin inventar mecánicas.
5. `DAN-005`: establecer puertas de Pygame F3.4/F3.5/F4/Familiar/RC/manifest.
6. `DAN-006`: documentar carpetas y reglas de assets/licencias; proteger `.gitignore`.
7. `DAN-011`: instalar editor estable en estación de desarrollo y anotar proceso.
8. `DAN-012`: construir POC de export vacío a Android y Web en rama de prueba.
9. `DAN-013`: abrir Godot y cambiar visualmente posición, colisión y animación de un Dante de prueba.
10. Registrar feedback humano: ¿resultó de verdad más fácil controlarlo desde el editor?

**Resultado esperado:** un repositorio auténtico con planificación y un laboratorio técnico, no un segundo juego medio terminado que compita con el equipo Pygame.

---

## J. Fuentes y referencias

**Código / roadmap propio**
- https://github.com/HikariLucy/FlappyDan (privado, accesible con permisos)
- `ROADMAP.md` del repositorio Legacy; ver F3.4, F3.5, F4 y F5.
- `build_android.sh` y `buildozer.spec`: auditar antes de prometer APK Legacy.

**Godot oficial**
- https://godotengine.org/download/archive/ (4.7.2-stable verificada al 13-10-2026)
- https://docs.godotengine.org/en/stable/tutorials/best_practices/project_organization.html
- https://docs.godotengine.org/en/stable/tutorials/best_practices/version_control_systems.html
- https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_android.html
- https://docs.godotengine.org/en/stable/tutorials/rendering/multiple_resolutions.html
- https://docs.godotengine.org/en/stable/tutorials/animation/animation_tree.html


---

## K. TABLERO VIVO CANONICO — FUENTE UNICA DE TAREAS

**Corte verificado: 2026-10-13.** Este apartado es el **único registro operativo** de hitos pendientes, en curso y completados para Dantopia, en sus implementaciones Legacy/Pygame y Godot. Las secciones A–J (incluidas las casillas antiguas de P0–P17) conservan la planificación de migración y sus especificaciones de referencia; **no deben interpretarse como el estado actualizado de ejecución** cuando difieran de K. El resumen ejecutivo remite a K y nunca sustituye sus casillas. No se crea una segunda lista oficial en el repositorio Legacy ni en herramientas personales.

**Situación de ramas verificadas:** F3.4/Claude en HikariLucy/FlappyDan, commit f4dd697 (rama feat/f3.4-claude-design-pass); Roguelite M0–B0/Codex en commit 6d2ddbb (rama feat/roguelite-foundation-m0). Las dos descienden de 5c19d05 y **no están integradas**. Los reportes señalan 2317 tests F3.4 y 205 tests + 560 subtests de M0–B0 por separado; **no existe aún un resultado de suite conjunta**. Las 8 ilustraciones familiares no están versionadas y no deben añadirse sin consentimiento explícito.

### K.0. Contrato del roadmap vivo

- **Un único libro mayor:** cada cambio de alcance, decisión, bloqueo, subtarea, evidencia y reapertura se registra **primero aquí**, mediante commit a este archivo. Los demás documentos pueden describir la implementación, nunca contradecir los estados operativos de K.
- **Identificadores estables:** usar prefijos GOV, F34, F35, MOD, ECO, FRU, POW, SKIN, UI, VAR, ROG, INT, QA, AND, GOD y REL; **no reutilizar ni renumerar IDs**. Si se divide una tarea, añadir subhitos como UI-04.1, UI-04.2; conservar el padre y sus criterios de salida.
- **Estados:** casilla [x] = implementado y respaldado con la evidencia indicada; [ ] = pendiente, en curso, bloqueado o en revisión, diferenciados mediante anotaciones **EN CURSO**, **BLOQUEADO**, **REVISIÓN HUMANA**, **NO INICIADO**. La aprobación artística parcial **no** equivale a aprobación integral del hito padre.
- **Reabrir sin borrar historia:** cambiar [x] a [ ] si hay una regresión confirmada, añadir motivo, fecha, evidencia y enlace al arreglo. No falsear métricas de progreso ocultando subhitos recién descubiertos.
- **Definition of Done:** objetivo observable + aceptación por modo/dispositivo + pruebas y regresión + evidencias/capturas sin material sensible + revisión de rendimiento cuando corresponda + decisión humana para experiencia, arte, audio y UX. El commit por sí solo **no** da HUMAN PASS.
- **Tareas nuevas:** proponer ID, área, objetivo, prioridad P0–P3, dependencia, criterio de aceptación y dueño operativo (Codex/Claude/humano). El responsable valida prioridad antes de ejecutar. Si cambia el alcance, documentar qué se aplaza o reemplaza.
- **No migrar errores de Legacy a Godot:** congelar comportamiento intencional, no el código ni defectos históricos. Godot sigue siendo una reconstrucción separada; no duplicar implementaciones sin pasar los gates.
- **Modo Clásico** = endless de récord y cosméticos, sin perks roguelite; **Familiar** = endless amable, corazones, recuperación y economía propia; **Arcade** = expedición con jefes, builds y final familiar. Mantener economías y reglas diferenciadas.
- **Plataformas vigentes:** escritorio Linux/Windows primero, luego APK Android instalable para familia. Web queda fuera de las prioridades; no dedicar sprints a Pygbag, browser ni despliegue web sin decisión nueva. La antigua fase P16 de web pasa a **PAUSADA**.
- **Recursos familiares y música:** imágenes privadas nunca a GitHub o paquetes públicos por defecto; «You Are My Sunshine» es elección creativa, **no** prueba de derechos de la grabación utilizada. Revisar composición, interpretación, sincronización y distribución antes de compartir un paquete.
- **Seguimiento:** cada sesión termina dejando actualizadas las casillas afectadas, evidencia/commit y el siguiente bloqueo. Actualizar el resumen solamente tras actualizar este archivo.

### K.1. Gobierno, respaldo e integración inmediata — prioridad P0

- [x] **GOV-01** Crear repositorio privado HikariLucy/Dantopia para visión, migración Godot y seguimiento central; mantener FlappyDan como producto Legacy vigente. **Evidencia:** repositorios existentes.
- [x] **GOV-02** Definir prioridad desktop → APK familiar Android; descartar trabajo web activo. **Evidencia:** decisión de producto 2026-10-13.
- [x] **GOV-03** Respaldar fundación Roguelite M0–B0 en rama aislada. **Evidencia:** 6d2ddbb.
- [x] **GOV-04** Respaldar código F3.4/Claude en rama aislada. **Evidencia:** f4dd697; no incluye ilustraciones privadas.
- [ ] **GOV-05** **REVISIÓN:** auditar el commit F3.4 de 847 archivos, incluidos arte, evidencias y el JSON de timeline; comprobar tamaño, contenido sensible, archivos sobrantes y espacios finales, sin reescritura destructiva del historial.
- [ ] **GOV-06** Copia cifrada o privada adicional de las ocho imágenes, hashes y música; asegurar traslado trabajo/casa sin perder originales y sin subirlos al repositorio.
- [ ] **GOV-07** Sincronizar en casa las dos ramas desde GitHub, verificar commits, estado limpio e integridad de assets locales; no alterar worktrees históricos.
- [ ] **GOV-08** Incorporar enlace visible al roadmap canónico desde repositorio Legacy; no mantener allí un segundo checklist divergente.
- [ ] **GOV-09** Mantener plantilla de actualización por sesión: IDs afectados, estado anterior/nuevo, causa, evidencia, riesgos, bloqueos, siguiente acción y responsable.
- [ ] **GOV-10** Reconciliar la planificación detallada P0–P17 y M0–M8 con este registro antes de iniciar cada fase; solo K determina estado actual.

**Salida GOV:** ambas líneas respaldadas y revisadas, originales privados conservados, base para integración reproducible.

### K.2. Cierre BUENAS NOCHES / CAMA (Legacy) — prioridad P0

- [x] **F34-01** Construir pasillo nocturno y habitación, capas, mobiliario y transición desde DUCHA. **Evidencia:** f4dd697 y visual polish.
- [x] **F34-02** Implementar CAMA con mamadera, pañal, cepillo y fase combinada en Arcade. **Evidencia:** vuelo determinista reportado y 2317 tests.
- [x] **F34-03** Animar jefes: mamadera 10 estados, pañal 10, cepillo 11; conservar hitboxes durante Animation Pass 3.0. **Evidencia:** README animation-pass-3.
- [x] **F34-04** Unificar a 2× pantufla, oso, libro, tren, móvil y cortinas; ambiente nocturno animado. **Evidencia:** pase 3.0, f4dd697.
- [x] **F34-05** Integrar 8 ilustraciones grandes como final de Arcade tras fase combinada, sin HUD, con fundidos, avances y confirmación de omisión. **Evidencia:** final ilustrado implementado y aprobación artística del usuario. **No implica permiso de distribución de imágenes.**
- [x] **F34-06** Integrar BUENAS NOCHES en Clásico y Familiar sin jefe ni final, usando políticas de obstáculos diferenciadas. **Evidencia:** tests de shared modes y capturas.
- [ ] **F34-07** **REVISIÓN HUMANA:** jugar el recorrido completo en pantalla real y otorgar o denegar HUMAN PASS integral F3.4 (ritmo, choque visible, pantalla pequeña, transición baño, dificultad y sensaciones).
- [ ] **F34-07.1** Evaluar recorrido nocturno y 4 fases en Arcade, con victoria/reintento y sin softlocks.
- [ ] **F34-07.2** Evaluar Clásico y Familiar en sesiones prolongadas, sin activar boss ni final.
- [ ] **F34-08** Redibujar torre de juguetes a densidad 2× con cobertura del colisionador y comparación visual.
- [ ] **F34-09** Reparar estrella diminuta del emblema HUD CAMA y centelleo de ambiente; validar a resolución efectiva.
- [ ] **F34-10** **PROPUESTA, NO AUTORIZADA PARA IMPLEMENTACIÓN:** replantear el chorro pressure de mamadera desde la tetina. Hacer prototipo, comparar geometría/hitbox y esquivabilidad con antes/después; separar de arreglos puramente visuales y pedir aprobación antes de cambiar colisiones.
- [ ] **F34-11** Repetir benchmark completo posterior a la optimización del pañal, con mediciones comparables y p95; analizar picos de primera generación de cachés.
- [ ] **F34-12** Confirmar límites de memoria y precarga del final ilustrado en hardware objetivo; no confundir prueba desktop con Android.
- [ ] **F34-13** Marcar HUMAN PASS del final ilustrado como aprobación **artística parcial** y verificar que la versión exacta (duración, imágenes, música, salto) sea la reproducida en la build final.

**Salida F34:** juego nocturno técnicamente consolidado y aprobado por humanos, no solo tests verdes.

### K.3. Modos infinitos: identidad y diferenciación — prioridad P1

- [ ] **MOD-01** Inventariar reglas reales de Clásico y Familiar desde código y pruebas: velocidad, gaps, corazones, recuperación, obstáculos, récord, monedas, tiendas, tutorial y duración; no describir deseos como implementados.
- [ ] **MOD-02** Documentar promesa de jugador: Clásico = puntuación y dominio; Familiar = accesibilidad, disfrute y colección; Arcade = viaje y build.
- [ ] **MOD-03** Medir sesiones de 5/15/30 min para cada endless: aburrimiento, dificultad, repetición y deseo de reintentar.
- [ ] **MOD-04** Ajustar Clásico sin añadir perks de Arcade: curva, riesgo/recompensa, variedad de escenarios, lectura de récord y motivación de mejora técnica.
- [ ] **MOD-05** Dar identidad propia a Familiar más allá de menor dificultad: ritmo amable, ayudas explicadas, menos frustración, protección accesible, hitos positivos.
- [ ] **MOD-05.1** Probar claridad de los tres corazones, invulnerabilidad, curación y recuperación, con feedback infantil comprensible.
- [ ] **MOD-05.2** Auditar política nocturna: cortinas y torres sólidas, sin móvil/torre Montessori; decidir si necesita variedad adicional sin romper accesibilidad.
- [ ] **MOD-05.3** Diseñar pequeñas metas de sesión y celebraciones no intrusivas; distinguir experiencia cozy de farmeo sin fin.
- [ ] **MOD-06** Mantener fondos, obstáculos y render compartidos cuando corresponda, pero políticas de dificultad/recompensa separadas.
- [ ] **MOD-07** Validar con jugadores nuevos: identificar el modo sin ver su título; medir diversión, frustración y ganas de volver.
- [ ] **MOD-08** Probar que Clásico/Familiar no disparan bosses, cinemática Arcade ni perks exclusivos en regresiones.

**Salida MOD:** ambos infinitos se perciben diferentes y tienen razones propias para rejugar.

### K.4. Economía, monedas, frutas y deseos de colección — prioridad P1

- [ ] **ECO-01** Inventariar tres monederos, tablas de recompensas, compras, balances, perfil, persistencia y fuentes/sumideros por modo.
- [ ] **ECO-02** Auditar con partidas reales qué compra la gente, qué ignora y cuánto tarda en lograr su primer desbloqueo interesante.
- [ ] **ECO-03** Definir rol concreto de moneda por modo: persistencia, gasto, premios, límites y relación con récord; no juntar wallets accidentalmente.
- [ ] **ECO-04** Definir rol **actual** de fruta por modo y distinguirlo de ideas nuevas (score/combo/carga/curación son propuestas hasta validación).
- [ ] **ECO-05** Hacer inconfundibles monedas vs frutas en silueta, audio, VFX, tamaño, animación, HUD y mensajes de recogida.
- [ ] **ECO-06** Añadir vista previa del siguiente premio asequible en tiendas, precios transparentes y metas cercanas.
- [ ] **ECO-07** Diseñar recompensas deseables de tres clases: expresión visual, colección y capacidades autorizadas por modo (sin boosts en Clásico).
- [ ] **ECO-08** Simular curvas novato/intermedio/experto: ganancias/hora, primera compra, compras duplicadas, granjas, inflación y riesgo de bloqueo.
- [ ] **ECO-09** Ensayar fallo de escritura/partida antigua/perfiles y garantizar que no hay doble cobro ni premios fantasma.
- [ ] **ECO-10** Test de comprensión sin instrucciones: «¿Para qué sirve esta fruta? ¿Para qué sirven estas monedas? ¿Qué comprarías?».

**Salida ECO:** economía legible, separada, motivadora y verificable; no incentivar compras sin valor.

### K.5. Frutas: variedad significativa, no ruido — prioridad P1/P2

- [ ] **FRU-01** Auditar frutas existentes, pickups, rarezas, zonas de aparición y economía actual en los tres modos.
- [ ] **FRU-02** Diseñar catálogo inicial máximo de 4–6 **tipos funcionalmente distinguibles**, solo si aporta lectura/jugabilidad; propuestas: manzana, plátano, frutilla, uvas, naranja y fruta rara.
- [ ] **FRU-03** Elegir comportamiento y efectos por modo, evitando que un pickup cambie balance o economía sin autorización.
- [ ] **FRU-04** Separar aparición puramente cosmética de efectos mecánicos; si se necesitan sólo siluetas variadas, no inventar cinco monedas diferentes.
- [ ] **FRU-05** Diseñar pixel art coherente y animaciones reconocibles; paleta y escala testeadas a velocidad de vuelo.
- [ ] **FRU-06** Especificar rarezas, tablas spawn y antirrepetición, RNG determinista y compatibilidad con colecciones.
- [ ] **FRU-07** Probar feedback por fruta (visual/sonoro/UI), colisión real, accesibilidad de color y rendimiento móvil.
- [ ] **FRU-08** Medir monotonía y balance antes/después; retirar tipos que solo ensucian la lectura.

**Salida FRU:** más variedad perceptible sin coleccionables redundantes ni descontrol de recompensas.

### K.6. Poderes, builds y habilidades memorables — prioridad P1

- [ ] **POW-01** Inventariar poderes reales, requisitos, duración, límites, feedback, sinergias y bugs existentes antes de proponer nuevos.
- [ ] **POW-02** Clasificarlos por supervivencia, control, recompensa o fantasía y registrar si afectan elección real.
- [ ] **POW-03** Detectar redundantes, débiles, obligatorios o invisibles durante la partida con registros de elecciones.
- [ ] **POW-04** Rediseñar presentación: nombre, icono, descripción de una línea, activación, feedback, finalización y prueba de lectura.
- [ ] **POW-05** Prototipar tres poderes de alto impacto visual/mecánico para Arcade sin romper vuelo ni colisiones.
- [ ] **POW-06** Prototipar combinaciones/sinergias con límites y caps explícitos, evitando exploits de monedas o invulnerabilidad perpetua.
- [ ] **POW-07** Mantener Clásico sin perks roguelite y explicar qué ayudas sí corresponden a Familiar.
- [ ] **POW-08** Comparar build novato, equilibrado y experto en varios seeds; ninguna elección debe ser obligatoria.
- [ ] **POW-09** Antes de aprobar un poder nuevo: pruebas deterministas, balance, ahorro de partida, performance y HUMAN PASS.

**Salida POW:** poderes fáciles de entender y que inspiran «otra run», sin falsear balance.

### K.7. Skins oficiales de Dante — prioridad P1

- [x] **SKIN-01** Contar con referencia visual inicial de Dante rubio aprobado y variante Dino (idle, subida +10 y caída -10). **Evidencia:** lámina entregada por el usuario; no presupone atlas completo ni integración.
- [ ] **SKIN-02** Inventariar selector y cosméticos existentes, modelo base, animaciones, superposición de equipos y consistencia en 3 modos.
- [ ] **SKIN-03** Crear Art Bible de Dante: silueta, perfil, contorno, paleta, densidad 2×, pivotes, tamaños, ojos, expresiones y política de animación.
- [ ] **SKIN-04** Decidir si skins son atlas completos o capas combinables (base, cabeza, ropa, accesorios, estela) tras comparar coste y complejidad.
- [ ] **SKIN-05** Completar **Dino** y **Base** en todos los estados de vuelo autorizados, no solo los tres frames de referencia.
- [ ] **SKIN-06** Diseñar y aprobar primera colección: Buenas Noches, Toalla/Baño, Explorador, Estrellita; adicionales solo tras medir coste.
- [ ] **SKIN-07** Definir desbloqueo por logro/tienda, precio por economía correspondiente, rareza solo si aporta valor; ninguna skin de Clásico da ventaja.
- [ ] **SKIN-08** Selector en menús con vista previa animada, estados comprado/equipado/bloqueado y fallback a Base ante assets faltantes.
- [ ] **SKIN-09** Verificar contornos, hitboxes sin cambios, audio/FX, legibilidad ante escenarios, skins y accesorios superpuestos.
- [ ] **SKIN-10** Ensayar compras, equipamiento, perfil nuevo, guardado y migraciones antes de dar HUMAN PASS visual.

**Salida SKIN:** Dante reconocible en todas sus variantes y deseo real de coleccionarlas.

### K.8. UI/HUD 2.0: identidad Dantopia — prioridad P1

- [ ] **UI-01** Capturar todos los menús, juego, tienda, selección, bosses, pausa, derrota y victoria en desktop y viewport pequeño.
- [ ] **UI-02** Elaborar auditoría de «ruido»: márgenes, cajas excesivas, overlays, contrastes, iconos inconsistentes, fuentes y lectura en movimiento.
- [ ] **UI-03** Definir lenguaje visual: paleta cálida/nocturna, bordes pixel-art, jerarquía tipográfica, grid, espaciado y escalas enteras coherentes.
- [ ] **UI-04** Diseñar tres perfiles de HUD: Clásico competitivo, Familiar sencillo y Arcade informativo, con componentes reutilizados, no copias inconexas.
- [ ] **UI-04.1** Clásico: score/récord y feedback de fruta/moneda; eliminar datos que no sirven durante el vuelo.
- [ ] **UI-04.2** Familiar: corazones, protección y ayudas prioritarias; reducir la presión visual.
- [ ] **UI-04.3** Arcade: estado de build, jefe y expedición, recursos separados y advertencias contextuales.
- [ ] **UI-05** Diferenciar pickups, poderes y estados de combate mediante iconografía consistente a tamaño real.
- [ ] **UI-06** Rehacer selección de modo, menú principal, tiendas, selector Dante, HUD de jefe, pausa, Game Over y victoria bajo un mismo sistema.
- [ ] **UI-07** Diseñar botones/objetivos táctiles con áreas de pulsación y safe areas, sin tapar trayectoria de Dante.
- [ ] **UI-08** Probar contraste, lectura con imágenes densas, estrés visual, escala móvil y FPS; no dejar efectos del UI afectando gameplay.
- [ ] **UI-09** HUMAN PASS por pantalla y regresión sobre las tres economías y el final ilustrado.

**Salida UI:** interfaz identificable como Dantopia, limpia y entendible durante el vuelo.

### K.9. Obstáculos, regiones y ritmo / F3.5 y F4 — prioridad P1

- [ ] **VAR-01** Inventariar todas las familias de obstáculos y pesos por región/modo, incluidas 11 localizaciones de Clásico/Familiar.
- [ ] **VAR-02** Completar pulido pendiente de torre de juguetes, estrellas y problemas visuales admitidos en F3.4.
- [ ] **VAR-03** Diseñar antirrepetición con RNG testeado y transiciones más variadas sin crear obstáculos ilegibles.
- [ ] **VAR-04** Analizar telegraph, contraste y coherencia de hitbox para cada obstáculo y boss.
- [ ] **VAR-05** Balancear dificultad de los tres modos con perfiles observados, no solo autopilot; preservar el final familiar de Arcade.
- [ ] **F35-01** Integrar partida Arcade completa TIERRA → PATIO → CASA/DUCHA → BUENAS NOCHES/CAMA en una sola experiencia manual.
- [ ] **F35-02** Verificar todas las transiciones, elecciones, recompensas, vida, derrotas/reinicio, victoria y guardado sin bloqueos.
- [ ] **F35-03** Probar al menos novato/intermedio/experto y registrar balance, tiempo y frustración.
- [ ] **F35-04** Completar criterios de aceptación F3.5; no declarar completado por el solo vuelo automático.
- [ ] **VAR-06** F4: auditar economía y accesibilidad específica de Clásico, cosméticos y contenido infinito antes de ampliar catálogos.

**Salida VAR/F35:** Arcade completo jugable y endless con variedad legible.

### K.10. Roguelite / Rincón de Dante — prioridad P0 integración, P1 desarrollo

- [x] **ROG-01** Completar auditoría, diseño de progresión, hub DEMO y simulación M0–B0 en módulos aislados. **Evidencia:** 6d2ddbb; 205 tests y 560 subtests reportados.
- [ ] **ROG-02** Integrar primero la base F3.4 en rama de integración nueva; revisar funciones y contratos compartidos, sin activar B1.
- [ ] **ROG-03** Resolver decisiones B1 sobre owner único, saves reparables, respaldo flat, errores de escritura, concurrencia y congelamiento económico.
- [ ] **ROG-04** Reauditar los ~25 sitios/19 funciones legacy mutadoras sobre la base integrada y reconstruir pruebas AST ante cualquier cambio.
- [ ] **ROG-05** Implementar owner desktop único transaccional con respaldo y pruebas de compatibilidad, sin tocar datos de usuario reales durante pruebas.
- [ ] **ROG-06** Migrar compras, perfiles, ajustes, premios y récords de forma atómica, con tres monederos intactos y efectos solo tras confirmación.
- [ ] **ROG-07** Implementar reconciliación del progreso no guardado ante fallo, sin doble acreditación; documentar pérdida residual por cierre inesperado hasta M3.
- [ ] **ROG-08** Conectar Rincón real exclusivamente a Arcade, con navegación, estaciones y vuelta a expedición; Clásico/Familiar mantienen sus tiendas.
- [ ] **ROG-09** M2: revisar vida y protección, fuentes de daño, recuperación y efectos de build.
- [ ] **ROG-10** M3: ledger de recompensas persistentes e idempotentes por perfil.
- [ ] **ROG-11** M4: mejoras permanentes con precios, límites, compra y rollback.
- [ ] **ROG-12** M5: builds, elecciones y sinergias memorables en Arcade.
- [ ] **ROG-13** M6: arte y animación del hub con identidad coherente y tests de navegación.
- [ ] **ROG-14** M7: simulación de balance y playtests; medir progreso de primeras horas.
- [ ] **ROG-15** Congelar y auditar integración final del roguelite con regiones, jefes y final ilustrado.

**Salida ROG:** progreso seguro y atractivo sin regresiones ni compras fantasmas.

### K.11. Integración, QA y deuda técnica — prioridad P0/P1

- [ ] **INT-01** Comparar cambios F3.4 vs Roguelite a partir del ancestro 5c19d05 y registrar inventario de rutas compartidas.
- [ ] **INT-02** Crear rama nueva de integración desde la revisión F3.4 aprobada; incorporar commits M0–B0 sin editar las fuentes privadas.
- [ ] **INT-03** Ejecutar pruebas de Claude y Codex juntas; comparar IDs de tests, resultados y fallos del entorno.
- [ ] **INT-04** Smoke real en Arcade/CAMA, Clásico y Familiar, incluyendo menús, guardado sintético, recompensas y salida.
- [ ] **INT-05** Revisar que 8 ilustraciones privadas sigan ausentes de Git; plan de entrega local autorizado para un paquete familiar.
- [ ] **INT-06** Aprobar la rama integrada antes de B1; no hacer merge a main por inercia.
- [ ] **QA-01** Perfilado de frame: rutas, jefes, HUD, cachés, primercarga y p95; atribuir cuellos de botella.
- [ ] **QA-02** Pruebas de regresión por modo y casos borde de perfiles, input mantenido, reinicio, victoria y carga.
- [ ] **QA-03** Capturas golden, evidencias antes/después y checklist HUMAN PASS sin material sensible publicado.
- [ ] **QA-04** Matriz de resoluciones y dispositivos; medir desktop primero, después Android físico.
- [ ] **QA-05** Registrar deuda técnica con impacto y condiciones para reabrir, no dejarla como «terminado» por pasar tests.
- [ ] **QA-06** Cerrar las tareas solo tras aprobación humana cuando afecten experiencia, claridad o dificultad.

**Salida INT/QA:** integración estable y mediciones repetibles, sin mezclar responsabilidad de ramas.

### K.12. APK Android y entrega familiar — prioridad P1 tras gate desktop

- [x] **AND-01** Elegir APK Android instalable directamente para compartir con familia, sin Play Store inicialmente; Web no es prioridad. **Evidencia:** decisión del usuario.
- [ ] **AND-02** Evaluar coste/viabilidad de APK Legacy Pygame vs exportar APK desde Godot; no emprender dos ports completos.
- [ ] **AND-03** Prueba de control táctil real (vuelo, interacción, mantener/soltar, menús, pausa, skip de cinemática).
- [ ] **AND-04** Benchmark Android real en teléfono de referencia: FPS mediano/p95, RAM, primera carga, audio, calor y batería.
- [ ] **AND-05** Decidir resolución base, escalado y safe areas según pantallas y orientación.
- [ ] **AND-06** Diseñar rutas persistentes Android, permisos mínimos, perfiles, backups y actualizaciones sin pérdida de save.
- [ ] **AND-07** Validar reproducción de las 8 ilustraciones en paquete privado autorizado; verificar tamaño/memoria, consentimiento de distribución y privacidad.
- [ ] **AND-08** Auditar derechos de composición y **grabación concreta** de «You Are My Sunshine» para sincronizar y redistribuir en APK; si no hay licencia, usar composición/grabación autorizada o música original.
- [ ] **AND-09** Configurar paquete, icono, identidad, versión, firmado y keystore seguro fuera de Git.
- [ ] **AND-10** Generar APK reproducible y smoke en dispositivo físico sin tienda.
- [ ] **AND-11** Playtest familiar con instalación, progreso entre sesiones, offline, suspensión/reanudación y actualización.
- [ ] **AND-12** Gate de publicación: privacidad, licencias, cero bugs bloqueantes y aprobación humana del instalador.

**Salida AND:** APK reproducible y jugable de forma autónoma, no solo un archivo generado.

### K.13. Migración Godot y futuro — prioridad P2 después del cierre Legacy

- [x] **GOD-01** Crear proyecto/repositorio privado Dantopia y roadmap inicial P0–P17. **Evidencia:** repositorio actual.
- [ ] **GOD-02** Cerrar Legacy F3.4/F3.5/F4 y baseline de referencia antes de trasladar gameplay.
- [ ] **GOD-03** Congelar commit/tag, manifest de assets, reglas de los tres modos y golden fixtures reproducibles.
- [ ] **GOD-04** Probar editor Godot con laboratorio aislado, movimiento, colisión, animación y cambios de asset visuales.
- [ ] **GOD-05** Vertical slice TIERRA con equivalencia de controles, física y loop; HUMAN PASS antes del port masivo.
- [ ] **GOD-06** Reconstruir Clásico y Familiar con sistemas compartidos pero economía y dificultad separadas.
- [ ] **GOD-07** Reconstruir Arcade, cuatro regiones/jefes, builds, final ilustrado y transiciones desde la especificación Legacy.
- [ ] **GOD-08** Migrar UI/HUD 2.0, skins y poderes aprobados como recursos configurables en editor, no copiar render de Pygame.
- [ ] **GOD-09** Portar guardado con formato versionado/importación opcional y prueba de reversión.
- [ ] **GOD-10** QA paridad, desktop y Android, arte/audio/licencias, empaquetado y release candidate.
- [ ] **GOD-11** Metroidvania del mundo de sueños: idea narrativa preservada como **juego distinto**, no etapa obligatoria de Dantopia actual.
- [ ] **GOD-12** Export web P16: **PAUSADA** salvo decisión explícita nueva; no detener APK por esta tarea.

**Salida GOD:** edición y control visual reales desde Godot, sin duplicar el desarrollo actual.

### K.14. Release, transparencia y mantenimiento — prioridad P2

- [ ] **REL-01** Crear matriz de alcance congelado para versión familiar: qué incluye y qué queda para después.
- [ ] **REL-02** Registrar CHANGELOG con hitos, revisiones, reversiones y bugs solucionados.
- [ ] **REL-03** Revisar audio, consentimiento de material familiar, autoría y derechos antes de distribuir APK.
- [ ] **REL-04** Pruebas de instalación, primer inicio, juego offline, cierre forzoso, reinicio y upgrade.
- [ ] **REL-05** Publicar primero beta familiar privada, recopilar comentarios concretos y priorizarlos aquí.
- [ ] **REL-06** Decisión posterior sobre Play Store, licencia pública y alcance comercial; no asumir publicación por defecto.
- [ ] **REL-07** Revisar backlog mensualmente: descartar/posponer ideas sin valor y priorizar bugs reales de jugadores.

### K.15. Gate actual, próximos pasos y control de cambios

**Gate de hoy:** F3.4 (f4dd697) y Roguelite M0–B0 (6d2ddbb) están respaldados **separadamente**; la **integración controlada INT-01..INT-06 está pendiente**. La cinemática ilustrada tiene aprobación artística; la aceptación integral de F3.4 requiere revisión manual; Android no está validado. No iniciar B1 antes de INT-06 y ROG-03.

**Orden recomendado, no secuencia rígida:** GOV-05/06/07 → INT-01/02/03/04/05/06 → ROG-03..08. En paralelo, sin alterar contratos compartidos: MOD-01/02, ECO-01/04, POW-01, SKIN-02/03, UI-01/02. Después pruebas de producto reales y priorización. **Si una regresión obliga a volver, abrir subhito y mantener registro: avanzar no implica no retroceder.**

**Plantilla obligatoria al actualizar una tarea:**

- ID y título: ...
- Estado: pendiente / en curso / bloqueado / revisión / implementado / human pass.
- Evidencia (commit, prueba, captura, observación humana): ...
- Dependencias, riesgo, responsable y criterio de salida: ...
- Cambio de alcance / subtareas nuevas (si corresponde): ...
- Fecha del cambio y próximo paso: ...

**Resumen de lectura rápida:** [docs/RESUMEN_EJECUTIVO.md](docs/RESUMEN_EJECUTIVO.md). Si difiere del estado aquí escrito, prevalece **esta sección K de ROADMAP.md**.

**Fin del tablero canónico.**
