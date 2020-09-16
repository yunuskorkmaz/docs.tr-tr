---
title: Yüksek CPU kullanımı hata ayıkla-.NET Core
description: .NET Core 'da yüksek CPU kullanımında hata ayıklama konusunda size yol gösteren bir öğretici.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 71e0b98f7ad38836c6a20c3e0e75a878fb6525c7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538715"
---
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="edb42-103">.NET Core 'da yüksek CPU kullanımını hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="edb42-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="edb42-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="edb42-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="edb42-105">Bu öğreticide, aşırı CPU kullanımı senaryosunda hata ayıklamayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="edb42-106">[Web uygulaması](/samples/dotnet/samples/diagnostic-scenarios) kaynak kodu deposu ASP.NET Core sunulan örneği kullanarak, kasıtlı olarak bir kilitlenmeye neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="edb42-107">Uç nokta, askıda kalma ve iş parçacığı birikmesi ile karşılaşacaktır.</span><span class="sxs-lookup"><span data-stu-id="edb42-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="edb42-108">Çeşitli araçları kullanarak bu senaryoyu tanılama verilerinin çeşitli önemli parçalarından nasıl tanınbileceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="edb42-109">Bu öğreticide şunları yapacaksınız:</span><span class="sxs-lookup"><span data-stu-id="edb42-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="edb42-110">Yüksek CPU kullanımını araştır</span><span class="sxs-lookup"><span data-stu-id="edb42-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="edb42-111">[DotNet sayaçları](dotnet-counters.md) ile CPU kullanımını belirleme</span><span class="sxs-lookup"><span data-stu-id="edb42-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="edb42-112">İzleme oluşturma için [DotNet-Trace](dotnet-trace.md) kullanın</span><span class="sxs-lookup"><span data-stu-id="edb42-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="edb42-113">PerfView 'da profil performansı</span><span class="sxs-lookup"><span data-stu-id="edb42-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="edb42-114">Aşırı CPU kullanımını Tanıla ve çöz</span><span class="sxs-lookup"><span data-stu-id="edb42-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="edb42-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="edb42-115">Prerequisites</span></span>

<span data-ttu-id="edb42-116">Öğretici şunları kullanır:</span><span class="sxs-lookup"><span data-stu-id="edb42-116">The tutorial uses:</span></span>

