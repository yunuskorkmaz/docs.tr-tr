---
title: (Mod) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: e2d2c4cd6fd62cf5785d6b69aa399a74f8d04d30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326742"
---
# <a name="modulo-entity-sql"></a>(Mod) (Varlık SQL)
Bir başkası tarafından ayrılmış bir ifadenin kalanı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Bölmek için sayısal ifade. `dividend` sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.  
  
 `divisor`  
 Bölünenin bölüneceği sayısal ifade. `divisor` sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.  
  
## <a name="result-types"></a>Sonuç türleri  
 Edm.Int32  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu % aritmetik işleç bir başkası tarafından ayrılmış tek bir ifade kalanını döndürmek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
