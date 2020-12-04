---
title: Çöp toplama çalışma zamanı olayları
description: .NET atık toplayıcısına özgü tanılama bilgilerini topladığımız .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96590001"
---
# <a name="net-runtime-garbage-collection-events"></a>.NET çalışma zamanı atık toplama olayları

Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar. Çöp toplamanın kaç kez gerçekleştirildiğini belirleme, çöp toplama sırasında ne kadar bellek serbest bırakılmış vb. gibi tanılama ve hata ayıklama konusunda yardımcı olurlar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

## <a name="gcstart_v2-event"></a>GCStart_V2 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCStart_V1`|1|Çöp toplama işlemi başlatıldı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|*N*. çöp toplama.|
|`Depth`|`win:UInt32`|Toplanmakta olan oluşturma.|
|`Reason`|`win:UInt32`|Çöp toplamanın neden tetiklendiği:<br /><br /> `0x0` -Küçük nesne yığını ayırması.<br /><br /> `0x1` Zorlanmadı.<br /><br /> `0x2` -Düşük bellek.<br /><br /> `0x3` Olmamalıdır.<br /><br /> `0x4` -Büyük nesne yığını ayırması.<br /><br /> `0x5` -Alan kalmadı (küçük nesne yığını için).<br /><br /> `0x6` -Alan kalmadı (büyük nesne yığını için).<br /><br /> `0x7` -Alınmış ancak engelleme olarak zorlanmadı.|
|`Type`|`win:UInt32`|`0x0` -Arka plan atık toplama dışında çöp toplama engelleme gerçekleşti.<br /><br /> `0x1` -Arka plan atık toplama.<br /><br /> `0x2` -Arka plan atık toplama sırasında atık toplamayı engelleme oluştu.|
|`ClrInstanceID`|Win: UInt16|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcend_v1-event"></a>GCEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCEnd_V1`|2|Çöp toplama sona erdi.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|*N*. çöp toplama.|
|`Depth`|`win:UInt32`|Toplanan nesil.|
|`ClrInstanceID`|Win: UInt16|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcheapstats_v2-event"></a>GCHeapStats_V2 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|4|Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|0. nesil belleğin bayt cinsinden boyutu.|
|`TotalPromotedSize0`|`win:UInt64`|Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.|
|`GenerationSize1`|`win:UInt64`|1. nesil belleğin bayt cinsinden boyutu.|
|`TotalPromotedSize1`|`win:UInt64`|1. nesil 2 ' ye kadar yükseltilen bayt sayısı.|
|`GenerationSize2`|`win:UInt64`|2. nesil belleğin bayt cinsinden boyutu.|
|`TotalPromotedSize2`|`win:UInt64`|Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.|
|`GenerationSize3`|`win:UInt64`|Büyük nesne yığınının bayt cinsinden boyutu.|
|`TotalPromotedSize3`|`win:UInt64`|Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.|
|`FinalizationPromotedSize`|`win:UInt64`|Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.|
|`FinalizationPromotedCount`|`win:UInt64`|Sonlandırmaya hazırlanma nesne sayısı.|
|`PinnedObjectCount`|`win:UInt32`|Sabitlenmiş (taşınamaz) nesne sayısı.|
|`SinkBlockCount`|`win:UInt32`|Kullanımdaki eşitleme bloklarının sayısı.|
|`GCHandleCount`|`win:UInt32`|Kullanımdaki çöp toplama tanıtıcılarının sayısı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|
|`GenerationSize4`|`win:UInt64`|Sabitlenmiş nesne yığınının bayt cinsinden boyutu.|
|`TotalPromotedSize4`|`win:UInt64`|Son koleksiyondan sonra sabitlenmiş nesne yığınında kalan bayt sayısı.|

## <a name="gccreatesegment_v1-event"></a>GCCreateSegment_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|5|Yeni bir atık toplama segmenti oluşturuldu. Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|Segmentin adresi.|
|`Size`|`win:UInt64`|Segmentin boyutu.|
|`Type`|`win:UInt32`|0x0-küçük nesne yığını.<br /><br /> 0x1-büyük nesne yığını.<br /><br /> 0x2-salt okunurdur yığın.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın. Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.

