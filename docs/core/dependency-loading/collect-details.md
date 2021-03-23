---
title: Ayrıntılı derleme yükleme bilgilerini toplayın-.NET Core
description: .NET Core 'da derleme yükleme bilgilerinin nasıl toplanalınacağını gösteren açıklama
author: elinor-fung
ms.author: elfung
ms.date: 11/17/2020
ms.openlocfilehash: 505fc827021fe4d34675b2ef5a7fc5746ada1af6
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872944"
---
# <a name="collect-detailed-assembly-loading-information"></a><span data-ttu-id="31023-103">Ayrıntılı derleme yükleme bilgilerini topla</span><span class="sxs-lookup"><span data-stu-id="31023-103">Collect detailed assembly loading information</span></span>

<span data-ttu-id="31023-104">.NET 5,0 ' den itibaren, çalışma zamanı, `EventPipe` derleme yükleme sorunlarını tanılamaya yardımcı olmak üzere [yönetilen derleme yükleme](loading-managed.md) hakkında ayrıntılı bilgiler aracılığıyla olayları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="31023-104">Starting with .NET 5.0, the runtime can emit events through `EventPipe` with detailed information about [managed assembly loading](loading-managed.md) to aid in diagnosing assembly loading issues.</span></span> <span data-ttu-id="31023-105">Bu [Olaylar](../../fundamentals/diagnostics/runtime-loader-binder-events.md) `Microsoft-Windows-DotNETRuntime` sağlayıcı tarafından `AssemblyLoader` () anahtar sözcüğü altında dağıtılır `0x4` .</span><span class="sxs-lookup"><span data-stu-id="31023-105">These [events](../../fundamentals/diagnostics/runtime-loader-binder-events.md) are emitted by the `Microsoft-Windows-DotNETRuntime` provider under the `AssemblyLoader` keyword (`0x4`).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31023-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="31023-106">Prerequisites</span></span>

