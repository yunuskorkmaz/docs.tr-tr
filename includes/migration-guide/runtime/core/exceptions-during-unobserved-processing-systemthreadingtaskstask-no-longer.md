---
ms.openlocfilehash: bae211e5684dc1fbbb1d7e69c928e37c1c532096
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497113"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a><span data-ttu-id="fa5be-101">System. Threading. Tasks. Task içinde gözlemlenmemiş işlem sırasında özel durumlar artık Sonlandırıcı iş parçacığında yaymaz</span><span class="sxs-lookup"><span data-stu-id="fa5be-101">Exceptions during unobserved processing in System.Threading.Tasks.Task no longer propagate on finalizer thread</span></span>

#### <a name="details"></a><span data-ttu-id="fa5be-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fa5be-102">Details</span></span>

<span data-ttu-id="fa5be-103"><xref:System.Threading.Tasks.Task?displayProperty=fullName>Sınıfı zaman uyumsuz bir işlemi temsil ettiğinden, zaman uyumsuz işleme sırasında oluşan tüm önemli olmayan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="fa5be-103">Because the <xref:System.Threading.Tasks.Task?displayProperty=fullName> class represents an asynchronous operation, it catches all non-severe exceptions that occur during asynchronous processing.</span></span> <span data-ttu-id="fa5be-104">.NET Framework 4,5 ' de, bir özel durum gözlemlenmez ve kodunuz görevde hiçbir zaman beklemeyeceğini, özel durum artık Sonlandırıcı iş parçacığı üzerinde yayılmaz ve çöp toplama sırasında işlemi kilitetmez.</span><span class="sxs-lookup"><span data-stu-id="fa5be-104">In the .NET Framework 4.5, if an exception is not observed and your code never waits on the task, the exception will no longer propagate on the finalizer thread and crash the process during garbage collection.</span></span> <span data-ttu-id="fa5be-105">Bu değişiklik, gözlemlenen zaman uyumsuz işleme gerçekleştirmek için görev sınıfını kullanan uygulamaların güvenilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="fa5be-105">This change enhances the reliability of applications that use the Task class to perform unobserved asynchronous processing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fa5be-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="fa5be-106">Suggestion</span></span>

<span data-ttu-id="fa5be-107">Bir uygulama, Sonlandırıcı iş parçacığına yayılan, gözlemlenen zaman uyumsuz özel durumlara bağımlıysa, önceki davranış olay için uygun bir işleyicinin sağlanması <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> veya bir [çalışma zamanı yapılandırma öğesi](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)ayarlanarak geri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fa5be-107">If an app depends on unobserved asynchronous exceptions propagating to the finalizer thread, the previous behavior can be restored by providing an appropriate handler for the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event, or by setting a [runtime configuration element](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).</span></span>

| <span data-ttu-id="fa5be-108">Name</span><span class="sxs-lookup"><span data-stu-id="fa5be-108">Name</span></span>    | <span data-ttu-id="fa5be-109">Değer</span><span class="sxs-lookup"><span data-stu-id="fa5be-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fa5be-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fa5be-110">Scope</span></span>   |<span data-ttu-id="fa5be-111">Edge</span><span class="sxs-lookup"><span data-stu-id="fa5be-111">Edge</span></span>|
|<span data-ttu-id="fa5be-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fa5be-112">Version</span></span>|<span data-ttu-id="fa5be-113">4,5</span><span class="sxs-lookup"><span data-stu-id="fa5be-113">4.5</span></span>|
|<span data-ttu-id="fa5be-114">Tür</span><span class="sxs-lookup"><span data-stu-id="fa5be-114">Type</span></span>|<span data-ttu-id="fa5be-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="fa5be-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fa5be-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fa5be-116">Affected APIs</span></span>

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
