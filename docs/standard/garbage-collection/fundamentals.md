---
title: Çöp toplamanın temelleri
description: Çöp toplayıcısının nasıl çalıştığını ve en iyi performans için nasıl yapılandırılabileceğini öğrenin.
ms.date: 03/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c1b73108227160aaff28525beeca7f3bd4cb5f8
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775320"
---
# <a name="fundamentals-of-garbage-collection"></a>Çöp toplamanın temelleri

<a name="top"></a>Ortak dil çalışma zamanında (CLR), çöp toplayıcı otomatik bellek yöneticisi olarak görev yapar. Aşağıdaki avantajları sağlar:

- Oluşturduğunuz nesneler için el ile bellek boşaltmaya gerek kalmadan uygulamanızı geliştirmenize olanak sağlar.

- Yönetilen yığında nesneleri verimli bir şekilde ayırır.

- Artık kullanılmayan nesneleri geri kazanır, hafızasını temizler ve belleğin gelecekteki ayırmalarda kullanılabilmesini önler. Yönetilen nesneler, ile başlamak için otomatik olarak temiz içerik alır, bu nedenle oluşturucuların her veri alanını başlatması gerekmez.

- Bir nesnenin başka bir nesnenin içeriğini kullanabilmesi için bellek güvenliği sağlar.

 Bu konuda çöp toplamanın temel kavramları açıklanmaktadır.

<a name="fundamentals_of_memory"></a>

## <a name="fundamentals-of-memory"></a>Belleğin temelleri

Aşağıdaki listede, önemli CLR belleği kavramları özetlenmektedir.

- Her işlemin kendi kendine ayrı bir sanal adres alanı vardır. Aynı bilgisayardaki tüm işlemlerin aynı fiziksel belleği paylaştığı ve varsa sayfa dosyasını paylaştığı bir işlem.

- Varsayılan olarak, 32 bit bilgisayarlarda, her işlemin 2 GB 'lık bir Kullanıcı modu sanal adres alanı vardır.

- Bir uygulama geliştiricisi olarak yalnızca sanal adres alanı ile çalışır ve fiziksel belleği doğrudan hiçbir şekilde işlemeyin. Çöp toplayıcı, yönetilen yığında sizin için sanal belleği ayırır ve serbest bırakır.

  Yerel kod yazıyorsanız, sanal adres alanı ile çalışmak için Win32 işlevlerini kullanırsınız. Bu işlevler, yerel yığınlardaki sanal belleği ayırır ve boşaltır.

- Sanal bellek üç durumda olabilir:

  - Süz. Bellek bloğunun kendisine başvuru yoktur ve ayırma için kullanılabilir.

  - Ayrılamadı. Bellek bloğu kullanım için kullanılabilir ve diğer herhangi bir ayırma isteği için kullanılamaz. Ancak, bu bellek bloğunda verileri kaydedilene kadar depoleyemez.

  - Yazıldı. Bellek bloğu fiziksel depolamaya atanır.

- Sanal adres alanı parçalanabilir. Bu, adres alanında delik olarak da bilinen boş blokların olduğu anlamına gelir. Sanal bellek ayırma istendiğinde, sanal bellek yöneticisinin, bu ayırma isteğini karşılamak için yeterince büyük olan tek bir ücretsiz blok bulması gerekir. 2 GB boş alan olsa bile, tüm bu boş alan tek bir adres bloğunda yer almadığı takdirde 2 GB gerektiren ayırma başarısız olur.

- Ayrılacak sanal adres alanı tükenmeniz veya fiziksel alanın kaydedilmesi için bellek tükeniyor.

Fiziksel bellek baskısı (yani fiziksel bellek talebi) düşük olsa bile sayfa dosyanız kullanılır. Fiziksel bellek basıncını ilk kez yüksek olduğunda, işletim sisteminin verileri depolamak için fiziksel bellekte yer yapması gerekir ve fiziksel bellekteki bazı verileri sayfa dosyasına yedekler. Bu veriler, gerekli olana kadar sayfalanmadığı için fiziksel bellek basıncının çok düşük olduğu durumlarda sayfalama ile karşılaşmak mümkündür.

