---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.topic: overview
ms.openlocfilehash: c0a45a1bfe866ad42890db576b5dd5098b1dbc3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318338"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="0df64-103">.NET Core 'da hangi tanılama araçları kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="0df64-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="0df64-104">Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0df64-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="0df64-105">Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="0df64-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="0df64-106">Yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="0df64-106">Managed debuggers</span></span>

<span data-ttu-id="0df64-107">[Yönetilen hata defterleri](managed-debuggers.md) , programla etkileşime girebilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="0df64-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="0df64-108">Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir.</span><span class="sxs-lookup"><span data-stu-id="0df64-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="0df64-109">Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.</span><span class="sxs-lookup"><span data-stu-id="0df64-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="0df64-110">Günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="0df64-110">Logging and tracing</span></span>

<span data-ttu-id="0df64-111">[Günlüğe kaydetme ve izleme](logging-tracing.md) ilgili teknikler.</span><span class="sxs-lookup"><span data-stu-id="0df64-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="0df64-112">Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar.</span><span class="sxs-lookup"><span data-stu-id="0df64-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="0df64-113">Dosyalar, bir programın yaptığı ayrıntıları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0df64-113">The files record the details of what a program does.</span></span> <span data-ttu-id="0df64-114">Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0df64-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="0df64-115">Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="0df64-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="0df64-116">Birim testi</span><span class="sxs-lookup"><span data-stu-id="0df64-116">Unit testing</span></span>

<span data-ttu-id="0df64-117">[Birim testi](../testing/index.md) , yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="0df64-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="0df64-118">Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0df64-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="0df64-119">.NET Core DotNet tanılama küresel araçları</span><span class="sxs-lookup"><span data-stu-id="0df64-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="0df64-120">DotNet-sayaçlar</span><span class="sxs-lookup"><span data-stu-id="0df64-120">dotnet-counters</span></span>

<span data-ttu-id="0df64-121">[DotNet sayaçları](dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="0df64-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="0df64-122">@No__t-0 API 'SI aracılığıyla yayınlanan performans sayacı değerlerini sunar.</span><span class="sxs-lookup"><span data-stu-id="0df64-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="0df64-123">Örneğin, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0df64-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="0df64-124">DotNet-döküm</span><span class="sxs-lookup"><span data-stu-id="0df64-124">dotnet-dump</span></span>

<span data-ttu-id="0df64-125">[DotNet-dump](dotnet-dump.md) Aracı, yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="0df64-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="0df64-126">DotNet-izleme</span><span class="sxs-lookup"><span data-stu-id="0df64-126">dotnet-trace</span></span>

<span data-ttu-id="0df64-127">.NET Core, tanılama verilerinin açığa çıkarılabileceği `EventPipe` olarak adlandırılan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0df64-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="0df64-128">[DotNet-Trace](dotnet-trace.md) Aracı, uygulamanızın yavaş çalışan uygulamaların yavaşlamasına neden olması gereken senaryolarda yardımcı olabilecek, uygulamanızda ilgi çekici profil oluşturma verilerini kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0df64-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>
