---
title: Çöp toplamanın temelleri
description: Çöp toplayıcısının nasıl çalıştığını ve en iyi performans için nasıl yapılandırılabileceğini öğrenin.
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330425"
---
# <a name="fundamentals-of-garbage-collection"></a>Çöp toplamanın temelleri

Ortak dil çalışma zamanında (CLR) Çöp toplayıcı (GC) otomatik bellek yöneticisi olarak görev yapar. Aşağıdaki avantajları sağlar:

- , El ile bellek boşaltmaya gerek kalmadan uygulamanızı geliştirmenize olanak sağlar.

- Yönetilen yığında nesneleri verimli bir şekilde ayırır.

- Artık kullanılmayan nesneleri geri kazanır, hafızasını temizler ve belleğin gelecekteki ayırmalarda kullanılabilmesini önler. Yönetilen nesneler, ile başlamak için otomatik olarak temiz içerik alır, bu nedenle oluşturucuların her veri alanını başlatması gerekmez.

- Bir nesnenin başka bir nesnenin içeriğini kullanabilmesi için bellek güvenliği sağlar.

Bu makalede çöp toplamanın temel kavramları açıklanmaktadır.

## <a name="fundamentals-of-memory"></a>Belleğin temelleri

Aşağıdaki listede, önemli CLR belleği kavramları özetlenmektedir.

- Her işlemin kendi kendine ayrı bir sanal adres alanı vardır. Aynı bilgisayardaki tüm süreçler, varsa aynı fiziksel belleği ve sayfa dosyasını paylaşır.

- Varsayılan olarak, 32 bit bilgisayarlarda, her işlemin 2 GB 'lık bir Kullanıcı modu sanal adres alanı vardır.

- Bir uygulama geliştiricisi olarak yalnızca sanal adres alanı ile çalışır ve fiziksel belleği doğrudan hiçbir şekilde işlemeyin. Çöp toplayıcı, yönetilen yığında sizin için sanal belleği ayırır ve serbest bırakır.

  Yerel kod yazıyorsanız, sanal adres alanı ile çalışmak için Windows işlevlerini kullanırsınız. Bu işlevler, yerel yığınlardaki sanal belleği ayırır ve boşaltır.

- Sanal bellek üç durumda olabilir:

  - Süz. Bellek bloğunun kendisine başvuru yoktur ve ayırma için kullanılabilir.

  - Ayrılamadı. Bellek bloğu kullanım için kullanılabilir ve diğer herhangi bir ayırma isteği için kullanılamaz. Ancak, bu bellek bloğunda verileri kaydedilene kadar depoleyemez.

  - Yazıldı. Bellek bloğu fiziksel depolamaya atanır.

- Sanal adres alanı parçalanabilir. Bu, adres alanında delik olarak da bilinen boş blokların olduğu anlamına gelir. Sanal bellek ayırma istendiğinde, sanal bellek yöneticisinin, bu ayırma isteğini karşılamak için yeterince büyük olan tek bir ücretsiz blok bulması gerekir. 2 GB boş alan olsa bile, tüm bu boş alan tek bir adres bloğunda yer almadığı takdirde 2 GB gerektiren ayırma başarısız olur.

- Ayırmak için yeterli sanal adres alanı yoksa ve yürütülecek fiziksel alan yoksa bellek tükeniyor.

  Fiziksel bellek baskısı (yani fiziksel bellek talebi) düşük olsa bile sayfa dosyası kullanılır. Fiziksel bellek baskısı ilk kez yüksek olduğunda, işletim sistemi, verileri depolamak için fiziksel bellekte yer almalıdır ve fiziksel bellekteki bazı verileri sayfa dosyasına yedekler. Bu veriler, gerekli olana kadar sayfalanmadığı için fiziksel bellek basıncının düşük olduğu durumlarda sayfalama ile karşılaşmak mümkündür.

## <a name="conditions-for-a-garbage-collection"></a>Çöp toplama koşulları

Çöp toplama, aşağıdaki koşullardan biri doğru olduğunda gerçekleşir:

- Sistemde fiziksel bellek yetersiz. Bu, ana bilgisayar tarafından belirtilen işletim sistemi ya da düşük bellekten düşük bellek bildirimi tarafından algılanır.

- Yönetilen yığında ayrılmış nesneler tarafından kullanılan bellek, kabul edilebilir bir eşik geçirir. İşlem çalışırken bu eşik sürekli olarak ayarlanır.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> yöntemi çağrılır. Neredeyse tüm durumlarda, çöp toplayıcı sürekli çalıştığından bu yöntemi çağırmanız gerekmez. Bu yöntem öncelikle benzersiz durumlar ve test için kullanılır.

