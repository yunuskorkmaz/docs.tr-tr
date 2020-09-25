---
title: IÇINDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 582a3b988247f1484197c0905fecf7f4407f88b0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203676"
---
# <a name="in-entity-sql"></a>IÇINDE (Entity SQL)

Bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `value`  
 Eşleştirilecek değeri döndüren geçerli bir ifade.  
  
 BAŞLATıLMADı  
 Sonucunun, IÇINDE olduğunu belirtir `Boolean` .  
  
 `expression`  
 Bir eşleşme için test edilecek koleksiyonu döndüren geçerli bir ifade. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `value` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` değer koleksiyonda bulunursa; değer null ise veya koleksiyon null ise null; Aksi takdirde, `false` . IÇINDE DEĞIL kullanılması, IÇINDEKI sonuçlarını geçersiz kılar.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini anlamak için ın işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