[Başa dön](#top)

<a name="conditions_for_a_garbage_collection"></a>

## <a name="conditions-for-a-garbage-collection"></a>Çöp toplama koşulları

Çöp toplama, aşağıdaki koşullardan biri doğru olduğunda gerçekleşir:

- Sistemde fiziksel bellek yetersiz. Bu, ana bilgisayar tarafından belirtilen işletim sistemi ya da düşük bellekten düşük bellek bildirimi tarafından algılanır.

- Yönetilen yığında ayrılmış nesneler tarafından kullanılan bellek, kabul edilebilir bir eşik geçirir. İşlem çalışırken bu eşik sürekli olarak ayarlanır.

- @No__t_0 yöntemi çağrılır. Neredeyse tüm durumlarda, çöp toplayıcı sürekli çalıştığından bu yöntemi çağırmanız gerekmez. Bu yöntem öncelikle benzersiz durumlar ve test için kullanılır.

[Başa dön](#top)

<a name="the_managed_heap"></a>

## <a name="the-managed-heap"></a>Yönetilen yığın

Çöp toplayıcı CLR tarafından başlatıldıktan sonra, nesneleri depolamak ve yönetmek için bir bellek segmenti ayırır. Bu bellek, işletim sistemindeki yerel bir yığının aksine yönetilen yığın olarak adlandırılır.

Yönetilen her işlem için yönetilen bir yığın vardır. İşlemdeki tüm iş parçacıkları aynı yığında nesneler için bellek ayırır.

Bellek ayırmak için, çöp toplayıcı Win32 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) işlevini çağırır ve yönetilen uygulamalar için bir seferde bir bellek segmentini ayırır. Çöp toplayıcı aynı zamanda kesimleri gereken şekilde ayırır ve Win32 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) işlevini çağırarak kesimleri işletim sistemine (herhangi bir nesne temizlenmeden sonra) yeniden yayınlar.

> [!IMPORTANT]
> Çöp toplayıcı tarafından ayrılan parçaların boyutu uygulamaya özgüdür ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değiştirilebilir. Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.

Yığın üzerinde daha az nesne ayrılmışsa, çöp toplayıcının yapması gereken daha az iş vardır. Nesneleri ayırdığınızda, yalnızca 15 bayta ihtiyacınız olduğunda 32 baytlık bir dizi tahsis etme gibi gereksinimlerinizi aşan yuvarlanmış değerler kullanmayın.

Çöp toplama tetiklendiğinde çöp toplayıcı, ölü nesneler tarafından kullanılan belleği geri kazanır. Geri kazanma işlemi, canlı nesneleri bir araya gelecek şekilde sıkıştırır ve atılacak alan kaldırıldıktan sonra yığın daha küçük hale getirir. Bu, birlikte ayrılan nesnelerin, konumlarını korumak için yönetilen yığında birlikte kalmasını sağlar.

Çöp koleksiyonlarının sürekliliği (sıklığı ve süresi), ayırma hacminin ve yönetilen yığında kalan bellek miktarının sonucudur.

Yığın iki sayfa@@ 'nin birikmesi olarak düşünülebilir: [büyük nesne yığını](large-object-heap.md) ve küçük nesne yığını.

[Büyük nesne yığını](large-object-heap.md) 85.000 bayt ve daha büyük olan çok büyük nesneler içerir. Büyük nesne yığınındaki nesneler genellikle dizilerdir. Örnek nesnesinin son derece büyük olması nadir bir durumdur.

