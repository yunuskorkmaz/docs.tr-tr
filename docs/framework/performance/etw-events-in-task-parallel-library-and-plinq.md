---
title: "Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a84fdb104296cf15b5f0d2d04f4ddd7ea1419643
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Görev Paralel Kitaplığı ve PLINQ'da ETW Olayları
Görev paralel kitaplığı ve PLINQ'da profil ve uygulamaları Windows Performans Çözümleyicisi'ni gibi araçları kullanarak sorun gidermek için kullanabileceğiniz olay izleme için Windows (ETW) olayları oluşturur. Ancak, çoğu senaryoda, profil paralel uygulama kodu en iyi yolu kullanmaktır [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer) içinde [!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)].  
  
## <a name="task-parallel-library-etw-events"></a>Görev paralel kitaplığı ETW olayları  
 EVENT_HEADER bir yapı tarafından oluşturulan olayları için providerID GUID <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> değil:  
  
```  
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5  
```  
  
### <a name="parallel-loop-begin"></a>Paralel döngü başla  
 EVENT_DESCRIPTOR. Görev 1 =  
  
 EVENT_DESCRIPTOR. ID = 1  
  
#### <a name="user-data"></a>Kullanıcı Verileri  
  
|**Ad**|**Türü**|**Açıklama**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan TaskScheduler kimliği.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçme ve çatalı/birleşim anlamsallarını olan olaylar için çiftleri göstermek için kullanılan benzersiz bir tanımlayıcı.|  
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü gösterir:<br /><br /> 1 ParallelInvoke =<br /><br /> 2 ParallelFor =<br /><br /> 3 ParallelForEach =|  
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacı başlangıç değeri|  
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Döngü sayacı bitiş değeri|  
  
### <a name="parallel-loop-end"></a>Paralel döngü bitiş  
 EVENT_DESCRIPTOR. Görev 2 =  
  
 EVENT_DESCRIPTOR. ID = 2  
  
#### <a name="user-data"></a>Kullanıcı Verileri  
  
|**Ad**|**Türü**|**Açıklama**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan TaskScheduler kimliği.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçme ve çatalı/birleşim anlamsallarını olan olaylar için çiftleri göstermek için kullanılan benzersiz bir tanımlayıcı.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yineleme sayısı|  
  
### <a name="parallel-invoke-begin"></a>Paralel başlangıç çağırma  
 EVENT_DESCRIPTOR. Görev 3 =  
  
 EVENT_DESCRIPTOR. ID = 3  
  
#### <a name="user-data"></a>Kullanıcı Verileri  
  
|**Ad**|**Türü**|**Açıklama**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan TaskScheduler kimliği.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçme ve çatalı/birleşim anlamsallarını olan olaylar için çiftleri göstermek için kullanılan benzersiz bir tanımlayıcı.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Yineleme sayısı|  
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Döngü türünü gösterir:<br /><br /> 1 ParallelInvoke =<br /><br /> 2 ParallelFor =<br /><br /> 3 ParallelForEach =|  
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|İçinde paralel Invoke yürütülecek eylemlerin sayısı.|  
  
### <a name="parallel-invoke-end"></a>Paralel son çağırma  
 EVENT_DESCRIPTOR. Görev 4 =  
  
 EVENT_DESCRIPTOR. ID = 4  
  
#### <a name="user-data"></a>Kullanıcı Verileri  
  
|**Ad**|**Türü**|**Açıklama**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan TaskScheduler kimliği.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|İç içe geçme ve çatalı/birleşim anlamsallarını olan olaylar için çiftleri göstermek için kullanılan benzersiz bir tanımlayıcı.|  
  
## <a name="plinq-etw-events"></a>PLINQ ETW olayları  
 EVENT_HEADER. PLINQ providerID GUID'dir:  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### <a name="parallel-query-begin"></a>Paralel sorgu başla  
 EVENT_DESCRIPTOR. Görev 1 =  
  
 EVENT_DESCRIPTOR. ID = 1  
  
#### <a name="user-data"></a>Kullanıcı Verileri  
  
|**Ad**|**Türü**|**Açıklama**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan TaskScheduler kimliği.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|  
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Benzersiz sorgu tanımlayıcısı.|  
  
### <a name="parallel-query-end"></a>Paralel sorgu bitiş  
 EVENT_DESCRIPTOR. Görev 2 =  
  
 EVENT_DESCRIPTOR. ID = 2  
  
#### <a name="user-data"></a>Kullanıcı Verileri  
  
|**Ad**|**Türü**|**Açıklama**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan TaskScheduler kimliği.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|Döngü başlatılan görev kimliği.|  
|QueryId|<xref:System.Int32?displayProperty=nameWithType>|Benzersiz sorgu tanımlayıcısı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework'te ETW Olayları](../../../docs/framework/performance/etw-events.md)  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
