# INSTALAR E RODAR — Personas Sintéticas no Claude Code

Da máquina limpa até a v0 completa do livro. Depois você traz `ENTREGA/` de volta para lapidar em Opus e Fable.

---

## PARTE 1 — O que vai no pacote, item por item

### Vai, e é obrigatório

| Arquivo | Papel na máquina de escrita |
|---|---|
| `CLAUDE.md` | lido automaticamente em toda sessão. Hierarquia de autoridade, as dez regras mais violadas, esqueleto de página, convenção `[LAPIDAR]`, fluxo da sessão |
| `docs/GABARITO_MASTER_v3.md` | **o mais importante.** É o esqueleto do livro inteiro, com 99 marcas `⟦ ⟧` dizendo o que vai em cada posição de cada capítulo, os 7 prompts já rascunhados, as caixas SUA VEZ, as faixas de progresso, e o Prefácio e o Capítulo 1 já parcialmente escritos. O Claude Code **preenche** este arquivo, não inventa estrutura |
| `docs/ARSENAL_VERIFICADO_v2_3.md` | a única fonte autorizada de caso, número e citação |
| `docs/FICHA_DE_VOZ_RAFAEL_GODOY_v1.md` | o envelope medido da prosa do livro 1 |
| `docs/ESTRUTURA_7_CAPITULOS.md` | os 7 capítulos, o mapa de figuras, o Apêndice |
| `docs/ESTRUTURA_ADENDO_v1_3_SUBTITULO_E_STORYTELLING.md` | a espinha narrativa. É o que impede os capítulos de virarem sete manuais soltos |
| `docs/MANIFESTO_E_PLANO_v3.md` | posicionamento e promessa — o que o livro se comprometeu a entregar |
| `docs/FRONTEIRA_LIVRO_3.md` | o que **não** é escopo. Impede a invasão do livro de métricas |
| `docs/SUBTITULOS_LINHA_v1.md` | consistência de série: subtítulo, gramática de capa, convenções da linha |
| `docs/PRONTIDAO_ESCRITA_v1_3.md` | inventário do que existe e do que falta |
| `docs/ROTEIRO_v1_HISTORICO.md` | o roteiro antigo, **sanitizado**: apaguei a §C inteira (os 20 prompts Gemini) e pus aviso no topo sobre os 12 capítulos. Fica pelo detalhe de conteúdo por sessão e pelo protocolo §B |
| `docs/PLANO_PRODUCAO_v2...md` · `docs/EXECUCAO_PASSO_A_PASSO.md` | o plano vigente |
| `docs/PROMPTS_AVULSOS.md` | os textos crus, caso um slash command não dispare |
| `gates/` | `hunt_g1_marcas_v2.py`, `hunt_g2_ecos.py`, `hunt_g3_voz.py`, `whitelist_ecos_ps.txt`, `rodar_gates.sh` |
| `verificar.sh` | diz se o setup está completo e se você pode escrever |

### Vai, e você preenche antes de escrever

`docs/DECISOES_F0.md` (as 12 decisões) · `docs/CONJUNTO_ANCORA.md` (proposições, 14 mensagens-âncora, 8 legendas) · `docs/BANCO_DE_CAMPO.md` (5 a 8 observações verdadeiras suas — a única autorização de primeira pessoa do livro).

O `verificar.sh` conta os campos `[PREENCHER]` e trava enquanto houver algum.

### Skills que vão

| Skill | Por quê |
|---|---|
| `personas-sinteticas-rewriter` (v4) | canon, glossário, gates, mapa |
| `book-editor-humanizer` | o Claude Code roda sobre o próprio rascunho depois dos gates |
| `book-context-block` | mantém a memória viva entre capítulos |
| `criterios-best-seller` | 18 critérios PASS/FAIL, puramente textuais, servem de autogate |

### O que NÃO vai, e a razão de cada um

| Fora | Por quê |
|---|---|
| **os 4 PDFs de fonte** (Harvard, Persona generators, Architects Playbook, Enterprise AI Playbook) | 17 MB e, pior, risco real: com o PDF na mão o Sonnet cita direto, sem passar pela disciplina de ficha. Todo dado que interessa **já está no arsenal**, verificado. Verificação N1 de fonte primária é trabalho do Fable, na sua máquina. Se quiser levá-los assim mesmo, ponha em `fontes/` — a regra continua: nada entra no texto sem ficha |
| **`Profissional_Exponencial_v131_KINDLE.docx`** | é o livro 1 inteiro. A voz dele já está destilada na Ficha de Voz, em números. O arquivo bruto só serviria para o Sonnet imitar frases — imitação de superfície em vez de envelope |
| **`MASTER_TEMPLATE_PERSONAS.docx`** | montagem de docx é do **seu** lado. A v0 sai em Markdown. Gerar docx lá significaria trazer um binário de volta para refazer aqui. Entreguei o template separado, veja a Parte 4 |
| **`hunt_g2.py`, `hunt_g3.py`, `whitelist_ecos_PE.txt`** | versões do livro 1, substituídas |
| **`SUBTITULOS_MW_v1.md`** | é do Modern Workflows, outro livro |
| **`diretor-editorial-big-five`, skills `mesa-*`** | precisam de busca e do manuscrito fechado, e rodam em Fable. Deixar fora também impede o Sonnet de se auto-aprovar no parecer final |
| **`excalidraw-para-livro`, `arte-kdp`, `capa-best-seller`, `amostra-kindle`, `book-translator`** | pós-produção, tudo do seu lado |
| **busca na web** | desligada no `settings.json`. Fonte é o arsenal, ponto |

