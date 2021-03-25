---
title: Dağıtılmış bir izleme toplayın-.NET
description: Opentelemetri, Application Insights veya ActivityListener kullanarak .NET uygulamalarında dağıtılmış izlemeler toplamamıza yönelik öğreticiler
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: f5e2ea6dc09edbc7c51586f4da8d4a6088804cbd
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111578"
---
# <a name="collect-a-distributed-trace"></a>Dağıtılmış bir izleme toplayın

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 2,1 ve üzeri sürümleri **ve** .NET Framework 4,5 ve sonraki sürümler

Belgelenmiş kod <xref:System.Diagnostics.Activity> , dağıtılmış izlemenin bir parçası olarak nesneler oluşturabilir, ancak tüm izlemenin daha sonra incelenebilecek şekilde bu nesnelerdeki bilgilerin merkezi depolamaya toplanması gerekir. Bu öğreticide, gerektiğinde uygulama sorunlarını tanılamak için kullanılabilir olması için dağıtılmış izleme telemetrisini farklı yollarla toplayacaksınız. Yeni izleme eklemeniz gerekiyorsa, bkz. [izleme öğreticisi](distributed-tracing-instrumentation-walkthroughs.md) .

## <a name="collect-traces-using-opentelemetry"></a>Opentelemetri kullanarak izlemeleri toplayın

### <a name="prerequisites"></a>Önkoşullar

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet) veya sonraki bir sürümü

### <a name="create-an-example-application"></a>Örnek uygulama oluşturma

Herhangi bir dağıtılmış izleme Telemetriyi toplamadan önce üretmemiz gerekiyor. Bu izleme genellikle kitaplıklarda olabilir ancak kolaylık sağlaması için, kullanarak bir örnek araç içeren küçük bir uygulama oluşturacaksınız <xref:System.Diagnostics.ActivitySource.StartActivity%2A> . Bu noktada henüz hiçbir koleksiyon gerçekleşmemiştir, StartActivity () yan etkiye sahip değildir ve null değerini döndürür. Daha fazla bilgi için bkz. [izleme öğreticisi](distributed-tracing-instrumentation-walkthroughs.md) .

```dotnetcli
dotnet new console
```

.NET 5 ve üstünü hedefleyen uygulamalar, gereken dağıtılmış izleme API 'Lerini zaten içeriyor. Eski .NET sürümlerini hedefleyen uygulamalar için [System. Diagnostics. DiagnosticSource NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) sürüm 5 veya üstünü ekleyin.

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

Oluşturulan program. cs içeriğini bu örnek kaynakla değiştirin:

```C#
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");

        static async Task Main(string[] args)
        {
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }

        static async Task DoSomeWork()
        {
            using (Activity a = s_source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }

        static async Task StepOne()
        {
            using (Activity a = s_source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity a = s_source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
    }
}
```

Uygulamayı çalıştırmak henüz hiçbir izleme verisi toplamaz:

```dotnetcli
> dotnet run
Example work done
```

### <a name="collect-using-opentelemetry"></a>Opentelemetri kullanarak toplama

