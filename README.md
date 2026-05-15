# NullOverlay

A native Windows x64 C++20 OpenGL/ImGui overlay framework for local Minecraft Java Edition Forge 1.21.1 debugging.

This project provides a clean, modular foundation for building external overlays that interact with the Minecraft JVM via JNI. It is intentionally designed as a "fail-closed" system, primarily focused on singleplayer development and debugging.

---

## 📁 Repository Structure

The project is organized into several key components to ensure maintainability and modularity:

- **`/src`**: The root of the source code.
  - `dllmain.cpp`: DLL entry point and initialization sequence.
- **`/src/core`**: Core lifecycle management and application state.
- **`/src/sdk`**: Minecraft SDK and JNI abstractions.
  - `minecraft.h/cpp`: Main interface for game interaction.
  - `entity.h/cpp`: Abstraction layer for game entities (players, mobs, etc.).
  - `world.h/cpp`: Access to world and level data.
- **`/src/render`**: Rendering and UI system.
  - `renderer.h/cpp`: Core OpenGL rendering wrappers.
  - `overlay_renderer.h/cpp`: Manages the overlay lifecycle and draw calls.
  - `menu.h/cpp`: The ImGui-based user interface.
- **`/src/modules`**: A modular system for adding features.
  - `module.h`: Base class for all feature modules.
  - `module_manager.h/cpp`: Handles module registration and updates.
  - `entity_overlay.h/cpp`: Implementation of entity information rendering.
- **`/src/config`**: Configuration system for saving/loading settings.
- **`/src/util`**: Common utilities (logging, memory, math).

---

## 🛠️ Build Requirements

- **Visual Studio 2022** with C++20 support.
- **CMake 3.24+**.
- **JDK Headers**: Ensure `JAVA_HOME` is set or JDK is in your path for `FindJNI`.
- **Dependencies**:
  - **MinHook**: Included in `MinHook_134_bin`.
  - **Dear ImGui**: Included in `imgui-1.92.8`.

### Build Instructions

```powershell
# Generate build files
cmake -S . -B build -A x64

# Build the project
cmake --build build --config Release
```

The compiled `NullOverlay.dll` will be located in `build/Release/`.

---

## 🚀 Usage

1. **Setup**: Ensure `MinHook.x64.dll` is in the same directory as your injector or `NullOverlay.dll`.
2. **Injection**: Inject `NullOverlay.dll` into the `javaw.exe` process (Forge 1.21.1).
3. **Controls**:
   - `INSERT`: Toggle the main menu.
   - `DELETE`: Unload the overlay gracefully.

---

## ⚠️ Security & Ethics

This project is intended for **educational and debugging purposes only**. 
- No multiplayer support or bypassing of anti-cheats is included.
- The framework is designed to clear caches and suspend modules if it detects it is not in a local singleplayer environment.
- Use responsibly and respect the EULA of the games you are interacting with.

---

## 📄 License

This project is open-source. See the individual headers for third-party library licenses (ImGui, MinHook).
