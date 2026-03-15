# RAG Curator — Claude Code Skill

Transforma qualquer material (PDF, transcrição, notas, prints) em documentos curtos, independentes e otimizados para busca semântica (RAG).

## O que faz

- Segmenta o material por blocos temáticos, gerando um documento autônomo por tema
- Cada documento segue um formato estruturado com título, tags, perguntas e resposta
- Output em texto puro, pronto para colar em qualquer sistema de RAG ou base de conhecimento

## Formato de cada documento

```
[TÍTULO EM CAIXA ALTA, OBJETIVO E FUNCIONAL]
Tags: termo1, termo2, termo3, termo4, termo5
P: Pergunta representando intenção real de busca
P: Segunda pergunta semanticamente distinta
R: Resposta entre 40 e 140 palavras.
```

## Como instalar

```bash
claude skill install efsstudioagents/rag-curator
```

Ou manualmente: copie `SKILL.md` para `~/.claude/skills/rag-curator/SKILL.md`

## Como usar

```
/rag-curator [cole o material aqui]
```

A skill analisa o material, lista os blocos temáticos identificados, confirma a segmentação com você e então gera os documentos.

## Features

- Análise prévia com confirmação antes de gerar (evita retrabalho em materiais grandes)
- Idioma automático: respeita o idioma do material
- Modo incremental: adiciona à base existente sem duplicar temas
- Tratamento de tema repetitivo: consolida em um documento
- Aproveitamento de FAQs existentes no material
- Itens `FALTANDO` listados ao final, sem interromper o fluxo

## Licença

MIT
