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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Kullanım HttpClientFactory dayanıklı HTTP isteklerini uygulamak için

`HttpClientFactory` .NET Core 2.1 itibaren kullanılabilir kendine özgü tarzı olan bir factory oluşturmak için `HttpClient` uygulamalarınızda kullanılacak örnekleri. 

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>' De .NET Core kullanılabilir özgün HttpClient sınıfı ile ilgili sorunlar

Özgün ve iyi-bilmesi [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) sınıfı kolayca kullanılabilir, ancak bazı durumlarda, düzgün bir şekilde çok sayıda geliştirici tarafından kullanıldığı değil. 

Bu sınıf atılabilir olsa da, ilk bir sorun kullanmak `using` deyimi değil en iyi seçenek çünkü çıkardığınızda bile `HttpClient` nesne, temel alınan yuva hemen serbest bırakılmaz ve adlı ciddi bir soruna neden olabilecek ' yuvaları Tükenmesi '. Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient yanlış kullanıyorsanız ve bu yazılım destabilizing](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog gönderisi.

Bu nedenle, `HttpClient` kez oluşturulacak hedeflenen ve bir uygulamanın ömrü yeniden. Örnekleme bir `HttpClient` her istek ağır yük altında kullanılabilir yuva sayısını harcadıklarını anlamış için sınıf. Sorun sonuçlanır `SocketException` hataları. Bu sorunu çözmek için olası bir yaklaşım oluşturma işlemini dayalı `HttpClient` nesne tekil veya statik bu konuda açıklandığı gibi [HttpClient kullanımı Microsoft makalesi](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient). 

İkinci bir sorundur ancak `HttpClient` tekil veya statik nesne olarak kullandığınızda, olabilir. Bu durumda, tekli veya statik `HttpClient` DNS değişikliklerinin, bu konuda açıklandığı gibi uymuyor [.NET Core GitHub deposunu, sorunu](https://github.com/dotnet/corefx/issues/11224). 

Belirtilen sorunları gidermek ve yönetimini kolaylaştırmak için `HttpClient` örneklerini daha kolay, .NET Core 2.1 sunan yeni bir `HttpClientFactory` , ayrıca Polly ile tümleştirerek dayanıklı HTTP çağrıları uygulamak için kullanılabilir.   

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

Konuyu uzatmamak amacıyla, bu kılavuzu kullanmak için yapılandırılmış en yolu gösterir. `HttpClientFactory` yazılan istemciler (hizmet Aracısı deseni) kullanılacak olan, ancak tüm seçenekler belirtilmiştir ve bu şu anda listelenen [HttpClientFactory kullanım kapsayan makale ](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Türü belirlenmiş istemci HttpClientFactory ile kullanma

Aşağıdaki diyagramda, yazılan istemciler HttpClientFactory ile nasıl kullanılacağını gösterir.

![Diyagram ile yapılandırılmış bir HttpClient HttpClientFactory ve Polly'nın ilkeleri tarafından dahili olarak kullanarak bir eklenen ClientService kullanarak bir MVC denetleyicisi](./media/image3.5.png)

**Şekil 10-4**. Kullanarak `HttpClientFactory`ile yazılmış istemci sınıfları.

İlk olarak, Kurulum `HttpClientFactory` uygulamanızdaki. Bir başvuru ekleyin `Microsoft.Extensions.Http` içeren paket `AddHttpClient()` genişletme yöntemi için `IServiceCollection`. Bu genişletme yöntemi kaydeder `DefaultHttpClientFactory` arabirimi tekil olarak kullanılacak `IHttpClientFactory`. Geçici bir yapılandırma için tanımladığı `HttpMessageHandlerBuilder`. Bu ileti işleyicisi (`HttpMessageHandler` nesne), uygulanan bir havuzdan tarafından kullanılan `HttpClient` fabrikadan döndürdü.

Sonraki kodunda gördüğünüz nasıl `AddHttpClient()` yazılan kullanması gereken istemciler (hizmet aracılar) kaydetmek için kullanılan `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Türü belirlenmiş istemci sınıflarınızı AddHttpClient() ile yalnızca ekleyerek kullandığınızda `HttpClient` oluşturucusu, aracılığıyla sınıfınıza eklenen nesne, `HttpClient` tüm yapılandırması ve ilkelerini sağlanan nesne kullanacağınız. Sonraki bölümlerde, bu ilkeleri Polly'nın deneme veya devre Kesiciler gibi görürsünüz.

### <a name="httpclient-lifetimes"></a>HttpClient yaşam süresi yok

Aldığınız her seferinde bir `HttpClient` IHttpClientFactory, yeni bir örneğini nesneden bir `HttpClient` döndürülür. Olacak bir HttpMessageHandler ** başına türü belirlenmiş istemci adlı. Ben`HttpClientFactory` kaynak tüketimini azaltmak için fabrika tarafından oluşturulan HttpMessageHandler örnekleri havuzu olur. HttpMessageHandler örneği havuzundan yeni bir oluştururken yeniden kullanılabilme `HttpClient` yaşam süresi dolmadıysa örneği.

Her işleyicisi genellikle kendi temel alınan HTTP bağlantıları yöneten işleyicileri havuzu tercih edilir; gerekenden daha fazla işleyicileri oluşturma bağlantı gecikmelerine neden olabilir. Bazı işleyiciler da bağlantıları açık süresiz olarak, DNS değişiklikleri tepki gelen, işleyici engelleyebilir tutun.

Havuzdaki HttpMessageHandler nesnelerin süreyi havuzundaki HttpMessageHandler örneği yeniden kullanılabilir olan bir ömre sahiptir. Varsayılan değer iki dakika, ancak adlandırılmış ya da yazılı istemci ayrı kılınabilir. Geçersiz kılmak için aşağıdaki kodda gösterildiği gibi istemci oluştururken, döndürülen IHttpClientBuilder SetHandlerLifetime() çağırın.

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Her bir türü belirlenmiş istemci veya adlandırılmış istemci kendi yapılandırılmış işleyici ömrü değeri olabilir. Yaşam süresi işleyicisi sona erme devre dışı bırakmak için InfiniteTimeSpan ayarlayın.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Eklenen ve yapılandırılmış HttpClient kullanan, türü belirlenmiş istemci sınıfları uygulama

Önceki bir adım olarak tanımlanan sınıflar 'BasketService', 'CatalogService', 'OrderingService' vb. gibi örnek kod gibi türü belirlenmiş istemci sınıfları olması gerekir: bir türü belirlenmiş istemci kabul eden bir sınıftır bir `HttpClient` nesne (aracılığıyla eklenen kendi Oluşturucu) ve bazı uzak bir HTTP hizmetine çağrı yapmak için kullanır. Örneğin:

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

Türü belirlenmiş istemci (örnekte CatalogService) herhangi bir kayıtlı hizmeti HttpClient yanı sıra kendi oluşturucusuna kabul edebilir, yani DI (bağımlılık ekleme) tarafından etkinleştirilir.

Türü belirlenmiş istemci, etkili bir şekilde, geçici bir nesne bir gereken her seferinde yeni bir örneği oluşturulur ve yeni bir alırsınız anlamına gelir `HttpClient` , oluşturulan her zaman örneği. Ancak, havuzdaki HttpMessageHandler nesneler tarafından birden çok Http isteklerini yeniden nesnelerdir.

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

Bu noktaya kadar gösterilen kod yalnızca normal Http isteği gerçekleştiriyor, ancak burada, ilkeleri ekleyip, kayıtlı işleyicileri için temsilci seçme yalnızca yazdığınız istemciler, tüm Http istekleri yapılması aşağıdaki bölümlerde 'sihirden' gelen `HttpClient` olur alırken hesap dayanıklı ilkeleri üstel geri alma, devre Kesiciler ve kimlik doğrulama belirteçlerini veya herhangi bir özel özellik kullanma gibi ek güvenlik özellikleri uygulamak için tüm diğer özel temsilci işleyicisi ile yeniden gibi davranır. 


## <a name="additional-resources"></a>Ek kaynaklar

-   **.NET Core 2.1 HttpClientFactory kullanma**
    [*https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)


-   **HttpClientFactory GitHub deposu**

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)



>[!div class="step-by-step"]
[Önceki] (explore-custom-http-call-retries-exponential-backoff.md) [İleri] (implement-http-call-retries-exponential-backoff-polly.md)
