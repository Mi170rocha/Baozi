# Baozi Store — API REST

Trabalho de Desenvolvimento Web Back-End — API REST de uma pequena loja
que vende pão chinês (baozi), com controle de clientes, produtos e pedidos.

**Stack:** Java 17 · Spring Boot 4 · Spring Data JPA · H2 em memória ·
Maven Wrapper (não precisa instalar Maven).

## Como rodar

```bash
cd Baozi
./mvnw spring-boot:run
```

A API sobe em `http://localhost:8080`.
Console do banco H2: `http://localhost:8080/h2-console`
(JDBC URL `jdbc:h2:mem:baozidb`, usuário `sa`, senha em branco).

Rodar os testes:

```bash
./mvnw test
```

## Entidades e campos

| Entidade | Campos |
|---|---|
| Cliente | `id` (Long), `nome` (String), `clienteDesde` (LocalDate) |
| Produto | `id` (Long), `nome` (String), `preco` (BigDecimal), `estoque` (Boolean) |
| Pedido | `id` (Long), `clienteId` (Long), `produtoId` (Long), `quantidade` (Integer) |

Pacotes (MVC do Spring): `model`, `repository`, `controller`.

## Endpoints

| Método | URL | Ação |
|---|---|---|
| POST | `/api/clientes` | criar cliente |
| GET | `/api/clientes` | listar clientes |
| GET | `/api/clientes/{id}` | consultar cliente por ID |
| PUT | `/api/clientes/{id}` | atualizar cliente |
| DELETE | `/api/clientes/{id}` | apagar cliente |
| POST | `/api/produtos` | criar produto |
| GET | `/api/produtos` | listar produtos |
| GET | `/api/produtos/{id}` | consultar produto por ID |
| PUT | `/api/produtos/{id}` | atualizar produto |
| DELETE | `/api/produtos/{id}` | apagar produto |
| POST | `/api/pedidos` | criar pedido |
| GET | `/api/pedidos` | listar pedidos |
| GET | `/api/pedidos/{id}` | consultar pedido por ID |
| PUT | `/api/pedidos/{id}` | atualizar pedido |
| DELETE | `/api/pedidos/{id}` | apagar pedido |

Respostas: `200` (OK), `204` (apagado), `400` (validação),
`404` (ID inexistente).

## Exemplos de requisições

Criar cliente:

```json
POST /api/clientes
{ "nome": "Michele5557613", "clienteDesde": "2026-10-06" }
```

Criar produto:

```json
POST /api/produtos
{ "nome": "Baozi de Carne", "preco": 12.50, "estoque": true }
```

Criar pedido (5 unidades):

```json
POST /api/pedidos
{ "clienteId": 1, "produtoId": 1, "quantidade": 5 }
```

## Descrição do negócio

A Baozi Store é uma loja especializada na venda de pão chinês (baozi). O sistema disponibiliza uma API REST para gerenciamento do fluxo de atendimento, permitindo cadastrar clientes, gerenciar o catálogo de produtos com preço e controle de estoque, além de registrar pedidos associando clientes, produtos e quantidades solicitadas.
