---
title: PerfCollect ile .NET uygulamalarını izleme.
description: .NET ' te PerfCollect ile izleme toplama konusunda size kılavuzluk eden bir öğretici.
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 20e1bf56714fb32b5231d45b0ba35cdfcedaea2e
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189936"
---
# <a name="trace-net-applications-with-perfcollect"></a><span data-ttu-id="6b63a-103">PerfCollect ile .NET uygulamalarını izleme</span><span class="sxs-lookup"><span data-stu-id="6b63a-103">Trace .NET applications with PerfCollect</span></span>

<span data-ttu-id="6b63a-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="6b63a-104">**This article applies to: ✔️** .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="6b63a-105">Linux üzerinde performans sorunlarıyla karşılaşıldığında, bir izleme toplama, `perfcollect` performans sorunu sırasında makinede neler olduğunu hakkında ayrıntılı bilgi toplamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-105">When performance problems are encountered on Linux, collecting a trace with `perfcollect` can be used to gather detailed information about what was happening on the machine at the time of the performance problem.</span></span>

<span data-ttu-id="6b63a-106">`perfcollect`, çalışma zamanının veya herhangi bir [EventSource](xref:System.Diagnostics.Tracing.EventListener)'dan yazılmış olayları toplamak Için [Linux izleme Tookit-Next oluşturma (lttng)](https://lttng.org) kullanan bir bash betiğidir ve hedef işlemin CPU örneklerini toplamak için [perf](https://perf.wiki.kernel.org/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-106">`perfcollect` is a bash script that leverages [Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) to collect events written from the runtime or any [EventSource](xref:System.Diagnostics.Tracing.EventListener), as well as [perf](https://perf.wiki.kernel.org/) to collect CPU samples of the target process.</span></span>

## <a name="prepare-your-machine"></a><span data-ttu-id="6b63a-107">Makinenizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="6b63a-107">Prepare your machine</span></span>

<span data-ttu-id="6b63a-108">Makinenizi ile bir performans izlemesi toplayacak şekilde hazırlamak için aşağıdaki adımları izleyin `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-108">Follow these steps to prepare your machine to collect a performance trace with `perfcollect`.</span></span>

> [!NOTE]
> <span data-ttu-id="6b63a-109">Bir kapsayıcı ortamındaysanız, kapsayıcının özelliği olması gerekir `SYS_ADMIN` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-109">If you are in a container environment, your container needs to have `SYS_ADMIN` capability.</span></span> <span data-ttu-id="6b63a-110">PerfCollect kullanarak kapsayıcılardaki uygulamaları izleme hakkında daha fazla bilgi için bkz. [kapsayıcılarda tanılamayı toplama](./diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="6b63a-110">For more information on tracing applications inside containers using PerfCollect, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

1. <span data-ttu-id="6b63a-111">İndirin `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-111">Download `perfcollect`.</span></span>

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. <span data-ttu-id="6b63a-112">Betiği çalıştırılabilir yapın.</span><span class="sxs-lookup"><span data-stu-id="6b63a-112">Make the script executable.</span></span>

    > ```bash
    > chmod +x perfcollect
    > ```

3. <span data-ttu-id="6b63a-113">İzleme önkoşullarını yükler-bunlar gerçek izleme kitaplıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-113">Install tracing prerequisites - these are the actual tracing libraries.</span></span>

    > ```bash
    > sudo ./perfcollect install
    > ```

    <span data-ttu-id="6b63a-114">Bu işlem makinenize aşağıdaki önkoşulları yükler:</span><span class="sxs-lookup"><span data-stu-id="6b63a-114">This will install the following prerequisites on your machine:</span></span>

    1. <span data-ttu-id="6b63a-115">`perf`: Linux performans olayları alt sistemi ve yardımcı Kullanıcı modu koleksiyonu/görüntüleyici uygulaması.</span><span class="sxs-lookup"><span data-stu-id="6b63a-115">`perf`: the Linux Performance Events subsystem and companion user-mode collection/viewer application.</span></span> <span data-ttu-id="6b63a-116">`perf` , Linux çekirdek kaynağının bir parçasıdır, ancak genellikle varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="6b63a-116">`perf` is part of the Linux kernel source, but is not usually installed by default.</span></span>

    2. <span data-ttu-id="6b63a-117">`LTTng`: Çalışma zamanında, CoreCLR tarafından yayılan olay verilerini yakalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-117">`LTTng`: Used to capture event data emitted at runtime by CoreCLR.</span></span> <span data-ttu-id="6b63a-118">Bu veriler daha sonra GC, JıT ve iş parçacığı havuzu gibi çeşitli çalışma zamanı bileşenlerinin davranışını çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-118">This data is then used to analyze the behavior of various runtime components such as the GC, JIT, and thread pool.</span></span>

