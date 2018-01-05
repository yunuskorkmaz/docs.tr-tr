---
title: "Devre kesici düzeni uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Devre kesici düzeni uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d7db6899068f84f9165022cfbf17767a75e7db9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="56491-104">Devre kesici düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="56491-104">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="56491-105">Daha önce belirtildiği gibi bir uzak hizmet veya kaynağına bağlanmaya çalıştığınızda oluşabilir gibi kurtarmak için değişken bir süre alabilir hataları işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="56491-105">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="56491-106">Bu tür bir hata işleme kararlılık ve bir uygulamanın dayanıklılık artırabilir.</span><span class="sxs-lookup"><span data-stu-id="56491-106">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="56491-107">Dağıtılmış bir ortama uzak kaynaklar ve hizmetleri çağrıları yavaş ağ bağlantıları ve zaman aşımları, gibi geçici hataları nedeniyle başarısız veya değiştirilebilir kaynakları eşitlenmediğini yavaş veya geçici olarak kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="56491-107">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="56491-108">Kısa bir süre sonra kendilerini genellikle bu hataları düzeltin ve güçlü bir bulut uygulama yeniden deneme düzeni gibi bir strateji kullanarak işlemek için hazırlıklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56491-108">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="56491-109">Ancak, aynı zamanda olabilir hataları düzeltmek için daha uzun sürebilir beklenmeyen olaylar nedeniyle olduğu durumlarda.</span><span class="sxs-lookup"><span data-stu-id="56491-109">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="56491-110">Bu hataları bağlantı kısmi bir kayıp derecesi tam başarısızlık, bir hizmetin aralığında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="56491-110">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="56491-111">Bu durumlarda, sürekli olarak başarısız olması beklenmez bir işlemi yeniden denemek bir uygulama için bir durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="56491-111">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="56491-112">Bunun yerine, uygulama işlemi başarısız oldu kabul etmek ve hata uygun şekilde işlemek için kodlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56491-112">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="56491-113">Devre kesici düzeni yeniden deneme düzeni farklı bir amaca sahiptir.</span><span class="sxs-lookup"><span data-stu-id="56491-113">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="56491-114">Yeniden deneme düzeni işlem sonunda başarılı Beklenti bir işlemi yeniden denemek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="56491-114">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="56491-115">Devre kesici düzeni büyük olasılıkla başarısız olacak bir işlemi gerçekleştirilirken bir uygulamanın engeller.</span><span class="sxs-lookup"><span data-stu-id="56491-115">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="56491-116">Bir uygulama, bu iki desenleri devre kesici aracılığıyla bir işlem çağırmak için Yeniden Dene'yi desenini kullanarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-116">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="56491-117">Ancak, yeniden deneme mantığı devre kesici tarafından döndürülen tüm özel durumlar için hassas olmalıdır ve bir arıza geçici değil devre kesici olduğunu gösteriyorsa, yeniden deneme girişimleri abandon.</span><span class="sxs-lookup"><span data-stu-id="56491-117">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="56491-118">İle Polly devre kesici düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="56491-118">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="56491-119">Yeniden deneme uygularken, Polly gibi kanıtlanmış .NET kitaplıklarına yararlanmak için önerilen yaklaşım hattı ayırıcıları için olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="56491-119">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="56491-120">EShopOnContainers uygulama, HTTP yeniden deneme uygularken Polly devre kesici İlkesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="56491-120">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="56491-121">Aslında, uygulama her iki ilkeyi ResilientHttpClient yardımcı program sınıfı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="56491-121">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="56491-122">(EShopOnContainers) gelen HTTP isteklerini ResilientHttpClient türünde bir nesne kullandığınızda, her iki bu ilkeleri uygulayarak, ancak ek ilkeler çok ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-122">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="56491-123">Yalnızca Burada HTTP çağrısı deneme için kullanılan kod için kod devre kesici İlkesi kullanmak için ilkeleri listesine aşağıdaki kodu sonunda gösterildiği gibi eklediğiniz eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="56491-123">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

