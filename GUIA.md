# Blog de recomendações — Guia

Como personalizar, publicar no GitHub Pages e manter o blog. HTML + CSS estático, sem custos.

---

## 1. Escolher um nicho

Antes de personalizar o conteúdo, decide um tema em que consigas criar artigos com consistência. Exemplos:

- **Tech** — gadgets, escritório em casa, reviews
- **Livros** — listas por género, "o que li este mês"
- **Casa** — organização, limpeza, decoração
- **Fitness / bem-estar** — equipamento, suplementos, roupa
- **Maternidade / bebés** — produtos essenciais, presentes
- **Descontos / ofertas** — "melhores compras", promoções

Edita o título e a tagline em `index.html` e adapta os títulos dos artigos em `artigos/*.html` ao teu nicho. Os links da Amazon já apontam para produtos reais (sem tag de afiliado); após aprovação, adiciona o teu tag a cada URL (ver secção 3).

---

## 2. Publicar no GitHub Pages (gratuito)

1. **Cria um repositório no GitHub**  
   - Vai a [github.com/new](https://github.com/new).  
   - Nome sugerido: `meu-blog-afiliados` ou `recomendacoes`.  
   - Pode ser público e sem descrição.

2. **Envia os ficheiros para o repositório**  
   No terminal, dentro da pasta do projeto:

   ```bash
   cd afiliados-amazon
   git init
   git add .
   git commit -m "Blog inicial"
   git branch -M main
   git remote add origin https://github.com/TEU_USERNAME/NOME_DO_REPO.git
   git push -u origin main
   ```

   (Substitui `TEU_USERNAME` e `NOME_DO_REPO` pelos teus dados.)

3. **Ativa o GitHub Pages**  
   - No repositório: **Settings** → **Pages**.  
   - Em **Source** escolhe **Deploy from a branch**.  
   - Branch: **main**, pasta **/ (root)**.  
   - Guarda. Em 1–2 minutos o site fica em:

   `https://TEU_USERNAME.github.io/NOME_DO_REPO/`

   Esse é o **URL do site**.

---

## 3. Links de afiliado (Amazon)

Se participares no programa de afiliados da Amazon:

1. **Escolhe o programa**  
   - Portugal/Espanha: [associados.amazon.es](https://associados.amazon.es)  
   - EUA: [affiliate-program.amazon.com](https://affiliate-program.amazon.com)

2. **No formulário**  
   - No campo **website / URL**, usa o URL do GitHub Pages, por exemplo:  
     `https://TEU_USERNAME.github.io/NOME_DO_REPO/`

3. **Depois de aprovado**  
   - Recebes um **tag de afiliado** (ex.: `meusite-21`).  
   - Para os links do site passarem a contar para comissão, adiciona `?tag=TEU_TAG` a cada URL de produto. Exemplo: `https://www.amazon.es/dp/B08N5WRWNW` → `https://www.amazon.es/dp/B08N5WRWNW?tag=meusite-21`.  
   - Podes fazer pesquisa e substituição em `artigos/*.html`: procurar `amazon.es/dp/` e acrescentar `?tag=TEU_TAG` antes do próximo `"` ou `target`.

---

## 4. Escrever conteúdo útil

- Cada ficheiro em `artigos/` é um artigo. Edita títulos e textos. Os links usam ASINs da Amazon.es; quando tiveres tag de afiliado, adiciona-o a cada link (secção 3).
- **Imagens:** As imagens dos produtos usam os **URLs da CDN da Amazon** (formato `m.media-amazon.com`). Se o pedido falhar (bloqueio, produto descontinuado), o `onerror` mostra o placeholder SVG. Para trocar uma imagem: abre a página do produto na Amazon, clica com o botão direito na imagem principal → "Copiar endereço da imagem" e cola no `src` do `<img>` no artigo.
- Mantém **reviews e listas** (melhores X, o que compro, presentes até X€). Inclui os links de forma natural no texto.
- Adiciona novos artigos: copia um `.html` existente em `artigos/`, renomeia e edita. Coloca o link no `index.html` na secção de listagem.

---

## 5. Divulgar sem gastar

- **Redes sociais** — partilha o link do blog na bio (Instagram, TikTok, etc.) e em stories/reels quando publicares um artigo novo.
- **Telegram / Facebook** — partilha em grupos relacionados ao teu nicho (respeitando as regras de cada grupo).
- **SEO básico** — títulos claros nos artigos e frases com palavras que as pessoas pesquisam (ex.: "melhores livros 2024", "presentes até 20 euros") ajudam a aparecer no Google.

---

## Estrutura do projeto

```
afiliados-amazon/
├── index.html          # Página inicial com lista de artigos
├── sobre.html          # Página Sobre
├── style.css           # Estilos (podes personalizar cores/fonte)
├── README.md           # Descrição do repositório
├── GUIA.md             # Este guia (instruções completas)
├── img/                # SVG de origem dos placeholders
└── artigos/
    ├── melhores-livros-2024.html
    ├── essenciais-casa.html
    ├── tech-escritorio.html
    ├── presentes-ate-20-euros.html
    ├── o-que-comprei-este-mes.html
    └── o-que-levar-em-viagem.html
```

Nenhum servidor nem base de dados: são só ficheiros HTML e CSS. O GitHub Pages serve tudo gratuitamente.

---

## Ver o site em local

Abre `index.html` no browser (duplo clique ou "Open with Live Server" no VS Code). Para pré-visualizar com servidor: na pasta do projeto: `python3 -m http.server 8000` e abre http://localhost:8000 no browser. No VS Code, a extensão Live Server também resolve.
