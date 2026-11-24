# Etapa 3: Insights da empresa

## Objetivo

Levantar o que o candidato precisa saber sobre a empresa: o que ela faz,
tamanho, receita, clientes, momento atual e reputação como empregadora. Com
isso, preparar a resposta para "What do you know about us?" e "Why us?".

Só roda quando a vaga tem fit (ver 1.8) ou quando o candidato decidiu seguir.

## Cache

Antes de pesquisar, procure `profile/companies/<empresa>.md`. Se tiver menos de
30 dias, reutilize o conteúdo e faça só uma busca de notícias recentes. Ao
terminar, salve ou atualize o cache com a data. As buscas e leituras de páginas
rodam no modelo menor (ver roteamento de modelo no `AGENT.md`).

## O que levantar

| Bloco | Itens |
|-------|-------|
| Identidade | o que faz, ramo/setor, sede, ano de fundação, fundadores ou CEO, capital aberto ou fechado (dono, fundos) |
| Tamanho | número de funcionários (e tendência), países ou regiões onde opera |
| Finanças | receita: auditada se for empresa aberta; se for fechada, estimativa com fonte; crescimento |
| Clientes | se for consultoria ou outsourcing: principais clientes públicos, setores atendidos, modelo de contratação (CLT, PJ, contractor) |
| Momento | notícias dos últimos 12 meses: aquisições, rodadas, parcerias, layoffs, troca de liderança, produtos novos |
| Reputação | nota no Glassdoor/Indeed (e quantidade de reviews), prós e contras recorrentes, relatos sobre o processo seletivo |
| Artigos de funcionários | artigos, posts ou palestras de funcionários da empresa ligados à área da vaga (ver abaixo) |
| Para este candidato | o que pesa no caso dele: modelo de contrato, moeda do pagamento, estabilidade, ligação com a experiência dele |

## Regras

1. **Todo número com fonte e data.** Se as fontes divergirem, mostre a faixa e
   diga qual é a mais confiável.
2. **Fato ≠ estimativa ≠ inferência.** Empresa fechada não publica receita:
   marque como estimativa. Conhecimento geral não verificado na busca vai
   marcado como **[verificar]**.
3. **Notícia recente pesa mais.** Dê prioridade aos últimos 12 meses e avise
   quando a fonte for antiga.
4. **Reputação equilibrada.** Mostre os temas que se repetem nos reviews, não
   um review isolado. Lembre que reviews são autosselecionados.
5. **Economia.** Faça de 3 a 5 buscas em paralelo, e só aprofunde se faltar
   algo importante.

## Artigos de funcionários

Procure conteúdo escrito por funcionários da empresa (atuais ou recentes) que
tenha relação com a área da vaga, mesmo que mínima, ou que seja
institucional:
- **Onde:** blog de engenharia da empresa, Medium, dev.to, LinkedIn Articles e
  posts, Substack, palestras (YouTube, conferências), repositórios públicos.
- **Buscas sugeridas:** `"<empresa>" engineering blog <tecnologia da vaga>`,
  `site:medium.com "<empresa>" <área>`, `site:linkedin.com/pulse "<empresa>"
  <área>`.
- **Prioridade:** 1) área técnica da vaga (ex.: DevOps, cloud, dados);
  2) engenharia em geral; 3) institucional (cultura, como trabalham, valores).
- **Registre de 3 a 5 itens:** título, autor e cargo (se público), data, link
  e uma linha sobre por que é útil na entrevista (assunto para puxar, sinal da
  stack, cultura do time).
- **Regras:**
  - só cite autor e cargo que estejam no próprio artigo ou perfil público;
  - não cite nada que você não abriu;
  - se não achar nada relevante, diga isso em uma linha.
- Se algum artigo combinar com a experiência do candidato, use-o como gancho
  na resposta abaixo ("I read a post from your team about…").

## Resposta para a entrevista

Escreva no idioma da entrevista, para ser falada em 45 a 60 segundos:

- **"What do you know about us?"**: 2 ou 3 fatos que mostram pesquisa (o que
  fazem, para quem, o momento atual). Não recite números, use no máximo um.
- **Ponte com o candidato**: ligue um fato da empresa a uma experiência real do
  CV. Só experiência que está no CV ou que o candidato confirmou.
- **"Why us?"**: uma ou duas frases, no nível e na voz do candidato, sem
  bajulação.
- Soa natural, não decorado. Sem clichês ("I've always admired…", "industry
  leader", "passionate").

## Output

- `outputs/<vaga>/03-company.md` (formato em `templates/03-company.md`)
- `context.json`: `step_completed: 3` e bloco `company` (resumo + fontes)
- No chat: até ~10 linhas com os insights e o veredito "bom lugar para
  trabalhar?", seguidas das respostas **completas** de "What do you know about
  us?" e "Why us?". Essas respostas são exceção à regra de economia: o
  candidato precisa lê-las sem abrir o arquivo.
