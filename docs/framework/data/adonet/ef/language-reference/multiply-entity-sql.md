---
description: 'Hakkında daha fazla bilgi edinin: * (çarpma) (Entity SQL)'
title: '* Bilirsiniz (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 92606e5f9e4646ab651d0e07095e6f419401188f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696626"
---
# <a name="-multiply-entity-sql"></a>* (Çarp) (Entity SQL)

İki ifadeyi çarpar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.  
  
## <a name="result-types"></a>Sonuç türleri  

 İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü. Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu iki sayıyı çarpmak için * aritmetik işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
