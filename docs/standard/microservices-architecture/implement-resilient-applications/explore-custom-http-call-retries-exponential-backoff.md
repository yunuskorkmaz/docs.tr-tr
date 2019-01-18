---
title: Üstel geri alma ile özel HTTP çağrı yeniden keşfedin
description: Sıfırdan olası HTTP hatası senaryolar işlemek için üstel geri alma ile HTTP çağrı yeniden nasıl uygulayabileceğine öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: fdbc09cddde34cb8897e1d5b105cb15c863b59ce
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362255"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Üstel geri alma ile özel HTTP çağrı yeniden keşfedin

Dayanıklı mikro hizmetler oluşturma için olası HTTP hatası senaryolar ele gerekir. Önerilmemesine rağmen bu hataları işleme bir yolu, kendi uygulamanız yeniden deneme ile üstel geri alma oluşturmaktır.

**Önemli Not:** Bu bölümde, HTTP çağrı yeniden uygulamak için kendi özel kodunuzu nasıl oluşturabileceğinizi gösterir. Ancak, daha güçlü kullanmak için kendi ancak yapmak için önerilen ve daha basit ancak gibi mekanizmaları kullanın güvenilir olmayan `HttpClientFactory` ile Polly, .NET Core 2.1 itibaren kullanılabilir. Bu yaklaşım önerilen sonraki bölümde açıklanmıştır.

İlk inceleme, üstel geri alma gibi için yardımcı program sınıfı ile kendi kodunuzu uygulayabilirsiniz [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), ayrıca aşağıdaki gibi kod.

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

Bu kodu kullanarak C istemci olarak\# uygulama (başka bir Web API'sini istemci mikro hizmet, bir ASP.NET MVC uygulaması veya hatta bir C\# Xamarin uygulama) oldukça basittir. Aşağıdaki örnekte gösterildiği nasıl HttpClient sınıfını kullanma.

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

Bu kod yalnızca bir kavram kanıtı uygun olduğunu unutmayın. Sonraki bölümlerde HttpClientFactory kullanarak daha basit olsa da, daha karmaşık yaklaşımları açıklanmaktadır. HttpClientFactory .NET Core 2.1 beri Polly gibi kendini kanıtlamış dayanıklılık kitaplıkları ile kullanılabilir.

>[!div class="step-by-step"]
>[Önceki](implement-resilient-entity-framework-core-sql-connections.md)
>[İleri](use-httpclientfactory-to-implement-resilient-http-requests.md)