## <a name="gcfreesegment_v1-event"></a>GCFreeSegment_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|6|Çöp toplama segmenti yayınlandı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|Segmentin adresi.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcrestarteebegin_v1-event"></a>GCRestartEEBegin_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|7|Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.|

Bu olay hiçbir olay verisine sahip değil.

## <a name="gcrestarteeend_v1-event"></a>GCRestartEEEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|3|Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.|

Bu olay hiçbir olay verisine sahip değil.

## <a name="gcsuspendeeend_v1-event"></a>GCSuspendEEEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|8|Çöp toplama için yürütme altyapısının askıya alınma sonu.|

Bu olay hiçbir olay verisine sahip değil.

## <a name="gcsuspendeebegin_v1-event"></a>GCSuspendEEBegin_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|8|Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|*N*. çöp toplama.|
|`Reason`|`win:UInt32`|EE askıya alma nedeni.<br/><br/>`0x0`: Diğerleri için askıya al<br/><br/>`0x1`: GC için askıya alın.<br/><br/>`0x2`: AppDomain kapatması için askıya al.<br/><br/>`0x3`: Kod alma için askıya al.<br/><br/>`0x4`: Kapat için askıya al.<br/><br/>`0x5`: Hata ayıklayıcı için askıya al.<br/><br/>`0x6`: GC hazırlığı için askıya alın.<br/><br/>`0x7`: Hata ayıklayıcı tarama için askıya al|

## <a name="gcallocationtick_v3-event"></a>GCAllocationTick_V3 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Verbose (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|10|Yaklaşık 100 KB ayrıldığı her seferinde.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|Bayt cinsinden ayırma boyutu. Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur. Ayırma daha büyükse, bu alan kesilmiş bir değer içerir. `AllocationAmount64`Çok büyük ayırmalar için kullanın.|
|`AllocationKind`|`win:UInt32`|`0x0` -Küçük nesne ayırma (ayırma küçük nesne yığınında).<br /><br /> `0x1` -Büyük nesne ayırma (ayırma büyük nesne yığınında).|
|`AllocationAmount64`|`win:UInt64`|Bayt cinsinden ayırma boyutu. Bu değer, çok büyük ayırmalar için doğrudur.|
|`TypeId`|`win:Pointer`|MethodTable 'ın adresi. Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.|
|`TypeName`|`win:UnicodeString`|Ayrılan türün adı. Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).|
|`HeapIndex`|`win:UInt32`|Nesnenin ayrıldığı yığın. Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.|
|`Address`|`win:Pointer`|Son ayrılan nesnenin adresi.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gccreateconcurrentthread_v1-event"></a>GCCreateConcurrentThread_V1 Olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|11|Eşzamanlı atık toplama iş parçacığı oluşturuldu.|

Bu olay hiçbir olay verisine sahip değil.

## <a name="gcterminateconcurrentthread_v1-event"></a>GCTerminateConcurrentThread_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|12|Eşzamanlı atık toplama iş parçacığı sonlandırıldı.|

Bu olay hiçbir olay verisine sahip değil.

## <a name="gcfinalizersbegin_v1-event"></a>GCFinalizersBegin_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|14|Sonlandırıcıları çalıştırmanın başlangıcı.|

Bu olay hiçbir olay verisine sahip değil.

