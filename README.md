# Dashboard Financeiro

Dashboard financeiro pessoal em **arquivo único** (`index.html`) — HTML/CSS/JS puro, roda offline no navegador. Dados ficam no `localStorage` (chave `finance_dash_v2`), nunca em arquivo versionado.

## Como rodar
Abra o `index.html` no navegador (duplo clique) ou rode um servidor local:
```
npx serve .
```

## Dados
- Os dados vivem no navegador (`localStorage`).
- Backup/restore via JSON dentro do próprio app (Configurações).
- Arquivos `backup-financeiro-*.json` ficam **fora do Git** (ver `.gitignore`) por conterem dados pessoais.

## Recursos
- Visão geral (saldo, entradas, despesas), transações, cartões com fechamento/vencimento
- Contas a pagar recorrentes, projeções, categorização automática (subcategorias)
- Importação de extrato (CSV, OFX, colar texto de PDF — formato BR)
- Meus Gastos (gráfico por categoria), Planejamento (metas), responsável por lançamento
- Chat IA (Gemini/Claude — chave fica só no aparelho), OCR de saldo (Tesseract via CDN)
- Backup/restore JSON, tema claro/escuro (dark neon OLED)

## Roadmap
- [ ] Sincronização automática via Google Drive (GIS OAuth)
- [ ] Publicar no GitHub Pages (servir `index.html`)
