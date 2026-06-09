# TecNews — Portal de Notícias

Projeto de estudos focado na prática de **CSS Grid**, desenvolvido como um portal de notícias de tecnologia fictício. O objetivo foi explorar na prática os principais recursos do Grid Layout, desde estruturas simples até padrões mais elaborados com áreas nomeadas, sobreposição de conteúdo e composição de seções assimétricas.

## Tecnologias utilizadas

- **HTML5** — estrutura semântica com `<article>`, `<aside>`, `<figure>`, `<figcaption>` e `<nav>`
- **CSS3** — CSS Grid, variáveis customizadas, `aspect-ratio`, `object-fit`, pseudo-elementos e hover states
- **Google Fonts** — fonte [Archivo](https://fonts.google.com/specimen/Archivo) com eixo de peso variável (100–900)

## Estrutura do projeto

```
portal-news/
├── index.html
├── assets/
│   ├── icons/          # SVGs (logo, menu, busca, setas)
│   ├── pictures/       # 18 imagens de artigos (PNG)
│   └── Ads.png         # Banner de anúncio
└── styles/
    ├── index.css       # Ponto de entrada (importa os demais)
    ├── global.css      # Variáveis, tipografia e reset base
    ├── header.css      # Navegação primária e secundária
    ├── sections.css    # Estilos específicos de cada seção
    └── utility.css     # Classes utilitárias de layout
```

## Layout

O layout principal é definido por um `grid-template-areas` com duas colunas (`2fr 1.5fr`) e três linhas:

```
┌───────────────────────────┐
│         featured          │  (span 2 colunas)
├───────────────────────────┤
│          weekly           │  (span 2 colunas)
├──────────────┬────────────┤
│      ai      │   aside    │  (2fr | 1.5fr)
└──────────────┴────────────┘
```

### Seções

| Seção | Descrição |
|---|---|
| **Header** | Dois níveis de navegação: identidade da marca + categorias |
| **Featured** | Destaque principal: 1 card grande + grid 2×2 com 4 notícias |
| **Weekly** | "Mais lidas da semana": 4 colunas de largura fixa (292px) |
| **AI Highlights** | 4 artigos alternados com imagem e texto em fluxo horizontal |
| **Aside** | Anúncio + seção "Você viu isso?" com 5 artigos em layout horizontal |

## Conceitos de CSS Grid praticados

- **`grid-template-areas`** — definição semântica das regiões do layout
- **`grid-template-columns`** com unidades `fr` e valores fixos (`px`)
- **`grid-auto-flow: column`** — fluxo horizontal em listas de artigos
- **`grid-column: span 2`** — células que ocupam múltiplas colunas
- **`gap`** — espaçamento consistente entre células (16px e 32px)
- **`aspect-ratio`** — proporções uniformes para imagens (1:1, 16:9)
- **`object-fit: cover`** — preenchimento responsivo de imagens sem distorção

## Outros destaques

- **Tema escuro** com paleta em tons de azul-ardósia (`#0F172A` de fundo, `#60A5FA` de destaque)
- **Variáveis CSS** (`--brand-color`, `--font-size-*`, etc.) para um sistema de design consistente
- **Gradiente sobre imagens** via pseudo-elemento `::before` para garantir legibilidade das legendas sobrepostas
- **Classes utilitárias** (`.grid`, `.grid-flow-col`, `.grid-cols-2`, `.gap-*`) para reduzir repetição de código
- **Ícones com estado de hover** — setas com imagem de background alternada no `:hover`
