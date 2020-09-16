---
title: Hata ayıklama kilitlenmesi-.NET Core
description: .NET Core 'da kilitleme sorununu ayıklamada size kılavuzluk eden bir öğretici.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: d9a9328b376de5886d22ca7315f6d7d9d73fd2c2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538702"
---
# <a name="debug-a-deadlock-in-net-core"></a><span data-ttu-id="2d8ca-103">.NET Core 'da kilitlenmeyle hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2d8ca-103">Debug a deadlock in .NET Core</span></span>

<span data-ttu-id="2d8ca-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="2d8ca-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="2d8ca-105">Bu öğreticide, bir kilitlenme senaryosunda hata ayıklamayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-105">In this tutorial, you'll learn how to debug a deadlock scenario.</span></span> <span data-ttu-id="2d8ca-106">[Web uygulaması](/samples/dotnet/samples/diagnostic-scenarios) kaynak kodu deposu ASP.NET Core sunulan örneği kullanarak, kasıtlı olarak bir kilitlenmeye neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="2d8ca-107">Uç nokta, askıda kalma ve iş parçacığı birikmesi ile karşılaşacaktır.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="2d8ca-108">Temel dökümler, temel döküm Analizi ve işlem izleme gibi sorunları çözümlemek için çeşitli araçları nasıl kullanabileceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-108">You'll learn how you can use various tools to analyze the problem, such as core dumps, core dump analysis, and process tracing.</span></span>

<span data-ttu-id="2d8ca-109">Bu öğreticide şunları yapacaksınız:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="2d8ca-110">Uygulama askıda kalmasına araştırma</span><span class="sxs-lookup"><span data-stu-id="2d8ca-110">Investigate an app hang</span></span>
> - <span data-ttu-id="2d8ca-111">Temel döküm dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d8ca-111">Generate a core dump file</span></span>
> - <span data-ttu-id="2d8ca-112">Döküm dosyasındaki işlem iş parçacıklarını çözümleyin</span><span class="sxs-lookup"><span data-stu-id="2d8ca-112">Analyze process threads in the dump file</span></span>
> - <span data-ttu-id="2d8ca-113">Çağrı yığınlarını ve eşitleme bloklarını çözümle</span><span class="sxs-lookup"><span data-stu-id="2d8ca-113">Analyze callstacks and sync blocks</span></span>
> - <span data-ttu-id="2d8ca-114">Bir kilitlenmesi tanılayın ve çözün</span><span class="sxs-lookup"><span data-stu-id="2d8ca-114">Diagnose and solve a deadlock</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2d8ca-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2d8ca-115">Prerequisites</span></span>

<span data-ttu-id="2d8ca-116">Öğretici şunları kullanır:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-116">The tutorial uses:</span></span>

