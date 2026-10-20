# Pacote de design: LEXORA (jornada longa em tomada única)

## 0. Produção

**Nível:** jornada longa, feita com UMA tomada de 15 segundos no Kling 3.0 Pro em vez de três trechos emendados. Mesma jornada, sem emendas, dentro do teto.

**Teto do usuário: 60 créditos.**

| Item | Modelo | Créditos |
|---|---|---|
| Quadro inicial (16:9, 2k) | Nano Banana Pro | 2 |
| Vídeo (15 s, pro, sem som) | Kling 3.0 Pro | 26,25 |
| **Primeira passada** | | **28,25** |
| Reserva: 1 nova tentativa de vídeo + 1 de imagem | | até 28,25 |
| **Pior caso** | | **56,5** |

Imagens de apoio: nenhuma gerada. As seções de baixo usam quadros tirados do vídeo aprovado (grátis) e desenhos em SVG/CSS.

**Mobile:** celulares e movimento reduzido recebem o hero estático (quadro final + texto composto). O vídeo roda em notebook e desktop.

**Pesquisa (linguagem real dos compradores):**
- Agências de site: "ignorou todas as mensagens", "não cumpriu o prazo", "mudanças solicitadas não eram executadas", ficar "sem o site e sem o dinheiro".
- WhatsApp: quem espera "simplesmente desaparece", "procura outro fornecedor". Noite, fim de semana e almoço são os buracos.
- Robôs: muita gente diz que "odeia" robô, principalmente quando a conversa fica "andando em círculos" sem chegar numa pessoa.

**A única chamada para ação:** o formulário de contato, âncora `#contato`, botão "Quero conversar" em toda a página.

## 1. A premissa da marca

O toque. Uma gota toca a água parada e a água inteira responde, sem pressa e sem barulho, até o horizonte. É assim que a Lexora trabalha: uma mensagem chega e o site e as automações respondem sozinhos, com calma, até onde for preciso. A pessoa entra quando faz diferença. Elemento assinatura: **o anel que se espalha.** Ele nasce na água do vídeo, continua na página (cada seção que entra, cada resposta da demonstração, o botão principal) e vira a marca no rodapé: um ponto com dois anéis.

## 2. Paleta (direção; tokens finais amostrados da filmagem aprovada)

```css
:root{
  --canvas:#0B1015;        /* grafite azulado, com grão */
  --panel:#111A21;         /* superfícies e cartões */
  --water:#16303B;         /* azul petróleo da água, preenchimentos suaves */
  --accent:#D3EAF4;        /* luz gelo: botão principal, foco, anéis */
  --accent-hover:#EAF6FB;
  --accent-muted:rgba(190,225,240,.22);
  --text-secondary:#93A3AE;
  --text-primary:#E8EEF2;
}
```

O botão principal é luz gelo com texto grafite. O acento aparece no botão, nos estados de foco e nos anéis. Em nenhum outro lugar.

## 3. Trio de fontes

- Display: **Sora** 300 e 400 (geométrica, calma, precisa; tamanhos grandes com tracking levemente negativo).
- Texto: **Hanken Grotesk** 400 e 500.
- Mono: **JetBrains Mono** 400 (rótulos pequenos, registro da demonstração).

## 4. Storyboard da tomada (15 segundos, uma tomada contínua)

| Tempo | Progresso | O que acontece |
|---|---|---|
| 0 a 5 s | 0.00 a 0.33 | Uma gota de luz gelo cai devagar pelo centro, atravessando névoa azul. A câmera desce junto, a névoa sobe pela lente. A água escura surge embaixo. |
| 5 a 7,5 s | 0.33 a 0.50 | A gota toca a água no centro: uma coroa pequena de luz, gotículas na lente com uma batida de desfoque, que limpa. Nasce o primeiro anel. |
| 7,5 a 12,5 s | 0.50 a 0.83 | A câmera baixa até rente à água e desliza para frente. Os anéis viajam até o horizonte, onde pontinhos de luz acendem um a um quando o anel chega. |
| 12,5 a 15 s | 0.83 a 1.00 | Repouso: água lisa na metade de baixo, anéis largos sumindo, fileira calma de luzes no horizonte, névoa e céu azul grafite na metade de cima. |

A faixa central fica livre para a gota. O texto vive nas colunas laterais durante a descida e na metade de cima no repouso.

## 5. Mapa de faixas (hero de 1000vh; validado pelo teste de flick na filmagem aprovada)

O toque na água acontece aos 4,55 s (progresso 0.30). As faixas foram reajustadas à filmagem real.

