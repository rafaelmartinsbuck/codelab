# CLAUDE.md — Personas Sintéticas

Você está produzindo a **v0 completa** do segundo livro do Rafael Godoy. Esta v0 vai ser lapidada depois em modelos maiores. Seu trabalho não é escrever a versão final: é entregar um manuscrito **estruturalmente correto, factualmente disciplinado e na voz certa**, com os pontos de lapidação marcados.

Leia este arquivo inteiro antes da primeira tarefa. Ele condensa correções que já custaram rodadas de retrabalho.

---

## O livro

**Título:** Personas Sintéticas
**Subtítulo (travado, nunca reescrever):** *Encontre as falhas antes dos seus usuários — e entregue sistemas de IA que escalam.*
**Produto:** o **Simulador** — painel de personas sintéticas + juiz de 3 métricas + dashboard + gate de CI/CD.
**Tese:** um agente que passa em todos os testes ainda quebra no primeiro cliente real, porque o teste usa input limpo e o cliente não. A cura é um painel de usuários sintéticos que quebra o agente antes do usuário.
**Estrutura:** **7 capítulos + Apêndice.** Qualquer referência a 12 capítulos, Parte 1/2/3 ou "Colab 08–12" é resíduo do outline morto — ignore e não reproduza.

Cadeia das 7 Capacidades, uma por capítulo, cada uma ingerindo a anterior:
conversa real → persona mínima → arquétipo → spec → painel → juiz → loop → Simulador.

## A hierarquia de autoridade — nesta ordem, sem exceção

1. **`docs/GABARITO_MASTER_v3.md`** — o esqueleto do livro inteiro, com 99 marcas `⟦ ⟧` indicando o que vai em cada posição de cada capítulo, os 7 prompts já rascunhados, as caixas SUA VEZ, as faixas de progresso e o Prefácio e o Capítulo 1 já parcialmente escritos. **Você preenche este gabarito. Você não inventa estrutura.** Se uma marca `⟦ ⟧` pede uma transcrição real do corpus e ela não existe, você escreve `[FALTA SAÍDA: ...]` — não improvisa a marca para outra coisa.
2. **`.claude/skills/personas-sinteticas-rewriter/SKILL.md`** — canon, glossário, gates, mapa dos 7 capítulos.
3. **`CLAUDE.md`** (este arquivo) — processo e as regras que mais foram violadas.
4. **`docs/ARSENAL_VERIFICADO_v2_3.md`** — a única fonte de caso, número e citação.

Conflito entre eles: gabarito manda na estrutura, skill manda no canon, este arquivo manda no processo, arsenal manda no fato. Se o conflito for real e não se resolver assim, **pare e pergunte** — não escolha sozinho.

## Como ler as marcas do gabarito

| Marca | Significa |
|---|---|
| `⟦ V<N> · vinheta ... ⟧` | vinheta de abertura. Você **não desenha**: escreve a ficha da figura (o que ela afirma, rótulos, alt-text ≤140) em `figuras/FICHAS.md` |
| `⟦ F2 · transcrição real do corpus ... ⟧` | caixa de SAÍDA. Cole a transcrição real de `corpus/`, sem editar. Sem corpus, `[FALTA SAÍDA: ...]` |
| `⟦ F4 · conceito em prosa / leitura do resultado / fechamento ⟧` | é aqui que você escreve. É a prosa do livro |
| `⟦ F6 · figura ... ⟧` | slot de figura numerada: ficha + legenda afirmativa |
| `⟦ PLOT real: ... ⟧` | gráfico do `plots.py`. Referencie o arquivo em `corpus/`, escreva a legenda |
| `· N DE 7 CAPACIDADES ·` | faixa de progresso. Mantenha literal |

---

## As dez regras que mais foram violadas — não viole nenhuma

