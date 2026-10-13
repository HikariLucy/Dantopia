# P3 — Laboratorio guiado Godot (primeros ejercicios)

> **No es el juego migrado.** Es un ejercicio de aprendizaje y viabilidad. La primera escena \`scenes/lab.tscn\` contiene solamente texto.

## Preparación
- Instalar Godot **4.7.2 stable** y confirmar versión de los export templates.
- Clonar \`https://github.com/HikariLucy/Dantopia.git\`.
- Abrir \`project.godot\` desde Project Manager.
- Abrir \`scenes/lab.tscn\` y ejecutar la escena principal con F6/F5.
- Registrar sistema operativo, versión Godot y si la escena abre sin errores.

## Lección 1 — Inspector y árbol de escenas
- Seleccionar \`Title\` y cambiar temporalmente el texto. Revertir el cambio.
- Mover y redimensionar un \`Control\`; distinguir escena e instancia.
- Usar Remote Scene Tree durante ejecución; entender transformaciones.
- Guardar una captura del editor y anotar dudas.

## Lección 2 — Dante Pixel como escena aislada
- Elegir solo un sprite original apto para port (anotar licencia/origen).
- Crear \`scenes/characters/dante_lab.tscn\` con \`Node2D\` + \`AnimatedSprite2D\` o \`Sprite2D\`.
- Configurar texturas sin blur y observar su escala.
- Agregar \`CollisionShape2D\` solo con dimensiones verificadas.
- Exponer al menos dos propiedades editables sin cambiar reglas globales.
- Animar \`idle\` y \`fly\` con frames y duración correctos.

## Lección 3 — Input sin acoplamiento
- Definir acción \`fly\` en Input Map y probar teclado/mando donde esté disponible.
- Input táctil es otro adaptador; no crear una segunda física para Android.
- Escribir una prueba conceptual de press/release/pause.

## Lección 4 — Web y Android mínimos
- Instalar export templates del mismo Godot.
- Comprobar export HTML5 desktop en navegador, anotar errores.
- Para Android, configurar OpenJDK y SDK, crear APK de prueba sin secretos versionados.
- Instalar APK en teléfono físico, verificar orientación, touch, audio y rendimiento.
- Etiquetar NO PROBADO cualquier resultado que no se haya ejecutado.

## G2: criterio de salida
El propietario puede editar sprites y sus animaciones desde Godot; la escena mínima corre en escritorio, se conoce la viabilidad Web/Android y hay evidencia de pruebas. No supone G0/G1 aprobadas.