**Achado na conferência:** o `Personas_Sinteticas_GABARITO_MASTER_v3.docx` da pasta **não é um .docx** — é texto com a extensão trocada, e nenhum leitor de Word abre. Renomeei para `.md` no pacote. Vale renomear na origem também.

---

## PARTE 2 — Instalação, comando por comando

```bash
# 1. Node 18+ e Claude Code
node --version
npm install -g @anthropic-ai/claude-code

# 2. o bundle
unzip personas-sinteticas-claude-code.zip
cd personas-sinteticas

# 3. Python
python3 --version                       # >= 3.10
pip install anthropic matplotlib pandas

# 4. chave de API — NÃO é a assinatura do Claude Code.
#    É uma chave de console.anthropic.com. Quem usa é o Laboratório, para rodar as personas.
export ANTHROPIC_API_KEY="sk-ant-..."         # macOS/Linux
# setx ANTHROPIC_API_KEY "sk-ant-..."         # Windows, e reabra o terminal

# 5. versionamento — 12 capítulos sem git é pedir para perder trabalho
git init && git add -A && git commit -m "bundle inicial"

# 6. conferir
bash verificar.sh
```

Ele vai dizer **AINDA NÃO**, e está certo: faltam as três decisões humanas e o corpus. É a trava funcionando.

```bash
# 7. abrir
claude
```

Dentro do Claude Code:

```
/model                # escolha o Sonnet disponível na sua conta
/permissions          # confirme: docs/ e gates/ negados para escrita
```

**Teste de fumaça, antes de qualquer coisa.** Em conversa nova:

```
Leia CLAUDE.md, docs/GABARITO_MASTER_v3.md e a skill personas-sinteticas-rewriter.
Depois responda em cinco linhas: quantos capítulos tem o livro, qual é o produto,
o que significa a marca ⟦ F2 ⟧ no gabarito, de onde vem um número que você cite,
e qual travessão você usa.
```

Certo: 7 capítulos + Apêndice · o Simulador · caixa de saída com transcrição real do corpus · só do arsenal · `–` com espaços.
Se responder "12 capítulos", a skill não carregou: confira que a pasta `.claude/` veio junto e reabra.

---

## PARTE 3 — As sessões, em ordem exata

Uma conversa por sessão. `/clear` entre elas. Nunca continue um capítulo em conversa já usada — o contexto acumulado puxa a voz para a média do que já foi escrito.

### Sessão 0 — você, sem modelo
Preencher `DECISOES_F0.md`, `CONJUNTO_ANCORA.md`, `BANCO_DE_CAMPO.md`. As duas primeiras nascem melhor em Opus, na outra máquina; aqui é colar. O Banco de Campo tem que sair da sua boca.
Rode `bash verificar.sh` até sobrar só o corpus como pendência.

### Sessão 1 — o Laboratório
```
/lab
```
Sete blocos, roda contra a API, arquiva `corpus/`: transcrições `.md` e sete PNGs a 300 dpi.
Verificação: `ls corpus/` tem ao menos um arquivo por capítulo e existe `corpus/INDICE.md`.
**Sem isso, não escreva capítulo.** Toda caixa de SAÍDA do livro sai daqui.

### Sessões 2 a 8 — os sete prompts
```
/prompt 1     …     /prompt 7
```
Cada um melhora o rascunho do gabarito, roda em três perfis (técnico, PM, não-técnico), arquiva as saídas e testa autocontenção. Prompt que só funciona para o técnico reprova — metade do público não codifica.
Saída: `docs/PROMPTS_FINAIS.md` e mais corpus.

### Sessões 9 a 30 — a escrita
Onze pares, sempre nesta ordem, sempre em conversas separadas:

```
/pacote E1        → confira STATUS: COMPLETO   → /clear
/escrever E1      → gates passam                → /clear
/auditar manuscrito/E1_prefacio.md              → /clear
```

