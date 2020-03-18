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
ms.openlocfilehash: 8caea6d8a97b8c0daf7c59718479ea2e12a52d78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141561"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>PLINQ ve TPL için Özel Bölümleyiciler

Bir işlemi veri kaynağındaki bir işlemi paralelleştirmek için, temel adımlardan biri kaynağı aynı anda birden çok iş parçacığı tarafından erişilebilen birden çok bölüme *bölmektir.* PLINQ ve Görev Paralel Kitaplığı (TPL), paralel sorgu veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yazdığınızda saydam olarak çalışan varsayılan bölümleyiciler sağlar. Daha gelişmiş senaryolar için, kendi bölümleyici takabilirsiniz.

## <a name="kinds-of-partitioning"></a>Bölümleme Türleri

Bir veri kaynağını bölmenin birçok yolu vardır. En verimli yaklaşımlarda, birden çok iş parçacığı, kaynağı fiziksel olarak birden çok alt diziye ayırmak yerine özgün kaynak sırasını işlemek için işbirliği yapar. Uzunluk önceden bilinen koleksiyonlar gibi <xref:System.Collections.IList> diziler ve diğer dizilimli kaynaklar için *aralık bölümleme* en basit bölümleme türüdür. Her iş parçacığı benzersiz başlangıç ve bitiş dizinleri alır, böylece kaynak aralığını başka bir iş parçacığı tarafından üzerine yazılmadan veya üzerine yazılmadan işleyebilir. Aralık bölümleme ile ilgili tek ek yükü aralıkları oluşturma nın ilk çalışmasıdır; bundan sonra ek bir eşitleme gerekmez. Bu nedenle, iş yükü eşit olarak bölündüğü sürece iyi performans sağlayabilir. Aralık bölümlemenin bir dezavantajı, bir iş parçacığı erken biterse, diğer iş parçacıklarının işlerini bitirmelerine yardımcı olamaz.

