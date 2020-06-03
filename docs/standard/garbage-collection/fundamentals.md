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
ms.openlocfilehash: d59f368f21964c07d371df604f0728fa6ca8ac00
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307039"
---
# <a name="fundamentals-of-garbage-collection"></a>Çöp toplamanın temelleri

Ortak dil çalışma zamanında (CLR) Çöp toplayıcı (GC) otomatik bellek yöneticisi olarak görev yapar. Çöp toplayıcı, bir uygulama için bellek ayırmayı ve serbest bırakma işlemini yönetir. Yönetilen kodla çalışan geliştiriciler için bu, bellek yönetimi görevlerini gerçekleştirmek için kod yazmanız gerekmediği anlamına gelir. Otomatik bellek yönetimi, bir nesneyi serbest bırakma ve Bellek sızıntısını sağlama veya zaten boşaltılmış bir nesne için belleğe erişme girişimi gibi yaygın sorunları ortadan kaldırabilir.

Bu makalede çöp toplamanın temel kavramları açıklanmaktadır.

## <a name="benefits"></a>Avantajlar

Çöp toplayıcı aşağıdaki avantajları sağlar:

- Geliştiricilerin belleği el ile serbest bırakma gereğini ortadan boşaltır.

- Yönetilen yığında nesneleri verimli bir şekilde ayırır.

- Artık kullanılmayan nesneleri geri kazanır, hafızasını temizler ve belleğin gelecekteki ayırmalarda kullanılabilmesini önler. Yönetilen nesneler, ile başlamak için otomatik olarak temiz içerik alır, bu nedenle oluşturucuları her veri alanını başlatmak zorunda kalmaz.

- Bir nesnenin başka bir nesnenin içeriğini kullanabilmesi için bellek güvenliği sağlar.

## <a name="fundamentals-of-memory"></a>Belleğin temelleri

Aşağıdaki listede, önemli CLR belleği kavramları özetlenmektedir.

- Her işlemin kendi kendine ayrı bir sanal adres alanı vardır. Aynı bilgisayardaki tüm süreçler, varsa aynı fiziksel belleği ve sayfa dosyasını paylaşır.

- Varsayılan olarak, 32 bit bilgisayarlarda, her işlemin 2 GB 'lık bir Kullanıcı modu sanal adres alanı vardır.

- Bir uygulama geliştiricisi olarak yalnızca sanal adres alanı ile çalışır ve fiziksel belleği doğrudan hiçbir şekilde işlemeyin. Çöp toplayıcı, yönetilen yığında sizin için sanal belleği ayırır ve serbest bırakır.

  Yerel kod yazıyorsanız, sanal adres alanı ile çalışmak için Windows işlevlerini kullanırsınız. Bu işlevler, yerel yığınlardaki sanal belleği ayırır ve boşaltır.

- Sanal bellek üç durumda olabilir:

  | Eyalet | Açıklama |
  |---------|---------|
  | Ücretsiz | Bellek bloğunun kendisine başvuru yoktur ve ayırma için kullanılabilir. |
  | Ayrıldı | Bellek bloğu kullanım için kullanılabilir ve diğer herhangi bir ayırma isteği için kullanılamaz. Ancak, bu bellek bloğunda verileri kaydedilene kadar depoleyemez. |
  | Yürütülen | Bellek bloğu fiziksel depolamaya atanır. |

- Sanal adres alanı parçalanabilir. Bu, adres alanında delik olarak da bilinen boş blokların olduğu anlamına gelir. Sanal bellek ayırma istendiğinde, sanal bellek yöneticisinin, bu ayırma isteğini karşılamak için yeterince büyük olan tek bir ücretsiz blok bulması gerekir. 2 GB boş alan olsa bile, tüm bu boş alan tek bir adres bloğunda yer almadığı takdirde 2 GB gerektiren bir ayırma başarısız olur.

