---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 9836ea11e7f17d6ed6e04bcba8bc0ed851bb368f
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105290"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="25bff-103">.NET Core 'da hangi tanılama araçları kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="25bff-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="25bff-104">Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="25bff-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="25bff-105">Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="25bff-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="25bff-106">Yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="25bff-106">Managed debuggers</span></span>

<span data-ttu-id="25bff-107">[Yönetilen hata defterleri](managed-debuggers.md) , programla etkileşime girebilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="25bff-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="25bff-108">Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir.</span><span class="sxs-lookup"><span data-stu-id="25bff-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="25bff-109">Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.</span><span class="sxs-lookup"><span data-stu-id="25bff-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="25bff-110">Günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="25bff-110">Logging and tracing</span></span>

<span data-ttu-id="25bff-111">[Günlüğe kaydetme ve izleme](logging-tracing.md) ilgili teknikler.</span><span class="sxs-lookup"><span data-stu-id="25bff-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="25bff-112">Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar.</span><span class="sxs-lookup"><span data-stu-id="25bff-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="25bff-113">Dosyalar, bir programın yaptığı ayrıntıları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="25bff-113">The files record the details of what a program does.</span></span> <span data-ttu-id="25bff-114">Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25bff-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="25bff-115">Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="25bff-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="metrics"></a><span data-ttu-id="25bff-116">Ölçümler</span><span class="sxs-lookup"><span data-stu-id="25bff-116">Metrics</span></span>

<span data-ttu-id="25bff-117">[Eventcounters](event-counters.md) , performans sorunlarını belirlemek ve izlemek için ölçümler yazmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="25bff-117">[EventCounters](event-counters.md) allows you to write metrics to identify and monitor performance issues.</span></span> <span data-ttu-id="25bff-118">Ölçümler, izlemeye kıyasla daha düşük performans yükü sağlar ve her zaman açık performans izleme için daha uygun hale gelir.</span><span class="sxs-lookup"><span data-stu-id="25bff-118">Metrics incur lower performance overhead compared to tracing, making it more suitable for an always-on performance monitoring.</span></span> <span data-ttu-id="25bff-119">.NET çalışma zamanı ve kitaplıkları, izleyebildiğiniz birkaç [iyi bilinen EventCounters](available-counters.md) yayımlar.</span><span class="sxs-lookup"><span data-stu-id="25bff-119">The .NET runtime and libraries publish several [well-known EventCounters](available-counters.md) that you can monitor as well.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="25bff-120">Birim testi</span><span class="sxs-lookup"><span data-stu-id="25bff-120">Unit testing</span></span>

<span data-ttu-id="25bff-121">[Birim testi](../testing/index.md) , yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="25bff-121">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="25bff-122">Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="25bff-122">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="25bff-123">Dökümler</span><span class="sxs-lookup"><span data-stu-id="25bff-123">Dumps</span></span>

<span data-ttu-id="25bff-124">[Döküm](./dumps.md) , oluşturma sırasında işlemin anlık görüntüsünü içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="25bff-124">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="25bff-125">Bunlar, hata ayıklama amacıyla uygulamanızın durumunu incelemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25bff-125">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="symbols"></a><span data-ttu-id="25bff-126">Simgeleri</span><span class="sxs-lookup"><span data-stu-id="25bff-126">Symbols</span></span>

<span data-ttu-id="25bff-127">[Semboller](./symbols.md) , kaynak kodu ile derleyici tarafından üretilen ikili arasında bir eşlemedir.</span><span class="sxs-lookup"><span data-stu-id="25bff-127">[Symbols](./symbols.md) are a mapping between the source code and the binary produced by the compiler.</span></span> <span data-ttu-id="25bff-128">Bunlar genellikle .NET hata ayıklayıcıları tarafından kaynak satır numaralarını, yerel değişken adlarını ve diğer tanılama bilgileri türlerini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25bff-128">These are commonly used by .NET debuggers to resolve source line numbers, local variable names, and other types of diagnostic information.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="25bff-129">Kapsayıcılarda tanılama toplama</span><span class="sxs-lookup"><span data-stu-id="25bff-129">Collect diagnostics in containers</span></span>

<span data-ttu-id="25bff-130">Kapsayıcısız Linux ortamlarında kullanılan aynı tanılama araçları, [kapsayıcılarda tanılamayı toplamak](diagnostics-in-containers.md)için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25bff-130">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="25bff-131">Araçların bir Docker kapsayıcısında çalıştığından emin olmak için birkaç kullanım değişikliği yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25bff-131">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="25bff-132">.NET Core tanılama küresel Araçlar</span><span class="sxs-lookup"><span data-stu-id="25bff-132">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="25bff-133">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="25bff-133">dotnet-counters</span></span>

