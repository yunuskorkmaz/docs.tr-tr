---
title: "Devre kesici düzeni uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Devre kesici düzeni uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d7db6899068f84f9165022cfbf17767a75e7db9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a>Devre kesici düzeni uygulama

Daha önce belirtildiği gibi bir uzak hizmet veya kaynağına bağlanmaya çalıştığınızda oluşabilir gibi kurtarmak için değişken bir süre alabilir hataları işlemesi gerekir. Bu tür bir hata işleme kararlılık ve bir uygulamanın dayanıklılık artırabilir.

Dağıtılmış bir ortama uzak kaynaklar ve hizmetleri çağrıları yavaş ağ bağlantıları ve zaman aşımları, gibi geçici hataları nedeniyle başarısız veya değiştirilebilir kaynakları eşitlenmediğini yavaş veya geçici olarak kullanılamıyor. Kısa bir süre sonra kendilerini genellikle bu hataları düzeltin ve güçlü bir bulut uygulama yeniden deneme düzeni gibi bir strateji kullanarak işlemek için hazırlıklı olmalıdır.

Ancak, aynı zamanda olabilir hataları düzeltmek için daha uzun sürebilir beklenmeyen olaylar nedeniyle olduğu durumlarda. Bu hataları bağlantı kısmi bir kayıp derecesi tam başarısızlık, bir hizmetin aralığında değişebilir. Bu durumlarda, sürekli olarak başarısız olması beklenmez bir işlemi yeniden denemek bir uygulama için bir durum olabilir. Bunun yerine, uygulama işlemi başarısız oldu kabul etmek ve hata uygun şekilde işlemek için kodlanmış olmalıdır.

Devre kesici düzeni yeniden deneme düzeni farklı bir amaca sahiptir. Yeniden deneme düzeni işlem sonunda başarılı Beklenti bir işlemi yeniden denemek bir uygulama sağlar. Devre kesici düzeni büyük olasılıkla başarısız olacak bir işlemi gerçekleştirilirken bir uygulamanın engeller. Bir uygulama, bu iki desenleri devre kesici aracılığıyla bir işlem çağırmak için Yeniden Dene'yi desenini kullanarak birleştirebilirsiniz. Ancak, yeniden deneme mantığı devre kesici tarafından döndürülen tüm özel durumlar için hassas olmalıdır ve bir arıza geçici değil devre kesici olduğunu gösteriyorsa, yeniden deneme girişimleri abandon.

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>İle Polly devre kesici düzeni uygulama

Yeniden deneme uygularken, Polly gibi kanıtlanmış .NET kitaplıklarına yararlanmak için önerilen yaklaşım hattı ayırıcıları için olduğu gibi.

EShopOnContainers uygulama, HTTP yeniden deneme uygularken Polly devre kesici İlkesi kullanır. Aslında, uygulama her iki ilkeyi ResilientHttpClient yardımcı program sınıfı için geçerlidir. (EShopOnContainers) gelen HTTP isteklerini ResilientHttpClient türünde bir nesne kullandığınızda, her iki bu ilkeleri uygulayarak, ancak ek ilkeler çok ekleyebilirsiniz.

Yalnızca Burada HTTP çağrısı deneme için kullanılan kod için kod devre kesici İlkesi kullanmak için ilkeleri listesine aşağıdaki kodu sonunda gösterildiği gibi eklediğiniz eklenmiştir:

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

Kod HTTP sarmalayıcı bir ilke ekler. İlke olarak kod ardışık özel durumları (bir satır durumlar), belirtilen sayıda algıladığında açıldığını devre kesici tanımlar (Bu durumda 5) exceptionsAllowedBeforeBreaking parametresi geçirildi. Bağlantı hattı açık olduğunda, HTTP isteklerini çalışmaz, ancak özel durum oluşturuldu.

Bağlantı hattı ayırıcıları da bir geri dönüş altyapısı, bir istemci uygulaması'ndan farklı bir ortamda dağıtılan belirli kaynak ya da HTTP çağrısıyla gerçekleştiriyor hizmet sorunlarınız varsa isteklerini yeniden yönlendirmek için kullanılmalıdır. Yalnızca, arka uç mikro ancak, istemci uygulamaları etkiler merkezinde bir kesinti ise bu şekilde, istemci uygulamaları için geri dönüş Hizmetleri yönlendirebilirsiniz. Polly bu otomatikleştirmek için yeni bir ilke planlama [yük devretme İlkesi](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryo.

