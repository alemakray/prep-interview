# Etapa 2: Sugestões de atualização do CV

## Objetivo

Sugerir ajustes no CV para a vaga analisada na etapa 1, usando projetos e casos
**reais** do candidato. As mudanças são **só sugestões**: nesta etapa nada é
editado, e o candidato não precisa aceitar nada para seguir. A edição do CV e o
PDF são oferecidos no **fim do fluxo** (ver `AGENT.md`).
Vale para qualquer vaga de tecnologia (dev, dados, SRE/DevOps, QA, segurança,
produto, gestão técnica).

## Inputs

- `outputs/context.json` da etapa 1 (gaps, keywords, nível, pontos fortes)
- `profile/cv.md` (texto do CV). O arquivo original só é aberto na geração do
  PDF ("Edição do CV", no fim do fluxo), para copiar o cabeçalho de contato e o estilo visual.

Sem a etapa 1, rode-a antes em modo compacto. Não sugira nada sem a vaga.
Se as respostas do candidato em 2.1 derrubarem o fit (score abaixo de 60 ou
gap estrutural novo), reaplique a recomendação de 1.8 antes de seguir com as
sugestões.

## Regras de escrita (o mais importante desta etapa)

1. **Mantenha o nível do candidato.** Identifique a senioridade pelo CV (cargos,
   anos, escopo) e escreva nesse nível. Não promova ninguém: um pleno não
   "definiu a estratégia da empresa", e um sênior não "participou de". Os verbos
   e o escopo precisam bater com os cargos que já estão no CV.
2. **Mantenha a voz e o formato do candidato.** Tamanho das frases, tom, idioma e
   estrutura das seções continuam iguais. O CV editado precisa parecer escrito
   pela mesma pessoa.
3. **Nada de fórmula "verbo + métrica + %".** Não transforme tudo em bullet com
   número. Descreva o contexto, o que foi feito e o que mudou, em linguagem
   concreta (sistema, problema, decisão, efeito). Use número só quando o
   candidato fornecer um número real.
4. **Zero invenção.** Só entra o que está no CV ou o que o candidato confirmar
   na conversa. Gap sem experiência real não vira linha de CV: vira uma linha
   de "estudar antes da entrevista".
5. **Sem clichês de CV gerado por IA.** Evite "spearheaded", "leveraged",
   "results-driven", "passionate", "cutting-edge", "drove X% improvement",
   "proven track record", "dynamic".
6. **Keywords com naturalidade.** Termos da vaga entram dentro de frases sobre
   trabalho real, nunca como lista solta para enganar o ATS.
7. **Mude pouco e com motivo.** Sugira só o que aumenta o fit (no máximo ~8
   alterações). Experiências irrelevantes para a vaga ficam como estão ou são
   encurtadas.

## Procedimento

### 2.1 Buscar casos reais para os gaps

Comece pelas `open_questions_for_candidate` do `context.json` (não crie
perguntas novas sobre o mesmo ponto). Antes de perguntar, consulte também
`profile/candidate-profile.json` (`tools`,
`education`, `exit_reasons`): o que já está lá não se pergunta de novo.
Para cada gap de impacto alto ou médio do `context.json`, faça **uma** pergunta
objetiva. Mande todas numa única mensagem, no máximo 5:

> "A vaga pede X. Você já usou X (ou algo parecido) em algum projeto? Se sim:
> onde, para resolver o quê e o que mudou depois?"

Pergunte também se existe algum projeto real relevante para a vaga que ficou
fora do CV. Espere a resposta antes de seguir. Se o candidato responder "não"
para algum gap, ele fica fora do CV. Salve as respostas no perfil (ex.:
`tools.<ferramenta> = "never_used"`).

### 2.2 Reformular o resumo (introdução)

Escreva uma versão nova do resumo, com 3 a 4 frases, na voz do candidato.

- Puxe para frente a experiência real que mais se sobrepõe à vaga.
- **Seja discreto:** não cite a empresa nem o título exato da vaga, não copie
  frases da JD e não use "seeking a role as…".
- **Teste:** o resumo continua fazendo sentido para outras vagas parecidas? Se
  um recrutador lesse a JD e o resumo lado a lado, pareceria cópia? Se
  parecer, reescreva.

### 2.3 Sugestões por seção

Liste só os itens que mudam, nesta ordem: experiência atual → experiências
relevantes → competências → formato. Para cada item:

```
[Seção / empresa]
Antes:  <texto atual, ou "—" se for novo>
Depois: <texto sugerido>
Por quê: <uma linha: qual requisito da vaga isso cobre>
```

Também vale sugerir: reordenar experiências ou competências, encurtar o que é
irrelevante, explicitar algo que estava implícito (ex.: uma ferramenta usada
mas não citada).

### 2.4 Ajustes de formato para vagas internacionais

Aponte só o que se aplica: foto, idade, estado civil, documentos, endereço
completo, certificação vencida, tamanho (1 a 2 páginas; até 3 para 15+ anos),
idioma do CV, layout que o ATS não lê (colunas, tabelas, texto em imagem).

### 2.5 Fechamento

**Imprima as sugestões completas no chat**: o novo resumo, cada
Antes / Depois / Por quê, os ajustes de formato e a lista "fora do CV". Isso é
exceção à regra de economia, porque o candidato precisa ler sem abrir o
arquivo. Termine com:

> "Essas são sugestões, nada foi alterado no seu CV. Vamos seguir para a
> próxima etapa; no fim do processo eu pergunto se você quer aplicar alguma."

Não pergunte sobre edição ou PDF aqui.

## Edição do CV (só no fim do fluxo, se o candidato aceitar)

Disparada pela pergunta de fim de fluxo do `AGENT.md`, ou quando o candidato
pedir a qualquer momento.

- Use `profile/cv.md` com as sugestões aceitas aplicadas. O cabeçalho de contato
  (nome, telefone, e-mail, LinkedIn) vem do arquivo original, lido só nesse
  momento e nunca salvo em cache.
- Pergunte quais sugestões aplicar (todas, algumas pelo número, ou nenhuma).
- Aplique só as sugestões aceitas. Mantenha a ordem das seções e o estilo
  visual do original sempre que possível.
- Formato amigável para ATS: uma coluna, texto selecionável, fontes padrão,
  sem informação importante em tabela ou imagem.
- Use a ferramenta disponível no runtime (HTML + navegador headless, pandoc,
  LaTeX, DOCX→PDF). Se o runtime não gera arquivos, entregue o CV final em
  Markdown para o candidato exportar.
- Salve em `outputs/cv-<empresa>-<AAAA-MM-DD>.pdf` e confira se o texto foi
  extraído corretamente (sem caracteres quebrados).

## Outputs

- `outputs/02-cv-suggestions.md` (formato em `templates/02-cv-suggestions.md`)
- `context.json`: atualizar `step_completed: 2` e `cv_update` (com
  `applied: null` até o fim do fluxo)
- Na edição do CV (fim do fluxo): PDF em `outputs/cv-<empresa>-<AAAA-MM-DD>.pdf`
  e `cv_update.applied: true` com a lista de sugestões aceitas

## Critério de pronto

- [ ] Toda sugestão se apoia no CV ou em resposta do candidato
- [ ] Nível e voz do candidato preservados; nenhuma métrica inventada
- [ ] O resumo passa no teste de discrição
- [ ] Sugestões impressas completas no chat, sem editar nada
