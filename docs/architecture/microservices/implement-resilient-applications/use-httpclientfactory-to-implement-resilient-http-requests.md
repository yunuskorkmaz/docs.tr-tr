---
title: Dayanıklı HTTP isteklerini uygulamak için HttpClientFactory kullanma
description: .NET Core 2,1 ' den bu yana sunulan httpclientfactory kullanarak, örnek oluşturma `HttpClient` hakkında bilgi edinmek için, bunu uygulamalarınızda kullanmanızı kolaylaştırır.
ms.date: 01/07/2019
ms.openlocfilehash: 68c841a6ba69a94eff420233124cf00fec506502
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296040"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="79196-103">Dayanıklı HTTP isteklerini uygulamak için HttpClientFactory kullanma</span><span class="sxs-lookup"><span data-stu-id="79196-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="79196-104">`HttpClientFactory`, uygulamalarınızda kullanılacak örnekleri oluşturmak <xref:System.Net.Http.HttpClient> için .NET Core 2,1 ' den beri sunulan bir OPTA ve dağıtılmış bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="79196-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="79196-105">.NET Core 'da sunulan özgün HttpClient sınıfı ile ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="79196-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="79196-106">Özgün ve iyi bilinen [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) sınıfı kolayca kullanılabilir, ancak bazı durumlarda birçok geliştirici tarafından düzgün şekilde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="79196-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="79196-107">İlk bir sorun olarak, bu sınıf atılabilir olduğu halde, nesne atılırken `using` `HttpClient` bile, temel alınan yuva hemen yayınlanmaz ve ' yuvalar ' adlı ciddi bir soruna neden olabilir. tükenme.</span><span class="sxs-lookup"><span data-stu-id="79196-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="79196-108">Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient kullanıyorsunuz ve yazılım blog gönderinizi kararlı hale](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) getirme.</span><span class="sxs-lookup"><span data-stu-id="79196-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="79196-109">Bu nedenle `HttpClient` , bir kez örneğinin oluşturulması ve bir uygulamanın ömrü boyunca yeniden kullanılması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79196-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="79196-110">Her istek `HttpClient` için bir sınıfın örnekleniyor, ağır yüklerin altında bulunan yuva sayısını tükeder.</span><span class="sxs-lookup"><span data-stu-id="79196-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="79196-111">Bu sorun `SocketException` hatalara neden olur.</span><span class="sxs-lookup"><span data-stu-id="79196-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="79196-112">Bu sorunu çözmek için olası yaklaşımlar, `HttpClient` [HttpClient kullanımıyla ilgili bu Microsoft makalesinde](/dotnet/csharp/tutorials/console-webapiclient)açıklandığı gibi nesnenin tek veya statik olarak oluşturulmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="79196-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="79196-113">Ancak, bunu tek veya statik nesne `HttpClient` olarak kullandığınızda kullanabileceğiniz ikinci bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="79196-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="79196-114">Bu durumda, bir tek veya statik `HttpClient` , bu [sorun .NET Core GitHub](https://github.com/dotnet/corefx/issues/11224)deposunda açıklandığı gibi DNS değişikliklerine uymaz.</span><span class="sxs-lookup"><span data-stu-id="79196-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="79196-115">Söz konusu sorunları gidermek ve `HttpClient` örneklerin yönetimini kolaylaştırmak için, .NET Core 2,1, aynı zamanda Polly ile tümleştirerek dayanıklı http çağrıları uygulamak için de kullanılabilecek yeni `HttpClientFactory` bir kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="79196-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="79196-116">HttpClientFactory nedir?</span><span class="sxs-lookup"><span data-stu-id="79196-116">What is HttpClientFactory</span></span>

<span data-ttu-id="79196-117">`HttpClientFactory`şunları yapmak için tasarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="79196-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="79196-118">Mantıksal HttpClients adlandırmak ve yapılandırmak için merkezi bir konum sağlayın.</span><span class="sxs-lookup"><span data-stu-id="79196-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="79196-119">Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Hizmet Aracısı) yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79196-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="79196-120">' Deki `HttpClient` işleyicileri devrederek ve Polly tabanlı ara yazılım kullanarak, dayanıklılık için Polly ilkelerinin avantajlarından faydalanarak giden ara yazılım kavramını codime edin.</span><span class="sxs-lookup"><span data-stu-id="79196-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="79196-121">`HttpClient`, giden HTTP istekleri için birlikte bağlanabilen işleyicileri temsilci seçme kavramına zaten sahiptir.</span><span class="sxs-lookup"><span data-stu-id="79196-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="79196-122">Http istemcilerini fabrika 'ye kaydedersiniz ve yeniden deneme, devre kesiciler, vb. için, Polly ilkelerinin kullanılmasına izin veren bir Polly işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79196-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="79196-123">Belirtilen sorunları/süreleri kendi başınıza yönetirken `HttpClient` oluşabilecek sorunları önlemek için httpclientmessagehandlers 'ın ömrünü yönetin.</span><span class="sxs-lookup"><span data-stu-id="79196-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="79196-124">HttpClientFactory kullanmanın birden çok yolu</span><span class="sxs-lookup"><span data-stu-id="79196-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="79196-125">Uygulamanızda kullanabileceğiniz `HttpClientFactory` çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="79196-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="79196-126">Doğrudan `HttpClientFactory` kullanma</span><span class="sxs-lookup"><span data-stu-id="79196-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="79196-127">Adlandırılmış Istemcileri kullan</span><span class="sxs-lookup"><span data-stu-id="79196-127">Use Named Clients</span></span>
- <span data-ttu-id="79196-128">Yazılan Istemcileri kullan</span><span class="sxs-lookup"><span data-stu-id="79196-128">Use Typed Clients</span></span>
- <span data-ttu-id="79196-129">Oluşturulan Istemcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="79196-129">Use Generated Clients</span></span>