Elbette, tüm bu durumlarda, yük devretmeyi onu sizin için konum saydamlığı olan Azure tarafından otomatik olarak yönetilen sahip aksine .NET kodundaki yönettiği özellikleridir.

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>EShopOnContainers ResilientHttpClient yardımcı programı sınıfından kullanma

.NET HttpClient sınıfı kullanma için benzer bir şekilde ResilientHttpClient yardımcı sınıfını kullanın. EShopOnContainers MVC web uygulamasından (OrderController tarafından kullanılan OrderingService Aracısı sınıfı) aşağıdaki örnekte, ResilientHttpClient Nesne oluşturucusu httpClient parametresi üzerinden eklenmiş. Ardından nesnesi, HTTP isteklerini gerçekleştirmek için kullanılır.

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

Her \_apiClient üye nesne kullanıldığında, dahili olarak Polly policiesؙ ile sarmalayıcı sınıfı kullanır; yeniden deneme ilkesi, devre kesici ilke ve Polly ilkeleri koleksiyondan uygulamak isteyebilirsiniz başka herhangi bir ilke.

## <a name="testing-retries-in-eshoponcontainers"></a>Yeniden deneme eShopOnContainers içinde test etme

Her bir Docker ana eShopOnContainers çözüm başlattığınızda, birden çok kapsayıcı başlatmak gerekiyor. Bazı kapsayıcıların başlatın ve başlatma, SQL Server kapsayıcı gibi daha yavaş. Görüntüleri ve veritabanını ayarlamak gerektiğinden bu Docker, eShopOnContainers uygulamasına dağıtmak ilk kez özellikle doğrudur. Bazı kapsayıcıları kapsayıcılar arasındaki bağımlılıkları ayarlasanız bile başkalarının başlangıçta HTTP özel durumlar, throw Hizmetleri rest neden olabilir daha yavaş başlatma olgu önceki bölümlerde açıklandığı gibi düzeyi, docker-oluşturun. Bu docker-kapsayıcılar arasındaki bağımlılıkları oluşturan öğeler yalnızca işlem düzeyinde. Kapsayıcının giriş noktası işlem başlatılamamış olabilir, ancak SQL Server sorguları için hazır olmayabilir. Sonuç art arda hatalar olabilir ve uygulama, belirli bir kapsayıcıda tüketen çalışılırken bir özel durum alabilirsiniz.

Buluta Uygulama dağıtırken, bu tür hatalara başlangıçta görebilirsiniz. Bu durumda, orchestrators kapsayıcıları bir düğüm veya VM (yani yeni örnekleri başlatılıyor) diğerine taşıma kapsayıcı sayısı küme düğümleri arasında dengeleme olduğunda.

EShopOnContainers bu sorunu çözer daha önce gösterilen yeniden deneme modeli kullanarak bir yoludur. Neden, çözüm başlatılırken, günlük izlemelerini veya aşağıdaki gibi uyarılar alabilirsiniz şöyledir:

> "**Polly'nın RetryPolicy ile uygulanan 1 yeniden deneme**, nedeni: System.Net.Http.HttpRequestException: isteği gönderilirken bir hata oluştu. ---&gt;System.Net.Http.CurlException: sunucusuna bağlanamadı\\System.Net.Http.CurlHandler.ThrowIfCURLEError (CURLcode hatası), n\\adresindeki n \[... \].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Devre kesici eShopOnContainers içinde test etme

Bağlantı hattı açın ve eShopOnContainers ile test birkaç yolu vardır.

Bir seçenektir için izin verilen 1 devre kesici İlkesi'nde yeniden deneme sayısını azaltmak ve Docker tam çözümü yeniden dağıtın. Tek bir yeniden deneme ile dağıtım sırasında bir HTTP isteği başarısız olur şansı yoktur, devre kesici açar ve bir hata alıyorsunuz.

Uygulanan özel ara yazılımı kullanmak için başka bir seçenektir `Basket` mikro hizmet. Bu ara yazılım etkinleştirildiğinde, tüm HTTP isteklerini yakalar ve durum kodu 500 döndürür. Ara yazılım için başarısız olan bir GET isteği yaparak etkinleştirebilirsiniz aşağıdaki gibi URI:

-   GET/başarısız

