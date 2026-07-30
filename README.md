# Lab 02 - Sockets L4, HTTP/1.1 a 3 e Server-Sent Events

**Microservice and Web Engineering & IT Services**
Prof. José Romualdo da Costa Filho | FIAP Sistemas de Informacao | 1o semestre de 2026-2

> Aula 02 - Protocolos de Aplicacao, SSE, Wireshark e Git Workflows | 11/08/2026

---

## Missao

Implementar o servidor de telemetria especificado na Aula 01: sockets TCP/UDP em Python e, sobre eles, um feed de rastreamento via SSE em Node.

Todos os laboratorios da disciplina evoluem o mesmo case: a **LogiTech Enterprise AI Platform**, uma
transportadora ficticia. O que voce entrega aqui e reaproveitado nas aulas
seguintes e desemboca na Global Solution.

---

## Como comecar

### Opcao 1: GitHub Codespaces (recomendado)

Clique em **Code > Codespaces > Create codespace on main**. O ambiente sobe
pronto, com todas as dependencias e o cliente de IA ja configurado. Nada para
instalar na sua maquina.

### Opcao 2: Local com Dev Container

Requer Docker e a extensao **Dev Containers** no VS Code.

```bash
git clone https://github.com/josercf/mwe-2026-2-lab02-http-sse.git
cd mwe-2026-2-lab02-http-sse
code .
# VS Code vai sugerir: "Reopen in Container"
```

Localmente, exporte o token para habilitar o assistente de IA:

```bash
export GITHUB_TOKEN=$(gh auth token)
```

---

## Assistente de IA incluso

O laboratorio traz um cliente minimo que fala com **GitHub Models** usando o
token que o Codespaces ja injeta. Voce nao precisa criar conta, gerar chave nem
cadastrar cartao.

```bash
python ai/ask.py "explique a diferenca entre TCP e UDP em duas frases"

# escolher outro modelo pequeno
MODEL=microsoft/phi-4-mini-instruct python ai/ask.py "..."

# usar um arquivo como prompt
cat prompts/prd.md | python ai/ask.py
```

Se o GitHub Models estiver indisponivel ou a cota da sua conta tiver acabado, o
script cai automaticamente para um **Ollama local**:

```bash
ollama serve
ollama pull qwen2.5:3b     # ~2 GB, roda em notebook sem GPU
```

> A cota gratuita do GitHub Models e limitada por dia. Se a turma inteira
> disparar requisicoes ao mesmo tempo, o fallback local resolve.

---

## Entregaveis

- `sockets-l4/server_telemetry.py`
- `sse/server.js`

Portas expostas pelo ambiente: 3000, 8080, 8081

---

## Regras de entrega

1. Trabalho em **dupla**. Um repositorio por dupla, gerado a partir deste
   (use **Fork** ou **Use this template**).
2. Commits seguindo [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/):

   ```bash
   git commit -m "feat(telemetria): adiciona listener UDP na porta 8081"
   ```

3. Submeta a URL do repositorio no formulario da disciplina ate o fim da aula.

---

## Estrutura

```
mwe-2026-2-lab02-http-sse/
├── .devcontainer/
│   ├── devcontainer.json   # ambiente reproduzivel (Codespaces e local)
│   └── post-create.sh      # instalacao de dependencias
├── ai/
│   └── ask.py              # cliente de IA (GitHub Models -> Ollama)
├── docs/                   # artefatos de especificacao
└── README.md
```

---

## Material da aula

- Slides: <https://josercf.github.io/FIAP-2026-2-3SI/>
- Biblioteca de skills: <https://github.com/josercf/skill-library>
