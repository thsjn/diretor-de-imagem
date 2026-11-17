# Realismo e textura: tirar o "chapado"

Imagem chapada é quando parece vetor colado: cor uniforme, borda perfeita, nada reage à luz. O remédio é sempre o mesmo: **descrever o material fisicamente** e **pôr uma luz que revele esse material**.

## Princípio geral

1. Peça `photorealistic` ou `real photograph` explicitamente.
2. Descreva **imperfeição concreta**: variação, borda irregular, marca de uso, poeira, fibra.
3. Use **luz rasante** ou lateral para a textura aparecer.
4. Proíba o defeito: `must never look digital, vector, printed or perfectly uniform`.
5. Prompte como se a foto fosse tirada no momento: `as if captured in the moment`.

## Por material

**Pintura em papel (aquarela e guache)**
- Papel: `heavy 300gsm cold-press watercolor paper, visible tooth, gentle cockling and buckling from water, edges slightly lifted casting a thin shadow`.
- Aguada: `wide flat brush washes, visible stroke direction, uneven pigment density, granulation settling in the paper grain, cauliflower blooms, hard drying edges`.
- Guache: `opaque gouache, raised pigment ridges along the edges, visible brush marks, slight asymmetry, some areas translucent showing the layer beneath`.
- Em processo: `freshly painted area still wet with a glossy sheen, darker than the dry areas`.
- Cada elemento único: `no two flowers identical, painted one by one by hand`.
- Prancha de estampa (a estampa da roupa mostrada como pintura): descreva os motivos, posições e cores da estampa original um a um no prompt e use a arte como referência de conteúdo, não como base de composição. Borda branca do papel pintada à mão com pequenos vazamentos. Luz de janela baixa e rasante, senão o papel sai liso. Deixe um canto livre na mesa para o logo da marca entrar depois.

**Tecido**
- `visible cotton weave`, `natural gathers and folds`, `finely stitched rolled hem`, `slight wrinkles from movement`, `fabric catching light on the folds`.
- Malha, linho, veludo, cetim: nomeie o tecido; cada um reflete luz de um jeito.

**Pele**
- `natural skin texture with fine pores`, `subtle natural sheen`, `no airbrushed look`, `rosy cheeks`, `light freckles` quando cabe.
- Criança: `no makeup look`.

**Madeira, pedra, cerâmica**
- `visible wood grain`, `micro scratches`, `matte glaze with small irregularities`, `slight dust in the crevices`.

**Metal, vidro, joia**
- `controlled reflections from softboxes`, `crisp specular highlights`, `subtle fingerprints` (se quiser realismo cru), `caustics on the table` para vidro.

**Comida**
- `steam rising`, `crumbs scattered`, `glossy sauce`, `irregular slices`, `condensation droplets` em bebida gelada.

**Papel e embalagem**
- `paper fibers`, `slight crease`, `soft shadow under the edges`, `uncoated matte stock`.

## Sinais de "cara de IA" e o antídoto

| Sinal | Antídoto no prompt |
|---|---|
| Tudo simétrico e perfeito | `slight natural asymmetry`, `each one slightly different` |
| Pele de plástico | `real skin texture, fine pores, no retouching` |
| Luz sem direção | Posicione a luz principal e diga onde cai a sombra |
| Fundo genérico desfocado | Descreva o cenário real e como ele se dissolve |
| Cor saturada demais | `natural true-to-life color, moderate saturation like a real e-commerce photo, NOT oversaturated, NOT HDR, no neon, no glow` |
| Rosto repetido ou "mesma cara" | Descreva traços diferentes E troque cor de cabelo ou fenótipo |
| Cabeça grande demais | `natural child body proportions, head size proportional to the body` |
| Pele com padrão quadriculado | `clean natural skin rendering without grid, checker, crosshatch or pixel pattern artifacts` |
| Objetos flutuando | `soft contact shadows grounding every object` |
| Mãos estranhas | `realistic hands with five natural fingers in a relaxed pose` |
| Excesso de polimento | `editorial candid feel, avoid studio polish` (quando não for catálogo) |

## Regerar a partir de uma imagem chapada

- No edit, dê papel à imagem: `Use the attached image only as reference for composition, colors and pattern.`
- Diga o que muda: `The painting must look genuinely painted by hand, NOT a flat digital print.`
- Na API, não force fidelidade alta à entrada (nos modelos antigos, `input_fidelity: low`; nos 2.x, só não peça para preservar o visual).
