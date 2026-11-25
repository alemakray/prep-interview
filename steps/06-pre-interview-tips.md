# Etapa 6: Dicas pré-entrevista

## Objetivo

Deixar o candidato descansado, tranquilo e sem imprevistos no dia da
entrevista. O conteúdo técnico já foi trabalhado nas etapas anteriores; aqui o
foco é o preparo físico, mental e logístico.

## Inputs

- `context.json` da vaga: empresa, fase do processo, `schedule` (data, horário,
  entrevistadores) e pistas do formato (live coding, case, painel).
- `profile/candidate-profile.json`: localização e fuso, nível de inglês.
- Se faltar a data, o horário, o fuso da empresa ou a plataforma (Zoom, Teams,
  Meet), pergunte em uma única mensagem e salve as respostas.

## Procedimento

Monte um checklist **personalizado** para a vaga e a fase. Use os blocos
abaixo como base e corte o que não se aplica (ex.: sem live coding, não fale de
IDE). No máximo ~25 itens no total.

### 6.1 Logística (até 2 dias antes)

- Converter o horário para o fuso do candidato e criar lembrete com
  antecedência. Atenção a horário de verão em um dos dois países.
- Testar a plataforma da call com o mesmo computador: link, áudio, câmera,
  compartilhamento de tela.
- Se houver live coding ou case: testar o editor ou a ferramenta que vão usar
  (ex.: CoderPad, HackerRank, Miro) e deixar o ambiente pronto.
- Plano B: internet de backup (roteador do celular), número ou e-mail do
  recrutador para avisar se cair.
- Revisar os nomes e cargos dos entrevistadores (etapa 4) e as 3 perguntas que
  o candidato vai fazer.

### 6.2 Véspera

- **Parar de estudar conteúdo técnico novo.** No máximo uma revisão leve de 30
  minutos das anotações-resumo. Estudar em cima da hora aumenta a ansiedade e
  quase não aumenta o desempenho.
- **Ensaiar em voz alta**, 2 ou 3 vezes: o "Tell me about yourself", o "Why
  us?" e 2 histórias STAR. Gravar uma vez e ouvir ajuda a cortar vícios de
  linguagem.
- Separar roupa (pelo menos a parte que aparece na câmera), água e papel.
- Dormir bem. Evitar álcool e telas até tarde.

### 6.3 No dia

- **Ambiente tranquilo:** porta fechada, aviso para quem mora junto, sem
  barulho de fundo. Fundo limpo ou desfocado.
- **Equipamento:** fone com microfone, câmera na altura dos olhos, luz de
  frente (não de costas para a janela), notebook na tomada, internet por cabo
  se possível.
- **Notificações desligadas:** celular no silencioso e longe, apps de
  mensagem fechados, só as abas necessárias abertas.
- **Corpo:** refeição leve 1 a 2 horas antes, **água por perto**, sem exagero
  de café. Ir ao banheiro antes.
- **Aquecimento em inglês:** 15 a 20 minutos antes, falar inglês em voz alta
  (ler um texto técnico, repetir a apresentação, ouvir um podcast). A primeira
  frase da entrevista não deve ser a primeira em inglês do dia.
- **Respiração:** 2 minutos de respiração lenta (ex.: inspirar 4 s, segurar
  4 s, soltar 4 s, segurar 4 s) para baixar a ansiedade.
- **Entrar na call 5 minutos antes**, com papel e caneta para anotar nomes e
  perguntas.

### 6.4 Durante

- Pausar 2 ou 3 segundos antes de responder; está tudo bem pensar.
- Pedir para repetir ou reformular se não entender ("Could you rephrase
  that?").
- Nas técnicas, pensar em voz alta. Se não souber, dizer o raciocínio
  ("I haven't used X, but here's how I'd approach it…").
- Respostas comportamentais com começo, meio e fim, em até 2 minutos.

### 6.5 Depois

- Anotar as perguntas que caíram, logo após a call, e salvar em
  `interview_history` do perfil (alimenta as próximas preparações).
- **E-mail de agradecimento** em até 24 horas, curto e personalizado, citando
  um assunto da conversa. Gere o rascunho no idioma da entrevista.

## Regras

- Tom de checklist prático, sem sermão. Itens curtos, com verbo no início.
- O checklist fica no idioma do candidato. As frases para usar na entrevista e
  o e-mail de agradecimento ficam no idioma da entrevista (ver princípio 8).
- Nada de conselho médico; para ansiedade forte, só técnicas gerais
  (respiração, ensaio, descanso).

## Output

- `outputs/<vaga>/06-pre-interview.md`: o checklist em formato `- [ ]` e o
  rascunho do e-mail de agradecimento.
- No chat: o checklist **completo** e o rascunho do e-mail. É exceção à regra
  de economia, porque o candidato vai usar o checklist como guia no dia.
