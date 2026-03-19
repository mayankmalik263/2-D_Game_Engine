```markdown
# 2D Game Engine in Java

#### Project Overview
This is a **2D Game Engine** developed in Java as a course project for the **Object-Oriented Programming (OOPS)** course in Semester 4 at **UPES Dehradun**. The engine is a comprehensive framework built from scratch using the Lightweight Java Game Library (LWJGL). 

The project showcases the practical application of OOPS concepts including **encapsulation**, **inheritance**, **polymorphism**, and **abstraction** through a modular, extensible game engine architecture. It demonstrates how to build a fully functional game editor and runtime environment capable of running 2D platformer games like a Mario clone.

---

#### 📋 Project Objectives
* Implement a scalable 2D game engine architecture using Java.
* Demonstrate core OOPS principles in a real-world application.
* Create a reusable framework for 2D game development with a decoupled editor and runtime environment.
* Implement essential game engine components including batched rendering, rigid-body physics, input handling, and an Entity-Component System (ECS).
* Build modular and maintainable code with clear separation of concerns.

---

#### 🎮 Features

##### Core Engine Components
* **Game Loop**: Manages frame updates, rendering, input processing, and Delta Time calculation for smooth hardware-independent movement.
* **Entity-Component System (ECS)**: A flexible architecture using `GameObject` entities that hold a list of abstract `Component` classes, avoiding deep and rigid inheritance hierarchies.
* **Batched Rendering System**: Highly optimized 2D graphics rendering using OpenGL that batches up to 1,000 quads into a single draw call, maintaining 60 FPS even with complex scenes.
* **Physics System**: Comprehensive physics simulation and collision detection wrapping the JBox2D library, supporting dynamic, static, and kinematic bodies with box, circle, and pillbox colliders.
* **Input Handling**: Centralized keyboard and mouse input management utilizing GLFW callbacks and normalized world-to-screen coordinate mapping.
* **Level Editor & UI**: Immediate-mode graphical user interface (ImGui) integrated directly into the engine, featuring a scene hierarchy panel, properties inspector, drag-and-drop support, and transform gizmos.
* **Serialization**: Automated level saving and loading using Google's Gson library and Java Reflection to dynamically discover and serialize component fields.
* **Audio System**: Sound and music playback management utilizing OpenAL and STB Vorbis.

##### Design Patterns Implemented
* **Component-Based Architecture**: Flexible entity composition prioritizing has-a over is-a relationships.
* **Observer Pattern**: A decoupled global Event System that notifies subscribed listeners of game state changes (e.g., play, stop, save).
* **Singleton Pattern**: Centralized resource management for classes that only require a single instance, such as the main `Window`, `MouseListener`, and `AssetPool`.

---

#### 🛠️ Technology Stack

| Component | Technology |
| ------ | ------ |
| **Language** | Java 8+ |
| **Build Tool** | Gradle |
| **Graphics & Windowing** | LWJGL (OpenGL, GLFW) |
| **Math Library** | JOML (Java Math Library) |
| **Physics Engine** | JBox2D |
| **Editor UI** | ImGui (spair/imgui-java port) |
| **Serialization** | Google Gson |
| **Audio & Media** | OpenAL, STB (stb_image, stb_vorbis) |
| **IDE** | IntelliJ IDEA / Eclipse / VS Code |
| **Version Control** | Git |

---

#### 📁 Project Structure
* `src/main/java/jade` - Core game engine files and window management.
* `src/main/java/components` - Standard ECS components (e.g., `SpriteRenderer`, `RigidBody2D`, colliders).
* `src/main/java/physics2d` - Wrappers and controllers for the JBox2D physics engine.
* `src/main/java/renderer` - Classes handling OpenGL graphics, shaders, and batched rendering.
* `src/main/java/editor` - Level editor windows, ImGui integration, and gizmo controls.
* `src/main/java/observers` - Event system and observer pattern implementations.
* `assets/` - Directory for storing shaders (`.glsl`), textures (`.png`), fonts (`.ttf`), and sounds (`.ogg`).

---

#### 🚀 Getting Started

##### Prerequisites
* **Java Development Kit (JDK)** 8 or higher
* **Gradle** (for dependency management and building)
* **Git** (for version control)

##### Installation
1. **Clone the repository**: `git clone <repository-url>`
2. **Build the project** (using Gradle): `gradle build`
3. **Run the engine**: Execute the `Main` class via your IDE or command line.

##### Alternative: Using IDE
1. Open the project in your IDE (IntelliJ IDEA recommended).
2. Configure the project SDK to use JDK 8+.
3. Import Gradle dependencies.
4. Run the main class to launch the game engine and editor.

---

#### 📖 Usage Example

##### Creating a Simple Game Entity
```java
// Create a new GameObject with a transform
GameObject player = new GameObject("Player", new Transform(new Vector2f(0, 0), new Vector2f(1, 1)), 0);

