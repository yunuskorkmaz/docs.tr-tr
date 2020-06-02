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
ms.openlocfilehash: 50553aab30d5a1bc5880ae0fe39c34508e57d0e5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276731"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>PLINQ ve TPL için Özel Bölümleyiciler

Bir veri kaynağındaki bir işlemi paralel hale getirmek için, temel adımlardan biri kaynağı birden çok iş parçacığı tarafından aynı anda erişilebilen birden çok bölüme *bölümlemesidir* . PLıNQ ve görev paralel kitaplığı (TPL), paralel bir sorgu veya döngü yazdığınızda saydam olarak çalışan varsayılan Bölümleyiciler sağlar <xref:System.Threading.Tasks.Parallel.ForEach%2A> . Daha gelişmiş senaryolar için kendi bölümleyici 'nizi takabilirsiniz.

## <a name="kinds-of-partitioning"></a>Bölümleme türleri

Bir veri kaynağını bölümleyerek birçok yol vardır. En verimli yaklaşımlar içinde, birden çok iş parçacığı kaynağı fiziksel olarak birden çok subsequences ayırmak yerine, özgün kaynak sırasını işlemek üzere çalışır. Uzunluğun önceden olduğu Koleksiyonlar gibi diziler ve diğer dizinli kaynaklar için <xref:System.Collections.IList> , *Aralık bölümleme* en basit bölümleme türüdür. Her iş parçacığı benzersiz başlangıç ve bitiş dizinlerini alır, böylece, başka bir iş parçacığı tarafından üzerine yazmadan veya üzerine yazılmadan kaynak aralığını işleyebilir. Aralık bölümlemeye dahil olan tek ek, aralıkları oluşturmaya yönelik ilk çalışmadır; Bundan sonra ek eşitleme gerekmez. Bu nedenle, iş yükü eşit olarak bölündüğü sürece iyi bir performans sağlayabilir. Aralık bölümlemenin bir dezavantajı, bir iş parçacığının erken sonlandırmasıdır, diğer iş parçacıklarının işlerini bitirmesini yardımcı olamaz.

Uzunluğu bilinmeyen bağlantılı listeler veya diğer koleksiyonlar için *öbek bölümleme*kullanabilirsiniz. Öbek bölümlendirme içinde, bir paralel döngü veya sorgudaki her iş parçacığı veya görev, bir öbekte birkaç kaynak öğesi tüketir, bunları işler ve sonra ek öğeleri almaya geri gelir. Bölümleyici tüm öğelerin dağıtılmasını ve yinelenen değer olmamasını sağlar. Bir öbek herhangi bir boyutta olabilir. Örneğin, [nasıl yapılır: dinamik bölümleri uygulama](how-to-implement-dynamic-partitions.md) bölümünde gösterilen bölümleyici yalnızca bir öğe içeren öbekleri oluşturur. Parçalar çok büyük olmadığı sürece, iş parçacıklarındaki öğelerin atanması önceden belirlenmediğinden, bu tür bir bölümleme, kendiliğinden yük dengedir. Ancak, bölümleyici, iş parçacığının başka bir öbeği alması gerektiğinde eşitleme ek yüküne neden olur. Bu durumlarda oluşan eşitleme miktarı, öbeklerin boyutuyla daha seyrek orantılı şekilde yapılır.

Genel olarak, Aralık bölümleme yalnızca temsilcinin yürütme süresi küçük ve orta arası olduğunda ve kaynakta çok sayıda öğe varsa ve her bölümün toplam çalışması kabaca eşdeğerdir. Çoğu durumda öbek bölümleme genellikle daha hızlıdır. Temsilci için az sayıda öğe veya daha uzun yürütme süresi olan kaynaklarda, öbek ve Aralık bölümlemenin performansı eşittir.

TPL Bölümleyiciler dinamik sayıda bölümü de destekler. Bu, örneğin, <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yeni bir görev oluştururken bir arada bölüm oluşturbilecekleri anlamına gelir. Bu özellik, bölümleyici 'nin döngüyle birlikte ölçeklenebilmesini sağlar. Dinamik Bölümleyiciler Ayrıca, doğal olarak yük dengedir. Özel bir bölümleyici oluşturduğunuzda, bir döngüden tüketilebilir olması için dinamik bölümlendirme desteği gerekir <xref:System.Threading.Tasks.Parallel.ForEach%2A> .

