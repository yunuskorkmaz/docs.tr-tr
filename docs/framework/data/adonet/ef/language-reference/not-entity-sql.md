---
title: '! (Değİl) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0b69d4cb64adc1f9232631d50ec42af0d1ba47e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150135"
---
# <a name="-not-entity-sql"></a>! (Değİl) (Varlık SQL)
Bir `Boolean` ifadeyi inkar eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `boolean_expression`  
 Boolean döndüren geçerli bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Ünlem işareti (!) NOT işleciyle aynı işlevsellik te sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifadeyi geçersiz kışuklamak için NOT işleci kullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
