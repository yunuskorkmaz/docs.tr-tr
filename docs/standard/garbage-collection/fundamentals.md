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
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400542"
---
# <a name="fundamentals-of-garbage-collection"></a>Çöp toplamanın temelleri

Ortak dil çalışma süresi (CLR) olarak, çöp toplayıcı (GC) otomatik bellek yöneticisi olarak hizmet vermektedir. Aşağıdaki yararları sağlar:

- Belleği el ile boşaltmak zorunda kalmadan uygulamanızı geliştirmenizi sağlar.

- Yönetilen yığındaki nesneleri verimli bir şekilde ayırır.

- Artık kullanılmayan nesneleri geri alır, belleklerini temizler ve belleği gelecekteki ayırmalar için kullanılabilir tutar. Yönetilen nesneler otomatik olarak temiz içerik ile başlamak için olsun, böylece onların yapıcıları her veri alanı başlatmak zorunda kalmaz.

- Bir nesnenin başka bir nesnenin içeriğini kullanamayacağından emin olarak bellek güvenliği sağlar.

Bu makalede, çöp toplama temel kavramları açıklanmaktadır.

## <a name="fundamentals-of-memory"></a>Belleğin temelleri

Aşağıdaki liste önemli CLR bellek kavramlarını özetleyilmektedir.

- Her işlemin kendine ait, ayrı bir sanal adres alanı vardır. Varsa, aynı bilgisayardaki tüm işlemler aynı fiziksel belleği ve sayfa dosyasını paylaşır.

- Varsayılan olarak, 32 bit bilgisayarlarda her işlemin 2 GB kullanıcı modu sanal adres alanı vardır.

- Bir uygulama geliştiricisi olarak, yalnızca sanal adres alanıyla çalışırsınız ve fiziksel belleği asla doğrudan işlemezsiniz. Çöp toplayıcı, yönetilen yığında sanal belleği sizin için ayırır ve serbest hale getirdi.

  Yerel kod yazıyorsanız, sanal adres alanıyla çalışmak için Windows işlevlerini kullanırsınız. Bu işlevler, yerel yığınlar üzerinde sizin için tahsis ve ücretsiz sanal bellek.

- Sanal bellek üç durumda olabilir:

  - Ücret -siz. Bellek bloğunun ona atıfta bulunulması yoktur ve ayırma için kullanılabilir.

  - Ayrılmış. Bellek bloğu kullanımınız için kullanılabilir ve başka bir ayırma isteği için kullanılamaz. Ancak, işlenene kadar verileri bu bellek bloğuna depolayamazsınız.

  - Kaydedilmiş. Bellek bloğu fiziksel depolamaya atanır.

- Sanal adres alanı parçalanmış alabilirsiniz. Bu, adres alanında delik olarak da bilinen boş bloklar olduğu anlamına gelir. Sanal bellek ayırma isteği istendiğinde, sanal bellek yöneticisinin bu ayırma isteğini karşılayacak kadar büyük tek bir boş blok bulması vardır. 2 GB boş alanınız olsa bile, tüm bu boş alan tek bir adres bloğunda olmadığı sürece 2 GB gerektiren ayırma başarısız olur.

- Ayırmak için yeterli sanal adres alanı veya bağlanmak için fiziksel alan yoksa, bellek tükenebilir.

  Fiziksel bellek basıncı (diğer bir süre önce fiziksel bellek talebi) düşük olsa bile sayfa dosyası kullanılır. Fiziksel bellek basıncı ilk kez yüksek olduğunda, işletim sistemi verileri depolamak için fiziksel bellekte yer açmak zorundadır ve sayfa dosyasına fiziksel bellekte olan bazı verileri yedekler. Bu veriler ihtiyaç duyulana kadar çağrılmamalıdır, bu nedenle fiziksel bellek basıncının düşük olduğu durumlarda çağrılama ile karşılaşmak mümkündür.

## <a name="conditions-for-a-garbage-collection"></a>Çöp toplama koşulları

Çöp toplama, aşağıdaki koşullardan biri doğru olduğunda oluşur:

