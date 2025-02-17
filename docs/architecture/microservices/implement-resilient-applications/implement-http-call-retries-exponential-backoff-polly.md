---
title: Polly üstel geri alma ile HTTP çağrı yeniden denemelerini uygulama
description: Polly ve ıhttpclientfactory ile HTTP hatalarının nasıl işleneceğini öğrenin.
ms.date: 01/13/2021
ms.openlocfilehash: cd209aa7f2802ffea80e14f0e3e77cc4fc29b6d5
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122969"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>Ihttpclientfactory ve Polly ilkeleriyle üstel geri alma ile HTTP çağrı yeniden denemeleri uygulayın

Üstel geri alma ile yeniden denemeler için önerilen yaklaşım, açık kaynaklı [Polly kitaplığı](https://github.com/App-vNext/Polly)gibi daha gelişmiş .net kitaplıklarından faydalanmalıdır.

Polly, esnekliği ve geçici hata işleme özellikleri sağlayan bir .NET kitaplığıdır. Yeniden deneme, devre kesici, Bulkhead yalıtımı, zaman aşımı ve geri dönüş gibi Polly ilkeler uygulayarak bu özellikleri uygulayabilirsiniz. .NET Framework 4. x ve .NET Standard 1,0, 1,1 ve 2,0 (.NET Core ve üstünü destekler).

Aşağıdaki adımlarda `IHttpClientFactory` , önceki bölümde açıklanan şekilde, ' deki ' i kullanarak http yeniden denemeleri nasıl kullanabileceğiniz gösterilmektedir.

**.NET 5 paketlerine başvurun**

`IHttpClientFactory` , .NET Core 2,1 sürümünden itibaren kullanılabilir ancak projenizde NuGet 'den en son .NET 5 paketlerini kullanmanızı öneririz. Uzantı paketine da başvurmanız gerekir `Microsoft.Extensions.Http.Polly` .

**Başlangıçta, bir istemciyi Polly 'nin yeniden deneme ilkesiyle yapılandırma**

Önceki bölümlerde gösterildiği gibi, standart Startup.ConfigureServices (...) yönteminde adlandırılmış veya yazılmış bir istemci HttpClient yapılandırması tanımlamanız gerekir, ancak şu anda üstel geri alma ile http yeniden denemeleri için ilkeyi belirten artımlı kod ekleyin:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**Addpolicyhandler ()** yöntemi, `HttpClient` kullanacağınız nesnelere ilke ekler. Bu durumda, üstel geri alma ile http yeniden denemeleri için bir Polly ilkesi ekliyor.

Daha modüler bir yaklaşıma sahip olmak için, `Startup.cs` aşağıdaki kodda gösterildiği gibi, http yeniden deneme ilkesi dosya içinde ayrı bir yöntemde tanımlanabilir:

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

Polly, yeniden deneme sayısı, üstel geri alma yapılandırması ve hatayı günlüğe kaydetme gibi bir HTTP özel durumu olduğunda gerçekleştirilecek eylemleri içeren bir yeniden deneme ilkesi tanımlayabilirsiniz. Bu durumda, ilke iki saniyeden itibaren bir üstel yeniden denemeye altı kez denemek üzere yapılandırılır.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Yeniden deneme ilkesine bir değişim stratejisi ekleyin

Düzenli bir yeniden deneme ilkesi, sisteminizi yüksek eşzamanlılık ve ölçeklenebilirlik durumlarında ve yüksek çekişme kapsamında etkileyebilir. Kısmi kesintilerden çok sayıda istemciden gelen benzer yeniden denemeler için yüksek bir çözüm olmak üzere, yeniden deneme algoritmasına/ilkeye bir değişim stratejisi eklemek iyi bir çözümdür. Bu strateji, uçtan uca sistemin genel performansını iyileştirebilirler. Bir üstel geri alma sırasında düzgün denetlenen bir ortanca ilk yeniden deneme gecikmesi ile uygulanan düzgün ve düzgün şekilde dağıtılmış yeniden deneme aralıklarıyla [uygulanan, doğru](https://github.com/App-vNext/Polly/wiki/Retry-with-jitter)bir değişim stratejisi, daha iyi bir şekilde önerilir. Bu yaklaşım, sorun ortaya çıkarsa ani artışları yaymaya yardımcı olur. İlke aşağıdaki örneğe göre gösterilmiştir:

```csharp

var delay = Backoff.DecorrelatedJitterBackoffV2(medianFirstRetryDelay: TimeSpan.FromSeconds(1), retryCount: 5);

var retryPolicy = Policy
    .Handle<FooException>()
    .WaitAndRetryAsync(delay);
```

## <a name="additional-resources"></a>Ek kaynaklar

- **Yeniden deneme biçimi**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly ve ıhttpclientfactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**  
  <https://github.com/App-vNext/Polly>

- **Polly: değişim ile yeniden dene**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marc Brooker. Değişim: rastgele bir işlem yaparak daha Iyi hale getirme**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Önceki](use-httpclientfactory-to-implement-resilient-http-requests.md) 
> [Sonraki](implement-circuit-breaker-pattern.md)
