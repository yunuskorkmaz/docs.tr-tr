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
ms.openlocfilehash: ed1b2df57c118a0ebb6b5ffa4326b3e2eac81dec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75632369"
---
# <a name="introduction-to-plinq"></a>PLINQ'e Giriş

## <a name="what-is-a-parallel-query"></a>Paralel Sorgu nedir?

Dil-Tümleşik Sorgu (LINQ) .NET Framework 3.5'te tanıtıldı. Herhangi <xref:System.Collections.IEnumerable?displayProperty=nameWithType> bir veri <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> kaynağını tür güvenli bir şekilde sorgulamak için birleşik bir model sunar. LinQ to Objects, bellek içi koleksiyonlar ve diziler gibi <xref:System.Collections.Generic.List%601> karşı çalıştırılabilen LINQ sorgularının adıdır. Bu makalede, LINQ temel bir anlayışa sahip olduğunu varsayar. Daha fazla bilgi için bkz: [Dil-Tümleşik Sorgu (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) veya [Dil-Tümleşik Sorgu (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).

Paralel LINQ (PLINQ) LINQ deseni paralel bir uygulamadır. Birçok yönden bir PLINQ sorgusu, Nesneler sorgusuna paralel olmayan bir LINQ sorgusuna benzer. PLINQ sorguları, sıralı LINQ sorguları gibi, <xref:System.Collections.IEnumerable> herhangi <xref:System.Collections.Generic.IEnumerable%601> bir bellek veya veri kaynağında çalışır ve yürütmeyi erteler, bu da sorgu numaralandırılAna kadar yürütmeye başlamadıkları anlamına gelir. Birincil fark, PLINQ sistemdeki tüm işlemcileri tam olarak kullanmaya çalışır. Bunu, veri kaynağını bölümlere ayırarak ve sonra her segmentteki sorguyu birden çok işlemciye paralel olarak ayrı bir alt iş parçacığı üzerinde gerçekleştirerek yapar. Çoğu durumda, paralel yürütme sorgunun önemli ölçüde daha hızlı çalıştığı anlamına gelir.

Paralel yürütme sayesinde PLINQ, genellikle yalnızca sorgu işlemini <xref:System.Linq.ParallelEnumerable.AsParallel%2A> veri kaynağına ekleyerek, belirli sorgu türleri için eski kod üzerinde önemli performans iyileştirmeleri elde edebilir. Ancak, paralellik kendi karmaşıklıklarını tanıtabilir ve tüm sorgu işlemleri PLINQ'da daha hızlı çalışmaz. Aslında, paralelleştirme aslında bazı sorguları yavaşlatıyor. Bu nedenle, sipariş verme gibi sorunların paralel sorguları nasıl etkilediğini anlamanız gerekir. Daha fazla bilgi için [PLINQ'da Çabuk'u Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.

> [!NOTE]
> Bu dokümantasyon PLINQ'daki delegeleri tanımlamak için lambda ifadelerini kullanır. C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.

Bu makalenin geri kalanı ana PLINQ sınıflarına genel bir bakış verir ve PLINQ sorgularının nasıl oluşturulup oluşturulabildiğini tartışır. Her bölüm daha ayrıntılı bilgi ve kod örnekleri bağlantılar içerir.

## <a name="the-parallelenumerable-class"></a>ParallelEnumerable Sınıfı

Sınıf <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> PLINQ işlevselliğinin hemen hemen tüm ortaya çıkarır. Bu ve <xref:System.Linq?displayProperty=nameWithType> diğer ad alanı türleri System.Core.dll derlemesine derlenir. Visual Studio'daki varsayılan C# ve Visual Basic projeleri hem derlemeye başvurur hem de ad alanını alır.

