---
title: "PLINQ'te Sıra Koruma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 164dce7c58e1ce44972e0e390e4f0bf2be8de548
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="order-preservation-in-plinq"></a>PLINQ'te Sıra Koruma
PLINQ'te, doğruluk koruyarak performansını en üst düzeye çıkarmak için belirtilir. Bir sorgu çalıştırmak mümkün olduğunca hızlı ancak hala doğru sonuçlar gerekir. Bazı durumlarda, doğruluk korunması için kaynak sıradaki sırasını gerektirir; Ancak, sıralama hesaplama açısından pahalı olabilir. Bu nedenle, varsayılan olarak, kaynak sıradaki sırasını PLINQ korumaz. Bu bağlamda PLINQ benzer [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], hangi sıralama korumak LINQ, nesnelere değil.  
  
 Varsayılan davranışı geçersiz kılmak için sıra koruma üzerinde kullanarak bırakabilir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> kaynak sıradaki işlecinin. Sonra sorgudaki daha sonra sıra koruma kullanarak devre dışı bırakabilirsiniz <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> yöntemi. Her iki yöntemde de sorgu sorgu paralel olarak çalıştırılıp çalıştırılmayacağını buluşsal yöntemler temelinde veya sıralı olarak işlenir. Daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Aşağıdaki örnek, bir koşul herhangi bir şekilde sonuçları sıralamak çalışmadan eşleşen tüm öğeler için filtreler sırasız bir paralel sorgu gösterir.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Bu sorgu koşula 1000 Şehir yerine bazı kümesi ancak koşulu karşılayan kaynak sıradaki ilk 1000 şehirlerde üretmez. PLINQ sorgu işleçleri eş zamanlı görevleri olarak işlenen birden çok sıraları içine kaynak sırası bölüm. Sıra koruma belirtilmezse, her bölüm sonuçlarından kapalı sorgu rastgele sırayla sonraki aşaması verilir. Ayrıca, kalan öğeleri işlemeye devam etmeden önce bir bölüm sonuçları kümesini verim. Sonuçta elde edilen sırası her zaman farklı olabilir. İşletim sistemi iş parçacıklarının nasıl zamanlar bağımlı olduğundan, uygulamanız bu denetleyemezsiniz.  
  
 Aşağıdaki örnek, kullanarak varsayılan davranışı geçersiz kılmaları <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> kaynak sıradaki işlecinin. Bu sağlar <xref:System.Linq.ParallelEnumerable.Take%2A> yöntemi ilk 1000 Şehir koşulu karşılayan kaynak sırasını döndürür.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Özgün bölümleri sıralama kaydını gerekir ve birleştirme zaman sıralama tutarlı olduğundan emin olun çünkü ancak, bu sorgu büyük olasılıkla düzenlenmemiş sürüm kadar hızlı çalışmaz. Bu nedenle, kullanmanızı öneririz <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> yalnızca gerekli olduğunda ve yalnızca gerektiren sorgunun bölümlerini. Sıra koruma artık gerekli olmadığında kullan <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> devre dışı bırakmak için. Aşağıdaki örnekte iki sorguları oluşturma tarafından elde eder.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 PLINQ sorgu geri kalanı için sipariş etkileyici işleçleri tarafından üretilen bir dizi sıralama korur unutmayın. Diğer bir deyişle, işleçler gibi <xref:System.Linq.ParallelEnumerable.OrderBy%2A> ve <xref:System.Linq.ParallelEnumerable.ThenBy%2A> çağrısıyla izlendiğini sanki kabul <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Sorgu işleçleri ve sıralama  
 Aşağıdaki sorgu işleçleri sıra koruma sorguda veya kadar sonraki tüm işlemlere tanıtmak <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> adı verilir:  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Bazı durumlarda, aşağıdaki PLINQ sorgu işleçleri doğru sonuçlar üretmek için sıralı kaynak sıraları gerektirebilir:  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Bazı PLINQ sorgu işleçleri olup bunların kaynak sıradaki sıralı sıralanmamış veya bağlı olarak farklı şekilde davranır. Aşağıdaki tabloda bu işleçleri listeler.  
  
|İşleç|Kaynak sıradaki sipariş edildiğinde sonucu|Kaynak sıradaki sırasız olduğunda sonuç|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Belirleyici olmayan çıktı nonassociative veya noncommutative işlemleri için|Belirleyici olmayan çıktı nonassociative veya noncommutative işlemleri için|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Belirleyici olmayan çıktı nonassociative veya noncommutative işlemleri için|Belirleyici olmayan çıktı nonassociative veya noncommutative işlemleri için|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Belirtilen öğe döndürür|Rastgele öğesi|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Belirtilen öğe döndürür|Rastgele öğesi|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Sırasız sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Belirtilen öğe döndürür|Rastgele öğesi|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Belirtilen öğe döndürür|Rastgele öğesi|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Paralel olarak belirleyici olmayan şekilde yürütür|Paralel olarak belirleyici olmayan şekilde yürütür|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Belirtilen öğe döndürür|Rastgele öğesi|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Belirtilen öğe döndürür|Rastgele öğesi|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Sıra yeniden sıralar|Yeni bölüm sıralı başlatır|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Sıra yeniden sıralar|Yeni bölüm sıralı başlatır|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Uygulanamaz (aynı varsayılan olarak <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Uygulanamaz (aynı varsayılan olarak <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Tersine çevirir|Hiçbir şey yapılmaz|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(dizin)|Sıralı sonuçları|Sırasız sonuçları.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Sıralı sonuçları.|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(dizin)|Sıralı sonuçları.|Sırasız sonuçları.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Sıralı karşılaştırma|Sırasız karşılaştırma|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|İlk atlar  *n*  öğeleri|Herhangi bir atlar  *n*  öğeleri|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Sıralı sonuçları.|Belirlenemez. SkipWhile geçerli rastgele siparişte gerçekleştirir|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Belirleyici olmayan çıktı nonassociative veya noncommutative işlemleri için|Belirleyici olmayan çıktı nonassociative veya noncommutative işlemleri için|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|İlk alır `n` öğeleri|Herhangi bir alan `n` öğeleri|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Sıralı sonuçları|Belirlenemez. TakeWhile geçerli rastgele siparişte gerçekleştirir|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Eklerin`OrderBy`|Eklerin`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Eklerin`OrderBy`|Eklerin`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Geçerli değil|Geçerli değil|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(dizin)|Sıralı sonuçları|Sırasız sonuçları|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Sıralı sonuçları|Sırasız sonuçları|  
  
 Sırasız sonuçları etkin olarak karışık değil; Bunlar yalnızca uygulanmış herhangi özel bir sıralama mantık sahip değilsiniz. Bazı durumlarda, kaynak dizi sıralaması düzenlenmemiş sorguyu tutabilir. Dizinli Select işlecini kullanın sorgularında PLINQ çıktı öğeleri artan dizinlerini ancak garanti hangi dizinlerini hakkında hangi öğelerin atanacak yapar sırasına göre gelir olduğunu güvence altına alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
