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
ms.openlocfilehash: e50b2bf15d9a627f70ff01616bf2c72c70d7ff33
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290687"
---
# <a name="introduction-to-plinq"></a>PLINQ'e Giriş

Parallel LINQ (PLıNQ), [dil Ile tümleşik sorgu (LINQ)](../../csharp/programming-guide/concepts/linq/index.md) deseninin paralel bir uygulamasıdır. PLıNQ, LINQ standart sorgu işleçlerinin tam kümesini ad alanı için uzantı yöntemleri olarak uygular <xref:System.Linq> ve paralel işlemler için ek işleçlere sahiptir. PLıNQ, LINQ sözdiziminin basitliğini ve okunabilirliğini paralel programlama gücüyle birleştirir.

> [!TIP]
> LINQ hakkında bilgi sahibi değilseniz, bir tür açısından güvenli şekilde, sıralanabilir veri kaynaklarını sorgulamak için birleştirilmiş bir model sunar. LINQ to Objects, ve dizileri gibi bellek içi koleksiyonlara karşı çalıştırılan LINQ sorgularının adıdır <xref:System.Collections.Generic.List%601> . Bu makalede, LINQ 'ın temel olarak anlaşıldığı varsayılmaktadır. Daha fazla bilgi için bkz. [dil Ile tümleşik sorgu (LINQ)](../../csharp/programming-guide/concepts/linq/index.md).

## <a name="what-is-a-parallel-query"></a>Paralel sorgu nedir?

Birçok şekilde bir PLıNQ sorgusu, paralel olmayan LINQ to Objects sorgusuna benzer. PLıNQ sorguları, sıralı LINQ sorguları gibi tüm bellek içi <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> veri kaynakları üzerinde çalışır ve bu, sorgu numaralandırılana kadar yürütülmeye başlamadıkları anlamına gelir. Birincil fark, PLıNQ 'in sistemdeki tüm işlemcileri tam olarak kullanmasını denemelerinde. Bu, veri kaynağını kesimlere bölümleyerek ve sonra her kesimde sorguyu birden çok işlemci üzerinde paralel olan ayrı çalışan iş parçacıklarında yürüterek yapar. Birçok durumda, paralel yürütme sorgunun önemli ölçüde daha hızlı çalıştığı anlamına gelir.

PLıNQ, paralel yürütme sayesinde, genellikle <xref:System.Linq.ParallelEnumerable.AsParallel%2A> veri kaynağına sorgu işlemi ekleyerek, belirli türde sorgular için eski kodla önemli performans geliştirmeleri elde edebilir. Ancak paralellik, kendi karmaşıklıklarını ortaya çıkarabilir ve tüm sorgu işlemleri PLıNQ 'te daha hızlı çalışmaz. Aslında, paralelleştirme bazı sorguları yavaşlatır. Bu nedenle, sıralama gibi sorunların Paralel sorguları nasıl etkilediğini anlamanız gerekir. Daha fazla bilgi için bkz. [PLıNQ 'Te hızlı Hızlandırlamayı anlama](understanding-speedup-in-plinq.md).

> [!NOTE]
> Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır. C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).

Bu makalenin geri kalanı, ana PLıNQ sınıflarına genel bir bakış sağlar ve PLıNQ sorgularının nasıl oluşturulacağını açıklar. Her bölümde daha ayrıntılı bilgi ve kod örneklerine ait bağlantılar yer alır.

## <a name="the-parallelenumerable-class"></a>ParallelEnumerable Sınıfı

<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>Sınıfı, neredeyse tüm PLıNQ işlevlerini gösterir. Bu ve <xref:System.Linq?displayProperty=nameWithType> ad alanı türlerinin geri kalanı System. Core. dll derlemesine derlenir. Visual Studio 'daki varsayılan C# ve Visual Basic projeleri derlemeye başvurur ve ad alanını içeri aktarır.

