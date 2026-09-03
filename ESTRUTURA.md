# Estrutura do HUC CRM

```text
HUC-CRM/
├── .github/
│   └── workflows/
│       └── quality.yml
├── .openai/
│   └── hosting.json
├── app/
│   ├── api/admin/
│   │   ├── collaborators/route.ts
│   │   └── leads/route.ts
│   ├── chatgpt-auth.ts
│   ├── crm-dashboard.tsx
│   ├── crm.css
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
├── build/
│   └── sites-vite-plugin.ts
├── components/ui/
│   └── componentes da interface
├── docs/
│   ├── CONFIGURACAO.md
│   ├── ESTRUTURA.md
│   └── hucstudios-integration/
│       ├── app/api/leads/
│       ├── app/api/crm/
│       ├── db/
│       ├── drizzle/
│       └── lib/
├── examples/d1/
├── hooks/
├── lib/
│   ├── admin-auth.ts
│   ├── huc-api.ts
│   └── utils.ts
├── public/
├── scripts/
├── tests/
├── vendor/
├── worker/
│   └── index.ts
├── .env.example
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
└── vite.config.ts
```

## Como os dados circulam

1. O visitante envia o formulário no site público.
2. `POST /api/leads` valida e grava o contato no banco D1.
3. O CRM chama suas APIs internas em `app/api/admin/`.
4. Essas APIs confirmam o usuário conectado e consultam o site público com o token de serviço.
5. O painel permite acompanhar, atribuir, validar e atualizar o lead.

## Onde alterar cada área

| Necessidade | Arquivo ou pasta |
| --- | --- |
| Tela, filtros e equipe | `app/crm-dashboard.tsx` |
| Estilos do CRM | `app/crm.css` |
| Usuários fixos e permissões | `lib/admin-auth.ts` |
| Endereço do site e token | `lib/huc-api.ts` |
| APIs protegidas do CRM | `app/api/admin/` |
| Estrutura do banco | `docs/hucstudios-integration/db/schema.ts` |
| Regras de qualidade do lead | `docs/hucstudios-integration/app/api/leads/route.ts` |
| Colaboradores dinâmicos | `docs/hucstudios-integration/app/api/crm/collaborators/route.ts` |

