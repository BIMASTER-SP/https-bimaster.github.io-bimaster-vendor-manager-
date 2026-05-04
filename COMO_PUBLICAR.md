# 🚀 Guia: Subir BiMaster no GitHub e publicar online

**Objetivo:** ter URL profissional em 15-20 minutos.
**Custo:** R$ 0 (tudo grátis).
**Pré-requisito:** conta GitHub ativa.

---

## Caminho A — GitHub Pages (mais simples, sem CLI)

### Passo 1 — Criar o repositório (3 min)

1. Acesse https://github.com/new
2. Preencher:
   - **Repository name:** `bimaster-vendor-manager`
   - **Description:** `Plataforma de gestão Amazon Vendor — BiMaster`
   - **Visibility:** **Public** (necessário para GitHub Pages grátis)
   - ⚠️ **NÃO marcar** "Add README", "Add .gitignore" ou "Choose a license"
3. Clicar **Create repository**

GitHub mostra a tela "Quick setup" com um link tipo `https://github.com/SEU_USUARIO/bimaster-vendor-manager.git`. **Anote esse link**, você usa nos próximos passos.

### Passo 2 — Subir os arquivos (5 min)

**Opção A.1 — Via interface web (mais fácil, sem terminal):**

1. Na tela do repositório vazio, clicar em "**uploading an existing file**" (link no meio da página)
2. Arrastar para a página os 3 arquivos do pacote que vou te entregar:
   - `index.html`
   - `README.md`
   - `.gitignore`
3. No campo de commit message: `Versão inicial do sistema BiMaster v10`
4. Clicar **Commit changes**

**Opção A.2 — Via terminal (se você tem git instalado):**

```bash
# Descompactar o ZIP que vou te enviar
unzip bimaster_github_repo.zip
cd github_repo

# Inicializar git
git init
git add .
git commit -m "Versão inicial do sistema BiMaster v10"
git branch -M main

# Conectar com seu repositório (substitua o link)
git remote add origin https://github.com/SEU_USUARIO/bimaster-vendor-manager.git
git push -u origin main
```

### Passo 3 — Ativar GitHub Pages (2 min)

1. No repositório → **Settings** (aba superior)
2. Menu lateral → **Pages**
3. Em "Source", selecionar:
   - Branch: `main`
   - Folder: `/ (root)`
4. Clicar **Save**
5. Aguardar 1-2 minutos
6. URL aparece no topo: `https://SEU_USUARIO.github.io/bimaster-vendor-manager/`

### Passo 4 — Validar (5 min)

1. Acessar a URL acima
2. Tela de login do BiMaster Vendor Manager deve aparecer
3. Login: `admin@dahuer.com.br` / qualquer senha
4. Validar que o dashboard carrega com banner ROI verde
5. **Pronto.** Pode mandar a URL para o cliente.

---

## Caminho B — Vercel (URL mais profissional, deploy automático)

Se você quiser uma URL mais bonita (sem o `/bimaster-vendor-manager/` no path), use **Vercel** em vez de GitHub Pages:

### Pré-requisito: ter feito Passo 1 e 2 do Caminho A acima

### Passo 5 — Conectar Vercel ao GitHub (3 min)

1. Acessar https://vercel.com/signup
2. Login com GitHub (recomendado)
3. Click "**Add New** → **Project**"
4. Selecionar o repositório `bimaster-vendor-manager`
5. Vercel detecta automaticamente que é um site estático
6. Click **Deploy**
7. Em ~30 segundos: URL pronta tipo `bimaster-vendor-manager-xxxx.vercel.app`

### Vantagens do Vercel sobre GitHub Pages:
- URL mais limpa (sem `/bimaster-vendor-manager/` no path)
- Deploy automático a cada push no GitHub
- HTTPS já vem ativo (no Pages também)
- Mais rápido (CDN global)
- Suporte a domínio próprio gratuito

---

## ⚠️ Atenção: usar com Lovable

Se a ideia é abrir esse repositório no Lovable depois:

**O Lovable é uma plataforma de desenvolvimento de apps em React/Vite/TypeScript.** Quando você conectar este repo lá:

1. Lovable vai detectar que **não é** um projeto React (não tem `package.json`, `src/`, etc.)
2. Ele provavelmente vai sugerir reconstruir tudo em React — **isso vai mudar o sistema**
3. Pode quebrar funcionalidades como Chart.js, dados embutidos, lógica de cache
4. Vai consumir créditos do Lovable para "consertar"

**Recomendação:**
- Para **apresentação ao cliente agora**: use GitHub Pages ou Vercel (não passa pelo Lovable)
- Para **desenvolvimento futuro com IA assistente**: aí sim valeria considerar reconstruir em React, mas é projeto à parte

---

## 🆘 Problemas comuns

### "Página 404 no GitHub Pages"
- Aguardar 5 minutos após salvar (provisionamento demora)
- Conferir se o arquivo se chama `index.html` (case-sensitive)
- Conferir que o repositório é **Public**

### "Tela em branco ao abrir"
- Abrir DevTools (F12) → Console
- Procurar erros de carregamento de Chart.js (CDN bloqueado?)
- Tentar em outro browser

### "Não consigo logar"
- Modo local aceita qualquer email/senha (só validação de formato)
- Se ativou Auth real, precisa configurar Supabase antes (vide DEPLOY_README.md)

### "Repositório privado, GitHub Pages não funciona"
- GitHub Pages só funciona com repo **público** no plano grátis
- Para repo privado: usar Vercel (suporta privado no plano grátis)

---

## 🎯 Checklist final

Antes de mandar a URL para o cliente, conferir:

- [ ] URL abre sem erro 404
- [ ] Tela de login aparece com logo "BiMaster"
- [ ] Login com `admin@dahuer.com.br` funciona
- [ ] Dashboard carrega com banner ROI verde
- [ ] KPIs mostram números corretos (1.452 POs, fill rate 79,9%)
- [ ] Charts renderizam sem erros
- [ ] Sino de notificações tem badge "3"
- [ ] Cmd+K abre busca global

Se todos os checks passarem: **pode apresentar ao cliente.**
