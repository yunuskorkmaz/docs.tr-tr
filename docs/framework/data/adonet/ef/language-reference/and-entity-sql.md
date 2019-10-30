---
title: '&amp;&amp; (ve) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: be6e7120e6c19714f151aa38a8b9a1355de29d1a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039960"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp; (ve) (Entity SQL)
Her iki ifade de `true``true` döndürür; Aksi takdirde, `false` veya `NULL`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
boolean_expression AND boolean_expression
```
 
veya  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Boolean döndüren geçerli bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Çift ve işareti (& &), ve işleciyle aynı işlevselliğe sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|YANLÝÞ|NULL|  
|`FALSE`|YANLÝÞ|YANLÝÞ|YANLÝÞ|  
|`NULL`|NULL|YANLÝÞ|NULL|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, ve işlecinin nasıl kullanılacağını göstermektedir. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
