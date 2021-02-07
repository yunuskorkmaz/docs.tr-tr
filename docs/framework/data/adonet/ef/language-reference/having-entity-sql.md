---
description: 'Hakkında daha fazla bilgi edinin: HAVING (Entity SQL)'
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 70ace20d67e93aa051873d2b32a49f560902e63d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696886"
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
