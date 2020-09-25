---
title: '- Çıkarma (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 17841f336ed186dcbc50b84254048546b15297e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181043"
---
# <a name="--subtract-entity-sql"></a>-(Çıkart) (Entity SQL)

İki sayıyı çıkartır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.  
  
## <a name="result-types"></a>Sonuç türleri  

 İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü. Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu iki sayıyı çıkarmak için-aritmetik işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
