---
ms.openlocfilehash: bae211e5684dc1fbbb1d7e69c928e37c1c532096
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497113"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>System. Threading. Tasks. Task içinde gözlemlenmemiş işlem sırasında özel durumlar artık Sonlandırıcı iş parçacığında yaymaz

#### <a name="details"></a>Ayrıntılar

<xref:System.Threading.Tasks.Task?displayProperty=fullName>Sınıfı zaman uyumsuz bir işlemi temsil ettiğinden, zaman uyumsuz işleme sırasında oluşan tüm önemli olmayan özel durumları yakalar. .NET Framework 4,5 ' de, bir özel durum gözlemlenmez ve kodunuz görevde hiçbir zaman beklemeyeceğini, özel durum artık Sonlandırıcı iş parçacığı üzerinde yayılmaz ve çöp toplama sırasında işlemi kilitetmez. Bu değişiklik, gözlemlenen zaman uyumsuz işleme gerçekleştirmek için görev sınıfını kullanan uygulamaların güvenilirliğini geliştirir.

#### <a name="suggestion"></a>Öneri

Bir uygulama, Sonlandırıcı iş parçacığına yayılan, gözlemlenen zaman uyumsuz özel durumlara bağımlıysa, önceki davranış olay için uygun bir işleyicinin sağlanması <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> veya bir [çalışma zamanı yapılandırma öğesi](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)ayarlanarak geri yüklenebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.Run(System.Action)`
- `M:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})`
- `M:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)`
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{``0})``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{``0},System.Threading.CancellationToken)``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{System.Threading.Tasks.Task{``0}})``
- ``M:System.Threading.Tasks.Task.Run``1(System.Func{System.Threading.Tasks.Task{``0}},System.Threading.CancellationToken)``
- `M:System.Threading.Tasks.Task.Start`
- `M:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)`

-->
