---
title: Dayanıklı HTTP isteklerini uygulamak için HttpClientFactory kullanma
description: .NET Core 2,1 ' den bu yana sunulan httpclientfactory kullanarak, örnek oluşturma `HttpClient` hakkında bilgi edinmek için, bunu uygulamalarınızda kullanmanızı kolaylaştırır.
ms.date: 08/08/2019
ms.openlocfilehash: 6c862171ee6b5eda6f95694878bfa43518a9bdfa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039971"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="b0c73-103">Dayanıklı HTTP isteklerini uygulamak için HttpClientFactory kullanma</span><span class="sxs-lookup"><span data-stu-id="b0c73-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="b0c73-104">`HttpClientFactory`, uygulamalarınızda kullanılacak örnekleri oluşturmak <xref:System.Net.Http.HttpClient> için .NET Core 2,1 ' den beri sunulan bir OPTA ve dağıtılmış bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="b0c73-105">.NET Core 'da sunulan özgün HttpClient sınıfı ile ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="b0c73-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="b0c73-106">Özgün ve iyi bilinen <xref:System.Net.Http.HttpClient> sınıf kolayca kullanılabilir, ancak bazı durumlarda birçok geliştirici tarafından düzgün şekilde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="b0c73-107">İlk bir sorun olarak, bu sınıf atılabilir olduğu halde, nesne atılırken `using` `HttpClient` bile, temel alınan yuva hemen yayınlanmaz ve ' yuvalar ' adlı ciddi bir soruna neden olabilir. tükenme.</span><span class="sxs-lookup"><span data-stu-id="b0c73-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="b0c73-108">Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient kullanıyorsunuz ve yazılım blog gönderinizi kararlı hale](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) getirme.</span><span class="sxs-lookup"><span data-stu-id="b0c73-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="b0c73-109">Bu nedenle `HttpClient` , bir kez örneğinin oluşturulması ve bir uygulamanın ömrü boyunca yeniden kullanılması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="b0c73-110">Her istek `HttpClient` için bir sınıfın örnekleniyor, ağır yüklerin altında bulunan yuva sayısını tükeder.</span><span class="sxs-lookup"><span data-stu-id="b0c73-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="b0c73-111">Bu sorun `SocketException` hatalara neden olur.</span><span class="sxs-lookup"><span data-stu-id="b0c73-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="b0c73-112">Bu sorunu çözmek için olası yaklaşımlar, `HttpClient` [HttpClient kullanımıyla ilgili bu Microsoft makalesinde](../../../csharp/tutorials/console-webapiclient.md)açıklandığı gibi nesnenin tek veya statik olarak oluşturulmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span>

