---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 76a63140668fb1f41cf9e6f901d9a43240a1d098
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936078"
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)
Grup veya toplama için bir arama koşulu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Grup veya toplanacak toplama için arama koşulunu belirtir. WITH GROUP for ALL kullanıldığında HAVING yan tümcesi tümünü geçersiz kılar.  
  
## <a name="remarks"></a>Açıklamalar  
 HAVING yan tümcesi, bir gruplandırmanın sonucu üzerinde ek bir filtreleme koşulu belirtmek için kullanılır. Sorgu ifadesinde GROUP BY yan tümcesi belirtilmemişse, örtük bir tek küme grubu varsayılır.  
  
> [!NOTE]
> HAVING yalnızca [Select](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) ifadesiyle kullanılabilir. [Group By](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) kullanılmazsa WHERE yan tümcesi gibi davranır.  
  
 HAVING yan tümcesi WHERE yan tümcesi gibi çalışarak GROUP BY işlemden sonra uygulanması hariç olur. Bu, HAVING yan tümcesinin yalnızca diğer adları ve toplamaları gruplandırmak için aşağıdaki örnekte gösterildiği gibi başvuru yapabileceği anlamına gelir.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Önceki gruplar, grupları yalnızca birden fazla ürün içeren olanlarla kısıtlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir grup veya toplama için bir arama koşulu belirtmek üzere HAVING ve GROUP BY işleçlerini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
