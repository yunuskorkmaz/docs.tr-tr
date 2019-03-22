---
title: Kullanım HttpClientFactory dayanıklı HTTP isteklerini uygulamak için
description: .NET Core 2.1 itibaren kullanılabilir olan HttpClientFactory oluşturmak için kullanmayı öğrenin `HttpClient` örnekleri, uygulamalarınızda kullanabileceğiniz kolaylaştırır.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 679de8577d1ce876823954cb7917c50daae9e230
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348719"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="b4352-103">Kullanım HttpClientFactory dayanıklı HTTP isteklerini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="b4352-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="b4352-104">`HttpClientFactory` .NET Core 2.1 itibaren kullanılabilir kendine özgü tarzı olan bir factory oluşturmak için <xref:System.Net.Http.HttpClient> uygulamalarınızda kullanılacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b4352-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="b4352-105">' De .NET Core kullanılabilir özgün HttpClient sınıfı ile ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="b4352-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="b4352-106">Özgün ve iyi bilinen [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) sınıfı kolayca kullanılabilir, ancak bazı durumlarda, düzgün bir şekilde çok sayıda geliştirici tarafından kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b4352-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="b4352-107">Bu sınıf atılabilir olsa da, ilk bir sorun kullanmak `using` deyimi değil en iyi seçenek çünkü çıkardığınızda bile `HttpClient` nesne, temel alınan yuva hemen serbest bırakılmaz ve adlı ciddi bir soruna neden olabilecek ' yuvaları Tükenmesi '.</span><span class="sxs-lookup"><span data-stu-id="b4352-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="b4352-108">Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient yanlış kullanıyorsanız ve bu yazılım destabilizing](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog gönderisi.</span><span class="sxs-lookup"><span data-stu-id="b4352-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="b4352-109">Bu nedenle, `HttpClient` kez oluşturulacak hedeflenen ve bir uygulamanın ömrü yeniden.</span><span class="sxs-lookup"><span data-stu-id="b4352-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="b4352-110">Örnekleme bir `HttpClient` her istek ağır yük altında kullanılabilir yuva sayısını harcadıklarını anlamış için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b4352-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="b4352-111">Sorun sonuçlanır `SocketException` hataları.</span><span class="sxs-lookup"><span data-stu-id="b4352-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="b4352-112">Bu sorunu çözmek için olası bir yaklaşım oluşturma işlemini dayalı `HttpClient` nesne tekil veya statik bu konuda açıklandığı gibi [HttpClient kullanımı Microsoft makalesi](/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="b4352-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="b4352-113">İkinci bir sorundur ancak `HttpClient` tekil veya statik nesne olarak kullandığınızda, olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4352-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="b4352-114">Bu durumda, tekli veya statik `HttpClient` DNS değişikliklerinin, bu konuda açıklandığı gibi uymuyor [.NET Core GitHub deposunu, sorunu](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="b4352-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="b4352-115">Belirtilen sorunları gidermek ve yönetimini kolaylaştırmak için `HttpClient` örneklerini daha kolay, .NET Core 2.1 tanıtılan yeni bir `HttpClientFactory` , ayrıca Polly ile tümleştirerek dayanıklı HTTP çağrıları uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4352-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="b4352-116">HttpClientFactory nedir</span><span class="sxs-lookup"><span data-stu-id="b4352-116">What is HttpClientFactory</span></span>

<span data-ttu-id="b4352-117">`HttpClientFactory` için tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="b4352-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="b4352-118">Adlandırma ve mantıksal HttpClients yapılandırmak için merkezi bir konum sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4352-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="b4352-119">Örneğin, belirli bir mikro hizmet erişmek için önceden yapılandırılmış bir istemci (hizmet Aracısı) yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4352-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="b4352-120">Kod oluşturma işleyicileri temsilci aracılığıyla giden ara yazılım kavramını `HttpClient` ve dayanıklılık için Polly'nın ilkeleri yararlanmak için ara yazılımı Polly tabanlı uygulama.</span><span class="sxs-lookup"><span data-stu-id="b4352-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="b4352-121">`HttpClient` Giden HTTP istekleri için birbirine işleyicileri temsilci olarak görevlendirme kavramı zaten sahip.</span><span class="sxs-lookup"><span data-stu-id="b4352-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="b4352-122">Http istemcilerini Fabrika kaydetme ayrıca yeniden deneme CircuitBreakers, vb. için kullanılacak ilkeleri Polly izin veren bir Polly işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4352-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="b4352-123">Belirtilen sorunları/yönetirken oluşabilecek sorunları önlemek için HttpClientMessageHandlers ömrünü yönetmek `HttpClient` ömürleri kendiniz.</span><span class="sxs-lookup"><span data-stu-id="b4352-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="b4352-124">Birden çok yolu HttpClientFactory kullanın</span><span class="sxs-lookup"><span data-stu-id="b4352-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="b4352-125">Kullanabileceğiniz birkaç şekilde `HttpClientFactory` uygulamanızdaki:</span><span class="sxs-lookup"><span data-stu-id="b4352-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="b4352-126">Kullanım `HttpClientFactory` doğrudan</span><span class="sxs-lookup"><span data-stu-id="b4352-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="b4352-127">İstemciler adlı kullanın</span><span class="sxs-lookup"><span data-stu-id="b4352-127">Use Named Clients</span></span>
- <span data-ttu-id="b4352-128">Türü belirlenmiş istemci kullanma</span><span class="sxs-lookup"><span data-stu-id="b4352-128">Use Typed Clients</span></span>
- <span data-ttu-id="b4352-129">Oluşturulan istemciler</span><span class="sxs-lookup"><span data-stu-id="b4352-129">Use Generated Clients</span></span>