<span data-ttu-id="56491-124">Kod HTTP sarmalayıcı bir ilke ekler.</span><span class="sxs-lookup"><span data-stu-id="56491-124">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="56491-125">İlke olarak kod ardışık özel durumları (bir satır durumlar), belirtilen sayıda algıladığında açıldığını devre kesici tanımlar (Bu durumda 5) exceptionsAllowedBeforeBreaking parametresi geçirildi.</span><span class="sxs-lookup"><span data-stu-id="56491-125">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="56491-126">Bağlantı hattı açık olduğunda, HTTP isteklerini çalışmaz, ancak özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="56491-126">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="56491-127">Bağlantı hattı ayırıcıları da bir geri dönüş altyapısı, bir istemci uygulaması'ndan farklı bir ortamda dağıtılan belirli kaynak ya da HTTP çağrısıyla gerçekleştiriyor hizmet sorunlarınız varsa isteklerini yeniden yönlendirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56491-127">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="56491-128">Yalnızca, arka uç mikro ancak, istemci uygulamaları etkiler merkezinde bir kesinti ise bu şekilde, istemci uygulamaları için geri dönüş Hizmetleri yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-128">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="56491-129">Polly bu otomatikleştirmek için yeni bir ilke planlama [yük devretme İlkesi](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryo.</span><span class="sxs-lookup"><span data-stu-id="56491-129">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="56491-130">Elbette, tüm bu durumlarda, yük devretmeyi onu sizin için konum saydamlığı olan Azure tarafından otomatik olarak yönetilen sahip aksine .NET kodundaki yönettiği özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="56491-130">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="56491-131">EShopOnContainers ResilientHttpClient yardımcı programı sınıfından kullanma</span><span class="sxs-lookup"><span data-stu-id="56491-131">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="56491-132">.NET HttpClient sınıfı kullanma için benzer bir şekilde ResilientHttpClient yardımcı sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="56491-132">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="56491-133">EShopOnContainers MVC web uygulamasından (OrderController tarafından kullanılan OrderingService Aracısı sınıfı) aşağıdaki örnekte, ResilientHttpClient Nesne oluşturucusu httpClient parametresi üzerinden eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="56491-133">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="56491-134">Ardından nesnesi, HTTP isteklerini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56491-134">Then the object is used to perform HTTP requests.</span></span>

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="56491-135">Her \_apiClient üye nesne kullanıldığında, dahili olarak Polly policiesؙ ile sarmalayıcı sınıfı kullanır; yeniden deneme ilkesi, devre kesici ilke ve Polly ilkeleri koleksiyondan uygulamak isteyebilirsiniz başka herhangi bir ilke.</span><span class="sxs-lookup"><span data-stu-id="56491-135">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="56491-136">Yeniden deneme eShopOnContainers içinde test etme</span><span class="sxs-lookup"><span data-stu-id="56491-136">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="56491-137">Her bir Docker ana eShopOnContainers çözüm başlattığınızda, birden çok kapsayıcı başlatmak gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="56491-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="56491-138">Bazı kapsayıcıların başlatın ve başlatma, SQL Server kapsayıcı gibi daha yavaş.</span><span class="sxs-lookup"><span data-stu-id="56491-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="56491-139">Görüntüleri ve veritabanını ayarlamak gerektiğinden bu Docker, eShopOnContainers uygulamasına dağıtmak ilk kez özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="56491-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="56491-140">Bazı kapsayıcıları kapsayıcılar arasındaki bağımlılıkları ayarlasanız bile başkalarının başlangıçta HTTP özel durumlar, throw Hizmetleri rest neden olabilir daha yavaş başlatma olgu önceki bölümlerde açıklandığı gibi düzeyi, docker-oluşturun.</span><span class="sxs-lookup"><span data-stu-id="56491-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="56491-141">Bu docker-kapsayıcılar arasındaki bağımlılıkları oluşturan öğeler yalnızca işlem düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="56491-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="56491-142">Kapsayıcının giriş noktası işlem başlatılamamış olabilir, ancak SQL Server sorguları için hazır olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="56491-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="56491-143">Sonuç art arda hatalar olabilir ve uygulama, belirli bir kapsayıcıda tüketen çalışılırken bir özel durum alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="56491-144">Buluta Uygulama dağıtırken, bu tür hatalara başlangıçta görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="56491-145">Bu durumda, orchestrators kapsayıcıları bir düğüm veya VM (yani yeni örnekleri başlatılıyor) diğerine taşıma kapsayıcı sayısı küme düğümleri arasında dengeleme olduğunda.</span><span class="sxs-lookup"><span data-stu-id="56491-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="56491-146">EShopOnContainers bu sorunu çözer daha önce gösterilen yeniden deneme modeli kullanarak bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="56491-146">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="56491-147">Neden, çözüm başlatılırken, günlük izlemelerini veya aşağıdaki gibi uyarılar alabilirsiniz şöyledir:</span><span class="sxs-lookup"><span data-stu-id="56491-147">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="56491-148">"**Polly'nın RetryPolicy ile uygulanan 1 yeniden deneme**, nedeni: System.Net.Http.HttpRequestException: isteği gönderilirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="56491-148">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="56491-149"> ---&gt;System.Net.Http.CurlException: sunucusuna bağlanamadı\\System.Net.Http.CurlHandler.ThrowIfCURLEError (CURLcode hatası), n\\adresindeki n \[... \].</span><span class="sxs-lookup"><span data-stu-id="56491-149"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="56491-150">Devre kesici eShopOnContainers içinde test etme</span><span class="sxs-lookup"><span data-stu-id="56491-150">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="56491-151">Bağlantı hattı açın ve eShopOnContainers ile test birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="56491-151">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="56491-152">Bir seçenektir için izin verilen 1 devre kesici İlkesi'nde yeniden deneme sayısını azaltmak ve Docker tam çözümü yeniden dağıtın.</span><span class="sxs-lookup"><span data-stu-id="56491-152">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="56491-153">Tek bir yeniden deneme ile dağıtım sırasında bir HTTP isteği başarısız olur şansı yoktur, devre kesici açar ve bir hata alıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="56491-153">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="56491-154">Uygulanan özel ara yazılımı kullanmak için başka bir seçenektir `Basket` mikro hizmet.</span><span class="sxs-lookup"><span data-stu-id="56491-154">Another option is to use custom middleware that is implemented in the `Basket` microservice.</span></span> <span data-ttu-id="56491-155">Bu ara yazılım etkinleştirildiğinde, tüm HTTP isteklerini yakalar ve durum kodu 500 döndürür.</span><span class="sxs-lookup"><span data-stu-id="56491-155">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="56491-156">Ara yazılım için başarısız olan bir GET isteği yaparak etkinleştirebilirsiniz aşağıdaki gibi URI:</span><span class="sxs-lookup"><span data-stu-id="56491-156">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="56491-157">GET/başarısız</span><span class="sxs-lookup"><span data-stu-id="56491-157">GET /failing</span></span>

