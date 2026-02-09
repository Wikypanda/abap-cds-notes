# CDS Views Concepts

## Introduction
Core Data Services (CDS) are a development model based on the concept of creating and consuming a semantic data model on an SAP system. They allow developers to define rich data models in a declarative manner that can be consumed in various ways.

## Types of CDS Views
1. **Standard CDS Views**: For defining a data model.
2. **Consumption Views**: Specifically designed for data consumption in applications.
3. **Time-dependent Views**: Manage time-dependent data.
4. **Access Control Views**: To control data access.

## Basic Syntax
CDS views are usually defined using the `@AbapCatalog.sqlViewName` annotation for SQL view naming. The syntax related to a CDS view is as follows:

```abap
@AbapCatalog.sqlViewName: 'Z_MY_VIEW'
define view ZMyView as select from my_table {
  key field1,
  field2,
  field3
}
```

## Joins
Joins allow you to combine records from two or more tables based on a related field:

```abap
define view ZMyJoinedView as select from my_table1 as t1
inner join my_table2 as t2 on t1.key = t2.key {
  t1.field1,
  t2.field2
}
```

## Expressions
You can use expressions to transform data:

```abap
define view ZMyExpressionView as select from my_table {
  key field1,
  cast(field2 as abap.int8) as new_field
}
```

## Calculations
CDS views also support calculations within the definition:

```abap
define view ZMyCalcView as select from my_table {
  key field1,
  sum(field2) as total
}
```

## Aggregations
Aggregation functions can summarize data:

```abap
define view ZMyAggregationView as select from my_table {
  key field1,
  count(field2) as count_field
}
```

## Filtering
You can filter data using the `where` clause:

```abap
define view ZMyFilteredView as select from my_table {
  key field1,
  field2
}
where field3 = 'value'
```

## Sorting
Data can be sorted using the `order by` clause:

```abap
define view ZMySortedView as select from my_table {
  key field1,
  field2
}
order by field1 asc
```

## Annotations
Annotations provide metadata for your views:

```abap
@AbapCatalog.sqlViewName: 'Z_MY_ANNOTATED_VIEW'
@AccessControl.authorizationCheck: #CHECK
define view ZMyAnnotatedView as select from my_table {
  key field1,
  field2
}
```

## Complete Example
Here is a complete example combining the concepts above:

```abap
@AbapCatalog.sqlViewName: 'Z_COMPLETE_EXAMPLE_VIEW'
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'Complete Example of CDS View'
define view ZCompleteExampleView as select from my_table as t {
  key t.field1,
  t.field2,
  sum(t.field3) as total_field3
}
where t.field4 = 'specific_value'
order by t.field1 asc
```

This example illustrates the definition of a CDS view that includes annotations, filtering, and basic aggregation.