<span data-ttu-id="b0c73-113">Ancak, bunu tek veya statik nesne `HttpClient` olarak kullandığınızda kullanabileceğiniz ikinci bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="b0c73-114">Bu durumda, DotNet/corefx `HttpClient` GitHub deposundaki bu [sorun](https://github.com/dotnet/corefx/issues/11224) bölümünde açıklandığı gibi, tek veya statik, DNS değişikliklerini dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="b0c73-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue](https://github.com/dotnet/corefx/issues/11224) at the dotnet/corefx GitHub repository.</span></span> 

<span data-ttu-id="b0c73-115">Söz konusu sorunları gidermek ve `HttpClient` örneklerin yönetimini kolaylaştırmak için, .NET Core 2,1, aynı zamanda Polly ile tümleştirerek dayanıklı http çağrıları uygulamak için de kullanılabilecek yeni `HttpClientFactory` bir kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="b0c73-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>

<span data-ttu-id="b0c73-116">[Polly](http://www.thepollyproject.org/) , geliştiricilerin önceden tanımlanmış bazı ilkeleri akıcı ve iş parçacığı açısından güvenli bir şekilde kullanarak uygulamalarına dayanıklılık eklemesine yardımcı olan geçici hata işleme kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-116">[Polly](http://www.thepollyproject.org/) is transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="b0c73-117">HttpClientFactory nedir?</span><span class="sxs-lookup"><span data-stu-id="b0c73-117">What is HttpClientFactory</span></span>

<span data-ttu-id="b0c73-118">`HttpClientFactory`şunları yapmak için tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="b0c73-118">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="b0c73-119">Mantıksal `HttpClient` nesneleri adlandırmak ve yapılandırmak için merkezi bir konum sağlayın.</span><span class="sxs-lookup"><span data-stu-id="b0c73-119">Provide a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="b0c73-120">Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Hizmet Aracısı) yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0c73-120">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="b0c73-121">' Deki `HttpClient` işleyicileri devrederek ve Polly tabanlı ara yazılım kullanarak, dayanıklılık için Polly ilkelerinin avantajlarından faydalanarak giden ara yazılım kavramını codime edin.</span><span class="sxs-lookup"><span data-stu-id="b0c73-121">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="b0c73-122">`HttpClient`, giden HTTP istekleri için birlikte bağlanabilen işleyicileri temsilci seçme kavramına zaten sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-122">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="b0c73-123">HTTP istemcilerini fabrikaya kaydedersiniz ve yeniden deneme, devre kesiciler ve benzeri bir ilke kullanmak için bir Polly işleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0c73-123">You register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="b0c73-124">Kullanım ömrünü `HttpClientMessageHandlers` yönetmek için, belirtilen sorunları/yaşam sürelerini kendi başınıza yönetirken `HttpClient` oluşabilecek sorunları önlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0c73-124">Manage the lifetime of `HttpClientMessageHandlers` to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="b0c73-125">HttpClientFactory kullanmanın birden çok yolu</span><span class="sxs-lookup"><span data-stu-id="b0c73-125">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="b0c73-126">Uygulamanızda kullanabileceğiniz `HttpClientFactory` çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="b0c73-126">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="b0c73-127">Doğrudan `HttpClientFactory` kullanma</span><span class="sxs-lookup"><span data-stu-id="b0c73-127">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="b0c73-128">Adlandırılmış Istemcileri kullan</span><span class="sxs-lookup"><span data-stu-id="b0c73-128">Use Named Clients</span></span>
- <span data-ttu-id="b0c73-129">Yazılan Istemcileri kullan</span><span class="sxs-lookup"><span data-stu-id="b0c73-129">Use Typed Clients</span></span>
- <span data-ttu-id="b0c73-130">Oluşturulan Istemcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="b0c73-130">Use Generated Clients</span></span>

<span data-ttu-id="b0c73-131">Kısaltma açısından bu kılavuzda, türü belirlenmiş istemcileri (Hizmet Aracısı kalıbı) kullanmak için en yapısal `HttpClientFactory`olarak kullanılan yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-131">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="b0c73-132">Ancak, tüm seçenekler belgelenmiştir ve şu anda [HttpClientFactory kullanımını kapsayan bu makalede](/aspnet/core/fundamentals/http-requests#consumption-patterns)listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-132">However, all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="b0c73-133">HttpClientFactory ile yazılan Istemcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="b0c73-133">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="b0c73-134">Bu nedenle, "yazılı Istemci" nedir?</span><span class="sxs-lookup"><span data-stu-id="b0c73-134">So, what's a "Typed Client"?</span></span> <span data-ttu-id="b0c73-135">Bu yalnızca `HttpClient` , `DefaultHttpClientFactory`tarafından eklenerek yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-135">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="b0c73-136">Aşağıdaki diyagramda, yazılan Istemcilerin ile `HttpClientFactory`nasıl kullanıldığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b0c73-136">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![Bir ClientService (bir denetleyici veya istemci kodu tarafından kullanılan), kayıtlı ıhttpclientfactory tarafından oluşturulan bir HttpClient kullanır.](./media/image3.5.png)

<span data-ttu-id="b0c73-140">**Şekil 8-4**.</span><span class="sxs-lookup"><span data-stu-id="b0c73-140">**Figure 8-4**.</span></span> <span data-ttu-id="b0c73-141">Türü belirtilmiş Istemci sınıflarıyla HttpClientFactory kullanma.</span><span class="sxs-lookup"><span data-stu-id="b0c73-141">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="b0c73-142">İlk olarak, `HttpClientFactory` için `Microsoft.Extensions.Http` genişletmeyöntemini`AddHttpClient()` içeren NuGet paketini yükleyerek uygulamanızda kurulum yapın. `IServiceCollection`</span><span class="sxs-lookup"><span data-stu-id="b0c73-142">First, setup `HttpClientFactory` in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="b0c73-143">Bu genişletme yöntemi, `DefaultHttpClientFactory` arabirimi `IHttpClientFactory`için tek olarak kullanılacak öğesini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b0c73-143">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="b0c73-144">İçin geçici bir yapılandırma tanımlar `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="b0c73-144">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="b0c73-145">Bir havuzdan alınan bu`HttpMessageHandler` ileti işleyici (nesne), fabrikada `HttpClient` döndürülen tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-145">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="b0c73-146">Sonraki kodda, kullanması `AddHttpClient()` `HttpClient`gereken yazılmış istemcileri (hizmet aracıları) kaydetmek için nasıl kullanılabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0c73-146">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="b0c73-147">İstemci hizmetlerini önceki kodda gösterildiği gibi kaydetmek, her hizmet için standart `DefaultClientFactory` `HttpClient` oluştur ' u oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0c73-147">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="b0c73-148">Ayrıca, kayda örneğe özgü yapılandırma ekleyebilirsiniz, örneğin, temel adresi yapılandırabilir ve aşağıdaki kodda gösterildiği gibi bazı dayanıklılık ilkeleri ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b0c73-148">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"])
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="b0c73-149">Yalnızca sake örneği için, sonraki kodda yukarıdaki ilkelerden birini görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b0c73-149">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="b0c73-150">[Sonraki makalede](implement-http-call-retries-exponential-backoff-polly.md)Polly kullanma hakkında daha fazla ayrıntı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0c73-150">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="b0c73-151">HttpClient yaşam süreleri</span><span class="sxs-lookup"><span data-stu-id="b0c73-151">HttpClient lifetimes</span></span>

