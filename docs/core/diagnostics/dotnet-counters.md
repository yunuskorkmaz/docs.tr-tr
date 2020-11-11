---
title: DotNet-sayaçlar-.NET Core
description: DotNet-Counter komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: 7ff29ad91ad271afd35e3d38a4d748bc79ad6c03
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507260"
---
# <a name="dotnet-counters"></a><span data-ttu-id="03a88-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="03a88-103">dotnet-counters</span></span>

<span data-ttu-id="03a88-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="03a88-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="03a88-105">DotNet-sayaçlar 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="03a88-105">Install dotnet-counters</span></span>

<span data-ttu-id="03a88-106">NuGet paketinin en son sürümünü yüklemek için `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="03a88-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="03a88-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="03a88-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="03a88-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03a88-108">Description</span></span>

<span data-ttu-id="03a88-109">`dotnet-counters` , geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="03a88-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="03a88-110">API aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz <xref:System.Diagnostics.Tracing.EventCounter> .</span><span class="sxs-lookup"><span data-stu-id="03a88-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="03a88-111">Örneğin, veya kullanarak daha ciddi performans araştırmasına gerek olmadan önce kuşkulu bir şey olup olmadığını görmek için, CPU kullanımı veya .NET Core uygulamanızda oluşturulan özel durumların oranı gibi şeyleri hızlıca izleyebilirsiniz `PerfView` `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="03a88-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="03a88-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="03a88-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="03a88-113">DotNet-Counters yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="03a88-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="03a88-114">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03a88-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="03a88-115">Komutlar</span><span class="sxs-lookup"><span data-stu-id="03a88-115">Commands</span></span>

| <span data-ttu-id="03a88-116">Komut</span><span class="sxs-lookup"><span data-stu-id="03a88-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="03a88-117">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="03a88-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="03a88-118">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="03a88-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="03a88-119">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="03a88-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="03a88-120">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="03a88-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="03a88-121">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="03a88-121">dotnet-counters collect</span></span>

