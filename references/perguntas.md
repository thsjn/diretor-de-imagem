# Banco de perguntas

Pergunte só o que falta. Cada pergunta tem um **padrão** para quando a pessoa disser "decide você".

## Rodada 1 (sempre)

**1. Para onde vai a imagem?**
a) Catálogo ou e-commerce (fundo limpo, produto inteiro, sem texto)
b) Anúncio ou post de rede social (espaço para texto aplicado depois)
c) Site, banner ou capa (formato largo, área livre para título)
d) Editorial ou lifestyle (clima, história, menos foco em produto)
Padrão: a) se houver produto, d) se não houver.
Define: tamanho, quanto de espaço livre, nível de acabamento.

**2. Qual é o herói, o que precisa sair perfeito?**
a) A roupa ou peça
b) O produto ou embalagem
c) Uma textura ou material (tinta, tecido, comida)
d) A pessoa e a emoção
Padrão: o objeto que a pessoa vende.

**3. Quantas tomadas e de que jeito?**
a) Uma foto principal
b) 3 tomadas (geral, média, detalhe)
c) Série de 6 a 12 para catálogo (frente, costas, perfil, movimento, detalhe, grupo)
d) Variações da mesma tomada (n=2 a 4)
Padrão: b).

**4. Qual estética?**
a) Estúdio comercial claro (high-key, fundo liso)
b) Natural e luminosa (luz de janela, casa, tons quentes)
c) Editorial com clima (contraste, cor marcada)
d) Igual à imagem de referência
Padrão: d) se houver referência, senão a).

## Rodada 2 (só o que faltar)

**Pessoas** (se houver)
- Idade, quantidade, diversidade (nacionalidades ou tons de pele variados por tomada?), expressão (espontânea, séria, rindo).
- Criança: sempre roupa e pose adequadas à idade, sem maquiagem, contexto familiar ou de catálogo.
- Padrão: diversidade variada, expressão espontânea.

**Produto ou roupa exata**
- Tem foto do produto real para anexar? Se tem, o prompt manda reproduzir sem mudanças. Se não, descrever corte, cor (com hex), estampa, tecido, acabamento.

**Cenário**
- Fundo liso de estúdio (qual cor?), ambiente real (qual?), mesa ou superfície (flat lay), tema sazonal (Natal, Páscoa, verão).
- Padrão: o da referência.

**Desfoque**
a) Fundo bem desfocado, sujeito destacado (f/1.4 a f/2)
b) Desfoque suave, fundo reconhecível (f/2.8 a f/4)
c) Tudo nítido (f/5.6 a f/8, flat lay e grupo)
d) Com primeiro plano desfocado emoldurando (camadas)
Padrão: a) para retrato e detalhe, c) para flat lay, b) para corpo inteiro.

**Texto na arte**
a) Nenhum (logo e texto aplicados depois na edição)
b) Sim, exatamente este texto: "..."
Padrão: a).

**Formato**
a) Vertical 2:3 ou 4:5 (feed, catálogo)
b) Quadrado 1:1
c) Horizontal 3:2 ou 16:9 (banner, site)
d) Story 9:16
Padrão: pelo uso da pergunta 1.

**Onde vai gerar**
a) Codex (gero direto aqui)
b) API da OpenAI (entrego .md com parâmetros)
c) ChatGPT ou Gemini, colando à mão
Padrão: b) com arquivo .md.

## Perguntas específicas por caso

| Caso | Pergunte também |
|---|---|
| Regerar imagem "chapada" | O que deve ficar igual (composição? paleta? estampa?) e o que deve mudar (textura, luz, ângulo) |
| Pintura, desenho, artesanato | Qual técnica (aquarela, guache, giz, lápis de cor)? Obra pronta ou em processo, com mão pintando? |
| Comida | Quente ou fria, recém servida, vapor, migalhas, ingrediente cru ao lado? |
| Joia, vidro, metal | Reflexo controlado ou brilho espalhado? Fundo claro ou escuro? |
| Personagem recorrente | Tem imagem aprovada do personagem para usar como referência em todas as cenas? |
| Recorte sem fundo | Precisa de transparência real (PNG com alfa)? |

## Ficha de direção (o que sai da entrevista)

```
Uso: ...
Herói: ...
Tomadas: N (lista curta)
Estética e cenário: ...
Pessoas: ...
Câmera e desfoque: ...
Luz: ...
Paleta: ...
Proibido: texto, logo, ...
Onde gera e formato de saída: ...
```
