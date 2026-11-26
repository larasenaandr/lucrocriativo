# LP · Imersão Lucro Criativo

Página estática: HTML, CSS e JS puro, sem build. É só publicar a pasta como está (o `index.html` fica na raiz).

## O que ajustar ao publicar no domínio da Koko
- No `index.html`, trocar `<meta name="robots" content="noindex,nofollow">` (está assim por ser prévia) pelo que a Koko usa em página de venda.
- `og:image` está como `img/og.png` (caminho relativo). Algumas redes pedem a URL completa: vale trocar pela URL final.
- A página não traz código de medição. Coloque no `<head>` o padrão da Koko (pixel 381066721735791, GA4 G-R3ZLJK2BQQ e o k.js), que só funciona em domínio koko.ag. O `venda.js` já manda o InitiateCheckout no clique de compra, pelo `koko.evento` ou pelo `fbq`, quando eles existem na página.

## Como a venda funciona (js/venda.js)
- Antes de 26/11 às 19h (Brasília), os botões dizem "Abre hoje às 19h", com contador. Às 19h viram "Quero meu ingresso por R$ 57" sozinhos. Depois de 16/01 às 10h, ficam como "Vendas encerradas".
- O horário vem do cabeçalho `Date` do servidor, não do relógio do aparelho.
- Os links `a[data-compra]` levam para checkout.koko.ag/lucro-criativo e repassam as UTMs e o fbclid. A origem fica guardada por 30 dias.
- O parâmetro `?agora=` (para simular horário) só funciona em netlify.app, localhost e arquivo local. No domínio final ele é ignorado.

Prévia: https://previa--lucro-criativo-previa.netlify.app
