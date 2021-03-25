---
title: Dağıtılmış izleme araçları ekleme-.NET
description: .NET uygulamalarında dağıtılmış izlemeleri işaretlemek için bir öğretici
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: eeb065d1ac39dd34d9b27e2ad63195818d0d6493
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111574"
---
# <a name="adding-distributed-tracing-instrumentation"></a>Dağıtılmış izleme araçları ekleme

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 2,1 ve üzeri sürümleri **ve** .NET Framework 4,5 ve sonraki sürümler

.NET uygulamaları, <xref:System.Diagnostics.Activity?displayProperty=nameWithType> Dağıtılmış izleme telemetrisi oluşturmak için API kullanılarak değiştirilebilir. Bazı araçlar standart .NET kitaplıklarında yerleşik olarak bulunur, ancak kodunuzun daha kolay diagnosable sağlamak için daha fazla eklemek isteyebilirsiniz. Bu öğreticide, yeni özel dağıtılmış izleme araçları ekleyeceksiniz. Bu izleme tarafından üretilen Telemetriyi kaydetme hakkında daha fazla bilgi edinmek için [koleksiyon öğreticisine](distributed-tracing-instrumentation-walkthroughs.md) bakın.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet) veya sonraki bir sürümü

## <a name="an-initial-app"></a>İlk uygulama

İlk olarak, Opentelemetri kullanarak telemetri toplayan, ancak henüz hiç izleme olmayan bir örnek uygulama oluşturacaksınız.

```dotnetcli
dotnet new console
```

.NET 5 ve üstünü hedefleyen uygulamalar, gereken dağıtılmış izleme API 'Lerini zaten içeriyor. Eski .NET sürümlerini hedefleyen uygulamalar için [System. Diagnostics. DiagnosticSource NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) sürüm 5 veya üstünü ekleyin.

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

