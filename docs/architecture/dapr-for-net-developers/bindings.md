---
title: Davpr bağlamaları yapı taşı
description: Bağlama oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: bc9c147e237e3cc27005fbf5bae25213cacfd33f
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629421"
---
# <a name="the-dapr-bindings-building-block"></a>Davpr bağlamaları yapı taşı

Azure Işlevleri ve AWS Lambda gibi bulut tabanlı *sunucusuz* teklifler, dağıtılmış mimari alanı genelinde geniş bir benimseme elde etmiş. Birçok avantaj arasında, bir mikro hizmetin bir dış sistemdeki olayları *işlemesini* veya *çağırma* , temel karmaşıklık ve sıhhi tesisat sorunlarını ortadan kaldırmak üzere etkinleştirirler. Dış kaynaklar çok farklıdır: farklı platformlar ve satıcılar arasında veri depoları, ileti sistemleri ve Web kaynakları içerirler. [Davpr bağlamaları yapı taşı](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/) , bu aynı kaynak bağlama yeteneklerini, davpr uygulamalarınızın doorstep getirir.

## <a name="what-it-solves"></a>Ne çözdüğü

Davpr kaynak bağlamaları, hizmetlerinizin iş işlemlerini acil uygulama dışındaki dış kaynaklar arasında tümleştirmesini sağlar. Dış bir sistemden gelen bir olay, hizmetinizdeki bir işlemi bağlamsal bilgileri geçirerek tetikleyebilir. Hizmetiniz daha sonra başka bir dış sistemdeki bir olayı tetikleyerek, bağlamsal yük bilgilerini geçirerek işlemi genişletebilir. Hizmetiniz dış kaynağın bağlantısı veya farkında olmadan iletişim kurar. Sıhhi tesisat, önceden tanımlanmış Davpr bileşenleri içinde kapsüllenir. Kullanılacak Davpr bileşeni, kod değişikliği yapılmadan çalışma zamanında kolayca değiştirilebilir.

Örneğin, bir Kullanıcı bir anahtar sözcük olarak her seferinde bir olayı tetikleyen bir Twitter hesabı göz önünde bulundurun. Hizmetiniz, Tweet alıp işleyen bir olay işleyicisini kullanıma sunar. Tamamlandıktan sonra, hizmetiniz bir dış Twilio hizmeti çağıran bir olayı tetikler. Twilio, Tweet içeren bir SMS iletisi gönderir. Şekil 8-1 Bu işlemin kavramsal mimarisini gösterir.

![Giriş bağlama](media/bindings/bindings-architecture.png)

**Şekil 8-1**. Bir Davpr kaynak bağlamasının kavramsal mimarisi.

İlk bakışta, kaynak bağlama davranışı bu kitapta daha önce açıklanan [Yayımla/abone ol düzenine](publish-subscribe.md) benzer şekilde görünebilir. Benzerlikler paylaştıkları sırada farklar vardır. Yayımlama/abone olma, Davpr Hizmetleri arasındaki zaman uyumsuz iletişime odaklanır. Kaynak bağlama çok daha geniş bir kapsama sahiptir. Yazılım platformları arasında sistem birlikte çalışabilirliğine odaklanır. Mikro hizmet uygulamanızın dışındaki farklı uygulamalar, veri depoları ve hizmetler arasında bilgi alışverişi yapın.

## <a name="how-it-works"></a>Nasıl çalışır?

Davpr kaynak bağlama bir bileşen yapılandırma dosyası ile başlar. Bu YAML dosyası, yapılandırma ayarlarıyla birlikte bağlayacağınız kaynak türünü açıklar. Bir kez yapılandırıldıktan sonra, hizmetiniz kaynaktaki olayları alabilir veya üzerindeki olayları tetikleyebilirler.

> [!NOTE]
> Bağlama yapılandırması, daha sonra *Bileşenler* bölümünde ayrıntılı olarak sunulur.

### <a name="input-bindings"></a>Giriş bağlamaları

Giriş bağlamaları kodunuzu dış kaynaklardaki gelen olaylar ile tetikler. Olayları ve verileri almak için, hizmetinize *olay işleyicisi* haline gelen bir genel uç nokta kaydedersiniz. Şekil 8-2, akışı gösterir:

![Davpr giriş bağlama akışı](media/bindings/input-binding-flow.png)

**Şekil 8-2**. Davpr giriş bağlama akışı.

Şekil 8,2, bir dış Twitter hesabından olay alma adımlarını açıklar:

