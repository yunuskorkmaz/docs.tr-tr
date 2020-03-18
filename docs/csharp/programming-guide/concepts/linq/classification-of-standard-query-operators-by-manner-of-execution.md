---
title: Standart Sorgu Operatörlerinin Yürütme Şekline Göre Sınıflandırılması (C#)
ms.date: 07/20/2015
ms.assetid: b9435ce5-a7cf-4182-9f01-f3468a5533dc
ms.openlocfilehash: ccf8fced5c92ceaaf84f9240e235da0e2b56ac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924287"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-c"></a>Standart Sorgu Operatörlerinin Yürütme Şekline Göre Sınıflandırılması (C#)
Standart sorgu işleci yöntemlerinin Nesnelere LINQ uygulamaları iki ana yoldan biriyle yürütülür: hemen veya ertelenmiş. Ertelenmiş yürütme kullanan sorgu işleçleri ayrıca iki kategoriye ayrılabilir: akış ve akış dışı. Farklı sorgu işleçleri nasıl yürütülür biliyorsanız, belirli bir sorgudan elde ettiğiniz sonuçları anlamanıza yardımcı olabilir. Bu, özellikle veri kaynağı değişiyorsa veya başka bir sorgunun üstüne bir sorgu oluşturuyorsanız geçerlidir. Bu konu, standart sorgu işleçlerini yürütme biçimlerine göre sınıfa alır.  
  
## <a name="manners-of-execution"></a>İdam Görgüleri  
  
### <a name="immediate"></a>Hemen  
 Hemen yürütme, veri kaynağının okunduğu ve işlemin sorgunun bildirildiği koddaki noktada gerçekleştirildiği anlamına gelir. Tek bir, sayısal olmayan sonuç döndüren tüm standart sorgu işleçleri hemen yürütülür.  
  
### <a name="deferred"></a>Ertelen -miş  
 Ertelenmiş yürütme, işlemin sorgunun bildirildiği koddaki noktada gerçekleştirilmediği anlamına gelir. İşlem yalnızca sorgu değişkeni numaralandırıldığında, örneğin bir `foreach` deyim kullanılarak gerçekleştirilir. Bu, sorgutanımlandığında değil, sorgu yürütüldüğünde sorgunun yürütülmesinin sonuçlarının veri kaynağının içeriğine bağlı olduğu anlamına gelir. Sorgu değişkeni birden çok kez numaralandırılırsa, sonuçlar her seferinde farklı olabilir. İade türü ertelenmiş bir şekilde <xref:System.Collections.Generic.IEnumerable%601> olan <xref:System.Linq.IOrderedEnumerable%601> veya çalıştırılan hemen hemen tüm standart sorgu işleçleri.  
  
 Ertelenmiş yürütme kullanan sorgu işleçleri ayrıca akış veya akış dışı olarak sınıflandırılabilir.  
  
#### <a name="streaming"></a>Akış  
 Akış işleçleri, öğeleri verim önce tüm kaynak verileri okumak zorunda değildir. Yürütme sırasında, bir akış işleci okundukça her kaynak öğesi üzerinde işlemini gerçekleştirir ve uygunsa öğeyi verir. Bir akış işleci, sonuç öğesi üretilene kadar kaynak öğeleriokumaya devam ediyor. Bu, bir sonuç öğesi oluşturmak için birden fazla kaynak öğesinin okunabileceği anlamına gelir.  
  
#### <a name="non-streaming"></a>Akış Dışı  
 Akış dışı işleçler, bir sonuç öğesi verebilmeleri için tüm kaynak verileri okumalıdır. Sıralama veya gruplandırma gibi işlemler bu kategoriye girer. Yürütme sırasında, akış sızak sorgu işleçleri tüm kaynak verileri okur, bir veri yapısına koyar, işlemi gerçekleştirir ve elde edilen öğeleri verir.  
  
## <a name="classification-table"></a>Sınıflandırma Tablosu  
 Aşağıdaki tablo, her standart sorgu işleci yöntemini yürütme yöntemine göre sınıflanır.  
  
> [!NOTE]
> Bir işleç iki sütunda işaretlenirse, işlemde iki giriş dizisi yer aldı ve her dizi farklı şekilde değerlendirilir. Bu gibi durumlarda, parametre listesinde her zaman ertelenmiş, akışlı bir şekilde değerlendirilen ilk sıradır.  
  
|Standart Sorgu Operatörü|Dönüş Türü|Hemen Yürütme|Ertelenmiş Akış Yürütme|Ertelenmiş Akışsız Yürütme|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|Tsource|X|||  
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
|<xref:System.Linq.Enumerable.ElementAt%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|Tsource|X|||  
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
|<xref:System.Linq.Enumerable.Single%2A>|Tsource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|Tsource|X|||  
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
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Standart Sorgu Operatörleri için Sorgu İfade Sözdizimi (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Nesnelere LINQ (C#)](./linq-to-objects.md)
