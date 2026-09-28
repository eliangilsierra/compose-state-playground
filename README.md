# Compose State Playground

Two small, focused Jetpack Compose exercises exploring different Compose **state management** patterns: local composable state versus `ViewModel`-hoisted state with derived (computed) values.

## Screens

### 🎲 Dice Roller (`DadoScreen`)
- Local UI state (`remember { mutableIntStateOf(1) }`) scoped entirely to the composable — no `ViewModel` needed for such a simple, screen-local interaction.
- Demonstrates mapping an `Int` state value to a drawable resource and triggering recomposition on a button click.

### 🧮 Tax Calculator (`FormTax` + `FormTaxViewModel`)
- State hoisted into a `ViewModel` (`inputCantidad`, `inputPorcentaje`, `switchRedondear`) so it survives configuration changes.
- A **derived/computed property** (`impuesto`) recalculates the result from the current state on every read, instead of being stored and manually synchronized — a common Compose pitfall this exercise avoids.
- Unidirectional data flow: the `TextField`/`Switch` composables only report events (`onValueChange`, `onCheckedChange`); the `ViewModel` is the single source of truth.

## Tech stack

| Layer | Technology |
|---|---|
| UI | Jetpack Compose, Material 3 |
| State management | Compose `remember`/`mutableStateOf` (local) and `ViewModel` + Compose `State` (hoisted) |
| Language | Kotlin |
| Build | Gradle Kotlin DSL, version catalogs (`libs.versions.toml`) |

## Getting started

**Requirements:** Android Studio (current stable), JDK 17+, Android SDK with API 36.

```bash
git clone https://github.com/eliangilsierra/compose-state-playground.git
cd compose-state-playground
./gradlew assembleDebug
```

Open the project in Android Studio and run the `app` configuration on an emulator or device (minSdk 26). Both screens are also annotated with `@Preview` for quick inspection in the IDE.

## Academic context

Developed as an exercise for the **Desarrollo de Aplicaciones Móviles** course, taught by professor **Fabián Enrique Suárez Carvajal** — Maestría en Gestión, Aplicación y Desarrollo de Software (MGADS), Universidad Autónoma de Bucaramanga (UNAB).

## License

MIT — see [LICENSE](LICENSE).
