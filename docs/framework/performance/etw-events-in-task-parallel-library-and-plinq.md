---
title: Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b5281b90605f14b75b4537333378903d5f67817
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778279"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları

Görev paralel kitaplığı ve PLINQ'da profilini ve Windows Performans Çözümleyicisi gibi araçları kullanarak uygulama sorunlarını giderme için kullanabileceğiniz olay izleme için Windows (ETW) olayları oluşturun. Ancak, çoğu senaryoda, profili paralel uygulama kodunun en iyi yolu kullanmaktır [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) Visual Studio'da.

## <a name="task-parallel-library-etw-events"></a>Görev paralel kitaplığı ETW olayları

Tarafından oluşturulan olayları providerID GUID EVENT_HEADER yapısında <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> olan:

```
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5
```

### <a name="parallel-loop-begin"></a>Paralel döngü başla

EVENT_DESCRIPTOR. Görev 1 =

EVENT_DESCRIPTOR. ID = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Türü**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü belirtir:<br /><br /> 1 Parallelınvoke =<br /><br /> 2 ParallelFor =<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacı başlangıç değeri|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacı bitiş değeri|

### <a name="parallel-loop-end"></a>Paralel döngü son
 EVENT_DESCRIPTOR. Görev 2 =

 EVENT_DESCRIPTOR. ID = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Türü**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yineleme toplam sayısı|

### <a name="parallel-invoke-begin"></a>Başlangıç paralel çağırma
 EVENT_DESCRIPTOR. Görev 3 =

 EVENT_DESCRIPTOR. Kimlik = 3

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Türü**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yineleme toplam sayısı|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü belirtir:<br /><br /> 1 Parallelınvoke =<br /><br /> 2 ParallelFor =<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Paralel Invoke içinde yürütülen eylem sayısı.|

### <a name="parallel-invoke-end"></a>Son paralel çağırma
 EVENT_DESCRIPTOR. Görev 4 =

 EVENT_DESCRIPTOR. ID = 4

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Türü**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|

## <a name="plinq-etw-events"></a>PLINQ ETW olayları
 EVENT_HEADER. PLINQ providerID GUID değeridir:

```
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87
```

### <a name="parallel-query-begin"></a>Paralel sorgu başlangıç
 EVENT_DESCRIPTOR. Görev 1 =

 EVENT_DESCRIPTOR. ID = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Türü**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Bir sorgu benzersiz tanımlayıcısı.|

### <a name="parallel-query-end"></a>Paralel sorgu bitiş olayı
 EVENT_DESCRIPTOR. Görev 2 =

 EVENT_DESCRIPTOR. ID = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Türü**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Bir sorgu benzersiz tanımlayıcısı.|

## <a name="see-also"></a>Ayrıca Bkz.

- [.NET Framework'te ETW Olayları](../../../docs/framework/performance/etw-events.md)
- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