### <a name="configuring-load-balancing-partitioners-for-plinq"></a>PLıNQ için Yük Dengeleme Bölümleyicilerinin yapılandırılması

Metodun bazı aşırı yüklemeleri, bir <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> dizi veya kaynak için bir bölümleyici oluşturmanıza <xref:System.Collections.IList> ve iş yükünü iş parçacıkları arasında dengelemeye çalışıp çalışmadığını belirtmenize olanak tanır. Bölümleyici, yük dengeleme için yapılandırıldığında, öbek bölümleme kullanılır ve öğeler istenen küçük öbeklerdeki her bölüme dağıtılır. Bu yaklaşım tüm tüm bölümlerin, tüm döngü veya sorgu tamamlanana kadar işlemek için öğelere sahip olduğundan emin olmanıza yardımcı olur. Herhangi bir kaynağın Yük Dengeleme bölümlemesini sağlamak için ek bir aşırı yükleme kullanılabilir <xref:System.Collections.IEnumerable> .

Genel olarak, Yük Dengeleme, bölümlerin bölümleyici 'den görece sıklıkta istek istemesine gerek duyar. Buna karşılık, statik bölümlendirme yapan bir bölümleyici her bir bölümleyici öğesine, her türlü veya öbek bölümlendirme kullanarak öğeleri atayabilir. Bu, yük dengelemeden daha az yük gerektirir, ancak bir iş parçacığının diğer diğerlerinden çok daha fazla iş ile sona ermemesi durumunda yürütülmesi daha uzun sürebilir. Varsayılan olarak, bir IList veya Array geçirildiğinde, PLıNQ her zaman yük dengeleme olmadan Aralık bölümlendirme kullanır. PLıNQ için yük dengelemeyi etkinleştirmek üzere, `Partitioner.Create` Aşağıdaki örnekte gösterildiği gibi yöntemini kullanın.

