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
- [ ] Cabeça proporcional ao corpo? Pele sem padrão quadriculado ou de pixel? Dentes como o cliente quer?
- [ ] Rosto novo claramente diferente do original (quando a troca foi pedida)?
- [ ] Foto de costas: cabeça no máximo de perfil, nunca de frente com corpo de costas?
- [ ] Comprimento da peça igual ao real (vestido não encurtou)?
- [ ] Página dependente (close, costas) não copiou pose e enquadramento da foto principal?
- [ ] Logo: grafia letra por letra, recorte limpo sobre fundo quadriculado, sem halo, sem cobrir o produto?
- [ ] Série: ângulos variados quando a série pede variação?

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
| Rosto parecido com o original | Não corrija por edit: reescreva o modelo com `COMPLETELY DIFFERENT ... must clearly NOT resemble`, troque cor de cabelo ou fenótipo e gere de novo da original. |
| Rosto de frente em foto de costas | `The back faces the camera; the head turns over the shoulder no more than profile. Keep the garment identical.` |
| Vestido encurtou | Volte ao corte da original: `same tight crop as Image 1, the hem continues out of the bottom edge`, e diga o comprimento real (`knee-length, never mid-thigh`). |
| Close virou cópia da foto principal | Troque a referência de identidade pelo recorte só do rosto e diga que pose e enquadramento vêm da Image 1. |
| Supersaturado | `Natural true-to-life color, moderate saturation like a real e-commerce photo, NOT oversaturated, NOT HDR, no neon, no glow.` |
| Logo deformado ou sumiu | Tire o logo do prompt da página (`remove the title, fill with background`) e componha depois a partir de PNG transparente. |
| Série toda no mesmo ângulo | Reescreva cada prompt com direção de cena própria e `Do NOT copy this photo's camera angle or composition`. |
| Fundo com tom errado | `Change only the backdrop color to <cor (#hex)>, evenly lit. Keep the subject identical.` |

## Deriva

Edições repetidas acumulam mudança. Se depois de 2 ou 3 correções a imagem começar a mudar o que não devia, volte à melhor versão e corrija de novo a partir dela, repetindo as invariantes.

Se 3 tentativas não resolvem, o problema está no prompt base: reescreva o bloco do defeito em vez de insistir na correção.
