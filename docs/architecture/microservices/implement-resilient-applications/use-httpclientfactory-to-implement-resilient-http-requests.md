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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Dayanıklı HTTP isteklerini uygulamak için HttpClientFactory kullanma

`HttpClientFactory`, uygulamalarınızda kullanılacak örnekleri oluşturmak <xref:System.Net.Http.HttpClient> için .NET Core 2,1 ' den beri sunulan bir OPTA ve dağıtılmış bir fabrikadır.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 'da sunulan özgün HttpClient sınıfı ile ilgili sorunlar

Özgün ve iyi bilinen [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) sınıfı kolayca kullanılabilir, ancak bazı durumlarda birçok geliştirici tarafından düzgün şekilde kullanılmamalıdır. 

İlk bir sorun olarak, bu sınıf atılabilir olduğu halde, nesne atılırken `using` `HttpClient` bile, temel alınan yuva hemen yayınlanmaz ve ' yuvalar ' adlı ciddi bir soruna neden olabilir. tükenme. Bu sorun hakkında daha fazla bilgi için bkz. [HttpClient kullanıyorsunuz ve yazılım blog gönderinizi kararlı hale](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) getirme.

Bu nedenle `HttpClient` , bir kez örneğinin oluşturulması ve bir uygulamanın ömrü boyunca yeniden kullanılması amaçlanmıştır. Her istek `HttpClient` için bir sınıfın örnekleniyor, ağır yüklerin altında bulunan yuva sayısını tükeder. Bu sorun `SocketException` hatalara neden olur. Bu sorunu çözmek için olası yaklaşımlar, `HttpClient` [HttpClient kullanımıyla ilgili bu Microsoft makalesinde](/dotnet/csharp/tutorials/console-webapiclient)açıklandığı gibi nesnenin tek veya statik olarak oluşturulmasına bağlıdır. 

