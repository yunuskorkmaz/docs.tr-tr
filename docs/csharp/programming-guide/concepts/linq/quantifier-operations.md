---
title: Niceleyici işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 22d7b86a5935c7721b7ab13eea1252231d6ac095
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509226"
---
# <a name="quantifier-operations-c"></a>Niceleyici işlemleri (C#)
Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazılarını veya tümünü bir dizideki öğelerin bir koşulu karşılayan olup olmadığını gösteren değer.  
  
 Aşağıdaki çizimde, iki farklı kaynak diziler üzerinde iki farklı niceleyici işlemleri gösterilmektedir. İlk işlem bir veya daha fazla öğe olan karakter 'A' ve sonucu olup olmadığını soran `true`. İkinci işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.  
  
 ![LINQ Niceleyici işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Tümü|Bir dizideki tüm öğeler bir koşulu karşılayan olup olmadığını belirler.|Uygulanamaz.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Tüm|Bir dizideki herhangi bir öğe bir koşulu karşılayan olup olmadığını belirler.|Uygulanamaz.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|İçerir|Bir dizi belirtilen öğeyi içerip içermediğini belirler.|Uygulanamaz.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [Nasıl yapılır: Belirli bir sözcükler (LINQ) kümesini içeren cümleleri sorgulama (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
