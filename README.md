# Cláudia Mesti Viagens

Landing page da assessoria de viagem da Cláudia Mesti.

Arquivo único (`index.html`), sem build e sem bibliotecas de terceiros. Basta
hospedar.

## Antes de publicar

Três coisas precisam do dado real:

**1. Número do WhatsApp.** Está no bloco `CONFIG`, logo no começo do `<script>`
no fim do arquivo. Troque `5566999999999` pelo número da Cláudia no formato
`55` + DDD + número. Um lugar só atualiza todos os botões do site.

**2. Foto da Cláudia.** Salve na pasta `assets/` com o nome `claudia`. A
extensão pode ser `.jpg`, `.jpeg`, `.png` ou `.webp`, o site testa as quatro.
O quadro é quadrado, então o ideal é uma foto quadrada de pelo menos
900x900px. A foto atual tem 422x422px, que é o tamanho de foto de perfil do
Instagram e fica um pouco borrada em celular. Vale pedir o arquivo original
para a Cláudia. Sem esse arquivo aparece um monograma "CM" no lugar, nunca uma
imagem quebrada. Se o enquadramento cortar mal, ajuste `object-position` na
regra `.portrait__frame img`. Se a foto nova for vertical, troque
`aspect-ratio` para `4/5` na regra `.portrait__frame`.

**3. Domínio.** Trocar `https://claudiamestiviagens.com.br/` nas tags
`canonical`, `og:url` e no bloco de dados estruturados no topo do arquivo.

Opcionais: `assets/og-cover.jpg` (1200x630px, imagem que aparece quando o link é
compartilhado no WhatsApp) e `assets/apple-touch-icon.png` (180x180px, ícone ao
salvar na tela inicial do iPhone).

O widget do Instagram é da Elfsight, app `8de620c6-17ef-405f-a291-374c6bb15cc2`,
conectado à conta @claudiamestiviagens. Ele puxa os posts em tempo real.

Se o widget não carregar em 5 segundos, por queda de rede ou por estouro da cota
do plano, uma galeria de reserva aparece no lugar e a seção nunca fica vazia.
Atenção: o plano grátis da Elfsight tem limite de visualizações por mês. Quando
estourar, os visitantes passam a ver a galeria de reserva, que hoje usa fotos de
banco de imagem. Vale trocar essas quatro fotos por fotos reais da Cláudia (estão
no `index.html`, no bloco `id="igReserva"`).

Para trocar o widget, basta substituir o ID na classe `elfsight-app-...`. Para
tirar de vez, apague a última tag `<script src="https://elfsightcdn.com...">` e a
`<div class="ig__embed ...">`; a galeria de reserva assume sozinha.

## Publicar

Qualquer hospedagem estática serve:

* Netlify ou Vercel: arraste a pasta na interface.
* GitHub Pages: Settings, Pages, branch `main`, pasta `/root`.
* cPanel ou FTP: envie `index.html` e a pasta `assets/` para `public_html`.

Para rodar na sua máquina:

```
npx http-server . -p 8080
```

## Conteúdo a confirmar com a cliente

Estes dados vieram do material original e ninguém verificou:

* "12 anos de experiência" e "300+ viajantes assessorados", no topo da página.
* Preço de R$ 1.997 e o parcelamento em 12x.
* A garantia de devolução de 100% nas duas primeiras sessões.
* Os três depoimentos (Ana Paula M., Mariana S., Juliana K.). Se houver
  depoimentos reais, vale trocar, de preferência com foto e link do perfil.
* Os quatro casos da seção "Por que você precisa disso". São situações comuns
  do mercado, não relatos de clientes identificados.

## Estrutura

```
index.html          página inteira: HTML, CSS e JS
assets/             fotos (ver assets/README.md)
```

As seções do `index.html` estão separadas por comentários em caixa alta, na
ordem em que aparecem na página. O CSS começa com os tokens de cor, tipografia
e espaçamento, usados no arquivo todo.
