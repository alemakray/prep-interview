# Etapa 4: Processo seletivo (simulação por fases)

## Objetivo

Preparar o candidato para cada fase do processo, supondo que a candidatura
avançou. Cada fase roda **uma por vez**, com as respostas impressas completas
no chat e salvas em `outputs/<vaga>/04-<fase>.md`. Ao terminar uma fase,
use a regra de **próximo passo** do `AGENT.md` (a fase seguinte costuma ser a
opção 1, mas a candidatura real pode indicar outra).

| Fase | Arquivo de saída |
|------|------------------|
| 4.1 Conversa com recrutador(a) | `04-1-recruiter.md` |
| 4.2 Entrevista técnica | `04-2-technical.md` |
| 4.3 Entrevista com o gerente da vaga | `04-3-manager.md` |

## Regras gerais

- **Pesquise perguntas reais** sobre a empresa e o cargo em fóruns e redes
  (Reddit, LinkedIn, Glassdoor Interviews, Blind, Levels.fyi, comunidades
  tech), com 2 a 3 buscas. Se a empresa não tiver relatos, pesquise o cargo e
  o nível em geral. Reutilize as perguntas já salvas em
  `profile/companies/<empresa>.md` (se tiverem menos de 30 dias) e salve as
  novas lá. As buscas rodam no modelo menor. Marque a origem de cada pergunta:
  **[relato]** (veio de fonte, com link) ou **[comum]** (padrão de mercado).
- **As respostas usam só o que é real.** A base é o CV e o que o candidato
  confirmou. Antes de tudo, consulte `profile/candidate-profile.json`. Onde
  ainda faltar um fato (motivo de saída, pretensão salarial, data de início),
  deixe um campo **[preencher: …]** em vez de inventar, e salve no perfil
  quando o candidato informar.
- **Pesquisa dos entrevistadores (opcional):** se o candidato souber o nome de
  quem vai entrevistá-lo em alguma fase, pesquise o perfil público (LinkedIn,
  posts, palestras, artigos, GitHub). Levante cargo, tempo de casa, trajetória,
  temas sobre os quais fala e pontos em comum com o candidato. Sugira 1 ou 2
  ganchos para a conversa e o que esse perfil provavelmente vai valorizar.
  Use só informação pública e profissional, nada pessoal. Registre na seção
  "Quem vai te entrevistar" do arquivo da fase.
- **Idioma:** pergunta, resposta modelo, tópicos-chave, `Bridge:` e
  `Why it's a trick:` são **todos no idioma da entrevista**, sem misturar (ver
  princípio 8). Dicas ao candidato ficam fora do bloco, no idioma dele.
  Exemplo de bloco correto:
  ```
  1.1 How would you connect two VNets? [relato]
  - Peering, regional or global. CIDRs can't overlap.
  - Many VNets: hub-and-spoke with a firewall and UDRs, or Virtual WAN.
  - Bridge: the hub-and-spoke I built at <empresa do CV>.
  ```
- **Voz e nível do candidato**, no idioma da entrevista. As respostas são para
  falar, não para ler: frases curtas e naturais.
- **Respostas comportamentais** seguem STAR (Situation, Task, Action, Result)
  sem rotular as partes, e o resultado é qualitativo se o candidato não tiver
  número real.

- **Registro para as próximas etapas:** ao fim de cada fase, salve em
  `context.json` → `interview_prep.<fase>` só os **títulos** das perguntas, e
  em `interview_prep.tricks_asked` as tricks usadas. A etapa 7 e as próximas
  execuções leem daí, sem abrir os arquivos `.md`.

## 4.1 Recrutador(a)

Objetivo da fase: triagem de fit, comunicação, inglês, logística e salário.
Faça de 8 a 10 perguntas, sempre incluindo:
- "Tell me about yourself" (60–90 s)
- motivo da mudança; sinais de atenção do `context.json` (vínculos curtos,
  ex-funcionário, gaps)
