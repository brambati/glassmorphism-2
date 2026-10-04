# Glassmorphism 2.0

Código do vídeo **"Glassmorphism 2.0"** do canal da [Digital Lift](https://digitallift.com.br).

Cards de vidro sobre fundo com blobs animados, com noise texture e hover com glow. **CSS puro, zero JavaScript.**

## Como rodar

Abra o `index.html` no navegador.

## As 3 propriedades do vidro

```css
.glass-card {
  backdrop-filter: blur(16px) saturate(180%);          /* 1. o blur do que está atrás */
  -webkit-backdrop-filter: blur(16px) saturate(180%);  /* Safari */
  background: rgba(255, 255, 255, 0.08);               /* 2. a camada de vidro */
  border: 1px solid rgba(255, 255, 255, 0.15);         /* 3. a borda luminosa */
}
```

**Sem um fundo colorido atrás, o efeito some.** O blur precisa de cores para borrar, e é para isso que servem os blobs com `radial-gradient` e o `hue-rotate` animado.

## O diferencial da versão 2.0: noise

Um `::before` com um SVG `feTurbulence` em `mix-blend-mode: overlay` e opacidade baixa (`0.15`). O resultado lembra vidro jateado de verdade. Passou muito disso, fica sujo.

## Detalhes

- **Hover:** mais blur (24px), mais opacidade (12%), glow roxo e `translateY(-4px)`
- **Transição do transform:** `cubic-bezier(0.34, 1.56, 0.64, 1)` dá uma leve elasticidade
- **Fallback:** o `@supports not (backdrop-filter…)` deixa o card mais opaco em navegadores sem suporte

## Suporte

O `backdrop-filter` funciona em todos os navegadores modernos: Chrome, Edge, Safari (com o prefixo `-webkit-`) e Firefox 103+.
