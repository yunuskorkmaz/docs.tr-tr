---
title: Application Insights-sunucusuz uygulamalar
description: Application Insights, geliştiricilerin Web Apps, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerde sorunları algılamasını, önceliklendirme ve tanılamalarını sağlayan sunucusuz bir tanılama platformudur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522739"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="e0a36-103">Application Insights ile telemetri</span><span class="sxs-lookup"><span data-stu-id="e0a36-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="e0a36-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) , geliştiricilerin Web Apps, mobil uygulamalar, masaüstü uygulamaları ve mikro hizmetlerde sorunları algılamasını, önceliklendirme ve tanılamalarını sağlayan sunucusuz bir tanılama platformudur.</span><span class="sxs-lookup"><span data-stu-id="e0a36-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="e0a36-105">Yalnızca portalda bir anahtarı açarak işlev uygulamaları için Application Insights açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0a36-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="e0a36-106">Application Insights, bir sunucu yapılandırmanıza veya kendi veritabanınızı ayarlamanıza gerek kalmadan tüm bu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0a36-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="e0a36-107">Tüm Application Insights ' özellikleri, uygulamalarınızla otomatik olarak tümleştirilen bir hizmet olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e0a36-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights logosu](./media/application-insights-logo.png)

<span data-ttu-id="e0a36-109">Mevcut uygulamalara Application Insights eklemek, uygulamanızın ayarlarına bir izleme anahtarı eklemek kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="e0a36-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="e0a36-110">Application Insights ile şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0a36-110">With Application Insights you can:</span></span>

- <span data-ttu-id="e0a36-111">İşlev etkinleştirmeleri sayısı, bir işlev çalıştırmak için geçen süre ve özel durumlar gibi ölçümleri temel alarak özel grafikler ve uyarılar oluşturun</span><span class="sxs-lookup"><span data-stu-id="e0a36-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="e0a36-112">Sorunları ve sunucu özel durumlarını çözümleme</span><span class="sxs-lookup"><span data-stu-id="e0a36-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="e0a36-113">İşleme göre performans ile detaya gitme ve üçüncü taraf bağımlılıklarını çağırmak için geçen süreyi ölçme</span><span class="sxs-lookup"><span data-stu-id="e0a36-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="e0a36-114">İşlev uygulamalarınızı barındıran tüm sunuculardaki CPU kullanımını, belleği ve fiyatları izleyin</span><span class="sxs-lookup"><span data-stu-id="e0a36-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="e0a36-115">İşlev uygulamalarınız için istek sayısı ve gecikme süresi dahil olmak üzere ölçümlerin canlı bir akışını görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="e0a36-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="e0a36-116">İşlev verileriniz üzerinde özel grafikler aramak, sorgulamak ve oluşturmak için [Analizi](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) kullanın</span><span class="sxs-lookup"><span data-stu-id="e0a36-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Ölçüm Gezgini](./media/metrics-explorer.png)

<span data-ttu-id="e0a36-118">Yerleşik telemetriye ek olarak, özel telemetri oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e0a36-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="e0a36-119">Aşağıdaki kod parçacığı, işlev uygulaması için ayarlanan izleme anahtarını kullanarak özel bir telemetri istemcisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e0a36-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="e0a36-120">Aşağıdaki kod, bir [Azure Tablo depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) örneğine yeni bir satır eklemek için geçen süreyi ölçer:</span><span class="sxs-lookup"><span data-stu-id="e0a36-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="e0a36-121">Elde edilen performans grafiği görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="e0a36-121">The resulting performance graph is shown:</span></span>

![Özel telemetri](./media/custom-telemetry.png)

<span data-ttu-id="e0a36-123">Özel telemetri, yeni bir satır eklemek için geçen ortalama süreyi 32,6 milisaniyedir.</span><span class="sxs-lookup"><span data-stu-id="e0a36-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="e0a36-124">Application Insights, sunucusuz uygulamalarınız hakkında ayrıntılı telemetri günlüğe kaydetmek için güçlü ve uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0a36-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="e0a36-125">Belirtilen izleme ve günlüğe kaydetme düzeyi üzerinde tam denetime sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e0a36-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="e0a36-126">Olaylar, bağımlılıklar ve sayfa görünümü gibi özel istatistikleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0a36-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="e0a36-127">Son olarak, güçlü analizler önemli sorular sorduğu ve grafikler ve gelişmiş Öngörüler üreten sorgular yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0a36-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="e0a36-128">Daha fazla bilgi için bkz. [Azure Işlevlerini izleme](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="e0a36-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e0a36-129">[Önceki](azure-functions.md)
>[İleri](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="e0a36-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
