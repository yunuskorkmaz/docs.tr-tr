---
title: IÇINDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 5a07ee79d5452da4341d391fae7c997c33b603a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250667"
---
# <a name="in-entity-sql"></a>IÇINDE (Entity SQL)
Bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Eşleştirilecek değeri döndüren geçerli bir ifade.  
  
 BAŞLATILMADI  
 Sonucunun, `Boolean` içinde olduğunu belirtir.  
  
 `expression`  
 Bir eşleşme için test edilecek koleksiyonu döndüren geçerli bir ifade. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde `value`olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`değer koleksiyonda bulunursa; değer null ise veya koleksiyon null ise null; Aksi takdirde `false`,. IÇINDE DEĞIL kullanılması, IÇINDEKI sonuçlarını geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini anlamak için ın işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
