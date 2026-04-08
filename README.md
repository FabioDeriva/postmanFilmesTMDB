# 🎬 filminhosDaSilva — Testes de API com Postman

Collection de testes automatizados no Postman utilizando a API do [The Movie Database (TMDB)](https://www.themoviedb.org/).

## Sobre o Projeto

Projeto criado para praticar testes de API REST usando o Postman, explorando diversos endpoints do TMDB como autenticação, busca de filmes, favoritos, classificação indicativa, elenco, segurança e validação de limites.

## Estrutura da Collection

### Requests Principais

| # | Request | Método | Descrição |
|---|---------|--------|-----------|
| 1 | GerarToken | `GET` | Gera um request token para autenticação |
| 2 | ValidarSession | `POST` | Cria uma session ID a partir do token aprovado |
| 3 | VerificarAccountID | `GET` | Obtém o Account ID do usuário |
| 4 | testeFilmesFavoritos | `GET` | Lista e testa filmes favoritos da conta |
| 5 | testeFilmeID | `GET` | Busca um filme por nome e retorna o ID |
| 6 | testeCaracteristicasFilme | `GET` | Verifica classificação indicativa e datas de lançamento |
| 7 | testesElencoFilme | `GET` | Testa elenco, diretor e equipe técnica |

### Testes de Segurança e Acesso

| # | Request | Método | Descrição |
|---|---------|--------|-----------|
| 8 | testesDeAcesso | `GET` | Acesso sem API Key (espera 401) |
| 9 | testeInjectNoToken | `POST` | Envio de dados sem sessão válida |
| 10 | testeSQLInjection | `GET` | Injeção SQL no campo de busca |
| 11 | testeIDOR | `GET` | Tentativa de adicionar item em lista alheia |

### Testes de Limites

| # | Request | Método | Descrição |
|---|---------|--------|-----------|
| 12 | testePaginacao | `GET` | Paginação acima do limite (page=1000) |
| 13 | testeIdGigante | `GET` | ID inexistente (99999999999) |
| 14 | testeDadoVazio | `GET` | Busca com query vazia |

### Testes Inválidos (Pasta)

| # | Request | Método | Descrição |
|---|---------|--------|-----------|
| 15 | testeDeleteTrendingContent | `DELETE` | DELETE em endpoint somente-leitura |
| 16 | testeDeleteVideos | `DELETE` | DELETE em vídeos de TV |
| 17 | testeDeleteDetalhes | `DELETE` | DELETE em detalhes de TV |
| 18 | testeDeletarFotoPerfil | `DELETE` | DELETE em foto de perfil |
| 19 | testeDeletarUsuário | `DELETE` | DELETE em usuário |
| 20 | testeDeletarAvaliacaoAleatoria | `DELETE` | DELETE em avaliação inexistente |
| 21 | testePostTrending | `POST` | POST em trending |
| 22 | testePostVideo | `POST` | POST em vídeos de TV |
| 23 | testePostUsuario | `POST` | POST em usuário |
| 24 | testePostFotoPerfil | `POST` | POST em foto de perfil |
| 25 | testePostAvaliacaoAleatoria | `POST` | POST em avaliação aleatória |

## Tipos de Testes

- **Funcional** — Valida o comportamento esperado dos endpoints
- **Estrutural** — Verifica a estrutura JSON das respostas (campos, tipos, arrays)
- **Negativo** — Testa cenários de erro: dados ausentes, IDs inválidos, métodos não permitidos
- **Segurança** — SQL Injection, IDOR, acesso sem autenticação, injeção de dados
- **Validação** — Confere regras de negócio: notas, datas, classificações
- **Exploratório** — Cenários com valores inesperados para verificar robustez da API

## Como Usar

### Pré-requisitos

- [Postman](https://www.postman.com/downloads/) instalado
- Uma conta no [TMDB](https://www.themoviedb.org/)
- Uma [API Key do TMDB](https://www.themoviedb.org/settings/api)

### Setup

1. Importe o arquivo `FilmesPostmanFabio.json` no Postman
2. Importe o arquivo `TMDB_postman_environment.json` como Environment
3. Na environment `TMDB`, preencha o valor de `api_key` com sua chave
4. Selecione a environment `TMDB` no dropdown do Postman

### Variáveis de Ambiente

| Variável | Valor | Preenchimento |
|----------|-------|---------------|
| `api_key` | Sua API Key do TMDB | Manual |
| `request_token` | Token temporário | Automático |
| `session_id` | ID de sessão | Automático |
| `account_id` | ID da conta | Automático |
| `filme_nome` | Nome do filme para busca | Manual |
| `filme_id` | ID do filme retornado | Automático |

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
- Use o **Collection Runner** para rodar múltiplos testes de uma vez

## Tecnologias

- [Postman](https://www.postman.com/) v12.5.3
- [TMDB API v3](https://developer.themoviedb.org/docs)
- Git + GitHub

## Uso de IA

Este projeto contou com o auxílio do modelo **Claude Opus 4.6** (Anthropic) para geração de scripts de teste, sugestão de cenários, estruturação do plano de testes e explicação de código. Todos os testes foram revisados, adaptados e validados manualmente pelos autores.

## Autores

- Fabio Miguel
- Henrique Campello
- Igor Araújo
