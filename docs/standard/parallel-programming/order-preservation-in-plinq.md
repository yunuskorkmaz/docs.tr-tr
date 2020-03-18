---
title: PLINQ'te Sıra Koruma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
ms.openlocfilehash: 5b067fa277816e6105d37047c6c4996a4cbb9b5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138215"
---
# <a name="order-preservation-in-plinq"></a>PLINQ'te Sıra Koruma
PLINQ'de amaç, doğruluğu korurken performansı en üst düzeye çıkarmaktır. Bir sorgu mümkün olduğunca hızlı çalışmalı, ancak yine de doğru sonuçları üretmelidir. Bazı durumlarda, doğruluk kaynak sıranın sırasını korumayı gerektirir; ancak, sipariş hesaplamalı pahalı olabilir. Bu nedenle, varsayılan olarak, PLINQ kaynak sıranın sırasını korumaz. Bu bağlamda, PLINQ [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)]benzer , ancak linq nesnelere benzer, hangi sipariş korur.  
  
 Varsayılan davranışı geçersiz kılmak için, kaynak dizisinde <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işleci kullanarak sipariş korumayı açabilirsiniz. Daha sonra <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> yöntemi kullanarak sorguda daha sonra sipariş korumayı kapatabilirsiniz. Her iki yöntemde de sorgu, sorguyu paralel mi yoksa sıralı olarak mı yürüteceğini belirleyen buluşsal yöntemlere göre işlenir. Daha fazla bilgi için [PLINQ'da Çabuk'u Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.  
  
 Aşağıdaki örnek, sonuçları herhangi bir şekilde sıralamaya çalışmadan, bir koşulla eşleşen tüm öğeler için filtreleyen sıralanmamış bir paralel sorgugösterir.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Bu sorgu, koşulla tanışan kaynak dizisindeki ilk 1000 şehri değil, koşulu karşılayan 1000 şehir kümesini oluşturmaz. PLINQ sorgu operatörleri, kaynak sırasını eşzamanlı görevler olarak işlenen birden çok alt sıraya bölümler. Sipariş koruma belirtilmemişse, her bölümün sonuçları rasgele bir sırada sorgunun bir sonraki aşamasına teslim edilir. Ayrıca, bir bölüm kalan öğeleri işlemeye devam etmeden önce sonuçlarının bir alt kümesi ni verebilir. Ortaya çıkan sipariş her seferinde farklı olabilir. İşletim sisteminin iş parçacıklarını nasıl zamanladığına bağlı olduğundan uygulamanız bunu denetleyemez.  
  
 Aşağıdaki örnek, kaynak dizisinde <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işleci kullanarak varsayılan davranışı geçersiz kılar. Bu, yöntemin <xref:System.Linq.ParallelEnumerable.Take%2A> durumu karşılayan kaynak sırayla ilk 1000 şehri döndürmesini sağlar.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Ancak, bu sorgu büyük olasılıkla sıralanmamış sürüm kadar hızlı çalışmaz, çünkü bölümler boyunca özgün sıralamayı izlemesi ve birleştirme zamanında sıralamanın tutarlı olduğundan emin olması gerekir. Bu nedenle, yalnızca <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> gerekli olduğunda ve yalnızca sorgunun bunu gerektiren bölümleri için kullanmanızı öneririz. Sipariş in denkorunması artık <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> gerekli olmadığında, kapatmak için kullanın. Aşağıdaki örnek, iki sorgu oluşturarak bunu başarır.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 PLINQ sorgunun geri kalanı için sipariş heybetli işleçler tarafından üretilen bir dizi sırasını korur unutmayın. Başka bir deyişle, <xref:System.Linq.ParallelEnumerable.OrderBy%2A> gibi <xref:System.Linq.ParallelEnumerable.ThenBy%2A> işleçler ve onlar için <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>bir çağrı tarafından takip edildi sanki tedavi edilir.  
  
## <a name="query-operators-and-ordering"></a>Sorgu Operatörleri ve Sipariş  
 Aşağıdaki sorgu işleçleri, bir sorguda veya çağrılana kadar <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> sonraki tüm işlemlere sipariş koruma sını sunar:  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Aşağıdaki PLINQ sorgu işleçleri bazı durumlarda doğru sonuçlar üretmek için sıralı kaynak dizileri gerektirebilir:  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Bazı PLINQ sorgu işleçleri, kaynak sıralarının sıralanıp sıralanmadığına bağlı olarak farklı şekilde davranılır. Aşağıdaki tabloda bu işleçler listeleneb.)  
  
|İşleç|Kaynak sıralı sıralandığında sonuç|Kaynak sırası sırasız olduğunda sonuç|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Nonassosiyatif veya noncommutative operasyonlar için nondeterministic çıkış|Nonassosiyatif veya noncommutative operasyonlar için nondeterministic çıkış|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Nonassosiyatif veya noncommutative operasyonlar için nondeterministic çıkış|Nonassosiyatif veya noncommutative operasyonlar için nondeterministic çıkış|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Belirtilen öğeyi döndür|Rasgele öğe|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Belirtilen öğeyi döndür|Rasgele öğe|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Sıralanmamış sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Belirtilen öğeyi döndür|Rasgele öğe|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Belirtilen öğeyi döndür|Rasgele öğe|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Paralel olarak nondeterministically yürütür|Paralel olarak nondeterministically yürütür|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Belirtilen öğeyi döndür|Rasgele öğe|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Belirtilen öğeyi döndür|Rasgele öğe|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Sırayı yeniden sıralar|Yeni sipariş edilen bölümü başlatır|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Sırayı yeniden sıralar|Yeni sipariş edilen bölümü başlatır|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Geçerli değil (aynı <xref:System.Linq.ParallelEnumerable.AsParallel%2A> varsayılan)|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Geçerli değil (aynı <xref:System.Linq.ParallelEnumerable.AsParallel%2A>varsayılan)|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Ters -ine çevirir|Hiçbir şey yapılmaz|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(dizine eklenmiş)|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Sipariş sonuçları.|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(dizine eklenmiş)|Sipariş sonuçları.|Sıralanmamış sonuçlar.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Sipariş karşılaştırması|Sıralanmamış karşılaştırma|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|İlk *n* öğelerini atlar|Herhangi bir *n* öğeyi atlar|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Sipariş sonuçları.|Nondeterministic. Geçerli rasgele sırada SkipWhile gerçekleştirir|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Nonassosiyatif veya noncommutative operasyonlar için nondeterministic çıkış|Nonassosiyatif veya noncommutative operasyonlar için nondeterministic çıkış|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|İlk `n` öğeleri alır|Herhangi `n` bir öğe alır|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Sipariş edilen sonuçlar|Nondeterministic. Geçerli rasgele sırada TakeWhile gerçekleştirir|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Takviye -leri`OrderBy`|Takviye -leri`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Takviye -leri`OrderBy`|Takviye -leri`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(dizine eklenmiş)|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Sipariş edilen sonuçlar|Sıralanmamış sonuçlar|  
  
 Sıralanmamış sonuçlar etkin olarak karıştırılmaz; onlar sadece onlara uygulanan herhangi bir özel sipariş mantığı yok. Bazı durumlarda, sıralanmamış bir sorgu kaynak sıranın sırasını koruyabilir. Dizinlenmiş Select işleci kullanan sorgular için PLINQ, çıktı öğelerinin artan endeksler sırasına göre ortaya çıkaracağını garanti eder, ancak hangi endekslerin hangi öğelere atanacağı konusunda hiçbir garanti vermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