<span data-ttu-id="25bff-134">[DotNet sayaçları](dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="25bff-134">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="25bff-135">API aracılığıyla yayınlanan performans sayacı değerlerini sunar <xref:System.Diagnostics.Tracing.EventCounter> .</span><span class="sxs-lookup"><span data-stu-id="25bff-135">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="25bff-136">Örneğin, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25bff-136">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="25bff-137">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="25bff-137">dotnet-dump</span></span>

<span data-ttu-id="25bff-138">[DotNet-dump](dotnet-dump.md) Aracı, yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="25bff-138">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="25bff-139">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="25bff-139">dotnet-gcdump</span></span>

<span data-ttu-id="25bff-140">[DotNet-gcdump](dotnet-gcdump.md) Aracı, canlı .net işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="25bff-140">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="25bff-141">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="25bff-141">dotnet-trace</span></span>

<span data-ttu-id="25bff-142">.NET Core, `EventPipe` Tanılama verilerinin sunulmasına ilişkin ne DENlerin dahil olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="25bff-142">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="25bff-143">[DotNet-Trace](dotnet-trace.md) Aracı, uygulamanızın yavaş çalışan uygulamaların yavaşlamasına neden olması gereken senaryolarda yardımcı olabilecek, uygulamanızda ilgi çekici profil oluşturma verilerini kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="25bff-143">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="25bff-144">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="25bff-144">dotnet-symbol</span></span>

<span data-ttu-id="25bff-145">[DotNet-symbol](dotnet-symbol.md) dosyaları indirir (semboller, dac/DBI, ana bilgisayar dosyaları vb.) temel döküm veya mini döküm açmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="25bff-145">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="25bff-146">Farklı bir makinede yakalanan bir döküm dosyasında hata ayıklaması yapmak için semboller ve modüller gerekiyorsa bu aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="25bff-146">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="25bff-147">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="25bff-147">dotnet-sos</span></span>

<span data-ttu-id="25bff-148">[DotNet-sos](dotnet-sos.md) , Linux ve MacOS 'A ( [WinDbg/CDB](/windows-hardware/drivers/debugger/debugger-download-tools)kullanıyorsanız Windows 'a) [sos hata ayıklama uzantısını](sos-debugging-extension.md) yükleme.</span><span class="sxs-lookup"><span data-stu-id="25bff-148">[dotnet-sos](dotnet-sos.md) installs the [SOS debugging extension](sos-debugging-extension.md) on Linux and macOS (and on Windows if you're using [Windbg/cdb](/windows-hardware/drivers/debugger/debugger-download-tools)).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="25bff-149">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="25bff-149">PerfCollect</span></span>

<span data-ttu-id="25bff-150">[PerfCollect](trace-perfcollect-lttng.md) , `perf` `LTTng` Linux dağıtımları üzerinde çalışan .NET uygulamalarının daha ayrıntılı bir performans analiziyle birlikte izlemeleri toplamak için kullanabileceğiniz bir bash betiğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="25bff-150">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="25bff-151">.NET Core tanılama öğreticileri</span><span class="sxs-lookup"><span data-stu-id="25bff-151">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="25bff-152">Bellek sızıntısında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="25bff-152">Debug a memory leak</span></span>

<span data-ttu-id="25bff-153">[Öğretici:](debug-memory-leak.md) Bellek sızıntısını bulma adım bir bellek sızıntısı.</span><span class="sxs-lookup"><span data-stu-id="25bff-153">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="25bff-154">Sızıntı [-Counters](dotnet-counters.md) Aracı, sızıntıyı doğrulamak için kullanılır ve sızıntı sorunlarını tanılamak için [DotNet-dump](dotnet-dump.md) aracı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25bff-154">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="25bff-155">Yüksek CPU kullanımı hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="25bff-155">Debug high CPU usage</span></span>

<span data-ttu-id="25bff-156">[Öğretici: hata ayıklama yüksek CPU](debug-highcpu.md) kullanımı, yüksek CPU kullanımını araştırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="25bff-156">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="25bff-157">Yüksek CPU kullanımını onaylamak için [DotNet-Counters](dotnet-counters.md) aracını kullanır.</span><span class="sxs-lookup"><span data-stu-id="25bff-157">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="25bff-158">Daha sonra, CPU kullanım profilini toplamak ve görüntülemek için [Performans Analizi yardımcı programı ( `dotnet-trace` ) veya Linux için izleme](dotnet-trace.md) 'yi kullanma konusunda size kılavuzluk eder `perf` .</span><span class="sxs-lookup"><span data-stu-id="25bff-158">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="25bff-159">Çıkmaz hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="25bff-159">Debug deadlock</span></span>

<span data-ttu-id="25bff-160">[Öğretici: hata ayıklama kilitlenmesi](debug-deadlock.md) , iş parçacıklarını ve kilitleri araştırmak için [DotNet-dump](dotnet-dump.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bff-160">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="debug-a-stackoverflow"></a><span data-ttu-id="25bff-161">StackOverflow hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="25bff-161">Debug a StackOverflow</span></span>

<span data-ttu-id="25bff-162">[Öğretici: StackOverflow hata ayıklama bir](debug-stackoverflow.md) Linux 'ta bir hata ayıklamanın nasıl yapılacağını gösterir <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="25bff-162">[Tutorial: Debug a StackOverflow](debug-stackoverflow.md) demonstrates how to debug a <xref:System.StackOverflowException> on Linux.</span></span>

### <a name="debug-linux-dumps"></a><span data-ttu-id="25bff-163">Linux dökümlerinin hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="25bff-163">Debug Linux dumps</span></span>

<span data-ttu-id="25bff-164">[Linux dökümlerinde hata ayıklama](debug-linux-dumps.md) , Linux üzerinde dökümleri nasıl toplayacağınızı ve analiz edeceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="25bff-164">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="25bff-165">EventCounters kullanarak performansı ölçme</span><span class="sxs-lookup"><span data-stu-id="25bff-165">Measure performance using EventCounters</span></span>

<span data-ttu-id="25bff-166">[Öğretici: .net 'Teki eventcounters kullanılarak performansı ölçmek](event-counter-perf.md) , <xref:System.Diagnostics.Tracing.EventCounter> .net uygulamanızda performansı ölçmek için API 'yi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bff-166">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
