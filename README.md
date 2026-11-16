# diretor-de-imagem

Skill de direção de fotografia para geração de imagem com IA (GPT Image no Codex ou na API da OpenAI, e também Gemini).

Antes de escrever o prompt, a skill entrevista a pessoa e monta uma ficha de direção: uso, herói, cenário, câmera, lente, abertura, desfoque em camadas, luz, cor e textura. Depois entrega prompts completos por tomada, prontos para colar ou gerar, e prompts de correção para o resultado.

## Instalar

Claude Code:

```bash
git clone https://github.com/thsjn/diretor-de-imagem ~/.claude/skills/diretor-de-imagem
```

Codex:

```bash
git clone https://github.com/thsjn/diretor-de-imagem ~/.codex/skills/diretor-de-imagem
```

## Estrutura

- `SKILL.md`: fluxo, regras de direção e formatos de saída
- `references/perguntas.md`: banco de perguntas com padrões
- `references/estrutura-do-prompt.md`: ordem dos blocos e esqueleto
- `references/direcao-de-cena.md`: ângulos, lentes, abertura e desfoque, luz, composição, cor
- `references/realismo-e-textura.md`: tirar o "chapado" e a cara de IA
- `references/modelos-de-prompt.md`: prompts testados
- `references/codex-e-api.md`: modelos, tamanhos e parâmetros
- `references/revisao-e-correcao.md`: checklist e correções
- `references/molde-entrega.md`: formato do arquivo de entrega
- `references/fontes.md`: fontes das boas práticas
- `agents/openai.yaml`: metadados para o Codex
