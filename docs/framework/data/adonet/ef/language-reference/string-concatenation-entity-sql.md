---
title: + (Dize birleştirme) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 8a1785d590c5f7fcc443856180d516bb40cfc28e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408480"
---
# <a name="-string-concatenation-entity-sql"></a>+ (Dize birleştirme) (varlık SQL)
İki dizeyi art arda ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli ifade EDM. Veri türü dize. Her iki ifade de aynı veri türünde olmalıdır veya bir ifade başka bir ifadenin veri türüne örtük dönüştürülmesi mümkün olması gerekir.  
  
## <a name="result-types"></a>Sonuç türleri  
 Bu iki bağımsız değişken örtük tür yükseltme sonuçlarından veri türü. Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır + işleci için iki dizeyi art arda ekler. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: Bu döndürür PrimitiveType sonuçları sorguyu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Kavramsal Model türleri (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
