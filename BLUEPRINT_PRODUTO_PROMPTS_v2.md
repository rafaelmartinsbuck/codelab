# Blueprint v2 — Prompts do Profissional Exponencial (formato simplificado)
**Para o Sonnet escrever cada prompt.** Substitui a v1 (Caderno/Agente Consultor com fichas e arquivos). Esta versão é mais simples, mais didática e foi desenhada para caber numa página Kindle por capítulo.

---

## PARTE 0 — A virada de chave (leia antes de escrever qualquer prompt)

**Uma thread só.** Os 7 prompts são colados em sequência, NA MESMA conversa. A IA lê o que está acima sozinha — não existe arquivo para carregar, ficha para colar, nem "Agente Consultor" como objeto separado. O encadeamento é invisível: o output do capítulo anterior já está na tela quando o leitor cola o próximo prompt. Frases-gatilho como "com base na sua análise acima" e "com base nas notas acima" são o mecanismo de encadeamento — não precisa de nada mais.

**Modelo mental do leitor (3 palavras, repetidas em todo capítulo): Input → Prompt → Output.** No Cap 1, o input é o material do leitor (CV/LinkedIn + 3 campos). Do Cap 2 em diante, o input já é o output anterior — está na tela; o leitor só lê o prompt e cola.

**3 campos fixos, preenchidos UMA VEZ no Cap 1** (não se repetem nos demais — a IA já sabe pela conversa):
- `País: [___]`
- `Profissão: [___]`
- `Onde quero chegar: [___]` (a ambição — promoção, cliente maior, transição; carrega a senioridade junto)

**Por que isso é incopiável (a fonte do valor de R$150):** o prompt sozinho, sem a conversa acumulada e sem os 3 campos preenchidos com a vida real do leitor, é um esqueleto vazio. O valor está na CONVERSA, não no texto do prompt. Cada leitor gera uma cadeia diferente porque os dados são dele. Um consultor de RH lendo o prompt isolado vê só uma estrutura; o que ele avalia de verdade é o que a estrutura produz quando alimentada com dados reais — e isso o livro garante.

**Cada prompt cabe numa página Kindle.** Por isso: nenhum prompt redefine o método inteiro (só o Cap 1 nomeia o Triângulo, e em uma linha); nenhum prompt tem mais que ~12-15 linhas; a moldura da página (frase de valor + o que colar + prompt + o que esperar) é fixa e enxuta.

**O gancho de aprofundamento (obrigatório em todo capítulo).** Toda resposta termina oferecendo uma continuação de UMA linha que o leitor pode colar se quiser ir mais a fundo — pesquisa de mercado com fonte real, ou um gráfico/visual mais detalhado. Não é um menu de 3 opções (isso inflava a página); é uma única frase-gancho, ex.: *"Quer que eu busque dados reais do seu mercado para validar isso? Só dizer 'sim, pesquise'."* Isso mantém o capítulo enxuto mas mostra ao leitor que pode extrair mais.

**Boas práticas de prompt engineering aplicadas em todos:**
- Papel definido na primeira linha (quem a IA é nesta interação).
- Instrução positiva, não negativa (diga o que fazer, não o que evitar, salvo quando crítico).
- Formato de saída explícito e curto (o leitor sabe exatamente o que vai receber).
- Pedido de raciocínio leve antes da resposta final, quando a tarefa exige diagnóstico (ex.: "primeiro identifique X, depois Y").
- Sem jargão técnico de IA voltado ao leitor (ele não precisa saber o que é "prompt engineering" para usar isto).

---

## PARTE 1 — O esqueleto de página (todo capítulo segue isto)

