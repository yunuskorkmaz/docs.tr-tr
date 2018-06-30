---
title: HTTP çağrısı deneme üstel geri alma ile Polly ile uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | HTTP çağrısı deneme üstel geri alma ile Polly ile uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: cce1392bb381859e7cad89c9f2518113241ae724
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106937"
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="4d798-103">HTTP çağrısı deneme üstel geri alma ile Polly ile uygulama</span><span class="sxs-lookup"><span data-stu-id="4d798-103">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="4d798-104">Açık kaynak gibi daha gelişmiş .NET kitaplıklarına yararlanmak için yeniden deneme üstel geri alma ile için önerilen yaklaşım olan [Polly](https://github.com/App-vNext/Polly) kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="4d798-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="4d798-105">Polly esnekliği ve geçici hata işleme yetenekleri sağlayan bir .NET kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="4d798-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="4d798-106">Bu özellikler kolayca yeniden deneme devre kesici, Bulkhead yalıtımı, zaman aşımı ve geri dönüş gibi Polly ilkelerini uygulayarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d798-106">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="4d798-107">Polly hedefler .NET 4.x ve .NET Standard sürüm 1.0 (hangi .NET Core destekler).</span><span class="sxs-lookup"><span data-stu-id="4d798-107">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="4d798-108">Yeniden deneme ilkesi Polly içinde eShopOnContainers HTTP yeniden deneme uygularken kullanılan yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="4d798-108">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="4d798-109">Standart HttpClient işlevini veya Polly, kullanmak istediğiniz hangi yeniden deneme ilkesi yapılandırmasına bağlı olarak kullanarak HttpClient esnek bir sürümünü ekleme için bir arabirimi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d798-109">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="4d798-110">Aşağıdaki örnek eShopOnContainers içinde uygulanan arabirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d798-110">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="4d798-111">Geliştirme veya basit yaklaşımlardan sınama esnek bir mekanizma olarak kullanmak istemiyorsanız, standart uygulama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d798-111">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="4d798-112">Aşağıdaki kod standart HttpClient uygulama izin verme isteği kimlik doğrulama belirteçleri ile isteğe bağlı bir durum olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d798-112">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="4d798-113">Başka bir, benzer sınıfı ancak Polly kullanmak istediğiniz dayanıklı mekanizmalar uygulaması kullanmayı kod ilginç uygulamasıdır — üstel geri alma ile aşağıdaki örnekte, yeniden deneme sayısı.</span><span class="sxs-lookup"><span data-stu-id="4d798-113">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="4d798-114">Polly ile bir yeniden deneme ilkesi sayısıyla yeniden deneme, üstel geri alma yapılandırma ve hata günlüğü gibi bir HTTP özel durum olduğunda gerçekleştirilecek eylemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4d798-114">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="4d798-115">Bu durumda, ilke türleri IOC kapsayıcısında kaydedilirken belirtilen sayıda deneyecek şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4d798-115">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="4d798-116">Kod HttpRequest istisna algıladığında üstel geri alma yapılandırması nedeniyle, Http isteği bir katlanarak İlkesi nasıl yapılandırılmış bağlı olarak artırır zaman miktarı bekledikten sonra yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="4d798-116">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="4d798-117">Önemli HttpInvoker, HTTP isteklerini bu yardımcı sınıf boyunca kılan olduğu yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="4d798-117">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="4d798-118">Yöntemi dahili olan HTTP isteği yürütür \_yeniden deneme ilkesi dikkate alır policyWrapper.ExecuteAsync.</span><span class="sxs-lookup"><span data-stu-id="4d798-118">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="4d798-119">İçinde eShopOnContainers Polly ilkeleri aşağıdaki kod olduğu gibi IOC kapsayıcı türlerini kaydedilirken belirttiğiniz [MVC web uygulaması haline adresindeki](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4d798-119">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="4d798-120">Böylece TCP bağlantılarını verimli bir şekilde hizmeti tarafından kullanılan IHttpClient nesneleri yerine bir singleton geçici olarak olarak örneği oluşturulmadan unutmayın ve [yuvaları ile ilgili bir sorunu](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="4d798-120">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="4d798-121">Ancak önemli dayanıklılığı hakkında CreateResilientHttpClient yöntemi ResilientHttpClientFactory içinde Polly WaitAndRetryAsync İlkesi uygulama aşağıdaki kodda gösterildiği şekilde noktadır:</span><span class="sxs-lookup"><span data-stu-id="4d798-121">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="4d798-122">[Önceki](implement-custom-http-call-retries-exponential-backoff.md)
[sonraki](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="4d798-122">[Previous](implement-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
