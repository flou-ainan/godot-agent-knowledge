# Guia de Configuração: Godot 4.7+ & VS Code no Linux (Mint, Ubuntu, Pop!_OS)

Este guia documenta o passo a passo exato para conectar a **Godot 4.7+** e o **VS Code (com Antigravity ou qualquer agente de IA)** em distribuições Linux baseadas em Ubuntu/Debian (Linux Mint, Ubuntu, Pop!_OS, Zorin OS).

---

## 1. Pré-requisitos & Descoberta do Executável do VS Code

Verifique se o seu VS Code foi instalado via pacote nativo (`.deb` / `apt`) ou Flatpak:

```bash
which code
```
* **Pacote Nativo (`.deb` / `apt`):** `/usr/bin/code` (padrão no Linux Mint e Ubuntu)
* **Flatpak:** `/var/lib/flatpak/exports/bin/com.visualstudio.code`

---

## 2. Configuração Global da Godot Engine no Linux

No Linux, a Godot salva as preferências do editor em `~/.config/godot/`. Para a versão 4.7, o arquivo é `~/.config/godot/editor_settings-4.7.tres` (ou `editor_settings-4.tres`).

### Opção A: Configuração via Terminal (Com a Godot Fechada)
Certifique-se de que a Godot está fechada para não sobrescrever o arquivo ao sair, e aplique ou verifique estas chaves:

```ini
text_editor/external/use_external_editor = true
text_editor/external/exec_path = "/usr/bin/code"
text_editor/external/exec_flags = "{project} --goto {file}:{line}:{col}"
text_editor/behavior/files/auto_reload_scripts_on_external_change = true
network/language_server/remote_port = 6005
network/language_server/remote_host = "127.0.0.1"
```

### Opção B: Configuração Visual pela Interface da Godot
1. Abra a Godot $\rightarrow$ **Editor** $\rightarrow$ **Configurações do Editor**.
2. Acesse **Editor de Texto** $\rightarrow$ **Externo**:
   * Marque **Usar Editor Externo** como `Ligado`.
   * Defina o **Caminho do Executável** como `/usr/bin/code` (ou o caminho do seu Flatpak).
   * Defina os **Argumentos do Executável** como `{project} --goto {file}:{line}:{col}`.
3. Acesse **Editor de Texto** $\rightarrow$ **Comportamento** $\rightarrow$ **Arquivos**:
   * Marque **Recarregar Scripts Automaticamente em Alteração Externa** como `Ligado`.
4. Acesse **Rede** $\rightarrow$ **Language Server**:
   * Verifique se a **Porta Remota** é `6005`.
   * Verifique se o **Host Remoto** é `127.0.0.1`.

---

## 3. Extensões Essenciais no VS Code

Abra o VS Code e instale estas duas extensões indispensáveis:
1. **`geequlim.godot-tools`**: Extensão oficial da Godot Engine para LSP e DAP (diagnósticos de erro em tempo real, autocompletar e depuração com breakpoints).
2. **`alfish.godot-files`**: Coloração de sintaxe para arquivos de cena (`.tscn`), recursos (`.tres`) e shaders (`.gdshader`).

---

## 4. Configuração da Pasta do Projeto no VS Code

Na raiz do seu projeto de jogo (ex.: `~/meu-projeto-godot/`), crie a pasta `.vscode/` com três arquivos de configuração:

### `.vscode/settings.json` (Conexão ao LSP e Auto-Save)
```json
{
  "godotTools.editorPath.godot4": "godot",
  "godotTools.lsp.serverPort": 6005,
  "godotTools.lsp.serverHost": "127.0.0.1",
  "files.autoSave": "off",
  "files.exclude": {
    "**/.git": true,
    "**/.godot": false
  }
}
```

### `.vscode/launch.json` (Playtest e Depuração via F5/F6)
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

### `.vscode/extensions.json` (Recomendação de Extensões)
```json
{
  "recommendations": [
    "geequlim.godot-tools",
    "alfish.godot-files"
  ]
}
```

---

## 5. Integrando a Base de Conhecimento e Regras de IA

### 5.1 Conhecimento Atômico Local no Projeto
Copie a biblioteca atômica e as regras mestras para a raiz do seu jogo:
```bash
cp -r /caminho/para/godot-agent-knowledge/agent_knowledge_godot47/ /caminho/para/meu-projeto-godot/
cp /caminho/para/godot-agent-knowledge/agent_knowledge_godot47/RULES_GODOT47.md /caminho/para/meu-projeto-godot/
```

### 5.2 Regra Permanente de Projeto para Agentes
Crie o arquivo `.agent/rules/godot.md` para que qualquer agente carregue as diretrizes automaticamente:
```bash
mkdir -p /caminho/para/meu-projeto-godot/.agent/rules
cp /caminho/para/meu-projeto-godot/RULES_GODOT47.md /caminho/para/meu-projeto-godot/.agent/rules/godot.md
```

### 5.3 Registro Global da Skill no Antigravity (Linux Mint)
Registre a skill globalmente no Antigravity:
```bash
mkdir -p ~/.gemini/antigravity/skills
ln -sf /caminho/para/godot-agent-knowledge/skills/godot4-dev ~/.gemini/antigravity/skills/godot4-dev
```

---

## 6. Checklist de Validação Final

1. Abra a Godot e abra o seu projeto.
2. Abra o VS Code na pasta do projeto (`code /caminho/para/meu-projeto-godot`).
3. Verifique a barra de status inferior do VS Code: ela deve indicar **"Godot: Connected"** (porta `6005`).
4. Pressione `F5` no VS Code ou na Godot: o jogo iniciará imediatamente.
5. No chat do seu assistente de IA, peça: *"Adicione um Timer na cena principal e conecte o timeout"*.
6. O agente injetará o nó no `.tscn` e avisará para você clicar em **Reload** na Godot.
