# slidev-vscode-conference-japan-2021

## live demo

SPA on [Netlify](https://loftkun-slidev-vscode-conference-japan-2021.netlify.app/)

## usage

```bash
git clone https://github.com/loftkun/slidev-vscode-conference-japan-2021.git
cd slidev-vscode-conference-japan-2021
npm install
npm run dev -- slides.md
```

Visit `http://localhost:3030/` and confirm the slides showed as SPA.

## publish SPA

```bash
# For GitHub Pages, require setting assets path on server with "--base" param.
npm run build -- --base slidev-vscode-conference-japan-2021/dist/
ls -Fla dist/
```