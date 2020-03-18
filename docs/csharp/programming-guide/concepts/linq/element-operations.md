---
title: Eleman İşlemleri (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: e9ec41793afffe60a7184622f91b5fc023e0958f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345154"
---
# <a name="element-operations-c"></a>Eleman İşlemleri (C#)

Öğe işlemleri bir diziden tek, belirli bir öğe döndürür.  
  
 Öğe işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Elementat|Bir koleksiyonda belirtilen dizinteki öğeyi döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|Elementatordefault|Dizin aralık dışındaysa, bir koleksiyonda belirtilen dizinteki öğeyi veya varsayılan değeri döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|İlk|Koleksiyonun ilk öğesini veya bir koşulu tatmin eden ilk öğeyi döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|Firstordefault|Koleksiyonun ilk öğesini veya bir koşulu tatmin eden ilk öğeyi döndürür. Böyle bir öğe yoksa varsayılan bir değer döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Son|Koleksiyonun son öğesini veya bir durumu tatmin eden son öğeyi döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|Lastordefault|Koleksiyonun son öğesini veya bir durumu tatmin eden son öğeyi döndürür. Böyle bir öğe yoksa varsayılan bir değer döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Tek|Bir koleksiyonun tek öğesini veya bir koşulu tatmin eden tek öğeyi döndürür. Döndürülecek <xref:System.InvalidOperationException> bir öğe veya birden fazla öğe varsa atar. |Geçerli değildir.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|Singleordefault|Bir koleksiyonun tek öğesini veya bir koşulu tatmin eden tek öğeyi döndürür. Döndürecek öğe yoksa varsayılan değer verir. Döndürmek için <xref:System.InvalidOperationException> birden fazla öğe varsa bir atar. |Geçerli değildir.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Dizin ağacındaki (LINQ) (C#) en büyük dosya veya dosyaları sorgulama](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
