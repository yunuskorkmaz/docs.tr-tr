---
title: Davpr hizmeti çağırma yapı taşı
description: Hizmet çağırma oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: amolenk
ms.date: 02/07/2021
ms.openlocfilehash: a68fc281b267ac32052fcc7729d257c44c9fc753
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629487"
---
# <a name="the-dapr-service-invocation-building-block"></a>Davpr hizmeti çağırma yapı taşı

Dağıtılmış bir sistemde, bir hizmetin genellikle bir iş işlemini tamamlaması için birbirleriyle iletişim kurması gerekir. [Davpr hizmeti çağırma yapı taşı](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/) , hizmetler arasındaki iletişimi kolaylaştırmaya yardımcı olabilir.

## <a name="what-it-solves"></a>Ne çözdüğü

Dağıtılmış bir uygulamadaki hizmetler arasında çağrı yapmak kolay görünebilir, ancak ilgili birçok zorluk vardır. Örneğin:

- Diğer hizmetlerin bulunduğu yer.
- Hizmet adresi verildiğinde hizmeti güvenli bir şekilde çağırma.
- Kısa süreli [geçici hatalar](https://docs.microsoft.com/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) oluştuğunda yeniden denemeleri işleme.

Son olarak, dağıtılmış uygulamalar birçok farklı hizmet oluştururken, hizmet çağrı grafikleri genelinde öngörüleri yakalamak, üretim sorunlarını tanılamak için kritik öneme sahiptir.

Hizmet çağırma oluşturma bloğu, hizmetiniz için bir [ters ara sunucu](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) olarak bir davpr sepet kullanarak bu zorlukları ele alır.

## <a name="how-it-works"></a>Nasıl çalışır?

Bir örnekle başlayalım. "Hizmet A" ve "hizmet B" olmak üzere iki hizmeti göz önünde bulundurun. Hizmetin `catalog/items` B hizmetinde API 'yi çağırması gerekir. A hizmeti, B hizmetine bir bağımlılık alabilir ve doğrudan buna çağrı yaparsanız, bunun yerine hizmet çağırma API 'sini Davpr sidecar üzerinde çağırır. Şekil 6-1, işlemi gösterir.

![Davpr hizmeti çağrısı nasıl yapılır?](./media/service-invocation/service-invocation-flow.png)

**Şekil 6-1**. Davpr hizmeti çağırma nasıl kullanılır.

Önceki şekildeki adımları göz önünde bulun:

1. A hizmeti `catalog/items` bir araç çubuğunda hizmet ÇAĞıRMA API 'sini çağırarak, hizmet B 'deki uç noktaya bir çağrı yapar.

    > [!NOTE]
    > Sepet, B hizmetinin adresini çözümlemek için takılabilir bir ad çözümleme mekanizması kullanır. Şirket içinde barındırılan modda, Davpr bunu bulmak için [MDNs](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) kullanır. Kubernetes modunda çalışırken, Kubernetes DNS hizmeti adresi belirler.  

1. Bir sepet hizmeti, isteği hizmet B sepet 'e iletir.

1. Hizmet B dışarıdan arabası gerçek `catalog/items` Isteği hizmet B API 'sine karşı yapar.

1. B hizmeti, isteği yürütür ve kendi arabasının geri yanıtını döndürür.

1. B arabası hizmeti, yanıtı bir sepet hizmetine geri iletir.

1. Bir sepet hizmeti, yanıtı A hizmetine geri döndürür.

Çağrılardan dolayı çağrı yaptığı için, Davpr bazı kullanışlı çapraz kesme davranışları ekleyebilir:

- Hata sonrasında çağrıları otomatik olarak yeniden dene.
- Otomatik Sertifika geçişi de dahil olmak üzere karşılıklı (mTLS) kimlik doğrulamasıyla hizmetler arasında çağrılar yapın.
- Hangi işlemler istemcilerinin erişim denetim ilkelerini kullanarak yapabileceğini denetleyin.
- Öngörüler ve Tanılamalar sağlamak için hizmetler arasındaki tüm çağrılar için izlemeleri ve ölçümleri yakalayın.

Herhangi bir uygulama, davpr dışarıdan **çekme API 'sini** kullanarak bir davpr sepet çağırabilir. API, HTTP ya da gRPC ile çağrılabilir. HTTP API 'sini çağırmak için aşağıdaki URL 'YI kullanın:

``` http
http://localhost:<dapr-port>/v1.0/invoke/<application-id>/method/<method-name>
```

- `<dapr-port>` Bapr 'nin dinlediği HTTP bağlantı noktası.
- `<application-id>` çağrılacak hizmetin uygulama kimliği.
- `<method-name>` uzak hizmette çağrılacak yöntemin adı.

Aşağıdaki örnekte,  `catalog/items` öğesinin ' Get ' uç noktası için bir kıvrımlı çağrı yapılır `Service B` :

```console
curl http://localhost:3500/v1.0/invoke/serviceb/method/catalog/items
```

> [!NOTE]
> Davpr API 'Leri, Davpr oluşturma blokları kullanmak için HTTP veya gRPC 'yi destekleyen tüm uygulama yığınlarını etkinleştirir. Bu nedenle, hizmet çağırma yapı taşı protokoller arasında köprü işlevi görebilir. Hizmetler, HTTP, gRPC veya her ikisinin birleşimini kullanarak birbirleriyle iletişim kurabilir.

Sonraki bölümde, hizmet çağırma çağrılarını basitleştirmek için .NET SDK 'sını nasıl kullanacağınızı öğreneceksiniz.

## <a name="use-the-dapr-net-sdk"></a>Davpr .NET SDK 'sını kullanma

Davpr [.NET SDK](https://github.com/dapr/dotnet-sdk) , .net geliştiricilerine, davpr ile etkileşime geçmek için sezgisel ve dile özgü bir yol sağlar. SDK, geliştiricilere uzak hizmet çağırma çağrıları yapmak için üç yol sunar:

1. HttpClient kullanarak HTTP hizmetlerini çağırma
1. Davprclient kullanarak HTTP hizmetlerini çağırma
1. Davprclient kullanarak gRPC hizmetlerini çağırma

### <a name="invoke-http-services-using-httpclient"></a>HttpClient kullanarak HTTP hizmetlerini çağırma

HTTP uç noktasını çağırmak için tercih edilen yol, ile birlikte, Davpr 'nin zengin tümleştirmesini kullanmaktır `HttpClient` . Aşağıdaki örnek, uygulamanın yöntemini çağırarak bir sıra gönderir `submit` `orderservice` :

```csharp
var httpClient = DaprClient.CreateHttpClient();
await httpClient.PostAsJsonAsync("http://orderservice/submit", order);
```

Örnekte, `DaprClient.CreateHttpClient` `HttpClient` davpr hizmeti çağrısı yapmak için kullanılan bir örnek döndürür. Döndürülen, `HttpClient` giden Isteklerin URI 'lerini yeniden yazar özel bir Davpr ileti işleyicisi kullanır. Ana bilgisayar adı, çağrılacak hizmetin uygulama kimliği olarak yorumlanır. Aslında Çağrılmakta olan yeniden yazan istek şunlardır:

```http
http://127.0.0.1:3500/v1/invoke/orderservice/method/submit
```

Bu örnek, bir olan Davpr HTTP uç noktası için varsayılan değeri kullanır `http://127.0.0.1:<dapr-http-port>/` . Değeri `dapr-http-port` `DAPR_HTTP_PORT` ortam değişkeninden alınır. Ayarlanmamışsa, varsayılan bağlantı noktası numarası `3500` kullanılır.

Alternatif olarak, çağrısında özel bir uç nokta yapılandırabilirsiniz `DaprClient.CreateHttpClient` :

```csharp
var httpClient = DaprClient.CreateHttpClient(daprEndpoint = "localhost:4000");
```

Ayrıca, uygulama kimliğini belirterek taban adresini doğrudan ayarlayabilirsiniz. Bu, bir çağrı yaparken göreli URI 'Leri kullanmayı mümkün kılar:

```csharp
var httpClient = DaprClient.CreateHttpClient("orderservice");
await httpClient.PostAsJsonAsync("/submit");
```

`HttpClient`Nesne uzun süreli olacak şekilde tasarlanmıştır. `HttpClient`Uygulamanın ömrü için tek bir örnek yeniden kullanılabilir. Sonraki senaryoda bir `OrderServiceClient` sınıfın bir Davpr örneğini yeniden nasıl yeniden kullandığı gösterilmektedir `HttpClient` :  

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddSingleton<IOrderServiceClient, OrderServiceClient>(
        _ => new OrderServiceClient(DaprClient.CreateInvokeHttpClient("orderservice")));
}
```

Yukarıdaki kod parçacığında, `OrderServiceClient` ASP.NET Core bağımlılık ekleme sistemiyle tek bir olarak kaydedilir. Uygulama fabrikası, çağırarak yeni bir `HttpClient` örnek oluşturur `DaprClient.CreateInvokeHttpClient` . Daha sonra nesneyi başlatmak için yeni oluşturulan ' ı kullanır `HttpClient` `OrderServiceClient` . `OrderServiceClient`Tek bir olarak kaydederek uygulamanın ömrü için yeniden kullanılır.

`OrderServiceClient`Kendisinin hiçbir Davpr 'e özgü kodu yoktur. PAPR hizmeti çağrısı, birlikte kullanıldığında, Davpr HttpClient 'ı diğer bir HttpClient gibi kabul edebilirsiniz:

```csharp
public class OrderServiceClient : IOrderServiceClient
{
    private readonly HttpClient _httpClient;

    public OrderServiceClient(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public async Task SubmitOrder(Order order)
    {
        var response = await _httpClient.PostAsJsonAsync("submit", order);
        response.EnsureSuccessStatusCode();
    }
}
```

HttpClient sınıfının Davpr hizmeti çağrısı ile kullanılması birçok avantaj sağlar:

- HttpClient birçok geliştiricinin kodda zaten kullandığı iyi bilinen bir sınıftır. Davpr hizmeti çağrısı için HttpClient kullanılması, geliştiricilerin mevcut becerilerini yeniden kullanmasına izin verir.
- HttpClient özel üstbilgiler, istek ve yanıt iletileri üzerinde tam denetim gibi gelişmiş senaryoları destekler.
- .NET 5 ' te HttpClient, System.Text.Jskullanarak otomatik serileştirme ve seri durumdan çıkarma destekler.
- HttpClient, [Refit](https://github.com/reactiveui/refit), [Restsharp](https://restsharp.dev/getting-started/getting-started.html#basic-usage)ve [Polly](https://github.com/App-vNext/Polly)gibi birçok mevcut çerçeve ve kitaplık ile tümleşir.

### <a name="invoke-http-services-using-daprclient"></a>Davprclient kullanarak HTTP hizmetlerini çağırma

HttpClient, HTTP semantiğini kullanarak hizmetleri çağırmak için tercih edilen yol olsa da, `DaprClient.InvokeMethodAsync` Yöntem ailesini de kullanabilirsiniz. Aşağıdaki örnek, uygulamanın yöntemini çağırarak bir sıra gönderir `submit` `orderservice` :

``` csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation =
        await daprClient.InvokeMethodAsync<Order, OrderConfirmation>(
            "orderservice", "submit", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

Bir nesnesi olan üçüncü bağımsız değişken `order` dahili olarak serileştirilir (ile `System.Text.JsonSerializer` ) ve istek yükü olarak gönderilir. .NET SDK, sidecar çağrısını üstlenir. Ayrıca, bir nesneye yapılan yanıtı da serileştirir `OrderConfirmation` . HTTP yöntemi belirtilmediğinden, istek bir HTTP POST olarak yürütülür.

Sonraki örnekte şunu belirterek bir HTTP GET isteği nasıl yapabileceğiniz gösterilmektedir `HttpMethod` :

```csharp
var catalogItems = await daprClient.InvokeMethodAsync<IEnumerable<CatalogItem>>(HttpMethod.Get, "catalogservice", "items");
```

Bazı senaryolarda istek iletisi üzerinde daha fazla denetime ihtiyacınız olabilir. Örneğin, istek üst bilgilerini belirtmeniz gerektiğinde veya yük için özel bir seri hale getirici kullanmak istiyorsanız. `DaprClient.CreateInvokeMethodRequest` oluşturur `HttpRequestMessage` . Aşağıdaki örnek, bir istek iletisine HTTP yetkilendirme üst bilgisinin nasıl ekleneceğini göstermektedir:

```csharp
var request = daprClient.CreateInvokeMethodRequest("orderservice", "submit", order);
request.Headers.Authorization = new AuthenticationHeaderValue("bearer", token);
```

`HttpRequestMessage`Şimdi aşağıdaki özellikler ayarlanmış:

- URL = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`
- HttpMethod = GÖNDERI
- Content =  `JsonContent` JSON seri hale getirilmiş nesneyi içeren nesne `order`
- Headers. Authorization = "taşıyıcı \<token> "

İsteği istediğiniz şekilde ayarladıktan sonra `DaprClient.InvokeMethodAsync` göndermek için kullanın:

```csharp
var orderConfirmation = await daprClient.InvokeMethodAsync<OrderConfirmation>(request);
```

`DaprClient.InvokeMethodAsync` istek başarılı olursa, bir nesneye yapılan yanıtı seri hale getirir `OrderConfirmation` . Alternatif olarak, `DaprClient.InvokeMethodWithResponseAsync` temeldeki öğesine tam erişim sağlamak için kullanabilirsiniz `HttpResponseMessage` :

```csharp
var response = await daprClient.InvokeMethodWithResponseAsync(request);
response.EnsureSuccessStatusCode();

var orderConfirmation = response.Content.ReadFromJsonAsync<OrderConfirmation>();
```

> [!NOTE]
> HTTP kullanan hizmet çağrısı çağrıları için, önceki bölümde sunulan Davpr HttpClient Tümleştirmesini kullanmayı göz önünde bulundurulmalıdır. HttpClient kullanımı, mevcut çerçeveler ve kitaplıklarla tümleştirme gibi ek avantajlar sağlar.

### <a name="invoke-grpc-services-using-daprclient"></a>Davprclient kullanarak gRPC hizmetlerini çağırma

Davprclient, `InvokeMethodGrpcAsync` gRPC uç noktaları çağırmak için bir yöntem ailesi sağlar. HTTP yöntemleriyle ilgili temel fark, JSON yerine Protoseri hale getirici kullanmaktır. Aşağıdaki örnek `submitOrder` `orderservice` GRPC Over metodunu çağırır.

```csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation = await daprClient.InvokeMethodGrpcAsync<Order, OrderConfirmation>("orderservice", "submitOrder", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

Yukarıdaki örnekte, Davprclient, `order` [protoarabelleğe](https://developers.google.com/protocol-buffers) kullanarak verilen nesneyi serileştirir ve sonucu GRPC istek gövdesi olarak kullanır. Benzer şekilde, yanıt gövdesi seri durumdan çıkarılmış olur ve çağırana döndürülür. Prototip genellikle HTTP hizmeti çağrısında kullanılan JSON yüklerinden daha iyi performans sağlar.

## <a name="reference-application-eshopondapr"></a>Başvuru uygulaması: Eshopondadpr

Microsoft 'un orijinal [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) mikro hizmet başvuru mımarısı, http/REST ve GRPC hizmetlerinin bir karışımını kullandı. GRPC kullanımı, [Toplayıcı hizmeti](../cloud-native/service-to-service-communication#service-aggregator-pattern) ile çekirdek arka uç hizmetleri arasındaki iletişim ile sınırlandırılmıştır. Şekil 6-2 mimariyi gösterme:

![eShopOnContainers 'da gRPC ve HTTP/REST çağrıları](./media/service-invocation/eshop-on-containers.png)

**Şekil 6-2**. eShopOnContainers 'da gRPC ve HTTP/REST çağrıları.

Önceki şekildeki adımları göz önünde bulun:

1. Ön uç, HTTP/REST kullanarak [API ağ geçidini](https://docs.microsoft.com/azure/architecture/microservices/design/gateway) çağırır.

1. API Gateway basit [CRUD](https://www.sumologic.com/glossary/crud/) (oluşturma, okuma, güncelleştirme, silme) isteklerini http/Rest kullanarak doğrudan bir çekirdek arka uç hizmetine iletir.

1. API Gateway, birden fazla arka uç hizmetine yönelik Eşgüdümlü çağrıları içeren karmaşık istekleri Web alışveriş toplayıcısı hizmeti 'ne iletir.

1. Toplayıcı hizmeti, çekirdek arka uç hizmetlerini çağırmak için gRPC 'yi kullanır.

Son güncellenen Eshopondadpr uygulamasında, hizmet ve API ağ geçidine Davpr sıfları eklenir. Şekil 6-3 güncelleştirilmiş mimariyi göster:

![eShopOnContainers 'da sıdecars ile gRPC ve HTTP/REST çağrıları](./media/service-invocation/eshop-on-dapr.png)

**Şekil 6-3**. Davpr kullanılarak eShop mimarisi güncelleştirildi.

Önceki şekildeki güncelleştirilmiş adımlara göz önünde edin:

1. Ön uç hala API ağ geçidini çağırmak için HTTP/REST kullanır.

1. API Gateway, HTTP isteklerini Davpr sidecar 'e iletir.

1. API ağ geçidi sepet, isteği toplayıcı veya arka uç hizmetinin sepet 'a gönderir.

1. Toplayıcı hizmeti, arka uç hizmetlerini dışarıdan çekme mimarisiyle çağırmak için, Davpr .NET SDK 'sını kullanır.

Davpr, gRPC ile sıfları arasındaki çağrıları uygular. Bu nedenle, uzak bir hizmeti HTTP/REST semantiğinin gerçekleştirseniz bile, taşımanın bir parçası gRPC kullanılarak gene de uygulanır.

Eshopondadpr başvuru uygulaması avantajlarından yararlanın. Avantajlara hizmet bulma, otomatik mTLS ve Observability dahildir.

### <a name="forward-http-requests-using-envoy-and-dapr"></a>Envoy ve Davpr kullanarak HTTP isteklerini ilet

Hem özgün hem de güncelleştirilmiş eShop uygulaması, bir API ağ geçidi olarak [Envoy proxy](https://www.envoyproxy.io/) 'sinden faydalanır. Envoy, modern dağıtılmış uygulamalar arasında popüler bir açık kaynaklı ara sunucu ve iletişim veri yolu. Lyft 'den kaynaklanan Envoy, [bulutta yerel bilgi Işlem altyapısı](https://www.cncf.io/)tarafından sahiplenilir ve korunur.

Özgün eShopOnContainers uygulamasında, Envoy API Gateway gelen HTTP isteklerini doğrudan toplayıcı veya arka uç hizmetlerine iletti. New Eshopondadpr 'de, Envoy proxy, isteği bir Davpr sidecar 'e iletir. Sepet hizmet çağrısı, mTLS ve Observability sağlar.

Envoy, proxy 'nin davranışını denetlemek için bir YAML tanım dosyası kullanılarak yapılandırılır. HTTP isteklerini bir davpr sepet kapsayıcısına iletmek için Envoy özelliğini etkinleştirmek için, `dapr` yapılandırmaya bir küme eklenir. Küme yapılandırması, ' de, Davpr dışarıdan arabasının dinlediği HTTP bağlantı noktasını gösteren bir konak içerir:

``` yaml
clusters:
- name: dapr
  connect_timeout: 0.25s
  type: strict_dns
  hosts:
  - socket_address:
    address: 127.0.0.1
    port_value: 3500
```

Envoy rotalar yapılandırması, gelen istekleri davpr sepet çağrısı olarak yeniden yazmak üzere güncelleştirilir ( `prefix_rewrite` anahtar/değer çiftine ödeme için dikkat edin):

``` yaml
- name: "c-short"
  match:
    prefix: "/c/"
  route:
    auto_host_rewrite: true
    prefix_rewrite: "/v1.0/invoke/catalog-api/method/"
    cluster: dapr
```

Ön uç istemcisinin Katalog öğelerinin bir listesini almak istediği bir senaryo düşünün. Katalog API 'SI, katalog öğelerini almak için bir uç nokta sağlar:

``` csharp
[Route("api/v1/[controller]")]
[ApiController]
public class CatalogController : ControllerBase
{
    [HttpGet("items")]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery] int pageSize = 10,
        [FromQuery] int pageIndex = 0)
    {
        // ...
    }
```

İlk olarak, ön uç, Envoy API ağ geçidine doğrudan HTTP çağrısı yapar.

```
GET http://<api-gateway>/c/api/v1/catalog/items?pageSize=20
```

Envoy proxy 'si rotayla eşleşir, HTTP isteğini yeniden yazar ve bunu, `invoke` Davpr sidecar 'in API 'sine iletir:

```
GET http://127.0.0.1:3500/v1.0/invoke/catalog-api/method/api/v1/catalog/items?pageSize=20
```

Sepet, hizmet bulmayı işler ve isteği katalog API 'SI araç çubuğu 'na yönlendirir. Son olarak, sepet, isteği yürütmek, katalog öğelerini getirmek ve bir yanıt döndürmek için katalog API 'sini çağırır:

```
GET http://localhost/api/v1/catalog/items?pageSize=20
```

### <a name="make-aggregated-service-calls-using-the-net-sdk"></a>.NET SDK kullanarak toplu hizmet çağrıları yapma

EShop ön ucu 'ndan çoğu çağrı basit CRUD çağrılardır. API Gateway, bunları işlenmek üzere tek bir hizmete iletir. Ancak, bazı senaryolar, bir isteği tamamlamaya yönelik birden fazla arka uç hizmetinin birlikte çalışmasını gerektirir. Bu daha karmaşık çağrılar için eShop, iş akışını birden çok hizmet arasında aracılık için Web alışveriş Toplayıcısı hizmetini kullanır. Şekil 6-4, alışveriş sepetinize bir öğe eklemenin işlem dizisini gösterir:

![Sepet sırası diyagramını Güncelleştir](./media/service-invocation/complex-call.png)

**Şekil 6-4**. Alışveriş sepeti sırasını güncelleştir.

Toplayıcı hizmeti ilk olarak katalog API 'sinden katalog öğelerini alır. Daha sonra öğe kullanılabilirliğini ve fiyatlandırmayı doğrular. Son olarak, Toplayıcı hizmeti, sepet API 'sini çağırarak güncelleştirilmiş alışveriş sepetini kaydeder.

Toplayıcı hizmeti, `BasketController` alışveriş sepetini güncelleştirmek için bir uç nokta sağlayan bir içerir:

``` csharp
[Route("api/v1/[controller]")]
[Authorize]
[ApiController]
public class BasketController : ControllerBase
{
    private readonly ICatalogService _catalog;
    private readonly IBasketService _basket;

    [HttpPost]
    [HttpPut]
    public async Task<ActionResult<BasketData>> UpdateAllBasketAsync(
        [FromBody] UpdateBasketRequest data, [FromHeader] string authorization)
    {
        // Get the item details from the catalog API.
        var catalogItems = await _catalog.GetCatalogItemsAsync(
            data.Items.Select(x => x.ProductId));

        // Check item availability and prices; store results in basket object.
        var basket = CreateValidatedBasket(data, catalogItems);

        // Save the shopping basket.
        await _basket.UpdateAsync(basket, authorization);

        return basket;
    }

    // ...
}
```

`UpdateAllBasketAsync`Yöntemi, gelen Isteğin *Yetkilendirme* üst bilgisini bir özniteliği kullanarak alır `FromHeader` . *Yetkilendirme* üst bilgisi, korumalı arka uç hizmetlerini çağırmak için gereken erişim belirtecini içerir.

Sepeti güncelleştirme isteği aldıktan sonra Toplayıcı hizmeti, öğe ayrıntılarını almak için katalog API 'sini çağırır. Sepet denetleyicisi, `ICatalogService` Bu çağrıyı yapmak ve Katalog API 'siyle iletişim kurmak için eklenen bir nesne kullanır. Uygulamanın orijinal uygulama çağrısı yapmak için gRPC kullandı. Güncelleştirilmiş uygulama HttpClient desteğiyle Davpr hizmeti çağrısını kullanır:

``` csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public Task<IEnumerable<CatalogItem>> GetCatalogItemsAsync(IEnumerable<int> ids)
    {
        var requestUri = $"api/v1/catalog/items?ids={string.Join(",", ids)}";
      
        return _httpClient.GetFromJsonAsync<IEnumerable<CatalogItem>>(requestUri);
    }

    // ...
}
```

Hizmet çağırma çağrısını yapmak için hiçbir hiçbir Davpr özel kodu gerekli değildir. Tüm iletişimler standart HttpClient nesnesi kullanılarak yapılır.

Davpr HttpClient, `CatalogService` yönteminde sınıfına eklenir `Startup.ConfigureServices` :

```csharp
services.AddSingleton<ICatalogService, CatalogService>(
    _ => new CatalogService(DaprClient.CreateInvokeHttpClient("catalog-api")));
```

Toplayıcı hizmeti tarafından yapılan diğer çağrı sepet API 'sidir. Yalnızca yetkili isteklere izin verir. Çağrı başarılı olduğundan emin olmak için, erişim belirteci bir *Yetkilendirme* isteği üst bilgisinde iletilir:

``` csharp
public class BasketService : IBasketService
{
    public Task UpdateAsync(BasketData currentBasket, string accessToken)
    {
        var request = new HttpRequestMessage(HttpMethod.Post, "api/v1/basket")
        {
            Content = JsonContent.Create(currentBasket)
        };
        request.Headers.Authorization = new AuthenticationHeaderValue(accessToken);
       
        var response = await _httpClient.SendAsync(request);
        response.EnsureSuccessStatusCode();
    }

    // ...
}
```

Bu örnekte, hizmeti çağırmak için yalnızca standart HttpClient işlevselliği kullanılır. Bu, HttpClient 'ı zaten bildiğiniz geliştiricilerin mevcut becerilerini yeniden kullanmasına olanak sağlar. Bu, mevcut HttpClient kodunun hiçbir değişiklik yapmadan PAPR hizmeti çağrısını kullanmasına de olanak sağlar.

## <a name="summary"></a>Özet

Bu bölümde, hizmet çağırma yapı taşı hakkında bilgi edindiniz. Hem Davpr dışarıdan çekme hem de Davpr .NET SDK kullanarak uzak yöntemlerin nasıl çağralınacağını gördünüz.

Davpr .NET SDK 'Sı, uzak yöntemleri çağırmak için birden çok yol sağlar. HttpClient desteği, var olan becerileri yeniden kullanmak isteyen geliştiriciler için harika ve mevcut birçok çerçeve ve kitaplık ile uyumludur. Davprclient, HTTP veya gRPC semantiğini kullanarak doğrudan Davpr hizmeti çağırma API 'sini kullanma desteği sunar.

Eshopondadpr başvuru mimarisi, eski eShopOnContainers çözümünün, Davpr hizmeti çağrısı kullanılarak nasıl modernleştirilmiştir. Davpr 'ye eShop eklemek, otomatik yeniden denemeler, mTLS kullanarak ileti şifreleme ve geliştirilmiş Observability gibi avantajlar sağlar.

### <a name="references"></a>Başvurular

- [Davpr hizmeti çağırma yapı taşı](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/)

- [Dağıtılmış bulutta yerel uygulamaları izleme](../cloud-native/observability-patterns)

> [!div class="step-by-step"]
> [Önceki](state-management.md) 
>  [Sonraki](publish-subscribe.md)