```
CAPÍTULO N — [nome em até 4 palavras]
[1 linha do que este capítulo faz por você — o valor, não o mecanismo]

O QUE COLAR JUNTO (só se houver dado novo deste capítulo — senão, omitir esta linha):
[ex.: "o link de 1 a 3 vagas do cargo que você quer"]

┌─ PROMPT ──────────────────────────────────────────────┐
│ [papel em 1 linha]                                     │
│ [gatilho de encadeamento: "Com base [...] acima"]      │
│ [PARÂMETROS DO LEITOR — sempre no topo, logo após       │
│  papel/gatilho, NUNCA no meio ou no fim:                │
│  só no Cap 1, os 3 campos; nos demais, o dado novo      │
│  deste capítulo, se houver]                             │
│ [a tarefa, 2-4 linhas — inclui 1 passo de raciocínio    │
│  curto antes de concluir: "primeiro releia X, depois Y"]│
│ [formato de saída, 2-3 linhas]                          │
│ [o gancho de aprofundamento, 1 linha]                   │
└──────────────────────────────────────────────────────┘

DE VOLTA: [1 linha do que o leitor recebe]
```

**Regra de ordem (inegociável):** todo parâmetro que o leitor preenche ou cola — os 3 campos do Cap 1, a vaga do Cap 3, a conversa difícil do Cap 5, as horas do Cap 6 — fica sempre **no topo do prompt**, imediatamente após o papel e o gatilho de encadeamento, nunca no meio ou no fim. É a primeira coisa que o leitor vê e preenche; só depois vem a instrução de tarefa que usa esse parâmetro. Isso evita o leitor ler a tarefa inteira e só depois descobrir que precisa colar algo.

**Regra de raciocínio (boa prática de prompt):** toda tarefa que envolve diagnóstico ou comparação pede um passo de leitura/análise antes da conclusão (ex.: "primeiro releia os fatos que te dei, depois conclua"; "primeiro extraia o que a vaga exige, só depois compare"). Isso evita resposta superficial e é o que um avaliador de RH chamaria de groundedness — toda conclusão ancorada em evidência relida, não em impressão.

Meta de tamanho: prompt entre 8 e 14 linhas. Página inteira (com moldura) cabe em ~250-300 palavras — uma página Kindle confortável.

---

## PARTE 2 — Briefing por capítulo (o que o Sonnet recebe para preencher o esqueleto)

### CAPÍTULO 1 — Sua força e seu freio
- **Único capítulo com setup embutido.** O leitor cola currículo (arquivo) ou link do LinkedIn, e preenche os 3 campos (País, Profissão, Onde quero chegar) — uma vez, aqui.
- **Método nomeado em 1 linha:** os três lados de uma carreira — Técnico (o que faz bem), Negócio (o quanto liga isso a resultado), Pessoas (como se relaciona e influencia) — e, quando algo falta, se é porque não desenvolveu, não mostrou, ou tem um medo te travando.
- **Tarefa:** primeiro releia o currículo/LinkedIn (ou a situação dada) e identifique fatos concretos nos três lados; só então diagnostique a força (1 frase utilizável) + o lado mais fraco hoje + a causa (desenvolver/comunicar/superar) + 1 passo concreto para a semana, amarrado a uma situação real de trabalho.
- **Formato de saída:** (1) sua força nomeada como frase pronta para usar; (2) o lado fraco + a causa; (3) o passo da semana.
- **Evidência exigida:** a IA extrai do CV/LinkedIn fatos reais — não elogio genérico. Se faltar dado, pede 1 situação concreta (o que fez, para quem, o que não aconteceu depois). Se o leitor só conseguir dar 1 exemplo, a IA entrega o diagnóstico mas avisa que é uma primeira leitura (vai ficar mais forte com mais exemplos) — nunca apresenta 1 exemplo só como conclusão fechada.
- **Gancho:** oferecer pesquisar 1 dado de mercado real sobre a força do leitor (com fonte) se ele quiser.
- **Alimenta:** Cap 2 (a força e o lado fraco entram como ponto de partida da medição).

