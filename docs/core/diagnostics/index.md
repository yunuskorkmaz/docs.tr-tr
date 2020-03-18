---
title: Teşhis araçlarına genel bakış - .NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araç ve tekniklere genel bakış.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399051"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="bfcf1-103">.NET Core'da hangi tanılama araçları mevcuttur?</span><span class="sxs-lookup"><span data-stu-id="bfcf1-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="bfcf1-104">Yazılım her zaman beklediğiniz gibi şekilde değil, ancak .NET Core'un bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçları ve API'leri vardır.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="bfcf1-105">Bu makalede, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="bfcf1-106">Yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="bfcf1-106">Managed debuggers</span></span>

<span data-ttu-id="bfcf1-107">[Yönetilen hata ayıklayıcıları,](managed-debuggers.md) programınızla etkileşimkurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="bfcf1-108">Duraklatma, aşamalı olarak yürütme, inceleme ve devam etme, kodunuzu davranış hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="bfcf1-109">Hata ayıklama, kolayca çoğaltılabilen işlevsel sorunları tanılamak için ilk tercihtir.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="bfcf1-110">Günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="bfcf1-110">Logging and tracing</span></span>

<span data-ttu-id="bfcf1-111">[Günlük ve izleme](logging-tracing.md) ile ilgili tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="bfcf1-112">Günlük dosyaları oluşturmak için enstrümanting koduna başvururlar.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="bfcf1-113">Dosyalar, bir programın ne yaptığının ayrıntılarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-113">The files record the details of what a program does.</span></span> <span data-ttu-id="bfcf1-114">Bu ayrıntılar en karmaşık sorunları tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="bfcf1-115">Zaman damgaları ile kombine edildiğinde, bu teknikler performans araştırmalarında da değerlidir.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="bfcf1-116">Birim testi</span><span class="sxs-lookup"><span data-stu-id="bfcf1-116">Unit testing</span></span>

<span data-ttu-id="bfcf1-117">[Birim testi,](../testing/index.md) sürekli tümleştirme ve yüksek kaliteli yazılım dağıtımının önemli bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="bfcf1-118">Birim testleri, bir şeyi kırdığınızda size erken uyarı vermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="bfcf1-119">.NET Core dotnet diagnostik Global Araçlar</span><span class="sxs-lookup"><span data-stu-id="bfcf1-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="bfcf1-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="bfcf1-120">dotnet-counters</span></span>

<span data-ttu-id="bfcf1-121">[dotnet sayaçları](dotnet-counters.md) birinci düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="bfcf1-122"><xref:System.Diagnostics.Tracing.EventCounter> API üzerinden yayınlanan performans sayacı değerlerini gözlemler.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="bfcf1-123">Örneğin, CPU kullanımı veya .NET Core uygulamanızda atılan özel durumlar oranı gibi şeyleri hızla izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="bfcf1-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="bfcf1-124">dotnet-dump</span></span>

<span data-ttu-id="bfcf1-125">[Dotnet-dump](dotnet-dump.md) aracı, windows ve Linux çekirdek dökümlerini yerel bir hata ayıklama olmadan toplamanın ve analiz etmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="bfcf1-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bfcf1-126">dotnet-trace</span></span>

<span data-ttu-id="bfcf1-127">.NET Core, tanılama `EventPipe` verilerinin hangi aracılığıyla açığa çıkarılana ne denir.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="bfcf1-128">[Dotnet izleme](dotnet-trace.md) aracı, uygulamanızın yavaş çalışmasını neden olan senaryolarda yardımcı olabilecek ilginç profil oluşturma verilerini uygulamanızdan tüketmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="bfcf1-129">.NET Core tanılama öğreticileri</span><span class="sxs-lookup"><span data-stu-id="bfcf1-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="bfcf1-130">Bellek sızıntısında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="bfcf1-130">Debug a memory leak</span></span>

<span data-ttu-id="bfcf1-131">[Öğretici: Hata ayıklama bir bellek sızıntısı](debug-memory-leak.md) bulma yoluyla yürür.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="bfcf1-132">[Dotnet sayaçları](dotnet-counters.md) aracı sızıntıyı doğrulamak için kullanılır ve sızıntıyı teşhis etmek için [dotnet-dump](dotnet-dump.md) aracı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bfcf1-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
