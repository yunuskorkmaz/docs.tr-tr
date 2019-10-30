---
title: Dayanıklı HTTP isteklerini uygulamak için HttpClientFactory kullanma
description: .NET Core 2,1 ' den bu yana sunulan HttpClientFactory ' ı kullanarak `HttpClient` örnekleri oluşturmaya, bunu uygulamalarınızda kullanmanızı kolaylaştırmayı öğrenin.
ms.date: 08/08/2019
ms.openlocfilehash: e32ffdd43ce8968ef9a0694873870b61510d7300
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093994"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Dayanıklı HTTP isteklerini uygulamak için HttpClientFactory kullanma

`HttpClientFactory`, .NET Core 2,1 ' den bu yana kullanılabilir olan ve uygulamalarınızda kullanılacak <xref:System.Net.Http.HttpClient> örnekleri oluşturmak için sunulan bir OPTA dağıtılmış fabrikadır.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 'da sunulan özgün HttpClient sınıfı ile ilgili sorunlar

Özgün ve iyi bilinen <xref:System.Net.Http.HttpClient> sınıfı kolayca kullanılabilir, ancak bazı durumlarda birçok geliştirici tarafından düzgün şekilde kullanılmamalıdır.

İlk bir sorun olarak, bu sınıf atılabilir olduğu halde, `using` ifadesiyle kullanılması en iyi seçenek değildir, çünkü `HttpClient` nesnesi atılırken, temeldeki yuva hemen serbest bırakılır ve ' yuva tükenmesi ' adlı ciddi bir soruna neden olabilir. Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient kullanıyorsunuz ve yazılım blog gönderinizi kararlı hale](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) getirme.

Bu nedenle, `HttpClient` bir kez oluşturulması ve bir uygulamanın ömrü boyunca yeniden kullanılması amaçlanmıştır. Her istek için bir `HttpClient` sınıfını örnekleme, ağır yüklerin altında bulunan yuva sayısını tükeder. Bu sorun `SocketException` hatalara neden olur. Bu sorunu çözmek için olası yaklaşımlar, [HttpClient kullanımındaki bu Microsoft makalesinde](../../../csharp/tutorials/console-webapiclient.md)açıklandığı gibi `HttpClient` nesnesinin tek veya statik olarak oluşturulmasına bağlıdır.