## <a name="the-managed-heap"></a>Yönetilen yığın

Çöp toplayıcı CLR tarafından başlatıldıktan sonra, nesneleri depolamak ve yönetmek için bir bellek segmenti ayırır. Bu bellek, işletim sistemindeki yerel bir yığının aksine yönetilen yığın olarak adlandırılır.

Yönetilen her işlem için yönetilen bir yığın vardır. İşlemdeki tüm iş parçacıkları aynı yığında nesneler için bellek ayırır.

Bellek ayırmak için çöp toplayıcı Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) işlevini çağırır ve yönetilen uygulamalar için bir seferde bir bellek kesimini ayırır. Çöp toplayıcı, gerektiğinde kesimleri de ayırır ve Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) işlevini çağırarak kesimleri işletim sistemine (herhangi bir nesne temizlenmeden sonra) yeniden yayınlar.

> [!IMPORTANT]
> Çöp toplayıcı tarafından ayrılan parçaların boyutu uygulamaya özgüdür ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değiştirilebilir. Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.

Yığın üzerinde daha az nesne ayrılmışsa, çöp toplayıcının yapması gereken daha az iş vardır. Nesneleri ayırdığınızda, yalnızca 15 bayta ihtiyacınız olduğunda 32 baytlık bir dizi tahsis etme gibi gereksinimlerinizi aşan yuvarlanmış değerler kullanmayın.

Çöp toplama tetiklendiğinde çöp toplayıcı, ölü nesneler tarafından kullanılan belleği geri kazanır. Geri kazanma işlemi, canlı nesneleri bir araya gelecek şekilde sıkıştırır ve atılacak alan kaldırıldıktan sonra yığın daha küçük hale getirir. Bu, birlikte ayrılan nesnelerin, konumlarını korumak için yönetilen yığında birlikte kalmasını sağlar.

Çöp koleksiyonlarının sürekliliği (sıklığı ve süresi), ayırma hacminin ve yönetilen yığında kalan bellek miktarının sonucudur.

Yığın iki sayfa@@ 'nin birikmesi olarak düşünülebilir: [büyük nesne yığını](large-object-heap.md) ve küçük nesne yığını.

[Büyük nesne yığını](large-object-heap.md) 85.000 bayt ve daha büyük olan çok büyük nesneler içerir. Büyük nesne yığınındaki nesneler genellikle dizilerdir. Örnek nesnesinin son derece büyük olması nadir bir durumdur.

> [!TIP]
> Nesnelerin [eşik boyutunu](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) büyük nesne yığınında gidilecek şekilde yapılandırabilirsiniz.

## <a name="generations"></a>İse

Yığın, uzun süreli ve kısa süreli nesneleri işleyebilmesi için nesiller halinde düzenlenir. Çöp toplama öncelikli olarak genellikle yığının yalnızca küçük bir kısmını kaplayan kısa süreli nesneler geri kazanma ile gerçekleşir. Yığında üç Neste nesne vardır:

- **Nesil 0**. Bu, kardeşinizin nesli ve kısa süreli nesneler içerir. Kısa süreli bir nesne örneği, geçici bir değişkendir. Çöp toplama bu nesde en sık oluşur.

  Yeni ayrılmış nesneler yeni nesil nesneler oluşturur ve örtülü olarak 0. nesil koleksiyonlardır. Ancak, büyük nesnelerse, kuşak 2 koleksiyonundaki büyük nesne yığınına gider.

  Çoğu nesne, oluşturma 0 ' da çöp toplama için geri kazanılır ve bir sonraki nesle devam etmez.

- **1. nesil**. Bu nesil, kısa süreli nesneler içerir ve kısa süreli nesneler ve uzun süreli nesneler arasında bir arabellek işlevi görür.

- **2. nesil**. Bu nesil uzun süreli nesneler içerir. Uzun süreli bir nesne örneği, işlem süresince canlı olan statik verileri içeren bir sunucu uygulamasındaki nesnedir.

Atık koleksiyonlar belirli nesiller üzerinde koşullar garanti olarak oluşur. Oluşturma toplanması, bu kuşak ve tüm küçük nesiller içindeki nesnelerin toplanması anlamına gelir. 2\. nesil atık toplama, tüm nesiller içindeki tüm nesneleri geri kazanır (yani, yönetilen yığındaki tüm nesneler) olduğu için tam çöp toplama olarak da bilinir.

