# Godot 4.7+ & VS Code Setup Guide for Ubuntu-Based Linux (Linux Mint, Ubuntu, Pop!_OS)

This guide documents the exact configuration procedure to connect **Godot 4.7+** and **VS Code (with Antigravity or any AI agent)** on Ubuntu-based distributions (Linux Mint, Ubuntu, Pop!_OS, Debian).

---

## 1. Prerequisites & Executable Discovery

### Verify VS Code Installation:
Check whether VS Code was installed via native package (`.deb` / `apt`) or Flatpak:

```bash
which code
```
* **Native package (`.deb` / `apt`):** `/usr/bin/code` (standard on Linux Mint / Ubuntu)
* **Flatpak:** `/var/lib/flatpak/exports/bin/com.visualstudio.code`

---

## 2. Global Godot Editor Configuration

Godot stores its user configuration on Linux at `~/.config/godot/`. For Godot 4.7, the settings file is `~/.config/godot/editor_settings-4.7.tres` (or `editor_settings-4.tres`).

### Option A: Automatic Configuration via Terminal (When Godot is Closed)
Ensure Godot is closed so it does not overwrite settings upon exit, then verify or apply these keys:

```ini
text_editor/external/use_external_editor = true
text_editor/external/exec_path = "/usr/bin/code"
text_editor/external/exec_flags = "{project} --goto {file}:{line}:{col}"
text_editor/behavior/files/auto_reload_scripts_on_external_change = true
network/language_server/remote_port = 6005
network/language_server/remote_host = "127.0.0.1"
```

### Option B: Manual UI Configuration inside Godot Editor
1. Open Godot $\rightarrow$ **Editor** $\rightarrow$ **Editor Settings**.
2. Navigate to **Text Editor** $\rightarrow$ **External**:
   * Set **Use External Editor** to `On`.
   * Set **Exec Path** to `/usr/bin/code` (or your Flatpak path).
   * Set **Exec Flags** to `{project} --goto {file}:{line}:{col}`.
3. Navigate to **Text Editor** $\rightarrow$ **Behavior** $\rightarrow$ **Files**:
   * Set **Auto Reload Scripts on External Change** to `On`.
4. Navigate to **Network** $\rightarrow$ **Language Server**:
   * Verify **Remote Port** is `6005`.
   * Verify **Remote Host** is `127.0.0.1`.

---

## 3. Essential VS Code Extensions

Open VS Code and install these two extensions:
1. **`geequlim.godot-tools`**: Official Godot Language Server & DAP integration (real-time diagnostics, autocompletion, debugging).
2. **`alfish.godot-files`**: Syntax highlighting for `.tscn` (scenes), `.tres` (resources), and `.gdshader`.

---

## 4. Configuring a Godot Project for VS Code

Inside your game project root (e.g. `~/my-godot-project/`), create the `.vscode/` directory with three configuration files:

### `.vscode/settings.json` (LSP Connection & Auto-Save)
```json
{
  "godotTools.editorPath.godot4": "godot",
  "godotTools.lsp.serverPort": 6005,
  "godotTools.lsp.serverHost": "127.0.0.1",
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "files.exclude": {
    "**/.git": true,
    "**/.godot": false
  }
}
```

### `.vscode/launch.json` (Playtesting via F5/F6)
```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Play Current Scene (Godot)",
      "type": "godot",
      "request": "launch",
      "project": "${workspaceFolder}",
      "port": 6006,
      "address": "127.0.0.1",
      "launch_scene": true
    },
    {
      "name": "Play Main Scene (Godot)",
      "type": "godot",
      "request": "launch",
      "project": "${workspaceFolder}",
      "port": 6006,
      "address": "127.0.0.1",
      "launch_game": true
    }
  ]
}
```

### `.vscode/extensions.json` (Recommended Workspace Extensions)
```json
{
  "recommendations": [
    "geequlim.godot-tools",
    "alfish.godot-files"
  ]
}
```

---

## 5. Integrating the AI Knowledge Base & Agent Rules

### 5.1 Project-Level Atomic Knowledge
Copy the knowledge library and rules into your project root:
```bash
cp -r /path/to/godot-agent-knowledge/agent_knowledge_godot47/ /path/to/my-godot-project/
cp /path/to/godot-agent-knowledge/agent_knowledge_godot47/RULES_GODOT47.md /path/to/my-godot-project/
```

### 5.2 Persistent Project Rule for AI Agents
Create `.agent/rules/godot.md` so Antigravity, Cursor, or Claude Code automatically loads the rules:
```bash
mkdir -p /path/to/my-godot-project/.agent/rules
cp /path/to/my-godot-project/RULES_GODOT47.md /path/to/my-godot-project/.agent/rules/godot.md
```

### 5.3 Global Antigravity Skill Registration
Register the skill globally on your Linux Mint machine:
```bash
mkdir -p ~/.gemini/antigravity/skills
ln -sf /path/to/godot-agent-knowledge/skills/godot4-dev ~/.gemini/antigravity/skills/godot4-dev
```

---

## 6. Verification Checklist

1. Launch Godot and open your project.
2. Launch VS Code in the project directory (`code /path/to/my-godot-project`).
3. Check the bottom status bar in VS Code: it should display **"Godot: Connected"** (connected to port `6005`).
4. Press `F5` in VS Code or Godot: your main scene will launch immediately.
5. In your AI agent chat, request: *"Add a Timer to the active scene and connect its timeout signal"*.
6. Notice the agent inject the node into `.tscn` and remind you to click **Reload** in the Godot Editor.
