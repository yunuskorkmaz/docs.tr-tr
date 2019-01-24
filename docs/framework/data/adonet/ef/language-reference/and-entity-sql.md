---
title: '&amp;&amp; (VE) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 6ee7987f2801a35fb9669472ce7b237e684f64e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579673"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp; (VE) (Varlık SQL)
Döndürür `true` her iki ifade ise `true`; Aksi takdirde `false` veya `NULL`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Bir Boole değeri döndüren herhangi bir geçerli ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Çift işaretlerini (& &) ve işleç aynı işlevselliğe sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri gösterir ve dönüş türleri.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|FALSE|NULL|  
|`FALSE`|FALSE|FALSE|FALSE|  
|`NULL`|NULL|FALSE|NULL|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu ve işlecini kullanmayı gösterir. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
