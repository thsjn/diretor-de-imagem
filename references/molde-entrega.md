# Molde do arquivo de entrega

Salve em `<pasta-do-projeto>/prompts-<tema>.md`. Copie as referências para `<pasta-do-projeto>/referencia/` e crie `<pasta-do-projeto>/saida/`. Informe à pessoa os caminhos absolutos.

```markdown
# <Tema>: <N> tomadas (<onde gera>)

Referência: `<caminho absoluto da imagem de referência>`
<Aviso se a referência tiver texto ou logo sobreposto.>

## Ficha de direção

| Item | Decisão |
|---|---|
| Uso | ... |
| Herói | ... |
| Estética | ... |
| Paleta | ... |
| Proibido | ... |

## Configuração da chamada

| Parâmetro | Valor |
|---|---|
| Modelo | ... |
| Endpoint | ... |
| `quality` | ... |
| `n` | ... |
Ordem das imagens no edits: Image 1 ..., Image 2 ...

## Resumo das tomadas

| # | Arquivo | Size | Ângulo | Lente | Destaque |
|---|---|---|---|---|---|
| 01 | `saida/01-....png` | ... | ... | ... | ... |

---

## 01. <Nome da tomada>

**Arquivo:** `saida/01-....png` · **Size:** `...`

` ` `
<prompt completo em inglês>
` ` `

---

## Correções rápidas

| Problema | Prompt de correção |
|---|---|
```

Regras do arquivo: sem travessão, sem blockquote, prompts em blocos de código, cada prompt completo e independente.
