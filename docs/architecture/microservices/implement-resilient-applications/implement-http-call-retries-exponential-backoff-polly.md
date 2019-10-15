---
title: Polly üstel geri alma ile HTTP çağrı yeniden denemelerini uygulama
description: Polly ve HttpClientFactory ile HTTP başarısızlıklarını nasıl ele alabileceğinizi öğrenin.
ms.date: 01/07/2019
ms.openlocfilehash: 82b3b0d37815e2f16ed3be1b1e7de37019b08ee8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318406"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>HttpClientFactory ve Polly ilkeleriyle üstel geri alma ile HTTP çağrı yeniden denemeleri uygulayın

Üstel geri alma ile yeniden denemeler için önerilen yaklaşım, açık kaynaklı [Polly kitaplığı](https://github.com/App-vNext/Polly)gibi daha gelişmiş .net kitaplıklarından faydalanmalıdır.

Polly, esnekliği ve geçici hata işleme özellikleri sağlayan bir .NET kitaplığıdır. Yeniden deneme, devre kesici, Bulkhead yalıtımı, zaman aşımı ve geri dönüş gibi Polly ilkeler uygulayarak bu özellikleri uygulayabilirsiniz. .NET Framework 4. x ve .NET Standard 1,0, 1,1 ve 2,0 (.NET Core desteklenir).

Ancak, HttpClient ile Polly 'in kitaplığını kullanmak için kendi özel kodunuzu yazmak önemli ölçüde karmaşık olabilir. EShopOnContainers 'ın orijinal sürümünde, Polly tabanlı bir [ResilientHttpClient yapı taşı](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) vardı. Ancak [Httpclientfactory](use-httpclientfactory-to-implement-resilient-http-requests.md)sürümü sayesinde, çok daha basit hale gelmiştir ve derleme bloğunun eShopOnContainers 'dan kullanım dışı bırakılması. 

Aşağıdaki adımlarda, önceki bölümde açıklanan HttpClientFactory ile tümleştirilen, http yeniden denemeleri nasıl kullanabileceğiniz gösterilmektedir.

**ASP.NET Core 2,2 paketlerine başvurun**

`HttpClientFactory`, .NET Core 2,1 ' den bu yana kullanılabilir ancak projenizde NuGet 'den en son ASP.NET Core 2,2 paketlerini kullanmanızı öneririz. Genellikle `AspNetCore` metapackage ve Extension Package-1 @no__t gerekir.

**Başlangıçta, bir istemciyi Polly 'nin yeniden deneme ilkesiyle yapılandırma**

Önceki bölümlerde gösterildiği gibi, standart başlangıç. ConfigureServices (...) yönteminde adlandırılmış veya yazılmış bir istemci HttpClient yapılandırması tanımlamanız gerekir, ancak şimdi üstel geri alma ile http yeniden denemeleri için ilkeyi belirten artımlı kod eklersiniz. below

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**Addpolicyhandler ()** yöntemi, kullanacağınız `HttpClient` nesnelerine ilke ekler. Bu durumda, üstel geri alma ile http yeniden denemeleri için bir Polly ilkesi ekliyor.

Daha modüler bir yaklaşıma sahip olmak için http yeniden deneme Ilkesi, aşağıdaki kodda gösterildiği gibi `Startup.cs` dosyasında ayrı bir yöntemde tanımlanabilir:

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

Düzenli bir yeniden deneme ilkesi, sisteminizi yüksek eşzamanlılık ve ölçeklenebilirlik durumlarında ve yüksek çekişme kapsamında etkileyebilir. Kısmi kesintiler söz konusu olduğunda birçok istemciden gelen benzer yeniden denemelerin büyük bir bölümünü aşmak için, yeniden deneme algoritmasına/ilkeye bir değişim stratejisi eklemek iyi bir çözümdür. Bu, üstel geri alma 'ya rastgele açıklık ekleyerek uçtan uca sistemin genel performansını iyileştirebilir. Bu, sorunlar ortaya çıktığında ani artışları yayar. Bir düz Polly İlkesi kullandığınızda, değişim uygulamak için kod aşağıdaki örneğe benzer olabilir:

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>Ek kaynaklar

- **Yeniden deneme biçimi**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly ve HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**  
  <https://github.com/App-vNext/Polly>

- **Marc Brooker. Değişim: rastgele bir işlem yaparak daha Iyi hale getirme**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Önceki](explore-custom-http-call-retries-exponential-backoff.md)
>[İleri](implement-circuit-breaker-pattern.md)
