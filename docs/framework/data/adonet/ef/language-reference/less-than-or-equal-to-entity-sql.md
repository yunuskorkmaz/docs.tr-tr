---
title: < (küçüktür veya eşittir) = (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 68a4c91800dce2ab6a632e849a8c58c378150535
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284719"
---
# <a name="-less-than-or-equal-to-entity-sql"></a>\<= (Küçüktür veya eşittir) (varlık SQL)
Sol ifade düşük bir değere eşit veya ondan sağ ifade olup olmadığını belirlemek için iki deyim karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli ifade. Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  
 `true` Sol ifade düşük bir değere eşit veya ondan sağ ifade varsa; Aksi takdirde, `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır < = sol ifade düşük bir değere eşit veya ondan sağ ifade olup olmadığını belirlemek için iki deyim karşılaştırmak için kullanılan karşılaştırma işleci. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