<span data-ttu-id="6b63a-119">.NET Core 'un son sürümleri ve Linux performans aracı, çerçeve kodu için yöntem adlarının otomatik olarak çözümlenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="6b63a-119">Recent versions of .NET Core and the Linux perf tool support automatic resolution of method names for framework code.</span></span> <span data-ttu-id="6b63a-120">.NET Core sürüm 3,1 veya daha az bir sürümle çalışıyorsanız, ek bir adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-120">If you are working with .NET Core version 3.1 or less, an extra step is necessary.</span></span> <span data-ttu-id="6b63a-121">Ayrıntılar için bkz. [çerçeve sembollerini çözme](#resolve-framework-symbols) .</span><span class="sxs-lookup"><span data-stu-id="6b63a-121">See [Resolving Framework Symbols](#resolve-framework-symbols) for details.</span></span>

<span data-ttu-id="6b63a-122">Yerel çalışma zamanı dll 'Lerinin (örneğin, libcoreclr.so) yöntem adlarını çözümlemek için, `perfcollect` verileri dönüştürürken, ancak yalnızca bu ikililerin sembolleri varsa, simgeler için sembolleri çözer.</span><span class="sxs-lookup"><span data-stu-id="6b63a-122">For resolving method names of native runtime DLLs (such as libcoreclr.so), `perfcollect` will resolve symbols for them when it converts the data, but only if the symbols for these binaries are present.</span></span> <span data-ttu-id="6b63a-123">Ayrıntılar için bkz. [yerel çalışma zamanı Için semboller alma](#get-symbols-for-the-native-runtime) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6b63a-123">See [Getting Symbols for the Native Runtime](#get-symbols-for-the-native-runtime) section for details.</span></span>

## <a name="collect-a-trace"></a><span data-ttu-id="6b63a-124">İzleme topla</span><span class="sxs-lookup"><span data-stu-id="6b63a-124">Collect a trace</span></span>

1. <span data-ttu-id="6b63a-125">, [ **Trace]** olarak adlandırılan ve uygulamayı çalıştırmak Için [ **Uygulama]** olarak adlandırılan iki kabuizin vardır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-125">Have two shells available - one for controlling tracing, referred to as **[Trace]**, and one for running the application, referred to as **[App]**.</span></span>

2. <span data-ttu-id="6b63a-126">**[Trace]** Koleksiyonu başlatın.</span><span class="sxs-lookup"><span data-stu-id="6b63a-126">**[Trace]** Start collection.</span></span>

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    <span data-ttu-id="6b63a-127">Beklenen Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6b63a-127">Expected Output:</span></span>

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. <span data-ttu-id="6b63a-128">**[Uygulama]** Uygulama kabuğunu aşağıdaki ortam değişkenleriyle ayarlama-bu, CoreCLR 'in izlenmesini izleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="6b63a-128">**[App]** Set up the application shell with the following environment variables - this enables tracing configuration of CoreCLR.</span></span>

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. <span data-ttu-id="6b63a-129">**[Uygulama]** Uygulamayı çalıştırın-performans sorununu yakalamak için ihtiyacınız olduğu sürece çalışmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-129">**[App]** Run the app - let it run as long as you need to in order to capture the performance problem.</span></span> <span data-ttu-id="6b63a-130">Tam Uzunluk, araştırmak istediğiniz performans sorununun gerçekleştiği zaman penceresini yeterince yakaladığı sürece gereksinim duyduğunuz kadar kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-130">The exact length can be as short as you need as long as it sufficiently captures the window of time where the performance problem you want to investigate occurs.</span></span>

    > ```bash
    > dotnet run
    > ```

