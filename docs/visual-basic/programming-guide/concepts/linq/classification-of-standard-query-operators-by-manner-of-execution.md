---
title: Standart sorgu Işleçleri yürütme yöntemine göre sınıflandırma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
ms.openlocfilehash: e89c58707b4980b208395cce67434a6e5efa5d22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939264"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>Standart sorgu Işleçleri yürütme yöntemine göre sınıflandırma (Visual Basic)
Standart sorgu işleci yöntemlerinin LINQ to Objects uygulamaları iki ana yöntemden biriyle yürütülür: ımımor ertelenmiş. Ertelenmiş yürütmeyi kullanan sorgu işleçleri Ayrıca iki kategoriye ayrılabilir: akış ve akış olmayan. Farklı sorgu işleçlerinin nasıl yürütüleceğini biliyorsanız, belirli bir sorgudan aldığınız sonuçları anlamanıza yardımcı olabilir. Bu, veri kaynağı değiştirilirken veya başka bir sorgunun üstünde bir sorgu oluşturuyorsanız özellikle doğrudur. Bu konu, standart sorgu işleçlerini yürütme tarzlarına göre sınıflandırır.  
  
## <a name="manners-of-execution"></a>Yürütme mananlar  
  
### <a name="immediate"></a>Hemen  
 Anında yürütme, veri kaynağının okunduğu ve işlemin sorgunun bildirildiği noktada gerçekleştirildiği anlamına gelir. Tek, Numaralandırılmamış bir sonuç döndüren tüm standart sorgu işleçleri hemen yürütülür.  
  
### <a name="deferred"></a>Ertelenmiş  
 Ertelenmiş yürütme, işlemin sorgunun bildirildiği noktada gerçekleştirilmediği anlamına gelir. İşlem yalnızca sorgu değişkeni numaralandırıldıktan sonra, örneğin bir `For Each` ifade kullanılarak yapılır. Bu, sorguyu yürütmenin sonuçlarının sorgu tanımlandığında değil, sorgu yürütüldüğünde veri kaynağının içeriğine bağlı olduğunu gösterir. Sorgu değişkeni birden çok kez numaralandırıldıktan sonra sonuçlar her seferinde farklılık gösterebilir. Dönüş türü <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IOrderedEnumerable%601> ertelenmiş bir şekilde yürütülen tüm standart sorgu işleçleri neredeyse hepsi.  
  
 Ertelenmiş yürütmeyi kullanan sorgu işleçleri ayrıca akış veya akış olmayan olarak sınıflandırılabilirler.  
  
#### <a name="streaming"></a>Akış  
 Akış işleçleri, öğeleri almadan önce tüm kaynak verileri okumak zorunda değildir. Yürütme sırasında, bir akış işleci her kaynak öğe okunışında işlemini gerçekleştirir ve uygunsa öğeyi verir. Bir akış işleci, bir sonuç öğesi üretilene kadar kaynak öğeleri okumaya devam eder. Bu, bir sonuç öğesi oluşturmak için birden fazla kaynak öğesinin okunabileceğini gösterir.  
  
#### <a name="non-streaming"></a>Akış olmayan  
 Akış olmayan operatörler, bir sonuç öğesi elde etmeden önce tüm kaynak verileri okummalıdır. Sıralama veya gruplama gibi işlemler bu kategoriye girer. Yürütme sırasında akış olmayan sorgu işleçleri tüm kaynak verileri okur, veri yapısına koyar, işlemi gerçekleştirir ve sonuçta elde edilen öğeleri verir.  
  
## <a name="classification-table"></a>Sınıflandırma tablosu  
 Aşağıdaki tabloda, her standart sorgu operatörü yöntemi yürütme yöntemine göre sınıflandırılırdı.  
  
> [!NOTE]
> Bir işleç iki sütunda işaretlenmişse, işleme iki giriş dizisi dahil edilir ve her sıra farklı şekilde değerlendirilir. Bu durumlarda, parametre listesindeki her zaman, ertelenmiş, akış halinde değerlendirilen ilk dizidir.  
  
|Standart sorgu Işleci|Dönüş Türü|Hemen Yürütme|Ertelenmiş akış yürütme|Ertelenmiş akış olmayan yürütme|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|Tek sayısal değer|X|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A>|Tek sayısal değer, TSource veya TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|Tek sayısal değer, TSource veya TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A>|Tek sayısal değer|X|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A>|TSource dizisi|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