// Add standard components
player.addComponent(new SpriteRenderer(new Vector4f(1, 0, 0, 1))); // Red square
player.addComponent(new RigidBody2D());
player.addComponent(new Box2DCollider());

// Add to the active scene
Window.getScene().addGameObjectToScene(player);
```

##### Implementing Game Logic
```java
public class PlayerController extends Component {
    @Override
    public void update(float dt) {
        // Implement custom frame-by-frame game logic here
        if (KeyListener.isKeyPressed(GLFW_KEY_RIGHT)) {
            // Move player right
        }
    }
}
```

---

#### 🧬 OOPS Principles Demonstrated

##### 1. **Encapsulation**
* Private attributes with public getter/setter methods protecting core engine state.
* The `AssetPool` encapsulates complex memory and resource management, distributing single texture references instead of reloading files.

##### 2. **Inheritance**
* Abstract `Component` base class extended by specific component types (e.g., `SpriteRenderer`, `RigidBody2D`).
* Abstract `Scene` class allowing for unique runtime and editor scenes.

##### 3. **Polymorphism**
* Method overriding in component `update(float dt)`, `start()`, and collision callback methods.
* Interface-based design utilized in the Observer pattern for event processing.

##### 4. **Abstraction**
* Complex OpenGL initialization and draw calls hidden behind simple `Shader` and `RenderBatch` classes.
* Physics processing and JBox2D interactions abstracted behind a friendly `Physics2D` wrapper system.

---

#### 💡 Key Classes

| Class | Purpose |
| ------ | ------ |
| `Window` | Main game class and entry point, manages GLFW |
| `GameObject` | Base class for game objects, container for components |
| `Component` | Abstract base class for entity behaviors |
| `RenderBatch` | Handles OpenGL draw calls and vertex buffering |
| `Physics2D` | Physics simulation and JBox2D wrapper |
| `MouseListener` / `KeyListener` | Handles keyboard and mouse input callbacks |
| `Scene` | Container for entities, rendering, and game logic |
| `AssetPool` | Manages loaded files like textures, sounds, and shaders |

---

#### 📝 Course Information
* **Course**: Object-Oriented Programming (OOPS) in Java
* **Institution**: UPES Dehradun
* **Semester**: 4
* **Academic Year**: 2025-2026

---

#### 🤝 Contributing
To contribute to this project:
1. Create a new branch for your feature: `git checkout -b feature-name`
2. Commit your changes: `git commit -m "Description of changes"`
3. Push to the branch: `git push origin feature-name`
4. Create a Pull Request describing your changes

---

#### 📚 Resources & References
* Java Object-Oriented Concepts
* Design Patterns in Java
* Game Engine Architecture
* LWJGL 3 Documentation
* Box2D Documentation

---

#### 📄 License
This project is developed as part of the OOPS course at UPES Dehradun and is available for educational purposes.

#### 👤 Author
**Student Name**: Mayank Malik
**SAP ID & Batch**: 590013857 Batch 13(AIML)
**Email**: mayankmalik263@gmail.com

#### 📞 Support & Questions
For questions or issues regarding this project, please contact your course instructor or create an issue in the repository.

**Last Updated**: March 2026
**Project Status**: Active Development
```