1. **Nunca invente caso, empresa, número ou citação.** Só entra o que está em `docs/ARSENAL_VERIFICADO_v2_3.md`, letra por letra. Se você precisa de um exemplo que não está lá, escreva um cenário **declaradamente hipotético** ("Imagine um agente de cobrança que…") ou pare e escreva `[FALTA FICHA: descrição do que seria necessário]`. Inventar case é o erro mais grave possível neste projeto.
2. **Toda caixa de PROMPT ou CÓDIGO é seguida de uma caixa de SAÍDA real**, copiada de `corpus/`. Se a saída não existe em `corpus/`, você não escreve a caixa — escreve `[FALTA SAÍDA: bloco N do lab]` e segue.
3. **Travessão é `–` com espaços, nunca `—`.** No livro 1: 524 contra 105. É a marca de texto de LLM não revisado.
4. **Nunca abra frase com conectivo.** Zero *Portanto, Assim, Além disso, No entanto, Ou seja, Dessa forma, Nesse sentido, Em resumo, Por fim, Vale ressaltar, É importante destacar, Diante disso*. No livro 1 isso é 0,36% das frases. A relação entre frases se faz pela ordem delas.
5. **Nunca use "nós", "nosso" ou "a gente".** Zero ocorrências no livro 1. O narrador fala com "você" (10,8/1000). Primeira pessoa do singular só sai de `docs/BANCO_DE_CAMPO.md`, no máximo 1,8/1000.
6. **Zero exclamação. Zero reticências. Quase zero ponto e vírgula** (≤0,9/1000).
7. **Ritmo irregular por construção.** Frase média 16,4 palavras, mas 14% das frases com até 5 palavras e 30% acima de 21. Se todo parágrafo tem frases de 20 palavras, você falhou. 37% dos parágrafos do livro 1 têm uma frase só.
8. **Capítulo nunca termina em pergunta retórica.** Termina em descoberta afirmada.
9. **Nunca abra capítulo por definição.** Abre por cena concreta, com detalhe operacional que ninguém inventaria. Alternância: ímpares no modo Sinek (pergunta que reorganiza), pares no modo Clear (hábito/mecanismo observável).
10. **Duas mensagens-âncora por capítulo, exatamente duas**, em páginas diferentes, nunca dentro de caixa. Elas vêm prontas no Pacote de v0 — você não as inventa. Negrito é **proibido** em número, em nome de métrica e em nome de Capacidade.

A régua completa da voz está em `docs/FICHA_DE_VOZ_RAFAEL_GODOY_v1.md`. Leia antes de cada sessão de escrita.

---

## O que NÃO fazer, especificamente

- Não escreva "jornada", "avatar", "mindset", "usuário fake", "bot de teste", "zona de conforto", "game-changer", "revolucionário", "desbloquear potencial", "próximo nível", "virada de chave".
- Não escreva que personas sintéticas substituem teste com usuário real. O livro afirma o contrário e cita fonte.
- Não use "nomear" como moldura ("vale nomear", "é importante nomear"). Diga a coisa. Rótulo técnico com particípio ("arquétipo nomeado") é permitido **1 vez por capítulo**.
- Não escreva legenda de figura dentro do desenho, e não escreva legenda descritiva. Legenda **afirma**: "Volume não é cobertura", não "As cinco personas".
- Não gere figura. Você produz o **texto** e a **ficha da figura** (o que ela afirma, rótulos, alt-text ≤140 caracteres). O desenho é feito no Excalidraw, depois, em outra etapa.
- Não reescreva o subtítulo, o glossário, os nomes das Capacidades nem a ordem canônica das três métricas.
- Não faça meta-comentário editorial no manuscrito ("Neste capítulo veremos…", "Como vimos anteriormente…").
- Não encerre parágrafo explicando que o que você acabou de dizer é importante. Termine uma linha antes do que parece confortável.

---

## A convenção `[LAPIDAR]`

Você é a v0. A lapidação acontece depois, com modelos maiores. Em vez de forçar brilho onde você não tem material, **marque**:

```
[LAPIDAR: abertura — a cena está correta mas seca; falta o detalhe sensorial do Banco de Campo]
[LAPIDAR: transição para a seção do juiz — está costurada por conectivo, precisa de ponte narrativa]
[FALTA FICHA: número de agentes em produção em 2026]
[FALTA SAÍDA: bloco 4 do lab, heatmap pass^k]
[DECISÃO RAFAEL: nome do arquétipo 3 em português]
```

Marcar é comportamento correto e esperado. Encher linguiça para tapar buraco é o erro. Uma marca honesta economiza uma rodada; um parágrafo genérico custa duas.

Meta: **no máximo 8 marcas `[LAPIDAR]` por capítulo.** Acima disso, o Pacote de v0 estava incompleto — pare e diga.

---

## Estrutura de página (resultado-first)

Diferente do livro 1. Aqui o produto **roda**, então a prova vem antes do convite:

```
conceito curto (2-4 parágrafos, dentro da história)
CAIXA: PROMPT ou CÓDIGO
CAIXA: SAÍDA real (do corpus/)
leitura do resultado (2-3 parágrafos) — é aqui que o capítulo ensina
faixa "Sua vez" (3-4 linhas, sem destaque de caixa)
linha do Laboratório: "No Laboratório (Apêndice), este passo em código."
faixa de progresso N de 7
```

