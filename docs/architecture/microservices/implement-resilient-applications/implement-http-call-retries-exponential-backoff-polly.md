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
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="aa1dc-103">IHttpClientFactory ve Polly politikaları yla üstel geri dönüşiçeren HTTP çağrı yeniden denemelerini uygulayın</span><span class="sxs-lookup"><span data-stu-id="aa1dc-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="aa1dc-104">Üstel geri tepme ile yeniden denemeler için önerilen yaklaşım, açık kaynak [Polly kitaplığı](https://github.com/App-vNext/Polly)gibi daha gelişmiş .NET kitaplıklarından yararlanmaktır.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="aa1dc-105">Polly, esneklik ve geçici hata işleme yetenekleri sağlayan bir .NET kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="aa1dc-106">Bu yetenekleri, Yeniden Deneme, Devre Kesici, Toplu Bölme İzolasyon, Zaman Ekme ve Geri Dönüş gibi Polly ilkelerini uygulayarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="aa1dc-107">Polly hedefleri .NET Framework 4.x ve .NET Standart 1.0, 1.1 ve 2.0 (.NET Core destekler).</span><span class="sxs-lookup"><span data-stu-id="aa1dc-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="aa1dc-108">Aşağıdaki adımlar, polly entegre ile Http retries `IHttpClientFactory`nasıl kullanabileceğinizi gösterir , hangi önceki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="aa1dc-109">**ASP.NET Core 3.1 paketlerine başvurun**</span><span class="sxs-lookup"><span data-stu-id="aa1dc-109">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="aa1dc-110">`IHttpClientFactory`.NET Core 2.1'den beri kullanılabilir, ancak projenizde NuGet'in en son ASP.NET Core 3.1 paketlerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="aa1dc-111">Genellikle de uzantı paketine `Microsoft.Extensions.Http.Polly`başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="aa1dc-112">**Başlangıç'ta bir istemciyi Polly'nin Yeniden Deneme ilkesiyle yapılandırma**</span><span class="sxs-lookup"><span data-stu-id="aa1dc-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="aa1dc-113">Önceki bölümlerde gösterildiği gibi, standart Startup.ConfigureServices(...) yönteminizde adlandırılmış veya yazılan istemci HttpClient yapılandırmasını tanımlamanız gerekir, ancak şimdi, üslü geri tepmeli Http yeniden denemeleri için ilkeyi belirten artımlı kod ekleyebilirsiniz, Aşağıda:</span><span class="sxs-lookup"><span data-stu-id="aa1dc-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="aa1dc-114">**AddPolicyHandler()** yöntemi, kullanacağınız `HttpClient` nesnelere ilkeler ekleyen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="aa1dc-115">Bu durumda, üstel geri tepme ile Http Retries için bir Polly politikası ekliyor.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="aa1dc-116">Daha modüler bir yaklaşıma sahip olmak için, Http Yeniden Deneme `Startup.cs` İlkesi, aşağıdaki kodda gösterildiği gibi dosya içinde ayrı bir yöntemle tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="aa1dc-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="aa1dc-117">Polly ile yeniden deneme sayısı, üstel geri dönüş yapılandırması ve hatayı günlüğe kaydetme gibi bir HTTP özel durumu olduğunda yapılacak eylemleri içeren bir Yeniden Deneme ilkesi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="aa1dc-118">Bu durumda, ilke iki saniyeden başlayarak üstel yeniden deneme ile altı kez denemek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="aa1dc-119">Yeniden deneme ilkesine bir jitter stratejisi ekleme</span><span class="sxs-lookup"><span data-stu-id="aa1dc-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="aa1dc-120">Düzenli bir Yeniden Deneme ilkesi, yüksek eşzamanlılık ve ölçeklenebilirlik durumlarında ve yüksek çekişme altında sisteminizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="aa1dc-121">Kısmi kesintiler durumunda birçok istemciden gelen benzer yeniden denemelerin doruklarına aşmak için, iyi bir geçici çözüm yeniden deneme algoritması /ilkesine bir gergin strateji eklemektir.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="aa1dc-122">Bu, üstel geri tepmeye rasgelelik ekleyerek uçtan uca sistemin genel performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="aa1dc-123">Sorunlar ortaya çıktığında bu ani artışlar yayılır.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="aa1dc-124">İlke aşağıdaki örnekle gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="aa1dc-124">The principle is illustrated by the following example:</span></span>

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

<span data-ttu-id="aa1dc-125">Polly, proje web sitesi üzerinden üretime hazır jitter algoritmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa1dc-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="aa1dc-126">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="aa1dc-126">Additional resources</span></span>

- <span data-ttu-id="aa1dc-127">**Yeniden deneme deseni**</span><span class="sxs-lookup"><span data-stu-id="aa1dc-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="aa1dc-128">**Polly ve IHttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="aa1dc-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="aa1dc-129">**Polly (.NET esneklik ve geçici hata işleme kitaplığı)**</span><span class="sxs-lookup"><span data-stu-id="aa1dc-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="aa1dc-130">**Polly: Jitter ile Yeniden Deneyin**</span><span class="sxs-lookup"><span data-stu-id="aa1dc-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="aa1dc-131">**Marc Brooker' ı. Jitter: Randomness ile Daha İyi Şeyler yapma**</span><span class="sxs-lookup"><span data-stu-id="aa1dc-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="aa1dc-132">[Önceki](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[Sonraki](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="aa1dc-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
