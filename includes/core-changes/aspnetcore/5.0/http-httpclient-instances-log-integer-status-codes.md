---
ms.openlocfilehash: 47f42305f4106f5e05e555a859f13c41bb950519
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811294"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="9942a-101">HTTP: ıhttpclientfactory günlük tamsayı durum kodları tarafından oluşturulan HttpClient örnekleri</span><span class="sxs-lookup"><span data-stu-id="9942a-101">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="9942a-102"><xref:System.Net.Http.HttpClient><xref:System.Net.Http.IHttpClientFactory>günlük http durum kodları tarafından, durum kodu adları yerine tamsayılar olarak oluşturulan örnekler.</span><span class="sxs-lookup"><span data-stu-id="9942a-102"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9942a-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9942a-103">Version introduced</span></span>

<span data-ttu-id="9942a-104">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="9942a-104">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9942a-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9942a-105">Old behavior</span></span>

<span data-ttu-id="9942a-106">Günlüğe kaydetme, HTTP durum kodlarının metinsel açıklamalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9942a-106">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="9942a-107">Aşağıdaki günlük iletilerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9942a-107">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a><span data-ttu-id="9942a-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9942a-108">New behavior</span></span>

<span data-ttu-id="9942a-109">Günlüğe kaydetme, HTTP durum kodlarının tamsayı değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9942a-109">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="9942a-110">Aşağıdaki günlük iletilerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9942a-110">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a><span data-ttu-id="9942a-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9942a-111">Reason for change</span></span>

<span data-ttu-id="9942a-112">Bu günlüğe kaydetmenin özgün davranışı, her zaman kullanılan tamsayı değerlerini içeren ASP.NET Core diğer bölümleri ile tutarsız.</span><span class="sxs-lookup"><span data-stu-id="9942a-112">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="9942a-113">Tutarsızlık, oturum açma gibi yapılandırılmış günlük sistemleri aracılığıyla sorgu yapmayı [zorlaştırır.](https://www.elastic.co/elasticsearch/)</span><span class="sxs-lookup"><span data-stu-id="9942a-113">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="9942a-114">Daha fazla bağlam için bkz. [DotNet/Extensions # 1549](https://github.com/dotnet/extensions/issues/1549).</span><span class="sxs-lookup"><span data-stu-id="9942a-114">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="9942a-115">Değer aralıklarında sorgulara izin verdiğinden tamsayı değerlerinin kullanılması metinden daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="9942a-115">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="9942a-116">Tamsayı durum kodunu yakalamak için başka bir günlük değeri eklenmesi kabul edildi.</span><span class="sxs-lookup"><span data-stu-id="9942a-116">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="9942a-117">Ne yazık ki, ASP.NET Core geri kalanı ile başka bir tutarsızlık ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="9942a-117">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="9942a-118">HttpClient günlüğü ve HTTP sunucusu/barındırma günlüğü, zaten aynı `StatusCode` anahtar adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9942a-118">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9942a-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9942a-119">Recommended action</span></span>

<span data-ttu-id="9942a-120">En iyi seçenek, günlük sorgularını durum kodlarının tamsayı değerlerini kullanacak şekilde güncelleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="9942a-120">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="9942a-121">Bu seçenek, birden çok ASP.NET Core sürümünde sorgu yazarken zorluk gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9942a-121">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="9942a-122">Ancak, bu amaçla tamsayıların kullanılması günlükleri sorgulamak için çok daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="9942a-122">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="9942a-123">Eski davranışla uyumluluğu zorlamak ve metin durum kodları kullanmak gerekirse, `IHttpClientFactory` günlük kaydını kendi ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9942a-123">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="9942a-124">Aşağıdaki sınıfların .NET Core 3,1 sürümlerini projenize kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="9942a-124">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="9942a-125">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="9942a-125">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="9942a-126">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="9942a-126">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="9942a-127">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="9942a-127">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="9942a-128">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="9942a-128">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="9942a-129">[Microsoft. Extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet paketindeki ortak türlerle çakışmaları önlemek için sınıfları yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9942a-129">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="9942a-130">Uygulamasının yerleşik uygulamasını, `LoggingHttpMessageHandlerBuilderFilter` projenin yönteminde kendi ile değiştirin `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="9942a-130">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="9942a-131">Örnek:</span><span class="sxs-lookup"><span data-stu-id="9942a-131">For example:</span></span>

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

#### <a name="category"></a><span data-ttu-id="9942a-132">Kategori</span><span class="sxs-lookup"><span data-stu-id="9942a-132">Category</span></span>

<span data-ttu-id="9942a-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9942a-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9942a-134">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9942a-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
