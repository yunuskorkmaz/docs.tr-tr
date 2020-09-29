---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: d78b73e53637927ecb877dd69054f75a1f5ac91f
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437996"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="db42e-103">.NET Core 'da hangi tanılama araçları kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="db42e-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="db42e-104">Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="db42e-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="db42e-105">Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="db42e-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="db42e-106">Yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="db42e-106">Managed debuggers</span></span>

<span data-ttu-id="db42e-107">[Yönetilen hata defterleri](managed-debuggers.md) , programla etkileşime girebilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="db42e-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="db42e-108">Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir.</span><span class="sxs-lookup"><span data-stu-id="db42e-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="db42e-109">Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.</span><span class="sxs-lookup"><span data-stu-id="db42e-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="db42e-110">Günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="db42e-110">Logging and tracing</span></span>

<span data-ttu-id="db42e-111">[Günlüğe kaydetme ve izleme](logging-tracing.md) ilgili teknikler.</span><span class="sxs-lookup"><span data-stu-id="db42e-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="db42e-112">Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar.</span><span class="sxs-lookup"><span data-stu-id="db42e-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="db42e-113">Dosyalar, bir programın yaptığı ayrıntıları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="db42e-113">The files record the details of what a program does.</span></span> <span data-ttu-id="db42e-114">Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db42e-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="db42e-115">Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="db42e-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="db42e-116">Birim testi</span><span class="sxs-lookup"><span data-stu-id="db42e-116">Unit testing</span></span>

<span data-ttu-id="db42e-117">[Birim testi](../testing/index.md) , yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="db42e-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="db42e-118">Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="db42e-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="db42e-119">Kapsayıcılarda tanılamayı toplayın</span><span class="sxs-lookup"><span data-stu-id="db42e-119">Collect diagnostics in containers</span></span>

<span data-ttu-id="db42e-120">Kapsayıcısız Linux ortamlarında kullanılan aynı tanılama araçları, [kapsayıcılarda tanılamayı toplamak](diagnostics-in-containers.md)için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db42e-120">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="db42e-121">Araçların bir Docker kapsayıcısında çalıştığından emin olmak için birkaç kullanım değişikliği yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db42e-121">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="db42e-122">Linux dökümlerinin hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="db42e-122">Debug Linux dumps</span></span>

<span data-ttu-id="db42e-123">[Linux dökümlerinde hata ayıklama](debug-linux-dumps.md) , Linux üzerinde dökümleri nasıl toplayacağınızı ve analiz edeceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="db42e-123">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="db42e-124">.NET Core tanılama küresel Araçlar</span><span class="sxs-lookup"><span data-stu-id="db42e-124">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="db42e-125">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="db42e-125">dotnet-counters</span></span>

<span data-ttu-id="db42e-126">[DotNet sayaçları](dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="db42e-126">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="db42e-127">API aracılığıyla yayınlanan performans sayacı değerlerini sunar <xref:System.Diagnostics.Tracing.EventCounter> .</span><span class="sxs-lookup"><span data-stu-id="db42e-127">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="db42e-128">Örneğin, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db42e-128">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="db42e-129">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="db42e-129">dotnet-dump</span></span>

<span data-ttu-id="db42e-130">[DotNet-dump](dotnet-dump.md) Aracı, yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="db42e-130">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="db42e-131">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="db42e-131">dotnet-gcdump</span></span>

<span data-ttu-id="db42e-132">[DotNet-gcdump](dotnet-gcdump.md) Aracı, canlı .net işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="db42e-132">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="db42e-133">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="db42e-133">dotnet-trace</span></span>

<span data-ttu-id="db42e-134">.NET Core, `EventPipe` Tanılama verilerinin sunulmasına ilişkin ne DENlerin dahil olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="db42e-134">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="db42e-135">[DotNet-Trace](dotnet-trace.md) Aracı, uygulamanızın yavaş çalışan uygulamaların yavaşlamasına neden olması gereken senaryolarda yardımcı olabilecek, uygulamanızda ilgi çekici profil oluşturma verilerini kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="db42e-135">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="db42e-136">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="db42e-136">dotnet-symbol</span></span>

<span data-ttu-id="db42e-137">[DotNet-symbol](dotnet-symbol.md) dosyaları indirir (semboller, dac/DBI, ana bilgisayar dosyaları vb.) temel döküm veya mini döküm açmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="db42e-137">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="db42e-138">Farklı bir makinede yakalanan bir döküm dosyasında hata ayıklaması yapmak için semboller ve modüller gerekiyorsa bu aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="db42e-138">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="db42e-139">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="db42e-139">dotnet-sos</span></span>

<span data-ttu-id="db42e-140">[DotNet-sos](dotnet-sos.md) , Linux veya MacOS 'a (veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'A) [sos hata ayıklama uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db42e-140">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="db42e-141">.NET Core tanılama öğreticileri</span><span class="sxs-lookup"><span data-stu-id="db42e-141">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="db42e-142">Bellek sızıntısında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="db42e-142">Debug a memory leak</span></span>

<span data-ttu-id="db42e-143">[Öğretici:](debug-memory-leak.md) Bellek sızıntısını bulma adım bir bellek sızıntısı.</span><span class="sxs-lookup"><span data-stu-id="db42e-143">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="db42e-144">Sızıntı [-Counters](dotnet-counters.md) Aracı, sızıntıyı doğrulamak için kullanılır ve sızıntı sorunlarını tanılamak için [DotNet-dump](dotnet-dump.md) aracı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db42e-144">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="db42e-145">Yüksek CPU kullanımı hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="db42e-145">Debug high CPU usage</span></span>

<span data-ttu-id="db42e-146">[Öğretici: hata ayıklama yüksek CPU](debug-highcpu.md) kullanımı, yüksek CPU kullanımını araştırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="db42e-146">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="db42e-147">Yüksek CPU kullanımını onaylamak için [DotNet-Counters](dotnet-counters.md) aracını kullanır.</span><span class="sxs-lookup"><span data-stu-id="db42e-147">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="db42e-148">Daha sonra, CPU kullanım profilini toplamak ve görüntülemek için [Performans Analizi yardımcı programı ( `dotnet-trace` ) veya Linux için izleme](dotnet-trace.md) 'yi kullanma konusunda size kılavuzluk eder `perf` .</span><span class="sxs-lookup"><span data-stu-id="db42e-148">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="db42e-149">Çıkmaz hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="db42e-149">Debug deadlock</span></span>

<span data-ttu-id="db42e-150">[Öğretici: hata ayıklama kilitlenmesi](debug-deadlock.md) , iş parçacıklarını ve kilitleri araştırmak için [DotNet-dump](dotnet-dump.md) aracının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db42e-150">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>
