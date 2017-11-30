---
title: "Çöp Toplama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
caps.latest.revision: "36"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1636bf1cf047e7505be7567f5b5061df25d899c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection"></a>Çöp Toplama
. NET'in atık toplayıcı ayırma ve sürüm, uygulamanız için bellek yönetir. Yeni bir nesne oluşturduğunuzda ortak dil çalışma zamanı, yönetilen yığından nesne için bellek ayırır. Yönetilen yığında kullanılabilir adres alanı bulunduğu sürece, çalışma zamanı yeni nesneler için bellek ayırmaya devam eder. Ancak, bellek sonsuz değildir. Bir süre sonra, atık toplayıcısının bellekte yer açmak için bir toplama işlemi gerçekleştirmesi gerekir. Atık toplayıcısının iyileştirme altyapısı, yapılan bellek ayrımlarına göre bir toplama işlemi gerçekleştirmek için en iyi zamanı belirler. Atık toplayıcı bir toplama işlemi gerçekleştirdiğinde, yönetilen yığın içinde uygulama tarafından artık kullanılmayan nesneleri denetler ve bu nesnelerin kullandığı belleği geri kazanmak için gerekli işlemleri gerçekleştirir.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Çöp toplamanın temelleri](../../../docs/standard/garbage-collection/fundamentals.md)|Atık toplamanın nasıl çalıştığını, nesnelere yönetilen yığında nasıl bellek ayrıldığını ve diğer temel kavramları açıklar.|  
|[Çöp toplama ve performans](../../../docs/standard/garbage-collection/performance.md)|Atık toplama ve performans sorunlarını tanılamak için kullanabileceğiniz performans denetimlerini açıklar.|  
|[Uyarılmış koleksiyonlar](../../../docs/standard/garbage-collection/induced.md)|Bir atık toplama işleminin nasıl oluşturulacağını açıklar.|  
|[Gecikme modları](../../../docs/standard/garbage-collection/latency.md)|Atık toplama işleminin ne kadar zorlayıcı olduğunu belirleyen modları açıklar.|  
|[Paylaşılan Web barındırma için iyileştirme](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Atık toplamanın birden çok küçük Web sitesi tarafından paylaşılan sunucularda nasıl iyileştirileceğini açıklar.|  
|[Çöp toplama bildirimleri](../../../docs/standard/garbage-collection/notifications.md)|Bir tam atık toplama işleminin yaklaşmakta olduğunun ve ne zaman tamamlandığının nasıl belirleneceğini açıklar.|  
|[Uygulama etki alanı kaynak izleme](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Bir uygulama etki alanının CPU ve bellek kullanımının nasıl izleneceğini açıklar.|  
|[Zayıf başvurular](../../../docs/standard/garbage-collection/weak-references.md)|Atık toplayıcının, uygulamanın bir nesneye erişmesine hala izin verirken o nesneyi toplamasına olanak sağlayan özellikleri açıklar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen kaynakları temizleme](../../../docs/standard/garbage-collection/unmanaged.md)
