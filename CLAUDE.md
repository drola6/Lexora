# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## O que é esta pasta

`LEXORA/` não é um app com código: contém a skill **site-de-10k** (em [site-de-10k/](site-de-10k/)), um fluxo em português brasileiro para construir e publicar sites cinematográficos com vídeo hero controlado por scroll (vídeo gerado por IA via Higgsfield, processado com ffmpeg, publicado na Cloudflare Pages via Wrangler). Não há build, lint nem testes.

Dois modos de trabalho aparecem aqui, e é preciso distinguir qual o usuário quer:

1. **Usar a skill para construir um site.** Leia [site-de-10k/SKILL.md](site-de-10k/SKILL.md) inteiro e todos os arquivos de [site-de-10k/references/](site-de-10k/references/) antes de responder. A primeira mensagem ao usuário é o checklist da Fase 1 (escaneamento de Higgsfield, ffmpeg, Node.js, curl). Siga as fases em ordem e nunca pule os GATEs (aprovação do storyboard, gate do vídeo por segmento, revisão de texto). Se outras skills de site estiverem instaladas (ex.: higgsfield-websites), esta governa.
2. **Editar a própria skill.** Mantenha o português brasileiro, o tom e as convenções descritas abaixo.

## Arquitetura da skill

- `SKILL.md` é o roteiro: 11 fases (configuração → conversa de design → pesquisa de clientes → nível de profundidade → pacote de design/storyboard → geração com gates → processamento ffmpeg → construção → autoteste → publicação → polimento). Ela referencia os arquivos de `references/` por nome; renomear um arquivo exige atualizar as referências cruzadas em todos os outros.
- `references/leis-de-prompt.md`: as doze leis do vídeo hero, modelos de prompt (em inglês de propósito, porque os geradores rendem melhor assim), encadeamento Nível 2, consulta de custos.
- `references/pacote-de-design.md`: modelo do documento produzido na Fase 5 e consumido ao pé da letra na Fase 8.
- `references/pipeline-scrub.md`: o padrão de engenharia do hero (vídeo buscado como Blob por causa de hospedagens sem HTTP Range, loop rAF interpolado, trava de seek à prova de deadlock, escrita no DOM só na mudança, faixas de legenda ritmadas em vh, portão do hero estático com cinco condições idênticas em CSS e JS) e o checklist de autoteste.
- `references/receitas-ffmpeg.md`: encode de scrub (`-g 8 -keyint_min 8`, `-movflags +faststart`, `-an`), pôster/quadro final, concat, crossfade, disciplina de pastas.
- `references/publicacao.md`: `cloudflare.env` + script `publicar` (`npx wrangler pages deploy`), verificação com `curl`, conversa de custos.
- `references/solucao-de-problemas.md`: tabelas sintoma → causa → conserto, incluindo a receita de Chrome headless para verificar o scrub.

## Regras que atravessam vários arquivos

- **Site gerado:** um `index.html` + `assets/`, HTML/CSS/JS vanilla, sem frameworks, sem build, sem npm.
- **Disciplina de pastas:** a pasta de publicação do site fica separada desta pasta da skill. Brutos, cópias de revisão, `cloudflare.env` e `publicar.sh`/`publicar.ps1` ficam FORA da pasta de publicação. Token e Account ID da Cloudflare nunca passam pelo chat.
- **Pré-visualização:** abrir `index.html` via file:// mostra só o hero estático (fetch bloqueado); o scrub completo precisa de servidor local (`npx http-server` ou `python -m http.server`).
- **Custos:** sempre consultar preço com `get_cost: true` e dizer ao usuário antes de gastar créditos do Higgsfield.
- **Texto (chat e site):** português brasileiro simples, nenhum travessão, perguntas por opções clicáveis. O gate de texto da Fase 9 faz grep no `index.html` por travessões e palavras de estoque (alavancar, robusto, empoderar, destravar, acionável, orientado a dados, soluções, sinergia, escalável) até zerar.
- Ambiente é Windows: `npx` roda como `npx.cmd`; ffmpeg/Node instalam via `winget`.