- <span data-ttu-id="2d8ca-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="2d8ca-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version</span></span>
- <span data-ttu-id="2d8ca-118">[Örnek hata ayıklama hedefi-](/samples/dotnet/samples/diagnostic-scenarios) senaryoyu tetiklemek için Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="2d8ca-118">[Sample debug target - web app](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario</span></span>
- <span data-ttu-id="2d8ca-119">[DotNet-](dotnet-trace.md) liste işlemlerine izleme</span><span class="sxs-lookup"><span data-stu-id="2d8ca-119">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="2d8ca-120">[DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm</span><span class="sxs-lookup"><span data-stu-id="2d8ca-120">[dotnet-dump](dotnet-dump.md) to collect, and analyze a dump file</span></span>

## <a name="core-dump-generation"></a><span data-ttu-id="2d8ca-121">Temel döküm oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d8ca-121">Core dump generation</span></span>

<span data-ttu-id="2d8ca-122">Uygulamanın yanıt verme hızını araştırmak için, temel döküm veya bellek dökümü, iş parçacıklarının durumunu ve çekişme sorunları olabilecek olası kilitleri incelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-122">To investigate application unresponsiveness, a core dump or memory dump allows you to inspect the state of its threads and any possible locks that may have contention issues.</span></span> <span data-ttu-id="2d8ca-123">Örnek kök dizininden aşağıdaki komutu kullanarak [örnek hata ayıklama](/samples/dotnet/samples/diagnostic-scenarios) uygulamasını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-123">Run the [sample debug](/samples/dotnet/samples/diagnostic-scenarios) application using the following command from the sample root directory:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="2d8ca-124">İşlem KIMLIĞINI bulmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="2d8ca-125">Komut çıktıınızdan işlem KIMLIĞI ' ni bir yere göz atın.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="2d8ca-126">İşlem KIMLIĞINIZ idi `4807` , ancak sizinki farklı olacak.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-126">Our process ID was `4807`, but yours will be different.</span></span> <span data-ttu-id="2d8ca-127">Örnek sitede bir API uç noktası olan aşağıdaki URL 'ye gidin:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-127">Navigate to the following URL, which is an API endpoint on the sample site:</span></span>

`https://localhost:5001/api/diagscenario/deadlock`

<span data-ttu-id="2d8ca-128">Siteye yönelik API isteği askıda kalır ve yanıt vermez.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-128">The API request to the site will hang and not respond.</span></span> <span data-ttu-id="2d8ca-129">İsteğin yaklaşık 10-15 saniye çalışmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-129">Let the request run for about 10-15 seconds.</span></span> <span data-ttu-id="2d8ca-130">Ardından aşağıdaki komutu kullanarak çekirdek dökümünü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-130">Then create the core dump using the following command:</span></span>

### <a name="linux"></a>[<span data-ttu-id="2d8ca-131">Linux</span><span class="sxs-lookup"><span data-stu-id="2d8ca-131">Linux</span></span>](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[<span data-ttu-id="2d8ca-132">Windows</span><span class="sxs-lookup"><span data-stu-id="2d8ca-132">Windows</span></span>](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a><span data-ttu-id="2d8ca-133">Çekirdek dökümünü analiz etme</span><span class="sxs-lookup"><span data-stu-id="2d8ca-133">Analyze the core dump</span></span>

<span data-ttu-id="2d8ca-134">Temel döküm analizini başlatmak için aşağıdaki komutu kullanarak çekirdek dökümünü açın `dotnet-dump analyze` .</span><span class="sxs-lookup"><span data-stu-id="2d8ca-134">To start the core dump analysis, open the core dump using the following `dotnet-dump analyze` command.</span></span> <span data-ttu-id="2d8ca-135">Bağımsız değişkeni, daha önce toplanan temel döküm dosyasının yoludur.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-135">The argument is the path to the core dump file that was collected earlier.</span></span>

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

<span data-ttu-id="2d8ca-136">Olası bir askıda kalma olduğunu bakıyorsunuzdur, işlemdeki iş parçacığı etkinliği için genel bir fikir istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-136">Since you're looking at a potential hang, you want an overall feel for the thread activity in the process.</span></span> <span data-ttu-id="2d8ca-137">`threads`Komutunu aşağıda gösterildiği gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-137">You can use the `threads` command as shown below:</span></span>

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

<span data-ttu-id="2d8ca-138">Çıktıda, ilişkili hata ayıklayıcı iş parçacığı KIMLIĞI ve işletim sistemi iş parçacığı KIMLIĞI ile işlemde çalışmakta olan tüm iş parçacıkları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-138">The output shows all the threads currently running in the process with their associated debugger thread ID and operating system thread ID.</span></span> <span data-ttu-id="2d8ca-139">Çıkışa göre 300 ' den fazla iş parçacığı vardır.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-139">Based on the output, there are over 300 threads.</span></span>

<span data-ttu-id="2d8ca-140">Bir sonraki adım, her iş parçacığının çağrı yığınını alarak iş parçacıklarının Şu anda neler yaptığını daha iyi anlayabilmektir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-140">The next step is to get a better understanding of what the threads are currently doing by getting each thread's callstack.</span></span> <span data-ttu-id="2d8ca-141">`clrstack`Komut, callyığınları çıkarmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-141">The `clrstack` command can be used to output callstacks.</span></span> <span data-ttu-id="2d8ca-142">Tek bir çağrı yığını veya tüm çağrı yığınlarının çıktısını alabilir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-142">It can either output a single callstack or all the callstacks.</span></span> <span data-ttu-id="2d8ca-143">İşlemdeki tüm iş parçacıkları için tüm çağrı yığınlarının çıkışını almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-143">Use the following command to output all the callstacks for all the threads in the process:</span></span>

```console
clrstack -all
```

<span data-ttu-id="2d8ca-144">Çıktının temsili bir kısmı şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-144">A representative portion of the output looks like:</span></span>

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

<span data-ttu-id="2d8ca-145">Tüm 300 + iş parçacıkları için çağrı yığınlarının gözlemlenme, iş parçacıklarının büyük çoğunluğunun ortak bir çağrı yığınını paylaştığı bir model gösterir:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-145">Observing the callstacks for all 300+ threads shows a pattern where a majority of the threads share a common callstack:</span></span>

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

<span data-ttu-id="2d8ca-146">Çağrı yığını, isteğin, bir çağrısı yaptığı kilitlenme yönteemizdeki geldiğini gösteriyor gibi görünüyor `Monitor.ReliableEnter` .</span><span class="sxs-lookup"><span data-stu-id="2d8ca-146">The callstack seems to show that the request arrived in our deadlock method that in turn makes a call to `Monitor.ReliableEnter`.</span></span> <span data-ttu-id="2d8ca-147">Bu yöntem, iş parçacıklarının bir izleyici kilidi girmeye çalışıyor olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-147">This method indicates that the threads are trying to enter a monitor lock.</span></span> <span data-ttu-id="2d8ca-148">Kilit kullanılabilirliğini bekliyor.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-148">They're waiting on the availability of the lock.</span></span> <span data-ttu-id="2d8ca-149">Muhtemelen farklı bir iş parçacığı tarafından kilitlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-149">It's likely locked by a different thread.</span></span>

<span data-ttu-id="2d8ca-150">Sonraki adımda, hangi iş parçacığının gerçekten izleyici kilidini tuttuğıdır.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-150">The next step then is to find out which thread is actually holding the monitor lock.</span></span> <span data-ttu-id="2d8ca-151">İzleyiciler genellikle eşitleme bloğu tablosunda kilit bilgilerini depodıklarından, `syncblk` daha fazla bilgi almak için komutunu kullanabiliriz:</span><span class="sxs-lookup"><span data-stu-id="2d8ca-151">Since monitors typically store lock information in the sync block table, we can use the `syncblk` command to get more information:</span></span>

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

<span data-ttu-id="2d8ca-152">İlgi **çekici ve** **sahip iş parçacığı bilgilerinin**iki ilginç sütunu.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-152">The two interesting columns are **MonitorHeld** and **Owning Thread Info**.</span></span> <span data-ttu-id="2d8ca-153">**Monitortutuldu** sütunu, bir iş parçacığı ve bekleme iş parçacığı sayısı tarafından bir izleyici kilidinin elde edilip edilmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-153">The **MonitorHeld** column shows whether a monitor lock is acquired by a thread and the number of waiting threads.</span></span> <span data-ttu-id="2d8ca-154">**Sahip Iş parçacığı bilgileri** sütununda, şu anda izleyici kilidine sahip olan iş parçacığı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-154">The **Owning Thread Info** column shows which thread currently owns the monitor lock.</span></span> <span data-ttu-id="2d8ca-155">İş parçacığı bilgisinde üç farklı alt sütun vardır.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-155">The thread info has three different subcolumns.</span></span> <span data-ttu-id="2d8ca-156">İkinci alt sütun, işletim sistemi iş parçacığı KIMLIĞINI gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-156">The second subcolumn shows operating system thread ID.</span></span>

<span data-ttu-id="2d8ca-157">Bu noktada, iki farklı iş parçacığını (0x5634 ve 0x51d4) bir izleyici kilidi tutabiliyoruz.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-157">At this point, we know two different threads (0x5634 and 0x51d4) hold a monitor lock.</span></span> <span data-ttu-id="2d8ca-158">Sonraki adım, bu iş parçacıklarının yaptığına göz atabilmenizdir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-158">The next step is to take a look at what those threads are doing.</span></span> <span data-ttu-id="2d8ca-159">Kilidi sonsuza kadar sürekli olarak takılıp takıldıklarından emin olmamız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-159">We need to check if they're stuck indefinitely holding the lock.</span></span> <span data-ttu-id="2d8ca-160">`setthread` `clrstack` Her iş parçacığının her birine geçiş yapmak ve çağrı yığınlarını göstermek için ve komutlarını kullanalım.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-160">Let's use the `setthread` and `clrstack` commands to switch to each of the threads and display the callstacks.</span></span>

<span data-ttu-id="2d8ca-161">İlk iş parçacığına bakmak için `setthread` komutunu çalıştırın ve 0x5634 iş parçacığının dizinini bulun (dizinimiz 28 idi).</span><span class="sxs-lookup"><span data-stu-id="2d8ca-161">To look at the first thread, run the `setthread` command, and find the index of the 0x5634 thread (our index was 28).</span></span> <span data-ttu-id="2d8ca-162">Kilitlenme işlevi bir kilit almayı bekliyor, ancak kilidin zaten var.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-162">The deadlock function is waiting to acquire a lock, but it already owns the lock.</span></span> <span data-ttu-id="2d8ca-163">Kilitlenmeyle zaten tuttuğu kilidi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-163">It's in deadlock waiting for the lock it already holds.</span></span>

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

<span data-ttu-id="2d8ca-164">İkinci iş parçacığı benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-164">The second thread is similar.</span></span> <span data-ttu-id="2d8ca-165">Ayrıca, sahip olduğu bir kilidi almaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-165">It's also trying to acquire a lock that it already owns.</span></span> <span data-ttu-id="2d8ca-166">Tüm bekleyen 300 + iş parçacıkları büyük olasılıkla kilitlenmeye neden olan kilitleri da bekler.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-166">The remaining 300+ threads that are all waiting are most likely also waiting on one of the locks that caused the deadlock.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d8ca-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d8ca-167">See also</span></span>

- <span data-ttu-id="2d8ca-168">[DotNet-](dotnet-trace.md) liste işlemlerine izleme</span><span class="sxs-lookup"><span data-stu-id="2d8ca-168">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="2d8ca-169">[DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar</span><span class="sxs-lookup"><span data-stu-id="2d8ca-169">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="2d8ca-170">[DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm</span><span class="sxs-lookup"><span data-stu-id="2d8ca-170">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="2d8ca-171">DotNet/Diagnostics</span><span class="sxs-lookup"><span data-stu-id="2d8ca-171">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="2d8ca-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2d8ca-172">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2d8ca-173">.NET Core 'da kullanılabilen tanılama araçları</span><span class="sxs-lookup"><span data-stu-id="2d8ca-173">What diagnostic tools are available in .NET Core</span></span>](index.md)