Ancak, bunu tek veya statik nesne `HttpClient` olarak kullandığınızda kullanabileceğiniz ikinci bir sorun vardır. Bu durumda, bir tek veya statik `HttpClient` , bu [sorun .NET Core GitHub](https://github.com/dotnet/corefx/issues/11224)deposunda açıklandığı gibi DNS değişikliklerine uymaz. 

Söz konusu sorunları gidermek ve `HttpClient` örneklerin yönetimini kolaylaştırmak için, .NET Core 2,1, aynı zamanda Polly ile tümleştirerek dayanıklı http çağrıları uygulamak için de kullanılabilecek yeni `HttpClientFactory` bir kullanıma sunuldu.   

## <a name="what-is-httpclientfactory"></a>HttpClientFactory nedir?

`HttpClientFactory`şunları yapmak için tasarlanmıştır:

- Mantıksal HttpClients adlandırmak ve yapılandırmak için merkezi bir konum sağlayın. Örneğin, belirli bir mikro hizmete erişmek için önceden yapılandırılmış bir istemciyi (Hizmet Aracısı) yapılandırabilirsiniz.
- ' Deki `HttpClient` işleyicileri devrederek ve Polly tabanlı ara yazılım kullanarak, dayanıklılık için Polly ilkelerinin avantajlarından faydalanarak giden ara yazılım kavramını codime edin.
- `HttpClient`, giden HTTP istekleri için birlikte bağlanabilen işleyicileri temsilci seçme kavramına zaten sahiptir. Http istemcilerini fabrika 'ye kaydedersiniz ve yeniden deneme, devre kesiciler, vb. için, Polly ilkelerinin kullanılmasına izin veren bir Polly işleyicisi kullanabilirsiniz.
- Belirtilen sorunları/süreleri kendi başınıza yönetirken `HttpClient` oluşabilecek sorunları önlemek için httpclientmessagehandlers 'ın ömrünü yönetin. 

## <a name="multiple-ways-to-use-httpclientfactory"></a>HttpClientFactory kullanmanın birden çok yolu

Uygulamanızda kullanabileceğiniz `HttpClientFactory` çeşitli yollar vardır:

- Doğrudan `HttpClientFactory` kullanma
- Adlandırılmış Istemcileri kullan
- Yazılan Istemcileri kullan
- Oluşturulan Istemcileri kullanma

Bu kılavuzda, bu kılavuzda, türü belirlenmiş istemcileri (Hizmet Aracısı kalıbı) kullanmak için kullanmanın `HttpClientFactory` en yapısal yolu gösterilmektedir, ancak tüm seçenekler belgelenmiştir ve şu anda [httpclientfactory kullanımını kapsayan bu makalede](/aspnet/core/fundamentals/http-requests?#consumption-patterns)listelenmiştir.  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>HttpClientFactory ile yazılan Istemcileri kullanma

Bu nedenle, "yazılı Istemci" nedir? Bu yalnızca `HttpClient` , `DefaultHttpClientFactory`tarafından eklenerek yapılandırılmıştır.

Aşağıdaki diyagramda, yazılan Istemcilerin ile `HttpClientFactory`nasıl kullanıldığı gösterilmektedir:

![Bir ClientService (bir denetleyici veya istemci kodu tarafından kullanılan), kayıtlı ıhttpclientfactory tarafından oluşturulan bir HttpClient kullanır. Bu fabrika, HttpClient 'ı yönettiği bir havuzdan HttpMessageHandler öğesine atar. HttpClient, dı kapsayıcısına ıhttpclientfactory ' i AddHttpClient uzantı yöntemiyle kaydettirilirken, Polly 'nin ilkeleriyle yapılandırılabilir.](./media/image3.5.png)

**Şekil 8-4**. Türü belirtilmiş Istemci sınıflarıyla HttpClientFactory kullanma.

İlk olarak, `HttpClientFactory` uygulamanızda, için `AddHttpClient()` `IServiceCollection`genişletme yöntemini içeren `Microsoft.Extensions.Http` pakete bir başvuru ekleyerek ayarlayın. Bu genişletme yöntemi, `DefaultHttpClientFactory` arabirimi `IHttpClientFactory`için tek olarak kullanılacak öğesini kaydeder. İçin geçici bir yapılandırma tanımlar `HttpMessageHandlerBuilder`. Bir havuzdan alınan bu`HttpMessageHandler` ileti işleyici (nesne), fabrikada `HttpClient` döndürülen tarafından kullanılır.

Sonraki kodda, kullanması `AddHttpClient()` `HttpClient`gereken yazılmış istemcileri (hizmet aracıları) kaydetmek için nasıl kullanılabileceğini görebilirsiniz.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

İstemci hizmetlerini önceki kodda gösterildiği gibi kaydetmek, `DefaultClientFactory` sonraki paragrafta açıklancağımız gibi, her bir hizmet için özel olarak yapılandırılmış bir `HttpClient` yapılandırma oluşturur.

İstemci hizmeti sınıfınızı ile `AddHttpClient()`kaydederek `HttpClient` , sınıfınıza eklenecek nesne kayıt sırasında sağlanmış yapılandırma ve ilkeleri kullanır. Sonraki bölümlerde, Polly 'in yeniden denemeleri veya devre kesiciler gibi ilkeleri görürsünüz.

### <a name="httpclient-lifetimes"></a>HttpClient yaşam süreleri

İçinden bir `HttpClient` nesne aldığınızda ,yenibirörnekdöndürülür.`IHttpClientFactory` `HttpMessageHandler` `HttpMessageHandler`Ancak, `HttpClient` süresidolmadığısürecekaynaktüketiminiazaltmakiçintarafındanhavuzaalınmışveyeniden`IHttpClientFactory` kullanılan bir kullanır.

Her işleyici genellikle kendi temel aldığı HTTP bağlantılarını yönettiğinden, işleyicilerin havuzlaması istenir; gerekenden daha fazla işleyici oluşturulması bağlantı gecikmeleri oluşmasına neden olabilir. Ayrıca, bazı işleyiciler bağlantıları süresiz olarak açık tutar, bu da işleyicinin DNS değişikliklerine yeniden davranmasını engelleyebilir.

Havuzdaki nesneler, havuzdaki bir `HttpMessageHandler` örneğin yeniden kullanılabilmesi için gereken süre olan bir yaşam süresine sahiptir. `HttpMessageHandler` Varsayılan değer iki dakikadır, ancak türü belirlenmiş Istemci başına geçersiz kılınabilir. Bunu geçersiz kılmak için, `SetHandlerLifetime()` aşağıdaki kodda `IHttpClientBuilder` gösterildiği gibi istemciyi oluştururken döndürülen ' i çağırın:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Her tür Istemcinin kendi yapılandırılmış işleyici yaşam süresi değeri olabilir. Kullanım süresini `InfiniteTimeSpan` , işleyicinin süre sonunu devre dışı bırakacak şekilde ayarlayın.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Eklenen ve yapılandırılmış HttpClient kullanan, yazılan Istemci sınıflarınızı uygulama

Önceki bir adım olarak, örnek kodda bulunan, örneğin ' basketservice ', ' catalogservice ', ' orderingservice ' vb. gibi tür istemci sınıflarınızın tanımlanmış olması gerekir. – türü belirtilmiş bir istemci, bir `HttpClient` nesneyi kabul eden bir sınıftır ( Oluşturucu) ve bunu, uzak HTTP hizmetini çağırmak için kullanır. Örneğin:

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

Türü belirlenmiş bir istemci, etkin bir şekilde geçici bir nesnedir, yani her gerektiğinde yeni bir örnek oluşturulur ve her oluşturulduğunda yeni `HttpClient` bir örnek alınır. Ancak, havuzdaki HttpMessageHandler nesneleri birden çok http isteği tarafından yeniden kullanılan nesnelerdir.

### <a name="use-your-typed-client-classes"></a>Türsüz Istemci sınıflarınızı kullanın

Son olarak, tür sınıflarınız uygulandıktan ve AddHttpClient () ile kaydolduktan sonra, bu hizmeti, örneğin her türlü Razor sayfası kodunda veya MVC web uygulamasının herhangi bir denetleyicisinde, örneğin, aşağıdaki kodda eShopOnContainers.

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

Bu noktaya kadar, gösterilen kod yalnızca normal http isteklerini gerçekleştiriyor, ancak ' Magic ', kayıtlı belirlenmiş istemcilerinize ilke ekleyerek ve işleyicileri temsilci seçerek aşağıdaki bölümlerde bulunur, bu, tarafından `HttpClient` yapılacak tüm http isteklerinin , üstel geri alma, devre kesiciler veya diğer özel temsilci seçme işleyicilerini kullanarak, kimlik doğrulama belirteçleri veya başka bir özel özellik gibi ek güvenlik özellikleri uygulamak üzere dayanıklı ilkeleri hesaba katmaya davranır. 

## <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core 'da HttpClientFactory kullanma**\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **HttpClientFactory GitHub deposu**\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
>[Önceki](explore-custom-http-call-retries-exponential-backoff.md)İleri
>[](implement-http-call-retries-exponential-backoff-polly.md)