- Sistemin fiziksel hafızası düşük. Bu, işletim sistemi düşük bellek bildirimi veya ana bilgisayar tarafından belirtildiği gibi düşük bellek tarafından algılanır.

- Yönetilen yığında ayrılan nesneler tarafından kullanılan bellek kabul edilebilir bir eşiği aşar. İşlem çalışırken bu eşik sürekli olarak ayarlanır.

- Yöntem <xref:System.GC.Collect%2A?displayProperty=nameWithType> denir. Çöp toplayıcı sürekli çalıştığından, hemen hemen her durumda bu yöntemi aramak zorunda kalmamalısınız. Bu yöntem öncelikle benzersiz durumlar ve sınama için kullanılır.

## <a name="the-managed-heap"></a>Yönetilen yığın

Çöp toplayıcıclr tarafından başharfe döndürülmeden sonra, nesneleri depolamak ve yönetmek için bellek bir segment ayırır. Bu bellek, işletim sistemindeki yerel yığın yerine yönetilen yığın olarak adlandırılır.

Yönetilen her işlem için yönetilen bir yığın vardır. İşlemdeki tüm iş parçacıkları, aynı yığındaki nesneler için bellek ayırır.

Bellek ayırmak için, çöp toplayıcı Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) işlevini çağırır ve yönetilen uygulamalar için bir defada bir bellek kesimi ayırır. Çöp toplayıcı sıyrık olarak segmentleri de ayırır ve Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) işlevini arayarak segmentleri işletim sistemine (herhangi bir nesneyi temizledikten sonra) geri salar.

> [!IMPORTANT]
> Çöp toplayıcıtarafından ayrılan segmentlerin boyutu uygulamaya özgüdür ve periyodik güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişebilir. Uygulamanız hiçbir zaman belirli bir segment boyutu hakkında varsayımlarda bulunmamalı veya belirli bir segment boyutuna bağlı kalmamalı ve segment ayırmaları için kullanılabilir bellek miktarını yapılandırmaya çalışmamalıdır.

Yığına ne kadar az nesne ayrılırsa, çöp toplayıcının yapması gereken o kadar az iş vardır. Nesneleri ayırdığınızda, yalnızca 15 bayt alabilmeniz gerektiğinde 32 baytlık bir dizi ayırma gibi gereksinimlerinizi aşan yuvarlatılmış değerler kullanmayın.

Bir çöp toplama tetiklendiğinde, çöp toplayıcı ölü nesneler tarafından işgal edilen belleği geri alır. Geri alma işlemi canlı nesneleri bir araya getirerek sıkıştırıyor ve ölü alan kaldırılarak yığın küçültülüyor. Bu, birlikte ayrılan nesnelerin yerelliklerini korumak için yönetilen yığında birlikte kalmalarını sağlar.

Çöp koleksiyonlarının müdahaleciliği (sıklık ve süre), ayırma hacminin ve yönetilen yığındaki hayatta kalan bellek miktarının bir sonucudur.

Yığın iki yığın birikimi olarak kabul edilebilir: [büyük nesne yığını](large-object-heap.md) ve küçük nesne yığını.

[Büyük nesne yığını](large-object-heap.md) 85.000 bayt ve daha büyük çok büyük nesneler içerir. Büyük nesne yığınındaki nesneler genellikle dizilerdir. Bir örnek nesnenin son derece büyük olması nadirdir.

> [!TIP]
> Nesnelerin büyük nesne yığınına gitmesi için [eşik boyutunu yapılandırabilirsiniz.](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold)

## <a name="generations"></a>Nesil

Yığın nesiller halinde düzenlenir, böylece uzun ömürlü ve kısa ömürlü nesneleri işleyebilir. Çöp toplama, öncelikle genellikle yığının yalnızca küçük bir bölümünü kaplayan kısa ömürlü nesnelerin ıslahı ile oluşur. Yığında üç nesil dir.

