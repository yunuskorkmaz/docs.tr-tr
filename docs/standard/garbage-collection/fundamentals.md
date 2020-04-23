---
title: Çöp toplamanın temelleri
description: Çöp toplayıcısının nasıl çalıştığını ve optimum performans için nasıl yapılandırılabildiğini öğrenin.
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
ms.openlocfilehash: 1fdf7fcd61fb4bf9e8e0cbfe28842208f6eadd00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102443"
---
# <a name="fundamentals-of-garbage-collection"></a>Çöp toplamanın temelleri

Ortak dil çalışma süresi (CLR) olarak, çöp toplayıcı (GC) otomatik bellek yöneticisi olarak hizmet vermektedir. Çöp toplayıcı, bir uygulama için bellek tahsisini ve serbest bırakılmasını yönetir. Yönetilen kodla çalışan geliştiriciler için bu, bellek yönetimi görevlerini gerçekleştirmek için kod yazmanız gerekolmadığı anlamına gelir. Otomatik bellek yönetimi, bir nesneyi serbest etmeyi unutma ve bellek sızıntısına neden olmak veya zaten serbest bırakılmış bir nesnenin belleğe erişmeye çalışması gibi sık karşılaşılan sorunları ortadan kaldırabilir.

Bu makalede, çöp toplama temel kavramları açıklanmaktadır.

## <a name="benefits"></a>Avantajlar

Çöp toplayıcı aşağıdaki avantajları sağlar:

- Geliştiricileri belleği el ile serbest bırakmak zorunda kalmaktan kurtarır.

- Yönetilen yığındaki nesneleri verimli bir şekilde ayırır.

- Artık kullanılmayan nesneleri geri alır, belleklerini temizler ve belleği gelecekteki ayırmalar için kullanılabilir tutar. Yönetilen nesneler, oluşturmakta olan ların her veri alanını başlatmak zorunda kalmaması için otomatik olarak temiz içerik alır.

- Bir nesnenin başka bir nesnenin içeriğini kullanamayacağından emin olarak bellek güvenliği sağlar.

## <a name="fundamentals-of-memory"></a>Belleğin temelleri

Aşağıdaki liste önemli CLR bellek kavramlarını özetleyilmektedir.

- Her işlemin kendine ait, ayrı bir sanal adres alanı vardır. Varsa, aynı bilgisayardaki tüm işlemler aynı fiziksel belleği ve sayfa dosyasını paylaşır.

- Varsayılan olarak, 32 bit bilgisayarlarda her işlemin 2 GB kullanıcı modu sanal adres alanı vardır.

- Bir uygulama geliştiricisi olarak, yalnızca sanal adres alanıyla çalışırsınız ve fiziksel belleği asla doğrudan işlemezsiniz. Çöp toplayıcı, yönetilen yığında sanal belleği sizin için ayırır ve serbest hale getirdi.

  Yerel kod yazıyorsanız, sanal adres alanıyla çalışmak için Windows işlevlerini kullanırsınız. Bu işlevler, yerel yığınlar üzerinde sizin için tahsis ve ücretsiz sanal bellek.

- Sanal bellek üç durumda olabilir:

  | Durum | Açıklama |
  |---------|---------|
  | Ücretsiz | Bellek bloğunun ona atıfta bulunulması yoktur ve ayırma için kullanılabilir. |
  | Ayrıldı | Bellek bloğu kullanımınız için kullanılabilir ve başka bir ayırma isteği için kullanılamaz. Ancak, işlenene kadar verileri bu bellek bloğuna depolayamazsınız. |
  | Yürütülen | Bellek bloğu fiziksel depolamaya atanır. |

- Sanal adres alanı parçalanmış alabilirsiniz. Bu, adres alanında delik olarak da bilinen boş bloklar olduğu anlamına gelir. Sanal bellek ayırma isteği istendiğinde, sanal bellek yöneticisinin bu ayırma isteğini karşılayacak kadar büyük tek bir boş blok bulması vardır. 2 GB boş alanınız olsa bile, tüm bu boş alan tek bir adres bloğunda olmadığı sürece 2 GB gerektiren bir ayırma başarısız olur.

