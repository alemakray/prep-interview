# Etapa 5: Plano de estudo dos gaps

## Objetivo

Transformar os gaps da vaga num plano de estudo prático com prazo, para que o
candidato chegue à entrevista falando com segurança sobre eles.

## Inputs

- `context.json` da vaga (gaps e o que ficou só como estudo, `cv_update.study_only`)
- `profile/candidate-profile.json` (o que o candidato já sabe ou nunca usou)
- **Data da entrevista e horas por dia disponíveis.** Pergunte, se não tiver.

## Procedimento

1. **Priorize os gaps** por impacto na vaga e por quanto o candidato consegue
   avançar até a data. Gap de must-have vem primeiro.
2. Para cada gap, defina:
   - **Objetivo:** o que o candidato precisa conseguir explicar ou fazer na
     entrevista (ex.: "explicar e desenhar um pipeline X → Y com autenticação
     sem secrets").
   - **Ponte:** o que ele já sabe que se parece com isso (ex.: Azure DevOps →
     GitHub Actions). É por onde o estudo começa.
   - **Conteúdo:** de 2 a 4 fontes, dando preferência a documentação oficial e
     tutoriais oficiais (Microsoft Learn, docs do produto). Só cite link que
     você abriu ou conhece com segurança.
   - **Mini-projeto:** algo pequeno e real que ele possa mostrar ou citar.
     Quando possível, junte vários gaps num repositório só.
   - **Tempo estimado**, em horas.
   - **Checagem:** 2 ou 3 perguntas que ele deve conseguir responder no fim.
3. **Monte o cronograma** até a data da entrevista, respeitando as horas por
   dia. Se não couber tudo, corte os gaps de menor impacto e diga quais
   ficaram de fora.

## Regras

- Seja realista: não prometa domínio de uma tecnologia em 2 dias. O objetivo é
  conseguir falar com honestidade ("I've been building X, here's what I
  learned").
- Quando o candidato concluir um item, atualize `candidate-profile.json`
  (ferramenta passa de "nunca usou" para "estudando" ou "projeto pessoal").

## Output

- `outputs/<vaga>/05-study-plan.md` com uma tabela por gap e o cronograma em
  checklist (`- [ ] dia X: …`).
- No chat: os 3 primeiros itens do cronograma e o caminho do arquivo.
