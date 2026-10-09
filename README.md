# Mini Dev Team AI

Uma equipe de agentes de inteligência artificial que trabalha em conjunto para planejar, desenvolver, testar e revisar pequenas funcionalidades de software utilizando **Google Agent Development Kit (ADK)**.

O projeto busca simular um fluxo de desenvolvimento de software com agentes especializados, automatizando etapas do processo e permitindo correções controladas antes da entrega final.

> **Status:** Em desenvolvimento 🚧

## Sobre o projeto

O Mini Dev Team AI recebe uma tarefa de programação descrita em linguagem natural e coordena diferentes agentes de IA para transformar essa solicitação em uma implementação funcional.

Em vez de concentrar todas as responsabilidades em um único agente, o sistema divide o trabalho em funções especializadas: planejamento, desenvolvimento, testes e revisão técnica.

O objetivo é explorar conceitos de sistemas multiagentes, orquestração de workflows, ferramentas, saídas estruturadas e avaliação de código utilizando Google ADK.

## Como funciona

O fluxo de desenvolvimento será organizado da seguinte maneira:

1. **Planner Agent:** interpreta a solicitação, identifica os requisitos e define um plano de implementação.
2. **Developer Agent:** implementa a funcionalidade seguindo o planejamento definido.
3. **QA Agent:** cria e executa testes automatizados para verificar o comportamento do código.
4. **Reviewer Agent:** analisa a implementação, os testes e possíveis problemas técnicos.
5. **Root Agent:** coordena os agentes, controla o fluxo de execução e decide quando solicitar correções ou finalizar a tarefa.

Caso os testes falhem ou sejam identificados problemas impeditivos na revisão, o coordenador poderá encaminhar as informações ao Developer para uma nova tentativa.

O ciclo de correção terá um limite configurável de tentativas para evitar execuções indefinidas.

### Exemplo de utilização

**Entrada:**

> Crie uma API em Python para cadastrar tarefas, listar tarefas e marcar uma tarefa como concluída. Inclua testes automatizados.

**Resultado esperado:**

* Plano de implementação com requisitos e critérios de aceitação.
* Arquivos Python contendo a funcionalidade solicitada.
* Testes automatizados.
* Resultados da execução dos testes.
* Revisão técnica do código.
* Relatório final com o resultado da tarefa e o histórico das tentativas.

## Funcionalidades planejadas

* [ ] Receber tarefas de programação em linguagem natural.
* [ ] Planejar a implementação automaticamente.
* [ ] Gerar e organizar arquivos de código.
* [ ] Criar testes automatizados.
* [ ] Executar testes em um ambiente isolado.
* [ ] Revisar código e identificar problemas técnicos.
* [ ] Corrigir falhas automaticamente com limite de tentativas.
* [ ] Coordenar os agentes por meio de workflows do Google ADK.
* [ ] Registrar logs e resultados intermediários.
* [ ] Gerar relatórios finais de execução.
* [ ] Avaliar a qualidade das entregas por meio de tarefas de referência.
* [ ] Permitir aprovação humana antes da aceitação final da solução.

## Tecnologias

| Tecnologia                         | Finalidade                                          |
| ---------------------------------- | --------------------------------------------------- |
| Python                             | Linguagem principal do projeto                      |
| Google ADK                         | Criação, composição e orquestração dos agentes      |
| LiteLLM                            | Integração com modelos de linguagem compatíveis     |
| pytest                             | Execução e organização dos testes automatizados     |
| Pydantic                           | Validação e estruturação de dados, quando aplicável |
| Docker ou outra solução de sandbox | Isolamento da execução do código gerado             |
| uv                                 | Gerenciamento de dependências e ambiente Python     |

As tecnologias e integrações poderão ser ajustadas durante a implementação.

## Arquitetura

O projeto será organizado em módulos para separar as responsabilidades dos agentes, das ferramentas e da orquestração.

```text
mini-dev-team/
├── src/
│   └── mini_dev_team/
│       ├── agent.py
│       ├── config/
│       │   └── settings.py
│       ├── agents/
│       │   ├── planner.py
│       │   ├── developer.py
│       │   ├── qa.py
│       │   └── reviewer.py
│       ├── tools/
│       │   ├── file_manager.py
│       │   ├── test_runner.py
│       │   └── code_analyzer.py
│       ├── workflows/
│       │   └── development.py
│       ├── schemas/
│       │   └── task.py
│       └── callbacks/
│           └── logging.py
├── tests/
├── workspace/
├── reports/
├── .env.example
├── .gitignore
├── pyproject.toml
└── README.md
```

