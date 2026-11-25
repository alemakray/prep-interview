# Etapa 0: Onboarding do perfil (roda uma vez)

## Objetivo

Montar o perfil do candidato **antes da primeira vaga**, com tudo o que não
muda de uma vaga para outra. Assim cada vaga nova só pergunta o que for
específico dela (ex.: uma tecnologia que nunca apareceu antes).

## Quando roda

- Automaticamente, se `profile/candidate-profile.json` não existir.
- Quando o candidato pedir ("atualizar perfil", "etapa 0") ou trocar de CV.

## Procedimento

### 0.1 Extrair o que o CV já responde

Crie `profile/cv.md` (cache do CV; ver `AGENT.md`) e preencha, sem perguntar:
nível, voz, formação, certificações, idiomas e, em `tools`, todas as
tecnologias do CV como `production`.

### 0.2 Questionário único

Mande **uma mensagem só**, em blocos curtos e numerados, para o candidato
responder de uma vez. Pule o que o CV já respondeu com clareza.

1. **Logística:** cidade/país e fuso; autorização de trabalho e visto; modelos
   de contrato aceitos (CLT, PJ, contractor, EOR); aviso prévio; horário com
   restrição.
2. **Remuneração:** atual (opcional), mínimo aceitável, faixa-alvo e moeda.
3. **Formação e certificações:** concluída ou não; certificações válidas até
   quando.
4. **Trajetória:** motivo de saída de cada empresa do CV (1 linha cada, como o
   candidato quer contar).
5. **Inventário de ferramentas adjacentes:** liste de 15 a 25 tecnologias
   comuns na área do candidato que **não** estão no CV (ex.: para DevOps:
   GitHub Actions, GitLab CI, Jenkins, Bicep, Pulumi, Ansible, AWS, GCP,
   Helm, Vault…). O candidato marca cada uma com uma letra:
   `P` produção · `E` projeto pessoal ou estudo · `N` nunca usei.
6. **Objetivo:** tipos de vaga que busca, níveis, setores que prefere ou evita.
7. **Inglês:** nível autodeclarado e situações em que usa (reuniões,
   documentação, clientes).

### 0.3 Banco de histórias STAR

A partir do CV, proponha de 6 a 8 histórias candidatas (título + uma linha).
Peça que o candidato confirme e complete cada uma em poucas frases: contexto,
o que ele fez e o que mudou depois (número só se for real). Salve em
`profile/star-stories.md`.

Se o candidato quiser pular agora, monte o banco depois, na primeira vez que
for necessário (etapa 4 ou 7).

### 0.4 Fechamento

Mostre no chat um resumo do perfil em até ~10 linhas e o que ficou em aberto.

## Regras

- O perfil não tem telefone, e-mail nem endereço.
- Tudo que for respondido aqui **não é perguntado de novo** nas vagas.
- Nas etapas das vagas, pergunte só sobre tecnologias ou fatos que **não estão
  no perfil**, e acrescente as respostas ao perfil (o inventário cresce a cada
  vaga).

## Output

- `profile/candidate-profile.json`
- `profile/cv.md`
- `profile/star-stories.md`