- Ayırmak için yeterli sanal adres alanı veya bağlanmak için fiziksel alan yoksa, bellek tükenebilir.

  Fiziksel bellek basıncı (diğer bir süre önce fiziksel bellek talebi) düşük olsa bile sayfa dosyası kullanılır. Fiziksel bellek basıncı ilk kez yüksek olduğunda, işletim sistemi verileri depolamak için fiziksel bellekte yer açmak zorundadır ve sayfa dosyasına fiziksel bellekte olan bazı verileri yedekler. Bu veriler ihtiyaç duyulana kadar çağrılmamalıdır, bu nedenle fiziksel bellek basıncının düşük olduğu durumlarda çağrılama ile karşılaşmak mümkündür.
  
### <a name="memory-allocation"></a>Bellek ayırma

Yeni bir işlem başlattığınızda, çalışma zamanı işlem için adres bölgesine bitişik bir adres alanı ayırır. Bu ayrılmış adres alanına yönetilen yığın denir. Yönetilen yığın, yığın içinde sıradaki nesnenin nereye ayrılacağını belirten bir işaretçi tutar. Başlangıçta, bu işaretçi yönetilen yığının taban adresi olarak ayarlanır. Tüm başvuru türleri yönetilen yığına ayrılır. Bir uygulama ilk referans türünü oluşturduğunda, türe yönelik bellek, yönetilen yığının taban adresinde ayrılır. Uygulama bir sonraki nesneyi oluşturduğunda, atık toplayıcı bunun için ilk nesnenin hemen ardındaki adres alanında bellek ayırır. Kullanılabilir adres alanı olduğu sürece, atık toplayıcı yeni nesnelere bu şekilde bellek ayırmaya devam eder.

Yönetilen yığından bellek ayırmak, yönetilmeyen bellek ayrımından daha hızlıdır. Çalışma zamanı, işaretçiye değer ekleyerek bir nesne için bellek ayırdığından, neredeyse yığından bellek ayırmak kadar hızlıdır. Ayrıca, ardışık olarak ayrılan yeni nesneler yönetilen yığında bitişik olarak depolandığı için, uygulama nesnelere hızlı bir şekilde erişebilir.

### <a name="memory-release"></a>Bellek sürümü

Atık toplayıcısının optimizasyon altyapısı, yapılan ayrımlara göre bir toplama işlemini gerçekleştirmek için en iyi zamanı belirler. Atık toplayıcı bir toplama gerçekleştirdiğinde, uygulama tarafından artık kullanılmayan nesnelere ayrılan belleği serbest bırakır. Uygulamanın *köklerini*inceleyerek hangi nesnelerin artık kullanılmadığını belirler. Bir uygulamanın kökleri statik alanları, yerel değişkenleri ve parametreleri bir iş parçacığı yığınında içerir ve CPU kayıtları. Her kök yönetilen yığındaki bir nesneye başvurur veya null olarak ayarlanır. Çöp toplayıcı, tam zamanında (JIT) derleyicisinin ve çalışma zamanının koruduğu etkin kökler listesine erişebilir. Bu listeyi kullanarak, çöp toplayıcı köklerden erişilebilen tüm nesneleri içeren bir grafik oluşturur.

Grafta bulunmayan nesnelere uygulamanın köklerinden ulaşılamaz. Çöp toplayıcı, erişileemeyen nesneleri çöp olarak kabul eder ve onlar için ayrılan belleği salar. Bir toplama sırasında, atık toplayıcı yönetilen yığını inceleyerek erişilemeyen nesneler tarafından kullanılan adres alanı bloklarını arar. Erişilemeyen nesneleri keşfettikçe, bir bellek kopyalama işleviyle bellekteki erişilebilir nesneleri sıkıştırır ve bu sayede, erişilemeyen nesnelere ayrılan adres alanlarını serbest bırakır. Erişilebilir nesneler için bellek sıkıştırıldıktan sonra atık toplayıcı gerekli işaretçi düzeltmelerini yaparak uygulamanın köklerinin nesnelerin yeni konumlarına işaret etmesini sağlar. Ayrıca yönetilen yığının işaretçisini erişilebilen son nesnenin sonuna konumlandırır.

