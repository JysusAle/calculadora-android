# Calculadora interactiva con formularios dinámicos

**Ejercicio 1 — Computación Móvil** · Android · Kotlin · Interfaz XML

Aplicación Android que permite seleccionar cuatro tipos de cálculos desde un menú y resolverlos mediante un formulario que se adapta al cálculo elegido, con validación de datos previa y presentación clara del resultado.

## Cálculos disponibles

| Opción | Fórmula | Datos de entrada | Resultado |
|---|---|---|---|
| Índice de masa corporal | `IMC = m / h²` | Peso (kg), Altura (m) | Valor + clasificación (bajo peso / peso normal / sobrepeso / obesidad) |
| Ley de Ohm | `V = I × R` | Corriente (A), Resistencia (Ω) | Voltaje en V |
| Interés simple | `I = C · r · t` | Capital ($), Tasa (%), Tiempo (años) | Interés ganado |
| Distancia recorrida | `d = v × t` | Velocidad (km/h), Tiempo (h) | Distancia en km |

El interés simple es el cálculo con **tres datos de entrada**; los demás requieren dos.

## Qué incluye

- **Menú de selección** (Spinner) con las 4 opciones de cálculo.
- **Formulario dinámico**: al cambiar de opción se actualizan etiquetas, unidades (sufijo de cada campo), ayudas al usuario, la imagen de la fórmula correspondiente y la cantidad de campos visibles (el tercer campo solo aparece cuando se necesita).
- **Validación antes de calcular**, específica para cada cálculo:
  - Campos obligatorios y valores numéricos válidos.
  - Restricción de positivos / no negativos / distintos de cero.
  - Rangos: peso 1–300 kg, altura 0.5–2.5 m, tasa 0–100 %, corriente y resistencia > 0, capital > 0, tiempo > 0.
  - El error se muestra en el campo correspondiente y **no se realiza ningún cálculo** mientras haya datos incorrectos.
- **Resultado** con valor calculado, unidad correspondiente y clasificación cuando aplica.
- **Ícono personalizado** (calculadora adaptativa con soporte de theming).
- **Sin textos hardcodeados**: todos los textos viven en recursos de cadenas.

## Idiomas

La app está en **español** (por defecto) e **inglés**, mediante recursos de texto:

```
app/src/main/res/
├── values/strings.xml          ← español
└── values-en-rUS/strings.xml   ← inglés
```

Cambia el idioma del dispositivo para verificarlo.

## Tecnología

- **Kotlin** + **XML** (Views) con **ViewBinding**
- Material 3 (`TextInputLayout`, Spinner, Button)
- `minSdk 28` · `targetSdk 37` · Gradle 9.6.0 · AGP 9.4.1
- Estructura: una sola actividad (`MainActivity`) con `NestedScrollView`.

## Estructura del proyecto

```
app/src/main/
├── AndroidManifest.xml
├── java/com/amaurypm/calculadora/
│   └── MainActivity.kt        # formulario dinámico, validación y cálculos
└── res/
    ├── layout/activity_main.xml
    ├── values/ (strings, colors, themes)
    ├── values-en-rUS/strings.xml
    ├── drawable-xhdpi/formula_*.png   # imágenes de fórmulas
    ├── drawable/ic_launcher_*.xml     # ícono adaptativo
    └── mipmap-*/                      # variantes de densidad
```

## Cómo ejecutar

1. Abrir la carpeta en **Android Studio**.
2. Conectar un dispositivo con **depuración USB** activada (o usar un emulador con API ≥ 28).
3. Presionar **Run ▶**.

También puede instalarse el APK generado en `app/build/outputs/apk/debug/app-debug.apk`.

## Prueba rápida

1. Seleccionar **Interés simple** → verificar que aparece el tercer campo (Tiempo).
2. Dejar un campo vacío y presionar **Calcular** → error en el campo, sin resultado.
3. Escribir tasa `150` → rechazo por rango (0–100).
4. IMC con peso `70`, altura `1.75` → `IMC: 22.86 — Peso normal`.
