# Etapa 1: Intake e análise (CV × Job Description)

## Objetivo

Receber o CV do candidato e a descrição da vaga, extrair as informações dos
dois de forma estruturada e cruzar uma com a outra para medir o fit.

> **Modo rápido** (`--quick`): faça só 1.1, 1.2, 1.6 (sem a tabela no chat),
> 1.7 (só o score) e 1.8. Pule o checkpoint 1.3. No chat, mostre só: score,
> veredito, recomendação e os 3 maiores gaps. Salve `context.json` com
> `mode: "quick"`. Se depois o candidato pedir a análise completa, reaproveite
> a extração e complete só o que falta (matriz no relatório, pontos fortes,
> perguntas).

## Inputs obrigatórios

| Input | Formatos aceitos | Obrigatório |
|-------|------------------|-------------|
| **CV do candidato** | PDF, DOC/DOCX, TXT/MD, texto colado, link público (Google Drive/Docs público, site pessoal, PDF hospedado) | sim |
| **Job Description** | Link público da vaga (Greenhouse, Lever, Workday, Ashby, site da empresa, LinkedIn público), PDF, DOC/DOCX, texto colado | sim |

Inputs opcionais (melhoram a análise, mas não bloqueiam):
- Perfil do LinkedIn (export em PDF)
- País/fuso do candidato e situação de visto/autorização de trabalho
- Nível de inglês autodeclarado
- Pretensão salarial / moeda

## Procedimento

### 1.1 Coletar

- Se o candidato não mandou os dois inputs, peça exatamente o que falta:
  > "Para começar preciso de: (1) seu CV e (2) a descrição da vaga. Pode ser
  > link público, PDF, DOC ou texto colado."
- Não comece a análise com um input só.

### 1.2 Ler / extrair

- **Link:** abra a URL. Se der login wall, paywall, 404, conteúdo gerado por
  JavaScript que não carregou, ou a página estiver sem o texto da vaga, diga
  isso e peça o texto colado ou um PDF. Muitos sites de vagas bloqueiam
  leitura automática (LinkedIn e vários ATS). Se o link for de um
  deles, peça o texto colado logo de cara, sem gastar tentativas.
- **CV:** se existir `profile/cv.md` com a mesma origem e a mesma data de
  modificação, use-o e não releia o arquivo. Senão, extraia e crie o cache
  (ver `AGENT.md`).
- **PDF/DOC:** extraia o texto. Se for imagem escaneada sem texto, avise e
  peça outra versão (ou use OCR, se o runtime tiver).
- **Validação:** confirme que o documento é o que deveria ser (um CV de fato,
  uma vaga de fato). Se a vaga estiver expirada/fechada, avise.

### 1.3 Confirmar extração (checkpoint)

Mostre um resumo curto e peça confirmação antes de seguir:

```
Vaga:   <título> @ <empresa> | <local/remoto> | <senioridade>
CV:     <cargo atual> | <anos de experiência> | <stack principal>
Faltou: <o que não deu para ler, se houver>
Está correto? Posso seguir com a análise?
```

### 1.4 Estruturar a vaga (JD)

Extraia:
- Título, empresa, localização, modelo (remoto/híbrido/presencial), fuso
  exigido, restrições de país/visto
- Senioridade e nível (IC/lead/manager)
- **Must-have** (requisitos obrigatórios, literais)
- **Nice-to-have** (diferenciais)
- Responsabilidades principais
- Stack/tecnologias
- Soft skills e sinais de cultura/valores
- Faixa salarial e benefícios (se constar)
- Pistas sobre o processo seletivo (etapas, take-home, live coding)
- Ambiguidades e possíveis red flags da vaga

### 1.5 Estruturar o CV

Extraia:
- Resumo profissional e cargo atual
- Experiências (empresa, cargo, período, principais entregas)
- Conquistas **com métricas** (e as que não têm métrica)
- Skills técnicas (com onde aparecem no CV)
- Formação, certificações, idiomas
- Lacunas de tempo, trocas frequentes, inconsistências
- **Já trabalhou na empresa da vaga?** Se sim, marque como ponto de atenção
  (vai cair a pergunta "por que saiu e por que voltar?")

### 1.6 Cruzar CV × JD (matriz de fit)

Para **cada requisito** da JD:

| Requisito | Tipo | Evidência no CV | Status |
|-----------|------|-----------------|--------|
| ... | must / nice | trecho ou "sem evidência no CV" | ✅ atende / 🟡 parcial / ❌ gap |

Regras:
- ✅ só com evidência explícita.
- 🟡 quando há experiência relacionada ou transferível (explique o porquê).
- ❌ quando não há evidência. Não é "o candidato não sabe", é "o CV não mostra".

### 1.7 Score e diagnóstico

- **Fit score (0–100):** must-haves pesam 70%, nice-to-haves 20%, senioridade e
  contexto (fuso, idioma, domínio) 10%. Mostre o cálculo.
- **Top 5 pontos fortes** para explorar na entrevista.
- **Top 5 gaps/riscos**, ordenados por impacto, cada um com uma estratégia
  (como endereçar na conversa, o que estudar, o que ajustar no CV).
- **Keywords da JD ausentes no CV** (útil para ATS), sem sugerir mentir.
- **Perguntas prováveis** que o entrevistador vai fazer com base nos gaps e na
  stack (lista curta, só os títulos; a preparação vem nas próximas etapas).
- **Perguntas para o candidato** que esclareceriam pontos ambíguos do CV.

### 1.8 Recomendação de candidatura

Recomende **não se candidatar** quando houver pelo menos um destes sinais:
- score abaixo de 60;
- veredito "arriscado" ou "fora do perfil";
- gap estrutural em must-have que ajuste de CV não resolve (anos em outra
  trilha de carreira, diploma obrigatório ausente, restrição de país, visto
  ou clearance, idioma).

Como comunicar (tom educado, sem desanimar):
> "Pelo que vi, essa vaga não tem um bom fit com o seu perfil: <motivo em uma
> frase>. Minha sugestão é não investir nela e focar em vagas de <tipo de vaga
> alinhado ao perfil>. Quer seguir com a preparação mesmo assim?"

Só avance para a etapa 2 se o candidato confirmar. Se o fit for bom, diga
isso em uma linha e siga.

## Outputs

1. `outputs/context.json`: os dados estruturados da vaga e o fit, com
   `step_completed: 1`. Só os campos que as próximas etapas usam. Do
   candidato, guarde só `level`, `voice` e `attention_points`: experiências e
   skills já estão em `profile/cv.md` e não são duplicadas.
2. `outputs/01-analysis.md`: relatório **compacto** (cerca de uma página) no
   formato de `templates/01-analysis-report.md`. Ele não repete a extração da
   vaga nem a do CV, que já estão no `context.json`.

## Critério de pronto

- [ ] Os dois inputs foram lidos de fato (ou a limitação foi declarada)
- [ ] O candidato confirmou a extração
- [ ] Todo requisito da JD aparece na matriz
- [ ] Todo ✅/🟡 tem evidência citada
- [ ] Score com cálculo visível
- [ ] `01-analysis.md` e `context.json` gerados