- Ayırmak için yeterli sanal adres alanı yoksa ve yürütülecek fiziksel alan yoksa bellek tükeniyor.

  Fiziksel bellek baskısı (yani fiziksel bellek talebi) düşük olsa bile sayfa dosyası kullanılır. Fiziksel bellek baskısı ilk kez yüksek olduğunda, işletim sistemi, verileri depolamak için fiziksel bellekte yer almalıdır ve fiziksel bellekteki bazı verileri sayfa dosyasına yedekler. Bu veriler, gerekli olana kadar sayfalanmadığı için fiziksel bellek basıncının düşük olduğu durumlarda sayfalama ile karşılaşmak mümkündür.
  
### <a name="memory-allocation"></a>Bellek ayırma

Yeni bir işlem başlattığınızda, çalışma zamanı işlem için adres bölgesine bitişik bir adres alanı ayırır. Bu ayrılmış adres alanına yönetilen yığın denir. Yönetilen yığın, yığın içinde sıradaki nesnenin nereye ayrılacağını belirten bir işaretçi tutar. Başlangıçta, bu işaretçi yönetilen yığının taban adresi olarak ayarlanır. Tüm başvuru türleri yönetilen yığında ayrılır. Bir uygulama ilk referans türünü oluşturduğunda, türe yönelik bellek, yönetilen yığının taban adresinde ayrılır. Uygulama bir sonraki nesneyi oluşturduğunda, atık toplayıcı bunun için ilk nesnenin hemen ardındaki adres alanında bellek ayırır. Kullanılabilir adres alanı olduğu sürece, atık toplayıcı yeni nesnelere bu şekilde bellek ayırmaya devam eder.

Yönetilen yığından bellek ayırmak, yönetilmeyen bellek ayrımından daha hızlıdır. Çalışma zamanı bir işaretçiye değer ekleyerek bir nesne için bellek ayırdığından, yığından bellek ayırma kadar hızlıdır. Ayrıca, art arda ayrılan yeni nesneler yönetilen yığında bitişik olarak depolandığından, bir uygulama nesnelere hızlı bir şekilde erişebilir.

### <a name="memory-release"></a>Bellek sürümü

Atık toplayıcısının optimizasyon altyapısı, yapılan ayrımlara göre bir toplama işlemini gerçekleştirmek için en iyi zamanı belirler. Atık toplayıcı bir toplama gerçekleştirdiğinde, uygulama tarafından artık kullanılmayan nesnelere ayrılan belleği serbest bırakır. Uygulamanın *köklerini*inceleyerek hangi nesnelerin artık kullanılmadığını belirler. Bir uygulamanın kökleri statik alanlar, yerel değişkenler ve bir iş parçacığının yığınındaki parametreleri ve CPU kayıtları içerir. Her kök yönetilen yığındaki bir nesneye başvurur veya null olarak ayarlanır. Çöp toplayıcı, tam zamanında (JıT) derleyicisinin ve çalışma zamanının korumasını sağlayan etkin kökler listesine erişebilir. Bu listeyi kullanarak, çöp toplayıcı köklerden erişilebilen tüm nesneleri içeren bir grafik oluşturur.

Grafta bulunmayan nesnelere uygulamanın köklerinden ulaşılamaz. Çöp toplayıcı erişilemeyen nesneleri atık olarak değerlendirir ve bunlar için ayrılan belleği serbest bırakır. Bir toplama sırasında, atık toplayıcı yönetilen yığını inceleyerek erişilemeyen nesneler tarafından kullanılan adres alanı bloklarını arar. Erişilemeyen nesneleri keşfettikçe, bir bellek kopyalama işleviyle bellekteki erişilebilir nesneleri sıkıştırır ve bu sayede, erişilemeyen nesnelere ayrılan adres alanlarını serbest bırakır. Erişilebilir nesneler için bellek sıkıştırıldıktan sonra atık toplayıcı gerekli işaretçi düzeltmelerini yaparak uygulamanın köklerinin nesnelerin yeni konumlarına işaret etmesini sağlar. Ayrıca yönetilen yığının işaretçisini erişilebilen son nesnenin sonuna konumlandırır.

Bellek yalnızca bir koleksiyon önemli sayıda ulaşılamaz nesne tespit ederseniz sıkıştırılır. Yönetilen bellekteki tüm nesneler bir toplamadan sonra kalmaya devam ederse, bellek sıkıştırmaya gerek yoktur.