<span data-ttu-id="b0c73-152">İçinden bir `HttpClient` nesne aldığınızda ,yenibirörnekdöndürülür.`IHttpClientFactory`</span><span class="sxs-lookup"><span data-stu-id="b0c73-152">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="b0c73-153">`HttpMessageHandler` `HttpMessageHandler`Ancak, `HttpClient` süresidolmadığısürecekaynaktüketiminiazaltmakiçintarafındanhavuzaalınmışveyeniden`IHttpClientFactory` kullanılan bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-153">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="b0c73-154">Her işleyici genellikle kendi temel aldığı HTTP bağlantılarını yönettiğinden, işleyicilerin havuzlaması istenir; gerekenden daha fazla işleyici oluşturulması bağlantı gecikmeleri oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-154">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="b0c73-155">Ayrıca, bazı işleyiciler bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine yeniden davranmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-155">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="b0c73-156">Havuzdaki nesneler, havuzdaki bir `HttpMessageHandler` örneğin yeniden kullanılabilmesi için gereken süre olan bir yaşam süresine sahiptir. `HttpMessageHandler`</span><span class="sxs-lookup"><span data-stu-id="b0c73-156">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="b0c73-157">Varsayılan değer iki dakikadır, ancak türü belirlenmiş Istemci başına geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-157">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="b0c73-158">Bunu geçersiz kılmak için, `SetHandlerLifetime()` aşağıdaki kodda `IHttpClientBuilder` gösterildiği gibi istemciyi oluştururken döndürülen ' i çağırın:</span><span class="sxs-lookup"><span data-stu-id="b0c73-158">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="b0c73-159">Her tür Istemcinin kendi yapılandırılmış işleyici yaşam süresi değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-159">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="b0c73-160">Kullanım süresini `InfiniteTimeSpan` , işleyicinin süre sonunu devre dışı bırakacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b0c73-160">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="b0c73-161">Eklenen ve yapılandırılmış HttpClient kullanan, yazılan Istemci sınıflarınızı uygulama</span><span class="sxs-lookup"><span data-stu-id="b0c73-161">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="b0c73-162">Önceki bir adım olarak, örnek kodda bulunan, örneğin ' basketservice ', ' catalogservice ', ' orderingservice ' vb. gibi tür istemci sınıflarınızın tanımlanmış olması gerekir. – türü belirtilmiş bir istemci, bir `HttpClient` nesneyi kabul eden bir sınıftır ( Oluşturucu) ve bunu, uzak HTTP hizmetini çağırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-162">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="b0c73-163">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0c73-163">For example:</span></span>

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take, 
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl, 
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

