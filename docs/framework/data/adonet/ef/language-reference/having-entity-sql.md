---
title: SAHİP (varlık SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 7b147a84a43677afa53f7872f8042f1cf44137cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316186"
---
# <a name="having-entity-sql"></a>SAHİP (varlık SQL)
Bir toplama veya bir grup için bir arama koşulu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Grup veya toplama karşılamak arama koşulu belirtir. HAVING GROUP BY ALL ile kullanıldığında, HAVING yan tümcesi tüm geçersiz kılar.  
  
## <a name="remarks"></a>Açıklamalar  
 HAVING yan tümcesi, bir gruplandırma sonucuna ek bir filtreleme koşulunu belirtmek için kullanılır. GROUP BY yan tümce sorgu ifadesi içinde belirtilen bir örtük tek küme grubu kabul edilir.  
  
> [!NOTE]
>  HAVING yalnızca kullanılabilir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimi. Zaman [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) olduğundan kullanılmayan, HAVING bir WHERE yan tümcesi gibi davranır.  
  
 HAVING yan WHERE yan tümcesi gibi çalışır GROUP BY işleminden sonra uygulanır. HAVING yan tümcesi yalnızca gruplandırma diğer adlar ve toplamalar, başvurular aşağıdaki örnekte gösterildiği gibi yapabileceğini anlamına gelir.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Önceki grupları yalnızca için birden fazla ürünü içeren kısıtlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu HAVING ve GROUP BY işleçleri toplama veya bir grup için bir arama koşulu belirtmek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
