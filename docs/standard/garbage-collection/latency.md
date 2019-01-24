---
title: Gecikme Modları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 897f49dc783885728f7d7242482a2b42f3a114bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498079"
---
# <a name="latency-modes"></a>Gecikme Modları
Nesneleri geri kazanmak için atık toplayıcı tüm yürütme iş parçacığı bir uygulamada durdurmanız gerekir. Uygulamanın ne zaman veri aldığını veya içeriğini görüntüler gibi bazı durumlarda, tam çöp toplama kritik bir zamanda meydana ve performans engelleyebildiğinden. Ne kadar zorlayıcı olduğunu atık toplayıcının ayarlayarak yapabilirsiniz <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> özelliğini birine <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> değerleri.  
  
 Gecikme süresi, çöp toplayıcı, uygulamanızda intrudes süreyi ifade eder. Düşük gecikme süreleri sırasında atık toplayıcı daha pasif ve nesneleri tekrar kullanılabilir hale getirme, daha az müdahale eden. <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> Numaralandırma iki düşük gecikme süresi ayarı sağlar:  
  
-   <xref:System.Runtime.GCLatencyMode.LowLatency> 2. nesil koleksiyonlar göstermez ve yalnızca 0 ve 1. nesil koleksiyonlar gerçekleştirir. Yalnızca kısa süreler için kullanılabilir. Sistem bellek Basıncı altında ise uzun süreler boyunca kısaca uygulamayı duraklatmak ve zaman açısından kritik işlem kesintiye bir koleksiyon, atık toplayıcı tetikler. Bu ayar, yalnızca iş istasyonu çöp toplama için kullanılabilir.  
  
-   <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> ön plan 2. nesil koleksiyonlar engeller ve yalnızca oluşturmayı gerçekleştiren 0, 1 ve arka plan 2. nesil koleksiyonlar. Uzun süreler için kullanılabilir ve hem iş istasyonu ve sunucu çöp toplama için kullanılabilir. Bu ayar, kullanılamaz [eş zamanlı çöp toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) devre dışı bırakıldı.  
  
 Aşağıdaki gerçekleşmediği sürece, düşük gecikme süresi dönemlerde 2. nesil koleksiyonlar bastırılan:  
  
-   Sistemin işletim sisteminden bir düşük bellek bildirimi alır.  
  
-   Uygulama kodunuz çağırarak bir koleksiyon sevk <xref:System.GC.Collect%2A?displayProperty=nameWithType> yöntemi ve 2 belirtme `generation` parametresi.  
  
 Uygulama senaryoları kullanmak için aşağıdaki tabloda listelenmektedir <xref:System.Runtime.GCLatencyMode> değerleri.  
  
|Gecikme süresi modu|Uygulama senaryoları|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Hiçbir kullanıcı Arabirimi veya sunucu tarafı işlemleri sahip uygulamalar için.<br /><br /> Bu varsayılan moddur olduğunda [eş zamanlı çöp toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) devre dışı bırakıldı.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Çoğu uygulama için bir kullanıcı Arabirimi sahip.<br /><br /> Bu varsayılan moddur olduğunda [eş zamanlı çöp toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) etkinleştirilir.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Kısa vadeli sahip uygulamalar için zamana duyarlı işlemler çöp toplayıcı hangi kesintilerden sırasında karışıklığa neden olabilir. Örneğin, animasyon işleme veya veri edinme işlevlerini yapmak uygulamalar.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Bir kapsanan ancak büyük olasılıkla daha uzun süre boyunca çöp toplayıcı kesintilerden karışıklığa neden olabilir, zamana duyarlı işlemleri sahip uygulamalar için. Örneğin, alım-satım saatleri boyunca hızlı yanıt süreleri Pazar veriler değiştikçe gerek duyan uygulamalar.<br /><br /> Bu mod modlardan daha büyük bir yönetilen yığın boyutu sonuçlanır. Yönetilen yığın compact değil çünkü daha yüksek parçalanma mümkündür. Yeterli bellek kullanılabilir olduğundan emin olun.|  
  
## <a name="guidelines-for-using-low-latency"></a>Düşük gecikme süresi kullanma yönergeleri  
 Kullanırken <xref:System.Runtime.GCLatencyMode.LowLatency> modu, aşağıdaki yönergeleri göz önünde bulundurun:  
  
-   Süre, düşük gecikme olabildiğince kısa tutun.  
  
-   Düşük gecikme süresi dönemlerde yüksek miktarlarda bellek ayırma kullanmayın. Çöp toplamanın daha az nesne sahiplendiğinden, düşük bellek bildirimi oluşabilir.  
  
-   Düşük gecikme süresi modundayken, büyük nesne yığını ve Sabitlenen nesne üzerine belirli ayırmaları yaptığınız ayırmaların sayısı en aza indirin.  
  
-   Ayırma, iş parçacıklarının dikkat edin. Çünkü <xref:System.Runtime.GCSettings.LatencyMode%2A> özellik ayarı işlem genelinde, oluşturduğunuz bir <xref:System.OutOfMemoryException> ayırma herhangi bir iş parçacığı üzerinde.  
  
-   Kısıtlı yürütme bölgeleri içinde düşük gecikme süresi kodu kaydırmak (daha fazla bilgi için [kısıtlı yürütme bölgeleri](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
-   Çağırarak, düşük gecikme süresi boyunca 2. nesil koleksiyonlar zorlayabilirsiniz <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.GC?displayProperty=nameWithType>
- [Uyarılmış Koleksiyonlar](../../../docs/standard/garbage-collection/induced.md)
- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
