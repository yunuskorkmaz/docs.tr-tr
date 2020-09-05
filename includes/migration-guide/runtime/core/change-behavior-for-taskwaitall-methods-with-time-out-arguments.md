---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497262"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a><span data-ttu-id="0f221-101">Zaman aşımı bağımsız değişkenlerine sahip Task. WaitAll yöntemleri için davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="0f221-101">Change in behavior for Task.WaitAll methods with time-out arguments</span></span>

#### <a name="details"></a><span data-ttu-id="0f221-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0f221-102">Details</span></span>

<span data-ttu-id="0f221-103"><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> davranış, .NET Framework 4 ' te .NET Framework daha tutarlı yapıldı, bu yöntemler tutarsız şekilde davranmış.</span><span class="sxs-lookup"><span data-stu-id="0f221-103"><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> behavior was made more consistent in .NET Framework 4.5.In the .NET Framework 4, these methods behaved inconsistently.</span></span> <span data-ttu-id="0f221-104">Zaman aşımı süresi dolduğunda, bir veya daha fazla görev tamamlandıysa veya yöntem çağrısından önce iptal edildiyse, yöntem bir <xref:System.AggregateException?displayProperty=fullName> özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="0f221-104">When the time-out expired, if one or more tasks were completed or canceled before the method call, the method threw an <xref:System.AggregateException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="0f221-105">Zaman aşımı süresi dolduğunda, hiçbir görev tamamlanmadıysa veya yöntem çağrısından önce iptal edildiyse, ancak bir veya daha fazla görev bu durumlara yöntem çağrısından sonra girdiyse, yöntem false değerini döndürdü.</span><span class="sxs-lookup"><span data-stu-id="0f221-105">When the time-out expired, if no tasks were completed or canceled before the method call, but one or more tasks entered these states after the method call, the method returned false.</span></span><br/><br/><span data-ttu-id="0f221-106">.NET Framework 4,5 ' de, bu yöntem aşırı yüklemeleri, zaman aşımı süresi dolduğunda herhangi bir görev hala çalışıyorsa yanlış döndürür ve <xref:System.AggregateException?displayProperty=fullName> yalnızca bir giriş görevi iptal edildiğinde (yöntem çağrısından önce veya sonra olup olmamasına bakılmaksızın) bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f221-106">In the .NET Framework 4.5, these method overloads now return false if any tasks are still running when the time-out interval expired, and they throw an <xref:System.AggregateException?displayProperty=fullName> exception only if an input task was cancelled (regardless of whether it was before or after the method call) and no other tasks are still running.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0f221-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="0f221-107">Suggestion</span></span>

<span data-ttu-id="0f221-108"><xref:System.AggregateException?displayProperty=fullName>Çağrılan çağrıdan önce iptal edilen bir görevi tespit eden bir yol olarak yakalandıysa <xref:System.Threading.Tasks.Task.WaitAll%2A> , bu kod, özelliği aracılığıyla aynı algılamayı yapmanız gerekir <xref:System.Threading.Tasks.Task.IsCanceled%2A> (örneğin:. Herhangi biri (t = &gt; t. ısiptal)); .NET Framework 4,6, bu durumda yalnızca tüm beklenen görevler zaman aşımından önce tamamlandığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0f221-108">If an <xref:System.AggregateException?displayProperty=fullName> was being caught as a means of detecting a task that was cancelled prior to the <xref:System.Threading.Tasks.Task.WaitAll%2A> call being invoked, that code should instead do the same detection via the  <xref:System.Threading.Tasks.Task.IsCanceled%2A> property (for example: .Any(t =&gt; t.IsCanceled)) since .NET Framework 4.6 will only throw in that case if all awaited tasks are completed prior to the timeout.</span></span>

| <span data-ttu-id="0f221-109">Name</span><span class="sxs-lookup"><span data-stu-id="0f221-109">Name</span></span>    | <span data-ttu-id="0f221-110">Değer</span><span class="sxs-lookup"><span data-stu-id="0f221-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0f221-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0f221-111">Scope</span></span>   |<span data-ttu-id="0f221-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="0f221-112">Minor</span></span>|
|<span data-ttu-id="0f221-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0f221-113">Version</span></span>|<span data-ttu-id="0f221-114">4,5</span><span class="sxs-lookup"><span data-stu-id="0f221-114">4.5</span></span>|
|<span data-ttu-id="0f221-115">Tür</span><span class="sxs-lookup"><span data-stu-id="0f221-115">Type</span></span>|<span data-ttu-id="0f221-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="0f221-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f221-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0f221-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->
