---
title: Davpr yayımlama & abonelik oluşturma bloğu
description: '& abonelik oluşturma-bloğunun ve bu uygulamayı nasıl uygulayacağınız için bir açıklama'
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 3283abda0322fa2227373a22a0b076eb807d9c28
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629643"
---
# <a name="the-dapr-publish--subscribe-building-block"></a>Davpr yayımlama & abonelik oluşturma bloğu

[Yayımla-abone ol](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) (genellikle "pub/Sub" olarak adlandırılır), iyi bilinen ve yaygın olarak kullanılan bir mesajlaşma modelidir. Mimarlar, dağıtılmış uygulamalarda yaygın olarak bu şekilde kullanılır. Ancak, bunu uygulamak için bir sıhhi tesisat karmaşık olabilir. Farklı mesajlaşma ürünleri arasında genellikle hafif özellik farklılıkları vardır. Davpr, yayın/alt işlevleri uygulamayı önemli ölçüde kolaylaştıran bir yapı taşı sunar.

## <a name="what-it-solves"></a>Ne çözdüğü

Publish-Subscribe deseninin birincil avantajı, bazen zamana bağlı [ayırma olarak adlandırılan](https://docs.microsoft.com/azure/architecture/guide/technology-choices/messaging#decoupling) **gevşek** bir modeldir. Model, iletileri ( **aboneler**) kullanan hizmetlerden iletiler ( **yayımcılar**) Gönderen Hizmetleri ayırır. Hem yayımcılar hem de aboneler birbirleriyle uyumlu değildir, her ikisi de iletileri dağıtan merkezi bir **ileti aracısına** bağımlıdır.

Şekil 7-1, pub/Sub deseninin üst düzey mimarisini gösterir.

![Yayın/alt model](./media/publish-subscribe/pub-sub-pattern.png)

**Şekil 7-1**. Yayın/alt model.

Önceki şekilden, düzenin adımlarını aklınızda bir değer:

1. Yayımcılar ileti aracısına iletiler gönderir.
1. Aboneler ileti aracısıdır bir aboneliğe bağlanır.
1. İleti Aracısı iletinin bir kopyasını ilgi aboneliklerine iletir.
1. Aboneler aboneliklerinden iletileri tüketir.

Çoğu ileti aracıları, alındıktan sonra iletileri kalıcı hale getirebileceği bir sıraya alma mekanizması kapsülleyebilirsiniz. Bu, ileti Aracısı iletiyi depolayarak **dayanıklılığı** güvence altına alır. Bir yayımcı bir ileti gönderdiğinde abonelerin hemen kullanılabilir veya hatta çevrimiçi olması gerekmez. Bir kez varsa, abone iletiyi alır ve işler.  Davpr ileti teslimi için **en az bir kez** semantiğini garanti eder. Bir ileti yayımlandıktan sonra, ilgili aboneye en az bir kez gönderilir.

 > Hizmetiniz yalnızca bir iletiyi bir kez işleyebilir, aynı iletinin birden çok kez işlenmemesini sağlamak için bir [Ise denetimi](https://docs.microsoft.com/azure/architecture/microservices/design/api-design#idempotent-operations) sağlamanız gerekir. Böyle bir mantık kodlanırken, Azure Service Bus gibi bazı ileti aracıları yerleşik olarak *yinelenen algılama* mesajlaşma özellikleri sağlar.

Hem ticari hem de açık kaynaklı çeşitli ileti Aracısı ürünleri mevcuttur. Her birinin avantajları ve dezavantajları vardır. İşiniz, sistem gereksinimlerinizi uygun aracı ile eşleşmedir. Seçildiğinde, uygulamanızı ileti Aracısı sıhhi bir şekilde ayırmak en iyi uygulamadır. Aracıyı bir *soyutlama* içinde sarmalayarak bu işlevselliği elde edersiniz. Soyutlama, ileti sıhhi tesisat düzeyini kapsüller ve kodunuza genel yayın/alt işlemleri sunar. Kodunuz gerçek ileti aracısıdır değil soyutlama ile iletişim kurar. Bir Wise kararı verirken, soyutlamayı ve onun temelindeki uygulamayı yazmanız ve korumanız gerekir. Bu yaklaşım karmaşık, yinelenen ve hataya açık olabilecek özel kod gerektirir.

Davpr Yayımla & abone ol yapı taşı, mesajlaşma soyutlamasını ve kullanıma hazır uygulamayı sağlar. Yazmak zorunda olduğunuz özel kod, Davpr yapı bloğunun içinde önceden oluşturulup kapsüllenir. Bağlayın ve onu kullanın. İleti sıhhi tesisat kodu yazmak yerine siz ve takımınız, müşterilerinize değer ekleyen iş işlevleri oluşturmaya odaklanmaktadır.

## <a name="how-it-works"></a>Nasıl çalışır?

Davpr Publish & Subscribe yapı taşı, ileti göndermek ve almak için platformdan bağımsız bir API altyapısı sağlar. Hizmetleriniz bir adlandırılmış [konuya](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions)ileti yayımlar. Hizmetleriniz iletileri tüketmek için bir konuya abone olur.

Hizmet, Davpr sidecar üzerinde pub/Sub API 'sini çağırır. Sonra sepet, belirli bir ileti Aracısı ürününü kapsülleyen önceden tanımlanmış bir Davpr pub/Sub bileşenine çağrı yapar. Şekil 7-2, Davpr pub/Sub mesajlaşma yığınını gösterir.

![Yayın/alt yığın](./media/publish-subscribe/pub-sub-buildingblock.png)

**Şekil 7-2**. Davpr yayımlama/alt yığını.

Davpr Publish & Subscribe derleme bloğu birçok şekilde çağrılabilir.

En düşük düzeyde, tüm programlama platformları, **Davpr NATIVE API**'SINI kullanarak http veya GRPC üzerinden yapı bloğunu çağırabilir. Bir ileti yayımlamak için aşağıdaki API çağrısını yaparsınız:

``` http
http://localhost:<dapr-port>/v1.0/publish/<pub-sub-name>/<topic>
```

Yukarıdaki çağrıda birkaç Davpr özel URL kesimi vardır:

- `<dapr-port>` , davpr sepet 'nin dinlediği bağlantı noktası numarasını sağlar.
- `<pub-sub-name>` Seçilen Davpr pub/Sub bileşeninin adını sağlar.
- `<topic>` iletinin yayımlandığı konunun adını sağlar.

Bir iletiyi yayımlamak için *kıvrımlı* komut satırı aracını kullanarak, bunu deneyebilirsiniz:

``` curl
curl -X POST http://localhost:3500/v1.0/publish/pubsub/newOrder \
  -H "Content-Type: application/json" \
  -d '{ "orderId": "1234", "productId": "5678", "amount": 2 }'
```

Bir konuya abone olarak ileti alırsınız. Başlangıç sırasında, Davpr çalışma zamanı, gerekli abonelikleri belirlemek ve oluşturmak için uygulamayı iyi bilinen bir uç noktada çağırır:

``` http
http://localhost:<appPort>/dapr/subscribe
```

- `<appPort>` uygulamanın dinlediği bağlantı noktasının Davpr dışarıdan arabası olduğunu bildirir.

Bu uç noktayı kendiniz uygulayabilirsiniz. Ancak, Davpr bunu uygulamaya yönelik daha sezgisel yollar sunar. Bu işlevselliği daha sonra bu bölümde ele alacağız.

Çağrıdan gelen yanıt, uygulamaların abone olacağı konuların bir listesini içerir. , Konusu bir ileti aldığında çağrılacak bir uç nokta içerir. Yanıt örneği aşağıda verilmiştir:

```json
[
  {
    "pubsubname": "pubsub",
    "topic": "newOrder",
    "route": "/orders"
  },
  {
    "pubsubname": "pubsub",
    "topic": "newProduct",
    "route": "/productCatalog/products"
  }
]
```

JSON yanıtında, uygulamanın konulara ve konuların abone olmak istediğini görebilirsiniz `newOrder` `newProduct` . Sırasıyla uç noktaları `/orders` ve `/productCatalog/products` her biri için kaydeder. Her iki abonelik için de uygulama, adlı bir Davpr bileşenine bağlanıyor `pubsub` .

Şekil 7-3, örneğin akışını gösterir.

![Davpr ile örnek yayın/alt akış](media/publish-subscribe/pub-sub-flow.png)

**Şekil 7-3**. Davpr ile yayımlama/alt akış.

Önceki şekilde, akışa göz önünde bulunan:

1. Hizmet B için bir Davpr sepet `/dapr/subscribe` uç noktasını, hizmet b 'den (tüketici) çağırır. Hizmet, oluşturmak istediği abonelikler ile yanıt verir.
1. Hizmet B için Davpr sepet, ileti aracısıdır istenen abonelikleri oluşturur.
1. A hizmeti `/v1.0/publish/<pub-sub-name>/<topic>` , vapr hizmeti bir sepet olan uç noktada bir ileti yayımlar.
1. Bir sepet hizmeti iletiyi ileti aracısına yayınlar.
1. İleti Aracısı, iletinin bir kopyasını hizmet B araç çubuğu 'na gönderir.
1. Hizmet B araç çubuğu, B hizmetinde aboneliğe (Bu durumda) karşılık gelen uç noktayı çağırır `/orders` . Hizmet bir HTTP durum kodu ile yanıt verir `200 OK` , böylece sepet iletiyi başarıyla işlendiği şekilde kabul eder.

Örnekte ileti başarıyla işlenir. Ancak, hizmet B isteği gerçekleştirirken bir sorun ortaya geçtiğinde, iletiyle ne olması gerektiğini belirtmek için yanıtı kullanabilir. Bir HTTP durum kodu döndürdüğünde bir `404` hata günlüğe kaydedilir ve ileti bırakılır. Ya da diğer herhangi bir durum kodu `200` ile `404` , bir uyarı günlüğe kaydedilir ve ileti yeniden denenir. Alternatif olarak, hizmet B, yanıt gövdesine bir JSON yükü ekleyerek, iletiyle ne olması gerektiğini açıkça belirtebilir:

```json
{
  "status": "<status>"
}
```

Bunlar kullanılabilir `status` değerlerdir:

| Durum           | Eylem                                                       |
| ---------------- | ------------------------------------------------------------ |
| BAŞARıLı          | İleti başarıyla işlendi ve bırakıldı olarak değerlendirilir. |
| RETRY            | İleti yeniden denenir.                                      |
| DROP             | Günlüğe bir uyarı kaydedilir ve ileti bırakılır.              |
| Başka herhangi bir durum | İleti yeniden denenir.                                      |

### <a name="competing-consumers"></a>Rekabet müşterileri

Bir konuya abone olan bir uygulamayı ölçeklendirirken, rekabet eden tüketicilerle uğraşmanız gerekir. Yalnızca bir uygulama örneği, konuya gönderilen bir iletiyi işlemelidir. Luckily, Davpr bu sorunu işler. Aynı uygulama kimliğine sahip bir hizmetin birden çok örneği bir konuya abone olduğunda, Davpr her iletiyi yalnızca birine gönderir.

### <a name="sdks"></a>SDK

Yerel Davpr API 'Lerine HTTP çağrıları yapmak zaman alan ve soyuttur. Çağrılarınız HTTP düzeyinde oluşturulur ve serileştirme ve HTTP yanıt kodları gibi sıhhi tesisat kaygılarını işlemeniz gerekir. Neyse ki, daha sezgisel bir yoldur. Davpr, popüler geliştirme platformları için dile özgü birkaç SDK sağlar. Bu yazma sırasında, Go, Node.js, Python, .NET, Java ve JavaScript kullanılabilir.

## <a name="use-the-dapr-net-sdk"></a>Davpr .NET SDK 'sını kullanma

.NET geliştiricileri için, [davpr .NET SDK 'sı](https://www.nuget.org/packages/Dapr.Client) , davpr ile çalışmanın daha üretken bir yolunu sağlar. SDK, `DaprClient` doğrudan Davpr işlevini çağırabileceğiniz bir sınıf sunar. Sezgisel ve kullanımı kolay bir işlemdir.

Bir ileti yayımlamak için, `DaprClient` bir yöntemi sunar `PublishEventAsync` .

```csharp
var data = new OrderData
{
  orderId = "123456",
  productId = "67890",
  amount = 2
}

var daprClient = new DaprClientBuilder().Build();

await daprClient.PublishEventAsync<OrderData>("pubsub", "newOrder", data);
```

- İlk bağımsız değişken, `pubsub` ileti Aracısı uygulamasını sağlayan Davpr bileşeninin adıdır. Bu bölümün ilerleyen kısımlarında bileşenleri ele alacağız.
- İkinci bağımsız değişken `neworder` iletiyi göndermek için konunun adını sağlar.
- Üçüncü bağımsız değişken iletinin yüküyle aynıdır.
- Yönteminin genel tür parametresini kullanarak iletinin .NET türünü belirtebilirsiniz.

İleti almak için, kayıtlı bir konu için bir uç noktayı bir aboneliğe bağlarsınız. Davpr için AspNetCore kitaplığı bu önemsiz hale getirir. Örneğin, var olan bir ASP.NET WebAPI eylem yöntemine sahip olduğunu varsayalım `CreateOrder` :

```csharp
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

 > CPR [. AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) NuGet paketine, davpr ASP.NET Core tümleştirmesini kullanmak için bir başvuru eklemeniz gerekir.

Bu eylem yöntemini bir konuya bağlamak için, özniteliği ile süslemeyi oluşturursunuz `Topic` :

```csharp
[Topic("pubsub", "newOrder")]
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

Bu öznitelikle iki anahtar öğesi belirtirsiniz:

- Hedeflenecek Davpr pub/Sub bileşeni (Bu durumda `pubsub` ).
- Abone olunacak konu (Bu durumda `newOrder` ).

Daha sonra, bu konu için iletileri aldığından bu eylem yöntemini çağırır.

Ayrıca, ASP.NET Core Davpr 'yi kullanmak için etkinleştirmeniz gerekir. Davpr .NET SDK, sınıfında çağrılabilecek çeşitli uzantı yöntemleri sağlar `Startup` .

`ConfigureServices`Yönteminde aşağıdaki genişletme yöntemini eklemeniz gerekir:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddControllers().AddDapr();
}
```

Genişletme yöntemine uzantı-yöntemi eklemek, `AddDapr` `AddControllers` DAVPR 'yi MVC işlem hattına bütünleştirmek için gerekli hizmetleri kaydeder. Ayrıca `DaprClient` , bir örneği bağımlılık ekleme kapsayıcısına kaydeder ve bu da hizmetinize herhangi bir yere eklenebilir.

`Configure`Yönteminde, Davpr 'yi etkinleştirmek için aşağıdaki ara yazılım bileşenlerini eklemeniz gerekir:

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // ...
    app.UseCloudEvents();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapSubscribeHandler();
        // ...
    });
}
```

' A çağrı, `UseCloudEvents` ASP.NET Core ara yazılım ardışık düzenine **Cloudevents** ara yazılımı ekler. Bu ara yazılım, CloudEvents yapılandırılmış biçimini kullanan istekleri geri sarmaz, bu nedenle alma yöntemi doğrudan olay yükünü okuyabilir.

> [Cloudevents](https://cloudevents.io/) , platformlar arasında olay bilgilerini tanımlamanın yaygın bir yolunu sağlayan standartlaştırılmış bir mesajlaşma biçimidir. Davpr emayraçları CloudEvents. CloudEvents hakkında daha fazla bilgi için bkz. [cloudevents belirtimi](https://github.com/cloudevents/spec/tree/v1.0).

`MapSubscribeHandler`Uç nokta yönlendirme yapılandırmasındaki çağrısı uygulamaya bir Davpr abonelik uç noktası ekler. Bu uç nokta, üzerindeki isteklere yanıt verir `/dapr/subscribe` . Bu uç nokta çağrıldığında, özniteliğiyle birlikte bulunan tüm WebAPI eylem yöntemlerini otomatik olarak bulur ve bu işlem `Topic` için bir abonelik oluşturmak üzere Davpr 'yi yönlendirir.

## <a name="pubsub-components"></a>Pub/Sub bileşenleri

Davpr [pub/Sub bileşenleri](https://github.com/dapr/components-contrib/tree/master/pubsub) , iletilerin gerçek aktarımını işler. Bazıları kullanılabilir. Her biri, yayın/alt işlevselliği uygulamak için belirli bir ileti Aracısı ürününü kapsüller. Yazma sırasında, aşağıdaki yayın/alt bileşenler kullanılabilir:

- Apache Kafka
- Azure Event Hubs
- Azure Service Bus
- AWS SNS/SQS
- GCP yayımlama/Sub
- Tehlikeli elcast
- MQTT
- NAT
- Pulöib
- RabbitMQ
- Redsıs akışları

> [!NOTE]
> Azure bulut yığınında hem mesajlaşma işlevselliği (Azure Service Bus) hem de olay akışı (Azure Event hub) kullanılabilirliği vardır.

Bu bileşenler, [GitHub 'da bir bileşen-Contrib deposunda](https://github.com/dapr/components-contrib/tree/master/pubsub)topluluk tarafından oluşturulur. Henüz desteklenmeyen bir ileti Aracısı için kendi Davpr bileşenini yazmanız önerilir.

### <a name="configure-pubsub-components"></a>Yayın/alt bileşenleri yapılandırma

Bir Davpr yapılandırma dosyası kullanarak, kullanılacak yayın/alt bileşenleri belirtebilirsiniz. Bu yapılandırma birkaç alan içerir. `name`Alan, kullanmak istediğiniz yayın/alt bileşeni belirtir. İleti gönderirken veya alırken, bu adı belirtmeniz gerekir (daha önce `PublishEventAsync` Yöntem imzasında gördüğünüz gibi).

Aşağıda, bir Kbbitmq ileti Aracısı bileşeni yapılandırmak için bir Davpr yapılandırma dosyası örneği görülmektedir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub-rq
spec:
  type: pubsub.rabbitmq
  version: v1
  metadata:
  - name: host
    value: "amqp://localhost:5672"
  - name: durable
    value: true
```

Bu örnekte, bloğunda herhangi bir ileti aracısına özgü yapılandırma belirtebilirsiniz `metadata` . Bu durumda, Kbbitmq dayanıklı kuyruklar oluşturmak için yapılandırılır. Ancak, Kbbitmq bileşeninin daha fazla yapılandırma seçeneği vardır. Her bir bileşenin yapılandırması kendi olası alanları kümesine sahip olur. Her bir [yayın/alt bileşen](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/)belgelerindeki hangi alanların kullanılabilir olduğunu okuyabilirsiniz.

Koddan bir konuya abone olmanın programlama yolunun yanında, Davpr pub/Sub da bir konuya abone olmak için bildirim temelli bir yol sağlar. Bu yaklaşım, uygulama kodundan gelen Davpr bağımlılığını kaldırır. Bu nedenle, var olan bir uygulamanın kodda herhangi bir değişiklik yapmadan konulara abone olma imkanı de sağlar. Aşağıda, bir aboneliği yapılandırmaya yönelik bir Davpr yapılandırma dosyası örneği görülmektedir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Subscription
metadata:
  name: newOrder-subscription
spec:
  pubsubname: pubsub
  topic: newOrder
  route: /orders
scopes:
- ServiceB
- ServiceC
```

Her abonelikle birkaç öğe belirtmeniz gerekir:

- Kullanmak istediğiniz Davpr pub/Sub bileşeninin adı (Bu durumda `pubsub` ).
- Abone olunacak konunun adı (Bu durumda `newOrder` ).
- Bu konu için çağrılması gereken API işlemi (Bu durumda `/orders` ).
- [Kapsam](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/) , hangi hizmetlerin bir konuya yayımlayabileceği ve abone olabileceği belirtilebilir.

## <a name="reference-application-eshopondapr"></a>Başvuru uygulaması: Eshopondadpr

Eşlik eden [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr) uygulaması, davpr uygulayan bir mikro Hizmetler uygulaması oluşturmak için uçtan uca bir başvuru mimarisi sağlar. Eshopondadpr, çok sayıda yıl önce oluşturulmuş yaygın olarak popüler [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainer) uygulamasının bir evrimi. Her iki sürüm de mikro hizmetler genelinde [tümleştirme olaylarını](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) iletişim kurmak için yayımlama/alt modelini kullanır. Tümleştirme olayları şunlardır:

- Bir Kullanıcı bir alışveriş sepetini denetlediğinde.
- Bir sipariş için ödeme başarılı olduğunda.
- Bir satınalmanın yetkisiz kullanım süresi dolduğunda.

EShopOnContainers içindeki olay aşağıdaki `IEventBus` arabirime dayalıdır:

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent integrationEvent);

    void Subscribe<T, THandler>()
        where TEvent : IntegrationEvent
        where THandler : IIntegrationEventHandler<T>;
}
```

Bu arabirimin somut uygulamaları, hem Kbbitmq hem de Azure Service Bus için eShopOnContainers içinde mevcuttur. Her uygulama, anlaşılması ve bakımının zor olması karmaşık olan özel bir sıhhi tesisat kodu içerir.

Yeni Eshopondadpr, Davpr kullanarak yayın/alt davranışını önemli ölçüde basitleştirir. Örneğin, `IEventBus` arabirim tek bir yönteme düşürüldü:

```csharp
public interface IEventBus
{
    Task PublishAsync(IntegrationEvent integrationEvent);
}
```

### <a name="publish-events"></a>Olayları Yayımla

Güncelleştirilmiş Eshopondadpr 'de, tek bir `DaprEventBus` uygulama herhangi bir Davpr tarafından desteklenen ileti Aracısı 'nı destekleyebilir. Aşağıdaki kod bloğu Basitleştirilmiş yayımlama yöntemini gösterir. `PublishAsync`Yönteminin bir olay yayımlamak için bir Davpr istemcisini nasıl kullandığını aklınızda edin:

```csharp
public class DaprEventBus : IEventBus
{
    private const string PubSubName = "pubsub";

    private readonly DaprClient _daprClient;
    private readonly ILogger<DaprEventBus> _logger;

    public DaprEventBus(DaprClient daprClient, ILogger<DaprEventBus> logger)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task PublishAsync(IntegrationEvent integrationEvent)
    {
        var topicName = integrationEvent.GetType().Name;

        // Dapr uses System.Text.Json which does not support serialization of a
        // polymorphic type hierarchy by default. Using object as the type
        // parameter causes all properties to be serialized.
        await _daprClient.PublishEventAsync<object>(PubSubName, topicName, integrationEvent);
    }
}
```

Kod parçacığında görebileceğiniz gibi, konu adı olay türünün adından türetilir. Tüm eShop Hizmetleri `IEventBus` soyutlama kullandığından, geriye doğru ekleme davpr, ana hat uygulama kodunda *kesinlikle hiçbir değişiklik* gerektirmez.

> [!IMPORTANT]
> Davpr SDK, `System.Text.Json` iletileri seri hale getirmek/seri durumdan çıkarmak için kullanır. Ancak, `System.Text.Json` türetilmiş sınıfların özelliklerini varsayılan olarak serileştirmez. EShop kodunda, bazen `IntegrationEvent` tümleştirme olayları için temel sınıf olarak açıkça bir olay olarak bildirilmiştir. Bu işlem, somut olay türü çalışma zamanında iş mantığı temel alınarak dinamik olarak belirlendiği için yapılır. Sonuç olarak, olay, türetilmiş sınıf değil, temel sınıfın tür bilgileri kullanılarak serileştirilir. `System.Text.Json`Bu durumda türetilmiş sınıfın tüm özelliklerini Serileştirmeye zorlamak için, kod `object` genel tür parametresi olarak kullanılır. Daha fazla bilgi için bkz. [.net belgeleri](https://docs.microsoft.com/dotnet/standard/serialization/system-text-json-polymorphism).

Davpr ile altyapı kodu **önemli ölçüde basitleştirilmiştir**. Farklı ileti aracıları arasında ayrım yapması gerekmez. Davpr sizin için bu soyutlamayı sağlar. Gerekirse, ileti aracılarını kolayca takas edebilir veya birden çok ileti Aracısı bileşeni yapılandırabilirsiniz.

### <a name="subscribe-to-events"></a>Olaylara abone olma

Önceki eShopOnContainers uygulaması, her ileti aracısının abonelik uygulamasını işleyecek olan *subscriptionapps* 'i içerir. Her yönetici, abonelik olaylarını işlemek için karmaşık ileti aracısına özgü kod içerir. Olayları almak için her hizmetin her bir olay türü için açıkça bir işleyici kaydetmesi gerekir.

Eshopondadpr, Davpr ASP.NET Core kitaplıklarını kullanarak olay aboneliklerine yönelik sıhhi tesisat kolaylaştırır. Her olay denetleyicisindeki bir eylem yöntemiyle işlenir. Bir `Topic` öznitelik, öğesine abone olmak için ilgili konunun adı ile eylem yöntemini dekorayırır. Aşağıda, öğesinden alınan bir kod parçacığı verilmiştir `PaymentService` :

```csharp
[Route("api/v1/[controller]")]
[ApiController]
public class IntegrationEventController : ControllerBase
{
    private const string DAPR_PUBSUB_NAME = "pubsub";

    private readonly IServiceProvider _serviceProvider;

    public IntegrationEventController(IServiceProvider serviceProvider)
    {
        _serviceProvider = serviceProvider;
    }

    [HttpPost("OrderStatusChangedToValidated")]
    [Topic(DAPR_PUBSUB_NAME, "OrderStatusChangedToValidatedIntegrationEvent")]
    public async Task OrderStarted(OrderStatusChangedToValidatedIntegrationEvent integrationEvent)
    {
        var handler = _serviceProvider.GetRequiredService<OrderStatusChangedToValidatedIntegrationEventHandler>();
        await handler.Handle(integrationEvent);
    }
}
```

`Topic`Özniteliğinde, etkinliğin .NET türünün adı, konu adı olarak kullanılır. Olayı işlemek için önceki eShopOnContainers kod tabanında zaten varolan bir olay işleyicisi çağırılır. Önceki örnekte, konudan alınan iletiler `OrderStatusChangedToValidatedIntegrationEvent` var olan `OrderStatusChangedToValidatedIntegrationEventHandler` olay işleyicisini çağırır. Davpr, abonelikler ve ileti aracıları için temeldeki sıhhi tesisat uyguladığından, büyük miktarda orijinal kod kullanılmıyor olur ve kod tabanından kaldırılmıştır. Bu kodun büyük bölümü anlaşılması ve bakımının zorlayıcı olması karmaşıktır.

### <a name="use-pubsub-components"></a>Yayın/alt bileşenleri kullanma

EShopOnDapr deposunda, bir klasör, `deployment` farklı dağıtım modları kullanılarak uygulamayı dağıtmaya yönelik dosyaları içerir: `Docker Compose` ve `Kubernetes` . `dapr`Bir klasörü tutan bu klasörlerin her birinde bir klasör bulunur `components` . Bu klasör, `eshop-pubsub.yaml` uygulamanın pub/Sub davranışı için kullanacağı DAPR pub/Sub bileşeninin yapılandırmasını içeren bir dosya içerir. Önceki kod parçacıklarında gördüğünüz gibi, kullanılan yayın/alt bileşen adı da olur `pubsub` . Dosyanın içeriği şu şekildedir `eshop-pubsub.yaml` `deployment/compose/dapr/components` :

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: default
spec:
  type: pubsub.nats
  version: v1
  metadata:
  - name: natsURL
    value: nats://demo.nats.io:4222
```

Önceki yapılandırma Bu örnek için istenen [NAT ileti Aracısı](https://nats.io/) 'nı belirtir. İleti aracılarını değiştirmek için, yalnızca Korbbitmq veya Azure Service Bus gibi farklı bir ileti Aracısı yapılandırmanız ve YAML dosyasını güncelleştirmeniz gerekir. Davpr ile, ana hat hizmeti kodunuzda ileti aracılarını değiştirirken hiçbir değişiklik yapılmaz.

Son olarak, "Neden bir uygulamada birden çok ileti aracısın gerekir?" sorabilirsiniz. Bir sistem, farklı özelliklere sahip iş yüklerini işleyecek birçok kez. Bir olay günde 10 kez gerçekleşebilir, ancak saniyede 5.000 kez bir olay oluşur. Mesajlaşma trafiğini farklı ileti aracılarına bölümleyerek yarar sağlayabilirsiniz. Davpr ile, her biri farklı bir ada sahip birden çok yayın/alt bileşen yapılandırması ekleyebilirsiniz.

## <a name="summary"></a>Özet

Yayın/alt model dağıtılmış bir uygulamada Hizmetleri ayırmanıza yardımcı olur. CPR Publish & Subscribe derleme bloğu uygulamanızda bu davranışı uygulamayı basitleştirir.

Davpr pub/Sub aracılığıyla belirli bir *konuya* ileti yayımlayabilirsiniz. Ayrıca yapı taşı, hangi konunun abone olunacağını öğrenmek için hizmetinizi sorgular.

HTTP üzerinden veya Davpr için .NET SDK gibi dile özgü SDK 'Lardan birini kullanarak, Davpr pub/Sub 'ı yerel olarak kullanabilirsiniz. .NET SDK, ASP.NET Core platformu ile sıkı bir şekilde tümleşir.

Davpr ile desteklenen bir ileti Aracısı ürününü uygulamanıza ekleyebilirsiniz. Daha sonra, uygulamanızda kod değişikliğine gerek duymadan ileti aracılarını takas edebilirsiniz.

> [!div class="step-by-step"]
> [Önceki](service-invocation.md) 
>  [Sonraki](bindings.md)