### CAPÍTULO 2 — Sua nota de verdade
- **Sem dado novo a colar** — usa a conversa acima.
- **Método:** medir com pergunta, não com achismo — 1-2 perguntas comportamentais por lado, e dar nota 0-10 a cada um, com gráfico.
- **Tarefa:** a IA faz 1-2 perguntas curtas por lado (Técnico/Negócio/Pessoas) baseadas no que já sabe do Cap 1; o leitor responde; a IA primeiro relê a resposta de cada lado, identifica o que ela realmente comprova, e só então dá a nota e desenha o gráfico dos três lados.
- **Formato de saída:** nota justificada por lado (declarando se é hipótese — poucas evidências — ou conclusão — evidência sólida) + gráfico (radar) plotado pela própria IA.
- **Evidência exigida:** nota ancorada na resposta real do leitor à pergunta, não em impressão.
- **Gancho:** oferecer comparar essa nota com a média do mercado na profissão dele (pesquisa).
- **Alimenta:** Cap 3 (as notas viram a base de comparação com o cargo-alvo).

### CAPÍTULO 3 — A distância até onde você quer chegar
- **O que colar (PARÂMETRO NO TOPO DO PROMPT, antes da tarefa):** o link de 1 a 3 vagas do cargo-alvo; OU descrever o cargo em 1 frase; OU, se não tiver nem isso (ambição ainda vaga, ex.: "quero crescer, talvez liderar"), a IA usa essa pista para BUSCAR 2-3 vagas reais do tipo de cargo mais provável antes de comparar — nunca inventa um cargo padrão da própria cabeça.
- **Método:** comparar o que o cargo pede com as notas do Cap 2 e nomear a diferença lado a lado.
- **Tarefa:** primeiro releia a(s) vaga(s) e extraia, fato por fato, o que ela exige nos três lados; só então compare com as notas do leitor e liste o que falta — do maior gap para o menor, marcando UMA causa por item (desenvolver, ou comunicar, ou superar; se houver duas plausíveis, escolher a que, resolvida, desbloqueia a outra).
- **Formato de saída:** os dois Triângulos lado a lado (atual vs. exigido) + a lista do que falta, do maior gap para o menor.
- **Evidência exigida:** o que falta vem da vaga real colada, não de suposição sobre "o que cargos assim geralmente pedem".
- **Gancho:** oferecer pesquisar mais 2-3 vagas reais do mesmo cargo para confirmar o padrão.
- **Alimenta:** Cap 4 (o gap define o que precisa ser comunicado/posicionado).

### CAPÍTULO 4 — Como dizer o que você vale
- **Sem dado novo a colar** — usa a conversa acima; a IA pode pedir 1 número/resultado concreto se faltar.
- **Método:** traduzir tarefa em impacto (antes → depois) e gerar uma frase de apresentação calibrada para o cargo-alvo do Cap 3.
- **Tarefa:** primeiro releia 1-2 entregas reais do leitor (do CV ou da conversa) e identifique o resultado de negócio por trás de cada uma; só então reescreva como "antes → depois" e gere 1 frase de apresentação (ex.: para LinkedIn ou para falar em 30s) mirando o gap do Cap 3.
- **Formato de saída:** "antes → depois" de cada entrega + 1 frase de apresentação pronta para usar.
- **Evidência exigida:** o "depois" usa números/resultados reais do leitor sempre que existirem.
- **Gancho:** oferecer gerar uma segunda versão da frase, para outro público (ex.: gestor em vez de LinkedIn).
- **Alimenta:** Cap 5 (a frase de apresentação entra na conversa difícil).

### CAPÍTULO 5 — A conversa que falta ter
- **O que colar (PARÂMETRO NO TOPO):** 1 linha dizendo qual conversa difícil falta (com quem, sobre o quê — ex.: pedir a promoção, renegociar um preço).
- **Método:** nomear o que trava (medo, crença, ou hábito) e treinar a conversa com a IA simulando o outro lado.
- **Tarefa:** primeiro releia a alavanca do Cap 1 e identifique a ligação real com a conversa difícil informada; só então nomeie a causa do bloqueio e monte um roteiro curto (abertura, 1 ponto de impacto do Cap 4, resposta a 1 objeção provável, pedido claro); simule a conversa com a IA no papel do outro lado.
- **Formato de saída:** o nome do bloqueio + o roteiro de 4 partes + o INÍCIO da simulação (a IA faz a primeira fala do outro lado e PARA, esperando o leitor responder — não é uma resposta de mão única como os demais capítulos).
- **Evidência exigida:** o bloqueio nomeado precisa estar ligado à alavanca real do Cap 1, não genérico ("medo de falar em público" solto).
- **Gancho:** oferecer uma segunda rodada de simulação com uma objeção mais difícil.
- **Alimenta:** Cap 6 (a conversa se torna um marco do plano).

