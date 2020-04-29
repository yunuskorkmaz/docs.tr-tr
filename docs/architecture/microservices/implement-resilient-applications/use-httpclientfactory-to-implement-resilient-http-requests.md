---
title: Dayanıklı HTTP isteklerini uygulamak için IHttpClientFactory kullanma
description: .NET Core 2,1 ' den bu yana sunulan ıhttpclientfactory kullanarak, örnek oluşturmak `HttpClient` için, bunu uygulamalarınızda kullanmanızı kolaylaştırmayı öğrenin.
ms.date: 03/03/2020
ms.openlocfilehash: ade26208a931faa456c8e267def2caef7a3f32de
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507305"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Dayanıklı HTTP isteklerini uygulamak için IHttpClientFactory kullanma

<xref:System.Net.Http.IHttpClientFactory>, uygulamalarınızda kullanılacak örnekleri oluşturmak `DefaultHttpClientFactory` <xref:System.Net.Http.HttpClient> için .NET Core 2,1 ' den beri sunulan, OPTA uygulanmış bir fabrika olan tarafından uygulanan bir sözleşmedir.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 'da sunulan özgün HttpClient sınıfı ile ilgili sorunlar

Özgün ve iyi bilinen <xref:System.Net.Http.HttpClient> sınıf kolayca kullanılabilir, ancak bazı durumlarda birçok geliştirici tarafından düzgün şekilde kullanılmamalıdır.

