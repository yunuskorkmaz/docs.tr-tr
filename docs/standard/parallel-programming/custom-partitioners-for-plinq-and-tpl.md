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
ms.openlocfilehash: 73c745fbbdb66777b50478623d969c125f92474b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698897"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>PLINQ ve TPL için Özel Bölümleyiciler
Bir işlem bir veri kaynağı üzerinde paralel hale getirmek için gerekli adımlar için biri *bölüm* birden çok iş parçacığı tarafından erişilebilen eşzamanlı olarak birden çok bölümlere kaynak. PLINQ ve görev paralel kitaplığı (TPL), paralel sorgu yazdığınızda şeffaf bir şekilde çalışması varsayılan bölümleyicilerin sağlayın veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü. Daha Gelişmiş senaryolar için kendi bölümleyici takabilirsiniz.  
  
## <a name="kinds-of-partitioning"></a>Bölümleme türleri  
 Bir veri kaynağı bölümlemek için birçok yolu vardır. Kaynak birden fazla demetlerin fiziksel olarak ayrılması yerine işlem özgün kaynak dizisi en verimli yaklaşımları birden çok iş parçacığı işbirliği yapar. Diziler ve diğer dizin kaynaklarını gibi <xref:System.Collections.IList> nerede uzunluğu bilinen önceden koleksiyonları *aralık bölümleme* bölümlemenin en basit türü. Her iş parçacığı, benzersiz dizin, tarihleri arasında üzerine yazmaya veya diğer iş parçacığı tarafından üzerine yazılmasını olmadan kaynak çeşitli işleyebilmesi alır. Yalnızca ek yükü de aralık bölümleme ilgili aralıkları oluşturmanın ilk çalışmadır; Ek eşitleme, daha sonra gereklidir. Bu nedenle, iş yükü şekilde eşit bölünür sürece iyi bir performans sağlayabilir. Aralık bölümleme bir dezavantajı, bir iş parçacığı erken tamamlanırsa işlerini son diğer iş parçacıklarını yardımcı olamaz, ' dir.  
  
 Bağlantılı liste veya uzunluğunu tanınmıyor diğer derlemeler için kullanabileceğiniz *öbek bölümleme*. Öbek bölümleme, her iş parçacığı veya bir paralel döngüde veya bir sorgu görevde bazı bir öbek kaynak öğe sayısı tüketir, işler ve ek öğeleri almak için geri gelir. Tüm öğeleri dağıtılır ve hiçbir Tekrarların bölümleyici sağlar. Bir öbek herhangi bir boyutta olabilir. Örneğin, örnekte gösterildiği bölümleyici [nasıl yapılır: Dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) yalnızca bir öğe içermelidir öbekleri oluşturur. Parçalar çok büyük olmayan sürece, iş parçacıkları öğelerin atama önceden belirlenemedi bölümleme bu tür Yük Dengeleme kendiliğinden olmasıdır. Ancak, bölümleyici eşitleme yükünü artırmak ve bu da iş parçacığı başka bir öbek almak için her durumda. Bu gibi durumlarda tahakkuk eşitleme miktarını öbek boyutunu inversely orantılıdır.  
  
 Genel olarak, aralık bölümleme yalnızca temsilci yürütme süresini Orta için küçük olduğunda ve öğeleri çok sayıda kaynak vardır ve her bölüm toplam iş kabaca eşdeğerdir daha hızlıdır. Öbek bölümleme bu nedenle çoğu durumda genellikle daha hızlıdır. Az sayıda öğeleri veya temsilci için artık yürütme süresi ile kaynaklarında performansını öbek ve aralık bölümleme hakkında eşit ise.  
  
 TPL bölümleyiciler dinamik bir bölüm sayısı da destekler. Bunlar oluşturabilirsiniz bölümleri üzerinde anında, örneğin başka bir deyişle, <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yeni bir görev olarak çoğaltılır. Bu özellik, döngü ile birlikte ölçeklendirmek bir bölümleyici sağlar. Dinamik bölümleyiciler kendiliğinden Yük Dengeleme de olur. Özel bir bölümleyici oluşturduğunuzda, gelen kullanılabilir olması için dinamik bölümlemeyi desteklemelidir bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>PLINQ için Bölümleyiciler yük dengelemeyi yapılandırma  
 Bazı aşırı yüklemeleri <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> yöntemi bir dizi için bir bölümleyici oluşturmanıza izin veren veya <xref:System.Collections.IList> kaynak ve iş parçacıkları arasında iş yükünü dengelemek denemelidir olup olmadığını belirtin. Bölümleyici yük dengelemek için yapılandırıldığında, öbek bölümleme kullanılır ve bunların istendiği gibi öğeleri kapalı küçük öbekler halinde her bölüm için verilir. Bu yaklaşım, tüm bölümleri kadar tüm döngü işlemek için öğeleri veya sorgu tamamlanmış olduğundan emin olun yardımcı olur. Ek bir aşırı bölümleme herhangi bir Yük Dengeleme sağlamak için kullanılan <xref:System.Collections.IEnumerable> kaynak.  
  
 Genel olarak, Yük Dengeleme öğeleri oldukça sık bölümleyici istek için bölümleri gerektirir. Aksine, statik bölümleme gerçekleştiren bir bölümleyici öğeler için her bir bölümleyici tümünü tek seferde aralığı veya öbek bölümleme kullanarak atayabilirsiniz. Bu, Yük Dengeleme çok daha az ek yük gerektirir, ancak diğerlerinden çok daha fazla iş bir iş parçacığı sonlanır, yürütmek için uzun sürebilir. IList ya da bir dizi geçirildiğinde varsayılan olarak PLINQ her zaman aralığı, Yük Dengeleme olmadan bölümleme kullanır. PLINQ için yük dengelemeyi etkinleştirmek için `Partitioner.Create` yöntemi, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 Yükleme kullanmak için belirli bir senaryoda Dengeleme denemeler yapın ve temsili yükler ve bilgisayar yapılandırmalarını altında tamamlamak için işlemleri ne kadar sürdüğünü ölçmek için olup olmadığını belirlemek için en iyi yolu. Örneğin, statik bölümleme yalnızca birkaç çekirdeği olan bir çok çekirdekli bilgisayarda önemli hızlandırmayı sağlayabilir, ancak oldukça fazla çekirdeğe sahip bilgisayarlarda yavaşlamalara neden olabilir.  
  
 Aşağıdaki tabloda kullanılabilir aşırı listeler <xref:System.Collections.Concurrent.Partitioner.Create%2A> yöntemi. Bu bölümleyiciler yalnızca PLINQ ile kullanmak için sınırlı değildir veya <xref:System.Threading.Tasks.Task>. Tüm özel paralel yapısı ile de kullanılabilir.  
  
