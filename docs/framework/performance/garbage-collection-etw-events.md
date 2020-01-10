---
title: Çöp Toplama ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 5ff214314b92796f4a4a89ddd33a976d8b1f21d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716064"
---
# <a name="garbage-collection-etw-events"></a>Çöp Toplama ETW Olayları

Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar. Çöp toplamanın kaç kez gerçekleştirildiğini, çöp toplama sırasında ne kadar bellek serbest olduğunu ve bu şekilde ne kadar bellek kaldığını belirleme dahil, tanılama ve hata ayıklamada yardımcı olurlar.

Bu kategori aşağıdaki olaylardan oluşur:

- [GCStart_V1 olayı](#gcstart_v1-event)
- [GCEnd_V1 olayı](#gcend_v1-event)
- [GCHeapStats_V1 olayı](#gcheapstats_v1-event)
- [GCCreateSegment_V1 olayı](#gccreatesegment_v1-event)
- [GCFreeSegment_V1 olayı](#gcfreesegment_v1-event)
- [GCRestartEEBegin_V1 olayı](#gcrestarteebegin_v1-event)
- [GCRestartEEEnd_V1 olayı](#gcrestarteeend_v1-event)
- [GCSuspendEE_V1 olayı](#gcsuspendee_v1-event)
- [GCSuspendEEEnd_V1 olayı](#gcsuspendeeend_v1-event)
- [GCAllocationTick_V2 olayı](#gcallocationtick_v2-event)
- [GCFinalizersBegin_V1 olayı](#gcfinalizersbegin_v1-event)
- [GCFinalizersEnd_V1 olayı](#gcfinalizersend_v1-event)
- [GCCreateConcurrentThread_V1 Olayı](#gccreateconcurrentthread_v1-event)
- [GCTerminateConcurrentThread_V1 olayı](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a>GCStart_V1 olayı  

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir. Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCStart_V1`|1\.|Çöp toplama işlemi başlatıldı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Count|Win: UInt32|*N*. çöp toplama.|
|Derinliğini|Win: UInt32|Toplanmakta olan oluşturma.|
|Neden|Win: UInt32|Çöp toplamanın neden tetiklendiği:<br /><br /> 0x0-küçük nesne yığını ayırması.<br /><br /> 0x1-alınmış.<br /><br /> 0x2-düşük bellek.<br /><br /> 0x3-boş.<br /><br /> 0x4-büyük nesne yığını ayırması.<br /><br /> 0x5-alan kalmadı (küçük nesne yığını için).<br /><br /> 0x6-alan kalmadı (büyük nesne yığını için).<br /><br /> 0x7-alınmış ancak engelleme olarak zorlanmadı.|
|Tür|Win: UInt32|0x0-arka plan atık toplama dışında bir çöp toplama engelleme gerçekleşti.<br /><br /> 0x1-arka plan atık toplama.<br /><br /> 0x2-arka plan atık toplama sırasında atık toplamayı engelleme oluştu.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcend_v1-event"></a>GCEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCEnd_V1`|2|Çöp toplama sona erdi.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Count|Win: UInt32|*N*. çöp toplama.|
|Derinliğini|Win: UInt32|Toplanan nesil.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcheapstats_v1-event"></a>GCHeapStats_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|4|Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|GenerationSize0|Win: UInt64|0\. nesil belleğin bayt cinsinden boyutu.|
|TotalPromotedSize0|Win: UInt64|Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.|
|GenerationSize1|Win: UInt64|1\. nesil belleğin bayt cinsinden boyutu.|
|TotalPromotedSize1|Win: UInt64|1\. nesil 2 ' ye kadar yükseltilen bayt sayısı.|
|GenerationSize2|Win: UInt64|2\. nesil belleğin bayt cinsinden boyutu.|
|TotalPromotedSize2|Win: UInt64|Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.|
|GenerationSize3|Win: UInt64|Büyük nesne yığınının bayt cinsinden boyutu.|
|TotalPromotedSize3|Win: UInt64|Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.|
|Sonlandırizationpromotedsize|Win: UInt64|Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.|
|Sonlandırizationpromotedcount|Win: UInt64|Sonlandırmaya hazırlanma nesne sayısı.|
|PinnedObjectCount|Win: UInt32|Sabitlenmiş (taşınamaz) nesne sayısı.|
|SinkBlockCount|Win: UInt32|Kullanımdaki eşitleme bloklarının sayısı.|
|Gchandlet sayısı|Win: UInt32|Kullanımdaki çöp toplama tanıtıcılarının sayısı.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|
  
## <a name="gccreatesegment_v1-event"></a>GCCreateSegment_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|5|Yeni bir atık toplama segmenti oluşturuldu. Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Adres|Win: UInt64|Segmentin adresi.|
|Boyut|Win: UInt64|Segmentin boyutu.|
|Tür|Win: UInt32|0x0-küçük nesne yığını.<br /><br /> 0x1-büyük nesne yığını.<br /><br /> 0x2-salt okunurdur yığın.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın. Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.

## <a name="gcfreesegment_v1-event"></a>GCFreeSegment_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|6|Çöp toplama segmenti yayınlandı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Adres|Win: UInt64|Segmentin adresi.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcrestarteebegin_v1-event"></a>GCRestartEEBegin_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|7|Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.|

Olay verisi yok.

## <a name="gcrestarteeend_v1-event"></a>GCRestartEEEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|3|Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.|

Olay verisi yok.

## <a name="gcsuspendee_v1-event"></a>GCSuspendEE_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|9|Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Neden|Win: UInt16|0x0-diğer.<br /><br /> 0x1-çöp toplama.<br /><br /> 0x2-Uygulama etki alanı kapanıyor.<br /><br /> 0x3-kod yeniden getiriliyor.<br /><br /> 0x4-kapanıyor.<br /><br /> 0x5-Debugger.<br /><br /> çöp toplama için 0x6 hazırlığı.|
|Count|Win: UInt32|GC sayısı (saat). Genellikle, bundan sonra sonraki bir GC başlangıç olayını görürsünüz ve çöp toplama sırasında GC dizinini artırdıkça bu sayı + 1 olur.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcsuspendeeend_v1-event"></a>GCSuspendEEEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|8|Çöp toplama için yürütme altyapısının askıya alınma sonu.|

Olay verisi yok.

## <a name="gcallocationtick_v2-event"></a>GCAllocationTick_V2 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|10|Yaklaşık 100 KB ayrıldığı her seferinde.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|AllocationAmount|Win: UInt32|Bayt cinsinden ayırma boyutu. Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur. Ayırma daha büyükse, bu alan kesilmiş bir değer içerir. Çok büyük ayırmalar için `AllocationAmount64` kullanın.|
|AllocationKind|Win: UInt32|0x0-küçük nesne ayırma (ayırma küçük nesne yığınında).<br /><br /> 0x1-büyük nesne ayırma (ayırma büyük nesne yığınında).|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|
|AllocationAmount64|Win: UInt64|Bayt cinsinden ayırma boyutu. Bu değer, çok büyük ayırmalar için doğrudur.|
|TürKimliği|Win: Işaretçi|MethodTable 'ın adresi. Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.|
|TypeName|Win: UnicodeString|Ayrılan türün adı. Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).|
|Heapındex|Win: UInt32|Nesnenin ayrıldığı yığın. Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.|

## <a name="gcfinalizersbegin_v1-event"></a>GCFinalizersBegin_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|14|Sonlandırıcıları çalıştırmanın başlangıcı.|

Olay verisi yok.

## <a name="gcfinalizersend_v1-event"></a>GCFinalizersEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|13|Sonlandırıcılardan çalıştırmanın sonu.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Count|Win: UInt32|Çalıştırılan sonlandırıcılar sayısı.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gccreateconcurrentthread_v1-event"></a>GCCreateConcurrentThread_V1 Olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|11|Eşzamanlı atık toplama iş parçacığı oluşturuldu.|

Olay verisi yok.

## <a name="gcterminateconcurrentthread_v1-event"></a>GCTerminateConcurrentThread_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Bilgilendirici (4)|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|12|Eşzamanlı atık toplama iş parçacığı sonlandırıldı.|

Olay verisi yok.

## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
