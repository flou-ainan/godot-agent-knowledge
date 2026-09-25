# Godot 4.7 Atomic AI Knowledge Base & Agent Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Open Source](https://img.shields.io/badge/Open_Source-100%25-green.svg)](./LICENSE)

This repository contains an **atomic, token-efficient, and zero-hallucination knowledge base** for **Godot Engine 4.7+** and **GDScript 2.0**, specifically tailored for AI coding assistants (such as Antigravity in VS Code) pairing continuously with a developer running the Godot Editor.

---

## 🚀 Quick Start for AI Agents

1. **Master Inviolable Rules:** Read [agent_knowledge_godot47/RULES_GODOT47.md](./agent_knowledge_godot47/RULES_GODOT47.md) before writing any code.
2. **Master Catalog & Index:** Browse [agent_knowledge_godot47/INDEX.md](./agent_knowledge_godot47/INDEX.md) for direct links to all topics.
3. **Agent Skill:** Use [skills/godot4-dev/SKILL.md](./skills/godot4-dev/SKILL.md) to integrate this knowledge base into your agent framework.

---

## 📁 Repository Structure

```
.
├── agent_knowledge_godot47/
│   ├── RULES_GODOT47.md                         # Master Inviolable Directives & Anti-Python Rules
│   ├── INDEX.md                                 # Full topic catalog & navigation index
│   ├── 00_environment/                          # VS Code + Godot LSP/DAP integration & reload protocol
│   ├── 01_gdscript_core/                        # Strict typing, style guide, signals, memory model
│   ├── 02_python_vs_gdscript/                   # Anti-patterns and side-by-side translation matrix
│   ├── 03_nodes_and_tree/                       # Lifecycle order, communication, node referencing
│   ├── 04_gameplay_and_physics/                 # CharacterBody2D/3D, collision layers, raycasts
│   ├── 05_ui_and_canvas/                        # Control layouts, anchors_preset, gamepad navigation
│   ├── 06_patterns_and_resources/               # Custom resources (.tres), state machines, event bus
│   ├── 07_scenes_and_formats/                   # .tscn format 3, safe node injection, procedural scenes
│   └── 08_testing_and_verification/             # Headless CLI checking and GUT unit testing
└── skills/
    └── godot4-dev/
        └── SKILL.md                             # Plug-and-play Antigravity / Agent Skill
```

---

## 🛡️ Core Guarantees & Philosophy

* **Zero Python Confusion:** Eliminates Python hallucinations (`self` in parameters, `len()`, `def`, list comprehensions, `None`, `import`, exceptions).
* **Zero Godot 3 Deprecations:** Strictly modern Godot 4.x syntax (`@export`, `@onready`, `await`, `CharacterBody2D/3D`, `Callable`).
* **Scene-First Architecture:** Prefers injecting components (`Timer`, `AudioStreamPlayer`, `GPUParticles`, UI) into `.tscn` so the developer can visually tweak sliders and curves in the Godot Inspector.
* **Context-Aware Node Referencing:** Guides the developer between `%UniqueName`, `$Path`, `@export`, and Groups based on scene requirements.
* **Reload vs. Resave Safety Protocol:** Mandatory alert when modifying `.tscn` files to prevent data loss in the Godot Editor.

---

## 📖 About & Contributing

* **How this was built & project goals:** Read [docs/about.md](./docs/about.md) for the story behind this project and our vision for AI-assisted Godot development.
* **Community Contributions:** Contributions, additional production recipes, and anti-pattern reports are warmly welcomed! See [docs/about.md](./docs/about.md) for guidelines on how to contribute.

---

## 📄 Open Source & License

This project is free, open-source software (FOSS) released under the **[MIT License](./LICENSE)** — the same permissive open-source license that powers the [Godot Engine](https://godotengine.org) itself.

You are free to use, modify, distribute, embed, and package this knowledge base into your personal, commercial, or open-source projects and AI systems without restriction.