| Faixa | Intervalo | Momento da filmagem | Rótulo pequeno | Texto (ao pé da letra) | Entrada |
|---|---|---|---|---|---|
| 1 | 0.00 a 0.15 | gota caindo alto na névoa | "23:04 · mensagem recebida" | "Seu cliente mandou mensagem às 23h." | deriva para baixo, palavra por palavra (ecoa a queda), coluna esquerda |
| 2 | 0.17 a 0.30 | gota perto da água, superfície surgindo | "fora do horário" | "Fora do horário. Todo mundo dormindo." | desfoque para nítido (ecoa a névoa), coluna direita |
| 3 | 0.33 a 0.50 | depois do toque, primeiros anéis | "23:04 · respondida em 2 segundos" | "Ele teve resposta na hora." | anel: caracteres surgem do centro da linha para as pontas (ecoa o anel), coluna esquerda |
| 4 | 0.54 a 0.76 | anéis viajando, fileira de luzes no horizonte | "23:05 · tudo resolvido" | "Horário marcado. Orçamento enviado. Você só confere de manhã." | as três frases acendem em sequência, cada uma com um ponto de luz, coluna direita no céu |
| 5 | 0.80 a 1.00 | repouso | | "LEXORA" / "Sites e automações que trabalham pelo seu negócio, em silêncio." / botão "Quero conversar" | letras do logo se abrem do centro para fora, depois subtítulo, depois botão; centralizado na metade de cima |

Indicador de scroll no pé do hero: anel de carregamento com uma seta e a palavra "role".

**Presente da filmagem:** as luzinhas do horizonte saíram num branco quente (token `--lamp:#F4E4D2`). Essa cor aparece só na fileira de luzes de Como funciona, nos pontos da faixa 4 e no marcador 23:04 do relógio.

## 6. Hero estático (celular, movimento reduzido)

Quadro final ao fundo. Linha pequena em cima: "Seu cliente mandou mensagem às 23h. Ele teve resposta na hora." Depois "LEXORA" grande, "Sites e automações que trabalham pelo seu negócio, em silêncio." e o botão "Quero conversar".

## 7. Abaixo da dobra (tudo afunila para `#contato`)

**Navegação:** logo (ponto com dois anéis + LEXORA). Links: Serviços, Teste, Trabalhos, Como funciona, Dúvidas. Botão: "Quero conversar".

**O problema** (kicker "O PROBLEMA"; layout de duas colunas: texto e relógio)
Título: "Quem espera resposta não reclama. Vai embora."
Texto: "O cliente manda mensagem, fica sem resposta e procura outro lugar. Sem avisar, sem voltar. Acontece mais à noite, no fim de semana e na hora do almoço, quando ninguém está olhando o celular."
Elemento vivo: um relógio de 24 horas em forma de anel. O arco das 9h às 18h aceso com o rótulo "Alguém respondendo", o resto apagado com o rótulo "O resto do dia". Um ponto de luz percorre o anel devagar.
Legenda: "Das 24 horas do dia, quantas têm alguém respondendo?"

**O que fazemos** (kicker "O QUE FAZEMOS"; layout dividido em dois pilares)
Título: "Duas coisas, bem feitas."
- Sites. "Para mostrar o seu negócio com clareza e levar o visitante até o contato." Itens: Sites institucionais, Lojas virtuais, Landing pages.
- Automações. "Para responder, agendar e organizar enquanto você cuida do resto." Itens: Atendimento no WhatsApp, Agendamento automático, Orçamentos e lembretes.
Linha final: "Funcionam sozinhos ou juntos. O site traz o cliente, a automação responde."

**Teste agora** (kicker "TESTE AGORA"; o momento interativo)
Título: "Mande uma mensagem e veja o que acontece."
Texto: "O Estúdio Brisa é um salão de exemplo, com uma automação de exemplo. Toque numa pergunta e veja a resposta chegar."
Conversa (cabeçalho "Estúdio Brisa · responde na hora"):
- Abertura: "Oi, aqui é o atendimento do Estúdio Brisa. Como posso ajudar?"
- "Vocês abrem sábado?" → "Abrimos sim, das 9h às 17h. Quer que eu veja um horário para você?"
- "Quanto custa um corte?" → "O corte feminino começa em R$ 80 e o masculino em R$ 50. Quer marcar?"
- "Quero marcar um horário" → "Tenho quinta às 15h ou sexta às 10h. Qual fica melhor?" → ("Quinta às 15h" ou "Sexta às 10h") → "Pronto, marcado para [dia e hora]. Mando um lembrete um dia antes."
- "Falar com uma pessoa" → "Claro. Já avisei a Ana, ela continua daqui assim que pegar o celular. Ela vai ver tudo o que você já me contou."
Painel ao lado, título "Por trás da conversa", com uma linha por ação e um anel saindo de cada uma: "Pergunta respondida em 2 segundos", "Tabela de preços enviada", "Horário reservado na agenda", "Lembrete agendado", "Ana avisada com o resumo da conversa".
Linha final: "Isso, no WhatsApp do seu negócio, 24 horas por dia."
Mecânica: cada toque mostra "digitando" por um instante, a resposta entra suave, o painel acende a linha certa e emite um anel. Movimento reduzido: respostas aparecem direto, sem anel.

