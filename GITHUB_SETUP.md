# Guia: Publicar no GitHub

## Passo 1: Criar Repositório no GitHub

### 1.1 Fazer Login

Acesse [github.com](https://github.com) e faça login com sua conta.

Se não tiver conta, crie uma em [github.com/signup](https://github.com/signup)

### 1.2 Criar Novo Repositório

1. Clique no ícone **+** (canto superior direito)
2. Selecione **New repository**
3. Preencha:
   - **Repository name**: `geolocation-api-comparison` ou similar
   - **Description**: "Aplicação Expo que compara APIs de mapas (Google Maps, Mapbox, OpenStreetMap) com Supabase"
   - **Public** (recomendado para avaliação)
   - ✅ Marcar "Add a README file"
   - ✅ Marcar "Add .gitignore" (Node)
4. Clique em **Create repository**

---

## Passo 2: Conectar Repositório Local

### 2.1 Inicializar Git (Se ainda não tiver)

```bash
cd geolocation-app
git init
git add .
git commit -m "Initial commit: Geolocation app with maps API comparison"
```

### 2.2 Adicionar Remote

Copie o comando do GitHub (na página do novo repositório):

```bash
git branch -M main
git remote add origin https://github.com/seu-usuario/seu-repositorio.git
git push -u origin main
```

### 2.3 Autenticar (Se necessário)

Se usar HTTPS, será solicitada autenticação:
- **Username**: seu usuário GitHub
- **Password**: token de acesso (veja abaixo)

#### Criar Token de Acesso:

1. GitHub Settings → Developer settings → Personal access tokens
2. Clique em **Generate new token**
3. Nome: "Git CLI Access"
4. Escopo: ✅ repo
5. Copie o token
6. Use como senha no git

#### Ou usar SSH (Recomendado):

1. [Configurar SSH key](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh)
2. Usar URL: `git@github.com:seu-usuario/seu-repositorio.git`

---

## Passo 3: Estruturar o Repositório

### 3.1 Arquitetura Recomendada

```
geolocation-app/
├── src/
│   ├── components/
│   ├── hooks/
│   ├── screens/
│   ├── services/
│   └── types/
├── app/
├── assets/
├── docs/
│   ├── COMPARATIVO_APIS.md
│   ├── GUIA_SETUP.md
│   └── SCREENSHOTS.md (opcional)
├── .env.example
├── .gitignore
├── README.md
├── app.json
├── package.json
└── tsconfig.json
```

### 3.2 Atualizar README Principal

O README deve conter:
- Descrição do projeto
- Screenshots ou GIFs
- Como instalar e rodar
- Como usar as funcionalidades
- Comparativo das APIs (link para documento)
- Tecnologias utilizadas
- Licença

---

## Passo 4: Fazer Commit e Push

### 4.1 Adicionar Mudanças

```bash
git add .
git commit -m "feat: Complete geolocation app with APIs comparison"
```

### 4.2 Fazer Push

```bash
git push origin main
```

Verifique no GitHub se os arquivos foram enviados!

---

## Passo 5: Adicionar Detalhes ao Repositório

### 5.1 Descrição do Repositório

No repositório do GitHub:
1. Clique em **⚙️ Settings**
2. Em "About":
   - Adicione descrição breve
   - Adicione website (se houver)
   - Selecione tópicos: `expo`, `react-native`, `maps`, `supabase`, `geolocation`

### 5.2 Topics

Clique em **Add topics** e selecione:
- `expo`
- `react-native`
- `mobile-app`
- `maps`
- `geolocation`
- `supabase`
- `educational`

---

## Passo 6: Adicionar Documentação Adicional

### 6.1 Criar Pastas

```bash
mkdir docs
mkdir docs/screenshots
```

### 6.2 Criar Documentos

```bash
# Guia de Setup
docs/SETUP.md

# Comparativo de APIs
docs/COMPARATIVO_APIS.md

# Instruções de Deploy
docs/DEPLOY.md

# Documentação da API
docs/API.md
```

### 6.3 Adicionar ao Git

```bash
git add docs/
git commit -m "docs: Add comprehensive documentation"
git push origin main
```

---

## Passo 7: Criar Releases (Opcional)

### 7.1 Criar uma Release

1. No repositório, vá para **Releases**
2. Clique em **Create a new release**
3. Preencha:
   - **Tag version**: `v1.0.0`
   - **Release title**: `v1.0.0 - Initial Release`
   - **Description**: Descreva as features
4. Clique em **Publish release**

---

## Passo 8: Adicionar Badge ao README

No GitHub README, adicione badges para melhor apresentação:

```markdown
# Geolocation & Maps API Comparison

[![Expo](https://img.shields.io/badge/Expo-000.svg?style=for-the-badge&logo=expo&logoColor=white)](https://expo.dev)
[![React Native](https://img.shields.io/badge/React%20Native-61DAFB?style=for-the-badge&logo=react&logoColor=white)](https://reactnative.dev)
[![Supabase](https://img.shields.io/badge/Supabase-181818?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
```

---

## Passo 9: Configurar Issues e Discussions (Opcional)

### 9.1 Habilitar Discussions

1. Vá para **⚙️ Settings**
2. Em "Features", marque ✅ **Discussions**
3. Clique em **Discussions** e customize

### 9.2 Criar Template de Issue

1. Vá para **⚙️ Settings**
2. **Code and automation** → **Issue templates**
3. Clique em **Set up templates** → **Add template: Bug report**
4. Customize conforme necessário

---

## Passo 10: Proteger Main Branch (Opcional)

Para produção segura:

1. Vá para **⚙️ Settings**
2. **Code and automation** → **Branches**
3. Clique em **Add rule**
4. Padrão de branch: `main`
5. Requisitos:
   - ✅ Require pull request reviews before merging
   - ✅ Require status checks to pass
   - ✅ Require branches to be up to date

---

## Verificar Lista de Verificação

- ✅ Repositório criado no GitHub
- ✅ Código enviado (pushed)
- ✅ README.md atualizado
- ✅ .env.example adicionado (SEM SENHAS!)
- ✅ .gitignore configurado
- ✅ Documentação completa
- ✅ Topics adicionados
- ✅ README com badges

---

## Comandos Git Úteis

```bash
# Ver status
git status

# Ver histórico
git log --oneline

# Fazer mudanças
git add .
git commit -m "mensagem descritiva"
git push origin main

# Criar nova branch
git checkout -b feature/nova-feature
git push -u origin feature/nova-feature

# Deletar branch
git branch -D feature/antiga
git push origin -d feature/antiga

# Sincronizar com remote
git pull origin main
```

---

## Próximos Passos

1. ✅ Repositório no GitHub
2. Criar vídeo demonstrando a app
3. Escrever documento comparativo detalhado
4. Fazer deploy (Expo Snack ou Vercel)
5. Compartilhar com professores/colegas

---

## Recursos

- [GitHub Docs](https://docs.github.com/)
- [Pro Git Book](https://git-scm.com/book/pt-BR)
- [GitHub Skills](https://skills.github.com/)

Parabéns! Seu repositório está pronto! 🚀