- **pretensão salarial com valor sugerido, baseado em pesquisa:**
  1. **Pesquise** (na mesma rodada de buscas da fase, pelo modelo menor):
     - **salário na empresa:** Glassdoor, Levels.fyi, Payscale, Indeed, relatos
       no Reddit e LinkedIn para o cargo ou cargos parecidos na mesma empresa;
     - **mercado:** o mesmo cargo e nível, no país do candidato e no modelo da
       vaga (CLT local, PJ, contractor em USD, EOR), em fontes de mercado e
       pesquisas salariais de consultorias de RH.
     - Reutilize a pesquisa salarial em `profile/companies/<empresa>.md` se
       tiver menos de 30 dias; senão, salve a nova lá. A etapa 8 reaproveita
       essa pesquisa.
  2. **Calcule a faixa sugerida:** cruze a empresa e o mercado com o
     `compensation` do perfil. O piso fica **acima do mínimo aceitável** do
     candidato e perto da mediana do mercado; o teto fica no percentil alto
     se o fit for forte. Use a moeda e o período da vaga (ex.: USD/mês para
     contractor, R$/mês ou ano para CLT).
  3. **Mostre, fora do bloco de resposta** e no idioma do candidato, uma
     tabela curta com fonte, data e valor de cada dado, e a faixa sugerida.
     Se os dados forem escassos ou antigos, diga isso e explique como a faixa
     foi estimada.
  4. **Resposta modelo** (no idioma da entrevista) com duas versões:
     - **principal:** dá a faixa sugerida com justificativa curta (escopo da
       vaga, experiência) e flexibilidade no pacote;
     - **alternativa:** devolve a pergunta ("budget range?") só se a
       recrutadora insistir em ouvir primeiro, já com a faixa pronta para
       a próxima resposta.
  Nunca invente um valor sem fonte. Se não houver dado nenhum, diga isso e
  peça o mínimo e a meta ao candidato.
- disponibilidade, aviso prévio, fuso, modelo de contrato
- checagem rápida dos must-haves com gap (resposta honesta + ponte)
- 3 perguntas para o candidato fazer ao recrutador

## 4.2 Técnica

- **Tópicos:** cada must-have técnico da JD vira um tópico, com **no máximo 6
  tópicos**. Se houver mais, agrupe requisitos relacionados (ex.: "Entra ID +
  RBAC + secrets", "Docker + Kubernetes"). Nice-to-haves técnicos entram só se
  sobrar espaço dentro dos 6.
- **4 perguntas por tópico**, calibradas pelo nível da vaga (inferido do título
  e dos requisitos da JD, não do candidato):

| Nível | Foco das perguntas |
|-------|--------------------|
| Júnior | conceitos, "o que é", comandos básicos |
| Pleno | como fazer, troubleshooting comum, boas práticas |
| Sênior | design, trade-offs, falhas em produção, segurança, escala |
| Especialista | arquitetura entre times, governança, decisões com custo/risco, padrões de organização |

- Para cada pergunta: **resposta modelo** curta (pontos-chave que o
  entrevistador quer ouvir) e, quando houver, ponte com experiência real.
- **Trick questions (3 por execução):** perguntas curtas que parecem fáceis,
  mas pegam quem decorou sem entender, ou que escondem uma premissa errada.
  Exemplo clássico: "Qual protocolo e qual porta o `ping` usa?" Resposta: ICMP
  (echo request/reply), que roda direto sobre IP; não usa TCP nem UDP, então
  **não tem porta**.
  - **Focadas na JD:** cada trick sai de um tópico técnico da vaga (ex.: rede,
    DNS, Kubernetes, IaC, CI/CD, cloud, banco, linguagem).
  - **Aleatórias:** sorteie os tópicos e varie as perguntas a cada execução.
    Não repita trick que já esteja em `context.json` (`interview_prep.tricks_asked`)
    nem em `interview_history` do perfil.
  - **Formato:** pergunta → resposta certa curta → **por que é trick** (qual a
    resposta errada comum e por que está errada) → como responder com
    segurança se o candidato não souber ("I'm not 100% sure, but my reasoning
    is…").
  - Misture as tricks entre as perguntas normais da fase, sem agrupar no fim.
- **Live test / case:** se você conhece ou encontrou relato de que a empresa
  aplica live coding, troubleshooting ao vivo, system design, take-home ou
  case, imprima um exemplo no mesmo formato, com enunciado e uma solução modelo
  (código, comandos ou desenho da arquitetura explicado). Se não houver
  relato, mostre o formato mais comum para o cargo e o nível, marcado como
  [comum].

## 4.3 Gerente da vaga

- 6 a 8 perguntas de soft skills: conflito, prioridade sob pressão, erro em
  produção, influência sem autoridade, feedback, autonomia remota, lidar com
  ambiguidade do cliente, aprendizado rápido.
- As respostas devem "fazer brilhar os olhos do gerente", mostrando o que
  gerentes valorizam: **ownership**, comunicação
  proativa (avisar cedo, não esconder problema), pensar no negócio/cliente,
  reduzir risco, deixar o time mais autônomo (documentação, padrões),
  aprender rápido e assumir erro com o que mudou depois.
- Cada resposta usa uma história do banco `profile/star-stories.md`, adaptada
  à vaga. Se o banco ainda não existir, monte-o primeiro (ver `AGENT.md`).
- Feche com 3 perguntas para o candidato fazer ao gerente, que mostrem
  interesse no sucesso do time.
- Se esta for a última fase pedida, faça a pergunta de **fim do fluxo** sobre a
  edição do CV (ver `AGENT.md`).