### CAPÍTULO 6 — Os próximos 90 dias
- **O que colar (PARÂMETRO NO TOPO):** quantas horas por semana o leitor tem disponíveis (1 número).
- **Método:** transformar o gap do Cap 3 + a conversa do Cap 5 num plano de 90 dias com 3 marcos (a cada ~30 dias), a maior parte no próprio trabalho.
- **Tarefa:** primeiro releia os gaps do Cap 3 em ordem de prioridade; só então monte 3 marcos, cada um ligado a um gap específico, com a ação principal no trabalho real e uma forma simples de saber que funcionou; encaixe a conversa do Cap 5 como um dos marcos. Se algum marco depender de aprovação de terceiro (ex.: o gestor aceitar dar mais responsabilidade), sinalize isso e sugira uma alternativa que o leitor controle sozinho.
- **Formato de saída:** linha do tempo de 90 dias com os 3 marcos, plotada como visual simples.
- **Evidência exigida:** cada marco aponta de volta para um gap específico do Cap 3 — nada genérico tipo "estudar mais".
- **Gancho:** oferecer ajustar o ritmo se 90 dias for muito apertado ou muito devagar.
- **Alimenta:** Cap 7 (o plano entra no consultor final como o que ele deve cobrar).

### CAPÍTULO 7 — Leve seu consultor para a vida
- **Sem dado novo a colar.**
- **Método:** destilar a conversa inteira num único comando, na primeira pessoa, com os dados do leitor já embutidos (não com espaços em branco) — e mostrar os dois jeitos de usá-lo.
- **Tarefa:** (1) primeiro releia toda a conversa e identifique os dados-chave (país, profissão, ambição, força, gap, plano); só então comprima num comando de ativação único, na primeira pessoa, com esses dados já embutidos (não com espaços em branco); (2) incluir a regra de revisar o plano a cada 15 dias; (3) o livro acrescenta — não o prompt — o mini-guia de instalação fixa (Claude Skill / ChatGPT GPT / Gemini Gem, 2-3 passos cada).
- **Formato de saída:** o comando de ativação completo, pronto para copiar.
- **Por que não pode ser genérico:** o comando é gerado A PARTIR da conversa real do leitor — cada um recebe um comando diferente, porque os dados embutidos são os dele.
- **Nível 1 (sempre funciona):** guardar o comando numa nota e colar numa conversa nova quando quiser.
- **Nível 2 (opcional, fixo):** colar o mesmo comando no campo de instruções de uma Skill (Claude) / GPT (ChatGPT) / Gem (Gemini).

---

## PARTE 3 — Gate de aceitação (HR-1..HR-11, por aplicabilidade — mantém-se da v1)

Cada prompt é avaliado como um consultor de RH sênior avaliaria: rigor sem stuffing. Critérios sempre-CORE (nunca N/A): **HR-1** (evidência real do leitor, nunca genérico), **HR-6** (Triângulo + causa coerente), **HR-7** (comportamento desenvolvível, sem rótulo/viés), **HR-9** (esforço mínimo, cabe numa página, não-guru), **HR-10** (resistiria à pergunta de um consultor experiente: "isso vale R$150?"), **HR-11** (sem a conversa acumulada e os dados do leitor, o prompt não produz nada de valor — só estrutura vazia).

Critérios contextuais (CORE só onde a função do capítulo exige): HR-2 (dado externo — Cap 1 feedback, Cap 3 vagas reais), HR-3 (direção/opções — Cap 1 ambição, Cap 3 cargo-alvo, Cap 6 ritmo), HR-4 (ação real — Cap 1, 5, 6), HR-5 (nota calibrada — Cap 1, 2), HR-8 (marcador de sucesso — Cap 1, 4, 6).

