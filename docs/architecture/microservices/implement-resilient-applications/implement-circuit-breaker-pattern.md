---
title: Devre kesici modelini uygulama
description: Devre kesici düzeninin http yeniden denemeleri için tamamlayıcı bir sistem olarak nasıl uygulanacağını öğrenin.
ms.date: 10/16/2018
ms.openlocfilehash: 00ca39b4b6fac37ff60adf128c3f4e22c5fc14e2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732829"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Devre Kesici desenini uygulama

Daha önce belirtildiği gibi, uzak bir hizmete veya kaynağa bağlanmayı denediğinizde gerçekleşebileceği gibi, kurtarmak için değişken bir süre sürebilecek hataları işlemeniz gerekir. Bu tür bir hatanın yönetilmesi, bir uygulamanın kararlılığını ve dayanıklılığını iyileştirebilirler.

Dağıtılmış bir ortamda, uzak kaynak ve hizmetlere yapılan çağrılar, yavaş ağ bağlantıları ve zaman aşımları gibi geçici hatalar nedeniyle veya kaynaklar yavaş yanıt veriyorsa veya geçici olarak devre dışı bırakılırsa başarısız olabilir. Bu hatalar genellikle kısa bir süre sonra kendilerini düzeltir ve güçlü bir bulut uygulaması, "yeniden deneme biçimi" gibi bir strateji kullanılarak bunları işleyecek şekilde hazırlanmalıdır.

Ancak, hataların düzeltilmesi çok daha uzun sürebilecek beklenmeyen olaylardan kaynaklanan durumlar da olabilir. Bu hatalar, bir hizmetin tamamen başarısızlığına yönelik kısmi bir bağlantı kaybından önem düzeyi olarak değişebilir. Bu durumlarda, bir uygulamanın başarılı olması olası olmayan bir işlemi sürekli olarak yeniden denemesi için bu durum daha az olabilir.

Bunun yerine, işlemin başarısız olduğunu kabul etmek ve hatayı uygun şekilde işlemek için uygulamanın kodlanmış olması gerekir.

