---
title: Bellek sızıntısı öğreticisinde hata ayıklama
description: .NET Core 'da Bellek sızıntısını nasıl ayıklayacağınızı öğrenin.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: 6764663eedc28cd75f9f68927a12ae5b2255d11b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431457"
---
# <a name="debug-a-memory-leak-in-net-core"></a><span data-ttu-id="94315-103">.NET Core 'da bellek sızıntısı hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="94315-103">Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="94315-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="94315-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="94315-105">Uygulamanız artık istenen görevi gerçekleştirmek için ihtiyaç duymadığı nesnelere başvurduğunda, bir bellek sızıntısı meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="94315-105">A memory leak may happen when your app references objects that it no longer needs to perform the desired task.</span></span> <span data-ttu-id="94315-106">Söyleyen nesnelere başvurmak, çöp toplayıcısının kullanılan belleği geri kazanmasına neden olur, genellikle performans düşüşüne ve büyük olasılıkla bir atma işlemini ortaya çıkarır <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="94315-106">Referencing said objects makes the garbage collector to be unable to reclaim the memory used, often resulting in performance degradation and potentially end up throwing a <xref:System.OutOfMemoryException>.</span></span>

<span data-ttu-id="94315-107">Bu öğreticide, .net tanılama CLı araçları kullanılarak .NET Core uygulamasında bir Bellek sızıntısının çözümlenmesi için Araçlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94315-107">This tutorial demonstrates the tools to analyze a memory leak in a .NET Core app using the .NET diagnostics CLI tools.</span></span> <span data-ttu-id="94315-108">Windows kullanıyorsanız, bellek sızıntısı hatalarını ayıklamak için [Visual Studio 'Nun bellek tanılama araçlarını kullanabilirsiniz](/visualstudio/profiling/memory-usage) .</span><span class="sxs-lookup"><span data-stu-id="94315-108">If you are on Windows, you may be able to [use Visual Studio's Memory Diagnostic tools](/visualstudio/profiling/memory-usage) to debug the memory leak.</span></span>

<span data-ttu-id="94315-109">Bu öğreticide, kasıtlı olarak bellek sızıntısı için tasarlanan örnek bir uygulama kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94315-109">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="94315-110">Örnek, bir alıştırma olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="94315-110">The sample is provided as an exercise.</span></span> <span data-ttu-id="94315-111">Yanlışlıkla bellek sızdıran bir uygulamayı analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-111">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="94315-112">Bu öğreticide şunları yapacaksınız:</span><span class="sxs-lookup"><span data-stu-id="94315-112">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="94315-113">[DotNet-Counters](dotnet-counters.md)ile yönetilen bellek kullanımını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="94315-113">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="94315-114">Döküm dosyası oluştur.</span><span class="sxs-lookup"><span data-stu-id="94315-114">Generate a dump file.</span></span>
> - <span data-ttu-id="94315-115">Döküm dosyasını kullanarak bellek kullanımını çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="94315-115">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94315-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="94315-116">Prerequisites</span></span>

<span data-ttu-id="94315-117">Öğretici şunları kullanır:</span><span class="sxs-lookup"><span data-stu-id="94315-117">The tutorial uses:</span></span>

- <span data-ttu-id="94315-118">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="94315-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="94315-119">[DotNet-](dotnet-trace.md) liste süreçlerini izleme.</span><span class="sxs-lookup"><span data-stu-id="94315-119">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="94315-120">[DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar.</span><span class="sxs-lookup"><span data-stu-id="94315-120">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="94315-121">[DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm.</span><span class="sxs-lookup"><span data-stu-id="94315-121">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="94315-122">Tanılama için bir [örnek hata ayıklama hedef](/samples/dotnet/samples/diagnostic-scenarios/) uygulaması.</span><span class="sxs-lookup"><span data-stu-id="94315-122">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="94315-123">Öğretici, örnek ve araçların yüklendiğini ve kullanıma hazırlandığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="94315-123">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="94315-124">Yönetilen bellek kullanımını incele</span><span class="sxs-lookup"><span data-stu-id="94315-124">Examine managed memory usage</span></span>

