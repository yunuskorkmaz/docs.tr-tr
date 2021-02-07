---
description: Hakkında daha fazla bilgi edinin:! = (eşit değildir) (Entity SQL)
title: '! = (Eşit değildir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: a7a96606fb1834b757253948c3a0d2cde11893dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696405"
---
# <a name="-not-equal-to-entity-sql"></a>! = (Eşit değildir) (Entity SQL)

Sol ifadenin sağ ifadeye eşit olup olmadığını anlamak için iki ifadeyi karşılaştırır. ! = (Eşit değildir) işleci, <> işlecine işlevsel olarak eşdeğerdir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  

 `true` sol ifade sağ ifadeye eşit değilse; Aksi takdirde, `false` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeye eşit olup olmadığını belirleyebilmek üzere iki ifadeyi karşılaştırmak için! = işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
