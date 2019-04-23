---
title: Çöp Toplama ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149740"
---
# <a name="garbage-collection-etw-events"></a>Çöp Toplama ETW Olayları
<a name="top"></a> Bu olaylar, çöp toplama hakkında bilgi toplayın. Bunlar Tanılama'da yardımcı olur ve hata ayıklama, çöp toplama kaç kez belirleme de dahil olmak üzere gerçekleştirildiyse, ne kadar bellek çöp toplama ve benzeri sırasında bırakılmış.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [GCStart_V1 olay](#gcstart_v1_event)  
  
-   [GCEnd_V1 Event](#gcend_v1_event)  
  
-   [GCHeapStats_V1 olay](#gcheapstats_v1_event)  
  
-   [GCCreateSegment_V1 Event](#gccreatesegment_v1_event)  
  
-   [GCFreeSegment_V1 Event](#gcfreesegment_v1_event)  
  
-   [GCRestartEEBegin_V1 olay](#gcrestarteebegin_v1_event)  
  
-   [GCRestartEEEnd_V1 olay](#gcrestarteeend_v1_event)  
  
-   [GCSuspendEE_V1 Event](#gcsuspendee_v1_event)  
  
-   [GCSuspendEEEnd_V1 Event](#gcsuspendeeend_v1_event)  
  
-   [GCAllocationTick_V2 olay](#gcallocationtick_v2_event)  
  
-   [GCFinalizersBegin_V1 Event](#gcfinalizersbegin_v1_event)  
  
-   [GCFinalizersEnd_V1 olay](#gcfinalizersend_v1_event)  
  
-   [GCCreateConcurrentThread_V1 olay](#gccreateconcurrentthread_v1_event)  
  
-   [GCTerminateConcurrentThread_V1 olay](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>GCStart_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1.|Bir çöp toplama başlatıldı.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayı|Kazanma: UInt32|*n*th çöp toplama.|  
|Derinliği|Kazanma: UInt32|Toplanmakta olan oluşturma.|  
|Neden|Kazanma: UInt32|Çöp toplama işlemine neden tetiklendi:<br /><br /> 0x0 - küçük nesne yığını ayırması.<br /><br /> 0x1 - başlattı.<br /><br /> 0x2 - bellek yetersiz.<br /><br /> 0x3 - boş.<br /><br /> 0x4 - büyük nesne yığını ayırması.<br /><br /> 0x5 - yetersiz alan (küçük nesne yığını için).<br /><br /> 0x6 - yetersiz alan (büyük nesne yığını için).<br /><br /> 0x7 - başlattığı ancak engelleme olarak zorunlu değildir.|  
|Tür|Kazanma: UInt32|0x0 - arka plan atık toplamanın dışında atık toplamayı engelleme oluştu.<br /><br /> 0x1 - arka plan çöp toplama.<br /><br /> 0x2 - arka plan çöp toplama sırasında atık toplamayı engelleme oluştu.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>GCEnd_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|Çöp toplama sona erdi.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayı|Kazanma: UInt32|*n*th çöp toplama.|  
|Derinliği|Kazanma: UInt32|Toplanan oluşturma.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>GCHeapStats_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Her çöp toplama sonunda yığında istatistiklerini gösterir.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|GenerationSize0|Kazanma: UInt64|Nesil 0 belleğin bayt cinsinden boyutu.|  
|TotalPromotedSize0|Kazanma: UInt64|1. nesil için nesil 0 ' yükseltilen bayt sayısı.|  
|GenerationSize1|Kazanma: UInt64|1. kuşak belleğin bayt cinsinden boyutu.|  
|TotalPromotedSize1|Kazanma: UInt64|Nesil 1 ' 2 yeni nesle yükseltilir bayt sayısı.|  
|GenerationSize2|Kazanma: UInt64|2. nesil belleğin bayt cinsinden boyutu.|  
|TotalPromotedSize2|Kazanma: UInt64|2. nesil son toplamadan sonra içinde kurtulan bayt sayısı.|  
|GenerationSize3|Kazanma: UInt64|Büyük nesne yığını bayt cinsinden boyutu.|  
|TotalPromotedSize3|Kazanma: UInt64|Büyük nesne yığınında sonra son toplamadan kurtulan bayt sayısı.|  
|FinalizationPromotedSize|Kazanma: UInt64|Baytlarında sonlandırma için hazır olan nesneleri toplam boyutu.|  
|FinalizationPromotedCount|Kazanma: UInt64|Sonlandırma için hazır olan nesnelerinin sayısı.|  
|PinnedObjectCount|Kazanma: UInt32|Sabitlenen (taşınamayan) nesne sayısı.|  
|SinkBlockCount|Kazanma: UInt32|Kullanımdaki eşitleme blokların sayısı.|  
|GCHandleCount|Kazanma: UInt32|Kullanımda olan çöp toplama sayısı.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>GCCreateSegment_V1 Event  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Yeni bir çöp toplama segment oluşturuldu. Ayrıca, zaten çalışan bir işlemde izleme etkin olduğunda, var olan her segment için bu olay oluşturulur.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Adres|Kazanma: UInt64|Segment adresi.|  
|Boyut|Kazanma: UInt64|Kesim boyutu.|  
|Tür|Kazanma: UInt32|0x0 - küçük nesne yığını.<br /><br /> 0x1 - büyük nesne yığını.<br /><br /> 0x2 - yığın salt okunur.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 Boyutu çöp toplayıcısının ayrılan parçaları uygulama özgü olan ve düzenli güncelleştirmeleri dahil olmak üzere dilediğiniz zaman değiştirilebilir unutmayın. Uygulamanız hiçbir zaman hakkında varsayımlar veya belirli bir segment boyutuna göre değişir ve segment ayırma için kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.  
  
 [Başa dön](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>GCFreeSegment_V1 Event  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Bir çöp toplama segment piyasaya Sürüldü.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Adres|Kazanma: UInt64|Segment adresi.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>GCRestartEEBegin_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|Ortak dil çalışma zamanı askıya alma gelen sürdürme başladı.|  
  
 Hiçbir olay verileri.  
  
 [Başa dön](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>GCRestartEEEnd_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|Ortak dil çalışma zamanı askıya alma gelen sürdürme sona erdi.|  
  
 Hiçbir olay verileri.  
  
 [Başa dön](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>GCSuspendEE_V1 Event  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Çöp toplama işlemi için yürütme altyapısının askıya alma başlangıcı.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Neden|Kazanma: UInt16|0x0 - diğer.<br /><br /> 0x1 - çöp toplama.<br /><br /> 0x2 - uygulama etki alanı kapatma.<br /><br /> 0x3 - kod pitching.<br /><br /> 0x4 - kapatma.<br /><br /> 0x5 - Hata Ayıklayıcısı'nı tıklatın.<br /><br /> 0x6 - çöp toplama için hazırlama.|  
|Sayı|Kazanma: UInt32|GC sayısı zaman. Genellikle, bundan sonra bir sonraki GC başlangıç olayı görür ve biz GC dizini çöp toplama sırasında arttıkça sayımına bu sayı + 1 olur.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>GCSuspendEEEnd_V1 Event  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir:  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tablo, olay bilgileri gösterir:  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Çöp toplama işlemi için yürütme altyapısının askıya alma sonu.|  
  
 Hiçbir olay verileri.  
  
 [Başa dön](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>GCAllocationTick_V2 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|Her seferinde yaklaşık 100 KB ayrılır.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AllocationAmount|Kazanma: UInt32|Ayırma bayt cinsinden boyutu. Bu değer, küçük bir ULONG (4,294,967,295 bayt), uzunluğundan ayırmalar için doğru olur. Ayırma büyükse, bu alan kesilmiş değer içerir. Kullanım `AllocationAmount64` çok büyük ayırmalar için.|  
|AllocationKind|Kazanma: UInt32|0x0 - küçük nesne ayırma (içinde küçük nesne yığını ayırma'dir).<br /><br /> 0x1 - büyük nesne ayırma (büyük nesne yığınında ayırma'dir).|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
|AllocationAmount64|Kazanma: UInt64|Ayırma bayt cinsinden boyutu. Bu değer çok büyük ayırmalarını doğru olur.|  
|typeId|Kazanma: işaretçi|MethodTable adresi. Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, bu son (100 KB eşiği olması nedeniyle nesne) ayrılmış nesne karşılık gelen MethodTable adresidir.|  
|TypeName|Kazanma: UnicodeString|Ayrılmış olan tür adı. Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, (100 KB eşiği olması nedeniyle nesne) ayrılan son nesnenin türü budur.|  
|HeapIndex|Kazanma: UInt32|Nesne ayrıldığı yığında. İş istasyonu çöp toplama ile çalışırken, bu değer 0 (sıfır) olur.|  
  
 [Başa dön](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>GCFinalizersBegin_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|Sonlandırıcılar çalıştırma başlangıcı.|  
  
 Hiçbir olay verileri.  
  
 [Başa dön](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>GCFinalizersEnd_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|Sonlandırıcılar çalıştırma bitiş olayı.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Sayı|Kazanma: UInt32|Çalıştırılan bir sonlandırıcı sayısı.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>GCCreateConcurrentThread_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|Eş zamanlı çöp toplama iş parçacığı oluşturulur.|  
  
 Hiçbir olay verileri.  
  
 [Başa dön](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>GCTerminateConcurrentThread_V1 olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Bilgilendirici (4)|  
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|Eş zamanlı çöp toplama iş parçacığı sonlandırıldı.|  
  
 Hiçbir olay verileri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
