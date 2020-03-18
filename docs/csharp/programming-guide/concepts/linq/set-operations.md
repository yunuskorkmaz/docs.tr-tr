---
title: İşlemleri Ayarla (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 44a145a625b5e2e16d2469b20f8cfda1858560a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167939"
---
# <a name="set-operations-c"></a>İşlemleri Ayarla (C#)
LINQ'daki işlemleri ayarlayın, aynı veya ayrı koleksiyonlarda (veya kümelerde) eşdeğer öğelerin varlığına veya yokluğuna dayanan bir sonuç kümesi oluşturan sorgu işlemlerine başvurur.  
  
 Set işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Yinelenen değerleri koleksiyondan kaldırır.|Geçerli değildir.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Dışlama|Küme farkını döndürür, bu da ikinci bir koleksiyonda görünmeyen bir koleksiyonun öğeleri anlamına gelir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Kesiştir|İki koleksiyonun her birinde görünen öğeler anlamına gelen ayarlı kesişimi döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Birleşim|İki koleksiyondan birinde görünen benzersiz öğeler anlamına gelen küme birliğini döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Set İşlemlerinin Karşılaştırılması  
  
### <a name="distinct"></a>Distinct  
 Aşağıdaki örnekte, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemin bir karakter dizisi üzerindeki davranışı gösterilmiştir. Döndürülen dizi, giriş dizisinden benzersiz öğeleri içerir.  
  
 ![Distinct&#40;&#41; davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a>Dışlama  
 Aşağıdaki örnekte <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Döndürülen dizi yalnızca ikinci giriş dizisinde olmayan ilk giriş dizisinden öğeler içerir.  
  
 ![&#40;&#41; Hariç'in eylemini gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Except'Un davranışını gösterir.")  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a>Kesiştir  
 Aşağıdaki örnekte <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Döndürülen dizi, her iki giriş dizisinde de ortak olan öğeleri içerir.  
  
 ![İki dizinin kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a>Birleşim  
 Aşağıdaki örnek, iki karakter dizisi üzerinde birleşim işlemi dir. Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.  
  
 ![İki dizinin birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)
- [İki liste (LINQ) (C#) arasındaki küme farkı nasıl bulabilirim?](./how-to-find-the-set-difference-between-two-lists-linq.md)