**Trabalhos** (kicker "TRABALHOS"; galeria)
Título: "O estilo do nosso trabalho."
Texto: "Projetos de exemplo, para mostrar como pensamos cada negócio."
Os três projetos de exemplo do site atual, mantidos (desenhados em HTML dentro de uma moldura de navegador): Atelier Moraes, Arquitetura. Casa Verbena, Restaurante vegano. Nórdica, Imobiliária.

**Como funciona** (kicker "COMO FUNCIONA"; linha do tempo horizontal que se traça com o scroll, um anel por etapa)
Título: "Do primeiro contato até tudo funcionando."
- 01 Conversa. "Você conta como funciona o seu negócio e onde perde tempo. A gente escuta antes de propor."
- 02 Proposta. "Escopo, prazo e valor por escrito, antes de começar."
- 03 Criação. "Você acompanha cada etapa e testa tudo antes de ir ao ar."
- 04 Entrega. "Site e automações no ar, com domínio e acessos no seu nome. E a gente continua por perto."

**Dúvidas** (kicker "DÚVIDAS"; coluna estreita com perguntas que abrem)
Título: "O que perguntam antes de começar."
- "Meu cliente vai perceber que está falando com um robô?" "A automação responde o que é simples, como horário, preço e agenda, numa conversa natural. Quando a pergunta foge disso, ela avisa e passa para uma pessoa da sua equipe."
- "E se o cliente quiser falar com uma pessoa?" "Ele pede e é atendido. A conversa chega para você com tudo o que já foi dito, sem o cliente repetir nada."
- "O site e o domínio ficam no meu nome?" "Ficam. Domínio, hospedagem e acessos são registrados no seu nome desde o começo."
- "Vocês somem depois de entregar?" "Não. Depois da entrega a gente continua disponível para ajustes e dúvidas, pelo mesmo WhatsApp de sempre."
- "Quanto tempo leva?" "Depende do tamanho do projeto. O prazo vem escrito na proposta, antes de começar."
- "Preciso entender de tecnologia?" "Não. Você explica o seu negócio com as suas palavras e a gente cuida da parte técnica."

**Depoimentos:** fora por enquanto. Entram quando houver frases reais de clientes. A demonstração faz o papel de prova.

**Contato** (id "contato"; formulário sobre o quadro final do vídeo)
Título: "Conte onde o seu negócio perde tempo."
Texto: "A gente responde em até 24 horas com uma ideia do que dá para fazer."
Campos: Nome ("Seu nome") / WhatsApp ("(00) 00000-0000") / O que você precisa (opções: Site, Automação, Os dois) / Conte um pouco do seu negócio ("O que você faz e onde perde mais tempo"). Botão: "Enviar".
Sucesso: "Recebemos. A gente responde em até 24 horas."
Destino do formulário: a definir com o usuário na Fase 8.

**Rodapé:** marca (ponto com dois anéis) + "LEXORA · Sites e automações". Instagram, e-mail, "© 2026 Lexora". Contatos reais a confirmar.

**Microtexto da construção:** relógio marca "23:04" no ponto das 23h. Painel da demonstração vazio: "Toque numa pergunta. O que a automação faz aparece aqui." Fim da conversa: botão "Recomeçar conversa". Erros do formulário: "Falta o seu nome.", "Confira o WhatsApp, com DDD.", "Conte um pouco do seu negócio."

**Confirmado pelo usuário:** resposta em até 24 horas, domínio no nome do cliente, suporte depois da entrega, prazo e valor por escrito. Destino do formulário: por enquanto só de exemplo (mostra o agradecimento, não envia). Contatos do rodapé ainda são exemplos.

## 8. Camada vetorial

