---
ms.openlocfilehash: b0e6d6f228647148083d3df64e65f817dc3455d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235891"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Artık System.Threading.Tasks.Task içinde gözetimsiz işleme sırasında özel durumları Sonlandırıcı iş parçacığında yayılmaz

|   |   |
|---|---|
|Ayrıntılar|Çünkü <xref:System.Threading.Tasks.Task?displayProperty=name> sınıfı zaman uyumsuz bir işlem sunduğundan, zaman uyumsuz işleme süresince ortaya çıkan tüm önemli olmayan özel durumları yakalar. .NET Framework 4.5, bir durum gözlenmezse ve kodunuz görevde beklemezse, özel durum artık Sonlandırıcı iş parçacığında yayılmaz ve çöp toplama sırasında işlemi kilitlenme. Bu değişiklik, gözetimsiz zaman uyumsuz işleme gerçekleştirmek için görev sınıfını kullanan uygulamaların güvenilirliğini arttırır.|
|Öneri|Gözetimsiz zaman uyumsuz özel durumları Sonlandırıcı iş parçacığı için yayma uygulama bağlıdır, önceki davranışı için uygun tanıtıcının sağlanmasıyla geri alınabilir <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> olay veya ayarlayarak bir [çalışma zamanı yapılandırma öğesi ](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
