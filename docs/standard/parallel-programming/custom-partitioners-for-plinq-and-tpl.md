---
title: PLINQ ve TPL için Özel Bölümleyiciler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0868ce76f82ed0575154744d9ab02814a0bd990a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>PLINQ ve TPL için Özel Bölümleyiciler
Bir veri kaynağı üzerinde bir işlemi paralel hale için gerekli adımları için biri *bölüm* birden çok iş parçacığı tarafından eşzamanlı olarak erişilebilir birden çok bölümlere kaynak. PLINQ ve görev paralel kitaplığı (TPL) saydam bir paralel sorgu yazma ne zaman çalışması varsayılan bölümleyiciler sağlayın veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü. Daha Gelişmiş senaryolar için kendi bölümleyici ekleyebilirsiniz.  
  
## <a name="kinds-of-partitioning"></a>Bölümlendirme, türleri  
 Bir veri kaynağı bölümlemek için birçok yolu vardır. En verimli yaklaşımlar birden çok iş parçacığı işlemi özgün kaynak sırası yerine fiziksel olarak kaynak birden çok sıraları ayırmak üzere işbirliği yapar. Diziler ve diğer dizine kaynakları gibi <xref:System.Collections.IList> burada uzunluğu bilinen önceden koleksiyonları *aralığı bölümleme* bölümlendirme, basit tür. Böylece üzerine yazmaya veya diğer iş parçacığı tarafından üzerine yazılmasını olmadan kaynağı olan çeşitli işleyebilir benzersiz başlangıç ve bitiş dizinler, her iş parçacığı alır. Aralık bölümleme söz konusu yalnızca ek yükü aralıkları oluşturma ilk iş var; hiçbir ek eşitleme bundan sonra gereklidir. Bu nedenle, iş yükü eşit olarak bölünür sürece iyi bir performans sağlayabilir. Aralık bölümleme bir dezavantajı tek bir iş parçacığı erken tamamlanırsa, işlerini son başka iş parçacıkları yardımcı olamaz emin olur.  
  
 Bağlantılı listeler veya uzunluğunu bilinmiyor diğer koleksiyonlar için kullanabileceğiniz *öbek bölümleme*. Öbek bölümlendirme, her iş parçacığı ya da görev paralel döngü veya sorguda bir öbek kaynak öğe bazı sayısı kullanır, bunları işler ve ek öğeler almak için geri gelir. Tüm öğeleri dağıtılır ve yinelenen olduğunu bölümleyici sağlar. Bir öbek herhangi bir boyutta olabilir. Örneğin, örnekte gösterildiği bölümleyici [nasıl yapılır: dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) yalnızca bir öğe içermesi öbekleri oluşturur. Öbek çok büyük olmayan sürece, iş parçacıkları öğelerine atama önceden belirlenemedi bu tür bölümleme kendiliğinden Yük Dengeleme olmasıdır. Ancak, bölümleyici eşitleme yükünü artırmak ve bu da her zaman başka bir öbek almak için iş parçacığı gerekiyor. Bu durumlarda ücrete eşitleme miktarını öbek boyutunu inversely orantılıdır.  
  
 Genel olarak, aralığı bölümleme yalnızca temsilci yürütme süresini Orta için küçük ve öğeleri çok sayıda kaynak olduğunda ve her bölümün toplam iş kabaca eşdeğerdir daha hızlıdır. Öbek bölümleme bu nedenle çoğu durumda genelde daha hızlıdır. Öğeleri veya uzun yürütme sürelerinin temsilci için az sayıda kaynaklarıyla üzerinde performansı öbek ve aralığı bölümleme hakkında eşit ise.  
  
 TPL bölümleyiciler dinamik bir bölüm sayısı da destekler. Bunlar oluşturabilirsiniz bölümleri üzerinde-çalışma sırasında Örneğin bu anlamına gelir, ne zaman <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yeni bir görev olarak çoğaltılır. Bu özellik, döngü ile birlikte ölçeklendirmek bölümleyici sağlar. Dinamik bölümleyiciler de kendiliğinden Yük Dengeleme. Özel bir bölümleyici oluşturduğunuzda, gelen tüketilebilir olması için dinamik bölümleme desteklemelidir bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Yük Dengeleme Bölümleyiciler PLINQ için yapılandırma  
 Bazı aşırı <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> yöntemi bir dizi için bir bölümleyici oluşturma izin vermek veya <xref:System.Collections.IList> kaynağı ve iş parçacıkları arasında iş yükünü dengelemek denemelidir olup olmadığını belirtin. Bölümleyici yük dengelemek için yapılandırıldığında, öbek bölümleme kullanılır ve bunların istendiği gibi öğeleri kapalı küçük parçalara her bölümün verilir. Bu yaklaşım, tüm bölümleri kadar tüm döngü işlemek için öğelere sahip veya sorgu tamamlandı sağlamaya yardımcı olur. Ek bir aşırı yük dengeleme herhangi birini bölümleri sağlamak için kullanılabilir <xref:System.Collections.IEnumerable> kaynak.  
  
 Genel olarak, Yük Dengeleme öğeleri görece sık bölümleyici isteği bölümlerini gerektirir. Bunun aksine, statik bölümleme yapan bir bölümleyici öğeleri her bölümleyici tümünü bir defada aralığı veya öbek bölümleme kullanarak atayabilirsiniz. Bu Yük Dengeleme daha az ek yük gerektirir, ancak bir iş parçacığı önemli ölçüde daha fazla iş diğerlerinden ererse yürütmek için uzun sürebilir. IList ya da bir dizi geçirildiğinde varsayılan olarak PLINQ her zaman aralığı Yük Dengeleme olmadan bölümleme kullanır. Yük Dengeleme için PLINQ etkinleştirmek için `Partitioner.Create` aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 Yükleme kullanmak için belirli bir senaryoda Dengeleme denemek ve temsili yükler ve bilgisayar yapılandırmalarını altında tamamlanması için işlemleri süreyi ölçmek için olup olmadığını belirlemek için en iyi yolu. Örneğin, statik bölümleme önemli speedup yalnızca birkaç çekirdeğe sahip bir çok çekirdekli bilgisayarda sağlayabilir, ancak göreceli olarak pek çok çekirdek bilgisayarlara yavaşlamalara neden.  
  
 Aşağıdaki tabloda kullanılabilir aşırı <xref:System.Collections.Concurrent.Partitioner.Create%2A> yöntemi. Bu bölümleyiciler yalnızca PLINQ ile kullanmak için sınırlı değildir veya <xref:System.Threading.Tasks.Task>. Tüm özel paralel yapı ile de kullanılabilir.  
  