|aşırı yükleme|Kullanan Yük Dengeleme|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Her zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Boole bağımsız değişkeni true belirtildiğinde|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Boole bağımsız değişkeni true belirtildiğinde|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|hiçbir zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|hiçbir zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|hiçbir zaman|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|hiçbir zaman|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Statik aralığı Bölümleyiciler Parallel.ForEach için yapılandırma  
 İçinde bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü, döngü gövdesinin yöntemi temsilci olarak sağlanır. Bu temsilci çağırma maliyeti, bir sanal yöntem çağrısının aynı hakkındadır. Bazı senaryolarda, paralel bir döngüden gövdesinin her döngü yinelemesinin üzerinde temsilci çağrısı maliyetini önemli hale kadar küçük olabilir. Bu gibi durumlarda, aşağıdakilerden birini kullanabilirsiniz <xref:System.Collections.Concurrent.Partitioner.Create%2A> oluşturmak için aşırı yüklemeler bir <xref:System.Collections.Generic.IEnumerable%601> aralığı bölümlerin kaynak öğeleri üzerinde. Ardından, bu aralıklar koleksiyonunu geçirebilirsiniz bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> gövde oluşur normal yöntemi `for` döngü. Bu yaklaşımın avantajı, temsilci çağırma yalnızca bir kez aralık başına yerine bir kez öğe başına ücret uygulanır emin olur. Aşağıdaki örnek, temel düzeni gösterir.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Her iş parçacığı döngüsünde kendi alır <xref:System.Tuple%602> başlangıç ve bitiş belirtilen alt aralığındaki dizini değerleri içeriyor. İç `for` döngü kullandığı `fromInclusive` ve `toExclusive` değerleri dizisi üzerinde döngü veya <xref:System.Collections.IList> doğrudan.  
  
 Aşağıdakilerden birini <xref:System.Collections.Concurrent.Partitioner.Create%2A> aşırı bölümler bölüm sayısı ve boyutu belirtmenize olanak sağlar. Bu aşırı yüklemesi, iş öğesi başına öğe başına tek bir sanal yöntem çağrısının performansı belirgin bir etkiye sahip kadar düşük olduğu senaryolarda kullanılabilir.  
  
