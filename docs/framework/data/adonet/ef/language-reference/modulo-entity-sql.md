---
title: (Modül) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: ad7b76c1479906e9dcd875407e75475b55d5ae16
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764547"
---
# <a name="modulo-entity-sql"></a>(Modül) (Varlık SQL)
Bir başkası tarafından ayrılmış bir ifade kalanı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Bölmek için sayısal ifade. `dividend` sayısal veri türleri herhangi birinin geçerli bir ifade değil.  
  
 `divisor`  
 Tarafından bölünen bölmek için sayısal ifade. `divisor` sayısal veri türleri herhangi birinin geçerli bir ifade değil.  
  
## <a name="result-types"></a>Sonuç türleri  
 Edm.Int32  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu % aritmetik işleç başkası tarafından ayrılmış bir ifade kalanı döndürmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
