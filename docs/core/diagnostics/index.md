---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: c43e661ad8c9f665151e0240bf6b54e61b9acfef
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031923"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="9dd7a-103">.NET Core 'da hangi tanılama araçları kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="9dd7a-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="9dd7a-104">Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="9dd7a-105">Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="9dd7a-106">Yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="9dd7a-106">Managed debuggers</span></span>

<span data-ttu-id="9dd7a-107">[Yönetilen hata defterleri](managed-debuggers.md) , programla etkileşime girebilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="9dd7a-108">Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="9dd7a-109">Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="9dd7a-110">Günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="9dd7a-110">Logging and tracing</span></span>

<span data-ttu-id="9dd7a-111">[Günlüğe kaydetme ve izleme](logging-tracing.md) ilgili teknikler.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="9dd7a-112">Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="9dd7a-113">Dosyalar, bir programın yaptığı ayrıntıları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-113">The files record the details of what a program does.</span></span> <span data-ttu-id="9dd7a-114">Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="9dd7a-115">Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="9dd7a-116">Birim testi</span><span class="sxs-lookup"><span data-stu-id="9dd7a-116">Unit testing</span></span>

<span data-ttu-id="9dd7a-117">[Birim testi](../testing/index.md) , yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="9dd7a-118">Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="9dd7a-119">Dökümleri</span><span class="sxs-lookup"><span data-stu-id="9dd7a-119">Dumps</span></span>

<span data-ttu-id="9dd7a-120">[Döküm](./dumps.md) , oluşturma sırasında işlemin anlık görüntüsünü içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-120">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="9dd7a-121">Bunlar, hata ayıklama amacıyla uygulamanızın durumunu incelemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-121">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="9dd7a-122">Kapsayıcılarda tanılama toplama</span><span class="sxs-lookup"><span data-stu-id="9dd7a-122">Collect diagnostics in containers</span></span>

<span data-ttu-id="9dd7a-123">Kapsayıcısız Linux ortamlarında kullanılan aynı tanılama araçları, [kapsayıcılarda tanılamayı toplamak](diagnostics-in-containers.md)için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-123">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="9dd7a-124">Araçların bir Docker kapsayıcısında çalıştığından emin olmak için birkaç kullanım değişikliği yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-124">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="9dd7a-125">Linux dökümlerinin hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dd7a-125">Debug Linux dumps</span></span>

<span data-ttu-id="9dd7a-126">[Linux dökümlerinde hata ayıklama](debug-linux-dumps.md) , Linux üzerinde dökümleri nasıl toplayacağınızı ve analiz edeceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-126">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="9dd7a-127">.NET Core tanılama küresel Araçlar</span><span class="sxs-lookup"><span data-stu-id="9dd7a-127">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="9dd7a-128">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="9dd7a-128">dotnet-counters</span></span>

<span data-ttu-id="9dd7a-129">[DotNet sayaçları](dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-129">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="9dd7a-130">API aracılığıyla yayınlanan performans sayacı değerlerini sunar <xref:System.Diagnostics.Tracing.EventCounter> .</span><span class="sxs-lookup"><span data-stu-id="9dd7a-130">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="9dd7a-131">Örneğin, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-131">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="9dd7a-132">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="9dd7a-132">dotnet-dump</span></span>

<span data-ttu-id="9dd7a-133">[DotNet-dump](dotnet-dump.md) Aracı, yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-133">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="9dd7a-134">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="9dd7a-134">dotnet-gcdump</span></span>

<span data-ttu-id="9dd7a-135">[DotNet-gcdump](dotnet-gcdump.md) Aracı, canlı .net işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-135">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="9dd7a-136">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="9dd7a-136">dotnet-trace</span></span>

<span data-ttu-id="9dd7a-137">.NET Core, `EventPipe` Tanılama verilerinin sunulmasına ilişkin ne DENlerin dahil olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-137">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="9dd7a-138">[DotNet-Trace](dotnet-trace.md) Aracı, uygulamanızın yavaş çalışan uygulamaların yavaşlamasına neden olması gereken senaryolarda yardımcı olabilecek, uygulamanızda ilgi çekici profil oluşturma verilerini kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-138">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="9dd7a-139">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="9dd7a-139">dotnet-symbol</span></span>

<span data-ttu-id="9dd7a-140">[DotNet-symbol](dotnet-symbol.md) dosyaları indirir (semboller, dac/DBI, ana bilgisayar dosyaları vb.) temel döküm veya mini döküm açmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-140">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="9dd7a-141">Farklı bir makinede yakalanan bir döküm dosyasında hata ayıklaması yapmak için semboller ve modüller gerekiyorsa bu aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-141">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="9dd7a-142">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="9dd7a-142">dotnet-sos</span></span>

<span data-ttu-id="9dd7a-143">[DotNet-sos](dotnet-sos.md) , Linux veya MacOS 'a (veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'A) [sos hata ayıklama uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-143">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="9dd7a-144">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="9dd7a-144">PerfCollect</span></span>

<span data-ttu-id="9dd7a-145">[PerfCollect](trace-perfcollect-lttng.md) , `perf` `LTTng` Linux dağıtımları üzerinde çalışan .NET uygulamalarının daha ayrıntılı bir performans analiziyle birlikte izlemeleri toplamak için kullanabileceğiniz bir bash betiğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-145">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="9dd7a-146">.NET Core tanılama öğreticileri</span><span class="sxs-lookup"><span data-stu-id="9dd7a-146">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="9dd7a-147">Bellek sızıntısında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dd7a-147">Debug a memory leak</span></span>

<span data-ttu-id="9dd7a-148">[Öğretici:](debug-memory-leak.md) Bellek sızıntısını bulma adım bir bellek sızıntısı.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-148">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="9dd7a-149">Sızıntı [-Counters](dotnet-counters.md) Aracı, sızıntıyı doğrulamak için kullanılır ve sızıntı sorunlarını tanılamak için [DotNet-dump](dotnet-dump.md) aracı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-149">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="9dd7a-150">Yüksek CPU kullanımı hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dd7a-150">Debug high CPU usage</span></span>

<span data-ttu-id="9dd7a-151">[Öğretici: hata ayıklama yüksek CPU](debug-highcpu.md) kullanımı, yüksek CPU kullanımını araştırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-151">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="9dd7a-152">Yüksek CPU kullanımını onaylamak için [DotNet-Counters](dotnet-counters.md) aracını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-152">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="9dd7a-153">Daha sonra, CPU kullanım profilini toplamak ve görüntülemek için [Performans Analizi yardımcı programı ( `dotnet-trace` ) veya Linux için izleme](dotnet-trace.md) 'yi kullanma konusunda size kılavuzluk eder `perf` .</span><span class="sxs-lookup"><span data-stu-id="9dd7a-153">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="9dd7a-154">Çıkmaz hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="9dd7a-154">Debug deadlock</span></span>

<span data-ttu-id="9dd7a-155">[Öğretici: hata ayıklama kilitlenmesi](debug-deadlock.md) , iş parçacıklarını ve kilitleri araştırmak için [DotNet-dump](dotnet-dump.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-155">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="9dd7a-156">EventCounters kullanarak performansı ölçme</span><span class="sxs-lookup"><span data-stu-id="9dd7a-156">Measure performance using EventCounters</span></span>

<span data-ttu-id="9dd7a-157">[Öğretici: .net 'Teki eventcounters kullanılarak performansı ölçmek](event-counter-perf.md) , <xref:System.Diagnostics.Tracing.EventCounter> .net uygulamanızda performansı ölçmek için API 'yi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dd7a-157">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
