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
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a>Öğretici: .NET Core 'da EventCounters kullanarak performansı ölçme

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,0 SDK ve sonraki sürümleri

Bu öğreticide, <xref:System.Diagnostics.Tracing.EventCounter> yüksek bir olay sıklığıyla performansı ölçmek için nasıl kullanılabileceğinizi öğreneceksiniz. Çeşitli resmi .NET Core paketleri, üçüncü taraf sağlayıcılar tarafından yayınlanan [kullanılabilir sayaçları](event-counters.md#available-counters) kullanabilir veya izleme için kendi ölçümlerinizi oluşturabilirsiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
>
> - Uygulayın <xref:System.Diagnostics.Tracing.EventSource> .
> - [DotNet sayaçları](dotnet-counters.md)olan sayaçları izleyin.

## <a name="prerequisites"></a>Önkoşullar

Öğretici şunları kullanır:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.
- olay sayaçlarını izlemek için [DotNet sayaçları](dotnet-counters.md) .
- Tanılama için bir [örnek hata ayıklama hedef](/samples/dotnet/samples/diagnostic-scenarios) uygulaması.

## <a name="get-the-source"></a>Kaynağı al

Örnek uygulama, izlemenin temeli olarak kullanılacaktır. [Örnek ASP.NET Core deposu](/samples/dotnet/samples/diagnostic-scenarios) , örnekler tarayıcısından kullanılabilir. ZIP dosyasını indirir, indirdikten sonra ayıklayın ve en sevdiğiniz IDE 'niz içinde açın. Doğru çalıştığından emin olmak için uygulamayı derleyin ve çalıştırın, sonra uygulamayı durdurun.

## <a name="implement-an-eventsource"></a>EventSource uygulama

Birkaç milisaniyede bir gerçekleşen olaylar için, olay başına ek yükün düşük (milisaniyenin altında) olmasını isteyeceksiniz. Aksi takdirde, performans üzerindeki etki önemli olur. Bir olayı günlüğe kaydetme, diske bir şey yazacağınız anlamına gelir. Disk yeterince hızlı değilse olayları kaybedersiniz. Olayın kendisini günlüğe kaydetme dışında bir çözüme ihtiyacınız vardır.

Çok sayıda olayla ilgilenirken, olay başına ölçüyü bilmek yararlı değildir. Çoğu zaman tüm ihtiyacınız olan yalnızca bazı istatistiklerdir. Bu nedenle, istatistikleri işlemin kendisi içinde alabilir ve ardından istatistikleri raporlamak için bir kez bir olay yazabilirsiniz. Bu, ne <xref:System.Diagnostics.Tracing.EventCounter> olur?

Uygulamasının nasıl uygulanacağını gösteren bir örnek aşağıda verilmiştir <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> . *MinimalEventCounterSource.cs* adlı yeni bir dosya oluşturun ve kaynak olarak kod parçacığını kullanın:

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>Satır <xref:System.Diagnostics.Tracing.EventSource> bölümüdür ve parçası değildir <xref:System.Diagnostics.Tracing.EventCounter> , olay sayacından bir iletiyi günlüğe kaydetmek için yazılmış olduğunu göstermek için yazılmıştır.

## <a name="add-an-action-filter"></a>Eylem filtresi ekleme

Örnek kaynak kodu bir ASP.NET Core projem. Toplam istek süresini günlüğe alacak şekilde genel bir [eylem filtresi](/aspnet/core/mvc/controllers/filters#action-filters) ekleyebilirsiniz. *LogRequestTimeFilterAttribute.cs*adlı yeni bir dosya oluşturun ve aşağıdaki kodu kullanın:

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

Eylem filtresi, <xref:System.Diagnostics.Stopwatch> istek başladığı sırada başlar ve tamamlandıktan sonra, geçen süreyi yakalayarak duraklar. Toplam milisaniye tekil `MinimalEventCounterSource` örneğe kaydedilir. Bu filtrenin uygulanması için filtre koleksiyonuna eklemeniz gerekir. *Startup.cs* dosyasında, `ConfigureServices` Bu filtreyi dahil etme içindeki yöntemi güncelleştirin.

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a>Olay sayacını izle

<xref:System.Diagnostics.Tracing.EventSource>Ve özel eylem filtresi üzerinde uygulama ile uygulamayı derleyin ve başlatın.
Ölçüyü öğesine açtınız, ancak bundan <xref:System.Diagnostics.Tracing.EventCounter> itibaren istatistiklere erişmediğiniz müddetçe faydalı değildir. İstatistikleri almak için, <xref:System.Diagnostics.Tracing.EventCounter> olayların yakalanması için bir dinleyici ve olayları istediğiniz sıklıkta tetiklenen bir Zamanlayıcı oluşturarak öğesini etkinleştirmeniz gerekir. Bunu yapmak için [DotNet-Counters](dotnet-counters.md)kullanabilirsiniz.

İzlenebilecek .NET işlemlerinin bir listesini göstermek için [DotNet-Counters PS](dotnet-counters.md#dotnet-counters-ps) komutunu kullanın.

```console
dotnet-counters ps
```

Komutun çıktısından işlem tanımlayıcısını kullanarak `dotnet-counters ps` , aşağıdaki komutla olay sayacını izlemeye başlayabilirsiniz `dotnet-counters monitor` :

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

Komut çalışırken `dotnet-counters monitor` , uç noktaya sürekli istek vermeyi başlatmak için tarayıcıda <kbd>F5</kbd> tuşunu basılı tutun `https://localhost:5001/api/values` . Birkaç saniye sonra <kbd>soru-cevap</kbd> ' a basılarak

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

`dotnet-counters monitor`Komut, etkin izleme için harika. Ancak, bu tanılama ölçümlerini son işleme ve analiz için toplamak isteyebilirsiniz. Bunun için `dotnet-counters collect` komutunu kullanın. `collect`Switch komutu `monitor` komuta benzerdir, ancak birkaç ek parametre kabul eder. İstenen çıkış dosyası adını ve biçimini belirtebilirsiniz. *diagnostics.js* ADLı bir JSON dosyası için aşağıdaki komutu kullanın:

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

Yine, komut çalışırken, uç noktaya sürekli istek vermeyi başlatmak için tarayıcıda <kbd>F5</kbd> tuşunu basılı tutun `https://localhost:5001/api/values` . Birkaç saniye sonra <kbd>q</kbd>tuşuna basarak durur. Dosyadaki *diagnostics.js* yazılır. Yazılan JSON dosyası girintili değildir; ancak okunabilirlik için burada girintilenir.

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

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [EventCounters](event-counters.md)