|Aşırı yükleme|Yük Dengeleme kullanır|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Her zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Boole bağımsız değişkeni doğru olarak belirtildiğinde|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Boole bağımsız değişkeni doğru olarak belirtildiğinde|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Hiçbir zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Hiçbir zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Hiçbir zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Hiçbir zaman|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Statik aralığı Bölümleyiciler Parallel.ForEach için yapılandırma  
 İçinde bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü, döngünün gövdesi yöntemine temsilci olarak sağlanır. Bu temsilci çağırma sanal yöntem çağrısı ile aynı hakkında maliyetidir. Bazı senaryolarda, paralel bir döngüden gövdesinin her döngü tekrarında temsilci çağrısının maliyetini önemli hale yetecek kadar küçük olabilir. Böyle durumlarda, aşağıdakilerden birini kullanabilirsiniz <xref:System.Collections.Concurrent.Partitioner.Create%2A> oluşturmak için aşırı bir <xref:System.Collections.Generic.IEnumerable%601> kaynağı öğeleri üzerinden aralığı bölümlerinin. Aralıklar için bu koleksiyonu daha sonra geçirin bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> , gövde oluşur normal yöntemi `for` döngü. Bu yaklaşımın avantajı, temsilci çağırma maliyet aralık başına yerine bir kez öğesi başına yalnızca bir kez sıkıştırılır ' dir. Aşağıdaki örnek, temel düzeni gösterir.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Her iş parçacığı döngüsünde kendi alan <xref:System.Tuple%602> başlangıç ve bitiş dizin değerlerinin belirtilen alt aralığında içerir. İç `for` döngü kullanır `fromInclusive` ve `toExclusive` dizi döngü değerleri veya <xref:System.Collections.IList> doğrudan.  
  
 Aşağıdakilerden birini <xref:System.Collections.Concurrent.Partitioner.Create%2A> aşırı bölümler ve bölüm boyutu belirtmenize olanak sağlar. Bu aşırı öğesi başına iş öğesi başına tek sanal yöntem çağrısı performansı belirgin bir etkiye sahip kadar düşük olduğu senaryolarda kullanılabilir.  
  