Performansı artırmak açısından, çalışma zamanı büyük nesneler için ayrı bir yığında bellek ayırır. Atık toplayıcı, büyük nesnelerin belleğini otomatik olarak serbest bırakır. Ancak, büyük nesnelerin bellekte taşınmasını önlemek için bu bellek genellikle sıkıştırmaz.

## <a name="conditions-for-a-garbage-collection"></a>Çöp toplama koşulları

Çöp toplama, aşağıdaki koşullardan biri doğru olduğunda gerçekleşir:

- Sistemde fiziksel bellek yetersiz. Bu, ana bilgisayar tarafından belirtilen işletim sistemi ya da düşük bellekten düşük bellek bildirimi tarafından algılanır.

- Yönetilen yığında ayrılmış nesneler tarafından kullanılan bellek, kabul edilebilir bir eşik geçirir. İşlem çalışırken bu eşik sürekli olarak ayarlanır.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType>Yöntemi çağrılır. Neredeyse tüm durumlarda, çöp toplayıcı sürekli olarak çalıştığından bu yöntemi çağırmanız gerekmez. Bu yöntem öncelikle benzersiz durumlar ve test için kullanılır.

## <a name="the-managed-heap"></a>Yönetilen yığın

Çöp toplayıcı CLR tarafından başlatıldıktan sonra, nesneleri depolamak ve yönetmek için bir bellek segmenti ayırır. Bu bellek, işletim sistemindeki yerel bir yığının aksine yönetilen yığın olarak adlandırılır.

Yönetilen her işlem için yönetilen bir yığın vardır. İşlemdeki tüm iş parçacıkları aynı yığında nesneler için bellek ayırır.

Bellek ayırmak için çöp toplayıcı Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) işlevini çağırır ve yönetilen uygulamalar için bir seferde bir bellek kesimini ayırır. Çöp toplayıcı, gerektiğinde kesimleri de ayırır ve Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) işlevini çağırarak kesimleri işletim sistemine (herhangi bir nesne temizlenmeden sonra) yeniden yayınlar.

> [!IMPORTANT]
> Çöp toplayıcı tarafından ayrılan parçaların boyutu uygulamaya özgüdür ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değiştirilebilir. Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.

Yığın üzerinde daha az nesne ayrılmışsa, çöp toplayıcının yapması gereken daha az iş vardır. Nesneleri ayırdığınızda, yalnızca 15 bayta ihtiyacınız olduğunda 32 baytlık bir dizi tahsis etme gibi gereksinimlerinizi aşan yuvarlanmış değerler kullanmayın.

Çöp toplama tetiklendiğinde çöp toplayıcı, ölü nesneler tarafından kullanılan belleği geri kazanır. Geri kazanma işlemi, canlı nesneleri bir araya gelecek şekilde sıkıştırır ve atılacak alan kaldırıldıktan sonra yığın daha küçük hale getirir. Bu, birlikte ayrılan nesnelerin, konumlarını korumak için yönetilen yığında birlikte kalmasını sağlar.

Çöp koleksiyonlarının sürekliliği (sıklığı ve süresi), ayırma hacminin ve yönetilen yığında kalan bellek miktarının sonucudur.

Yığın iki sayfa@@ 'nin birikmesi olarak düşünülebilir: [büyük nesne yığını](large-object-heap.md) ve küçük nesne yığını. Büyük nesne yığını, genellikle diziler olan 85.000 bayt ve daha büyük nesneler içerir. Örnek nesnenin son derece büyük olması nadir bir durumdur.

> [!TIP]
> Nesnelerin [eşik boyutunu](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) büyük nesne yığınında gidilecek şekilde yapılandırabilirsiniz.

## <a name="generations"></a>İse

GC algoritması çeşitli noktalara dayanır:

- Yönetilen yığının tamamı için yönetilen yığının bir bölümü için belleği sıkıştırmak daha hızlıdır.
- Daha yeni nesneler daha kısa ömürleri ve eski nesnelerin ömrü daha uzundur.
- Yeni nesneler birbirleriyle ilgili olacak ve uygulama tarafından aynı anda erişilme eğilimindedir.

