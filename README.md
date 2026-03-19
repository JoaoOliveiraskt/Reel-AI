# ReelAI 🎬

ReelAI é um aplicativo móvel desenvolvido como MVP (Minimum Viable Product) para o meu Trabalho Final de Curso. O objetivo é simplificar a descoberta de filmes e séries utilizando Inteligência Artificial Generativa para recomendações personalizadas e dados em tempo real sobre disponibilidade em serviços de streaming.

## 📱 Funcionalidades

- **Recomendações via IA**: Chat integrado com o Google Gemini (modelo `gemini-2.5-flash`) que atua como um especialista em cinema, sugerindo títulos com base no gosto do usuário, humor ou pedidos específicos.
- **Catálogo TMDB**: Integração com a API do TMDB para busca, populares, tendência, gêneros e detalhes de filmes.
- **Disponibilidade de Streaming**: Uso de `movie/{id}/watch/providers` do TMDB para mostrar onde assistir no Brasil.
- **Home com Seções**: Tela inicial com destaque e trilhas horizontais por categoria.
- **Busca Inteligente**: Pesquisa otimizada (com _debounce_) para encontrar filmes rapidamente sem sobrecarregar a rede.
- **Detalhes Completos**: Sinopse, elenco, ano de lançamento, gênero e links diretos para assistir.

## 🛠️ Tecnologias Utilizadas

Este projeto foi construído com uma stack moderna focada em performance e experiência do desenvolvedor:

- **React Native** (com Expo): Para desenvolvimento cross-platform (Android/iOS).
- **TypeScript**: Para tipagem estática e código mais seguro.
- **NativeWind** (Tailwind CSS): Para estilização rápida e responsiva.
- **Google Gemini API**: Motor de inteligência artificial para o chat.
- **TMDB API**: Fonte principal de catálogo de filmes e provedores de streaming.
- **Axios**: Cliente HTTP para requisições.
- **AsyncStorage**: Cache local para otimização de dados e economia de requisições.

## 🚀 Como Rodar o Projeto

### Pré-requisitos

- Node.js instalado.
- Token Bearer da API do TMDB.
- Chave de API do Google Gemini.

### Instalação

1.  Clone o repositório:

    ```bash
    git clone https://github.com/seu-usuario/reelai.git
    cd reelai
    ```

2.  Instale as dependências:

    ```bash
    npm install
    ```

3.  Configure as variáveis de ambiente:
    Crie um arquivo `.env` na raiz do projeto e adicione suas chaves:

    ```env
    EXPO_PUBLIC_TMDB_BEARER_TOKEN=seu_token_bearer_tmdb
    EXPO_PUBLIC_GEMINI_API_KEY=sua_chave_gemini
    EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY=sua_chave_clerk
    ```

4.  Execute o projeto:
    ```bash
    npx expo start
    ```

    - Use o aplicativo **Expo Go** no seu celular para escanear o QR Code.
    - Ou pressione `a` para rodar no emulador Android / `i` para simulador iOS.

## 📂 Estrutura do Projeto

- `app/`: Rotas e telas do aplicativo (Expo Router).
- `components/`: Componentes reutilizáveis de UI (Cards, Inputs, etc.).
- `services/`: Integrações com APIs externas (`api.ts`, `gemini.ts`).
- `scripts/`: Scripts utilitários para verificação e testes de API.