### Responsabilidades dos módulos

* `agents/`: instruções e configurações dos agentes especializados.
* `tools/`: ferramentas para manipular arquivos, executar testes e analisar código.
* `workflows/`: sequência de execução, decisões e ciclos de correção.
* `schemas/`: estruturas para requisitos, planos e resultados.
* `callbacks/`: registro de eventos e acompanhamento da execução.
* `config/`: configurações gerais do sistema.
* `workspace/`: arquivos criados durante as tarefas.
* `reports/`: relatórios produzidos ao final das execuções.
* `tests/`: testes automatizados do próprio Mini Dev Team AI.

## Roadmap

### Fase 1 — Fundação

* [ ] Configurar o ambiente Python e o Google ADK.
* [ ] Configurar o provedor de modelos.
* [ ] Criar os primeiros schemas.
* [ ] Implementar Planner e Developer.
* [ ] Criar a ferramenta de gerenciamento de arquivos.

### Fase 2 — Testes e revisão

* [ ] Implementar QA e Reviewer.
* [ ] Criar a ferramenta de execução dos testes.
* [ ] Padronizar as saídas dos agentes.
* [ ] Tratar erros de execução e respostas inválidas.

### Fase 3 — Orquestração e segurança

* [ ] Implementar o Root Agent.
* [ ] Integrar o workflow completo.
* [ ] Criar o ciclo limitado de correções.
* [ ] Implementar logs e acompanhamento do estado.
* [ ] Configurar o isolamento da execução do código gerado.

### Fase 4 — Avaliação e entrega

* [ ] Criar tarefas de referência.
* [ ] Avaliar os resultados e a taxa de aprovação dos testes.
* [ ] Medir tentativas de correção e consumo de tokens, quando disponível.
* [ ] Implementar o relatório final.
* [ ] Finalizar a documentação e os testes do sistema.

## Instalação e execução

### Pré-requisitos

* Python 3.12 ou superior.
* [uv](https://docs.astral.sh/uv/).
* Credenciais para o provedor de modelo escolhido.
* Dependências configuradas no `pyproject.toml`.

### Configuração

Clone o repositório:

```bash
git clone <URL_DO_REPOSITORIO>
cd mini-dev-team
```

Instale as dependências:

```bash
uv sync
```

Crie o arquivo `.env` a partir do exemplo:

**Windows — PowerShell**

```powershell
Copy-Item .env.example .env
```

**Linux — macOS**

```bash
cp .env.example .env
```

Configure as variáveis exigidas pelo provedor de modelo e pelo projeto. Consulte o `.env.example` para identificar os nomes utilizados na implementação.

### Execução

Após a implementação do agente principal e a configuração do Google ADK, a interface de desenvolvimento poderá ser iniciada com:

```bash
uv run adk web src/mini_dev_team
```

A execução de testes automatizados poderá ser realizada com:

```bash
uv run pytest
```

> Os comandos e as configurações serão ajustados conforme a implementação evoluir. A execução do código gerado deverá ocorrer em um ambiente isolado e com permissões restritas.

## Segurança

Como o sistema poderá gerar e executar código dinamicamente, a segurança será um requisito fundamental.

A execução deverá ser isolada do ambiente principal, com restrições de acesso a arquivos, credenciais, rede e recursos computacionais. O sistema também deverá limitar o tempo de execução e impedir que os agentes modifiquem arquivos fora dos diretórios autorizados.

As ferramentas disponíveis para cada agente deverão possuir apenas as permissões necessárias para suas responsabilidades.

## Escopo inicial

A primeira versão será limitada a pequenas funcionalidades em Python.

Integrações com GitHub, criação de pull requests, suporte a outras linguagens e desenvolvimento de aplicações completas ficam fora do escopo inicial e poderão ser consideradas em versões futuras.

## Objetivo de aprendizado

O Mini Dev Team AI também funciona como um laboratório prático para estudar:

* Sistemas multiagentes.
* Google ADK e composição de agentes.
* Tool calling e integração com ferramentas.
* Workflows sequenciais e ciclos de correção.
* Saídas estruturadas e gerenciamento de estado.
* Testes automatizados e revisão de código.
* Guardrails, isolamento e avaliação de sistemas de IA.

---

**Mini Dev Team AI** — explorando o desenvolvimento de software por meio de agentes de inteligência artificial colaborativos.