<span data-ttu-id="56491-158">Bu istek ara yazılım geçerli durumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="56491-158">This request returns the current state of the middleware.</span></span> <span data-ttu-id="56491-159">Ara yazılım etkinleştirilirse, isteği durum kodu 500 döndürür.</span><span class="sxs-lookup"><span data-stu-id="56491-159">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="56491-160">Ara yazılım devre dışıysa, yanıt yoktur.</span><span class="sxs-lookup"><span data-stu-id="56491-160">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="56491-161">GET/başarısız? etkinleştir</span><span class="sxs-lookup"><span data-stu-id="56491-161">GET /failing?enable</span></span>

<span data-ttu-id="56491-162">Bu istek ara yazılım sağlar.</span><span class="sxs-lookup"><span data-stu-id="56491-162">This request enables the middleware.</span></span>

-   <span data-ttu-id="56491-163">GET/başarısız? devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="56491-163">GET /failing?disable</span></span>

<span data-ttu-id="56491-164">Bu istek Ara devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="56491-164">This request disables the middleware.</span></span>

<span data-ttu-id="56491-165">Örneğin, uygulama çalışmaya başladıktan sonra aşağıdaki URI herhangi bir tarayıcı kullanarak bir istek yaparak ara yazılım etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-165">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="56491-166">Sıralama mikro hizmet bağlantı noktası 5103 oluşturun kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="56491-166">Note that the ordering microservice uses port 5103.</span></span>

<span data-ttu-id="56491-167">http://localhost:5103 / başarısız? etkinleştir</span><span class="sxs-lookup"><span data-stu-id="56491-167">http://localhost:5103/failing?enable</span></span>

<span data-ttu-id="56491-168">Ardından URI kullanılarak durumunu denetleyebilirsiniz [http://localhost:5103 / başarısız](http://localhost:5103/failing), Şekil 10-4'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="56491-168">You can then check the status using the URI [http://localhost:5103/failing](http://localhost:5103/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="56491-169">**Şekil 10-4**.</span><span class="sxs-lookup"><span data-stu-id="56491-169">**Figure 10-4**.</span></span> <span data-ttu-id="56491-170">"Başarısız" durumu denetimini devre dışı ASP.NET ara yazılım – bu durumda.</span><span class="sxs-lookup"><span data-stu-id="56491-170">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="56491-171">Bu noktada, durum koduyla çağırmanız her 500 Sepeti mikro hizmet yanıt bunu çağırır.</span><span class="sxs-lookup"><span data-stu-id="56491-171">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="56491-172">Ara yazılım çalışmaya başladıktan sonra MVC web uygulamasından bir sipariş oluşturmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-172">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="56491-173">İstekler başarısız olduğu için bağlantı hattı açılır.</span><span class="sxs-lookup"><span data-stu-id="56491-173">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="56491-174">Aşağıdaki örnekte, MVC web uygulaması bir catch olduğunu görebilirsiniz sipariş yerleştirme mantığındaki engelleyin.</span><span class="sxs-lookup"><span data-stu-id="56491-174">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="56491-175">Bir açık hattı özel durum kodu yakalar, kullanıcı beklenecek söyleyen kolay bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="56491-175">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            //… Other code
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode                 
            HandleBrokenCircuitException();
        }
        return View();
    }       

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

