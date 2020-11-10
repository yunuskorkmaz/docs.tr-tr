---
title: PerfCollect ile .NET uygulamalarını izleme.
description: .NET ' te PerfCollect ile izleme toplama konusunda size kılavuzluk eden bir öğretici.
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 7bf058869f0b9f76204d775b12febe7c58b78877
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445809"
---
# <a name="tracing-net-applications-with-perfcollect"></a><span data-ttu-id="15da0-103">PerfCollect ile .NET uygulamalarını izleme</span><span class="sxs-lookup"><span data-stu-id="15da0-103">Tracing .NET applications with PerfCollect</span></span>

<span data-ttu-id="15da0-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="15da0-104">**This article applies to: ✔️** .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="15da0-105">Linux üzerinde performans sorunlarıyla karşılaşıldığında, bir izleme toplama, `perfcollect` performans sorunu sırasında makinede neler olduğunu hakkında ayrıntılı bilgi toplamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15da0-105">When performance problems are encountered on Linux, collecting a trace with `perfcollect` can be used to gather detailed information about what was happening on the machine at the time of the performance problem.</span></span>

<span data-ttu-id="15da0-106">`perfcollect`, çalışma zamanının veya herhangi bir [EventSource](xref:System.Diagnostics.Tracing.EventListener)'dan yazılmış olayları toplamak Için [Linux izleme Tookit-Next oluşturma (lttng)](https://lttng.org) kullanan bir bash betiğidir ve hedef işlemin CPU örneklerini toplamak için [perf](https://perf.wiki.kernel.org/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="15da0-106">`perfcollect` is a bash script that leverages [Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) to collect events written from the runtime or any [EventSource](xref:System.Diagnostics.Tracing.EventListener), as well as [perf](https://perf.wiki.kernel.org/) to collect CPU samples of the target process.</span></span>

## <a name="preparing-your-machine"></a><span data-ttu-id="15da0-107">Makineniz hazırlanıyor</span><span class="sxs-lookup"><span data-stu-id="15da0-107">Preparing Your Machine</span></span>

<span data-ttu-id="15da0-108">Makinenizi ile bir performans izlemesi toplayacak şekilde hazırlamak için aşağıdaki adımları izleyin `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="15da0-108">Follow these steps to prepare your machine to collect a performance trace with `perfcollect`.</span></span>

> [!NOTE]
> <span data-ttu-id="15da0-109">Bir kapsayıcı ortamındaysanız, kapsayıcının özelliği olması gerekir `SYS_ADMIN` .</span><span class="sxs-lookup"><span data-stu-id="15da0-109">If you are in a container environment, your container needs to have `SYS_ADMIN` capability.</span></span> <span data-ttu-id="15da0-110">PerfCollect kullanarak kapsayıcı içindeki uygulamaları izleme hakkında daha fazla bilgi için bkz. [kapsayıcılar içinde tanılama toplama](./diagnostics-in-containers.md) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="15da0-110">For more information on tracing applications inside container using PerfCollect, refer to [Collect diagnostics in containers](./diagnostics-in-containers.md) documentation.</span></span>

1. <span data-ttu-id="15da0-111">İndirin `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="15da0-111">Download `perfcollect`.</span></span>

    > ```bash
    > curl -OL http://aka.ms/perfcollect
    > ```

2. <span data-ttu-id="15da0-112">Betiği çalıştırılabilir yapın.</span><span class="sxs-lookup"><span data-stu-id="15da0-112">Make the script executable.</span></span>

    > ```bash
    > chmod +x perfcollect
    > ```