### <a name="survival-and-promotions"></a>Acil ihtiyaç ve promosyonlar

Atık toplamada geri kazanımayan nesneler, acil sanal öğeler olarak bilinir ve bir sonraki oluşturmaya yükseltilir. Nesil 0 atık toplamayı sürdüren nesneler 1. nesil olarak yükseltilir; 1. nesil atık toplamayı sürdüren nesneler 2. nesil olarak yükseltilir; ve 2. nesil bir atık toplamayı sürdüren nesneler 2. kuşak olarak kalır.

Çöp toplayıcı, bir kuşakma hızının yüksek olduğunu algıladığında, bu kuşak için ayırmaların eşiğini arttırır. Sonraki koleksiyon, geri kazanılan bellek miktarını önemli ölçüde alır. CLR sürekli olarak iki öncelik dengeler: bir uygulamanın çalışma kümesinin çöp toplamayı geciktirerek çok büyük bir şekilde geçmesine izin vermez ve çöp toplamanın çok sık çalışmasına izin vermez.

### <a name="ephemeral-generations-and-segments"></a>Kısa ömürlü Nesler ve segmentler

Nesil 0 ve 1 ' deki nesneler kısa süreli olduğundan, bu nesiller, kısa ömürlü nesiller olarak bilinir.

Kısa ömürlü nesiller, kısa ömürlü segment olarak bilinen bellek segmentinde ayrılmalıdır. Çöp toplayıcı tarafından alınan her yeni segment, yeni kısa ömürlü segment olur ve 0. nesil atık toplamayı izleyen nesneleri içerir. Eski kısa ömürlü segment, yeni nesil 2 segmentine dönüşür.

Kısa ömürlü segmentin boyutu sistemin 32-bit mi yoksa 64 bit mi olduğunu ve çalıştırdığı çöp toplayıcı türünde olmasına bağlı olarak değişir. Varsayılan değerler aşağıdaki tabloda gösterilmiştir.

||32 bit:|64 bit|
|-|-------------|-------------|
|İş istasyonu GC|16 MB|256 MB|
|Sunucu GC|64 MB|4 GB|
|> 4 mantıksal CPU içeren sunucu GC|32 MB|2 GB|
|> 8 mantıksal CPU 'Lar ile sunucu GC|16 MB|1 GB|

Kısa ömürlü segment 2. nesil nesneleri içerebilir. 2\. nesil nesneler birden çok segment kullanabilir (işleminiz için gereken ve belleğin izin verdiği kadar).

Kısa ömürlü atık toplamanın serbest bırakılan bellek miktarı, kısa ömürlü segmentin boyutuyla sınırlıdır. Serbest bırakılan bellek miktarı, ölü nesneler tarafından kullanılan alanla orantılıdır.

## <a name="what-happens-during-a-garbage-collection"></a>Çöp toplama sırasında ne olur?

Bir çöp toplama işlemi aşağıdaki aşamaları içerir:

- Tüm canlı nesnelerin listesini bulan ve oluşturan bir işaretleme aşaması.

- Düzenlenecek nesneler için başvuruları güncelleştiren bir değiştirme aşaması.

- Yok sayılma nesnelerinin kapladığı alanı geri kazanır ve kalan nesneleri sıkıştırarak bir düzenleme aşaması. Sıkıştırma aşaması, bir atık toplamayı, segmentin eski ucuna doğru bir şekilde taşımış nesneleri hareket ettirir.

  2\. nesil koleksiyonlar birden çok parçayı kaplayabildiğinden, 2. nesil olarak yükseltilen nesneler eski bir kesime taşınabilir. 2\. nesil ve 2. nesil ve 2. nesil daha fazla VNet, 1. kuşak olarak yükseltildikleri için farklı bir kesime taşınabilir.

  Genellikle büyük nesne yığını (LOH) sıkıştırmaz, çünkü büyük nesneleri kopyalamak bir performans cezası uygular. Ancak, .NET Core 'da ve .NET Framework 4.5.1 ve üzeri sürümlerde, büyük nesne yığınını isteğe bağlı olarak sıkıştırmak için <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliğini kullanabilirsiniz. Ayrıca, bir sabit sınır belirtildiğinde, LOH otomatik olarak sıkıştırılır:

  - kapsayıcıda bir bellek sınırı veya
  - [gcheaphardlimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) veya [Gcheaphardlimit yüzdesi](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) çalışma zamanı yapılandırma seçenekleri

