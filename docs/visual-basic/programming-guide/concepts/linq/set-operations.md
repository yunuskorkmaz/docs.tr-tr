---
title: Ayarlama işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 59ab09607462c762758e6a246ec218a92e01f5de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786885"
---
# <a name="set-operations-visual-basic"></a>Ayarlama işlemleri (Visual Basic)
LINQ ayarlama işlemleri varlığı veya yokluğu, eşdeğer öğelerin aynı veya farklı koleksiyonlar (veya kümeleri) temel alan bir sonuç kümesi oluşturan sorgu işlemleri bakın.  
  
 Ayarlama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|Yinelenen değerleri bir koleksiyondan kaldırır.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Dışlama|İkinci bir koleksiyon içinde görünmeyen bir koleksiyon öğelerini anlamına gelir ayarlanmış farkı döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Kesiştir|Her iki koleksiyon içinde görünen öğelerin anlamına gelir küme kesişimini döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|UNION|İki koleksiyon birini görünen benzersiz öğeleri anlamına gelir küme birleşimi döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Ayarlama işlemleri karşılaştırması  
  
### <a name="distinct"></a>Distinct  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemi bir karakter dizisi. Döndürülen dizi Giriş dizisinin benzersiz öğeleri içerir.  
  
 ![DISTINCT davranışını gösteren grafik&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a>Dışlama  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Döndürülen dizinin ikinci giriş dizisi içinde olmayan yalnızca öğeleri ilk giriş dizisi içerir.  
  
 ![Eylemi gösteren grafik dışında&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Davranışını gösteren dışında.")  
  
### <a name="intersect"></a>Kesiştir  
 Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Döndürülen dizi hem giriş dizilerini için ortak olan öğeleri içerir.  
  
 ![İki dizinin kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)    
### <a name="union"></a>UNION  
 Aşağıdaki çizimde, iki sıranın karakterlerin bir birleşim işlemi gösterilmektedir. Döndürülen dizinin iki giriş dizilerini benzersiz öğeleri içerir.  
  
 ![İki dizinin birleşimi gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)    
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki örnekte `Distinct` benzersiz sayı tamsayılar listesinden döndürmek için bir LINQ sorgu yan tümcesi.  
  
 [!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Distinct Yan Tümcesi](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Nasıl yapılır: Birleştirme ve karşılaştırma (LINQ) (Visual Basic) dize koleksiyonları](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [Nasıl yapılır: (LINQ) (Visual Basic) iki liste arasında ayarlanmış farkı bulma](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