Telemetriyi toplamak için kullanılacak [opentelemetri](https://www.nuget.org/packages/OpenTelemetry/) ve [opentelemetri. ctelemetriyi](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) ekleyin.

```dotnetcli
dotnet add package OpenTelemetry
dotnet add package OpenTelemetry.Exporter.Console
```

Oluşturulan program. cs içeriğini bu örnek kaynakla değiştirin:

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static async Task Main(string[] args)
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork("banana", 8);
            Console.WriteLine("Example work done");
        }

        // All the functions below simulate doing some arbitrary work
        static async Task DoSomeWork(string foo, int bar)
        {
            await StepOne();
            await StepTwo();
        }

        static async Task StepOne()
        {
            await Task.Delay(500);
        }

        static async Task StepTwo()
        {
            await Task.Delay(1000);
        }
    }
}
```

Uygulamanın henüz bir izleme yok, bu nedenle görüntülenecek izleme bilgisi yok:

```dotnetcli
> dotnet run
Example work done
```

#### <a name="best-practices"></a>En İyi Uygulamalar

Yalnızca uygulama geliştiricilerinin, bu örnekteki Opentelemetri gibi dağıtılmış izleme telemetrisini toplamak için isteğe bağlı bir 3. taraf kitaplığına başvurması gerekir. .NET kitaplığı yazarları, .NET çalışma zamanının parçası olan System. Diagnostics. DiagnosticSource içindeki API 'Lere özel olarak güvenir. Bu, kitaplıkların hangi kitaplık veya satıcının telemetri toplamak için kullanılacağı konusunda ne olursa olsun, kitaplıkların çok çeşitli .NET uygulamalarında çalışmasını sağlar.

## <a name="adding-basic-instrumentation"></a>Temel Izleme ekleme

Uygulamalar ve kitaplıklar, ve sınıflarını kullanarak dağıtılmış izleme araçları ekler <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> <xref:System.Diagnostics.Activity?displayProperty=nameWithType> .

### <a name="activitysource"></a>Etkinlik kaynağı

Önce ActivitySource örneğini oluşturun. ActivitySource, etkinlik nesneleri oluşturmak ve başlatmak için API 'Ler sağlar. Main () ve using ifadelerine statik ActivitySource değişkenini ekleyin `using System.Diagnostics;` .

```csharp
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        private static ActivitySource source = new ActivitySource("Sample.DistributedTracing", "1.0.0");

        static async Task Main(string[] args)
        {
            ...    
```

#### <a name="best-practices"></a>En İyi Uygulamalar

- ActivitySource 'u bir kez oluşturun, bir statik değişkende depolayın ve bu örneği gereken sürece kullanın.
Her kitaplık veya kitaplık alt bileşeni kendi kaynağını oluşturabilir (ve genellikle). Uygulama geliştiricilerinin, kaynaklardaki etkinlik telemetrisini bağımsız olarak etkinleştirebilmekte ve devre dışı bırakacağından, mevcut olanı yeniden kullanmak yerine yeni bir kaynak oluşturmayı düşünün.

- Oluşturucuya geçirilen kaynak adı, diğer kaynaklarla çakışmalardan kaçınmak için benzersiz olmalıdır.
Aynı derlemede birden fazla kaynak varsa, derleme adı ve isteğe bağlı olarak bir bileşen adı içeren hiyerarşik bir ad kullanılması önerilir. Örneğin, `Microsoft.AspNetCore.Hosting`. Bir derleme, 2. bağımsız bir derlemede kod için izleme ekliyor ise, bu ad kodu izlenmekte olan derlemeyi değil, ActivitySource tanımlayan derlemeye dayalı olmalıdır.

- Sürüm parametresi isteğe bağlıdır. Kitaplığın birden çok sürümünü serbest bırakmanız ve belgelenmiş telemetride değişiklikler yapmanız durumunda sürümü sağlamanız önerilir.

> [!NOTE]
> Opentelemetri, ' Izleyici ' ve ' span ' diğer terimlerini kullanır. .NET ' ActivitySource ' içinde, Izleyici ve etkinliğin uygulanması ' span ' uygulamasıdır. . NET ' in etkinlik türü uzun ön tarihleri Opentelemetri belirtimi ve özgün .NET adlandırma, .NET ekosistemi ve .NET uygulama uyumluluğu dahilinde tutarlılık için korundu.

### <a name="activity-creation"></a>Etkinlik oluşturma

Etkinlik nesnelerini anlamlı iş birimleri etrafında başlatmak ve durdurmak için ActivitySource nesnesini kullanın. DoSomeWork () öğesini burada gösterilen kodla güncelleştirin:

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }
```

Uygulamayı çalıştırmak artık günlüğe kaydedilen yeni etkinliği gösterir:

```dotnetcli
> dotnet run
Activity.Id:          00-f443e487a4998c41a6fd6fe88bae644e-5b7253de08ed474f-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:36:51.4720202Z
Activity.Duration:    00:00:01.5025842
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 067f4bb5-a5a8-4898-a288-dec569d6dbef
```

#### <a name="notes"></a>Notlar

- <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> aynı anda etkinlik oluşturur ve başlatır. Listelenen kod stili, `using` bloğu yürüttükten sonra oluşturulan etkinlik nesnesini otomatik olarak ortadan kaldırın bloğunu kullanıyor. Etkinlik nesnesini elden atılırken kodun açıkça çağrılması için bu işlem durdurulur <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType> .
Bu, kodlama modelini basitleştirir.

- <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> , etkinliği kaydeden bir dinleyici olup olmadığını dahili olarak belirler. Kayıtlı bir dinleyici yoksa veya ilgilenmiyor olan dinleyiciler varsa, StartActivity () geri dönerek `null` etkinlik nesnesi oluşturmaktan kaçınacaktır. Bu, kod düzeninin çok sık çağrılan işlevlerde hala kullanılabilmesi için bir performans iyileştirmesidir.

## <a name="optional-populate-tags"></a>İsteğe bağlı: etiketleri doldur

Etkinlikler, genellikle Tanılama için faydalı olabilecek iş parametrelerini depolamak için kullanılan Etiketler adlı anahtar-değer verilerini destekler. DoSomeWork () öğesini bunları içerecek şekilde güncelleştirin:

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                await StepTwo();
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-2b56072db8cb5a4496a4bfb69f46aa06-7bc4acda3b9cce4d-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:37:31.4949570Z
Activity.Duration:    00:00:01.5417719
Activity.TagObjects:
    foo: banana
    bar: 8
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 25bbc1c3-2de5-48d9-9333-062377fea49c

Example work done
```

#### <a name="best-practices"></a>En İyi Uygulamalar

- Yukarıda belirtildiği gibi, `activity` tarafından döndürülen <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> null olabilir. Null-coallescing işleci?. C# ' de, yalnızca <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> etkinliğin null olmaması durumunda çağırmak için kullanışlı bir kısa süreli. Bu davranış yazma ile aynıdır:

```csharp
if(activity != null)
{
    activity.SetTag("foo", foo);
}
```

- Opentelemetri, uygulama işinin ortak türlerini temsil eden etkinliklerde Etiketler ayarlamak için önerilen bir [kurallar](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions) kümesi sağlar.

- İşlevleri yüksek performans gereksinimleriyle belirlerseniz, <xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> etkinlikleri dinleyen kodların herhangi birinin Etiketler gibi ikincil bilgileri okumayı amaçladığı bir ipucu olup olmadığını belirten bir ipucu vardır. Hiçbir dinleyici okunmaz, izlenen kodun, CPU döngülerini doldurmasına gerek kalmaz. Basitlik için bu örnek, bu iyileştirmesi uygulamaz.

## <a name="optional-adding-events"></a>İsteğe bağlı: olayları ekleme

Olaylar, etkinliklere ek tanılama verilerinin rastgele bir akışını iliştirebilmek için zaman damgamış iletilerdir. Etkinliğe bazı olaylar ekleyin:

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-82cf6ea92661b84d9fd881731741d04e-33fff2835a03c041-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:39:10.6902609Z
Activity.Duration:    00:00:01.5147582
Activity.TagObjects:
    foo: banana
    bar: 8
Activity.Events:
    Part way there [3/18/2021 10:39:11 AM +00:00]
    Done now [3/18/2021 10:39:12 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: ea7f0fcb-3673-48e0-b6ce-e4af5a86ce4f

Example work done
```

#### <a name="best-practices"></a>En İyi Uygulamalar

- Olaylar, bu mekanizmayı yalnızca bir ila büyüklükteki sayısını kaydetmek için uygun hale getiren, bir bellek içi listede depolanır. Bu görevde odaklanmış bir günlüğe kaydetme API 'SI kullanan büyük veya sınırsız miktarda olay için, [ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) gibi daha iyi bir seçimdir. ILogger Ayrıca, uygulama geliştiricisinin dağıtılmış izlemeyi kullanmasına bakılmaksızın günlüğe kaydetme bilgilerinin kullanılabilir olmasını sağlar.
ILogger, etkin etkinlik kimliklerinin otomatik olarak yakalanmasını destekler, böylece bu API ile günlüğe kaydedilen iletiler yine de Dağıtılmış izleme ile bağıntılı olabilir.

## <a name="optional-adding-status"></a>İsteğe bağlı: durum ekleme

Opentelemetri, her etkinliğin işin geçiş/başarısız sonucunu temsil eden bir [durum](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status) rapormasına olanak tanır. .NET şu anda bu amaçla kesin türü belirtilmiş bir API 'ye sahip değildir ancak Etiketler kullanılarak oluşturulmuş bir kural vardır:

- `otel.status_code` , depolamak için kullanılan etiket adıdır `StatusCode` . StatusCode etiketinin değerleri, "UNSET", "OK" veya "ERROR" dizelerinden biri olmalıdır ve numaralandırmalar, ve durum kodu için sırasıyla buna karşılık `Unset` gelir `Ok` `Error` .
- `otel.status_description` , isteğe bağlı olarak depolamak için kullanılan etiket adıdır `Description`

Şu durumu ayarlamak için DoSomeWork () öğesini güncelleştirin:

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
                
                // Pretend something went wrong
                activity?.SetTag("otel.status_code", "ERROR");
                activity?.SetTag("otel.status_description", "Use this text give more information about the error");
            }
        }
