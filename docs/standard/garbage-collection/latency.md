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
ms.openlocfilehash: 913a5d6ab28d375dbfdd99dec6fd153bc94efee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573906"
---
# <a name="latency-modes"></a>Gecikme Modları
Nesneleri geri kazanmak için atık toplayıcı tüm yürütme iş parçacığı bir uygulamada durdurmanız gerekir. Uygulama verileri alır veya içeriği, görüntüler gibi bazı durumlarda, tam atık toplama kritik bir zamanda meydana ve performansı olumsuz yönde. Ayarlayarak Atık toplayıcısının zorla girme ayarlayabilirsiniz <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> özelliğini birine <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> değerleri.  
  
 Gecikme atık toplayıcı uygulamanızda intrudes süreyi ifade eder. Düşük gecikme süreleri sırasında atık toplayıcısı daha pasif ve nesneleri geri kazanma içinde daha az müdahale. <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> Numaralandırma iki düşük gecikme süresi ayarları sağlar:  
  
-   <xref:System.Runtime.GCLatencyMode.LowLatency> 2. nesil koleksiyonları önler ve yalnızca 0 ve 1. nesil koleksiyonları gerçekleştirir. Yalnızca kısa sürelerle için kullanılabilir. Sistem bellek Basıncı altında ise uzun süreler boyunca kısaca uygulama durdurabilir ve zaman açısından kritik işlemi kesintiye bir koleksiyon atık toplayıcı tetikler. Bu ayar yalnızca iş istasyonu çöp toplama için kullanılabilir.  
  
-   <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> ön plan 2. nesil koleksiyonları önler ve yalnızca oluşturmayı gerçekleştiren 0, 1 ve arka plan 2. nesil koleksiyonları. Uzun süreler için kullanılabilir ve iş istasyonu ve sunucu atık toplama için kullanılabilir. Bu ayar, kullanılamaz [eşzamanlı atık toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) devre dışı bırakılır.  
  
 Aşağıdaki oluşmadığı sürece, düşük gecikme süreleri sırasında 2. nesil koleksiyonları bastırılan:  
  
-   Sistem, işletim sisteminden düşük bellek bildirimi alır.  
  
-   Uygulama kodunuz çağırarak bir koleksiyon uygulanmasını <xref:System.GC.Collect%2A?displayProperty=nameWithType> yöntemi ve 2 için belirterek `generation` parametresi.  
  
 Uygulama senaryoları kullanmak için aşağıdaki tabloda listelenmektedir <xref:System.Runtime.GCLatencyMode> değerleri.  
  
|Gecikme modu|Uygulama senaryoları|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Hiçbir kullanıcı Arabirimi veya sunucu tarafı işlemleri sahip uygulamalar için.<br /><br /> Bu varsayılan moddur zaman [eşzamanlı atık toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) devre dışı bırakılır.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Çoğu uygulama için bir kullanıcı Arabirimi sahip.<br /><br /> Bu varsayılan moddur zaman [eşzamanlı atık toplama](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) etkinleştirilir.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Kısa vadeli içeren uygulamalar için Atık toplayıcısının hangi kesintilerden zamana duyarlı işlemlerde kesintiye uğratan olabilir. Örneğin, animasyon işleme veya veri alım işlevleri yapmak uygulamalar.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Bir kapsanan ancak büyük olasılıkla daha uzun süre boyunca atık toplayıcı kesintilerden kesintiye uğratan olabilir zamana duyarlı işlemlerde sahip uygulamalar için. Örneğin, ticaret saatlerde Pazar veri değişikliklerini olarak hızlı yanıt süreleri ihtiyaç duyan uygulamalar.<br /><br /> Bu mod modlardan daha büyük bir yönetilen yığın boyutu sonuçlanır. Yönetilen yığın compact değil çünkü daha yüksek parçalanma mümkündür. Yeterli bellek kullanılabilir olduğundan emin olun.|  
  
## <a name="guidelines-for-using-low-latency"></a>Düşük gecikme süresi kullanma için yönergeler  
 Kullandığınızda <xref:System.Runtime.GCLatencyMode.LowLatency> modu, aşağıdaki yönergeleri dikkate alın:  
  
-   Düşük gecikme süresini olabildiğince kısa süre unutmayın.  
  
-   Düşük gecikme süreleri sırasında yüksek miktarda bellek ayırma kaçının. Düşük bellek bildirimleri atık toplama daha az nesne geri kazanır nedeniyle oluşabilir.  
  
-   Düşük gecikme süresi modundayken, sabitlenmiş nesneleri ve büyük nesne yığın üzerine belirli ayırmaları içinde olun ayırmaları sayısını en aza indirin.  
  
-   Ayırma iş parçacıkları, dikkat edin. Çünkü <xref:System.Runtime.GCSettings.LatencyMode%2A> özellik ayarı işlem genelinde, size üretebilir bir <xref:System.OutOfMemoryException> ayırma herhangi bir iş parçacığı üzerinde.  
  
-   Kısıtlı yürütme bölgeleri içinde düşük gecikme süresi kod sarmalamak (daha fazla bilgi için bkz: [kısıtlı yürütme bölgeleri](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
-   2. nesil koleksiyonları çağırarak düşük gecikme süresi sırasında zorlayabilir miyim <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.GC?displayProperty=nameWithType>  
 [Uyarılmış Koleksiyonlar](../../../docs/standard/garbage-collection/induced.md)  
 [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
