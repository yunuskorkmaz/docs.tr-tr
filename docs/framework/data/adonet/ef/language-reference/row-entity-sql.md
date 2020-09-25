---
title: SATıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 2ab91d0c6d3c3ed3f88a7f0ddbf3a6c2f36d8b04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202272"
---
# <a name="row-entity-sql"></a>SATıR (Entity SQL)

Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Bir satır türünde yapı için bir değer döndüren geçerli bir sorgu ifadesi.  
  
 `alias`  
 Satır türünde belirtilen değer için bir diğer ad belirtir. Bir diğer ad sağlanmazsa, diğer ad [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturma kurallarına göre bir diğer ad oluşturmaya çalışır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bir satır türü.  
  
## <a name="remarks"></a>Açıklamalar  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturmak için içinde satır oluşturucuları kullanırsınız. Bir satır oluşturucusunun sonuç türü, alan türleri satırı oluşturmak için kullanılan değerlerin türlerine karşılık gelen bir satır türüdür. Örneğin, aşağıdaki ifade türünde bir değer oluşturur `Record(a int, b string, c int)` .  
  
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
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturma Türleri](constructing-types-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Tür Tanımları](type-definitions-entity-sql.md)
