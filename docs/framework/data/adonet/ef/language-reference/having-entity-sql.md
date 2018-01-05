---
title: "(Varlık SQL) sahip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 92949205801e5bc498fdaaa67c2fa228140a2eb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="having-entity-sql"></a>(Varlık SQL) sahip
Bir grup veya bir toplama için bir arama koşulu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Grup veya toplama karşılamak arama koşulu belirtir. HAVING GROUP BY ALL ile kullanıldığında, HAVING yan tümcesi tüm geçersiz kılar.  
  
## <a name="remarks"></a>Açıklamalar  
 HAVING yan tümcesi bir gruplandırma sonucu üzerinde ek bir filtre koşulu belirtmek için kullanılır. Hiçbir GROUP BY yan tümcesi sorgu ifadesinde belirtilirse, örtük bir tek kümesi grubu varsayılır.  
  
> [!NOTE]
>  HAVING, yalnızca kullanılabilir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimi. Zaman [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) olan kullanılmaz, HAVING WHERE yan tümcesi gibi davranır.  
  
 HAVING yan tümcesi WHERE yan tümcesi gibi çalışır GROUP BY işleminden sonra uygulanır. Bu, HAVING yan tümcesi yalnızca diğer adlar ve toplamalar, gruplandırma başvurular aşağıdaki örnekte gösterildiği gibi yapabileceğini anlamına gelir.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Önceki grupları yalnızca için birden fazla ürün içeren kısıtlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu HAVING ve GROUP BY işleçleri bir grup veya bir toplama için bir arama koşulu belirtmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
