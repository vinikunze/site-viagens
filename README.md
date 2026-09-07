# Cláudia Mesti Viagens — Landing Page

Landing page de assessoria de viagem premium. Arquivo único (`index.html`), sem
build, sem dependências de JavaScript de terceiros: basta hospedar.

---

## ⚠️ Antes de publicar — 3 itens obrigatórios

| # | O que | Onde |
|---|-------|------|
| 1 | **Número do WhatsApp** | `index.html` → bloco `CONFIG` no início do `<script>`. Troque `5566999999999` pelo número real (formato `55` + DDD + número). Um só lugar atualiza **todos** os botões do site. |
| 2 | **Foto da Cláudia** | Salve como `assets/claudia.jpg` (recomendado 880×1100px, proporção 4:5). Enquanto o arquivo não existir, aparece um monograma elegante — nunca uma imagem quebrada. |
| 3 | **Domínio** | `index.html` → trocar `https://claudiamestiviagens.com.br/` nas tags `canonical`, `og:url` e no bloco de dados estruturados. |

### Itens opcionais
- `assets/og-cover.jpg` (1200×630px) — imagem exibida ao compartilhar o link no WhatsApp/Instagram.
- `assets/apple-touch-icon.png` (180×180px) — ícone ao salvar na tela inicial do iPhone.
- **Widget do Instagram (Elfsight):** o `<script>` do Elfsight no final do arquivo é
  opcional. Se a conta não estiver configurada, o widget simplesmente não aparece e a
  galeria estática abaixo dele garante a seção. Para remover, apague a última tag
  `<script src="https://elfsightcdn.com/platform.js">` e a `<div class="ig__embed ...">`.

---

## Como publicar

Qualquer hospedagem estática serve. As mais simples:

- **Netlify / Vercel:** arraste a pasta do projeto na interface — publica em segundos.
- **GitHub Pages:** Settings → Pages → Branch `main` → `/root`.
- **Hospedagem tradicional (cPanel/FTP):** envie `index.html` e a pasta `assets/`
  para a raiz (`public_html`).

### Rodar localmente
```bash
npx http-server . -p 8080
# abre http://localhost:8080
```

---

## O que foi implementado

**Conversão**
- CTA principal acima da dobra em todas as resoluções testadas (1440×900, 1280×720, 820×1180, 390×844, 360×640).
- CTA flutuante de WhatsApp que aparece após a primeira dobra e **se esconde** sobre a
  seção de preço, para não competir com o botão principal.
- Prova social (46 países, depoimentos, contadores animados), quebra de objeções (casos
  reais + FAQ) e garantia explícita antes do preço.

**UI / UX**
- Design system com tokens (cores, tipografia fluida com `clamp()`, espaçamento, curvas de animação).
- Tipografia editorial: Cormorant Garamond (display) + Inter (interface).
- Animações de entrada por `IntersectionObserver`, barra de progresso de leitura,
  linha da timeline que preenche conforme a rolagem, parallax sutil na colagem do hero
  (apenas mouse, apenas desktop), céu estrelado em `<canvas>`.
- Ícones em SVG vetorial (sprite `<symbol>`) — nítidos em qualquer tela, zero requisições.

**Mobile (pensado separadamente, não apenas adaptado)**
- Menu em painel de tela cheia com entrada escalonada, trava de rolagem, fechamento por
  ESC / clique no link / redimensionamento.
- Depoimentos viram carrossel com `scroll-snap` e indicadores de posição.
- "Como funciona" passa de 4 colunas para lista com número ao lado do texto.
- CTA flutuante vira barra larga; respeita `env(safe-area-inset-bottom)` no iPhone.
- Zero overflow horizontal em todos os breakpoints (verificado em navegador real).

**Performance**
- Um único laço de scroll com `requestAnimationFrame` (em vez de vários listeners).
- Canvas com `devicePixelRatio`, densidade proporcional à área e **pausa automática**
  quando o hero sai da tela ou a aba fica em segundo plano.
- Fontes carregadas sem bloquear a renderização; imagens com `width`/`height` (evita
  salto de layout), `loading="lazy"` e `fetchpriority="high"` nas duas do hero.

**Acessibilidade e SEO**
- Um único `<h1>`, hierarquia de títulos sem saltos, landmarks semânticos.
- Link "pular para o conteúdo", `:focus-visible` em tudo, FAQ com `aria-expanded` /
  `aria-controls` / `aria-labelledby` e navegação por teclado.
- Alvos de toque ≥ 24px, todas as imagens com `alt`, `rel="noopener"` nos links externos.
- Suporte a `prefers-reduced-motion` (desliga animações e o canvas) e a impressão.
- Meta tags completas, Open Graph, Twitter Card e dados estruturados JSON-LD
  (`TravelAgency`, `Person`, `Service`, `FAQPage`).

---

## Conteúdo a revisar com a cliente

Os textos abaixo vieram do material original e devem ser confirmados antes de publicar:

- **"12 anos de experiência"** e **"300+ viajantes assessorados"** — números do hero.
- **Preço R$ 1.997 / 12x** — confirmar valor e forma de pagamento.
- **Garantia de 100% em 2 sessões** — confirmar a política.
- **Depoimentos** (Ana Paula M., Mariana S., Juliana K.) — trocar pelos reais e, se
  possível, com foto e link para o perfil.
- **Casos reais** na seção "Por que você precisa disso" — são relatos genéricos de
  mercado; se forem histórias de clientes reais, vale nomear a fonte.
