---
title: Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
ms.openlocfilehash: 61429babf7378b9d271ffd60a6228ae4bfe7a5e5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644255"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları

Hem Görev Paralel Kitaplığı hem de PLINQ, Windows Performans Çözümleyicisi gibi araçları kullanarak uygulamaları profillemek ve sorun gidermek için kullanabileceğiniz Windows için Olay İzleme (ETW) olayları oluşturur. Ancak, çoğu senaryoda, paralel uygulama kodunu profillemenin en iyi yolu Visual Studio'da [Eşzamanlılık Görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) kullanmaktır.

## <a name="task-parallel-library-etw-events"></a>Görev Paralel Kütüphane ETW Olaylar

EVENT_HEADER yapısında, sağlayıcı tarafından <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>oluşturulan olaylar <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> için <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> GUID ve:

`0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5`

### <a name="parallel-loop-begin"></a>Paralel Döngü Başlangıç

EVENT_DESCRIPTOR. Görev = 1

EVENT_DESCRIPTOR. Id = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Adı**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|KaynakTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler'ın kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Çatal/birleştirme semantikli olaylar için iç içe geçme ve çiftleri belirtmek için kullanılan benzersiz bir tanımlayıcı.|
|Operationtype|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü gösterir:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParalelForeach|
|Dahil From|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacının başlangıç değeri|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacının bitiş değeri|

### <a name="parallel-loop-end"></a>Paralel Döngü Sonu
 EVENT_DESCRIPTOR. Görev = 2

 EVENT_DESCRIPTOR. Id = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Adı**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|KaynakTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler'ın kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Çatal/birleştirme semantikli olaylar için iç içe geçme ve çiftleri belirtmek için kullanılan benzersiz bir tanımlayıcı.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yinelemelerin toplam sayısı|

### <a name="parallel-invoke-begin"></a>Paralel Çağrı Başlat
 EVENT_DESCRIPTOR. Görev = 3

 EVENT_DESCRIPTOR. Id = 3

#### <a name="user-data"></a>Kullanıcı Verileri

|**Adı**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|KaynakTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler'ın kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Çatal/birleştirme semantikli olaylar için iç içe geçme ve çiftleri belirtmek için kullanılan benzersiz bir tanımlayıcı.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yinelemelerin toplam sayısı|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü gösterir:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParalelForeach|
|Eylem Sayısı|<xref:System.Int32?displayProperty=nameWithType>|Paralel çağrıda yürütülecek eylemlerin sayısı.|

### <a name="parallel-invoke-end"></a>Paralel Çağırma Sonu
 EVENT_DESCRIPTOR. Görev = 4

 EVENT_DESCRIPTOR. Id = 4

#### <a name="user-data"></a>Kullanıcı Verileri

|**Adı**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|KaynakTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler'ın kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin kimliği.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Çatal/birleştirme semantikli olaylar için iç içe geçme ve çiftleri belirtmek için kullanılan benzersiz bir tanımlayıcı.|

## <a name="plinq-etw-events"></a>PLINQ ETW Etkinlikleri
 The EVENT_HEADER. PLINQ için ProviderId GUID:

`0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87`

### <a name="parallel-query-begin"></a>Paralel Sorgu Başla
 EVENT_DESCRIPTOR. Görev = 1

 EVENT_DESCRIPTOR. Id = 1

#### <a name="user-data"></a>Kullanıcı Verileri

|**Adı**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|KaynakTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler'ın kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin kimliği.|
|Queryıd|<xref:System.Int32?displayProperty=nameWithType>|Benzersiz bir sorgu tanımlayıcısı.|

### <a name="parallel-query-end"></a>Paralel Sorgu Sonu
 EVENT_DESCRIPTOR. Görev = 2

 EVENT_DESCRIPTOR. Id = 2

#### <a name="user-data"></a>Kullanıcı Verileri

|**Adı**|**Tür**|**Açıklama**|
|--------------|--------------|---------------------|
|KaynakTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan TaskScheduler'ın kimliği.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngüyü başlatan görevin kimliği.|
|Queryıd|<xref:System.Int32?displayProperty=nameWithType>|Benzersiz bir sorgu tanımlayıcısı.|

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te ETW Olayları](etw-events.md)
- [Görev Paralel Kitaplığı (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralel LINQ (PLINQ)](../../standard/parallel-programming/introduction-to-plinq.md)
