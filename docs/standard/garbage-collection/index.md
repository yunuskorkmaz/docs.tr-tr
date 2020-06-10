---
title: .NET atık toplama
description: .NET 'teki çöp toplama hakkında bilgi edinin. .NET atık toplayıcısı, uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir.
ms.date: 04/21/2020
ms.technology: dotnet-standard
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
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662491"
---
# <a name="garbage-collection"></a>Atık toplama

. NET ' in atık toplayıcısı, uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir. Yeni bir nesne oluşturduğunuzda ortak dil çalışma zamanı, yönetilen yığından nesne için bellek ayırır. Yönetilen yığında kullanılabilir adres alanı bulunduğu sürece, çalışma zamanı yeni nesneler için bellek ayırmaya devam eder. Ancak, bellek sonsuz değildir. Bir süre sonra, atık toplayıcısının bellekte yer açmak için bir toplama işlemi gerçekleştirmesi gerekir. Atık toplayıcısının iyileştirme altyapısı, yapılan bellek ayrımlarına göre bir toplama işlemi gerçekleştirmek için en iyi zamanı belirler. Atık toplayıcı bir toplama işlemi gerçekleştirdiğinde, yönetilen yığın içinde uygulama tarafından artık kullanılmayan nesneleri denetler ve bu nesnelerin kullandığı belleği geri kazanmak için gerekli işlemleri gerçekleştirir.  
  
## <a name="in-this-section"></a>Bu bölümde
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Çöp toplamanın temelleri](fundamentals.md)|Atık toplamanın nasıl çalıştığını, nesnelere yönetilen yığında nasıl bellek ayrıldığını ve diğer temel kavramları açıklar.|  
|[İş istasyonu ve sunucu atık toplama](workstation-server-gc.md)|İstemci uygulamaları için iş istasyonu atık toplama ve sunucu uygulamaları için sunucu çöp toplama arasındaki farkları açıklar.|
|[Arka plan atık toplama](background-gc.md)|2. nesil toplama işlemi devam ederken, nesil 0 ve 1 nesnelerinin toplanması olan arka plan çöp toplama işlemini açıklar.|
|[Büyük nesne yığını](large-object-heap.md)|Büyük nesne yığınını (LOH) ve büyük nesneleri atık toplanan olarak tanımlar.|
|[Çöp toplama ve performans](performance.md)|Atık toplama ve performans sorunlarını tanılamak için kullanabileceğiniz performans denetimlerini açıklar.|  
|[Uyarılmış koleksiyonlar](induced.md)|Bir atık toplama işleminin nasıl oluşturulacağını açıklar.|  
|[Gecikme modları](latency.md)|Atık toplama işleminin ne kadar zorlayıcı olduğunu belirleyen modları açıklar.|  
|[Paylaşılan web barındırma için iyileştirme](optimization-for-shared-web-hosting.md)|Atık toplamanın birden çok küçük Web sitesi tarafından paylaşılan sunucularda nasıl iyileştirileceğini açıklar.|  
|[Çöp toplama bildirimleri](notifications.md)|Bir tam atık toplama işleminin yaklaşmakta olduğunun ve ne zaman tamamlandığının nasıl belirleneceğini açıklar.|  
|[Uygulama etki alanı kaynak izleme](app-domain-resource-monitoring.md)|Bir uygulama etki alanının CPU ve bellek kullanımının nasıl izleneceğini açıklar.|  
|[Zayıf başvurular](weak-references.md)|Atık toplayıcının, uygulamanın bir nesneye erişmesine hala izin verirken o nesneyi toplamasına olanak sağlayan özellikleri açıklar.|  
  
## <a name="reference"></a>Başvuru

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen kaynakları temizleme](unmanaged.md)
