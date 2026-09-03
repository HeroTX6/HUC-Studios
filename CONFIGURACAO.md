# Configuração

## 1. Clonar e instalar

```bash
git clone URL_DO_SEU_REPOSITORIO
cd HUC-CRM
npm ci
```

## 2. Criar a configuração local

Crie `.env.local` usando `.env.example` como referência:

```env
HUC_CRM_SERVICE_TOKEN=um_token_aleatorio_com_mais_de_32_caracteres
```

Não envie `.env.local` ao GitHub. Ele já está protegido pelo `.gitignore`.

## 3. Configurar a conexão

O mesmo valor de `HUC_CRM_SERVICE_TOKEN` deve existir:

- no ambiente do HUC CRM;
- no ambiente do site público HUC Studios.

Se os valores forem diferentes, o CRM abrirá, mas não conseguirá consultar os leads nem administrar colaboradores.

## 4. Usuários iniciais

Os usuários de recuperação estão em `lib/admin-auth.ts`. A integração do site mantém a lista equivalente em `docs/hucstudios-integration/lib/crm-members.ts`.

Depois do acesso inicial, proprietários e administradores podem cadastrar outros colaboradores pelo menu **Equipe**.

## 5. Executar

```bash
npm run dev
```

## 6. Conferir antes de publicar

```bash
npm run lint
npm test
```

## Observação importante

Este repositório contém o painel do CRM. O banco e as rotas que recebem os formulários ficam no site público. A pasta `docs/hucstudios-integration/` guarda uma cópia dos arquivos necessários para reproduzir essa conexão sem misturar a interface do CRM ao site público.