Ancak `HttpClient` ile tek veya statik nesne olarak kullandığınızda kullanabileceğiniz ikinci bir sorun vardır. Bu durumda, bir tek veya statik `HttpClient`, bu [sorun](https://github.com/dotnet/corefx/issues/11224) için DotNet/corefx GitHub deposunda AÇıKLANDıĞı gibi DNS değişikliklerine uymaz.

Söz konusu sorunları gidermek ve `HttpClient` örneklerinin yönetimini kolaylaştırmak için, .NET Core 2,1, Polly ile tümleştirerek dayanıklı HTTP çağrılarını uygulamak için de kullanılabilecek yeni bir `HttpClientFactory` sunmuştur.

[Polly](http://www.thepollyproject.org/) , geliştiricilerin önceden tanımlanmış bazı ilkeleri akıcı ve iş parçacığı açısından güvenli bir şekilde kullanarak uygulamalarına dayanıklılık eklemesine yardımcı olan geçici hata işleme kitaplığıdır.

## <a name="what-is-httpclientfactory"></a>HttpClientFactory nedir?

`HttpClientFactory` şu şekilde tasarlanmıştır:

- Mantıksal `HttpClient` nesnelerinin adlandırılması ve yapılandırılması için merkezi bir konum sağlayın. Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Hizmet Aracısı) yapılandırabilirsiniz.
- `HttpClient` 'de işleyiciler devrederek ve Polly tabanlı bir ara yazılım kullanarak, dayanıklılık açısından bir dizi işlem gerçekleştirerek giden ara yazılım kavramını codime edin.
- `HttpClient`, giden HTTP istekleri için birlikte bağlanabilen işleyicileri temsilci seçme kavramına zaten sahiptir. HTTP istemcilerini fabrikaya kaydedersiniz ve yeniden deneme, devre kesiciler ve benzeri bir ilke kullanmak için bir Polly işleyici kullanabilirsiniz.
- Belirtilen sorunları/`HttpClient` yaşam sürelerini yönetirken oluşabilecek sorunları önlemek için `HttpClientMessageHandlers` ömrünü yönetin.

> [!NOTE]
> `HttpClientFactory`, `Microsoft.Extensions.DependencyInjection` NuGet paketindeki bağımlılık ekleme (dı) uygulamasına sıkı bir şekilde bağlıdır. Diğer bağımlılık ekleme kapsayıcılarını kullanma hakkında daha fazla bilgi için bu [GitHub tartışmasına](https://github.com/aspnet/Extensions/issues/1345)bakın.

## <a name="multiple-ways-to-use-httpclientfactory"></a>HttpClientFactory kullanmanın birden çok yolu

Uygulamanızda `HttpClientFactory` kullanabileceğiniz çeşitli yollar vardır:

- `HttpClientFactory` doğrudan kullan
- Adlandırılmış Istemcileri kullan
- Yazılan Istemcileri kullan
- Oluşturulan Istemcileri kullanma

Kısaltma açısından bu kılavuzda, türü `HttpClientFactory` kullanmanın en yapısal yolu gösterilmektedir, bu, yazılan Istemcileri (Hizmet Aracısı deseninin) kullanmaktır. Ancak, tüm seçenekler belgelenmiştir ve şu anda [HttpClientFactory kullanımını kapsayan bu makalede](/aspnet/core/fundamentals/http-requests#consumption-patterns)listelenmiştir.

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>HttpClientFactory ile yazılan Istemcileri kullanma

Bu nedenle, "yazılı Istemci" nedir? Bu yalnızca, `DefaultHttpClientFactory` tarafından eklenen `HttpClient` yapılandırılmış bir.

Aşağıdaki diyagramda, yazılan Istemcilerin `HttpClientFactory` ile nasıl kullanıldığı gösterilmektedir:

![Bir ClientService (bir denetleyici veya istemci kodu tarafından kullanılan), kayıtlı ıhttpclientfactory tarafından oluşturulan bir HttpClient kullanır. Bu fabrika, HttpClient 'ı yönettiği bir havuzdan HttpMessageHandler öğesine atar. HttpClient, dı kapsayıcısına ıhttpclientfactory ' i AddHttpClient uzantı yöntemiyle kaydettirilirken, Polly 'nin ilkeleriyle yapılandırılabilir.](./media/image3.5.png)

**Şekil 8-4**. Türü belirtilmiş Istemci sınıflarıyla HttpClientFactory kullanma.

İlk olarak, `IServiceCollection` için `AddHttpClient()` uzantısı yöntemini içeren `Microsoft.Extensions.Http` NuGet paketini yükleyerek uygulamanızda `HttpClientFactory` ayarlayın. Bu genişletme yöntemi, arabirim `IHttpClientFactory` için bir tek olarak kullanılacak `DefaultHttpClientFactory` kaydeder. `HttpMessageHandlerBuilder`için geçici bir yapılandırma tanımlar. Bir havuzdan alınan bu ileti işleyicisi (`HttpMessageHandler` nesnesi), fabrikada döndürülen `HttpClient` tarafından kullanılır.

Sonraki kodda, `HttpClient` kullanması gereken yazılı Istemcileri (hizmet aracıları) kaydetmek için `AddHttpClient()` nasıl kullanılabileceğini görebilirsiniz.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Önceki kodda gösterildiği gibi istemci hizmetlerini kaydetme, `DefaultClientFactory` her hizmet için standart bir `HttpClient` oluşturmasını sağlar.

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

`IHttpClientFactory``HttpClient` bir nesne aldığınızda, yeni bir örnek döndürülür. Ancak her `HttpClient`, `HttpMessageHandler` süresinin süresinin dolmadığı sürece kaynak tüketimini azaltmak için `IHttpClientFactory` tarafından havuza alınmış ve yeniden kullanılan bir `HttpMessageHandler` kullanır.

Her işleyici genellikle kendi temel aldığı HTTP bağlantılarını yönettiğinden, işleyicilerin havuzlaması istenir; gerekenden daha fazla işleyici oluşturulması bağlantı gecikmeleri oluşmasına neden olabilir. Ayrıca, bazı işleyiciler bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine yeniden davranmasını engelleyebilir.

Havuzdaki `HttpMessageHandler` nesnelerinin ömrü, havuzdaki bir `HttpMessageHandler` örneğinin yeniden kullanılabilmesi için gereken süre. Varsayılan değer iki dakikadır, ancak türü belirlenmiş Istemci başına geçersiz kılınabilir. Bunu geçersiz kılmak için, aşağıdaki kodda gösterildiği gibi, istemcisi oluştururken döndürülen `IHttpClientBuilder` `SetHandlerLifetime()` çağırın:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Her tür Istemcinin kendi yapılandırılmış işleyici yaşam süresi değeri olabilir. İşleyici süre sonunu devre dışı bırakmak için yaşam süresini `InfiniteTimeSpan` olarak ayarlayın.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Eklenen ve yapılandırılmış HttpClient kullanan, yazılan Istemci sınıflarınızı uygulama

Önceki bir adım olarak, örnek kodda bulunan, örneğin ' BasketService ', ' CatalogService ', ' OrderingService ' vb. gibi belirlenmiş Istemci sınıflarının tanımlanması gerekir. türü belirtilmiş bir Istemci, bir `HttpClient` nesnesini kabul eden bir sınıftır ( Oluşturucu) ve bunu, uzak HTTP hizmetini çağırmak için kullanır. Örneğin:

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

Yazılan Istemci (örnekteki CatalogService), dı (bağımlılık ekleme) tarafından etkinleştirilir, yani, HttpClient ' a ek olarak oluşturucudaki kayıtlı bir hizmeti kabul edebilir.

Türü belirlenmiş bir Istemci, etkin bir şekilde geçici bir nesnedir, yani her gerektiğinde yeni bir örnek oluşturulur ve her oluşturulduğunda yeni bir `HttpClient` örneği alır. Ancak, havuzdaki HttpMessageHandler nesneleri birden çok http isteği tarafından yeniden kullanılan nesnelerdir.

### <a name="use-your-typed-client-classes"></a>Türsüz Istemci sınıflarınızı kullanın

Son olarak, klavyeyle oluşturulmuş sınıflarınız uygulandıktan ve `AddHttpClient()` ile kaydolduktan sonra, bu dosyaları, DI tarafından eklenen hizmetlere sahip olduğunuz her yerde kullanabilirsiniz. Örneğin, bir MVC web uygulamasının Razor sayfa kodunda veya denetleyicisinde eShopOnContainers 'dan aşağıdaki kodda olduğu gibi:

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

Bu noktaya kadar, gösterilen kod yalnızca normal http isteklerini gerçekleştiriyor, ancak ' Magic ', kayıtlı belirlenmiş Istemcilerinize ilke ekleyerek ve işleyicileri temsilci seçerek aşağıdaki bölümlerde bulunur, `HttpClient` tarafından yapılacak tüm HTTP istekleri çalışır üstel geri alma, devre kesiciler veya diğer özel temsilci seçme işleyicilerini, kimlik doğrulama belirteçlerini veya başka bir özel özelliği kullanmak gibi ek güvenlik özellikleri uygulayacak şekilde hesaba katılarak dayanıklı ilkeler alma.

## <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core 'da HttpClientFactory kullanma**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **`aspnet/Extensions` GitHub deposundaki HttpClientFactory kaynak kodu**  
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- **Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**  
  <http://www.thepollyproject.org/>
  
- **Bağımlılık ekleme olmadan HttpClientFactory kullanma (GitHub sorunu)**  
  <https://github.com/aspnet/Extensions/issues/1345>

>[!div class="step-by-step"]
>[Önceki](explore-custom-http-call-retries-exponential-backoff.md)
>[İleri](implement-http-call-retries-exponential-backoff-polly.md)