3. <span data-ttu-id="15da0-113">İzleme önkoşullarını yükler-bunlar gerçek izleme kitaplıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="15da0-113">Install tracing prerequisites - these are the actual tracing libraries.</span></span>

    > ```bash
    > sudo ./perfcollect install
    > ```

    <span data-ttu-id="15da0-114">Bu işlem makinenize aşağıdaki önkoşulları yükler:</span><span class="sxs-lookup"><span data-stu-id="15da0-114">This will install the following prerequisites on your machine:</span></span>

    1. <span data-ttu-id="15da0-115">`perf`: Linux performans olayları alt sistem ve yardımcı Kullanıcı modu koleksiyonu/görüntüleyici uygulaması.</span><span class="sxs-lookup"><span data-stu-id="15da0-115">`perf`: the Linux Performance Events sub-system and companion user-mode collection/viewer application.</span></span> <span data-ttu-id="15da0-116">`perf` , Linux çekirdek kaynağının bir parçasıdır, ancak genellikle varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="15da0-116">`perf` is part of the Linux kernel source, but is not usually installed by default.</span></span>

    2. <span data-ttu-id="15da0-117">`LTTng`: Çalışma zamanında, CoreCLR tarafından yayılan olay verilerini yakalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15da0-117">`LTTng`: Used to capture event data emitted at runtime by CoreCLR.</span></span> <span data-ttu-id="15da0-118">Bu veriler daha sonra GC, JıT ve iş parçacığı havuzu gibi çeşitli çalışma zamanı bileşenlerinin davranışını çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15da0-118">This data is then used to analyze the behavior of various runtime components such as the GC, JIT and thread pool.</span></span>

<span data-ttu-id="15da0-119">.NET Core 'un son sürümleri ve Linux performans aracı, çerçeve kodu için yöntem adlarının otomatik olarak çözümlenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="15da0-119">Recent versions of .NET Core and the Linux perf tool support automatic resolution of method names for framework code.</span></span> <span data-ttu-id="15da0-120">.NET Core sürüm 3,1 veya daha az bir sürümle çalışıyorsanız, ek bir adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="15da0-120">If you are working with .NET Core version 3.1 or less, an extra step is necessary.</span></span> <span data-ttu-id="15da0-121">Ayrıntılar için bkz. [çerçeve sembollerini çözme](#resolving-framework-symbols) .</span><span class="sxs-lookup"><span data-stu-id="15da0-121">See [Resolving Framework Symbols](#resolving-framework-symbols) for details.</span></span>

<span data-ttu-id="15da0-122">Yerel çalışma zamanı dll 'Lerinin (örneğin, libcoreclr.so) yöntem adlarını çözümlemek için, `perfcollect` verileri dönüştürürken, ancak yalnızca bu ikililerin sembolleri varsa, simgeler için sembolleri çözer.</span><span class="sxs-lookup"><span data-stu-id="15da0-122">For resolving method names of native runtime DLLs (such as libcoreclr.so), `perfcollect` will resolve symbols for them when it converts the data, but only if the symbols for these binaries are present.</span></span> <span data-ttu-id="15da0-123">Ayrıntılar için bkz. [yerel çalışma zamanı Için semboller alma](#getting-symbols-for-the-native-runtime) bölümü.</span><span class="sxs-lookup"><span data-stu-id="15da0-123">See [Getting Symbols for the Native Runtime](#getting-symbols-for-the-native-runtime) section for details.</span></span>

## <a name="collecting-a-trace"></a><span data-ttu-id="15da0-124">Izleme toplama</span><span class="sxs-lookup"><span data-stu-id="15da0-124">Collecting a Trace</span></span>

1. <span data-ttu-id="15da0-125">, [ **Trace]** olarak adlandırılan ve uygulamayı çalıştırmak Için [ **Uygulama]** olarak adlandırılan iki kabuizin vardır.</span><span class="sxs-lookup"><span data-stu-id="15da0-125">Have two shells available - one for controlling tracing, referred to as **[Trace]** , and one for running the application, referred to as **[App]**.</span></span>

2. <span data-ttu-id="15da0-126">**[Trace]** Koleksiyonu başlatın.</span><span class="sxs-lookup"><span data-stu-id="15da0-126">**[Trace]** Start collection.</span></span>

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    <span data-ttu-id="15da0-127">Beklenen Çıktı:</span><span class="sxs-lookup"><span data-stu-id="15da0-127">Expected Output:</span></span>

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. <span data-ttu-id="15da0-128">**[Uygulama]** Uygulama kabuğunu aşağıdaki ortam değişkenleriyle ayarlama-bu, CoreCLR 'in izlenmesini izleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="15da0-128">**[App]** Set up the application shell with the following environment variables - this enables tracing configuration of CoreCLR.</span></span>

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. <span data-ttu-id="15da0-129">**[Uygulama]** Uygulamayı çalıştırın-performans sorununu yakalamak için ihtiyacınız olduğu sürece çalışmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="15da0-129">**[App]** Run the app - let it run as long as you need to in order to capture the performance problem.</span></span> <span data-ttu-id="15da0-130">Tam Uzunluk, araştırmak istediğiniz performans sorununun gerçekleştiği zaman penceresini yeterince yakaladığı sürece gereksinim duyduğunuz kadar kısa olabilir.</span><span class="sxs-lookup"><span data-stu-id="15da0-130">The exact length can be as short as you need as long as it sufficiently captures the window of time where the performance problem you want to investigate occurs.</span></span>

    > ```bash
    > dotnet run
    > ```

