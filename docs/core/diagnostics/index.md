---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 0aa404497cb7d6a488fb51e1df8f7f45d4f213fd
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678093"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="a8b1c-103">.NET Core 'da hangi tanılama araçları kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="a8b1c-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="a8b1c-104">Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="a8b1c-105">Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="a8b1c-106">Yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="a8b1c-106">Managed debuggers</span></span>

<span data-ttu-id="a8b1c-107">[Yönetilen hata defterleri](managed-debuggers.md) , programla etkileşime girebilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="a8b1c-108">Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="a8b1c-109">Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="a8b1c-110">Günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="a8b1c-110">Logging and tracing</span></span>

<span data-ttu-id="a8b1c-111">[Günlüğe kaydetme ve izleme](logging-tracing.md) ilgili teknikler.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="a8b1c-112">Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="a8b1c-113">Dosyalar, bir programın yaptığı ayrıntıları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-113">The files record the details of what a program does.</span></span> <span data-ttu-id="a8b1c-114">Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="a8b1c-115">Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="metrics"></a><span data-ttu-id="a8b1c-116">Ölçümler</span><span class="sxs-lookup"><span data-stu-id="a8b1c-116">Metrics</span></span>

<span data-ttu-id="a8b1c-117">[Eventcounters](event-counters.md) , performans sorunlarını belirlemek ve izlemek için ölçümler yazmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-117">[EventCounters](event-counters.md) allows you to write metrics to identify and monitor performance issues.</span></span> <span data-ttu-id="a8b1c-118">Ölçümler, izlemeye kıyasla daha düşük performans yükü sağlar ve her zaman açık performans izleme için daha uygun hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-118">Metrics incur lower performance overhead compared to tracing, making it more suitable for an always-on performance monitoring.</span></span> <span data-ttu-id="a8b1c-119">.NET çalışma zamanı ve kitaplıkları, izleyebildiğiniz birkaç [iyi bilinen EventCounters](available-counters.md) yayımlar.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-119">The .NET runtime and libraries publish several [well-known EventCounters](available-counters.md) that you can monitor as well.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="a8b1c-120">Birim testi</span><span class="sxs-lookup"><span data-stu-id="a8b1c-120">Unit testing</span></span>

<span data-ttu-id="a8b1c-121">[Birim testi](../testing/index.md) , yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-121">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="a8b1c-122">Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-122">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="a8b1c-123">Dökümler</span><span class="sxs-lookup"><span data-stu-id="a8b1c-123">Dumps</span></span>

<span data-ttu-id="a8b1c-124">[Döküm](./dumps.md) , oluşturma sırasında işlemin anlık görüntüsünü içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-124">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="a8b1c-125">Bunlar, hata ayıklama amacıyla uygulamanızın durumunu incelemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-125">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="a8b1c-126">Kapsayıcılarda tanılama toplama</span><span class="sxs-lookup"><span data-stu-id="a8b1c-126">Collect diagnostics in containers</span></span>

<span data-ttu-id="a8b1c-127">Kapsayıcısız Linux ortamlarında kullanılan aynı tanılama araçları, [kapsayıcılarda tanılamayı toplamak](diagnostics-in-containers.md)için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-127">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="a8b1c-128">Araçların bir Docker kapsayıcısında çalıştığından emin olmak için birkaç kullanım değişikliği yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-128">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="a8b1c-129">.NET Core tanılama küresel Araçlar</span><span class="sxs-lookup"><span data-stu-id="a8b1c-129">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="a8b1c-130">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="a8b1c-130">dotnet-counters</span></span>