## <a name="gcfinalizersend_v1-event"></a>GCFinalizersEnd_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|13|Sonlandırıcılardan çalıştırmanın sonu.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|Çalıştırılan sonlandırıcılar sayısı.|
|`ClrInstanceID`|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="setgchandle-event"></a>SetGCHandle olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCHandleKeyword` 0x2|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`SetGCHandle`|30|GC tanıtıcısı ayarlandı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|Ayrılmış tanıtıcının adresi.|
|`ObjectID`|`win:Pointer`|Tutamacı oluşturulan nesnenin adresi.|
|`Kind`|`win:UInt32`|Ayarlanan GC tanıtıcısının türü. <br /><br />`0x0`: WeakShort <br/><br/>`0x1`: WeakLong <br /><br />`0x2`: Strong <br /><br />`0x3`: Sabitlenmiş <br /><br />`0x4`: Değişken<br /><br />`0x5`: Refsayılan <br /><br />`0x6`: Bağımlı<br /><br />`0x7`: Asyncpınlan<br /><br />`0x8`: SizedRef|
|`Generation`|`win:UInt32`|Tutamacı oluşturulduğu nesnenin oluşturulması.|
|`AppDomainID`|`win:UInt64`|AppDomain KIMLIĞI.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="destroygchandle-event"></a>DestroyGCHandle olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCHandleKeyword` 0x2|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|31|GC tanıtıcısı yok edilir.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|Yok etme tanıtıcısının adresi.|
|`ClrInstanceID`|Win: UInt16|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="pinobjectatgctime-event"></a>PinObjectAtGCTime olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Verbose (5)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|33|GC sırasında bir nesne sabitlendi.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|Tanıtıcının adresi.|
|`ObjectID`|`win:Pointer`|Sabitlenmiş nesnenin adresi.|
|`ObjectSize`|`win:UInt64`|Sabitlenmiş nesnenin boyutu.|
|`TypeName`|`win:UnicodeString`|Sabitlenmiş nesnenin türünün adı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gctriggered-event"></a>GCTriggered olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Verbose (5)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCTriggered`|33|GC tetiklendi.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|GC 'nin tetiklenme nedeni.<br/><br/>`0x0`: AllocSmall<br/><br/>`0x1`: Alınmış <br/><br/>`0x2`: LowMemory <br/><br/>`0x3`: Boş <br/><br/>`0x4`: AllocLarge <br/><br/>`0x5`: OutOfSpaceSmallObjectHeap <br/><br/>`0x6`: OutOfSpaceLargeObjectHeap <br/><br/>`0x7`:InducedNoForce <br/><br/>`0x8`: Stres <br/><br/>`0x9`: Endücedlowmemory|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="increasememorypressure-event"></a>Increasememorypresbir olay

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgi (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|200|Bellek baskısı arttı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan Adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ClrInstanceID`|Win: UInt16|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="decreasememorypressure-event"></a>DecreaseMemoryPressure olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgi (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|201|Bellek baskısı azaltılmıştı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan Adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|Serbest bırakılan bayt.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="gcmarkwithtype-event"></a>GCMarkWithType olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Bilgi (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|----------------|---------------|-----------------|
|`GCMarkWithType`|202|GC işareti aşamasında bir GC kökü işaretlendi.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan Adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|Yığın numarası.|
|`ClrInstanceID`|Win: UInt16|CoreCLR örneği için benzersiz KIMLIK.|
|`Type`|`win:UInt32`|GC kök türü.<br/><br/>`0x0`: Yığın<br/><br/>`0x1`: Sonlandırıcı<br/><br/>`0x2`: Tanıtıcı<br/><br/>`0x3`: Daha eski<br/><br/>`0x4`: SizedRef<br/><br/>`0x5`: Taşma<br/><br/>|
|`Bytes`|`win:UInt64`|İşaretlenmiş baytların sayısı.|

## <a name="gcjoin_v2-event"></a>GCJoin_V2 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`GCKeyword` 0x1|Verbose (5)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`GCJoin_V2`|203|Birleştirilmiş bir GC iş parçacığı.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|Yığın numarası|
|`JoinTime`|`win:UInt32`|Bu olayın birleştirmenin başlangıcında mi, yoksa bir birleşimin sonunda mi tetiklendiğini belirtir (JOIN `0x0` için, `0x1` JOIN End for JOIN için)|
|`JoinType`|`win:UInt32`|JOIN türü. <br/><br/>`0x0`: Son ekleme<br/><br/>`0x1`: Birleştir <br/><br/>`0x2`: Yeniden Başlat <br/><br/>`0x3`: İlk olarak katılmayı geri çevir<br/><br/>`0x4`: Ters Birleştir<br/><br/>|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|
