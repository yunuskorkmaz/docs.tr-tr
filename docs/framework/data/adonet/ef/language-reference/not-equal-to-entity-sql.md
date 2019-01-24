---
title: '! = (Eşit değildir) (varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: d5e59fe61dbc05a48e98f5720dca446482b9968e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568145"
---
# <a name="-not-equal-to-entity-sql"></a>! = (Eşit değildir) (varlık SQL)
Sol ifade doğru ifade eşit olup olmadığını belirlemek için iki deyim karşılaştırır. ! = (Eşit değildir) işlecini <> işlecine eşdeğer işleve sahiptir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  
 `true` Sol ifade doğru ifade eşit değilse, Aksi takdirde, `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır! = işleci sol ifade doğru ifade eşit olup olmadığını belirlemek için iki deyim karşılaştırmak için. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
