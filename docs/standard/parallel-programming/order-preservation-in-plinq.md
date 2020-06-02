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
ms.openlocfilehash: 45752f3ffa64079079505934afd76e812daad7bd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290661"
---
# <a name="order-preservation-in-plinq"></a>PLINQ'te Sıra Koruma
PLıNQ 'te hedef, doğruluğu sürdürirken performansı en üst düzeye çıkarmaktır. Bir sorgu mümkün olduğunca hızlı çalışmalıdır, ancak yine de doğru sonuçları üretir. Bazı durumlarda doğruluk, kaynak sırasının sırasını gerektirir; Ancak, sıralama hesaplama açısından pahalı olabilir. Bu nedenle, varsayılan olarak PLıNQ, kaynak sırasının sırasını korumaz. Bu şekilde, PLıNQ benzerdir, [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] ancak sıralamayı koruyan LINQ to Objects farklı değildir.  
  
 Varsayılan davranışı geçersiz kılmak için, kaynak dizideki işlecini kullanarak sıra korumasını açabilirsiniz <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> . Daha sonra yöntemi kullanarak sorgu içinde sıra korumasını kapatabilirsiniz <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> . Her iki yöntemle de sorgu, sorgunun paralel veya sıralı olarak yürütülüp yürütülmeyeceğini tespit eden buluşsal yöntemler temelinde işlenir. Daha fazla bilgi için bkz. [PLıNQ 'Te hızlı Hızlandırlamayı anlama](understanding-speedup-in-plinq.md).  
  
 Aşağıdaki örnek, sonuçları herhangi bir şekilde bildirmeye çalışmamak zorunda kalmadan, bir koşulla eşleşen tüm öğeler için filtre uygulayan sıralanmamış bir paralel sorgu gösterir.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Bu sorgu, koşulu karşılayan kaynak dizide ilk 1000 şehri üretmeyebilir, ancak koşulu karşılayan bazı 1000 şehirlerin bir kümesini oluşturur. PLıNQ sorgu işleçleri, kaynak diziyi, eşzamanlı görevler olarak işlenen birden çok subsequences olarak bölümleyin. Sıra koruması belirtilmemişse, her bölümden elde edilen sonuçlar, sorgunun bir sonraki aşamasına rastgele bir sırayla geçirilir. Ayrıca, bir bölüm kalan öğeleri işlemeye devam etmeden önce sonuçlarının bir alt kümesini verebilir. Elde edilen sıra her seferinde farklı olabilir. Uygulamanız, işletim sisteminin iş parçacıklarını nasıl zamanlamalarına bağlı olduğundan bunu kontrol edemez.  
  
 Aşağıdaki örnek, kaynak dizideki işlecini kullanarak varsayılan davranışı geçersiz kılar <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> . Bu, yönteminin, <xref:System.Linq.ParallelEnumerable.Take%2A> koşulu karşılayan kaynak dizideki ilk 1000 şehri döndürmesini sağlar.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Ancak, bu sorgu büyük olasılıkla sıralanmamış sürüm kadar hızlı çalışmaz, çünkü bölümler genelinde orijinal sıralamayı takip etmelidir ve birleştirme sırasında sıralamanın tutarlı olduğundan emin olun. Bu nedenle, yalnızca <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> gerekli olduğunda ve yalnızca sorgunun gerektirdiği parçalar için kullanmanızı öneririz. Sıraya saklama işlemi artık gerekmiyorsa, <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> bunu kapatmak için kullanın. Aşağıdaki örnek, iki sorgu oluşturarak bunu elde eder.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 PLıNQ 'nın, sorgunun geri kalanı için Order-prodüme işleçleri tarafından üretilen bir dizinin sıralamasını koruyabileceğini unutmayın. Diğer bir deyişle, ve gibi işleçler <xref:System.Linq.ParallelEnumerable.OrderBy%2A> , <xref:System.Linq.ParallelEnumerable.ThenBy%2A> öğesine yapılan bir çağrı tarafından izlenmiş gibi değerlendirilir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> .  
  
## <a name="query-operators-and-ordering"></a>Sorgu Işleçleri ve sıralaması  
 Aşağıdaki sorgu işleçleri bir sorgudaki sonraki tüm işlemlere sıra koruma sağlar veya şu şekilde <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> adlandırılır:  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Aşağıdaki PLıNQ sorgu işleçleri bazı durumlarda, doğru sonuçlar üretmek için sıralı kaynak dizileri gerektirebilir:  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Bazı PLıNQ sorgu işleçleri, kaynak sırasının sıralı veya sıralanmamış olmasına bağlı olarak farklı davranır. Aşağıdaki tabloda bu işleçler listelenmektedir.  
  
|Operatör|Kaynak sırası sipariş edildiğinde sonuç|Kaynak sırası sıralanmamış olduğunda sonuç|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|İlişkilendirilebilir olmayan veya işleme olmayan işlemler için belirleyici olmayan çıkış|İlişkilendirilebilir olmayan veya işleme olmayan işlemler için belirleyici olmayan çıkış|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|İlişkilendirilebilir olmayan veya işleme olmayan işlemler için belirleyici olmayan çıkış|İlişkilendirilebilir olmayan veya işleme olmayan işlemler için belirleyici olmayan çıkış|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Belirtilen öğeyi döndür|Rastgele öğe|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Belirtilen öğeyi döndür|Rastgele öğe|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Sıralanmamış sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Belirtilen öğeyi döndür|Rastgele öğe|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Belirtilen öğeyi döndür|Rastgele öğe|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Belirleyici olmayan bir şekilde paralel olarak yürütür|Belirleyici olmayan bir şekilde paralel olarak yürütür|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Belirtilen öğeyi döndür|Rastgele öğe|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Belirtilen öğeyi döndür|Rastgele öğe|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Sırayı yeniden sipariş edin|Yeni sıralı Bölüm başlatır|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Sırayı yeniden sipariş edin|Yeni sıralı Bölüm başlatır|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Uygulanamaz (aynı varsayılan değer <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Uygulanamaz (aynı varsayılan değer <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Çevirir|Hiçbir şey yapılmaz|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>oluşturulmayacak|Düzenli sonuçlar|Sırasız sonuçlar.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Düzenli sonuçlar.|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>oluşturulmayacak|Düzenli sonuçlar.|Sırasız sonuçlar.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Sıralı karşılaştırma|Sırasız karşılaştırma|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|İlk *n* öğeyi atlar|*N* öğeyi atlar|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Düzenli sonuçlar.|Belirleyici olmayan. Geçerli rastgele sırada Skipon gerçekleştirir|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|İlişkilendirilebilir olmayan veya işleme olmayan işlemler için belirleyici olmayan çıkış|İlişkilendirilebilir olmayan veya işleme olmayan işlemler için belirleyici olmayan çıkış|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|İlk `n` öğeleri alır|Herhangi bir `n` öğeyi alır|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Düzenli sonuçlar|Belirleyici olmayan. Geçerli rastgele sırada TakeWhile gerçekleştirir|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Güvenliği`OrderBy`|Güvenliği`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Güvenliği`OrderBy`|Güvenliği`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Uygulanamaz|Uygulanamaz|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>oluşturulmayacak|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Düzenli sonuçlar|Sıralanmamış sonuçlar|  
  
 Sıralanmamış sonuçlar etkin bir şekilde karıştırılır; yalnızca özel bir sıralama mantığı uygulanmaz. Bazı durumlarda, sıralanmamış bir sorgu kaynak dizinin sıralamasını koruyabilir. Dizinli Select işlecini kullanan sorgularda PLıNQ, çıkış öğelerinin, artan dizinler sırasıyla gelmesini güvence altına alır, ancak hangi dizinlerin hangi dizine atanacağını garanti etmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
- [Paralel programlama](index.md)
