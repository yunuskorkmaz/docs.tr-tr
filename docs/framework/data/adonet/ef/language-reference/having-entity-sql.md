---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: a117f377b3f03b6a1a12e39426a24f3141aa40ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204469"
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)

Grup veya toplama için bir arama koşulu belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `search_condition`  
 Grup veya toplanacak toplama için arama koşulunu belirtir. WITH GROUP for ALL kullanıldığında HAVING yan tümcesi tümünü geçersiz kılar.  
  
## <a name="remarks"></a>Açıklamalar  

 HAVING yan tümcesi, bir gruplandırmanın sonucu üzerinde ek bir filtreleme koşulu belirtmek için kullanılır. Sorgu ifadesinde GROUP BY yan tümcesi belirtilmemişse, örtük bir tek küme grubu varsayılır.  
  
> [!NOTE]
> HAVING yalnızca [Select](select-entity-sql.md) ifadesiyle kullanılabilir. [Group By](group-by-entity-sql.md) kullanılmazsa WHERE yan tümcesi gibi davranır.  
  
HAVING yan tümcesi WHERE yan tümcesi gibi çalışarak GROUP BY işlemden sonra uygulanması hariç olur. Bu, HAVING yan tümcesinin yalnızca diğer adları ve toplamaları gruplandırmak için aşağıdaki örnekte gösterildiği gibi başvuru yapabileceği anlamına gelir:
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Önceki gruplar, grupları yalnızca birden fazla ürün içeren olanlarla kısıtlar.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir grup veya toplama için bir arama koşulu belirtmek üzere HAVING ve GROUP BY işleçlerini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Sorgu İfadeleri](query-expressions-entity-sql.md)