- <span data-ttu-id="edb42-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="edb42-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="edb42-118">Senaryonun tetiklenmesi için [örnek hata ayıklama hedefi](/samples/dotnet/samples/diagnostic-scenarios) .</span><span class="sxs-lookup"><span data-stu-id="edb42-118">[Sample debug target](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="edb42-119">[DotNet-](dotnet-trace.md) işlem listelemek ve bir profil oluşturmak için izleyin.</span><span class="sxs-lookup"><span data-stu-id="edb42-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="edb42-120">[DotNet sayaçları](dotnet-counters.md) , CPU kullanımını izlemeye yönelik sayaçlardır.</span><span class="sxs-lookup"><span data-stu-id="edb42-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="edb42-121">CPU sayaçları</span><span class="sxs-lookup"><span data-stu-id="edb42-121">CPU counters</span></span>

<span data-ttu-id="edb42-122">Tanılama verilerini toplamayı denemeden önce, yüksek bir CPU koşulu gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="edb42-123">Proje kök dizininde aşağıdaki komutu kullanarak [Örnek uygulamayı](/samples/dotnet/samples/diagnostic-scenarios) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="edb42-123">Run the [sample application](/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="edb42-124">İşlem KIMLIĞINI bulmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="edb42-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="edb42-125">Komut çıktıınızdan işlem KIMLIĞI ' ni bir yere göz atın.</span><span class="sxs-lookup"><span data-stu-id="edb42-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="edb42-126">İşlem KIMLIĞINIZ idi `22884` , ancak sizinki farklı olacak.</span><span class="sxs-lookup"><span data-stu-id="edb42-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="edb42-127">Geçerli CPU kullanımını denetlemek için [DotNet-Counters](dotnet-counters.md) aracı komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="edb42-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="edb42-128">, `refresh-interval` Sayaç yoklama CPU değerleri arasındaki saniye sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="edb42-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="edb42-129">Çıktının aşağıdakine benzer olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="edb42-129">The output should be similar to the following:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

<span data-ttu-id="edb42-130">Web uygulaması çalışırken, başlangıçtan hemen sonra CPU tüketilmez ve tarihinde raporlanır `0%` .</span><span class="sxs-lookup"><span data-stu-id="edb42-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="edb42-131">Rota `api/diagscenario/highcpu` parametresi olarak bulunan yola gidin `60000` :</span><span class="sxs-lookup"><span data-stu-id="edb42-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

`https://localhost:5001/api/diagscenario/highcpu/60000`

<span data-ttu-id="edb42-132">Şimdi [DotNet-Counters](dotnet-counters.md) komutunu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="edb42-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="edb42-133">Yalnızca öğesini izlemek için `cpu-usage` `System.Runtime[cpu-usage]` komutunun bir parçası olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="edb42-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="edb42-134">CPU kullanımında aşağıda gösterildiği gibi bir artış görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="edb42-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="edb42-135">İstek süresince CPU kullanımı %25 ' in üzerine gelmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="edb42-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="edb42-136">Konak makinesine bağlı olarak, değişen CPU kullanımı beklenir.</span><span class="sxs-lookup"><span data-stu-id="edb42-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="edb42-137">Daha yüksek bir CPU kullanımını görselleştirmek için, bu uç noktayı birden çok tarayıcı sekmesinde aynı anda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="edb42-138">Bu noktada, CPU 'nun beklediğinizden daha yüksek bir şekilde çalıştığını söyleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="edb42-139">İzleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="edb42-139">Trace generation</span></span>

<span data-ttu-id="edb42-140">Yavaş bir istek analiz edilirken, kodun yaptığına ilişkin Öngörüler sağlayabilen bir tanılama aracına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="edb42-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="edb42-141">Olağan seçim bir profil oluşturucu ve aralarından seçim yapabileceğiniz farklı profil Oluşturucu seçenekleri vardır.</span><span class="sxs-lookup"><span data-stu-id="edb42-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="edb42-142">Linux</span><span class="sxs-lookup"><span data-stu-id="edb42-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="edb42-143">`perf`Araç .NET Core uygulama profilleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="edb42-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="edb42-144">[Örnek hata ayıklama hedefinin](/samples/dotnet/samples/diagnostic-scenarios)önceki örneğinden çıkın.</span><span class="sxs-lookup"><span data-stu-id="edb42-144">Exit the previous instance of the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="edb42-145">`COMPlus_PerfMapEnabled`.NET Core uygulamasının dizinde bir dosya oluşturmasını sağlamak için ortam değişkenini ayarlayın `map` `/tmp` .</span><span class="sxs-lookup"><span data-stu-id="edb42-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="edb42-146">Bu `map` dosya tarafından, `perf` CPU adresini JIT tarafından oluşturulan işlevlere ada göre eşlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="edb42-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="edb42-147">Daha fazla bilgi için bkz. [yazma perf Map](../run-time-config/debugging-profiling.md#write-perf-map).</span><span class="sxs-lookup"><span data-stu-id="edb42-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="edb42-148">[Örnek hata ayıklama hedefini](/samples/dotnet/samples/diagnostic-scenarios) aynı Terminal oturumunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="edb42-148">Run the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="edb42-149">Yüksek CPU API uç noktasını ( `https://localhost:5001/api/diagscenario/highcpu/60000` ) yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="edb42-149">Exercise the high CPU API endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="edb42-150">1 dakikalık istek içinde çalışırken, `perf` Işlem Kimliğinizle komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="edb42-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="edb42-151">`perf`Komut, performans toplama işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="edb42-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="edb42-152">20-30 saniye boyunca çalışmasına izin verin ve ardından, koleksiyon işleminden çıkmak için <kbd>CTRL + C</kbd> tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="edb42-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="edb42-153">`perf`İzlemenin çıkışını görmek için aynı komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="edb42-154">Aşağıdaki komutları kullanarak bir _Flame grafiği_ de oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="edb42-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="edb42-155">Bu komut `flamegraph.svg` , tarayıcıda görüntüleyebilmeniz için performans sorununu araştırmak üzere bir oluşturur:</span><span class="sxs-lookup"><span data-stu-id="edb42-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="edb42-156">[![Flame grafiği SVG resmi](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="edb42-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="edb42-157">Windows</span><span class="sxs-lookup"><span data-stu-id="edb42-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="edb42-158">Windows 'da, [DotNet-Trace](dotnet-trace.md) aracını bir profil oluşturucu olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edb42-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="edb42-159">Önceki [örnek hata ayıklama hedefini](/samples/dotnet/samples/diagnostic-scenarios)kullanarak, yüksek CPU uç noktasını ( `https://localhost:5001/api/diagscenario/highcpu/60000` ) yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="edb42-159">Using the previous [sample debug target](/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="edb42-160">1 dakikalık istek içinde çalışırken `collect` komutunu aşağıdaki gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="edb42-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="edb42-161">20-30 saniye boyunca [DotNet-Trace](dotnet-trace.md) çalışmasına izin verin ve ardından <kbd>ENTER</kbd> tuşuna basarak koleksiyondan çıkın.</span><span class="sxs-lookup"><span data-stu-id="edb42-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="edb42-162">Sonuç, `nettrace` aynı klasörde bulunan bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="edb42-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="edb42-163">`nettrace`Dosyalar, Windows 'da mevcut analiz araçlarını kullanmanın harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="edb42-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="edb42-164">Öğesini `nettrace` [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) aşağıda gösterildiği gibi açın.</span><span class="sxs-lookup"><span data-stu-id="edb42-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="edb42-165">[![PerfView resmi](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="edb42-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="edb42-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb42-166">See also</span></span>

- <span data-ttu-id="edb42-167">[DotNet-](dotnet-trace.md) liste işlemlerine izleme</span><span class="sxs-lookup"><span data-stu-id="edb42-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="edb42-168">[DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar</span><span class="sxs-lookup"><span data-stu-id="edb42-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="edb42-169">[DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm</span><span class="sxs-lookup"><span data-stu-id="edb42-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="edb42-170">DotNet/Diagnostics</span><span class="sxs-lookup"><span data-stu-id="edb42-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="edb42-171">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="edb42-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="edb42-172">.NET Core 'da kilitlenmeyle hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="edb42-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
