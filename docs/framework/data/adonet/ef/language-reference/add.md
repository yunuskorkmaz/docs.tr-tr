---
title: + (Ekle)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b86d273658362c3bb204d5220ff5e9db1f8de9fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198060"
---
# <a name="-add"></a>+ (Ekle)

İki sayı ekler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.  
  
## <a name="result-types"></a>Sonuç türleri  

 İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü. Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).  
  
## <a name="remarks"></a>Açıklamalar  

 EDM için. Dize türleri, ekleme birleştirme.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu iki sayı eklemek için + aritmetik işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Kavramsal model türleri (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