1. Davpr sepet, bağlama yapılandırma dosyasını okur ve dış kaynak için belirtilen olaya abone olur. Örnekte, olay kaynağı bir Twitter hesabıdır.
1. Twitter 'da eşleşen bir tweet yayımlandığında, davpr sepet 'de çalışan bağlama bileşeni onu seçer ve bir olayı tetikler.
1. Davpr sepet bağlama için yapılandırılmış uç noktayı (olay işleyicisi) çağırır. Bu örnekte hizmet, `/tweet` 6000 numaralı bağlantı noktasındaki uç noktada BIR http gönderisi dinler. Bir HTTP POST işlemi olduğundan, olayın JSON yükü istek gövdesine geçirilir.
1. Olay işlendikten sonra hizmet bir HTTP durum kodu döndürür `200 OK` .

Aşağıdaki ASP.NET Core denetleyicisi Twitter bağlaması tarafından tetiklenen bir olayın işlenmesine bir örnek sağlar:

```csharp
[ApiController]
public class SomeController : ControllerBase
{
    public class TwitterTweet
    {
        [JsonPropertyName("id_str")]
        public string ID {get; set; }

        [JsonPropertyName("text")]
        public string Text {get; set; }
    }

    [HttpPost("/tweet")]
    public ActionResult Post(TwitterTweet tweet)
    {
        // Handle tweet
        Console.WriteLine("Tweet received: {0}: {1}", tweet.ID, tweet.Text);

        // ...

        // Acknowledge message
        return Ok();
    }
}
```

İşlem hata içeriyorsa, uygun 400 veya 500 düzeyinde HTTP durum kodunu geri döndürebilirsiniz. *En az bir kez teslim* garantisi sunan bağlamalar için, davpr sepet Tetikleyiciyi yeniden dener. En *az bir kez* veya *tam bir kez* teslim garantisi sunmanın gerekip gerekmediğini görmek için [kaynak bağlamaları için davpr belgeleri] [1] göz atın.

### <a name="output-bindings"></a>Çıkış bağlamaları

Davpr Ayrıca *Çıkış bağlama* özelliklerini içerir. Bunlar, hizmetinizin bir dış kaynağı çağıran bir olayı tetiklemesine olanak tanır. Yine, çıkış bağlamayı açıklayan bir bağlama yapılandırması YAML dosyası yapılandırarak başlar. Bir kez daha olduktan sonra, uygulamanızın davpr sepet üzerinde Bindings API 'sini çağıran bir olayı tetiklersiniz. Şekil 8-3, çıkış bağlamasının akışını gösterir:

![Davpr çıkış bağlama akışı](media/bindings/output-binding-flow.png)

**Şekil 8-3**. Davpr çıkış bağlama akışı.

1. Davpr sepet, bağlama yapılandırma dosyasını dış kaynağa bağlanma hakkındaki bilgilerle okur. Örnekte, dış kaynak bir Twilio SMS hesabıdır.
1. Uygulamanız, `/v1.0/bindings/sms` uç noktayı Davpr sidecar üzerinde çağırır. Bu durumda, API 'yi çağırmak için bir HTTP POST kullanır. GRPC kullanmak da mümkündür.
1. Davpr sepet içinde çalışan bağlama bileşeni, iletiyi göndermek için harici mesajlaşma sistemini çağırır. İleti, POST isteğine geçirilen yükü içerecektir.

Örnek olarak, kıvrımlı kullanarak bir çıkış bağlamayı çağırabilirsiniz:

```console
curl -X POST http://localhost:3500/v1.0/bindings/sms \
  -H "Content-Type: application/json" \
  -d '{
        "data": "Welcome to this awesome service",
        "metadata": {
          "toNumber": "555-3277"
        },
        "operation": "create"
      }'
```

HTTP bağlantı noktasının, davpr sepet (Bu durumda, varsayılan davpr http bağlantı noktası) tarafından kullanılan ile aynı olduğunu unutmayın `3500` .

Yükün (yani, gönderilen mesaj) yapısı, bağlama başına farklılık gösterir. Yukarıdaki örnekte, yük `data` bir ileti içeren bir öğesi içerir. Diğer dış kaynak türlerine olan bağlamalar, özellikle gönderilen meta veriler için farklı olabilir. Her yük `operation` , bağlamanın yürütemeyeceği işlemi tanımlayan bir alan de içermelidir. Yukarıdaki örnekte `create` SMS iletisini oluşturan bir işlem belirtilir. Ortak işlemler şunlardır:

- oluşturmaya
- get
- silme
- list

Bu, bağlamanın desteklediği işlemleri bağlayan bağlamanın yazarına kadar olur. Her bağlamaya yönelik belgeler, kullanılabilir işlemleri ve bunların nasıl çağırılacağını açıklar.

## <a name="using-the-dapr-net-sdk"></a>Davpr .NET SDK 'sını kullanma