5. <span data-ttu-id="6b63a-131">**[Trace]** Toplamayı durdur-isabet CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="6b63a-131">**[Trace]** Stop collection - hit CTRL+C.</span></span>

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    <span data-ttu-id="6b63a-132">Sıkıştırılmış izleme dosyası artık geçerli çalışma dizininde depolanıyor.</span><span class="sxs-lookup"><span data-stu-id="6b63a-132">The compressed trace file is now stored in the current working directory.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="6b63a-133">İzleme görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6b63a-133">View a trace</span></span>

<span data-ttu-id="6b63a-134">Toplanan izlemeyi görüntülemek için çeşitli seçenekler vardır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-134">There are a number of options for viewing the trace that was collected.</span></span> <span data-ttu-id="6b63a-135">İzlemeler, Windows üzerinde [PerfView](https://aka.ms/perfview) kullanılarak en iyi şekilde görüntülenebilir, ancak kendi veya kullanan Linux üzerinde doğrudan görüntülenebilirler `PerfCollect` `TraceCompass` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-135">Traces are best viewed using [PerfView](https://aka.ms/perfview) on Windows, but they can be viewed directly on Linux using `PerfCollect` itself or `TraceCompass`.</span></span>

### <a name="use-perfcollect-to-view-the-trace-file"></a><span data-ttu-id="6b63a-136">İzleme dosyasını görüntülemek için PerfCollect kullanın</span><span class="sxs-lookup"><span data-stu-id="6b63a-136">Use PerfCollect to view the trace file</span></span>

<span data-ttu-id="6b63a-137">Topladığımız izlemeyi görüntülemek için PerfCollect kendisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b63a-137">You can use perfcollect itself to view the trace that you collected.</span></span> <span data-ttu-id="6b63a-138">Bunu yapmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="6b63a-138">To do this, use the following command:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip
```

<span data-ttu-id="6b63a-139">Bu, varsayılan olarak, kullanılarak uygulamanın CPU izlemesini gösterir `perf` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-139">By default, this will show the CPU trace of the application using `perf`.</span></span>

<span data-ttu-id="6b63a-140">Aracılığıyla toplanan olaylara bakmak için `LTTng` , `-viewer lttng` tek tek olayları görmek için bayrağını geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b63a-140">To look at the events that were collected via `LTTng`, you can pass in the flag `-viewer lttng` to see the individual events:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

<span data-ttu-id="6b63a-141">Bu işlem `babeltrace` , olay yükünü yazdırmak için görüntüleyiciyi kullanır:</span><span class="sxs-lookup"><span data-stu-id="6b63a-141">This will use `babeltrace` viewer to print the events payload:</span></span>

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a><span data-ttu-id="6b63a-142">İzleme dosyasını açmak için PerfView kullanın</span><span class="sxs-lookup"><span data-stu-id="6b63a-142">Use PerfView to open the trace file</span></span>

<span data-ttu-id="6b63a-143">Hem CPU örneğinin hem de olaylarının toplam görünümünü görmek için, `PerfView` bir Windows makinesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b63a-143">To see an aggregate view of both the CPU sample and the events, you can use `PerfView` on a Windows machine.</span></span>

1. <span data-ttu-id="6b63a-144">trace.zip dosyasını Linux 'tan bir Windows makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6b63a-144">Copy the trace.zip file from Linux to a Windows machine.</span></span>

2. <span data-ttu-id="6b63a-145">PerfView öğesini öğesinden indirin <https://aka.ms/perfview> .</span><span class="sxs-lookup"><span data-stu-id="6b63a-145">Download PerfView from <https://aka.ms/perfview>.</span></span>

3. <span data-ttu-id="6b63a-146">PerfView.exe Çalıştır</span><span class="sxs-lookup"><span data-stu-id="6b63a-146">Run PerfView.exe</span></span>

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

<span data-ttu-id="6b63a-147">PerfView, izleme dosyasında bulunan verilere göre desteklenen görünümlerin listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6b63a-147">PerfView will display the list of views that are supported based on the data contained in the trace file.</span></span>

- <span data-ttu-id="6b63a-148">CPU araştırmaları için **CPU yığınları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-148">For CPU investigations, choose **CPU stacks**.</span></span>

- <span data-ttu-id="6b63a-149">Ayrıntılı GC bilgileri için **GCStats** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-149">For detailed GC information, choose **GCStats**.</span></span>

- <span data-ttu-id="6b63a-150">İşlem başına/modül/Yöntem JıT bilgileri için, **Jınstats**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-150">For per-process/module/method JIT information, choose **JITStats**.</span></span>

- <span data-ttu-id="6b63a-151">İhtiyacınız olan bilgiler için bir görünüm yoksa ham olaylar görünümündeki olayları aramaya çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="6b63a-151">If there is not a view for the information you need, you can try looking for the events in the raw events view.</span></span>  <span data-ttu-id="6b63a-152">**Olayları** seçin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-152">Choose **Events**.</span></span>

<span data-ttu-id="6b63a-153">PerfView içindeki görünümleri yorumlama hakkında daha fazla bilgi için bkz. görünümdeki yardım bağlantıları veya PerfView 'daki ana pencereden **Yardım->kullanıcıları Kılavuzu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-153">For more information on how to interpret views in PerfView, see help links in the view itself, or from the main window in PerfView, choose **Help->Users Guide**.</span></span>

> [!NOTE]
> <span data-ttu-id="6b63a-154">API aracılığıyla yazılan olaylar <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> (Framework 'ün olayları dahil), sağlayıcı adının altında gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="6b63a-154">Events written via <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> API (including the events from Framework) won't show up under their provider name.</span></span> <span data-ttu-id="6b63a-155">Bunun yerine, `EventSourceEvent` sağlayıcı altında olay olarak yazılır `Microsoft-Windows-DotNETRuntime` ve yükleri JSON serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-155">Instead, they are written as `EventSourceEvent` events under `Microsoft-Windows-DotNETRuntime` provider and their payloads are JSON serialized.</span></span>

### <a name="use-tracecompass-to-open-the-trace-file"></a><span data-ttu-id="6b63a-156">İzleme dosyasını açmak için Tracepusula kullanma</span><span class="sxs-lookup"><span data-stu-id="6b63a-156">Use TraceCompass to open the trace file</span></span>

<span data-ttu-id="6b63a-157">[Çakışan Küreler Tracepusula](https://www.eclipse.org/tracecompass/) , izlemeleri görüntülemek için kullanabileceğiniz başka bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-157">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) is another option you can use to view the traces.</span></span> <span data-ttu-id="6b63a-158">`TraceCompass` , Linux makinelerinde da çalışarak, izinizi bir Windows makinesine taşımanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="6b63a-158">`TraceCompass` works on Linux machines as well, so you don't need to move your trace over to a Windows machine.</span></span> <span data-ttu-id="6b63a-159">`TraceCompass`İzleme Dosyanızı açmak için kullanmak üzere dosyayı sıkıştırmayı açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-159">To use `TraceCompass` to open your trace file, you will need to unzip the file.</span></span>

```bash
unzip myTrace.trace.zip
```

<span data-ttu-id="6b63a-160">`perfcollect` , toplanan LTTng izlemesini içindeki bir alt dizinde CTF dosya biçiminde kaydeder `lttngTrace` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-160">`perfcollect` will save the LTTng trace it collected into a CTF file format in a subdirectory in the `lttngTrace`.</span></span> <span data-ttu-id="6b63a-161">Özel olarak, CTF dosyası gibi görünen bir dizinde yer alır `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-161">Specifically, the CTF file will be located in a directory that looks like `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\`.</span></span>

<span data-ttu-id="6b63a-162">' İ seçerek CTF izleme dosyasını açın `TraceCompass` `File -> Open Trace` ve `metadata` dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-162">You can open the CTF trace file in `TraceCompass` by selecting `File -> Open Trace` and select the `metadata` file.</span></span>

<span data-ttu-id="6b63a-163">Daha fazla ayrıntı için lütfen [ `TraceCompass` belgelere](https://www.eclipse.org/tracecompass/)bakın.</span><span class="sxs-lookup"><span data-stu-id="6b63a-163">For more details, please refer to [`TraceCompass` documentation](https://www.eclipse.org/tracecompass/).</span></span>

## <a name="resolve-framework-symbols"></a><span data-ttu-id="6b63a-164">Çerçeve sembollerini çözümle</span><span class="sxs-lookup"><span data-stu-id="6b63a-164">Resolve framework symbols</span></span>

<span data-ttu-id="6b63a-165">Çerçeve simgelerinin, izlemenin toplandığı sırada el ile oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-165">Framework symbols need to be manually generated at the time the trace is collected.</span></span> <span data-ttu-id="6b63a-166">Uygulama kodu tam zamanında derlenirken çerçeve önceden derlendiği için uygulama düzeyi sembollerine göre farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-166">They are different than app-level symbols because the framework is pre-compiled while app code is just-in-time-compiled.</span></span> <span data-ttu-id="6b63a-167">Yerel koda önceden derlenmiş çerçeve kodu için, `crossgen` yerel koddan yöntemlerin adına eşlemenin nasıl oluşturulacağını bilen bir çağrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-167">For framework code that was precompiled to native code, you need to call `crossgen` that knows how to generate the mapping from the native code to the name of the methods.</span></span>

<span data-ttu-id="6b63a-168">`perfcollect` , sizin için ayrıntıların çoğunu işleyebilir, ancak kullanılabilir olması gerekir `crossgen` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-168">`perfcollect` can handle most of the details for you, but it needs to have `crossgen` available.</span></span> <span data-ttu-id="6b63a-169">Varsayılan olarak .NET dağıtımı ile birlikte yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="6b63a-169">By default it is not installed with .NET distribution.</span></span> <span data-ttu-id="6b63a-170">Orada yoksa sizi `crossgen` `perfcollect` uyarır ve sizi bu yönergelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="6b63a-170">If `crossgen` is not there, `perfcollect` warns you and refers you to these instructions.</span></span> <span data-ttu-id="6b63a-171">Kullanmakta olduğunuz çalışma zamanına ilişkin çapraz genel sürümü tam olarak getirmek için ihtiyaç duyduğunuz şeyleri düzeltir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-171">To fix things you need to fetch exactly the right version of crossgen for the runtime you are using.</span></span> <span data-ttu-id="6b63a-172">Çapraz genel aracı 'nı .NET çalışma zamanı dll 'Leriyle aynı dizine yerleştirirseniz (örneğin, libcoreclr.so), `perfcollect` bunu bulabilir ve izleme dosyasına çerçeve sembolleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b63a-172">If you place the crossgen tool in the same directory as the .NET Runtime DLLs (for example, libcoreclr.so), then `perfcollect` can find it and add the framework symbols to the trace file for you.</span></span>

<span data-ttu-id="6b63a-173">Normalde, bir .NET uygulaması oluşturduğunuzda, Rest için çalışma zamanının paylaşılan bir kopyasını kullanarak yazdığınız kod için DLL 'yi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b63a-173">Normally when you create a .NET application, it just generates the DLL for the code you wrote, using a shared copy of the runtime for the rest.</span></span>   <span data-ttu-id="6b63a-174">Ancak, bir uygulamanın ' kendine ait ' bir sürümü olarak adlandırılan ' i de oluşturabilirsiniz ve bu, tüm çalışma zamanı dll 'Leri içerir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-174">However you can also generate what is called a 'self-contained' version of an application and this contains all runtime DLLs.</span></span> <span data-ttu-id="6b63a-175">`crossgen` , kendi kendine içerilen uygulamalar oluşturmak için kullanılan NuGet paketinin bir parçasıdır. bu nedenle, doğru sürümünü almanın bir yolu, `crossgen` uygulamanızın kendine dahil edilen bir paketini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-175">`crossgen` is part of the NuGet package that is used to create self-contained apps, so one way of getting the right version of `crossgen` is to create a self-contained package of your application.</span></span>

<span data-ttu-id="6b63a-176">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6b63a-176">For example:</span></span>

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

<span data-ttu-id="6b63a-177">Bu, yeni bir Merhaba Dünya uygulaması oluşturur ve bunu kendi kendine içerilen bir uygulama olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b63a-177">This creates a new Hello World application and builds it as a self-contained app.</span></span>

<span data-ttu-id="6b63a-178">Kendi içinde kapsanan uygulamayı oluşturmanın yan etkisi olarak, DotNet Aracı, Runtime. Linux-x64. Microsoft. netcore. app adlı bir NuGet paketini indirir ve ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION dizinine yerleştirirken, sürüm .NET Core çalışma zamanının sürüm numarasıdır (örneğin, 2.1.0).</span><span class="sxs-lookup"><span data-stu-id="6b63a-178">As a side effect of creating the self-contained application the dotnet tool will download a NuGet package called runtime.linux-x64.microsoft.netcore.app and place it in the directory ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, where VERSION is the version number of your .NET Core runtime (for example, 2.1.0).</span></span> <span data-ttu-id="6b63a-179">Bu, öğesinin altında bir araçlar dizinidir ve ihtiyacınız olan çapraz genel araç vardır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-179">Under that is a tools directory and inside there is the crossgen tool you need.</span></span> <span data-ttu-id="6b63a-180">.NET Core 3,0 ile başlayarak, paket konumu ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span><span class="sxs-lookup"><span data-stu-id="6b63a-180">Starting with .NET Core 3.0, the package location is ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span></span>

<span data-ttu-id="6b63a-181">`crossgen`Aracın, uygulamanız tarafından gerçekten kullanılan çalışma zamanının yanına alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-181">The `crossgen` tool needs to be put next to the runtime that is actually used by your application.</span></span> <span data-ttu-id="6b63a-182">Genellikle uygulamanız .NET Core 'un/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION adresinde yüklü olan paylaşılan sürümünü kullanır; burada sürüm .NET çalışma zamanının sürüm numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-182">Typically your app uses the shared version of .NET Core that is installed at /usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION where VERSION is the version number of the .NET Runtime.</span></span> <span data-ttu-id="6b63a-183">Bu paylaşılan bir konumdur, bu nedenle değiştirmek için süper kullanıcı olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-183">This is a shared location, so you need to be super-user to modify it.</span></span> <span data-ttu-id="6b63a-184">SÜRÜM 2.1.0 ise güncelleştirme komutları `crossgen` şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="6b63a-184">If the VERSION is 2.1.0 the commands to update `crossgen` would be:</span></span>

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

<span data-ttu-id="6b63a-185">Bunu yaptıktan sonra, `perfcollect` çerçeve sembolleri dahil etmek için çapraz gen kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-185">Once you have done this, `perfcollect` will use crossgen to include framework symbols.</span></span> <span data-ttu-id="6b63a-186">`perfcollect`Sorun için kullanılan uyarı, dışarıda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-186">The warning that `perfcollect` used to issue should go away.</span></span> <span data-ttu-id="6b63a-187">Bu, makine başına yalnızca bir kez olmalıdır (çalışma alanınızı güncelleştirene kadar).</span><span class="sxs-lookup"><span data-stu-id="6b63a-187">This only has to be one once per machine (until you update your runtime).</span></span>

### <a name="alternative-turn-off-use-of-precompiled-code"></a><span data-ttu-id="6b63a-188">Alternatif: önceden derlenmiş kodun kullanımını devre dışı bırakın</span><span class="sxs-lookup"><span data-stu-id="6b63a-188">Alternative: Turn off use of precompiled code</span></span>

<span data-ttu-id="6b63a-189">.NET çalışma zamanını (eklemek için) güncelleştiremezseniz `crossgen` veya yukarıdaki yordam bazı nedenlerle çalışmazsa, çerçeve sembolleri almaya yönelik başka bir yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-189">If you don't have the ability to update the .NET Runtime (to add `crossgen`), or if the above procedure did not work for some reason, there is another approach to getting framework symbols.</span></span> <span data-ttu-id="6b63a-190">Çalışma zamanına yalnızca önceden derlenmiş Framework kodunu kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-190">You can tell the runtime to simply not use the precompiled framework code.</span></span> <span data-ttu-id="6b63a-191">Kod, tam zamanında derlenir ve `crossgen` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-191">The code will be Just-In-Time compiled and `crossgen` is not needed.</span></span>

> [!NOTE]
> <span data-ttu-id="6b63a-192">Bu yaklaşım seçildiğinde uygulamanızın başlama süresi artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-192">Choosing this approach may increase the startup time for your application.</span></span>

<span data-ttu-id="6b63a-193">Bunu yapmak için aşağıdaki ortam değişkenini ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b63a-193">To do this, you can add the following environment variable:</span></span>

```bash
export COMPlus_ZapDisable=1
```

<span data-ttu-id="6b63a-194">Bu değişiklik ile tüm .NET kodu için sembolleri almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-194">With this change, you should get the symbols for all .NET code.</span></span>

## <a name="get-symbols-for-the-native-runtime"></a><span data-ttu-id="6b63a-195">Yerel çalışma zamanı için sembolleri al</span><span class="sxs-lookup"><span data-stu-id="6b63a-195">Get symbols for the native runtime</span></span>

<span data-ttu-id="6b63a-196">Çoğu zaman kendi kodunuzla ilgileniyorsunuz. Bu, `perfcollect` Varsayılan olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-196">Most of the time you are interested in your own code, which `perfcollect` resolves by default.</span></span> <span data-ttu-id="6b63a-197">Bazen, .NET DLL 'leri içinde neler olduğunu (son bölümün yaklaşık olarak) görmek yararlıdır, ancak bazen yerel çalışma zamanı dll 'lerinde (genellikle libcoreclr.so) neler olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="6b63a-197">Sometimes it is useful to see what is going on inside the .NET DLLs (which is what the last section was about), but sometimes what is going on in the native runtime dlls (typically libcoreclr.so), is interesting.</span></span>  <span data-ttu-id="6b63a-198">`perfcollect` , yalnızca bu yerel dll sembolleri varsa (ve bunların kendisi için oldukları kitaplığın yanında ise) sembolleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6b63a-198">`perfcollect` will resolve the symbols for these when it converts its data, but only if the symbols for these native DLLs are present (and are beside the library they are for).</span></span>

<span data-ttu-id="6b63a-199">Bunu yapan [DotNet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) adlı bir genel komut vardır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-199">There is a global command called [dotnet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) that does this.</span></span> <span data-ttu-id="6b63a-200">Yerel çalışma zamanı sembolleri almak için DotNet-symbol kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="6b63a-200">To use dotnet-symbol to get native runtime symbols:</span></span>

1. <span data-ttu-id="6b63a-201">`dotnet-symbol` yükleme:</span><span class="sxs-lookup"><span data-stu-id="6b63a-201">Install `dotnet-symbol`:</span></span>

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. <span data-ttu-id="6b63a-202">Sembolleri indirin.</span><span class="sxs-lookup"><span data-stu-id="6b63a-202">Download the symbols.</span></span> <span data-ttu-id="6b63a-203">.NET Core çalışma zamanının yüklü sürümü 2.1.0 ise, bunu yapmak için komut şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="6b63a-203">If your installed version of the .NET Core runtime is 2.1.0, the command to do this is:</span></span>

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. <span data-ttu-id="6b63a-204">Sembolleri doğru yere kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6b63a-204">Copy the symbols to the correct place.</span></span>

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    <span data-ttu-id="6b63a-205">Uygun dizine yazma erişiminizin olmadığı için bu işlem yapılacağından, `perf buildid-cache` sembolleri eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b63a-205">If this cannot be done because you do not have write access to the appropriate directory, you can use `perf buildid-cache` to add the symbols.</span></span>

<span data-ttu-id="6b63a-206">Bundan sonra, çalıştırdığınızda yerel dll 'ler için simgesel adlar almalısınız `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-206">After this, you should get symbolic names for the native dlls when you run `perfcollect`.</span></span>

## <a name="collect-in-a-docker-container"></a><span data-ttu-id="6b63a-207">Bir Docker kapsayıcısında toplayın</span><span class="sxs-lookup"><span data-stu-id="6b63a-207">Collect in a Docker container</span></span>

<span data-ttu-id="6b63a-208">Kapsayıcı ortamlarında kullanma hakkında daha fazla bilgi için `perfcollect` bkz. [kapsayıcılarda tanılamayı toplama](./diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="6b63a-208">For more information on how to use `perfcollect` in container environments, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

## <a name="learn-more-about-collection-options"></a><span data-ttu-id="6b63a-209">Koleksiyon seçenekleri hakkında daha fazla bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="6b63a-209">Learn more about collection options</span></span>

<span data-ttu-id="6b63a-210">`perfcollect`Tanılama gereksinimlerinize daha iyi uyacak şekilde, aşağıdaki isteğe bağlı bayrakları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b63a-210">You can specify the following optional flags with `perfcollect` to better suit your diagnostic needs.</span></span>

### <a name="collect-for-a-specific-duration"></a><span data-ttu-id="6b63a-211">Belirli bir süre için topla</span><span class="sxs-lookup"><span data-stu-id="6b63a-211">Collect for a specific duration</span></span>

<span data-ttu-id="6b63a-212">Belirli bir süre için bir izleme toplamak istediğinizde, `-collectsec` ve için bir izlemenin toplanacağı toplam saniyeyi belirten bir sayı olan seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b63a-212">When you want to collect a trace for a specific duration, you can use `-collectsec` option followed by a number specifying the total seconds to collect a trace for.</span></span>

### <a name="collect-threadtime-traces"></a><span data-ttu-id="6b63a-213">İşParçacığıSüresi izlemelerini topla</span><span class="sxs-lookup"><span data-stu-id="6b63a-213">Collect threadtime traces</span></span>

<span data-ttu-id="6b63a-214">`-threadtime`İle belirtmek `perfcollect` iş parçacığı başına CPU kullanım verilerini toplamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6b63a-214">Specifying `-threadtime` with `perfcollect` lets you collect per-thread CPU usage data.</span></span> <span data-ttu-id="6b63a-215">Bu, her iş parçacığının CPU süresini hangi noktada harcamalarından analiz etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b63a-215">This lets you analyze where every thread was spending its CPU time.</span></span>

### <a name="collect-traces-for-managed-memory-and-garbage-collector-performance"></a><span data-ttu-id="6b63a-216">Yönetilen bellek ve çöp toplayıcı performansı için izlemeleri toplayın</span><span class="sxs-lookup"><span data-stu-id="6b63a-216">Collect traces for managed memory and garbage collector performance</span></span>

<span data-ttu-id="6b63a-217">Aşağıdaki seçenekler, GC olaylarını özel olarak çalışma zamanından toplamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b63a-217">The following options let you specifically collect the GC events from the runtime.</span></span>

* `perfcollect collect -gccollectonly`

<span data-ttu-id="6b63a-218">Yalnızca minimal bir GC toplama olayları kümesi toplayın.</span><span class="sxs-lookup"><span data-stu-id="6b63a-218">Collect only a minimal set of GC Collection events.</span></span> <span data-ttu-id="6b63a-219">Bu, hedef uygulamanın performansına en düşük etkisi olan en az ayrıntılı GC olay toplama profilidir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-219">This is the least verbose GC eventing collection profile with the lowest impact on the target app's performance.</span></span> <span data-ttu-id="6b63a-220">Bu komut `PerfView.exe /GCCollectOnly collect` PerfView komutuna benzer.</span><span class="sxs-lookup"><span data-stu-id="6b63a-220">This command is analogous to `PerfView.exe /GCCollectOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gconly`

<span data-ttu-id="6b63a-221">JıT, yükleyici ve özel durum olaylarıyla daha ayrıntılı GC toplama olayları toplayın.</span><span class="sxs-lookup"><span data-stu-id="6b63a-221">Collect more verbose GC collection events with JIT, Loader, and Exception events.</span></span> <span data-ttu-id="6b63a-222">Bu, daha ayrıntılı Olaylar (örneğin, ayırma bilgileri ve GC JOIN bilgileri) ister ve hedef uygulamanın performansına göre daha fazla etkiye sahip olacaktır `-gccollectonly` .</span><span class="sxs-lookup"><span data-stu-id="6b63a-222">This requests more verbose events (such as the allocation information and GC join information) and will have more impact to the target app's performance than `-gccollectonly` option.</span></span> <span data-ttu-id="6b63a-223">Bu komut `PerfView.exe /GCOnly collect` PerfView komutuna benzer.</span><span class="sxs-lookup"><span data-stu-id="6b63a-223">This command is analogous to `PerfView.exe /GCOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gcwithheap`

<span data-ttu-id="6b63a-224">En ayrıntılı GC toplama olaylarını toplayın. Bu, yığın daha fazla sonuç ve hareketlerini de izler.</span><span class="sxs-lookup"><span data-stu-id="6b63a-224">Collect the most verbose GC collection events which tracks the heap survival and movements as well.</span></span> <span data-ttu-id="6b63a-225">Bu, GC davranışının derinlemesine analizini sağlar ancak her GC ikiden fazla kez daha uzun sürebileceğinden yüksek performans maliyeti olur.</span><span class="sxs-lookup"><span data-stu-id="6b63a-225">This gives in-depth analysis of the GC behavior but will incur high performance cost as each GC can take more than two times longer.</span></span> <span data-ttu-id="6b63a-226">Üretim ortamlarında izlerken bu izleme seçeneğini kullanmanın performansını anlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="6b63a-226">It is recommended you understand the performance implication of using this trace option when tracing in production environments.</span></span>
