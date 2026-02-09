# Concepts de CDS Views

Les CDS Views (Core Data Services) sont des définitions de modèles de données qui permettent aux développeurs de créer des vues sur des tables de base de données dans un environnement SAP. Elles permettent de simplifier la création de requêtes complexes tout en offrant des fonctionnalités avancées pour l'analyse des données.

## Avantages des CDS Views
- **Réutilisabilité** : Les CDS Views peuvent être réutilisées par d'autres développements, réduisant ainsi le temps de développement.
- **Performance** : Grâce à leur définition au niveau de la base de données, elles peuvent optimiser les performances des requêtes.
- **Sécurité** : Les CDS Views permettent de gérer les habilitations et la sécurité des données de manière centralisée.

## Types de CDS Views
1. **CDS Views de base** : Représentent des tables de données de manière simple.
2. **CDS Views enrichies** : Permettent de calculer des champs supplémentaires et d'incorporer des jointures avec d'autres tables.

## Exemple de syntaxe
Voici un exemple simple de création d'une CDS View :
```sql
@AbapCatalog.sqlViewName: 'ZCDS_VIEW'
@AbapCatalog.compilerCompare: true
@EndUserText.label: 'Exemple de CDS View'
define view ZCDS_VIEW as select from ZTABLE
{
    key field1,
    field2,
    field3
}
```

## Conclusion
Les CDS Views sont un outil puissant dans le développement SAP, fournissant une approche robuste pour la gestion et l'accès aux données.