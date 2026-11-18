# Repositório das Letras — Livros

Microsserviço de **Livros** do sistema [Repositório das Letras](https://github.com/kauanysartor/Repositorio-das-Letras). O documento de requisitos e o descritivo técnico completo estão no repositório principal.

Gerencia o acervo: cadastro de livros e quantidade de exemplares.

## Endpoints

| Método | Rota               | Descrição          |
|--------|--------------------|--------------------|
| GET    | `/api/livros`      | Lista os livros    |
| GET    | `/api/livros/{id}` | Busca um livro     |
| POST   | `/api/livros`      | Cadastra um livro  |
| PUT    | `/api/livros/{id}` | Atualiza um livro  |
| DELETE | `/api/livros/{id}` | Exclui um livro    |

Documentação interativa (Scalar) em `/scalar`.

## Integrações

| # | Tipo                   | Quem chama                                                      | Rota                   |
|---|------------------------|-----------------------------------------------------------------|------------------------|
| 2 | Busca de dados simples | [Empréstimos](https://github.com/alexsanderantunesbarbosa/rdl-emprestimos) | `GET /api/livros/{id}` |

Ao registrar ou consultar um empréstimo, o serviço de Empréstimos busca o livro aqui para validar se há exemplar disponível.

## Configuração

| Variável                               | Descrição                                   | Padrão                  |
|----------------------------------------|---------------------------------------------|-------------------------|
| `ConnectionStrings__DefaultConnection` | Conexão com o banco SQLite                  | `Data Source=Livros.db` |
| `PORT`                                 | Porta informada ao Render (usar `8080`)     | —                       |

## Como executar localmente

```
cd AppTemplate
dotnet run
```

Acessar `http://localhost:5001/scalar`.

## Docker

```
docker build -t rdl-livros .
docker run -p 8080:8080 rdl-livros
```

## Outros microsserviços

- [Leitores](https://github.com/alexsanderantunesbarbosa/rdl-leitores)
- [Empréstimos](https://github.com/alexsanderantunesbarbosa/rdl-emprestimos)
- [Multas](https://github.com/alexsanderantunesbarbosa/rdl-multas)