5. <span data-ttu-id="15da0-131">**[Trace]** Toplamayı durdur-isabet CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="15da0-131">**[Trace]** Stop collection - hit CTRL+C.</span></span>

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

    <span data-ttu-id="15da0-132">Sıkıştırılmış izleme dosyası artık geçerli çalışma dizininde depolanıyor.</span><span class="sxs-lookup"><span data-stu-id="15da0-132">The compressed trace file is now stored in the current working directory.</span></span>

## <a name="viewing-a-trace"></a><span data-ttu-id="15da0-133">Izleme görüntüleme</span><span class="sxs-lookup"><span data-stu-id="15da0-133">Viewing a Trace</span></span>

<span data-ttu-id="15da0-134">Toplanan izlemeyi görüntülemek için bazı seçenekler vardır.</span><span class="sxs-lookup"><span data-stu-id="15da0-134">There are number of options for viewing the trace that was collected.</span></span> <span data-ttu-id="15da0-135">İzlemeler, Windows üzerinde [PerfView](http://aka.ms/perfview>) kullanılarak en iyi şekilde görüntülenebilir, ancak kendi veya kullanan Linux üzerinde doğrudan görüntülenebilirler `PerfCollect` `TraceCompass` .</span><span class="sxs-lookup"><span data-stu-id="15da0-135">Traces are best viewed using [PerfView](http://aka.ms/perfview>) on Windows, but they can be viewed directly on Linux using `PerfCollect` itself or `TraceCompass`.</span></span>

### <a name="using-perfcollect-to-view-the-trace-file"></a><span data-ttu-id="15da0-136">İzleme dosyasını görüntülemek için PerfCollect kullanma</span><span class="sxs-lookup"><span data-stu-id="15da0-136">Using PerfCollect to view the trace file</span></span>

<span data-ttu-id="15da0-137">Topladığımız izlemeyi görüntülemek için PerfCollect kendisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15da0-137">You can use perfcollect itself to view the trace that you collected.</span></span> <span data-ttu-id="15da0-138">Bunu yapmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="15da0-138">To do this, use the following command:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip
```

<span data-ttu-id="15da0-139">Bu, varsayılan olarak, kullanılarak uygulamanın CPU izlemesini gösterir `perf` .</span><span class="sxs-lookup"><span data-stu-id="15da0-139">By default, this will show the CPU trace of the application using `perf`.</span></span>

<span data-ttu-id="15da0-140">Aracılığıyla toplanan olaylara bakmak için `LTTng` , `-viewer lttng` tek tek olayları görmek için bayrağını geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15da0-140">To look at the events that were collected via `LTTng`, you can pass in the flag `-viewer lttng` to see the individual events:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

<span data-ttu-id="15da0-141">Bu işlem `babeltrace` , olay yükünü yazdırmak için görüntüleyiciyi kullanır:</span><span class="sxs-lookup"><span data-stu-id="15da0-141">This will use `babeltrace` viewer to print the events payload:</span></span>

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="using-perfview-to-open-the-trace-file"></a><span data-ttu-id="15da0-142">İzleme dosyasını açmak için PerfView kullanma</span><span class="sxs-lookup"><span data-stu-id="15da0-142">Using PerfView to open the trace file</span></span>

<span data-ttu-id="15da0-143">Hem CPU örneğinin hem de olaylarının toplam görünümünü görmek için, `PerfView` bir Windows makinesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15da0-143">To see an aggregate view of both the CPU sample and the events, you can use `PerfView` on a Windows machine.</span></span>

1. <span data-ttu-id="15da0-144">trace.zip dosyasını Linux 'tan bir Windows makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="15da0-144">Copy the trace.zip file from Linux to a Windows machine.</span></span>

2. <span data-ttu-id="15da0-145">PerfView öğesini öğesinden indirin <http://aka.ms/perfview> .</span><span class="sxs-lookup"><span data-stu-id="15da0-145">Download PerfView from <http://aka.ms/perfview>.</span></span>

3. <span data-ttu-id="15da0-146">PerfView.exe Çalıştır</span><span class="sxs-lookup"><span data-stu-id="15da0-146">Run PerfView.exe</span></span>

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

<span data-ttu-id="15da0-147">PerfView, izleme dosyasında bulunan verilere göre desteklenen görünümlerin listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="15da0-147">PerfView will display the list of views that are supported based on the data contained in the trace file.</span></span>

- <span data-ttu-id="15da0-148">CPU araştırmaları için **CPU yığınları** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="15da0-148">For CPU investigations, choose **CPU stacks**.</span></span>

- <span data-ttu-id="15da0-149">Ayrıntılı GC bilgileri için **GCStats** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="15da0-149">For very detailed GC information, choose **GCStats**.</span></span>

- <span data-ttu-id="15da0-150">İşlem başına/modül/Yöntem JıT bilgileri için, **Jınstats** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="15da0-150">For per-process/module/method JIT information, choose **JITStats**.</span></span>

- <span data-ttu-id="15da0-151">İhtiyacınız olan bilgiler için bir görünüm yoksa ham olaylar görünümündeki olayları aramaya çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="15da0-151">If there is not a view for the information you need, you can try looking for the events in the raw events view.</span></span>  <span data-ttu-id="15da0-152">**Olayları** seçin.</span><span class="sxs-lookup"><span data-stu-id="15da0-152">Choose **Events**.</span></span>

<span data-ttu-id="15da0-153">PerfView içindeki görünümleri yorumlama hakkında daha fazla bilgi için bkz. görünümdeki yardım bağlantıları veya PerfView 'daki ana pencereden **Yardım->kullanıcıları Kılavuzu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="15da0-153">For more details on how to interpret views in PerfView, see help links in the view itself, or from the main window in PerfView choose **Help->Users Guide**.</span></span>

### <a name="using-tracecompass-to-open-the-trace-file"></a><span data-ttu-id="15da0-154">İzleme dosyasını açmak için Tracepusula kullanma</span><span class="sxs-lookup"><span data-stu-id="15da0-154">Using TraceCompass to open the trace file</span></span>

<span data-ttu-id="15da0-155">[Çakışan Küreler Tracepusula](https://www.eclipse.org/tracecompass/) , izlemeleri görüntülemek için kullanabileceğiniz başka bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="15da0-155">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) is another option you may use to view the traces.</span></span> <span data-ttu-id="15da0-156">`TraceCompass` , Linux makinelerinde da çalışarak, izinizi bir Windows makinesine taşımanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="15da0-156">`TraceCompass` works on Linux machines as well, so you don't need to move your trace over to a Windows machine.</span></span> <span data-ttu-id="15da0-157">`TraceCompass`İzleme Dosyanızı açmak için kullanmak üzere dosyayı sıkıştırmayı açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15da0-157">To use `TraceCompass` to open your trace file, you will need to unzip the file.</span></span>

```bash
unzip myTrace.trace.zip
```

<span data-ttu-id="15da0-158">`perfcollect` , toplanan LTTng izlemesini içindeki bir alt dizinde CTF dosya biçiminde kaydeder `lttngTrace` .</span><span class="sxs-lookup"><span data-stu-id="15da0-158">`perfcollect` will save the LTTng trace it collected into a CTF file format in a subdirectory in the `lttngTrace`.</span></span> <span data-ttu-id="15da0-159">Özel olarak, CTF dosyası gibi görünen bir dizinde yer alır `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` .</span><span class="sxs-lookup"><span data-stu-id="15da0-159">Specifically, the CTF file will be located in a directory that looks like `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\`.</span></span>

<span data-ttu-id="15da0-160">' İ seçerek CTF izleme dosyasını açın `TraceCompass` `File -> Open Trace` ve `metadata` dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="15da0-160">You can open the CTF trace file in `TraceCompass` by selecting `File -> Open Trace` and select the `metadata` file.</span></span>

<span data-ttu-id="15da0-161">Daha fazla ayrıntı için lütfen [ `TraceCompass` belgelere](https://www.eclipse.org/tracecompass/)bakın.</span><span class="sxs-lookup"><span data-stu-id="15da0-161">For more details, please refer to [`TraceCompass` documentation](https://www.eclipse.org/tracecompass/).</span></span>

## <a name="resolving-framework-symbols"></a><span data-ttu-id="15da0-162">Çerçeve sembollerini çözme</span><span class="sxs-lookup"><span data-stu-id="15da0-162">Resolving Framework Symbols</span></span>

<span data-ttu-id="15da0-163">Çerçeve simgelerinin, izlemenin toplandığı sırada el ile oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="15da0-163">Framework symbols need to be manually generated at the time the trace is collected.</span></span> <span data-ttu-id="15da0-164">Uygulama kodu tam zamanında derlenirken çerçeve önceden derlendiği için uygulama düzeyi sembollerine göre farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="15da0-164">They are different than app-level symbols because the framework is pre-compiled while app code is just-in-time-compiled.</span></span> <span data-ttu-id="15da0-165">Yerel koda önceden derlenmiş çerçeve kodu için, `crossgen` yerel koddan yöntemlerin adına eşlemenin nasıl oluşturulacağını bilen bir çağrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15da0-165">For framework code that was precompiled to native code, you need to call `crossgen` that knows how to generate the mapping from the native code to the name of the methods.</span></span>

<span data-ttu-id="15da0-166">`perfcollect` , sizin için ayrıntıların çoğunu işleyebilir, ancak kullanılabilir olması gerekir `crossgen` .</span><span class="sxs-lookup"><span data-stu-id="15da0-166">`perfcollect` can handle most of the details for you, but it needs to have `crossgen` available.</span></span> <span data-ttu-id="15da0-167">Varsayılan olarak .NET dağıtımı ile birlikte yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="15da0-167">By default it is not installed with .NET distribution.</span></span> <span data-ttu-id="15da0-168">Orada yoksa sizi `crossgen` `perfcollect` uyarır ve sizi bu yönergelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="15da0-168">If `crossgen` is not there, `perfcollect` warns you and refers you to these instructions.</span></span> <span data-ttu-id="15da0-169">Kullanmakta olduğunuz çalışma zamanına ilişkin çapraz genel sürümü tam olarak getirmek için ihtiyaç duyduğunuz şeyleri düzeltir.</span><span class="sxs-lookup"><span data-stu-id="15da0-169">To fix things you need to fetch exactly the right version of crossgen for the runtime you are using.</span></span> <span data-ttu-id="15da0-170">Çapraz genel aracı 'nı .NET çalışma zamanı dll 'Leriyle aynı dizine yerleştirirseniz (örn. libcoreclr.so), `perfcollect` bunu bulabilir ve izleme dosyasına çerçeve sembolleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15da0-170">If you place the crossgen tool in the same directory as the .NET Runtime DLLs (e.g. libcoreclr.so), then `perfcollect` can find it and add the framework symbols to the trace file for you.</span></span>

<span data-ttu-id="15da0-171">Normalde, bir .NET uygulaması oluşturduğunuzda, Rest için çalışma zamanının paylaşılan bir kopyasını kullanarak yazdığınız kod için DLL 'yi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15da0-171">Normally when you create a .NET application, it just generates the DLL for the code you wrote, using a shared copy of the runtime for the rest.</span></span>   <span data-ttu-id="15da0-172">Ancak, bir uygulamanın ' kendine ait ' bir sürümü olarak adlandırılan ' i de oluşturabilirsiniz ve bu, tüm çalışma zamanı dll 'Leri içerir.</span><span class="sxs-lookup"><span data-stu-id="15da0-172">However you can also generate what is called a 'self-contained' version of an application and this contains all runtime DLLs.</span></span> <span data-ttu-id="15da0-173">`crossgen` , kendi kendine içerilen uygulamalar oluşturmak için kullanılan NuGet paketinin bir parçasıdır. bu nedenle, doğru sürümünü almanın bir yolu, `crossgen` uygulamanızın kendine dahil edilen bir paketini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="15da0-173">`crossgen` is part of the Nuget package that is used to create self-contained apps, so one way of getting the right version of `crossgen` is to create a self-contained package of your application.</span></span>

<span data-ttu-id="15da0-174">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="15da0-174">For example:</span></span>

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

<span data-ttu-id="15da0-175">Bu, yeni bir Merhaba Dünya uygulaması oluşturur ve bunu kendi kendine içerilen bir uygulama olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15da0-175">This creates a new Hello World application and builds it as a self-contained app.</span></span>

<span data-ttu-id="15da0-176">Kendi içinde kapsanan uygulamayı oluşturmanın yan etkisi olarak, DotNet Aracı, Runtime. Linux-x64. Microsoft. netcore. app adlı bir NuGet paketini indirir ve ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION dizinine yerleştirirken, sürüm .NET Core çalışma zamanının sürüm numarasıdır (ör. 2.1.0).</span><span class="sxs-lookup"><span data-stu-id="15da0-176">As a side effect of creating the self-contained application the dotnet tool will download a nuget package called runtime.linux-x64.microsoft.netcore.app and place it in the directory ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, where VERSION is the version number of your .NET Core runtime (e.g. 2.1.0).</span></span> <span data-ttu-id="15da0-177">Bu, öğesinin altında bir araçlar dizinidir ve ihtiyacınız olan çapraz genel araç vardır.</span><span class="sxs-lookup"><span data-stu-id="15da0-177">Under that is a tools directory and inside there is the crossgen tool you need.</span></span> <span data-ttu-id="15da0-178">.NET Core 3,0 ile başlayarak, paket konumu ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span><span class="sxs-lookup"><span data-stu-id="15da0-178">Starting with .NET Core 3.0, the package location is ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span></span>

<span data-ttu-id="15da0-179">`crossgen`Aracın, uygulamanız tarafından gerçekten kullanılan çalışma zamanının yanına alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="15da0-179">The `crossgen` tool needs to be put next to the runtime that is actually used by your application.</span></span> <span data-ttu-id="15da0-180">Genellikle uygulamanız .NET Core 'un/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION adresinde yüklü olan paylaşılan sürümünü kullanır; burada sürüm .NET çalışma zamanının sürüm numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="15da0-180">Typically your app uses the shared version of .NET Core that is installed at /usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION where VERSION is the version number of the .NET Runtime.</span></span> <span data-ttu-id="15da0-181">Bu paylaşılan bir konumdur, bu nedenle değiştirmek için süper kullanıcı olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15da0-181">This is a shared location, so you need to be super-user to modify it.</span></span> <span data-ttu-id="15da0-182">SÜRÜM 2.1.0 ise güncelleştirme komutları `crossgen` şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="15da0-182">If the VERSION is 2.1.0 the commands to update `crossgen` would be:</span></span>

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

<span data-ttu-id="15da0-183">Bunu yaptıktan sonra, `perfcollect` çerçeve sembolleri dahil etmek için çapraz gen kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="15da0-183">Once you have done this, `perfcollect` will use crossgen to include framework symbols.</span></span> <span data-ttu-id="15da0-184">`perfcollect`Sorun için kullanılan uyarı, dışarıda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15da0-184">The warning that `perfcollect` used to issue should go away.</span></span> <span data-ttu-id="15da0-185">Bu, makine başına yalnızca bir kez olmalıdır (çalışma alanınızı güncelleştirene kadar).</span><span class="sxs-lookup"><span data-stu-id="15da0-185">This only has to be one once per machine (until you update your runtime).</span></span>

### <a name="alternative-turn-off-use-of-precompiled-code"></a><span data-ttu-id="15da0-186">Alternatif: önceden derlenmiş kodun kullanımını devre dışı bırakın</span><span class="sxs-lookup"><span data-stu-id="15da0-186">Alternative: Turn off use of precompiled code</span></span>

<span data-ttu-id="15da0-187">.NET çalışma zamanını (eklemek için) güncelleştiremezseniz `crossgen` veya yukarıdaki yordam bazı nedenlerle çalışmazsa, çerçeve sembolleri almaya yönelik başka bir yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="15da0-187">If you don't have the ability to update the .NET Runtime (to add `crossgen`), or if the above procedure did not work for some reason, there is another approach to getting framework symbols.</span></span> <span data-ttu-id="15da0-188">Çalışma zamanına yalnızca önceden derlenmiş Framework kodunu kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="15da0-188">You can tell the runtime to simply not use the precompiled framework code.</span></span> <span data-ttu-id="15da0-189">Kod, tam zamanında derlenir ve `crossgen` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="15da0-189">The code will be Just-In-Time compiled and `crossgen` is not needed.</span></span>

> [!NOTE]
> <span data-ttu-id="15da0-190">Bu yaklaşım seçildiğinde uygulamanızın başlama süresi artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="15da0-190">Choosing this approach may increase the startup time for your application.</span></span>

<span data-ttu-id="15da0-191">Bunu yapmak için aşağıdaki ortam değişkenini ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15da0-191">To do this, you can add the following environment variable:</span></span>

```bash
export COMPlus_ZapDisable=1
```

<span data-ttu-id="15da0-192">Bu değişiklik ile tüm .NET kodu için sembolleri almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15da0-192">With this change you should get the symbols for all .NET code.</span></span>

## <a name="getting-symbols-for-the-native-runtime"></a><span data-ttu-id="15da0-193">Yerel çalışma zamanı için semboller alma</span><span class="sxs-lookup"><span data-stu-id="15da0-193">Getting Symbols for the Native Runtime</span></span>

<span data-ttu-id="15da0-194">Çoğu zaman kendi kodunuzla ilgileniyorsunuz. Bu, `perfcollect` Varsayılan olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="15da0-194">Most of the time you are interested in your own code, which `perfcollect` resolves by default.</span></span> <span data-ttu-id="15da0-195">Bazı durumlarda, .NET DLL 'lerinde (son bölümün yaklaşık olduğu) neler olduğunu görmek çok yararlı olur, ancak bazen yerel çalışma zamanı dll 'lerinde (genellikle libcoreclr.so) neler olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="15da0-195">Sometimes it is very useful to see what is going on inside the .NET DLLs (which is what the last section was about), but sometimes what is going on in the native runtime dlls (typically libcoreclr.so), is interesting.</span></span>  <span data-ttu-id="15da0-196">`perfcollect` , yalnızca bu yerel dll sembolleri varsa (ve bunların kendisi için oldukları kitaplığın yanında ise) sembolleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="15da0-196">`perfcollect` will resolve the symbols for these when it converts its data, but only if the symbols for these native DLLs are present (and are beside the library they are for).</span></span>

<span data-ttu-id="15da0-197">Bunu belirleyen [DotNet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) adlı bir genel komut vardır.</span><span class="sxs-lookup"><span data-stu-id="15da0-197">There is a global command called [dotnet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) which does this.</span></span> <span data-ttu-id="15da0-198">Yerel çalışma zamanı sembolleri almak için DotNet-symbol kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="15da0-198">To use dotnet-symbol to get native runtime symbols:</span></span>

1. <span data-ttu-id="15da0-199">`dotnet-symbol` yükleme:</span><span class="sxs-lookup"><span data-stu-id="15da0-199">Install `dotnet-symbol`:</span></span>

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. <span data-ttu-id="15da0-200">Sembolleri indirin.</span><span class="sxs-lookup"><span data-stu-id="15da0-200">Download the symbols.</span></span> <span data-ttu-id="15da0-201">.NET Core çalışma zamanının yüklü sürümü 2.1.0 ise bunu yapmak için komut</span><span class="sxs-lookup"><span data-stu-id="15da0-201">If your installed version of the .NET Core runtime is 2.1.0 the command to do this is</span></span>

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. <span data-ttu-id="15da0-202">Sembolleri doğru yere kopyalayın</span><span class="sxs-lookup"><span data-stu-id="15da0-202">Copy the symbols to the correct place</span></span>

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    <span data-ttu-id="15da0-203">Uygun dizine yazma erişiminizin olmadığı için bu işlem yapılacağından, `perf buildid-cache` sembolleri eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15da0-203">If this cannot be done because you do not have write access to the appropriate directory, you can use `perf buildid-cache` to add the symbols.</span></span>

<span data-ttu-id="15da0-204">Bundan sonra, çalıştırdığınızda yerel dll 'ler için simgesel adlar almalısınız `perfcollect` .</span><span class="sxs-lookup"><span data-stu-id="15da0-204">After this, you should get symbolic names for the native dlls when you run `perfcollect`.</span></span>

## <a name="collecting-in-a-docker-container"></a><span data-ttu-id="15da0-205">Bir Docker kapsayıcısında toplama</span><span class="sxs-lookup"><span data-stu-id="15da0-205">Collecting in a Docker Container</span></span>

<span data-ttu-id="15da0-206">Kapsayıcı ortamlarında kullanma hakkında daha fazla bilgi için `perfcollect` bkz. [kapsayıcılar Içinde tanılama toplama](./diagnostics-in-containers.md) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="15da0-206">For more information on how to use `perfcollect` in container environments, refer to [Collect diagnostics in containers](./diagnostics-in-containers.md) documentation.</span></span>
