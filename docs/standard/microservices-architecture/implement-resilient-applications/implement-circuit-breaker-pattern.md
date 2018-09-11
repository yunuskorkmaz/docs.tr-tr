---
title: Devre kesici desenini uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Http yeniden tamamlayıcı bir sisteme olarak devre kesici desenini uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 8cd3564e5240ec5a8783edb336957549be27ea6a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274563"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Devre kesici desenini uygulama

Daha önce belirtildiği gibi bir uzak hizmete veya kaynağa bağlanmaya çalıştığınızda oluşabilir gibi kurtarmak için değişken bir süre gereken değişiklik gösterebileceği hataları işlemelidir. Bu tür bir hata işleme kararlılığını ve dayanıklılığını uygulamanın artırabilir.

Dağıtılmış bir ortamda uzak kaynak ve hizmetlere çağrılar yavaş ağ bağlantıları ve zaman aşımları, gibi geçici hatalardan dolayı başarısız olabilir veya kaynaklar yavaş yanıt vermiyor veya geçici olarak kullanılamıyor. Kısa bir süre sonra kendilerini genellikle bu hataları düzeltin ve sağlam bir bulut uygulaması "yeniden deneme düzenini" gibi bir strateji kullanarak işlemek için hazırlıklı olmalıdır. 

Ancak, olabilir hataları düzeltmek çok daha uzun sürebilir, beklenmedik olaylardan kaynaklanır olduğu durumlar. Bu hataların önem derecesi kısmi bağlantı kaybı gelen bir hizmetin tamamen çökmesi arasında değişebilir. Bu durumda, bir uygulama başarılı olma ihtimali düşük bir işlemi sürekli yeniden denemesi anlamsız olabilir. 

Bunun yerine uygulama işlemin başarısız olduğunu kabul edin ve hatayı uygun şekilde işlemek için kodlanmış olmalıdır.

HTTP yeniden carelessly kullanarak neden olabilir bir hizmet reddi oluşturmak ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) saldırı kendi yazılımınızı içinde. Bir mikro hizmet başarısız olursa veya yavaş çalışıyor gibi birden çok istemci art arda başarısız istekleri yeniden deneme. Başarısız olan hizmetine yönelik trafiği katlanarak artan tehlikeli riski oluşturur.

Bu nedenle, çalışırken değer tutma olmadığında aşırı isteklerini durdurmak için savunma engel tür gerekir. Kesin olarak devre kesici, savunma engel olur.

Devre kesici düzeni, "yeniden deneme düzenini" farklı bir amaca sahip. "Yeniden deneme düzenini" bir işlem sonunda başarılı beklentisi işleminde yeniden denemek bir uygulama sağlar. Devre kesici düzeni uygulamanın başarısız olma olasılığı yüksek bir işlemi gerçekleştirilirken engeller. Bir uygulama, bu iki Düzen birleştirebilirsiniz. Ancak, yeniden deneme mantığının devre kesici tarafından döndürülen herhangi bir özel durum duyarlı olması gerekir ve devre kesici bir hataya geçici olmadığını gösteriyorsa, yeniden denemeyi bırakması.

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>HttpClientFactory ve Polly devre kesici desenini uygulama

Yeniden denemeler yaparken, devre Kesiciler önerilen yaklaşım Polly ve yerel tümleştirmesi sayesinde HttpClientFactory gibi kendini kanıtlamış .NET kitaplıkları yararlanmak için olduğu gibi.

Bir devre kesici İlkesi, HttpClientFactory ekleme giden ara yazılım ardışık düzenini HttpClientFactory kullanırken olduğunuz için artımlı tek kod parçasını eklemek kadar kolaydır.

Yalnızca Burada HTTP çağrı yeniden için kullanılan kod için kod devre kesici İlkesi kullanmak için ilkeleri listesine aşağıdaki artımlı kodda ConfigureServices() yöntemi parçası gösterildiği eklediğiniz ektir.

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

`AddPolicyHandler()`Yöntemdir hangi ilkeleri kullanacağınız HttpClient nesneleri ekler. Bu durumda, devre kesici Polly ilke eklemektir.

