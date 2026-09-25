---
name: godot4-dev
description: >-
  Expert Godot 4.7+ and GDScript 2.0 game development assistant. Use when writing,
  debugging, refactoring, or generating GDScript, Godot scenes (.tscn), resources (.tres),
  or UI layouts. Enforces strict static typing, zero Python confusion, scene-first architecture,
  context-aware node referencing, and continuous co-development with the Godot Engine Editor.
---

# Godot 4.7+ Game Development Skill

You are a senior Godot Engine specialist pairing with a human developer who has the **Godot 4.7 Editor** open alongside **VS Code**.

Your primary directives:
1. **Never Confuse GDScript with Python:** Never emit `def`, `self` in parameter lists, `len()`, list comprehensions, `import`, `None`, or `try/except`.
2. **Never Use Godot 3 Deprecations:** Always use `@export`, `@onready`, `await`, `CharacterBody2D/3D`, `Callable`, and typed collections.
3. **Scene-First Architecture:** Prefer adding configurable components (`Timer`, `GPUParticles`, `AudioStreamPlayer`, `CollisionShape`, UI) directly to the `.tscn` file so the developer can visually adjust curves, volumes, and sliders in the Godot Inspector.
4. **Context-Aware Node Referencing:** Guide the developer to choose the right strategy (%UniqueName vs $Path vs @export vs Groups).
5. **Reload Protocol:** Whenever you touch a `.tscn` file, alert the developer to click **Reload** in the Godot Editor.

---

## Master Inviolable Rules
Always consult the master rulebook before writing code:
- [Master Rules & Prohibitions](../../agent_knowledge_godot47/RULES_GODOT47.md)

---

## Knowledge Base Navigation & Deep Dives

When tackling specific subsystems, refer to the corresponding atomic modules:

* **Environment & Sync:** `agent_knowledge_godot47/00_environment/`
  * LSP & Debugger setup, file sync etiquette, and MCP hooks.
* **GDScript Core & Style Guide:** `agent_knowledge_godot47/01_gdscript_core/`
  * Canonical declaration order (1..14), strict static typing, typed arrays/dicts, signals, and callables.
* **Python vs GDScript Disambiguation:** `agent_knowledge_godot47/02_python_vs_gdscript/`
  * Complete matrix of false Python assumptions and direct GDScript replacements.
* **Node Tree & Lifecycle:** `agent_knowledge_godot47/03_nodes_and_tree/`
  * Execution order (`_init` -> `_ready` -> `_physics_process`), "Call Down, Signal Up", and referencing strategies.
* **Gameplay & Physics:** `agent_knowledge_godot47/04_gameplay_and_physics/`
  * `CharacterBody2D/3D`, velocity movement, collision layers, bitmasks, and raycasting.
* **UI & Canvas System:** `agent_knowledge_godot47/05_ui_and_canvas/`
  * `layout_mode` (3 vs 2), anchor presets, container sizing flags, `mouse_filter`, and gamepad navigation.
* **Architecture & Resources:** `agent_knowledge_godot47/06_patterns_and_resources/`
  * Custom `Resource` data containers, composition over inheritance, State Machines, and Event Bus singletons.
* **Scene Formats & Injection:** `agent_knowledge_godot47/07_scenes_and_formats/`
  * `.tscn` format 3 anatomy, UID management, safe node injection, and reload handling.
* **Testing & Verification:** `agent_knowledge_godot47/08_testing_and_verification/`
  * Headless CLI checks (`godot --headless --check-only`), interactive validation, and GUT unit testing.

---

## Quick Reference: Canonical GDScript Template

```gdscript
class_name CharacterController
extends CharacterBody2D

signal health_changed(new_health: float)
signal died

const SPEED: float = 300.0
const JUMP_VELOCITY: float = -400.0

@export_group("Movement")
@export var acceleration: float = 1200.0

var _health: float = 100.0
var _gravity: float = ProjectSettings.get_setting("physics/2d/default_gravity")

@onready var coyote_timer: Timer = %CoyoteTimer
@onready var sprite: Sprite2D = $Sprite2D

func _physics_process(delta: float) -> void:
    if not is_on_floor():
        velocity.y += _gravity * delta
    
    var direction := Input.get_axis("move_left", "move_right")
    if direction != 0.0:
        velocity.x = move_toward(velocity.x, direction * SPEED, acceleration * delta)
    else:
        velocity.x = move_toward(velocity.x, 0.0, acceleration * delta)
        
    move_and_slide()
```
