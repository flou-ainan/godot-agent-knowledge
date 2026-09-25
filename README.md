# Godot 4.7 Atomic AI Knowledge Base & Agent Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](./LICENSE)
[![Open Source](https://img.shields.io/badge/Open_Source-100%25-green.svg?style=for-the-badge)](./LICENSE)
[![Leia em Português](https://img.shields.io/badge/🇧🇷_Leia_em-Português_Brasileiro-009c3b?style=for-the-badge)](./docs/pt-br/README.md)

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
├── docs/
│   ├── about.md                                 # Project origins, goals, and vision (English)
│   └── pt-br/                                   # Documentação e README em Português Brasileiro
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

## 💻 Setup & Usage by OS (Linux, macOS, Windows)

### 1. Adding to your Godot Project

#### Method A: Direct Project Integration (Recommended)
Copy the atomic rules and knowledge into your project root:
* **Linux (Mint / Ubuntu / Debian / Fedora / Arch):**
  ```bash
  cp -r agent_knowledge_godot47/ /path/to/my-godot-project/
  cp agent_knowledge_godot47/RULES_GODOT47.md /path/to/my-godot-project/
  ```
* **macOS:**
  ```bash
  cp -r agent_knowledge_godot47/ /Users/<user>/my-godot-project/
  cp agent_knowledge_godot47/RULES_GODOT47.md /Users/<user>/my-godot-project/
  ```
* **Windows (PowerShell):**
  ```powershell
  Copy-Item -Recurse agent_knowledge_godot47 C:\Projects\MyGodotProject\
  Copy-Item agent_knowledge_godot47\RULES_GODOT47.md C:\Projects\MyGodotProject\
  ```

#### Method B: Global Antigravity Agent Skill
Link the skill directly so any workspace can activate it:
* **Linux / macOS:**
  ```bash
  mkdir -p ~/.gemini/antigravity/skills/
  ln -s "$(pwd)/skills/godot4-dev" ~/.gemini/antigravity/skills/godot4-dev
  ```
* **Windows (Run PowerShell as Administrator):**
  ```powershell
  New-Item -ItemType SymbolicLink -Path "$env:USERPROFILE\.gemini\antigravity\skills\godot4-dev" -Target "$PWD\skills\godot4-dev"
  ```

#### Method C: Dedicated Project Rule (`.agent/rules/godot.md`)
Create a persistent rule file in your game repository so any agent automatically loads these rules:
```bash
mkdir -p .agent/rules
cp agent_knowledge_godot47/RULES_GODOT47.md .agent/rules/godot.md
```

---

### 2. Configuring Godot Editor & VS Code Co-Development

To enable seamless two-way editing between the Godot Editor and VS Code:

1. Open Godot $\rightarrow$ **Editor** $\rightarrow$ **Editor Settings** $\rightarrow$ **Text Editor** $\rightarrow$ **External**:
   * Check: **Use External Editor** = `On`
   * Set **Exec Path** according to your OS:
     * **Linux Mint / Ubuntu / Debian (.deb / apt):** `/usr/bin/code`
     * **Linux (Flatpak):** `/var/lib/flatpak/exports/bin/com.visualstudio.code`
     * **macOS:** `/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code`
     * **Windows:** `C:\Users\<User>\AppData\Local\Programs\Microsoft VS Code\Code.exe`
   * Set **Exec Flags**: `{project} --goto {file}:{line}:{col}`

2. Enable the Language Server in Godot:
   * **Editor Settings** $\rightarrow$ **Network** $\rightarrow$ **Language Server**:
     * `Remote Port`: `6005`
     * `Remote Host`: `127.0.0.1`

3. In VS Code:
   * Install the official **Godot Tools** extension (`geequlim.godot-tools`).
   * When Godot is open, VS Code will automatically connect to port `6005` for real-time autocompletion and diagnostics.

---

## 📖 About & Contributing

* **How this was built & project goals:** Read [docs/about.md](./docs/about.md) for the story behind this project and our vision for AI-assisted Godot development.
* **Community Contributions:** Contributions, additional production recipes, and anti-pattern reports are warmly welcomed! See [docs/about.md](./docs/about.md) for guidelines on how to contribute.

---

## 📄 Open Source & License

This project is free, open-source software (FOSS) released under the **[MIT License](./LICENSE)** — the same permissive open-source license that powers the [Godot Engine](https://godotengine.org) itself.

You are free to use, modify, distribute, embed, and package this knowledge base into your personal, commercial, or open-source projects and AI systems without restriction.

