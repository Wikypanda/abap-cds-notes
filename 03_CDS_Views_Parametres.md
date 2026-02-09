# Les CDS Views avec Paramètres

Les CDS Views (Core Data Services Views) sont une technologie essentielle dans SAP qui permet de définir des modèles de données et d'extraire des données de manière efficace. Lorsqu'il s'agit de créer des CDS Views avec des paramètres, cela ajoute une flexibilité considérable à la manière dont les données peuvent être filtrées et affichées.

## Qu'est-ce qu'un paramètre dans une CDS View?

Un paramètre dans une CDS View est une variable qui peut être utilisée pour filtrer les résultats de la vue en fonction de la valeur fournie à l'exécution. Cela permet aux utilisateurs de saisir des valeurs spécifiques lors de l'exécution d'une requête, offrant ainsi une personnalisation dynamique des données affichées.

## Comment créer une CDS View avec des paramètres?

1. **Définir la vue** : Commencez par définir votre CDS View de base.
   ```abap
   @AbapCatalog.sqlViewName: 'ZCDS_PARAM'
   define view ZCDS_View_Parameters
   with parameters
       p_param1 : abap.int4
   as select from your_table
   where field_name = :p_param1;
   ```

2. **Utiliser des paramètres** : Dans l'exemple ci-dessus, `p_param1` est un paramètre que vous pouvez passer à votre CDS View afin de filtrer les résultats en fonction de la valeur souhaitée.

## Exécuter la CDS View avec des paramètres

Lors de l'exécution de la CDS View, vous serez invité à fournir une valeur pour le paramètre. Il vous suffit de saisir cette valeur, et la vue renverra les résultats filtrés.

## Conclusion

Les CDS Views avec des paramètres sont un moyen puissant de personnaliser les données dans SAP. En permettant aux utilisateurs de fournir des valeurs spécifiques, vous pouvez rendre vos CDS Views beaucoup plus dynamiques et utiles pour les analyses.

## Exemple d'utilisation

Voici un petit exemple d'utilisation de CDS Views avec des paramètres dans des requêtes ABAP:

```abap
DATA(lo_view) = NEW cl_abap_sql_view( name = 'ZCDS_View_Parameters' ).
DATA(lt_results) = lo_view->execute( p_param1 = 100 ).
" Traitez les résultats comme nécessaire
```