# How to Run in VS Code

This repo currently contains planning and architecture documents, not a compiled app yet.

## Option A: View the documentation (current state)

1. Open VS Code.
2. Click **File → Open Folder...** and select this repository.
3. Open `README.md` and the files under `docs/`.
4. (Optional) Install **Markdown Preview Enhanced** extension and preview docs with `Ctrl+Shift+V`.

---

## Option B: Start the Flutter app from this plan

Use this path if you want to begin implementation now.

### 1) Prerequisites
- Install **Flutter SDK**
- Install **Android Studio** (for Android SDK + emulator)
- Install **VS Code extensions**:
  - Flutter
  - Dart

### 2) Create app scaffold

From VS Code terminal (repository root):

```bash
flutter create app
cd app
```

### 3) Run on emulator/device

```bash
flutter pub get
flutter run
```

### 4) Suggested next implementation order
1. Home shell + bottom navigation (Videos/Music/Folders)
2. Storage permission + media scan
3. Video player controls + subtitle + resume
4. Audio player + background notification controls
5. File manager operations

Use these docs as implementation references:
- `docs/ui-wireframes.md`
- `docs/feature-documentation.md`
- `docs/module-structure.md`
- `docs/development-timeline.md`

---

## Troubleshooting

- If `flutter` command is not found:
  - Add Flutter SDK `bin` to PATH and restart VS Code.
- If no devices are detected:
  - Start Android emulator from Android Studio Device Manager.
  - Or connect a physical device with USB debugging enabled.
- If Gradle build fails on first run:
  - Run `flutter doctor` and fix reported SDK/licensing issues.
