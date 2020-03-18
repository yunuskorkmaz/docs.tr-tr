---
title: Uygulama Öngörüleri - Sunucusuz uygulamalar
description: Application Insights, geliştiricilerin web uygulamaları, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerdeki sorunları algılamasını, triyajlamasını ve tanılamasını sağlayan sunucusuz bir tanılama platformudur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522739"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="f1613-103">Application Insights ile telemetri</span><span class="sxs-lookup"><span data-stu-id="f1613-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="f1613-104">[Application Insights,](https://docs.microsoft.com/azure/application-insights) geliştiricilerin web uygulamaları, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerdeki sorunları algılamasını, triyajetmesini ve tanılamasını sağlayan sunucusuz bir tanılama platformudur.</span><span class="sxs-lookup"><span data-stu-id="f1613-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="f1613-105">İşlev uygulamaları için Uygulama Öngörüleri'ni portaldaki bir anahtarı çevirerek açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1613-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="f1613-106">Application Insights, bir sunucuyu yapılandırmanız veya kendi veritabanınızı kurmanız gerekmeden tüm bu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1613-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="f1613-107">Application Insights'ın tüm özellikleri, uygulamalarınız ile otomatik olarak entegre olan bir hizmet olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f1613-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Uygulama Öngörüleri logosu](./media/application-insights-logo.png)

<span data-ttu-id="f1613-109">Mevcut uygulamalara Uygulama Öngörüleri eklemek, uygulamanızın ayarlarına bir enstrümantasyon anahtarı eklemek kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="f1613-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="f1613-110">Uygulama Öngörüleri ile şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1613-110">With Application Insights you can:</span></span>

- <span data-ttu-id="f1613-111">İşlev çağırma sayısı, bir işlevi çalıştırmak için gereken süre ve özel durumlar gibi ölçümlere göre özel grafikler ve uyarılar oluşturun</span><span class="sxs-lookup"><span data-stu-id="f1613-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="f1613-112">Hataları ve sunucu özel durumlarını çözümleme</span><span class="sxs-lookup"><span data-stu-id="f1613-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="f1613-113">Operasyonla performansa sondaj yapmak ve üçüncü taraf bağımlılıklarını aramak için gereken süreyi ölçün</span><span class="sxs-lookup"><span data-stu-id="f1613-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="f1613-114">İşlev uygulamalarınızı barındıran tüm sunucularda CPU kullanımını, belleği ve oranları izleyin</span><span class="sxs-lookup"><span data-stu-id="f1613-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="f1613-115">İşlev uygulamalarınız için istek sayısı ve gecikme sayısı da dahil olmak üzere canlı bir ölçüm akışını görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="f1613-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="f1613-116">İşlev verileriniz üzerinde arama yapmak, sorgulamak ve özel grafikler oluşturmak için [Analytics'i](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) kullanın</span><span class="sxs-lookup"><span data-stu-id="f1613-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Ölçümler gezgini](./media/metrics-explorer.png)

<span data-ttu-id="f1613-118">Dahili telemetriye ek olarak, özel telemetri de oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f1613-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="f1613-119">Aşağıdaki kod snippet işlevi uygulaması için enstrümantasyon anahtarı kümesini kullanarak özel bir telemetri istemcisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f1613-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="f1613-120">Aşağıdaki kod, bir [Azure Tablo Depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) örneğine yeni bir satır eklemenin ne kadar süreceğini ölçer:</span><span class="sxs-lookup"><span data-stu-id="f1613-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="f1613-121">Elde edilen performans grafiği gösterilir:</span><span class="sxs-lookup"><span data-stu-id="f1613-121">The resulting performance graph is shown:</span></span>

![Özel telemetri](./media/custom-telemetry.png)

<span data-ttu-id="f1613-123">Özel telemetri, yeni bir satır eklemek için ortalama süre 32,6 milisaniye olduğunu ortaya koymaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1613-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="f1613-124">Application Insights, sunucusuz uygulamalarınız hakkında ayrıntılı telemetri günlüğe kaydetmek için güçlü ve kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1613-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="f1613-125">Sağlanan izleme ve günlüğe kaydetme düzeyi üzerinde tam denetime sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1613-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="f1613-126">Olaylar, bağımlılıklar ve sayfa görünümü gibi özel istatistikleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1613-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="f1613-127">Son olarak, güçlü analitik, önemli sorular soran ve grafikler ve gelişmiş öngörüler oluşturan sorgular yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1613-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="f1613-128">Daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)</span><span class="sxs-lookup"><span data-stu-id="f1613-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f1613-129">[Önceki](azure-functions.md)
>[Sonraki](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="f1613-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
