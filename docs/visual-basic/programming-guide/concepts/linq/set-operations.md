---
title: Işlemleri ayarlama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: fe8dbff00ecd6da9b3b0e9792e67422583a00180
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582916"
---
# <a name="set-operations-visual-basic"></a>Işlemleri ayarlama (Visual Basic)

LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.

Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.

## <a name="methods"></a>Yöntemler

|Yöntem adı|Açıklama|Sorgu Ifadesi söz dizimini Visual Basic|Daha fazla bilgi|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|Yinelenen değerleri bir koleksiyondan kaldırır.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|Dışlama|İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.|Yok.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|Kesiştir|Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.|Yok.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|UNION|İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.|Yok.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>Ayarlama Işlemlerinin karşılaştırması

### <a name="distinct"></a>Distinct

Aşağıdaki çizimde, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yönteminin bir karakter dizisinde davranışı gösterilmektedir. Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.

![DISTINCT&#40;&#41;davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>Dışlama

Aşağıdaki çizimde <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> davranışı gösterilmektedir. Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.

![Haricinde&#40;&#41;eylemini gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")

### <a name="intersect"></a>Kesiştir

Aşağıdaki çizimde <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> davranışı gösterilmektedir. Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.

![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>UNION

Aşağıdaki çizimde iki karakter dizisi üzerinde bir bileşim işlemi gösterilmektedir. Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.

![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği

Aşağıdaki örnek, bir LINQ sorgusunda `Distinct` yan tümcesini kullanarak tamsayı listesinden benzersiz sayılar döndürür.

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Distinct Yan Tümcesi](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Nasıl yapılır: dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [Nasıl yapılır: Iki liste arasındaki küme farkını bulma (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
