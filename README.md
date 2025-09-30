# Refinando-um-Projeto-Conceitual-de-Banco-de-Dados-E-COMMERCE

O esquema apresentado é um Diagrama de Entidade-Relacionamento (DER) que representa o projeto conceitual de um sistema de E-commerce (comércio eletrônico).

Descrição do Projeto Conceitual
Este modelo conceitual descreve as principais entidades e como elas se relacionam para formar a estrutura de um sistema de vendas online, focando na organização de produtos, vendas/pedidos, clientes, fornecedores/terceiros, e logística/pagamento.

Entidades Chave e Suas Relações
1. Produtos e Estoque
Produto: O item que é vendido. Possui atributos como IdProduto, Categoria, Descrição, e Valor.

Estoque: Representa o local físico onde os produtos são armazenados, com IdEstoque e Local.

Produto_has_Estoque: Uma relação muitos para muitos (N:N) que indica a Quantidade de um determinado Produto que está em um determinado Estoque.

2. Fornecimento de Produtos
O sistema suporta duas formas principais de aquisição de produtos:

Fornecedor: Uma entidade que fornece produtos diretamente à plataforma, com IdFornecedor, Razão Social e CNPJ.

Fornecedor_has_Produto: Relação N:N que define quais produtos são fornecidos por cada Fornecedor.

Terceiro - Vendedor: Representa vendedores parceiros (marketplaces) que vendem seus próprios produtos através da plataforma. Possui IdTerceiro, Razão Social e Local.

Produtos por Vendedor (Terceiro): Relação N:N que indica quais Produtos são vendidos por qual Terceiro - Vendedor, incluindo a Quantidade de produtos que o terceiro tem disponível para venda.

3. Clientes e Tipos de Pessoa
Cliente: A entidade que realiza as compras, identificada por IdCliente, Nome, Endereço e um identificador genérico (Identificação).

Pessoa Física e Pessoa Jurídica: O modelo utiliza um conceito de especialização (representado pelo "1" em ambas as extremidades e pela linha única) para detalhar o tipo de cliente. Um Cliente pode ser uma Pessoa Física (com CPF e Data de Nascimento) ou uma Pessoa Jurídica (com CNPJ e Razão Social).

4. Pedidos e Logística
Pedido: A transação de compra, com IdPedido, Status do Pedido, Descrição, Frete (FLOAT) e a Entrega_idEntrega (chave estrangeira para a entidade Entrega).

Relação de Produto/Pedido: Relação N:N que detalha quais Produtos estão em qual Pedido e em que Quantidade.

Entrega: A entidade de logística associada ao Pedido, com IdEntrega, Status Entrega e Código Rastreio.

5. Pagamento
Pagamento: Associada ao Cliente, registra a forma de pagamento, com IdPagamento, Tipo (ex: cartão, boleto, pix) e Dados do Pagamento. A relação 1:1 com o Cliente sugere que as formas de pagamento estão vinculadas ao cadastro do cliente para uso em pedidos futuros, embora o Pedido em si não esteja diretamente ligado ao Pagamento nesta visualização (é implícito que um pedido usa um ou mais pagamentos registrados).

Objetivo do Sistema
O objetivo principal deste sistema é gerenciar o ciclo de vida completo de uma transação de e-commerce, desde a listagem e estoque de produtos (próprios e de terceiros) até a realização do pedido pelo cliente, passando pelo processamento do pagamento e, finalmente, a entrega do produto. O modelo é robusto o suficiente para suportar um modelo de marketplace (venda por terceiros).