<xref:System.Linq.ParallelEnumerable>her birini paralel hale getirmek denemese de, LINQ to Objects desteklediği tüm standart sorgu işleçlerinin uygulamalarını içerir. LINQ hakkında bilginiz yoksa LINQ ['A giriş (C#)](../../csharp/programming-guide/concepts/linq/index.md) ve [LINQ (Visual Basic) uygulamasına giriş](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)konusuna bakın.

Standart sorgu işleçlerine ek olarak, <xref:System.Linq.ParallelEnumerable> sınıfı paralel yürütmeye özel davranışları etkinleştiren bir yöntemler kümesi içerir. Bu PLıNQ 'e özgü yöntemler aşağıdaki tabloda listelenmiştir.

|ParallelEnumerable Işleci|Description|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|PLıNQ için giriş noktası. Mümkünse sorgunun geri kalanının paralelleştirilmesine sahip olması gerektiğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Sorgunun geri kalanının paralel olmayan bir LINQ sorgusu olarak sırayla çalıştırılması gerektiğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|PLıNQ 'ın, sorgunun geri kalanı için kaynak dizinin sıralamasını korumalı veya sıralama değiştirilene kadar (örneğin, bir OrderBy (by Visual Basic) yan tümcesinin kullanılması gerektiğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Kaynak dizinin sıralamasını korumak için sorgunun geri kalanı için PLıNQ öğesinin gerekli değildir olduğunu belirtir.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|PLıNQ 'ın, belirtilen iptal belirtecinin durumunu düzenli olarak izlemesi gerektiğini ve istenirse yürütmeyi iptal edip etmediğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|PLıNQ 'ın sorguyu paralel hale getirmek için kullanması gereken en fazla işlemci sayısını belirtir.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|PLıNQ 'in mümkünse, paralel sonuçları tüketim iş parçacığında yalnızca bir sırayla birleştirerek bir ipucu sağlar.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Varsayılan davranış ardışık olarak çalıştırmak olduğunda bile PLıNQ 'ın sorguyu paralel hale getirmek gerekip gerekmediğini belirtir.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Sorgunun sonuçlarını yinelemeden farklı olan çok iş parçacıklı numaralandırma yöntemi, önce tüketici iş parçacığına geri birleştirmeden sonuçların paralel olarak işlenmesini sağlar.|
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>yüklemek|PLıNQ için benzersiz olan ve iş parçacığı yerel bölümleri üzerinde ara toplamayı sağlayan bir aşırı yükleme ve tüm bölümlerin sonuçlarını birleştirmek için son toplama işlevi.|

## <a name="the-opt-in-model"></a>Abone Olma Modeli

Bir sorgu yazdığınızda, <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, veri kaynağındaki genişletme yöntemini çağırarak PLINQ ' yi kabul edin.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

<xref:System.Linq.ParallelEnumerable.AsParallel%2A>Uzantı yöntemi, sonraki sorgu işleçlerini Bu örnekte `where` ve `select` , <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> uygulamalarına bağlar.

## <a name="execution-modes"></a>Yürütme Modları

Varsayılan olarak PLıNQ, koruyucu olur. Çalışma zamanında, PLıNQ altyapısı sorgunun genel yapısını analiz eder. Sorgunun paralelleştirme yoluyla hızlı hale getirme olasılığı varsa PLıNQ, kaynak dizisini aynı anda çalıştırılabilen görevlere bölümler. Bir sorgu paralel hale getirmek için güvenli değilse PLıNQ sorguyu sırayla çalıştırır. PLıNQ, potansiyel olarak pahalı bir paralel algoritma veya pahalı bir sıralı algoritma arasında seçim yaptıysanız, varsayılan olarak sıralı algoritmayı seçer. <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> PLINQ 'in paralel algoritmayı seçmesini sağlamak için yöntemini ve sabit listesini kullanabilirsiniz. Bu, belirli bir sorgunun paralel olarak daha hızlı yürütüldüğünü test ve ölçüyle bildiğiniz durumlarda faydalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ 'Te yürütme modunu belirtme](how-to-specify-the-execution-mode-in-plinq.md).

## <a name="degree-of-parallelism"></a>Paralellik Derecesi

Varsayılan olarak, PLıNQ ana bilgisayardaki tüm işlemcileri kullanır. Yöntemini kullanarak PLıNQ 'ın belirtilen sayıda işlemciyi daha fazla kullanmasını sağlayabilirsiniz <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> . Bu, bilgisayarda çalışan diğer işlemlerin belirli bir CPU süresi miktarını aldığından emin olmak istediğinizde yararlıdır. Aşağıdaki kod parçacığı, en fazla iki işlemciyi kullanarak sorguyu sınırlandırır.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

Bir sorgunun dosya g/ç gibi işlem dışı bağlı önemli miktarda işi gerçekleştirdiği durumlarda, makinedeki çekirdek sayısından daha büyük bir paralellik derecesi belirtmek yararlı olabilir.

## <a name="ordered-versus-unordered-parallel-queries"></a>Sıralı ve Sırasız Paralel Sorgular

