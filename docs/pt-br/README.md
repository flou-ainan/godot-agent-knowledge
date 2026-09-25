# Base de Conhecimento Atômica & Skill para IA - Godot 4.7

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](../../LICENSE)
[![Open Source](https://img.shields.io/badge/Open_Source-100%25-green.svg)](../../LICENSE)
[🇺🇸 English Version](../../README.md)

Este repositório contém uma **base de conhecimento atômica, densa em tokens e à prova de alucinações** para a **Godot Engine 4.7+** e **GDScript 2.0**, projetada especificamente para assistentes de código com IA (como o Antigravity no VS Code) trabalhando lado a lado com um desenvolvedor com o editor da Godot aberto.

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

## 📖 Sobre & Contribuições

* **Como este projeto foi criado e objetivos:** Leia [docs/pt-br/about.md](./about.md) para conhecer a história do projeto e nossa visão para o desenvolvimento na Godot com IA.
* **Contribuições Comunitárias:** Contribuições, novas receitas de produção e reportes de alucinações são muito bem-vindos! Veja [docs/pt-br/about.md](./about.md) para diretrizes de como contribuir.

---

## 📄 Código Aberto & Licença

Este projeto é um software livre de código aberto (FOSS) disponibilizado sob a **[Licença MIT](../../LICENSE)** — a mesma licença permissiva adotada pela própria [Godot Engine](https://godotengine.org).

Você tem total liberdade para usar, modificar, distribuir e integrar esta base de conhecimento em seus projetos pessoais, comerciais ou sistemas de IA sem qualquer restrição.