Bellek, yalnızca bir koleksiyon önemli sayıda erişilemez nesne keşfederse sıkıştırılır. Yönetilen bellekteki tüm nesneler bir toplamadan sonra kalmaya devam ederse, bellek sıkıştırmaya gerek yoktur.

Performansı artırmak açısından, çalışma zamanı büyük nesneler için ayrı bir yığında bellek ayırır. Atık toplayıcı, büyük nesnelerin belleğini otomatik olarak serbest bırakır. Ancak, bellekte büyük nesneleri hareket ettirmeyi önlemek için, bu bellek genellikle sıkıştırılmış değildir.

## <a name="conditions-for-a-garbage-collection"></a>Çöp toplama koşulları

Çöp toplama, aşağıdaki koşullardan biri doğru olduğunda oluşur:

- Sistemin fiziksel hafızası düşük. Bu, işletim sistemi düşük bellek bildirimi veya ana bilgisayar tarafından belirtildiği gibi düşük bellek tarafından algılanır.

- Yönetilen yığında ayrılan nesneler tarafından kullanılan bellek kabul edilebilir bir eşiği aşar. İşlem çalışırken bu eşik sürekli olarak ayarlanır.

- Yöntem <xref:System.GC.Collect%2A?displayProperty=nameWithType> denir. Çöp toplayıcı sürekli çalıştığından, hemen hemen her durumda bu yöntemi aramanız gerekmez. Bu yöntem öncelikle benzersiz durumlar ve sınama için kullanılır.

## <a name="the-managed-heap"></a>Yönetilen yığın

Çöp toplayıcıclr tarafından başharfe döndürülmeden sonra, nesneleri depolamak ve yönetmek için bellek bir segment ayırır. Bu bellek, işletim sistemindeki yerel yığın yerine yönetilen yığın olarak adlandırılır.

Yönetilen her işlem için yönetilen bir yığın vardır. İşlemdeki tüm iş parçacıkları, aynı yığındaki nesneler için bellek ayırır.

Bellek ayırmak için, çöp toplayıcı Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) işlevini çağırır ve yönetilen uygulamalar için bir defada bir bellek kesimi ayırır. Çöp toplayıcı sıyrık olarak segmentleri de ayırır ve Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) işlevini arayarak segmentleri işletim sistemine (herhangi bir nesneyi temizledikten sonra) geri salar.

> [!IMPORTANT]
> Çöp toplayıcıtarafından ayrılan segmentlerin boyutu uygulamaya özgüdür ve periyodik güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişebilir. Uygulamanız hiçbir zaman belirli bir segment boyutu hakkında varsayımlarda bulunmamalı veya belirli bir segment boyutuna bağlı kalmamalı ve segment ayırmaları için kullanılabilir bellek miktarını yapılandırmaya çalışmamalıdır.

Yığına ne kadar az nesne ayrılırsa, çöp toplayıcının yapması gereken o kadar az iş vardır. Nesneleri ayırırken, yalnızca 15 bayt alabilmeniz gerektiğinde 32 baytlık bir dizi ayırma gibi ihtiyaçlarınızı aşan yuvarlatılmış değerler kullanmayın.

Bir çöp toplama tetiklendiğinde, çöp toplayıcı ölü nesneler tarafından işgal edilen belleği geri alır. Geri alma işlemi canlı nesneleri bir araya getirerek sıkıştırıyor ve ölü alan kaldırılarak yığın küçültülüyor. Bu, birlikte ayrılan nesnelerin yerelliklerini korumak için yönetilen yığında bir arada kalmasını sağlar.

Çöp koleksiyonlarının müdahaleciliği (sıklık ve süre), ayırma hacminin ve yönetilen yığındaki hayatta kalan bellek miktarının bir sonucudur.