<xref:System.Linq.ParallelEnumerable>LINQ to Objects'in desteklediği tüm standart sorgu işleçlerinin uygulamalarını içerir, ancak her birini paralelleştirmeye çalışmaz. LINQ'ya aşina değilseniz, [LINQ'ya Giriş (C#)](../../csharp/programming-guide/concepts/linq/index.md) ve [LINQ'a Giriş (Visual Basic) (Visual Basic) 'ye](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)bakın.

<xref:System.Linq.ParallelEnumerable> Standart sorgu işleçlerine ek olarak, sınıf paralel yürütmeye özgü davranışları etkinleştiren bir yöntem kümesi içerir. Bu PLINQ özel yöntemler aşağıdaki tabloda listelenmiştir.

|ParallelUmerable Operatörü|Açıklama|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|PLINQ için giriş noktası. Mümkünse, sorgunun geri kalanının paralelleştirilmesi gerektiğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Sorgunun geri kalanının paralel olmayan bir LINQ sorgusu olarak sırayla çalıştırılması gerektiğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|PLINQ'un, örneğin bir orderby (Visual Basic'te Sırayla) yan tümcesi kullanarak, örneğin sipariş değiştirilene kadar veya sorgunun geri kalanı için kaynak sıranın sırasını koruması gerektiğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Sorgunun geri kalanı için PLINQ kaynak sırasını korumak için gerekli olmadığını belirtir.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|PLINQ'nin, verilen iptal jetonunun durumunu periyodik olarak izlemesi ve talep edilmesi halinde yürütmeyi iptal etmesi gerektiğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|PLINQ'un sorguyu paralelleştirmek için kullanması gereken maksimum işlemci sayısını belirtir.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|PLINQ'un, mümkünse paralel sonuçları tüketen iş parçacığıüzerinde tek bir sırayla nasıl birleştirmesi gerektiği hakkında bir ipucu sağlar.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|PlinQ'un sorguyu paralelleştirip paralelleştirmesi gerektiğini belirtir, varsayılan davranış sırayla çalıştırmak için olsa bile.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Sorgunun sonuçları üzerinde yineleme aksine, ilk tüketici iş parçacığı geri birleştirme den sonuçları paralel olarak işlenmesini sağlayan çok iş parçacığı numaralandırma yöntemi.|
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>Aşırı|PLINQ'ye özgü olan ve iş parçacığı yerel bölümleri üzerinde ara toplama yı sağlayan aşırı yük ve tüm bölümlerin sonuçlarını birleştirmek için son bir toplama işlevi.|

## <a name="the-opt-in-model"></a>Abone Olma Modeli

Bir sorgu yazarken, aşağıdaki örnekte gösterildiği gibi, <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> veri kaynağındaki uzantı yöntemini çağırarak PLINQ'yi tercih edin.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

Uzantı <xref:System.Linq.ParallelEnumerable.AsParallel%2A> yöntemi, bu durumda sonraki sorgu işleçlerini `where` ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> `select`uygulamaları bağlar.

## <a name="execution-modes"></a>Yürütme Modları

Varsayılan olarak, PLINQ muhafazakar. Çalışma zamanında, PLINQ altyapısı sorgunun genel yapısını analiz eder. Sorgu paralelleştirme ile hız lanma olasılığı yüksekse, PLINQ kaynak sırasını aynı anda çalıştırılabilen görevlere bölümlere ayırır. Bir sorguyu paralelleştirmek güvenli değilse, PLINQ sorguyu sırayla çalıştırZ. PLINQ potansiyel olarak pahalı bir paralel algoritma veya ucuz sıralı algoritma arasında bir seçim varsa, varsayılan olarak sıralı algoritmaseçer. PlinQ'a paralel algoritmayı <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> seçmetalimatı vermek için yöntemi ve <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> numaralandırmayı kullanabilirsiniz. Bu, belirli bir sorgunun paralel olarak daha hızlı yürütüldettiğini sınayıp ölçerek bildiğinizde kullanışlıdır. Daha fazla bilgi için [bkz: PLINQ'da Yürütme Modunu belirtin.](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)

## <a name="degree-of-parallelism"></a>Paralellik Derecesi

Varsayılan olarak PLINQ, ana bilgisayardaki tüm işlemcileri kullanır. PLINQ'a <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> yöntemi kullanarak belirli sayıdaişlemciden daha fazla kullanmamasını talimatı verebilirsiniz. Bu, bilgisayarda çalışan diğer işlemlerin belirli bir cpu süresi aldığından emin olmak istediğinizde yararlıdır. Aşağıdaki parçacık sorguyu en fazla iki işlemci kullanmakla sınırlar.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

Bir sorgunun Dosya G/Ç gibi önemli miktarda bilgi işlem le yükümlü olmayan bir çalışma gerçekleştirdiği durumlarda, makinedeki çekirdek sayısından daha büyük bir paralellik derecesi belirtmek yararlı olabilir.

