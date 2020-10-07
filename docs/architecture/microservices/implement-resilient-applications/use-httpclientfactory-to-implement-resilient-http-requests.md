---
title: Dayanıklı HTTP isteklerini uygulamak için IHttpClientFactory kullanma
description: .NET Core 2,1 ' den bu yana sunulan ıhttpclientfactory kullanarak, örnek oluşturmak için, `HttpClient` bunu uygulamalarınızda kullanmanızı kolaylaştırmayı öğrenin.
ms.date: 08/31/2020
ms.openlocfilehash: 4ebb82395dd685d30846b3549b654abf7c41d43f
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804815"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="72f11-103">Dayanıklı HTTP isteklerini uygulamak için IHttpClientFactory kullanma</span><span class="sxs-lookup"><span data-stu-id="72f11-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="72f11-104"><xref:System.Net.Http.IHttpClientFactory> , `DefaultHttpClientFactory` uygulamalarınızda kullanılacak örnekleri oluşturmak için .NET Core 2,1 ' den beri sunulan, OPTA uygulanmış bir fabrika olan tarafından uygulanan bir sözleşmedir <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="72f11-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="72f11-105">.NET Core 'da sunulan özgün HttpClient sınıfı ile ilgili sorunlar</span><span class="sxs-lookup"><span data-stu-id="72f11-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="72f11-106">Özgün ve iyi bilinen <xref:System.Net.Http.HttpClient> sınıf kolayca kullanılabilir, ancak bazı durumlarda birçok geliştirici tarafından düzgün şekilde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="72f11-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="72f11-107">Bu sınıf `IDisposable` , `using` `HttpClient` nesne aktiften çıkarıldığında, temeldeki yuva hemen serbest bırakılmadığı ve bir _yuva tükenmesi_ sorununa yol açabilecek için bir deyimin içinde bunu uygulayan, örneklenmemiş, örnek oluşturma ve örnekleme tercih edilmez.</span><span class="sxs-lookup"><span data-stu-id="72f11-107">Though this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="72f11-108">Bu sorun hakkında daha fazla bilgi için, HttpClient kullanan blog gönderisine göz atın [ve yazılımınızı sabitleyen hale gelir](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="72f11-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="72f11-109">Bu nedenle, `HttpClient` bir kez örneğinin oluşturulması ve bir uygulamanın ömrü boyunca yeniden kullanılması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="72f11-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="72f11-110">`HttpClient`Her istek için bir sınıfın örnekleniyor, ağır yüklerin altında bulunan yuva sayısını tükeder.</span><span class="sxs-lookup"><span data-stu-id="72f11-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="72f11-111">Bu sorun hatalara neden olur `SocketException` .</span><span class="sxs-lookup"><span data-stu-id="72f11-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="72f11-112">Bu sorunu çözmek için olası yaklaşımlar, `HttpClient` [HttpClient kullanımıyla Ilgili bu Microsoft makalesinde](../../../csharp/tutorials/console-webapiclient.md)açıklandığı gibi nesnenin tek veya statik olarak oluşturulmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="72f11-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="72f11-113">Bu, kısa süreli konsol uygulamaları için iyi bir çözüm veya benzer şekilde, günde birkaç kez çalışan bir çözüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="72f11-113">This can be a good solution for short-lived console apps or similar, that run a few times a day.</span></span>

<span data-ttu-id="72f11-114">Geliştiricilerin üzerinde çalıştığı diğer bir sorun `HttpClient` da uzun süreli işlemlerde paylaşılan bir örnek kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="72f11-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long-running processes.</span></span> <span data-ttu-id="72f11-115">HttpClient 'ın tek veya statik bir nesne olarak örneklendiği bir durumda, DotNet/Runtime GitHub deposunun bu [sorunu](https://github.com/dotnet/runtime/issues/18348) konusunda AÇıKLANDıĞı gibi DNS değişikliklerini işleyemez.</span><span class="sxs-lookup"><span data-stu-id="72f11-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/runtime/issues/18348) of the dotnet/runtime GitHub repository.</span></span>