[Başa dön](#top)

<a name="generations"></a>

## <a name="generations"></a>İse

Yığın, uzun süreli ve kısa süreli nesneleri işleyebilmesi için nesiller halinde düzenlenir. Çöp toplama öncelikli olarak genellikle yığının yalnızca küçük bir kısmını kaplayan kısa süreli nesneler geri kazanma ile gerçekleşir. Yığında üç Neste nesne vardır:

- **Nesil 0**. Bu, kardeşinizin nesli ve kısa süreli nesneler içerir. Kısa süreli bir nesne örneği, geçici bir değişkendir. Çöp toplama bu nesde en sık oluşur.

  Yeni ayrılmış nesneler yeni nesil nesneler oluşturur ve büyük nesneler olmadıkları müddetçe örtük olarak nesil 0 koleksiyonlardır ve bu durumda 2. nesil bir koleksiyonda büyük nesne yığınında gider.

  Çoğu nesne, oluşturma 0 ' da çöp toplama için geri kazanılır ve bir sonraki nesle devam etmez.

- **1. nesil**. Bu nesil, kısa süreli nesneler içerir ve kısa süreli nesneler ve uzun süreli nesneler arasında bir arabellek işlevi görür.

- **2. nesil**. Bu nesil uzun süreli nesneler içerir. Uzun süreli bir nesne örneği, işlem süresince canlı olan statik verileri içeren bir sunucu uygulamasındaki nesnedir.

Atık koleksiyonlar belirli nesiller üzerinde koşullar garanti olarak oluşur. Oluşturma toplanması, bu kuşak ve tüm küçük nesiller içindeki nesnelerin toplanması anlamına gelir. 2\. nesil atık toplama, tüm nesiller içindeki tüm nesneleri geri kazanır (yani, yönetilen yığındaki tüm nesneler) olduğu için tam çöp toplama olarak da bilinir.

### <a name="survival-and-promotions"></a>Acil ihtiyaç ve promosyonlar

Atık toplamada geri kazanımayan nesneler, acil sanal öğeler olarak bilinir ve bir sonraki nesil olarak yükseltilir. Nesil 0 atık toplamayı sürdüren nesneler 1. nesil olarak yükseltilir; 1. nesil atık toplamayı sürdüren nesneler 2. nesil olarak yükseltilir; ve 2. nesil bir atık toplamayı sürdüren nesneler 2. kuşak olarak kalır.

Çöp toplayıcı, bir kuşakma hızının yüksek olduğunu algıladığında, bu kuşak için ayırmaların eşiğini artırır, bu nedenle sonraki koleksiyon, geri kazanılan bellek miktarını önemli ölçüde alır. CLR sürekli olarak iki öncelik dengeler: bir uygulamanın çalışma kümesinin çöp toplamayı erteleyerek çok büyük almasını ve çöp toplamanın çok sık çalışmasına izin vermez.

### <a name="ephemeral-generations-and-segments"></a>Kısa ömürlü Nesler ve segmentler

Nesil 0 ve 1 ' deki nesneler kısa süreli olduğundan, bu nesiller, kısa ömürlü nesiller olarak bilinir.

Kısa ömürlü nesiller, kısa ömürlü segment olarak bilinen bellek segmentinde ayrılmalıdır. Çöp toplayıcı tarafından alınan her yeni segment, yeni kısa ömürlü segment olur ve 0. nesil atık toplamayı izleyen nesneleri içerir. Eski kısa ömürlü segment, yeni nesil 2 segmentine dönüşür.

Kısa ömürlü segmentin boyutu sistemin 32 veya 64 bit olmasına ve çalıştırdığı çöp toplayıcı türüne bağlı olarak farklılık gösterir. Varsayılan değerler aşağıdaki tabloda gösterilmiştir.

||32 bit:|64 bit|
|-|-------------|-------------|
|İş istasyonu GC|16 MB|256 MB|
|Sunucu GC|64 MB|4 GB|
|> 4 mantıksal CPU içeren sunucu GC|32 MB|2 GB|
|> 8 mantıksal CPU 'Lar ile sunucu GC|16 MB|1 GB|

Kısa ömürlü segment 2. nesil nesneleri içerebilir. 2\. nesil nesneler birden çok segment kullanabilir (işleminiz için gereken ve belleğin izin verdiği kadar).

Kısa ömürlü atık toplamanın serbest bırakılan bellek miktarı, kısa ömürlü segmentin boyutuyla sınırlıdır. Serbest bırakılan bellek miktarı, ölü nesneler tarafından kullanılan alanla orantılıdır.

[Başa dön](#top)

<a name="what_happens_during_a_garbage_collection"></a>

## <a name="what-happens-during-a-garbage-collection"></a>Çöp toplama sırasında ne olur?

Bir çöp toplama işlemi aşağıdaki aşamaları içerir:

- Tüm canlı nesnelerin listesini bulan ve oluşturan bir işaretleme aşaması.

- Düzenlenecek nesneler için başvuruları güncelleştiren bir değiştirme aşaması.

- Yok sayılma nesnelerinin kapladığı alanı geri kazanır ve kalan nesneleri sıkıştırarak bir düzenleme aşaması. Sıkıştırma aşaması, bir atık toplamayı, segmentin eski ucuna doğru bir şekilde taşımış nesneleri hareket ettirir.

  2\. nesil koleksiyonlar birden çok parçayı kaplayabildiğinden, 2. nesil olarak yükseltilen nesneler eski bir kesime taşınabilir. 2\. nesil ve 2. nesil ve 2. nesil daha fazla VNet, 1. kuşak olarak yükseltildikleri için farklı bir kesime taşınabilir.

  Genellikle büyük nesne yığını düzenlenmez, çünkü büyük nesneleri kopyalamak bir performans cezası uygular. Ancak, .NET Framework 4.5.1 ile başlayarak, büyük nesne yığınını isteğe bağlı olarak sıkıştırmak için <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliğini kullanabilirsiniz.

Çöp toplayıcı, nesnelerin canlı olup olmadığını anlamak için aşağıdaki bilgileri kullanır:

- **Yığın kökleri**. Tam zamanında (JıT) derleyici ve yığın denetçisi tarafından sunulan yığın değişkenleri. JıT iyileştirmelerinin, yığın değişkenlerinin çöp toplayıcısına bildirildiği kod bölgelerini uzatabilir veya kısaltabileceğini unutmayın.

- **Çöp toplama tutamaçları**. Yönetilen nesneleri işaret eden ve Kullanıcı kodu veya ortak dil çalışma zamanı tarafından ayrılabilen işler.

- **Statik veriler**. Uygulama etki alanlarında diğer nesnelere başvurıbir statik nesneler. Her uygulama etki alanı, kendi statik nesnelerini izler.

Çöp toplama başlamadan önce, çöp toplamayı tetikleyen iş parçacığı hariç tüm yönetilen iş parçacıkları askıya alınır.

Aşağıdaki çizimde, çöp toplamayı tetikleyen ve diğer iş parçacıklarının askıya alınmasına neden olan bir iş parçacığı gösterilmektedir.

![Bir iş parçacığı bir çöp toplama işlemi tetiklerse](../../../docs/standard/garbage-collection/media/gc-triggered.png "Bir iş parçacığı bir çöp toplama işlemi tetiklerse")

[Başa dön](#top)

<a name="manipulating_unmanaged_resources"></a>

## <a name="manipulating-unmanaged-resources"></a>Yönetilmeyen kaynakları düzenleme

Yönetilen nesneleriniz, kendi yerel dosya tutamaçlarını kullanarak yönetilmeyen nesnelere başvuru yaptığından, atık toplayıcı yalnızca yönetilen yığında belleği izlediğinden, yönetilmeyen nesneleri açık bir şekilde serbest yapmanız gerekir.

Yönetilen nesnenizin kullanıcıları, nesne tarafından kullanılan yerel kaynakları yok edebilir. Temizleme işlemini gerçekleştirmek için, yönetilen nesnenizin sonlandırılabilir olmasını sağlayabilirsiniz. Sonlandırma, nesne artık kullanımda olmadığında yürütmeniz gereken Temizleme eylemlerinden oluşur. Yönetilen nesneniz, sonlandırıcı yönteminde belirtilen temizleme eylemlerini gerçekleştirir.

Sonlandırılabilir bir nesnenin etkin olmadığı tespit edildiğinde, temizleme eylemlerinin yürütülmesi için Sonlandırıcı bir sıraya konur, ancak nesnenin kendisi bir sonraki oluşturmaya yükseltilir. Bu nedenle, nesnenin geri kazanılıp kazanılmadığını öğrenmek için bu kuşada gerçekleşen sonraki atık toplamaya (bir sonraki atık toplama olması gerekmez) kadar beklemeniz gerekir.

[Başa dön](#top)

<a name="workstation_and_server_garbage_collection"></a>

## <a name="workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu atık toplama

Çöp toplayıcı kendi kendini ayarlamadır ve çok çeşitli senaryolarda çalışabilir. Bir yapılandırma dosyası ayarını, iş yükünün özelliklerine göre çöp toplamanın türünü ayarlamak için kullanabilirsiniz. CLR aşağıdaki çöp toplama türlerini sağlar:

- Tüm istemci iş istasyonları ve tek başına bilgisayarlar için olan iş istasyonu atık toplama. Bu, çalışma zamanı yapılandırma şemasında [\<gcServer > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) için varsayılan ayardır.

  İş istasyonu atık toplama işlemi eşzamanlı olabilir veya eşzamanlı olmayan bir şekilde olabilir. Eşzamanlı atık toplama, yönetilen iş parçacıklarının bir çöp toplama sırasında işlemlere devam etmesine olanak sağlar.

  .NET Framework 4 ' ten başlayarak, arka plan atık toplama, eşzamanlı çöp toplama yerini alır.

- Yüksek aktarım hızı ve ölçeklenebilirlik gerektiren sunucu uygulamalarına yönelik olan sunucu çöp toplama. Sunucu atık toplama, eş zamanlı olmayan veya arka plan olabilir.

Aşağıdaki çizimde, bir sunucusunda çöp toplamayı gerçekleştiren adanmış iş parçacıkları gösterilmektedir.

![Sunucu atık toplama Iş parçacıkları](../../../docs/standard/garbage-collection/media/gc-server.png "Sunucu atık toplama Iş parçacıkları")

### <a name="configuring-garbage-collection"></a>Çöp toplamayı yapılandırma

CLR 'nin gerçekleştirmesini istediğiniz çöp toplamanın türünü belirtmek için çalışma zamanı yapılandırma şemasının [\<gcServer > öğesini](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) kullanabilirsiniz. Bu öğenin `enabled` özniteliği `false` (varsayılan) olarak ayarlandığında, CLR iş istasyonu atık toplama işlemini gerçekleştirir. @No__t_0 özniteliğini `true` olarak belirlediğinizde, CLR sunucu çöp toplama işlemini gerçekleştirir.

Eşzamanlı atık toplama, çalışma zamanı yapılandırma şemasının [\<gcConcurrent > öğesiyle](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) belirtildi. Varsayılan ayar `enabled` ' dır. Bu ayar hem eşzamanlı hem de arka plan çöp toplamayı denetler.

Ayrıca, yönetilmeyen barındırma arabirimleriyle sunucu çöp toplamayı belirtebilirsiniz. ASP.NET ve SQL Server, uygulamanız bu ortamların birinde barındırılıyorsa sunucu çöp toplamayı otomatik olarak etkinleştirdiğine unutmayın.

### <a name="comparing-workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplamayı karşılaştırma

İş istasyonu çöp toplama işlemi için iş parçacığı ve performans değerlendirmeleri aşağıda verilmiştir:

- Koleksiyon, çöp toplamayı tetikleyen ve aynı önceliğe kalan Kullanıcı iş parçacığında oluşur. Kullanıcı iş parçacıkları genellikle normal öncelikte çalıştığı için çöp toplayıcı (normal bir öncelikli iş parçacığı üzerinde çalışır), CPU süresi için diğer iş parçacıklarıyla rekabet etmelidir.

  Yerel kod çalıştıran iş parçacıkları askıya alınmaz.

- İş istasyonu çöp toplama, [\<gcServer >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) ayarından bağımsız olarak yalnızca bir işlemciye sahip olan bir bilgisayarda kullanılır. Sunucu çöp toplamayı belirtirseniz, CLR eşzamanlılık devre dışı olan iş istasyonu çöp toplamayı kullanır.

Aşağıda sunucu çöp toplama için iş parçacığı ve performans konuları verilmiştir:

- Koleksiyon `THREAD_PRIORITY_HIGHEST` öncelik düzeyinde çalışan birden fazla adanmış iş parçacığında oluşur.

- Her CPU için bir yığın ve bir ayrılmış iş parçacığı her CPU için sağlanır ve sayfa@@ 'ler aynı anda toplanır. Her yığın küçük bir nesne yığını ve büyük bir nesne yığını içerir ve tüm yığınlara Kullanıcı kodu tarafından erişilebilir. Farklı yığınlardaki nesneler birbirlerine başvurabilir.

- Birden çok çöp toplama iş parçacığı birlikte çalıştığından, sunucu çöp toplama, aynı boyuttaki yığında iş istasyonu atık toplamadan daha hızlıdır.

- Sunucu çöp toplama genellikle daha büyük boyut segmentlerine sahiptir. Bununla birlikte, bunun yalnızca bir Genelleştirme olduğunu unutmayın: segment boyutu uygulamaya özgüdür ve değişikliğe tabidir. Uygulamanızı ayarlamaya yönelik çöp toplayıcı tarafından ayrılan segmentlerin boyutu hakkında bir varsayımın olmaması gerekir.

- Sunucu atık toplama, kaynak kullanımı yoğun olabilir. Örneğin, 4 işlemcili bir bilgisayarda çalışan 12 işlem varsa, sunucu çöp toplama işlemi kullanılıyorsa 48 adanmış çöp toplama iş parçacığı olacaktır. Yüksek bellek yükleme durumunda, tüm süreçler çöp toplama işlemini başlatırsanız, çöp toplayıcının zamanlamaya göre 48 iş parçacığı olacaktır.

Bir uygulamanın yüzlerce örneğini çalıştırıyorsanız, eşzamanlı atık toplama devre dışı bırakılmış iş istasyonu çöp toplamayı kullanmayı düşünün. Bu, performansı iyileştirebilen daha az bağlam geçişe neden olur.

[Başa dön](#top)

<a name="concurrent_garbage_collection"></a>

## <a name="concurrent-garbage-collection"></a>Eşzamanlı atık toplama

İş istasyonu veya sunucu çöp toplama bölümünde, iş parçacıklarının, koleksiyon süresince büyük bir süre için çöp toplamayı gerçekleştiren adanmış bir iş parçacığıyla eşzamanlı olarak çalışmasını sağlayan eşzamanlı atık toplamayı etkinleştirebilirsiniz. Bu seçenek, kuşak 2 ' de yalnızca çöp koleksiyonlarını etkiler; nesil 0 ve 1 her zaman eşzamanlı değildir çünkü çok hızlı tamamlanır.

Eşzamanlı atık toplama, bir koleksiyon için duraklamaları en aza indirerek etkileşimli uygulamaların daha fazla yanıt vermesini sağlar. Yönetilen iş parçacıkları, eşzamanlı atık toplama iş parçacığı çalışırken çoğu zaman çalışmaya devam edebilir. Çöp toplama işlemi gerçekleşirken bu, daha kısa duraklamalar oluşur.

Birkaç işlem çalışırken performansı artırmak için, eşzamanlı atık toplamayı devre dışı bırakın. Bunu, uygulamanın yapılandırma dosyasına bir [\<gcConcurrent > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) ekleyerek ve `enabled` özniteliğinin değerini `"false"` olarak ayarlayarak yapabilirsiniz.

Eş zamanlı çöp toplama, adanmış bir iş parçacığında gerçekleştirilir. Varsayılan olarak, CLR, eşzamanlı atık toplama özellikli iş istasyonu çöp toplamayı çalıştırır. Bu, tek işlemci ve çok işlemcili bilgisayarlar için geçerlidir.

Eşzamanlı atık toplama sırasında yığın üzerinde küçük nesneler ayırma olanağınız, eşzamanlı bir atık toplama başladığında kısa ömürlü kesimde kalan nesnelerle sınırlıdır. Segmentin sonuna ulaştığınızda, küçük nesne ayırmaları yapmak için gereken yönetilen iş parçacıkları askıya alındığında eşzamanlı çöp toplama işleminin bitmesini beklemeniz gerekecektir.

Eşzamanlı atık toplama işlemi, eşzamanlı toplama sırasında nesneleri ayırabilmeniz için biraz daha büyük bir çalışma kümesine (eşzamanlı olmayan Çöp toplamakla karşılaştırıldığında) sahiptir. Ancak, ayırdığı nesneler çalışma kümesinin bir parçası haline geldiği için bu, performansı etkileyebilir. Temelde, eşzamanlı atık toplama, daha kısa duraklamalar için bazı CPU ve bellek ile ilgili bir süre

Aşağıdaki çizimde ayrı bir adanmış iş parçacığında gerçekleştirilen eşzamanlı çöp toplama gösterilmektedir.

![Eşzamanlı atık toplama Iş parçacıkları](../../../docs/standard/garbage-collection/media/gc-concurrent.png "Eşzamanlı atık toplama Iş parçacıkları")

[Başa dön](#top)

<a name="background_garbage_collection"></a>

## <a name="background-workstation-garbage-collection"></a>Arka plan iş istasyonu çöp toplama

Arka plan atık toplama, .NET Framework 4 ile başlayarak eşzamanlı iş istasyonu çöp toplama yerini alır ve .NET Framework 4,5 ile başlayan eşzamanlı sunucu çöp toplama yerini alır.  Arka plan atık toplamada, 2. nesil toplama işlemi devam ederken, kısa ömürlü nesiller (0 ve 1) gerektiği şekilde toplanır. Özel bir iş parçacığında gerçekleştirilir ve yalnızca 2. nesil koleksiyonlar için geçerlidir. Arka plan atık toplama otomatik olarak varsayılan olarak etkindir ve .NET Framework uygulamalarında [\<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma ayarıyla etkinleştirilebilir veya devre dışı bırakılabilir. 

> [!NOTE]
> Arka plan atık toplama yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir. .NET Framework 4 ' te yalnızca iş istasyonu çöp toplama için desteklenir. .NET Framework 4,5 ' den başlayarak, arka plan atık toplama hem iş istasyonu hem de sunucu çöp toplama için kullanılabilir.

Arka plan atık toplama sırasında kısa ömürlü oluşumlara yönelik bir koleksiyon, ön plan atık toplama olarak bilinir. Ön plan atık koleksiyonları gerçekleştiğinde, tüm yönetilen iş parçacıkları askıya alınır.

Arka plan atık toplama işlemi devam ederken ve nesil 0 ' da yeterli nesne ayırdığınızda CLR, 1. nesil bir ön plan atık toplama işlemi gerçekleştirir. Adanmış arka plan atık toplama iş parçacığı, ön plan atık toplama için bir istek olup olmadığını anlamak için sık kullanılan güvenli noktaları denetler. Varsa, ön plan atık toplama işleminin gerçekleşmesi için arka plan koleksiyonu kendisini askıya alır. Ön plan atık toplama işlemi tamamlandıktan sonra, adanmış arka plan atık toplama iş parçacığı ve Kullanıcı iş parçacıkları sürdürülür.

Arka plan atık toplama sırasında kısa ömürlü çöp koleksiyonları gerçekleşebildiğinden arka plan atık toplama, eşzamanlı atık toplama tarafından uygulanan ayırma kısıtlamalarını ortadan kaldırır. Bu, arka plan atık toplamanın kısa ömürlü nesillerdeki ölü nesneleri kaldırabileceği ve 1. nesil atık toplama sırasında gerekirse yığını genişletebileceği anlamına gelir.

Aşağıdaki çizimde, bir iş istasyonunda ayrı bir adanmış iş parçacığında gerçekleştirilen arka plan atık toplama işlemi gösterilmektedir:

![Arka plan iş istasyonu çöp toplamayı gösteren diyagram.](./media/fundamentals/background-workstation-garbage-collection.png "Arka plan iş istasyonu çöp toplamayı gösteren diyagram.")

[Başa dön](#top)

<a name="background_server_garbage_collection"></a>

## <a name="background-server-garbage-collection"></a>Arka plan sunucusu çöp toplama

.NET Framework 4,5 ile başlayarak, arka plan sunucusu çöp toplama sunucu çöp toplama için varsayılan moddur. Bu modu seçmek için, [\<gcServer > öğesinin](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) `enabled` özniteliğini çalışma zamanı yapılandırma şemasında `true` olarak ayarlayın. Bu mod, önceki bölümde açıklanan arka plan iş istasyonu çöp toplamasına benzer şekilde çalışır, ancak birkaç farklılık vardır. Arka plan iş istasyonu çöp toplama, bir adanmış arka plan atık toplama iş parçacığı kullanır, ancak arka plan sunucusu çöp toplama, genellikle her mantıksal işlemci için ayrılmış bir iş parçacığı kullanır. İş istasyonu arka plan atık toplama iş parçacığından farklı olarak, bu iş parçacıkları zaman aşımına uğrar.

Aşağıdaki çizimde, bir sunucudaki ayrı bir adanmış iş parçacığında gerçekleştirilen arka plan atık toplama işlemi gösterilmektedir:

![Arka plan sunucusu çöp toplamayı gösteren diyagram.](./media/fundamentals/background-server-garbage-collection.png "Arka plan sunucusu çöp toplamayı gösteren diyagram.")

## <a name="see-also"></a>Ayrıca bkz.

- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
