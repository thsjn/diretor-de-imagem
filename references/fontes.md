# Fontes

Consultadas em 16/11/2026.

**Oficiais (OpenAI)**
- GPT Image prompting guide (modelos 2.5 e 2.6, parâmetros, edição, armadilhas): https://developers.openai.com/api/docs/guides/image-prompting
- Cookbook, GPT Image Generation Models Prompting Guide: https://developers.openai.com/cookbook/examples/multimodal/image-gen-models-prompting-guide
- Cookbook, gpt-image-1.5 Prompting Guide: https://developers.openai.com/cookbook/examples/multimodal/image-gen-1.5-prompting_guide
- Skill nativa do Codex `imagegen` (local: `~/.codex/skills/.system/imagegen`, arquivos `SKILL.md`, `references/prompting.md`, `references/sample-prompts.md`): taxonomia de uso, esquema rotulado, política de especificidade

**Comunidade (usar como apoio, não como regra)**
- fal.ai, GPT Image 2 Prompting Guide: https://fal.ai/learn/tools/prompting-gpt-image-2
- Luma, GPT Image 2 Complete Guide: https://lumalabs.ai/learning-center/articles/gpt-image-2-complete-guide
- Atlas Cloud, 7 dicas de luz e composição: https://www.atlascloud.ai/blog/guides/beyond-the-prompt-7-advanced-gpt-image-tips-for-perfect-lighting-and-composition
- Skills públicas de GPT Image: ycwfs/gpt-image, wuyoscar/gpt-image2-skill, intellectronica/agent-skills

**Prática própria**
- Sessões reais de catálogo de moda infantil de Natal (12 tomadas) e de pintura floral realista em papel (3 tomadas), cujos prompts estão em `modelos-de-prompt.md`.
- Pipeline de vídeo com IA (geração de imagem com Gemini, referência de estilo, revisão por folha de contato).

## O que as fontes concordam

1. Defina resultado e uso antes de tudo; seções rotuladas em prompt complexo.
2. Descreva o visível (material, luz, cor, meio); palavra de clima sozinha não basta.
3. Câmera é pista de aparência, não garantia física.
4. Pessoas: enquadramento, olhar, interação com objetos ("feet included").
5. Texto exato entre aspas, quantas vezes aparece, e "no extra text".
6. Edição: "change only X", lista do que preservar, papel numerado de cada imagem.
7. Itere uma mudança por vez e repita as restrições; "same style as before" não garante.
8. Série: descrição fixa do personagem repetida em todo prompt + imagem aprovada como entrada.
9. Qualidade mais alta não garante resultado melhor; compare na sua carga.

## Prática própria

- Regeração de um catálogo infantil de 48 páginas pelo Codex (`codex exec` em lote), 17/11/2026: origem de regerar-serie.md, dos gotchas de lote em codex-e-api.md e dos exemplos E e F em modelos-de-prompt.md.