Davpr .NET SDK, .NET Core geliştiricileri için dile özgü destek sağlar. Aşağıdaki örnekte, öğesine yapılan çağrı `HttpClient.PostAsync()` `DaprClient.InvokeBindingAsync()` yöntemiyle değiştirilmiştir. Bu özelleştirilmiş Yöntem yapılandırılmış bir çıkış bağlamasını çağırma işlemini basitleştirir:

```csharp
private async Task SendSMSAsync([FromServices] DaprClient daprClient)
{
    var message = "Welcome to this awesome service";
    var metadata = new Dictionary<string, string> 
    { 
      { "toNumber", "555-3277" } 
    };
    await daprClient.InvokeBindingAsync("sms", "create", message, metadata);
}
```

Yöntemi `metadata` ve `message` değerlerini bekler.

Bir bağlamayı çağırmak için kullanıldığında, `DaprClient` davpr sidecar üzerinde DAVPR API 'sini çağırmak Için gRPC 'yi kullanır.

## <a name="binding-components"></a>Bileşenleri bağlama

Kaynak bağlamaları, aynı şekilde, Davpr bağlama bileşenleri ile uygulanır. Bunlar, topluluk tarafından katkıda bulunuyoruz ve go 'da yazılmıştır. Henüz hiçbir Davpr bağlamasının olmadığı bir dış kaynakla tümleştirmeniz gerekiyorsa, kendiniz oluşturabilirsiniz. Bağlama nasıl katkıda bulunabileceğinizi görmek için, [Davpr bileşenleri-contrib depoya](https://github.com/dapr/components-contrib) göz atın.