Yığın iki yığın birikimi olarak kabul edilebilir: [büyük nesne yığını](large-object-heap.md) ve küçük nesne yığını. Büyük nesne yığını, genellikle diziolan 85.000 bayt ve daha büyük nesneler içerir. Bir örnek nesnenin son derece büyük olması nadirdir.

> [!TIP]
> Nesnelerin büyük nesne yığınına gitmesi için [eşik boyutunu yapılandırabilirsiniz.](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold)

## <a name="generations"></a>Nesil

GC algoritması çeşitli hususlara dayanmaktadır:

- Yönetilen yığının bir kısmı için belleği sıkıştırmak, yönetilen yığının tamamına göre daha hızlıdır.
- Yeni nesnelerin daha kısa kullanım ömürleri ve eski nesnelerin ömürleri daha uzundur.
- Yeni nesneler birbiriyle ilişkili olma eğilimindedir ve uygulama tarafından aynı anda erişilir.

Çöp toplama öncelikle kısa ömürlü nesnelerin ıslahı ile oluşur. Çöp toplayıcısının performansını optimize etmek için yönetilen yığın, uzun ömürlü ve kısa ömürlü nesneleri ayrı ayrı işleyebilmek için 0, 1 ve 2 olmak üzere üç nesle ayrılır. Çöp toplayıcı, yeni nesneleri nesil 0'da depolar. Uygulama ömrünün başlarında oluşturulan ve toplamalardan sonra varlığını sürdüren nesneler yükseltilerek nesil 1 ve 2'de tutulur. Yönetilen yığının bir kısmını sıkıştırmak tüm yığından daha hızlı olduğundan, bu şema çöp toplayıcısının bir koleksiyonu her gerçekleştiriğinde yönetilen yığının tamamının belleği serbest bırakmak yerine belleği belirli bir nesilde serbest bırakmasına olanak tanır.

- **Nesil 0**. Bu en genç nesil ve kısa ömürlü nesneler içerir. Kısa ömürlü bir nesneörneği geçici bir değişkendir. Çöp toplama en sık bu nesilde oluşur.

  Yeni ayrılan nesneler yeni nesil nesneler oluşturur ve örtülü olarak nesil 0 koleksiyonlarıdır. Ancak, büyük nesnelerse, bir nesil 2 koleksiyonunda büyük nesne yığınına giderler.

  Çoğu nesne nesil 0 çöp toplama için geri alınır ve bir sonraki nesil için hayatta değildir.
  
  Bir uygulama nesil 0 dolduğunda yeni bir nesne oluşturmaya çalışırsa, çöp toplayıcı nesne için adres alanı boşaltmak için bir koleksiyon gerçekleştirir. Atık toplayıcı, yönetilen yığındaki tüm nesneler yerine nesil 0'daki nesneleri inceleyerek başlar. Yalnızca nesil 0 koleksiyonu genellikle uygulamanın yeni nesneler oluşturmaya devam etmesini sağlamak için yeterli belleği geri alır.

- **Nesil 1**. Bu nesil kısa ömürlü nesneler içerir ve kısa ömürlü nesneler ve uzun ömürlü nesneler arasında bir arabellek olarak hizmet vermektedir.

  Çöp toplayıcı nesil 0 koleksiyonunu yaptıktan sonra, erişilebilen nesnelerin belleği sıkıştırır ve bunları nesil 1'e yükseltir. Toplama işleminden sonra varlığını sürdüren nesneler daha uzun ömre sahip olmaya eğilimli olduklarından, bunları daha yüksek bir nesle yükseltmek mantıklıdır. Çöp toplayıcı, nesil 0'dan oluşan bir koleksiyon gerçekleştirdiğinde nesneleri nesiller 1 ve 2'de yeniden incelemek zorunda değildir.
  
  Nesil 0 koleksiyonu, uygulamanın yeni bir nesne oluşturması için yeterli belleği geri alamıyorsa, çöp toplayıcı nesil 1, sonra nesil 2'den oluşan bir koleksiyon gerçekleştirebilir. Nesil 1'de toplama işlemlerinden sonra varlığına devam eden nesneler nesil 2'ye yükselir.

