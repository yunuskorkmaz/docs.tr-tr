---
title: Dağıtılmış izleme-.NET
description: .NET dağıtılmış izleme 'ye giriş.
ms.date: 02/02/2021
ms.openlocfilehash: 573f749d7c3253499b6d01f5ba927dfa015e66a8
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99551574"
---
# <a name="net-distributed-tracing"></a>.NET dağıtılmış Izleme

Dağıtılmış izleme, dağıtılmış bir sistemde izleme verilerini yayımlama ve gözlemlemeye yönelik bir yoldur.
.NET Framework ve .NET Core, API 'leri kullanarak izlemeyi destekliyor <xref:System.Diagnostics> .

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType> Tanılama bağlamının depolanmasına ve bunlara erişilmesine ve günlük sistemiyle kullanılmasına izin veren sınıf.
- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> Bu, izlenen işlem dahilinde tüketim için zengin veri yükleri üretim zamanı günlüğü için kodun değiştirilmesine izin verir.

HTTP gelen isteklerden izleme verilerinin nasıl yayımlanacağını gösteren bir örnek aşağıda verilmiştir:

```csharp
   public void OnIncomingRequest(DiagnosticListener httpListener, HttpContext context)
   {
       if (httpListener.IsEnabled("Http_In"))
       {
           var activity = new Activity("Http_In");

           //add tags, baggage, etc.
           activity.SetParentId(context.Request.headers["Request-id"])
           foreach (var pair in context.Request.Headers["Correlation-Context"])
           {
               var baggageItem = NameValueHeaderValue.Parse(pair);
               activity.AddBaggage(baggageItem.Key, baggageItem.Value);
           }
           httpListener.StartActivity(activity, new { context });
           try
           {
               //process request ...
           }
           finally
           {
               //stop activity
               httpListener.StopActivity(activity, new {context} );
           }
       }
   }
```

Etkinlik olaylarını dinlemek için örnek aşağıda verilmiştir:

```csharp
    DiagnosticListener.AllListeners.Subscribe(delegate (DiagnosticListener listener)
    {
        if (listener.Name == "MyActivitySource")
        {
            listener.Subscribe(delegate (KeyValuePair<string, object> value)
            {
                if (value.Key.EndsWith("Start", StringComparison.Ordinal))
                    LogActivityStart();
                else if (value.Key.EndsWith("Stop", StringComparison.Ordinal))
                    LogActivityStop();
            });
        }
    }
```

