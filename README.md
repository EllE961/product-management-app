<div align="center">

# product-management-app

**The first version of my product manager: a Vite 6 and React 19 scaffold that renders one centered "Hello World!" page.**

![javascript](https://img.shields.io/badge/javascript-vite%206-1f1d1b?style=flat-square&labelColor=0d0c0b)
![react](https://img.shields.io/badge/react-19.1-d95926?style=flat-square&labelColor=0d0c0b)
![eslint](https://img.shields.io/badge/eslint-9%20flat%20config-9085e9?style=flat-square&labelColor=0d0c0b)
![license](https://img.shields.io/badge/license-MIT-1f1d1b?style=flat-square&labelColor=0d0c0b)


</div>

This is where the product manager project started. I generated the official Vite React template, cut it down to a
single component and made the page fill the viewport, and stopped there. There is no routing, no product data and no
styling library yet.

[prodmanager](https://github.com/EllE961/prodmanager) is the newer, more complete version: about a week later I rebuilt
it on Create React App with React Router, React Bootstrap, a product table and a contact form. Go there for the
actual UI; this repo stays up as the starting point.

## Compared with prodmanager

| | product-management-app (this repo) | [prodmanager](https://github.com/EllE961/prodmanager) |
|---|---|---|
| First commit | 2025-05-22 | 2025-05-30 |
| Build tool | Vite 6.3 | Create React App (`react-scripts` 5) |
| React | 19.1 | 19.1 |
| Routing | none | React Router 7, three routes |
| UI library | none (two small CSS files) | React Bootstrap 2.10, Bootstrap Icons |
| Pages | one "Hello World!" heading | home, products table, contact form |
| Product data | none | two sample products in component state |

## How it works

```mermaid
flowchart LR
    html["index.html<br/>div#root"]:::a --> main["src/main.jsx<br/>createRoot · StrictMode"]:::a
    main --> app["src/App.jsx<br/>h1 Hello World!"]:::c
    main --> icss["index.css<br/>html · body · #root<br/>100% height"]:::b
    app --> acss["App.css<br/>flex centering"]:::b
    vite["Vite 6<br/>@vitejs/plugin-react"]:::d --> html
    vite --> dist["dist/<br/>production build"]:::d

    classDef a fill:#2a1710,stroke:#d95926,color:#ecebe6
    classDef b fill:#0f1d30,stroke:#3987e5,color:#ecebe6
    classDef c fill:#0c231b,stroke:#199e70,color:#ecebe6
    classDef d fill:#1c1a33,stroke:#9085e9,color:#ecebe6
```

`index.html` loads `src/main.jsx` as an ES module, which mounts `<App />` into `#root` inside `StrictMode`. The only
layout work is in CSS: `index.css` sets `html`, `body` and `#root` to full height with no margin, and `App.css` makes
the container a flexbox that centers the heading on both axes. Vite serves it with hot reload through
`@vitejs/plugin-react`, and ESLint 9 uses the template's flat config with the React Hooks and React Refresh plugins.

## Quickstart

```bash
git clone https://github.com/EllE961/product-management-app.git
cd product-management-app
npm ci
npm run dev      # dev server on http://localhost:5173
npm run build    # production build in dist/
npm run lint
```

On my machine (Node 22) the build transformed 30 modules into a 187.4 kB JavaScript bundle (58.9 kB gzip) in under a
second, and `npm run lint` reported no problems.

## Repository map

```text
index.html          page shell, loads src/main.jsx
src/
  main.jsx          mounts <App /> in StrictMode
  App.jsx           the Hello World! component
  App.css           flex centering for the container
  index.css         full-height html, body and #root
  assets/react.svg  template logo, no longer imported
public/vite.svg     favicon
vite.config.js      React plugin
eslint.config.js    ESLint 9 flat config from the template
docs/assets/        screenshot used in this README
```

## License

MIT, see [LICENSE](LICENSE).
