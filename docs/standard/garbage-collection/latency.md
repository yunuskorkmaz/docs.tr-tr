---
title: Gecikme Modları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: a8eaf0c80aa32978eead80c51a905cbcd66a537b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283590"
---
# <a name="latency-modes"></a>Gecikme modları

Nesneleri geri almak için, çöp toplayıcı (GC) bir uygulamadaki tüm yürütme iş parçacığı durdurmak gerekir. Çöp toplayıcısının etkin olduğu süre, *gecikme süresi*olarak adlandırılır.

Bir uygulama veri aldığında veya içeriği görüntülediğinde, kritik bir anda tam bir çöp toplama oluşabilir ve performansı engelleyebilir gibi bazı durumlarda. <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> Özelliği <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> değerlerden birine ayarlayarak çöp toplayıcının müdahaleciliğini ayarlayabilirsiniz.

## <a name="low-latency-settings"></a>Düşük gecikme sonu ayarları

"Düşük" gecikme ayarı kullanmak, çöp toplayıcısının uygulamanıza daha az izinsiz girdiği anlamına gelir. Çöp toplama bellek geri alma konusunda daha muhafazakar.

Numaralandırma <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> iki düşük gecikme sonu ayarı sağlar:

- [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) nesil 2 koleksiyonları bastırır ve sadece nesil 0 ve 1 koleksiyonları gerçekleştirir. Sadece kısa süreler için kullanılabilir. Uzun süreler boyunca, sistem bellek baskısı altındaysa, çöp toplayıcı, uygulamayı kısa bir süre duraklatabilecek ve zaman açısından kritik bir işlemi bozabilecek bir koleksiyonu tetikler. Bu ayar yalnızca iş istasyonu çöp toplama için kullanılabilir.

- [GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) ön plan nesil 2 koleksiyonları bastırır ve sadece nesil 0, 1 ve arka plan nesil 2 koleksiyonları gerçekleştirir. Daha uzun süreler için kullanılabilir ve hem iş istasyonu hem de sunucu çöp toplama için kullanılabilir. Arka plan çöp toplama devre dışı bırakılırsa bu ayar kullanılamaz.

Düşük gecikme süreleri sırasında, aşağıdakiler oluşmadığı sürece nesil 2 koleksiyonları bastırılır:

- Sistem işletim sisteminden düşük bellek bildirimi alır.

- Uygulama <xref:System.GC.Collect%2A?displayProperty=nameWithType> kodu, yöntemi arayarak ve `generation` parametre için 2 belirterek bir koleksiyona neden olur.

## <a name="scenarios"></a>Senaryolar

Aşağıdaki tablo <xref:System.Runtime.GCLatencyMode> değerleri kullanmak için uygulama senaryoları listeler:

|Gecikme modu|Uygulama senaryoları|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Kullanıcı arabirimi (UI) veya sunucu tarafı işlemleri olmayan uygulamalar için.<br /><br />Arka plan çöp toplama devre dışı bırakıldığında, bu iş istasyonu ve sunucu çöp toplama için varsayılan moddur. <xref:System.Runtime.GCLatencyMode.Batch>modu da [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) ayarı geçersiz kılar, yani arka plan veya eşzamanlı koleksiyonları engeller.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Kullanıcı Arabirimi olan çoğu uygulama için.<br /><br />Bu, iş istasyonu ve sunucu çöp toplama için varsayılan moddur. Ancak, bir uygulama barındırılırsa, barındırma işleminin çöp toplayıcı ayarları önceliklidir.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Çöp toplayıcısından gelen kesintilerin kesintiye uğrayabileceği kısa süreli, zamana duyarlı işlemleri olan uygulamalar için. Örneğin, animasyonlar veya veri toplama işlevleri oluşturan uygulamalar.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Çöp toplayıcısından gelen kesintilerin kesintiye uğrayabileceği, içerdiği ancak potansiyel olarak daha uzun bir süre için zamana duyarlı işlemleri olan uygulamalar için. Örneğin, işlem saatlerinde piyasa verileri değiştikçe hızlı yanıt süreleri gerektiren uygulamalar.<br /><br />Bu mod, diğer modlardan daha büyük yönetilen yığın boyutuyla sonuçlanır. Yönetilen yığını sıkıştırmadığından, daha yüksek parçalanma mümkündür. Yeterli belleğin kullanılabilir olduğundan emin olun.|

## <a name="guidelines-for-using-low-latency"></a>Düşük gecikme gecikmesi kullanma yönergeleri

[GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) modunu kullandığınızda, aşağıdaki yönergeleri göz önünde bulundurun:

- Süreyi mümkün olduğunca kısa bir süre düşük gecikme süresi içinde tutun.

- Düşük gecikme süreleri boyunca yüksek miktarda bellek ayırmaktan kaçının. Çöp toplama daha az nesneyi geri aldığından düşük bellek bildirimleri oluşabilir.

- Düşük gecikme modundayken, yeni ayırmaların sayısını, özellikle büyük nesne yığınına ve sabitlenmiş nesnelere ayırmasayısını en aza indirin.

- Tahsis edilebilen iş parçacıklarına dikkat edin. <xref:System.Runtime.GCSettings.LatencyMode%2A> Özellik ayarı işlem genelinde <xref:System.OutOfMemoryException> olduğundan, ayrılan herhangi bir iş parçacığı üzerinde özel durumlar oluşturulabilir.

- Kısıtlı yürütme bölgelerindeki düşük gecikme kodunu sarın. Daha fazla bilgi için [bkz.](../../../docs/framework/performance/constrained-execution-regions.md)

- <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> Yöntemi arayarak düşük bir gecikme süresi boyunca nesil 2 koleksiyonlarını zorlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.GC?displayProperty=nameWithType>
- [Uyarılmış Koleksiyonlar](../../../docs/standard/garbage-collection/induced.md)
- [Çöp Toplama](../../../docs/standard/garbage-collection/index.md)
