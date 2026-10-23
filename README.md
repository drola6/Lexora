# LEXORA

Site da Lexora (sites e automações), com abertura em vídeo que avança e volta junto com o scroll: uma gota de luz cai na água e os anéis se espalham até o horizonte.

- `index.html` + `assets/`: o site, na raiz do repositório (é o que a Vercel publica). HTML, CSS e JavaScript puros, sem build.
- `pacote-de-design.md`: as decisões de design e todos os textos do site.

## Ver no computador

Abra um servidor local na raiz do repositório e acesse o endereço que ele mostrar:

```
npx http-server .
```

Abrir o `index.html` com dois cliques também funciona, mas mostra só a abertura parada (o navegador bloqueia o vídeo fora de um servidor). Celulares e quem usa movimento reduzido também veem a abertura parada, de propósito.

## Antes de publicar

Os projetos e o Instagram e o e-mail do rodapé ainda são exemplos. O formulário de contato mostra a mensagem de recebido, mas ainda não envia para lugar nenhum. O questionário que abre nos botões "Quero conversar" também só mostra o resumo na tela: para as respostas chegarem no WhatsApp, coloque o número da Lexora em `LEXORA_WHATS`, no script do `index.html`. A seção de depoimentos volta quando houver frases reais de clientes.
