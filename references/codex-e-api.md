# Codex e API: modelos e parâmetros

Conferido em 16/11/2026 nos guias oficiais da OpenAI. Modelos mudam rápido: se a pessoa citar outro nome, confira em developers.openai.com/api/docs/guides/image-prompting antes de afirmar parâmetro.

## Codex (skill nativa `imagegen`)

- O Codex tem a ferramenta embutida `image_gen` (não precisa de `OPENAI_API_KEY`). É o caminho padrão.
- A ferramenta **não recebe** `quality`, `size`, `input_fidelity` nem caminho de saída. Tamanho e formato vão **no texto do prompt** (`vertical 2:3 portrait framing`).
- Imagens saem em `$CODEX_HOME/generated_images/...` (no Windows, `C:\Users\<user>\.codex\generated_images`). Para o projeto, **copie** a escolhida para a pasta do trabalho com o nome da tomada.
- Imagem local para editar ou usar de referência: carregue com `view_image` primeiro.
- Uma chamada por tomada. `n` é para variações do mesmo prompt, não para tomadas diferentes.
- CLI de reserva (`scripts/image_gen.py`, subcomandos `generate`, `edit`, `generate-batch`) só se a pessoa pedir; usa `gpt-image-2` e exige `OPENAI_API_KEY`.
- `image_gen` não entrega fundo transparente. Para logo ou recorte: gere sobre cor lisa e recorte por distância de cor (ver regerar-serie.md, seção 6).

### Lote pelo terminal (`codex exec`)

Para série grande, rode um script que chama o Codex uma vez por tomada, em série:

```bash
timeout 900 codex exec -c approval_policy=never --skip-git-repo-check \
  -C "<pasta do trabalho>" -s workspace-write "$INSTRUCAO" < /dev/null > "logs/$n.log" 2>&1
sid="$(grep -m1 -oE 'session id: [0-9a-f-]+' "logs/$n.log" | cut -d' ' -f3)"
[ -n "$sid" ] && cp "$(ls -t ~/.codex/generated_images/$sid/*.png | head -1)" "saida/$n.png"
```

Instrução que funcionou: "Tarefa única, sem perguntas. Use a ferramenta nativa image_gen. 1. Abra com view_image, nesta ordem, cada arquivo listado em INPUT IMAGES (caminhos absolutos); se faltar algum, pare. 2. Gere UMA imagem com o prompt abaixo, palavra por palavra, com a Image 1 como alvo de edição. 3. Não copie nem altere arquivo nenhum." seguida do prompt.

Gotchas:
- **`< /dev/null` é obrigatório.** Sem ele o `codex exec` pode ficar lendo stdin e não gerar nada.
- **Não peça ao Codex para copiar a imagem:** ele trava pedindo permissão. O script copia.
- **Copie pela pasta da sessão** (`generated_images/<session id>/`), nunca "o PNG mais novo da pasta inteira": se a chamada falhar ou houver duas filas, vem imagem de outro trabalho. Sem session id, marque falha.
- **Uma fila por vez.** Duas em paralelo dobram memória; um lote já foi encerrado por falta de memória da máquina.
- **Ao parar um lote**, mate o loop do shell e os `codex.exe` filhos e confira com `ps` que nada sobrou. Parar só a tarefa deixa o loop vivo gerando e copiando por cima.
- Cada imagem leva ~1,5 min. Teste 1 tomada antes do lote e revise a primeira leva antes de seguir.
- Arquivo do script com acento: grave em UTF-8; instrução em pt-BR funciona.

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
