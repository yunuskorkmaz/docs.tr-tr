---
title: Gecikme Modları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 8833c88c3221c0a375011eb62dd712340f7e89cd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120914"
---
# <a name="latency-modes"></a>Gecikme Modları
Nesneleri geri kazanmak için çöp toplayıcı, bir uygulamadaki tüm yürütülen iş parçacıklarını durdurmalıdır. Örneğin, bir uygulamanın verileri aldığı veya içeriği gösterdiği durumlarda, tam bir çöp toplama işlemi kritik bir zamanda gerçekleşebilir ve performansı kesin bir şekilde gerçekleştirebilir. <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> değerlerinden birine ayarlayarak çöp toplayıcısının izinsiz kullanımını ayarlayabilirsiniz.  
  
 Gecikme süresi, çöp toplayıcı intrudes uygulamanızdaki süreyi ifade eder. Düşük gecikme süreleri boyunca çöp toplayıcı daha koruyucu olur ve geri kazanma nesnelerinde daha az zorlayıcıdır. <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> numaralandırması iki düşük gecikme süresi ayarı sağlar:  
  
- <xref:System.Runtime.GCLatencyMode.LowLatency> 2. nesil koleksiyonları bastırır ve yalnızca nesil 0 ve 1 koleksiyonlar gerçekleştirir. Bu, yalnızca kısa süreler için kullanılabilir. Daha uzun süreler, sistem bellek baskısı altındaysa çöp toplayıcı bir koleksiyonu tetikler, bu da uygulamayı kısaca duraklatabilir ve zaman kritik bir işlemi kesintiye uğratabilir. Bu ayar yalnızca iş istasyonu çöp toplama için kullanılabilir.  
  
- <xref:System.Runtime.GCLatencyMode.SustainedLowLatency>, ön plan oluşturma 2 koleksiyonlarını bastırır ve yalnızca nesil 0, 1 ve arka plan oluşturma 2 koleksiyonlarını gerçekleştirir. Daha uzun süreler için kullanılabilir ve hem iş istasyonu hem de sunucu çöp toplama için kullanılabilir. [Eşzamanlı çöp toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) devre dışıysa bu ayar kullanılamaz.  
  
 Düşük gecikme süreleri sırasında, 2. nesil koleksiyonlar aşağıdakiler gerçekleşmediği takdirde bastırılır:  
  
- Sistem, işletim sisteminden düşük bir bellek bildirimi alır.  
  
- Uygulama kodunuz, <xref:System.GC.Collect%2A?displayProperty=nameWithType> yöntemini çağırarak ve `generation` parametresi için 2 belirterek bir koleksiyona sahiptir.  
  
 Aşağıdaki tabloda <xref:System.Runtime.GCLatencyMode> değerlerini kullanmaya yönelik uygulama senaryoları listelenmektedir.  
  
|Gecikme modu|Uygulama senaryoları|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Kullanıcı arabirimi veya sunucu tarafı işlemleri olmayan uygulamalar için.<br /><br /> [Eşzamanlı atık toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) devre dışı bırakıldığında bu varsayılan moddur.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Kullanıcı arabirimi olan çoğu uygulama için.<br /><br /> [Eşzamanlı atık toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) etkinleştirildiğinde bu varsayılan moddur.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Kısa süreli ve çöp toplayıcısından kesintiler kesintiye uğratan, zamana duyarlı işlemler içeren uygulamalar için. Örneğin, animasyon işleme veya veri alma işlevleri gerçekleştiren uygulamalar.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|İçinde, atık toplayıcıdan kesintileri kesintiye uğratan daha uzun bir süre için zamana duyarlı işlemler içeren uygulamalar için. Örneğin, Ticaret saatlerinde Pazar verileri değiştikçe hızlı yanıt süresi gerektiren uygulamalar.<br /><br /> Bu mod, diğer moddan daha büyük bir yönetilen yığın boyutuna neden olur. Yönetilen yığını sıkıştırmadığından, daha yüksek parçalanma mümkündür. Yeterli belleğin kullanılabildiğinden emin olun.|  
  
## <a name="guidelines-for-using-low-latency"></a>Düşük gecikme süresi kullanımı için yönergeler  
 <xref:System.Runtime.GCLatencyMode.LowLatency> modu kullandığınızda aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Süreyi düşük gecikme süresine olabildiğince kısa tutun.  
  
- Düşük gecikme süreleri sırasında yüksek miktarda bellek ayırmaktan kaçının. Çöp toplama geri kazanır daha az nesne olduğundan düşük bellek bildirimleri meydana gelebilir.  
  
- Düşük gecikme modundayken, büyük nesne yığını ve sabitlenmiş nesneler üzerinde belirli ayırmalarda, yaptığınız ayırma sayısını en aza indirin.  
  
- Ayrılamıyor iş parçacıklarından haberdar olun. <xref:System.Runtime.GCSettings.LatencyMode%2A> özellik ayarı işlem genelinde olduğundan, ayırmak için herhangi bir iş parçacığında bir <xref:System.OutOfMemoryException> oluşturabilirsiniz.  
  
- Sınırlı yürütme bölgelerinde düşük gecikme süresi kodunu sarın (daha fazla bilgi için bkz. [kısıtlı yürütme bölgeleri](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
- <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> yöntemini çağırarak düşük gecikme süresi boyunca 2 koleksiyonu oluşturmaya zorlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.GC?displayProperty=nameWithType>
- [Uyarılmış Koleksiyonlar](../../../docs/standard/garbage-collection/induced.md)
- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
