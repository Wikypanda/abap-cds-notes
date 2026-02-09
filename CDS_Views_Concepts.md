# CDS Views

## Definition
Core Data Services (CDS) views are a data modeling infrastructure provided by SAP to define semantic data models at the database level. CDS views allow developers to define views on the underlying data model that can be consumed by various applications. 

## Types
1. **Basic CDS Views**: These are derived from one or more database tables or other views and do not include any complex processing.
2. **Composite CDS Views**: These are built on top of basic CDS views and can include additional logic, such as joins, aggregations, and filtering.
3. **Consumption CDS Views**: These views are optimized for consumption in UI applications, often used to expose data to Fiori apps.

## Syntax
The basic syntax for defining a CDS view is:
```sql
define view <ViewName> as select from <TableName> {
    <Field1>,
    <Field2>,
    ...
}
```

## Joins
Joins in CDS views can be performed via the `join` keyword. Here is an example:
```sql
define view ZProductSales as select from ZProduct as Product
    join ZSales as Sales on Product.ProductID = Sales.ProductID {
    Product.ProductName,
    Sales.QuantitySold
}
```

## Expressions
CDS views support various expressions, including:
- **Arithmetic Expressions**: e.g., `Sales.TotalAmount - Sales.Discount`
- **Conditional Expressions (CASE)**: e.g., `case when Sales.Quantity > 0 then 'In Stock' else 'Out of Stock' end as StockStatus`

## Annotations
CDS annotations provide additional metadata and are defined using the `@` symbol. Example:
```sql
@AbapCatalog.viewEnhancement: {  }
@EndUserText.label: 'Sales Data View'
define view ZSalesData as select from ZSales {
    Sales.ProductID,
    Sales.QuantitySold
}
```

## Complete Examples
```sql
define view ZCompleteExample as select from ZSales as Sales
    join ZProduct as Product on Sales.ProductID = Product.ProductID
    join ZCustomer as Customer on Sales.CustomerID = Customer.CustomerID {
    Product.ProductName,
    Customer.CustomerName,
    Sales.QuantitySold,
    case when Sales.QuantitySold > 100 then 'High Demand' else 'Normal Demand' end as DemandStatus
}
```

This example illustrates the power of CDS views to create complex queries using joins, expressions, and annotations, making it easier to handle complex business logic directly in the database layer.