<span data-ttu-id="b0c73-164">Yazılan Istemci (örnekteki CatalogService), dı (bağımlılık ekleme) tarafından etkinleştirilir, yani, HttpClient ' a ek olarak oluşturucudaki kayıtlı bir hizmeti kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-164">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="b0c73-165">Türü belirlenmiş bir istemci, etkin bir şekilde geçici bir nesnedir, yani her gerektiğinde yeni bir örnek oluşturulur ve her oluşturulduğunda yeni `HttpClient` bir örnek alınır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-165">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="b0c73-166">Ancak, havuzdaki HttpMessageHandler nesneleri birden çok http isteği tarafından yeniden kullanılan nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="b0c73-166">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="b0c73-167">Türsüz Istemci sınıflarınızı kullanın</span><span class="sxs-lookup"><span data-stu-id="b0c73-167">Use your Typed Client classes</span></span>

<span data-ttu-id="b0c73-168">Son olarak, klavyeyle oluşturulmuş sınıflarınız uygulandıktan ve ile `AddHttpClient()`kaydolduktan sonra, bu hizmetleri, dı tarafından eklenen hizmetlere sahip olduğunuz her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0c73-168">Finally, once you have your typed classes implemented and have them registered with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="b0c73-169">Örneğin, bir MVC web uygulamasının Razor sayfa kodunda veya denetleyicisinde eShopOnContainers 'dan aşağıdaki kodda olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="b0c73-169">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) =>
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied,
                                               int? TypesFilterApplied,
                                               int? page,
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0,
                                                            itemsPage,
                                                            BrandFilterApplied,
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

<span data-ttu-id="b0c73-170">Bu noktaya kadar, gösterilen kod yalnızca normal http isteklerini gerçekleştiriyor, ancak ' Magic ', kayıtlı belirlenmiş istemcilerinize ilke ekleyerek ve işleyicileri temsilci seçerek aşağıdaki bölümlerde bulunur, bu, tarafından `HttpClient` yapılacak tüm http isteklerinin , üstel geri alma, devre kesiciler veya diğer özel temsilci seçme işleyicilerini kullanarak, kimlik doğrulama belirteçleri veya başka bir özel özellik gibi ek güvenlik özellikleri uygulamak üzere dayanıklı ilkeleri hesaba katmaya davranır.</span><span class="sxs-lookup"><span data-stu-id="b0c73-170">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b0c73-171">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b0c73-171">Additional resources</span></span>

- <span data-ttu-id="b0c73-172">**.NET Core 'da HttpClientFactory kullanma** </span><span class="sxs-lookup"><span data-stu-id="b0c73-172">**Using HttpClientFactory in .NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="b0c73-173">**HttpClientFactory GitHub deposu** </span><span class="sxs-lookup"><span data-stu-id="b0c73-173">**HttpClientFactory GitHub repo** </span></span>\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="b0c73-174">**Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**  </span><span class="sxs-lookup"><span data-stu-id="b0c73-174">**Polly (.NET resilience and transient-fault-handling library)** </span></span>\
  <http://www.thepollyproject.org/>

>[!div class="step-by-step"]
><span data-ttu-id="b0c73-175">[Önceki](explore-custom-http-call-retries-exponential-backoff.md)İleri
>[](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="b0c73-175">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
