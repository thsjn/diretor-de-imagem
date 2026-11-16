# Revisão e correção

## Checklist (olhe cada imagem)

- [ ] O herói está fiel? (cor, estampa, corte, proporção)
- [ ] Herói inteiro, nada cortado (barra, sapato, borda do produto)?
- [ ] Texto, letra, número ou logo que não foi pedido?
- [ ] Mãos e dedos naturais? Rostos sem deformação?
- [ ] Desfoque no lugar certo (herói nítido, fundo suave)?
- [ ] Textura real ou chapado?
- [ ] Luz com direção e sombra de contato no chão?
- [ ] Pele com tom fiel?
- [ ] Série consistente (mesmo fundo, luz, paleta das outras tomadas)?
- [ ] Criança: pose e roupa adequadas à idade?

Uma folha de contato acelera a revisão de série grande (todas as imagens lado a lado num JPG).

## Correção: uma mudança por vez

Mande a imagem gerada como `Image 1: edit target` (e a foto do produto como `Image 2` quando for fidelidade de peça). Sempre termine com `Keep everything else identical.`

| Problema | Prompt de correção |
|---|---|
| Estampa ou cor diferente do produto | `Change only the dress print and color so they match Image 2 exactly. Keep the child, pose, set, lighting and lens blur identical.` |
| Texto ou logo indesejado | `Remove any text, letters, numbers or logos. Keep everything else identical.` |
| Fundo nítido demais | `Keep the subject identical. Make the background much more defocused, as if shot at f/1.4: background elements become soft round bokeh with smooth edges.` |
| Herói desfocado | `Keep everything identical but bring the <hero> into sharp focus; only the background stays soft.` |
| Peça cortada | `Extend the canvas downward so the full hem and shoes are visible. Keep everything else identical.` |
| Mãos estranhas | `Fix the hands so each has five natural fingers in a relaxed pose. Keep everything else identical.` |
| Chapado, sem textura | `Keep the composition identical. Make the <material> physically real: <textura concreta do realismo-e-textura.md>, revealed by low raking light.` |
| Tudo igual e simétrico | `Make every <element> slightly different in shape, size and angle, as if made one by one by hand.` |
| Pele de plástico | `Keep identity identical. Restore natural skin texture with fine pores, no retouching.` |
| Cor lavada ou estourada | `Keep everything identical. Restore true-to-life colors: <cor com hex>, natural white balance.` |
| Fundo com tom errado | `Change only the backdrop color to <cor (#hex)>, evenly lit. Keep the subject identical.` |

## Deriva

Edições repetidas acumulam mudança. Se depois de 2 ou 3 correções a imagem começar a mudar o que não devia, volte à melhor versão e corrija de novo a partir dela, repetindo as invariantes.

Se 3 tentativas não resolvem, o problema está no prompt base: reescreva o bloco do defeito em vez de insistir na correção.