## <a name="ordered-versus-unordered-parallel-queries"></a>Sıralı ve Sırasız Paralel Sorgular

Bazı sorgularda, bir sorgu işleci kaynak sıranın sırasını koruyan sonuçlar üretmelidir. PLINQ <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> bu amaç için operatör sağlar. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>dan <xref:System.Linq.ParallelEnumerable.AsSequential%2A>farklıdır. Bir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sıra hala paralel olarak işlenir, ancak sonuçları arabelleğe alınır ve sıralanır. Sipariş koruma genellikle ek çalışma <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> içerdiğinden, bir dizi varsayılan <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> diziden daha yavaş işlenebilir. Belirli bir sıralı paralel işlemin, işlemin sıralı bir sürümünden daha hızlı olup olmadığı birçok etkene bağlıdır.

Aşağıdaki kod örneği, koruma sırasına nasıl seçilen gösterir.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Daha fazla bilgi için [PLINQ'da Sipariş Koruma'ya](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)bakın.

## <a name="parallel-vs-sequential-queries"></a>Paralel ve Sıralı Sorgular

Bazı işlemler, kaynak verilerin sıralı bir şekilde teslim edilmesini gerektirir. Sorgu <xref:System.Linq.ParallelEnumerable> işleçleri gerektiğinde otomatik olarak sıralı moda geri döner. Kullanıcı tanımlı sorgu işleçleri ve sıralı yürütme gerektiren <xref:System.Linq.ParallelEnumerable.AsSequential%2A> kullanıcı temsilcileri için PLINQ yöntemi sağlar. Kullandığınızda, <xref:System.Linq.ParallelEnumerable.AsSequential%2A>sorgudaki sonraki tüm işleçler <xref:System.Linq.ParallelEnumerable.AsParallel%2A> yeniden çağrılana kadar sırayla yürütülür. Daha fazla bilgi için [bkz: Paralel ve Sıralı LINQ Sorgularını Birleştir.](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)

## <a name="options-for-merging-query-results"></a>Sorgu Sonuçlarını Birleştirme Seçenekleri

