---
title: Üstel geri alma ile özel HTTP çağrısı yeniden denemelerini keşfet
description: Kapalı HTTP hatası senaryolarını işlemek için sıfırdan üstel geri alma ile HTTP çağrı yeniden denemeleri uygulama hakkında bilgi edinin.
ms.date: 10/16/2018
ms.openlocfilehash: 2b40b73a014faa87d4eb42192c72b5a9b6c8d4fa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296123"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Üstel geri alma ile özel HTTP çağrısı yeniden denemelerini keşfet

Dayanıklı mikro hizmetler oluşturmak için olası HTTP hatası senaryolarını işlemeniz gerekir. Bu hataların yerine getirmenin bir yolu, önerilmez, ancak üstel geri alma ile kendi yeniden deneme uygulamanızı oluşturmaktır.

**Önemli bir dikkat:** Bu bölümde, HTTP çağrısı yeniden denemeleri uygulamak için kendi özel kodunuzu nasıl oluşturacağınız gösterilmektedir. Ancak, .NET Core 2,1 ' den beri kullanılabilir `HttpClientFactory` olan, daha basit ve güvenilir bir şekilde kullanılması önerilir. Bu önerilen yaklaşımlar sonraki bölümlerde açıklanmıştır.

İlk araştırma olarak, [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260)' de olduğu gibi üstel geri alma için yardımcı program sınıfıyla kendi kodunuzu uygulayabilir ve aşağıdakine benzer bir kod ekleyebilirsiniz.

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

Bu kodu bir istemci C\# uygulamasında kullanmak (başka bir Web API istemcisi mikro hizmeti, ASP.NET MVC uygulaması, hatta C\# Xamarin uygulaması) basittir. Aşağıdaki örnekte, HttpClient sınıfının nasıl kullanıldığı gösterilmektedir.

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

Bu kodun yalnızca kavram kanıtı olarak uygun olduğunu unutmayın. Sonraki bölümlerde, HttpClientFactory kullanarak daha basit olan daha karmaşık yaklaşımların nasıl kullanılacağı açıklanmaktadır. HttpClientFactory, .NET Core 2,1 sürümünden itibaren Polly gibi kanıtlanmış dayanıklılık kitaplıklarıyla kullanılabilir.

>[!div class="step-by-step"]
>[Önceki](implement-resilient-entity-framework-core-sql-connections.md)İleri
>[](use-httpclientfactory-to-implement-resilient-http-requests.md)
