---
title: Polly üstel geri alma ile HTTP çağrı yeniden denemelerini uygulama
description: Polly ve HttpClientFactory ile HTTP başarısızlıklarını nasıl ele alabileceğinizi öğrenin.
ms.date: 01/07/2019
ms.openlocfilehash: aa500b5525eff9f0bbf91bf98de8945f7c84704f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296074"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="228b2-103">HttpClientFactory ve Polly ilkeleriyle üstel geri alma ile HTTP çağrı yeniden denemeleri uygulayın</span><span class="sxs-lookup"><span data-stu-id="228b2-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="228b2-104">Üstel geri alma ile yeniden denemeler için önerilen yaklaşım, açık kaynaklı [Polly kitaplığı](https://github.com/App-vNext/Polly)gibi daha gelişmiş .net kitaplıklarından faydalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="228b2-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="228b2-105">Polly, esnekliği ve geçici hata işleme özellikleri sağlayan bir .NET kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="228b2-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="228b2-106">Yeniden deneme, devre kesici, Bulkhead yalıtımı, zaman aşımı ve geri dönüş gibi Polly ilkeler uygulayarak bu özellikleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="228b2-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="228b2-107">Polly, .NET 4. x ve .NET Standard kitaplığı 1,0 (.NET Core ' u destekler) olarak hedefler.</span><span class="sxs-lookup"><span data-stu-id="228b2-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="228b2-108">Ancak, HttpClient ile kendi özel kodunuzla Polly 'in kitaplığını kullanmak önemli ölçüde karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="228b2-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="228b2-109">EShopOnContainers 'ın orijinal sürümünde, Polly tabanlı bir [ResilientHttpClient yapı taşı](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) vardı.</span><span class="sxs-lookup"><span data-stu-id="228b2-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="228b2-110">Ancak [Httpclientfactory](use-httpclientfactory-to-implement-resilient-http-requests.md)sürümü sayesınde dayanıklı http iletişimi, uygulama için çok daha basit hale gelmiştir, böylece, derleme bloğu eShopOnContainers 'dan kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="228b2-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), resilient HTTP communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="228b2-111">Aşağıdaki adımlarda, önceki bölümde açıklanan HttpClientFactory ile tümleştirilen, http yeniden denemeleri nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="228b2-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="228b2-112">**ASP.NET Core 2,2 paketlerine başvurun**</span><span class="sxs-lookup"><span data-stu-id="228b2-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="228b2-113">`HttpClientFactory`, .NET Core 2,1 sürümünden itibaren kullanılabilir ancak projenizde NuGet 'den en son ASP.NET Core 2,2 paketlerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="228b2-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="228b2-114">Genellikle `AspNetCore` metapackage ve uzantı paketinin `Microsoft.Extensions.Http.Polly`olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="228b2-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="228b2-115">**Başlangıçta, bir istemciyi Polly 'nin yeniden deneme ilkesiyle yapılandırma**</span><span class="sxs-lookup"><span data-stu-id="228b2-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="228b2-116">Önceki bölümlerde gösterildiği gibi, standart başlangıç. ConfigureServices (...) yönteminde adlandırılmış veya yazılmış bir istemci HttpClient yapılandırması tanımlamanız gerekir, ancak şimdi üstel geri alma ile http yeniden denemeleri için ilkeyi belirten artımlı kod eklersiniz. below</span><span class="sxs-lookup"><span data-stu-id="228b2-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="228b2-117">**Addpolicyhandler ()** yöntemi, kullanacağınız `HttpClient` nesnelere ilke ekler.</span><span class="sxs-lookup"><span data-stu-id="228b2-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="228b2-118">Bu durumda, üstel geri alma ile http yeniden denemeleri için bir Polly ilkesi ekliyor.</span><span class="sxs-lookup"><span data-stu-id="228b2-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="228b2-119">Daha modüler bir yaklaşıma sahip olmak için, aşağıdaki kodda gösterildiği gibi, http yeniden deneme ilkesi `Startup.cs` dosya içinde ayrı bir yöntemde tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="228b2-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="228b2-120">Polly, yeniden deneme sayısı, üstel geri alma yapılandırması ve hatayı günlüğe kaydetme gibi bir HTTP özel durumu olduğunda gerçekleştirilecek eylemleri içeren bir yeniden deneme ilkesi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="228b2-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="228b2-121">Bu durumda, ilke iki saniyeden itibaren bir üstel yeniden denemeye altı kez denemek üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="228b2-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="228b2-122">Bu nedenle, altı kez denenecek ve her yeniden deneme arasındaki saniyeler iki saniyeden itibaren üstel olacaktır.</span><span class="sxs-lookup"><span data-stu-id="228b2-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="228b2-123">Yeniden deneme ilkesine bir değişim stratejisi ekleyin</span><span class="sxs-lookup"><span data-stu-id="228b2-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="228b2-124">Düzenli bir yeniden deneme ilkesi, sisteminizi yüksek eşzamanlılık ve ölçeklenebilirlik durumlarında ve yüksek çekişme kapsamında etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="228b2-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="228b2-125">Kısmi kesintiler söz konusu olduğunda birçok istemciden gelen benzer yeniden denemelerin büyük bir bölümünü aşmak için, yeniden deneme algoritmasına/ilkeye bir değişim stratejisi eklemek iyi bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="228b2-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="228b2-126">Bu, üstel geri alma 'ya rastgele açıklık ekleyerek uçtan uca sistemin genel performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="228b2-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="228b2-127">Bu, sorunlar ortaya çıktığında ani artışları yayar.</span><span class="sxs-lookup"><span data-stu-id="228b2-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="228b2-128">Bir düz Polly İlkesi kullandığınızda, değişim uygulamak için kod aşağıdaki örneğe benzer olabilir:</span><span class="sxs-lookup"><span data-stu-id="228b2-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="228b2-129">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="228b2-129">Additional resources</span></span>

- <span data-ttu-id="228b2-130">**Yeniden deneme biçimi**</span><span class="sxs-lookup"><span data-stu-id="228b2-130">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="228b2-131">**Polly ve HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="228b2-131">**Polly and HttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="228b2-132">**Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**</span><span class="sxs-lookup"><span data-stu-id="228b2-132">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="228b2-133">**Marc Brooker. Den Rastgele hale getirmek için şeyleri daha Iyi hale getirme**</span><span class="sxs-lookup"><span data-stu-id="228b2-133">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="228b2-134">[Önceki](explore-custom-http-call-retries-exponential-backoff.md)İleri
>[](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="228b2-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