## <a name="custom-partitioners"></a>Özel Bölümleyiciler  
 Bazı senaryolarda faydalı ya da kendi bölümleyici uygulamak için bile gerekli olabilir. Örneğin, bölümleyiciler bilginiz iç yapısı sınıfın temel varsayılandan daha verimli bir şekilde bölüm özel koleksiyon sınıfına sahip olabilir. Veya, ne kadar bu işlemi öğelere kaynak koleksiyondaki farklı konumlarda sürer, bilginiz göre farklı boyutlarda aralığı bölümlerini oluşturmak isteyebilirsiniz.  
  
 Temel özel bölümleyici oluşturma için öğesinden bir sınıf türetin <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> ve aşağıdaki tabloda açıklandığı gibi sanal yöntemleri geçersiz kılın.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Bu yöntem, ana iş parçacığı tarafından bir kez çağrılır ve bir IList(IEnumerator(TSource)) döndürür. Döngü veya sorgudaki her bir çalışan iş parçacığı çağırabilir `GetEnumerator` almak için listedeki bir <xref:System.Collections.Generic.IEnumerator%601> ayrı bir bölüm üzerinde.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Dönüş `true` öğesini uygularsanız <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, aksi takdirde `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Varsa <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> olan `true`, bu yöntem yerine isteğe bağlı olarak çağrılabilir <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Sonuçları sıralanabilir veya elemanlara dizine alınan erişimi gerektirir, ardından öğesinden türetilen <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> ve aşağıdaki tabloda açıklandığı gibi sanal yöntemlerini geçersiz kılar.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Bu yöntem, ana iş parçacığı tarafından bir kez çağrılır ve döndüren bir `IList(IEnumerator(TSource))`. Döngü veya sorgudaki her bir çalışan iş parçacığı çağırabilir `GetEnumerator` almak için listedeki bir <xref:System.Collections.Generic.IEnumerator%601> ayrı bir bölüm üzerinde.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Dönüş `true` öğesini uygularsanız <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; Aksi takdirde false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Genellikle, bu yalnızca çağırır <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Varsa <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> olan `true`, bu yöntem yerine isteğe bağlı olarak çağrılabilir <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Aşağıdaki tabloda hakkında ek ayrıntılar sağlanmaktadır Yük Dengeleme bölümleyiciler uygulama üç tür <xref:System.Collections.Concurrent.OrderablePartitioner%601> sınıfı.  
  
|Yöntem/özellik|IList / dizi Yük Dengeleme olmadan|IList / dizi yük dengelemesi ile|IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Aralık bölümleme kullanır|Belirtilen bölüm sayısı için listeler için en iyi duruma getirilmiş öbek kullanır bölümlendirme|Kullanır, statik bir bölüm sayısı oluşturarak öbek bölümleme.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Desteklenmeyen atar özel durumu|Listeler için en iyi duruma getirilmiş öbek kullanır bölümlendirme ve dinamik bölümleri|Kullanır, dinamik bir bölüm sayısı oluşturarak öbek bölümleme.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|döndürür `true`|döndürür `true`|döndürür `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|döndürür `true`|döndürür `false`|döndürür `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|döndürür `true`|döndürür `true`|döndürür `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|döndürür `false`|döndürür `true`|döndürür `true`|  
  
### <a name="dynamic-partitions"></a>Dinamik bölümleri  
 Kullanılacak bölümleyici düşünüyorsanız bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemi, sağlayabilmelidir bölümleri dinamik sayısını döndürür. Başka bir deyişle, döngü yürütme sırasında herhangi bir zamanda bölümleyici bir yeni bölümü isteğe bağlı için bir numaralandırıcı sağlayabilir. Temel olarak, yeni bir paralel görev döngü ekler her görev için yeni bir bölüm ister. Verilerin orderable gerekiyorsa, ardından öğesinden türetilen <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> böylece her bölüm her öğe benzersiz bir dizin atanır.  
  
 Daha fazla bilgi ve bir örnek için bkz: [nasıl yapılır: dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Sözleşme Bölümleyiciler için  
 Özel bir bölümleyici uyguladığınızda PLINQ doğru etkileşim sağlamaya yardımcı olmak için aşağıdaki yönergeleri izleyin ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> tpl'de:  
  
-   Varsa <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> çağrılan bağımsız değişkeni sıfır veya daha az `partitionsCount`, throw <xref:System.ArgumentOutOfRangeException>. PLINQ ve TPL hiçbir zaman içinde geçecek rağmen bir `partitionCount` 0 değerine eşit, ancak yine de olasılığını karşı koruma öneririz.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> ve <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> her zaman döndürmelidir `partitionsCount` bölüm sayısı. Bölümleyici veri dışında çalışır ve istendiği gibi birçok bölüm oluşturulamıyor, yöntem her kalan bölümleri için boş bir numaralandırıcı döndürmelidir. PLINQ ve TPL Aksi takdirde, özel durum oluşturacak bir <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, ve <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> hiçbir zaman döndürmelidir `null` (`Nothing` Visual Basic'te). İçermiyorlarsa PLINQ / TPL throw bir <xref:System.InvalidOperationException>.  
  
-   Bölümler döndüren yöntemler her zaman tam olarak ve benzersiz veri kaynağı numaralandırabilir bölümleri döndürmelidir. Özellikle bölümleyici tasarım tarafından gerekli kılınmadıkça hiçbir veri kaynağı veya atlanan öğeleri tekrarları olmalıdır. Bu kural uyulmazsa çıkış sırası karıştırılmış.  
  
-   Böylece çıkış sırası değil karıştırılmış aşağıdaki Boolean alıcıları her zaman doğru bir şekilde aşağıdaki değerler döndürmesi gerekir:  
  
    -   `KeysOrderedInEachPartition`: Her bölüm anahtarı dizinlerini artan öğeleri döndürür.  
  
    -   `KeysOrderedAcrossPartitions`: Bölüm anahtar çiftlerine getirilen tüm bölümler için *ı* bölüm anahtar çiftlerine yüksektir *ı*-1.  
  
    -   `KeysNormalized`: Tüm anahtar dizinlerini tekdüze sıfırdan başlangıç boşluk olmayan artmaktadır.  
  
-   Tüm dizinler benzersiz olması gerekir. Yinelenen dizinler olmayabilir. Bu kural uyulmazsa çıkış sırası karıştırılmış.  
  
-   Tüm dizinler negatif olmayan olması gerekir. Bu kural uyulmazsa PLINQ/TPL özel durumlar oluşturma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [Nasıl yapılır: Dinamik Bölümleri Uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
 [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
