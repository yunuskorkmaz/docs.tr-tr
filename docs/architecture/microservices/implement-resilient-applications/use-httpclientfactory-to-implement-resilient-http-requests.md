---
title: Esnek HTTP isteklerini uygulamak için IHttpClientFactory'yi kullanın
description: .NET Core 2.1'den beri kullanılabilen iHttpClientFactory'yi, örnek oluşturmak `HttpClient` ve uygulamalarınızda kullanmanızı kolaylaştırmak için nasıl kullanacağınızı öğrenin.
ms.date: 03/03/2020
ms.openlocfilehash: 088fb6c7e10ad656247ee4065da5c13d383b2cf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847225"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Esnek HTTP isteklerini uygulamak için IHttpClientFactory'yi kullanın

<xref:System.Net.Http.IHttpClientFactory>.NET Core 2.1'den beri kullanılabilen, uygulamalarınızda kullanılacak örnekler `DefaultHttpClientFactory` <xref:System.Net.Http.HttpClient> oluşturmak için, dik kafalı bir fabrika tarafından uygulanan bir sözleşmedir.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core'da bulunan orijinal HttpClient sınıfıyla ilgili sorunlar

Özgün ve iyi <xref:System.Net.Http.HttpClient> bilinen sınıf kolayca kullanılabilir, ancak bazı durumlarda, düzgün birçok geliştiriciler tarafından kullanılan değildir.

Bu sınıf uygular `IDisposable`iken , bir `using` ifade içinde beyan ve anlık tercih `HttpClient` edilmez, çünkü nesne bertaraf edildiğinde, altta yatan soket hemen serbest bırakılmaz, hangi bir _soket tükenme_ ssorununa yol açabilir. Bu sorun hakkında daha fazla bilgi için, [httpclient yanlış kullanıyorsanız ve yazılım ınızın istikrarını bozan](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)blog yazısına bakın.

Bu `HttpClient` nedenle, bir kez anlık ve bir uygulama ömrü boyunca yeniden tasarlanmıştır. Her istek için `HttpClient` bir sınıfın anında bulunması, ağır yükler altında bulunan soket sayısını tüketir. Bu sorun hatalara `SocketException` neden olur. Bu sorunu çözmek için olası yaklaşımlar, HttpClient kullanımı yla ilgili bu `HttpClient` Microsoft [makalesinde](../../../csharp/tutorials/console-webapiclient.md)açıklandığı gibi, nesnenin singleton veya statik olarak oluşturulmasına dayanır. Bu, kısa ömürlü konsol uygulamaları veya günde birkaç kez çalıştırılan benzerleri için iyi bir çözüm olabilir.

