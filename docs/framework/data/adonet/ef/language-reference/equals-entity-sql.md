---
title: = (Eşittir) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 101dccd40e9197c7cf0795ccb80ded367676842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150318"
---
# <a name="-equals-entity-sql"></a>= (Eşittir) (Varlık SQL)
İki ifadenin eşitliğini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Herhangi bir geçerli ifade. Her iki ifadede de dolaylı olarak dönüştürülebilir veri türleri olmalıdır.  
  
## <a name="result-types"></a>Sonuç Türleri  
 `true`sol ifade doğru ifadeye eşitse; aksi `false`takdirde, .  
  
## <a name="remarks"></a>Açıklamalar  
 == işleci ='ya eşdeğerdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, iki ifadenin eşitliğini karşılaştırmak için = karşılaştırma işleci kullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
