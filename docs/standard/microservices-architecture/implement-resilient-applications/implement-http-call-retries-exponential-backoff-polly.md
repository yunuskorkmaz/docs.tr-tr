---
title: HTTP çağrısı deneme üstel geri alma ile Polly ile uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | HTTP çağrısı deneme üstel geri alma ile Polly ile uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 66ac57fc824e01f96d6584ab86bb95ba1b0174a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>HTTP çağrısı deneme üstel geri alma ile Polly ile uygulama

Açık kaynak gibi daha gelişmiş .NET kitaplıklarına yararlanmak için yeniden deneme üstel geri alma ile için önerilen yaklaşım olan [Polly](https://github.com/App-vNext/Polly) kitaplığı.

Polly esnekliği ve geçici hata işleme yetenekleri sağlayan bir .NET kitaplıktır. Bu özellikler kolayca yeniden deneme devre kesici, Bulkhead yalıtımı, zaman aşımı ve geri dönüş gibi Polly ilkelerini uygulayarak uygulayabilirsiniz. Polly hedefler .NET 4.x ve .NET Standard sürüm 1.0 (hangi .NET Core destekler).

Yeniden deneme ilkesi Polly içinde eShopOnContainers HTTP yeniden deneme uygularken kullanılan yaklaşımdır. Standart HttpClient işlevini veya Polly, kullanmak istediğiniz hangi yeniden deneme ilkesi yapılandırmasına bağlı olarak kullanarak HttpClient esnek bir sürümünü ekleme için bir arabirimi uygulayabilirsiniz.

Aşağıdaki örnek eShopOnContainers içinde uygulanan arabirimi gösterir.

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

Geliştirme veya basit yaklaşımlardan sınama esnek bir mekanizma olarak kullanmak istemiyorsanız, standart uygulama kullanabilirsiniz. Aşağıdaki kod standart HttpClient uygulama izin verme isteği kimlik doğrulama belirteçleri ile isteğe bağlı bir durum olarak gösterir.

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

Başka bir, benzer sınıfı ancak Polly kullanmak istediğiniz dayanıklı mekanizmalar uygulaması kullanmayı kod ilginç uygulamasıdır — üstel geri alma ile aşağıdaki örnekte, yeniden deneme sayısı.

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

Polly ile bir yeniden deneme ilkesi sayısıyla yeniden deneme, üstel geri alma yapılandırma ve hata günlüğü gibi bir HTTP özel durum olduğunda gerçekleştirilecek eylemleri tanımlayın. Bu durumda, ilke türleri IOC kapsayıcısında kaydedilirken belirtilen sayıda deneyecek şekilde yapılandırılır. Kod HttpRequest istisna algıladığında üstel geri alma yapılandırması nedeniyle, Http isteği bir katlanarak İlkesi nasıl yapılandırılmış bağlı olarak artırır zaman miktarı bekledikten sonra yeniden dener.

Önemli HttpInvoker, HTTP isteklerini bu yardımcı sınıf boyunca kılan olduğu yöntemidir. Yöntemi dahili olan HTTP isteği yürütür \_yeniden deneme ilkesi dikkate alır policyWrapper.ExecuteAsync.

İçinde eShopOnContainers Polly ilkeleri aşağıdaki kod olduğu gibi IOC kapsayıcı türlerini kaydedilirken belirttiğiniz [MVC web uygulaması haline adresindeki](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) sınıfı.

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

Böylece TCP bağlantılarını verimli bir şekilde hizmeti tarafından kullanılan IHttpClient nesneleri yerine bir singleton geçici olarak olarak örneği oluşturulmadan unutmayın ve [yuvaları ile ilgili bir sorunu](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) gerçekleşmez.

Ancak önemli dayanıklılığı hakkında CreateResilientHttpClient yöntemi ResilientHttpClientFactory içinde Polly WaitAndRetryAsync İlkesi uygulama aşağıdaki kodda gösterildiği şekilde noktadır:

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
[Önceki] (implement-custom-http-call-retries-exponential-backoff.md) [sonraki] (uygulama-hattı-ayırıcı-pattern.md)