Çöp toplama öncelikle geri kazanma of Short-ömürlü nesneler ile gerçekleşir. Çöp toplayıcısının performansını iyileştirmek için, yönetilen yığın üç Neste, 0, 1 ve 2 ' ye bölünür, bu nedenle uzun süreli ve kısa süreli nesneleri ayrı olarak işleyebilir. Çöp toplayıcı yeni nesneleri nesil 0 ' da depolar. Uygulama ömrünün başlarında oluşturulan ve toplamalardan sonra varlığını sürdüren nesneler yükseltilerek nesil 1 ve 2'de tutulur. Yönetilen yığının tümüyle yığının bir bölümünü sıkıştırmak daha hızlı olduğundan, bu düzen çöp toplayıcısının bir koleksiyon her yaptığında tüm yönetilen yığın için belleği serbest bırakmaktansa belleği belirli bir nesle serbest bırakmasına olanak tanır.

- **Nesil 0**. Bu, kardeşinizin nesli ve kısa süreli nesneler içerir. Kısa süreli bir nesne örneği, geçici bir değişkendir. Çöp toplama bu nesde en sık oluşur.

  Yeni ayrılmış nesneler yeni nesil nesneler oluşturur ve örtülü olarak 0. nesil koleksiyonlardır. Ancak, büyük nesnelerse, bazen *2. nesil*olarak adlandırılan büyük nesne yığınına (LOH) gider. Nesil 3, 2. kuşak kapsamında mantıksal olarak toplanan fiziksel bir oluşturma.

  Çoğu nesne, 1. nesil atık toplama için geri kazanılır ve bir sonraki nesle kalmaz.
  
  Bir uygulama, 1. nesil dolduğunda yeni bir nesne oluşturmaya çalışırsa, çöp toplayıcı nesnenin adres alanını serbest bırakma girişiminde bir koleksiyon gerçekleştirir. Atık toplayıcı, yönetilen yığındaki tüm nesneler yerine nesil 0'daki nesneleri inceleyerek başlar. Tek başına 0 kuşak bir koleksiyon, uygulamanın yeni nesne oluşturmaya devam etmesini sağlamak için yeterli bellek geri kazanır.

- **1. nesil**. Bu nesil, kısa süreli nesneler içerir ve kısa süreli nesneler ve uzun süreli nesneler arasında bir arabellek işlevi görür.

  Çöp toplayıcı nesil 0 ' ın bir koleksiyonunu gerçekleştirdikten sonra, erişilebilir nesneler için belleği sıkıştırır ve bunları 1. nesil olarak yükseltir. Toplama işleminden sonra varlığını sürdüren nesneler daha uzun ömre sahip olmaya eğilimli olduklarından, bunları daha yüksek bir nesle yükseltmek mantıklıdır. Atık toplayıcısının, 1. nesil bir toplama işlemi yaptığı her seferinde neslin 1 ve 2 ' deki nesneleri yeniden incelemesi gerekmez.
  
  2. nesil bir koleksiyon, uygulamanın yeni bir nesne oluşturması için yeterli belleği geri kazanmıyorsa, çöp toplayıcı 1. nesil bir koleksiyon ve sonra 2. nesil bir toplama işlemi gerçekleştirebilir. Nesil 1'de toplama işlemlerinden sonra varlığına devam eden nesneler nesil 2'ye yükselir.

- **2. nesil**. Bu nesil uzun süreli nesneler içerir. Uzun süreli bir nesne örneği, işlem süresince canlı olan statik verileri içeren bir sunucu uygulamasındaki nesnedir.

  Kuşak 2 ' deki nesneler, gelecekteki bir koleksiyonda ulaşılamaz olarak belirlenene kadar 2. nesil bir koleksiyon üzerinde kalır.
  
  Büyük nesne yığınındaki nesneler (bazen *nesil 3*olarak adlandırılır) 2. nesil ile de toplanır.

