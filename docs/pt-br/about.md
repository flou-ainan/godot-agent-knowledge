# Sobre Este Projeto

## Origem & Motivação

Ao utilizar assistentes de código com inteligência artificial modernos (como Antigravity, Claude ou Cursor) no desenvolvimento de jogos na Godot Engine, desenvolvedores enfrentam com frequência obstáculos conhecidos:
* **Alucinações de Sintaxe Python:** Modelos de Linguagem de Grande Porte (LLMs) treinados maciçamente em Python tendem a "sangrar" sintaxe de Python no GDScript (alucinando chamadas como `len()`, `def`, o parâmetro `self` em métodos, `import`, list comprehensions ou o literal `None`).
* **Mistura de Versões (Godot 3 vs Godot 4):** Agentes frequentemente misturam sintaxes obsoletas da Godot 3 (`yield`, `KinematicBody`, `export(int)`, `onready var`, `connect("signal", self, "method")`) com código da Godot 4.
* **Saturação de Contexto vs. Eficiência de Tokens:** A documentação oficial canônica para humanos é rica em texto descritivo e narrativas tutoriais. Embora fantástica para leitura humana, ela rapidamente satura a janela de contexto de uma IA com tokens de baixa densidade.
* **Perda da Ergonomia do Editor Visual:** IAs têm o vício de instanciar nós procedurais por código (`Timer.new()`, `GPUParticles2D.new()`), privando o desenvolvedor da maior força da Godot: ajustar curvas, timers, volumes de áudio e propriedades visuais diretamente com sliders no Inspector da engine.

Para solucionar esses gargalos, destilamos toda a documentação oficial da Godot Engine (mais de 1.600 arquivos `.rst` e 1.100+ referências de classes) em uma **base de conhecimento atômica, modular e orientada a regras**, projetada especificamente para compreensão de agentes e desenvolvimento contínuo em conjunto com o editor da **Godot 4.7+**.

---

## Como Foi Criado

1. **Extração Sistemática:** Mapeamos os manuais oficiais da Godot, isolando invariantes arquiteturais, a ordem canônica de declaração de código e a mecânica de ciclo de vida de nós.
2. **Integração de Padrões Oficiais de Demos:** Analisamos o repositório oficial de demonstrações (`godot-demo-projects/gui`) para mapear as regras exatas de serialização no `.tscn` (como as propriedades `layout_mode = 3` vs `layout_mode = 2` e flags de contêiner da Godot 4) que evitam que IAs corrompam arquivos de cena.
3. **Matriz de Desambiguação GDScript vs Python:** Criamos tabelas e listas explícitas de anti-patterns traduzindo os vícios de Python diretamente para os equivalentes em GDScript 4.7.
4. **Protocolos de Co-Desenvolvimento Contínuo:** Formalizamos as regras de sincronização entre o editor externo (VS Code) e o editor aberto da Godot, incluindo o alerta obrigatório de **"Reload vs. Resave"** e a análise contextual de referência de nós (`%UniqueName` vs caminhos diretos vs `@export`).
5. **Empacotamento em Skill para Agentes:** Estruturamos toda a biblioteca em uma Skill oficial pronta para uso (`skills/godot4-dev/SKILL.md`), permitindo que qualquer agente a carregue instantaneamente em futuros projetos.

---

## Nosso Objetivo

Nossa meta é estabelecer o padrão de excelência para **desenvolvimento de jogos assistido por IA na Godot**:
* Capacitar agentes de IA a escrever GDScript 2.0 limpo, estritamente tipado e pronto para produção.
* Manter a filosofia **Scene-First**, garantindo que o desenvolvedor humano preserve o controle visual no Inspector da Godot.
* Garantir **Usabilidade 100% Agnóstica a Agentes**: embora usemos atualmente o Google Antigravity no VS Code para criar e testar este projeto, toda a arquitetura de conhecimento foi projetada para ser universal e compatível com qualquer agente ou assistente (Cursor, Claude Code, Windsurf, Copilot, Roo Code, Aider ou LLMs locais).
* Disponibilizar uma base de conhecimento livre, aberta e agnóstica a fornecedores, compatível com qualquer IDE, LLM local ou ferramenta de IA.

---

## Contribuindo

Contribuições da comunidade são muito bem-vindas! A Godot é uma engine movida pela comunidade, e esta base de conhecimento foi pensada para evoluir continuamente.

### Como Você Pode Ajudar:
* **Compartilhe Padrões de Produção:** Envie receitas testadas em batalha para máquinas de estado, geração procedural, shaders ou UI responsiva.
* **Reporte Falhas de Modelos de IA:** A IA alucinou alguma sintaxe ou usou uma API errada da Godot 4? Abra uma Issue ou Pull Request detalhando o caso.
* **Refine as Regras:** Ajude a tornar as diretrizes ainda mais concisas, densas e diretas ao ponto.

Sinta-se à vontade para abrir uma **Issue** ou enviar um **Pull Request** no GitHub!
