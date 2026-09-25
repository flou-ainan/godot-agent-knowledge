# Base de Conhecimento Atômica & Skill para IA - Godot 4.7

[![Licença: MIT](https://img.shields.io/badge/Licença-MIT-blue.svg?style=for-the-badge)](../../LICENSE)
[![Código Aberto](https://img.shields.io/badge/Código_Aberto-100%25-green.svg?style=for-the-badge)](../../LICENSE)
[![Read in English](https://img.shields.io/badge/🇺🇸_Read_in-English-2563eb?style=for-the-badge)](../../README.md)

Este repositório contém uma **base de conhecimento atômica, altamente eficiente em tokens e à prova de alucinações** para a **Godot Engine 4.7+** e **GDScript 2.0**, projetada especificamente para assistentes de código com IA (como o Antigravity no VS Code) trabalhando lado a lado com um desenvolvedor com o editor da Godot aberto.

---

## 🚀 Guia Rápido para Agentes de IA

1. **Regras Mestras Invioláveis:** Leia [agent_knowledge_godot47/RULES_GODOT47.md](../../agent_knowledge_godot47/RULES_GODOT47.md) antes de escrever qualquer código.
2. **Catálogo Geral & Índice:** Acesse [agent_knowledge_godot47/INDEX.md](../../agent_knowledge_godot47/INDEX.md) para links diretos a todos os tópicos.
3. **Skill para Agentes:** Utilize [skills/godot4-dev/SKILL.md](../../skills/godot4-dev/SKILL.md) para integrar esta base de conhecimento ao seu agente ou ambiente.

---

## 📁 Estrutura do Repositório

```
.
├── agent_knowledge_godot47/
│   ├── RULES_GODOT47.md                         # Diretrizes Mestras Invioláveis & Regras Anti-Python
│   ├── INDEX.md                                 # Catálogo geral de tópicos e índice de navegação
│   ├── 00_environment/                          # Integração VS Code + Godot LSP/DAP & protocolo de reload
│   ├── 01_gdscript_core/                        # Tipagem estrita, style guide, sinais, gerenciamento de memória
│   ├── 02_python_vs_gdscript/                   # Anti-patterns e matriz de tradução lado a lado
│   ├── 03_nodes_and_tree/                       # Ciclo de vida de nós, comunicação e estratégias de referência
│   ├── 04_gameplay_and_physics/                 # CharacterBody2D/3D, camadas de colisão e raycasts
│   ├── 05_ui_and_canvas/                        # Layouts de Control, anchors_preset e navegação por gamepad
│   ├── 06_patterns_and_resources/               # Recursos customizados (.tres), máquinas de estado e event bus
│   ├── 07_scenes_and_formats/                   # Formato .tscn 3, injeção segura de nós e cenas procedurais
│   └── 08_testing_and_verification/             # Validação estática headless por CLI e testes com GUT
├── docs/
│   ├── about.md                                 # Sobre a origem, objetivos e visão do projeto (Inglês)
│   └── pt-br/                                   # Documentação e README em Português Brasileiro
└── skills/
    └── godot4-dev/
        └── SKILL.md                             # Skill pronta para agentes de IA (Antigravity)
```

---

## 🛡️ Garantias Centrais & Filosofia

* **Zero Confusão com Python:** Elimina alucinações de sintaxe Python (`self` em parâmetros, `len()`, `def`, list comprehensions, `None`, `import`, exceções).
* **Zero Código Obsoleto da Godot 3:** Apenas sintaxe moderna da Godot 4.x (`@export`, `@onready`, `await`, `CharacterBody2D/3D`, `Callable`).
* **Arquitetura Scene-First:** Prioriza injetar componentes (`Timer`, `AudioStreamPlayer`, `GPUParticles`, UI) no `.tscn` para que o desenvolvedor possa regular sliders e curvas visualmente no Inspector da Godot.
* **Referência de Nós Contextual:** Orienta a escolha entre `%UniqueName`, caminhos `$Path`, `@export` e Grupos de acordo com as necessidades de cada cena.
* **Protocolo de Segurança Reload vs. Resave:** Alerta obrigatório ao modificar arquivos `.tscn` para evitar perda de dados no editor da Godot.

---

## 💻 Guia de Configuração e Uso por Sistema Operacional (Linux, macOS, Windows)

### 1. Adicionando ao seu Projeto Godot

#### Método A: Integração Direta no Projeto (Recomendado)
Copie as regras atômicas e a base de conhecimento para a raiz do seu projeto de jogo:
* **Linux (Mint / Ubuntu / Debian / Fedora / Arch):**
  ```bash
  cp -r agent_knowledge_godot47/ /caminho/para/meu-projeto-godot/
  cp agent_knowledge_godot47/RULES_GODOT47.md /caminho/para/meu-projeto-godot/
  ```
* **macOS:**
  ```bash
  cp -r agent_knowledge_godot47/ /Users/<usuario>/meu-projeto-godot/
  cp agent_knowledge_godot47/RULES_GODOT47.md /Users/<usuario>/meu-projeto-godot/
  ```
* **Windows (PowerShell):**
  ```powershell
  Copy-Item -Recurse agent_knowledge_godot47 C:\Projetos\MeuProjetoGodot\
  Copy-Item agent_knowledge_godot47\RULES_GODOT47.md C:\Projetos\MeuProjetoGodot\
  ```

#### Método B: Skill Global do Agente Antigravity
Crie um link simbólico da skill para que qualquer workspace ou projeto possa ativá-la:
* **Linux / macOS:**
  ```bash
  mkdir -p ~/.gemini/antigravity/skills/
  ln -s "$(pwd)/skills/godot4-dev" ~/.gemini/antigravity/skills/godot4-dev
  ```
* **Windows (Execute o PowerShell como Administrador):**
  ```powershell
  New-Item -ItemType SymbolicLink -Path "$env:USERPROFILE\.gemini\antigravity\skills\godot4-dev" -Target "$PWD\skills\godot4-dev"
  ```

---

### 2. Configurando o Co-Desenvolvimento entre Godot Editor & VS Code

Para habilitar a edição sincronizada em duas vias entre o editor visual da Godot e o VS Code:

1. Abra a Godot $\rightarrow$ **Editor** $\rightarrow$ **Configurações do Editor** $\rightarrow$ **Editor de Texto** $\rightarrow$ **Externo**:
   * Marque: **Usar Editor Externo** = `Ligado`
   * Preencha o **Caminho do Executável** de acordo com seu SO:
     * **Linux Mint / Ubuntu / Debian (.deb ou apt):** `/usr/bin/code`
     * **Linux (Flatpak):** `/var/lib/flatpak/exports/bin/com.visualstudio.code`
     * **macOS:** `/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code`
     * **Windows:** `C:\Users\<Usuario>\AppData\Local\Programs\Microsoft VS Code\Code.exe`
   * Defina os **Argumentos do Executável**: `{project} --goto {file}:{line}:{col}`

2. Ative o Language Server (LSP) na Godot:
   * **Configurações do Editor** $\rightarrow$ **Rede** $\rightarrow$ **Language Server**:
     * `Porta Remota`: `6005`
     * `Host Remoto`: `127.0.0.1`

3. No VS Code:
   * Instale a extensão oficial **Godot Tools** (`geequlim.godot-tools`).
   * Com o editor da Godot aberto, o VS Code se conectará automaticamente à porta `6005` para fornecer autocompletar e diagnósticos em tempo real.

---

## 📖 Sobre & Contribuições

* **Como este projeto foi criado e objetivos:** Leia [docs/pt-br/about.md](./about.md) para conhecer a história do projeto e nossa visão para o desenvolvimento na Godot com IA.
* **Contribuições Comunitárias:** Contribuições, novas receitas de produção e reportes de alucinações são muito bem-vindos! Veja [docs/pt-br/about.md](./about.md) para diretrizes de como contribuir.

---

## 📄 Código Aberto & Licença

Este projeto é um software livre de código aberto (FOSS) disponibilizado sob a **[Licença MIT](../../LICENSE)** — a mesma licença permissiva adotada pela própria [Godot Engine](https://godotengine.org).

Você tem total liberdade para usar, modificar, distribuir e integrar esta base de conhecimento em seus projetos pessoais, comerciais ou sistemas de IA sem qualquer restrição.
