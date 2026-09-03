# HUC CRM

CRM interno da HUC Studios, conectado ao formulário do site público sem aparecer dentro dele.

O projeto reúne painel de oportunidades, qualificação automática, detecção de possíveis duplicidades, filtros avançados, responsáveis, anotações, gestão de colaboradores e controle de acesso por função.

## Recursos

- Recebimento dos cadastros enviados pelo site da HUC Studios
- Funil com os status Novo, Em contato, Proposta enviada, Fechado e Arquivado
- Pontuação de qualidade de 0 a 100
- Validação como Qualificado, Revisar, Duplicado ou Descartado
- Pesquisa e filtros por responsável, plano, período, status e validação
- Ordenação por data, atualização e qualidade
- Cadastro, desativação e reativação de colaboradores
- Perfis Proprietário, Administrador e Atendimento
- Login com ChatGPT e autorização adicional por e-mail
- Comunicação protegida com o site público por token de serviço

## Estrutura principal

```text
app/                         páginas, painel e APIs internas
components/ui/               componentes visuais reutilizáveis
lib/                         autorização e comunicação com o site HUC
worker/                      entrada do Worker para publicação
public/                      ícones e arquivos públicos
tests/                       verificações automatizadas
docs/                        documentação e integração com o site público
.github/workflows/           validação automática no GitHub
.openai/hosting.json         configuração do projeto no ChatGPT Sites
```

Consulte [docs/ESTRUTURA.md](docs/ESTRUTURA.md) para a árvore detalhada e [docs/CONFIGURACAO.md](docs/CONFIGURACAO.md) para preparar o ambiente.

## Requisitos

- Node.js 22.13 ou superior
- npm
- A mesma chave `HUC_CRM_SERVICE_TOKEN` configurada no CRM e no site público
- Backend do site HUC Studios com as rotas descritas em `docs/hucstudios-integration/`

## Rodar localmente

1. Duplique `.env.example` como `.env.local`.
2. Coloque em `.env.local` o token usado para conectar o CRM ao site.
3. Execute `npm ci`.
4. Execute `npm run dev`.

## Verificações

```bash
npm run lint
npm test
```

## Segurança

- Nunca envie `.env.local` ou o token verdadeiro para o GitHub.
- Mantenha o repositório privado, pois a lista inicial de usuários autorizados faz parte do código.
- O token precisa ter no mínimo 32 caracteres e deve ser diferente de senhas pessoais.
- Adicionar alguém à lista de colaboradores do CRM não dá acesso ao código-fonte do repositório.

## Integração com o site público

O site público registra o lead e mantém o banco de dados. O CRM consulta e atualiza esses dados por rotas protegidas. Os arquivos necessários dessa integração estão documentados em [docs/hucstudios-integration/README.md](docs/hucstudios-integration/README.md).

## Site em produção

- CRM: https://huc-crm.herotx6.chatgpt.site
- Site público: https://hucstudios.herotx6.chatgpt.site

