---
title: '! = (Eşit değildir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3f6f66d38eb9650e1adb06fa3ef5edbccf110374
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319504"
---
# <a name="-not-equal-to-entity-sql"></a>! = (Eşit değildir) (Entity SQL)
Sol ifadenin sağ ifadeye eşit olup olmadığını anlamak için iki ifadeyi karşılaştırır. ! = (Eşit değildir) işleci, < > işlecine işlevsel olarak eşdeğerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  
 sol ifade sağ ifadeye eşit değilse, `true`; Aksi takdirde, `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeye eşit olup olmadığını belirleyebilmek üzere iki ifadeyi karşılaştırmak için! = işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