- **Nesil 0**. Bu en genç nesil ve kısa ömürlü nesneler içerir. Kısa ömürlü bir nesneörneği geçici bir değişkendir. Çöp toplama en sık bu nesilde oluşur.

  Yeni ayrılan nesneler yeni nesil nesneler oluşturur ve örtülü olarak nesil 0 koleksiyonlarıdır. Ancak, büyük nesnelerse, bir nesil 2 koleksiyonunda büyük nesne yığınına giderler.

  Çoğu nesne nesil 0 çöp toplama için geri alınır ve bir sonraki nesil için hayatta değildir.

- **Nesil 1**. Bu nesil kısa ömürlü nesneler içerir ve kısa ömürlü nesneler ve uzun ömürlü nesneler arasında bir arabellek olarak hizmet vermektedir.

- **Nesil 2**. Bu nesil uzun ömürlü nesneler içerir. Uzun ömürlü bir nesnenin bir örneği, bir sunucu uygulamasında işlem süresince canlı statik veri içeren bir nesnedir.

Çöp toplama koşulları gerektirdiği gibi belirli nesillerde oluşur. Bir nesil toplamak, o nesildeki ve tüm genç nesildeki nesneleri toplamak anlamına gelir. Bir nesil 2 çöp toplama da tam bir çöp toplama olarak bilinir, çünkü tüm nesiller (yani yönetilen yığındaki tüm nesneleri) tüm nesneleri geri alır.

### <a name="survival-and-promotions"></a>Hayatta kalma ve promosyonlar

Çöp toplamada geri alınmayan nesneler kurtulanlar olarak bilinir ve bir sonraki nesle yükseltilir. Bir nesil 0 çöp toplama hayatta nesneler nesil 1 yükseltilir; bir nesil 1 çöp toplama hayatta nesneler nesil 2 yükseltilir; ve bir nesil 2 çöp toplama hayatta nesneler nesil 2 kalır.

Çöp toplayıcı, bir nesilde hayatta kalma oranının yüksek olduğunu algıladığında, o nesil için ayırma eşiğini artırır. Bir sonraki koleksiyon, geri kazanılmış bellek önemli bir boyut alır. CLR sürekli olarak iki önceliği dengeler: çöp toplamayı geciktirerek bir uygulamanın çalışma kümesinin çok büyük büyümesine izin vermemek ve çöp toplamanın çok sık çalışmasına izin vermemek.

### <a name="ephemeral-generations-and-segments"></a>Geçici nesiller ve segmentler

0 ve 1 kuşaklarında nesneler kısa ömürlü olduğundan, bu nesiller geçici nesiller olarak bilinir.

Geçici nesiller, geçici kesim olarak bilinen bellek segmentine ayrılmalıdır. Çöp toplayıcıtarafından edinilen her yeni segment yeni geçici segment olur ve bir nesil 0 çöp toplama hayatta nesneleri içerir. Eski geçici segment yeni nesil 2 segment olur.

Geçici kesimin boyutu, sistemin 32 bit veya 64 bit olup olmadığına ve çalıştığı çöp toplayıcının türüne bağlı olarak değişir. Varsayılan değerler aşağıdaki tabloda gösterilmiştir.

||32 bit|64 bit|
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

  - bir kapsayıcıda bir bellek sınırı veya
  - [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) veya [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) çalışma zamanı yapılandırma seçenekleri

Çöp toplayıcı, nesnelerin canlı olup olmadığını belirlemek için aşağıdaki bilgileri kullanır:

- **Yığın kökleri**. Tam zamanında (JIT) derleyici ve yığın yürütücüsü tarafından sağlanan değişkenleri yığın. JIT optimizasyonları, yığın değişkenlerinin çöp toplayıcıya raporedildiği kod bölgelerini uzatabilir veya kısaltabilir.

- **Çöp toplama tutamaçları.** Yönetilen nesnelere işaret eden ve kullanıcı kodu veya ortak dil çalışma süresi tarafından tahsis edilebilen işler.

- **Statik veriler**. Diğer nesnelere başvuruyor olabilecek uygulama etki alanlarındaki statik nesneler. Her uygulama etki alanı statik nesnelerini izler.

