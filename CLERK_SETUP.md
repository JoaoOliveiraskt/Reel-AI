# Configuração do Clerk para ReelAI

Este guia vai te ajudar a configurar o Clerk e habilitar autenticação com Google OAuth.

## Passo 1: Criar Conta no Clerk

1. Acesse [clerk.com](https://clerk.com)
2. Clique em **"Start building for free"**
3. Crie sua conta (pode usar Google para facilitar)

## Passo 2: Criar Nova Aplicação

1. Após fazer login, clique em **"Create application"**
2. Dê um nome para sua aplicação: **"ReelAI"**
3. Em **"How will your users sign in?"**, selecione apenas:
   - ✅ **Google**
4. Clique em **"Create application"**

## Passo 3: Configurar Google OAuth

### 3.1 Obter Credenciais do Google

1. No dashboard do Clerk, você verá um aviso para configurar o Google OAuth
2. Clique em **"Configure"** ao lado de Google
3. Siga as instruções para criar um projeto no Google Cloud Console:
   - Acesse [Google Cloud Console](https://console.cloud.google.com)
   - Crie um novo projeto ou selecione um existente
   - Vá para **"APIs & Services" > "Credentials"**
   - Clique em **"Create Credentials" > "OAuth 2.0 Client ID"**
   - Configure a tela de consentimento se solicitado
   - Tipo de aplicação: **"Web application"**
   - Adicione os URIs de redirecionamento fornecidos pelo Clerk

### 3.2 Adicionar Credenciais no Clerk

1. Copie o **Client ID** e **Client Secret** do Google
2. Cole no formulário do Clerk
3. Clique em **"Save"**

## Passo 4: Obter Chaves da API

1. No dashboard do Clerk, vá para **"API Keys"** no menu lateral
2. Você verá duas chaves:
   - **Publishable key** (começa com `pk_test_...`)
   - **Secret key** (começa com `sk_test_...`)

## Passo 5: Configurar Variáveis de Ambiente

1. Abra o arquivo `.env` no projeto ReelAI
2. Adicione a chave pública do Clerk:

```env
RAPID_API_KEY=your_rapidapi_key_here
GEMINI_API_KEY=your_gemini_api_key_here
EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_sua_chave_aqui
```

> ⚠️ **IMPORTANTE**: Use apenas a **Publishable Key** (pk_test_...). Nunca adicione a Secret Key no código do app!

## Passo 6: Configurar URLs de Redirecionamento

1. No dashboard do Clerk, vá para **"Paths"**
2. Configure os seguintes caminhos:
   - **Sign-in path**: `/(auth)/sign-in`
   - **Sign-up path**: `/(auth)/sign-up`
   - **After sign-in**: `/(tabs)`
   - **After sign-up**: `/(tabs)`

## Passo 7: Testar a Aplicação

1. Reinicie o servidor Expo:
   ```bash
   # Pressione Ctrl+C no terminal onde o Expo está rodando
   npm start
   ```

2. Abra o app no Expo Go
3. Complete o onboarding
4. Você será redirecionado para a tela de login
5. Clique em **"Continue with Google"**
6. Faça login com sua conta Google
7. Você será redirecionado para a home do app!

## Troubleshooting

### Erro: "Missing Publishable Key"
- Verifique se você adicionou `EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY` no arquivo `.env`
- Reinicie o servidor Expo após adicionar a variável

### Erro no OAuth do Google
- Verifique se os URIs de redirecionamento estão corretos no Google Cloud Console
- Certifique-se de que o Google OAuth está habilitado no Clerk

### App não redireciona após login
- Verifique se os paths estão configurados corretamente no Clerk
- Limpe o cache do Expo: `npx expo start -c`

## Recursos Adicionais

- [Documentação do Clerk](https://clerk.com/docs)
- [Clerk + Expo Guide](https://clerk.com/docs/quickstarts/expo)
- [Google OAuth Setup](https://clerk.com/docs/authentication/social-connections/google)
