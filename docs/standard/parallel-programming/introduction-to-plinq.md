---
title: PLINQ'e Giriş
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, introduction to
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9b842243cd7b9ae244688b0da348f63b68f08a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492045"
---
# <a name="introduction-to-plinq"></a>PLINQ'e Giriş
## <a name="what-is-a-parallel-query"></a>Paralel Sorgu nedir?  
 Dil ile tümleşik sorgu (LINQ) öğesinde tanıtılmıştır [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  Bunu herhangi sorgulamak için bir birleşik modele sahiptir <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> tür açısından güvenli bir şekilde veri kaynağı. LINQ to Objects'in gibi bellek içi koleksiyonlara karşı çalışan LINQ sorguları addır <xref:System.Collections.Generic.List%601> ve diziler. Bu makalede, LINQ temel bir anlayışa sahip olduğunuz varsayılır. Daha fazla bilgi için [LINQ (dil ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Paralel LINQ (PLINQ) bir paralel LINQ desen uygulamasıdır. Bir PLINQ sorgusu birçok yönden paralel olmayan LINQ to Objects sorgusuna benzer. PLINQ sorguları, tıpkı gibi sıralı [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] sorguları, tüm bellek üzerinde çalışan <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> veri kaynağı ve değil çalışmaya ve sorgu numaralandırılana kadar yürütme yani yürütme ertelenmiş yürütmeleri vardır. PLINQ sistemde tüm işlemcileri tam kullanabilmesine dener birincil farktır. Veri kaynağını parçalara bölümleme ve ardından her segmentine ayrı iş parçacığı üzerinde birden çok işlemci üzerinde paralel sorgu yürütme bunu yapar. Çoğu durumda, Paralel yürütme sorgunun önemli ölçüde daha hızlı çalışmasını anlamına gelir.  
  
 Paralel yürütme yoluyla, belirli sorgu ekleyerek genellikle sadece türleri için eski kod üzerinden, önemli performans geliştirmeleri PLINQ ulaşabileceği <xref:System.Linq.ParallelEnumerable.AsParallel%2A> sorgu işlemini veri kaynağına. Ancak, paralellik kendi karmaşıklığını ortaya çıkarabilir ve PLINQ'da tüm sorgu işlemleri bir daha hızlı çalışmasını. Aslında, paralelleştirme gerçekten bazı sorguları yavaşlatır. Bu nedenle, sıralama gibi konuların paralel sorguları nasıl etkilediğini anlamanız gerekir. Daha fazla bilgi için [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
> [!NOTE]
>  Bu belgede lambda ifadeleri PLINQ'te temsilciler tanımlamak için kullanılır. C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Bu makalenin geri kalanında ana PLINQ sınıflarına genel bir bakış sunar ve PLINQ sorgularının nasıl oluşturulacağı açıklanır. Her bölümde daha ayrıntılı bilgiler ve kod örneklerine bağlantılar içerir.  
  
## <a name="the-parallelenumerable-class"></a>ParallelEnumerable Sınıfı  
 <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> Sınıfı hemen hemen tüm PLINQ işlevselliğini gösterir.  Bu ve diğer <xref:System.Linq?displayProperty=nameWithType> ad alanı türleri, System.Core.dll dosyasına derlenir derlenir. Visual Studio'daki varsayılan C# ve Visual Basic projeleri derleme başvurusu hem ad alanını içeri aktarır.  
  
 <xref:System.Linq.ParallelEnumerable> Bunu her birini paralelleştirmeye çalışmasa LINQ to Objects'in desteklediği tüm standart sorgu işleçlerinin uygulamalarını içerir. İle aşina değilseniz [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], bkz: [LINQ'e giriş](https://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).  
  
 Standart sorgu işleçler ek olarak <xref:System.Linq.ParallelEnumerable> sınıfı, bir paralel yürütmeye özel davranışları etkinleştirme yöntemleri kümesi içerir. PLINQ'ya özgü bu yöntemler aşağıdaki tabloda listelenmiştir.  
  
|ParallelEnumerable işleci|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|PLINQ için giriş noktası. Mümkünse, sorgunun geri kalanı paralelleştirilmesi gerektiğini, belirtir.|  
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Sorgu geri kalanı sırayla, paralel olmayan LINQ sorgusu çalıştırılması gerektiğini belirtir.|  
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|PLINQ için rest sorgu veya sıralama, örneğin bir (Order By geri Basic'te) orderby yan tümcesi kullanımı tarafından değiştirilene kadar kaynak dizinin sıralamasını koruması gerektiğini belirtir.|  
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Sorgu geri kalanı için PLINQ'nun kaynak dizi sıralamasını korumak için gerekli olmadığını belirtir.|  
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|PLINQ düzenli olarak sağlanan iptali belirtecinin durumunu izlemeniz ve istenirse yürütmeyi iptal etmesi gerektiğini belirtir.|  
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|PLINQ'nun sorguyu paralelleştirmek için kullanması gereken işlemcilerin en fazla sayısını belirtir.|  
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Mümkünse, PLINQ nasıl gerektiği hakkında bir ipucu sağlar paralel sonuçları tüketim iş parçacığı üzerinde tek bir sıra uygulamasına geri birleştirin.|  
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Hatta sıralı olarak çalıştırmak için varsayılan davranışı System.Diagnostics.processpriorityclass.ıdle'da PLINQ sorguyu paralelleştirmesi gerekip gerekmediğini belirtir.|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Paralel olarak geri tüketicinin iş parçacığıyla ilk birleştirme olmaksızın sonuçların farklı olarak sorgunun sonuçları üzerinde yineleme aksine sağlar, çok iş parçacıklı numaralandırması yöntemi.|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A> aşırı yükleme|PLINQ için benzersiz olan ve iş parçacığı-yerel bölümleri yanı sıra tüm bölümlerin sonuçları birleştirmek için nihai toplama işlevine üzerinde Ara toplamaya sağlayan bir aşırı yükleme.|  
  
## <a name="the-opt-in-model"></a>Abone Olma Modeli  
 Bir sorgu yazdığınızda, PLINQ için çağırarak plınq'yu kabul edin <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> genişletme yöntemi aşağıdaki örnekte gösterildiği gibi veri kaynağı.  
  
 [!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
 [!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]  
  
 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> Genişletme yöntemi bağlar sonraki sorgu işleçlerini, bu durumda, `where` ve `select`, <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> uygulamaları.  
  
## <a name="execution-modes"></a>Yürütme Modları  
 Varsayılan olarak, PLINQ koruyucu. Çalışma zamanında, PLINQ altyapısı sorgunun genel yapısını çözümler. Sorgunun paralelleştirme ile hızlanma getirebilir, PLINQ kaynak sırasını eş zamanlı çalıştırılabilecek görevlere böler. Bir sorguyu paralel yapmak güvenli değilse, PLINQ sorguyu yalnızca sırayla'e çalıştırır. PLINQ büyük olasılıkla pahalı paralel algoritma veya ucuz bir sıralı algoritma arasında bir seçim varsa, varsayılan olarak sıralı algoritmayı seçer. Kullanabileceğiniz <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi ve <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> PLINQ'nun paralel algoritmayı seçmesi amacıyla istemek için sabit listesi. Bu, test ve belirli bir sorgu paralel olarak daha hızlı yürütür ölçüm bildiğinizde yararlıdır. Daha fazla bilgi için [nasıl yapılır: PLINQ'te yürütme modunu belirtme](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
## <a name="degree-of-parallelism"></a>Paralellik Derecesi  
 Varsayılan olarak, PLINQ ana bilgisayar üzerinde işlemcilerin tümünü kullanır. Belirtilen bir işlemci sayısı en fazla kullanarak PLINQ'ye söyleyebilirsiniz <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> yöntemi. Bilgisayarda çalışan diğer işlemlerin belirli miktarda CPU süresi aldığından emin olmak istediğinizde kullanışlıdır. Aşağıdaki kod parçacığı, sorguyu en fazla iki işlemci kullanan sınırlar.  
  
 [!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
 [!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]  
  
 Burada bir sorgunun File I/O gibi hesaplama bağlantılı olmayan iş önemli miktarda yaptığı durumlarda, makinede çekirdek sayısından daha büyük bir paralellik derecesi belirlemek faydalı olabilir.  
  
## <a name="ordered-versus-unordered-parallel-queries"></a>Sıralı ve Sırasız Paralel Sorgular  
 Bazı sorgularda, bir sorgu işlecinin kaynak dizi sıralamasını koruyan sonuçlar üretmesi gerekir. PLINQ sağlar <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> bu amaçla işleci. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> den farklıdır <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. Bir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sırası paralel olarak işlenmeye devam ediyor, ancak sonuçları arabelleğe alındı ve sıralandı. Sıra koruması genellikle ek iş içerdiğinden bir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> dizisi işlenir varsayılandan daha yavaş <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> dizisi. Belirli bir sıralı paralel işlemin işlemin sıralı sürümünden daha hızlı olup olmadığını birçok faktöre bağlıdır.  
  
 Aşağıdaki kod örneği, sıra korumasının nasıl gösterir.  
  
 [!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
 [!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]  
  
 Daha fazla bilgi için [plınq'te sıra koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="parallel-vs-sequential-queries"></a>Paralel vs. Sıralı sorgular  
 Bazı işlemler, kaynak verilerin sıralı bir şekilde teslim edilmesini gerektirir. <xref:System.Linq.ParallelEnumerable> İşleçleri sıralı moda geçer otomatik olarak gerekli olduğunda sorgu. Kullanıcı tanımlı sorgu işleçleri ve sıralı yürütme gerektiren kullanıcı temsilcileri için PLINQ sağlar <xref:System.Linq.ParallelEnumerable.AsSequential%2A> yöntemi. Kullanırken <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, kadar sorgudaki izleyen tüm işleçler sırayla yürütülen <xref:System.Linq.ParallelEnumerable.AsParallel%2A> yeniden adlandırılır. Daha fazla bilgi için [nasıl yapılır: Paralel ve sıralı LINQ sorgularını birleştirme](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).  
  
## <a name="options-for-merging-query-results"></a>Sorgu Sonuçlarını Birleştirme Seçenekleri  
 Tüketim için ana iş parçacığı üzerine geri bir PLINQ sorgusu paralel olarak yürütüldüğünde, her iş parçacığı, sonuçları birleştirilmelidir bir `foreach` döngü (`For Each` Visual Basic'te), veya bir liste veya dizi içine ekleme. Bazı durumlarda, örneğin belirli bir birleştirme işlemi türünü belirtmek için daha hızlı sonuç üretmeye başlamak için yararlı olabilir. Bu amaçla, PLINQ destekler <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> yöntemi ve <xref:System.Linq.ParallelMergeOptions> sabit listesi. Daha fazla bilgi için [plınq'te Birleştirme Seçenekleri](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
## <a name="the-forall-operator"></a>ForAll İşleci  
 Sıralı [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] sorguları, yürütme ve sorgu numaralandırılana kadar ertelenmiş ya da bir `foreach` (`For Each` Visual Basic'te) döngüsünde veya göre çağrılırken bir yöntemi gibi <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> , veya <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. PLINQ'da de kullanabilirsiniz `foreach` sorguyu çalıştırıp sonuçlarını yinelemek için. Ancak, `foreach` kendisi paralel çalışmaz ve bu nedenle tüm paralel görevlerden gelen çıkış yeniden döngünün çalıştığı iş parçasında birleştirilmesini gerektirir. PLINQ'da kullanabileceğiniz `foreach` ne zaman, sorgu sonuçlarının nihai sıralamasını korumanız ve ayrıca her işlerken sonuçları seri biçimde, örneğin, aradığınız `Console.WriteLine` her öğe için. İçin daha hızlı sorgu yürütmesi sıra koruması gerekmediğinde ve sonuçlarının işlenmesi kendi paralelleştirilebilir, kullanın <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi bir PLINQ sorgusu yürütün. <xref:System.Linq.ParallelEnumerable.ForAll%2A> Bu son birleştirme adımını gerçekleştirmez. Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> birden çok iş parçacığı herhangi bir öğeyi kaldırmaya çalışmadan aynı anda eklemek için iyileştirildiği için burada kullanılır.  
  
 [!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
 [!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]  
  
 Arasındaki fark aşağıdaki çizimde `foreach` ve <xref:System.Linq.ParallelEnumerable.ForAll%2A> sorgu yürütme ile ilgili.  
  
 ![ForAll vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")  
  
## <a name="cancellation"></a>İptal Etme  
 PLINQ deki iptal türleri ile tümleşiktir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. (Daha fazla bilgi için [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).) Bu nedenle, Plınq sorgularının sıralı LINQ, PLINQ sorguları iptal edilebilir. İptal edilebilir bir PLINQ sorgusu oluşturmak için kullanın <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu işlecini ve sağlayan bir <xref:System.Threading.CancellationToken> örneği bağımsız değişken olarak. Zaman <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> belirtecine özelliği, PLINQ true olarak ayarlandığında, dikkat, tüm iş parçacıklarında işlemi durdurur ve throw bir <xref:System.OperationCanceledException>.  
  
 PLINQ sorgusunu iptal belirteci ayarladıktan sonra bazı öğeleri işlemeye devam etmesi mümkündür.  
  
 Daha fazla duyarlılık için uzun süre çalışan kullanıcı temsilcilerinde iptal isteklerine de yanıt verebilir. Daha fazla bilgi için [nasıl yapılır: PLINQ sorgusunu iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="exceptions"></a>Özel Durumlar  
 Birden çok özel bir PLINQ sorgusu yürütüldüğünde, farklı iş parçacıklarından aynı anda atılabilir. Ayrıca, özel durumu işlemek üzere kod, farklı bir iş parçacığında özel durum oluşturan koda olabilir. PLINQ kullanan <xref:System.AggregateException> bir sorgu tarafından oluşturulan tüm özel durumları yalıtılacak yazın ve bu özel durumlar çağıran iş parçacığına geri dön hazırlama. Çağıran iş parçacığında, yalnızca bir try-catch bloğu gereklidir. Ancak, tüm özel durumların, kapsüllenmiş yineleyebilirsiniz <xref:System.AggregateException> ve, güvenle kurtarabileceğiniz herhangi yakalayın. Nadiren de olsa bazı özel durumlar olarak kaydırılan değil oluşturulabilir bir <xref:System.AggregateException>, ve <xref:System.Threading.ThreadAbortException>s de değil sarılır.  
  
 Ne zaman bir sorgu özel durum oluştuktan sonra bazı öğeleri işlemeye devam edebilir mümkündür özel durumları ayarlama geri katılan iş parçacığına Kabarcık halinde çıkmasına izin verilmez.  
  
 Daha fazla bilgi için [nasıl yapılır: PLINQ sorgusunda özel durumları işlemek](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="custom-partitioners"></a>Özel Bölümleyiciler  
 Bazı durumlarda, kaynak verilerin bazı özellik yararlanan özel bir bölümleyici yazarak sorgu performansını iyileştirebilir. Sorguda özel bölümleyici sorgulanan sıralanabilir nesnedir.  
  
 [!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
 [!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]  
  
 (Veri dinamik olarak bu bölümlere Yük Dengelemesi için çalışma zamanı sırasında atanabilmelerine rağmen.) PLINQ, sabit sayıda bölümleri destekler. <xref:System.Threading.Tasks.Parallel.For%2A> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> değiştiği sayısını çalışma zamanında yani yalnızca dinamik bölümlemeyi destekler. Daha fazla bilgi için [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="measuring-plinq-performance"></a>PLINQ Performansını Ölçme  
 Çoğu durumda, sorgu paralelleştirilebilir, ancak paralel sorgulaması oluşturma yükü kazanılan performans avantajını ağır. Bir sorgu çok fazla hesaplama yapmazsa ya da veri kaynağı küçükse bir PLINQ sorgusu sıralı bir LINQ to Objects sorgusundan yavaş olabilir. İşlemci performansı sorunlarını bulmaya ve sorgunuzu paralel mi yoksa sırayla çalışıp çalışmadığını belirlemek için çeşitli sorguların performansını karşılaştırmak için Visual Studio Team Server paralel Performans Çözümleyicisi'ni kullanabilirsiniz. Daha fazla bilgi için [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) ve [nasıl yapılır: PLINQ sorgu performansını ölçme](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [PLINQ'te Hızlandırmayı Anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