Http yeniden denemeleri daha sorunsuz bir şekilde kullanılması, kendi yazılımınız dahilinde hizmet reddi ([DOS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) saldırısı oluşturulmasına neden olabilir. Mikro hizmet başarısız olur veya yavaş çalışır, birden fazla istemci başarısız istekleri tekrar tekrar deneyebilir. Bu, başarısız olan hizmette hedeflenen trafiği üstel olarak artırarak tehlikeli bir risk oluşturur.

Bu nedenle, çalışmaya devam etmek için değer olmadığında aşırı isteklerin durdurulması için bir çeşit savunma engeli gerekir. Bu savunma engeli tam olarak devre kesici olur.

Devre kesici deseninin amacı "yeniden deneme düzeniyle" farklıdır. "Yeniden deneme biçimi", bir uygulamanın işlemin sonunda başarılı olacağı beklentide bir işlemi yeniden denemesini sağlar. Devre kesici stili, bir uygulamanın başarısız olma olasılığı olan bir işlem gerçekleştirmesini engeller. Bir uygulama, bu iki deseni birleştirebilir. Ancak, yeniden deneme mantığı devre kesici tarafından döndürülen herhangi bir özel duruma duyarlıdır ve devre kesici bir hatanın geçici olmadığını gösteriyorsa yeniden deneme girişimlerini iptal etmelidir.

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>HttpClientFactory ve Polly ile devre kesici modelini uygulayın

Yeniden denemeler uygularken, devre kesiciler için önerilen yaklaşım, Polly gibi kanıtlanmış .NET kitaplıklarından ve HttpClientFactory ile yerel tümleştirmeden faydalanmalıdır.

HttpClientFactory giden ara yazılım ardışık düzenine bir devre kesici ilkesi eklemek, HttpClientFactory kullanırken zaten sahip olduğunuz koda tek bir artımlı kod parçası eklemek kadar basittir.

Burada HTTP çağrısı yeniden denemeleri için kullanılan koda yapılan tek ekleme, aşağıdaki artımlı kodda, ConfigureServices () yönteminin bir parçası olarak da gösterildiği gibi, kullanılacak ilke listesine devre kesici ilkesi eklediğiniz koddur.

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

`AddPolicyHandler()` yöntemi, kullanacağınız `HttpClient` nesnelerine ilke ekler. Bu durumda, devre kesici için bir Polly ilkesi ekliyor.

Daha modüler bir yaklaşıma sahip olmak için, devre kesici Ilkesi aşağıdaki kodda gösterildiği gibi `GetCircuitBreakerPolicy()`adlı ayrı bir yöntemde tanımlanmıştır:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

Yukarıdaki kod örneğinde, devre kesici ilkesi, http istekleri yeniden denendiğinde beş ardışık hata olduğunda devre dışı bırakıldığında veya açılacak şekilde yapılandırılır. Bu durumda, devre 30 saniye boyunca kesilir: Bu dönemde, çağrılar aslında yerleştirilmektense devre kesici tarafından hemen başarısız olur.  İlke, [ilgili özel durumları ve http durum kodlarını](/aspnet/core/fundamentals/http-requests#handle-transient-faults) hata olarak otomatik olarak yorumlar.  

Devre kesiciler, HTTP çağrısını gerçekleştiren istemci uygulama veya hizmetten farklı bir ortamda dağıtılan belirli bir kaynakta bir geri dönüş altyapısına yeniden yönlendirmek için de kullanılmalıdır. Bu şekilde, veri merkezinde yalnızca arka uç mikro hizmetlerinizi etkileyen ancak istemci uygulamalarınıza yönelik bir kesinti varsa, istemci uygulamalar geri dönüş hizmetlerine yeniden yönlendirebilir. Polly, bu [Yük devretme ilkesi](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryosuna otomatik hale getirmek için yeni bir ilke planlıyor.

Bu özelliklerin tümü, Azure tarafından sizin için otomatik olarak yönetilmek yerine, konum saydamlığı ile, yük devretmeyi .NET kodu içinden yönettiğiniz durumlar içindir.

Bir kullanım noktasından, HttpClient kullanılırken, önceki bölümlerde gösterildiği gibi, bu kod, HttpClientFactory ile HttpClient kullanırken olduğu gibi, burada yeni bir şey eklemeniz gerekmez.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>EShopOnContainers 'da http yeniden denemelerini ve devre kesicileri sınama

Bir Docker konağında eShopOnContainers çözümünü her başlattığınızda, birden çok kapsayıcı başlatması gerekir. Kapsayıcıların bazıları SQL Server kapsayıcısı gibi başlangıç ve başlatma için daha yavaştır. Bu özellikle, eShopOnContainers uygulamasını, görüntüleri ve veritabanını ayarlaması gerektiğinden Docker 'a ilk kez dağıttığınızda doğrudur. Bazı kapsayıcıların diğerlerinden daha yavaş başlaması, önceki bölümlerde açıklandığı gibi, Docker-Compose düzeyinde kapsayıcılar arasında bağımlılıklar ayarlamış olsanız bile hizmetlerin geri kalanının ilk olarak HTTP özel durumlarını oluşturmasına neden olabilir. Kapsayıcılar arasındaki Docker-Compose bağımlılıkları yalnızca işlem düzeyindedir. Kapsayıcının giriş noktası işlemi başlatılmış olabilir, ancak SQL Server sorgular için hazırlanmayabilir. Sonuç hataların bir basamakla olabilir ve uygulama söz konusu kapsayıcıyı tüketmeye çalışırken bir özel durum alabilir.

Ayrıca, uygulama buluta dağıtıldığında başlangıçta bu tür bir hata görebilirsiniz. Bu durumda, düzenleyiciler küme düğümleri genelinde kapsayıcı sayısı dengelemesinde, kapsayıcıları bir düğümden veya VM 'den diğerine (yani yeni örnekler başlayarak) taşıyor olabilir.

' EShopOnContainers ' yöntemi, tüm kapsayıcıları başlatırken bu sorunları çözirken daha önce gösterilen yeniden deneme modelini kullanmaktır.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>EShopOnContainers içinde devre kesiciyi test etme

Devreni bölmek/açmak ve eShopOnContainers ile test etmek için birkaç yol vardır.

Bir seçenek, devre kesici ilkesinde izin verilen yeniden deneme sayısını 1 ' e düşürmenin yanı sıra tüm çözümü Docker 'a yeniden dağıtmanıza olanak sağlar. Tek bir yeniden denemeye karşı, dağıtım sırasında bir HTTP isteğinin başarısız olması, devre kesicinin açılması ve bir hata elde etmeniz iyi bir şansınız vardır.

Diğer bir seçenek de **sepet** mikro hizmetinde uygulanan özel ara yazılım kullanmaktır. Bu ara yazılım etkinleştirildiğinde tüm HTTP isteklerini yakalar ve 500 durum kodunu döndürür. Aşağıdaki gibi, başarısız URI 'ye bir GET isteği yaparak ara yazılımı etkinleştirebilirsiniz:

- `GET http://localhost:5103/failing`\
  Bu istek, ara yazılımın geçerli durumunu döndürür. Ara yazılım etkinleştirilmişse, istek 500 durum kodunu döndürür. Ara yazılım devre dışıysa, yanıt verilmez.

- `GET http://localhost:5103/failing?enable`\
  Bu istek, ara yazılımı sunar.

- `GET http://localhost:5103/failing?disable`\
  Bu istek, ara yazılımı devre dışı bırakır.

Örneğin, uygulama çalışmaya başladıktan sonra herhangi bir tarayıcıda aşağıdaki URI 'yi kullanarak bir istek yaparak ara yazılımı etkinleştirebilirsiniz. Sıralama mikro hizmeti 'nin 5103 numaralı bağlantı noktasını kullandığını unutmayın.

`http://localhost:5103/failing?enable`

Ardından, Şekil 8-5 ' de gösterildiği gibi, URI `http://localhost:5103/failing`kullanarak durumu kontrol edebilirsiniz.

![Başarısız olan ara yazılım simülasyonu durumunun kontrol etme ekran görüntüsü.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

**Şekil 8-5**. "Başarısız" ASP.NET ara yazılım durumu denetleniyor ve bu durumda devre dışı bırakıldı.

Bu noktada sepet mikro hizmeti, çağırma her çağırdığınızda durum kodu 500 ile yanıt verir.

Ara yazılım çalışmaya başladıktan sonra MVC web uygulamasından bir sıra yapmayı deneyebilirsiniz. İstekler başarısız olduğundan, devre açılır.

Aşağıdaki örnekte, MVC web uygulamasının bir siparişi yerleştirmek için mantığdaki bir catch bloğuna sahip olduğunu görebilirsiniz.  Kod bir açık devre özel durumu yakalarsa, kullanıcıya beklemesini isteyen kolay bir ileti gösterir.

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

İşte bir Özet. Yeniden deneme ilkesi, HTTP isteğini yapmak ve HTTP hatalarını almak için birkaç kez çalışır. Yeniden deneme sayısı, devre kesici ilkesi için ayarlanan en büyük sayıya ulaştığında (Bu durumda, 5), uygulama bir Brokencırcuitexception oluşturur. Şekil 8-6 ' de gösterildiği gibi, sonuç kolay bir iletidir.

![Sepet hizmeti hata ile MVC web uygulamasının ekran görüntüsü.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

**Şekil 8-6**. Devre kesici Kullanıcı arabirimine hata döndürüyor

Devre için ne zaman açılacağı/kesilecek farklı Logic uygulayabilirsiniz. Ya da bir geri dönüş veri merkezi veya yedek bir arka uç sistemi varsa, farklı bir arka uç mikro hizmetine karşı HTTP isteği de deneyebilirsiniz.

Son olarak, `CircuitBreakerPolicy` başka bir olasılık `Isolate` (açık ve ayrı tutmaya zorlar devre dışı bırakmak) ve `Reset` (yeniden kapatan) kullanmaktır. Bunlar, ilke üzerinde doğrudan ayırma ve sıfırlama sağlayan bir yardımcı program HTTP uç noktası oluşturmak için kullanılabilir.  Bu tür bir HTTP uç noktası Ayrıca, bir aşağı akış sistemini geçici olarak yalıtmak için üretimde uygun şekilde, örneğin, yükseltmek istediğiniz zaman kullanılabilir. Ya da bir aşağı akış sisteminin hatalı olması şüpheli bir aşağı akış sistemini korumak için devreyi el ile gezti.

## <a name="additional-resources"></a>Ek kaynaklar

- **Devre kesici deseninin**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Önceki](implement-http-call-retries-exponential-backoff-polly.md)
>[İleri](monitor-app-health.md)
