# Etapa 7: Simulação de entrevista ao vivo (mock)

## Objetivo

Treinar de verdade. O agent faz o papel do entrevistador, uma pergunta por
vez, espera a resposta do candidato e dá feedback.

## Configuração (pergunte no início, em uma mensagem)

- **Fase:** recrutador, técnica, gerente ou mista
- **Quantidade de perguntas** (padrão: 6)
- **Feedback:** depois de cada resposta, ou só no final (padrão: no final, como
  numa entrevista real)
- **Dificuldade:** nível da vaga (padrão) ou um acima

## Condução

1. Fale **no idioma da entrevista**, no tom do entrevistador da fase. Comece
   com uma apresentação curta do entrevistador, como numa call de verdade.
2. **Uma pergunta por mensagem.** Espere a resposta. Não dê dica nem
   resposta durante a simulação.
3. Faça **follow-ups** como um entrevistador real: "Why?", "What would you do
   differently?", "How would that scale?". No máximo 1 ou 2 por pergunta.
4. Misture perguntas da etapa 4 (`context.json` → `interview_prep`) com
   perguntas novas. Na fase técnica, inclua
   pelo menos **1 trick question** (ver etapa 4.2), sem avisar que é trick.
5. Se o candidato responder em português, siga a simulação e registre isso no
   feedback.
6. O candidato pode dizer "pausa" ou "parar" a qualquer momento.

## Feedback (no idioma do candidato; a "versão melhorada" fica no idioma da entrevista)

Para cada resposta:

| Critério | O que avaliar |
|----------|---------------|
| Conteúdo | respondeu o que foi perguntado? Está tecnicamente correto? Ficou no nível da vaga? |
| Estrutura | STAR nas comportamentais; nas técnicas, começa pela resposta e depois detalha |
| Clareza e tamanho | objetiva? Longa demais (mais de 2 min) ou curta demais? |
| Inglês | erros de gramática que atrapalham, vocabulário técnico, palavras de preenchimento, falsos cognatos comuns de brasileiro (ex.: "actually", "pretend", "assist") |
| Sinal para o entrevistador | o que essa resposta comunica (ownership, senioridade, insegurança…) |

- **Nota de 1 a 5** por resposta, com **uma frase de melhoria** e uma
  **versão melhorada** curta (usando só fatos reais).
- **No final:** nota geral, os 3 pontos que mais precisam melhorar e se o
  candidato passaria nessa fase (sim / no limite / não), com o motivo.

## Output

- `outputs/<vaga>/07-mock-<fase>-<n>.md` **compacto**: para cada pergunta, o
  título, a nota e uma linha de melhoria, mais a nota geral e os 3 pontos a
  melhorar. Não transcreva as respostas do candidato nem repita o feedback
  completo, que já está no chat. Isso basta para medir a evolução entre
  simulações.
- Adicione as tricks usadas a `interview_prep.tricks_asked`.
- Atualize `profile/star-stories.md` se surgir uma história nova boa, depois de
  confirmar com o candidato.
- No chat, a simulação acontece completa. O feedback final também vai completo.
