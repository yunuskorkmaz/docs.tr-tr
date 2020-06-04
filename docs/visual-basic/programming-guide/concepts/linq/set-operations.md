---
title: Ayarlama İşlemleri
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406826"
---
# <a name="set-operations-visual-basic"></a>Işlemleri ayarlama (Visual Basic)

LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.

Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.

## <a name="methods"></a>Yöntemler

|Yöntem adı|Description|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|Yinelenen değerleri bir koleksiyondan kaldırır.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|Dışlama|İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|Kesiştir|Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|Birleşim|İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>Ayarlama Işlemlerinin karşılaştırması

### <a name="distinct"></a>Distinct

Aşağıdaki çizim, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> bir karakter dizisi üzerinde yönteminin davranışını gösterir. Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.

![Ayrı&#40;&#41; davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>Dışlama

Aşağıdaki çizimde davranışını gösterilmektedir <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> . Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.

![&#40;&#41; hariç eylemi gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")

### <a name="intersect"></a>Kesiştir

Aşağıdaki çizimde davranışını gösterilmektedir <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> . Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.

![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>Birleşim

Aşağıdaki çizimde iki karakter dizisi üzerinde bir bileşim işlemi gösterilmektedir. Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.

![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği

Aşağıdaki örnek, `Distinct` bir tamsayı listesinden benzersiz sayıları döndürmek için BIR LINQ sorgusunda yan tümcesini kullanır.

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Distinct Yan Tümcesi](../../../language-reference/queries/distinct-clause.md)
- [Nasıl yapılır: dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)
- [Nasıl yapılır: Iki liste arasındaki küme farkını bulma (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)
