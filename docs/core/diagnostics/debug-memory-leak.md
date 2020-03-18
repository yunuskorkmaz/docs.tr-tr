---
title: Hata ayıklama bir bellek sızıntısı öğretici
description: .NET Core'da bellek sızıntısını nasıl hata ayıklayın öğrenin.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737733"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="1bfd3-103">Öğretici: .NET Core'da bellek sızıntısını hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1bfd3-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="1bfd3-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="1bfd3-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="1bfd3-105">Bu öğretici, bir .NET Core bellek sızıntısıanaliz etmek için araçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="1bfd3-106">Bu öğretici, kasıtlı olarak bellek sızdırmak için tasarlanmış bir örnek uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="1bfd3-107">Örnek bir egzersiz olarak sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="1bfd3-108">İstemeden bellek sızdıran bir uygulamayı da analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="1bfd3-109">Bu öğreticide şunları yapacaksınız:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1bfd3-110">Yönetilen bellek kullanımını [dotnet sayaçları](dotnet-counters.md)ile inceleyin.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="1bfd3-111">Bir döküm dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-111">Generate a dump file.</span></span>
> - <span data-ttu-id="1bfd3-112">Döküm dosyasını kullanarak bellek kullanımını çözümle.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bfd3-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1bfd3-113">Prerequisites</span></span>

<span data-ttu-id="1bfd3-114">Öğretici kullanır:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-114">The tutorial uses:</span></span>