Daha modüler bir yaklaşım sahip olmak için aşağıdaki kod olarak GetCircuitBreakerPolicy() adlı ayrı bir yöntem devre kesici İlkesi tanımlanmıştır.

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

Yukarıdaki kod örneğinde, keser veya olduğunda beş art arda hatalar Http isteklerini kurulmaya çalışılırken bağlantı hattını açılır devre kesici İlkesi yapılandırılır. Bu durum oluştuğunda, bağlantı hattı için 30 saniye çalışmamasına neden olur: Bu dönemde çağrıları devre kesici tarafından hemen başarısız yerine gerçekten yerleştirilmesi.  İlke otomatik olarak yorumlar [ilgili özel durumları ve HTTP durum kodları](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) hataları olarak.  

Devre Kesiciler, istekleri, bir istemci uygulamadan daha farklı bir ortamda dağıtılan belirli bir kaynağa veya HTTP çağrısı gerçekleştiriyor hizmet sorunları varsa, bir geri dönüş altyapısını yeniden yönlendirmek için de kullanılmalıdır. Bu şekilde, yalnızca arka uç mikro hizmetlerin ancak, istemci uygulamaları etkileyen veri merkezinde bir kesinti oluşursa istemci uygulamaları için geri dönüş Hizmetleri yönlendirebilirsiniz. Polly bu otomatik hale getirmek için yeni bir ilke planlama [yük devretme İlkesi](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryo. 

Tüm durumlarda nereye yük aksine, sizin için konum saydamlığı olan Azure tarafından otomatik olarak yönetilen sahip .NET kod içinde yönetiyor olsanız özelliklerdir. 

Bir kullanım HttpClient kullanırken açısından, önceki bölümlerde gösterildiği gibi kod HttpClient HttpClientFactory ile kullanırken daha aynı olduğu için yeni bir şey burada eklemenize gerek yoktur. 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Test Http yeniden ve hizmetine devre Kesiciler

Bir Docker konağı hizmetine çözüm başlattığınızda, birden çok kapsayıcı başlatmak gerekir. Bazı kapsayıcıları başlatmak ve, gibi SQL sunucu kapsayıcısı başlatmak daha yavaş. Görüntüleri ve veritabanını ayarlamak gerektiğinden bu Docker'ı hizmetine uygulamasına dağıtmak ilk kez özellikle doğrudur. Bazı kapsayıcıları kapsayıcılar arasındaki bağımlılıkları ayarlasanız bile diğerleri rest Hizmetleri HTTP özel durumlar, başlangıçta throw çıkabilir daha yavaş Başlat olgu önceki bölümlerde açıklandığı gibi düzeyi docker-compose. Bu docker kapsayıcılar arasındaki bağımlılıkları compose olan işlem düzeyinde yeterlidir. Kapsayıcının giriş noktası işlemi başlatıldı, ancak SQL Server sorguları için hazır olmayabilir. Sonucu bir art arda hatalar olabilir ve uygulamanın, bu belirli bir kapsayıcıda tüketmeye çalışırken bir özel durum elde edebilirsiniz. 

Buluta Uygulama dağıtırken, bu tür başlangıçta görebilirsiniz. Bu durumda, Düzenleyicileri kapsayıcıları bir düğüm veya VM (yani yeni örnekleri başlatılıyor) diğerine taşıma, kapsayıcı sayısı küme düğümleri arasında dengeleme.

Tüm kapsayıcıları başlatılıyor daha önce gösterilen yeniden deneme düzenini kullanarak olduğunda 'hizmetine' yolu bu sorunları çözer. 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Devre kesici hizmetine test etme

Bağlantı hattı kesme/açık ve onu hizmetine ile test edebilirsiniz birkaç yolu vardır.

Bir seçenek olduğu için izin verilen yeniden deneme sayısı 1 devre kesici ilkesinde düşürün ve çözümün tamamının Docker yeniden dağıtın. Tek bir yeniden deneme ile dağıtım sırasında bir HTTP isteği başarısız olur şansı yoktur, devre kesici açılır ve bir hata alıyorsunuz.

Başka bir seçenek, sepet mikro hizmet içinde uygulanan özel bir ara yazılım kullanmaktır. Bu ara yazılım etkinleştirildiğinde, tüm HTTP isteklerini yakalar ve 500 durum kodunu döndürür. Ara yazılım için başarısız olan bir GET isteği yaparak etkinleştirebilirsiniz aşağıdaki gibi bir URI'si:

- `GET http://localhost:5103/failing`

Bu istek, ara yazılımın geçerli durumunu döndürür. Ara yazılım etkinleştirilirse, istek 500 durum kodunu döndürür. Ara yazılım devre dışıysa, yanıt yok. 

- `GET http://localhost:5103/failing?enable`

Bu istek, ara yazılım sağlar. 

- `GET http://localhost:5103/failing?disable`

Bu istek Ara devre dışı bırakır. 

Örneğin, uygulama çalışmaya başladıktan sonra herhangi bir tarayıcıda aşağıdaki URI kullanılarak bir isteği yaparak ara yazılım etkinleştirebilirsiniz. Sıralama mikro hizmet bağlantı noktası 5103 oluşturun kullandığına dikkat edin.

`http://localhost:5103/failing?enable` 

Daha sonra URI'yi kullanarak durumu denetleyebilirsiniz http://localhost:5103/failingŞekil 10-4'te gösterildiği gibi.

![](./media/image4.png)

**Şekil 10-4**. "Başarısız" durumu denetimi devre dışı ASP.NET ara yazılım – bu durumda. 

Bu noktada, sepet mikro hizmet yanıt durum koduyla çağırmanızı her 500 onu çağırır.

Ara yazılım çalıştırıldıktan sonra MVC web uygulamasında bir sipariş oluşturmayı deneyebilirsiniz. İstekleri başarısız olduğundan, bağlantı hattının açılır. 

Aşağıdaki örnekte, MVC web uygulaması bir catch olduğunu görebilir sipariş verme mantığı açma işlemini engelleyin.  Kod devre açın istisna yakalarsa kullanıcı beklenecek bildiren kolay bir ileti gösterilir.

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

Bir özeti aşağıda verilmiştir. Yeniden deneme ilkesi, HTTP hataları alır ve HTTP isteği yapmak için birkaç kez çalışır. Yeniden deneme sayısı (Bu durumda, 5) devre kesici ilkesi için en fazla sayı kümesini eriştiğinde, uygulamanın bir BrokenCircuitException oluşturur. Kolay bir ileti Şekil 10-5'te gösterildiği gibi sonucudur.

![](./media/image5.png)

**Şekil 10-5**. Devre kesici kullanıcı Arabirimi için bir hata döndürüyor

Ne zaman açık/bağlantı hattı kesme farklı mantığı uygulayabilir. Ya da geri dönüş datacenter veya yedekli arka uç sistemine ise farklı bir arka uç mikro hizmet karşı HTTP isteği deneyebilirsiniz. 

Son olarak, başka bir olasılık için `CircuitBreakerPolicy` kullanmaktır `Isolate` (açık zorlar ve bağlantı hattı açık tutar) ve `Reset` (hangi kapatır, yeniden). Bu ilkenin üzerine ayırma ve sıfırlama doğrudan çağıran bir yardımcı programı HTTP uç noktası oluşturmak için kullanılabilir.  Bu tür, bir HTTP uç nokta da, uygun şekilde, geçici olarak yükseltmek istediğinizde gibi bir aşağı akış sistem yalıtmak için üretim ortamında güvenli kullanılabilir. Veya bir aşağı akış sistem hatalı olması şüphelendiğiniz el ile korunacak bağlantı hattını geçirmek.


## <a name="additional-resources"></a>Ek kaynaklar


-   **Devre kesici düzeni**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)


>[!div class="step-by-step"]
[Önceki](implement-http-call-retries-exponential-backoff-polly.md)
[İleri](monitor-app-health.md)
