---
title: '> (Büyüktür) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 52a9f9f645aa51402ceb8cb0a40d2040d1c0802c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147950"
---
# <a name="-greater-than-entity-sql"></a>> (büyüktür) (Entity SQL)

Sol ifadenin sağ ifadeden daha büyük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  

 `true` sol ifade sağ ifadeden daha büyük bir değere sahipse; Aksi takdirde, `false` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeden daha büyük bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için > karşılaştırma işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
