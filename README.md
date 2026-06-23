# TecNews — Portal de Notícias

Projeto de estudos focado na prática de **CSS Grid**, desenvolvido como um portal de notícias de tecnologia fictício. O objetivo foi explorar na prática os principais recursos do Grid Layout, desde estruturas simples até padrões mais elaborados com áreas nomeadas, sobreposição de conteúdo e composição de seções assimétricas — incluindo a adaptação completa do layout para mobile e desktop.

## Tecnologias utilizadas

- **HTML5** — estrutura semântica com `<article>`, `<aside>`, `<figure>`, `<figcaption>` e `<nav>`
- **CSS3** — CSS Grid, nesting (`&`), media queries, variáveis customizadas, `aspect-ratio`, `object-fit`, pseudo-elementos e hover states
- **Design responsivo** — layout mobile-first com breakpoint único para desktop
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

O layout é **mobile-first**: por padrão, todas as seções seguem em uma única coluna. A partir do breakpoint `80em` (1280px), o `grid-template-areas` do `<main>` muda para duas colunas (`2fr 1.5fr`) em três linhas:

```
Mobile (< 80em)              Desktop (≥ 80em)
┌──────────────┐             ┌───────────────────────────┐
│   featured   │             │         featured          │  (span 2 colunas)
├──────────────┤             ├───────────────────────────┤
│    weekly    │             │          weekly           │  (span 2 colunas)
├──────────────┤             ├──────────────┬────────────┤
│      ai      │             │      ai      │   aside    │  (2fr | 1.5fr)
├──────────────┤             └──────────────┴────────────┘
│    aside     │
└──────────────┘
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

- **`grid-template-areas`** — definição semântica das regiões do layout, redefinida por breakpoint
- **`grid-template-columns`** com unidades `fr` e valores fixos (`rem`)
- **`grid-auto-flow: column`** — fluxo horizontal em listas de artigos (reorganizado em coluna no mobile)
- **`order`** — inversão da ordem de imagem/texto entre mobile e desktop na seção AI
- **`gap`** — espaçamento consistente entre células, em `rem`
- **`aspect-ratio`** — proporções uniformes para imagens (1:1, 16:9)
- **`object-fit: cover`** — preenchimento responsivo de imagens sem distorção

## Responsividade

- **Mobile-first**: estilos base pensados para telas pequenas, com um único breakpoint `@media (width >= 80em)` para desktop
- **Nesting CSS** (`&`) para escopar as regras de cada media query dentro do próprio seletor
- **Classes utilitárias `.mobile-only` / `.desktop-only`** para alternar textos completos (mobile) por versões truncadas (desktop) sem duplicar marcação via JS
- **Unidades relativas (`rem`)** no lugar de `px` para espaçamentos, larguras e tipografia
- **`overflow-x: scroll`** na navegação secundária do header em telas pequenas

## Outros destaques

- **Tema escuro** com paleta em tons de azul-ardósia (`#0F172A` de fundo, `#60A5FA` de destaque)
- **Variáveis CSS** (`--brand-color`, `--font-size-*`, etc.) para um sistema de design consistente
- **Gradiente sobre imagens** via pseudo-elemento `::before` para garantir legibilidade das legendas sobrepostas
- **Classes utilitárias** (`.grid`, `.grid-flow-col`, `.gap-*`) para reduzir repetição de código
- **Ícones com estado de hover** — setas com imagem de background alternada no `:hover`
