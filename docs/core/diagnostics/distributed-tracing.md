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
# <a name="net-distributed-tracing"></a><span data-ttu-id="9bae7-103">.NET dağıtılmış Izleme</span><span class="sxs-lookup"><span data-stu-id="9bae7-103">.NET Distributed Tracing</span></span>

<span data-ttu-id="9bae7-104">Dağıtılmış izleme, dağıtılmış bir sistemde izleme verilerini yayımlama ve gözlemlemeye yönelik bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="9bae7-104">Distributed tracing is the way to publish and observe the tracing data in a distributed system.</span></span>
<span data-ttu-id="9bae7-105">.NET Framework ve .NET Core, API 'leri kullanarak izlemeyi destekliyor <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="9bae7-105">.NET Framework and .NET Core has been supporting tracing through the <xref:System.Diagnostics> APIs.</span></span>

- <span data-ttu-id="9bae7-106"><xref:System.Diagnostics.Activity?displayProperty=nameWithType> Tanılama bağlamının depolanmasına ve bunlara erişilmesine ve günlük sistemiyle kullanılmasına izin veren sınıf.</span><span class="sxs-lookup"><span data-stu-id="9bae7-106"><xref:System.Diagnostics.Activity?displayProperty=nameWithType> class which allows storing and accessing diagnostics context and consuming it with logging system.</span></span>
- <span data-ttu-id="9bae7-107"><xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> Bu, izlenen işlem dahilinde tüketim için zengin veri yükleri üretim zamanı günlüğü için kodun değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-107"><xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> that allows code to be instrumented for production-time logging of rich data payloads for consumption within the process that was instrumented.</span></span>

<span data-ttu-id="9bae7-108">HTTP gelen isteklerden izleme verilerinin nasıl yayımlanacağını gösteren bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9bae7-108">Here is an example shows how to publish tracing data from the HTTP incoming requests:</span></span>

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

<span data-ttu-id="9bae7-109">Etkinlik olaylarını dinlemek için örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9bae7-109">Here is example for how to listen to the Activity events:</span></span>

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