- **O anel (assinatura):** círculos SVG finos em `--accent` que se expandem e somem. Nascem no fim do hero (continuando os anéis da água), no ponto do kicker de cada seção quando ela entra, em cada resposta da demonstração e no hover do botão principal. No rodapé, dois anéis se desenham em volta de um ponto e formam a marca.
- **Relógio de 24 horas** em anel na seção do problema, com um ponto de luz girando em 60 segundos.
- **Linha do tempo** de Como funciona, traçada com o scroll, anel aceso em cada etapa.
- **Ambiente fixo:** névoa azul em deriva lenta (ciclo de 80 segundos) e grão fino.
- **Partículas em sussurro:** poucas gotinhas de luz descendo devagar em O problema e O que fazemos.
- **Movimento reduzido:** anéis no estado final, linha traçada, relógio parado, nenhum motor rodando.

## 9. Prompts (em inglês de propósito; os geradores rendem melhor assim)

**Quadro inicial** (Nano Banana Pro, 16:9, 2k):

```
A single glowing drop of cool ice-white light falling in the upper center of the frame, composed as the first moment of a motion that will follow it straight down into perfectly still water far below. The drop bisects the frame, dead center, equal distance from the left and right edges. Soft layered blue mist fills the entire frame edge to edge, deep blue-graphite and dark petrol blue, gently drifting, with depth receding into soft shadow across the left and right thirds. Both halves of the frame have an identical treatment: no objects, no structures, no bright highlights on either side. At the very bottom of the frame, the faint dark mirror of still water barely catches the glow of the drop. Lighting: the drop is the only light source, a quiet cold glow softly illuminating the mist around it; everything else in calm low-key blue. Palette: deep blue-graphite, dark petrol blue, cool ice-white light, faint pale silver in the mist. Calm, precise, quiet atmosphere. Cinematic, photorealistic, 16:9. No text, no logos, no lettering anywhere.
```

**Vídeo** (Kling 3.0 Pro, imagem para vídeo, 15 s, sem som):

```
One continuous shot, no cuts. A single glowing drop of cool ice-white light falls slowly straight down the center of the frame through soft drifting blue mist, and the camera descends with it at the same steady speed, so the drop stays near the center while the mist streams gently upward past the lens. The drop stays alive throughout: it trembles and stretches slightly as it falls, its glow pulsing softly. Around the fifth second the dark, perfectly still water surface rises into view below and the drop touches it dead center: a small, delicate crown of light splashes up, a few fine droplets hit the lens with a brief beat of soft blur, then clear. From the point of contact, thin luminous rings spread outward across the black mirror-like water. The camera settles low, just above the surface, and glides slowly forward as the rings travel calmly toward a distant horizon, where a sparse row of tiny floating points of light just above the waterline brighten one by one as each ring reaches them; no buildings, no structures. The scene stays alive: low mist drifting over the water, faint reflections shimmering. The shot ends at rest: a wide, calm, dark water surface fills the lower half of the frame with several wide, faint concentric rings slowly fading, a quiet row of small steady lights along the horizon, soft blue mist and a deep blue-graphite sky filling the upper half, everything nearly still. No text or lettering anywhere.
```

## 10. Engenharia

Blob transmitido com anel de carregamento (vídeo acima de 8 MB) e watchdog de 20 s, interpolação normalizada por dt, seeks travados, escritas de DOM por delta, faixas ritmadas com teste de flick, legibilidade em quatro camadas (variante de dois lados: scrim por coluna, faixa central livre), cinco portões do hero estático vivos com listeners, completo sem o vídeo, piso de qualidade de pipeline-scrub.md, padrão site-inteiro-animado. Encode com atenção a banding: névoa e água são gradientes suaves, então checar os quadros calmos.

**Otimização do scrub (depois do primeiro teste do usuário, que achou o vídeo travado):** o encode com `-g 8` e quadros B levava em média 137 ms por pulo. Troquei por 1600 de largura, todo quadro é quadro-chave, sem quadros B e decodificação leve (`-vf scale=1600:-2 -crf 22 -g 1 -keyint_min 1 -bf 0 -tune fastdecode`), com 9,9 MB e PSNR de 52 dB contra o bruto: 30 ms por pulo. O JavaScript pede só o centro de quadros inteiros e ignora pedidos para o quadro já exibido. Na página, o atraso médio do vídeo atrás do scroll caiu de 17 para 4 quadros.

Restrições de texto: nada de "premium", "luxo", "exclusivo", "para poucos", "vagas limitadas", "promoção", "barato", "o melhor", "garantido", nenhum ponto de exclamação. Movimento lento, nada pisca ou pula.

## 11. Gate de texto

Cada linha acima embarca ao pé da letra. Antes de alguém ver: zero travessões, zero palavras de estoque, zero palavras proibidas, zero exclamações, varredura de sinais de IA. O trio "Horário marcado. Orçamento enviado. Você só confere de manhã." e o par "Fora do horário. Todo mundo dormindo." são dispositivos de marca deliberados e ficam.