Bağlı listeler veya uzunluğu bilinmeyen diğer koleksiyonlar için *yığın bölümleme*kullanabilirsiniz. Yığın bölümlemede, paralel döngü veya sorgudaki her iş parçacığı veya görev bir yığında bazı kaynak öğelerini tüketir, işler ve ek öğeleri almak için geri gelir. Bölümleyici, tüm öğelerin dağıtılmasını ve yineleyici olmamasını sağlar. Bir yığın herhangi bir boyutta olabilir. Örneğin, [Nasıl Yapılır: Dinamik Bölümleri Uygulama'da](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) gösterilen bölümleyici, yalnızca bir öğe içeren parçalar oluşturur. Parçalar çok büyük olmadığı sürece, bu tür bölümleme doğal olarak yük dengelemedir, çünkü öğelerin iş parçacıklarına atanması önceden belirlenmemiştir. Ancak, bölümleyici iş parçacığı başka bir yığın almak için her zaman eşitleme yükü tabi yok. Bu gibi durumlarda tahakkuk eden eşitleme miktarı, parçaların boyutuyla ters orantılıdır.

Genel olarak, aralık bölümleme yalnızca temsilcinin yürütme süresi küçük ve kaynak öğeleri çok sayıda ve her bölümün toplam çalışma kabaca eşdeğerolduğunda daha hızlıdır. Bu nedenle, yığın bölümleme genellikle çoğu durumda daha hızlıdır. Az sayıda öğe veya temsilci için daha uzun yürütme süreleri olan kaynaklarda, yığın ve aralık bölümleme performansı yaklaşık eşittir.

TPL bölümleyiciler de bölümdinamik bir sayı yı destekler. Bu, örneğin <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yeni bir görev doğurduğunda, anında bölümler oluşturabilecekleri anlamına gelir. Bu özellik, bölümleyicinin döngünün kendisiyle birlikte ölçeklendirmesini sağlar. Dinamik bölümleyiciler de doğal olarak yük dengeleme vardır. Özel bir bölümleyici oluşturduğunuzda, bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüden tüketilebilir olması için dinamik bölümlemayı desteklemeniz gerekir.

### <a name="configuring-load-balancing-partitioners-for-plinq"></a>PLINQ için Yük Dengeleme Bölümleyicileri Yapılandırma

<xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> Yöntemin bazı aşırı yükleri, bir dizi veya <xref:System.Collections.IList> kaynak için bir bölümleyici oluşturmanıza ve iş parçacıkları arasındaki iş yükünü dengelemeye çalışıp çalışmayacağını belirtmenize izin verebilirsiniz. Bölümleyici yük dengesi için yapılandırıldığında, yığın bölümleme kullanılır ve öğeler istendiği gibi küçük parçalar halinde her bölüme teslim edilir. Bu yaklaşım, tüm döngü veya sorgu tamamlanana kadar tüm bölümlerin işletilen öğelere sahip olmasını sağlamaya yardımcı olur. Herhangi bir <xref:System.Collections.IEnumerable> kaynağın yük dengeleme bölümleme sağlamak için ek bir aşırı yük kullanılabilir.

Genel olarak, yük dengeleme bölümleyici nispeten sık öğeleri istemek için bölümleri gerektirir. Buna karşılık, statik bölümleme yapan bir bölümleyici, aralık veya yığın bölümleme kullanarak öğeleri her bölümleyiciye aynı anda atayabilir. Bu, yük dengelemedaha az genel yük gerektirir, ancak bir iş parçacığı diğerlerinden önemli ölçüde daha fazla iş ile biterse yürütülmesi daha uzun sürebilir. Varsayılan olarak bir IList veya dizi geçirildiğinde, PLINQ her zaman yük dengeleme olmadan aralık bölümleme kullanır. PLINQ için yük dengelemesini etkinleştirmek için aşağıdaki örnekte gösterildiği gibi `Partitioner.Create` yöntemi kullanın.

[!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
[!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]

Herhangi bir senaryoda yük dengelemesinin kullanılıp kullanılmayacağını belirlemenin en iyi yolu, temsili yükler ve bilgisayar yapılandırmaları altında işlemlerin tamamlanmasının ne kadar sürdüğünü denemek ve ölçmektir. Örneğin, statik bölümleme yalnızca birkaç çekirdekli çok çekirdekli bir bilgisayarda önemli bir hız sağlayabilir, ancak nispeten çok sayıda çekirdek olan bilgisayarlarda yavaşlamalara neden olabilir.

Aşağıdaki tabloda yöntemin kullanılabilir <xref:System.Collections.Concurrent.Partitioner.Create%2A> aşırı yükleri listelenir. Bu bölümleyiciler sadece PLINQ veya <xref:System.Threading.Tasks.Task>kullanmak için sınırlı değildir. Onlar da herhangi bir özel paralel yapı ile kullanılabilir.

|Aşırı|Yük dengeleme kullanır|
|--------------|-------------------------|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Her zaman|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Boolean bağımsız değişkeni doğru olarak belirtildiğinde|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Boolean bağımsız değişkeni doğru olarak belirtildiğinde|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Hiçbir zaman|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Hiçbir zaman|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Hiçbir zaman|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Hiçbir zaman|

### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Parallel.ForEach için Statik Aralık Bölümleyicileri Yapılandırma

Bir <xref:System.Threading.Tasks.Parallel.For%2A> döngüde, döngü gövdesi metoduna temsilci olarak sağlanır. Bu temsilci çağırmanın maliyeti, sanal yöntem çağrısıyla hemen hemen aynıdır. Bazı senaryolarda, paralel döngü gövdesi, her döngü yinelemesindeki temsilci çağırma maliyetinin önemli hale gelmesinden yeterince küçük olabilir. Bu gibi durumlarda, kaynak öğeler <xref:System.Collections.Concurrent.Partitioner.Create%2A> üzerinde bir <xref:System.Collections.Generic.IEnumerable%601> dizi bölümleri oluşturmak için aşırı yüklerden birini kullanabilirsiniz. Daha sonra, bu aralıklar koleksiyonunu, <xref:System.Threading.Tasks.Parallel.ForEach%2A> gövdesi normal `for` bir döngüden oluşan bir yönteme geçirebilirsiniz. Bu yaklaşımın yararı, temsilci çağırma maliyetinin öğe başına bir değil, aralık başına yalnızca bir kez tahakkuk ettirilmesidir. Aşağıdaki örnek, temel deseni göstermektedir.

[!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
[!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]

Döngüdeki her iş parçacığı, belirtilen alt aralıktaki başlangıç ve bitiş dizin değerlerini içeren kendi <xref:System.Tuple%602> iş parçacığıalır. `for` İç döngü, `fromInclusive` dizi `toExclusive` veya <xref:System.Collections.IList> doğrudan üzerinde döngü ve değerleri kullanır.

<xref:System.Collections.Concurrent.Partitioner.Create%2A> Aşırı yüklemelerden biri, bölümlerin boyutunu ve bölüm sayısını belirtmenizi sağlar. Bu aşırı yük, öğe başına çalışmanın o kadar düşük olduğu senaryolarda kullanılabilir ki, öğe başına bir sanal yöntem çağrısı bile performans üzerinde gözle görülür bir etkiye sahiptir.

## <a name="custom-partitioners"></a>Özel Bölümleyiciler

Bazı senaryolarda, değerli olabilir veya hatta kendi bölümleyici uygulamak için gerekli olabilir. Örneğin, sınıfın iç yapısı hakkındaki bilginize bağlı olarak varsayılan bölümleyicilerden daha verimli bir şekilde bölümlere ayrılayabildiğiniz özel bir koleksiyon sınıfınuz olabilir. Veya, kaynak koleksiyonundaki farklı konumlardaki öğeleri işlemenin ne kadar süreceğü hakkında bilginize bağlı olarak farklı boyutlarda aralık bölümleri oluşturmak isteyebilirsiniz.

Temel bir özel bölümleyici oluşturmak için, <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> aşağıdaki tabloda açıklandığı gibi bir sınıf türetin ve sanal yöntemleri geçersiz kılın.

|||
|-|-|
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Bu yöntem ana iş parçacığı tarafından bir kez çağrılır ve bir IList(IEnumerator(TSource)) döndürür. Döngü veya sorgudaki her alt `GetEnumerator` iş parçacığı, <xref:System.Collections.Generic.IEnumerator%601> farklı bir bölüm üzerinde almak için listede çağırabilir.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Uygularsanız `true` <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>geri dönün, `false`aksi takdirde.|
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Ise, <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> bu yöntem isteğe bağlı olarak yerine <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> `true`|

Sonuçlar sıralanabilir olması gerekiyorsa veya öğelere dizinli erişim gerektiriyorsanız, aşağıdaki tabloda açıklandığı gibi sanal yöntemlerinden <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> türetin ve geçersiz kılın.

|||
|-|-|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Bu yöntem ana iş parçacığı tarafından `IList(IEnumerator(TSource))`bir kez çağrılır ve bir . Döngü veya sorgudaki her alt `GetEnumerator` iş parçacığı, <xref:System.Collections.Generic.IEnumerator%601> farklı bir bölüm üzerinde almak için listede çağırabilir.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Uygularsanız `true` <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>geri dönün; aksi takdirde, yanlış.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Tipik olarak, bu <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>sadece çağırır .|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Ise, <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> bu yöntem isteğe bağlı olarak yerine <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> `true`|

Aşağıdaki tablo, üç tür yük dengeleme bölümleyicilerinin <xref:System.Collections.Concurrent.OrderablePartitioner%601> sınıfı nasıl uyguladığı hakkında ek ayrıntılar sağlar.

|Yöntem / Özellik|Yük Dengelemeolmadan IList / Dizi|Yük Dengelemeli IList / Dizi|ıenumerable|
|----------------------|-------------------------------------------|----------------------------------------|-----------------|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Aralık bölümleme kullanır|Belirtilen bölümSayısı için Listeler için en iyi duruma getirilmiş yığın bölümleme kullanır|Statik bölüm sayısı oluşturarak yığın bölümleme kullanır.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Desteklenmeyen özel durum atar|Listeler ve dinamik bölümler için en iyi duruma getirilmiş yığın bölümleme kullanır|Dinamik bir bölüm sayısı oluşturarak yığın bölümleme kullanır.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Döndürür`true`|Döndürür`true`|Döndürür`true`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Döndürür`true`|Döndürür`false`|Döndürür`false`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Döndürür`true`|Döndürür`true`|Döndürür`true`|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Döndürür`false`|Döndürür`true`|Döndürür`true`|

### <a name="dynamic-partitions"></a>Dinamik Bölümler

Bölümleyicinin bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemde kullanılmasını istiyorsanız, dinamik sayıda bölüm döndürebilmelisin. Bu, bölümleyici döngü yürütme sırasında herhangi bir zamanda isteğe bağlı yeni bir bölüm için bir sayısallaştırıcı kaynağı anlamına gelir. Temel olarak, döngü yeni bir paralel görev eklendiğinde, bu görev için yeni bir bölüm ister. Verilerin düzenlenebilir olmasını istiyorsanız, her bölümdeki <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> her öğeye benzersiz bir dizin atanması için türetin.

Daha fazla bilgi ve bir örnek için [bkz.](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)

### <a name="contract-for-partitioners"></a>Bölümleyiciler için Sözleşme

Özel bir bölümleyici uyguladığınızda, PLINQ ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> TPL ile doğru etkileşimi sağlamaya yardımcı olmak için aşağıdaki yönergeleri izleyin:

- Sıfır <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> veya daha az bir argüman `partitionsCount`ile <xref:System.ArgumentOutOfRangeException>çağrılırsa , atmak . PLINQ ve TPL 0'a `partitionCount` eşit olarak asla geçmeyecek olsa da, yine de bu olasına karşı korumanızı öneririz.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>ve <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> her `partitionsCount` zaman bölüm sayısını döndürmelidir. Bölümleyici veri biterse ve istenildikçe çok sayıda bölüm oluşturamıyorsa, yöntem kalan bölümlerin her biri için boş bir sayısalatör döndürmelidir. Aksi takdirde, hem PLINQ ve <xref:System.InvalidOperationException>TPL bir atar.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> , ve `null` `Nothing` asla geri dönmemelidir (Visual Basic'te). Bunu yaparsanız, PLINQ / TPL bir <xref:System.InvalidOperationException>atacaktır .

- Bölümleri döndüren yöntemler, veri kaynağını tam ve benzersiz olarak sayısalabilen bölümleri her zaman döndürmelidir. Bölümleyicinin tasarımı tarafından özel olarak gerekmedikçe, veri kaynağında veya atlanan öğelerde yineleme olmamalıdır. Bu kurala uyulmazsa, çıktı sırası karıştırılabilir.

- Aşağıdaki Boolean getters her zaman doğru çıktı sırası şifreli değil, böylece aşağıdaki değerleri döndürmelidir:

  - `KeysOrderedInEachPartition`: Her bölüm, artan anahtar dizinleri olan öğeleri döndürür.

  - `KeysOrderedAcrossPartitions`: Döndürülen tüm bölümler için, bölüm *i'deki* anahtar endeksleri bölüm *i*-1'deki anahtar endekslerinden daha yüksektir.

  - `KeysNormalized`: Tüm temel endeksler sıfırdan başlayarak boşluklar olmadan monoton olarak artmaktadır.

- Tüm endeksler benzersiz olmalıdır. Yinelenen endeksler olmayabilir. Bu kurala uyulmazsa, çıktı sırası karıştırılabilir.

- Tüm endeksler negatif olmamalıdır. Bu kurala uyulmazsa, PLINQ/TPL özel durumlar atabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Nasıl yapılır: Dinamik Bölümleri Uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)
- [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
