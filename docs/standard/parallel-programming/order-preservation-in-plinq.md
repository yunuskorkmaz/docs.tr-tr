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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1587b2c4d19833c615c5a10a2fe0d6b28e854aca
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061526"
---
# <a name="order-preservation-in-plinq"></a>PLINQ'te Sıra Koruma
PLINQ'da hedef doğruluk sürdürürken performans en üst düzeye çıkarmaktır. Bir sorgu çalıştırmak mümkün olduğunca hızlı ancak yine de doğru sonuçlar gerekir. Bazı durumlarda, korunması için kaynak dizisinin sırasını doğruluk gerektirir; Ancak, sıralama hesaplama açısından pahalı olabilir. Bu nedenle, varsayılan olarak, PLINQ kaynak dizi sıralamasını korumaz. Bu bağlamda, PLINQ benzer [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ancak sıralamasını korumak, nesnelere LINQ,.  
  
 Varsayılan davranışı geçersiz kılmak için üzerinde sıra koruma kullanarak açabilirsiniz <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işlecinin kaynak dizi. Ardından daha sonra bir sorguda sıra koruma kullanarak devre dışı bırakabilirsiniz <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> yöntemi. Her iki yöntemde de sorgu, sorgu paralel olarak çalıştırılıp çalıştırılmayacağını buluşsal yöntemler temelinde veya sıralı olarak işlenir. Daha fazla bilgi için [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Aşağıdaki örnek, herhangi bir yolla sonuçlarını sıralama çalışmadan bir koşul ile eşleşen tüm öğeleri için filtreler bir sırasız paralel sorgu gösterir.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Bu sorgu, ancak bazı kümesi yerine koşula uyan 1000 şehirlerin koşula uyan ilk 1000 şehirleri kaynak dizisindeki üretmez. Sorgu işleçleri PLINQ kaynak sırasını eş zamanlı görevleri olarak işlenen birden çok sıraları bölümleme. Sıra koruma belirtilmezse, her bölüm sonuçlardan kapalı rastgele sırayla sorgunun sonraki aşamaya verilir. Ayrıca, kalan öğeleri işlemeye devam etmeden önce bir bölüm sonuçları kümesini hızlanmasını sağlayabilir. Sonuçta elde edilen sırayla her seferinde farklı olabilir. İşletim sistemi iş parçacıklarını nasıl zamanlar bağlı olduğundan, uygulamanızı bu denetleyemezsiniz.  
  
 Aşağıdaki örneği kullanarak, varsayılan davranışı geçersiz kılar <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işlecinin kaynak dizi. Bu, sağlar <xref:System.Linq.ParallelEnumerable.Take%2A> yöntemi ilk 1000 şehirleri koşula uyan kaynak sırasını döndürür.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Bölümler özgün sıralama izlemek ve birleştirme zaman sıralama tutarlı olmasını sağlamak gerekir çünkü Bununla birlikte, bu sorgu büyük olasılıkla sıralanmamış sürümü olarak hızlı şekilde çalışmaz. Bu nedenle, kullanmanızı öneririz <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> yalnızca gerekli olduğunda ve yalnızca gerektiren sorgunun bölümlerini. Sıra koruması artık gerekli olmadığında kullanın <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> devre dışı bırakmak için. Aşağıdaki örnek bunu iki sorguları bir araya getirerek ulaşır.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 PLINQ sorgu geri kalanı için sipariş izlenmesi işleçleri tarafından üretilen bir dizi sıralamasını koruyaraktan olduğunu unutmayın. Diğer bir deyişle, işleçler gibi <xref:System.Linq.ParallelEnumerable.OrderBy%2A> ve <xref:System.Linq.ParallelEnumerable.ThenBy%2A> bir çağrı tarafından takip gibi değerlendirilir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Sorgu işleçleri ve sıralama  
 Sıra koruması bir sorgu veya kadar tüm işlemler aşağıdaki sorgu işleçleri tanıtmak <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> çağrılır:  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Bazı durumlarda, aşağıdaki PLINQ sorgu işleçleri doğru sonuçlar için sıralanmış kaynak dizilerini gerektirebilir:  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Bazı PLINQ sorgu işleçleri, ister kendi kaynak dizisi sıralı sırasız veya bağlı olarak farklı davranır. Aşağıdaki tabloda bu işleçleri listelenir.  
  
|İşleç|Kaynak dizisi sıralandığında sonucu|Kaynak sırası sırasız olduğunda sonucu|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Belirleyici olmayan bir çıkış nonassociative veya noncommutative işlemler için|Belirleyici olmayan bir çıkış nonassociative veya noncommutative işlemler için|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Belirleyici olmayan bir çıkış nonassociative veya noncommutative işlemler için|Belirleyici olmayan bir çıkış nonassociative veya noncommutative işlemler için|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Belirtilen öğeyi döndürür|Rastgele bir öğe|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Belirtilen öğeyi döndürür|Rastgele bir öğe|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Sırasız sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Belirtilen öğeyi döndürür|Rastgele bir öğe|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Belirtilen öğeyi döndürür|Rastgele bir öğe|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Belirleyici olmayan şekilde paralel olarak yürütür|Belirleyici olmayan şekilde paralel olarak yürütür|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Belirtilen öğeyi döndürür|Rastgele bir öğe|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Belirtilen öğeyi döndürür|Rastgele bir öğe|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Sıra yeniden sıralar.|Yeni bölüm sıralı başlatır|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Sıra yeniden sıralar.|Yeni bölüm sıralı başlatır|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Geçerli değil (aynı varsayılan olarak <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Geçerli değil (aynı varsayılan olarak <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Tersine çevirir|Hiçbir şey yapılmaz|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (dizinlenmiş)|Sıralanmış sonuçları|Sırasız sonuçları.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Sıralanmış sonuçları.|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (dizinlenmiş)|Sıralanmış sonuçları.|Sırasız sonuçları.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Sıralı karşılaştırma|Sırasız karşılaştırma|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|İlk atlar *n* öğeleri|Tüm atlar *n* öğeleri|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Sıralanmış sonuçları.|Belirleyici olmayan. SkipWhile geçerli rastgele siparişin gerçekleştirir.|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Belirleyici olmayan bir çıkış nonassociative veya noncommutative işlemler için|Belirleyici olmayan bir çıkış nonassociative veya noncommutative işlemler için|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|İlk alan `n` öğeleri|Herhangi bir alan `n` öğeleri|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Sıralanmış sonuçları|Belirleyici olmayan. TakeWhile geçerli rastgele siparişin gerçekleştirir.|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Eklerin `OrderBy`|Eklerin `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Eklerin `OrderBy`|Eklerin `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (dizinlenmiş)|Sıralanmış sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Sıralanmış sonuçları|Sırasız sonuçları|  
  
 Sırasız sonuçları etkin olarak karışık değil; Bunlar yalnızca uygulanmış herhangi özel bir sıralama mantık yok. Bazı durumlarda, sırasız bir sorgu, kaynak dizi sıralamasını korumak. Dizinli seçme işlecini kullanan sorgular için PLINQ, çıkış öğeleri artan dizinlerini ancak hangi dizinlerin tutarlılık garantisi için hangi öğelerin atanacak yapar sırasına göre gelir olduğunu garanti eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
