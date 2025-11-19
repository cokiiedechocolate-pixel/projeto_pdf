# Biblioteca Digital — Downloads de PDF/EPUB/MOBI

Página responsiva (HTML5, CSS3, JS) para listar livros com capas, buscar, filtrar por formato e baixar diretamente sem backend.

## Estrutura

- `index.html`: página principal com cabeçalho, busca, filtro e lista
- `assets/styles.css`: estilos responsivos, acessíveis e temas
- `assets/script.js`: carregamento dinâmico, filtros e downloads
- `books/books.json`: catálogo de livros (título, descrição, arquivos, capas)
- `books/pdf/*.pdf`: arquivos PDF
- `books/epub/*.epub`: arquivos EPUB
- `books/mobi/*.mobi`: arquivos MOBI
- `books/covers/*`: imagens de capa

## Como usar

1) Adicione seus arquivos nas pastas correspondentes (`books/pdf`, `books/epub`, `books/mobi`, `books/covers`).

2) Edite `books/books.json` e descreva seus livros. Exemplo com um único formato:

```json
[
  {
    "title": "Franz Kafka - O Processo",
    "description": "…",
    "filename": "O Processo - Franz Kafka.pdf",
    "url": "books/O Processo - Franz Kafka.pdf",
    "size": 111149056,
    "cover": "books/covers/o-processo.jpg",
    "format": "pdf",
    "files": { "pdf": "books/O Processo - Franz Kafka.pdf" }
  }
]
```

Exemplo com múltiplos formatos (PDF/EPUB/MOBI):

```json
[
  {
    "title": "Molly Knox Ostertag - O menino bruxa (Vol.1)",
    "description": "…",
    "filename": "O menino bruxa (Vol.1) Molly Knox Ostertag.pdf",
    "url": "books/pdf/O menino bruxa (Vol.1) Molly Knox Ostertag.pdf",
    "size": 16777216,
    "cover": "books/covers/o-menino-bruxa.webp",
    "files": {
      "pdf": "books/pdf/O menino bruxa (Vol.1) Molly Knox Ostertag.pdf",
      "epub": "books/epub/O menino bruxa (Vol. 1) - Molly Knox Ostertag_comp.epub",
      "mobi": "books/mobi/O menino bruxa (Vol.1) Molly Knox Ostertag.mobi"
    }
  }
]
```

3) Sirva a pasta `site/` com um servidor estático e acesse no navegador:

- `python -m http.server 8000` → abrir `http://localhost:8000/`
- ou `npx serve -l 5173` → abrir `http://localhost:5173/`

## Recursos

- Busca com debounce por título/descrição
- Filtro de formato: `Todos`, `PDF`, `EPUB`, `MOBI`
- Download direto via `fetch` com fallback por link
- Capas por imagem ou capa automática (SVG com inicial)
- “Ler mais” abre modal acessível para descrição completa
- Renderização incremental com botão “Carregar mais”
- Toast de feedback clicável e com tempo de auto-ocultação

## Acessibilidade

- Navegação por teclado e foco visível
- Modal com `role="dialog"`, `aria-modal="true"`, fechamento por `Esc`
- `aria-live` para mensagens e atualizações

## Dicas

- Se um livro não aparecer ao filtrar `EPUB/MOBI`, verifique `files.{epub|mobi}` em `books.json` ou a extensão de `url/filename`.
- Se a UI usar arquivos antigos em cache, faça um hard refresh (`Ctrl+F5`).

> Inicado em 11.11.2025