Atık koleksiyonlar belirli nesiller üzerinde koşullar garanti olarak oluşur. Oluşturma toplanması, bu kuşak ve tüm küçük nesiller içindeki nesnelerin toplanması anlamına gelir. 2. nesil atık toplama, tüm oluşumlardaki nesneleri geri kazanır (yani, yönetilen yığındaki tüm nesneler) olduğu için tam çöp toplama olarak da bilinir.

### <a name="survival-and-promotions"></a>Acil ihtiyaç ve promosyonlar

Atık toplamada geri kazanımayan nesneler, acil sanal öğeler olarak bilinir ve bir sonraki oluşturmaya yükseltilir:

- Nesil 0 atık toplamayı sürdüren nesneler 1. nesil olarak yükseltilir.
- 1. nesil atık toplamayı sürdüren nesneler 2. nesil olarak yükseltilir.
- 2. nesil atık toplamayı sürdüren nesneler 2. kuşak olarak kalır.

Çöp toplayıcı, bir kuşakma hızının yüksek olduğunu algıladığında, bu kuşak için ayırmaların eşiğini arttırır. Sonraki koleksiyon, geri kazanılan bellek miktarını önemli ölçüde alır. CLR sürekli olarak iki öncelik dengeler: bir uygulamanın çalışma kümesinin çöp toplamayı geciktirerek çok büyük bir şekilde geçmesine izin vermez ve çöp toplamanın çok sık çalışmasına izin vermez.

### <a name="ephemeral-generations-and-segments"></a>Kısa ömürlü Nesler ve segmentler

Nesil 0 ve 1 ' deki nesneler kısa süreli olduğundan, bu nesiller, kısa *ömürlü nesiller*olarak bilinir.

Kısa ömürlü nesiller, kısa ömürlü segment olarak bilinen bellek segmentinde ayrılır. Çöp toplayıcı tarafından alınan her yeni segment, yeni kısa ömürlü segment olur ve 0. nesil atık toplamayı izleyen nesneleri içerir. Eski kısa ömürlü segment, yeni nesil 2 segmentine dönüşür.

Kısa ömürlü segmentin boyutu sistemin 32 bit mi yoksa 64 bit mi olduğunu ve çalıştırdığı çöp toplayıcı türü ([Workstation veya Server GC](workstation-server-gc.md)) olmasına bağlı olarak değişir. Aşağıdaki tabloda, kısa ömürlü segmentin varsayılan boyutları gösterilmektedir.

|İş istasyonu/sunucu GC|32 bit|64 bit|
|-|-------------|-------------|
|İş istasyonu GC|16 MB|256 MB|
|Sunucu GC|64 MB|4 GB|
|> 4 mantıksal CPU içeren sunucu GC|32 MB|2 GB|
|> 8 mantıksal CPU 'Lar ile sunucu GC|16 MB|1 GB|

Kısa ömürlü segment 2. nesil nesneleri içerebilir. 2. nesil nesneler birden çok segment kullanabilir (işleminiz için gereken ve belleğin izin verdiği kadar).

Kısa ömürlü atık toplamanın serbest bırakılan bellek miktarı, kısa ömürlü segmentin boyutuyla sınırlıdır. Serbest bırakılan bellek miktarı, ölü nesneler tarafından kullanılan alanla orantılıdır.

## <a name="what-happens-during-a-garbage-collection"></a>Çöp toplama sırasında ne olur?

Bir çöp toplama işlemi aşağıdaki aşamaları içerir:

- Tüm canlı nesnelerin listesini bulan ve oluşturan bir işaretleme aşaması.

- Düzenlenecek nesneler için başvuruları güncelleştiren bir değiştirme aşaması.