Çöp toplayıcı, nesnelerin canlı olup olmadığını anlamak için aşağıdaki bilgileri kullanır:

- **Yığın kökleri**. Tam zamanında (JıT) derleyici ve yığın denetçisi tarafından sunulan yığın değişkenleri. JıT iyileştirmeleri, yığın değişkenlerinin çöp toplayıcısına bildirildiği kod bölgelerini uzatabilir veya kısaltabilir.

- **Çöp toplama tutamaçları**. Yönetilen nesneleri işaret eden ve Kullanıcı kodu veya ortak dil çalışma zamanı tarafından ayrılabilen işler.

- **Statik veriler**. Uygulama etki alanlarında diğer nesnelere başvurıbir statik nesneler. Her uygulama etki alanı, kendi statik nesnelerini izler.

Çöp toplama başlamadan önce, çöp toplamayı tetikleyen iş parçacığı hariç tüm yönetilen iş parçacıkları askıya alınır.

Aşağıdaki çizimde, çöp toplamayı tetikleyen ve diğer iş parçacıklarının askıya alınmasına neden olan bir iş parçacığı gösterilmektedir.

![Bir iş parçacığı bir çöp toplama işlemi tetiklerse](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Yönetilmeyen kaynakları değiştirme

Yönetilen nesneler, kendi yerel dosya tutamaçlarını kullanarak yönetilmeyen nesnelere başvuru yaptığından, atık toplayıcı yalnızca yönetilen yığında belleği izlediği için yönetilmeyen nesneleri açık bir şekilde serbest yapmanız gerekir.

Yönetilen nesne kullanıcıları, nesne tarafından kullanılan yerel kaynakları atılamayabilir. Temizleme işlemini gerçekleştirmek için, yönetilen nesneyi sonlandırılabilir hale getirebilirsiniz. Sonlandırma, nesne artık kullanımda olmadığında yürütülen Temizleme eylemlerinden oluşur. Yönetilen nesne söz konusu olduğunda, sonlandırıcı yönteminde belirtilen temizleme eylemlerini gerçekleştirir.

Sonlandırılabilir bir nesnenin etkin olmadığı tespit edildiğinde, temizleme eylemlerinin yürütülmesi için Sonlandırıcı bir sıraya konur, ancak nesnenin kendisi bir sonraki oluşturmaya yükseltilir. Bu nedenle, nesnenin geri kazanılıp kazanılmadığını öğrenmek için bu kuşada gerçekleşen sonraki atık toplamaya (bir sonraki atık toplama olması gerekmez) kadar beklemeniz gerekir.

Sonlandırma hakkında daha fazla bilgi için bkz. <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu atık toplama

Çöp toplayıcı kendi kendini ayarlamadır ve çok çeşitli senaryolarda çalışabilir. Bir [yapılandırma dosyası ayarını](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) , iş yükünün özelliklerine göre çöp toplamanın türünü ayarlamak için kullanabilirsiniz. CLR aşağıdaki çöp toplama türlerini sağlar:

- İş istasyonu çöp toplama (GC), istemci uygulamaları için tasarlanmıştır. Tek başına uygulamalar için varsayılan GC Flavor 'dir. Barındırılan uygulamalarda, örneğin, ASP.NET tarafından barındırılan uygulamalar için, ana bilgisayar varsayılan GC özelliğini belirler.

  İş istasyonu atık toplama işlemi eşzamanlı olabilir veya eşzamanlı olmayan bir şekilde olabilir. Eşzamanlı atık toplama, yönetilen iş parçacıklarının bir çöp toplama sırasında işlemlere devam etmesine olanak sağlar. [Arka plan atık toplama](#background-workstation-garbage-collection) , .NET Framework 4 ve sonraki sürümlerde [eşzamanlı çöp toplama](#concurrent-garbage-collection) yerini alır.

- Yüksek aktarım hızı ve ölçeklenebilirlik gerektiren sunucu uygulamalarına yönelik olan sunucu çöp toplama.

  - .NET Core 'da, sunucu çöp toplama, eş zamanlı olmayan veya arka plan olabilir.

  - .NET Framework 4,5 ve sonraki sürümlerinde, sunucu çöp toplama, eş zamanlı olmayan veya arka plan olabilir (arka plan atık toplama, eşzamanlı atık toplamayı değiştirir). .NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama işlemi eşzamanlı değildir.

Aşağıdaki çizimde, bir sunucusunda çöp toplamayı gerçekleştiren adanmış iş parçacıkları gösterilmektedir:

![Sunucu atık toplama Iş parçacıkları](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplamayı karşılaştırın

İş istasyonu çöp toplama işlemi için iş parçacığı ve performans değerlendirmeleri aşağıda verilmiştir:

- Koleksiyon, çöp toplamayı tetikleyen ve aynı önceliğe kalan Kullanıcı iş parçacığında oluşur. Kullanıcı iş parçacıkları genellikle normal öncelikte çalıştığı için çöp toplayıcı (normal bir öncelikli iş parçacığı üzerinde çalışır), CPU süresi için diğer iş parçacıklarıyla rekabet etmelidir. (Yerel kod çalıştıran iş parçacıkları sunucu veya iş istasyonu çöp toplamadan askıya alınmaz.)

- İş istasyonu çöp toplama her zaman, [yapılandırma ayarından](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)bağımsız olarak yalnızca bir işlemciye sahip olan bir bilgisayarda kullanılır.

Aşağıda sunucu çöp toplama için iş parçacığı ve performans konuları verilmiştir:

- Koleksiyon `THREAD_PRIORITY_HIGHEST` öncelik düzeyinde çalışan birden fazla adanmış iş parçacığında oluşur.

- Her CPU için bir yığın ve bir ayrılmış iş parçacığı her CPU için sağlanır ve sayfa@@ 'ler aynı anda toplanır. Her yığın küçük bir nesne yığını ve büyük bir nesne yığını içerir ve tüm yığınlara Kullanıcı kodu tarafından erişilebilir. Farklı yığınlardaki nesneler birbirlerine başvurabilir.

- Birden çok çöp toplama iş parçacığı birlikte çalıştığından, sunucu çöp toplama, aynı boyuttaki yığında iş istasyonu atık toplamadan daha hızlıdır.

- Sunucu çöp toplama genellikle daha büyük boyut segmentlerine sahiptir. Ancak, bu yalnızca bir Genelleştirme 'dir: kesim boyutu uygulamaya özeldir ve değiştirilebilir. Uygulamanızı ayarlamaya yönelik çöp toplayıcı tarafından ayrılan parçaların boyutu hakkında varsayımlar yapmayın.

- Sunucu atık toplama, kaynak kullanımı yoğun olabilir. Örneğin, 4 işlemcili bir bilgisayarda çalışan sunucu GC 'yi kullanan 12 işlem olduğunu düşünün. Tüm süreçler aynı anda çöp toplama işlemi gerçekleşiyorsa, aynı işlemcide zamanlanan 12 iş parçacığı olduğu için birbirleriyle karışacaktır. Süreçler etkinse, hepsi sunucu GC 'yi kullanmak iyi bir fikir değildir.

Bir uygulamanın yüzlerce örneğini çalıştırıyorsanız, eşzamanlı atık toplama devre dışı bırakılmış iş istasyonu çöp toplamayı kullanmayı düşünün. Bu, performansı iyileştirebilen daha az bağlam geçişe neden olur.

## <a name="background-workstation-garbage-collection"></a>Arka plan iş istasyonu çöp toplama

Arka plan iş istasyonu çöp toplama bölümünde, 2. nesil toplama işlemi devam ederken kısa ömürlü nesiller (0 ve 1) gerektiği şekilde toplanır. Arka plan iş istasyonu çöp toplama işlemi adanmış bir iş parçacığında gerçekleştirilir ve yalnızca 2. nesil koleksiyonlar için geçerlidir.

Arka plan atık toplama varsayılan olarak etkindir ve .NET Framework uygulamalar veya .NET Core uygulamalarında [System. GC. eş zamanlı](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) ayarı [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma ayarıyla etkinleştirilebilir veya devre dışı bırakılabilir.

> [!NOTE]
> Arka plan atık toplama, [eşzamanlı atık toplamayı](#concurrent-garbage-collection) değiştirir ve .NET Framework 4 ve sonraki sürümlerde kullanılabilir. .NET Framework 4 ' te yalnızca iş istasyonu çöp toplama için desteklenir. .NET Framework 4,5 ' den başlayarak, arka plan atık toplama, hem iş istasyonu hem de sunucu çöp toplama için kullanılabilir.

Arka plan atık toplama sırasında kısa ömürlü oluşumlara yönelik bir koleksiyon, ön plan atık toplama olarak bilinir. Ön plan atık koleksiyonları gerçekleştiğinde, tüm yönetilen iş parçacıkları askıya alınır.

Arka plan atık toplama işlemi devam ederken ve nesil 0 ' da yeterli nesne ayırdığınızda CLR, 1. nesil bir ön plan atık toplama işlemi gerçekleştirir. Adanmış arka plan atık toplama iş parçacığı, ön plan atık toplama için bir istek olup olmadığını anlamak için sık kullanılan güvenli noktaları denetler. Varsa, ön plan atık toplama işleminin gerçekleşmesi için arka plan koleksiyonu kendisini askıya alır. Ön plan atık toplama işlemi tamamlandıktan sonra, adanmış arka plan atık toplama iş parçacığı ve Kullanıcı iş parçacıkları sürdürülür.

Arka plan atık toplama sırasında kısa ömürlü çöp koleksiyonları gerçekleşebildiğinden arka plan atık toplama, eşzamanlı atık toplama tarafından uygulanan ayırma kısıtlamalarını ortadan kaldırır. Arka plan atık toplama, kısa ömürlü neslerdeki ölü nesneleri kaldırabilir. Ayrıca, 1. nesil atık toplama işlemi sırasında gerekirse yığını genişletebilir.

Aşağıdaki çizimde, bir iş istasyonunda ayrı bir adanmış iş parçacığında gerçekleştirilen arka plan atık toplama işlemi gösterilmektedir:

![Arka plan iş istasyonu çöp toplama](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Arka plan sunucusu çöp toplama

.NET Framework 4,5 ile başlayarak, arka plan sunucusu çöp toplama sunucu çöp toplama için varsayılan moddur.

Arka plan sunucusu çöp toplama, önceki bölümde açıklanan arka plan iş istasyonu çöp toplamasına benzer şekilde çalışır, ancak bazı farklılıklar vardır:

- Arka plan iş istasyonu çöp toplama, bir adanmış arka plan atık toplama iş parçacığı kullanır, ancak arka plan sunucusu çöp toplama birden çok iş Genellikle, her mantıksal işlemci için adanmış bir iş parçacığı vardır.

- İş istasyonu arka plan atık toplama iş parçacığından farklı olarak, bu iş parçacıkları zaman aşımına uğrar.

Aşağıdaki çizimde, bir sunucudaki ayrı bir adanmış iş parçacığında gerçekleştirilen arka plan atık toplama işlemi gösterilmektedir:

![Arka plan sunucusu çöp toplama](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Eşzamanlı atık toplama

> [!TIP]
> Bu bölüm için geçerlidir:
>
> - İş istasyonu atık toplama için .NET Framework 3,5 ve öncesi
> - Sunucu atık toplama için .NET Framework 4 ve öncesi
>
> Eş zamanlı atık, sonraki sürümlerde [arka plan atık toplama](#background-workstation-garbage-collection) ile değiştirilmiştir.

İş istasyonu veya sunucu çöp toplama bölümünde, iş parçacıklarının, koleksiyon süresince büyük bir süre için çöp toplamayı gerçekleştiren adanmış bir iş parçacığıyla eşzamanlı olarak çalışmasını sağlayan [eşzamanlı atık toplamayı etkinleştirebilirsiniz](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md). Bu seçenek, kuşak 2 ' de yalnızca çöp koleksiyonlarını etkiler; nesil 0 ve 1 her zaman eşzamanlı değildir çünkü çok hızlı tamamlanır.

Eşzamanlı atık toplama, bir koleksiyon için duraklamaları en aza indirerek etkileşimli uygulamaların daha fazla yanıt vermesini sağlar. Yönetilen iş parçacıkları, eşzamanlı atık toplama iş parçacığı çalışırken çoğu zaman çalışmaya devam edebilir. Çöp toplama işlemi gerçekleşirken bu, daha kısa duraklamalar oluşur.

Eş zamanlı çöp toplama, adanmış bir iş parçacığında gerçekleştirilir. Varsayılan olarak, CLR, eşzamanlı atık toplama özellikli iş istasyonu çöp toplamayı çalıştırır. Bu, tek işlemci ve çok işlemcili bilgisayarlar için geçerlidir.

Aşağıdaki çizimde ayrı bir adanmış iş parçacığında gerçekleştirilen eşzamanlı çöp toplama gösterilmektedir.

![Eşzamanlı atık toplama Iş parçacıkları](./media/gc-concurrent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [GC için yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
- [Çöp toplama](index.md)
