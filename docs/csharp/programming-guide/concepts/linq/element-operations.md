---
title: Öğe Işlemleri (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: e9ec41793afffe60a7184622f91b5fc023e0958f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345154"
---
# <a name="element-operations-c"></a>Öğe Işlemleri (C#)

Öğe işlemleri bir dizideki tek ve belirli bir öğeyi döndürür.  
  
 Öğe işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Koleksiyonda belirtilen dizindeki öğeyi döndürür.|Yok.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Dizin aralık dışında olduğunda, bir koleksiyondaki belirtilen dizindeki öğeyi veya varsayılan değeri döndürür.|Yok.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|Birinci|Bir koleksiyonun ilk öğesini veya bir koşulu karşılayan ilk öğeyi döndürür.|Yok.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Bir koleksiyonun ilk öğesini veya bir koşulu karşılayan ilk öğeyi döndürür. Böyle bir öğe yoksa, varsayılan bir değer döndürür.|Yok.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Sonuncu|Bir koleksiyonun son öğesini veya bir koşulu karşılayan son öğeyi döndürür.|Yok.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Bir koleksiyonun son öğesini veya bir koşulu karşılayan son öğeyi döndürür. Böyle bir öğe yoksa, varsayılan bir değer döndürür.|Yok.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Tek|Bir koleksiyonun tek bir öğesini veya bir koşulu karşılayan tek öğeyi döndürür. Döndürülecek bir öğe veya birden fazla öğe yoksa bir <xref:System.InvalidOperationException> oluşturur. |Yok.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Bir koleksiyonun tek bir öğesini veya bir koşulu karşılayan tek öğeyi döndürür. Döndürülecek öğe yoksa, varsayılan bir değer döndürür. Döndürülecek birden fazla öğe varsa bir <xref:System.InvalidOperationException> oluşturur. |Yok.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
