-- Creating the Fornecedor table to store supplier information
CREATE TABLE "Fornecedor" (
  "ID_fornecedor" int PRIMARY KEY, -- Unique identifier for each supplier
  "razao_social" varchar,        -- Legal name of the supplier
  "CNPJ" varchar UNIQUE          -- Unique tax identification number (Brazilian context)
);

-- Creating the Produto table to store product information
CREATE TABLE "Produto" (
  "ID_produto" int PRIMARY KEY,  -- Unique identifier for each product
  "categoria" varchar,          -- Category of the product
  "descricao" varchar,          -- Description of the product
  "valor" decimal               -- Price of the product
);

-- Creating the Estoque table to store inventory locations
CREATE TABLE "Estoque" (
  "ID_estoque" int PRIMARY KEY,  -- Unique identifier for each inventory location
  "local" varchar               -- Location description
);

-- Creating the Vendedor_terceiro table to store third-party seller information
CREATE TABLE "Vendedor_terceiro" (
  "ID_terceiro" int PRIMARY KEY, -- Unique identifier for each third-party seller
  "razao_social" varchar,       -- Legal name of the third-party seller
  "local" varchar               -- Location of the third-party seller
);

-- Creating the Cliente table to store customer information
CREATE TABLE "Cliente" (
  "ID_cliente" int PRIMARY KEY, -- Unique identifier for each customer
  "nome" varchar,              -- Name of the customer
  "identificacao" varchar UNIQUE, -- Unique customer identification (e.g., CPF/CNPJ)
  "endereco" varchar,          -- Address of the customer
  "tipo" varchar               -- Type of customer (e.g., individual or corporate)
);

-- Creating the Pedido table to store order information
CREATE TABLE "Pedido" (
  "ID_pedido" int PRIMARY KEY,  -- Unique identifier for each order
  "status" varchar,            -- Current status of the order
  "descricao" varchar,         -- Description of the order
  "cliente_ID_cliente" int,    -- Foreign key referencing the Cliente table
  "frete" decimal              -- Shipping cost for the order
);

-- Creating the Pagamento table to store payment information
CREATE TABLE "Pagamento" (
  "ID_pagamento" int PRIMARY KEY, -- Unique identifier for each payment
  "tipo" varchar,                -- Payment type (e.g., credit, debit, cash)
  "pedido_ID_pedido" int         -- Foreign key referencing the Pedido table
);

-- Creating the Entrega table to store delivery information
CREATE TABLE "Entrega" (
  "ID_entrega" int PRIMARY KEY,   -- Unique identifier for each delivery
  "status" varchar,              -- Current status of the delivery
  "codigo_rastreio" varchar,     -- Tracking code for the delivery
  "pedido_ID_pedido" int         -- Foreign key referencing the Pedido table
);

-- Creating a junction table to relate Fornecedor and Produto
CREATE TABLE "Fornecedor_tem_produto" (
  "fornecedor_ID_fornecedor" int, -- Foreign key referencing Fornecedor table
  "produto_ID_produto" int,       -- Foreign key referencing Produto table
  PRIMARY KEY(fornecedor_ID_fornecedor, produto_ID_produto) -- Composite primary key
);

-- Creating a junction table to relate Estoque and Produto
CREATE TABLE "Estoque_tem_produto" (
  "produto_ID_produto" int,       -- Foreign key referencing Produto table
  "estoque_ID_estoque" int,       -- Foreign key referencing Estoque table
  "quantidade" int,               -- Quantity of the product in this inventory location
  PRIMARY KEY(produto_ID_produto, estoque_ID_estoque) -- Composite primary key
);

-- Creating a junction table to relate Vendedor_terceiro and Produto
CREATE TABLE "Terceiro_tem_produto" (
  "terceiro_ID_terceiro" int,     -- Foreign key referencing Vendedor_terceiro table
  "produto_ID_produto" int,       -- Foreign key referencing Produto table
  "quantidade" int,               -- Quantity of the product available from this seller
  PRIMARY KEY(terceiro_ID_terceiro, produto_ID_produto) -- Composite primary key
);

-- Creating a junction table to relate Produto and Pedido
CREATE TABLE "Relacao_produto_pedido" (
  "produto_ID_produto" int,       -- Foreign key referencing Produto table
  "pedido_ID_pedido" int,         -- Foreign key referencing Pedido table
  "quantidade" int,               -- Quantity of the product in the order
  PRIMARY KEY(produto_ID_produto, pedido_ID_pedido) -- Composite primary key
);

-- Adding foreign key constraints to Pedido table
ALTER TABLE "Pedido" ADD FOREIGN KEY ("cliente_ID_cliente") REFERENCES "Cliente" ("ID_cliente");

-- Adding foreign key constraints to Pagamento table
ALTER TABLE "Pagamento" ADD FOREIGN KEY ("pedido_ID_pedido") REFERENCES "Pedido" ("ID_pedido");

-- Adding foreign key constraints to Entrega table
ALTER TABLE "Entrega" ADD FOREIGN KEY ("pedido_ID_pedido") REFERENCES "Pedido" ("ID_pedido");

-- Adding foreign key constraints to Fornecedor_tem_produto table
ALTER TABLE "Fornecedor_tem_produto" ADD FOREIGN KEY ("fornecedor_ID_fornecedor") REFERENCES "Fornecedor" ("ID_fornecedor");
ALTER TABLE "Fornecedor_tem_produto" ADD FOREIGN KEY ("produto_ID_produto") REFERENCES "Produto" ("ID_produto");

-- Adding foreign key constraints to Estoque_tem_produto table
ALTER TABLE "Estoque_tem_produto" ADD FOREIGN KEY ("produto_ID_produto") REFERENCES "Produto" ("ID_produto");
ALTER TABLE "Estoque_tem_produto" ADD FOREIGN KEY ("estoque_ID_estoque") REFERENCES "Estoque" ("ID_estoque");

-- Adding foreign key constraints to Terceiro_tem_produto table
ALTER TABLE "Terceiro_tem_produto" ADD FOREIGN KEY ("terceiro_ID_terceiro") REFERENCES "Vendedor_terceiro" ("ID_terceiro");
ALTER TABLE "Terceiro_tem_produto" ADD FOREIGN KEY ("produto_ID_produto") REFERENCES "Produto" ("ID_produto");

-- Adding foreign key constraints to Relacao_produto_pedido table
ALTER TABLE "Relacao_produto_pedido" ADD FOREIGN KEY ("produto_ID_produto") REFERENCES "Produto" ("ID_produto");
ALTER TABLE "Relacao_produto_pedido" ADD FOREIGN KEY ("pedido_ID_pedido") REFERENCES "Pedido" ("ID_pedido");
