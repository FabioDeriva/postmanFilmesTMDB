# 🎬 filminhosDaSilva — Testes de API com Postman

Collection de testes automatizados no Postman utilizando a API do [The Movie Database (TMDB)](https://www.themoviedb.org/).

## Sobre o Projeto

Projeto criado para praticar testes de API REST usando o Postman, explorando diversos endpoints do TMDB como busca de filmes, favoritos, elenco e classificação indicativa.

## Requests da Collection

| # | Request | Método | Descrição |
|---|---------|--------|-----------|
| 1 | GerarToken | `GET` | Gera um request token para autenticação |
| 2 | ValidarSession | `POST` | Cria uma session ID a partir do token aprovado |
| 3 | VerificarAccountID | `GET` | Obtém o Account ID do usuário |
| 4 | testeFilmesFavoritos | `GET` | Lista e testa filmes favoritos da conta |
| 5 | testeFilmeID | `GET` | Busca um filme por nome e retorna o ID |
| 6 | testeCaracteristicasFilme | `GET` | Verifica classificação indicativa e datas de lançamento |
| 7 | testesElencoFilme | `GET` | Testa elenco, diretor e equipe técnica |

## Tipos de Testes

- **Testes de status e estrutura** — Valida status code, formato JSON e campos obrigatórios
- **Testes de validação** — Verifica notas, datas, classificação indicativa e relevância de busca
- **Testes negativos** — Valida cenários que devem falhar (conteúdo adulto, dados inválidos)
- **Testes criativos** — Testes com mensagens personalizadas e cenários divertidos
- **Visualizações** — Respostas formatadas na aba Visualize do Postman

## Como Usar

### Pré-requisitos

- [Postman](https://www.postman.com/downloads/) instalado
- Uma conta no [TMDB](https://www.themoviedb.org/)
- Uma [API Key do TMDB](https://www.themoviedb.org/settings/api)

### Setup

1. Importe o arquivo `filminhosDaSilva_postman_collection.json` no Postman
2. Crie uma **Environment** chamada `TMDB` com as seguintes variáveis:

| Variável | Valor |
|----------|-------|
| `api_key` | Sua API Key do TMDB |
| `request_token` | *(preenchido automaticamente)* |
| `session_id` | *(preenchido automaticamente)* |
| `account_id` | *(preenchido automaticamente)* |
| `filme_nome` | Nome do filme que deseja buscar |
| `filme_id` | *(preenchido automaticamente)* |

3. Selecione a environment `TMDB` no dropdown do Postman

### Fluxo de Autenticação

1. Rode a request **GerarToken**
2. Copie o `request_token` da resposta
3. Abra no navegador: `https://www.themoviedb.org/authenticate/SEU_TOKEN`
4. Aprove o acesso
5. Rode **ValidarSession** imediatamente (o token expira rápido)
6. Rode **VerificarAccountID**
7. Pronto! As demais requests já funcionam

### Executando os Testes

- Rode cada request individualmente e confira os resultados na aba **Test Results**
- Use o **Console** (`Ctrl + Alt + C`) para ver logs detalhados
- Clique na aba **Visualize** para ver as respostas formatadas
- Use o **Collection Runner** para rodar todos os testes de uma vez

## Tecnologias

- [Postman](https://www.postman.com/)
- [TMDB API v3](https://developer.themoviedb.org/docs)

## Autor

Fábio
