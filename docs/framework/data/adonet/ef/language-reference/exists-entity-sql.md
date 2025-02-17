---
description: 'Hakkında daha fazla bilgi edinin: var (Entity SQL)'
title: VAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: c6c5b86616d63b9cc3389365a96c382101463732
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786387"
---
# <a name="exists-entity-sql"></a>VAR (Entity SQL)

Bir koleksiyonun boş olup olmadığını belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Bir koleksiyon döndüren geçerli bir ifade.  
  
 NOT  
 Sonucunun var olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` koleksiyon boş değilse, Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 EXISTS, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. Set işleçleri için öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bkz. [except](except-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, koleksiyonun boş olup olmadığını anlamak için EXISTS işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
