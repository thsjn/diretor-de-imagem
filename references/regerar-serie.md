# Regerar uma série a partir de fotos prontas

Caso típico: catálogo ou campanha que já existe (PDF ou pranchas), ficou ruim (supersaturado, cara de IA, rosto repetido) e precisa ser refeito mantendo produto, pose e layout, trocando modelo, luz ou textura. Lições de uma regeração real de catálogo infantil com 48 páginas.

## 1. Levantar o material antes de escrever prompt

- Extraia a imagem embutida de cada página do PDF (`fitz`/PyMuPDF: `page.get_images()` + `doc.extract_image`). Se houver os arquivos-fonte em alta (pranchas JPG), case cada um com a página certa por diferença de miniatura (24x34 px, menor erro médio) e prefira o de alta.
- Monte uma folha de contato do PDF inteiro e classifique cada página: foto principal da peça (heroína), costas, close, dupla ou trio, prancha de estampa, capa.
- Texto queimado na imagem (nome, preço, REF): leia e passe para um arquivo de dados (`produtos.json`). Ele vira texto vivo no PDF novo e para de ser problema de imagem.
- Anote o que estiver estranho nos dados (REF com dígitos a menos, tamanho único) e pergunte ao cliente; não "corrija" sozinho.

## 2. Ordem de geração

1. **Heroínas primeiro** (uma por produto): definem o rosto novo de cada modelo.
2. **Revise as heroínas** antes de seguir. Rosto parecido demais com o original ou defeito de anatomia: refaça agora, porque as outras páginas vão copiar esse rosto.
3. **Dependentes depois** (costas, close, dupla, trio), usando o rosto aprovado.
4. Logos e artes gráficas numa fila à parte (ver seção 6).

## 3. Edit preservando a roupa

- `Image 1` = a foto original como **base de edição** (pose, corte, enquadramento, cenário, corte exato da roupa).
- `Image 2` = a arte plana da estampa (prancha, ficha técnica) como **fonte da verdade** de motivos e cores. Diga para ignorar mão, pincel, papel e logo que estiverem nela.
- Descreva a roupa em texto também: cor com faixa hex, decote, manga, babado, laço, comprimento, o que tem nas costas.
- Peça cor natural explicitamente quando o problema anterior foi saturação: `moderate saturation exactly like a real e-commerce photo, NOT oversaturated, NOT HDR, no neon, no glow`.

## 4. Rosto novo de verdade

- "Different child" sozinho não basta: o modelo devolve um rosto quase igual. Use `COMPLETELY DIFFERENT child ... must clearly NOT resemble the child in Image 1: different face shape, eyes, nose, eyebrows, lips, jaw and cheekbones`.
- Mude também **cor de cabelo** ou **fenótipo** na descrição; só com traços faciais a semelhança persiste. Mantenha penteado, coroa e laço se fazem parte da direção.
- Em pose de perfil ou cabeça baixa o rosto aparece pouco e tende a repetir o original: troque o cabelo com mais força nessas.
- Defeitos que apareceram e viraram regra fixa no bloco do modelo: cabeça desproporcional (`head size proportional to the body, normal for the age`), textura quadriculada na pele (`no grid, checker, crosshatch or pixel pattern artifacts`), dente faltando quando o cliente não quer (`complete set of teeth, no gaps`).

## 5. Mesma criança em várias páginas

- Passe como referência de identidade **só o recorte do rosto** da heroína aprovada (terço de cima da imagem), não a foto inteira. Com a foto inteira o modelo copia pose e enquadramento e a página de close vira cópia da heroína.
- Diga o papel: `FACE CLOSE-UP ... use it ONLY for identity ... Do not take pose, framing or clothes from it`, e que pose e enquadramento vêm só da `Image 1`.
- **Costas:** `the head turns over the shoulder no more than in Image 1 (profile or three-quarter at most) ... never fully frontal while the back faces the camera`. Sem isso sai rosto de frente com corpo de costas.
- **Comprimento da peça:** se a original corta a saia, peça o **mesmo corte apertado** com a barra saindo pela base do quadro. Pedir o vestido inteiro faz o modelo encurtar a peça. Diga o comprimento real (`KNEE-LENGTH, hem just below the knees, never mid-thigh`).

## 6. Logo e título: sempre em camada separada

- Prompt da página manda **remover** o título e deixar a área com o fundo. O logo entra depois por composição, nítido e na posição medida na página original.
- Gere o logo sozinho sobre **cor lisa conhecida** e recorte por distância de cor até o fundo (alfa = distância; desfaça a mistura para não ficar halo).
  - **Não use preto** atrás de giz/traço fino: os cinzas do traço viram mancha no recorte e o modelo inventa névoa de giz.
  - **Não use branco** atrás de letra branca (já aconteceu: veio branco sobre branco).
  - Use uma cor sólida bem diferente da letra, de preferência a do fundo onde o logo vai morar (`perfectly flat solid #027C68, no texture, no gradient`).
- Versão colorida de um logo já aprovado: faça edit a partir do aprovado (`CHANGE ONLY the big word: fill each letter with ...`) em vez de gerar do zero.
- Confira grafia letra por letra (acentos, cedilha) e confira o recorte sobre fundo quadriculado.
- Logo da marca em várias páginas com ângulos diferentes: escolha a posição à mão por página (canto livre da mesa), não confie em detecção automática de "área lisa".

## 7. Série que precisa variar

- Edit sobre a mesma base em todas as páginas gera tudo no mesmo ângulo. Para variar, a imagem de entrada vira **referência de conteúdo**, não base: `reference of the print artwork ... Do NOT copy this photo's camera angle or composition`.
- Escreva uma direção de cena **diferente por tomada** (vista de cima girada, 35° rasante, três quartos, varal com pregadores, cavalete, segurada pelas mãos, close no pincel, colada com fita numa prancha) com lente e abertura próprias.

## 8. Texto do produto no PDF

- Texto vivo (HTML + Chrome `--print-to-pdf`, ou ferramenta de layout), nunca na imagem: fica nítido, corrige sem regerar e o cliente consegue editar depois.
- Ordem de leitura que o cliente de moda infantil pediu: **nome grande, tamanhos grandes, preço menor, REF discreta**. Preço grande demais rouba a atenção da peça. Sem caixa branca por cima da foto.
- Versão para WhatsApp: reduza só as fotos (1200 px de largura, JPG ~66) e mantenha o texto vivo; 48 páginas A4 ficaram em ~9 MB.
- Um PDF de antes e depois lado a lado ajuda a aprovar com o cliente.
