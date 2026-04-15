---
name: git-commit-formatter
description: Formata mensagens de commit seguindo a especificação Conventional Commits. Use para garantir um histórico rastreável e profissional no GitHub.
stack: Git
status: active
---
# 🚀 Skill: Git Conventional Commits & GitHub Standards

### 📋 Descrição Geral

Capacidade de aplicar convenções semânticas em mensagens de commit e manter um histórico de projeto limpo, rastreável e profissional. Foco no padrão **Conventional Commits** e fluxos de trabalho que facilitam o code review e a automação de _changelogs_.

---

### 🛠️ Especificações Técnicas

#### 1. Anatomia do Commit Semântico

As mensagens seguem a estrutura: `<tipo>(escopo): <descrição curta>`

- **Tipos Principais:**
    
    - `feat`: Uma nova funcionalidade (ex: `feat(auth): adiciona login com Supabase`).
        
    - `fix`: Correção de um bug (ex: `fix(api): corrige erro de permissão no Docker`).
        
    - `docs`: Alterações na documentação (ex: `docs(readme): atualiza guia de instalação do Arch`).
        
    - `style`: Alterações que não afetam o significado do código (espaços, formatação).
        
    - `refactor`: Alteração de código que não corrige bug nem adiciona funcionalidade.
        
    - `perf`: Mudança de código focada em performance.
        
    - `chore`: Atualização de tarefas de build, pacotes ou ferramentas (ex: `chore: atualiza dependências do Next.js`).
        

#### 2. Boas Práticas no GitHub

- **Mensagens Imperativas:** Escrever como se estivesse a dar uma ordem ao código (ex: "adiciona" em vez de "adicionado" ou "adicionando").
    
- **Escopo Opcional:** Utilizar parênteses para especificar a parte do sistema afetada (ex: `env`, `ui`, `database`).
    
- **Corpo do Commit:** Para mudanças complexas, usar o corpo da mensagem (após uma linha em branco) para explicar o **porquê** da mudança, não o **como**.
    

---

### ⚙️ Implementação no Arch Linux (Automação)

Para garantir que o Antigravity siga este padrão sem esforço manual, adicione estas ferramentas ao seu ambiente:

1. **Commitizen:** Interface de linha de comando que ajuda a gerar o commit correto.
    
    Bash
    
    ```
    # No Arch
    npm install -g commitizen cz-conventional-changelog
    echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
    ```
    
2. **Husky & Commitlint:** Impedir que commits fora do padrão sejam feitos no repositório.
    
3. **Alias no ZSH/Bash:** Adicione ao seu `.zshrc` para agilizar:
    
    Bash
    
    ```
    alias gc="git commit -m"
    alias gca="git add . && git commit -m"
    ```
    

---

### 💡 Diferencial Antigravity (Multi-Identity)

Como você gere identidades pessoais e da EXL Trade, a skill inclui a configuração correta de SSH e autor:

- **Identidade por Pasta:** No seu `.gitconfig`, use `includeIf` para trocar o e-mail automaticamente se estiver na pasta da empresa, garantindo que o commit apareça com o perfil correto no GitHub.
    
- **Assinatura GPG:** Ativar a verificação de commits ("Verified") para aumentar a autoridade do seu perfil profissional.
    

---
> **Nota de Conexão:** Esta skill é pré-requisito para o deploy eficiente na **Vercel** [[vercel-infrastructure-manager]], onde cada commit gera uma nova visualização de preview.
