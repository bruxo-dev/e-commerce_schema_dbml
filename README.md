# Database Schema Documentation
This repository was created to carry out the project **Refining a Conceptual Database Project – E-COMMERCE** from Digital Innovation One (web.dio.me).

## Overview
The project defines a relational database schema for managing entities such as suppliers, products, customers, orders, and related transactions. It is written in **DBML** and follows standard conventions represent relational database schematics for latter use on database implementation.

## Objective
The goal of this project is to refine the presented model by incorporating the following new features:
- **Corporate and PF Client:** An account can be either Corporate or PF (Personal), but cannot contain both types of information simultaneously.
- **Payment:** Supports multiple payment methods for a single transaction.
- **Delivery:** Includes status and tracking code for effective shipment management.

## Key Concepts
The database schema includes the following key entities:
- **Fornecedor (Supplier):** Stores information about suppliers, including their unique identification (CNPJ).
- **Produto (Product):** Represents products with details like category, description, and value.
- **Cliente (Customer):** Contains customer details such as identification, address, and type (individual or corporate).
- **Pedido (Order):** Tracks orders placed by customers, including status and associated shipping costs.
- **Pagamento (Payment):** Links orders to their respective payments and supports multiple payment methods.
- **Entrega (Delivery):** Manages order deliveries with tracking information and current status.
- **Estoque (Inventory):** Tracks product quantities at different storage locations.
- **Vendedor Terceiro (Third-party Seller):** Manages products offered by third-party vendors.
- **Junction Tables:** Handle many-to-many relationships between entities, such as products and suppliers, or products and orders.

##Workflow
In order to upgrade the actual schema logic for the project, I have created an algorithm in DBML to convert the schema logic from visual context to a script with the databse structure with rules and regulations. This process made it possible to make declarations of the project new features, requests and test the schema for logic errors and bugs.

## Visual Representation
To better understand the database structure, a visual representation can be generated using [dbdiagram.io](https://dbdiagram.io/):

1. Copy the DBML code from `e-commerce_schema.dbml`.
2. Paste it into the **dbdiagram.io** editor.
3. Adjust tables positions and organization for clarity using the visual editing tools on the website.

The generated ER diagram provides an intuitive overview of the database structure, including primary and foreign key relationships.

## Final Result
The resulting database schema from the procedures above is as follows on file `e-commerce_schema.png`.

## Contact
For questions or suggestions, feel free to say "Hello, friend!" at [rmjo.inbox@gmail.com] or at my GitHub Inbox.