- Yok sayılma nesnelerinin kapladığı alanı geri kazanır ve kalan nesneleri sıkıştırarak bir düzenleme aşaması. Sıkıştırma aşaması, bir atık toplamayı, segmentin eski ucuna doğru bir şekilde taşımış nesneleri hareket ettirir.

  2. nesil koleksiyonlar birden çok parçayı kaplayabildiğinden, 2. nesil olarak yükseltilen nesneler eski bir kesime taşınabilir. 2. nesil ve 2. nesil ve 2. nesil daha fazla VNet, 1. kuşak olarak yükseltildikleri için farklı bir kesime taşınabilir.

  Genellikle büyük nesne yığını (LOH) sıkıştırmaz, çünkü büyük nesneleri kopyalamak bir performans cezası uygular. Ancak, .NET Core 'da ve .NET Framework 4.5.1 ve üzeri sürümlerde, <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> büyük nesne yığınını isteğe bağlı olarak sıkıştırmak için özelliğini kullanabilirsiniz. Ayrıca, bir sabit sınır belirtildiğinde, LOH otomatik olarak sıkıştırılır:

  - Kapsayıcıda bir bellek sınırı.
  - [Gcheaphardlimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) veya [Gcheaphardlimit yüzdesi](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) çalışma zamanı yapılandırma seçenekleri.

Çöp toplayıcı, nesnelerin canlı olup olmadığını anlamak için aşağıdaki bilgileri kullanır:

- **Yığın kökleri**. Tam zamanında (JıT) derleyici ve yığın denetçisi tarafından sunulan yığın değişkenleri. JıT iyileştirmeleri, yığın değişkenlerinin çöp toplayıcısına bildirildiği kod bölgelerini uzatabilir veya kısaltabilir.

- **Çöp toplama tutamaçları**. Yönetilen nesneleri işaret eden ve Kullanıcı kodu veya ortak dil çalışma zamanı tarafından ayrılabilen işler.

- **Statik veriler**. Uygulama etki alanlarında diğer nesnelere başvurıbir statik nesneler. Her uygulama etki alanı, kendi statik nesnelerini izler.

Çöp toplama başlamadan önce, çöp toplamayı tetikleyen iş parçacığı hariç tüm yönetilen iş parçacıkları askıya alınır.

Aşağıdaki çizimde, çöp toplamayı tetikleyen ve diğer iş parçacıklarının askıya alınmasına neden olan bir iş parçacığı gösterilmektedir.

![Bir iş parçacığı bir çöp toplama işlemi tetiklerse](media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Yönetilmeyen kaynaklar

Uygulamanızın oluşturduğu nesnelerin çoğu için, gerekli bellek yönetimi görevlerini otomatik olarak gerçekleştirmek üzere çöp toplamaya güvenebilirsiniz. Ancak, yönetilmeyen kaynakların açıkça temizlenmesi gerekir. Yönetilmeyen kaynakların en yaygın türü, bir dosya işleyicisi, pencere işleyicisi veya ağ bağlantısı gibi işletim sistemi kaynağını sarmalayan bir nesnedir. Çöp toplayıcı yönetilmeyen bir kaynağı sarmalayan yönetilen bir nesnenin ömrünü takip edebilse de, kaynağın nasıl temizleyilerek ilgili belirli bir bilgiye sahip değildir.

Yönetilmeyen bir kaynağı sarmalayan bir nesne oluşturduğunuzda, bir genel yöntemde yönetilmeyen kaynağı temizlemek için gerekli kodu sağlamanız önerilir `Dispose` . Bir yöntemi sunarak `Dispose` , nesnenizin kullanıcılarına, nesne ile işiniz bittiğinde belleği açık bir şekilde boşaltmaya olanak sağlayabilirsiniz. Yönetilmeyen bir kaynağı sarmalayan bir nesne kullandığınızda, gereken şekilde çağırdığınızdan emin olun `Dispose` .

Ayrıca, bir tür tüketicisinin çağrısını unutması durumunda, yönetilmeyen kaynaklarınızın serbest bırakılması için bir yol sağlamalısınız `Dispose` . Yönetilmeyen kaynağı kaydırmak veya yöntemi geçersiz kılmak için güvenli bir tanıtıcı kullanabilirsiniz <xref:System.Object.Finalize?displayProperty=nameWithType> .

Yönetilmeyen kaynakları temizleme hakkında daha fazla bilgi için bkz. [yönetilmeyen kaynakları temizleme](unmanaged.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İş istasyonu ve sunucu atık toplama](workstation-server-gc.md)
- [Arka plan atık toplama](background-gc.md)
- [GC için yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
- [Atık toplama](index.md)