## <a name="custom-partitioners"></a>Özel Bölümleyiciler  
 Bazı senaryolarda, faydalı veya hatta kendi bölümleyici uygulama için gerekli olabilir. Örneğin, bölümleyiciler bilginiz sınıfı iç yapısını tabanlı varsayılandan daha verimli bir şekilde bölüm bir özel koleksiyon sınıfı olabilir. Veya bilginiz ne kadar kaynak koleksiyondaki farklı konumlardaki işlem öğelerine sürer, bağlı olan çeşitli boyutlardaki aralığı bölümleri oluşturmak isteyebilirsiniz.  
  
 Temel, özel bir bölümleyici oluşturma için öğesinden bir sınıf türetin <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> ve sanal yöntemler aşağıdaki tabloda açıklandığı şekilde geçersiz kılın.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Bu yöntem, ana iş parçacığı tarafından bir kez çağrılır ve bir IList(IEnumerator(TSource)) döndürür. Her döngü veya sorgu iş parçacığı çağırabilirsiniz `GetEnumerator` almak için listede bir <xref:System.Collections.Generic.IEnumerator%601> farklı bir bölüme üzerinden.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Dönüş `true` uygularsanız <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, aksi takdirde, `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Varsa <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> olduğu `true`, bu yöntem yerine isteğe bağlı olarak çağrılabilir <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Ardından türetilmesi sonuçları sıralanabilir ya da bu öğeleri eklemek için dizini oluşturulmuş erişmesi <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> ve aşağıdaki tabloda açıklandığı gibi kendi sanal yöntemleri geçersiz kılın.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Bu yöntem, ana iş parçacığı tarafından bir kez çağrılır ve döndüren bir `IList(IEnumerator(TSource))`. Her döngü veya sorgu iş parçacığı çağırabilirsiniz `GetEnumerator` almak için listede bir <xref:System.Collections.Generic.IEnumerator%601> farklı bir bölüme üzerinden.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Dönüş `true` uygularsanız <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; Aksi takdirde false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Genellikle, bu yalnızca çağıran <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Varsa <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> olduğu `true`, bu yöntem yerine isteğe bağlı olarak çağrılabilir <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Aşağıdaki tabloda hakkında ek ayrıntılar sağlar üç farklı Yük Dengeleme bölümleyiciler uygulama <xref:System.Collections.Concurrent.OrderablePartitioner%601> sınıfı.  
  
|Metot/özellik|IList / Array yük dengelemesi olmadan|IList / Array ile Yük Dengeleme|IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Aralık bölümleme kullanır|Kullanımları listeler için belirtilen bölüm sayısı için en iyi duruma getirilmiş öbek bölümleme|Kullanır, öbek statik bir bölüm sayısı oluşturarak bölümleme.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Desteklenmeyen oluşturur özel durumu|Kullanımları listeler için en iyi duruma getirilmiş öbek bölümleme ve dinamik bölümleri|Kullanır, öbek dinamik bir bölüm sayısı oluşturarak bölümleme.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|döndürür `true`|döndürür `true`|döndürür `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|döndürür `true`|döndürür `false`|döndürür `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|döndürür `true`|döndürür `true`|döndürür `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|döndürür `false`|döndürür `true`|döndürür `true`|  
  
