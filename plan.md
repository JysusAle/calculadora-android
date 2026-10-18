# Plan: calculadora-android — Calculadora interactiva con formularios dinámicos

## Decisiones tomadas
- **UI:** XML + ViewBinding, mismo estilo que **EsPrimo** (AppCompatActivity, ConstraintLayout, Material, edge-to-edge, `EditText.error` + Toast para errores).
- **Stack clonado de EsPrimo:** Gradle 9.6.0, AGP 9.4.1, Java 11, compileSdk/target 37, **minSdk 28** (lo pide el enunciado; EsPrimo usa 26), Kotlin integrado en AGP 9.
- **4 cálculos:** BMI (2 datos + clasificación), Ley de Ohm (2), **Interés simple (3 datos ✓)**, Distancia (2).
- **Menú:** Spinner desplegable. **Fórmulas:** 4 PNG generados con Python/PIL (pizarra blanca, texto negro).
- **Paquete:** `com.amaurypm.calculadora`. **Idiomas:** español (`values/`) + inglés (`values-en-rUS/`, igual que EsPrimo).

## Estructura objetivo (idéntica a EsPrimo)
```
calculadora-android/          ← ya existe con README (enunciado) y .gitignore
├── build.gradle.kts, settings.gradle.kts ("Calculadora"), gradle.properties
├── gradle/ (wrapper 9.6.0 + libs.versions.toml copiados de EsPrimo)
├── gradlew, gradlew.bat
└── app/
    ├── build.gradle.kts (namespace/applicationId com.amaurypm.calculadora, viewBinding)
    └── src/main/
        ├── AndroidManifest.xml
        ├── java/com/amaurypm/calculadora/MainActivity.kt
        └── res/
            ├── layout/activity_main.xml
            ├── values/ (strings es, colors, themes, arrays)
            ├── values-en-rUS/strings.xml
            ├── drawable/ (4 fórmulas PNG + ic_launcher_foreground)
            ├── mipmap-*/ (ícono personalizado adaptivo)
            └── xml/ (backup rules)
```

## Fases (parte por parte)

### Fase 1 — Esqueleto Gradle (copiar y adaptar de EsPrimo)
- Copiar wrapper, `.gitignore` raíz/app, `build.gradle.kts` raíz, `settings.gradle.kts`, `gradle.properties`, `libs.versions.toml`.
- Renombrar proyecto a "Calculadora", `minSdk = 28`, carpeta java `com/amaurypm/calculadora`.

### Fase 2 — Layout + textos
- `activity_main.xml`: título, **Spinner**, **ImageView** (`ivFormula`), 3 `EditText` (campo1/campo2/campo3 con labels y unidades en el hint), botón **Calcular**, `TextView` resultado. Campo3 arranca `gone`.
- `strings.xml` (es) + `values-en-rUS/strings.xml`: todos los textos, hints, unidades, errores, `string-array` con las 4 opciones, clasificaciones de BMI. **Cero textos hardcodeados.**
- `colors.xml`/`themes.xml` al estilo EsPrimo (con color states del botón).

### Fase 3 — Fórmulas PNG + ícono
- Script Python/PIL → `formula_bmi.png`, `formula_ohm.png`, `formula_interes.png`, `formula_distancia.png` en `drawable/`.
- Ícono adaptivo personalizado (foreground vector sencillo tipo "ƒx"/calculadora + background de color).

### Fase 4 — Lógica en `MainActivity.kt`
- `Spinner.onItemSelected` → función `configurarFormulario(posicion)`: cambia labels/hints/unidades (`setText` de recursos), muestra/oculta campo3, pone la imagen de fórmula, limpia errores y resultado.
- `btnCalcular.setOnClickListener` → `validar()` según el cálculo activo; si hay error: `EditText.error` + foco, **no se calcula**; si todo OK → cálculo + resultado con unidad (2 decimales) en el `TextView`.
- Validaciones por cálculo:

| Cálculo | Campos | Fórmula | Validaciones particulares |
|---|---|---|---|
| BMI | peso (kg), altura (m) | BMI = m/h² | peso 1–300, altura 0.5–2.5; clasificación (bajo/peso normal/sobrepeso/obesidad) |
| Ohm | corriente (A), resistencia (Ω) | V = I·R | ambos > 0 |
| Interés simple | capital ($), tasa (%), tiempo (años) | I = C·r·t | capital > 0, tasa 0–100, tiempo > 0 |
| Distancia | velocidad (km/h), tiempo (h) | d = v·t | ambos ≥ 0 |

- `enableEdgeToEdge` + insets igual que EsPrimo; `windowSoftInputMode="adjustResize"` en el manifest.

### Fase 5 — Verificación
- `gradlew.bat assembleDebug` + revisión de que no queden textos hardcodeados.
- Commits incrementales por fase.

## Estado
- [x] Fase 1 — Esqueleto Gradle (BUILD SUCCESSFUL, minSdk 28, paquete com.amaurypm.calculadora)
- [ ] Fase 2 — Layout + textos
- [ ] Fase 3 — Fórmulas PNG + ícono
- [ ] Fase 4 — Lógica MainActivity
- [ ] Fase 5 — Verificación
