---
title: Işlemleri ayarla (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: cea0c0ba4dd6c7f874f69e3ec4a179248397b67d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591121"
---
# <a name="set-operations-c"></a>Işlemleri ayarla (C#)
LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.  
  
 Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Yinelenen değerleri bir koleksiyondan kaldırır.|Geçerli değildir.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Dışlama|İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Kesiştir|Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|UNION|İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Ayarlama Işlemlerinin karşılaştırması  
  
### <a name="distinct"></a>Distinct  
 Aşağıdaki çizim, bir karakter dizisi üzerinde <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yönteminin davranışını gösterir. Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.  
  
 ![DISTINCT&#40;&#41;davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a>Dışlama  
 Aşağıdaki çizimde davranışını <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>gösterilmektedir. Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.  
  
 ![&#40;Haricinde&#41;eylemini gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")  
  
### <a name="intersect"></a>Kesiştir  
 Aşağıdaki çizimde davranışını <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>gösterilmektedir. Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.  
  
 ![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a>UNION  
 Aşağıdaki çizimde iki karakter dizisi üzerinde bir bileşim işlemi gösterilmektedir. Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.  
  
 ![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [Nasıl yapılır: Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)
- [Nasıl yapılır: Iki liste arasındaki (LINQ) (C#) küme farkını bulma](./how-to-find-the-set-difference-between-two-lists-linq.md)
