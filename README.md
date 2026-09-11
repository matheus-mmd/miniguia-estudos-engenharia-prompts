# 📘 Miniguia de Estudos: Engenharia de Prompts para IA Generativa

> Projeto do desafio **"Treinando uma IA de Aprendizagem: Explore o Poder do NotebookLM"** — Digital Innovation One (DIO)

Este repositório documenta a construção de um **Caderno Temático no NotebookLM** sobre Engenharia de Prompts, incluindo a curadoria de fontes, o processo de testes de prompts (com acertos, erros e "cicatrizes") e a entrega final: um miniguia de estudo pronto para revisões futuras.

---

## 🎯 Contexto e Objetivos

**Assunto escolhido:** Engenharia de Prompts (*Prompt Engineering*) aplicada a modelos de IA generativa (LLMs) — como Claude, GPT e Gemini.

**Por que esse tema?** Prompt Engineering é a habilidade mais transferível do momento para quem trabalha com IA no dia a dia: dev, estudante ou profissional de qualquer área. Entender os princípios por trás de um bom prompt evita respostas genéricas, reduz retrabalho e é a base para tarefas mais avançadas, como automações e agentes de IA.

**Objetivos de estudo com este material:**

1. Entender os fundamentos da engenharia de prompts (clareza, contexto, formato de saída, exemplos).
2. Comparar as boas práticas recomendadas por diferentes fornecedores de IA (Anthropic, OpenAI e Google) e identificar pontos em comum.
3. Praticar técnicas específicas — *few-shot prompting*, *chain-of-thought*, *role prompting*, uso de tags estruturais — testando-as num caso real dentro do NotebookLM.
4. Documentar o raciocínio por trás dos resultados obtidos (não só a resposta final, mas o caminho até ela).
5. Consolidar tudo em um miniguia de consulta rápida, com glossário e prompts reutilizáveis, para revisão futura.

---

## 📚 Curadoria de Fontes

Fontes abertas (texto e PDF) selecionadas e carregadas no NotebookLM para formar a base do caderno temático:

