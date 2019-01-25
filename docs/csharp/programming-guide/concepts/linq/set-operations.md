---
title: Ayarlama işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 8a9cf898faeccdf513daf1ae384e811cd559e72a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692187"
---
# <a name="set-operations-c"></a>Ayarlama işlemleri (C#)
LINQ ayarlama işlemleri varlığı veya yokluğu, eşdeğer öğelerin aynı veya farklı koleksiyonlar (veya kümeleri) temel alan bir sonuç kümesi oluşturan sorgu işlemleri bakın.  
  
 Ayarlama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Yinelenen değerleri bir koleksiyondan kaldırır.|Uygulanamaz.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Dışlama|İkinci bir koleksiyon içinde görünmeyen bir koleksiyon öğelerini anlamına gelir ayarlanmış farkı döndürür.|Uygulanamaz.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Kesiştir|Her iki koleksiyon içinde görünen öğelerin anlamına gelir küme kesişimini döndürür.|Uygulanamaz.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|UNION|İki koleksiyon birini görünen benzersiz öğeleri anlamına gelir küme birleşimi döndürür.|Uygulanamaz.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Ayarlama işlemleri karşılaştırması  
  
### <a name="distinct"></a>Distinct  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemi bir karakter dizisi. Döndürülen dizi Giriş dizisinin benzersiz öğeleri içerir.  
  
 ![DISTINCT davranışını gösteren grafik&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Ayrı")  
  
### <a name="except"></a>Dışlama  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Döndürülen dizinin ikinci giriş dizisi içinde olmayan yalnızca öğeleri ilk giriş dizisi içerir.  
  
 ![Eylemi gösteren grafik dışında&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/except.png "Dışında")  
  
### <a name="intersect"></a>Kesiştir  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Döndürülen dizi hem giriş dizilerini için ortak olan öğeleri içerir.  
  
 ![İki dizinin kesişimini gösteren grafik. ](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Kesişen")  
  
### <a name="union"></a>UNION  
 Aşağıdaki çizimde, iki sıranın karakterlerin bir birleşim işlemi gösterilmektedir. Döndürülen dizinin iki giriş dizilerini benzersiz öğeleri içerir.  
  
 ![İki dizinin birleşimi gösteren grafik. ](../../../../csharp/programming-guide/concepts/linq/media/union.png "Birleşim")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Nasıl yapılır: (LINQ) dize koleksiyonlarını birleştirme ve karşılaştırma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [Nasıl yapılır: (LINQ) iki liste arasında ayarlanmış farkı bulma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
