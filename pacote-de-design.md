# Pacote de design: LEXORA (Nível 1, jornada única)

## 1. A premissa da marca

A linha. Todo site começa com uma linha bem colocada: a primeira conversa, o primeiro traço, o alinhamento certo. A Lexora trabalha devagar e com intenção, e a página prova isso sem dizer: uma única linha de luz roxo-azulada desce no vídeo, deita como horizonte, continua desenhada pelas seções e, no rodapé, se cruza consigo mesma e forma o X do logo. Elemento assinatura: a linha contínua.

## 2. Paleta (direção; tokens finais amostrados da filmagem aprovada)

```css
:root{
  --canvas:#0D0D12;        /* preto fosco levemente azulado, com grão */
  --panel:#15151C;
  --accent:#7468FF;        /* roxo-azulado: linhas, botão, X */
  --accent-hover:#8D83FF;
  --accent-muted:rgba(116,104,255,.28);
  --text-secondary:#9C9AAB;
  --text-primary:#ECEBF3;
}
```

## 3. Trio de fontes

- Display: Michroma 400 (larga, espaçada, tracking alto).
- Texto: Instrument Sans 400 e 500.
- Mono: IBM Plex Mono 400 (títulos pequenos em maiúsculas espaçadas).

## 4. Mapa de faixas (hero de 400vh; pontos de partida)

| Faixa | Intervalo | Momento da filmagem | Texto (ao pé da letra) | Entrada |
|---|---|---|---|---|
| 1 | 0.00 a 0.30 | o fio de luz começa a descer pelo centro | "Sites que falam por você." | deriva para baixo (ecoa a descida), coluna esquerda |
| 2 | 0.36 a 0.64 | o fio chega perto do chão do quadro | "Cada projeto começa com uma conversa." | desfoque para nítido, coluna direita |
| 3 | 0.72 a 1.00 | o fio deita e vira horizonte, repouso | "LEXORA" / "Criamos sites que fazem sua marca ser vista do jeito que ela merece." / botão "Iniciar projeto" | metades se abrindo a partir do centro (ecoa a linha se estendendo), subtítulo e botão em etapas |

## 5. Hero estático (celular, movimento reduzido)

Quadro final ao fundo. "LEXORA" grande no centro, "Criamos sites que fazem sua marca ser vista do jeito que ela merece." embaixo, botão "Iniciar projeto".

## 6. Abaixo da dobra (CTA único: o formulário de contato, âncora #contato)

**O que fazemos** (kicker "O QUE FAZEMOS")
Título: "Três formas de estar presente."
- Sites institucionais. "Para apresentar quem você é, com clareza."
- Lojas virtuais. "Para vender todos os dias, do seu jeito."
- Landing pages. "Para uma campanha, um produto, uma ideia."

**Trabalhos** (kicker "TRABALHOS")
Um projeto por vez, grande, só nome e segmento. Projetos de exemplo, desenhados em HTML/SVG dentro de uma moldura de navegador, para troca pelos reais:
- Atelier Moraes. Arquitetura (fachada de casa moderna, faixa com três obras).
- Casa Verbena. Restaurante vegano (prato de legumes, horários, trecho do cardápio com preços).
- Nórdica. Imobiliária (busca de imóveis, três anúncios com foto, preço e metragem).

**Como funciona** (kicker "COMO FUNCIONA")
Título: "Do primeiro contato ao site no ar."
- 01 Conversa. "Você conta sobre o seu negócio. A gente escuta antes de desenhar."
- 02 Proposta. "Escopo, prazo e valor por escrito, antes de começar."
- 03 Criação. "Você acompanha cada etapa e vê o site antes de ele ir ao ar."
- 04 Entrega. "O site no ar, com domínio e acessos no seu nome. E a gente continua por perto."
Momento interativo: "Segure para traçar." Segurar desenha a linha que liga as quatro etapas e acende cada uma. Soltar cedo recua a linha devagar. Movimento reduzido mostra tudo traçado.

**Depoimentos** (kicker "DEPOIMENTOS")
Uma frase por vez, sem estrelas. EXEMPLOS, trocar por frases reais antes de publicar:
- "Entenderam o restaurante antes de falar de site." Casa Verbena.
- "Recebemos cada etapa no dia combinado." Atelier Moraes.
- "Os imóveis finalmente aparecem do jeito que merecem." Nórdica.

**Contato** (id "contato")
Título: "Vamos conversar sobre o seu projeto."
Texto: "Conte o que você precisa. Respondemos em até 24 horas."
Campos: Nome / WhatsApp / Conte sobre seu projeto. Botão: "Enviar".
Sucesso: "Recebemos. Respondemos em até 24 horas."
Destino do formulário: a definir com o usuário na Fase 8.

**Rodapé**
Logo, redes sociais, e-mail. Sem mais nada.

## 7. Camada vetorial

- A linha assinatura: SVG fino em --accent que se traça com o scroll entre as seções, saindo do horizonte do vídeo; no rodapé dois traços se cruzam e formam o X.
- Grão fosco fixo de fundo (SVG feTurbulence), deriva lenta acima de 60s.
- Poeira de luz em nível de sussurro em O que fazemos.
- Movimento reduzido: linhas já traçadas, motores parados.

## 8. Engenharia

Blob simples (vídeo abaixo de 8 MB), interpolação normalizada por dt, seeks travados, escritas de DOM por delta, faixas ritmadas com teste de flick, legibilidade em quatro camadas, cinco portões do hero estático vivos com listeners, completo sem o vídeo, piso de qualidade de pipeline-scrub.md, padrão site-inteiro-animado.

Restrições do briefing: nada de "premium", "luxo", "exclusivo", "para poucos", "vagas limitadas", "edição limitada", "promoção", "barato", "o melhor", "garantido", nenhum ponto de exclamação. Movimento lento, nada pisca ou pula.

## 9. Gate de texto

Cada linha acima embarca ao pé da letra. Antes de alguém ver: zero travessões, zero palavras de estoque, zero palavras proibidas do briefing, zero exclamações, varredura de sinais de IA.
