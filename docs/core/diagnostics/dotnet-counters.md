---
title: DotNet-sayaçlar Tanılama aracı-.NET CLı
description: Ad hoc sistem durumu izleme ve ilk düzey performans araştırması için DotNet-Counter CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 1c802e33602c2d8f18600b9771a1f68e722d8fdf
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583301"
---
# <a name="investigate-performance-counters-dotnet-counters"></a><span data-ttu-id="f5dc2-103">Performans sayaçlarını araştırın (DotNet-sayaçlar)</span><span class="sxs-lookup"><span data-stu-id="f5dc2-103">Investigate performance counters (dotnet-counters)</span></span>

<span data-ttu-id="f5dc2-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f5dc2-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="f5dc2-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="f5dc2-105">Install</span></span>

<span data-ttu-id="f5dc2-106">İndirmek ve yüklemek için iki yol vardır `dotnet-counters` :</span><span class="sxs-lookup"><span data-stu-id="f5dc2-106">There are two ways to download and install `dotnet-counters`:</span></span>

- <span data-ttu-id="f5dc2-107">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="f5dc2-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="f5dc2-108">NuGet paketinin en son sürümünü yüklemek için `dotnet-counters` [](https://www.nuget.org/packages/dotnet-counters) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f5dc2-108">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- <span data-ttu-id="f5dc2-109">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="f5dc2-109">**Direct download:**</span></span>

  <span data-ttu-id="f5dc2-110">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="f5dc2-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="f5dc2-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f5dc2-111">OS</span></span>  | <span data-ttu-id="f5dc2-112">Platform</span><span class="sxs-lookup"><span data-stu-id="f5dc2-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="f5dc2-113">Windows</span><span class="sxs-lookup"><span data-stu-id="f5dc2-113">Windows</span></span> | <span data-ttu-id="f5dc2-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [ARM](https://aka.ms/dotnet-counters/win-arm) \| [ARM-x64](https://aka.ms/dotnet-counters/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="f5dc2-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span></span> |
  | <span data-ttu-id="f5dc2-115">Mac OS</span><span class="sxs-lookup"><span data-stu-id="f5dc2-115">macOS</span></span>   | [<span data-ttu-id="f5dc2-116">x64</span><span class="sxs-lookup"><span data-stu-id="f5dc2-116">x64</span></span>](https://aka.ms/dotnet-counters/osx-x64) |
  | <span data-ttu-id="f5dc2-117">Linux</span><span class="sxs-lookup"><span data-stu-id="f5dc2-117">Linux</span></span>   | <span data-ttu-id="f5dc2-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [ARM](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="f5dc2-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="f5dc2-119">`dotnet-counters`X86 uygulamasında kullanmak için, aracın karşılık gelen x86 sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-119">To use `dotnet-counters` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f5dc2-120">Özeti</span><span class="sxs-lookup"><span data-stu-id="f5dc2-120">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="f5dc2-121">Description</span><span class="sxs-lookup"><span data-stu-id="f5dc2-121">Description</span></span>

<span data-ttu-id="f5dc2-122">`dotnet-counters` , geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-122">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="f5dc2-123">API aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz <xref:System.Diagnostics.Tracing.EventCounter> .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-123">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="f5dc2-124">Örneğin, veya kullanarak daha ciddi performans araştırmasına gerek olmadan önce kuşkulu bir şey olup olmadığını görmek için, CPU kullanımı veya .NET Core uygulamanızda oluşturulan özel durumların oranı gibi şeyleri hızlıca izleyebilirsiniz `PerfView` `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-124">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="f5dc2-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f5dc2-125">Options</span></span>

- **`--version`**

  <span data-ttu-id="f5dc2-126">DotNet-Counters yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-126">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f5dc2-127">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-127">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="f5dc2-128">Komutlar</span><span class="sxs-lookup"><span data-stu-id="f5dc2-128">Commands</span></span>

| <span data-ttu-id="f5dc2-129">Komut</span><span class="sxs-lookup"><span data-stu-id="f5dc2-129">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="f5dc2-130">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="f5dc2-130">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="f5dc2-131">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="f5dc2-131">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="f5dc2-132">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="f5dc2-132">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="f5dc2-133">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="f5dc2-133">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="f5dc2-134">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="f5dc2-134">dotnet-counters collect</span></span>

<span data-ttu-id="f5dc2-135">Seçili sayaç değerlerini düzenli olarak toplayın ve işleme sonrası için belirtilen dosya biçimine dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-135">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f5dc2-136">Özeti</span><span class="sxs-lookup"><span data-stu-id="f5dc2-136">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="f5dc2-137">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f5dc2-137">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="f5dc2-138">Sayaç verilerinin toplanacağı işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-138">The ID of the process to be collect counter data from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="f5dc2-139">Sayaç verilerinin toplanacağı işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-139">The name of the process to be collect counter data from.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="f5dc2-140">Oluşturulacak tanılama bağlantı noktasının adı.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-140">The name of the diagnostic port to create.</span></span> <span data-ttu-id="f5dc2-141">Uygulama başlangıcında sayaçları izlemeye başlamak için bu seçeneğin nasıl kullanılacağı hakkında bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-141">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="f5dc2-142">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="f5dc2-142">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="f5dc2-143">Sayaçların virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-143">A comma-separated list of counters.</span></span> <span data-ttu-id="f5dc2-144">Sayaçlar belirtilebilir `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-144">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="f5dc2-145">, `provider_name` Uygun sayaçların bir listesi olmadan kullanılırsa, sağlayıcıdan gelen tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-145">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="f5dc2-146">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-146">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="f5dc2-147">Aktarılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-147">The format to be exported.</span></span> <span data-ttu-id="f5dc2-148">Şu anda kullanılabilir: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-148">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="f5dc2-149">Çıktı dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-149">The name of the output file.</span></span>

- <span data-ttu-id="f5dc2-150">**`-- <command>` (yalnızca .NET 5,0 veya üzeri sürümleri çalıştıran hedef uygulamalar için)**</span><span class="sxs-lookup"><span data-stu-id="f5dc2-150">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="f5dc2-151">Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-151">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="f5dc2-152">`dotnet-counters` , belirtilen komutla bir işlem başlatır ve istenen ölçümleri toplar.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-152">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="f5dc2-153">Bu, genellikle uygulamanın başlangıç yolu için ölçümleri toplamak ve ana giriş noktasından önce veya kısa bir süre sonra ortaya çıkan sorunları tanılamak veya izlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-153">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5dc2-154">Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-154">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="f5dc2-155">Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-155">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5dc2-156">DotNet sayaçları aracılığıyla bir .NET yürütülebiliri başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-156">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="f5dc2-157">CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-157">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="f5dc2-158">Alt işlem, araçtan önce çıktığında, araç da sonlandırılır ve izlemenin güvenle görüntülenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-158">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="f5dc2-159">STDIN/STDOUT kullanmanız gerekiyorsa `--diagnostic-port` seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-159">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="f5dc2-160">Daha fazla bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-160">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="f5dc2-161">Linux ve macOS 'ta, bu komut hedef uygulamayı bekler ve `dotnet-counters` aynı `TMPDIR` ortam değişkenini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-161">On Linux and macOS, this command expects the target application and `dotnet-counters` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="f5dc2-162">Aksi takdirde, komut zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-162">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="f5dc2-163">Kullanarak ölçümleri toplamak için `dotnet-counters` , hedef işlem ya da kök olarak çalışan kullanıcı ile aynı kullanıcı olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-163">To collect metrics using `dotnet-counters`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="f5dc2-164">Aksi halde araç, hedef işlemle bağlantı kurmayacak.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-164">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

### <a name="examples"></a><span data-ttu-id="f5dc2-165">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f5dc2-165">Examples</span></span>

- <span data-ttu-id="f5dc2-166">Tüm sayaçları 3 saniyelik yenileme aralığında toplayın ve çıkış olarak bir CSV oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f5dc2-166">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="f5dc2-167">`dotnet mvc.dll`Bir alt işlem olarak başlatın ve çalışma zamanı sayaçlarını toplamaya başlayın ve başlatma işleminden ASP.NET Core barındırma sayaçlarını başlatın ve bunu BIR JSON çıkışı olarak kaydedin:</span><span class="sxs-lookup"><span data-stu-id="f5dc2-167">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="f5dc2-168">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="f5dc2-168">dotnet-counters list</span></span>

<span data-ttu-id="f5dc2-169">Sağlayıcıya göre gruplandırılan sayaç adlarının ve açıklamalarının listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-169">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f5dc2-170">Özeti</span><span class="sxs-lookup"><span data-stu-id="f5dc2-170">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="f5dc2-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5dc2-171">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs per interval
    gen-1-gc-count                               Number of Gen 1 GCs per interval
    gen-2-gc-count                               Number of Gen 2 GCs per interval
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions per interval
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
> <span data-ttu-id="f5dc2-172">`Microsoft.AspNetCore.Hosting`Sayaçlar, bu sayaçları destekleyen bir işlem olduğunda (örneğin, konak makinede bir ASP.NET Core uygulama çalışırken) görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-172">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="f5dc2-173">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="f5dc2-173">dotnet-counters monitor</span></span>

<span data-ttu-id="f5dc2-174">Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-174">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f5dc2-175">Özeti</span><span class="sxs-lookup"><span data-stu-id="f5dc2-175">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="f5dc2-176">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f5dc2-176">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="f5dc2-177">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-177">The ID of the process to be monitored.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="f5dc2-178">İzlenecek işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-178">The name of the process to be monitored.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="f5dc2-179">Oluşturulacak tanılama bağlantı noktasının adı.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-179">The name of the diagnostic port to create.</span></span> <span data-ttu-id="f5dc2-180">Uygulama başlangıcında sayaçları izlemeye başlamak için bu seçeneğin nasıl kullanılacağı hakkında bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-180">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="f5dc2-181">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="f5dc2-181">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="f5dc2-182">Sayaçların virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-182">A comma-separated list of counters.</span></span> <span data-ttu-id="f5dc2-183">Sayaçlar belirtilebilir `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-183">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="f5dc2-184">, `provider_name` Uygun sayaçların bir listesi olmadan kullanılırsa, sağlayıcıdan gelen tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-184">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="f5dc2-185">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-185">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="f5dc2-186">**`-- <command>` (yalnızca .NET 5,0 veya üzeri sürümleri çalıştıran hedef uygulamalar için)**</span><span class="sxs-lookup"><span data-stu-id="f5dc2-186">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="f5dc2-187">Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-187">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="f5dc2-188">`dotnet-counters` , belirtilen komutla bir işlem başlatır ve istenen ölçümleri izler.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-188">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="f5dc2-189">Bu, genellikle uygulamanın başlangıç yolu için ölçümleri toplamak ve ana giriş noktasından önce veya kısa bir süre sonra ortaya çıkan sorunları tanılamak veya izlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-189">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5dc2-190">Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-190">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="f5dc2-191">Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-191">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5dc2-192">DotNet sayaçları aracılığıyla bir .NET yürütülebiliri başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-192">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="f5dc2-193">CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-193">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="f5dc2-194">Alt işlem, araçtan önce çıktıklarında, araç da sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-194">If the child process exits before the tool, the tool will exit as well.</span></span> <span data-ttu-id="f5dc2-195">STDIN/STDOUT kullanmanız gerekiyorsa `--diagnostic-port` seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-195">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="f5dc2-196">Daha fazla bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-196">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="f5dc2-197">Linux ve macOS 'ta, bu komut hedef uygulamayı bekler ve `dotnet-counters` aynı `TMPDIR` ortam değişkenini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-197">On Linux and macOS, this command expects the target application and `dotnet-counters` to share the same `TMPDIR` environment variable.</span></span>

> [!NOTE]
> <span data-ttu-id="f5dc2-198">Kullanarak ölçümleri izlemek için `dotnet-counters` , hedef işlem ya da kök olarak çalışan kullanıcı ile aynı kullanıcı olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-198">To monitor metrics using `dotnet-counters`, it needs to be run as the same user as the user running target process or as root.</span></span>

> [!NOTE]
> <span data-ttu-id="f5dc2-199">Aşağıdakine benzer bir hata iletisi görürseniz `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.` , `dotnet-counters` hedef işleme karşı eşleşmeyen bit genişliğine sahip olan kullanmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-199">If you see an error message similar to the following one: `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, you are trying to use `dotnet-counters` that has mismatched bitness against the target process.</span></span> <span data-ttu-id="f5dc2-200">[Yükleme](#install) bağlantısında aracın doğru bit durumunu indirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-200">Make sure to download the correct bitness of the tool in the [install](#install) link.</span></span>

### <a name="examples"></a><span data-ttu-id="f5dc2-201">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f5dc2-201">Examples</span></span>

- <span data-ttu-id="f5dc2-202">Tüm sayaçları `System.Runtime` 3 saniyelik yenileme aralığından izleyin:</span><span class="sxs-lookup"><span data-stu-id="f5dc2-202">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="f5dc2-203">Yalnızca CPU kullanımı ve GC yığın boyutunu izle `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="f5dc2-203">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="f5dc2-204">`EventCounter`Kullanıcı tanımlı değerleri izleme `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-204">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="f5dc2-205">Daha fazla bilgi için bkz. [öğretici: .NET Core 'Da EventCounters kullanarak performansı ölçme](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="f5dc2-205">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="f5dc2-206">' De kullanılabilen tüm iyi bilinen sayaçları görüntüleyin `dotnet-counters` :</span><span class="sxs-lookup"><span data-stu-id="f5dc2-206">View all well-known counters that are available in `dotnet-counters`:</span></span>

  ```console
  > dotnet-counters list

  Showing well-known counters for .NET (Core) version 3.1 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active

  Microsoft.AspNetCore.Hosting
      requests-per-second                Number of requests between update intervals
      total-requests                     Total number of requests
      current-requests                   Current number of requests
      failed-requests                    Failed number of requests
  ```

- <span data-ttu-id="f5dc2-207">.NET 5 uygulamaları için ' de kullanılabilen tüm iyi bilinen sayaçları görüntüleyin `dotnet-counters` :</span><span class="sxs-lookup"><span data-stu-id="f5dc2-207">View all well-known counters that are available in `dotnet-counters` for .NET 5 apps:</span></span>

  ```console
  > dotnet-counters list --runtime-version 5.0

  Showing well-known counters for .NET (Core) version 5.0 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      poh-size                           POH (Pinned Object Heap) Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      gc-fragmentation                   GC Heap Fragmentation
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active
      il-bytes-jitted                    Total IL bytes jitted
      methods-jitted-count               Number of methods jitted

  Microsoft.AspNetCore.Hosting
      requests-per-second   Number of requests between update intervals
      total-requests        Total number of requests
      current-requests      Current number of requests
      failed-requests       Failed number of requests

  Microsoft-AspNetCore-Server-Kestrel
      connections-per-second      Number of connections between update intervals
      total-connections           Total Connections
      tls-handshakes-per-second   Number of TLS Handshakes made between update intervals
      total-tls-handshakes        Total number of TLS handshakes made
      current-tls-handshakes      Number of currently active TLS handshakes
      failed-tls-handshakes       Total number of failed TLS handshakes
      current-connections         Number of current connections
      connection-queue-length     Length of Kestrel Connection Queue
      request-queue-length        Length total HTTP request queue

  System.Net.Http
      requests-started        Total Requests Started
      requests-started-rate   Number of Requests Started between update intervals
      requests-aborted        Total Requests Aborted
      requests-aborted-rate   Number of Requests Aborted between update intervals
      current-requests        Current Requests
  ```

- <span data-ttu-id="f5dc2-208">`my-aspnet-server.exe`Başlangıçtan yüklenen derlemelerin sayısını başlatın ve izleyin (yalnızca .net 5,0 veya üzeri):</span><span class="sxs-lookup"><span data-stu-id="f5dc2-208">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f5dc2-209">Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-209">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="f5dc2-210">`my-aspnet-server.exe` `arg1` Ve `arg2` komut satırı bağımsız değişkenleri ile başlatın ve çalışma kümesi ve GC yığın boyutunu başlangıçtan (yalnızca .NET 5,0 veya üzeri) izleyin:</span><span class="sxs-lookup"><span data-stu-id="f5dc2-210">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f5dc2-211">Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-211">This works for apps running .NET 5.0 or later only.</span></span>

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

## <a name="dotnet-counters-ps"></a><span data-ttu-id="f5dc2-212">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="f5dc2-212">dotnet-counters ps</span></span>

<span data-ttu-id="f5dc2-213">İzlenebilecek DotNet işlemlerinin bir listesini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-213">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f5dc2-214">Özeti</span><span class="sxs-lookup"><span data-stu-id="f5dc2-214">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="f5dc2-215">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5dc2-215">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a><span data-ttu-id="f5dc2-216">Tanılama bağlantı noktasını kullanma</span><span class="sxs-lookup"><span data-stu-id="f5dc2-216">Using diagnostic port</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f5dc2-217">Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-217">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="f5dc2-218">Tanılama bağlantı noktası, .NET 5 ' te eklenen ve uygulama başlangıcında sayaç izlemeye veya toplamaya başlayabilmeniz için yeni bir çalışma zamanı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-218">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start monitoring or collecting counters from app startup.</span></span> <span data-ttu-id="f5dc2-219">Bunu kullanarak yapmak için `dotnet-counters` `dotnet-counters <collect|monitor> -- <command>` Yukarıdaki örneklerde açıklandığı gibi kullanabilirsiniz veya `--diagnostic-port` seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-219">To do this using `dotnet-counters`, you can either use `dotnet-counters <collect|monitor> -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="f5dc2-220">`dotnet-counters <collect|monitor> -- <command>`Uygulamayı bir alt işlem olarak başlatmak için kullanmak, bunu başlangıçtan hızlı bir şekilde izlemenin en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-220">Using `dotnet-counters <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly monitor it from its startup.</span></span>

<span data-ttu-id="f5dc2-221">Bununla birlikte, izlenen uygulamanın ömrü boyunca daha ayrıntılı bir denetim elde etmek istediğinizde (örneğin, uygulamayı yalnızca ilk 10 dakika boyunca izleyin ve yürütülmeye devam edin) veya CLı kullanarak uygulamayla etkileşime ihtiyacınız varsa, kullanma `--diagnostic-port` seçeneği, hem izlenen hem de hedef uygulamayı denetlemenize olanak tanır `dotnet-counters` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-221">However, when you want to gain a finer control over the lifetime of the app being monitored (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-counters`.</span></span>

1. <span data-ttu-id="f5dc2-222">Aşağıdaki komut, DotNet-Counters adlı bir tanılama yuvası oluşturur `myport.sock` ve bir bağlantı bekler.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-222">The command below makes dotnet-counters create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="f5dc2-223">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="f5dc2-223">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="f5dc2-224">Ayrı bir konsolda, hedef uygulamayı `DOTNET_DiagnosticPorts` Çıkış içindeki değere ayarlanmış ortam değişkeni ile başlatın `dotnet-counters` .</span><span class="sxs-lookup"><span data-stu-id="f5dc2-224">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-counters` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="f5dc2-225">Bu, daha sonra `dotnet-counters` sayaçların toplanmasına başlaması gerekir `my-dotnet-app` :</span><span class="sxs-lookup"><span data-stu-id="f5dc2-225">This should then enable `dotnet-counters` to start collecting counters on `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="f5dc2-226">`dotnet run`DotNet CLI, uygulamanız olmayan çok sayıda alt işlem oluşturduğundan ve uygulamanızın `dotnet-counters` çalışma zamanında askıya alınması için uygulamadan önce bağlanabildikleri için uygulamanızın ile başlatılması sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-226">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-counters` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="f5dc2-227">Uygulamanın otomatik olarak kapsanan bir sürümünü kullanmanız veya `dotnet exec` uygulamayı başlatmak için kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="f5dc2-227">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>
