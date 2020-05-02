---
ms.openlocfilehash: 44d33fb28e66e590e4604c6dd2c73616e4c5e943
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728289"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a>HTTP: ıhttpclientfactory günlük tamsayı durum kodları tarafından oluşturulan HttpClient örnekleri

<xref:System.Net.Http.HttpClient>günlük HTTP durum <xref:System.Net.Http.IHttpClientFactory> kodları tarafından, durum kodu adları yerine tamsayılar olarak oluşturulan örnekler.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

#### <a name="old-behavior"></a>Eski davranış

Günlüğe kaydetme, HTTP durum kodlarının metinsel açıklamalarını kullanır. Aşağıdaki günlük iletilerini göz önünde bulundurun:

```
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a>Yeni davranış

Günlüğe kaydetme, HTTP durum kodlarının tamsayı değerlerini kullanır. Aşağıdaki günlük iletilerini göz önünde bulundurun:

```
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu günlüğe kaydetmenin özgün davranışı, her zaman kullanılan tamsayı değerlerini içeren ASP.NET Core diğer bölümleri ile tutarsız. Tutarsızlık, oturum açma gibi yapılandırılmış günlük sistemleri aracılığıyla sorgu yapmayı [zorlaştırır.](https://www.elastic.co/elasticsearch/) Daha fazla bağlam için bkz. [DotNet/Extensions # 1549](https://github.com/dotnet/extensions/issues/1549).

Değer aralıklarında sorgulara izin verdiğinden tamsayı değerlerinin kullanılması metinden daha esnektir.

Tamsayı durum kodunu yakalamak için başka bir günlük değeri eklenmesi kabul edildi. Ne yazık ki, ASP.NET Core geri kalanı ile başka bir tutarsızlık ortaya çıkarabilir. HttpClient günlüğü ve HTTP sunucusu/barındırma günlüğü, zaten aynı `StatusCode` anahtar adını kullanır.

#### <a name="recommended-action"></a>Önerilen eylem

En iyi seçenek, günlük sorgularını durum kodlarının tamsayı değerlerini kullanacak şekilde güncelleştirmedir. Bu seçenek, birden çok ASP.NET Core sürümünde sorgu yazarken zorluk gösterebilir. Ancak, bu amaçla tamsayıların kullanılması günlükleri sorgulamak için çok daha esnektir.

Eski davranışla uyumluluğu zorlamak ve metin durum kodları kullanmak gerekirse, `IHttpClientFactory` günlük kaydını kendi ile değiştirin:

1. Aşağıdaki sınıfların .NET Core 3,1 sürümlerini projenize kopyalayın:

    * [LoggingHttpMessageHandlerBuilderFilter](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [LoggingHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [LoggingScopeHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [HttpHeadersLogValue](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. [Microsoft. Extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet paketindeki ortak türlerle çakışmaları önlemek için sınıfları yeniden adlandırın.

1. Uygulamasının `LoggingHttpMessageHandlerBuilderFilter` yerleşik uygulamasını, projenin `Startup.ConfigureServices` yönteminde kendi ile değiştirin. Örneğin:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        var descriptors = services.Where(
            s => s.ServiceType == typeof(IHttpMessageHandlerBuilderFilter));
        foreach (var descriptor in descriptors)
        {
            services.Remove(descriptor);
        }

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
