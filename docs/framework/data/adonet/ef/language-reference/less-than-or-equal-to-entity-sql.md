---
title: <= (küçüktür veya eşittir) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 09f2a7f53d00739b8542cb1149397f24d3b04f42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161808"
---
# <a name="-less-than-or-equal-to-entity-sql"></a>\<= (Küçüktür veya eşittir) (Entity SQL)

Sol ifadenin doğru ifadeye eşit veya ondan küçük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  

 `true` sol ifade, doğru ifadeye eşit veya daha küçük bir değere sahipse; Aksi takdirde, `false` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, sol ifadenin doğru ifadeye eşit veya daha küçük bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için <= karşılaştırma işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