---

## Fluxo obrigatório de cada sessão de escrita

1. Ler `pacotes/PACOTE_E<N>.md`. **Se ele não existe ou está incompleto, pare e diga.** Não escreva capítulo sem pacote.
2. Ler `docs/FICHA_DE_VOZ_RAFAEL_GODOY_v1.md` e `docs/CONTEXT_BLOCK.md`.
3. Escrever em `manuscrito/E<N>_<nome>.md`, do começo ao fim, numa passada.
4. Rodar `bash gates/rodar_gates.sh manuscrito/E<N>_<nome>.md`.
5. Corrigir **só** o que o gate apontou como BLOQUEIO ou falha de envelope. Rodar de novo até passar.
6. Listar em `manuscrito/E<N>_RELATORIO.md`: o que ficou marcado `[LAPIDAR]`, o que ficou `[FALTA]`, e as métricas finais dos três gates.
7. Atualizar `docs/CONTEXT_BLOCK.md` (≤300 tokens: o que este capítulo estabeleceu, cena usada, âncoras usadas, promessa aberta para o próximo).

**Um capítulo por sessão, sempre.** Nunca continue um capítulo em sessão nova — reescreva do começo. Nunca escreva dois capítulos na mesma sessão.

---

## Gates

```bash
bash gates/rodar_gates.sh manuscrito/E03_cap1.md
```

Roda os três em sequência:
- `hunt_g1_marcas_v2.py` — padrão vetado, três baldes. **BLOQUEIO reprova.** REVISAR você lista no relatório e não corrige sozinho.
- `hunt_g2_ecos.py` — repetição verbatim entre capítulos.
- `hunt_g3_voz.py --ref` — envelope estatístico da prosa. Falha aqui é reescrita de ritmo, não corte de palavra.

**Como corrigir falha do g3 sem estragar o texto:** se a frase média está alta, o problema quase nunca é frase longa demais — é falta de frase curta. Acrescente as curtas. Se a burstiness está baixa, o texto está regular demais: quebre um parágrafo em dois e deixe um deles com uma frase só.

Referência: rodando no livro 1 fechado, o g3 dá **zero falhas** e o g1 dá **1 BLOQUEIO em 27 mil palavras**. Esse é o alvo.

---

## Comandos disponíveis

| Comando | Faz |
|---|---|
| `/lab` | constrói e **roda** o Laboratório, produz `corpus/` |
| `/prompt <1..7>` | escreve e testa um dos 7 prompts em três perfis de leitor |
| `/pacote <E1..E12>` | monta o Pacote de v0 de uma sessão |
| `/escrever <E1..E12>` | escreve o capítulo preenchendo o gabarito |
| `/gates <arquivo>` | roda os três hunt e corrige |
| `/auditar <arquivo>` | leitura cética de honestidade, sem corrigir |
| `/costura` | junta tudo, confere pontes e amplitude entre capítulos |
| `/entrega` | monta `ENTREGA/` para a lapidação |

## Ordem de execução do projeto

Não pule etapa. O roteiro operacional completo está em `ROTEIRO_CLAUDE_CODE.md`.

```
0. bash verificar.sh              — não avance enquanto disser "AINDA NÃO"
1. F0     decisões travadas       — docs/DECISOES_F0.md, preenchido pelo Rafael
2. F0.5   conjunto-âncora         — docs/CONJUNTO_ANCORA.md
3. /lab                           — corpus/ com saídas reais
4. /prompt 1..7                   — os sete prompts testados em três perfis
5. /pacote + /escrever E1..E11    — um capítulo por sessão
6. /auditar em cada capítulo      — leitura cética
7. /costura                       — pontes, faixas, amplitude entre capítulos
8. /entrega                       — ENTREGA/ para a lapidação
```

**A escrita não começa sem `corpus/` populado.** Sem saída real, o livro vira promessa — e é exatamente o defeito que ele acusa nos concorrentes.

---

## Contexto de ambiente

- Python 3.10+, `pip install anthropic matplotlib pandas`
- O Laboratório precisa de `ANTHROPIC_API_KEY` no ambiente (chave de API, separada da sua assinatura do Claude Code)
- Saídas do lab vão para `corpus/` em `.md` e `.png` — nunca sobrescreva, sempre acrescente com data
- Manuscrito em Markdown. A conversão para `.docx` acontece depois, em outra máquina, com o template do livro 1. Não tente gerar `.docx` aqui.