> [!NOTE]
> DAPR ve tüm bileşenleri [Golang](https://golang.org/) (go) dilinde yazılır. Go, modern, bulutta yerel bir programlama platformu olarak değerlendirilir.

YAML yapılandırma dosyası kullanarak bağlamaları yapılandırırsınız. Twitter bağlamasına yönelik örnek bir yapılandırma aşağıda verilmiştir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: twitter-mention
  namespace: default
spec:
  type: bindings.twitter
  version: v1
  metadata:
  - name: consumerKey
    value: "****" # twitter api consumer key, required
  - name: consumerSecret
    value: "****" # twitter api consumer secret, required
  - name: accessToken
    value: "****" # twitter api access token, required
  - name: accessSecret
    value: "****" # twitter api access secret, required
  - name: query
    value: "dapr" # your search query, required
```

Her bağlama yapılandırması `metadata` `name` , ve alanı içeren genel bir öğesi içerir `namespace` . Davpr, yapılandırılmış alana göre hizmetinizi çağırmak için uç noktayı tespit eder `name` . Yukarıdaki örnekte, Davpr bir olay gerçekleştiğinde hizmetinize açıklama eklenmiş yöntemi çağırır `/twitter-mention` .

Öğesinde, bağlamayı `spec` ve bağlamaya özel ' i belirtirsiniz `type` `metadata` . Örnek, API 'sini kullanarak bir Twitter hesabına erişim için kimlik bilgilerini belirtir. Meta veriler, giriş ve çıkış bağlamaları arasında farklılık gösterebilir. Örneğin, Twitter 'yı bir giriş bağlama olarak kullanmak için, alanı kullanarak ara, arayanları aramak üzere metni belirtmeniz gerekir `query` . Eşleşen bir tweet her gönderildiğinde, davpr sepet `/twitter-mention` hizmette uç noktayı çağırır. Ayrıca, Tweet içeriğini de teslim eder.

Bağlama, giriş, çıkış veya her ikisi için yapılandırılabilir. Intergelme, bağlama açıkça giriş veya çıkış yapılandırması belirtmez. Bunun yerine, yönü yapılandırma değerleriyle birlikte bağlamanın kullanımı tarafından algılanır.

[1] kaynak bağlamaları için [Davpr belgeleri, kullanılabilir bağlamaların ve bunlara özgü yapılandırma ayarlarının tamamen bir listesini sağlar.

### <a name="cron-binding"></a>Cron bağlama

Davpr 'nin cron bağlamasının dikkatini hemen ödeyin. Bir dış sistemden olaylara abone olmaz. Bunun yerine, bu bağlama uygulamanızı tetiklemek için yapılandırılabilir bir Aralık zamanlaması kullanır. Bağlama, bir arka plan çalışanını daha sonra, bir zaman için, yapılandırılabilir bir gecikmeyle sonsuz bir döngüye uygulama gerekmeden, bir arka plan çalışanı uygulamak için basit bir yol sağlar. Bir cron bağlama yapılandırmasına bir örnek aşağıda verilmiştir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: checkOrderBacklog
  namespace: default
spec:
  type: bindings.cron
  version: v1
  metadata:
  - name: schedule
    value: "@every 30m"
```

Bu örnekte, Davpr, `/checkOrderBacklog` uç noktayı her 30 dakikada bir çağırarak bir hizmeti tetikler. Değer belirtmek için kullanılabilecek çeşitli desenler vardır `schedule` . Daha fazla bilgi için [cron bağlama belgelerine](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/)bakın.

## <a name="reference-application-eshopondapr"></a>Başvuru uygulaması: Eshopondadpr

Eşlik eden Eshopondadpr başvuru uygulaması, çıkış bağlama örneği uygular. Yeni bir sipariş yerleştirildiğinde kullanıcıya bir e-posta göndermek için DAPR [SendGrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) bağlamasını tetikler. Bu bağlamayı `eshop-email.yaml` dosya içinde bileşenler klasöründe bulabilirsiniz:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: sendmail
  namespace: eshop
spec:
  type: bindings.twilio.sendgrid
  version: v1
  metadata:
  - name: apiKey
    secretKeyRef:
      name: sendGridAPIKey
auth:
  secretStore: eshop-secretstore
```

Bu yapılandırma [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) bağlama bileşenini kullanır. Hizmetine bağlanmak için API anahtarının bir Davpr gizli başvurusu kullandığını aklınızda edin. Bu yaklaşım, yapılandırma dosyasının dışında gizli dizileri tutar. Davpr gizli dizileri hakkında daha fazla bilgi edinmek için [gizli dizi derleme bloğu](secrets.md) bölümünü okuyun.

Bağlama yapılandırması, `/sendmail` Davpr sidecar üzerinde uç nokta kullanılarak çağrılabilecek bir bağlama bileşeni belirtir. Aşağıda, bir sipariş her başlatıldığında e-postanın gönderildiği bir kod parçacığı verilmiştir:

```csharp
public Task Handle(OrderStartedDomainEvent notification, CancellationToken cancellationToken)
{
    var string message = CreateEmailBody(notification);
    var metadata = new Dictionary<string, string>
    { 
        {"emailFrom", "eShopOn@dapr.io"},
        {"emailTo", notification.UserName},
        {"subject", $"Your eShopOnDapr order #{notification.Order.Id}"}
    };
    return _daprClient.InvokeBindingAsync("sendmail", "create", message, metadata, cancellationToken);
}
```

Bu örnekte gördüğünüz gibi, `message` ileti gövdesini içerir. `CreateEmailBody`Yöntemi yalnızca gövde metniyle bir dizeyi biçimlendirir. E-posta `metadata` Göndericisini, alıcıyı ve e-posta iletisinin konusunu belirtir. Bu değerler statikse, yapılandırma dosyasındaki meta veri alanlarına da eklenebilir. Çağrılacak bağlamanın adı `sendmail` ve işlem `create` .

## <a name="summary"></a>Özet

Davpr kaynak bağlamaları, kitaplıkları veya SDK 'lerinde bağımlılıklar almadan farklı dış kaynaklarla ve sistemlerle tümleştirmenize imkan tanır. Bu dış sistemlerin hizmet veri yolu veya ileti Aracısı gibi mesajlaşma sistemleri olması gerekmez. Veri depoları ve Twitter ya da SendGrid gibi Web kaynakları için bağlamalar de mevcuttur.

Giriş bağlamaları (veya Tetikleyicileri), bir dış sistemde gerçekleşen olaylara tepki verir. Uygulamanızda önceden yapılandırılmış genel HTTP uç noktalarını çağırır. Davpr, uygulamanızda çağrılacak uç noktayı öğrenmek için yapılandırmadaki bağlamanın adını kullanır.

Çıkış bağlamaları, bir dış sisteme iletiler gönderir. Bir çıkış bağlamayı `/v1.0/bindings/<binding-name>` , Davpr sidecar üzerindeki uç noktada BIR http gönderisi yaparak tetiklersiniz. Ayrıca, bağlamayı çağırmak için gRPC 'yi de kullanabilirsiniz. .NET SDK, `InvokeBindingAsync` gRPC kullanarak Davpr bağlamalarını çağırmak için bir yöntem sunar.

Bir bağlantı, bir Davpr bileşeniyle birlikte uygulanır. Bu bileşenler, topluluk tarafından katkıda bulunur. Her bağlama bileşeninin yapılandırmasında, soyutlayan dış sisteme özgü meta veriler bulunur. Ayrıca, desteklediği komutlar ve yük yapısı bağlama bileşenine göre farklılık gösterir.

### <a name="references"></a>Başvurular

- [Kaynak bağlamaları için davpr belgeleri](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/)

>[!div class="step-by-step"]
>[Önceki](publish-subscribe.md) 
> [Sonraki](observability.md)
