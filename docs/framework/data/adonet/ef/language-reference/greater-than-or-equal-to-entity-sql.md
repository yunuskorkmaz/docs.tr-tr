---
title: '>= (Büyüktür veya eşittir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 02e03d6d2da321bd02ea2b14e45a910853d39c4d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158428"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a>>= (büyüktür veya eşittir) (Entity SQL)

Sol ifadenin sağ ifadeden büyük veya ona eşit bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  

 `true` Sol ifadede sağ ifadeden daha büyük veya ona eşit bir değer varsa; Aksi takdirde, `false` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeden büyük veya ona eşit bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için >= karşılaştırma işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
