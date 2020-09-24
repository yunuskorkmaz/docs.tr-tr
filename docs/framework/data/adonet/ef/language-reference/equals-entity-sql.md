---
title: = (Eşittir) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 31299670d9f47ed7672b980a3415b8d214463b8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148093"
---
# <a name="-equals-entity-sql"></a>= (Eşittir) (Entity SQL)

İki ifadenin eşitliğini karşılaştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  

 `true` sol ifade sağ ifadeye eşitse; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 = = İşleci = = ile eşdeğerdir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu iki ifadenin eşitliğini karşılaştırmak için = Comparison işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
