---
title: Polly üstel geri alma ile HTTP çağrı yeniden denemelerini uygulama
description: Polly ve IHttpClientFactory ile HTTP hatalarını nasıl işleyeceğinizi öğrenin.
ms.date: 03/03/2020
ms.openlocfilehash: 49396dd545a05699278254474c77acf1483e0e0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846802"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>IHttpClientFactory ve Polly politikaları yla üstel geri dönüşiçeren HTTP çağrı yeniden denemelerini uygulayın

Üstel geri tepme ile yeniden denemeler için önerilen yaklaşım, açık kaynak [Polly kitaplığı](https://github.com/App-vNext/Polly)gibi daha gelişmiş .NET kitaplıklarından yararlanmaktır.

Polly, esneklik ve geçici hata işleme yetenekleri sağlayan bir .NET kitaplığıdır. Bu yetenekleri, Yeniden Deneme, Devre Kesici, Toplu Bölme İzolasyon, Zaman Ekme ve Geri Dönüş gibi Polly ilkelerini uygulayarak uygulayabilirsiniz. Polly hedefleri .NET Framework 4.x ve .NET Standart 1.0, 1.1 ve 2.0 (.NET Core destekler).

Aşağıdaki adımlar, polly entegre ile Http retries `IHttpClientFactory`nasıl kullanabileceğinizi gösterir , hangi önceki bölümde açıklanmıştır.

**ASP.NET Core 3.1 paketlerine başvurun**

`IHttpClientFactory`.NET Core 2.1'den beri kullanılabilir, ancak projenizde NuGet'in en son ASP.NET Core 3.1 paketlerini kullanmanızı öneririz. Genellikle de uzantı paketine `Microsoft.Extensions.Http.Polly`başvurmanız gerekir.

**Başlangıç'ta bir istemciyi Polly'nin Yeniden Deneme ilkesiyle yapılandırma**

Önceki bölümlerde gösterildiği gibi, standart Startup.ConfigureServices(...) yönteminizde adlandırılmış veya yazılan istemci HttpClient yapılandırmasını tanımlamanız gerekir, ancak şimdi, üslü geri tepmeli Http yeniden denemeleri için ilkeyi belirten artımlı kod ekleyebilirsiniz, Aşağıda:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** yöntemi, kullanacağınız `HttpClient` nesnelere ilkeler ekleyen yöntemdir. Bu durumda, üstel geri tepme ile Http Retries için bir Polly politikası ekliyor.

Daha modüler bir yaklaşıma sahip olmak için, Http Yeniden Deneme `Startup.cs` İlkesi, aşağıdaki kodda gösterildiği gibi dosya içinde ayrı bir yöntemle tanımlanabilir:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

Polly ile yeniden deneme sayısı, üstel geri dönüş yapılandırması ve hatayı günlüğe kaydetme gibi bir HTTP özel durumu olduğunda yapılacak eylemleri içeren bir Yeniden Deneme ilkesi tanımlayabilirsiniz. Bu durumda, ilke iki saniyeden başlayarak üstel yeniden deneme ile altı kez denemek için yapılandırılır.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Yeniden deneme ilkesine bir jitter stratejisi ekleme

Düzenli bir Yeniden Deneme ilkesi, yüksek eşzamanlılık ve ölçeklenebilirlik durumlarında ve yüksek çekişme altında sisteminizi etkileyebilir. Kısmi kesintiler durumunda birçok istemciden gelen benzer yeniden denemelerin doruklarına aşmak için, iyi bir geçici çözüm yeniden deneme algoritması /ilkesine bir gergin strateji eklemektir. Bu, üstel geri tepmeye rasgelelik ekleyerek uçtan uca sistemin genel performansını artırabilir. Sorunlar ortaya çıktığında bu ani artışlar yayılır. İlke aşağıdaki örnekle gösterilmiştir:

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

Polly, proje web sitesi üzerinden üretime hazır jitter algoritmaları sağlar.

## <a name="additional-resources"></a>Ek kaynaklar

- **Yeniden deneme deseni**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly ve IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET esneklik ve geçici hata işleme kitaplığı)**  
  <https://github.com/App-vNext/Polly>

- **Polly: Jitter ile Yeniden Deneyin**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marc Brooker' ı. Jitter: Randomness ile Daha İyi Şeyler yapma**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Önceki](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[Sonraki](implement-circuit-breaker-pattern.md)
