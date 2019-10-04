---
title: IÇINDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833688"
---
# <a name="in-entity-sql"></a>IÇINDE (Entity SQL)
Bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Eşleştirilecek değeri döndüren geçerli bir ifade.  
  
 BAŞLATıLMADı  
 Öğesinin `Boolean` sonucunun bir arada olduğunu belirtir.  
  
 `expression`  
 Bir eşleşme için test edilecek koleksiyonu döndüren geçerli bir ifade. Tüm ifadeler aynı türde veya ortak bir temel ya da türetilmiş türden `value` olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 değer koleksiyonda bulunursa, `true`; değer null ise veya koleksiyon null ise null; Aksi takdirde, `false`. IÇINDE DEĞIL kullanılması, IÇINDEKI sonuçlarını geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini anlamak için ın işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