.NET 5,0, [Opentelemetri](https://opentelemetry.io/) izleme senaryolarına izin vermek, örnekleme özellikleri eklemek, izleme kodlama düzeninin basitleştirilmesi ve etkinlik olaylarını dinlemeyi daha kolay ve esnek hale getirmeye yönelik dağıtılmış izlemenin özelliğini genişletti.

> [!NOTE]
> Tüm eklenen .NET 5,0 özelliklerine erişmek için [System. Diagnostics. DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet paketi sürüm 5,0 veya sonraki bir sürüme başvurulduğundan emin olun. Bu paket, .NET Framework, .NET Core ve .NET Standard desteklenen sürümlerini hedefleyen kitaplıklarda ve uygulamalarda kullanılabilir. .NET 5,0 veya üstünü hedefliyorsanız, .NET SDK ile yüklenen paylaşılan kitaplıkta yer aldığı için pakete el ile başvurulmasına gerek yoktur.

## <a name="getting-started-with-tracing"></a>Izlemeye Başlarken

Uygulamalar ve kitaplıklar yalnızca ve sınıflarını kullanarak izleme verilerini kolayca yayımlayabilir <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> <xref:System.Diagnostics.Activity?displayProperty=nameWithType> .

### <a name="activitysource"></a>Etkinlik kaynağı

İzleme verilerini yayımlamanın ilk adımı, ActivitySource sınıfının örneğini oluşturmaktır. ActivitySource sınıfı, etkinlik nesnelerinin oluşturulması ve başlatılması ve etkinlik olaylarını dinlemek için ActivityListener nesnelerinin kaydedilmesi için API 'Ler sağlar.

```csharp
    internal static ActivitySource source = new ActivitySource("MyCompany.MyComponent.SourceName", "v1");
```

#### <a name="best-practices"></a>En İyi Uygulamalar

- ActivitySource 'u bir kez oluşturun ve statik bir değişkende depolayın ve bu örneği gereken sürece kullanın.

- Oluşturucuya geçirilen kaynak adı, diğer kaynaklarla çakışmalardan kaçınmak için benzersiz olmalıdır. Hiyerarşik ad kullanılması önerilir; parçalar, şirket adı, bileşen adı ve kaynak adı bulunur. Örneğin, `Microsoft.System.HttpClient.HttpInOutRequests`.

- Sürüm parametresi isteğe bağlıdır. Büyük/küçük harf planının, kitaplığın veya uygulamanın birden çok sürümünü serbest bırakmak ve farklı sürümlerin kaynakları arasında ayrım yapmak için sürümü sağlamanız önerilir.

### <a name="activity-creation"></a>Etkinlik oluşturma

Şimdi oluşturulan ActivitySource nesnesi, koddaki istenen yerlerde tüm izleme verilerini günlüğe kaydetmek için kullanılan etkinlik nesneleri oluşturmak ve başlatmak için kullanılabilir.

```csharp
        using (Activity activity = source.StartActivity("OperationName"))
        {
            // Do something

            activity?.AddTag("key", "value"); // log the tracing
        }
```

Bu örnek kod, etkinlik nesnesini oluşturmayı ve sonra bazı izleme etiketlerini ve günlüğünü günlüğe kaydetmek için çalışır `key` `value` .

#### <a name="notes"></a>Notlar

- `ActivitySource.StartActivity` aynı anda etkinlik oluşturup başlatmaya çalışır. Listelenen kod stili, `using` bloğu yürüttükten sonra oluşturulan etkinlik nesnesini otomatik olarak atıyen bloğu kullanıyor. Etkinlik nesnesini elden atma, bu başlatılan etkinliği durdurur ve kodun açık etkinliğini açıkça durdurması gerekmez. Kodlama modelini basitleştirecek

- `ActivitySource.StartActivity` Bu tür olaylara herhangi bir dinleyici varsa dahili olarak bir şekilde öğrenin. Kayıtlı bir dinleyici yoksa veya böyle bir olayla ilgilenmeyecek bir dinleyici varsa, `ActivitySource.StartActivity` `null` nesne döndürür ve etkinlik nesnesi oluşturmaktan kaçınılmasını sağlar. Bunun nedeni, kodun ifadesinde null yapılabilir işlecini kullanmasının neden olduğunu `?` `activity?.AddTag` . Genel olarak, bloğun içinde `using` , `?` etkinlik nesnesi adından sonra her zaman Nullable işlecini kullanın.

## <a name="listening-to-the-activity-events"></a>Etkinlik olaylarını dinleme

.NET, <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> bir veya daha fazla ActivitySource 'tan tetiklenen etkinlik olaylarını dinlemek için kullanılabilecek sınıfı sağlar.
Dinleyici, izleme verilerini toplama, örnekleme veya etkinlik nesnesinin oluşturulmasını zorlama için kullanılabilir.

`ActivityListener`Sınıfı, farklı olayları işlemek için farklı geri çağrılar sağlar.

```csharp

ActivityListener listener = new ActivityListener()

ShouldListenTo = (activitySource) => object.ReferenceEquals(source, activitySource),
ActivityStarted = activity => /* Handle the Activity start event here */ DoSomething(),
ActivityStopped = activity => /* Handle the Activity stop event here */ DoSomething(),
SampleUsingParentId = (ref ActivityCreationOptions<string> activityOptions) => ActivitySamplingResult.AllData,
Sample = (ref ActivityCreationOptions<ActivityContext> activityOptions) => ActivitySamplingResult.AllData

// Enable the listener
ActivitySource.AddActivityListener(listener);
```

- `ShouldListenTo` belirli bir nesneye dinlemeyi sağlar `ActivitySource` . Örnekte, `ActivitySource` daha önce oluşturduğumuz nesneyi dinlemeyi sağlar. `ActivitySource`Girişin ve girişini denetleyerek diğer nesneleri dinlemek için daha fazla esneklik vardır `Name` `Version` `ActivitySource` .

- `ActivityStarted` ve `ActivityStopped` `Activity` `Activity` `ActivitySource` geri çağırma tarafından dinlemek üzere etkinleştirilen nesneler tarafından oluşturulan tüm nesneler için başlatma ve durdurma olaylarını almayı etkinleştirin `ShouldListenTo` .

- `Sample` ve `SampleUsingParentId` örnekleme için tasarlanan ana geri aramalardır. Bu iki geri çağırmalar, `ActivitySamplingResult` Geçerli oluşturma isteğinin örneğine veya dışına örnek olarak söylenebilen enum değerini döndürür `Activity` . Geri çağırma geri döner `ActivitySamplingResult.None` ve diğer etkin bir dinleyici farklı bir değer döndürmediğinde, etkinlik WIL oluşturulmaz ve `ActivitySource.StartActivity` döndürür `null` . Aksi takdirde, `Activity` nesne oluşturulur.

## <a name="net-50-new-features"></a>.NET 5,0 yeni özellikler

For etmek beklemeniz `Activity` sınıfı, izleme ana senaryolarını destekliyor. Anahtar-değer çiftleri olan izleme verilerinin bulunduğu etiketlerin çapraz olmasına izin verilir. Bu, hat genelinde yayılmakta tasarlanan anahtar-değer etiketleri olan Baggleri destekliyordu.

.NET 5,0, genellikle Opentelemetri senaryolarını etkinleştirmek için daha fazla özelliği destekler.

### <a name="activitycontext"></a>ActivityContext

<xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> , izleme işlemlerinin bağlamını taşıyan bir struct (örn. İzleme kimliği, span ID, Trace bayrakları ve izleme durumu). Artık `Activity` üst izleme bağlamını sağlayan yeni bir oluşturmak mümkündür. Ayrıca, özelliği çağırarak herhangi bir nesneden izleme bağlamını ayıklamak kolaydır `Activity` `Activity.Context` .

### <a name="activitylink"></a>Etkinlik bağlantısı

<xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> , izleme bağlam örneğini içeren ve casuon ile ilgili nesneye bağlanabilen struct `Activity` . `Activity`Oluşturma sırasında bağlantı listesini yöntemine geçirerek bağlantılar nesnesine eklenebilir `ActivitySource.StartActivity` `Activity` . Tüm `Activity` nesne ekli bağlantıları özelliği kullanılarak alınabilir `Activity.Links` .

### <a name="activityevent"></a>ActivityEvent

<xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> ad ve zaman damgası içeren bir olayı ve isteğe bağlı etiket listesini temsil eder. Olaylar, `Activity` metodu çağırarak nesnesine eklenebilir `Activity.AddEvent` . `Activity`Nesne olaylarının tam listesi, özelliği kullanılarak alınabilir `Activity.Events` .

### <a name="activitykind"></a>Etkinlik türü

<xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> etkinlik, üst öğeleri ve bir izlemede alt öğeleri arasındaki ilişkiyi açıklar. Türü `Activity` , oluşturulurken tür değeri yöntemine geçirerek nesnesine ayarlanabilir `ActivitySource.StartActivity` `Activity` . `Activity`Nesne türü, özelliği kullanılarak alınabilir `Activity.Kind` .

### <a name="isalldatarequested"></a>Isalldatareşitlenmiş

<xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> Bu etkinliğin tüm yayma bilgileriyle doldurulmasının yanı sıra bağlantılar, Etiketler ve olaylar gibi diğer tüm özellikleri içerip içermediğini gösterir. Değeri, `IsAllDataRequested` Tüm dinleyicilerinin `Sample` ve `SampleUsingParentId` geri çağırmaların döndürdüğü sonuçtan belirlenir. Değer, özelliği kullanılarak alınabilir `Activity.IsAllDataRequested` .

### <a name="activitysource"></a>Activity. Source

<xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> Bu etkinlikle ilişkili etkinlik kaynağını alır.

### <a name="activitydisplayname"></a>Activity. DisplayName

<xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> etkinliğin bir görünen adını almaya veya ayarlamaya izin verir.

### <a name="activitytagobjects"></a>Activity. TagObjects

`Activity` sınıfı, `Activity.Tags` anahtar ve değer için dize türü etiketlerinin anahtar-değer çifti listesini döndüren özelliğine sahiptir. Bu tür Etiketler, `Activity` yöntemi kullanılarak öğesine eklenebilir `AddTag(string, string)` . `Activity` , `AddTag(string, object)` bir tür değere sahip olmasını sağlayan aşırı yüklenmiş yöntemi sağlayarak etiketlerin desteğini genişletmiştir.  Bu tür etiketlerin tamamen listesi kullanılarak alınabilir <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType> .

## <a name="sampling"></a>Örnekleme

Örnekleme, toplanan ve arka uca gönderilen izlemelerin örnek sayısını azaltarak paraziti ve yükünü denetlemek için bir mekanizmadır. Örnekleme, önemli bir Opentelemetri senaryosudur. .NET 5,0 ' de örnekleme yapmak kolaydır. İyi bir uygulama kullanarak yeni nesneleri oluşturur `Activity` `ActivitySource.StartActivity` ve tüm olası kullanılabilir verileri (örneğin, Etiketler, tür, bağlantılar,...) sağlamayı deneyin. vb.) Bu yöntem çağrılırken. Verilerin sağlanması, ' i kullanarak uygulanan örnekleyicilerin `ActivityListener` doğru örnekleme kararına sahip olmasını sağlayacaktır. Nesneyi oluşturmadan önce verilerin oluşturulmasını önlemek için performans önemliyse `Activity` , `ActivitySource.HasListeners` gerekli verileri oluşturmadan önce herhangi bir dinleyici olup olmadığını denetlemek yararlı olur.

## <a name="opentelemetry"></a>OpenTelemetry

Opentelemetri SDK 'Sı, uçtan uca dağıtılmış izleme senaryolarını destekleyen birçok özellik ile gelir. Aralarından seçim yapabileceğiniz birden fazla örnekleyiciler ve dışarı vericiler sağlar. Özel örnekleyiciler ve dışarı vericiler da oluşturulmasına olanak sağlar.

Opentelemetri, toplanan izleme verilerinin farklı arka uçlara verilmesini destekler (örneğin, Jaeger, Zipkaya, yeni relik,...) vb.). Daha fazla ayrıntı için [Opentelemetri-DotNet](https://github.com/open-telemetry/opentelemetry-dotnet/) adresine başvurun ve paketler için arama NuGet.org `OpenTelemetry.Exporter.` , dışarı aktarma paketleri listesini almak üzere ile başlar.

Aşağıda, izleme verilerinin konsola ne kadar kolay örnek ve dışarı aktarılacağı hakkında [Opentelemetri-DotNet ile başlayan](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) örnek bir kod verilmiştir.

```csharp
// <copyright file="Program.cs" company="OpenTelemetry Authors">
// Copyright The OpenTelemetry Authors
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
// </copyright>

using System.Diagnostics;
using OpenTelemetry;
using OpenTelemetry.Trace;

public class Program
{
    private static readonly ActivitySource MyActivitySource = new ActivitySource(
        "MyCompany.MyProduct.MyLibrary");

    public static void Main()
    {
        using var tracerProvider = Sdk.CreateTracerProviderBuilder()
            .SetSampler(new AlwaysOnSampler())
            .AddSource("MyCompany.MyProduct.MyLibrary")
            .AddConsoleExporter()
            .Build();

        using (var activity = MyActivitySource.StartActivity("SayHello"))
        {
            activity?.SetTag("foo", 1);
            activity?.SetTag("bar", "Hello, World!");
            activity?.SetTag("baz", new int[] { 1, 2, 3 });
        }
    }
}
```

Örneğin [Opentelemetri. dışarı aktarma. Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2)paketine başvurması gerekiyor.