<span data-ttu-id="72f11-116">Ancak, sorun `HttpClient` büyük bir dönem için değildir, ancak yukarıda bahsedilen yuva tükenmesi ve DNS değişiklik sorunları olan yeni bir somut örnek oluşturduğundan, [HttpClient için varsayılan oluşturucuya](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)sahip değildir <xref:System.Net.Http.HttpMessageHandler> . *sockets exhaustion*</span><span class="sxs-lookup"><span data-stu-id="72f11-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="72f11-117">Yukarıda bahsedilen sorunları gidermek ve örnekleri yönetilebilir hale getirmek için `HttpClient` .NET Core 2,1, <xref:System.Net.Http.IHttpClientFactory> `HttpClient` bağımlılık ekleme (dı) aracılığıyla bir uygulamadaki örnekleri yapılandırmak ve oluşturmak için kullanılabilecek arabirimi kullanıma sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="72f11-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="72f11-118">Ayrıca, HttpClient 'daki işleyiciler için temsilci atama özelliğinden yararlanmak üzere, Polly tabanlı ara yazılım için uzantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="72f11-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="72f11-119">[Polly](http://www.thepollyproject.org/) , geliştiricilerin önceden tanımlanmış bazı ilkeleri akıcı ve iş parçacığı açısından güvenli bir şekilde kullanarak uygulamalarına dayanıklılık eklemesine yardımcı olan geçici hata işleme bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="72f11-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="72f11-120">Ihttpclientfactory kullanmanın avantajları</span><span class="sxs-lookup"><span data-stu-id="72f11-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="72f11-121"><xref:System.Net.Http.IHttpClientFactory>Aynı zamanda uygulayan geçerli uygulamasının <xref:System.Net.Http.IHttpMessageHandlerFactory> aşağıdaki avantajları sunar:</span><span class="sxs-lookup"><span data-stu-id="72f11-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="72f11-122">Mantıksal nesneleri adlandırmak ve yapılandırmak için merkezi bir konum sağlar `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="72f11-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="72f11-123">Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Hizmet Aracısı) yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72f11-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="72f11-124">' Deki işleyicileri devrederek `HttpClient` ve Polly tabanlı ara yazılım kullanarak, dayanıklılık Için Polly ilkelerinin avantajlarından faydalanarak giden ara yazılım kavramını codime edin.</span><span class="sxs-lookup"><span data-stu-id="72f11-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="72f11-125">`HttpClient` , giden HTTP istekleri için birlikte bağlanabilen işleyicileri temsilci seçme kavramına zaten sahiptir.</span><span class="sxs-lookup"><span data-stu-id="72f11-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="72f11-126">HTTP istemcilerini fabrikaya kaydedebilir ve yeniden deneme, devre kesiciler vb. için Polly ilkeleri kullanmak üzere bir Polly işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72f11-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="72f11-127">Kullanım ömrünü yönetmek <xref:System.Net.Http.HttpMessageHandler> için, belirtilen sorunları/ `HttpClient` yaşam sürelerini kendi başınıza yönetirken oluşabilecek sorunları önlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72f11-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="72f11-128">, `HttpClient` İlişkili fabrika tarafından yönetildiğinden, dı tarafından eklenen örnekler güvenli bir şekilde atılamaz `HttpMessageHandler` .</span><span class="sxs-lookup"><span data-stu-id="72f11-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="72f11-129">Aslında, eklenen `HttpClient` örnekler BIR dı perspektifinden *kapsamlandırılır* .</span><span class="sxs-lookup"><span data-stu-id="72f11-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="72f11-130">() Uygulamasının uygulanması, `IHttpClientFactory` `DefaultHttpClientFactory` NUGET paketindeki dı uygulamasına sıkı bir şekilde bağlıdır `Microsoft.Extensions.DependencyInjection` .</span><span class="sxs-lookup"><span data-stu-id="72f11-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="72f11-131">Diğer dı kapsayıcılarını kullanma hakkında daha fazla bilgi için bu [GitHub tartışmasına](https://github.com/dotnet/extensions/issues/1345)bakın.</span><span class="sxs-lookup"><span data-stu-id="72f11-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="72f11-132">Ihttpclientfactory kullanmanın birden çok yolu</span><span class="sxs-lookup"><span data-stu-id="72f11-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="72f11-133">Uygulamanızda kullanabileceğiniz çeşitli yollar vardır `IHttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="72f11-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="72f11-134">Temel kullanım</span><span class="sxs-lookup"><span data-stu-id="72f11-134">Basic usage</span></span>
- <span data-ttu-id="72f11-135">Adlandırılmış Istemcileri kullan</span><span class="sxs-lookup"><span data-stu-id="72f11-135">Use Named Clients</span></span>
- <span data-ttu-id="72f11-136">Yazılan Istemcileri kullan</span><span class="sxs-lookup"><span data-stu-id="72f11-136">Use Typed Clients</span></span>
- <span data-ttu-id="72f11-137">Oluşturulan Istemcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="72f11-137">Use Generated Clients</span></span>

