---
name: nextjs-fullstack-developer
description: Desenvolve aplicações completas utilizando Next.js, integrando interfaces de alta performance (Frontend) com lógica de servidor escalável (Backend) no App Router.
stack: Next.js, React, Node.js, TypeScript
status: active
---

# 🚀 Next.js Full-stack Mastery

### 📋 Descrição Geral
Capacidade de construir aplicações web modernas que eliminam a barreira entre cliente e servidor. Esta skill foca na utilização do **App Router** para gerenciar estados, dados e interface em um único fluxo unificado, priorizando performance (Web Vitals) e segurança.

---

### 🛠️ Especificações Técnicas

#### 1. Frontend: Experiência e Performance
* **React Server Components (RSC):** Renderização de componentes no servidor por padrão para reduzir o bundle de JavaScript enviado ao navegador.
* **Client Components (Interatividade):** Uso estratégico de `'use client'` apenas onde a interatividade do usuário (hooks como `useState`, `useEffect`) é indispensável.
* **Layouts & Slots:** Arquitetura de interfaces complexas usando layouts aninhados e *Parallel Routes* para dashboards dinâmicos.
* **Otimização Nativa:** Implementação de `next/image` para imagens responsivas e `next/font` para eliminar Layout Shift (CLS).

#### 2. Backend: Lógica Serverless e APIs
* **Route Handlers:** Criação de APIs REST robustas dentro da pasta `app/api`, utilizando métodos HTTP (GET, POST, PATCH, DELETE) com suporte nativo a Edge Runtime.
* **Server Actions:** Execução de funções assíncronas no servidor chamadas diretamente de componentes de cliente, eliminando a necessidade de gerenciar fetchs manuais e endpoints de API para formulários.
* **Middleware:** Interceptação de requisições para validação de sessões, bots e redirecionamentos antes da renderização da página.
* **Data Fetching & Caching:** Domínio das funções `fetch` estendidas pelo Next.js para controle granular de cache e revalidação de dados (Tags e Path Revalidation).

---

### 💡 Padrões Antigravity

Para manter o código limpo e escalável, esta skill segue estas diretrizes:

* **Zod Validation:** Validação rigorosa de esquemas tanto no recebimento de dados via API quanto nas Server Actions.
* **Loading & Error States:** Uso de arquivos `loading.tsx` e `error.tsx` para fornecer feedback instantâneo ao usuário sem complexidade de estado manual.
* **SEO Dinâmico:** Geração de metadados dinâmicos e sitemaps baseados em dados do banco de dados (Supabase).

---

> **Conexão:** [[vercel-infrastructure-manager]] | [[supabase-backend-expert]]