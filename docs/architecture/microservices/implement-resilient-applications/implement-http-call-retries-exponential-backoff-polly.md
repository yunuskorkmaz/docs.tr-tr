---
title: Polly üstel geri alma ile HTTP çağrı yeniden denemelerini uygulama
description: Polly ve ıhttpclientfactory ile HTTP hatalarının nasıl işleneceğini öğrenin.
ms.date: 01/13/2021
ms.openlocfilehash: c2831f73ed38b48fd32fa241f8fe1792b9adf3d4
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511794"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="5d73d-103">Ihttpclientfactory ve Polly ilkeleriyle üstel geri alma ile HTTP çağrı yeniden denemeleri uygulayın</span><span class="sxs-lookup"><span data-stu-id="5d73d-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="5d73d-104">Üstel geri alma ile yeniden denemeler için önerilen yaklaşım, açık kaynaklı [Polly kitaplığı](https://github.com/App-vNext/Polly)gibi daha gelişmiş .net kitaplıklarından faydalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d73d-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="5d73d-105">Polly, esnekliği ve geçici hata işleme özellikleri sağlayan bir .NET kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="5d73d-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="5d73d-106">Yeniden deneme, devre kesici, Bulkhead yalıtımı, zaman aşımı ve geri dönüş gibi Polly ilkeler uygulayarak bu özellikleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d73d-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="5d73d-107">.NET Framework 4. x ve .NET Standard 1,0, 1,1 ve 2,0 (.NET Core ve üstünü destekler).</span><span class="sxs-lookup"><span data-stu-id="5d73d-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core and later).</span></span>

<span data-ttu-id="5d73d-108">Aşağıdaki adımlarda `IHttpClientFactory` , önceki bölümde açıklanan şekilde, ' deki ' i kullanarak http yeniden denemeleri nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5d73d-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="5d73d-109">**.NET 5 paketlerine başvurun**</span><span class="sxs-lookup"><span data-stu-id="5d73d-109">**Reference the .NET 5 packages**</span></span>

<span data-ttu-id="5d73d-110">`IHttpClientFactory` , .NET Core 2,1 sürümünden itibaren kullanılabilir ancak projenizde NuGet 'den en son .NET 5 paketlerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="5d73d-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest .NET 5 packages from NuGet in your project.</span></span> <span data-ttu-id="5d73d-111">Uzantı paketine da başvurmanız gerekir `Microsoft.Extensions.Http.Polly` .</span><span class="sxs-lookup"><span data-stu-id="5d73d-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="5d73d-112">**Başlangıçta, bir istemciyi Polly 'nin yeniden deneme ilkesiyle yapılandırma**</span><span class="sxs-lookup"><span data-stu-id="5d73d-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="5d73d-113">Önceki bölümlerde gösterildiği gibi, standart Startup.ConfigureServices (...) yönteminde adlandırılmış veya yazılmış bir istemci HttpClient yapılandırması tanımlamanız gerekir, ancak şu anda üstel geri alma ile http yeniden denemeleri için ilkeyi belirten artımlı kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5d73d-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="5d73d-114">**Addpolicyhandler ()** yöntemi, `HttpClient` kullanacağınız nesnelere ilke ekler.</span><span class="sxs-lookup"><span data-stu-id="5d73d-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="5d73d-115">Bu durumda, üstel geri alma ile http yeniden denemeleri için bir Polly ilkesi ekliyor.</span><span class="sxs-lookup"><span data-stu-id="5d73d-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="5d73d-116">Daha modüler bir yaklaşıma sahip olmak için, `Startup.cs` aşağıdaki kodda gösterildiği gibi, http yeniden deneme ilkesi dosya içinde ayrı bir yöntemde tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="5d73d-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="5d73d-117">Polly, yeniden deneme sayısı, üstel geri alma yapılandırması ve hatayı günlüğe kaydetme gibi bir HTTP özel durumu olduğunda gerçekleştirilecek eylemleri içeren bir yeniden deneme ilkesi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d73d-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="5d73d-118">Bu durumda, ilke iki saniyeden itibaren bir üstel yeniden denemeye altı kez denemek üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5d73d-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="5d73d-119">Yeniden deneme ilkesine bir değişim stratejisi ekleyin</span><span class="sxs-lookup"><span data-stu-id="5d73d-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="5d73d-120">Düzenli bir yeniden deneme ilkesi, sisteminizi yüksek eşzamanlılık ve ölçeklenebilirlik durumlarında ve yüksek çekişme kapsamında etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="5d73d-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="5d73d-121">Kısmi kesintiler söz konusu olduğunda birçok istemciden gelen benzer yeniden denemelerin büyük bir bölümünü aşmak için, yeniden deneme algoritmasına/ilkeye bir değişim stratejisi eklemek iyi bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="5d73d-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="5d73d-122">Bu, üstel geri alma 'ya rastgele açıklık ekleyerek uçtan uca sistemin genel performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5d73d-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="5d73d-123">Bu, sorunlar ortaya çıktığında ani artışları yayar.</span><span class="sxs-lookup"><span data-stu-id="5d73d-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="5d73d-124">İlke aşağıdaki örneğe göre gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5d73d-124">The principle is illustrated by the following example:</span></span>

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

<span data-ttu-id="5d73d-125">Polly, proje Web sitesi aracılığıyla üretime hazırlı değişim algoritmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d73d-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="5d73d-126">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5d73d-126">Additional resources</span></span>

- <span data-ttu-id="5d73d-127">**Yeniden deneme biçimi**</span><span class="sxs-lookup"><span data-stu-id="5d73d-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="5d73d-128">**Polly ve ıhttpclientfactory**</span><span class="sxs-lookup"><span data-stu-id="5d73d-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="5d73d-129">**Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**</span><span class="sxs-lookup"><span data-stu-id="5d73d-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="5d73d-130">**Polly: değişim ile yeniden dene**</span><span class="sxs-lookup"><span data-stu-id="5d73d-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="5d73d-131">**Marc Brooker. Değişim: rastgele bir işlem yaparak daha Iyi hale getirme**</span><span class="sxs-lookup"><span data-stu-id="5d73d-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="5d73d-132">[Önceki](use-httpclientfactory-to-implement-resilient-http-requests.md) 
> [Sonraki](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="5d73d-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
