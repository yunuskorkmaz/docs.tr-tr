---
title: Kullanım HttpClientFactory dayanıklı HTTP isteklerini uygulamak için
description: HttpClientFactory oluşturmak için .NET Core 2.1 itibaren kullanılabilir kendine özgü tarzı olan bir Fabrika olan `HttpClient` uygulamalarınızda kullanılacak örnekleri.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 6fd30a9358ca9c07b2a6e2ec591e4c5d7db54ccb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395546"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="d9196-103">Kullanım HttpClientFactory dayanıklı HTTP isteklerini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="d9196-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="d9196-104">`HttpClientFactory` .NET Core 2.1 itibaren kullanılabilir kendine özgü tarzı olan bir factory oluşturmak için `HttpClient` uygulamalarınızda kullanılacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d9196-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating `HttpClient` instances to be used in your applications.</span></span> 

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="d9196-105">' De .NET Core kullanılabilir özgün HttpClient sınıfı ile ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="d9196-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="d9196-106">Özgün ve iyi-bilmesi [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) sınıfı kolayca kullanılabilir, ancak bazı durumlarda, düzgün bir şekilde çok sayıda geliştirici tarafından kullanıldığı değil.</span><span class="sxs-lookup"><span data-stu-id="d9196-106">The original and well-know [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it is not being properly used by many developers.</span></span> 

