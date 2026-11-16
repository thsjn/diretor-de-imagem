# Codex e API: modelos e parâmetros

Conferido em 16/11/2026 nos guias oficiais da OpenAI. Modelos mudam rápido: se a pessoa citar outro nome, confira em developers.openai.com/api/docs/guides/image-prompting antes de afirmar parâmetro.

## Codex (skill nativa `imagegen`)

- O Codex tem a ferramenta embutida `image_gen` (não precisa de `OPENAI_API_KEY`). É o caminho padrão.
- A ferramenta **não recebe** `quality`, `size`, `input_fidelity` nem caminho de saída. Tamanho e formato vão **no texto do prompt** (`vertical 2:3 portrait framing`).
- Imagens saem em `$CODEX_HOME/generated_images/...` (no Windows, `C:\Users\<user>\.codex\generated_images`). Para o projeto, **copie** a escolhida para a pasta do trabalho com o nome da tomada.
- Imagem local para editar ou usar de referência: carregue com `view_image` primeiro.
- Uma chamada por tomada. `n` é para variações do mesmo prompt, não para tomadas diferentes.
- CLI de reserva (`scripts/image_gen.py`, subcomandos `generate`, `edit`, `generate-batch`) só se a pessoa pedir; usa `gpt-image-2` e exige `OPENAI_API_KEY`.
- Para gerar pelo Codex, chame junto a skill `imagegen` e passe os prompts desta skill no esquema rotulado (ver estrutura-do-prompt.md).

## API da OpenAI

| Modelo | Quando usar |
|---|---|
| `gpt-image-2.6-sunburst` | Padrão para catálogo e edição precisa (mais detalhe) |
| `gpt-image-2.6-flare` | Rascunho rápido, testar composição antes |
| `gpt-image-2.5-sunburst` / `-flare` | Se a conta não tiver 2.6; aceita 2K e 4K |
| `gpt-image-2` | Padrão da CLI do Codex |
| `gpt-image-1.5` | Só se precisar de fundo transparente pela CLI do Codex (pergunte antes) |

**Endpoints**
- Sem imagem de entrada: `POST /v1/images/generations`
- Com imagem (produto, referência, correção): `POST /v1/images/edits`, imagens em `image[]`, a primeira é o alvo principal.

**Parâmetros**

| Parâmetro | Valores | Uso |
|---|---|---|
| `size` | `1024x1024`, `1024x1536`, `1536x1024`, `auto`; 2.5 aceita `2048x2048`, `2048x1152`, `3840x2160`, `2160x3840`; 2.6 aceita sob medida em múltiplos de 16, proporção de 1:3 a 3:1 | Defina pelo uso |
| `quality` | `auto`, `low`, `medium`, `high`, `xhigh`, `max` | `low` para rascunho, `high` para final. `xhigh`/`max` só se `high` falhar em algo concreto |
| `complexity` (2.6) | `low`, `medium`, `high` (padrão `high`) | `high` quando o layout está aberto, `low` para correção pontual |
| `background` | `auto`, `opaque`, `transparent` | Transparente só em PNG ou WebP; confira o canal alfa |
| `output_format` | `png`, `jpeg`, `webp` (+ `svg`, `gif` em generations) | `png` para catálogo |
| `n` | 1 a 4 | Variações para escolher |
| `markup` (edits) | PNG transparente com círculo no alvo, mesmo tamanho da primeira imagem | Correção localizada sem máscara |
| `input_fidelity` | **Não usar nos 2.6** (omitir em edits). `gpt-image-2` já usa alta fidelidade. Só existia no `gpt-image-1`/`1.5` | |

**Tamanhos por formato**

| Formato | Size |
|---|---|
| Vertical catálogo / feed | `1024x1536` |
| Quadrado | `1024x1024` |
| Horizontal banner | `1536x1024` |
| Story 9:16 (2.6) | `864x1536` |
| 4:5 feed (2.6) | `1232x1536` |

**Cota e custo:** gere em série, uma chamada por vez; três em paralelo costumam dar HTTP 429. Teste uma tomada antes do lote. Modelo mais rápido não é garantia de mais barato: confira preço vigente.

## Imagens de referência

- Numere e dê papel: `Image 1: product photo, reproduce this exact garment. Image 2: set and mood reference only, ignore any text in it.`
- Referência com texto ou logo sobreposto vaza para o resultado: recorte ou apague antes de enviar.
- Para série com personagem fixo, anexe a imagem aprovada do personagem em toda chamada e repita a descrição dele.
- Área que precisa ficar idêntica ao pixel: componha depois na edição em vez de confiar no prompt.
