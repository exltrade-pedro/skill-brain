Para o **Antigravity**, o desenvolvimento com o conjunto Next.js, Vercel e Supabase exige uma abordagem focada em **reatividade em tempo real**, **segurança a nível de linha (RLS)** e uma experiência de usuário (UX) fluida com **Server Components**.

Abaixo está o detalhamento técnico dessa competência:

---

## 🛠️ Stack Skill: Full-stack Serverless (Next.js + Supabase)

### 1. Arquitetura Next.js (App Router)

Dominar a renderização híbrida é o coração de uma aplicação moderna no ecossistema Vercel.

- **React Server Components (RSC):** Buscar dados diretamente no lado do servidor com o Supabase Client, reduzindo o _bundle size_ no cliente e melhorando o SEO.
    
- **Streaming & Suspense:** Implementar carregamentos progressivos para interfaces de alta performance, garantindo que o usuário veja partes da página enquanto o restante dos dados é processado.
    
- **Server Actions:** Substituir rotas de API tradicionais por funções assíncronas no servidor para manipulação de formulários e mutações de dados.
    

### 2. Supabase como Backend-as-a-Service (BaaS)

O diferencial aqui é a integração profunda com o PostgreSQL e a camada de autenticação.

- **Row Level Security (RLS):** Configurar políticas de segurança granulares diretamente no banco de dados, garantindo que usuários só acessem ou modifiquem seus próprios dados.
    
- **Real-time Subscriptions:** Utilizar o protocolo de WebSockets do Supabase para refletir mudanças no banco de dados instantaneamente na UI (ideal para dashboards e chats).
    
- **Supabase Auth:** Implementar fluxos de autenticação (OAuth, Magic Links) integrados ao Middleware do Next.js para proteção de rotas.
    

### 3. Deploy e Infraestrutura na Vercel

A Vercel não é apenas hospedagem; é a camada de otimização da entrega.

- **Edge Runtime:** Executar funções o mais próximo possível do usuário final para reduzir a latência.
    
- **Incremental Static Regeneration (ISR):** Atualizar conteúdos estáticos sem necessidade de um novo build completo.
    
- **CI/CD & Preview Deployments:** Gerenciar múltiplos ambientes de staging integrados ao fluxo do GitHub.
    

---

## 🚀 Aplicação no Contexto Antigravity

Para projetos que buscam "desafiar a gravidade" (velocidade extrema e baixa fricção), o foco deve ser:

- **Type Safety Total:** Uso de **TypeScript** com a geração automática de tipos do Supabase CLI ($supabase\ gen\ types\ typescript$).
    
- **Caching Estratégico:** Uso inteligente do `fetch` cache do Next.js para evitar chamadas desnecessárias ao banco de dados.
    
- **Optimistic UI:** Atualizar a interface antes mesmo da confirmação do servidor para uma sensação de velocidade instantânea.
    

> **Dica Pro:** No Antigravity, evite o "clutter" de estados complexos no cliente. Deixe o banco de dados (Supabase) ser a fonte da verdade e o Next.js ser o condutor eficiente desses dados.