Geliştiricilerin karşısına çıkan bir diğer sorun `HttpClient` da, uzun süren işlemlerin paylaşılan bir örneğini kullanırken olmasıdır. HttpClient bir singleton veya statik bir nesne olarak instantiated bir durumda, dotnet / corefx GitHub deposunun bu [sayısında](https://github.com/dotnet/corefx/issues/11224) açıklandığı gibi DNS değişiklikleri işlemek için başarısız olur.

Ancak, `HttpClient` sorun gerçekten başına değil, [httpClient için varsayılan yapıcı](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)ile , yeni bir somut örnek <xref:System.Net.Http.HttpMessageHandler>oluşturur çünkü , *hangi soketleri tükenmesi* ve DNS değişiklikleri sorunları yukarıda belirtilen biridir.

Yukarıda belirtilen sorunları gidermek ve `HttpClient` örnekleri yönetilebilir hale getirmek için ,.NET <xref:System.Net.Http.IHttpClientFactory> Core 2.1 Bağımlılık Enjeksiyonu (DI) aracılığıyla bir uygulamada örnekleri yapılandırmak ve oluşturmak `HttpClient` için kullanılabilecek arabirimi tanıttı. Ayrıca, Polly tabanlı ara yazılımların HttpClient'da işleyicileri devretme avantajlarından yararlanması için uzantılar da sağlar.

[Polly,](http://www.thepollyproject.org/) geliştiricilerin önceden tanımlanmış bazı ilkeleri akıcı ve iş parçacığı güvenli bir şekilde kullanarak uygulamalarına esneklik eklemelerine yardımcı olan geçici bir hata işleme kitaplığıdır.

## <a name="benefits-of-using-ihttpclientfactory"></a>IHttpClientFactory kullanmanın faydaları

Geçerli uygulama <xref:System.Net.Http.IHttpClientFactory>, aynı zamanda <xref:System.Net.Http.IHttpMessageHandlerFactory>uygular , aşağıdaki yararları sunar:

- Mantıksal `HttpClient` nesneleri adlandırmak ve yapılandırmak için merkezi bir konum sağlar. Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Servis Aracısı) yapılandırabilirsiniz.
- Polly'nin esneklik politikalarından yararlanmak için işleyicileri atayarak `HttpClient` ve Polly tabanlı ara yazılımları uygulayarak giden ara yazılım kavramını kodlar.
- `HttpClient`zaten giden HTTP istekleri için birbirine bağlanabilir işleyicileri delegating kavramı vardır. HTTP istemcilerini fabrikaya kaydedebilirsiniz ve Retry, CircuitBreakers ve benzeri için Polly ilkelerini kullanmak için bir Polly işleyicisi kullanabilirsiniz.
- Yaşam ömürlerini <xref:System.Net.Http.HttpMessageHandler> yönetirken `HttpClient` oluşabilecek belirtilen sorunlardan/sorunlardan kaçınmak için kullanım ömrünü yönetin.

> [!TIP]
> DI `HttpClient` tarafından enjekte edilen örnekler, güvenli bir şekilde bertaraf `HttpMessageHandler` edilebilir, çünkü ilişkili fabrika tarafından yönetilir. Nitekim olarak, enjekte `HttpClient` edilen örnekler DI perspektifinden *scoped* edilir.

> [!NOTE]
> ( ) `IHttpClientFactory` `DefaultHttpClientFactory`uygulaması NuGet paketindeki DI uygulamasına `Microsoft.Extensions.DependencyInjection` sıkıca bağlıdır. Diğer DI kapsayıcıları kullanma hakkında daha fazla bilgi için bu [GitHub tartışmasına](https://github.com/dotnet/extensions/issues/1345)bakın.

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>IHttpClientFactory'yi kullanmanın birden çok yolu

Uygulamanızda kullanabileceğiniz `IHttpClientFactory` birkaç yol vardır:

- Temel kullanım
- Adlandırılmış İstemcileri Kullanma
- YazılMıZ İstemcileri Kullanma
- Oluşturulan İstemcileri Kullanma

Kısaltma uğruna, bu kılavuz, `IHttpClientFactory`Typed Clients (Service Agent deseni) kullanmak için en yapılandırılmış yolu gösterir. Ancak, tüm seçenekler belgelenmiştir ve şu anda [ `IHttpClientFactory` bu makalede kullanımı kapsayan](/aspnet/core/fundamentals/http-requests#consumption-patterns)listelenir.

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>IHttpClientFactory ile Typed İstemleri nasıl kullanılır?

"Yazılı İstemci" nedir? Bu sadece belirli `HttpClient` bir kullanım için önceden yapılandırılmış bir. Bu yapılandırma, temel sunucu, HTTP üstbilgi veya zaman açıkları gibi belirli değerleri içerebilir.

Aşağıdaki diyagram, Türetil İstemcilerin aşağıdakilerle `IHttpClientFactory`nasıl kullanıldığını gösterir:

![IHttpClientFactory ile yazılan istemcilerin nasıl kullanıldığını gösteren diyagram.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Şekil 8-4**. Typed Client sınıfları ile kullanma. `IHttpClientFactory`

Yukarıdaki resimde, bir `ClientService` (denetleyici veya istemci kodu tarafından `HttpClient` kullanılan) `IHttpClientFactory`kayıtlı tarafından oluşturulan bir . Bu fabrika bir `HttpMessageHandler` `HttpClient`havuzdan. Di `HttpClient` `IHttpClientFactory` kapsayıcıda uzantı yöntemi <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>ile kayıt yaparken Polly ilkeleri ile yapılandırılabilir.

Yukarıdaki yapıyı yapılandırmak <xref:System.Net.Http.IHttpClientFactory> için, `Microsoft.Extensions.Http` <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>''nin uzantı yöntemini <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> içeren NuGet paketini yükleyerek uygulamanızı ekleyin. Bu uzantı yöntemi, `DefaultHttpClientFactory` arabirim `IHttpClientFactory`için singleton olarak kullanılmak üzere dahili sınıfı kaydeder. Bu <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>için geçici bir yapılandırma tanımlar. Havuzdan alınan<xref:System.Net.Http.HttpMessageHandler> bu ileti işleyicisi (nesne), fabrikadan `HttpClient` döndürülen ler tarafından kullanılır.

Sonraki kodda, kullanması `AddHttpClient()` `HttpClient`gereken Typed İstemcileri (Servis Aracıları) kaydetmek için nasıl kullanılabileceğini görebilirsiniz.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Önceki kodda gösterildiği gibi istemci hizmetlerinin kaydedilmesi, `DefaultClientFactory` `HttpClient` oluşturmayı her hizmet için bir standart haline getirir.

Ayrıca, örneğin temel adresi yapılandırmak ve aşağıdaki kodda gösterildiği gibi bazı esneklik ilkeleri eklemek için kayıtta örneğe özgü yapılandırma da ekleyebilirsiniz:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Sadece örnek olarak, yukarıdaki ilkelerden birini sonraki kodda görebilirsiniz:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

[Sonraki makalede](implement-http-call-retries-exponential-backoff-polly.md)Polly kullanma hakkında daha fazla bilgi bulabilirsiniz.

### <a name="httpclient-lifetimes"></a>Httpİstem yaşam ları

Her zaman bir `HttpClient` nesne `IHttpClientFactory`almak , yeni bir örnek döndürülür. Ancak `HttpClient` her `HttpMessageHandler` biri, `HttpMessageHandler`'ömür süresi dolmamış `IHttpClientFactory` sayılmadığı sürece, kaynak tüketimini azaltmak için biraraya gelen ve yeniden kullanılan bir tane kullanır.

İşleyicilerin biraraya dolması, her işleyicinin genellikle kendi temel HTTP bağlantılarını yönettiği için istenir; gerekenden daha fazla işleyici oluşturmak bağlantı gecikmelerine neden olabilir. Bazı işleyiciler de bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine tepki sini engelleyebilir.

Havuzdaki `HttpMessageHandler` nesnelerin, havuzdaki bir `HttpMessageHandler` örneğin yeniden kullanılabileceğinigösteren bir kullanım ömrü vardır. Varsayılan değer iki dakikadır, ancak Typed İstemci başına geçersiz kılınabilir. Geçersiz kılmak için, `SetHandlerLifetime()` aşağıdaki <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> kodda gösterildiği gibi istemci oluşturulurken döndürülenleri arayın:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Her Typed İstemci kendi yapılandırılmış işleyicisi ömür boyu değeri olabilir. Kullanım ömrünü `InfiniteTimeSpan` işleyicinin sona erme tarihini devre dışı bırakacak şekilde ayarlayın.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Enjekte edilen ve yapılandırılan HttpClient'ı kullanan Typed Client sınıflarınızı uygulayın

Önceki adım olarak, 'BasketService', 'CatalogService', 'OrderingService' vb. gibi örnek koddaki sınıflar gibi Typed Client sınıflarınızın tanımlanması gerekir – Yazılı İstemci, bir `HttpClient` nesneyi kabul eden (oluşturucusu aracılığıyla enjekte edilen) ve bazı uzak HTTP hizmetini aramak için kullanan bir sınıftır. Örnek:

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

Typed Client`CatalogService` (örnekte) DI (Bağımlılık Enjeksiyonu) tarafından etkinleştirilir, yani kendi yapısında kayıtlı `HttpClient`herhangi bir hizmeti kabul edebilir, ek olarak .

Bir Typed İstemci, etkili bir şekilde, geçici bir nesnedir, yani her ihtiyaç duyulduğunda yeni bir örnek oluşturulur ve her oluşturulduğunda yeni `HttpClient` bir örnek alır. Ancak, `HttpMessageHandler` havuzdaki nesneler, birden çok `HttpClient` örnek tarafından yeniden kullanılan nesnelerdir.

### <a name="use-your-typed-client-classes"></a>Typed İstemci sınıflarınızı kullanma

Son olarak, yazdığınız sınıfları uyguladıktan ve bunları kaydettirdikten ve yapılandırdıktan `AddHttpClient()`sonra, bunları DI tarafından enjekte edilen hizmetleri kullanabileceğiniz her yerde kullanabilirsiniz. Örneğin, bir Jilet sayfa kodunda veya bir MVC web uygulamasının denetleyicisinde, eShopOnContainers'dan aşağıdaki kodda olduğu gibi:

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

Bu noktaya kadar, gösterilen kod sadece düzenli Http isteklerini yerine getirerek, ancak 'sihirli' aşağıdaki bölümlerde gelir, sadece politikalar ekleyerek ve kayıtlı Typed Müşterilere `HttpClient` işleyicileri atayarak, tüm HTTP istekleri tarafından yapılacak üstel geri dönüş, devre kesiciler veya diğer özel atama işleyicileri gibi ek güvenlik özellikleri uygulamak için, auth tokens, veya diğer özel özellikleri kullanarak gibi esnek politikaları dikkate alarak hareket edecektir.

## <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core'da HttpClientFactory kullanma**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **GitHub deposunda `dotnet/extensions` httpClientFactory kaynak kodu**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (.NET esneklik ve geçici hata işleme kitaplığı)**  
  <http://www.thepollyproject.org/>
  
- **Bağımlılık enjeksiyonu olmadan IHttpClientFactory kullanma (GitHub sorunu)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Önceki](implement-resilient-entity-framework-core-sql-connections.md)
>[Sonraki](implement-http-call-retries-exponential-backoff-polly.md)
