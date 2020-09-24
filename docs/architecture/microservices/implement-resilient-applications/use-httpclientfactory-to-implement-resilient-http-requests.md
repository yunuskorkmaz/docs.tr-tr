---
title: Dayanıklı HTTP isteklerini uygulamak için IHttpClientFactory kullanma
description: .NET Core 2,1 ' den bu yana sunulan ıhttpclientfactory kullanarak, örnek oluşturmak için, `HttpClient` bunu uygulamalarınızda kullanmanızı kolaylaştırmayı öğrenin.
ms.date: 08/31/2020
ms.openlocfilehash: ae093ef960b2540bf4916bf72ad3bec51fa33ebe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152578"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Dayanıklı HTTP isteklerini uygulamak için IHttpClientFactory kullanma

<xref:System.Net.Http.IHttpClientFactory> , `DefaultHttpClientFactory` uygulamalarınızda kullanılacak örnekleri oluşturmak için .NET Core 2,1 ' den beri sunulan, OPTA uygulanmış bir fabrika olan tarafından uygulanan bir sözleşmedir <xref:System.Net.Http.HttpClient> .

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 'da sunulan özgün HttpClient sınıfı ile ilgili sorunlar

Özgün ve iyi bilinen <xref:System.Net.Http.HttpClient> sınıf kolayca kullanılabilir, ancak bazı durumlarda birçok geliştirici tarafından düzgün şekilde kullanılmamalıdır.