| Par | Sessão | Sai |
|---|---|---|
| 1 | E1 | Prefácio + Antes de começar |
| 2 | E2 | Introdução |
| 3 | E3 | Cap 1 — O teste que passa em tudo |
| 4 | E4 | Cap 2 — Os cinco jeitos de quebrar |
| 5 | E5 | Cap 3 — A persona que não desmonta |
| 6 | E6 | Cap 4 — O painel que discorda |
| 7 | E7 | Cap 5 — As três perguntas |
| 8 | E8 | Cap 6 — Da falha ao conserto |
| 9 | E9 | Cap 7 — O Simulador |
| 10 | E10 | Apêndice — O Laboratório |
| 11 | E11 | O que o método não entrega + Notas + Sobre o Autor + Agradecimentos |

Depois de cada `/escrever`, três conferências antes de seguir: o relatório diz `TODOS OS GATES PASSARAM`; as marcas `[LAPIDAR]` são menos de 8; a auditoria não listou mais de três parágrafos genéricos. Falhou alguma, volte um passo em vez de acumular dívida.

Commit a cada capítulo aprovado: `git add -A && git commit -m "E3 cap1 v0"`.

### Sessão 31 — costura
```
/costura
```
Junta tudo, confere pontes, ordem das métricas, faixas, nomes das Capacidades, e checa a **amplitude entre capítulos** — capítulos parecidos demais reprovam mesmo tendo passado isoladamente.

### Sessão 32 — entrega
```
/entrega
```
Monta `ENTREGA/`. É essa pasta que volta.

**Total: ~32 sessões de Sonnet.** Duas ou três por dia, no máximo. Aprovar capítulo cansado contamina o Context Block, que contamina o próximo.

---

## PARTE 4 — A volta, e o que fazer aqui

| O que volta | Tratamento | Modelo |
|---|---|---|
| `ENTREGA/LIVRO_COMPLETO.md` | lapidação capítulo a capítulo | **Opus 5** |
| `RELATORIO_DE_LAPIDACAO.md` | resolve cada `[LAPIDAR]`, na ordem | **Opus 5** |
| itens `[FALTA FICHA]` | busca e verificação em fonte primária | **Fable 5** |
| Capítulo 1 | **reescrever inteiro** com a v0 como esqueleto — é o capítulo cujo tom todos os outros herdam | **Fable 5** |
| `FICHAS_DE_FIGURA.md` | vira a cena do Excalidraw, 26 frames em lote | **Sonnet 5** |
| `METRICAS.md` | mostra onde a v0 raspou o limite da faixa | leitura |
| montagem | `MASTER_TEMPLATE_PERSONAS.docx` + manuscrito lapidado | **Sonnet 5** |

Sobre o template entregue à parte: saiu do v131 preservando os 46 estilos, os headings e **as três caixas** — a escura `#1e1e1e` do prompt, a verde e a azul. Falta uma coisa, de propósito: **a paleta ainda é a do livro 1**. Trocar verde e azul pelo petróleo `#0F4C5C` é a primeira tarefa da montagem, e é edição de duas cores no `document.xml`, não regeneração.

---

## PARTE 5 — O que o pacote previne, e como detectar se falhou

| Erro | O que previne | Sinal de que passou |
|---|---|---|
| escrever 12 capítulos | `CLAUDE.md` + skill v4 + gabarito | "Parte 1/2/3" no manuscrito |
| inventar estrutura de página | gabarito com as 99 marcas | seção que não existe no gabarito |
| inventar caso ou número | arsenal somente leitura + web desligada | empresa fora do arsenal |
| caixa de prompt sem saída | regra 2 | `[FALTA SAÍDA]` no relatório |
| travessão `—` | G3 | "travessão curto" < 0,70 |
| conectivo abrindo frase | G3 | "aberturas conectivas" > 1,2% |
| "nós", "a gente" | G1 BLOQUEIO | bloqueio de 1ª pessoa do plural |
| prosa chapada | G3 burstiness | < 0,58 |
| capítulos iguais entre si | `/costura` | amplitude da frase média < 2,5 palavras |
| pergunta retórica no fecho | G1 | bloqueio "fechamento em pergunta retórica" |
| legenda descritiva | fichas de figura | legenda que começa com "As", "Os", "O diagrama" |
| invadir o Livro 3 | `FRONTEIRA_LIVRO_3.md` + `/auditar` | item 5 da auditoria |
| encher linguiça no buraco | convenção `[LAPIDAR]` | capítulo **sem marca nenhuma** |

O último merece atenção. Se um capítulo voltar sem nenhum `[LAPIDAR]` e nenhum `[FALTA]`, desconfie em vez de comemorar. V0 honesta de livro técnico tem lacuna. Zero lacuna quase sempre significa buraco tapado com prosa vaga — o defeito mais caro de consertar depois, porque parece pronto.
