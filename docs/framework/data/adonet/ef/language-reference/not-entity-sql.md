---
title: '! BAŞLATıLMADı (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 7755219c5238f78e59332c508643fe2ae1f5096f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319527"
---
# <a name="-not-entity-sql"></a>! BAŞLATıLMADı (Entity SQL)
@No__t-0 ifadesini geçersiz kılar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
``` 
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Boolean döndüren geçerli bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Ünlem işareti (!), NOT işleci ile aynı işlevselliğe sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifadesini geçersiz hale getirir için NOT işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
