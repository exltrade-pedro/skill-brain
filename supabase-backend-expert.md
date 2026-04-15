---
name: supabase-backend-expert
description: Arquiteta e gerencia infraestrutura de backend usando Supabase. Especialista em PostgreSQL, segurança via RLS e fluxos de autenticação robustos.
stack: Supabase, PostgreSQL, Auth, Realtime
status: active
---

# ⚡ Supabase & Database Architecture

### 📋 Descrição Geral
Capacidade de configurar e escalar um Backend-as-a-Service (BaaS) focado em performance e segurança. Esta skill abrange desde a modelagem de dados relacional no PostgreSQL até a implementação de políticas de acesso granulares e sistemas de autenticação modernos.

---

### 🛠️ Especificações Técnicas

#### 1. Autenticação & Autorização (Auth)
* **Estratégias de Login:** Implementação de fluxos variados (OAuth: Google/GitHub, Magic Links, e Usuário/Senha) integrados ao Next.js Auth Helpers.
* **Gestão de Sessões:** Uso de JWT (JSON Web Tokens) e Cookies seguros para persistência de login no lado do servidor (SSR).
* **Hooks de Auth:** Monitoramento de mudanças de estado de autenticação (`onAuthStateChange`) para sincronizar a UI em tempo real.
* **MFA (Multi-Factor Authentication):** Configuração de camadas extras de segurança para usuários administrativos.

#### 2. Segurança: Row Level Security (RLS)
* **Políticas de Acesso:** Escrita de políticas SQL que garantem que cada usuário acesse apenas seus próprios registros (ex: `auth.uid() = user_id`).
* **Service Role:** Uso correto da `SUPABASE_SERVICE_ROLE_KEY` apenas em ambientes de servidor seguros para bypass de RLS quando necessário.
* **Views e RPCs:** Criação de funções de banco de dados (Stored Procedures) para operações complexas que exigem performance atômica.

#### 3. Realtime & Edge Functions
* **Postgres Changes:** Subscrição em canais específicos para atualizar a interface do usuário instantaneamente quando um dado muda no banco.
* **Edge Functions (Deno):** Desenvolvimento de lógica de backend personalizada em TypeScript que roda próxima ao usuário para integrações com terceiros (ex: Stripe, Webhooks).
* **Storage:** Gestão de buckets para armazenamento de arquivos e imagens com políticas de acesso e otimização.

---

### 💡 Boas Práticas Antigravity

* **Database-First Security:** Nunca confiar apenas na validação do frontend; a segurança deve ser garantida no banco de dados via RLS.
* **Geração de Tipos (TypeScript):** Sincronizar o esquema do banco com o código para evitar erros de runtime:
    `npx supabase gen types typescript --project-id "id-do-projeto" > types/supabase.ts`
* **Migrations:** Uso do Supabase CLI para versionar o banco de dados, permitindo ambientes de desenvolvimento, staging e produção consistentes.
* **Soft Deletes:** Implementação de colunas `deleted_at` para evitar perda acidental de dados e manter integridade referencial.

---

> **Status:** Pronta para o Vault.
> **Conexão:** [[nextjs-fullstack-developer]] | [[vercel-infrastructure-manager]]