Çöp toplama başlamadan önce, çöp toplamayı tetikleyen iş parçacığı dışında tüm yönetilen iş parçacıkları askıya alınır.

Aşağıdaki resimde, çöp toplamayı tetikleyen ve diğer iş parçacıklarının askıya alınmasına neden olan bir iş parçacığı gösterilmektedir.

![Bir iş parçacığı Çöp Toplama'yı tetiklediğinde](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Yönetilmeyen kaynakları işleme

Yönetilen nesneler yerel dosya tanıtıcılarını kullanarak yönetilmeyen nesnelere başvuruyorsa, çöp toplayıcı yalnızca yönetilen yığındaki belleği izlediğinden, yönetilmeyen nesneleri açıkça serbest toplamanız gerekir.

Yönetilen nesnenin kullanıcıları, nesne tarafından kullanılan yerel kaynakları elden çıkarmayabilir. Temizleme gerçekleştirmek için yönetilen nesneyi sonlanabilir yapabilirsiniz. Sonlandırma, nesne artık kullanılmadığında çalıştırılatan temizleme eylemlerinden oluşur. Yönetilen nesne öldüğünde, sonlandırıcı yönteminde belirtilen temizleme eylemlerini gerçekleştirir.

Kesinleştirilebilir bir nesnenin öldüğü keşfedildiğinde, sonlandırıcısı, temizleme eylemlerinin yürütülmesi için sıraya alınır, ancak nesnenin kendisi bir sonraki nesle yükseltilir. Bu nedenle, nesnenin geri kazanılıp geri alınmadığını belirlemek için o nesilde (bir sonraki çöp toplama olmak zorunda olmayan) oluşan bir sonraki çöp toplamayı beklemeniz gerekir.

Sonlandırma hakkında daha fazla <xref:System.Object.Finalize?displayProperty=nameWithType>bilgi için bkz.

## <a name="workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplama

Çöp toplayıcı kendi kendini ayarlıyor ve çok çeşitli senaryolarda çalışabilir. İş yükünün özelliklerine göre çöp toplama türünü ayarlamak için yapılandırma [dosyası ayarını](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) kullanabilirsiniz. CLR aşağıdaki çöp toplama türlerini sağlar:

- İş istasyonu çöp toplama (GC) istemci uygulamaları için tasarlanmıştır. Bağımsız uygulamalar için varsayılan GC tadıdır. Barındırılan uygulamalar için, örneğin, ASP.NET tarafından barındırılan uygulamalar için, ana bilgisayar varsayılan GC lezzetini belirler.

  İş istasyonu çöp toplama eşzamanlı veya eşzamanlı olmayan olabilir. Eşzamanlı çöp toplama, yönetilen iş parçacıklarının çöp toplama sırasında işlemlerine devam etmesini sağlar. [Arka plan çöp toplama](#background-workstation-garbage-collection) ,NET Framework 4 ve sonraki sürümlerde [eşzamanlı çöp toplama](#concurrent-garbage-collection) değiştirir.

- Yüksek iş gücü ve ölçeklenebilirlik gerektiren sunucu uygulamaları için tasarlanmış sunucu çöp toplama.

  - .NET Core'da sunucu çöp toplama eşzamanlı olmayan veya arka plan olabilir.

  - .NET Framework 4.5 ve sonraki sürümlerde, sunucu çöp toplama eşzamanlı olmayan veya arka plan olabilir (arka plan çöp toplama eşzamanlı çöp toplama yerine gelir). .NET Framework 4 ve önceki sürümlerde sunucu çöp toplama eşzamanlı değildir.

Aşağıdaki resimde, bir sunucuda çöp toplama işlemini gerçekleştiren özel iş parçacıkları gösterilmektedir:

![Sunucu Çöp Toplama İş parçacıkları](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplama karşılaştırma

İş istasyonu çöp toplama için iş parçacığı ve performans hususları şunlardır:

- Koleksiyon, çöp toplamayı tetikleyen kullanıcı iş parçacığında oluşur ve aynı öncelikte kalır. Kullanıcı iş parçacıkları genellikle normal öncelikte çalıştığından, çöp toplayıcı (normal bir öncelik iş parçacığı üzerinde çalışır) CPU süresi için diğer iş parçacıkları ile rekabet etmelidir. (Yerel kodu çalıştıran iş parçacıkları sunucu veya iş istasyonu çöp toplama da askıya alınmaz.)

- İş istasyonu çöp toplama, [yapılandırma ayarından](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)bağımsız olarak her zaman yalnızca bir işlemciye sahip bir bilgisayarda kullanılır.

Sunucu çöp toplama için iş parçacığı ve performans konuları şunlardır:

- Koleksiyon, `THREAD_PRIORITY_HIGHEST` öncelik düzeyinde çalışan birden çok özel iş parçacığı üzerinde oluşur.

- Her CPU için çöp toplama yapmak için bir yığın ve özel bir iş parçacığı sağlanır ve yığınlar aynı anda toplanır. Her yığın küçük bir nesne yığını ve büyük bir nesne yığını içerir ve tüm yığınlara kullanıcı koduyla erişilebilir. Farklı yığınlar üzerindeki nesneler birbirine başvurabilir.

- Birden çok çöp toplama iş parçacığı birlikte çalıştığıiçin, sunucu çöp toplama aynı boyuttaki yığındaki iş istasyonu çöp toplama işleminden daha hızlıdır.

- Sunucu çöp toplama genellikle daha büyük boyutlu segmentleri vardır. Ancak, bu yalnızca bir genellemedir: segment boyutu uygulamaya özgüdür ve değiştirilebilir. Uygulamanızı alarken çöp toplayıcıtarafından ayrılan segmentlerin boyutu hakkında varsayımlarda bulunmayın.

- Sunucu çöp toplama kaynak yoğun olabilir. Örneğin, 4 işlemcisi olan bir bilgisayarda çalışan sunucu GC kullanan 12 işlem olduğunu düşünün. Tüm işlemler aynı anda çöp toplamak için olur, onlar birbirlerine müdahale olur, aynı işlemci üzerinde zamanlanmış 12 iş parçacığı olurdu. İşlemler etkinse, hepsinin sunucu GC'sini kullanmasını sağlamak iyi bir fikir değildir.

Bir uygulamanın yüzlerce örneğini çalıştırıyorsanız, eşzamanlı çöp toplama devre dışı bırakılmış iş istasyonu çöp toplama kullanmayı düşünün. Bu, performansı artırabilecek daha az bağlam geçişine neden olur.

## <a name="background-workstation-garbage-collection"></a>Arka plan iş istasyonu çöp toplama

Arka plandaki iş istasyonu çöp toplamada, geçici nesiller (0 ve 1) gerektiğinde toplanırve nesil 2'nin koleksiyonu devam eder. Arka plan iş istasyonu çöp toplama özel bir iş parçacığı üzerinde gerçekleştirilir ve yalnızca nesil 2 koleksiyonları için geçerlidir.

Arka plan çöp toplama varsayılan olarak etkinleştirilir ve .NET Framework uygulamalarındaki [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma ayarı veya .NET Core uygulamalarındaki [System.GC.Eşzamanlı](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) ayar ile etkinleştirilebilir veya devre dışı bırakılır.

> [!NOTE]
> Arka plan çöp [toplama eşzamanlı çöp toplama](#concurrent-garbage-collection) nın yerini alır ve .NET Framework 4 ve sonraki sürümlerde kullanılabilir. .NET Framework 4'te yalnızca iş istasyonu çöp toplama için desteklenir. .NET Framework 4.5 ile başlayarak, arka plan çöp toplama hem iş istasyonu hem de sunucu çöp toplama için kullanılabilir.

Arka plan çöp toplama sırasında geçici nesiller üzerine bir koleksiyon ön planda çöp toplama olarak bilinir. Ön plan çöp koleksiyonları oluştuğunda, yönetilen tüm iş parçacıkları askıya alınır.

Arka plan çöp toplama devam ediyor ve nesil 0'da yeterli nesne ayırdıysanız, CLR bir nesil 0 veya nesil 1 ön plan çöp toplama gerçekleştirir. Özel arka plan çöp toplama iş parçacığı, ön plan çöp toplama için bir istek olup olmadığını belirlemek için sık sık güvenli noktalarda denetler. Varsa, ön plan çöp toplama oluşabilir, böylece arka plan koleksiyonu kendini askıya alır. Ön plan çöp toplama tamamlandıktan sonra, özel arka plan çöp toplama iş parçacığı ve kullanıcı iş parçacıkları devam eder.

Arka plan çöp toplama, arka plan çöp toplama sırasında geçici çöp koleksiyonları oluşabilir, çünkü eşzamanlı çöp toplama tarafından uygulanan ayırma kısıtlamaları kaldırır. Arka plan çöp toplama geçici nesillerde ölü nesneleri kaldırabilirsiniz. Ayrıca bir nesil 1 çöp toplama sırasında gerekirse yığın genişletebilirsiniz.

Aşağıdaki resimde, iş istasyonunda ayrı bir özel iş parçacığı üzerinde gerçekleştirilen arka plan çöp toplama gösterilmektedir:

![Arka plan iş istasyonu çöp toplama](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Arka plan sunucusu çöp toplama

.NET Framework 4.5 ile başlayarak, arka plan sunucusu çöp toplama sunucu çöp toplama için varsayılan moddur.

Arka plan sunucusu çöp toplama önceki bölümde açıklanan arka plan iş istasyonu çöp toplama benzer işlevleri, ancak birkaç fark vardır:

- Arka plan iş istasyonu çöp toplama, arka plan sunucusu çöp toplama birden çok iş parçacığı kullanır ise bir özel arka plan çöp toplama iş parçacığı kullanır. Genellikle, her mantıksal işlemci için özel bir iş parçacığı vardır.

- İş istasyonu arka plan çöp toplama iş parçacığı aksine, bu iş parçacıkları zaman dışarı yok.

Aşağıdaki resimde, bir sunucuda ayrı bir özel iş parçacığı üzerinde gerçekleştirilen arka plan çöp toplama gösterilmektedir:

![Arka plan sunucusu çöp toplama](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Eşzamanlı çöp toplama

> [!TIP]
> Bu bölüm aşağıdakiler için geçerlidir:
>
> - .NET Framework 3.5 ve daha önceki iş istasyonu çöp toplama
> - .NET Framework 4 ve daha önceki sunucu çöp toplama
>
> Eşzamanlı çöp sonraki sürümlerde [arka plan çöp toplama](#background-workstation-garbage-collection) ile değiştirilir.

İş istasyonu veya sunucu çöp toplama, iş parçacıkları toplama süresinin çoğu için çöp toplama gerçekleştiren özel bir iş parçacığı ile aynı anda çalışmasını sağlayan [eşzamanlı çöp toplama etkinleştirebilirsiniz.](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) Bu seçenek yalnızca nesil 2'deki çöp toplamaları etkiler; 0 ve 1.

Eşzamanlı çöp toplama, bir koleksiyon için duraklamaları en aza indirerek etkileşimli uygulamaların daha duyarlı olmasını sağlar. Yönetilen iş parçacıkları, eşzamanlı çöp toplama iş parçacığı çalışırken çoğu zaman çalışmaya devam edebilir. Bu, çöp toplama oluşurken daha kısa duraklamalara neden olur.

Eşzamanlı çöp toplama özel bir iş parçacığı üzerinde gerçekleştirilir. Varsayılan olarak, CLR eşzamanlı çöp toplama etkin iş istasyonu çöp toplama çalışır. Bu, tek işlemcili ve çok işlemcili bilgisayarlar için geçerlidir.

Aşağıdaki resimde, ayrı bir özel iş parçacığı üzerinde gerçekleştirilen eşzamanlı çöp toplama gösterilmektedir.

![Eşzamanlı Çöp Toplama İşparçacıkları](./media/gc-concurrent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [GC için yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
- [Çöp toplama](index.md)