- **Nesil 2**. Bu nesil uzun ömürlü nesneler içerir. Uzun ömürlü bir nesnenin bir örneği, bir sunucu uygulamasında işlem süresince canlı statik veri içeren bir nesnedir.

  Bir koleksiyondan kurtulan 2.

Çöp toplama koşulları gerektirdiği gibi belirli nesillerde oluşur. Bir nesil toplamak, o nesildeki ve tüm genç nesildeki nesneleri toplamak anlamına gelir. Bir nesil 2 çöp toplama da tam bir çöp toplama olarak bilinir, çünkü tüm nesillernesneleri geri alır (yani, yönetilen yığıntüm nesneler).

### <a name="survival-and-promotions"></a>Hayatta kalma ve promosyonlar

Çöp toplamada geri alınmayan nesneler kurtulanlar olarak bilinir ve bir sonraki nesle yükseltilir:

- Bir nesil 0 çöp toplama hayatta nesneler nesil 1 yükseltilir.
- Bir nesil 1 çöp toplama hayatta nesneler nesil 2 yükseltilir.
- Bir nesil 2 çöp toplama hayatta nesneler nesil 2 kalır.

Çöp toplayıcı, bir nesilde hayatta kalma oranının yüksek olduğunu algıladığında, o nesil için ayırma eşiğini artırır. Bir sonraki koleksiyon, geri kazanılmış bellek önemli bir boyut alır. CLR sürekli olarak iki önceliği dengeler: çöp toplamayı geciktirerek bir uygulamanın çalışma kümesinin çok büyük büyümesine izin vermemek ve çöp toplamanın çok sık çalışmasına izin vermemek.

### <a name="ephemeral-generations-and-segments"></a>Geçici nesiller ve segmentler

0 ve 1. *ephemeral generations*

Geçici nesiller, geçici kesim olarak bilinen bellek segmentinde ayrılır. Çöp toplayıcıtarafından edinilen her yeni segment yeni geçici segment olur ve bir nesil 0 çöp toplama hayatta nesneleri içerir. Eski geçici segment yeni nesil 2 segment olur.

Geçici segmentin boyutu, bir sistemin 32 bit veya 64 bit olup olmadığına ve çalıştığı çöp toplayıcının türüne[(iş istasyonu veya sunucu GC)](workstation-server-gc.md)bağlı olarak değişir. Aşağıdaki tablo, geçici kesimin varsayılan boyutlarını gösterir.

|İş istasyonu/sunucu GC|32 bit|64 bit|
|-|-------------|-------------|
|İş istasyonu GC|16mb|256mb|
|Sunucu GC|64 MB|4 GB|
|> 4 mantıksal CPU'su ile Sunucu GC|32mb|2 GB|
|8 mantıksal CPU'> sunucu GC|16mb|1 GB|

Geçici kesim nesil 2 nesneleri içerebilir. Nesil 2 nesneleri birden çok segment kullanabilir (işleminizin gerektirdiği ve belleğin izin verdiği kadar).

Geçici bir çöp koleksiyonundan serbest bırakılan bellek miktarı, geçici kesimin boyutuyla sınırlıdır. Serbest bırakılan bellek miktarı, ölü cisimlerin işgal ettiği alanla orantılıdır.

## <a name="what-happens-during-a-garbage-collection"></a>Çöp toplama sırasında ne olur?

Çöp toplama nın aşağıdaki aşamaları vardır:

- Tüm canlı nesnelerin listesini bulan ve oluşturan bir işaretleme aşaması.

- Sıkıştırılacak nesnelere yapılan başvuruları güncelleyen bir taşınma aşaması.

