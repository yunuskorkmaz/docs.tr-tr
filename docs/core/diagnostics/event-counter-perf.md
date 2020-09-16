---
title: .NET Core 'da EventCounters kullanarak performansı ölçme
description: Bu öğreticide, EventCounters kullanarak performansı ölçme hakkında bilgi edineceksiniz.
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: db9a0889d46cc4db02baac60cbed6f6e0ba6856b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538572"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="f7634-103">Öğretici: .NET Core 'da EventCounters kullanarak performansı ölçme</span><span class="sxs-lookup"><span data-stu-id="f7634-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="f7634-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f7634-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="f7634-105">Bu öğreticide, <xref:System.Diagnostics.Tracing.EventCounter> yüksek bir olay sıklığıyla performansı ölçmek için nasıl kullanılabileceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="f7634-106">Çeşitli resmi .NET Core paketleri, üçüncü taraf sağlayıcılar tarafından yayınlanan [kullanılabilir sayaçları](event-counters.md#available-counters) kullanabilir veya izleme için kendi ölçümlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-106">You can use the [available counters](event-counters.md#available-counters) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="f7634-107">Bu öğreticide şunları yapacaksınız:</span><span class="sxs-lookup"><span data-stu-id="f7634-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f7634-108">Uygulayın <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="f7634-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="f7634-109">[DotNet sayaçları](dotnet-counters.md)olan sayaçları izleyin.</span><span class="sxs-lookup"><span data-stu-id="f7634-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7634-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f7634-110">Prerequisites</span></span>

<span data-ttu-id="f7634-111">Öğretici şunları kullanır:</span><span class="sxs-lookup"><span data-stu-id="f7634-111">The tutorial uses:</span></span>

- <span data-ttu-id="f7634-112">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="f7634-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="f7634-113">olay sayaçlarını izlemek için [DotNet sayaçları](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="f7634-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="f7634-114">Tanılama için bir [örnek hata ayıklama hedef](/samples/dotnet/samples/diagnostic-scenarios) uygulaması.</span><span class="sxs-lookup"><span data-stu-id="f7634-114">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="f7634-115">Kaynağı al</span><span class="sxs-lookup"><span data-stu-id="f7634-115">Get the source</span></span>

<span data-ttu-id="f7634-116">Örnek uygulama, izlemenin temeli olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7634-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="f7634-117">[Örnek ASP.NET Core deposu](/samples/dotnet/samples/diagnostic-scenarios) , örnekler tarayıcısından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7634-117">The [sample ASP.NET Core repository](/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="f7634-118">ZIP dosyasını indirir, indirdikten sonra ayıklayın ve en sevdiğiniz IDE 'niz içinde açın.</span><span class="sxs-lookup"><span data-stu-id="f7634-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="f7634-119">Doğru çalıştığından emin olmak için uygulamayı derleyin ve çalıştırın, sonra uygulamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="f7634-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="f7634-120">EventSource uygulama</span><span class="sxs-lookup"><span data-stu-id="f7634-120">Implement an EventSource</span></span>

<span data-ttu-id="f7634-121">Birkaç milisaniyede bir gerçekleşen olaylar için, olay başına ek yükün düşük (milisaniyenin altında) olmasını isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="f7634-122">Aksi takdirde, performans üzerindeki etki önemli olur.</span><span class="sxs-lookup"><span data-stu-id="f7634-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="f7634-123">Bir olayı günlüğe kaydetme, diske bir şey yazacağınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7634-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="f7634-124">Disk yeterince hızlı değilse olayları kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="f7634-125">Olayın kendisini günlüğe kaydetme dışında bir çözüme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="f7634-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="f7634-126">Çok sayıda olayla ilgilenirken, olay başına ölçüyü bilmek yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f7634-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="f7634-127">Çoğu zaman tüm ihtiyacınız olan yalnızca bazı istatistiklerdir.</span><span class="sxs-lookup"><span data-stu-id="f7634-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="f7634-128">Bu nedenle, istatistikleri işlemin kendisi içinde alabilir ve ardından istatistikleri raporlamak için bir kez bir olay yazabilirsiniz. Bu, ne <xref:System.Diagnostics.Tracing.EventCounter> olur?</span><span class="sxs-lookup"><span data-stu-id="f7634-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="f7634-129">Uygulamasının nasıl uygulanacağını gösteren bir örnek aşağıda verilmiştir <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="f7634-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="f7634-130">*MinimalEventCounterSource.cs* adlı yeni bir dosya oluşturun ve kaynak olarak kod parçacığını kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7634-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="f7634-131"><xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>Satır <xref:System.Diagnostics.Tracing.EventSource> bölümüdür ve parçası değildir <xref:System.Diagnostics.Tracing.EventCounter> , olay sayacından bir iletiyi günlüğe kaydetmek için yazılmış olduğunu göstermek için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f7634-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="f7634-132">Eylem filtresi ekleme</span><span class="sxs-lookup"><span data-stu-id="f7634-132">Add an action filter</span></span>

<span data-ttu-id="f7634-133">Örnek kaynak kodu bir ASP.NET Core projem.</span><span class="sxs-lookup"><span data-stu-id="f7634-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="f7634-134">Toplam istek süresini günlüğe alacak şekilde genel bir [eylem filtresi](/aspnet/core/mvc/controllers/filters#action-filters) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="f7634-135">*LogRequestTimeFilterAttribute.cs*adlı yeni bir dosya oluşturun ve aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7634-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="f7634-136">Eylem filtresi, <xref:System.Diagnostics.Stopwatch> istek başladığı sırada başlar ve tamamlandıktan sonra, geçen süreyi yakalayarak duraklar.</span><span class="sxs-lookup"><span data-stu-id="f7634-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="f7634-137">Toplam milisaniye tekil `MinimalEventCounterSource` örneğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f7634-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="f7634-138">Bu filtrenin uygulanması için filtre koleksiyonuna eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7634-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="f7634-139">*Startup.cs* dosyasında, `ConfigureServices` Bu filtreyi dahil etme içindeki yöntemi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7634-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="f7634-140">Olay sayacını izle</span><span class="sxs-lookup"><span data-stu-id="f7634-140">Monitor event counter</span></span>

<span data-ttu-id="f7634-141"><xref:System.Diagnostics.Tracing.EventSource>Ve özel eylem filtresi üzerinde uygulama ile uygulamayı derleyin ve başlatın.</span><span class="sxs-lookup"><span data-stu-id="f7634-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="f7634-142">Ölçüyü öğesine açtınız, ancak bundan <xref:System.Diagnostics.Tracing.EventCounter> itibaren istatistiklere erişmediğiniz müddetçe faydalı değildir.</span><span class="sxs-lookup"><span data-stu-id="f7634-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="f7634-143">İstatistikleri almak için, <xref:System.Diagnostics.Tracing.EventCounter> olayların yakalanması için bir dinleyici ve olayları istediğiniz sıklıkta tetiklenen bir Zamanlayıcı oluşturarak öğesini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7634-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="f7634-144">Bunu yapmak için [DotNet-Counters](dotnet-counters.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="f7634-145">İzlenebilecek .NET işlemlerinin bir listesini göstermek için [DotNet-Counters PS](dotnet-counters.md#dotnet-counters-ps) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7634-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="f7634-146">Komutun çıktısından işlem tanımlayıcısını kullanarak `dotnet-counters ps` , aşağıdaki komutla olay sayacını izlemeye başlayabilirsiniz `dotnet-counters monitor` :</span><span class="sxs-lookup"><span data-stu-id="f7634-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="f7634-147">Komut çalışırken `dotnet-counters monitor` , uç noktaya sürekli istek vermeyi başlatmak için tarayıcıda <kbd>F5</kbd> tuşunu basılı tutun `https://localhost:5001/api/values` .</span><span class="sxs-lookup"><span data-stu-id="f7634-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="f7634-148">Birkaç saniye sonra <kbd>soru-cevap</kbd> ' a basılarak</span><span class="sxs-lookup"><span data-stu-id="f7634-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="f7634-149">`dotnet-counters monitor`Komut, etkin izleme için harika.</span><span class="sxs-lookup"><span data-stu-id="f7634-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="f7634-150">Ancak, bu tanılama ölçümlerini son işleme ve analiz için toplamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="f7634-151">Bunun için `dotnet-counters collect` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7634-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="f7634-152">`collect`Switch komutu `monitor` komuta benzerdir, ancak birkaç ek parametre kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f7634-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="f7634-153">İstenen çıkış dosyası adını ve biçimini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7634-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="f7634-154">*diagnostics.js* ADLı bir JSON dosyası için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7634-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="f7634-155">Yine, komut çalışırken, uç noktaya sürekli istek vermeyi başlatmak için tarayıcıda <kbd>F5</kbd> tuşunu basılı tutun `https://localhost:5001/api/values` .</span><span class="sxs-lookup"><span data-stu-id="f7634-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="f7634-156">Birkaç saniye sonra <kbd>q</kbd>tuşuna basarak durur.</span><span class="sxs-lookup"><span data-stu-id="f7634-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="f7634-157">Dosyadaki *diagnostics.js* yazılır.</span><span class="sxs-lookup"><span data-stu-id="f7634-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="f7634-158">Yazılan JSON dosyası girintili değildir; ancak okunabilirlik için burada girintilenir.</span><span class="sxs-lookup"><span data-stu-id="f7634-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="f7634-159">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f7634-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f7634-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="f7634-160">EventCounters</span></span>](event-counters.md)