- <span data-ttu-id="1bfd3-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya daha sonraki bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="1bfd3-116">[nokta-izleme](dotnet-trace.md) liste işlemleri için.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="1bfd3-117">yönetilen bellek kullanımını denetlemek için [dotnet sayaçları.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="1bfd3-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="1bfd3-118">bir döküm dosyasını toplamak ve çözümlemek için [dotnet-dökümü.](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="1bfd3-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="1bfd3-119">Tanılamak için [örnek hata ayıklama hedef](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="1bfd3-120">Öğretici, örnek ve araçların yüklü ve kullanıma hazır olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="1bfd3-121">Yönetilen bellek kullanımını inceleme</span><span class="sxs-lookup"><span data-stu-id="1bfd3-121">Examine managed memory usage</span></span>

<span data-ttu-id="1bfd3-122">Bu senaryoya neden olmamıza yardımcı olacak tanılama verilerini toplamaya başlamadan önce, gerçekten bir bellek sızıntısı (bellek büyümesi) gördüğünüzden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="1bfd3-123">Bunu doğrulamak için [dotnet sayaçları](dotnet-counters.md) aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="1bfd3-124">Bir konsol penceresi açın ve [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)indirip fermuarını açtığınız dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="1bfd3-125">Hedefi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="1bfd3-126">Ayrı bir konsoldan, [dotnet izleme](dotnet-trace.md) aracını kullanarak işlem kimliğini bulun:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="1bfd3-127">Çıktı aşağıdakilere benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="1bfd3-128">Şimdi, [dotnet sayaçları](dotnet-counters.md) aracıyla yönetilen bellek kullanımını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="1bfd3-129">Yenilemeler `--refresh-interval` arasındaki saniye sayısını belirtir:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="1bfd3-130">Canlı çıktı aşağıdakilere benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="1bfd3-131">Bu satıra odaklanarak:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="1bfd3-132">Yönetilen yığın belleği başlatmadan hemen sonra 4 MB olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="1bfd3-133">Şimdi, URL'ye `http://localhost:5000/api/diagscenario/memleak/20000`vur.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="1bfd3-134">Bellek kullanımının 30 MB'a kadar büyüdüğünü gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="1bfd3-135">Bellek kullanımını izleyerek, belleğin büyüdüğünü veya sızdırdığını rahatlıkla söyleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="1bfd3-136">Bir sonraki adım bellek analizi için doğru verileri toplamaktır.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="1bfd3-137">Bellek dökümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bfd3-137">Generate memory dump</span></span>

<span data-ttu-id="1bfd3-138">Olası bellek sızıntılarını analiz ederken, uygulamanın bellek yığınına erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="1bfd3-139">Sonra bellek içeriğini analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="1bfd3-140">Nesneler arasındaki ilişkilere baktığınızda, belleğin neden serbest bırakılmadığını niçin oluşturduğuna dair teoriler oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="1bfd3-141">Ortak bir tanılama veri kaynağı, Windows'daki bir bellek dökümü veya Linux'taki eşdeğer çekirdek dökümüdür.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="1bfd3-142">.NET Core uygulamasının dökümdöküm'ü oluşturmak için [dotnet dökümü aracını](dotnet-dump.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="1bfd3-143">Daha önce başlatılan [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) kullanarak, linux çekirdek dökümü oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="1bfd3-144">Sonuç, aynı klasörde bulunan bir çekirdek dökümüdür.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="1bfd3-145">Başarısız işlemi yeniden başlatma</span><span class="sxs-lookup"><span data-stu-id="1bfd3-145">Restart the failed process</span></span>

<span data-ttu-id="1bfd3-146">Döküm toplandıktan sonra, başarısız işlemi tanılamak için yeterli bilgiye sahip olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="1bfd3-147">Başarısız olan işlem bir üretim sunucusunda çalışıyorsa, şimdi işlemi yeniden başlatarak kısa vadeli düzeltme için ideal bir zaman.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="1bfd3-148">Bu öğreticide, artık [Örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) bitirdiniz ve kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="1bfd3-149">Sunucuyu başlatan terminale gidin `Control-C`ve 'ye basın.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="1bfd3-150">Çekirdek dökümünün analizi</span><span class="sxs-lookup"><span data-stu-id="1bfd3-150">Analyze the core dump</span></span>

<span data-ttu-id="1bfd3-151">Şimdi oluşturulan bir çekirdek dökümü var, dökümü analiz etmek için [dotnet-dump)](dotnet-dump.md) aracını kullanın:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-151">Now that you have a core dump generated, use the [dotnet-dump)](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="1bfd3-152">Analiz `core_20190430_185145` etmek istediğiniz çekirdek dökümünün adı nerede?</span><span class="sxs-lookup"><span data-stu-id="1bfd3-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="1bfd3-153">*libdl.so* bulunamaz şikayet eden bir hata görürseniz, *libc6-dev* paketini yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="1bfd3-154">Daha fazla bilgi [için Linux'ta .NET Core için Ön koşullara](../linux-prerequisites.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-154">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

<span data-ttu-id="1bfd3-155">SOS komutlarını girebileceğiniz bir istem sunulur.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="1bfd3-156">Genellikle, bakmak istediğiniz ilk şey yönetilen yığının genel durumudur:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="1bfd3-157">Burada çoğu nesnenin veya `String` `Customer` nesnenin olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="1bfd3-158">Tüm `String` örneklerin `dumpheap` listesini almak için yöntem tablosu (MT) ile komutu yeniden kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="1bfd3-159">Nesnenin `gcroot` nasıl ve neden `System.String` köksünün dayandığını görmek için artık bir örnekteki komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="1bfd3-160">Bu komut 30 MB'lık bir yığınla birkaç dakika aldığından sabırlı olun:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="1bfd3-161">Doğrudan nesne tarafından `String` tutulduğunu `Customer` ve dolaylı olarak bir `CustomerCache` nesne tarafından tutulduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="1bfd3-162">Çoğu `String` nesnenin benzer bir deseni takip ettiğini görmek için nesneleri boşaltmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="1bfd3-163">Bu noktada, araştırma kodunuzda kök nedeni belirlemek için yeterli bilgi sağladı.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="1bfd3-164">Bu genel yordam, büyük bellek sızıntılarının kaynağını belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="1bfd3-165">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="1bfd3-165">Clean up resources</span></span>

<span data-ttu-id="1bfd3-166">Bu öğreticide, örnek bir web sunucusu başlattınız.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="1bfd3-167">Bu sunucu, başarısız işlemi yeniden [başlat](#restart-the-failed-process) bölümünde açıklandığı gibi kapatılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="1bfd3-168">Oluşturulan döküm dosyasını da silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bfd3-169">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1bfd3-169">Next steps</span></span>

<span data-ttu-id="1bfd3-170">Bu öğretici tamamladıktan sonra tebrikler.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="1bfd3-171">Hala daha fazla tanı lama eğitimi yayınlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="1bfd3-172">Taslak sürümleri [dotnet/teşhis](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) deposunda okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="1bfd3-173">Bu öğretici, anahtar .NET tanılama araçlarının temellerini kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="1bfd3-174">Gelişmiş kullanım için aşağıdaki başvuru belgelerine bakın:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="1bfd3-175">[nokta-izleme](dotnet-trace.md) liste işlemleri için.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="1bfd3-176">yönetilen bellek kullanımını denetlemek için [dotnet sayaçları.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="1bfd3-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="1bfd3-177">bir döküm dosyasını toplamak ve çözümlemek için [dotnet-dökümü.](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="1bfd3-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
