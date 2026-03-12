# 🔧 Configuração de Redirect URLs no Clerk

## Problema Atual

Você está recebendo o erro:
```
ERR_UNKNOWN_URL_SCHEME
exp://10.0.10.157:8081/--/oauth-native-callback
```

Isso acontece porque o Clerk precisa saber para onde redirecionar após o login com Google.

## Solução: Configurar Redirect URLs no Clerk

### Passo 1: Acessar o Dashboard do Clerk

1. Acesse [dashboard.clerk.com](https://dashboard.clerk.com)
2. Faça login
3. Selecione sua aplicação **ReelAI**

### Passo 2: Configurar Allowed Redirect URLs

1. No menu lateral, clique em **"Configure"** ou **"Settings"**
2. Procure por **"Paths"** ou **"URLs and redirects"**
3. Encontre a seção **"Allowed redirect URLs"** ou **"OAuth redirect URIs"**

### Passo 3: Adicionar as URLs

Adicione as seguintes URLs (uma por linha):

```
exp://10.0.10.157:8081
exp://10.0.10.157:8081/--/oauth-native-callback
http://localhost:8081
http://localhost:8081/--/oauth-native-callback
```

> 💡 **Dica**: Substitua `10.0.10.157` pelo IP que aparece no seu QR code do Expo

### Passo 4: Configurar Allowed Origins (se houver)

Se houver uma seção **"Allowed origins"**, adicione:

```
exp://10.0.10.157:8081
http://localhost:8081
```

### Passo 5: Salvar

Clique em **"Save"** ou **"Update"**

---

## Alternativa: Usar Expo Dev Client (Recomendado para Produção)

Se o problema persistir, você pode usar o Expo Dev Client ao invés do Expo Go:

```bash
npx expo install expo-dev-client
npx expo prebuild
npx expo run:android
```

Mas por enquanto, tente primeiro configurar as URLs no Clerk!

---

## Verificação

Após configurar:

1. **Reinicie o servidor Expo**:
   ```bash
   # Ctrl+C para parar
   npx expo start --clear
   ```

2. **Recarregue o app** no Expo Go

3. **Tente fazer login** novamente

4. **Deve funcionar!** 🎉

---

## Troubleshooting

### Se ainda não funcionar:

1. **Verifique se salvou as configurações no Clerk**
2. **Confirme que o IP está correto** (olhe o QR code do Expo)
3. **Tente limpar o cache do Clerk**:
   - No dashboard do Clerk, procure por "Clear cache" ou "Reset"
4. **Reinicie completamente o Expo**

### Ainda com problemas?

Me envie:
- Screenshot da tela de configuração do Clerk (URLs)
- O IP que aparece no QR code do Expo
- Qualquer erro que aparecer no console
