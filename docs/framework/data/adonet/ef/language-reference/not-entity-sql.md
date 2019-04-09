---
title: '! (NOT) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: a5f469a89e86dcfbce4f3fcbc8dea09478522762
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177547"
---
# <a name="-not-entity-sql"></a>! (NOT) (Varlık SQL)
Verilerek bir `Boolean` ifade.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Bir Boole değeri döndüren herhangi bir geçerli ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Ünlem işareti (!), NOT işleci ile aynı işlevlere sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu verilerek için değil işlecini kullanan bir `Boolean` ifade. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