- Ölü nesnelerin işgal ettiği alanı geri alan ve hayatta kalan nesneleri sıkıştıran sıkıştırma aşaması. Sıkıştırma aşaması, çöp toplamadan kurtulan nesneleri segmentin eski ucuna taşır.

  Nesil 2 koleksiyonları birden çok kesimi kaplayabildiği için, nesil 2'ye yükseltilen nesneler eski bir segmente taşınabilir. Hem nesil 1 hem de nesil 2 hayatta kalanlar farklı bir segmente taşınabilir, çünkü nesil 2'ye terfi ederler.

  Normalde, büyük nesne yığını (LOH) sıkıştırılmış değildir, çünkü büyük nesneleri kopyalamak bir performans cezası uygular. Ancak, .NET Core'da ve .NET Framework 4.5.1 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> ve sonraki durumlarda, isteğe bağlı büyük nesne yığınını sıkıştırmak için özelliği kullanabilirsiniz. Buna ek olarak, loh otomatik olarak bir sabit sınır ya belirterek ayarlanır sıkıştırılır:

  - Bir kapsayıcıda bellek sınırı.
  - [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) veya [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) çalışma zamanı yapılandırma seçenekleri.

Çöp toplayıcı, nesnelerin canlı olup olmadığını belirlemek için aşağıdaki bilgileri kullanır:

- **Yığın kökleri**. Tam zamanında (JIT) derleyici ve yığın yürütücüsü tarafından sağlanan değişkenleri yığın. JIT optimizasyonları, yığın değişkenlerinin çöp toplayıcıya raporedildiği kod bölgelerini uzatabilir veya kısaltabilir.

- **Çöp toplama tutamaçları.** Yönetilen nesnelere işaret eden ve kullanıcı kodu veya ortak dil çalışma süresi tarafından tahsis edilebilen işler.

- **Statik veriler**. Diğer nesnelere başvuruyor olabilecek uygulama etki alanlarındaki statik nesneler. Her uygulama etki alanı statik nesnelerini izler.

Çöp toplama başlamadan önce, çöp toplamayı tetikleyen iş parçacığı dışında tüm yönetilen iş parçacıkları askıya alınır.

Aşağıdaki resimde, çöp toplamayı tetikleyen ve diğer iş parçacıklarının askıya alınmasına neden olan bir iş parçacığı gösterilmektedir.

![Bir iş parçacığı Çöp Toplama'yı tetiklediğinde](./media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Yönetilmeyen kaynaklar

Uygulamanızın oluşturduğu nesnelerin çoğu için, gerekli bellek yönetimi görevlerini otomatik olarak gerçekleştirmek için çöp toplama'ya güvenebilirsiniz. Ancak, yönetilmeyen kaynakların açıkça temizlenmesi gerekir. Yönetilmeyen kaynakların en yaygın türü, bir dosya işleyicisi, pencere işleyicisi veya ağ bağlantısı gibi işletim sistemi kaynağını sarmalayan bir nesnedir. Çöp toplayıcı, yönetilmeyen bir kaynağı kapsülleyen yönetilen bir nesnenin kullanım ömrünü izleyebilse de, kaynağın nasıl temizleyeceği hakkında özel bir bilgiye sahip değildir.

Yönetilmeyen bir kaynağı kapsülleyen bir nesne oluşturduğunuzda, genel `Dispose` bir yöntemde yönetilmeyen kaynağı temizlemek için gerekli kodu sağlamanız önerilir. Bir `Dispose` yöntem sağlayarak, nesnenizin kullanıcılarının nesneyle işi bittiğinde belleği açıkça serbest etmelerini sağlarsınız. Yönetilmeyen bir kaynağı kapsülleyen bir nesne kullandığınızda, gerektiği `Dispose` gibi aradığından emin olun.

Ayrıca, türünüzdeki bir tüketicinin aramayı `Dispose`unutması durumunda, yönetilmeyen kaynaklarınızın serbest bırakılması için bir yol da sağlamalısınız. Yönetilmeyen kaynağı sarmak veya <xref:System.Object.Finalize?displayProperty=nameWithType> yöntemi geçersiz kılmak için güvenli bir tanıtıcı kullanabilirsiniz.

Yönetilmeyen kaynakları temizleme hakkında daha fazla bilgi için [bkz.](unmanaged.md)

## <a name="see-also"></a>Ayrıca bkz.

- [İş istasyonu ve sunucu çöp toplama](workstation-server-gc.md)
- [Arka plan çöp toplama](background-gc.md)
- [GC için yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
- [Atık toplama](index.md)
