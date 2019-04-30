---
title: Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85ca55e976a010a4875d260b3da30f5bc3cf2ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723621"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları

Görev paralel kitaplığı ve PLINQ'da profilini ve Windows Performans Çözümleyicisi gibi araçları kullanarak uygulama sorunlarını giderme için kullanabileceğiniz olay izleme için Windows (ETW) olayları oluşturun. Ancak, çoğu senaryoda, profili paralel uygulama kodunun en iyi yolu kullanmaktır [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) Visual Studio'da.

## <a name="task-parallel-library-etw-events"></a>Görev paralel kitaplığı ETW olayları

Tarafından oluşturulan olayları providerID GUID EVENT_HEADER yapısında <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> olan:

```
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5
```

### <a name="parallel-loop-begin"></a>Paralel döngü başla

EVENT_DESCRIPTOR.Task = 1

EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü belirtir:<br /><br /> 1 Parallelınvoke =<br /><br /> 2 ParallelFor =<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacı başlangıç değeri|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacı bitiş değeri|

### <a name="parallel-loop-end"></a>Paralel döngü son
 EVENT_DESCRIPTOR.Task = 2

 EVENT_DESCRIPTOR.Id = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yineleme toplam sayısı|

### <a name="parallel-invoke-begin"></a>Başlangıç paralel çağırma
 EVENT_DESCRIPTOR.Task = 3

 EVENT_DESCRIPTOR.Id = 3

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yineleme toplam sayısı|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü belirtir:<br /><br /> 1 Parallelınvoke =<br /><br /> 2 ParallelFor =<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Paralel Invoke içinde yürütülen eylem sayısı.|

### <a name="parallel-invoke-end"></a>Son paralel çağırma
 EVENT_DESCRIPTOR.Task = 4

 EVENT_DESCRIPTOR.Id = 4

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçirme ve çatal/birleştir semantiğine sahip olaylar için çiftleri göstermek için kullanılan benzersiz tanımlayıcısı.|

## <a name="plinq-etw-events"></a>PLINQ ETW Events
 EVENT_HEADER. PLINQ providerID GUID değeridir:

```
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87
```

### <a name="parallel-query-begin"></a>Paralel sorgu başlangıç
 EVENT_DESCRIPTOR.Task = 1

 EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Bir sorgu benzersiz tanımlayıcısı.|

### <a name="parallel-query-end"></a>Paralel sorgu bitiş olayı
 EVENT_DESCRIPTOR.Task = 2

 EVENT_DESCRIPTOR.Id = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü çalışmaya TaskScheduler kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Bir sorgu benzersiz tanımlayıcısı.|

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te ETW Olayları](../../../docs/framework/performance/etw-events.md)
- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
