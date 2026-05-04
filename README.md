# BiMaster Vendor Manager

Plataforma de gestão Amazon Vendor — sistema interno BiMaster.

## 🌐 Acesso ao sistema

A versão hospedada está disponível em: **https://[seu-usuario].github.io/bimaster-vendor-manager/**

(URL será atualizada após primeiro deploy)

## 📋 Sobre

Sistema profissional para gestão de operações Amazon Vendor:
- Pedidos de Compra (POs) e seu fluxo completo
- Agendamentos e incidentes operacionais
- Catálogo de produtos com performance comercial
- Forecast e estratégia de reposição
- Movimentação financeira
- Comunicação interna entre equipes

**Cliente piloto:** Dahuer Cosméticos (1.452 POs, 218 SKUs, dados auditados).

## 🛠️ Tecnologias

- HTML / CSS / JavaScript vanilla (sem build step necessário)
- Chart.js 4 para visualizações
- Supabase JS para autenticação (modo opcional)
- LocalStorage para persistência client-side
- Single-file architecture — todo o sistema em `index.html`

## 🚀 Como rodar localmente

Não precisa instalar nada. Basta abrir o `index.html` no browser:

```bash
# Opção 1: abrir direto
open index.html

# Opção 2: servidor local simples (recomendado para teste de Auth real)
python3 -m http.server 8000
# Depois abrir: http://localhost:8000
```

## ⚙️ Configuração

No início do `index.html` há o objeto `BIMASTER_CONFIG`:

```js
window.BIMASTER_CONFIG = {
  dataMode: 'local',     // 'local' (dados embutidos) ou 'api' (Supabase)
  apiUrl: '',            // URL do projeto Supabase (apenas modo api)
  apiKey: '',            // anon key do Supabase
  auth: { enabled: false }, // ativar magic link via Supabase Auth
  cache: { enabled: true, ttl: 60000, storage: 'localStorage' },
  vendor: { current: 'dahuer' }
};
```

## 📂 Estrutura

```
bimaster-vendor-manager/
├── index.html       ← sistema completo (single-file)
├── README.md        ← este arquivo
├── .gitignore
└── docs/            ← documentação
    ├── MANUAL_USUARIO.md
    ├── MANUAL_OPERADOR.md
    └── FAQ.md
```

## 🔐 Acesso de teste

**Login de demonstração** (modo local):
- Email: qualquer (`admin@dahuer.com.br`, `op@bimaster.com.br`, etc)
- Senha: qualquer

**Login real** (se modo API ativado):
- Magic link enviado via Supabase Auth para o email cadastrado.

## 📞 Suporte

Equipe BiMaster — suporte interno.

---

© 2026 BiMaster Tecnologia. Todos os direitos reservados.