[Opentelemetri](https://opentelemetry.io/) , bulut Yerel [bilgi işlem altyapısı](https://www.cncf.io/) tarafından desteklenen, bulut Yerel yazılım için telemetri oluşturma ve toplama işlemini standartlaştırmaya yönelik bir satıcı tarafsız açık kaynak projesimdir. Bu örnekte, Opentelemetri daha başka bir yere gönderilmek üzere yeniden yapılandırısa da, dağıtılmış izleme bilgilerini konsolda toplayıp görüntüleyirsiniz. Daha fazla bilgi için bkz. [Opentelemetri Başlangıç Kılavuzu](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) .

[Opentelemetri. dışarı aktarma. konsol](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet paketini ekleyin.

```dotnetcli
dotnet add package OpenTelemetry.Exporter.Console
```

Using deyimleri kullanarak program. cs 'yi ek Opentelemetri ile güncelleştirin:

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;
```

Opentelemetri izleme sağlayıcısı oluşturmak için Main () öğesini güncelleştirin:

```C#
        public static async Task Main()
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork();
            Console.WriteLine("Example work done");
        }
```

Uygulama artık dağıtılmış izleme bilgilerini toplayıp konsola görüntülüyor:

```dotnetcli
> dotnet run
Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-6081a9b8041cd840-01
Activity.ParentId:    00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:46.8649754Z
Activity.Duration:    00:00:00.5069226
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-d2b283db91cf774c-01
Activity.ParentId:    00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:47.3838737Z
Activity.Duration:    00:00:01.0142278
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:46.8634510Z
Activity.Duration:    00:00:01.5402045
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Example work done
```

#### <a name="sources"></a>Kaynaklar

`AddSource("Sample.DistributedTracing")`Bu durumda, Opentelemetriyi kodda zaten bulunan ActivitySource tarafından üretilen etkinlikleri yakalayacak şekilde, çağrılan örnek kodda:

```csharp
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");
```

Herhangi bir ActivitySource 'tan alınan telemetri, AddSource () kaynağını kaynağın adıyla çağırarak yakalanabilir.

#### <a name="exporters"></a>Dışarı vericiler

Konsol dışarı aktarıcı, Hızlı örnekler veya yerel geliştirme için yararlıdır, ancak bir üretim dağıtımında, büyük olasılıkla izlemeleri merkezi bir depoya göndermek istersiniz. Opentelemetri, farklı [dışarı](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library)vericiler kullanan çeşitli hedefleri destekler.
Opentelemetri yapılandırma hakkında daha fazla bilgi için bkz. [Opentelemetri Başlangıç Kılavuzu](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started) .

## <a name="collect-traces-using-application-insights"></a>Application Insights kullanarak izlemeleri toplayın

Dağıtılmış izleme telemetrisi, Application Insights SDK ([ASP.net](https://docs.microsoft.com/azure/azure-monitor/app/asp-net), [ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) yapılandırıldıktan sonra veya [kod daha az izleme](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview)etkinleştirilerek otomatik olarak yakalanır.

Daha fazla bilgi için bkz. [Application Insights dağıtılmış izleme belgeleri](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) .

> [!NOTE]
> Şu anda Application Insights yalnızca belirli bir tanınmış etkinlik araçları toplamayı destekler ve yeni kullanıcı tarafından eklenen etkinlikleri yoksayar. Application Insights, özel dağıtılmış izleme bilgileri eklemek için satıcıya özgü bir API olarak [Trackdependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) sunar.

## <a name="collect-traces-using-custom-logic"></a>Özel mantık kullanarak izlemeleri toplayın

Geliştiriciler, etkinlik izleme verileri için kendi özelleştirilmiş koleksiyon mantığını oluşturmak ücretsizdir. Bu örnek, <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> .NET tarafından sunulan API 'yi kullanarak Telemetriyi toplayıp konsola yazdırır.

### <a name="prerequisites"></a>Önkoşullar

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet) veya sonraki bir sürümü

### <a name="create-an-example-application"></a>Örnek uygulama oluşturma

İlk olarak, bazı dağıtılmış izleme araçlarına sahip olan ancak izleme verisi toplanmayan örnek bir uygulama oluşturacaksınız.

```dotnetcli
dotnet new console
```

.NET 5 ve üstünü hedefleyen uygulamalar, gereken dağıtılmış izleme API 'Lerini zaten içeriyor. Eski .NET sürümlerini hedefleyen uygulamalar için [System. Diagnostics. DiagnosticSource NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) sürüm 5 veya üstünü ekleyin.

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

Oluşturulan program. cs içeriğini bu örnek kaynakla değiştirin:

```C#
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");

        static async Task Main(string[] args)
        {
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }

        static async Task DoSomeWork()
        {
            using (Activity a = s_source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }

        static async Task StepOne()
        {
            using (Activity a = s_source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity a = s_source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
    }
}
```

Uygulamayı çalıştırmak henüz hiçbir izleme verisi toplamaz:

```dotnetcli
> dotnet run
Example work done
```

### <a name="add-code-to-collect-the-traces"></a>İzlemeleri toplamak için kod ekleyin

Main () öğesini şu kodla güncelleştir:

```C#
        static async Task Main(string[] args)
        {
            Activity.DefaultIdFormat = ActivityIdFormat.W3C;
            Activity.ForceDefaultIdFormat = true;

            Console.WriteLine("         {0,-15} {1,-60} {2,-15}", "OperationName", "Id", "Duration");
            ActivitySource.AddActivityListener(new ActivityListener()
            {
                ShouldListenTo = (source) => true,
                Sample = (ref ActivityCreationOptions<ActivityContext> options) => ActivitySamplingResult.AllDataAndRecorded,
                ActivityStarted = activity => Console.WriteLine("Started: {0,-15} {1,-60}", activity.OperationName, activity.Id),
                ActivityStopped = activity => Console.WriteLine("Stopped: {0,-15} {1,-60} {2,-15}", activity.OperationName, activity.Id, activity.Duration)
            });
            
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }
```

Çıktı şimdi günlüğe kaydetme içerir:

```dotnetcli
> dotnet run
         OperationName   Id                                                           Duration
Started: SomeWork        00-bdb5faffc2fc1548b6ba49a31c4a0ae0-c447fb302059784f-01
Started: StepOne         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-a7c77a4e9a02dc4a-01
Stopped: StepOne         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-a7c77a4e9a02dc4a-01      00:00:00.5093849
Started: StepTwo         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-9210ad536cae9e4e-01
Stopped: StepTwo         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-9210ad536cae9e4e-01      00:00:01.0111847
Stopped: SomeWork        00-bdb5faffc2fc1548b6ba49a31c4a0ae0-c447fb302059784f-01      00:00:01.5236391
Example work done
```

<xref:System.Diagnostics.Activity.DefaultIdFormat>Ve <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> isteğe bağlıdır, ancak örneğin farklı .NET çalışma zamanı sürümlerinde benzer bir çıkış ürettiğinden emin olur. .NET 5, varsayılan olarak W3C TraceContext ID biçimini kullanır, ancak önceki .NET sürümleri varsayılan olarak <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> kimlik biçimini kullanır. Daha fazla ayrıntı için bkz. [etkinlik kimlikleri](distributed-tracing-concepts.md#activity-ids) .

<xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> , bir etkinliğin ömrü boyunca geri çağırmaları almak için kullanılır.

- <xref:System.Diagnostics.ActivityListener.ShouldListenTo> -Her etkinlik, ad alanı ve üreticisi olarak davranan bir ActivitySource ile ilişkilendirilir.
Bu geri çağırma, işlemdeki her ActivitySource için bir kez çağrılır. Örnekleme gerçekleştirmeyi veya bu kaynak tarafından üretilen etkinliklere yönelik başlatma/durdurma olayları hakkında bildirim almak istiyorsanız true döndürün.
- <xref:System.Diagnostics.ActivityListener.Sample> - <xref:System.Diagnostics.ActivitySource.StartActivity%2A> Bazı ActivityListener örneklenmeyeceğini belirtmedikçe, varsayılan olarak bir etkinlik nesnesi oluşturmaz. Mektir <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded>
Etkinliğin oluşturulması gerektiğini, <xref:System.Diagnostics.Activity.IsAllDataRequested> true olarak ayarlanması gerektiğini ve <xref:System.Diagnostics.Activity.ActivityTraceFlags> <xref:System.Diagnostics.ActivityTraceFlags.Recorded> bayrağın ayarlanmış olacağını gösterir. Iallldatarequary, bir dinleyicinin Etiketler ve olaylar gibi çok sayıda etkinlik bilgisinin doldurulduğundan emin olmak istediği bir ipucu olarak, belgelenmiş kodla gözlemlenebilir.
Kaydedilen bayrak W3C TraceContext KIMLIĞINDE kodlanır ve bu izlemenin örneklendiği dağıtılmış izlemede yer alan diğer işlemlere yönelik bir ipucu olur.
- <xref:System.Diagnostics.ActivityListener.ActivityStarted> ve <xref:System.Diagnostics.ActivityListener.ActivityStopped> sırasıyla bir etkinlik başlatıldığında ve durdurulduğunda çağrılır. Bu geri çağrılar, etkinlik veya değişiklik için olası bilgileri kaydetmek üzere bir oportunity sağlar.
Bir etkinlik, verilerin büyük bölümü hala tamamlanmamış olabilir ve etkinlik durdurulmadan önce doldurulur.

Bir ActivityListener oluşturulduktan ve geri çağrılar doldurulduktan sonra, çağırma <xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType>
geri çağırmaları çağırma işlemini başlatır. <xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType>Geri çağırmaların akışını durdurmak için çağırın. Dispose () çalışırken çok iş parçacıklı kod geri çağırma bildirimlerinin devam ettiğini ve geri dönmesinin ardından çok kısa sürede alındığını unutmayın.
