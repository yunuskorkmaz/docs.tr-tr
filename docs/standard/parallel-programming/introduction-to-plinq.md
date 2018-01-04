---
title: "PLINQ'e Giriş"
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
helpviewer_keywords: PLINQ queries, introduction to
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d14f82fa73400695faad49f010e6ef52a14dd9e3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-plinq"></a>PLINQ'e Giriş
## <a name="what-is-a-parallel-query"></a>Paralel Sorgu nedir?  
 Dil ile tümleşik sorgu (LINQ) içinde sunulmuştur [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  Herhangi bir sorgulama için birleşik bir modeli özellikleri <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> bir tür kullanımı uyumlu şekilde veri kaynağı. Nesnelere LINQ bellek içi koleksiyonları karşı gibi çalıştırmak LINQ sorgularını addır <xref:System.Collections.Generic.List%601> ve dizi. Bu makalede LINQ temel bir anlama sahip olduğunuzu varsayar. Daha fazla bilgi için bkz: [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Paralel LINQ (PLINQ) bir paralel LINQ düzeni uygulamasıdır. Birçok yolu PLINQ sorgusunda olmayan paralel LINQ to nesneleri sorgusunda benzer. PLINQ sorguları, olduğu gibi sıralı [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] sorguları, çalışan tüm bellek içi üzerinde <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> veri kaynağı ve bunlar değil başlamak sorgu numaralandırılan kadar yürütme anlamına gelir yürütme ertelenmiş. PLINQ sistemdeki tüm işlemcilerin tam kullanımını yapma girişiminde birincil farktır. Veri kaynağı kesimler halinde bölümlendirme ve birden çok işlemci üzerinde paralel ayrı çalışan iş parçacığı üzerinde her kesiminde sorgu yürütülürken tarafından bunu yapar. Çoğu durumda, sorgu önemli ölçüde daha hızlı çalışır, Paralel yürütme anlamına gelir.  
  
 Paralel yürütme, sorguları, ekleyerek genellikle yalnızca belirli türdeki için eski kod üzerinden, önemli performans geliştirmeleri PLINQ gerçekleştirebilirsiniz <xref:System.Linq.ParallelEnumerable.AsParallel%2A> sorgu veri kaynağı işlemi. Ancak, paralellik kendi karmaşıklık getirebilir ve tüm sorgu işlemleri PLINQ'te daha hızlı çalışır. Aslında, paralelleştirme gerçekte bazı sorgular yavaşlatır. Bu nedenle, sıralama gibi sorunlar paralel sorgular nasıl etkileyeceğini anlamanız gerekir. Daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
> [!NOTE]
>  Bu belge lambda ifadeleri temsilciler PLINQ'te tanımlamak için kullanır. C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Bu makalenin sonraki bölümlerinde ana PLINQ sınıfları genel bir bakış sağlar ve PLINQ sorgu oluşturma açıklanır. Her bölüm daha ayrıntılı bilgi ve kod örnekleri bağlantılar içerir.  
  
## <a name="the-parallelenumerable-class"></a>ParallelEnumerable Sınıfı  
 <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> Sınıfı neredeyse tüm PLINQ'in işlevselliğini kullanıma sunar.  Bu ve diğer <xref:System.Linq?displayProperty=nameWithType> ad alanı türleri System.Core.dll bütünleştirilmiş koda derlenmiş. Visual Studio'da varsayılan C# ve Visual Basic projeleri derleme başvurusu hem ad içeri aktarın.  
  
 <xref:System.Linq.ParallelEnumerable>her biri paralel hale çalışmaz ancak nesnelere LINQ destekleyen tüm standart sorgu işleçlerinin uygulamaları içerir. Alışık değilseniz [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], bkz: [Lınq'ye](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).  
  
 Standart sorgu işleçleri yanı sıra <xref:System.Linq.ParallelEnumerable> sınıfı Paralel yürütme belirli davranışları sağlayan yöntemler kümesi içerir. Bu PLINQ özgü yöntemleri aşağıdaki tabloda listelenmiştir.  
  
|ParallelEnumerable işleci|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|PLINQ için giriş noktası. Mümkünse sorgunun kalan bölümüyle paralel birkaç ölçeklendirin olduğunu, belirtir.|  
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Sorgunun kalan bölümüyle ardışık olarak olmayan paralel LINQ Sorgu olarak çalıştırılması gerektiğini belirtir.|  
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|PLINQ sorgu veya sıralama, örneğin (Order By Vlsual Basic'te) orderby yan tümcesinin kullandığı değiştirilene kadar kalan için kaynak sıradaki sıralama korumak belirtir.|  
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|PLINQ sorgu geri kalanı için kaynak dizi sıralaması korumak için gerekli olmadığını belirtir.|  
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|PLINQ düzenli aralıklarla sağlanan iptal belirteci durumunu izlemek ve istenirse yürütme iptal belirtir.|  
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|En fazla PLINQ sorgu paralel hale kullanması gereken işlemci sayısını belirtir.|  
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Mümkünse, nasıl PLINQ gerektiği hakkında bir ipucu sağlar Süren iş parçacığı üzerinde yalnızca bir sıralı uygulamasına geri paralel sonuçları birleştirir.|  
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Sıralı olarak çalıştırmak için varsayılan davranış bile olacaktır zaman PLINQ sorgu paralel hale olup olmadığını belirtir.|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Sağlayan, sorgu sonuçları yineleme aksine ilk geri tüketici iş parçacığı için birleştirme olmadan paralel olarak işlenecek sonuçları birden çok iş parçacıklı numaralandırma yöntemi.|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>aşırı yükleme|PLINQ için benzersizdir ve iş parçacığı yerel bölümleri artı tüm bölümleri sonuçlarını birleştirmek için bir son toplama işlevi ara toplama sağlayan bir aşırı.|  
  
## <a name="the-opt-in-model"></a>Abone Olma Modeli  
 Bir sorgu yazdığınızda, PLINQ için çağırarak kabul <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> genişletme yöntemi aşağıdaki örnekte gösterildiği gibi veri kaynağı üzerinde.  
  
 [!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
 [!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]  
  
 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> Genişletme yöntemi bağlar sonraki sorgu işleçleri bu durumda, `where` ve `select`, <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> uygulamaları.  
  
## <a name="execution-modes"></a>Yürütme Modları  
 Varsayılan olarak, PLINQ koruyucu. Çalışma zamanında PLINQ altyapı sorgu genel yapısını analiz eder. Sorgu speedups paralelleştirme tarafından elde etmek üzere olasılığı varsa, kaynak sırası, eşzamanlı olarak çalışan görevler içine PLINQ bölümler. Bir sorgu paralel hale güvenli değilse, PLINQ yalnızca sorgu sırayla çalıştırır. PLINQ olası pahalı bir paralel algoritması veya pahalı olmayan bir sıralı algoritma arasında bir seçim varsa, varsayılan olarak sıralı algoritmasını seçer. Kullanabileceğiniz <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi ve <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> paralel algoritmasını seçmek için PLINQ istemek üzere numaralandırması. Test etme ve belirli bir sorgu paralel olarak hızlı yürütür ölçüm bildiğiniz durumlarda kullanışlıdır. Daha fazla bilgi için bkz: [nasıl yapılır: PLINQ'te yürütme modunu belirtme](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
## <a name="degree-of-parallelism"></a>Paralellik Derecesi  
 Varsayılan olarak, PLINQ tüm işlemcilerin ana bilgisayara kullanır. Belirtilen bir işlemci sayısı birden fazla kullanarak PLINQ söyleyebilirsiniz <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> yöntemi. Bilgisayarda çalışan başka işlemler belirli bir miktarda CPU süresi aldığınızdan emin olmak istediğinizde kullanışlıdır. Aşağıdaki kod parçacığında en fazla iki işlemci kullanılarak sorgu sınırlar.  
  
 [!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
 [!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]  
  
 Bir sorgu önemli miktarda dosya g/ç gibi işlem bağlı iş yeri gerçekleştiriyor durumlarda çekirdek sayısından büyük paralellik derecesini makinede belirtmek faydalı olabilir.  
  
## <a name="ordered-versus-unordered-parallel-queries"></a>Sıralı ve Sırasız Paralel Sorgular  
 Bazı sorgular, sorgu işleci kaynak dizi sıralaması korumak sonuçlara yol gerekir. PLINQ sağlar <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> bu amaçla işleci. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>farklıdır <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. Bir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> dizisi hala paralel olarak işlenir, ancak sonuçlarını arabelleğe ve sıralanır. Sıra koruma genellikle ek iş içerdiğinden bir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> dizisi işlenmesi varsayılan daha yavaş <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> dizisi. Belirli bir sıralı paralel işlem işlemi sıralı bir sürümünü daha hızlı olup olmadığını birçok faktöre bağlıdır.  
  
 Aşağıdaki kod örneğinde, sıra koruma için kabul gösterilmektedir.  
  
 [!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
 [!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]  
  
 Daha fazla bilgi için bkz: [plınq'te sıra koruma](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="parallel-vs-sequential-queries"></a>Paralel vs. Sıralı sorguları  
 Bazı işlemler, veri kaynağını sıralı bir şekilde teslim edilmesi gerekir. <xref:System.Linq.ParallelEnumerable> Sorgu işleçleri, gerekli olduğunda sıralı moduna otomatik olarak geri döndürüyoruz. Kullanıcı tanımlı sorgu işleçleri ve sıralı yürütme gerektiren kullanıcı temsilcileri için PLINQ sağlar <xref:System.Linq.ParallelEnumerable.AsSequential%2A> yöntemi. Kullandığınızda <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, sorgudaki tüm sonraki işleçleri kadar sırayla yürütülen <xref:System.Linq.ParallelEnumerable.AsParallel%2A> yeniden adlandırılır. Daha fazla bilgi için bkz: [nasıl yapılır: birleştirmek paralel ve sıralı LINQ sorgularını](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).  
  
## <a name="options-for-merging-query-results"></a>Sorgu Sonuçlarını Birleştirme Seçenekleri  
 Tüketimi için ana iş parçacığı üzerine geri bir PLINQ sorgusu paralel olarak yürütüldüğünde, her iş parçacığı kendi sonuçlarından birleştirilmelidir bir `foreach` döngü (`For Each` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), veya bir liste veya dizi ekleme. Bazı durumlarda, örneğin birleştirme işlemi, belirli bir tür belirtmek için sonuçlar daha hızlı oluşturan başlamak için faydalı olabilir. Bu amaçla PLINQ destekleyen <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> yöntemi ve <xref:System.Linq.ParallelMergeOptions> numaralandırması. Daha fazla bilgi için bkz: [plınq'te Birleştirme Seçenekleri](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
## <a name="the-forall-operator"></a>ForAll İşleci  
 Sıralı olarak [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] sorguları, yürütme sorgu numaralandırılan kadar ertelenmiş ya da bir `foreach` (`For Each` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) döngü veya göre çağrılırken bir yöntem gibi <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> , veya <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. De kullanabilirsiniz, PLINQ'te `foreach` sorguyu yürütmek ve sonuçlarını yinelemek için. Ancak, `foreach` kendisini paralel olarak çalışmaz ve bu nedenle, tüm Paralel Görevler çıktısını geri döngü çalıştığı akışına birleştirilemez gerektirir. PLINQ'te, kullandığınız `foreach` zaman son sorgu sonuçlarını sıralama korumanız gerekir ve ayrıca her işlediğiniz sonuçları, çağrılırken örneğin seri bir şekilde `Console.WriteLine` her öğe için. İçin daha hızlı sorgu yürütme sıra koruma gerekli olmadığında ve sonuçları işlenmesini kendisini paralel birkaç ölçeklendirin kullanacağınız <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi bir PLINQ sorgusu yürütülemedi. <xref:System.Linq.ParallelEnumerable.ForAll%2A>Bu son birleştirme adım gerçekleştirmez. Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>aynı anda tüm öğeleri kaldırmak çalışırken olmadan ekleme birden çok iş parçacığı için optimize edilmiş olduğundan burada kullanılır.  
  
 [!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
 [!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]  
  
 Aşağıdaki çizimde arasındaki farkı gösterir `foreach` ve <xref:System.Linq.ParallelEnumerable.ForAll%2A> sorgu yürütme sabittir.  
  
 ![ForAll vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")  
  
## <a name="cancellation"></a>İptal Etme  
 PLINQ iptal türler ile tümleştirildiğinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. (Daha fazla bilgi için bkz: [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).) Bu nedenle, nesneler sorgulara sıralı LINQ PLINQ sorguları iptal edilebilir. İptal edilebilen bir PLINQ sorgusu oluşturmak için kullanmak <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu işlecinin ve sağlayan bir <xref:System.Threading.CancellationToken> örneği bağımsız değişkeni olarak. Zaman <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> belirteç özelliği PLINQ true olarak ayarlanmış, dikkat, tüm iş parçacıklarında işlemeyi durdur ve throw bir <xref:System.OperationCanceledException>.  
  
 PLINQ sorgusunu iptal belirteci ayarlandıktan sonra bazı öğeler işlemeye devam edebilir mümkündür.  
  
 Büyük yanıtlama hızı için uzun süre çalışan kullanıcı temsilcileri içinde iptal isteklerini yanıtlayabilir. Daha fazla bilgi için bkz: [nasıl yapılır: PLINQ sorgusunu iptal](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="exceptions"></a>Özel Durumlar  
 Bir PLINQ sorgusu yürütüldüğünde, birden çok farklı iş parçacığı tarafından eşzamanlı olarak özel durumlar. Ayrıca, farklı bir iş parçacığında özel durum oluşturdu kodu daha özel durumu işlemek üzere kod olabilir. PLINQ kullanan <xref:System.AggregateException> bir sorgu tarafından oluşturulan tüm özel durumları kapsülleyen yazın ve bu özel durumlar çağıran iş parçacığı dön'ı sıralama. Çağıran iş parçacığı üzerinde yalnızca bir try-catch bloğu gereklidir. Ancak, tüm içinde kapsüllenmiş özel durumların aracılığıyla yineleyebilirsiniz <xref:System.AggregateException> ve güvenli bir şekilde kurtarabilir herhangi catch. Nadir durumlarda bazı özel durumlar olarak kaydırılan değil durum oluşturulabilir bir <xref:System.AggregateException>, ve <xref:System.Threading.ThreadAbortException>s ayrıca değil sarılır.  
  
 Özel durum oluşturulduktan sonra bazı öğeleri işlemek bir sorgu devam edebilir mümkündür ne zaman özel durumlar oluşturan geri katılma akışa Kabarcık izin verilir.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: PLINQ sorgusunda özel durumları işlemek](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="custom-partitioners"></a>Özel Bölümleyiciler  
 Bazı durumlarda, bazı karakteristiğini kaynak verileri, yararlanan özel bir bölümleyici yazarak sorgu performansını iyileştirebilir. Sorgu, özel bölümleyici sorgulanan numaralandırılabilir nesnesidir.  
  
 [!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
 [!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]  
  
 (Veri dinamik olarak o bölümler için Yük Dengeleme için çalışma zamanı sırasında atanabilir. rağmen) PLINQ bölümleri sabit sayıda destekler. <xref:System.Threading.Tasks.Parallel.For%2A>ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> yalnızca dinamik bölümlendirme, bölümler değişiklik sayısı çalışma zamanında anlamına destekler. Daha fazla bilgi için bkz: [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="measuring-plinq-performance"></a>PLINQ Performansını Ölçme  
 Çoğu durumda, bir sorgu paralel birkaç ölçeklendirin, ancak elde edilen performans avantajı paralel sorgulamasını oluşturma yükünü ağır. Bir sorgu kadar hesaplama yapmıyorsa veya veri kaynağı küçükse, bir PLINQ sorgusu sıralı LINQ to nesneleri sorgusunda daha yavaş olabilir. İşleme engelleri bulun ve sorgunuzu paralel veya sıralı olarak çalışıp çalışmadığını belirlemek için çeşitli sorguların performansını karşılaştırmak için Visual Studio Team Server'da paralel Performans Çözümleyicisi'ni kullanın. Daha fazla bilgi için bkz: [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) ve [nasıl yapılır: PLINQ sorgu performansını ölçü](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [PLINQ'te Hızlandırmayı Anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
