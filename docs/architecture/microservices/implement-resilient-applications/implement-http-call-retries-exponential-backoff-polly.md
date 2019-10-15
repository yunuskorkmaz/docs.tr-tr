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
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="79f51-103">HttpClientFactory ve Polly ilkeleriyle üstel geri alma ile HTTP çağrı yeniden denemeleri uygulayın</span><span class="sxs-lookup"><span data-stu-id="79f51-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="79f51-104">Üstel geri alma ile yeniden denemeler için önerilen yaklaşım, açık kaynaklı [Polly kitaplığı](https://github.com/App-vNext/Polly)gibi daha gelişmiş .net kitaplıklarından faydalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="79f51-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="79f51-105">Polly, esnekliği ve geçici hata işleme özellikleri sağlayan bir .NET kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="79f51-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="79f51-106">Yeniden deneme, devre kesici, Bulkhead yalıtımı, zaman aşımı ve geri dönüş gibi Polly ilkeler uygulayarak bu özellikleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79f51-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="79f51-107">.NET Framework 4. x ve .NET Standard 1,0, 1,1 ve 2,0 (.NET Core desteklenir).</span><span class="sxs-lookup"><span data-stu-id="79f51-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="79f51-108">Ancak, HttpClient ile Polly 'in kitaplığını kullanmak için kendi özel kodunuzu yazmak önemli ölçüde karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="79f51-108">However, writing your own custom code to use Polly’s library with HttpClient can be significantly complex.</span></span> <span data-ttu-id="79f51-109">EShopOnContainers 'ın orijinal sürümünde, Polly tabanlı bir [ResilientHttpClient yapı taşı](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) vardı.</span><span class="sxs-lookup"><span data-stu-id="79f51-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="79f51-110">Ancak [Httpclientfactory](use-httpclientfactory-to-implement-resilient-http-requests.md)sürümü sayesinde, çok daha basit hale gelmiştir ve derleme bloğunun eShopOnContainers 'dan kullanım dışı bırakılması.</span><span class="sxs-lookup"><span data-stu-id="79f51-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), implementing resilient HTTP communication with Polly has become much simpler, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="79f51-111">Aşağıdaki adımlarda, önceki bölümde açıklanan HttpClientFactory ile tümleştirilen, http yeniden denemeleri nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="79f51-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="79f51-112">**ASP.NET Core 2,2 paketlerine başvurun**</span><span class="sxs-lookup"><span data-stu-id="79f51-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="79f51-113">`HttpClientFactory`, .NET Core 2,1 ' den bu yana kullanılabilir ancak projenizde NuGet 'den en son ASP.NET Core 2,2 paketlerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="79f51-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="79f51-114">Genellikle `AspNetCore` metapackage ve Extension Package-1 @no__t gerekir.</span><span class="sxs-lookup"><span data-stu-id="79f51-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="79f51-115">**Başlangıçta, bir istemciyi Polly 'nin yeniden deneme ilkesiyle yapılandırma**</span><span class="sxs-lookup"><span data-stu-id="79f51-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="79f51-116">Önceki bölümlerde gösterildiği gibi, standart başlangıç. ConfigureServices (...) yönteminde adlandırılmış veya yazılmış bir istemci HttpClient yapılandırması tanımlamanız gerekir, ancak şimdi üstel geri alma ile http yeniden denemeleri için ilkeyi belirten artımlı kod eklersiniz. below</span><span class="sxs-lookup"><span data-stu-id="79f51-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="79f51-117">**Addpolicyhandler ()** yöntemi, kullanacağınız `HttpClient` nesnelerine ilke ekler.</span><span class="sxs-lookup"><span data-stu-id="79f51-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="79f51-118">Bu durumda, üstel geri alma ile http yeniden denemeleri için bir Polly ilkesi ekliyor.</span><span class="sxs-lookup"><span data-stu-id="79f51-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="79f51-119">Daha modüler bir yaklaşıma sahip olmak için http yeniden deneme Ilkesi, aşağıdaki kodda gösterildiği gibi `Startup.cs` dosyasında ayrı bir yöntemde tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="79f51-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="79f51-120">Polly, yeniden deneme sayısı, üstel geri alma yapılandırması ve hatayı günlüğe kaydetme gibi bir HTTP özel durumu olduğunda gerçekleştirilecek eylemleri içeren bir yeniden deneme ilkesi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79f51-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="79f51-121">Bu durumda, ilke iki saniyeden itibaren bir üstel yeniden denemeye altı kez denemek üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="79f51-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="79f51-122">Yeniden deneme ilkesine bir değişim stratejisi ekleyin</span><span class="sxs-lookup"><span data-stu-id="79f51-122">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="79f51-123">Düzenli bir yeniden deneme ilkesi, sisteminizi yüksek eşzamanlılık ve ölçeklenebilirlik durumlarında ve yüksek çekişme kapsamında etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="79f51-123">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="79f51-124">Kısmi kesintiler söz konusu olduğunda birçok istemciden gelen benzer yeniden denemelerin büyük bir bölümünü aşmak için, yeniden deneme algoritmasına/ilkeye bir değişim stratejisi eklemek iyi bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="79f51-124">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="79f51-125">Bu, üstel geri alma 'ya rastgele açıklık ekleyerek uçtan uca sistemin genel performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="79f51-125">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="79f51-126">Bu, sorunlar ortaya çıktığında ani artışları yayar.</span><span class="sxs-lookup"><span data-stu-id="79f51-126">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="79f51-127">Bir düz Polly İlkesi kullandığınızda, değişim uygulamak için kod aşağıdaki örneğe benzer olabilir:</span><span class="sxs-lookup"><span data-stu-id="79f51-127">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="79f51-128">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="79f51-128">Additional resources</span></span>

- <span data-ttu-id="79f51-129">**Yeniden deneme biçimi**</span><span class="sxs-lookup"><span data-stu-id="79f51-129">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="79f51-130">**Polly ve HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="79f51-130">**Polly and HttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="79f51-131">**Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**</span><span class="sxs-lookup"><span data-stu-id="79f51-131">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="79f51-132">**Marc Brooker. Değişim: rastgele bir işlem yaparak daha Iyi hale getirme**</span><span class="sxs-lookup"><span data-stu-id="79f51-132">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="79f51-133">[Önceki](explore-custom-http-call-retries-exponential-backoff.md)
>[İleri](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="79f51-133">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
