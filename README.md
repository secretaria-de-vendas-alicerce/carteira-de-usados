# Wrapper — Carteira de Usados (Alicerce)

Página que embute o web app do Apps Script num `<iframe credentialless>`, contornando o roteador
de conta `/u/N/` do Google (a falha "Não foi possível abrir o arquivo" em navegador com 2+ contas
Google logadas). **Este é o link que a equipe deve usar** — nunca a `/exec` direta.

- `index.html` — o wrapper (embute a `/exec` do deployment `@1`).
- `.nojekyll` — desliga o Jekyll no GitHub Pages.

Esta pasta é o ESPELHO da fonte (Regra 30): o repositório do Pages é montado fora do Drive
(Regra 7) a partir destes arquivos.

## Publicar (ainda NÃO publicado — 19/09/2026)

Repo previsto: **`secretaria-de-vendas-alicerce/carteira-de-usados`** (público; o wrapper só
carrega a `/exec`, e o app tem login próprio). URL da equipe, depois de publicado:
**`https://secretaria-de-vendas-alicerce.github.io/carteira-de-usados/`**

```bash
gh auth switch --user secretaria-de-vendas-alicerce   # a pessoal leva 403
# numa pasta FORA do Drive, com os arquivos desta:
git init -b main && git add -A && git commit -m "..."
gh repo create secretaria-de-vendas-alicerce/carteira-de-usados --public --source=. --remote=origin --push
gh api -X POST repos/secretaria-de-vendas-alicerce/carteira-de-usados/pages -f "source[branch]=main" -f "source[path]=/"
gh auth switch --user joaopcsn21-cmyk                 # devolver: o push do cephalon é da pessoal
```

Se a `/exec` mudar de `deploymentId`, atualizar o `src` do iframe **e** o `href` do fallback, e
conferir de fora: o id na lista do `clasp deployments` e GET (nunca `-I`) com 200 na `/exec`.
