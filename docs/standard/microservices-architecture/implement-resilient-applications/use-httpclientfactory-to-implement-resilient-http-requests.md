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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Kullanım HttpClientFactory dayanıklı HTTP isteklerini uygulamak için

`HttpClientFactory` .NET Core 2.1 itibaren kullanılabilir kendine özgü tarzı olan bir factory oluşturmak için <xref:System.Net.Http.HttpClient> uygulamalarınızda kullanılacak örnekleri.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>' De .NET Core kullanılabilir özgün HttpClient sınıfı ile ilgili sorunlar

Özgün ve iyi bilinen [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) sınıfı kolayca kullanılabilir, ancak bazı durumlarda, düzgün bir şekilde çok sayıda geliştirici tarafından kullanılmıyor. 

Bu sınıf atılabilir olsa da, ilk bir sorun kullanmak `using` deyimi değil en iyi seçenek çünkü çıkardığınızda bile `HttpClient` nesne, temel alınan yuva hemen serbest bırakılmaz ve adlı ciddi bir soruna neden olabilecek ' yuvaları Tükenmesi '. Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient yanlış kullanıyorsanız ve bu yazılım destabilizing](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog gönderisi.

Bu nedenle, `HttpClient` kez oluşturulacak hedeflenen ve bir uygulamanın ömrü yeniden. Örnekleme bir `HttpClient` her istek ağır yük altında kullanılabilir yuva sayısını harcadıklarını anlamış için sınıf. Sorun sonuçlanır `SocketException` hataları. Bu sorunu çözmek için olası bir yaklaşım oluşturma işlemini dayalı `HttpClient` nesne tekil veya statik bu konuda açıklandığı gibi [HttpClient kullanımı Microsoft makalesi](/dotnet/csharp/tutorials/console-webapiclient). 

İkinci bir sorundur ancak `HttpClient` tekil veya statik nesne olarak kullandığınızda, olabilir. Bu durumda, tekli veya statik `HttpClient` DNS değişikliklerinin, bu konuda açıklandığı gibi uymuyor [.NET Core GitHub deposunu, sorunu](https://github.com/dotnet/corefx/issues/11224). 

Belirtilen sorunları gidermek ve yönetimini kolaylaştırmak için `HttpClient` örneklerini daha kolay, .NET Core 2.1 tanıtılan yeni bir `HttpClientFactory` , ayrıca Polly ile tümleştirerek dayanıklı HTTP çağrıları uygulamak için kullanılabilir.   

## <a name="what-is-httpclientfactory"></a>HttpClientFactory nedir

`HttpClientFactory` için tasarlanmıştır:

- Adlandırma ve mantıksal HttpClients yapılandırmak için merkezi bir konum sağlar. Örneğin, belirli bir mikro hizmet erişmek için önceden yapılandırılmış bir istemci (hizmet Aracısı) yapılandırabilirsiniz.
- Kod oluşturma işleyicileri temsilci aracılığıyla giden ara yazılım kavramını `HttpClient` ve dayanıklılık için Polly'nın ilkeleri yararlanmak için ara yazılımı Polly tabanlı uygulama.
- `HttpClient` Giden HTTP istekleri için birbirine işleyicileri temsilci olarak görevlendirme kavramı zaten sahip. Http istemcilerini Fabrika kaydetme ayrıca yeniden deneme CircuitBreakers, vb. için kullanılacak ilkeleri Polly izin veren bir Polly işleyicisi kullanabilirsiniz.
- Belirtilen sorunları/yönetirken oluşabilecek sorunları önlemek için HttpClientMessageHandlers ömrünü yönetmek `HttpClient` ömürleri kendiniz. 

## <a name="multiple-ways-to-use-httpclientfactory"></a>Birden çok yolu HttpClientFactory kullanın

Kullanabileceğiniz birkaç şekilde `HttpClientFactory` uygulamanızdaki:

- Kullanım `HttpClientFactory` doğrudan
- İstemciler adlı kullanın
- Türü belirlenmiş istemci kullanma
- Oluşturulan istemciler

Konuyu uzatmamak amacıyla, bu kılavuzu kullanmak için yapılandırılmış en yolu gösterir. `HttpClientFactory` yazılan istemciler (hizmet Aracısı deseni) kullanılacak olan, ancak tüm seçenekler belirtilmiştir ve bu şu anda listelenen [HttpClientFactory kullanım kapsayan makale ](/aspnet/core/fundamentals/http-requests?#consumption-patterns).  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Türü belirlenmiş istemci HttpClientFactory ile kullanma

Bu nedenle, bir "türü belirlenmiş istemci" nedir? Yalnızca olduğu bir `HttpClient` eklenmesiyle üzerine yapılandırılmış `DefaultHttpClientFactory`.

Aşağıdaki diyagramda yazılan istemcileri ile nasıl kullanıldığı gösterilmektedir `HttpClientFactory`:

![(Bir denetleyici veya istemci kodu tarafından kullanılır) bir ClientService kayıtlı IHttpClientFactory tarafından oluşturulan bir HttpClient kullanır. Bu fabrika HttpClient bir HttpMessageHandler yönettiği bir havuzdan atar. HttpClient IHttpClientFactory AddHttpClient genişletme yöntemi ile DI kapsayıcısında kaydederken Polly'nın ilkeleri ile yapılandırılabilir.](./media/image3.5.png)

**Şekil 8-4**. İstemci türü belirtilmiş sınıflarıyla HttpClientFactory kullanma.

İlk olarak, Kurulum `HttpClientFactory` uygulamanızda bir başvuru eklemeyi `Microsoft.Extensions.Http` içeren paketi `AddHttpClient()` genişletme yöntemi için `IServiceCollection`. Bu genişletme yöntemi kaydeder `DefaultHttpClientFactory` arabirimi tekil olarak kullanılacak `IHttpClientFactory`. Geçici bir yapılandırma için tanımladığı `HttpMessageHandlerBuilder`. Bu ileti işleyicisi (`HttpMessageHandler` nesne), uygulanan bir havuzdan tarafından kullanılan `HttpClient` fabrikadan döndürdü.

Sonraki kodunda gördüğünüz nasıl `AddHttpClient()` yazılan kullanması gereken istemciler (hizmet aracılar) kaydetmek için kullanılan `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Önceki kodda gösterildiği gibi istemci hizmetlerine kaydetme yapar `DefaultClientFactory` oluşturmak bir `HttpClient` paragrafında açıklayacağız olarak her hizmet için özel olarak yapılandırılmış.

İstemci hizmet sınıfınızı ile kaydederek yalnızca `AddHttpClient()`, `HttpClient` sınıfınıza eklenen nesne yapılandırması ve ilkelerini kayıt sırasında sağlanan kullanır. Sonraki bölümlerde, bu ilkeleri Polly'nın deneme veya devre Kesiciler gibi görürsünüz.

### <a name="httpclient-lifetimes"></a>HttpClient yaşam süresi yok

Aldığınız her seferinde bir `HttpClient` nesnesinden `IHttpClientFactory`, yeni bir örneği döndürülür. Ancak her `HttpClient` kullanan bir `HttpMessageHandler` , havuza alınmış olan ve tarafından yeniden `IHttpClientFactory` sürece kaynak tüketimini azaltmak için `HttpMessageHandler`'s taşınmadığından yaşam süresi doldu.

Her işleyicisi genellikle kendi temel alınan HTTP bağlantıları yöneten işleyicileri havuzu tercih edilir; gerekenden daha fazla işleyicileri oluşturma bağlantı gecikmelerine neden olabilir. Bazı işleyiciler da bağlantıları açık süresiz olarak, DNS değişiklikleri tepki gelen, işleyici engelleyebilir tutun.

`HttpMessageHandler` Havuzdaki nesnelerin sürenin uzunluğunu olan bir ömrü vardır, bir `HttpMessageHandler` havuzundaki örneği yeniden kullanılabilir. Varsayılan değer, iki dakika olmakla birlikte, türü belirlenmiş istemci geçersiz kılınabilir. Geçersiz kılmak için çağrı `SetHandlerLifetime()` üzerinde `IHttpClientBuilder` döndürülen istemci oluştururken aşağıdaki kodda gösterildiği gibi:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Her bir türü belirlenmiş istemci kendi yapılandırılmış işleyici ömrü değeri olabilir. Süresini ayarlamak `InfiniteTimeSpan` işleyicisi sona erme devre dışı bırakmak için.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Eklenen ve yapılandırılmış HttpClient kullanan, türü belirlenmiş istemci sınıfları uygulama

Önceki adımda tanımlanan sınıflar 'BasketService', 'CatalogService', 'OrderingService' vb. gibi örnek kod gibi türü belirlenmiş istemci sınıfları olması gerekir: bir türü belirlenmiş istemci kabul eden bir sınıf bir `HttpClient` nesne (aracılığıyla eklenen kendi Oluşturucu) ve bazı uzak bir HTTP hizmetine çağrı yapmak için kullanır. Örneğin:

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

Türü belirlenmiş istemci (örnekte CatalogService) DI HttpClient yanı sıra, yapıcısına bulunan kayıtlı bir hizmet kabul edebilir anlamına gelir (bağımlılık ekleme) tarafından etkinleştirilir.

Türü belirlenmiş bir istemci, etkili bir şekilde, geçici bir nesne bir gereken her seferinde yeni bir örneği oluşturulur ve yeni bir alırsınız anlamına gelir `HttpClient` , oluşturulan her zaman örneği. Ancak, havuzdaki HttpMessageHandler nesneler tarafından birden çok Http isteklerini yeniden nesnelerdir.

### <a name="use-your-typed-client-classes"></a>Türü belirlenmiş istemci sınıfları kullanın

Türü sınıflarınızı uygulanmış olan ve onlara AddHttpClient() ile kayıtlı sonra son olarak, bunu herhangi bir yere Hizmetleri DI tarafından örneğin herhangi bir Razor sayfası kod veya herhangi bir MVC web uygulaması denetleyicisinde gibi aşağıdaki kod, eklenmiş olabilir kullanabilirsiniz Hizmetine.

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

Bu noktaya kadar gösterilen kod yalnızca normal Http isteği gerçekleştiriyor, ancak aşağıdaki bölümlerde 'sihirden' gelen, yalnızca ilke ekleyerek ve temsilci yapılacak işleyicileri kayıtlı yazılmış istemciler için tüm HTTP istekleri `HttpClient` olur alırken hesap dayanıklı ilkeleri üstel geri alma, devre Kesiciler ve kimlik doğrulama belirteçlerini veya herhangi bir özel özellik kullanma gibi ek güvenlik özellikleri uygulamak için tüm diğer özel temsilci işleyicisi ile yeniden gibi davranır. 

## <a name="additional-resources"></a>Ek kaynaklar

- **' De .NET Core HttpClientFactory kullanma**\
  [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **HttpClientFactory GitHub deposu**\
  [*https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory*](https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory)

>[!div class="step-by-step"]
>[Önceki](explore-custom-http-call-retries-exponential-backoff.md)
>[İleri](implement-http-call-retries-exponential-backoff-polly.md)
