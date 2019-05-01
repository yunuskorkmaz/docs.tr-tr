---
title: Application Insights - sunucusuz uygulamalar
description: Application Insights, geliştiricilerin belirleme, Önceliklendirme ve web uygulamaları, mobil uygulamaları, Masaüstü uygulamaları ve mikro hizmetler sorunları tanılamanıza olanak sağlayan bir sunucusuz tanılama platformudur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4884d483de07c1c2077f7280b6b77c6059572c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051240"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="33d94-103">Application Insights ile telemetri</span><span class="sxs-lookup"><span data-stu-id="33d94-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="33d94-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) algılamak, önceliklendirmek ve web uygulamaları, mobil uygulamaları, Masaüstü uygulamaları ve mikro hizmetler sorunları tanılamak geliştiricilerin sağlayan bir sunucusuz tanılama platformudur.</span><span class="sxs-lookup"><span data-stu-id="33d94-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="33d94-105">Portalda yalnızca bir anahtar döndürerek işlev uygulamaları için Application Insights kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33d94-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="33d94-106">Application Insights sunar bu özelliklerin tümünü gerek kalmadan bir sunucuyu yapılandırmak veya kendi veritabanınızı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="33d94-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="33d94-107">Application Insights özelliklerin tümünü ile uygulamalarınızı otomatik olarak hizmeti olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="33d94-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights logosu](./media/application-insights-logo.png)

<span data-ttu-id="33d94-109">Mevcut uygulamaları için Application Insights ekleme, bir izleme anahtarı, uygulamanızın ayarlar eklemek kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="33d94-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="33d94-110">Application Insights ile şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="33d94-110">With Application Insights you can:</span></span>

* <span data-ttu-id="33d94-111">Özel grafikler ve işlev çağrılarını sayısı gibi ölçümlere göre uyarılar oluşturun, bir işlev ve özel durumlar çalıştırmak için geçen süre</span><span class="sxs-lookup"><span data-stu-id="33d94-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
* <span data-ttu-id="33d94-112">Hataları ve sunucu özel durumları analiz edin</span><span class="sxs-lookup"><span data-stu-id="33d94-112">Analyze failures and server exceptions</span></span>
* <span data-ttu-id="33d94-113">Bir performans sağladığını işlemiyle ayrıntıya ve üçüncü taraf bağımlılıklarının çağırmak için gereken süreyi ölçün</span><span class="sxs-lookup"><span data-stu-id="33d94-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
* <span data-ttu-id="33d94-114">CPU kullanımı, bellek ve oranları işlev uygulamalarınızı barındıran tüm sunucular arasında izleyin</span><span class="sxs-lookup"><span data-stu-id="33d94-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
* <span data-ttu-id="33d94-115">İstek sayısı ve gecikme süresi, işlev uygulamalarınızı da dahil seçilen ölçümlerin Canlı akışı görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="33d94-115">View a live stream of metrics including request count and latency for your function apps</span></span>
* <span data-ttu-id="33d94-116">Kullanım [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) aramak için sorgu ve işlev verileriniz üzerinde özel grafikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="33d94-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Ölçüm Gezgini](./media/metrics-explorer.png)

<span data-ttu-id="33d94-118">Yerleşik telemetri yanı sıra, ayrıca özel telemetri oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="33d94-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="33d94-119">Aşağıdaki kod parçacığı, işlev uygulaması için izleme anahtarını kullanarak özel telemetri istemcisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="33d94-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="33d94-120">Yeni bir satır eklemek için ne kadar sürer, aşağıdaki kodu ölçer bir [Azure tablo depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) örneği:</span><span class="sxs-lookup"><span data-stu-id="33d94-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="33d94-121">Ortaya çıkan performans grafiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="33d94-121">The resulting performance graph is shown:</span></span>

![Özel telemetri](./media/custom-telemetry.png)

<span data-ttu-id="33d94-123">Özel telemetri için yeni bir satır eklemek için geçen ortalama süre 32.6 milisaniyedir gösterir.</span><span class="sxs-lookup"><span data-stu-id="33d94-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="33d94-124">Application Insights, sunucusuz uygulamalarınız hakkında daha ayrıntılı telemetri oturum güçlü, kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="33d94-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="33d94-125">İzleme düzeyi üzerinde tam denetime sahiptir ve günlük sağlanır.</span><span class="sxs-lookup"><span data-stu-id="33d94-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="33d94-126">Olaylar, bağımlılıklar ve sayfa görüntüleme gibi özel istatistikleri takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33d94-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="33d94-127">Son olarak, güçlü analiz, önemli soru sorun ve grafikler ve Gelişmiş Öngörüler oluşturmak sorgular yazmaya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="33d94-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="33d94-128">Daha fazla bilgi için [İzleyici Azure işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="33d94-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="33d94-129">[Önceki](azure-functions.md)
>[İleri](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="33d94-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>