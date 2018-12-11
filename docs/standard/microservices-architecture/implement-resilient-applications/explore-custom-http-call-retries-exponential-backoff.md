---
title: Üstel geri alma ile özel HTTP çağrı yeniden keşfedin
description: Nasıl size, sıfırdan, olası HTTP hatası senaryolar işlemek için bir üstel geri alma ile HTTP çağrı yeniden uygulayabileceğine öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: b7aaad9199bb275f45fd088a6207d707e8e5751c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145104"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="4a042-103">Üstel geri alma ile özel HTTP çağrı yeniden keşfedin</span><span class="sxs-lookup"><span data-stu-id="4a042-103">Explore custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="4a042-104">Dayanıklı mikro hizmetler oluşturma için olası HTTP hatası senaryolar ele gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a042-104">To create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="4a042-105">Önerilmemesine rağmen bu hataları işleme bir yolu, kendi uygulamanız yeniden deneme ile üstel geri alma oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="4a042-105">One way of handling those failures, although not recommended, is to create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="4a042-106">**Önemli Not:** Bu bölümde, HTTP çağrı yeniden uygulamak için kendi özel kodunuzu nasıl oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a042-106">**Important note:** This section shows you how you could create your own custom code to implement HTTP call retries.</span></span> <span data-ttu-id="4a042-107">Ancak, bunu yapmak için kendi tarafından ancak daha güçlü, güvenilir ve daha basit ancak gibi mekanizmaları kullanın kullanılacak önerilmez `HttpClientFactory` ile Polly, .NET Core 2.1 itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a042-107">However, it is not recommended to do it by your own but to use more powerful and reliable while simpler to use mechanisms, such as `HttpClientFactory` with Polly, available since .NET Core 2.1.</span></span> <span data-ttu-id="4a042-108">Bu yaklaşım önerilen sonraki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4a042-108">Those recommended approaches are explained in the next sections.</span></span> 

<span data-ttu-id="4a042-109">İlk inceleme, üstel geri alma gibi için yardımcı program sınıfı ile kendi kodunuzu uygulayabilirsiniz [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), aşağıdaki gibi kod artı (kullanılabildiği ayrıca şu anda [GitHub Depo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span><span class="sxs-lookup"><span data-stu-id="4a042-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following (which is also available at this [GitHub repo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span></span>

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

<span data-ttu-id="4a042-110">Bu kodu kullanarak C istemci olarak\# uygulama (başka bir Web API'sini istemci mikro hizmet, bir ASP.NET MVC uygulaması veya hatta bir C\# Xamarin uygulama) oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="4a042-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="4a042-111">Aşağıdaki örnekte gösterildiği nasıl HttpClient sınıfını kullanma.</span><span class="sxs-lookup"><span data-stu-id="4a042-111">The following example shows how, using the HttpClient class.</span></span>

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

<span data-ttu-id="4a042-112">Bu kod yalnızca bir kavram kanıtı uygun olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4a042-112">Remember that this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="4a042-113">Sonraki bölümlerde HttpClientFactory kullanarak daha basit olsa da, daha karmaşık yaklaşımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a042-113">The next sections explain how to use more sophisticated approaches while simpler, by using HttpClientFactory.</span></span>
<span data-ttu-id="4a042-114">HttpClientFactory .NET Core 2.1 beri Polly gibi kendini kanıtlamış dayanıklılık kitaplıkları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a042-114">HttpClientFactory is available since .NET Core 2.1, with proven resiliency libraries like Polly.</span></span> 

>[!div class="step-by-step"]
><span data-ttu-id="4a042-115">[Önceki](implement-resilient-entity-framework-core-sql-connections.md)
>[İleri](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="4a042-115">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>