[!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
[!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]

Belirli bir senaryoda yük dengelemenin kullanılıp kullanılmayacağını belirlemenin en iyi yolu, temsilci yükleme ve bilgisayar yapılandırması altında işlemin ne kadar sürdüğünü tamamlamaya ve ölçmeye yönelik bir deneymidir. Örneğin, statik bölümlendirme yalnızca birkaç çekirdeğe sahip olan çok çekirdekli bir bilgisayarda önemli bir hızlı yol sunabilir, ancak nispeten fazla çekirdeğe sahip bilgisayarlarda yavaşlamalara neden olabilir.

Aşağıdaki tabloda, yönteminin kullanılabilir aşırı yüklemeleri listelenmektedir <xref:System.Collections.Concurrent.Partitioner.Create%2A> . Bu bölümleyicilerin yalnızca PLıNQ veya ile kullanılması sınırlı değildir <xref:System.Threading.Tasks.Task> . Ayrıca, özel bir paralel yapı ile de kullanılabilirler.

|Yüklemek|Yük dengelemeyi kullanır|
|--------------|-------------------------|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Her zaman|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Boole bağımsız değişkeni true olarak belirtildiğinde|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Boole bağımsız değişkeni true olarak belirtildiğinde|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Asla|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Asla|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Asla|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Asla|

### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Statik Aralık Bölümleyiciler paralel. ForEach için Yapılandırılıyor

Bir <xref:System.Threading.Tasks.Parallel.For%2A> döngüde, döngünün gövdesi yönteme bir temsilci olarak sağlanır. Bu temsilciyi çağırma maliyeti, sanal yöntem çağrısıyla aynı şekilde yapılır. Bazı senaryolarda, paralel bir döngünün gövdesi, her döngü yinelemesinde temsilci çağrısı maliyetinin önemli hale geldiği kadar küçük olabilir. Bu gibi durumlarda, <xref:System.Collections.Concurrent.Partitioner.Create%2A> <xref:System.Collections.Generic.IEnumerable%601> kaynak öğeler üzerinde Aralık bölümleri oluşturmak için aşırı yüklerden birini kullanabilirsiniz. Daha sonra, bu aralıklar koleksiyonunu <xref:System.Threading.Tasks.Parallel.ForEach%2A> gövde düzenli bir döngüden oluşan bir yönteme geçirebilirsiniz `for` . Bu yaklaşımın avantajı, temsilci çağırma maliyetinin her öğe için bir kez değil, her aralığa yalnızca bir kez tahakkuk etcidir. Aşağıdaki örnekte temel desenler gösterilmektedir.

[!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
[!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]

Döngüdeki her iş parçacığı, <xref:System.Tuple%602> belirtilen alt aralıktaki başlangıç ve bitiş dizini değerlerini içeren kendisini alır. İç `for` döngü, `fromInclusive` `toExclusive` dizi üzerinde veya doğrudan döngü yapmak için ve değerlerini kullanır <xref:System.Collections.IList> .

Aşırı yüklerden biri <xref:System.Collections.Concurrent.Partitioner.Create%2A> bölümlerin boyutunu ve bölüm sayısını belirtmenize olanak tanır. Bu aşırı yükleme, her öğe için, her öğe için bir sanal yöntem çağrısı performansa göre belirgin bir etkiye sahip olduğu durumlarda kullanılabilir.

## <a name="custom-partitioners"></a>Özel Bölümleyiciler

Bazı senaryolarda, kendi bölümleyici 'nizi uygulamak için de gerekli olabilir. Örneğin, sınıfın iç yapısına bağlı olarak, varsayılan Bölümleyiciler tarafından daha verimli bir şekilde bölümleyebilir bir özel koleksiyon sınıfınız olabilir. Ya da, kaynak koleksiyondaki farklı konumlarda bulunan öğeleri işlemek için ne kadar süreceğine bağlı olarak değişen boyutlarda Aralık bölümleri oluşturmak isteyebilirsiniz.

Temel bir özel bölümleyici oluşturmak için, aşağıdaki tabloda açıklandığı gibi, ' dan bir sınıf türetebilir <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> ve sanal yöntemleri geçersiz kılın.

|||
|-|-|
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Bu yöntem, ana iş parçacığı tarafından bir kez çağrılır ve bir IList (IEnumerator (TSource)) döndürür. Döngü veya sorgudaki her çalışan iş parçacığı, farklı bir `GetEnumerator` bölüm üzerinden almak için listeyi çağırabilir <xref:System.Collections.Generic.IEnumerator%601> .|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|`true`Öğesini uygularsanız, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A> Aksi takdirde, döndürün `false` .|
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>İse `true` , bu yöntem yerine isteğe bağlı olarak çağrılabilir <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> .|

Sonuçlar sıralanabilir olmalıdır veya öğelere dizinli erişim istiyorsanız, <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> Aşağıdaki tabloda açıklandığı gibi, sanal yöntemlerini türeten ve geçersiz kılabilirsiniz.

|||
|-|-|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Bu yöntem, ana iş parçacığı tarafından bir kez çağrılır ve döndürür `IList(IEnumerator(TSource))` . Döngü veya sorgudaki her çalışan iş parçacığı, farklı bir `GetEnumerator` bölüm üzerinden almak için listeyi çağırabilir <xref:System.Collections.Generic.IEnumerator%601> .|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|`true`Öğesini uyguladığınızda döndürün <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A> ; Aksi takdirde, false.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Genellikle bu yalnızca çağırır <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> .|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>İse `true` , bu yöntem yerine isteğe bağlı olarak çağrılabilir <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> .|

Aşağıdaki tabloda, üç tür yük dengeleme Bölümleyiciler sınıfının nasıl uygulandığı hakkında ek ayrıntılar verilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601> .

|Metot/Özellik|Yük Dengeleme olmadan IList/Array|Yük Dengeleme ile IList/Array|IEnumerable|
|----------------------|-------------------------------------------|----------------------------------------|-----------------|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Aralık bölümleme kullanır|Belirtilen partitionCount listeleri için en iyi duruma getirilmiş öbek bölümleme kullanır|Statik sayıda bölüm oluşturarak öbek bölümleme kullanır.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Desteklenmeyen özel durum oluşturur|Listeler ve dinamik bölümler için en iyi duruma getirilmiş öbek bölümleme kullanır|Dinamik sayıda bölüm oluşturarak öbek bölümleme kullanır.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Döndürdüğü`true`|Döndürdüğü`true`|Döndürdüğü`true`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Döndürdüğü`true`|Döndürdüğü`false`|Döndürdüğü`false`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Döndürdüğü`true`|Döndürdüğü`true`|Döndürdüğü`true`|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Döndürdüğü`false`|Döndürdüğü`true`|Döndürdüğü`true`|

### <a name="dynamic-partitions"></a>Dinamik bölümler

Bir yöntemde kullanılacak olan bölümleyici <xref:System.Threading.Tasks.Parallel.ForEach%2A> 'yi düşünüyorsanız, dinamik sayıda bölüm döndürebilmelisiniz. Bu, bölümleyici 'nin döngü yürütme sırasında dilediğiniz zaman isteğe bağlı yeni bir bölüm için bir Numaralandırıcı sağlayabileceği anlamına gelir. Temel olarak, döngü yeni bir paralel görev eklediğinde, bu görev için yeni bir bölüm ister. Verilerin sıralı olmasını istiyorsanız, <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> her bölümdeki her bir öğeye benzersiz bir dizin atanması için öğesinden türetebilirsiniz.

Daha fazla bilgi ve bir örnek için bkz. [nasıl yapılır: dinamik bölümleri uygulama](how-to-implement-dynamic-partitions.md).

### <a name="contract-for-partitioners"></a>Bölümleyiciler için sözleşme

Özel bir bölümleyici uyguladığınızda, PLıNQ ile ve TPL 'de doğru etkileşimi sağlamaya yardımcı olmak için aşağıdaki yönergeleri izleyin <xref:System.Threading.Tasks.Parallel.ForEach%2A> :

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, İçin sıfır veya daha küçük bir bağımsız değişkenle çağrılırsa `partitionsCount` throw <xref:System.ArgumentOutOfRangeException> . PLıNQ ve TPL hiçbir şekilde 0 ' a eşit geçmeyecektir `partitionCount` , ancak olasılığa karşı koruma yapmanızı öneririz.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>ve <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> her zaman `partitionsCount` bölüm sayısını döndürmelidir. Bölümleyici veri tükendiyse ve istenen sayıda bölüm oluşturamaz, bu durumda yöntem kalan bölümlerin her biri için boş bir Numaralandırıcı döndürmelidir. Aksi halde, PLıNQ ve TPL her ikisi de oluşturur <xref:System.InvalidOperationException> .

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>,,, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A> ve <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> asla döndürmemelidir `null` ( `Nothing` Visual Basic). Yapalarsa PLıNQ/TPL bir oluşturur <xref:System.InvalidOperationException> .

- Bölüm döndüren yöntemler her zaman veri kaynağını tam ve benzersiz bir şekilde numaralandırmayan bölümler döndürmelidir. Bölümleyici tasarımının özel olarak gerekmediği müddetçe veri kaynağında yineleme olmaması veya atlanan öğeler olması gerekir. Bu kurala uyulmazsa çıkış sırası karıştırılmış olabilir.

- Aşağıdaki Boole alıcıları, çıkış sırası karıştırılamamasını sağlayacak şekilde aşağıdaki değerleri her zaman doğru döndürmelidir:

  - `KeysOrderedInEachPartition`: Her bölüm, artan anahtar dizinlerini içeren öğeleri döndürür.

  - `KeysOrderedAcrossPartitions`: Döndürülen tüm bölümler için *, Bölüm ı* *-1*' deki anahtar dizinlerinden daha yüksek.

  - `KeysNormalized`: Tüm anahtar dizinleri, sıfırdan başlayarak boşluklar olmadan tek bir şekilde artıyor.

- Tüm dizinler benzersiz olmalıdır. Yinelenen dizinler bulunmayabilir. Bu kurala uyulmazsa çıkış sırası karıştırılmış olabilir.

- Tüm dizinler negatif olmalıdır. Bu kurala uyulmazsa PLıNQ/TPL özel durumlar oluşturabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel programlama](index.md)
- [Nasıl yapılır: Dinamik Bölümleri Uygulama](how-to-implement-dynamic-partitions.md)
- [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](how-to-implement-a-partitioner-for-static-partitioning.md)
