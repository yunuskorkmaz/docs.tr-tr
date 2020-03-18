---
title: Devre Kesici desenini uygulama
description: Http yeniden denemelerine tamamlayıcı bir sistem olarak Devre Kesici deseni nasıl uygulayacağınızı öğrenin.
ms.date: 03/03/2020
ms.openlocfilehash: a79c6fcca1e29f3c30d697cb369060d59a72c121
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847251"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Devre Kesici desenini uygulama

Daha önce de belirtildiği gibi, uzak bir hizmete veya kaynağa bağlanmaya çalıştığınızda olabileceği gibi, kurtarması değişken miktarda zaman alabilecek hataları işlemeniz gerekir. Bu tür bir hatanın işlenmesi, bir uygulamanın kararlılığını ve esnekliğini artırabilir.

Dağıtılmış bir ortamda, uzak kaynaklara ve hizmetlere yapılan çağrılar, yavaş ağ bağlantıları ve zaman zaman ekmeleri gibi geçici hatalar veya kaynakların yavaş yanıt verdiği veya geçici olarak kullanılamaması nedeniyle başarısız olabilir. Bu hatalar genellikle kısa bir süre sonra kendilerini düzeltir ve "Yeniden Deneme deseni" gibi bir strateji kullanarak bunları işlemek için sağlam bir bulut uygulaması hazırlanmalıdır.

Ancak, hataların düzeltilmesi çok daha uzun sürebilecek beklenmeyen olaylardan kaynaklandığı durumlar da olabilir. Bu hataların önem derecesi kısmi bağlantı kaybıyla bir hizmetin tamamen çökmesi arasında değişebilir. Bu gibi durumlarda, bir uygulamanın sürekli olarak başarılı olması beklenmeyen bir işlemi yeniden denemesi anlamsız olabilir.

Bunun yerine, uygulama işlemin başarısız olduğunu kabul etmek ve buna göre başarısızlığı işlemek için kodlanmalıdır.

