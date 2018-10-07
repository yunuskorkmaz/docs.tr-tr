---
title: Öğe işlemleri (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: dbae8c0b3d98fe9674fbbeb432c1e42763e81026
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836783"
---
# <a name="element-operations-c"></a>Öğe işlemleri (C#)

Öğe işlemleri tek, belirli bir öğe bir dizisini döndürür.  
  
 Öğe işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Bir koleksiyondaki belirtilen dizinindeki öğeyi döndürür.|Yok.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Dizin aralık dışında ise belirtilen dizindeki öğe koleksiyonu veya varsayılan bir değer döndürür.|Yok.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|ilk|Koleksiyonun ilk öğesine veya bir koşulu karşılayan ilk öğeyi döndürür.|Yok.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Koleksiyonun ilk öğesine veya bir koşulu karşılayan ilk öğeyi döndürür. Böyle bir öğe varsa, varsayılan bir değer döndürür.|Yok.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Son|Koleksiyonun son öğesine ya da bir koşulu karşılayan son öğeyi döndürür.|Yok.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Koleksiyonun son öğesine ya da bir koşulu karşılayan son öğeyi döndürür. Böyle bir öğe varsa, varsayılan bir değer döndürür.|Yok.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Tek|Bir koleksiyonun tek öğe veya bir koşulu karşılayan tek öğe döndürür. Oluşturur bir <xref:System.InvalidOperationException> herhangi bir öğe veya döndürmek için birden fazla öğe varsa. |Yok.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Bir koleksiyonun tek öğe veya bir koşulu karşılayan tek öğe döndürür. Herhangi bir öğe döndürmek için ise varsayılan bir değer döndürür. Oluşturur bir <xref:System.InvalidOperationException> döndürmek için birden fazla öğe varsa. |Yok.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Linq>  
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacındaki (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
