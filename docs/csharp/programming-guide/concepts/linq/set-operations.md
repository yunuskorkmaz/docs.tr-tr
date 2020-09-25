---
title: Ayarlama Işlemleri (C#)
description: C# ' de LINQ içinde ayarlanan işlemleri gerçekleştiren ayarlama işlemleri ve standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 8679f804adaaeada390206e3e1dd2a0711a2cbf6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195616"
---
# <a name="set-operations-c"></a>Ayarlama Işlemleri (C#)

LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.  
  
 Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu Ifadesi sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Yinelenen değerleri bir koleksiyondan kaldırır.|Geçerli değildir.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Dışlama|İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Kesiştir|Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Birleşim|İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Ayarlama Işlemlerinin karşılaştırması  
  
### <a name="distinct"></a>Distinct  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> bir karakter dizisi üzerinde yönteminin davranışını gösterir. Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.  
  
 ![Ayrı&#40;&#41; davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a>Dışlama  

 Aşağıdaki örnek, davranışını gösterir <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> . Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.  
  
 ![&#40;&#41; hariç eylemi gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a>Kesiştir  

 Aşağıdaki örnek, davranışını gösterir <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> . Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.  
  
 ![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a>Birleşim  

 Aşağıdaki örnek iki karakter dizisi üzerinde bir bileşim işlemini gösterir. Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.  
  
 ![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)
- [Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)
- [İki liste arasındaki küme farkını bulma (LINQ) (C#)](./how-to-find-the-set-difference-between-two-lists-linq.md)