<span data-ttu-id="d9196-107">Bu sınıf atılabilir olsa da, ilk bir sorun kullanmak `using` deyimi değil en iyi seçenek çünkü çıkardığınızda bile `HttpClient` nesne, temel alınan yuva hemen serbest bırakılmaz ve adlı ciddi bir soruna neden olabilecek ' yuvaları Tükenmesi '.</span><span class="sxs-lookup"><span data-stu-id="d9196-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="d9196-108">Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient yanlış kullanıyorsanız ve bu yazılım destabilizing](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog gönderisi.</span><span class="sxs-lookup"><span data-stu-id="d9196-108">For more information about this issue, see [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="d9196-109">Bu nedenle, `HttpClient` kez oluşturulacak hedeflenen ve bir uygulamanın ömrü yeniden.</span><span class="sxs-lookup"><span data-stu-id="d9196-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="d9196-110">Örnekleme bir `HttpClient` her istek ağır yük altında kullanılabilir yuva sayısını harcadıklarını anlamış için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d9196-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="d9196-111">Sorun sonuçlanır `SocketException` hataları.</span><span class="sxs-lookup"><span data-stu-id="d9196-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="d9196-112">Bu sorunu çözmek için olası bir yaklaşım oluşturma işlemini dayalı `HttpClient` nesne tekil veya statik bu konuda açıklandığı gibi [HttpClient kullanımı Microsoft makalesi](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="d9196-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="d9196-113">İkinci bir sorundur ancak `HttpClient` tekil veya statik nesne olarak kullandığınızda, olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9196-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="d9196-114">Bu durumda, tekli veya statik `HttpClient` DNS değişikliklerinin, bu konuda açıklandığı gibi uymuyor [.NET Core GitHub deposunu, sorunu](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="d9196-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="d9196-115">Belirtilen sorunları gidermek ve yönetimini kolaylaştırmak için `HttpClient` örneklerini daha kolay, .NET Core 2.1 sunan yeni bir `HttpClientFactory` , ayrıca Polly ile tümleştirerek dayanıklı HTTP çağrıları uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9196-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 offers a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="d9196-116">HttpClientFactory nedir</span><span class="sxs-lookup"><span data-stu-id="d9196-116">What is HttpClientFactory</span></span>

<span data-ttu-id="d9196-117">`HttpClientFactory` için tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="d9196-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="d9196-118">Adlandırma ve mantıksal HttpClients yapılandırmak için merkezi bir konum sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9196-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="d9196-119">Örneğin, belirli bir mikro hizmet erişmek için önceden yapılandırılmış bir istemci (hizmet Aracısı) yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9196-119">For example, you may configure a client (Service Agent) that is pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="d9196-120">Kod oluşturma işleyicileri temsilci aracılığıyla giden ara yazılım kavramını `HttpClient` ve dayanıklılık için Polly'nın ilkeleri yararlanmak için ara yazılımı Polly tabanlı uygulama.</span><span class="sxs-lookup"><span data-stu-id="d9196-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="d9196-121">`HttpClient` Giden HTTP istekleri için birbirine işleyicileri temsilci olarak görevlendirme kavramı zaten sahip.</span><span class="sxs-lookup"><span data-stu-id="d9196-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="d9196-122">Http istemcilerini Fabrika kaydetme ayrıca yeniden deneme CircuitBreakers, vb. için kullanılacak ilkeleri Polly izin veren bir Polly işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9196-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="d9196-123">Belirtilen sorunları/yönetirken oluşabilecek sorunları önlemek için HttpClientMessageHandlers ömrünü yönetmek `HttpClient` ömürleri kendiniz.</span><span class="sxs-lookup"><span data-stu-id="d9196-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="d9196-124">Birden çok yolu HttpClientFactory kullanın</span><span class="sxs-lookup"><span data-stu-id="d9196-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="d9196-125">Kullanabileceğiniz birkaç şekilde `HttpClientFactory` uygulamanızdaki:</span><span class="sxs-lookup"><span data-stu-id="d9196-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="d9196-126">Kullanım `HttpClientFactory` doğrudan</span><span class="sxs-lookup"><span data-stu-id="d9196-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="d9196-127">İstemciler adlı kullanın</span><span class="sxs-lookup"><span data-stu-id="d9196-127">Use Named Clients</span></span>
- <span data-ttu-id="d9196-128">Türü belirlenmiş istemci kullanma</span><span class="sxs-lookup"><span data-stu-id="d9196-128">Use Typed Clients</span></span>
- <span data-ttu-id="d9196-129">Oluşturulan istemciler</span><span class="sxs-lookup"><span data-stu-id="d9196-129">Use Generated Clients</span></span>

<span data-ttu-id="d9196-130">Konuyu uzatmamak amacıyla, bu kılavuzu kullanmak için yapılandırılmış en yolu gösterir. `HttpClientFactory` yazılan istemciler (hizmet Aracısı deseni) kullanılacak olan, ancak tüm seçenekler belirtilmiştir ve bu şu anda listelenen [HttpClientFactory kullanım kapsayan makale ](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="d9196-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that is to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="d9196-131">Türü belirlenmiş istemci HttpClientFactory ile kullanma</span><span class="sxs-lookup"><span data-stu-id="d9196-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="d9196-132">Aşağıdaki diyagramda, yazılan istemciler HttpClientFactory ile nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9196-132">The following diagram shows how Typed Clients are used with HttpClientFactory.</span></span>

![Diyagram ile yapılandırılmış bir HttpClient HttpClientFactory ve Polly'nın ilkeleri tarafından dahili olarak kullanarak bir eklenen ClientService kullanarak bir MVC denetleyicisi](./media/image3.5.png)

<span data-ttu-id="d9196-134">**Şekil 10-4**.</span><span class="sxs-lookup"><span data-stu-id="d9196-134">**Figure 10-4**.</span></span> <span data-ttu-id="d9196-135">Kullanarak `HttpClientFactory`ile yazılmış istemci sınıfları.</span><span class="sxs-lookup"><span data-stu-id="d9196-135">Using `HttpClientFactory`with Typed Client classes.</span></span>

<span data-ttu-id="d9196-136">İlk olarak, Kurulum `HttpClientFactory` uygulamanızdaki.</span><span class="sxs-lookup"><span data-stu-id="d9196-136">First, setup `HttpClientFactory` in your application.</span></span> <span data-ttu-id="d9196-137">Bir başvuru ekleyin `Microsoft.Extensions.Http` içeren paket `AddHttpClient()` genişletme yöntemi için `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="d9196-137">Add a reference to the `Microsoft.Extensions.Http` package which includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="d9196-138">Bu genişletme yöntemi kaydeder `DefaultHttpClientFactory` arabirimi tekil olarak kullanılacak `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="d9196-138">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="d9196-139">Geçici bir yapılandırma için tanımladığı `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="d9196-139">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="d9196-140">Bu ileti işleyicisi (`HttpMessageHandler` nesne), uygulanan bir havuzdan tarafından kullanılan `HttpClient` fabrikadan döndürdü.</span><span class="sxs-lookup"><span data-stu-id="d9196-140">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="d9196-141">Sonraki kodunda gördüğünüz nasıl `AddHttpClient()` yazılan kullanması gereken istemciler (hizmet aracılar) kaydetmek için kullanılan `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="d9196-141">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="d9196-142">Türü belirlenmiş istemci sınıflarınızı AddHttpClient() ile yalnızca ekleyerek kullandığınızda `HttpClient` oluşturucusu, aracılığıyla sınıfınıza eklenen nesne, `HttpClient` tüm yapılandırması ve ilkelerini sağlanan nesne kullanacağınız.</span><span class="sxs-lookup"><span data-stu-id="d9196-142">Just by adding your typed client classes with AddHttpClient(), whenever you use the `HttpClient` object that will be injected to your class through its constructor, that `HttpClient` object will be using all the configuration and policies provided.</span></span> <span data-ttu-id="d9196-143">Sonraki bölümlerde, bu ilkeleri Polly'nın deneme veya devre Kesiciler gibi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d9196-143">In the next sections, you will see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="d9196-144">HttpClient yaşam süresi yok</span><span class="sxs-lookup"><span data-stu-id="d9196-144">HttpClient lifetimes</span></span>

<span data-ttu-id="d9196-145">Aldığınız her seferinde bir `HttpClient` IHttpClientFactory, yeni bir örneğini nesneden bir `HttpClient` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d9196-145">Each time you get an `HttpClient` object from IHttpClientFactory, a new instance of an `HttpClient` is returned.</span></span> <span data-ttu-id="d9196-146">Olacak bir HttpMessageHandler ** başına türü belirlenmiş istemci adlı.</span><span class="sxs-lookup"><span data-stu-id="d9196-146">There will be an HttpMessageHandler** per named of typed client.</span></span> <span data-ttu-id="d9196-147">Ben`HttpClientFactory` kaynak tüketimini azaltmak için fabrika tarafından oluşturulan HttpMessageHandler örnekleri havuzu olur.</span><span class="sxs-lookup"><span data-stu-id="d9196-147">I`HttpClientFactory` will pool the HttpMessageHandler instances created by the factory to reduce resource consumption.</span></span> <span data-ttu-id="d9196-148">HttpMessageHandler örneği havuzundan yeni bir oluştururken yeniden kullanılabilme `HttpClient` yaşam süresi dolmadıysa örneği.</span><span class="sxs-lookup"><span data-stu-id="d9196-148">An HttpMessageHandler instance may be reused from the pool when creating a new `HttpClient` instance if its lifetime hasn't expired.</span></span>

<span data-ttu-id="d9196-149">Her işleyicisi genellikle kendi temel alınan HTTP bağlantıları yöneten işleyicileri havuzu tercih edilir; gerekenden daha fazla işleyicileri oluşturma bağlantı gecikmelerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9196-149">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="d9196-150">Bazı işleyiciler da bağlantıları açık süresiz olarak, DNS değişiklikleri tepki gelen, işleyici engelleyebilir tutun.</span><span class="sxs-lookup"><span data-stu-id="d9196-150">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="d9196-151">Havuzdaki HttpMessageHandler nesnelerin süreyi havuzundaki HttpMessageHandler örneği yeniden kullanılabilir olan bir ömre sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d9196-151">The HttpMessageHandler objects in the pool have a lifetime that is the length of time that an HttpMessageHandler instance in the pool can be reused.</span></span> <span data-ttu-id="d9196-152">Varsayılan değer iki dakika, ancak adlandırılmış ya da yazılı istemci ayrı kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="d9196-152">The default value is two minutes, but it can be overridden per named or typed client basis.</span></span> <span data-ttu-id="d9196-153">Geçersiz kılmak için aşağıdaki kodda gösterildiği gibi istemci oluştururken, döndürülen IHttpClientBuilder SetHandlerLifetime() çağırın.</span><span class="sxs-lookup"><span data-stu-id="d9196-153">To override it, call SetHandlerLifetime() on the IHttpClientBuilder that is returned when creating the client, as shown in the following code.</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="d9196-154">Her bir türü belirlenmiş istemci veya adlandırılmış istemci kendi yapılandırılmış işleyici ömrü değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9196-154">Each typed client or named client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="d9196-155">Yaşam süresi işleyicisi sona erme devre dışı bırakmak için InfiniteTimeSpan ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d9196-155">Set the lifetime to InfiniteTimeSpan to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="d9196-156">Eklenen ve yapılandırılmış HttpClient kullanan, türü belirlenmiş istemci sınıfları uygulama</span><span class="sxs-lookup"><span data-stu-id="d9196-156">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="d9196-157">Önceki bir adım olarak tanımlanan sınıflar 'BasketService', 'CatalogService', 'OrderingService' vb. gibi örnek kod gibi türü belirlenmiş istemci sınıfları olması gerekir: bir türü belirlenmiş istemci kabul eden bir sınıftır bir `HttpClient` nesne (aracılığıyla eklenen kendi Oluşturucu) ve bazı uzak bir HTTP hizmetine çağrı yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9196-157">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A typed client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="d9196-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d9196-158">For example:</span></span>

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

<span data-ttu-id="d9196-159">Türü belirlenmiş istemci (örnekte CatalogService) herhangi bir kayıtlı hizmeti HttpClient yanı sıra kendi oluşturucusuna kabul edebilir, yani DI (bağımlılık ekleme) tarafından etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d9196-159">The typed client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="d9196-160">Türü belirlenmiş istemci, etkili bir şekilde, geçici bir nesne bir gereken her seferinde yeni bir örneği oluşturulur ve yeni bir alırsınız anlamına gelir `HttpClient` , oluşturulan her zaman örneği.</span><span class="sxs-lookup"><span data-stu-id="d9196-160">A typed client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it is constructed.</span></span> <span data-ttu-id="d9196-161">Ancak, havuzdaki HttpMessageHandler nesneler tarafından birden çok Http isteklerini yeniden nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="d9196-161">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="d9196-162">Türü belirlenmiş istemci sınıfları kullanın</span><span class="sxs-lookup"><span data-stu-id="d9196-162">Use your Typed Client classes</span></span>

<span data-ttu-id="d9196-163">Türü sınıflarınızı uygulanmış olan ve onlara AddHttpClient() ile kayıtlı sonra son olarak, bunu herhangi bir yere Hizmetleri DI tarafından örneğin herhangi bir Razor sayfası kod veya herhangi bir MVC web uygulaması denetleyicisinde gibi aşağıdaki kod, eklenmiş olabilir kullanabilirsiniz Hizmetine.</span><span class="sxs-lookup"><span data-stu-id="d9196-163">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="d9196-164">Bu noktaya kadar gösterilen kod yalnızca normal Http isteği gerçekleştiriyor, ancak burada, ilkeleri ekleyip, kayıtlı işleyicileri için temsilci seçme yalnızca yazdığınız istemciler, tüm Http istekleri yapılması aşağıdaki bölümlerde 'sihirden' gelen `HttpClient` olur alırken hesap dayanıklı ilkeleri üstel geri alma, devre Kesiciler ve kimlik doğrulama belirteçlerini veya herhangi bir özel özellik kullanma gibi ek güvenlik özellikleri uygulamak için tüm diğer özel temsilci işleyicisi ile yeniden gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="d9196-164">Until this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered typed clients, all the Http requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 


## <a name="additional-resources"></a><span data-ttu-id="d9196-165">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d9196-165">Additional resources</span></span>

-   <span data-ttu-id="d9196-166">**.NET Core 2.1 HttpClientFactory kullanma**
    [*https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span><span class="sxs-lookup"><span data-stu-id="d9196-166">**Using HttpClientFactory in .NET Core 2.1**
[*https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span></span>


-   <span data-ttu-id="d9196-167">**HttpClientFactory GitHub deposu**</span><span class="sxs-lookup"><span data-stu-id="d9196-167">**HttpClientFactory GitHub repo**</span></span>

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)



>[!div class="step-by-step"]
<span data-ttu-id="d9196-168">[Önceki] (explore-custom-http-call-retries-exponential-backoff.md) [İleri] (implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="d9196-168">[Previous] (explore-custom-http-call-retries-exponential-backoff.md) [Next] (implement-http-call-retries-exponential-backoff-polly.md)</span></span>