<span data-ttu-id="56491-176">Bir özeti aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="56491-176">Here’s a summary.</span></span> <span data-ttu-id="56491-177">Yeniden deneme ilkesi, HTTP hataları alır ve HTTP isteği yapmak için birkaç kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="56491-177">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="56491-178">Deneme sayısı (Bu durumda, 5) devre kesici ilkesi için en fazla sayı kümesi ulaştığında, uygulamanın bir BrokenCircuitException oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56491-178">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="56491-179">Sonuç, Şekil 10-5'te gösterildiği gibi kolay bir ileti olur.</span><span class="sxs-lookup"><span data-stu-id="56491-179">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="56491-180">**Şekil 10-5**.</span><span class="sxs-lookup"><span data-stu-id="56491-180">**Figure 10-5**.</span></span> <span data-ttu-id="56491-181">Devre kesici kullanıcı Arabirimi için bir hata döndürüyor</span><span class="sxs-lookup"><span data-stu-id="56491-181">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="56491-182">Bağlantı hattı açmak ne zaman farklı mantığı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-182">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="56491-183">Ya da bir geri dönüş datacenter veya yedek arka uç sistemi ise farklı bir arka uç mikro hizmet karşı bir HTTP isteği deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56491-183">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="56491-184">Son olarak, diğer bir olasılık CircuitBreakerPolicy için (hangi açık zorlar ve bağlantı hattı açık tutar) ayırma ve (hangi yeniden kapatır) sıfırlama kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="56491-184">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="56491-185">Bu ayırma ve doğrudan sıfırlama ilkesini çağıran bir yardımcı programı HTTP uç noktası oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56491-185">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="56491-186">Bu tür, bir HTTP uç nokta da, düzgün, geçici olarak yükseltmek istediğinizde gibi bir aşağı akış sistem yalıtılması üretimde güvenli kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56491-186">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="56491-187">Ya da hatalı olması için şüpheleniyorsanız bir aşağı akış sistemi el ile korunacak bağlantı hattı trip.</span><span class="sxs-lookup"><span data-stu-id="56491-187">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="56491-188">Yeniden deneme ilkesi değişim stratejisi ekleme</span><span class="sxs-lookup"><span data-stu-id="56491-188">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="56491-189">Normal bir yeniden deneme ilkesi sisteminizi durumlarda yüksek eşzamanlılık ve ölçeklenebilirlik ve yüksek çakışma altında etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="56491-189">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="56491-190">Kısmi kesintiler durumunda birçok istemcilerden gelen benzer yeniden deneme yükselmeleri üstesinden gelmek için bir değişim stratejisi yeniden deneme algoritması/ilkesine eklemek için iyi geçici bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="56491-190">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="56491-191">Üstel geri alma için rastgele ekleyerek bu uçtan uca sistem genel performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="56491-191">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="56491-192">Sorunlar çıkması olduğunda bu ani yayar.</span><span class="sxs-lookup"><span data-stu-id="56491-192">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="56491-193">Polly kullandığınızda, değişim uygulamak için kodu aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="56491-193">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="56491-194">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="56491-194">Additional resources</span></span>

-   <span data-ttu-id="56491-195">**Desen yeniden deneme**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="56491-195">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="56491-196">**Bağlantı dayanıklılığı** (Entity Framework Çekirdek) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="56491-196">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="56491-197">**Polly** (.NET esnekliği ve geçici hata işleme kitaplık) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="56491-197">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="56491-198">**Devre kesici düzeni**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="56491-198">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="56491-199">**Marc Brooker. Değişim: Şeyler rastgele ile daha iyi yapma** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="56491-199">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="56491-200">[Önceki] (implement-http-call-retries-exponential-backoff-polly.md) [sonraki] (İzleyicisi-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="56491-200">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>
