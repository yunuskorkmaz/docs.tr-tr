---
title: ThreadPool çalışma zamanı olayları
description: .NET Core 'da iş parçacığı havuzu hakkında tanılama bilgilerini toplayacak .NET Runtime iş parçacığı havuzu olayları bölümüne bakın. İş parçacığı havuzu olayları, çalışan iş parçacığı havuzu olayları veya g/ç iş parçacığı havuzu olaylardır.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96590045"
---
# <a name="net-runtime-thread-pool-events"></a>.NET çalışma zamanı iş parçacığı havuzu olayları

Bu olaylar, ThreadPool içindeki çalışan ve g/ç iş parçacıkları hakkında bilgi toplar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

## <a name="iothreadcreate_v1-event"></a>IOThreadCreate_V1 olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|44|İş parçacığı havuzunda bir g/ç iş parçacığı oluşturulur.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|Yeni oluşturulan iş parçacığı dahil olmak üzere g/ç iş parçacıklarının sayısı.|
|`NumRetired`|`win:UInt64`|Kullanımdan kaldırılan çalışan iş parçacıklarının sayısı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="iothreadterminate_v1-event"></a>IOThreadTerminate_V1 olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir

|Olayı yükseltmek için anahtar sözcük|Level
|-----------------------------------|-----------
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|45|İş parçacığı havuzunda bir g/ç iş parçacığı sonlandırılır.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.|
|`NumRetired`|`win:UInt64`|Kullanımdan kaldırılan g/ç iş parçacığı sayısı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="iothreadretire_v1-event"></a>IOThreadRetire_V1 olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|46|Bir g/ç iş parçacığı bir kullanımdan kaldırma adayı haline gelir.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.|
|`NumRetired`|`win:UInt64`|Kullanımdan kaldırılan g/ç iş parçacığı sayısı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="iothreadunretire_v1-event"></a>IOThreadUnretire_V1 olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|47|Bir g/ç iş parçacığı, iş parçacığı bir kullanımdan kaldırma adayı olduktan sonra bekleme süresi içinde ulaşan g/ç nedeniyle kullanımdan kaldırıldı.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|Bu dahil iş parçacığı havuzundaki g/ç iş parçacıklarının sayısı.|
|`NumRetired`|`win:UInt64`|Kullanımdan kaldırılan g/ç iş parçacığı sayısı.|
|`ClrInstanceID`|`Win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadstart-event"></a>ThreadPoolWorkerThreadStart olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|50|Bir çalışan iş parçacığı oluşturulur.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadstop-event"></a>ThreadPoolWorkerThreadStop olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|51|Çalışan iş parçacığı durduruldu.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadwait-event"></a>ThreadPoolWorkerThreadWait olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|57|Çalışan iş parçacığı çalışmaya başlar.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadretirementstart-event"></a>ThreadPoolWorkerThreadRetirementStart olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|52|Bir çalışan iş parçacığı yeniden oluşturma.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadretirementstop-event"></a>ThreadPoolWorkerThreadRetirementStop olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|53|Kullanımdan kaldırılan bir çalışan iş parçacığı yeniden etkin hale gelir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.|
|`RetiredWorkerThreadCount`|`win:UInt32`|Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a>Threadpoolworkerthreadadadatmentsample olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Bir örnek için bilgi toplamayı ifade eder; diğer bir deyişle, belirli bir eşzamanlılık düzeyi olan aktarım hızı, zaman içinde bir ölçümdür.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|Zaman birimi başına tamamlama sayısı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a>Threadpoolworkerthreadadyatmentadolayını ayarlama olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|İş parçacığı ekleme (Hill-climbing) algoritması eşzamanlılık düzeyindeki bir değişikliğin yerinde olduğunu belirlediğinde denetimdeki bir değişikliği kaydeder.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|Ölçüm örneğinin ortalama performansı.|
|`NewWorkerThreadCount`|`win:UInt32`|Yeni etkin çalışan iş parçacığı sayısı.|
|`Reason`|`win:UInt32`|Ayarlamanın nedeni.<br /><br /> `0x0` Isınma.<br /><br /> `0x1` Başlatarak.<br /><br /> `0x2` -Rastgele taşı.<br /><br /> `0x3` -Geçiş taşı.<br /><br /> `0x4` -Değişiklik noktası.<br /><br /> `0x5` Sabitleniyor.<br /><br /> `0x6` Yetersizliğine neden olabilir.<br /><br /> `0x7` -İş parçacığı zaman aşımına uğradı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a>Threadpoolworkerthreadadadatmentstats olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Verbose (5)

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|56|İş parçacığı havuzundaki verileri toplar.|

 Aşağıdaki tabloda olay verileri gösterilmektedir

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|Bu istatistiklerin toplandığı sürenin saniye cinsinden miktarı.|
|`Throughput`|`win:Double`|Bu Aralık sırasında saniye başına ortalama tamamlama sayısı.|
|`ThreadWave`|`win:Double`|Dahili kullanım için ayrılmıştır.|
|`ThroughputWave`|`win:Double`|Dahili kullanım için ayrılmıştır.|
|`ThroughputErrorEstimate`|`win:Double`|Dahili kullanım için ayrılmıştır.|
|`AverageThroughputErrorEstimate`|`win:Double`|Dahili kullanım için ayrılmıştır.|
|`ThroughputRatio`|`win:Double`|Bu zaman aralığı boyunca etkin çalışan iş parçacığı sayısında değişimler nedeniyle üretilen iş akışındaki göreli geliştirme.|
|`Confidence`|`win:Double`|ThroughputRatio alanının geçerlilik süresinin ölçüsü.|
|`NewcontrolSetting`|`win:Double`|Etkin iş parçacığı sayısında gelecekteki Çeşitlemeler için temel olarak görev yapacak etkin çalışan iş parçacıklarının sayısı.|
|`NewThreadWaveMagnitude`|`win:UInt16`|Etkin iş parçacığı sayısı ' nda gelecekteki varyasyonların büyüklüğü.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolenqueue-event"></a>ThreadPoolEnqueue olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Verbose (5)

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|61|İş öğesi, iş parçacığı havuzu kuyruğunda sıraya alındı.|

 Aşağıdaki tabloda olay verileri gösterilmektedir

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|İş isteğine yönelik işaretçi.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpooldequeue-event"></a>Threadpoolsıradan çıkarma olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Verbose (5)

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|62|İş öğesi, iş parçacığı havuzu sırasından kuyruğa alındı.|

 Aşağıdaki tabloda olay verileri gösterilmektedir

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|İş isteğine yönelik işaretçi.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpoolioenqueue-event"></a>Threadpokayokuyruğa alma olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Verbose (5)

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|63|Bir iş parçacığı, zaman uyumsuz GÇ tamamlandıktan sonra bir GÇ tamamlama bildirimini sıraya alır.|

 Aşağıdaki tabloda olay verileri gösterilmektedir

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|Dahili kullanım için ayrılmıştır.|
|`Overlapped`|`win:Pointer`|Dahili kullanım için ayrılmıştır.|
|`MultiDequeues`|`win:Boolean`|Dahili kullanım için ayrılmıştır.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpooliodequeue-event"></a>Threadpokaykıosıradan çıkarma olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Verbose (5)

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|64|Bir iş parçacığı GÇ tamamlama bildirimini kaldırır.|

 Aşağıdaki tabloda olay verileri gösterilmektedir

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|Dahili kullanım için ayrılmıştır.|
|`Overlapped`|`win:Pointer`|Dahili kullanım için ayrılmıştır.|
|`MultiDequeues`|`win:Boolean`|Dahili kullanım için ayrılmıştır.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadpooliopack-event"></a>ThreadPoolIOPack olayı

 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Verbose (5)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|65|İş parçacığı çakışan GÇ paketi çağırılır.|

 Aşağıdaki tabloda olay verileri gösterilmektedir

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|Dahili kullanım için ayrılmıştır.|
|`Overlapped`|`win:Pointer`|Dahili kullanım için ayrılmıştır.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadcreating-event"></a>Threadevent oluşturma

 Aşağıdaki tabloda anahtar kelimeleri ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|----------------|---------------|-----------------|
|`ThreadCreating`|70|İş parçacığı oluşturuldu.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|İş parçacığı KIMLIĞI|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadrunning-event"></a>ThreadRunning olayı

 Aşağıdaki tabloda anahtar kelimeleri ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|----------------|---------------|-----------------|
|`ThreadRunning`|71|İş parçacığı çalışmaya başladı.|

 Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|İş parçacığı KIMLIĞI|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|
