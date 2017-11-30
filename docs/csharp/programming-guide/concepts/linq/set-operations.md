---
title: "Ayarlama işlemleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5b546d9df8752fd7afd6e0db4525bc923a74bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-c"></a>Ayarlama işlemleri (C#)
Ayarlama işlemleri LINQ varlığının veya yokluğunun aynı ya da ayrı koleksiyonlar (veya içindeki ayarlar) eşdeğer öğelerinin temel alan bir sonuç kümesi oluşturan sorgu işlemlerini bakın.  
  
 Ayarlama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Yinelenen değerleri koleksiyondan kaldırır.|Yok.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Dışlama|İkinci bir koleksiyonda görünmez bir koleksiyonun öğelerini anlamına gelir ayarlanmış farkı döndürür.|Yok.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Kesiştir|Her iki koleksiyon görünen öğelerin anlamına gelir kümesi kümenin kesişimini döndürür.|Yok.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|UNION|İki koleksiyon birini görünen benzersiz öğelerin anlamına gelir kümesi UNION döndürür.|Yok.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Ayarlama işlemleri karşılaştırması  
  
### <a name="distinct"></a>Distinct  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemi bir karakter dizisi. Döndürülen dizi giriş sırası benzersiz öğeleri içerir.  
  
 ![DISTINCT &#40; &#41;davranışını gösteren grafik;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Ayrı")  
  
### <a name="except"></a>Dışlama  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Döndürülen dizi ikinci giriş sırayla olmayan yalnızca öğeleri ilk giriş dizisi içerir.  
  
 ![Eylemini gösteren grafik dışında &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "Dışında")  
  
### <a name="intersect"></a>Kesiştir  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Döndürülen dizi hem giriş dizilerini için ortak olan öğeleri içerir.  
  
 ![İki dizinin kesişimini gösteren grafik. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Kesiştiği")  
  
### <a name="union"></a>UNION  
 Aşağıdaki çizimde iki sıraları karakterden oluşan bir bileşim işlemi gösterilmektedir. Döndürülen dizi hem giriş dizilerini benzersiz öğeleri içerir.  
  
 ![İki sıraları birleşimi gösteren grafik. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Birleşim")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Nasıl yapılır: dize koleksiyonlarını (LINQ) (C#) birleştirme ve karşılaştırma](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [Nasıl yapılır: (LINQ) (C#) iki liste arasında ayarlanmış farkı bulma](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
