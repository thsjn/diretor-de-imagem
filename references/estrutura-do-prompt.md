# Estrutura do prompt

O modelo lê em ordem e dá mais peso ao que vem primeiro. Ordem recomendada pela OpenAI: cenário, sujeito, detalhes, restrições, intenção de uso. Para fotografia comercial, a ordem abaixo funciona melhor porque abre com o tipo de foto e o herói.

## Blocos (em inglês, rótulos em maiúsculas)

1. **Abertura (1 a 2 frases):** tipo de imagem + uso + herói. `Professional children's fashion catalog photograph for a Christmas collection. The clothing is the hero of the image.`
2. **INPUT IMAGES** (só se houver): papel de cada uma, numerado.
3. **SCENE DIRECTION:** a ação, a pose, a expressão, o momento. Escreva como um diretor falando com o fotógrafo. Diga onde o olho deve cair.
4. **MODEL(S) / SUBJECT:** quem ou o quê, com traços concretos (idade, cabelo, tom de pele, expressão; ou formato, material, acabamento).
5. **WARDROBE / PRODUCT (must be exact):** a peça descrita como ficha técnica: corte, decote, manga, comprimento, tecido, cor com faixa hex, estampa, acabamento, calçado e acessórios.
6. **SET:** fundo, chão, props, o que fica perto e longe. Termine com "nothing covers the [herói]".
7. **CAMERA AND LENS:** corpo full-frame, lente em mm, abertura, ISO, velocidade, altura da câmera, distância até o sujeito, orientação.
8. **DEPTH OF FIELD AND LENS BLUR:** plano de foco, o que está nítido, como o fundo se dissolve, primeiro plano desfocado se houver, qualidade do bokeh.
9. **LIGHTING:** principal, preenchimento, recorte, fundo, sombras, reflexo nos olhos.
10. **COLOR AND FINISH:** gradação, fidelidade de cor do herói, pele, grão, nível de detalhe.
11. **STRICT:** proibições e exigências finais.

## Esqueleto para copiar

```
<Image type> for <use>. The <hero> is the hero of the image.

INPUT IMAGES: Image 1: <role>. Image 2: <role>.

SCENE DIRECTION: <action, pose, expression, moment, where the eye lands>.

SUBJECT: <concrete visible traits>.

WARDROBE / PRODUCT (must be exact and fully visible): <technical description, colors with hex range>.

SET: <backdrop, floor, props near and far>. Nothing covers the <hero>.

CAMERA AND LENS: Full-frame camera, <mm> lens at f/<x>, ISO <x>, 1/<x>s, camera at <height>, <angle>, subject about <x> meters away, <orientation> framing.

DEPTH OF FIELD AND LENS BLUR: Focus on <plane>. <What is sharp>. <How the background dissolves>. <Foreground blur if any>. Smooth bokeh, no onion rings, no cutout halo.

LIGHTING: <key: type, side, angle>, <fill>, <rim>, <background light>. <Shadow description>.

COLOR AND FINISH: <grading>, <hero color fidelity>, <skin tones>, fine natural grain, ultra high detail.

STRICT: No text, no letters, no logos, no watermarks, no captions, no overlays. <Hero> fully visible, never cropped. Realistic hands.
```

## Esquema rotulado do Codex (ferramenta nativa `image_gen`)

O Codex aceita o mesmo conteúdo em linhas rotuladas curtas. Use quando for gerar dentro do Codex:

```
Use case: <photorealistic-natural | product-mockup | ads-marketing | ...>
Asset type: <onde será usado>
Primary request: <pedido em uma frase>
Input images: Image 1: <papel>; Image 2: <papel>
Scene/backdrop: ...
Subject: ...
Style/medium: ...
Composition/framing: ...
Lighting/mood: ...
Color palette: ...
Materials/textures: ...
Camera/lens: ...
Constraints: ...
Avoid: ...
```

## Tamanho do prompt

- Prompt longo e específico funciona bem quando cada linha descreve algo **visível**. Corte adjetivo vazio ("amazing", "beautiful", "8k masterpiece").
- Se a pessoa já trouxe um prompt detalhado, só organize nos blocos. Não invente personagem, objeto ou slogan que ela não pediu.
