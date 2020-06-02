---
title: Gecikme Modları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: ee45fe5e8016c7507bc3a873e615fd8379810a8e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286021"
---
# <a name="latency-modes"></a>Gecikme modları

Nesneleri geri kazanmak için çöp toplayıcı (GC) bir uygulamadaki tüm yürütülen iş parçacıklarını durdurmalıdır. Çöp toplayıcısının etkin olduğu zaman dilimi, *gecikme*süresi olarak adlandırılır.

Örneğin, bir uygulamanın verileri aldığı veya içeriği gösterdiği durumlarda, tam bir çöp toplama işlemi kritik bir zamanda gerçekleşebilir ve performansı kesin bir şekilde gerçekleştirebilir. Özelliği değerlerden birine ayarlayarak çöp toplayıcısının izinsiz kullanımını ayarlayabilirsiniz <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> .

## <a name="low-latency-settings"></a>Düşük gecikme süresi ayarları

"Düşük" gecikme süresi ayarı kullanmak, uygulamanızda çöp toplayıcı intrudes daha az anlamına gelir. Çöp toplama geri kazanma bellek hakkında daha koruyucu olur.

<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>Sabit listesi iki düşük gecikme süresi ayarı sağlar:

- [Gclatkenmode. LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 2. nesil koleksiyonları bastırır ve yalnızca nesil 0 ve 1 koleksiyonlar gerçekleştirir. Bu, yalnızca kısa süreler için kullanılabilir. Daha uzun süreler, sistem bellek baskısı altındaysa çöp toplayıcı bir koleksiyonu tetikler, bu da uygulamayı kısaca duraklatabilir ve zaman kritik bir işlemi kesintiye uğratabilir. Bu ayar yalnızca iş istasyonu çöp toplama için kullanılabilir.

- [Gclatkenmode. Sussaledlowlatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) ön plan oluşturma 2 koleksiyonlarını bastırır ve yalnızca nesil 0, 1 ve arka plan oluşturma 2 koleksiyonlarını gerçekleştirir. Daha uzun süreler için kullanılabilir ve hem iş istasyonu hem de sunucu çöp toplama için kullanılabilir. Arka plan atık toplama devre dışıysa bu ayar kullanılamaz.

Düşük gecikme süreleri sırasında, 2. nesil koleksiyonlar aşağıdakiler gerçekleşmediği takdirde bastırılır:

- Sistem, işletim sisteminden düşük bir bellek bildirimi alır.

- Uygulama kodu, <xref:System.GC.Collect%2A?displayProperty=nameWithType> yöntemini çağırarak ve parametresi için 2 belirterek bir koleksiyona sahiptir `generation` .

## <a name="scenarios"></a>Senaryolar

Aşağıdaki tabloda, değerleri kullanmaya yönelik uygulama senaryoları listelenmektedir <xref:System.Runtime.GCLatencyMode> :

|Gecikme modu|Uygulama senaryoları|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Kullanıcı arabirimi (UI) veya sunucu tarafı işlemleri olmayan uygulamalar için.<br /><br />Arka plan atık toplama devre dışı bırakıldığında, bu, iş istasyonu ve sunucu çöp toplama için varsayılan moddur. <xref:System.Runtime.GCLatencyMode.Batch>mod ayrıca [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) ayarını geçersiz kılar, diğer bir deyişle, arka plan veya eşzamanlı koleksiyonları engeller.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Kullanıcı arabirimi olan çoğu uygulama için.<br /><br />Bu, iş istasyonu ve sunucu çöp toplama için varsayılan moddur. Ancak, bir uygulama barındırılıyorsa, barındırma işleminin çöp toplayıcı ayarları önceliklidir.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Kısa süreli ve çöp toplayıcısından kesintiler kesintiye uğratan, zamana duyarlı işlemler içeren uygulamalar için. Örneğin, animasyonları veya veri alımı işlevlerini işleyen uygulamalar.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|İçinde, atık toplayıcıdan kesintileri kesintiye uğratan daha uzun bir süre için zamana duyarlı işlemler içeren uygulamalar için. Örneğin, Ticaret saatlerinde Pazar verileri değiştikçe hızlı yanıt süresi gerektiren uygulamalar.<br /><br />Bu mod, diğer moddan daha büyük bir yönetilen yığın boyutuna neden olur. Yönetilen yığını sıkıştırmadığından, daha yüksek parçalanma mümkündür. Yeterli belleğin kullanılabildiğinden emin olun.|

## <a name="guidelines-for-using-low-latency"></a>Düşük gecikme süresi kullanımı için yönergeler

[Gclatkenmode. LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) modunu kullandığınızda aşağıdaki yönergeleri göz önünde bulundurun:

- Süreyi düşük gecikme süresine olabildiğince kısa tutun.

- Düşük gecikme süreleri sırasında yüksek miktarda bellek ayırmaktan kaçının. Çöp toplama geri kazanır daha az nesne olduğundan düşük bellek bildirimleri meydana gelebilir.

- Düşük gecikme modundayken, büyük nesne yığınında ve sabitlenmiş nesnelerde, belirli ayırmalarda, yeni ayırma sayısını en aza indirin.

- Ayrılamıyor iş parçacıklarından haberdar olun. <xref:System.Runtime.GCSettings.LatencyMode%2A>Özellik ayarı işlem genelinde olduğundan, ayrılan <xref:System.OutOfMemoryException> her iş parçacığında özel durumlar oluşturulabilir.

- Sınırlı yürütme bölgelerinde düşük gecikme süresi kodunu sarın. Daha fazla bilgi için bkz. [kısıtlı yürütme bölgeleri](../../framework/performance/constrained-execution-regions.md).

- Yöntemini çağırarak, düşük gecikme süresi boyunca 2 koleksiyonu oluşturmaya zorlayabilirsiniz <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.GC?displayProperty=nameWithType>
- [Alınmış Koleksiyonlar](induced.md)
- [Çöp toplama](index.md)