Bir PLINQ sorgusu paralel olarak yürütüldüğünde, her alt iş parçacığının sonuçları bir `foreach` döngü (Visual`For Each` Basic'te) veya bir liste veya diziye eklemek tarafından tüketim için ana iş parçacığına geri birleştirilmelidir. Bazı durumlarda, sonuçları daha hızlı üretmeye başlamak için belirli bir tür birleştirme işlemi belirtmek yararlı olabilir. Bu amaçla PLINQ <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> yöntemi ve numaralandırmayı <xref:System.Linq.ParallelMergeOptions> destekler. Daha fazla bilgi için [PLINQ'daki Seçenekleri Birleştir'e](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)bakın.

## <a name="the-forall-operator"></a>ForAll İşleci

Ardışık LINQ sorgularında, yürütme sorgu `foreach` (Visual`For Each` Basic' de) veya <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> veya <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. PLINQ'de, sorguyu `foreach` yürütmek ve sonuçları doğrulamak için de kullanabilirsiniz. Ancak, `foreach` kendisi paralel olarak çalışmaz ve bu nedenle, tüm paralel görevlerden çıktı döngü çalışan iş parçacığı geri birleştirilmelidir gerektirir. PLINQ'de, sorgu `foreach` sonuçlarının son sırasını korumanız gerektiğinde ve sonuçları seri bir şekilde işlediğinizde, örneğin her `Console.WriteLine` öğe için arama yaparken kullanabilirsiniz. Sipariş koruma gerekli olmadığında ve sonuçların işlenmesi paralelleştirilebildiği nde daha hızlı <xref:System.Linq.ParallelEnumerable.ForAll%2A> sorgu yürütmesi için, plinq sorgusu yürütmek için yöntemi kullanın. <xref:System.Linq.ParallelEnumerable.ForAll%2A>bu son birleştirme adımLarını gerçekleştirmez. Aşağıdaki kod örneği yöntemin <xref:System.Linq.ParallelEnumerable.ForAll%2A> nasıl kullanılacağını gösterir. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>herhangi bir öğeyi kaldırmaya çalışmadan aynı anda ekleyerek birden çok iş parçacığı için optimize edilmiş olduğundan burada kullanılır.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Aşağıdaki resimde sorgu yürütme `foreach` <xref:System.Linq.ParallelEnumerable.ForAll%2A> ile ilgili ve arasındaki farkı gösterir.

![ForAll vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>İptal

PLINQ,.NET Framework 4'teki iptal türleri ile entegre edilmiştir. (Daha fazla bilgi için yönetilen [iş parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)konusuna bakın.) Bu nedenle, nesnelere sıralı LINQ'dan farklı olarak PLINQ sorguları iptal edilebilir. İptal edilebilir bir PLINQ sorgusu <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> oluşturmak için, sorguda <xref:System.Threading.CancellationToken> işleci kullanın ve bağımsız değişken olarak bir örnek sağlayın. Belirteç üzerindeki <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özellik doğru ayarlandığında, PLINQ bunu fark edecek, tüm iş <xref:System.OperationCanceledException>parçacıkları üzerinde işlemeyi durduracak ve bir .

İptal belirteci ayarlandıktan sonra bir PLINQ sorgusunun bazı öğeleri işlemeye devam etmesi mümkündür.

Daha fazla yanıt verme için, uzun süredir devam eden kullanıcı temsilcilerindeki iptal isteklerine de yanıt verebilirsiniz. Daha fazla bilgi için [bkz: PLINQ Sorgusuiptal edin.](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)

## <a name="exceptions"></a>Özel durumlar

Bir PLINQ sorgusu yürütüldüğünde, aynı anda farklı iş parçacığından birden çok özel durum atılabilir. Ayrıca, özel durumu işlemek için kod özel durum attı kod farklı bir iş parçacığı üzerinde olabilir. <xref:System.AggregateException> PLINQ, sorgu tarafından atılan tüm özel durumları kapsüllemek ve bu özel durumları arama iş parçacığına geri döndürmek için türü kullanır. Arama iş parçacığında yalnızca bir try-catch bloğu gereklidir. Ancak, kapsüllenmiş tüm özel durumlar aracılığıyla yineleyebilir <xref:System.AggregateException> ve güvenli bir şekilde kurtarabilirsiniz herhangi bir yakalamak. Nadir durumlarda, bazı özel durumlar bir <xref:System.AggregateException>sarılmış değil atılabilir <xref:System.Threading.ThreadAbortException>ve s de sarılmış değildir.

Özel durumların birleştirme iş parçacığına geri dönmesine izin verildiğinde, özel durum yükseltildikten sonra bir sorgunun bazı öğeleri işlemeye devam etmesi mümkündür.

Daha fazla bilgi için [bkz: PLINQ Sorgusunda Özel Durumları Nasıl İşleyin.](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)

## <a name="custom-partitioners"></a>Özel Bölümleyiciler

Bazı durumlarda, kaynak verilerin bazı özelliklerinden yararlanan özel bir bölümleyici yazarak sorgu performansını artırabilirsiniz. Sorguda, özel bölümleyicinin kendisi sorgulanacak sayısal nesnedir.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

PLINQ sabit sayıda bölümü destekler (ancak yük dengeleme için çalışma süresi boyunca veriler dinamik olarak bu bölümlere yeniden atanabilir.) <xref:System.Threading.Tasks.Parallel.For%2A>ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> yalnızca dinamik bölümleme desteği, bu da bölüm sayısının çalışma zamanında değiştiği anlamına gelir. Daha fazla bilgi [için PLINQ ve TPL için Özel Bölümleyiciler'e](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)bakın.

## <a name="measuring-plinq-performance"></a>PLINQ Performansını Ölçme

Çoğu durumda, bir sorgu paralelolabilir, ancak paralel sorgu ayarlama yükü kazanılan performans avantajından daha ağır basar. Bir sorgu çok hesaplama gerçekleştirmezse veya veri kaynağı küçükse, PLINQ sorgusu Nesneler için sıralı BIR LINQ sorgusundan daha yavaş olabilir. Visual Studio Team Server'daki Paralel Performans Çözümleyicisini çeşitli sorguların performansını karşılaştırmak, işlem darboğazlarını bulmak ve sorgunuzun paralel mi sırayla mı çalıştığını belirlemek için kullanabilirsiniz. Daha fazla bilgi için [Eşzamanlılık Görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) ve [Nasıl Yapılacağını görün: PLINQ Sorgu Performansını Ölçün.](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [PLINQ'te Hızlandırmayı Anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