<span data-ttu-id="72f11-138">Kısaltma açısından bu kılavuzda, `IHttpClientFactory` türü belirlenmiş istemcileri (Hizmet Aracısı kalıbı) kullanmak için en yapısal olarak kullanılan yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72f11-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="72f11-139">Ancak, tüm seçenekler belgelenmiştir ve şu anda [ `IHttpClientFactory` kullanımı kapsayan bu makalede](/aspnet/core/fundamentals/http-requests#consumption-patterns)listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="72f11-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="72f11-140">Ihttpclientfactory ile yazılan Istemcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="72f11-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="72f11-141">Bu nedenle, "yazılı Istemci" nedir?</span><span class="sxs-lookup"><span data-stu-id="72f11-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="72f11-142">Yalnızca `HttpClient` belirli bir kullanım için önceden yapılandırılmış bir.</span><span class="sxs-lookup"><span data-stu-id="72f11-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="72f11-143">Bu yapılandırma, temel sunucu, HTTP üstbilgileri veya zaman aşımları gibi belirli değerleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="72f11-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="72f11-144">Aşağıdaki diyagramda, yazılan Istemcilerin ile nasıl kullanıldığı gösterilmektedir `IHttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="72f11-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![Yazılan istemcilerin ıhttpclientfactory ile nasıl kullanıldığını gösteren diyagram.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="72f11-146">**Şekil 8-4**.</span><span class="sxs-lookup"><span data-stu-id="72f11-146">**Figure 8-4**.</span></span> <span data-ttu-id="72f11-147">`IHttpClientFactory`Türü belirtilmiş istemci sınıflarıyla kullanma.</span><span class="sxs-lookup"><span data-stu-id="72f11-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="72f11-148">Yukarıdaki görüntüde, bir `ClientService` (denetleyici veya istemci kodu tarafından kullanılan), `HttpClient` kayıtlı tarafından oluşturulan bir tarafından kullanılır `IHttpClientFactory` .</span><span class="sxs-lookup"><span data-stu-id="72f11-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="72f11-149">Bu fabrika, ' `HttpMessageHandler` a bir havuzdan bir atar `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="72f11-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="72f11-150">, `HttpClient` `IHttpClientFactory` Dı kapsayıcısına uzantı yöntemiyle kaydedilirken Polly 'in ilkeleriyle yapılandırılabilir <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> .</span><span class="sxs-lookup"><span data-stu-id="72f11-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A>.</span></span>

<span data-ttu-id="72f11-151">Yukarıdaki yapıyı yapılandırmak için, <xref:System.Net.Http.IHttpClientFactory> `Microsoft.Extensions.Http` için genişletme yöntemini içeren NuGet paketini yükleyerek uygulamanıza ekleyin <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="72f11-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="72f11-152">Bu genişletme yöntemi, `DefaultHttpClientFactory` arabirim için tek tek kullanılacak iç sınıfı kaydeder `IHttpClientFactory` .</span><span class="sxs-lookup"><span data-stu-id="72f11-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="72f11-153">İçin geçici bir yapılandırma tanımlar <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> .</span><span class="sxs-lookup"><span data-stu-id="72f11-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="72f11-154">Bir havuzdan alınan bu ileti işleyici ( <xref:System.Net.Http.HttpMessageHandler> nesne), `HttpClient` fabrikada döndürülen tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72f11-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="72f11-155">Sonraki kodda, `AddHttpClient()` kullanması gereken yazılmış istemcileri (hizmet aracıları) kaydetmek için nasıl kullanılabileceğini görebilirsiniz `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="72f11-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="72f11-156">İstemci hizmetlerini önceki kodda gösterildiği gibi kaydetmek, `DefaultClientFactory` her hizmet için standart oluştur ' u oluşturur `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="72f11-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="72f11-157">Ayrıca, kayda örneğe özgü yapılandırma ekleyebilirsiniz, örneğin, temel adresi yapılandırabilir ve aşağıdaki kodda gösterildiği gibi bazı dayanıklılık ilkeleri ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72f11-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="72f11-158">Yalnızca sake örneği için, sonraki kodda yukarıdaki ilkelerden birini görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72f11-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="72f11-159">[Sonraki makalede](implement-http-call-retries-exponential-backoff-polly.md)Polly kullanma hakkında daha fazla ayrıntı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72f11-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="72f11-160">HttpClient yaşam süreleri</span><span class="sxs-lookup"><span data-stu-id="72f11-160">HttpClient lifetimes</span></span>

<span data-ttu-id="72f11-161">`HttpClient`İçinden bir nesne aldığınızda `IHttpClientFactory` , yeni bir örnek döndürülür.</span><span class="sxs-lookup"><span data-stu-id="72f11-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="72f11-162">Ancak `HttpClient` `HttpMessageHandler` , `IHttpClientFactory` süresi dolmadığı sürece kaynak tüketimini azaltmak için tarafından havuza alınmış ve yeniden kullanılan bir kullanır `HttpMessageHandler` .</span><span class="sxs-lookup"><span data-stu-id="72f11-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="72f11-163">Her işleyici genellikle kendi temel aldığı HTTP bağlantılarını yönettiğinden, işleyicilerin havuzlaması istenir; gerekenden daha fazla işleyici oluşturulması bağlantı gecikmeleri oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="72f11-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="72f11-164">Ayrıca, bazı işleyiciler bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine yeniden davranmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="72f11-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="72f11-165">`HttpMessageHandler`Havuzdaki nesneler, havuzdaki bir örneğin yeniden kullanılabilmesi için gereken süre olan bir yaşam süresine sahiptir `HttpMessageHandler` .</span><span class="sxs-lookup"><span data-stu-id="72f11-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="72f11-166">Varsayılan değer iki dakikadır, ancak türü belirlenmiş Istemci başına geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="72f11-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="72f11-167">Bunu geçersiz kılmak için, `SetHandlerLifetime()` <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> aşağıdaki kodda gösterildiği gibi istemciyi oluştururken döndürülen ' i çağırın:</span><span class="sxs-lookup"><span data-stu-id="72f11-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="72f11-168">Her tür Istemcinin kendi yapılandırılmış işleyici yaşam süresi değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="72f11-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="72f11-169">Kullanım süresini, `InfiniteTimeSpan` işleyicinin süre sonunu devre dışı bırakacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72f11-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="72f11-170">Eklenen ve yapılandırılmış HttpClient kullanan, yazılan Istemci sınıflarınızı uygulama</span><span class="sxs-lookup"><span data-stu-id="72f11-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="72f11-171">Önceki bir adım olarak, örnek kodda bulunan, örneğin ' BasketService ', ' CatalogService ', ' OrderingService ' vb. gibi belirlenmiş Istemci sınıflarının tanımlanmış olması gerekir. – türü belirtilmiş bir Istemci, bir nesneyi kabul eden `HttpClient` (Oluşturucusu aracılığıyla eklenen) ve bir uzak HTTP hizmetini çağırmak için onu kullanan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="72f11-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="72f11-172">Örnek:</span><span class="sxs-lookup"><span data-stu-id="72f11-172">For example:</span></span>

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

<span data-ttu-id="72f11-173">Türü belirtilmiş Istemci ( `CatalogService` örnekteki), dı (bağımlılık ekleme) tarafından etkinleştirilir, bu da öğesine ek olarak, oluşturucusunda kayıtlı bir hizmeti kabul edebileceği anlamına gelir `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="72f11-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), that means it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="72f11-174">Türü belirtilmiş bir Istemci etkin bir şekilde geçici bir nesnedir. Bu, her gerektiğinde yeni bir örnek oluşturulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72f11-174">A Typed Client is effectively a transient object, that means a new instance is created each time one is needed.</span></span> <span data-ttu-id="72f11-175">Her oluşturulduğu zaman yeni bir `HttpClient` örnek alır.</span><span class="sxs-lookup"><span data-stu-id="72f11-175">It receives a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="72f11-176">Ancak, `HttpMessageHandler` havuzdaki nesneler birden çok örnek tarafından yeniden kullanılan nesnelerdir `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="72f11-176">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="72f11-177">Türsüz Istemci sınıflarınızı kullanın</span><span class="sxs-lookup"><span data-stu-id="72f11-177">Use your Typed Client classes</span></span>

<span data-ttu-id="72f11-178">Son olarak, klavyeyle oluşturulmuş sınıflarınız uygulandıktan sonra, ile kaydolmasını ve yapılandırmasını sağlayabilirsiniz `AddHttpClient()` .</span><span class="sxs-lookup"><span data-stu-id="72f11-178">Finally, once you have your typed classes implemented, you can have them registered and configured with `AddHttpClient()`.</span></span> <span data-ttu-id="72f11-179">Bundan sonra bu hizmetleri, DI tarafından eklenen hizmetlerin bulunduğu her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72f11-179">After that you can use them wherever have services injected by DI.</span></span> <span data-ttu-id="72f11-180">Örneğin, bir MVC web uygulamasının Razor sayfa kodunda veya denetleyicisinde eShopOnContainers 'dan aşağıdaki kodda olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="72f11-180">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="72f11-181">Bu noktaya kadar, yukarıdaki kod parçacığı yalnızca normal HTTP istekleri gerçekleştirme örneğini göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="72f11-181">Up to this point, the above code snippet has only shown the example of performing regular HTTP requests.</span></span> <span data-ttu-id="72f11-182">Ancak ' Magic ', tarafından yapılan tüm HTTP isteklerinin, `HttpClient` üstel geri alma, devre kesiciler, kimlik doğrulama belirteçlerini kullanan güvenlik özellikleri, hatta başka herhangi bir özel özellik ile yeniden denemeler gibi dayanıklı ilkelere sahip olduğunu gösteren aşağıdaki bölümlerde gelir.</span><span class="sxs-lookup"><span data-stu-id="72f11-182">But the 'magic' comes in the following sections where it shows how all the HTTP requests made by `HttpClient`, can have resilient policies such as retries with exponential backoff, circuit breakers, security features using auth tokens, or even any other custom feature.</span></span> <span data-ttu-id="72f11-183">Tüm bunlar, yalnızca ilkeler eklenerek ve kayıtlı türü olan Istemcilerinize işleyiciler devrederken yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="72f11-183">And all of these can be done just by adding policies and delegating handlers to your registered Typed Clients.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="72f11-184">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="72f11-184">Additional resources</span></span>

- <span data-ttu-id="72f11-185">**.NET Core 'da HttpClientFactory kullanma**</span><span class="sxs-lookup"><span data-stu-id="72f11-185">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="72f11-186">**GitHub deposundaki HttpClientFactory kaynak kodu `dotnet/extensions`**</span><span class="sxs-lookup"><span data-stu-id="72f11-186">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/v3.1.8/src/HttpClientFactory>

- <span data-ttu-id="72f11-187">**Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**</span><span class="sxs-lookup"><span data-stu-id="72f11-187">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="72f11-188">**Bağımlılık ekleme olmadan ıhttpclientfactory kullanma (GitHub sorunu)**</span><span class="sxs-lookup"><span data-stu-id="72f11-188">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="72f11-189">[Önceki](implement-resilient-entity-framework-core-sql-connections.md) 
> [Sonraki](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="72f11-189">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