<span data-ttu-id="79196-130">Bu kılavuzda, bu kılavuzda, türü belirlenmiş istemcileri (Hizmet Aracısı kalıbı) kullanmak için kullanmanın `HttpClientFactory` en yapısal yolu gösterilmektedir, ancak tüm seçenekler belgelenmiştir ve şu anda [httpclientfactory kullanımını kapsayan bu makalede](/aspnet/core/fundamentals/http-requests?#consumption-patterns)listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="79196-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="79196-131">HttpClientFactory ile yazılan Istemcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="79196-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="79196-132">Bu nedenle, "yazılı Istemci" nedir?</span><span class="sxs-lookup"><span data-stu-id="79196-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="79196-133">Bu yalnızca `HttpClient` , `DefaultHttpClientFactory`tarafından eklenerek yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="79196-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="79196-134">Aşağıdaki diyagramda, yazılan Istemcilerin ile `HttpClientFactory`nasıl kullanıldığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="79196-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![Bir ClientService (bir denetleyici veya istemci kodu tarafından kullanılan), kayıtlı ıhttpclientfactory tarafından oluşturulan bir HttpClient kullanır.](./media/image3.5.png)

<span data-ttu-id="79196-138">**Şekil 8-4**.</span><span class="sxs-lookup"><span data-stu-id="79196-138">**Figure 8-4**.</span></span> <span data-ttu-id="79196-139">Türü belirtilmiş Istemci sınıflarıyla HttpClientFactory kullanma.</span><span class="sxs-lookup"><span data-stu-id="79196-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="79196-140">İlk olarak, `HttpClientFactory` uygulamanızda, için `AddHttpClient()` `IServiceCollection`genişletme yöntemini içeren `Microsoft.Extensions.Http` pakete bir başvuru ekleyerek ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="79196-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="79196-141">Bu genişletme yöntemi, `DefaultHttpClientFactory` arabirimi `IHttpClientFactory`için tek olarak kullanılacak öğesini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="79196-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="79196-142">İçin geçici bir yapılandırma tanımlar `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="79196-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="79196-143">Bir havuzdan alınan bu`HttpMessageHandler` ileti işleyici (nesne), fabrikada `HttpClient` döndürülen tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79196-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="79196-144">Sonraki kodda, kullanması `AddHttpClient()` `HttpClient`gereken yazılmış istemcileri (hizmet aracıları) kaydetmek için nasıl kullanılabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79196-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="79196-145">İstemci hizmetlerini önceki kodda gösterildiği gibi kaydetmek, `DefaultClientFactory` sonraki paragrafta açıklancağımız gibi, her bir hizmet için özel olarak yapılandırılmış bir `HttpClient` yapılandırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="79196-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="79196-146">İstemci hizmeti sınıfınızı ile `AddHttpClient()`kaydederek `HttpClient` , sınıfınıza eklenecek nesne kayıt sırasında sağlanmış yapılandırma ve ilkeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="79196-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="79196-147">Sonraki bölümlerde, Polly 'in yeniden denemeleri veya devre kesiciler gibi ilkeleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="79196-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="79196-148">HttpClient yaşam süreleri</span><span class="sxs-lookup"><span data-stu-id="79196-148">HttpClient lifetimes</span></span>

<span data-ttu-id="79196-149">İçinden bir `HttpClient` nesne aldığınızda ,yenibirörnekdöndürülür.`IHttpClientFactory`</span><span class="sxs-lookup"><span data-stu-id="79196-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="79196-150">`HttpMessageHandler` `HttpMessageHandler`Ancak, `HttpClient` süresidolmadığısürecekaynaktüketiminiazaltmakiçintarafındanhavuzaalınmışveyeniden`IHttpClientFactory` kullanılan bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="79196-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="79196-151">Her işleyici genellikle kendi temel aldığı HTTP bağlantılarını yönettiğinden, işleyicilerin havuzlaması istenir; gerekenden daha fazla işleyici oluşturulması bağlantı gecikmeleri oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="79196-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="79196-152">Ayrıca, bazı işleyiciler bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine yeniden davranmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="79196-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="79196-153">Havuzdaki nesneler, havuzdaki bir `HttpMessageHandler` örneğin yeniden kullanılabilmesi için gereken süre olan bir yaşam süresine sahiptir. `HttpMessageHandler`</span><span class="sxs-lookup"><span data-stu-id="79196-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="79196-154">Varsayılan değer iki dakikadır, ancak türü belirlenmiş Istemci başına geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="79196-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="79196-155">Bunu geçersiz kılmak için, `SetHandlerLifetime()` aşağıdaki kodda `IHttpClientBuilder` gösterildiği gibi istemciyi oluştururken döndürülen ' i çağırın:</span><span class="sxs-lookup"><span data-stu-id="79196-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="79196-156">Her tür Istemcinin kendi yapılandırılmış işleyici yaşam süresi değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="79196-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="79196-157">Kullanım süresini `InfiniteTimeSpan` , işleyicinin süre sonunu devre dışı bırakacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="79196-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="79196-158">Eklenen ve yapılandırılmış HttpClient kullanan, yazılan Istemci sınıflarınızı uygulama</span><span class="sxs-lookup"><span data-stu-id="79196-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="79196-159">Önceki bir adım olarak, örnek kodda bulunan, örneğin ' basketservice ', ' catalogservice ', ' orderingservice ' vb. gibi tür istemci sınıflarınızın tanımlanmış olması gerekir. – türü belirtilmiş bir istemci, bir `HttpClient` nesneyi kabul eden bir sınıftır ( Oluşturucu) ve bunu, uzak HTTP hizmetini çağırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="79196-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="79196-160">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="79196-160">For example:</span></span>

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

<span data-ttu-id="79196-161">Yazılan Istemci (örnekteki CatalogService), dı (bağımlılık ekleme) tarafından etkinleştirilir, yani, HttpClient ' a ek olarak oluşturucudaki kayıtlı bir hizmeti kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="79196-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="79196-162">Türü belirlenmiş bir istemci, etkin bir şekilde geçici bir nesnedir, yani her gerektiğinde yeni bir örnek oluşturulur ve her oluşturulduğunda yeni `HttpClient` bir örnek alınır.</span><span class="sxs-lookup"><span data-stu-id="79196-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="79196-163">Ancak, havuzdaki HttpMessageHandler nesneleri birden çok http isteği tarafından yeniden kullanılan nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="79196-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="79196-164">Türsüz Istemci sınıflarınızı kullanın</span><span class="sxs-lookup"><span data-stu-id="79196-164">Use your Typed Client classes</span></span>

<span data-ttu-id="79196-165">Son olarak, tür sınıflarınız uygulandıktan ve AddHttpClient () ile kaydolduktan sonra, bu hizmeti, örneğin her türlü Razor sayfası kodunda veya MVC web uygulamasının herhangi bir denetleyicisinde, örneğin, aşağıdaki kodda eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="79196-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="79196-166">Bu noktaya kadar, gösterilen kod yalnızca normal http isteklerini gerçekleştiriyor, ancak ' Magic ', kayıtlı belirlenmiş istemcilerinize ilke ekleyerek ve işleyicileri temsilci seçerek aşağıdaki bölümlerde bulunur, bu, tarafından `HttpClient` yapılacak tüm http isteklerinin , üstel geri alma, devre kesiciler veya diğer özel temsilci seçme işleyicilerini kullanarak, kimlik doğrulama belirteçleri veya başka bir özel özellik gibi ek güvenlik özellikleri uygulamak üzere dayanıklı ilkeleri hesaba katmaya davranır.</span><span class="sxs-lookup"><span data-stu-id="79196-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="79196-167">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="79196-167">Additional resources</span></span>

- <span data-ttu-id="79196-168">**.NET Core 'da HttpClientFactory kullanma**</span><span class="sxs-lookup"><span data-stu-id="79196-168">**Using HttpClientFactory in .NET Core**</span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="79196-169">**HttpClientFactory GitHub deposu**</span><span class="sxs-lookup"><span data-stu-id="79196-169">**HttpClientFactory GitHub repo**</span></span>\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
><span data-ttu-id="79196-170">[Önceki](explore-custom-http-call-retries-exponential-backoff.md)İleri
>[](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="79196-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