Bazı sorgularda, bir sorgu işleci kaynak dizinin sıralamasını koruyan sonuçlar üretmelidir. PLıNQ <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> Bu amaçla operatör sağlar. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>, öğesinden farklıdır <xref:System.Linq.ParallelEnumerable.AsSequential%2A> . Bir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> dizi hala paralel olarak işlenir, ancak sonuçları arabelleğe alınır ve sıralanır. Sıra koruması genellikle ek iş içerdiğinden, bir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sıra varsayılan sırasından daha yavaş işlenebilir <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> . Belirli bir sıralı paralel işlemin, işlemin sıralı bir sürümünden daha hızlı olup olmadığı birçok faktöre bağlıdır.

Aşağıdaki kod örneğinde, siparişin korunmasını nasıl kabul edilecek gösterilmektedir.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Daha fazla bilgi için bkz. [PLıNQ 'Te sıra koruma](order-preservation-in-plinq.md).

## <a name="parallel-vs-sequential-queries"></a>Paralel ve sıralı sorgular

Bazı işlemler, kaynak verilerinin sıralı bir şekilde teslim edilmesini gerektirir. <xref:System.Linq.ParallelEnumerable>Sorgu işleçleri gerektiğinde otomatik olarak sıralı moda döndürülür. Kullanıcı tanımlı sorgu işleçleri ve sıralı yürütme gerektiren Kullanıcı temsilcileri için PLıNQ <xref:System.Linq.ParallelEnumerable.AsSequential%2A> yöntemi sağlar. Kullandığınızda <xref:System.Linq.ParallelEnumerable.AsSequential%2A> , sorguda sonraki tüm işleçler <xref:System.Linq.ParallelEnumerable.AsParallel%2A> tekrar çağrılıncaya kadar sırayla yürütülür. Daha fazla bilgi için bkz. [nasıl yapılır: paralel ve sıralı LINQ sorgularını birleştirme](how-to-combine-parallel-and-sequential-linq-queries.md).

## <a name="options-for-merging-query-results"></a>Sorgu Sonuçlarını Birleştirme Seçenekleri

Bir PLıNQ sorgusu paralel olarak yürütüldüğünde, her bir çalışan iş parçacığının sonuçları bir döngüye göre tüketim `foreach` ( `For Each` Visual Basic) veya bir liste ya da diziye ekleme için ana iş parçacığından geri birleştirilmelidir. Bazı durumlarda, örneğin, sonuçların daha hızlı bir şekilde üretilmeye başlaması gibi belirli bir birleştirme işlemi türü belirtmek yararlı olabilir. Bu amaçla PLıNQ, <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> yöntemini ve <xref:System.Linq.ParallelMergeOptions> sabit listesini destekler. Daha fazla bilgi için bkz. [PLıNQ 'Te birleştirme seçenekleri](merge-options-in-plinq.md).

## <a name="the-forall-operator"></a>ForAll İşleci

Sıralı LINQ sorgularında, sorgu bir `foreach` ( `For Each` Visual Basic) döngüsünde numaralandırılıncaya veya, ya da gibi bir yöntemi çağırarak, yürütme ertelenir <xref:System.Linq.ParallelEnumerable.ToList%2A> <xref:System.Linq.ParallelEnumerable.ToArray%2A> <xref:System.Linq.ParallelEnumerable.ToDictionary%2A> . PLıNQ 'te, `foreach` sorguyu yürütmek ve sonuçlar boyunca yinelemek için de kullanabilirsiniz. Ancak, `foreach` kendisi paralel çalışmaz ve bu nedenle, tüm paralel görevlerden çıktının döngünün çalıştığı iş parçacığına geri birleştirilmesi gerekir. PLıNQ 'te, `foreach` sorgu sonuçlarının son sıralamasını korumanız gerektiğinde ve ayrıca her bir öğe için arama yaptığınızda sonuçları seri olarak işlerken kullanabilirsiniz `Console.WriteLine` . Daha hızlı sorgu yürütme sırası gerektiğinde ve sonuçların işlenmesi kendisini paralelleştirirse, <xref:System.Linq.ParallelEnumerable.ForAll%2A> BIR PLıNQ sorgusu yürütmek için yöntemini kullanın. <xref:System.Linq.ParallelEnumerable.ForAll%2A>Bu son birleştirme adımını gerçekleştirmez. Aşağıdaki kod örneği, yönteminin nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.ForAll%2A> . <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>, herhangi bir öğeyi kaldırmaya çalışmadan eşzamanlı olarak birden çok iş parçacığı eklemek için iyileştirildiğinden burada kullanılır.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Aşağıdaki çizimde, `foreach` <xref:System.Linq.ParallelEnumerable.ForAll%2A> sorgu yürütmeyle ilgili olarak ve arasındaki fark gösterilmektedir.

![ForAll vs. ForEach](media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>İptal

PLıNQ, .NET Framework 4 ' teki iptal türleriyle tümleşiktir. (Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../threading/cancellation-in-managed-threads.md).) Bu nedenle, sıralı LINQ to Objects sorgularının aksine PLıNQ sorguları iptal edilebilir. Bir iptal edilebilen PLıNQ sorgusu oluşturmak için, <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgudaki işleci kullanın ve <xref:System.Threading.CancellationToken> bağımsız değişken olarak bir örnek sağlayın. <xref:System.Threading.CancellationToken.IsCancellationRequested%2A>Belirteçteki özelliği true olarak ayarlandığında PLINQ bunu fark eder, tüm iş parçacıklarında işlemeyi durdurur ve bir oluşturur <xref:System.OperationCanceledException> .

Bir PLıNQ sorgusunun, iptal belirteci ayarlandıktan sonra bazı öğeleri işlemeye devam etmesi mümkündür.

Daha fazla yanıt verme için, uzun süre çalışan Kullanıcı Temsilcilerde iptal isteklerine de yanıt verebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgusunu Iptal etme](how-to-cancel-a-plinq-query.md).

## <a name="exceptions"></a>Özel durumlar

Bir PLıNQ sorgusu yürütüldüğünde, farklı iş parçacıklarından aynı anda birden çok özel durum oluşturulabilir. Ayrıca, özel durumu işleyen kod, özel durumu oluşturan koddan farklı bir iş parçacığında olabilir. PLıNQ, <xref:System.AggregateException> bir sorgu tarafından oluşturulan tüm özel durumları kapsüllemek ve bu özel durumları çağıran iş parçacığına geri sıralamak için türünü kullanır. Çağıran iş parçacığında yalnızca bir try-catch bloğu gereklidir. Bununla birlikte, içinde kapsüllenmiş tüm özel durumlar boyunca yineleyebilir <xref:System.AggregateException> ve güvenle kurtarabileceğiniz her türlü özel durumu yakalayın. Nadiren de olsa, bazı özel durumlar, bir içinde sarmalanmamış <xref:System.AggregateException> ve <xref:System.Threading.ThreadAbortException> öğeleri sarmalanmamış olabilir.

Özel durumların katılan iş parçacığına balon ekleme yapmasına izin verildiğinde, bir sorgu özel durum oluşturulduktan sonra bazı öğeleri işlemeye devam edebilir.

Daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgusunda özel durumları işleme](how-to-handle-exceptions-in-a-plinq-query.md).

## <a name="custom-partitioners"></a>Özel Bölümleyiciler

Bazı durumlarda, kaynak verilerinin bazı özelliklerden yararlanan özel bir bölümleyici yazarak sorgu performansını artırabilirsiniz. Sorguda, özel bölümleyici, sorgulanan sıralanabilir nesnedir.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

PLıNQ, sabit sayıda bölümü destekler (ancak, veriler yük dengeleme için çalışma süresi boyunca dinamik olarak bu bölümlere yeniden atanabilir.). <xref:System.Threading.Tasks.Parallel.For%2A>ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> yalnızca dinamik Bölümlendirmeyi destekler, bu da çalışma zamanında bölüm sayısının değiştiği anlamına gelir. Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md).

## <a name="measuring-plinq-performance"></a>PLINQ Performansını Ölçme

Birçok durumda, bir sorgu paralellik olabilir, ancak paralel sorgu ayarlama yükü, kazanılan performans avantajını ortadan kaldırır. Bir sorgu çok fazla hesaplama gerçekleştirmezse veya veri kaynağı küçükse, bir PLıNQ sorgusu sıralı bir LINQ to Objects sorgusundan daha yavaş olabilir. Çeşitli sorguların performansını karşılaştırmak için, Visual Studio Team Server 'daki paralel Performans Çözümleyicisi ' ni kullanarak, işleme performans sorunlarını bulabilir ve sorgunuzun paralel veya sıralı olarak çalışıp çalışmadığını belirleyebilirsiniz. Daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) ve [nasıl yapılır: PLINQ sorgu performansını ölçme](how-to-measure-plinq-query-performance.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
- [PLINQ'te Hızlandırmayı Anlama](understanding-speedup-in-plinq.md)