<span data-ttu-id="94315-125">Bu senaryonun köke neden olması için tanılama verileri toplamaya başlamadan önce, aslında bir bellek sızıntısı (bellek büyümesi) gördüğünüzü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="94315-125">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="94315-126">Doğrulamak için [DotNet-Counters](dotnet-counters.md) aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-126">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="94315-127">Bir konsol penceresi açın ve [örnek hata ayıklama hedefini](/samples/dotnet/samples/diagnostic-scenarios/)indirdiğiniz ve sıkıştırmadan indirdiğiniz dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="94315-127">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="94315-128">Hedefi Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="94315-128">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="94315-129">Ayrı bir konsoldan, [DotNet-Trace](dotnet-trace.md) aracını kullanarak işlem kimliğini bulun:</span><span class="sxs-lookup"><span data-stu-id="94315-129">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="94315-130">Çıktının şuna benzer olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="94315-130">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="94315-131">Şimdi, [DotNet-Counters](dotnet-counters.md) aracıyla yönetilen bellek kullanımını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="94315-131">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="94315-132">`--refresh-interval`Yenilemeler arasındaki saniye sayısını belirtir:</span><span class="sxs-lookup"><span data-stu-id="94315-132">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="94315-133">Canlı çıktının şuna benzer olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="94315-133">The live output should be similar to:</span></span>

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

<span data-ttu-id="94315-134">Bu satıra odaklanma:</span><span class="sxs-lookup"><span data-stu-id="94315-134">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="94315-135">Yönetilen yığın belleğinin başlangıçtan sonra 4 MB olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-135">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="94315-136">Şimdi URL 'ye basın `https://localhost:5001/api/diagscenario/memleak/20000` .</span><span class="sxs-lookup"><span data-stu-id="94315-136">Now, hit the URL `https://localhost:5001/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="94315-137">Bellek kullanımının 30 MB 'a kadar büyüdiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="94315-137">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="94315-138">Bellek kullanımını izleyerek belleğin büyüdüğünü veya sızmasını güvenli bir şekilde söyleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-138">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="94315-139">Sonraki adım bellek analizine yönelik doğru verileri toplamaktır.</span><span class="sxs-lookup"><span data-stu-id="94315-139">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="94315-140">Bellek dökümü oluştur</span><span class="sxs-lookup"><span data-stu-id="94315-140">Generate memory dump</span></span>

<span data-ttu-id="94315-141">Olası bellek sızıntılarını analiz edilirken uygulamanın bellek yığınına erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="94315-141">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="94315-142">Daha sonra bellek içeriğini çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-142">Then you can analyze the memory contents.</span></span> <span data-ttu-id="94315-143">Nesneler arasındaki ilişkilere bakarak belleğin neden serbest bırakılmadığına ilişkin bir kayıt oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="94315-143">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="94315-144">Ortak bir tanılama veri kaynağı, Windows 'da bellek dökümleridir veya Linux üzerinde eşdeğer çekirdek dökümleridir.</span><span class="sxs-lookup"><span data-stu-id="94315-144">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="94315-145">.NET Core uygulamasının bir dökümünü oluşturmak için [DotNet-dump)](dotnet-dump.md) aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-145">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="94315-146">Önceden başlatılan [örnek hata ayıklama hedefini](/samples/dotnet/samples/diagnostic-scenarios/) kullanarak bir Linux core dökümü oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="94315-146">Using the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="94315-147">Sonuç, aynı klasörde bulunan temel bir dökümdir.</span><span class="sxs-lookup"><span data-stu-id="94315-147">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="94315-148">Başarısız olan işlemi yeniden Başlat</span><span class="sxs-lookup"><span data-stu-id="94315-148">Restart the failed process</span></span>

<span data-ttu-id="94315-149">Döküm toplandıktan sonra, başarısız olan işlemi tanılamak için yeterli bilgiye sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="94315-149">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="94315-150">Başarısız işlem bir üretim sunucusunda çalışıyorsa, artık işlemi yeniden başlatarak kısa süreli düzeltmeye yönelik ideal bir süredir.</span><span class="sxs-lookup"><span data-stu-id="94315-150">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="94315-151">Bu öğreticide, şimdi [örnek hata ayıklama hedefini](/samples/dotnet/samples/diagnostic-scenarios/) tamamladınız ve kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-151">In this tutorial, you're now done with the [Sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="94315-152">Sunucuyu başlatan terminale gidin ve <kbd>CTRL + C</kbd>tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="94315-152">Navigate to the terminal that started the server, and press <kbd>Ctrl+C</kbd>.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="94315-153">Çekirdek dökümünü analiz etme</span><span class="sxs-lookup"><span data-stu-id="94315-153">Analyze the core dump</span></span>