| # | Fonte | Autor / Organização | Formato | Por que foi escolhida |
|---|-------|----------------------|---------|------------------------|
| 1 | [Prompt engineering overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) | Anthropic (documentação oficial do Claude) | Página web / texto | Referência oficial com técnicas testadas (clareza, exemplos, tags XML, "pensar antes de responder"). |
| 2 | [prompt-eng-interactive-tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial) | Anthropic (GitHub) | Texto / notebooks | Tutorial interativo e gratuito, aprofunda cada técnica com exercícios práticos. |
| 3 | [Prompt engineering — OpenAI API Guides](https://developers.openai.com/api/docs/guides/prompt-engineering) | OpenAI | Página web / texto | Traz a perspectiva de outro fornecedor, útil para comparar convenções (ex: uso de delimitadores, decomposição de tarefas). |
| 4 | [Prompt Engineering (Whitepaper)](https://www.kaggle.com/whitepaper-prompt-engineering) — Lee Boonstra | Google | PDF | Whitepaper técnico e denso, ótimo para o NotebookLM extrair definições formais e parâmetros de configuração (temperature, top-k, top-p). |
| 5 | [Prompt Engineering Guide](https://www.promptingguide.ai/) | DAIR.AI (comunidade open source) | Página web / texto | Guia comunitário abrangente, com técnicas avançadas (ReAct, Tree of Thought) e exemplos comparativos entre modelos. |

> 💡 Dica de quem já passou por isso: dar preferência a 1 ou 2 fontes **densas** (o whitepaper em PDF) e 3 ou 4 fontes **mais diretas** (páginas de documentação) ajuda o NotebookLM a equilibrar profundidade técnica com respostas objetivas nas citações.

---

## 🧪 Engenharia de Prompts e "Cicatrizes"

Aqui está o registro honesto do processo: as perguntas estratégicas feitas ao caderno no NotebookLM, como elas foram evoluindo, e as dificuldades reais de extrair boas respostas.

### Rodada 1 — Pergunta ampla demais

**Prompt inicial:**
> "Me explica engenharia de prompts."

**Resultado:** resposta correta, porém genérica — misturou conceitos de níveis diferentes (do básico ao avançado) sem hierarquia, e citou as 5 fontes de forma solta, sem comparar entre si.

**Cicatriz / aprendizado:** perguntas amplas demais fazem o NotebookLM "resumir tudo de uma vez", perdendo profundidade. Prompts precisam de **escopo definido** (uma técnica, uma comparação, um caso de uso por vez).

---

### Rodada 2 — Adicionando estrutura e formato de saída

**Prompt refinado:**
> "Com base nas fontes, liste as 5 técnicas de prompt engineering mais recomendadas. Para cada uma: (1) nome, (2) quando usar, (3) um exemplo de prompt. Formate como tabela."

**Resultado:** muito melhor. O NotebookLM organizou clareza de instrução, few-shot prompting, chain-of-thought, role prompting e uso de delimitadores/tags, cada um com uma citação de origem clicável.

**Cicatriz / aprendizado:** pedir **formato de saída explícito** (tabela, lista numerada, JSON) reduz drasticamente a resposta "em bloco de texto corrido" e facilita comparar fontes diferentes lado a lado.

---

### Rodada 3 — Comparando fornecedores (ponto de fricção real)

**Prompt:**
> "As fontes da Anthropic, OpenAI e Google concordam sobre o uso de exemplos (few-shot)? Aponte semelhanças e diferenças, citando a fonte de cada afirmação."

**Resultado:** aqui apareceu a primeira dificuldade real — o NotebookLM tendeu a **justapor** trechos de cada fonte em vez de de fato contrastá-los. Foi preciso reforçar o prompt.

**Prompt ajustado (2ª tentativa):**
> "Faça uma tabela comparativa com colunas: Fornecedor | O que recomenda sobre few-shot | Diferença em relação aos outros dois. Se não houver diferença explícita numa fonte, escreva 'não abordado' em vez de inferir."

**Cicatriz / aprendizado:** para tarefas de **comparação**, é melhor prompt explicitamente pedir uma tabela com colunas nomeadas e instruir o modelo a admitir quando uma fonte "não aborda" o ponto — isso evita que ele invente semelhanças que não estão nos documentos (alucinação por analogia).

---

### Rodada 4 — Testando "role prompting" dentro do próprio caderno

**Prompt:**
> "Assuma o papel de um revisor técnico cético. Aponte 3 possíveis limitações ou riscos de aplicar engenharia de prompts sem testes automatizados, com base nas fontes."

**Resultado:** resposta mais crítica e menos "promocional" — trouxe pontos como dependência de versão do modelo, custo de iteração manual e risco de prompts que funcionam bem só em exemplos testados (overfitting ao caso de teste).

**Cicatriz / aprendizado:** atribuir um **papel/persona** ao pedido muda o tom e a profundidade crítica da resposta, mesmo usando exatamente as mesmas fontes — uma técnica poderosa para gerar contrapontos.

---

### Rodada 5 — Prompt para gerar o glossário final

**Prompt:**
> "Extraia das fontes um glossário com os 8 a 10 termos técnicos mais citados sobre engenharia de prompts. Defina cada termo em até 2 linhas, em português, com linguagem simples."

**Resultado:** primeira tentativa trouxe termos em inglês sem tradução. Foi necessário reforçar "em português" e "linguagem simples" explicitamente — sem isso, o NotebookLM tende a manter a terminologia original das fontes (que estão em inglês).

**Cicatriz / aprendizado:** **idioma e nível de linguagem não são assumidos automaticamente** — mesmo com fontes em inglês, é preciso declarar no prompt o idioma e o público-alvo da resposta.

### 🔧 Dificuldades gerais de troubleshooting no NotebookLM

- **Citações genéricas demais:** em perguntas muito abertas, as citações às vezes apontavam para o documento inteiro em vez do trecho específico — resolvido pedindo respostas mais segmentadas.
- **Limite de fontes por pergunta:** ao perguntar sobre "todas as fontes" de uma vez, a resposta ficava rasa; funcionou melhor perguntar por 2–3 fontes específicas por vez e depois pedir uma síntese final.
- **Tendência a concordar demais:** por padrão o modelo tende a harmonizar as fontes; pedir explicitamente por divergências e contradições trouxe respostas mais ricas.

---

## 📖 Miniguia de Estudo (Entrega Final)

### 🧩 Resumos Estruturados

**1. O que é engenharia de prompts**
É o processo de projetar e refinar instruções (prompts) para obter respostas melhores, mais confiáveis e mais úteis de um modelo de IA generativa. Não é "adivinhação" — é um processo iterativo e testável, assim como debugar código.

**2. Princípios fundamentais (consenso entre Anthropic, OpenAI e Google)**

- **Seja claro e específico:** diga exatamente o que quer, incluindo contexto, formato de saída e restrições. Instruções vagas geram respostas vagas.
- **Dê exemplos (few-shot prompting):** mostrar 1 a 3 exemplos do padrão de resposta esperado melhora consistência muito mais do que apenas descrever a regra.
- **Divida tarefas complexas:** em vez de um único prompt gigante, quebre em etapas menores e encadeadas (prompt chaining).
- **Permita que o modelo "pense":** técnicas como *chain-of-thought* ("pense passo a passo antes de responder") melhoram tarefas de raciocínio e reduzem erros.
- **Use estrutura no texto:** delimitadores, tags (como `<contexto>`, `<pergunta>`) ou Markdown ajudam o modelo a separar instrução de conteúdo e a formatar a resposta corretamente.
- **Atribua papéis (role prompting):** pedir que o modelo assuma uma persona (ex: "revisor técnico cético") muda o tom, o nível de detalhe e o senso crítico da resposta.
- **Itere como em um experimento:** o primeiro prompt raramente é o melhor — testar variações e comparar resultados é parte do processo, não uma falha.

**3. Parâmetros técnicos que também influenciam a resposta**
Além do texto do prompt, parâmetros de configuração do modelo (quando disponíveis) afetam o resultado: *temperature* (mais alta = respostas mais criativas/variadas; mais baixa = mais determinísticas e focadas), além de *top-k* e *top-p*, que controlam a diversidade de palavras candidatas em cada etapa da geração.

**4. Erros comuns (as "cicatrizes" generalizadas)**
Prompts amplos demais geram respostas rasas; pedir comparações sem estrutura gera justaposição em vez de análise; não especificar idioma/tom/formato faz o modelo assumir o padrão da fonte, não o da pergunta.

---

### 📔 Glossário

| Termo | Definição rápida |
|---|---|
| **Prompt** | A instrução (texto) enviada a um modelo de IA para obter uma resposta. |
| **Prompt Engineering** | Prática de projetar e refinar prompts de forma sistemática para melhorar a qualidade das respostas. |
| **Few-shot Prompting** | Técnica de incluir exemplos de entrada/saída no próprio prompt para guiar o padrão de resposta. |
| **Zero-shot Prompting** | Pedir uma tarefa sem fornecer exemplos prévios, contando apenas com a instrução. |
| **Chain-of-Thought (CoT)** | Técnica que incentiva o modelo a "raciocinar em etapas" antes de dar a resposta final, melhorando tarefas lógicas/matemáticas. |
| **Role Prompting** | Atribuir uma persona ou papel ao modelo (ex: "aja como um professor") para moldar tom e profundidade da resposta. |
| **System Prompt** | Instrução de alto nível, geralmente definida antes da conversa, que estabelece regras gerais de comportamento do modelo. |
| **Temperature** | Parâmetro que controla a aleatoriedade/criatividade das respostas geradas. |
| **Alucinação (Hallucination)** | Quando o modelo gera uma informação que parece plausível mas não é factual nem está nas fontes fornecidas. |
| **Prompt Chaining** | Encadear vários prompts menores, usando a saída de um como entrada do próximo, para resolver tarefas complexas. |

---

### 🔁 Prompts Reutilizáveis (para revisões futuras)

Um pequeno kit de prompts testados e prontos para reaproveitar — no NotebookLM ou em qualquer LLM:

```text
# 1. Para gerar uma visão geral de um tema com base em fontes
Com base nas fontes fornecidas, resuma [TEMA] em até 5 pontos principais.
Formate como lista numerada e cite a fonte de cada ponto.

# 2. Para comparar fornecedores/abordagens diferentes
Faça uma tabela comparativa sobre [TEMA] com colunas: Fonte | Posição/Recomendação | Diferença em relação às demais.
Se uma fonte não abordar o ponto, escreva "não abordado" em vez de inferir.

# 3. Para gerar um glossário de revisão
Extraia das fontes os principais termos técnicos sobre [TEMA].
Defina cada um em até 2 linhas, em português, com linguagem simples, em formato de tabela.

# 4. Para obter uma crítica / contraponto
Assuma o papel de um revisor técnico cético sobre [TEMA].
Aponte 3 limitações, riscos ou pontos em aberto, com base apenas nas fontes fornecidas.

# 5. Para transformar o aprendizado em um plano de estudo
Com base no que foi discutido sobre [TEMA], monte um plano de revisão de 3 etapas,
cada uma com um objetivo de aprendizado e uma pergunta de autoavaliação.
```

---

## 🛠️ Como este projeto foi construído

1. Escolha do tema (Engenharia de Prompts) e definição dos objetivos de estudo.
2. Curadoria de 5 fontes abertas (documentação oficial + whitepaper + guia open source) e upload no NotebookLM.
3. Elaboração de perguntas estratégicas ao caderno, em rodadas, refinando o prompt a cada dificuldade encontrada (documentado na seção *Engenharia de Prompts e Cicatrizes*).
4. Consolidação das respostas validadas em um miniguia de estudo: resumos, glossário e prompts reutilizáveis.
5. Organização de tudo neste `README.md`, publicado no GitHub como parte do portfólio.

---

## ✅ Checklist do desafio

- [x] Contexto e objetivos de estudo definidos
- [x] Curadoria de 3 a 5 fontes abertas (texto/PDF)
- [x] Perguntas estratégicas e variações de prompts documentadas
- [x] Respostas, referências e dificuldades (cicatrizes) registradas
- [x] Miniguia final: resumos + glossário + prompts reutilizáveis

---

*Projeto desenvolvido como parte do desafio de projeto da [Digital Innovation One (DIO)](https://www.dio.me/) — trilha de Inteligência Artificial.*
