---
title: Standart sorgu işleçlerinin yöntemine göre sınıflandırılması yürütme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
ms.openlocfilehash: 6331ad0994e121d2d7007c9999f3a684b83efe6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021771"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>Standart sorgu işleçlerinin yöntemine göre sınıflandırılması yürütme (Visual Basic)
Standart sorgu işleci yöntemleri nesneleri uygulamalarına LINQ iki ana yoldan biriyle yürütün: hemen veya ertelenmiş. Ertelenmiş yürütme kullanan sorgu işleçler ek olarak iki kategoriye ayrılabilir: akış ve akış dışı. Nasıl farklı sorgu işleçlerinin yürütme biliyorsanız, belirli bir sorgudan Al sonuçları anlamanıza yardımcı olabilir. Bu veri kaynağı değiştiğinde veya başka bir sorgu üzerinde bir sorgu oluşturuyorsanız özellikle doğrudur. Bu konuda, standart sorgu işleçlerinin yürütme kendi şekilde göre sınıflandırır.  
  
## <a name="manners-of-execution"></a>Yolla yürütme  
  
### <a name="immediate"></a>Hemen  
 Hemen yürütme, veri kaynağını okuyun ve işlem kodda bir noktada sorgu burada bildirilir gerçekleştirilir anlamına gelir. Numaralandırılabilir olmayan, tek bir sonuç tüm standart sorgu işleçleri hemen yürütün.  
  
### <a name="deferred"></a>Ertelenmiş  
 Ertelenmiş yürütme işlemi kodda bir noktada sorgu burada bildirilir yapılmaz, anlamına gelir. Yalnızca bir sorgu değişkeni, örneğin kullanarak numaralandırılana işlemi gerçekleştirilir bir `For Each` deyimi. Bu sorgu zaman tanımlanan yerine sorgu yürütüldüğünde sorgu yürütülürken sonuçlarını veri kaynağı içeriğine bağlı anlamına gelir. Sorgu değişkeni birden çok kez numaralandırılana, sonuçları her seferinde farklı olabilir. Dönüş türü olan neredeyse tüm standart sorgu işleçleri <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IOrderedEnumerable%601> ertelenmiş bir şekilde yürütün.  
  
 Ertelenmiş yürütme kullanan bir sorgu işleçleri, ayrıca akış veya akış dışı olarak sınıflandırılabilir.  
  
#### <a name="streaming"></a>Akış  
 Akış işleçleri bunlar öğeleri yield önce tüm kaynak verileri okumak yok. Okunan ve uygunsa öğe verir, yürütme sırasında bir akış işleci her kaynak öğesi kendi işlemi gerçekleştirir. Bir akış işleci, bir sonuç öğesi üretilen kadar kaynak öğeleri okumak devam eder. Başka bir deyişle, bir sonuç öğesi oluşturmak için birden fazla kaynak öğesi okuma.  
  
#### <a name="non-streaming"></a>Akış dışı  
 Akış dışı işleçler, bir sonuç öğesi yol açabilir önce tüm kaynak verilerini okuyun gerekir. Sıralama veya gruplama gibi operations, bu kategoriye girer. Yürütme zamanında akış dışı işleçler sorgu tüm kaynak verileri okumasını, bir veri yapısına yerleştirin, işlemi gerçekleştirmek ve verim elde edilen öğeleri.  
  
## <a name="classification-table"></a>Sınıflandırma tablo  
 Aşağıdaki tabloda her standart sorgu işleci yöntem yürütme yönteminin göre sınıflandırır.  
  
> [!NOTE]
>  Bir işleç iki sütun olarak işaretlenmişse, iki giriş dizilerini işlemde katılan ve her sırası farklı olarak kabul edilir. Bu durumlarda, her zaman değerlendirilir parametre listesindeki ilk dizi olduğu şekilde ertelenmiş, akış.  
  
|Standart sorgu işleci|Dönüş Türü|Hemen Yürütme|Akış ertelenmiş yürütme|Akış dışı yürütme ertelendi|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|Tek bir sayısal değer|X|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A>|Tek bir sayısal değer, Tkaynak veya TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|Tek bir sayısal değer, Tkaynak veya TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|Tkaynak|X|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A>|Tek bir sayısal değer|X|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A>|Tkaynak dizi|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu işleçleri (Visual Basic) için sorgu ifade sözdizimi](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [LINQ to Objects'in (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
