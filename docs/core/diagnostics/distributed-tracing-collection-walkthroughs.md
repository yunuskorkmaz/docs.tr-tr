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
# <a name="collect-a-distributed-trace"></a><span data-ttu-id="26167-103">Dağıtılmış bir izleme toplayın</span><span class="sxs-lookup"><span data-stu-id="26167-103">Collect a distributed trace</span></span>

<span data-ttu-id="26167-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 2,1 ve üzeri sürümleri **ve** .NET Framework 4,5 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="26167-104">**This article applies to: ✔️** .NET Core 2.1 and later versions **and** .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="26167-105">Belgelenmiş kod <xref:System.Diagnostics.Activity> , dağıtılmış izlemenin bir parçası olarak nesneler oluşturabilir, ancak tüm izlemenin daha sonra incelenebilecek şekilde bu nesnelerdeki bilgilerin merkezi depolamaya toplanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="26167-105">Instrumented code can create <xref:System.Diagnostics.Activity> objects as part of a distributed trace, but the information in these objects needs to be collected into centralized storage so that the entire trace can be reviewed later.</span></span> <span data-ttu-id="26167-106">Bu öğreticide, gerektiğinde uygulama sorunlarını tanılamak için kullanılabilir olması için dağıtılmış izleme telemetrisini farklı yollarla toplayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="26167-106">In this tutorial you will collect the distributed trace telemetry in different ways so that it is available to diagnose application issues when needed.</span></span> <span data-ttu-id="26167-107">Yeni izleme eklemeniz gerekiyorsa, bkz. [izleme öğreticisi](distributed-tracing-instrumentation-walkthroughs.md) .</span><span class="sxs-lookup"><span data-stu-id="26167-107">See [the instrumentation tutorial](distributed-tracing-instrumentation-walkthroughs.md) if you need to add new instrumentation.</span></span>

## <a name="collect-traces-using-opentelemetry"></a><span data-ttu-id="26167-108">Opentelemetri kullanarak izlemeleri toplayın</span><span class="sxs-lookup"><span data-stu-id="26167-108">Collect traces using OpenTelemetry</span></span>

### <a name="prerequisites"></a><span data-ttu-id="26167-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="26167-109">Prerequisites</span></span>

- <span data-ttu-id="26167-110">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet) veya sonraki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="26167-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

### <a name="create-an-example-application"></a><span data-ttu-id="26167-111">Örnek uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="26167-111">Create an example application</span></span>

<span data-ttu-id="26167-112">Herhangi bir dağıtılmış izleme Telemetriyi toplamadan önce üretmemiz gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="26167-112">Before any distributed trace telemetry can be collected we need to produce it.</span></span> <span data-ttu-id="26167-113">Bu izleme genellikle kitaplıklarda olabilir ancak kolaylık sağlaması için, kullanarak bir örnek araç içeren küçük bir uygulama oluşturacaksınız <xref:System.Diagnostics.ActivitySource.StartActivity%2A> .</span><span class="sxs-lookup"><span data-stu-id="26167-113">Often this instrumentation might be in libraries but for simplicity you will create a small app that has some example instrumentation using <xref:System.Diagnostics.ActivitySource.StartActivity%2A>.</span></span> <span data-ttu-id="26167-114">Bu noktada henüz hiçbir koleksiyon gerçekleşmemiştir, StartActivity () yan etkiye sahip değildir ve null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="26167-114">At this point no collection is happening yet, StartActivity() has no side-effect and returns null.</span></span> <span data-ttu-id="26167-115">Daha fazla bilgi için bkz. [izleme öğreticisi](distributed-tracing-instrumentation-walkthroughs.md) .</span><span class="sxs-lookup"><span data-stu-id="26167-115">See [the instrumentation tutorial](distributed-tracing-instrumentation-walkthroughs.md) for more details.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="26167-116">.NET 5 ve üstünü hedefleyen uygulamalar, gereken dağıtılmış izleme API 'Lerini zaten içeriyor.</span><span class="sxs-lookup"><span data-stu-id="26167-116">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="26167-117">Eski .NET sürümlerini hedefleyen uygulamalar için [System. Diagnostics. DiagnosticSource NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) sürüm 5 veya üstünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26167-117">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="26167-118">Oluşturulan program. cs içeriğini bu örnek kaynakla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="26167-118">Replace the contents of the generated Program.cs with this example source:</span></span>

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

