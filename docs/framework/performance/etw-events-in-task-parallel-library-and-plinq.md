---
title: Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları
description: Paralel kitaplık ve PLıNQ görevi içindeki ETW olayları hakkında bilgi edinin. Uygulamaları profil ve sorunlarını gidermek için bu olayları kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
ms.openlocfilehash: 4cb4967ea704064ae08d09311ff33720e3871e19
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263652"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları

Hem görev paralel kitaplığı hem de PLıNQ, Windows Performans Çözümleyicisi gibi araçları kullanarak uygulamaları profil oluşturmak ve sorunlarını gidermek için kullanabileceğiniz Windows için olay Izleme (ETW) olayları oluştur. Ancak çoğu senaryoda, paralel uygulama kodu profilini oluşturmanın en iyi yolu, Visual Studio 'da [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) kullanmaktır.

## <a name="task-parallel-library-etw-events"></a>Görev paralel kitaplığı ETW olayları

EVENT_HEADER yapısında, ve tarafından oluşturulan olaylar için SağlayıcıKimliği GUID 'SI <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> :

`0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5`

### <a name="parallel-loop-begin"></a>Paralel döngü başlangıcı

EVENT_DESCRIPTOR. Görev = 1

EVENT_DESCRIPTOR. Kimlik = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler KIMLIĞI.|
|Originatingtaskıd|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin KIMLIĞI.|
|Forkjoincontextıd|<xref:System.Int32?displayProperty=nameWithType>|Çatal/JOIN semantiğinin bulunduğu olaylar için iç içe ve çiftleri göstermek üzere kullanılan benzersiz bir tanımlayıcı.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü belirtir:<br /><br /> 1 = Paralellinvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|Yani,|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacının başlangıç değeri|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacının bitiş değeri|

### <a name="parallel-loop-end"></a>Paralel döngü bitişi

 EVENT_DESCRIPTOR. Görev = 2

 EVENT_DESCRIPTOR. Kimlik = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler KIMLIĞI.|
|Originatingtaskıd|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin KIMLIĞI.|
|Forkjoincontextıd|<xref:System.Int32?displayProperty=nameWithType>|Çatal/JOIN semantiğinin bulunduğu olaylar için iç içe ve çiftleri göstermek üzere kullanılan benzersiz bir tanımlayıcı.|
|Totalyinelemelerde|<xref:System.Int64?displayProperty=nameWithType>|Toplam yineleme sayısı|

### <a name="parallel-invoke-begin"></a>Parallel Invoke BEGIN

 EVENT_DESCRIPTOR. Görev = 3

 EVENT_DESCRIPTOR. Kimlik = 3

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler KIMLIĞI.|
|Originatingtaskıd|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin KIMLIĞI.|
|Forkjoincontextıd|<xref:System.Int32?displayProperty=nameWithType>|Çatal/JOIN semantiğinin bulunduğu olaylar için iç içe ve çiftleri göstermek üzere kullanılan benzersiz bir tanımlayıcı.|
|Totalyinelemelerde|<xref:System.Int64?displayProperty=nameWithType>|Toplam yineleme sayısı|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü belirtir:<br /><br /> 1 = Paralellinvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Paralel Invoke içinde yürütülecek eylemlerin sayısı.|

### <a name="parallel-invoke-end"></a>Paralel çağırma bitişi

 EVENT_DESCRIPTOR. Görev = 4

 EVENT_DESCRIPTOR. Kimlik = 4

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler KIMLIĞI.|
|Originatingtaskıd|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin KIMLIĞI.|
|Forkjoincontextıd|<xref:System.Int32?displayProperty=nameWithType>|Çatal/JOIN semantiğinin bulunduğu olaylar için iç içe ve çiftleri göstermek üzere kullanılan benzersiz bir tanımlayıcı.|

## <a name="plinq-etw-events"></a>PLıNQ ETW olayları

 EVENT_HEADER. PLıNQ için SağlayıcıKimliği GUID 'SI:

`0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87`

### <a name="parallel-query-begin"></a>Paralel sorgu başlangıcı

 EVENT_DESCRIPTOR. Görev = 1

 EVENT_DESCRIPTOR. Kimlik = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler KIMLIĞI.|
|Originatingtaskıd|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin KIMLIĞI.|
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Benzersiz bir sorgu tanımlayıcısı.|

### <a name="parallel-query-end"></a>Paralel sorgu bitişi

 EVENT_DESCRIPTOR. Görev = 2

 EVENT_DESCRIPTOR. Kimlik = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Ad**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler KIMLIĞI.|
|Originatingtaskıd|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin KIMLIĞI.|
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Benzersiz bir sorgu tanımlayıcısı.|

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te ETW Olayları](etw-events.md)
- [Görev Paralel Kitaplığı (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralel LINQ (PLINQ)](../../standard/parallel-programming/introduction-to-plinq.md)
