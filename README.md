# Desafio Técnico Backend - API de Gestão de Estoque

## Objetivo
O objetivo deste desafio é desenvolver uma API RESTful para gerenciar o estoque de produtos e suas movimentações (entradas e saídas). Queremos avaliar sua capacidade de estruturar o código, desenhar a modelagem do banco de dados e aplicar regras de negócio consistentes.

## Tecnologias Exigidas
* **Node.js** com **TypeScript**
* **Prisma ORM**
* Banco de Dados **PostgreSQL**
* **Express**

## Requisitos e Endpoints
A API deve permitir o gerenciamento de três entidades principais: **Categorias**, **Produtos** e **Movimentações**.

### 1. Categorias
* `POST /categorias`: Criar uma categoria.
* `GET /categorias`: Listar todas as categorias.
* `GET /categorias/:id`: Buscar uma categoria por ID.
* `PUT /categorias/:id`: Atualizar nome.
* `DELETE /categorias/:id`: Deletar categoria (*Regra: Não permitir exclusão se houver produtos vinculados*).

### 2. Produtos
* `POST /produtos`: Criar produto (*Regra: SKU deve ser único. O estoque inicial deve ser 0, não permitir enviar estoque pelo corpo da requisição*).
* `GET /produtos`: Listar produtos (Diferencial: adicionar paginação).
* `GET /produtos/:id`: Buscar produto por ID.
* `PUT /produtos/:id`: Atualizar dados (*Regra: Não permitir atualização manual do campo `quantidade_estoque` por aqui*).
* `DELETE /produtos/:id`: Deletar produto.

### 3. Movimentações
* `POST /movimentacoes`: Registrar entrada ou saída. (*Regra 1: Atualizar o estoque do produto. Regra 2: Bloquear saída se a quantidade for maior que o saldo em estoque*).
* `GET /movimentacoes`: Listar histórico.
* `GET /produtos/:id/movimentacoes`: Listar histórico de um produto específico.
* `DELETE /movimentacoes/:id`: Cancelar movimentação. (*Regra: Ao cancelar, o impacto no estoque do produto deve ser revertido*).

## Arquitetura e Injeção de Dependência
Esperamos que a aplicação siga uma separação clara de responsabilidades, seguindo conceitos da arquitetura em camadas.

## Entregáveis
Para que sua avaliação seja concluída, você deve fornecer os seguintes itens na sua entrega:
* **Código Fonte:** O repositório completo com a aplicação desenvolvida.
* **Tutorial de Utilização:** Instruções claras detalhando como utilizar o **Docker** para subir a aplicação e o banco de dados, além de como executar a API.
* **Relatório de Criação:** Um breve documento explicando as decisões de arquitetura, como desenhou as tabelas e os desafios encontrados.
* **Outros Dados Adicionais:** Coleções do Postman/Insomnia, scripts extras, ou qualquer outro material que auxilie na avaliação.

## Como será avaliado
1. **Arquitetura:** Respeito à estrutura solicitada.
2. **Modelagem de Dados (Prisma):** Avaliaremos a forma como você estruturou o `schema.prisma`, os tipos de dados escolhidos e como lidou com os relacionamentos entre as tabelas.
3. **Regras de Negócio:** Tratamento de erros, status HTTP corretos e consistência nos cálculos de estoque.
4. **Boas Práticas:** Uso correto do TypeScript, padronização e código limpo.
5. **Setup e Docker:** A clareza do tutorial entregue e o funcionamento correto dos containers da aplicação.