<span data-ttu-id="a8b1c-131">[DotNet sayaçları](dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-131">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="a8b1c-132">API aracılığıyla yayınlanan performans sayacı değerlerini sunar <xref:System.Diagnostics.Tracing.EventCounter> .</span><span class="sxs-lookup"><span data-stu-id="a8b1c-132">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="a8b1c-133">Örneğin, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-133">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="a8b1c-134">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="a8b1c-134">dotnet-dump</span></span>

<span data-ttu-id="a8b1c-135">[DotNet-dump](dotnet-dump.md) Aracı, yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-135">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="a8b1c-136">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="a8b1c-136">dotnet-gcdump</span></span>

<span data-ttu-id="a8b1c-137">[DotNet-gcdump](dotnet-gcdump.md) Aracı, canlı .net işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-137">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="a8b1c-138">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="a8b1c-138">dotnet-trace</span></span>

<span data-ttu-id="a8b1c-139">.NET Core, `EventPipe` Tanılama verilerinin sunulmasına ilişkin ne DENlerin dahil olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-139">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="a8b1c-140">[DotNet-Trace](dotnet-trace.md) Aracı, uygulamanızın yavaş çalışan uygulamaların yavaşlamasına neden olması gereken senaryolarda yardımcı olabilecek, uygulamanızda ilgi çekici profil oluşturma verilerini kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-140">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="a8b1c-141">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="a8b1c-141">dotnet-symbol</span></span>

<span data-ttu-id="a8b1c-142">[DotNet-symbol](dotnet-symbol.md) dosyaları indirir (semboller, dac/DBI, ana bilgisayar dosyaları vb.) temel döküm veya mini döküm açmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-142">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="a8b1c-143">Farklı bir makinede yakalanan bir döküm dosyasında hata ayıklaması yapmak için semboller ve modüller gerekiyorsa bu aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-143">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="a8b1c-144">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="a8b1c-144">dotnet-sos</span></span>

<span data-ttu-id="a8b1c-145">[DotNet-sos](dotnet-sos.md) , Linux veya MacOS 'a (veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'A) [sos hata ayıklama uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-145">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="a8b1c-146">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="a8b1c-146">PerfCollect</span></span>

<span data-ttu-id="a8b1c-147">[PerfCollect](trace-perfcollect-lttng.md) , `perf` `LTTng` Linux dağıtımları üzerinde çalışan .NET uygulamalarının daha ayrıntılı bir performans analiziyle birlikte izlemeleri toplamak için kullanabileceğiniz bir bash betiğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-147">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="a8b1c-148">.NET Core tanılama öğreticileri</span><span class="sxs-lookup"><span data-stu-id="a8b1c-148">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="a8b1c-149">Bellek sızıntısında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a8b1c-149">Debug a memory leak</span></span>

<span data-ttu-id="a8b1c-150">[Öğretici:](debug-memory-leak.md) Bellek sızıntısını bulma adım bir bellek sızıntısı.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-150">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="a8b1c-151">Sızıntı [-Counters](dotnet-counters.md) Aracı, sızıntıyı doğrulamak için kullanılır ve sızıntı sorunlarını tanılamak için [DotNet-dump](dotnet-dump.md) aracı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-151">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="a8b1c-152">Yüksek CPU kullanımı hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="a8b1c-152">Debug high CPU usage</span></span>

<span data-ttu-id="a8b1c-153">[Öğretici: hata ayıklama yüksek CPU](debug-highcpu.md) kullanımı, yüksek CPU kullanımını araştırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-153">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="a8b1c-154">Yüksek CPU kullanımını onaylamak için [DotNet-Counters](dotnet-counters.md) aracını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-154">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="a8b1c-155">Daha sonra, CPU kullanım profilini toplamak ve görüntülemek için [Performans Analizi yardımcı programı ( `dotnet-trace` ) veya Linux için izleme](dotnet-trace.md) 'yi kullanma konusunda size kılavuzluk eder `perf` .</span><span class="sxs-lookup"><span data-stu-id="a8b1c-155">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="a8b1c-156">Çıkmaz hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="a8b1c-156">Debug deadlock</span></span>

<span data-ttu-id="a8b1c-157">[Öğretici: hata ayıklama kilitlenmesi](debug-deadlock.md) , iş parçacıklarını ve kilitleri araştırmak için [DotNet-dump](dotnet-dump.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-157">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="debug-linux-dumps"></a><span data-ttu-id="a8b1c-158">Linux dökümlerinin hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="a8b1c-158">Debug Linux dumps</span></span>

<span data-ttu-id="a8b1c-159">[Linux dökümlerinde hata ayıklama](debug-linux-dumps.md) , Linux üzerinde dökümleri nasıl toplayacağınızı ve analiz edeceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-159">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="a8b1c-160">EventCounters kullanarak performansı ölçme</span><span class="sxs-lookup"><span data-stu-id="a8b1c-160">Measure performance using EventCounters</span></span>

<span data-ttu-id="a8b1c-161">[Öğretici: .net 'Teki eventcounters kullanılarak performansı ölçmek](event-counter-perf.md) , <xref:System.Diagnostics.Tracing.EventCounter> .net uygulamanızda performansı ölçmek için API 'yi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8b1c-161">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
