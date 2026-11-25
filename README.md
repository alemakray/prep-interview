<div align="center">

# 🎯 prep-interview

**Seu coach de entrevistas para vagas de tecnologia fora do Brasil, rodando no Claude Code.**

Mande seu CV e o link da vaga: o agent analisa o fit, sugere ajustes no CV, pesquisa a empresa,
prepara você para cada fase do processo seletivo, simula a entrevista em inglês e ajuda a negociar a oferta.

[![Claude Code](https://img.shields.io/badge/Claude%20Code-agent-D97757?logo=anthropic&logoColor=white)](https://claude.com/claude-code)
[![Modelo](https://img.shields.io/badge/modelo-Sonnet-8A63D2)](#-modelo-e-custo)
[![Idioma](https://img.shields.io/badge/idioma-PT--BR%20%2B%20EN-2EA44F)](#-princípios)
[![Licença: MIT](https://img.shields.io/badge/licen%C3%A7a-MIT-blue.svg)](LICENSE)

</div>

---

## ✨ O que ele faz

| | Etapa | O que você recebe |
|---|---|---|
| 👤 | **0. Perfil** | Um questionário único que monta seu perfil e um banco de 6 a 8 histórias STAR reais, salvos na sua máquina. Cada vaga depois só pergunta o que for novo |
| 📊 | **1. Análise de fit** | Nota de 0 a 100, requisito por requisito com evidência do seu CV, gaps e uma recomendação honesta: vale ou não se candidatar |
| 📝 | **2. Sugestões de CV** | Antes / Depois / Por quê, mantendo seu nível e sua voz. Nada é alterado sem você pedir |
| 🏢 | **3. Empresa** | Ramo, tamanho, receita, clientes, notícias, reputação, artigos de funcionários e a resposta para *"What do you know about us?"* |
| 🎤 | **4. Processo seletivo** | Recrutador (com faixa salarial pesquisada), entrevista técnica (com *trick questions* e live test) e gerente (soft skills, com suas histórias STAR adaptadas para a vaga) |
| 📚 | **5. Plano de estudo** | Os gaps viram um cronograma com mini-projetos até a data da entrevista |
| 🧘 | **6. Dicas pré-entrevista** | Checklist da semana, da véspera e do dia: ambiente, equipamento, descanso, ensaio da apresentação, aquecimento em inglês e e-mail de agradecimento |
| 🎭 | **7. Simulação ao vivo** | Uma pergunta por vez, em inglês, com nota e feedback de conteúdo e de inglês |
| 💰 | **8. Negociação** | Faixa de mercado, CLT × PJ × contractor e roteiro de contraproposta |

Funciona para **qualquer vaga de tecnologia**: dev, dados, DevOps/SRE, cloud, QA, segurança, produto.

## 🔄 Como funciona

```mermaid
flowchart LR
    CV["📄 Seu CV"] --> P0["Etapa 0 · Perfil"]
    JD["🔗 Vaga"] --> E1
    P0 --> E1["Etapa 1 · Análise de fit"]
    E1 -->|sem fit| X["🚫 Recomenda não se candidatar"]
    E1 -->|com fit| E2["Etapa 2 · Sugestões de CV"]
    E2 --> E3["Etapa 3 · Empresa"]
    E3 --> E4["Etapa 4 · Recrutador, Técnica, Gerente"]
    E4 --> FIM["✅ Aplicar sugestões e gerar PDF?"]
    E1 -. sob demanda .-> E5["Etapa 5 · Estudo"]
    E1 -. sob demanda .-> E6["Etapa 6 · Dicas pré-entrevista"]
    E1 -. sob demanda .-> E7["Etapa 7 · Simulação"]
    E1 -. sob demanda .-> E8["Etapa 8 · Negociação"]
```

## 🚀 Começando

**Pré-requisito:** [Claude Code](https://claude.com/claude-code) (plano Pro, Max ou chave de API).

```bash
git clone https://github.com/alemakray/prep-interview.git
cd prep-interview
claude
```

Dentro do Claude Code:

```text
/model sonnet
/prep-interview etapa 0                              # primeiro uso: monta seu perfil
/prep-interview inputs/cv/meu-cv.pdf <link-da-vaga>  # análise completa de uma vaga
```

O comando `/prep-interview` já vem no repositório (`.claude/skills/`) e fica disponível quando você abre o
Claude Code nesta pasta.

<details>
<summary><b>📦 Recomendado: instalar o <code>pdftotext</code></b></summary>

O agent lê o CV em PDF uma vez e guarda o texto em cache. Com o `pdftotext`, essa primeira leitura sai bem
mais barata (sem ele, cada página também vai como imagem).

```bash
sudo apt install -y poppler-utils   # Debian / Ubuntu / WSL
brew install poppler                # macOS
choco install poppler               # Windows (ou: scoop install poppler)
```

</details>

## 🧭 Conversando com o agent

Você não precisa decorar números de etapa. Fale do jeito que quiser:

```text
/prep-interview                                   # painel: suas vagas, onde parou e o que fazer agora
/prep-interview tenho call com o recrutador amanhã
/prep-interview me chamaram pra técnica dia 12
/prep-interview quero treinar
/prep-interview recebi a proposta
```

O agent:

- **Mostra onde você parou** quando você abre a sessão.
- **Sugere o próximo passo** no fim de cada etapa. Responda só com o número.
- **Acompanha o processo real** (aplicou, recrutador, técnica, gerente, proposta) e prepara a fase certa.
- **Prioriza pelo tempo:** entrevista amanhã? Vai direto para dicas e uma simulação curta. Uma semana? Monta
  o plano de estudo.
- **Faz o debrief** depois de cada entrevista e usa as perguntas que caíram na próxima preparação.
- **Deixa pular etapas:** se faltar algo, roda o mínimo necessário sozinho, sem travar.

### Atalhos

| Comando | O que faz |
|---|---|
| `/prep-interview <cv> <vaga>` | Análise completa de uma vaga (etapa 1) e segue o fluxo |
| `/prep-interview --quick <cv> <vaga>` | Triagem rápida: nota, veredito e 3 maiores gaps em ~10 linhas |
| `/prep-interview --compare` | Tabela comparando todas as vagas já analisadas |
| `/prep-interview --all <cv> <vaga>` | Modo contínuo: etapas 1 a 4 em sequência, parando só quando precisa de você |
| `/prep-interview etapa N` | Roda a etapa N (0 a 8) na vaga mais recente |

> 💡 **Fluxo econômico:** rode `--quick` em várias vagas, depois `--compare`, e faça a análise completa só
> nas que valem a pena.

A vaga pode ser um link (Greenhouse, Lever, Workday, Ashby, site da empresa), PDF, DOC ou texto colado.
Alguns sites, como o LinkedIn, bloqueiam leitura automática: nesse caso, cole o texto.

## 🧠 Princípios

- **Zero invenção.** Nada de experiência, métrica ou cargo que não esteja no seu CV ou que você não tenha
  confirmado. Toda afirmação cita a evidência.
- **Honestidade sobre o fit.** Se a vaga não combina com você, o agent diz isso com educação e sugere vagas
  mais alinhadas. A decisão é sua.
- **Seu nível e sua voz.** As sugestões de CV não inflam cargos nem usam a fórmula "verbo + métrica + %".
  O resumo é ajustado de forma discreta, sem parecer feito para a vaga.
- **Inglês onde importa.** Toda pergunta e resposta de entrevista sai 100% em inglês; orientações e feedback
  ficam em português.
- **Memória entre vagas.** Tudo o que você responde é salvo no seu perfil e não é perguntado de novo.

## 💸 Modelo e custo

**Use o Sonnet** (`/model sonnet`). Ele roda bem todas as etapas pela metade do preço do Opus.

| Uso | Modelo |
|---|---|
| Todas as etapas, `--quick`, `--compare` | **Sonnet** (recomendado) |
| CV (etapa 2) e simulação (etapa 7) | Opus, opcional, para mais refinamento |
| Buscas e leitura de páginas | Haiku, automático |

**Custo estimado do processo completo (etapas 0 a 8) com chave de API:** cerca de US$ 1,50 a 2,50 no Sonnet,
ou US$ 3 a 5 no Opus. São estimativas; use `/cost` no fim da sessão para ver o valor real. Nos planos Pro e
Max não há cobrança por token: o custo é o consumo do seu limite de uso.

<details>
<summary><b>⚡ Como o agent economiza tokens</b></summary>

- **Cache do CV:** o PDF é lido uma vez e vira `profile/cv.md`.
- **Cache de empresa:** a pesquisa fica guardada por 30 dias e é reaproveitada.
- **Perfil persistente:** o que você já respondeu não é perguntado de novo. As histórias STAR ficam em `profile/star-stories.md` e são reaproveitadas (e enriquecidas) a cada vaga.
- **Estado por vaga:** cada etapa lê só um `context.json` compacto, não os relatórios anteriores.
- **Modelo menor nas buscas:** pesquisas em lote vão para um subagent com Haiku.
- **Entrevista técnica enxuta:** no máximo 6 tópicos, agrupando requisitos parecidos.

**Hábitos que ajudam:**
- Abra o Claude Code nesta pasta, não dentro de um workspace de trabalho (que carrega `CLAUDE.md`, hooks e
  memórias de outros projetos em toda sessão).
- Use uma sessão por vaga ou por etapa (`/clear` entre elas). O estado fica salvo em arquivos, e o agent
  continua de onde parou.

</details>

## 🌐 Usando fora do Claude Code

O agent é só texto em Markdown, então dá para usar em outros chats de IA. A experiência é mais manual:
você perde o comando `/prep-interview`, os arquivos salvos automaticamente e as buscas com modelo menor.

### Passo a passo

1. **Crie um espaço com instruções fixas** no chat que você usa:

   | Chat | Onde |
   |---|---|
   | Claude.ai | **Projects** → instruções do projeto |
   | ChatGPT | **Projects** ou **Custom GPT** → instruções |
   | Gemini | **Gems** → instruções |
   | Outros / API | o *system prompt* |

2. **Cole o conteúdo do `AGENT.md`** como instrução.
3. **Adicione como arquivos de conhecimento** os arquivos de `steps/` e `templates/`. Se o chat não aceitar
   arquivos, cole o conteúdo da etapa no início da conversa.
4. **Comece pela etapa 0:** envie seu CV e peça *"rode a etapa 0"*.
5. **Para cada vaga:** envie o CV e o link ou texto da vaga e peça *"rode a etapa 1"*. Depois, *"etapa 2"*,
   *"etapa 3"* e assim por diante.

### Guardando a memória entre conversas

Sem acesso a arquivos, o agent não consegue salvar sozinho. No fim de cada etapa, peça:

> *"Me mostre o `context.json` desta vaga e o `candidate-profile.json` atualizados."*

Guarde os dois (num arquivo de texto ou como arquivo do projeto) e cole na próxima conversa. Assim o
agent continua de onde parou e não repete perguntas.

### O que muda

| Recurso | Claude Code | Outros chats |
|---|---|---|
| Ler CV em PDF | ✅ | ✅ na maioria (anexo) |
| Pesquisa na web (etapas 3, 4 e 8) | ✅ | ✅ se o chat tiver busca ativada |
| Memória entre vagas | ✅ automática | ⚠️ manual (copiar e colar) |
| Gerar o PDF do CV | ✅ | ⚠️ depende do chat (alguns executam código) |
| Simulação ao vivo (etapa 7) | ✅ | ✅, mas pode bater no limite de mensagens do plano gratuito |

> ⚠️ **Qualidade:** as instruções foram escritas e testadas com o Claude. Modelos menores tendem a ignorar
> regras como "não inventar experiência" e "manter seu nível e sua voz". Prefira os modelos mais capazes do
> seu chat e confira as sugestões de CV com atenção.

## 🔒 Privacidade

Seus dados ficam **só na sua máquina**. As pastas `inputs/` (CV e vagas), `profile/` (perfil, histórias,
caches) e `outputs/` (resultados) estão no `.gitignore` e nunca vão para o repositório. O cache do CV não
guarda telefone, e-mail nem endereço.

> ⚠️ Guarde o CV numa pasta pessoal, não em armazenamento do seu empregador (OneDrive ou Drive corporativo).

## 📁 Estrutura

```text
prep-interview/
├── AGENT.md                     # instruções principais: princípios, fluxo, modos, memória
├── steps/                       # uma instrução por etapa (00 a 08)
├── templates/                   # formatos de saída e schemas JSON
├── .claude/skills/prep-interview/
│   └── SKILL.md                 # o comando /prep-interview
├── inputs/                      # 🔒 seus CVs e vagas
├── profile/                     # 🔒 seu perfil, histórias STAR e caches
└── outputs/<empresa>-<id>/      # 🔒 resultados por vaga
```

## 🤝 Contribuindo

Sugestões e PRs são bem-vindos: novas etapas, melhorias nas instruções, exemplos de vagas de outras áreas.
Ao abrir um PR, **não inclua CVs, vagas ou resultados reais**.

## 📄 Licença

[MIT](LICENSE)