<span data-ttu-id="9bae7-110">.NET 5,0, [Opentelemetri](https://opentelemetry.io/) izleme senaryolarına izin vermek, örnekleme özellikleri eklemek, izleme kodlama düzeninin basitleştirilmesi ve etkinlik olaylarını dinlemeyi daha kolay ve esnek hale getirmeye yönelik dağıtılmış izlemenin özelliğini genişletti.</span><span class="sxs-lookup"><span data-stu-id="9bae7-110">.NET 5.0 has extended the capability of the distributed tracing to allow the [OpenTelemetry](https://opentelemetry.io/) tracing scenarios, added Sampling capabilities, simplified the tracing coding pattern, and made the listening to the Activity events easier and flexible.</span></span>

> [!NOTE]
> <span data-ttu-id="9bae7-111">Tüm eklenen .NET 5,0 özelliklerine erişmek için [System. Diagnostics. DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet paketi sürüm 5,0 veya sonraki bir sürüme başvurulduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9bae7-111">To access all added .NET 5.0 capabilities, ensure referencing the [System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet package version 5.0 or later.</span></span> <span data-ttu-id="9bae7-112">Bu paket, .NET Framework, .NET Core ve .NET Standard desteklenen sürümlerini hedefleyen kitaplıklarda ve uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-112">This package can be used in libraries and apps targeting any supported version of the .NET Framework, .NET Core, and .NET Standard.</span></span> <span data-ttu-id="9bae7-113">.NET 5,0 veya üstünü hedefliyorsanız, .NET SDK ile yüklenen paylaşılan kitaplıkta yer aldığı için pakete el ile başvurulmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="9bae7-113">If targeting .NET 5.0 or later, no need to manually reference the package as it is included in the shared library installed with the .NET SDK.</span></span>

## <a name="getting-started-with-tracing"></a><span data-ttu-id="9bae7-114">Izlemeye Başlarken</span><span class="sxs-lookup"><span data-stu-id="9bae7-114">Getting Started With Tracing</span></span>

<span data-ttu-id="9bae7-115">Uygulamalar ve kitaplıklar yalnızca ve sınıflarını kullanarak izleme verilerini kolayca yayımlayabilir <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> <xref:System.Diagnostics.Activity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9bae7-115">The applications and the libraries can easily publish tracing data by simply using the <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> and the <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes.</span></span>

### <a name="activitysource"></a><span data-ttu-id="9bae7-116">Etkinlik kaynağı</span><span class="sxs-lookup"><span data-stu-id="9bae7-116">ActivitySource</span></span>

<span data-ttu-id="9bae7-117">İzleme verilerini yayımlamanın ilk adımı, ActivitySource sınıfının örneğini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-117">First step to publish tracing data is to create instance of the ActivitySource class.</span></span> <span data-ttu-id="9bae7-118">ActivitySource sınıfı, etkinlik nesnelerinin oluşturulması ve başlatılması ve etkinlik olaylarını dinlemek için ActivityListener nesnelerinin kaydedilmesi için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-118">The ActivitySource is the class provides APIs to create and start Activity objects and to register ActivityListener objects to listen to the Activity events.</span></span>

```csharp
    internal static ActivitySource source = new ActivitySource("MyCompany.MyComponent.SourceName", "v1");
```

#### <a name="best-practices"></a><span data-ttu-id="9bae7-119">En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="9bae7-119">Best Practices</span></span>

- <span data-ttu-id="9bae7-120">ActivitySource 'u bir kez oluşturun ve statik bir değişkende depolayın ve bu örneği gereken sürece kullanın.</span><span class="sxs-lookup"><span data-stu-id="9bae7-120">Create the ActivitySource once and store it in a static variable and use that instance as long as needed.</span></span>

- <span data-ttu-id="9bae7-121">Oluşturucuya geçirilen kaynak adı, diğer kaynaklarla çakışmalardan kaçınmak için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-121">The source name passed to the constructor has to be unique to avoid the conflicts with any other sources.</span></span> <span data-ttu-id="9bae7-122">Hiyerarşik ad kullanılması önerilir; parçalar, şirket adı, bileşen adı ve kaynak adı bulunur.</span><span class="sxs-lookup"><span data-stu-id="9bae7-122">It is recommended to use hierarchical name contains the parts, the company name, the component name, and the source name.</span></span> <span data-ttu-id="9bae7-123">Örneğin, `Microsoft.System.HttpClient.HttpInOutRequests`.</span><span class="sxs-lookup"><span data-stu-id="9bae7-123">For example, `Microsoft.System.HttpClient.HttpInOutRequests`.</span></span>

- <span data-ttu-id="9bae7-124">Sürüm parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-124">The version parameter is optional.</span></span> <span data-ttu-id="9bae7-125">Büyük/küçük harf planının, kitaplığın veya uygulamanın birden çok sürümünü serbest bırakmak ve farklı sürümlerin kaynakları arasında ayrım yapmak için sürümü sağlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-125">It is recommended to provide the version in case plan to release multiple versions of the library or the application and want to distinguish between the sources of different versions.</span></span>

### <a name="activity-creation"></a><span data-ttu-id="9bae7-126">Etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="9bae7-126">Activity Creation</span></span>

<span data-ttu-id="9bae7-127">Şimdi oluşturulan ActivitySource nesnesi, koddaki istenen yerlerde tüm izleme verilerini günlüğe kaydetmek için kullanılan etkinlik nesneleri oluşturmak ve başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-127">Now the created ActivitySource object can be used to create and start Activity objects which used to log any tracing data in any desired places in the code.</span></span>

```csharp
        using (Activity activity = source.StartActivity("OperationName"))
        {
            // Do something

            activity?.AddTag("key", "value"); // log the tracing
        }
```

<span data-ttu-id="9bae7-128">Bu örnek kod, etkinlik nesnesini oluşturmayı ve sonra bazı izleme etiketlerini ve günlüğünü günlüğe kaydetmek için çalışır `key` `value` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-128">This sample code try to create the Activity object and then log some tracing tag `key` and `value`.</span></span>

#### <a name="notes"></a><span data-ttu-id="9bae7-129">Notlar</span><span class="sxs-lookup"><span data-stu-id="9bae7-129">Notes</span></span>

- <span data-ttu-id="9bae7-130">`ActivitySource.StartActivity` aynı anda etkinlik oluşturup başlatmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-130">`ActivitySource.StartActivity` tries to create and start the activity in same time.</span></span> <span data-ttu-id="9bae7-131">Listelenen kod stili, `using` bloğu yürüttükten sonra oluşturulan etkinlik nesnesini otomatik olarak atıyen bloğu kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="9bae7-131">The listed code pattern is using the `using` block which automatically dispose the created Activity object after executing the block.</span></span> <span data-ttu-id="9bae7-132">Etkinlik nesnesini elden atma, bu başlatılan etkinliği durdurur ve kodun açık etkinliğini açıkça durdurması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9bae7-132">Disposing the Activity object will stop this started activity and the code doesn't have to explicitly stop te activity.</span></span> <span data-ttu-id="9bae7-133">Kodlama modelini basitleştirecek</span><span class="sxs-lookup"><span data-stu-id="9bae7-133">That simplify the coding pattern</span></span>

- <span data-ttu-id="9bae7-134">`ActivitySource.StartActivity` Bu tür olaylara herhangi bir dinleyici varsa dahili olarak bir şekilde öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9bae7-134">`ActivitySource.StartActivity` internally figure out if there any listener to such events.</span></span> <span data-ttu-id="9bae7-135">Kayıtlı bir dinleyici yoksa veya böyle bir olayla ilgilenmeyecek bir dinleyici varsa, `ActivitySource.StartActivity` `null` nesne döndürür ve etkinlik nesnesi oluşturmaktan kaçınılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-135">If there is no registered listeners or there is a listeners which not interested in such event, `ActivitySource.StartActivity` simply will return `null` object and avoid creating the Activity object.</span></span> <span data-ttu-id="9bae7-136">Bunun nedeni, kodun ifadesinde null yapılabilir işlecini kullanmasının neden olduğunu `?` `activity?.AddTag` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-136">That is why the code used the nullable operator `?`  in the statement `activity?.AddTag`.</span></span> <span data-ttu-id="9bae7-137">Genel olarak, bloğun içinde `using` , `?` etkinlik nesnesi adından sonra her zaman Nullable işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9bae7-137">In general, inside the `using` block, always use the nullable operator `?` after the activity object name.</span></span>

## <a name="listening-to-the-activity-events"></a><span data-ttu-id="9bae7-138">Etkinlik olaylarını dinleme</span><span class="sxs-lookup"><span data-stu-id="9bae7-138">Listening to the Activity Events</span></span>

<span data-ttu-id="9bae7-139">.NET, <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> bir veya daha fazla ActivitySource 'tan tetiklenen etkinlik olaylarını dinlemek için kullanılabilecek sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-139">.NET provide the class <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> which can be used to listen to the Activity events triggered from one or more ActivitySource.</span></span>
<span data-ttu-id="9bae7-140">Dinleyici, izleme verilerini toplama, örnekleme veya etkinlik nesnesinin oluşturulmasını zorlama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-140">The listener can be used collecting tracing data, sampling, or forcing creating the Activity object.</span></span>

<span data-ttu-id="9bae7-141">`ActivityListener`Sınıfı, farklı olayları işlemek için farklı geri çağrılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-141">The `ActivityListener` class provides a different callbacks to handle different events.</span></span>

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

- <span data-ttu-id="9bae7-142">`ShouldListenTo` belirli bir nesneye dinlemeyi sağlar `ActivitySource` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-142">`ShouldListenTo` enables listening to a specific `ActivitySource` objects.</span></span> <span data-ttu-id="9bae7-143">Örnekte, `ActivitySource` daha önce oluşturduğumuz nesneyi dinlemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-143">In the example, it enables listening to the `ActivitySource` object we have previously created.</span></span> <span data-ttu-id="9bae7-144">`ActivitySource`Girişin ve girişini denetleyerek diğer nesneleri dinlemek için daha fazla esneklik vardır `Name` `Version` `ActivitySource` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-144">There is more flexibility to listen to any other `ActivitySource` objects by checking the `Name` and `Version` of the input `ActivitySource`.</span></span>

- <span data-ttu-id="9bae7-145">`ActivityStarted` ve `ActivityStopped` `Activity` `Activity` `ActivitySource` geri çağırma tarafından dinlemek üzere etkinleştirilen nesneler tarafından oluşturulan tüm nesneler için başlatma ve durdurma olaylarını almayı etkinleştirin `ShouldListenTo` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-145">`ActivityStarted` and `ActivityStopped` enable getting the `Activity` Start and Stop events for all `Activity` objects created by the `ActivitySource` objects which was enabled to listen to by `ShouldListenTo` callback.</span></span>

- <span data-ttu-id="9bae7-146">`Sample` ve `SampleUsingParentId` örnekleme için tasarlanan ana geri aramalardır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-146">`Sample` and `SampleUsingParentId` are the main callbacks which intended for sampling.</span></span> <span data-ttu-id="9bae7-147">Bu iki geri çağırmalar, `ActivitySamplingResult` Geçerli oluşturma isteğinin örneğine veya dışına örnek olarak söylenebilen enum değerini döndürür `Activity` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-147">These two callbacks return the `ActivitySamplingResult` enum value which can tell either to sample in or out the current `Activity` creation request.</span></span> <span data-ttu-id="9bae7-148">Geri çağırma geri döner `ActivitySamplingResult.None` ve diğer etkin bir dinleyici farklı bir değer döndürmediğinde, etkinlik WIL oluşturulmaz ve `ActivitySource.StartActivity` döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-148">If the callback return `ActivitySamplingResult.None` and no other enabled listeners return different value, then the Activity wil not get created and `ActivitySource.StartActivity` will return `null`.</span></span> <span data-ttu-id="9bae7-149">Aksi takdirde, `Activity` nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9bae7-149">Otherwise, the `Activity` object will get created.</span></span>

## <a name="net-50-new-features"></a><span data-ttu-id="9bae7-150">.NET 5,0 yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="9bae7-150">.NET 5.0 New Features</span></span>

<span data-ttu-id="9bae7-151">For etmek beklemeniz `Activity` sınıfı, izleme ana senaryolarını destekliyor.</span><span class="sxs-lookup"><span data-stu-id="9bae7-151">For awhile `Activity` class has been supporting tracing main scenarios.</span></span> <span data-ttu-id="9bae7-152">Anahtar-değer çiftleri olan izleme verilerinin bulunduğu etiketlerin çapraz olmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-152">It allowed sticking tags which is key-value pairs of tracing data.</span></span> <span data-ttu-id="9bae7-153">Bu, hat genelinde yayılmakta tasarlanan anahtar-değer etiketleri olan Baggleri destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="9bae7-153">It has been supporting Baggages which is a key-value tags intended to be propagated across the wire.</span></span>

<span data-ttu-id="9bae7-154">.NET 5,0, genellikle Opentelemetri senaryolarını etkinleştirmek için daha fazla özelliği destekler.</span><span class="sxs-lookup"><span data-stu-id="9bae7-154">.NET 5.0 supports more features mainly to enable OpenTelemetry scenarios.</span></span>

### <a name="activitycontext"></a><span data-ttu-id="9bae7-155">ActivityContext</span><span class="sxs-lookup"><span data-stu-id="9bae7-155">ActivityContext</span></span>

<span data-ttu-id="9bae7-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> , izleme işlemlerinin bağlamını taşıyan bir struct (örn. İzleme kimliği, span ID, Trace bayrakları ve izleme durumu).</span><span class="sxs-lookup"><span data-stu-id="9bae7-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> is the struct carrying the context of the tracing operations (e.g. the trace Id, Span Id, trace flags, and trace state).</span></span> <span data-ttu-id="9bae7-157">Artık `Activity` üst izleme bağlamını sağlayan yeni bir oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9bae7-157">Now it is possible to create a new `Activity` with providing the parent tracing context.</span></span> <span data-ttu-id="9bae7-158">Ayrıca, özelliği çağırarak herhangi bir nesneden izleme bağlamını ayıklamak kolaydır `Activity` `Activity.Context` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-158">Also, it is easy to extract the tracing context from any `Activity` object by calling `Activity.Context` property.</span></span>

### <a name="activitylink"></a><span data-ttu-id="9bae7-159">Etkinlik bağlantısı</span><span class="sxs-lookup"><span data-stu-id="9bae7-159">ActivityLink</span></span>

<span data-ttu-id="9bae7-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> , izleme bağlam örneğini içeren ve casuon ile ilgili nesneye bağlanabilen struct `Activity` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> is the struct containing the tracing context instance which can be linked to casually related `Activity` object.</span></span> <span data-ttu-id="9bae7-161">`Activity`Oluşturma sırasında bağlantı listesini yöntemine geçirerek bağlantılar nesnesine eklenebilir `ActivitySource.StartActivity` `Activity` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-161">Links can be added to the `Activity` object by passing the links list to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="9bae7-162">Tüm `Activity` nesne ekli bağlantıları özelliği kullanılarak alınabilir `Activity.Links` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-162">The whole `Activity` object attached links can be  retrieved using the property `Activity.Links`.</span></span>

### <a name="activityevent"></a><span data-ttu-id="9bae7-163">ActivityEvent</span><span class="sxs-lookup"><span data-stu-id="9bae7-163">ActivityEvent</span></span>

<span data-ttu-id="9bae7-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> ad ve zaman damgası içeren bir olayı ve isteğe bağlı etiket listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9bae7-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> represents an event containing a name and a timestamp, as well as an optional list of tags.</span></span> <span data-ttu-id="9bae7-165">Olaylar, `Activity` metodu çağırarak nesnesine eklenebilir `Activity.AddEvent` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-165">Events can be added to the `Activity` object by calling `Activity.AddEvent` method.</span></span> <span data-ttu-id="9bae7-166">`Activity`Nesne olaylarının tam listesi, özelliği kullanılarak alınabilir `Activity.Events` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-166">The whole list of the `Activity` object Events can be retrieved using the property `Activity.Events`.</span></span>

### <a name="activitykind"></a><span data-ttu-id="9bae7-167">Etkinlik türü</span><span class="sxs-lookup"><span data-stu-id="9bae7-167">ActivityKind</span></span>

<span data-ttu-id="9bae7-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> etkinlik, üst öğeleri ve bir izlemede alt öğeleri arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> describes the relationship between the activity, its parents and its children in a trace.</span></span> <span data-ttu-id="9bae7-169">Türü `Activity` , oluşturulurken tür değeri yöntemine geçirerek nesnesine ayarlanabilir `ActivitySource.StartActivity` `Activity` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-169">Kind can be set  to the `Activity` object by passing the kind value to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="9bae7-170">`Activity`Nesne türü, özelliği kullanılarak alınabilir `Activity.Kind` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-170">The `Activity` object kind can be retrieved using the property `Activity.Kind`.</span></span>

### <a name="isalldatarequested"></a><span data-ttu-id="9bae7-171">Isalldatareşitlenmiş</span><span class="sxs-lookup"><span data-stu-id="9bae7-171">IsAllDataRequested</span></span>

<span data-ttu-id="9bae7-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> Bu etkinliğin tüm yayma bilgileriyle doldurulmasının yanı sıra bağlantılar, Etiketler ve olaylar gibi diğer tüm özellikleri içerip içermediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> indicates whether this activity should be populated with all the propagation information, as well as all the other properties, such as links, tags, and events.</span></span> <span data-ttu-id="9bae7-173">Değeri, `IsAllDataRequested` Tüm dinleyicilerinin `Sample` ve `SampleUsingParentId` geri çağırmaların döndürdüğü sonuçtan belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-173">The value of `IsAllDataRequested` is determined from the result returned from all listeners `Sample` and `SampleUsingParentId` callbacks.</span></span> <span data-ttu-id="9bae7-174">Değer, özelliği kullanılarak alınabilir `Activity.IsAllDataRequested` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-174">The value can be retrieved using `Activity.IsAllDataRequested` property.</span></span>

### <a name="activitysource"></a><span data-ttu-id="9bae7-175">Activity. Source</span><span class="sxs-lookup"><span data-stu-id="9bae7-175">Activity.Source</span></span>

<span data-ttu-id="9bae7-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> Bu etkinlikle ilişkili etkinlik kaynağını alır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> gets the activity source associated with this activity.</span></span>

### <a name="activitydisplayname"></a><span data-ttu-id="9bae7-177">Activity. DisplayName</span><span class="sxs-lookup"><span data-stu-id="9bae7-177">Activity.DisplayName</span></span>

<span data-ttu-id="9bae7-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> etkinliğin bir görünen adını almaya veya ayarlamaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> allows getting or setting a display name to the activity.</span></span>

### <a name="activitytagobjects"></a><span data-ttu-id="9bae7-179">Activity. TagObjects</span><span class="sxs-lookup"><span data-stu-id="9bae7-179">Activity.TagObjects</span></span>

<span data-ttu-id="9bae7-180">`Activity` sınıfı, `Activity.Tags` anahtar ve değer için dize türü etiketlerinin anahtar-değer çifti listesini döndüren özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-180">`Activity` class has the property `Activity.Tags` which return the a key-value pair list of the tags of type string for the key and value.</span></span> <span data-ttu-id="9bae7-181">Bu tür Etiketler, `Activity` yöntemi kullanılarak öğesine eklenebilir `AddTag(string, string)` .</span><span class="sxs-lookup"><span data-stu-id="9bae7-181">Such Tags can be added to the `Activity` using the method `AddTag(string, string)`.</span></span> <span data-ttu-id="9bae7-182">`Activity` , `AddTag(string, object)` bir tür değere sahip olmasını sağlayan aşırı yüklenmiş yöntemi sağlayarak etiketlerin desteğini genişletmiştir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-182">`Activity` has extended the support of tags by providing the overloaded method `AddTag(string, object)` allowing to have values of any type.</span></span>  <span data-ttu-id="9bae7-183">Bu tür etiketlerin tamamen listesi kullanılarak alınabilir <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9bae7-183">The complete list of such tags can be retrieved using <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType>.</span></span>

## <a name="sampling"></a><span data-ttu-id="9bae7-184">Örnekleme</span><span class="sxs-lookup"><span data-stu-id="9bae7-184">Sampling</span></span>

<span data-ttu-id="9bae7-185">Örnekleme, toplanan ve arka uca gönderilen izlemelerin örnek sayısını azaltarak paraziti ve yükünü denetlemek için bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-185">Sampling is a mechanism to control the noise and overhead by reducing the number of samples of traces collected and sent to the backend.</span></span> <span data-ttu-id="9bae7-186">Örnekleme, önemli bir Opentelemetri senaryosudur.</span><span class="sxs-lookup"><span data-stu-id="9bae7-186">Sampling is important OpenTelemetry scenario.</span></span> <span data-ttu-id="9bae7-187">.NET 5,0 ' de örnekleme yapmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-187">In .NET 5.0 it is easy to allow sampling.</span></span> <span data-ttu-id="9bae7-188">İyi bir uygulama kullanarak yeni nesneleri oluşturur `Activity` `ActivitySource.StartActivity` ve tüm olası kullanılabilir verileri (örneğin, Etiketler, tür, bağlantılar,...) sağlamayı deneyin. vb.) Bu yöntem çağrılırken.</span><span class="sxs-lookup"><span data-stu-id="9bae7-188">A good practice is create the  new `Activity` objects using `ActivitySource.StartActivity` and try to provide all possible available data (e.g. tags, kind, links, ...etc.) when calling this method.</span></span> <span data-ttu-id="9bae7-189">Verilerin sağlanması, ' i kullanarak uygulanan örnekleyicilerin `ActivityListener` doğru örnekleme kararına sahip olmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9bae7-189">Providing the data will allow the samplers which implemented using the `ActivityListener` to have proper sampling decision.</span></span> <span data-ttu-id="9bae7-190">Nesneyi oluşturmadan önce verilerin oluşturulmasını önlemek için performans önemliyse `Activity` , `ActivitySource.HasListeners` gerekli verileri oluşturmadan önce herhangi bir dinleyici olup olmadığını denetlemek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9bae7-190">If the performance is critical to avoid creating the data before creating the `Activity` object, the property `ActivitySource.HasListeners` comes handy to check if there is any listeners before creating the needed data.</span></span>

## <a name="opentelemetry"></a><span data-ttu-id="9bae7-191">OpenTelemetry</span><span class="sxs-lookup"><span data-stu-id="9bae7-191">OpenTelemetry</span></span>

<span data-ttu-id="9bae7-192">Opentelemetri SDK 'Sı, uçtan uca dağıtılmış izleme senaryolarını destekleyen birçok özellik ile gelir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-192">OpenTelemetry SDK comes with many features that support end-to-end distributed tracing scenarios.</span></span> <span data-ttu-id="9bae7-193">Aralarından seçim yapabileceğiniz birden fazla örnekleyiciler ve dışarı vericiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-193">It provides multiple samplers and exporters which can choose from.</span></span> <span data-ttu-id="9bae7-194">Özel örnekleyiciler ve dışarı vericiler da oluşturulmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-194">It allows creating a custom samplers and exporters too.</span></span>

<span data-ttu-id="9bae7-195">Opentelemetri, toplanan izleme verilerinin farklı arka uçlara verilmesini destekler (örneğin, Jaeger, Zipkaya, yeni relik,...) vb.).</span><span class="sxs-lookup"><span data-stu-id="9bae7-195">OpenTelemetry supports exporting the collected tracing data to different backends (e.g. Jaeger, Zipkin, New Relic,...etc.).</span></span> <span data-ttu-id="9bae7-196">Daha fazla ayrıntı için [Opentelemetri-DotNet](https://github.com/open-telemetry/opentelemetry-dotnet/) adresine başvurun ve paketler için arama NuGet.org `OpenTelemetry.Exporter.` , dışarı aktarma paketleri listesini almak üzere ile başlar.</span><span class="sxs-lookup"><span data-stu-id="9bae7-196">Refer to [OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/) for more details and search Nuget.org for packages starts with `OpenTelemetry.Exporter.` to get the exporter packages list.</span></span>

<span data-ttu-id="9bae7-197">Aşağıda, izleme verilerinin konsola ne kadar kolay örnek ve dışarı aktarılacağı hakkında [Opentelemetri-DotNet ile başlayan](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) örnek bir kod verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9bae7-197">Here is a sample code ported from [OpenTelemetry-dotnet getting started](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) showing how easy can sample and export tracing data to the console.</span></span>

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

<span data-ttu-id="9bae7-198">Örneğin [Opentelemetri. dışarı aktarma. Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2)paketine başvurması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="9bae7-198">The sample needs to reference the package [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2).</span></span>