<span data-ttu-id="94315-154">Oluşturulmuş bir temel döküm olduğuna göre, dökümü çözümlemek için [DotNet-dump](dotnet-dump.md) aracını kullanın:</span><span class="sxs-lookup"><span data-stu-id="94315-154">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="94315-155">`core_20190430_185145`, Analiz etmek istediğiniz temel döküm adıdır.</span><span class="sxs-lookup"><span data-stu-id="94315-155">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="94315-156">*Libdl.so* bulunamadığını belirten bir hata görürseniz, *libc6-dev* paketini yüklemek zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-156">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="94315-157">Daha fazla bilgi için bkz. [Linux üzerinde .NET Core önkoşulları](../install/linux.md).</span><span class="sxs-lookup"><span data-stu-id="94315-157">For more information, see [Prerequisites for .NET Core on Linux](../install/linux.md).</span></span>

<span data-ttu-id="94315-158">SOS komutları girebileceğiniz bir istem sunulur.</span><span class="sxs-lookup"><span data-stu-id="94315-158">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="94315-159">Genellikle, bakmak istediğiniz ilk şey, yönetilen yığının genel durumudur:</span><span class="sxs-lookup"><span data-stu-id="94315-159">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

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

<span data-ttu-id="94315-160">Burada nesnelerin ya da nesnelerin olduğunu görebilirsiniz `String` `Customer` .</span><span class="sxs-lookup"><span data-stu-id="94315-160">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="94315-161">`dumpheap`Tüm örneklerin bir listesini almak için komutunu Yöntem tablosu (MT) ile birlikte kullanabilirsiniz `String` :</span><span class="sxs-lookup"><span data-stu-id="94315-161">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

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

<span data-ttu-id="94315-162">Artık `gcroot` `System.String` nesnenin nasıl ve neden kök olarak oluşturulduğunu görmek için bir örnek üzerinde komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-162">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="94315-163">Bu komutun 30 MB 'lik bir yığın ile birkaç dakika sürdüğü için sabırlı olun:</span><span class="sxs-lookup"><span data-stu-id="94315-163">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

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

<span data-ttu-id="94315-164">`String` `Customer` Nesnesinin doğrudan nesne tarafından ve bir nesne tarafından dolaylı olarak tutulduğundan emin olabilirsiniz `CustomerCache` .</span><span class="sxs-lookup"><span data-stu-id="94315-164">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="94315-165">Birçok `String` nesnenin benzer bir düzende izlediğinden emin olmak için nesnelerin dökümünü almaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-165">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="94315-166">Bu noktada, araştırma kodunuzda kök nedenini belirlemek için yeterli bilgi sağladı.</span><span class="sxs-lookup"><span data-stu-id="94315-166">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="94315-167">Bu genel yordam, büyük bellek sızıntılarının kaynağını tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="94315-167">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="94315-168">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="94315-168">Clean up resources</span></span>

<span data-ttu-id="94315-169">Bu öğreticide, örnek bir Web sunucusu başladıysanız.</span><span class="sxs-lookup"><span data-stu-id="94315-169">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="94315-170">Bu sunucu, [başarısız Işlem yeniden başlatma](#restart-the-failed-process) bölümünde açıklandığı gibi kapatılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94315-170">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="94315-171">Oluşturulan döküm dosyasını da silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94315-171">You can also delete the dump file that was created.</span></span>

## <a name="see-also"></a><span data-ttu-id="94315-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94315-172">See also</span></span>

- <span data-ttu-id="94315-173">[DotNet-](dotnet-trace.md) liste işlemlerine izleme</span><span class="sxs-lookup"><span data-stu-id="94315-173">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="94315-174">[DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar</span><span class="sxs-lookup"><span data-stu-id="94315-174">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="94315-175">[DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm</span><span class="sxs-lookup"><span data-stu-id="94315-175">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="94315-176">DotNet/Diagnostics</span><span class="sxs-lookup"><span data-stu-id="94315-176">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)
- [<span data-ttu-id="94315-177">Bellek sızıntılarını ayıklamak için Visual Studio 'Yu kullanma</span><span class="sxs-lookup"><span data-stu-id="94315-177">Use Visual Studio to debug memory leaks</span></span>](/visualstudio/profiling/memory-usage)

## <a name="next-steps"></a><span data-ttu-id="94315-178">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="94315-178">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="94315-179">.NET Core 'da yüksek CPU 'YU hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="94315-179">Debug high CPU in .NET Core</span></span>](debug-highcpu.md)