**Teste decisivo de HR-10:** um consultor de RH com 15 anos de experiência, lendo o output (não o prompt — o resultado real, gerado com dados de um leitor de teste), assinaria embaixo como um diagnóstico que ele mesmo entregaria numa sessão paga? Se a resposta é "isso é genérico, eu não cobraria por isso", reprova.

**Teste decisivo de HR-9 (página Kindle):** o prompt, com a moldura completa (título + frase de valor + o que colar + prompt + "de volta"), cabe em uma página Kindle (~250-300 palavras) sem cortar nada essencial? Se não cabe, é sinal de que o prompt está fazendo mais do que deveria — corte, não encolha a fonte.

---

## PARTE 4 — Os 4 critérios de qualidade do prompt (checar em TODO capítulo)

Além do gate HR-1..HR-11 (Parte 3), todo prompt passa por estes 4 testes específicos de engenharia de prompt antes de ser aceito:

**1. Formação de bom prompt (papel → contexto → tarefa → raciocínio → formato → restrição).** O prompt tem papel definido na 1ª linha, usa instrução positiva, e — o ponto que mais se perde por descuido — pede um passo curto de raciocínio antes da conclusão ("primeiro releia X, depois conclua Y"). Sem esse passo, a IA tende a responder de forma superficial, e é o tipo de falha que um avaliador de RH nota de cara.

**2. Minimalista, sem enfeite ("vibing").** Zero frases decorativas tipo "aja como um especialista de classe mundial" ou apelos de autoridade vazios. Cada linha do prompt cumpre uma função (papel, parâmetro, tarefa, raciocínio, formato, ou gancho) — se uma linha não cumpre nenhuma dessas, ela sai. Teste rápido: remova a linha; se nada quebra, ela não devia estar lá.

**3. Parâmetro do leitor sempre no TOPO, nunca no meio ou no fim.** Todo dado que o leitor cola ou preenche — os 3 campos do Cap 1, a vaga do Cap 3, a conversa difícil do Cap 5, as horas do Cap 6 — vem logo após o papel/gatilho, ANTES de qualquer instrução de tarefa. O leitor preenche o que é dele primeiro; só depois lê o que a IA vai fazer com isso. Um parâmetro encontrado no meio do prompt (depois da instrução de tarefa) é erro de estrutura — corrigir movendo para o topo.

**4. Groundedness de RH (toda conclusão ancorada em evidência relida, nunca em impressão).** A IA nunca conclui sem antes citar o fato específico que sustenta a conclusão; quando a evidência é fraca, ela declara isso (hipótese, não conclusão fechada — como no Cap 1, "primeira leitura", e no Cap 2, "hipótese ou conclusão"). É o critério mais técnico e o que mais aproxima o resultado de uma avaliação profissional de RH, em vez de um teste de personalidade de internet.

---

## PARTE 4B — Auditoria honesta desta reescrita

O que a v1 errava e a v2 corrige:
1. **Carga cognitiva no leitor → carga na thread.** Antes o leitor gerenciava fichas/arquivo; agora a conversa faz isso sozinha.
2. **Múltiplos artefatos por capítulo → um prompt, uma resposta.** Sem "Agente Consultor" como objeto paralelo até o Cap 7.
3. **Setup separado (Cap 0) → embutido no Cap 1**, como pedido.
4. **Menu de 3 opções → 1 gancho de 1 linha.** Mantém o valor de "dá pra ir mais a fundo" sem inflar a página.
5. **Cap 7 vago ("cole num lugar") → dois níveis explícitos**, honestos sobre o que a IA gera (o comando) vs. o que o leitor clica (instalar na plataforma).
6. **Personalização abstrata → 3 campos concretos**, preenchidos uma vez, herdados o resto do livro pela própria conversa.

**Veredito:** a v2 é mais simples de usar e mais difícil de copiar — porque o que protege o valor não é mais a complexidade do mecanismo, é a conversa acumulada com os dados reais do leitor. Isso é mais robusto, não menos.