```

## <a name="optional-add-additional-activities"></a>İsteğe bağlı: ek etkinlikler ekleme

Etkinlikler, daha büyük bir iş biriminin bölümlerini betimleyen iç içe olabilir. Bu, özellikle, belirli dış bağımlılıklardan gelen hızlı bir şekilde yürütülemeyebilir veya daha iyi yerelleştirilmesine izin veren kod bölümlerinin etrafında yararlı olabilir. Bu örnek her yöntemde bir etkinlik kullansa da yalnızca ek kod simge durumuna küçültülmüş olabilir. Her yöntemde etkinlik kullanan daha büyük ve daha gerçekçi bir projede, önerilmez.

Bu ayrı adımların etrafında daha fazla izleme eklemek için StepOne ve StepTwo güncelleştirin:

```csharp
        static async Task StepOne()
        {
            using (Activity activity = source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity activity = source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-39cac574e8fda44b-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4278822Z
Activity.Duration:    00:00:00.5051364
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-4ccccb6efdc59546-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.9441095Z
Activity.Duration:    00:00:01.0052729
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4256627Z
Activity.Duration:    00:00:01.5286408
Activity.TagObjects:
    foo: banana
    bar: 8
    otel.status_code: ERROR
    otel.status_description: Use this text give more information about the error
Activity.Events:
    Part way there [3/18/2021 10:40:51 AM +00:00]
    Done now [3/18/2021 10:40:52 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Example work done
```

Her iki StepOne ve StepTwo, SomeWork 'e başvuran bir parentID içerir. Konsol, iç içe geçmiş iş ağaçlarının harika bir görselleştirmesi değildir, ancak [zipa](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md) gıbı birçok GUI Görüntüleyici bunu bir Gantt grafiği olarak gösterebilir:

[![Zipkaya Gantt grafiği](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)

### <a name="optional-activitykind"></a>İsteğe bağlı: ActivityKind

Etkinlikler <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType> , etkinlik, üst ve alt öğeleri arasındaki ilişkiyi açıklayan bir özelliğe sahiptir. Varsayılan olarak, tüm yeni etkinlikler, <xref:System.Diagnostics.ActivityKind.Internal> uzak üst veya alt öğeleri olmayan bir uygulama içinde iç işlem olan etkinliklere uygun olarak ayarlanır. Diğer türleri üzerinde tür parametresi kullanılarak ayarlanabilir <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> . <xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType>Diğer seçenekler için bkz..

### <a name="optional-links"></a>İsteğe bağlı: bağlantılar

Toplu işlem sistemlerinde iş gerçekleştiğinde tek bir etkinlik, her birinin kendi izleme kimliği olan aynı anda birçok farklı istek adına işi temsil edebilir. Etkinlik tek bir üst öğeye sahip olacak şekilde kısıtlanmış olsa da, kullanarak ek izleme kimliklerine bağlanabilir <xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> . Her ActivityLink, <xref:System.Diagnostics.ActivityContext> bağlanmakta olan etkinlik HAKKıNDAKI kimlik bilgilerini depolayan bir ile doldurulur. ActivityContext, kullanarak işlem içi etkinlik nesnelerinden alınabilir <xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> veya kullanılarak serileştirilmiş kimlik bilgileri ayrıştırılabilir <xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType> .

```csharp
void DoBatchWork(ActivityContext[] requestContexts)
{
    // Assume each context in requestContexts encodes the trace-id that was sent with a request
    using(Activity activity = s_source.StartActivity(name: "BigBatchOfWork",
                                                     kind: ActivityKind.Internal,
                                                     parentContext: null,
                                                     links: requestContexts.Select(ctx => new ActivityLink(ctx))
    {
        // do the batch of work here
    }
}
```

İsteğe bağlı eklenebilen olayların ve etiketlerin aksine, StartActivity () sırasında bağlantıların eklenmesi ve daha sonra sabit olmaları gerekir.