Bu istek ara yazılım geçerli durumunu döndürür. Ara yazılım etkinleştirilirse, isteği durum kodu 500 döndürür. Ara yazılım devre dışıysa, yanıt yoktur.

-   GET/başarısız? etkinleştir

Bu istek ara yazılım sağlar.

-   GET/başarısız? devre dışı bırak

Bu istek Ara devre dışı bırakır.

Örneğin, uygulama çalışmaya başladıktan sonra aşağıdaki URI herhangi bir tarayıcı kullanarak bir istek yaparak ara yazılım etkinleştirebilirsiniz. Sıralama mikro hizmet bağlantı noktası 5103 oluşturun kullandığına dikkat edin.

http://localhost:5103 / başarısız? etkinleştir

Ardından URI kullanılarak durumunu denetleyebilirsiniz [http://localhost:5103 / başarısız](http://localhost:5103/failing), Şekil 10-4'te gösterildiği gibi.

![](./media/image4.png)

**Şekil 10-4**. "Başarısız" durumu denetimini devre dışı ASP.NET ara yazılım – bu durumda. 

Bu noktada, durum koduyla çağırmanız her 500 Sepeti mikro hizmet yanıt bunu çağırır.

Ara yazılım çalışmaya başladıktan sonra MVC web uygulamasından bir sipariş oluşturmayı deneyebilirsiniz. İstekler başarısız olduğu için bağlantı hattı açılır.

Aşağıdaki örnekte, MVC web uygulaması bir catch olduğunu görebilirsiniz sipariş yerleştirme mantığındaki engelleyin. Bir açık hattı özel durum kodu yakalar, kullanıcı beklenecek söyleyen kolay bir ileti gösterir.

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            //… Other code
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

Bir özeti aşağıda verilmiştir. Yeniden deneme ilkesi, HTTP hataları alır ve HTTP isteği yapmak için birkaç kez çalışır. Deneme sayısı (Bu durumda, 5) devre kesici ilkesi için en fazla sayı kümesi ulaştığında, uygulamanın bir BrokenCircuitException oluşturur. Sonuç, Şekil 10-5'te gösterildiği gibi kolay bir ileti olur.

![](./media/image5.png)

**Şekil 10-5**. Devre kesici kullanıcı Arabirimi için bir hata döndürüyor

Bağlantı hattı açmak ne zaman farklı mantığı uygulayabilirsiniz. Ya da bir geri dönüş datacenter veya yedek arka uç sistemi ise farklı bir arka uç mikro hizmet karşı bir HTTP isteği deneyebilirsiniz.

Son olarak, diğer bir olasılık CircuitBreakerPolicy için (hangi açık zorlar ve bağlantı hattı açık tutar) ayırma ve (hangi yeniden kapatır) sıfırlama kullanmaktır. Bu ayırma ve doğrudan sıfırlama ilkesini çağıran bir yardımcı programı HTTP uç noktası oluşturmak için kullanılabilir. Bu tür, bir HTTP uç nokta da, düzgün, geçici olarak yükseltmek istediğinizde gibi bir aşağı akış sistem yalıtılması üretimde güvenli kullanılabilir. Ya da hatalı olması için şüpheleniyorsanız bir aşağı akış sistemi el ile korunacak bağlantı hattı trip.

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Yeniden deneme ilkesi değişim stratejisi ekleme

Normal bir yeniden deneme ilkesi sisteminizi durumlarda yüksek eşzamanlılık ve ölçeklenebilirlik ve yüksek çakışma altında etkileyebilir. Kısmi kesintiler durumunda birçok istemcilerden gelen benzer yeniden deneme yükselmeleri üstesinden gelmek için bir değişim stratejisi yeniden deneme algoritması/ilkesine eklemek için iyi geçici bir çözüm değildir. Üstel geri alma için rastgele ekleyerek bu uçtan uca sistem genel performansını artırabilir. Sorunlar çıkması olduğunda bu ani yayar. Polly kullandığınızda, değişim uygulamak için kodu aşağıdaki gibi görünebilir:

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>Ek kaynaklar

-   **Desen yeniden deneme**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Bağlantı dayanıklılığı** (Entity Framework Çekirdek) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (.NET esnekliği ve geçici hata işleme kitaplık) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Devre kesici düzeni**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Brooker. Değişim: Şeyler rastgele ile daha iyi yapma** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[Önceki] (implement-http-call-retries-exponential-backoff-polly.md) [sonraki] (İzleyicisi-app-health.md)
