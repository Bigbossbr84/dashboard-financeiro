# Dashboard Financeiro

Dashboard financeiro pessoal em **arquivo único** (`index.html`) — HTML/CSS/JS puro, roda no navegador (celular ou PC). Os dados ficam no `localStorage` do aparelho e, opcionalmente, sincronizam pelo **Google Drive** entre você e a Keli.

**🌐 No ar em:** <https://bigbossbr84.github.io/dashboard-financeiro/>

## Como rodar
Abra o `index.html` no navegador (duplo clique) ou rode um servidor local:
```
npx serve .
```
> A sincronização com o Google Drive **só funciona via URL `https://` (GitHub Pages)** — não funciona abrindo o arquivo direto (`file://`).

## Dados
- Os dados vivem no navegador (`localStorage`, chave `finance_dash_v2`).
- Sincronização opcional pelo Google Drive (arquivo `dashboard-financeiro-dados.json`).
- Backup/restore via JSON dentro do app (Configurações).
- Arquivos `*-dados.json` e `backup-financeiro-*.json` ficam **fora do Git** (ver `.gitignore`) por conterem dados pessoais.

## Recursos
- Visão geral (saldo total + **data da última atualização do saldo**), transações, cartões
- Contas a pagar recorrentes, projeções, categorização automática (subcategorias)
- Importação de extrato (CSV, OFX, colar texto de PDF — formato BR)
- Meus Gastos (gráfico por categoria), Planejamento (metas), responsável por lançamento
- Chat IA (Gemini/Claude — chave fica só no aparelho), OCR de saldo (Tesseract via CDN)
- **Sincronização Google Drive** (GIS OAuth) + compartilhar com a Keli como editora
- Layout responsivo (menu inferior no celular), backup/restore JSON, tema claro/escuro

---

## Sincronização entre celulares (Google OAuth)

O app já está publicado. Para você e a Keli verem os mesmos dados ao vivo, configure o Google uma vez:

### 1. Configurar o Google OAuth
1. Acesse <https://console.cloud.google.com/> → crie um projeto.
2. **APIs e serviços → Biblioteca →** ative a **Google Drive API**.
3. **Tela de consentimento OAuth →** tipo **Externo** → adicione seu e-mail e o da Keli em **Usuários de teste**.
4. **Credenciais → Criar credencial → ID do cliente OAuth → Aplicativo da Web.**
   - **Origens JavaScript autorizadas:** `https://bigbossbr84.github.io`  *(só isso, sem `/dashboard-financeiro`)*
5. Copie o **Client ID** (`...apps.googleusercontent.com`).

### 2. Conectar dentro do app
Abra <https://bigbossbr84.github.io/dashboard-financeiro/> → Configurações → Sincronização:
cole o **Client ID** → **Conectar Google** → marque **Sincronizar automaticamente** →
em **email da Keli** digite o Gmail dela → **Compartilhar**.
A Keli abre o mesmo link, cola o **mesmo Client ID**, conecta com o Gmail dela e os dados aparecem.

> **Dica:** ao abrir o app, clique em **Conectar Google** para baixar a versão mais recente
> (o login do Google expira a cada sessão, por segurança).

## Atualizar o app publicado
Depois de editar o `index.html`, basta `git push` — o GitHub Pages reconstrói sozinho em ~1 min.

## Roadmap
- [x] Data da última atualização do saldo (visível na Visão Geral e em Contas)
- [x] Sincronização automática via Google Drive (GIS OAuth)
- [x] Conciliação de contas a pagar com o extrato
- [x] Layout para celular (responsivo)
- [x] Publicado no GitHub Pages