Bu sınıf `IDisposable` , `using` `HttpClient` nesne aktiften çıkarıldığında, temeldeki yuva hemen serbest bırakılmadığı ve bir _yuva tükenmesi_ sorununa yol açabilecek için bir deyimin içinde bunu uygulayan, örneklenmemiş, örnek oluşturma ve örnekleme tercih edilmez. Bu sorun hakkında daha fazla bilgi için, HttpClient kullanan blog gönderisine göz atın [ve yazılımınızı sabitleyen hale gelir](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Bu nedenle, `HttpClient` bir kez örneğinin oluşturulması ve bir uygulamanın ömrü boyunca yeniden kullanılması amaçlanmıştır. `HttpClient`Her istek için bir sınıfın örnekleniyor, ağır yüklerin altında bulunan yuva sayısını tükeder. Bu sorun hatalara neden olur `SocketException` . Bu sorunu çözmek için olası yaklaşımlar, `HttpClient` [HttpClient kullanımıyla Ilgili bu Microsoft makalesinde](../../../csharp/tutorials/console-webapiclient.md)açıklandığı gibi nesnenin tek veya statik olarak oluşturulmasına bağlıdır. Bu, kısa süreli konsol uygulamaları için iyi bir çözüm veya benzer şekilde, günde birkaç kez çalışan bir çözüm olabilir.

Geliştiricilerin üzerinde çalıştığı diğer bir sorun `HttpClient` da uzun süreli işlemlerde paylaşılan bir örnek kullanıyor. HttpClient 'ın tek veya statik bir nesne olarak örneklendiği bir durumda, DotNet/Runtime GitHub deposunun bu [sorunu](https://github.com/dotnet/runtime/issues/18348) konusunda AÇıKLANDıĞı gibi DNS değişikliklerini işleyemez.

Ancak, sorun `HttpClient` büyük bir dönem için değildir, ancak yukarıda bahsedilen yuva tükenmesi ve DNS değişiklik sorunları olan yeni bir somut örnek oluşturduğundan, [HttpClient için varsayılan oluşturucuya](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)sahip değildir <xref:System.Net.Http.HttpMessageHandler> . *sockets exhaustion*

Yukarıda bahsedilen sorunları gidermek ve örnekleri yönetilebilir hale getirmek için `HttpClient` .NET Core 2,1, <xref:System.Net.Http.IHttpClientFactory> `HttpClient` bağımlılık ekleme (dı) aracılığıyla bir uygulamadaki örnekleri yapılandırmak ve oluşturmak için kullanılabilecek arabirimi kullanıma sunmuştur. Ayrıca, HttpClient 'daki işleyiciler için temsilci atama özelliğinden yararlanmak üzere, Polly tabanlı ara yazılım için uzantılar sağlar.

[Polly](http://www.thepollyproject.org/) , geliştiricilerin önceden tanımlanmış bazı ilkeleri akıcı ve iş parçacığı açısından güvenli bir şekilde kullanarak uygulamalarına dayanıklılık eklemesine yardımcı olan geçici hata işleme bir kitaplıktır.

## <a name="benefits-of-using-ihttpclientfactory"></a>Ihttpclientfactory kullanmanın avantajları

<xref:System.Net.Http.IHttpClientFactory>Aynı zamanda uygulayan geçerli uygulamasının <xref:System.Net.Http.IHttpMessageHandlerFactory> aşağıdaki avantajları sunar:

- Mantıksal nesneleri adlandırmak ve yapılandırmak için merkezi bir konum sağlar `HttpClient` . Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Hizmet Aracısı) yapılandırabilirsiniz.
- ' Deki işleyicileri devrederek `HttpClient` ve Polly tabanlı ara yazılım kullanarak, dayanıklılık Için Polly ilkelerinin avantajlarından faydalanarak giden ara yazılım kavramını codime edin.
- `HttpClient` , giden HTTP istekleri için birlikte bağlanabilen işleyicileri temsilci seçme kavramına zaten sahiptir. HTTP istemcilerini fabrikaya kaydedebilir ve yeniden deneme, devre kesiciler vb. için Polly ilkeleri kullanmak üzere bir Polly işleyicisi kullanabilirsiniz.
- Kullanım ömrünü yönetmek <xref:System.Net.Http.HttpMessageHandler> için, belirtilen sorunları/ `HttpClient` yaşam sürelerini kendi başınıza yönetirken oluşabilecek sorunları önlemek için kullanabilirsiniz.

> [!TIP]
> , `HttpClient` İlişkili fabrika tarafından yönetildiğinden, dı tarafından eklenen örnekler güvenli bir şekilde atılamaz `HttpMessageHandler` . Aslında, eklenen `HttpClient` örnekler BIR dı perspektifinden *kapsamlandırılır* .

> [!NOTE]
> () Uygulamasının uygulanması, `IHttpClientFactory` `DefaultHttpClientFactory` NUGET paketindeki dı uygulamasına sıkı bir şekilde bağlıdır `Microsoft.Extensions.DependencyInjection` . Diğer dı kapsayıcılarını kullanma hakkında daha fazla bilgi için bu [GitHub tartışmasına](https://github.com/dotnet/extensions/issues/1345)bakın.

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Ihttpclientfactory kullanmanın birden çok yolu

Uygulamanızda kullanabileceğiniz çeşitli yollar vardır `IHttpClientFactory` :

- Temel kullanım
- Adlandırılmış Istemcileri kullan
- Yazılan Istemcileri kullan
- Oluşturulan Istemcileri kullanma

Kısaltma açısından bu kılavuzda, `IHttpClientFactory` türü belirlenmiş istemcileri (Hizmet Aracısı kalıbı) kullanmak için en yapısal olarak kullanılan yol gösterilmektedir. Ancak, tüm seçenekler belgelenmiştir ve şu anda [ `IHttpClientFactory` kullanımı kapsayan bu makalede](/aspnet/core/fundamentals/http-requests#consumption-patterns)listelenmiştir.

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Ihttpclientfactory ile yazılan Istemcileri kullanma

Bu nedenle, "yazılı Istemci" nedir? Yalnızca `HttpClient` belirli bir kullanım için önceden yapılandırılmış bir. Bu yapılandırma, temel sunucu, HTTP üstbilgileri veya zaman aşımları gibi belirli değerleri içerebilir.

Aşağıdaki diyagramda, yazılan Istemcilerin ile nasıl kullanıldığı gösterilmektedir `IHttpClientFactory` :

![Yazılan istemcilerin ıhttpclientfactory ile nasıl kullanıldığını gösteren diyagram.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Şekil 8-4**. `IHttpClientFactory`Türü belirtilmiş istemci sınıflarıyla kullanma.

Yukarıdaki görüntüde, bir `ClientService` (denetleyici veya istemci kodu tarafından kullanılan), `HttpClient` kayıtlı tarafından oluşturulan bir tarafından kullanılır `IHttpClientFactory` . Bu fabrika, ' `HttpMessageHandler` a bir havuzdan bir atar `HttpClient` . , `HttpClient` `IHttpClientFactory` Dı kapsayıcısına uzantı yöntemiyle kaydedilirken Polly 'in ilkeleriyle yapılandırılabilir <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> .

Yukarıdaki yapıyı yapılandırmak için, <xref:System.Net.Http.IHttpClientFactory> `Microsoft.Extensions.Http` için genişletme yöntemini içeren NuGet paketini yükleyerek uygulamanıza ekleyin <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . Bu genişletme yöntemi, `DefaultHttpClientFactory` arabirim için tek tek kullanılacak iç sınıfı kaydeder `IHttpClientFactory` . İçin geçici bir yapılandırma tanımlar <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> . Bir havuzdan alınan bu ileti işleyici ( <xref:System.Net.Http.HttpMessageHandler> nesne), `HttpClient` fabrikada döndürülen tarafından kullanılır.

Sonraki kodda, `AddHttpClient()` kullanması gereken yazılmış istemcileri (hizmet aracıları) kaydetmek için nasıl kullanılabileceğini görebilirsiniz `HttpClient` .

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

İstemci hizmetlerini önceki kodda gösterildiği gibi kaydetmek, `DefaultClientFactory` her hizmet için standart oluştur ' u oluşturur `HttpClient` .

Ayrıca, kayda örneğe özgü yapılandırma ekleyebilirsiniz, örneğin, temel adresi yapılandırabilir ve aşağıdaki kodda gösterildiği gibi bazı dayanıklılık ilkeleri ekleyebilirsiniz:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Yalnızca sake örneği için, sonraki kodda yukarıdaki ilkelerden birini görebilirsiniz:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

[Sonraki makalede](implement-http-call-retries-exponential-backoff-polly.md)Polly kullanma hakkında daha fazla ayrıntı bulabilirsiniz.

### <a name="httpclient-lifetimes"></a>HttpClient yaşam süreleri

`HttpClient`İçinden bir nesne aldığınızda `IHttpClientFactory` , yeni bir örnek döndürülür. Ancak `HttpClient` `HttpMessageHandler` , `IHttpClientFactory` süresi dolmadığı sürece kaynak tüketimini azaltmak için tarafından havuza alınmış ve yeniden kullanılan bir kullanır `HttpMessageHandler` .

Her işleyici genellikle kendi temel aldığı HTTP bağlantılarını yönettiğinden, işleyicilerin havuzlaması istenir; gerekenden daha fazla işleyici oluşturulması bağlantı gecikmeleri oluşmasına neden olabilir. Ayrıca, bazı işleyiciler bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine yeniden davranmasını engelleyebilir.

`HttpMessageHandler`Havuzdaki nesneler, havuzdaki bir örneğin yeniden kullanılabilmesi için gereken süre olan bir yaşam süresine sahiptir `HttpMessageHandler` . Varsayılan değer iki dakikadır, ancak türü belirlenmiş Istemci başına geçersiz kılınabilir. Bunu geçersiz kılmak için, `SetHandlerLifetime()` <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> aşağıdaki kodda gösterildiği gibi istemciyi oluştururken döndürülen ' i çağırın:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Her tür Istemcinin kendi yapılandırılmış işleyici yaşam süresi değeri olabilir. Kullanım süresini, `InfiniteTimeSpan` işleyicinin süre sonunu devre dışı bırakacak şekilde ayarlayın.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Eklenen ve yapılandırılmış HttpClient kullanan, yazılan Istemci sınıflarınızı uygulama

Önceki bir adım olarak, örnek kodda bulunan, örneğin ' BasketService ', ' CatalogService ', ' OrderingService ' vb. gibi belirlenmiş Istemci sınıflarının tanımlanmış olması gerekir. – türü belirtilmiş bir Istemci, bir nesneyi kabul eden `HttpClient` (Oluşturucusu aracılığıyla eklenen) ve bir uzak HTTP hizmetini çağırmak için onu kullanan bir sınıftır. Örneğin:

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

Türü belirtilmiş Istemci ( `CatalogService` örnekteki), dı (bağımlılık ekleme) tarafından etkinleştirilir, bu da öğesine ek olarak, oluşturucusunda kayıtlı bir hizmeti kabul edebileceği anlamına gelir `HttpClient` .

Türü belirtilmiş bir Istemci etkin bir şekilde geçici bir nesnedir. Bu, her gerektiğinde yeni bir örnek oluşturulduğu anlamına gelir. Her oluşturulduğu zaman yeni bir `HttpClient` örnek alır. Ancak, `HttpMessageHandler` havuzdaki nesneler birden çok örnek tarafından yeniden kullanılan nesnelerdir `HttpClient` .

### <a name="use-your-typed-client-classes"></a>Türsüz Istemci sınıflarınızı kullanın

Son olarak, klavyeyle oluşturulmuş sınıflarınız uygulandıktan sonra, ile kaydolmasını ve yapılandırmasını sağlayabilirsiniz `AddHttpClient()` . Bundan sonra bu hizmetleri, DI tarafından eklenen hizmetlerin bulunduğu her yerde kullanabilirsiniz. Örneğin, bir MVC web uygulamasının Razor sayfa kodunda veya denetleyicisinde eShopOnContainers 'dan aşağıdaki kodda olduğu gibi:

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

Bu noktaya kadar, yukarıdaki kod parçacığı yalnızca normal HTTP istekleri gerçekleştirme örneğini göstermiştir. Ancak ' Magic ', tarafından yapılan tüm HTTP isteklerinin, `HttpClient` üstel geri alma, devre kesiciler, kimlik doğrulama belirteçlerini kullanan güvenlik özellikleri, hatta başka herhangi bir özel özellik ile yeniden denemeler gibi dayanıklı ilkelere sahip olduğunu gösteren aşağıdaki bölümlerde gelir. Tüm bunlar, yalnızca ilkeler eklenerek ve kayıtlı türü olan Istemcilerinize işleyiciler devrederken yapılabilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core 'da HttpClientFactory kullanma**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **GitHub deposundaki HttpClientFactory kaynak kodu `dotnet/extensions`**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**  
  <http://www.thepollyproject.org/>
  
- **Bağımlılık ekleme olmadan ıhttpclientfactory kullanma (GitHub sorunu)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Önceki](implement-resilient-entity-framework-core-sql-connections.md) 
> [Sonraki](implement-http-call-retries-exponential-backoff-polly.md)