<span data-ttu-id="26167-119">Uygulamayı çalıştırmak henüz hiçbir izleme verisi toplamaz:</span><span class="sxs-lookup"><span data-stu-id="26167-119">Running the app does not collect any trace data yet:</span></span>

```dotnetcli
> dotnet run
Example work done
```

### <a name="collect-using-opentelemetry"></a><span data-ttu-id="26167-120">Opentelemetri kullanarak toplama</span><span class="sxs-lookup"><span data-stu-id="26167-120">Collect using OpenTelemetry</span></span>

<span data-ttu-id="26167-121">[Opentelemetri](https://opentelemetry.io/) , bulut Yerel [bilgi işlem altyapısı](https://www.cncf.io/) tarafından desteklenen, bulut Yerel yazılım için telemetri oluşturma ve toplama işlemini standartlaştırmaya yönelik bir satıcı tarafsız açık kaynak projesimdir.</span><span class="sxs-lookup"><span data-stu-id="26167-121">[OpenTelemetry](https://opentelemetry.io/) is a vendor neutral open source project supported by the [Cloud Native Computing Foundation](https://www.cncf.io/) that aims to standardize generating and collecting telemetry for cloud-native software.</span></span> <span data-ttu-id="26167-122">Bu örnekte, Opentelemetri daha başka bir yere gönderilmek üzere yeniden yapılandırısa da, dağıtılmış izleme bilgilerini konsolda toplayıp görüntüleyirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26167-122">In this example you will collect and display distributed trace information on the console though OpenTelemetry can be reconfigured to send it elsewhere.</span></span> <span data-ttu-id="26167-123">Daha fazla bilgi için bkz. [Opentelemetri Başlangıç Kılavuzu](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) .</span><span class="sxs-lookup"><span data-stu-id="26167-123">See the [OpenTelemetry getting started guide](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) for more information.</span></span>

<span data-ttu-id="26167-124">[Opentelemetri. dışarı aktarma. konsol](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26167-124">Add the [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet package.</span></span>

```dotnetcli
dotnet add package OpenTelemetry.Exporter.Console
```

<span data-ttu-id="26167-125">Using deyimleri kullanarak program. cs 'yi ek Opentelemetri ile güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="26167-125">Update Program.cs with additional OpenTelemetry using statments:</span></span>

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;
```

<span data-ttu-id="26167-126">Opentelemetri izleme sağlayıcısı oluşturmak için Main () öğesini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="26167-126">Update Main() to create the OpenTelemetry TracerProvider:</span></span>

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

<span data-ttu-id="26167-127">Uygulama artık dağıtılmış izleme bilgilerini toplayıp konsola görüntülüyor:</span><span class="sxs-lookup"><span data-stu-id="26167-127">Now the app collects distributed trace information and displays it to the console:</span></span>

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

#### <a name="sources"></a><span data-ttu-id="26167-128">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="26167-128">Sources</span></span>

<span data-ttu-id="26167-129">`AddSource("Sample.DistributedTracing")`Bu durumda, Opentelemetriyi kodda zaten bulunan ActivitySource tarafından üretilen etkinlikleri yakalayacak şekilde, çağrılan örnek kodda:</span><span class="sxs-lookup"><span data-stu-id="26167-129">In the example code you invoked `AddSource("Sample.DistributedTracing")` so that OpenTelemetry would capture the Activities produced by the ActivitySource that was already present in the code:</span></span>

```csharp
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");
```

<span data-ttu-id="26167-130">Herhangi bir ActivitySource 'tan alınan telemetri, AddSource () kaynağını kaynağın adıyla çağırarak yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="26167-130">Telemetry from any ActivitySource can captured by calling AddSource() with the source's name.</span></span>

#### <a name="exporters"></a><span data-ttu-id="26167-131">Dışarı vericiler</span><span class="sxs-lookup"><span data-stu-id="26167-131">Exporters</span></span>

<span data-ttu-id="26167-132">Konsol dışarı aktarıcı, Hızlı örnekler veya yerel geliştirme için yararlıdır, ancak bir üretim dağıtımında, büyük olasılıkla izlemeleri merkezi bir depoya göndermek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="26167-132">The console exporter is helpful for quick examples or local development but in a production deployment you will probably want to send traces to a centralized store.</span></span> <span data-ttu-id="26167-133">Opentelemetri, farklı [dışarı](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library)vericiler kullanan çeşitli hedefleri destekler.</span><span class="sxs-lookup"><span data-stu-id="26167-133">OpenTelemetry supports a variety of destinations using different [exporters](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library).</span></span>
<span data-ttu-id="26167-134">Opentelemetri yapılandırma hakkında daha fazla bilgi için bkz. [Opentelemetri Başlangıç Kılavuzu](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started) .</span><span class="sxs-lookup"><span data-stu-id="26167-134">See the [OpenTelemetry getting started guide](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started) for more information on configuring OpenTelemetry.</span></span>

## <a name="collect-traces-using-application-insights"></a><span data-ttu-id="26167-135">Application Insights kullanarak izlemeleri toplayın</span><span class="sxs-lookup"><span data-stu-id="26167-135">Collect traces using Application Insights</span></span>

<span data-ttu-id="26167-136">Dağıtılmış izleme telemetrisi, Application Insights SDK ([ASP.net](https://docs.microsoft.com/azure/azure-monitor/app/asp-net), [ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) yapılandırıldıktan sonra veya [kod daha az izleme](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview)etkinleştirilerek otomatik olarak yakalanır.</span><span class="sxs-lookup"><span data-stu-id="26167-136">Distributed tracing telemetry is automatically captured after configuring the Application Insights SDK ([ASP.NET](https://docs.microsoft.com/azure/azure-monitor/app/asp-net), [ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) or by enabling [code-less instrumentation](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview).</span></span>

<span data-ttu-id="26167-137">Daha fazla bilgi için bkz. [Application Insights dağıtılmış izleme belgeleri](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) .</span><span class="sxs-lookup"><span data-stu-id="26167-137">See the [Application Insights distributed tracing documentation](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="26167-138">Şu anda Application Insights yalnızca belirli bir tanınmış etkinlik araçları toplamayı destekler ve yeni kullanıcı tarafından eklenen etkinlikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="26167-138">Currently Application Insights only supports collecting specific well-known Activity instrumentation and will ignore new user added Activities.</span></span> <span data-ttu-id="26167-139">Application Insights, özel dağıtılmış izleme bilgileri eklemek için satıcıya özgü bir API olarak [Trackdependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) sunar.</span><span class="sxs-lookup"><span data-stu-id="26167-139">Application Insights offers [TrackDependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) as a vendor specific API for adding custom distributed tracing information.</span></span>

## <a name="collect-traces-using-custom-logic"></a><span data-ttu-id="26167-140">Özel mantık kullanarak izlemeleri toplayın</span><span class="sxs-lookup"><span data-stu-id="26167-140">Collect traces using custom logic</span></span>

<span data-ttu-id="26167-141">Geliştiriciler, etkinlik izleme verileri için kendi özelleştirilmiş koleksiyon mantığını oluşturmak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="26167-141">Developers are free to create their own customized collection logic for Activity trace data.</span></span> <span data-ttu-id="26167-142">Bu örnek, <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> .NET tarafından sunulan API 'yi kullanarak Telemetriyi toplayıp konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="26167-142">This example collects the telemetry using the <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> API provided by .NET and prints it to the console.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="26167-143">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="26167-143">Prerequisites</span></span>

- <span data-ttu-id="26167-144">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet) veya sonraki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="26167-144">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

### <a name="create-an-example-application"></a><span data-ttu-id="26167-145">Örnek uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="26167-145">Create an example application</span></span>

<span data-ttu-id="26167-146">İlk olarak, bazı dağıtılmış izleme araçlarına sahip olan ancak izleme verisi toplanmayan örnek bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="26167-146">First you will create an example application that has some distributed trace instrumentation but no trace data is being collected.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="26167-147">.NET 5 ve üstünü hedefleyen uygulamalar, gereken dağıtılmış izleme API 'Lerini zaten içeriyor.</span><span class="sxs-lookup"><span data-stu-id="26167-147">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="26167-148">Eski .NET sürümlerini hedefleyen uygulamalar için [System. Diagnostics. DiagnosticSource NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) sürüm 5 veya üstünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26167-148">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="26167-149">Oluşturulan program. cs içeriğini bu örnek kaynakla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="26167-149">Replace the contents of the generated Program.cs with this example source:</span></span>

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

<span data-ttu-id="26167-150">Uygulamayı çalıştırmak henüz hiçbir izleme verisi toplamaz:</span><span class="sxs-lookup"><span data-stu-id="26167-150">Running the app does not collect any trace data yet:</span></span>

```dotnetcli
> dotnet run
Example work done
```

### <a name="add-code-to-collect-the-traces"></a><span data-ttu-id="26167-151">İzlemeleri toplamak için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="26167-151">Add code to collect the traces</span></span>

<span data-ttu-id="26167-152">Main () öğesini şu kodla güncelleştir:</span><span class="sxs-lookup"><span data-stu-id="26167-152">Update Main() with this code:</span></span>

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

<span data-ttu-id="26167-153">Çıktı şimdi günlüğe kaydetme içerir:</span><span class="sxs-lookup"><span data-stu-id="26167-153">The output now includes logging:</span></span>

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

<span data-ttu-id="26167-154"><xref:System.Diagnostics.Activity.DefaultIdFormat>Ve <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> isteğe bağlıdır, ancak örneğin farklı .NET çalışma zamanı sürümlerinde benzer bir çıkış ürettiğinden emin olur.</span><span class="sxs-lookup"><span data-stu-id="26167-154">Setting <xref:System.Diagnostics.Activity.DefaultIdFormat> and <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> is optional but helps ensure the sample produces similar output on different .NET runtime versions.</span></span> <span data-ttu-id="26167-155">.NET 5, varsayılan olarak W3C TraceContext ID biçimini kullanır, ancak önceki .NET sürümleri varsayılan olarak <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> kimlik biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="26167-155">.NET 5 uses the W3C TraceContext ID format by default but earlier .NET versions default to using <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID format.</span></span> <span data-ttu-id="26167-156">Daha fazla ayrıntı için bkz. [etkinlik kimlikleri](distributed-tracing-concepts.md#activity-ids) .</span><span class="sxs-lookup"><span data-stu-id="26167-156">See [Activity IDs](distributed-tracing-concepts.md#activity-ids) for more details.</span></span>

<span data-ttu-id="26167-157"><xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> , bir etkinliğin ömrü boyunca geri çağırmaları almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26167-157"><xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> is used to receive callbacks during the lifetime of an Activity.</span></span>

- <span data-ttu-id="26167-158"><xref:System.Diagnostics.ActivityListener.ShouldListenTo> -Her etkinlik, ad alanı ve üreticisi olarak davranan bir ActivitySource ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="26167-158"><xref:System.Diagnostics.ActivityListener.ShouldListenTo> - Each Activity is associated with an ActivitySource which acts as its namespace and producer.</span></span>
<span data-ttu-id="26167-159">Bu geri çağırma, işlemdeki her ActivitySource için bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26167-159">This callback is invoked once for each ActivitySource in the process.</span></span> <span data-ttu-id="26167-160">Örnekleme gerçekleştirmeyi veya bu kaynak tarafından üretilen etkinliklere yönelik başlatma/durdurma olayları hakkında bildirim almak istiyorsanız true döndürün.</span><span class="sxs-lookup"><span data-stu-id="26167-160">Return true if you are interested in performing sampling or being notified about start/stop events for Activities produced by this source.</span></span>
- <span data-ttu-id="26167-161"><xref:System.Diagnostics.ActivityListener.Sample> - <xref:System.Diagnostics.ActivitySource.StartActivity%2A> Bazı ActivityListener örneklenmeyeceğini belirtmedikçe, varsayılan olarak bir etkinlik nesnesi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="26167-161"><xref:System.Diagnostics.ActivityListener.Sample> - By default <xref:System.Diagnostics.ActivitySource.StartActivity%2A> does not create an Activity object unless some ActivityListener indicates it should be sampled.</span></span> <span data-ttu-id="26167-162">Mektir <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded></span><span class="sxs-lookup"><span data-stu-id="26167-162">Returning <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded></span></span>
<span data-ttu-id="26167-163">Etkinliğin oluşturulması gerektiğini, <xref:System.Diagnostics.Activity.IsAllDataRequested> true olarak ayarlanması gerektiğini ve <xref:System.Diagnostics.Activity.ActivityTraceFlags> <xref:System.Diagnostics.ActivityTraceFlags.Recorded> bayrağın ayarlanmış olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26167-163">indicates that the Activity should be created, <xref:System.Diagnostics.Activity.IsAllDataRequested> should be set to true, and <xref:System.Diagnostics.Activity.ActivityTraceFlags> will have the <xref:System.Diagnostics.ActivityTraceFlags.Recorded> flag set.</span></span> <span data-ttu-id="26167-164">Iallldatarequary, bir dinleyicinin Etiketler ve olaylar gibi çok sayıda etkinlik bilgisinin doldurulduğundan emin olmak istediği bir ipucu olarak, belgelenmiş kodla gözlemlenebilir.</span><span class="sxs-lookup"><span data-stu-id="26167-164">IsAllDataRequested can be observed by the instrumented code as a hint that a listener wants to ensure that auxilliary Activity information such as Tags and Events are populated.</span></span>
<span data-ttu-id="26167-165">Kaydedilen bayrak W3C TraceContext KIMLIĞINDE kodlanır ve bu izlemenin örneklendiği dağıtılmış izlemede yer alan diğer işlemlere yönelik bir ipucu olur.</span><span class="sxs-lookup"><span data-stu-id="26167-165">The Recorded flag is encoded in the W3C TraceContext ID and is a hint to other processes involved in the distributed trace that this trace should be sampled.</span></span>
- <span data-ttu-id="26167-166"><xref:System.Diagnostics.ActivityListener.ActivityStarted> ve <xref:System.Diagnostics.ActivityListener.ActivityStopped> sırasıyla bir etkinlik başlatıldığında ve durdurulduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26167-166"><xref:System.Diagnostics.ActivityListener.ActivityStarted> and <xref:System.Diagnostics.ActivityListener.ActivityStopped> are called when an Activity is started and stopped respectively.</span></span> <span data-ttu-id="26167-167">Bu geri çağrılar, etkinlik veya değişiklik için olası bilgileri kaydetmek üzere bir oportunity sağlar.</span><span class="sxs-lookup"><span data-stu-id="26167-167">These callbacks provide an oportunity to record relevant information about the Activity or potentially to modify it.</span></span>
<span data-ttu-id="26167-168">Bir etkinlik, verilerin büyük bölümü hala tamamlanmamış olabilir ve etkinlik durdurulmadan önce doldurulur.</span><span class="sxs-lookup"><span data-stu-id="26167-168">When an Activity has just started much of the data may still be incomplete and it will be populated before the Activity stops.</span></span>

<span data-ttu-id="26167-169">Bir ActivityListener oluşturulduktan ve geri çağrılar doldurulduktan sonra, çağırma <xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="26167-169">Once an ActivityListener has been created and the callbacks are populated, calling <xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType></span></span>
<span data-ttu-id="26167-170">geri çağırmaları çağırma işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="26167-170">initiates invoking the callbacks.</span></span> <span data-ttu-id="26167-171"><xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType>Geri çağırmaların akışını durdurmak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="26167-171">Call <xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType> to stop the flow of callbacks.</span></span> <span data-ttu-id="26167-172">Dispose () çalışırken çok iş parçacıklı kod geri çağırma bildirimlerinin devam ettiğini ve geri dönmesinin ardından çok kısa sürede alındığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="26167-172">Beware that in multi-threaded code callback notifications in progress could be received while Dispose() is running or even very shortly after it has returned.</span></span>