<span data-ttu-id="03a88-122">Seçili sayaç değerlerini düzenli olarak toplayın ve işleme sonrası için belirtilen dosya biçimine dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="03a88-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="03a88-123">Özeti</span><span class="sxs-lookup"><span data-stu-id="03a88-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="03a88-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="03a88-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="03a88-125">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="03a88-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="03a88-126">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="03a88-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="03a88-127">Sayaçların virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="03a88-127">A comma-separated list of counters.</span></span> <span data-ttu-id="03a88-128">Sayaçlar belirtilebilir `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="03a88-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="03a88-129">, `provider_name` Uygun sayaçların bir listesi olmadan kullanılırsa, sağlayıcıdan gelen tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="03a88-129">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="03a88-130">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="03a88-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="03a88-131">Aktarılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="03a88-131">The format to be exported.</span></span> <span data-ttu-id="03a88-132">Şu anda kullanılabilir: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="03a88-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="03a88-133">Çıktı dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="03a88-133">The name of the output file.</span></span>

- <span data-ttu-id="03a88-134">**`-- <command>` (yalnızca .NET 5,0 veya üzeri sürümleri çalıştıran hedef uygulamalar için)**</span><span class="sxs-lookup"><span data-stu-id="03a88-134">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="03a88-135">Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="03a88-135">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="03a88-136">`dotnet-counters` , belirtilen komutla bir işlem başlatır ve istenen ölçümleri toplar.</span><span class="sxs-lookup"><span data-stu-id="03a88-136">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="03a88-137">Bu, genellikle uygulamanın başlangıç yolu için ölçümleri toplamak ve ana giriş noktasından önce veya kısa bir süre sonra ortaya çıkan sorunları tanılamak veya izlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03a88-137">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

> [!NOTE]
> <span data-ttu-id="03a88-138">Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır.</span><span class="sxs-lookup"><span data-stu-id="03a88-138">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="03a88-139">Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .</span><span class="sxs-lookup"><span data-stu-id="03a88-139">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="03a88-140">Örnekler</span><span class="sxs-lookup"><span data-stu-id="03a88-140">Examples</span></span>

- <span data-ttu-id="03a88-141">Tüm sayaçları 3 saniyelik yenileme aralığında toplayın ve çıkış olarak bir CSV oluşturun:</span><span class="sxs-lookup"><span data-stu-id="03a88-141">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="03a88-142">`dotnet mvc.dll`Bir alt işlem olarak başlatın ve çalışma zamanı sayaçlarını toplamaya başlayın ve başlatma işleminden ASP.NET Core barındırma sayaçlarını başlatın ve bunu BIR JSON çıkışı olarak kaydedin:</span><span class="sxs-lookup"><span data-stu-id="03a88-142">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="03a88-143">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="03a88-143">dotnet-counters list</span></span>

<span data-ttu-id="03a88-144">Sağlayıcıya göre gruplandırılan sayaç adlarının ve açıklamalarının listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="03a88-144">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="03a88-145">Özeti</span><span class="sxs-lookup"><span data-stu-id="03a88-145">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="03a88-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="03a88-146">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="03a88-147">`Microsoft.AspNetCore.Hosting`Sayaçlar, bu sayaçları destekleyen bir işlem olduğunda (örneğin, konak makinede bir ASP.NET Core uygulama çalışırken) görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="03a88-147">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="03a88-148">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="03a88-148">dotnet-counters monitor</span></span>

<span data-ttu-id="03a88-149">Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="03a88-149">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="03a88-150">Özeti</span><span class="sxs-lookup"><span data-stu-id="03a88-150">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="03a88-151">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="03a88-151">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="03a88-152">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="03a88-152">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="03a88-153">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="03a88-153">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="03a88-154">Sayaçların virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="03a88-154">A comma-separated list of counters.</span></span> <span data-ttu-id="03a88-155">Sayaçlar belirtilebilir `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="03a88-155">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="03a88-156">, `provider_name` Uygun sayaçların bir listesi olmadan kullanılırsa, sağlayıcıdan gelen tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="03a88-156">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="03a88-157">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="03a88-157">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="03a88-158">**`-- <command>` (yalnızca .NET 5,0 veya üzeri sürümleri çalıştıran hedef uygulamalar için)**</span><span class="sxs-lookup"><span data-stu-id="03a88-158">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="03a88-159">Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="03a88-159">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="03a88-160">`dotnet-counters` , belirtilen komutla bir işlem başlatır ve istenen ölçümleri izler.</span><span class="sxs-lookup"><span data-stu-id="03a88-160">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="03a88-161">Bu, genellikle uygulamanın başlangıç yolu için ölçümleri toplamak ve ana giriş noktasından önce veya kısa bir süre sonra ortaya çıkan sorunları tanılamak veya izlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03a88-161">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="03a88-162">Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır.</span><span class="sxs-lookup"><span data-stu-id="03a88-162">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="03a88-163">Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .</span><span class="sxs-lookup"><span data-stu-id="03a88-163">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="03a88-164">Örnekler</span><span class="sxs-lookup"><span data-stu-id="03a88-164">Examples</span></span>

- <span data-ttu-id="03a88-165">Tüm sayaçları `System.Runtime` 3 saniyelik yenileme aralığından izleyin:</span><span class="sxs-lookup"><span data-stu-id="03a88-165">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- <span data-ttu-id="03a88-166">Yalnızca CPU kullanımı ve GC yığın boyutunu izle `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="03a88-166">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="03a88-167">`EventCounter`Kullanıcı tanımlı değerleri izleme `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="03a88-167">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="03a88-168">Daha fazla bilgi için bkz. [öğretici: .NET Core 'Da EventCounters kullanarak performansı ölçme](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="03a88-168">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="03a88-169">`my-aspnet-server.exe`Başlangıçtan yüklenen derlemelerin sayısını başlatın ve izleyin (yalnızca .net 5,0 veya üzeri):</span><span class="sxs-lookup"><span data-stu-id="03a88-169">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="03a88-170">NOTE: Bu yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="03a88-170">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="03a88-171">`my-aspnet-server.exe` `arg1` Ve `arg2` komut satırı bağımsız değişkenleri ile başlatın ve çalışma kümesi ve GC yığın boyutunu başlangıçtan (yalnızca .NET 5,0 veya üzeri) izleyin:</span><span class="sxs-lookup"><span data-stu-id="03a88-171">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="03a88-172">NOTE: Bu yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="03a88-172">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a><span data-ttu-id="03a88-173">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="03a88-173">dotnet-counters ps</span></span>

<span data-ttu-id="03a88-174">İzlenebilecek DotNet işlemlerinin bir listesini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="03a88-174">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="03a88-175">Özeti</span><span class="sxs-lookup"><span data-stu-id="03a88-175">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="03a88-176">Örnek</span><span class="sxs-lookup"><span data-stu-id="03a88-176">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
