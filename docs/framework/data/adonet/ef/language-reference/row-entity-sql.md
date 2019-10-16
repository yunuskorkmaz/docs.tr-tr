---
title: SATıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 4fb16fe0072066580bff36ac0879ff38217f1e34
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319383"
---
# <a name="row-entity-sql"></a>SATıR (Entity SQL)
Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir satır türünde yapı için bir değer döndüren geçerli bir sorgu ifadesi.  
  
 `alias`  
 Satır türünde belirtilen değer için bir diğer ad belirtir. Bir diğer ad sağlanmazsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] [!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad oluşturma kurallarına göre bir diğer ad oluşturmaya çalışır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir satır türü.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' da satır oluşturucuları kullanırsınız. Bir satır oluşturucusunun sonuç türü, alan türleri satırı oluşturmak için kullanılan değerlerin türlerine karşılık gelen bir satır türüdür. Örneğin, aşağıdaki ifade `Record(a int, b string, c int)` türünde bir değer oluşturur.  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Bir satır oluşturucusunda ifade için bir diğer ad sağlamazsanız, Entity Framework bir tane oluşturmaya çalışacaktır. Daha fazla bilgi için, [tanımlayıcılar](identifiers-entity-sql.md) konusunun "diğer ad kuralları" bölümüne bakın.  
  
 Aşağıdaki kurallar, bir satır oluşturucusunda ifade diğer ad için geçerlidir:  
  
- Bir satır oluşturucudaki ifadeler aynı oluşturucuda diğer diğer adlara başvuramaz.  
  
- Aynı satır oluşturucusunun iki ifadesi aynı diğer ada sahip olamaz.  
  
 Sorgu oluşturucular hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, anonim ve yapısal olarak belirlenmiş kayıtlar oluşturmak için satır işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturma Türleri](constructing-types-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Tür Tanımları](type-definitions-entity-sql.md)
