---
name: prep-interview
description: Interview-prep agent for tech jobs. Use when the user runs /prep-interview or asks to analyze a CV against a job description, suggest CV improvements for a job, research a hiring company, prepare recruiter/technical/manager interviews, build a study plan for gaps, run a mock interview, negotiate an offer, triage jobs quickly (--quick) or compare analyzed jobs (--compare).
argument-hint: "[pedido livre | --quick | --compare | --all | etapa 0-8] [cv] [vaga]"
---

# prep-interview

Todos os caminhos são relativos à raiz deste repositório.

1. Leia `AGENT.md` e siga os princípios, o fluxo, os modos e a memória do
   candidato. Ele tem precedência sobre o estilo padrão de resposta.
2. Leia `profile/candidate-profile.json` e, se existir,
   `outputs/<vaga>/context.json`.
3. Leia **só** o arquivo da etapa que vai rodar (`steps/0N-*.md`) e o template
   dela. Não carregue as outras etapas.
4. Interprete os argumentos, nesta ordem (detalhes em "Navegação" no
   `AGENT.md`):
   - sem `profile/candidate-profile.json` → etapa 0 (onboarding) antes de tudo
     (exceto `--quick`)
   - `--quick` → modo rápido · `--compare` → comparar · `--all` → modo contínuo
   - `etapa N` → roda a etapa N na vaga indicada ou na mais recente
   - CV + vaga sem flag → etapa 1 completa
   - texto livre ("tenho técnica amanhã", "quero treinar") → identifique a
     intenção e a etapa
   - sem argumentos → painel das vagas salvas e sugestão de continuação; sem
     vagas, peça CV e vaga
5. Salve os resultados em `outputs/<empresa>-<id>/` e os fatos novos do
   candidato em `profile/` (crie as pastas se não existirem).
6. Economia:
   - Use `profile/cv.md` em vez de reler o PDF (ver `AGENT.md`). Para criar o
     cache, tente `pdftotext -layout <cv.pdf> -`; só se não estiver instalado
     ou não houver texto, leia o PDF.
   - **Pesquisa em lote** (etapas 3, 4 e 8, com 3 ou mais buscas ou leitura
     de páginas): mande tudo para **um** subagent com `model: "haiku"` (ou
     `"sonnet"` se as páginas forem complexas), pedindo um resumo estruturado
     com fontes. **Busca isolada** (1 ou 2): chame WebSearch direto. Rode
     buscas independentes em paralelo.
   - Não leia os schemas se o `context.json` da vaga já existir.
7. PDF do CV ("Edição do CV" da etapa 2, no fim do fluxo): gere um HTML de uma
   coluna e converta com o que estiver disponível, nesta ordem: `pandoc`,
   `chromium`/`google-chrome --headless --print-to-pdf`, `wkhtmltopdf`,
   `libreoffice --convert-to pdf`. No WSL sem nenhum deles, use o Chrome ou
   Edge do Windows em headless, convertendo os caminhos com `wslpath -w`. Se
   nada funcionar, entregue o HTML e peça para o candidato imprimir em PDF.

Argumentos recebidos: $ARGUMENTS