- <span data-ttu-id="31023-107">[.Net 5,0 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="31023-107">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="31023-108">[DotNet-Trace](../diagnostics/dotnet-trace.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="31023-108">[dotnet-trace](../diagnostics/dotnet-trace.md) tool.</span></span>

## <a name="collect-a-trace-with-assembly-loading-events"></a><span data-ttu-id="31023-109">Derleme yükleme olayları ile bir izleme toplama</span><span class="sxs-lookup"><span data-stu-id="31023-109">Collect a trace with assembly loading events</span></span>

<span data-ttu-id="31023-110">Çalışma zamanında derleme yükleme olaylarını etkinleştirmek ve bunların bir izlemesini toplamak için `dotnet-trace` aşağıdaki komutla kullanın:</span><span class="sxs-lookup"><span data-stu-id="31023-110">To enable assembly loading events in the runtime and collect a trace of them, use `dotnet-trace` with the following command:</span></span>

```console
dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id <pid>
```

<span data-ttu-id="31023-111">Bu, belirtilen bir izleme toplar ve bu, `<pid>` `AssemblyLoader` `Microsoft-Windows-DotNETRuntime` sağlayıcıdaki olayları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="31023-111">This will collect a trace of the specified `<pid>`, enabling the `AssemblyLoader` events in the `Microsoft-Windows-DotNETRuntime` provider.</span></span> <span data-ttu-id="31023-112">Sonuç bir `.nettrace` dosyadır.</span><span class="sxs-lookup"><span data-stu-id="31023-112">The result is a `.nettrace` file.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="31023-113">İzleme görüntüleme</span><span class="sxs-lookup"><span data-stu-id="31023-113">View a trace</span></span>

<span data-ttu-id="31023-114">Toplanan izleme dosyası, Windows 'da [PerfView](https://github.com/microsoft/perfview)içindeki olaylar görünümü kullanılarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="31023-114">The collected trace file can be viewed on Windows using the Events view in [PerfView](https://github.com/microsoft/perfview).</span></span> <span data-ttu-id="31023-115">Tüm derleme yükleme olayları ön ekine sahip olacaktır `Microsoft-Windows-DotNETRuntime/AssemblyLoader` .</span><span class="sxs-lookup"><span data-stu-id="31023-115">All the assembly loading events will be prefixed with `Microsoft-Windows-DotNETRuntime/AssemblyLoader`.</span></span>

## <a name="example-on-windows"></a><span data-ttu-id="31023-116">Örnek (Windows üzerinde)</span><span class="sxs-lookup"><span data-stu-id="31023-116">Example (on Windows)</span></span>

<span data-ttu-id="31023-117">Bu örnek, [uzantı noktaları örneğini yükleyen derlemeyi](https://docs.microsoft.com/samples/dotnet/samples/assembly-loading-extension-points/)kullanır.</span><span class="sxs-lookup"><span data-stu-id="31023-117">This example uses the [assembly loading extension points sample](https://docs.microsoft.com/samples/dotnet/samples/assembly-loading-extension-points/).</span></span> <span data-ttu-id="31023-118">Uygulama bir derlemeyi yüklemeye çalışır `MyLibrary` -uygulama tarafından başvurulmayan bir derleme ve bu nedenle, bir derlemenin uzantı noktası yükleme yüklemesinin başarıyla yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31023-118">The application attempts to load an assembly `MyLibrary` - an assembly that is not referenced by the application and thus requires handling in an assembly loading extension point to be successfully loaded.</span></span>

### <a name="collect-the-trace"></a><span data-ttu-id="31023-119">İzlemeyi topla</span><span class="sxs-lookup"><span data-stu-id="31023-119">Collect the trace</span></span>

01. <span data-ttu-id="31023-120">İndirilen örnekteki dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="31023-120">Navigate to the directory with the downloaded sample.</span></span> <span data-ttu-id="31023-121">Uygulamayı ile oluşturun:</span><span class="sxs-lookup"><span data-stu-id="31023-121">Build the application with:</span></span>

    ```console
    dotnet build
    ```

01. <span data-ttu-id="31023-122">Uygulamayı duraklaması gerektiğini belirten bağımsız değişkenlerle başlatın, anahtar basma için bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="31023-122">Launch the application with arguments indicating that it should pause, waiting for a key press.</span></span> <span data-ttu-id="31023-123">Devam etmek `AssemblyLoadContext` için, başarılı bir yük için gerekli işleme olmadan derlemeyi varsayılan olarak yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="31023-123">On resuming, it will attempt to load the assembly in the default `AssemblyLoadContext` - without the handling necessary for a successful load.</span></span> <span data-ttu-id="31023-124">Çıkış dizinine gidin ve şunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="31023-124">Navigate to the output directory and run:</span></span>

    ```console
    AssemblyLoading.exe /d default
    ```

01. <span data-ttu-id="31023-125">Uygulamanın işlem KIMLIĞINI bulun.</span><span class="sxs-lookup"><span data-stu-id="31023-125">Find the application's process ID.</span></span>

    ```console
    dotnet-trace ps
    ```

    <span data-ttu-id="31023-126">Çıktı, kullanılabilir işlemlerin listesini listelecektir.</span><span class="sxs-lookup"><span data-stu-id="31023-126">The output will list the available processes.</span></span> <span data-ttu-id="31023-127">Örnek:</span><span class="sxs-lookup"><span data-stu-id="31023-127">For example:</span></span>

    ```console
    35832 AssemblyLoading C:\src\AssemblyLoading\bin\Debug\net5.0\AssemblyLoading.exe
    ```

01. <span data-ttu-id="31023-128">`dotnet-trace`Çalışan uygulamaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31023-128">Attach `dotnet-trace` to the running application.</span></span>

    ```console
    dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id 35832
    ```

01. <span data-ttu-id="31023-129">Uygulamayı çalıştıran pencerede, programın devam etmesini sağlamak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="31023-129">In the window running the application, press any key to let the program continue.</span></span> <span data-ttu-id="31023-130">Uygulama çıktıktan sonra izleme otomatik olarak durur.</span><span class="sxs-lookup"><span data-stu-id="31023-130">Tracing will automatically stop once the application exits.</span></span>

### <a name="view-the-trace"></a><span data-ttu-id="31023-131">İzlemeyi görüntüleme</span><span class="sxs-lookup"><span data-stu-id="31023-131">View the trace</span></span>

<span data-ttu-id="31023-132">Toplanan izlemeyi [PerfView](https://github.com/microsoft/perfview) ' de açın ve olaylar görünümünü açın.</span><span class="sxs-lookup"><span data-stu-id="31023-132">Open the collected trace in [PerfView](https://github.com/microsoft/perfview) and open the Events view.</span></span> <span data-ttu-id="31023-133">Olaylar listesini `Microsoft-Windows-DotNETRuntime/AssemblyLoader` olaylara filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="31023-133">Filter the events list to `Microsoft-Windows-DotNETRuntime/AssemblyLoader` events.</span></span>

:::image type="content" source="media/collect-details/assembly-loader-filter.png" alt-text="PerfView derleme yükleyicisi filtre resmi":::

<span data-ttu-id="31023-135">İzleme başlatıldıktan sonra uygulamada gerçekleşen tüm derleme yüklemeleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="31023-135">All assembly loads that occurred in the application after tracing started will be shown.</span></span> <span data-ttu-id="31023-136">Bu örnek için ilgili derleme için yükleme işlemini incelemek üzere `MyLibrary` daha fazla filtreleme yapabiliriz.</span><span class="sxs-lookup"><span data-stu-id="31023-136">To inspect the load operation for the assembly of interest for this example - `MyLibrary`, we can do some more filtering.</span></span>

### <a name="assembly-loads"></a><span data-ttu-id="31023-137">Derleme yükleri</span><span class="sxs-lookup"><span data-stu-id="31023-137">Assembly loads</span></span>

<span data-ttu-id="31023-138">Görünümü [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) ve [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) olayları `Microsoft-Windows-DotNETRuntime/AssemblyLoader` sol taraftaki olay listesini kullanarak filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="31023-138">Filter the view to the [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) and [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) events under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="31023-139">Sütunları, `AssemblyName` `ActivityID` ve `Success` görünümüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31023-139">Add the columns `AssemblyName`, `ActivityID`, and `Success` to the view.</span></span> <span data-ttu-id="31023-140">İçeren olaylara filtre uygulayın `MyLibrary` .</span><span class="sxs-lookup"><span data-stu-id="31023-140">Filter to events containing `MyLibrary`.</span></span>

:::image type="content" source="media/collect-details/start-stop.png" alt-text="PerfView başlatma ve durdurma olayları görüntüsü":::

| <span data-ttu-id="31023-142">Olay Adı</span><span class="sxs-lookup"><span data-stu-id="31023-142">Event Name</span></span>             | <span data-ttu-id="31023-143">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31023-143">AssemblyName</span></span>                                      | <span data-ttu-id="31023-144">ActivityID</span><span class="sxs-lookup"><span data-stu-id="31023-144">ActivityID</span></span> | <span data-ttu-id="31023-145">Başarılı</span><span class="sxs-lookup"><span data-stu-id="31023-145">Success</span></span> |
| ---------------------- | ------------------------------------------------- | ---------- | ------- |
| `AssemblyLoader/Start` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31023-146">1/2/</span><span class="sxs-lookup"><span data-stu-id="31023-146">//1/2/</span></span>     |         |
| `AssemblyLoader/Stop`  | `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31023-147">1/2/</span><span class="sxs-lookup"><span data-stu-id="31023-147">//1/2/</span></span>     | <span data-ttu-id="31023-148">Yanlış</span><span class="sxs-lookup"><span data-stu-id="31023-148">False</span></span>   |

<span data-ttu-id="31023-149">`Start` / `Stop` `Success=False` `Stop` Olayda, yükleme işleminin başarısız olduğunu belirten bir çift görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="31023-149">You should see one `Start`/`Stop` pair with `Success=False` on the `Stop` event, indicating the load operation failed.</span></span> <span data-ttu-id="31023-150">İki olayın aynı etkinlik KIMLIĞINE sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="31023-150">Note that the two events have the same activity ID.</span></span> <span data-ttu-id="31023-151">Etkinlik KIMLIĞI, diğer tüm derleme yükleyicisi olaylarını yalnızca bu yükleme işlemine karşılık gelen olanlarla filtrelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31023-151">The activity ID can be used to filter all the other assembly loader events to just the ones corresponding to this load operation.</span></span>

### <a name="breakdown-of-attempt-to-load"></a><span data-ttu-id="31023-152">Yükleme denemesinin dökümü</span><span class="sxs-lookup"><span data-stu-id="31023-152">Breakdown of attempt to load</span></span>

<span data-ttu-id="31023-153">Yükleme işleminin daha ayrıntılı bir dökümü için, görünümü soldaki olay listesini kullanarak altındaki [ `ResolutionAttempted` olaylara](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) filtreleyin `Microsoft-Windows-DotNETRuntime/AssemblyLoader` .</span><span class="sxs-lookup"><span data-stu-id="31023-153">For a more detailed breakdown of the load operation, filter the view to the [`ResolutionAttempted` events](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="31023-154">Sütunları, `AssemblyName` `Stage` ve `Result` görünümüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31023-154">Add the columns `AssemblyName`, `Stage`, and `Result` to the view.</span></span> <span data-ttu-id="31023-155">Çiftin etkinlik kimliği olan olaylara filtre uygulayın `Start` / `Stop` .</span><span class="sxs-lookup"><span data-stu-id="31023-155">Filter to events with the activity ID from the `Start`/`Stop` pair.</span></span>

:::image type="content" source="media/collect-details/resolution-attempted.png" alt-text="PerfView Resolutiondenenen olaylar görüntüsü":::

| <span data-ttu-id="31023-157">Olay Adı</span><span class="sxs-lookup"><span data-stu-id="31023-157">Event Name</span></span>                           | <span data-ttu-id="31023-158">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31023-158">AssemblyName</span></span>                                      | <span data-ttu-id="31023-159">Aşama</span><span class="sxs-lookup"><span data-stu-id="31023-159">Stage</span></span>                               | <span data-ttu-id="31023-160">Sonuç</span><span class="sxs-lookup"><span data-stu-id="31023-160">Result</span></span>             |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AppDomainAssemblyResolveEvent`     | `AssemblyNotFound` |

<span data-ttu-id="31023-161">Yukarıdaki olaylar, derleme yükleyicisinin geçerli yükleme bağlamına bakarak, yönetilen uygulama derlemeleri için varsayılan yoklama mantığını çalıştırıp, olay için işleyicileri çağırarak <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> ve için işleyicileri çağırarak derlemeyi çözmeyi denediğini gösterir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="31023-161">The events above indicate that the assembly loader attempted to resolve the assembly by looking in the current load context, running the default probing logic for managed application assemblies, invoking handlers for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event, and invoking handlers for the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31023-162">Bu adımların tümü için derleme bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="31023-162">For all of these steps, the assembly was not found.</span></span>

### <a name="extension-points"></a><span data-ttu-id="31023-163">Uzantı noktaları</span><span class="sxs-lookup"><span data-stu-id="31023-163">Extension points</span></span>

<span data-ttu-id="31023-164">Hangi uzantı noktalarının çağırılacağını görmek için, görünümün [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) sol taraftaki `Microsoft-Windows-DotNETRuntime/AssemblyLoader` olay listesini kullanarak ve altındaki öğesine filtre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="31023-164">To see which extension points were invoked, filter the view to the [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) and [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="31023-165">Sütunları `AssemblyName` ve görünüme ekleyin `HandlerName` .</span><span class="sxs-lookup"><span data-stu-id="31023-165">Add the columns `AssemblyName` and `HandlerName` to the view.</span></span> <span data-ttu-id="31023-166">Çiftin etkinlik kimliği olan olaylara filtre uygulayın `Start` / `Stop` .</span><span class="sxs-lookup"><span data-stu-id="31023-166">Filter to events with the activity ID from the `Start`/`Stop` pair.</span></span>

:::image type="content" source="media/collect-details/extension-point.png" alt-text="PerfView uzantı noktası olayları görüntüsü":::

| <span data-ttu-id="31023-168">Olay Adı</span><span class="sxs-lookup"><span data-stu-id="31023-168">Event Name</span></span>                                                  | <span data-ttu-id="31023-169">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31023-169">AssemblyName</span></span>                                      | <span data-ttu-id="31023-170">HandlerName</span><span class="sxs-lookup"><span data-stu-id="31023-170">HandlerName</span></span>                      |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` |
| `AssemblyLoader/AppDomainAssemblyResolveHandlerInvoked`     | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAppDomainAssemblyResolve`     |

<span data-ttu-id="31023-171">Yukarıdaki olaylar, `OnAssemblyLoadContextResolving` olay için çağrılan <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> ve `OnAppDomainAssemblyResolve` olay için çağrılan bir işleyici olarak adlandırılan bir işleyicinin olduğunu gösterir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="31023-171">The events above indicate that a handler named `OnAssemblyLoadContextResolving` was invoked for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event and a handler named `OnAppDomainAssemblyResolve` was invoked for the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

### <a name="collect-another-trace"></a><span data-ttu-id="31023-172">Başka bir izleme topla</span><span class="sxs-lookup"><span data-stu-id="31023-172">Collect another trace</span></span>

<span data-ttu-id="31023-173">Uygulamayı olay için işleyicisi derlemeyi yükleyecek şekilde bağımsız değişkenlerle çalıştırın <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> `MyLibrary` .</span><span class="sxs-lookup"><span data-stu-id="31023-173">Run the application with arguments such that its handler for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event will load the `MyLibrary` assembly.</span></span>

```console
AssemblyLoading /d default alc-resolving
```

<span data-ttu-id="31023-174">`.nettrace` [Yukarıdaki adımları](#collect-the-trace)kullanarak başka bir dosya toplayın ve açın.</span><span class="sxs-lookup"><span data-stu-id="31023-174">Collect and open another `.nettrace` file using the [steps from above](#collect-the-trace).</span></span>

<span data-ttu-id="31023-175">`Start`Ve `Stop` olaylarına yeniden filtre uygulayın `MyLibrary` .</span><span class="sxs-lookup"><span data-stu-id="31023-175">Filter to the `Start` and `Stop` events for `MyLibrary` again.</span></span> <span data-ttu-id="31023-176">Aralarında `Start` / `Stop` başka bir çift görmeniz gerekir `Start` / `Stop` .</span><span class="sxs-lookup"><span data-stu-id="31023-176">You should see a `Start`/`Stop` pair with another `Start`/`Stop` between them.</span></span> <span data-ttu-id="31023-177">İç yükleme işlemi, ne zaman çağrıldığı için işleyicinin tetiklediği yükü temsil eder <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="31023-177">The inner load operation represents the load triggered by the handler for <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> when it called <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31023-178">Bu kez, `Success=True` `Stop` olayda yükleme işleminin başarılı olduğunu belirten bir olay görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="31023-178">This time, you should see `Success=True` on the `Stop` event, indicating the load operation succeeded.</span></span> <span data-ttu-id="31023-179">`ResultAssemblyPath`Alan, sonuçta elde edilen derlemenin yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31023-179">The `ResultAssemblyPath` field shows the path of the resulting assembly.</span></span>

:::image type="content" source="media/collect-details/start-stop-success.png" alt-text="PerfView başarılı başlatma ve durdurma olayları görüntüsü":::

| <span data-ttu-id="31023-181">Olay Adı</span><span class="sxs-lookup"><span data-stu-id="31023-181">Event Name</span></span>             | <span data-ttu-id="31023-182">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31023-182">AssemblyName</span></span>                                                       | <span data-ttu-id="31023-183">ActivityID</span><span class="sxs-lookup"><span data-stu-id="31023-183">ActivityID</span></span> | <span data-ttu-id="31023-184">Başarılı</span><span class="sxs-lookup"><span data-stu-id="31023-184">Success</span></span> | <span data-ttu-id="31023-185">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="31023-185">ResultAssemblyPath</span></span>                                      |
| ---------------------- | ------------------------------------------------------------------ |------------|---------| ------------------------------------------------------- |
| `AssemblyLoader/Start` |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31023-186">1/2/</span><span class="sxs-lookup"><span data-stu-id="31023-186">//1/2/</span></span>     |         |                                                         |
| `AssemblyLoader/Start` | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31023-187">1/2/1/</span><span class="sxs-lookup"><span data-stu-id="31023-187">//1/2/1/</span></span>   |         |                                                         |
| `AssemblyLoader/Stop`  | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31023-188">1/2/1/</span><span class="sxs-lookup"><span data-stu-id="31023-188">//1/2/1/</span></span>   | <span data-ttu-id="31023-189">Doğru</span><span class="sxs-lookup"><span data-stu-id="31023-189">True</span></span>    | <span data-ttu-id="31023-190">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31023-190">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |
| `AssemblyLoader/Stop`  |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31023-191">1/2/</span><span class="sxs-lookup"><span data-stu-id="31023-191">//1/2/</span></span>     | <span data-ttu-id="31023-192">Doğru</span><span class="sxs-lookup"><span data-stu-id="31023-192">True</span></span>    | <span data-ttu-id="31023-193">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31023-193">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="31023-194">Daha sonra, `ResolutionAttempted` derlemenin başarıyla çözümlenme adımını öğrenmek için dış yükün etkınlık kimliği olan olaylara bakabiliriz.</span><span class="sxs-lookup"><span data-stu-id="31023-194">We can then look at the `ResolutionAttempted` events with the activity ID from the outer load to determine the step at which the assembly was successfully resolved.</span></span> <span data-ttu-id="31023-195">Bu kez, olaylar `AssemblyLoadContextResolvingEvent` aşamanın başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31023-195">This time, the events will show that the `AssemblyLoadContextResolvingEvent` stage was successful.</span></span> <span data-ttu-id="31023-196">`ResultAssemblyPath`Alan, sonuçta elde edilen derlemenin yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31023-196">The `ResultAssemblyPath` field shows the path of the resulting assembly.</span></span>

:::image type="content" source="media/collect-details/resolution-attempted-success.png" alt-text="PerfView başarıyla Resolutiondenenen olaylar görüntüsü":::

| <span data-ttu-id="31023-198">Olay Adı</span><span class="sxs-lookup"><span data-stu-id="31023-198">Event Name</span></span>                           | <span data-ttu-id="31023-199">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31023-199">AssemblyName</span></span>                                      | <span data-ttu-id="31023-200">Aşama</span><span class="sxs-lookup"><span data-stu-id="31023-200">Stage</span></span>                               | <span data-ttu-id="31023-201">Sonuç</span><span class="sxs-lookup"><span data-stu-id="31023-201">Result</span></span>             | <span data-ttu-id="31023-202">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="31023-202">ResultAssemblyPath</span></span> |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `Success`          | <span data-ttu-id="31023-203">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31023-203">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="31023-204">Olaylara bakmak `AssemblyLoadContextResolvingHandlerInvoked` adlı işleyicinin `OnAssemblyLoadContextResolving` çağırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31023-204">Looking at `AssemblyLoadContextResolvingHandlerInvoked` events will show that the handler named `OnAssemblyLoadContextResolving` was invoked.</span></span> <span data-ttu-id="31023-205">`ResultAssemblyPath`Alan, işleyicinin döndürdüğü derlemenin yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31023-205">The `ResultAssemblyPath` field shows the path of the assembly returned by the handler.</span></span>

:::image type="content" source="media/collect-details/extension-point-success.png" alt-text="PerfView başarılı uzantı noktası olayları görüntüsü":::

| <span data-ttu-id="31023-207">Olay Adı</span><span class="sxs-lookup"><span data-stu-id="31023-207">Event Name</span></span>                                                  | <span data-ttu-id="31023-208">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31023-208">AssemblyName</span></span>                                      | <span data-ttu-id="31023-209">HandlerName</span><span class="sxs-lookup"><span data-stu-id="31023-209">HandlerName</span></span>                      | <span data-ttu-id="31023-210">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="31023-210">ResultAssemblyPath</span></span> |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------ |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` | <span data-ttu-id="31023-211">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31023-211">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="31023-212">`ResolutionAttempted` `AppDomainAssemblyResolveEvent` `AppDomainAssemblyResolveHandlerInvoked` Olayı başlatan yükleme algoritmasındaki adıma ulaşmadan önce, aşama veya herhangi bir olay ile artık bir olay olmadığını unutmayın <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="31023-212">Note that there is no longer a `ResolutionAttempted` event with the `AppDomainAssemblyResolveEvent` stage or any `AppDomainAssemblyResolveHandlerInvoked` events, as the assembly was successfully loaded before reaching the step of the loading algorithm that raises the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

## <a name="see-also"></a><span data-ttu-id="31023-213">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31023-213">See also</span></span>

- [<span data-ttu-id="31023-214">Derleme yükleyici olayları</span><span class="sxs-lookup"><span data-stu-id="31023-214">Assembly loader events</span></span>](../../fundamentals/diagnostics/runtime-loader-binder-events.md)
- [<span data-ttu-id="31023-215">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="31023-215">dotnet-trace</span></span>](../diagnostics/dotnet-trace.md)
- [<span data-ttu-id="31023-216">PerfView</span><span class="sxs-lookup"><span data-stu-id="31023-216">PerfView</span></span>](https://github.com/microsoft/perfview)
