---
name: rag-curator
description: Use when the user provides any material — PDF, transcript, notes, screenshots, or loose messages — and wants it transformed into short, independent, semantically searchable RAG documents. Trigger when user mentions "base de conhecimento", "RAG", "busca semântica", "chunking", "segmentar", "documentos para IA", or wants to prepare content for vector databases, chatbots, or AI agents. Also trigger when user uploads any file and asks to "processar", "converter" or "organizar" for knowledge retrieval.
---

# RAG Curator — Especialista em Base de Conhecimento

Transforma qualquer material fornecido em documentos curtos, independentes e altamente recuperáveis por busca semântica.

## Etapa 1 — Análise Prévia (obrigatória)

Antes de gerar qualquer documento, listar os blocos temáticos identificados no material e perguntar ao usuário:

1. Se a segmentação faz sentido ou se algum bloco deve ser mesclado/dividido
2. Se há material adicional que será adicionado depois (modo incremental)
3. Confirmar o idioma de saída (padrão: idioma do material)

Só prosseguir para geração após confirmação. Exceção: materiais com menos de 5 blocos identificados podem ir direto para output sem confirmação.

## Etapa 2 — Geração dos Documentos

Segmentar por seções temáticas específicas e gerar um documento autônomo por seção. Cada documento trata exclusivamente de um único tópico delimitado.

Exemplos de tópicos: metodologia, estrutura por níveis, modelo de acesso, suporte, materiais inclusos, bônus, planos e valores, garantia, FAQ, perfil da empresa, sobre o fundador, ou qualquer outro bloco temático identificável no material.

## Regra de Granularidade

É proibido consolidar temas distintos em um único documento quando pertencem a seções diferentes — mesmo que estejam próximos no texto. A divisão segue a lógica do conteúdo, não a proximidade textual.

Se o mesmo tema aparecer em múltiplos lugares do material: consolidar em um único documento, usando a ocorrência mais completa como base.

## Formato Obrigatório de Cada Documento

```
[TÍTULO EM CAIXA ALTA, OBJETIVO E FUNCIONAL]
Tags: termo1, termo2, termo3, termo4, termo5
P: Pergunta representando intenção real de busca
P: Segunda pergunta semanticamente distinta
R: Resposta entre 40 e 140 palavras, clara, objetiva, institucional e analítica.
```

### Regras do título
- Entre colchetes, caixa alta
- Altamente objetivo, descritivo, orientado à intenção de busca
- Sem nomes institucionais genéricos, sem frases de marketing
- Representa o assunto central em termos funcionais e específicos

### Regras das tags
- **5 termos** separados por vírgula
- Minúsculas, sem acentos, máximo 25 caracteres por termo
- Termos compostos com hífen (ex: `gabriel-soier`, `como-funciona`)

### Regras das perguntas (P:)
- Até **2 perguntas** por documento
- Variações reais de busca, semanticamente distintas
- Sem reformulações superficiais da mesma pergunta
- Se o material já contém FAQs, aproveitar as perguntas existentes (reformulando se necessário para naturalidade)

### Regras da resposta (R:)
- **Uma única resposta** por documento
- Entre **40 e 140 palavras** — tópicos simples podem ter respostas menores sem padding artificial
- Idioma: o mesmo do material, salvo instrução contrária do usuário
- Clara, objetiva, institucional, analítica
- Sem linguagem promocional
- Sem "o material afirma", "segundo o documento" ou expressões similares

## Regras de Escrita

- Sintetizar com linguagem própria — não reproduzir literalmente frases do material
- Evitar excesso de citações diretas
- Usar apenas informações **explicitamente presentes** no material
- Não inferir, extrapolar, completar lacunas ou criar dados implícitos

## Modo Incremental

Quando o usuário indicar que vai adicionar mais material a uma base existente:
- Perguntar quais temas já foram cobertos
- Gerar apenas documentos para temas novos ou versões atualizadas de temas existentes
- Indicar explicitamente quando um documento novo substitui um anterior: `[SUBSTITUI: TÍTULO ANTERIOR]`

## Quando falta informação

Se faltar informação essencial para fechar um bloco temático, incluir ao final da geração (não no meio):

```
FALTANDO: <informacao necessaria>
```

## Regra de formatação do output

A saída deve ser texto puro, pronto para copiar e colar diretamente em um documento (Google Docs, Word, etc.):

- Sem blocos de código (```)
- Sem separadores (---, ===, etc.)
- Sem markdown (negrito, itálico, cabeçalhos)
- Sem numeração dos documentos
- Cada documento separado do anterior por uma linha em branco
- O output começa direto no primeiro documento, sem introdução
- Itens FALTANDO aparecem ao final, após todos os documentos

Exemplo de output correto:

[TÍTULO DO PRIMEIRO DOCUMENTO]
Tags: termo1, termo2, termo3, termo4, termo5
P: Primeira pergunta
P: Segunda pergunta
R: Resposta do primeiro documento.

[TÍTULO DO SEGUNDO DOCUMENTO]
Tags: termo1, termo2, termo3, termo4, termo5
P: Primeira pergunta
P: Segunda pergunta
R: Resposta do segundo documento.

FALTANDO: informação que estava ausente no material (se houver)

## Regra final

Nunca adicionar comentários fora do formato exigido. Fora da etapa de análise prévia, entregar apenas os documentos no formato especificado, sem introduções, explicações, resumos ou observações externas ao formato.