### <a name="dynamic-partitions"></a>Dinamik bölümleri  
 Kullanılacak bölümleyici düşünüyorsanız bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemi, sağlayabilmelidir bölümler dinamik bir sayısını döndürür. Başka bir deyişle döngü yürütme sırasında herhangi bir zamanda bölümleyici bir yeni bölümü isteğe bağlı bir numaralandırıcı sağlayabilirsiniz. Temel olarak, yeni paralel görev döngüyü ekler her görev için yeni bir bölüm ister. Veriler orderable gerekiyorsa, ardından öğesinden türetilen <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> böylece her bölümdeki her öğe benzersiz bir dizin atanır.  
  
 Daha fazla bilgi ve örnek için bkz [nasıl yapılır: Dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Sözleşme Bölümleyiciler  
 Özel bir bölümleyici uygulama PLINQ doğru etkileşimi sağlamak için aşağıdaki yönergeleri izleyin ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> tpl'de:  
  
-   Varsa <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> adlı bağımsız değişkeni sıfır veya daha az `partitionsCount`, throw <xref:System.ArgumentOutOfRangeException>. PLINQ ve TPL hiçbir zaman içinde geçer ancak bir `partitionCount` 0 eşittir, ancak yine de olasılığını karşı koruma sağlamak öneririz.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> ve <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> her zaman döndürmelidir `partitionsCount` bölüm sayısı. Bölümleyici verileri çalıştırır ve istenen sayıda bölüm oluşturulamıyor, yöntem her kalan bir bölüm için boş bir numaralandırıcı döndürmesi gerekir. Aksi takdirde, PLINQ ve TPL hem oluşturmaz bir <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, ve <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> hiçbir zaman döndürmelidir `null` (`Nothing` Visual Basic'te). Eğer öyleyse, PLINQ / TPL oluşturur bir <xref:System.InvalidOperationException>.  
  
-   Bölümler döndüren yöntemler, her zaman tam olarak ve benzersiz bir şekilde veri kaynağı numaralandırabilirsiniz bölümler döndürmelidir. Özel bölümleyici tasarımını tarafından gerekli kılınmadıkça hiçbir çoğaltma veri kaynağı veya atlanan öğeleri olmalıdır. Bu kural uyulmazsa, çıkış sırası karıştırılmış.  
  
-   Böylece çıkış sırasını değil karıştırılmış aşağıdaki Boole alıcıları her zaman doğru bir şekilde aşağıdaki değerleri döndürmesi gerekir:  
  
    -   `KeysOrderedInEachPartition`: Her bölüm anahtar dizinlerini artan öğeleri döndürür.  
  
    -   `KeysOrderedAcrossPartitions`: Bölüm anahtar çiftlerine getirilen tüm bölümler için *miyim* bölüm anahtar çiftlerine yüksektir *miyim*-1.  
  
    -   `KeysNormalized`: Tüm anahtar dizinlerini tekdüze sıfırdan başlayarak, boşluk olmadan artmaktadır.  
  
-   Tüm dizinler benzersiz olması gerekir. Yinelenen dizinleri olmayabilir. Bu kural uyulmazsa, çıkış sırası karıştırılmış.  
  
-   Tüm dizinler negatif olmamalıdır. Bu kural uyulmazsa, PLINQ/TPL özel durumlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Nasıl yapılır: Dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)
- [Nasıl yapılır: Statik bölümleme için bir Bölümleyici uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
