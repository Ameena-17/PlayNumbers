# PlayNumbers 🌌

**PlayNumbers** is a highly interactive, state-of-the-art Flutter mathematical playground application. It allows users to dynamically highlight numbers from 1 to 100 based on core arithmetic patterns and advanced number sequences, utilizing a premium glassmorphic cosmic-dark interface, buttery-smooth animations, and reactive state bindings.

Designed with high-quality coding practices, this application follows the professional **MVVM (Model-View-ViewModel)** architectural pattern and is optimized to run at $60$/$120$fps across mobile, tablet, and web browsers.

---

## 🌟 Key Features

### 🌌 1. Premium Glassmorphic Visuals
* **Nebula Backdrop**: A deep radial gradient in indigo-slate that creates a modern, spacious visual flow.
* **Translucent Frosted Cards**: Each grid tile features semi-transparent cards (`Color(0x0DFFFFFF)`) with fine-drawn borders to give a glass-like feel.
* **Vibrant Neon Accent Glows**: Custom color palettes tailored to each rule:
  * **Odd Numbers**: Rich Amber glow
  * **Even Numbers**: Cyber Cyan glow
  * **Primes**: Radiant Violet/Magenta glow
  * **Fibonacci**: Bright Emerald Green glow
  * **Multiples of X**: Vibrant Coral Orange glow

### ⚡ 2. High-Performance Mathematical Engine
* **Instant $O(1)$ Grid Checking**: Checks like Prime numbers and Fibonacci calculations are precomputed on startup using optimized trial-division algorithms and cached in hash-based `Set` collections. This prevents layout stuttering when switching rules.
* **Unicode superscript exponents**: Exponent values are dynamically converted to high-fidelity subscripts and superscripts for standard display (e.g. `28` displays as `2² × 7`).
* **Lazy Detail Compilation**: Divisors lists, hex codes, and prime factorizations are compiled only when a tile is tapped, saving system memory.

### 📐 3. Bouncy, Responsive 10x10 Grid
* **Tactile Interactions**: Implemented bouncy spring physics on grid items using custom animations to scale cards down on press.
* **Multi-Device Responsiveness**: Integrates `LayoutBuilder` delegates to automatically adjust grid layouts from 10 columns (desktop/tablets) down to 8 or 6 columns (tight mobile viewports) without clipping.

### 🎛️ 4. Dynamic Control Panels
* **Horizontal Rules Ribbon**: A scrollable header panel containing the rule selection cards accompanied by live count statistics.
* **Live Match Indicator**: A glowing progress dial displaying the percentage of highlighted grid cells in real-time.
* **Dynamic Divisors Slider**: An active slider that fades in when selecting "Multiples of X", allowing real-time divisor shifts from 2 to 15.

---

## 🏗️ Architectural Overview (MVVM)

This project strictly follows the **MVVM (Model-View-ViewModel)** architectural design to enforce separation of concerns, ease unit testing, and support clean scalability:

```
lib/
├── main.dart                      # App bootstrap, configures overlays and boots DashboardView
├── models/
│   ├── highlight_rule.dart        # HighlightRule enum and RuleStyle design preset mapper
│   └── number_properties.dart     # Calculations and properties model for single integers
├── viewmodels/
│   └── numbers_viewmodel.dart     # Main state controller (ChangeNotifier) handling math caches and triggers
└── views/
    ├── dashboard_view.dart        # Main layout, reactively updates via native ListenableBuilder
    └── widgets/
        ├── rule_card.dart         # Ribbon rule selectors
        ├── number_grid_tile.dart  # Custom tiles supporting hover scale and gesture bounces
        └── number_detail_sheet.dart # Custom drawer sheet for mathematical facts
```

* **Models (Data)**: Defines structural entities and math formulas. Completely decoupled from UI views.
* **ViewModel (Logic)**: Operates as a reactive state controller using `ChangeNotifier`. Modulates data, processes precomputed sets, and triggers view rebuilds via `notifyListeners()`.
* **Views & Widgets (UI)**: Subscribes to the ViewModel using Flutter's high-efficiency `ListenableBuilder` to selectively rebuild only the dynamic portions of the widget tree.

---

## 🧪 Testing and Quality Control

* **Widget Tests**: Located in `test/widget_test.dart`. Simulates user gestures, taps rule selection cards, and asserts that theme state shifts react dynamically.
* **Static Analysis**: Complies with strict Dart analyzer settings, maintaining zero warnings, errors, or package layout conflicts.

---

## 🚀 How to Run the Project

Ensure you have Flutter installed and configured on your machine.

### 1. Get Dependencies
Run this command in the root folder to download all required packages:
```bash
flutter pub get
```

### 2. Run the App
To start the application on an emulator, connected device, or web browser:
```bash
flutter run
```

### 3. Run Automated Tests
To run the automated widget verification suite:
```bash
flutter test
```

### 4. Build Production APK
To build a release-mode APK for Android devices:
```bash
flutter build apk --release
```
The compiled APK will be located at:  
`build/app/outputs/flutter-apk/app-release.apk`
