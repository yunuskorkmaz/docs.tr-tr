---
title: "Ayarlama işlemleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a>Ayarlama işlemleri (Visual Basic)
Ayarlama işlemleri LINQ varlığının veya yokluğunun aynı ya da ayrı koleksiyonlar (veya içindeki ayarlar) eşdeğer öğelerinin temel alan bir sonuç kümesi oluşturan sorgu işlemlerini bakın.  
  
 Ayarlama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|Yinelenen değerleri koleksiyondan kaldırır.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
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
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki örnek kullanır `Distinct` benzersiz numaraları tamsayılar listesinden döndürmek için bir LINQ sorgu yan tümcesinde.  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Distinct tümcesi](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Nasıl yapılır: dize koleksiyonlarını (LINQ) (Visual Basic) birleştirme ve karşılaştırma](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [Nasıl yapılır: iki liste (LINQ) (Visual Basic) arasında ayarlanmış farkı bulma](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