Bu `IDisposable`sınıf uygulanırken `using` , `HttpClient` nesne aktiften çıkarıldığında temeldeki yuva hemen serbest bırakılamadığından, bu sınıf bir bildirimde bildirilmek ve örneklenir, ancak bir _yuva tükenmesi_ sorununa yol açabilir. Bu sorun hakkında daha fazla bilgi için, HttpClient kullanan blog gönderisine göz atın [ve yazılımınızı sabitleyen hale gelir](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Bu nedenle `HttpClient` , bir kez örneğinin oluşturulması ve bir uygulamanın ömrü boyunca yeniden kullanılması amaçlanmıştır. Her istek `HttpClient` için bir sınıfın örnekleniyor, ağır yüklerin altında bulunan yuva sayısını tükeder. Bu sorun `SocketException` hatalara neden olur. Bu sorunu çözmek için olası yaklaşımlar, `HttpClient` [HttpClient kullanımıyla ilgili bu Microsoft makalesinde](../../../csharp/tutorials/console-webapiclient.md)açıklandığı gibi nesnenin tek veya statik olarak oluşturulmasına bağlıdır. Bu, kısa süreli konsol uygulamaları için ve günde birkaç kez çalıştırılan benzer şekilde iyi bir çözüm olabilir.

Geliştiricilerin ' de çalıştırdığı diğer bir sorun, uzun süre çalışan işlemlerde paylaşılan `HttpClient` bir örneğini kullanmaktır. HttpClient 'ın tek veya statik bir nesne olarak örneklendiği bir durumda, DotNet/Runtime GitHub deposunun bu [sorunu](https://github.com/dotnet/runtime/issues/18348) konusunda AÇıKLANDıĞı gibi DNS değişikliklerini işleyemez.

Ancak, sorun `HttpClient` büyük bir dönem için değildir, ancak yukarıda bahsedilen *yuva tükenmesi* ve DNS değişiklik sorunları olan yeni bir somut örnek <xref:System.Net.Http.HttpMessageHandler>oluşturduğundan, [HttpClient için varsayılan oluşturucuya](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)sahip değildir.

Yukarıda bahsedilen sorunları gidermek ve örnekleri yönetilebilir hale getirmek `HttpClient` Için .net Core 2,1, bağımlılık ekleme ( <xref:System.Net.Http.IHttpClientFactory> dı) aracılığıyla bir uygulamadaki örnekleri yapılandırmak ve oluşturmak `HttpClient` için kullanılabilecek arabirimi kullanıma sunmuştur. Ayrıca, HttpClient 'daki işleyiciler için temsilci atama özelliğinden yararlanmak üzere, Polly tabanlı ara yazılım için uzantılar sağlar.

[Polly](http://www.thepollyproject.org/) , geliştiricilerin önceden tanımlanmış bazı ilkeleri akıcı ve iş parçacığı açısından güvenli bir şekilde kullanarak uygulamalarına dayanıklılık eklemesine yardımcı olan geçici hata işleme bir kitaplıktır.

## <a name="benefits-of-using-ihttpclientfactory"></a>Ihttpclientfactory kullanmanın avantajları

Aynı zamanda uygulayan <xref:System.Net.Http.IHttpMessageHandlerFactory>geçerli <xref:System.Net.Http.IHttpClientFactory>uygulamasının aşağıdaki avantajları sunar:

- Mantıksal `HttpClient` nesneleri adlandırmak ve yapılandırmak için merkezi bir konum sağlar. Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Hizmet Aracısı) yapılandırabilirsiniz.
- ' Deki `HttpClient` işleyicileri devrederek ve Polly tabanlı ara yazılım kullanarak, dayanıklılık Için Polly ilkelerinin avantajlarından faydalanarak giden ara yazılım kavramını codime edin.
- `HttpClient`, giden HTTP istekleri için birlikte bağlanabilen işleyicileri temsilci seçme kavramına zaten sahiptir. HTTP istemcilerini fabrikaya kaydedebilir ve yeniden deneme, devre kesiciler vb. için Polly ilkeleri kullanmak üzere bir Polly işleyicisi kullanabilirsiniz.
- Kullanım ömrünü yönetmek <xref:System.Net.Http.HttpMessageHandler> için, belirtilen sorunları/yaşam sürelerini kendi başınıza yönetirken `HttpClient` oluşabilecek sorunları önlemek için kullanabilirsiniz.

> [!TIP]
> , `HttpClient` İlişkili `HttpMessageHandler` FABRIKA tarafından yönetildiğinden, dı tarafından eklenen örnekler güvenli bir şekilde atılamaz. Aslında, eklenen `HttpClient` örnekler bir dı perspektifinden *kapsamlandırılır* .

> [!NOTE]
> ( `IHttpClientFactory` `DefaultHttpClientFactory`) Uygulamasının uygulanması, `Microsoft.Extensions.DependencyInjection` NuGet paketindeki dı uygulamasına sıkı bir şekilde bağlıdır. Diğer dı kapsayıcılarını kullanma hakkında daha fazla bilgi için bu [GitHub tartışmasına](https://github.com/dotnet/extensions/issues/1345)bakın.

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Ihttpclientfactory kullanmanın birden çok yolu

Uygulamanızda kullanabileceğiniz `IHttpClientFactory` çeşitli yollar vardır:

- Temel kullanım
- Adlandırılmış Istemcileri kullan
- Yazılan Istemcileri kullan
- Oluşturulan Istemcileri kullanma

Kısaltma açısından bu kılavuzda, türü belirlenmiş Istemcileri (Hizmet Aracısı kalıbı) kullanmak için en yapısal `IHttpClientFactory`olarak kullanılan yol gösterilmektedir. Ancak, tüm seçenekler belgelenmiştir ve şu anda [ `IHttpClientFactory` kullanımı kapsayan bu makalede](/aspnet/core/fundamentals/http-requests#consumption-patterns)listelenmiştir.

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Ihttpclientfactory ile yazılan Istemcileri kullanma

Bu nedenle, "yazılı Istemci" nedir? Yalnızca belirli bir kullanım `HttpClient` için önceden yapılandırılmış bir. Bu yapılandırma, temel sunucu, HTTP üstbilgileri veya zaman aşımları gibi belirli değerleri içerebilir.

Aşağıdaki diyagramda, yazılan Istemcilerin ile `IHttpClientFactory`nasıl kullanıldığı gösterilmektedir:

![Yazılan istemcilerin ıhttpclientfactory ile nasıl kullanıldığını gösteren diyagram.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Şekil 8-4**. Türü `IHttpClientFactory` belirtilmiş istemci sınıflarıyla kullanma.

Yukarıdaki görüntüde, bir `ClientService` (denetleyici veya istemci kodu tarafından kullanılan), kayıtlı `HttpClient` `IHttpClientFactory`tarafından oluşturulan bir tarafından kullanılır. Bu fabrika, `HttpClient`' `HttpMessageHandler` a bir havuzdan bir atar. `HttpClient` , Dı kapsayıcısına uzantı yöntemiyle `IHttpClientFactory` <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>kaydedilirken Polly 'in ilkeleriyle yapılandırılabilir.

Yukarıdaki yapıyı yapılandırmak <xref:System.Net.Http.IHttpClientFactory> için, için `Microsoft.Extensions.Http` <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>genişletme yöntemini içeren NuGet paketini yükleyerek uygulamanıza ekleyin. Bu genişletme yöntemi, arabirim `DefaultHttpClientFactory` `IHttpClientFactory`için tek tek kullanılacak iç sınıfı kaydeder. İçin geçici bir yapılandırma tanımlar <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Bir havuzdan alınan bu<xref:System.Net.Http.HttpMessageHandler> ileti işleyici (nesne), fabrikada `HttpClient` döndürülen tarafından kullanılır.

Sonraki kodda, kullanması `AddHttpClient()` `HttpClient`gereken yazılmış istemcileri (hizmet aracıları) kaydetmek için nasıl kullanılabileceğini görebilirsiniz.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

İstemci hizmetlerini önceki kodda gösterildiği gibi kaydetmek, her hizmet için standart `DefaultClientFactory` `HttpClient` oluştur ' u oluşturur.

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

İçinden bir `HttpClient` nesne aldığınızda `IHttpClientFactory`, yeni bir örnek döndürülür. Ancak, `HttpClient` `HttpMessageHandler` `IHttpClientFactory` süresi dolmadığı sürece `HttpMessageHandler`kaynak tüketimini azaltmak için tarafından havuza alınmış ve yeniden kullanılan bir kullanır.

Her işleyici genellikle kendi temel aldığı HTTP bağlantılarını yönettiğinden, işleyicilerin havuzlaması istenir; gerekenden daha fazla işleyici oluşturulması bağlantı gecikmeleri oluşmasına neden olabilir. Ayrıca, bazı işleyiciler bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine yeniden davranmasını engelleyebilir.

Havuzdaki `HttpMessageHandler` nesneler, havuzdaki bir `HttpMessageHandler` örneğin yeniden kullanılabilmesi için gereken süre olan bir yaşam süresine sahiptir. Varsayılan değer iki dakikadır, ancak türü belirlenmiş Istemci başına geçersiz kılınabilir. Bunu geçersiz kılmak için, `SetHandlerLifetime()` aşağıdaki kodda <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> gösterildiği gibi istemciyi oluştururken döndürülen ' i çağırın:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Her tür Istemcinin kendi yapılandırılmış işleyici yaşam süresi değeri olabilir. Kullanım süresini `InfiniteTimeSpan` , işleyicinin süre sonunu devre dışı bırakacak şekilde ayarlayın.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Eklenen ve yapılandırılmış HttpClient kullanan, yazılan Istemci sınıflarınızı uygulama

Önceki bir adım olarak, örnek kodda bulunan, örneğin ' BasketService ', ' CatalogService ', ' OrderingService ' vb. gibi belirlenmiş Istemci sınıflarının tanımlanmış olması gerekir. – türü belirtilmiş bir Istemci, bir `HttpClient` nesneyi kabul eden (Oluşturucusu aracılığıyla eklenen) ve bır uzak HTTP hizmetini çağırmak için onu kullanan bir sınıftır. Örneğin:

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

Türü belirtilmiş Istemci (`CatalogService` örnekteki),, ' nin yanı sıra oluşturucudaki kayıtlı bir hizmeti kabul edebileceği anlamına gelir (bağımlılık ekleme) tarafından etkinleştirilir `HttpClient`.

Türü belirlenmiş bir Istemci, etkin bir şekilde geçici bir nesnedir, yani her gerektiğinde yeni bir örnek oluşturulur ve her oluşturulduğunda yeni `HttpClient` bir örnek alınır. Ancak, havuzdaki `HttpMessageHandler` nesneler birden çok `HttpClient` örnek tarafından yeniden kullanılan nesnelerdir.

### <a name="use-your-typed-client-classes"></a>Türsüz Istemci sınıflarınızı kullanın

Son olarak, yazdığınız sınıflar uygulandıktan ve ile kaydolduktan ve ile `AddHttpClient()`yapılandırıldıktan sonra, bu HIZMETLERI, dı tarafından eklenen hizmetlere sahip olduğunuz her yerde kullanabilirsiniz. Örneğin, bir MVC web uygulamasının Razor sayfa kodunda veya denetleyicisinde eShopOnContainers 'dan aşağıdaki kodda olduğu gibi:

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

Bu noktaya kadar, gösterilen kod yalnızca normal http isteklerini gerçekleştiriyor, ancak, ' Magic ', kayıtlı türü olan Istemcilerinize ilke ekleyerek ve işleyicileri temsilci seçerek, tarafından `HttpClient` yapılacak tüm http isteklerinin, üstel geri alma, devre kesiciler veya diğer özel temsilci seçme işleyicileriyle yeniden denemeler, kimlik doğrulama belirteçleri veya başka bir özel özellik gibi ek güvenlik özellikleri uygulamak için, daha fazla hesaba sahip olduğu durumlarda aşağıdaki bölümlerde gelir.

## <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core 'da HttpClientFactory kullanma**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **`dotnet/extensions` GitHub deposundaki HttpClientFactory kaynak kodu**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**  
  <http://www.thepollyproject.org/>
  
- **Bağımlılık ekleme olmadan ıhttpclientfactory kullanma (GitHub sorunu)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Önceki](implement-resilient-entity-framework-core-sql-connections.md)
>[İleri](implement-http-call-retries-exponential-backoff-polly.md)
