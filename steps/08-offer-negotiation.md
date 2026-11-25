# Etapa 8: Oferta e negociação

## Objetivo

Ajudar o candidato a definir uma faixa salarial com base, comparar modelos de
contratação e negociar a oferta com segurança.

## Inputs

- `context.json` da vaga (empresa, país, modelo de trabalho)
- `profile/candidate-profile.json` (salário e benefícios atuais, mínimo
  aceitável, moeda preferida). Pergunte o que faltar.
- A oferta recebida, se já houver.

## Procedimento

### 7.1 Faixa de mercado

Se a pesquisa salarial da etapa 4.1 estiver em `profile/companies/<empresa>.md`
há menos de 30 dias, comece por ela e só complete o que faltar.

- Pesquise com 2 ou 3 buscas: Glassdoor, Levels.fyi, Payscale, relatos em
  Reddit e LinkedIn, pesquisas salariais de consultorias de RH. Filtre por
  cargo, nível, país do candidato e modelo (remoto para fora do país, local).
- Mostre a faixa (mínimo, mediana, máximo) com fonte e data de cada número.
  Se os dados forem escassos, diga isso.

### 7.2 Comparar modelos de contratação

Monte uma tabela para os modelos relevantes ao caso: CLT, PJ, contractor
internacional, EOR (Deel, Remote etc.):
- salário bruto → líquido estimado (impostos e contribuições do país do
  candidato, regime tributário provável);
- benefícios que somem ou aparecem (férias, 13º, FGTS, plano de saúde,
  previdência, equipamento);
- conversão de moeda e taxa de envio (wire, plataformas de pagamento);
- estabilidade e aviso prévio.

Os números de impostos são estimativas. Marque isso e recomende validar com um
contador.

### 7.3 Estratégia e roteiro

- **Âncora:** a faixa que o candidato vai pedir, com o piso acima do mínimo
  real.
- **Roteiro de contraproposta** no idioma da empresa: agradecer, mostrar
  interesse, ancorar no valor (escopo, experiência), pedir o ajuste, propor
  alternativas (bônus de assinatura, revisão em 6 meses, equipamento,
  dias de folga).
- **O que não dizer:** salário atual exato (quando não for obrigatório),
  aceitar na hora, ultimato sem alternativa.

### 7.4 Alertas no contrato

Checklist: cláusula de não concorrência e exclusividade, propriedade
intelectual de projetos pessoais, multa por rescisão, período de experiência,
aviso prévio, dia e moeda do pagamento, quem paga as taxas de câmbio, fuso e
horas exigidas, o que acontece quando o projeto ou cliente termina.

## Output

- `outputs/<vaga>/08-offer.md`
- No chat: a faixa recomendada, a comparação resumida e o **roteiro de
  contraproposta completo** (é resposta para falar ou escrever, então vai
  inteiro).
