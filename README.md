# 🛒 Projeto de Banco de Dados: E-commerce

Este projeto apresenta a modelagem lógica e relacional de um banco de dados para um sistema de e-commerce. O objetivo é representar clientes, vendedores, fornecedores, produtos, pedidos, entregas e pagamentos, com integridade referencial e suporte a consultas analíticas.

## 📐 Modelagem

A modelagem foi feita com base no modelo ER refinado para contemplar:
- Clientes Pessoa Física (CPF) ou Jurídica (CNPJ), mas nunca ambos
- Vendedores e fornecedores distintos, com validação de CNPJ
- Produtos com categorias, avaliações e tamanhos
- Pedidos com múltiplos produtos, formas de pagamento e entregas rastreáveis

## 🧱 Estrutura do Banco

- `client`: Clientes PF ou PJ
- `seller`: Vendedores
- `supplier`: Fornecedores
- `product`: Produtos
- `orders`: Pedidos
- `delivery`: Entregas com status e rastreio
- `payment`: Formas de pagamento
- `productOrder`: Produtos em pedidos
- `productSeller`: Relação produto-vendedor
- `productSupplier`: Relação produto-fornecedor
- `productStorage` e `storageLocation`: Estoque e localização

## 🛠️ Tecnologias

- MySQL
- MySQL Workbench
- SQL padrão com constraints, chaves primárias e estrangeiras
- `ON DELETE CASCADE` e `ON UPDATE CASCADE` aplicados onde necessário

## 📥 População de Dados

Scripts de inserção simulam:
- Clientes reais e empresas
- Produtos variados
- Pedidos com múltiplas formas de pagamento
- Entregas com rastreio

## 🔍 Consultas SQL

### Quantos pedidos foram feitos por cada cliente?
```sql
SELECT c.Fname, COUNT(o.idOrder) AS total_pedidos
FROM client c
JOIN orders o ON c.idClient = o.idClient
GROUP BY c.idClient;

