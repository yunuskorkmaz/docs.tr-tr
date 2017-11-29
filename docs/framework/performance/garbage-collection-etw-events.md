---
title: "Çöp Toplama ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06fc335e4b8011afd92e698b20e4b84572b153c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-etw-events"></a>Çöp Toplama ETW Olayları
<a name="top"></a>Bu olaylar çöp toplama ilgili bilgi toplayın. Tanılamada yardımcı olurlar ve hata ayıklama, atık toplama kaç kez belirleme dahil olmak üzere gerçekleştirildiyse, ne kadar bellek çöp toplama ve benzeri sırasında bırakılmış.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [GCStart_V1 olayı](#gcstart_v1_event)  
  
-   [GCEnd_V1 olayı](#gcend_v1_event)  
  
-   [GCHeapStats_V1 olayı](#gcheapstats_v1_event)  
  
-   [GCCreateSegment_V1 olayı](#gccreatesegment_v1_event)  
  
-   [GCFreeSegment_V1 olayı](#gcfreesegment_v1_event)  
  
-   [GCRestartEEBegin_V1 olayı](#gcrestarteebegin_v1_event)  
  
-   [GCRestartEEEnd_V1 olayı](#gcrestarteeend_v1_event)  
  
-   [GCSuspendEE_V1 olayı](#gcsuspendee_v1_event)  
  
-   [GCSuspendEEEnd_V1 olayı](#gcsuspendeeend_v1_event)  
  
-   [GCAllocationTick_V2 olayı](#gcallocationtick_v2_event)  
  
-   [GCFinalizersBegin_V1 olayı](#gcfinalizersbegin_v1_event)  
  
-   [GCFinalizersEnd_V1 olayı](#gcfinalizersend_v1_event)  
  
-   [GCCreateConcurrentThread_V1 olayı](#gccreateconcurrentthread_v1_event)  
  
-   [GCTerminateConcurrentThread_V1 olayı](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>GCStart_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1.|Çöp toplama başlatıldı.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayısı|Win: UInt32|*n* Th atık toplama.|  
|Derinliği|Win: UInt32|Toplanacak oluşturma.|  
|Neden|Win: UInt32|Çöp toplama neden tetiklendi:<br /><br /> 0x0 - küçük nesne yığın ayırma.<br /><br /> 0x1 - kopyaladığınızda.<br /><br /> 0x2 - bellek yetersiz.<br /><br /> 0x3 - boş.<br /><br /> 0x4 - büyük nesne yığın ayırma.<br /><br /> 0x5 - (için küçük nesne yığın) alanı yetersiz.<br /><br /> 0x6 - (için büyük nesne yığın) alanı yetersiz.<br /><br /> 0x7 - kopyaladığınızda ancak engelleme olarak zorunlu değildir.|  
|Tür|Win: UInt32|0x0 - arka plan çöp toplama dışında engelleme çöp toplama oluştu.<br /><br /> 0x1 - arka plan çöp toplama.<br /><br /> 0x2 - engelleme çöp toplama arka plan çöp toplama sırasında oluştu.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>GCEnd_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|Çöp toplama sona erdi.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayısı|Win: UInt32|*n* Th atık toplama.|  
|Derinliği|Win: UInt32|Toplanan oluşturma.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>GCHeapStats_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Her çöp toplama işleminin sonunda yığın istatistiklerini gösterir.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|GenerationSize0|Win: UInt64|Kuşak 0 belleğin bayt cinsinden boyutu.|  
|TotalPromotedSize0|Win: UInt64|0 kuşaktan 1. nesil için öne çıkar bayt sayısı.|  
|GenerationSize1|Win: UInt64|1. nesil belleğin bayt cinsinden boyutu.|  
|TotalPromotedSize1|Win: UInt64|1 kuşaktan 2. nesil için öne çıkar bayt sayısı.|  
|GenerationSize2|Win: UInt64|2. nesil belleğin bayt cinsinden boyutu.|  
|TotalPromotedSize2|Win: UInt64|2. nesil son koleksiyon sonra içinde derdi bitti bayt sayısı.|  
|GenerationSize3|Win: UInt64|Bayt olarak büyük nesne yığın boyutu.|  
|TotalPromotedSize3|Win: UInt64|Büyük nesne yığın sonra son koleksiyon derdi bitti bayt sayısı.|  
|FinalizationPromotedSize|Win: UInt64|Sonlandırma için hazır olan nesnelerin bayt toplam boyutu.|  
|FinalizationPromotedCount|Win: UInt64|Sonlandırma için hazır nesnelerin sayısı.|  
|PinnedObjectCount|Win: UInt32|Sabitlenmiş (taşınamayan) nesnelerin sayısı.|  
|SinkBlockCount|Win: UInt32|Kullanımdaki eşitleme bloğu sayısı.|  
|GCHandleCount|Win: UInt32|Çöp toplama sayısı kullanımda işler.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>GCCreateSegment_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Yeni bir atık toplama segment oluşturuldu. Ayrıca, izleme zaten çalıştırılan bir işlemde etkinleştirildiğinde, varolan her segment için bu olay tetiklenir.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Adres|Win: UInt64|Kesim adresi.|  
|Boyut|Win: UInt64|Kesim boyutu.|  
|Tür|Win: UInt32|0x0 - küçük nesne yığın.<br /><br /> 0x1 - büyük nesne yığın.<br /><br /> 0x2 - salt okunur yığın.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 Çöp toplayıcı tarafından ayrılan kesimleri boyutunu uygulamasına özeldir ve düzenli güncelleştirmeleri dahil olmak üzere, istediğiniz zaman değiştirilebilir unutmayın. Uygulamanız hiçbir zaman hakkında varsayımlar olun veya belirli bir segmentle boyutuna göre değişir ve segment ayırmalarının kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.  
  
 [Başa dön](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>GCFreeSegment_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Çöp toplama kesimi yayımladı.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Adres|Win: UInt64|Kesim adresi.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>GCRestartEEBegin_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|Ortak dil çalışma zamanı askıya gelen sürdürme başladı.|  
  
 Olay verisi yok.  
  
 [Başa dön](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>GCRestartEEEnd_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|Ortak dil çalışma zamanı askıya gelen sürdürme sona erdi.|  
  
 Olay verisi yok.  
  
 [Başa dön](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>GCSuspendEE_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Çöp toplama yürütme altyapısı ertelenmesi başlangıcı.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Neden|Win: UInt16|0x0 - diğer.<br /><br /> 0x1 - atık toplama.<br /><br /> 0x2 - uygulama etki alanı kapatma.<br /><br /> 0x3 - kod pitching.<br /><br /> 0x4 - kapatma.<br /><br /> 0x5 - hata ayıklayıcı.<br /><br /> 0x6 - atık toplama için hazırlama.|  
|Sayısı|Win: UInt32|Zaman GC sayısı. Genellikle, bundan sonra bir sonraki GC başlangıç olayı görür ve biz çöp toplama sırasında GC dizin arttıkça sayımına bu sayı + 1 olacaktır.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>GCSuspendEEEnd_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir:  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterir:  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Çöp toplama yürütme altyapısı ertelenmesi sonu.|  
  
 Olay verisi yok.  
  
 [Başa dön](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>GCAllocationTick_V2 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|Her seferinde yaklaşık 100 KB tahsis edilir.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AllocationAmount|Win: UInt32|Ayırma bayt cinsinden boyutu. Bu değer, ULONG (4,294,967,295 bayt) uzunluğundan daha küçük olan ayırma için doğrudur. Ayırma büyükse, bu alan kesilmiş değer içerir. Kullanım `AllocationAmount64` için çok büyük ayırma.|  
|AllocationKind|Win: UInt32|0x0 - küçük nesne ayırma (küçük nesne yığın ayırma'dir).<br /><br /> 0x1 - büyük nesne ayırma (büyük nesne yığın ayırma'dir).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
|AllocationAmount64|Win: UInt64|Ayırma bayt cinsinden boyutu. Bu değer çok büyük ayırmalarını doğru olur.|  
|TypeId|Win: işaretçi|MethodTable adresi. Bu olay sırasında ayrılan nesneleri çeşitli olduğunda, bu son (100 KB eşiği aşıldı nedeniyle nesne) ayrılmış nesne karşılık gelen MethodTable adresidir.|  
|TypeName|Win: UnicodeString|Ayrıldı türünün adı. Bu olay sırasında ayrılan nesneleri çeşitli olduğunda (100 KB eşiği aşıldı nedeniyle nesne) tahsis son nesnesinin türü budur.|  
|HeapIndex|Win: UInt32|Burada nesne ayrıldı yığın. Bu değer, iş istasyonu çöp toplama ile çalışırken 0 (sıfır) olur.|  
  
 [Başa dön](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>GCFinalizersBegin_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|Sonlandırıcılar çalıştıran başlangıcı.|  
  
 Olay verisi yok.  
  
 [Başa dön](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>GCFinalizersEnd_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|Sonlandırıcılar çalıştıran sonu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayısı|Win: UInt32|Çalıştırılan sonlandırıcılar sayısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>GCCreateConcurrentThread_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|Eşzamanlı atık toplama iş parçacığı oluşturuldu.|  
  
 Olay verisi yok.  
  
 [Başa dön](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>GCTerminateConcurrentThread_V1 olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword`(0x1)|Bilgilendirici (4)|  
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|Eşzamanlı atık toplama iş parçacığı sona erdirildi.|  
  
 Olay verisi yok.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md)