Http yeniden denemelerini dikkatsizce kullanmak, kendi yazılımınızda Bir Hizmet Reddi[(DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)saldırısı oluşturmaya neden olabilir. Bir microservice başarısız olduğunda veya yavaş yavaş performans gösterdiğinde, birden çok istemci başarısız istekleri tekrar tekrar yeniden deneebilir. Bu, başarısız hizmeti hedefleyen trafiği katlanarak artırma konusunda tehlikeli bir risk oluşturur.

Bu nedenle, aşırı istekleri denemeye devam etmeye değer olmadığında durdurmak böylece savunma bariyeri çeşit gerekir. Bu savunma bariyeri tam olarak devre kesici.

Devre Kesici deseni "Retry deseni"nden farklı bir amaca sahiptir. "Yeniden Deneme deseni", bir uygulamanın, işlemin sonunda başarılı olacağı beklentisiyle bir işlemi yeniden denemesini sağlar. Devre Kesici deseni, bir uygulamanın başarısız olma olasılığı olan bir işlemi gerçekleştirmesini engeller. Bir uygulama bu iki desen birleştirebilir. Ancak, yeniden deneme mantığı devre kesici tarafından döndürülen herhangi bir özel durum duyarlı olmalı ve devre kesici bir hata geçici olmadığını gösterirse yeniden deneme girişimleri terk etmelidir.

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a>Ve Polly `IHttpClientFactory` ile Devre Kesici deseni uygulayın

Yeniden denemeler icra ederken olduğu gibi, devre kesiciler için önerilen yaklaşım Polly ve onun `IHttpClientFactory`yerel entegrasyonu gibi kanıtlanmış .NET kitaplıklarından yararlanmaktır.

Giden ara yazılım ardışık alan içine `IHttpClientFactory` bir devre kesici ilkesi eklemek, kullanırken `IHttpClientFactory`zaten sahip olduğunuz kodlara tek bir artımlı kod eklemek kadar kolaydır.

HTTP çağrı yeniden denemeleri için kullanılan koda burada eklenen tek ek, ConfigureServices() yönteminin bir parçası olan aşağıdaki artımlı kodda gösterildiği gibi, Devre Kesici ilkesini kullanılacak ilkeler listesine eklediğiniz koddur.

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Yöntem, `AddPolicyHandler()` kullanacağınız `HttpClient` nesnelere ilkeler ekleyen yöntemdir. Bu durumda, bir devre kesici için Polly politikası ekliyor.

Daha modüler bir yaklaşıma sahip olmak için, Devre `GetCircuitBreakerPolicy()`Kesici Politikası aşağıdaki kodda gösterildiği gibi ayrı bir yöntemle tanımlanır:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

Yukarıdaki kod örneğinde, devre kesici ilkesi, Http isteklerini yeniden denerken ardışık beş hata olduğunda devreyi kıracak veya açar şekilde yapılandırılır. Bu durumda, devre 30 saniye boyunca kırılır: bu dönemde, aramalar aslında yerine devre kesici tarafından hemen başarısız olacaktır.  İlke, ilgili [özel durumları ve HTTP durum kodlarını](/aspnet/core/fundamentals/http-requests#handle-transient-faults) otomatik olarak hata olarak yorumlar.  

Devre kesiciler, http çağrısını gerçekleştiren istemci uygulamasından veya hizmetten farklı bir ortamda dağıtılan belirli bir kaynakta sorunlar varsa, istekleri geri dönüş altyapısına yönlendirmek için de kullanılmalıdır. Bu şekilde, veri merkezinde yalnızca arka uç mikro hizmetlerinizi etkileyen ancak istemci uygulamalarınızı etkilemeyen bir kesinti olursa, istemci uygulamaları geri dönüş hizmetlerine yönlendirilebilir. Polly bu [başarısız ilke](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryosuotomatikleştirmek için yeni bir ilke planlıyor.

Tüm bu özellikler, yer saydamlığıyla azure tarafından sizin için otomatik olarak yönetilmesinin aksine, .NET kodu içinden başarısızlığı yönettiğiniz durumlar içindir.

Kullanım açısından bakıldığında, HttpClient'ı kullanırken, kod önceki bölümlerde gösterildiği `HttpClient` `IHttpClientFactory`gibi, kod ile aynı olduğundan buraya yeni bir şey eklemenize gerek yoktur.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Test Http retries ve devre kesiciler eShopOnContainers

Bir Docker ana bilgisayarda eShopOnContainers çözüm başlattığınızda, birden fazla kapsayıcı başlatmak gerekir. Bazı kapsayıcılar, SQL Server kapsayıcısı gibi başlatmak ve başlatmak için daha yavaş. Bu özellikle görüntüleri ve veritabanıkurmak için gereken çünkü Docker içine eShopOnContainers uygulaması dağıtmak ilk kez doğrudur. Bazı kapsayıcıların diğerlerinden daha yavaş başlaması, önceki bölümlerde açıklandığı gibi, konteynerler arasındaki bağımlılıkları docker-comoluşturma düzeyinde ayarlasanız bile, hizmetlerin geri kalanının başlangıçta HTTP özel durumları oluşturmasına neden olabilir. Kapsayıcılar arasındaki docker-com-com-bağımlılıkları sadece işlem düzeyindedir. Kapsayıcının giriş noktası işlemi başlatılabilir, ancak SQL Server sorgular için hazır olmayabilir. Sonuç, bir hata basamaklı olabilir ve uygulama, belirli bir kapsayıcıyı tüketmeye çalışırken bir özel durum alabilir.

Uygulama buluta dağıtılırken başlangıçta de bu tür bir hata görebilirsiniz. Bu durumda, orkestratörler kümenin düğümleri üzerinde kapsayıcı sayısını dengeleme yaparken bir düğüm veya VM'den diğerine (diğer bir deyişle yeni örnekler başlatArak) kapsayıcıları taşıyor olabilir.

'eShopOnContainers' tüm kapsayıcılar başlatırken bu sorunları çözer yolu daha önce gösterildiği Retry desen kullanarak.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>eShopOnContainers devre kesici test

Devreyi kırmanın/açmanın ve eShopOnContainers ile test etmenin birkaç yolu vardır.

Bir seçenek, devre kesici ilkesinde izin verilen yeniden deneme sayısını 1'e düşürmek ve tüm çözümü Docker'a yeniden dağıtmaktır. Tek bir yeniden denemede, bir HTTP isteğinin dağıtım sırasında başarısız olma olasılığı yüksektir, devre kesici açılır ve bir hata alırsınız.

Başka bir seçenek **Sepet** microservice uygulanan özel ara yazılım kullanmaktır. Bu ara yazılım etkinleştirildiğinde, tüm HTTP isteklerini yakalar ve durum kodu 500 döndürür. Aşağıdaki gibi başarısız URI'ye GET isteğinde bulunarak ara yazılımı etkinleştirebilirsiniz:

- `GET http://localhost:5103/failing`\
  Bu istek, ara yazılımın geçerli durumunu döndürür. Ara yazılım etkinse, istek iade durum kodu 500. Ara yazılım devre dışı bırakılırsa, yanıt yoktur.

- `GET http://localhost:5103/failing?enable`\
  Bu istek ara yazılımı etkinleştirir.

- `GET http://localhost:5103/failing?disable`\
  Bu istek ara yazılımı devre dışı kılabilir.

Örneğin, uygulama çalışmaya başladığında, herhangi bir tarayıcıda aşağıdaki URI'yi kullanarak istekte bulunarak ara yazılımı etkinleştirebilirsiniz. Sipariş microservice port 5103 kullanır unutmayın.

`http://localhost:5103/failing?enable`

Daha sonra Şekil 8-5'te gösterildiği gibi URI'yi `http://localhost:5103/failing`kullanarak durumu kontrol edebilirsiniz.

![Başarısız ara yazılım simülasyonunun durumunun kontrol edilmesi ekran görüntüsü.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

**Şekil 8-5**. "Failing" ASP.NET aracının durumunu kontrol etmek – Bu durumda devre dışı bırakılır.

Bu noktada, Sepet microservice çağrı her çağrıda durum kodu 500 ile yanıt verir.

Ara yazılım lar çalışmaya başladığında, MVC web uygulamasından sipariş yapmayı deneyebilirsiniz. İstekler başarısız olduğu için devre açılır.

Aşağıdaki örnekte, MVC web uygulamasının sipariş vermek için mantıkta bir catch bloğu olduğunu görebilirsiniz.  Kod açık devre özel durum yakalarsa, kullanıcıya beklemelerini söyleyen bir ileti gösterir.

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            var user = _appUserParser.Parse(HttpContext.User);
            //Http requests using the Typed Client (Service Agent)
            var vm = await _basketSvc.GetBasket(user);
            return View(vm);
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode
            HandleBrokenCircuitException();
        }
        return View();
    }

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

İşte bir özeti. Yeniden Deneme ilkesi, HTTP isteğini gerçekleştirmek için birkaç kez çalışır ve HTTP hatalarını alır. Yeniden deneme sayısı Devre Kesici ilkesi için belirlenen maksimum sayıya ulaştığında (bu durumda, 5), uygulama bir BrokenCircuitException atar. Sonuç, Şekil 8-6'da gösterildiği gibi dostça bir mesajdır.

![Sepet hizmeti inoperative hata ile MVC web uygulaması ekran görüntüsü.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

**Şekil 8-6**. Devre kesici UI'ye hata döndürür

Devreyi ne zaman açacağınız/kıracağınız için farklı mantık uygulayabilirsiniz. Ya da bir geri dönüş veri merkezi veya gereksiz arka uç sistemi varsa farklı bir arka uç microservice karşı bir HTTP isteği deneyebilirsiniz.

Son olarak, başka `CircuitBreakerPolicy` bir `Isolate` olasılık kullanmaktır (hangi kuvvetler açık `Reset` ve açık devre tutar) ve (tekrar kapatır). Bunlar, doğrudan ilke üzerinde Yalıtma ve Sıfırlama çağıran bir yardımcı program HTTP bitiş noktası oluşturmak için kullanılabilir.  Böyle bir HTTP bitiş noktası, yükseltme yapmak istediğinizde olduğu gibi, bir akış aşağı sistemi geçici olarak yalıtmak için üretimde de kullanılabilir, uygun şekilde güvenli hale gelir. Ya da hatalı olduğundan şüphelendiğiniz bir aşağı sistemi korumak için devreyi manuel olarak titretebilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Devre Kesici deseni**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Önceki](implement-http-call-retries-exponential-backoff-polly.md)
>[Sonraki](monitor-app-health.md)
