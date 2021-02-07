---
description: Hakkında daha fazla bilgi edinin:! BAŞLATıLMADı (Entity SQL)
title: '! BAŞLATıLMADı (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 648cc4ff73769ae280570b2d42934b2001fa5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696457"
---
# <a name="-not-entity-sql"></a>! BAŞLATıLMADı (Entity SQL)

Bir ifadeyi geçersiz kılar `Boolean` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `boolean_expression`  
 Boolean döndüren geçerli bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 Ünlem işareti (!), NOT işleci ile aynı işlevselliğe sahiptir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir ifadeyi geçersiz hale getirir için NOT işlecini kullanır `Boolean` . Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