<span data-ttu-id="b4352-130">Konuyu uzatmamak amacıyla, bu kılavuzu kullanmak için yapılandırılmış en yolu gösterir. `HttpClientFactory` yazılan istemciler (hizmet Aracısı deseni) kullanılacak olan, ancak tüm seçenekler belirtilmiştir ve bu şu anda listelenen [HttpClientFactory kullanım kapsayan makale ](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="b4352-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="b4352-131">Türü belirlenmiş istemci HttpClientFactory ile kullanma</span><span class="sxs-lookup"><span data-stu-id="b4352-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="b4352-132">Bu nedenle, bir "türü belirlenmiş istemci" nedir?</span><span class="sxs-lookup"><span data-stu-id="b4352-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="b4352-133">Yalnızca olduğu bir `HttpClient` eklenmesiyle üzerine yapılandırılmış `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="b4352-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="b4352-134">Aşağıdaki diyagramda yazılan istemcileri ile nasıl kullanıldığı gösterilmektedir `HttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="b4352-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![(Bir denetleyici veya istemci kodu tarafından kullanılır) bir ClientService kayıtlı IHttpClientFactory tarafından oluşturulan bir HttpClient kullanır.](./media/image3.5.png)

<span data-ttu-id="b4352-138">**Şekil 8-4**.</span><span class="sxs-lookup"><span data-stu-id="b4352-138">**Figure 8-4**.</span></span> <span data-ttu-id="b4352-139">İstemci türü belirtilmiş sınıflarıyla HttpClientFactory kullanma.</span><span class="sxs-lookup"><span data-stu-id="b4352-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="b4352-140">İlk olarak, Kurulum `HttpClientFactory` uygulamanızda bir başvuru eklemeyi `Microsoft.Extensions.Http` içeren paketi `AddHttpClient()` genişletme yöntemi için `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="b4352-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="b4352-141">Bu genişletme yöntemi kaydeder `DefaultHttpClientFactory` arabirimi tekil olarak kullanılacak `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="b4352-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="b4352-142">Geçici bir yapılandırma için tanımladığı `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="b4352-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="b4352-143">Bu ileti işleyicisi (`HttpMessageHandler` nesne), uygulanan bir havuzdan tarafından kullanılan `HttpClient` fabrikadan döndürdü.</span><span class="sxs-lookup"><span data-stu-id="b4352-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="b4352-144">Sonraki kodunda gördüğünüz nasıl `AddHttpClient()` yazılan kullanması gereken istemciler (hizmet aracılar) kaydetmek için kullanılan `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="b4352-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="b4352-145">Önceki kodda gösterildiği gibi istemci hizmetlerine kaydetme yapar `DefaultClientFactory` oluşturmak bir `HttpClient` paragrafında açıklayacağız olarak her hizmet için özel olarak yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="b4352-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="b4352-146">İstemci hizmet sınıfınızı ile kaydederek yalnızca `AddHttpClient()`, `HttpClient` sınıfınıza eklenen nesne yapılandırması ve ilkelerini kayıt sırasında sağlanan kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4352-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="b4352-147">Sonraki bölümlerde, bu ilkeleri Polly'nın deneme veya devre Kesiciler gibi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b4352-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="b4352-148">HttpClient yaşam süresi yok</span><span class="sxs-lookup"><span data-stu-id="b4352-148">HttpClient lifetimes</span></span>

<span data-ttu-id="b4352-149">Aldığınız her seferinde bir `HttpClient` nesnesinden `IHttpClientFactory`, yeni bir örneği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b4352-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="b4352-150">Ancak her `HttpClient` kullanan bir `HttpMessageHandler` , havuza alınmış olan ve tarafından yeniden `IHttpClientFactory` sürece kaynak tüketimini azaltmak için `HttpMessageHandler`'s taşınmadığından yaşam süresi doldu.</span><span class="sxs-lookup"><span data-stu-id="b4352-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="b4352-151">Her işleyicisi genellikle kendi temel alınan HTTP bağlantıları yöneten işleyicileri havuzu tercih edilir; gerekenden daha fazla işleyicileri oluşturma bağlantı gecikmelerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4352-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="b4352-152">Bazı işleyiciler da bağlantıları açık süresiz olarak, DNS değişiklikleri tepki gelen, işleyici engelleyebilir tutun.</span><span class="sxs-lookup"><span data-stu-id="b4352-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="b4352-153">`HttpMessageHandler` Havuzdaki nesnelerin sürenin uzunluğunu olan bir ömrü vardır, bir `HttpMessageHandler` havuzundaki örneği yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4352-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="b4352-154">Varsayılan değer, iki dakika olmakla birlikte, türü belirlenmiş istemci geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="b4352-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="b4352-155">Geçersiz kılmak için çağrı `SetHandlerLifetime()` üzerinde `IHttpClientBuilder` döndürülen istemci oluştururken aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="b4352-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="b4352-156">Her bir türü belirlenmiş istemci kendi yapılandırılmış işleyici ömrü değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4352-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="b4352-157">Süresini ayarlamak `InfiniteTimeSpan` işleyicisi sona erme devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="b4352-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="b4352-158">Eklenen ve yapılandırılmış HttpClient kullanan, türü belirlenmiş istemci sınıfları uygulama</span><span class="sxs-lookup"><span data-stu-id="b4352-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="b4352-159">Önceki adımda tanımlanan sınıflar 'BasketService', 'CatalogService', 'OrderingService' vb. gibi örnek kod gibi türü belirlenmiş istemci sınıfları olması gerekir: bir türü belirlenmiş istemci kabul eden bir sınıf bir `HttpClient` nesne (aracılığıyla eklenen kendi Oluşturucu) ve bazı uzak bir HTTP hizmetine çağrı yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4352-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="b4352-160">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b4352-160">For example:</span></span>

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

<span data-ttu-id="b4352-161">Türü belirlenmiş istemci (örnekte CatalogService) DI HttpClient yanı sıra, yapıcısına bulunan kayıtlı bir hizmet kabul edebilir anlamına gelir (bağımlılık ekleme) tarafından etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b4352-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="b4352-162">Türü belirlenmiş bir istemci, etkili bir şekilde, geçici bir nesne bir gereken her seferinde yeni bir örneği oluşturulur ve yeni bir alırsınız anlamına gelir `HttpClient` , oluşturulan her zaman örneği.</span><span class="sxs-lookup"><span data-stu-id="b4352-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="b4352-163">Ancak, havuzdaki HttpMessageHandler nesneler tarafından birden çok Http isteklerini yeniden nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="b4352-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="b4352-164">Türü belirlenmiş istemci sınıfları kullanın</span><span class="sxs-lookup"><span data-stu-id="b4352-164">Use your Typed Client classes</span></span>

<span data-ttu-id="b4352-165">Türü sınıflarınızı uygulanmış olan ve onlara AddHttpClient() ile kayıtlı sonra son olarak, bunu herhangi bir yere Hizmetleri DI tarafından örneğin herhangi bir Razor sayfası kod veya herhangi bir MVC web uygulaması denetleyicisinde gibi aşağıdaki kod, eklenmiş olabilir kullanabilirsiniz Hizmetine.</span><span class="sxs-lookup"><span data-stu-id="b4352-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="b4352-166">Bu noktaya kadar gösterilen kod yalnızca normal Http isteği gerçekleştiriyor, ancak aşağıdaki bölümlerde 'sihirden' gelen, yalnızca ilke ekleyerek ve temsilci yapılacak işleyicileri kayıtlı yazılmış istemciler için tüm HTTP istekleri `HttpClient` olur alırken hesap dayanıklı ilkeleri üstel geri alma, devre Kesiciler ve kimlik doğrulama belirteçlerini veya herhangi bir özel özellik kullanma gibi ek güvenlik özellikleri uygulamak için tüm diğer özel temsilci işleyicisi ile yeniden gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="b4352-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="b4352-167">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b4352-167">Additional resources</span></span>

- <span data-ttu-id="b4352-168">**' De .NET Core HttpClientFactory kullanma**\\</span><span class="sxs-lookup"><span data-stu-id="b4352-168">**Using HttpClientFactory in .NET Core**\\</span></span>
  [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="b4352-169">**HttpClientFactory GitHub deposu**\\</span><span class="sxs-lookup"><span data-stu-id="b4352-169">**HttpClientFactory GitHub repo**\\</span></span>
  [*https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory*](https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory)

>[!div class="step-by-step"]
><span data-ttu-id="b4352-170">[Önceki](explore-custom-http-call-retries-exponential-backoff.md)
>[İleri](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="b4352-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
