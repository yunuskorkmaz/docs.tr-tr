---
title: Nicelik belirteci Işlemleri (C#)
description: Belirleyici işlemler hakkında bilgi edinin. Bu işlemler, bir dizideki bazı veya tüm öğelerin bir koşulu karşılayıp karşılamadığını belirten bir Boole değeri döndürür.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ffefe1715fd8a074692967e825e0f55673bb2b27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202545"
---
# <a name="quantifier-operations-c"></a>Nicelik belirteci Işlemleri (C#)

Nicelik belirteci işlemleri bir <xref:System.Boolean> dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten bir değer döndürür.  
  
 Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir. İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç olur `true` . İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını ve sonucun olduğunu sorar `true` .  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu Ifadesi sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Tümü|Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Herhangi biri|Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contains|Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  
  
### <a name="all"></a>Tümü  

Aşağıdaki örnek, `All` tüm dizelerin belirli bir uzunlukta olduğunu denetlemek için öğesini kullanır.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Herhangi biri  

Aşağıdaki örnek `Any` ' o ' ile başlayan dizelerin olduğunu denetlemek için öğesini kullanır.  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Contains  

Aşağıdaki örnek, `Contains` bir diziyi denetlemek için öğesini kullanır, belirli bir öğesi.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
