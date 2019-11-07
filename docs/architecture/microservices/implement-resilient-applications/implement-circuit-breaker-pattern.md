---
title: Devre kesici modelini uygulama
description: Devre kesici düzeninin http yeniden denemeleri için tamamlayıcı bir sistem olarak nasıl uygulanacağını öğrenin.
ms.date: 10/16/2018
ms.openlocfilehash: 00ca39b4b6fac37ff60adf128c3f4e22c5fc14e2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732829"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="a1ef7-103">Devre Kesici desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="a1ef7-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="a1ef7-104">Daha önce belirtildiği gibi, uzak bir hizmete veya kaynağa bağlanmayı denediğinizde gerçekleşebileceği gibi, kurtarmak için değişken bir süre sürebilecek hataları işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="a1ef7-105">Bu tür bir hatanın yönetilmesi, bir uygulamanın kararlılığını ve dayanıklılığını iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="a1ef7-106">Dağıtılmış bir ortamda, uzak kaynak ve hizmetlere yapılan çağrılar, yavaş ağ bağlantıları ve zaman aşımları gibi geçici hatalar nedeniyle veya kaynaklar yavaş yanıt veriyorsa veya geçici olarak devre dışı bırakılırsa başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="a1ef7-107">Bu hatalar genellikle kısa bir süre sonra kendilerini düzeltir ve güçlü bir bulut uygulaması, "yeniden deneme biçimi" gibi bir strateji kullanılarak bunları işleyecek şekilde hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span>

<span data-ttu-id="a1ef7-108">Ancak, hataların düzeltilmesi çok daha uzun sürebilecek beklenmeyen olaylardan kaynaklanan durumlar da olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="a1ef7-109">Bu hatalar, bir hizmetin tamamen başarısızlığına yönelik kısmi bir bağlantı kaybından önem düzeyi olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="a1ef7-110">Bu durumlarda, bir uygulamanın başarılı olması olası olmayan bir işlemi sürekli olarak yeniden denemesi için bu durum daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-110">In these situations, it might be pointless for an application to continually retry an operation that's unlikely to succeed.</span></span>

<span data-ttu-id="a1ef7-111">Bunun yerine, işlemin başarısız olduğunu kabul etmek ve hatayı uygun şekilde işlemek için uygulamanın kodlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="a1ef7-112">Http yeniden denemeleri daha sorunsuz bir şekilde kullanılması, kendi yazılımınız dahilinde hizmet reddi ([DOS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) saldırısı oluşturulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="a1ef7-113">Mikro hizmet başarısız olur veya yavaş çalışır, birden fazla istemci başarısız istekleri tekrar tekrar deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="a1ef7-114">Bu, başarısız olan hizmette hedeflenen trafiği üstel olarak artırarak tehlikeli bir risk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="a1ef7-115">Bu nedenle, çalışmaya devam etmek için değer olmadığında aşırı isteklerin durdurulması için bir çeşit savunma engeli gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it isn't worth to keep trying.</span></span> <span data-ttu-id="a1ef7-116">Bu savunma engeli tam olarak devre kesici olur.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="a1ef7-117">Devre kesici deseninin amacı "yeniden deneme düzeniyle" farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="a1ef7-118">"Yeniden deneme biçimi", bir uygulamanın işlemin sonunda başarılı olacağı beklentide bir işlemi yeniden denemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="a1ef7-119">Devre kesici stili, bir uygulamanın başarısız olma olasılığı olan bir işlem gerçekleştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-119">The Circuit Breaker pattern prevents an application from performing an operation that's likely to fail.</span></span> <span data-ttu-id="a1ef7-120">Bir uygulama, bu iki deseni birleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-120">An application can combine these two patterns.</span></span> <span data-ttu-id="a1ef7-121">Ancak, yeniden deneme mantığı devre kesici tarafından döndürülen herhangi bir özel duruma duyarlıdır ve devre kesici bir hatanın geçici olmadığını gösteriyorsa yeniden deneme girişimlerini iptal etmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="a1ef7-122">HttpClientFactory ve Polly ile devre kesici modelini uygulayın</span><span class="sxs-lookup"><span data-stu-id="a1ef7-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="a1ef7-123">Yeniden denemeler uygularken, devre kesiciler için önerilen yaklaşım, Polly gibi kanıtlanmış .NET kitaplıklarından ve HttpClientFactory ile yerel tümleştirmeden faydalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="a1ef7-124">HttpClientFactory giden ara yazılım ardışık düzenine bir devre kesici ilkesi eklemek, HttpClientFactory kullanırken zaten sahip olduğunuz koda tek bir artımlı kod parçası eklemek kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="a1ef7-125">Burada HTTP çağrısı yeniden denemeleri için kullanılan koda yapılan tek ekleme, aşağıdaki artımlı kodda, ConfigureServices () yönteminin bir parçası olarak da gösterildiği gibi, kullanılacak ilke listesine devre kesici ilkesi eklediğiniz koddur.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="a1ef7-126">`AddPolicyHandler()` yöntemi, kullanacağınız `HttpClient` nesnelerine ilke ekler.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-126">The `AddPolicyHandler()` method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="a1ef7-127">Bu durumda, devre kesici için bir Polly ilkesi ekliyor.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-127">In this case, it's adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="a1ef7-128">Daha modüler bir yaklaşıma sahip olmak için, devre kesici Ilkesi aşağıdaki kodda gösterildiği gibi `GetCircuitBreakerPolicy()`adlı ayrı bir yöntemde tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="a1ef7-128">To have a more modular approach, the Circuit Breaker Policy is defined in a separate method called `GetCircuitBreakerPolicy()`, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="a1ef7-129">Yukarıdaki kod örneğinde, devre kesici ilkesi, http istekleri yeniden denendiğinde beş ardışık hata olduğunda devre dışı bırakıldığında veya açılacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="a1ef7-130">Bu durumda, devre 30 saniye boyunca kesilir: Bu dönemde, çağrılar aslında yerleştirilmektense devre kesici tarafından hemen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="a1ef7-131">İlke, [ilgili özel durumları ve http durum kodlarını](/aspnet/core/fundamentals/http-requests#handle-transient-faults) hata olarak otomatik olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-131">The policy automatically interprets [relevant exceptions and HTTP status codes](/aspnet/core/fundamentals/http-requests#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="a1ef7-132">Devre kesiciler, HTTP çağrısını gerçekleştiren istemci uygulama veya hizmetten farklı bir ortamda dağıtılan belirli bir kaynakta bir geri dönüş altyapısına yeniden yönlendirmek için de kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that's deployed in a different environment than the client application or service that's performing the HTTP call.</span></span> <span data-ttu-id="a1ef7-133">Bu şekilde, veri merkezinde yalnızca arka uç mikro hizmetlerinizi etkileyen ancak istemci uygulamalarınıza yönelik bir kesinti varsa, istemci uygulamalar geri dönüş hizmetlerine yeniden yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-133">That way, if there's an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="a1ef7-134">Polly, bu [Yük devretme ilkesi](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryosuna otomatik hale getirmek için yeni bir ilke planlıyor.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="a1ef7-135">Bu özelliklerin tümü, Azure tarafından sizin için otomatik olarak yönetilmek yerine, konum saydamlığı ile, yük devretmeyi .NET kodu içinden yönettiğiniz durumlar içindir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

<span data-ttu-id="a1ef7-136">Bir kullanım noktasından, HttpClient kullanılırken, önceki bölümlerde gösterildiği gibi, bu kod, HttpClientFactory ile HttpClient kullanırken olduğu gibi, burada yeni bir şey eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span>

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="a1ef7-137">EShopOnContainers 'da http yeniden denemelerini ve devre kesicileri sınama</span><span class="sxs-lookup"><span data-stu-id="a1ef7-137">Test Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="a1ef7-138">Bir Docker konağında eShopOnContainers çözümünü her başlattığınızda, birden çok kapsayıcı başlatması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="a1ef7-139">Kapsayıcıların bazıları SQL Server kapsayıcısı gibi başlangıç ve başlatma için daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="a1ef7-140">Bu özellikle, eShopOnContainers uygulamasını, görüntüleri ve veritabanını ayarlaması gerektiğinden Docker 'a ilk kez dağıttığınızda doğrudur.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-140">This is especially true the first time you deploy the eShopOnContainers application into Docker because it needs to set up the images and the database.</span></span> <span data-ttu-id="a1ef7-141">Bazı kapsayıcıların diğerlerinden daha yavaş başlaması, önceki bölümlerde açıklandığı gibi, Docker-Compose düzeyinde kapsayıcılar arasında bağımlılıklar ayarlamış olsanız bile hizmetlerin geri kalanının ilk olarak HTTP özel durumlarını oluşturmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="a1ef7-142">Kapsayıcılar arasındaki Docker-Compose bağımlılıkları yalnızca işlem düzeyindedir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="a1ef7-143">Kapsayıcının giriş noktası işlemi başlatılmış olabilir, ancak SQL Server sorgular için hazırlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="a1ef7-144">Sonuç hataların bir basamakla olabilir ve uygulama söz konusu kapsayıcıyı tüketmeye çalışırken bir özel durum alabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="a1ef7-145">Ayrıca, uygulama buluta dağıtıldığında başlangıçta bu tür bir hata görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="a1ef7-146">Bu durumda, düzenleyiciler küme düğümleri genelinde kapsayıcı sayısı dengelemesinde, kapsayıcıları bir düğümden veya VM 'den diğerine (yani yeni örnekler başlayarak) taşıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="a1ef7-147">' EShopOnContainers ' yöntemi, tüm kapsayıcıları başlatırken bu sorunları çözirken daha önce gösterilen yeniden deneme modelini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span>

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="a1ef7-148">EShopOnContainers içinde devre kesiciyi test etme</span><span class="sxs-lookup"><span data-stu-id="a1ef7-148">Test the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="a1ef7-149">Devreni bölmek/açmak ve eShopOnContainers ile test etmek için birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="a1ef7-150">Bir seçenek, devre kesici ilkesinde izin verilen yeniden deneme sayısını 1 ' e düşürmenin yanı sıra tüm çözümü Docker 'a yeniden dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="a1ef7-151">Tek bir yeniden denemeye karşı, dağıtım sırasında bir HTTP isteğinin başarısız olması, devre kesicinin açılması ve bir hata elde etmeniz iyi bir şansınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-151">With a single retry, there's a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="a1ef7-152">Diğer bir seçenek de **sepet** mikro hizmetinde uygulanan özel ara yazılım kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-152">Another option is to use custom middleware that's implemented in the **Basket** microservice.</span></span> <span data-ttu-id="a1ef7-153">Bu ara yazılım etkinleştirildiğinde tüm HTTP isteklerini yakalar ve 500 durum kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="a1ef7-154">Aşağıdaki gibi, başarısız URI 'ye bir GET isteği yaparak ara yazılımı etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1ef7-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`\
  <span data-ttu-id="a1ef7-155">Bu istek, ara yazılımın geçerli durumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="a1ef7-156">Ara yazılım etkinleştirilmişse, istek 500 durum kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="a1ef7-157">Ara yazılım devre dışıysa, yanıt verilmez.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-157">If the middleware is disabled, there's no response.</span></span>

- `GET http://localhost:5103/failing?enable`\
  <span data-ttu-id="a1ef7-158">Bu istek, ara yazılımı sunar.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-158">This request enables the middleware.</span></span>

- `GET http://localhost:5103/failing?disable`\
  <span data-ttu-id="a1ef7-159">Bu istek, ara yazılımı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-159">This request disables the middleware.</span></span>

<span data-ttu-id="a1ef7-160">Örneğin, uygulama çalışmaya başladıktan sonra herhangi bir tarayıcıda aşağıdaki URI 'yi kullanarak bir istek yaparak ara yazılımı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="a1ef7-161">Sıralama mikro hizmeti 'nin 5103 numaralı bağlantı noktasını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable`

<span data-ttu-id="a1ef7-162">Ardından, Şekil 8-5 ' de gösterildiği gibi, URI `http://localhost:5103/failing`kullanarak durumu kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-162">You can then check the status using the URI `http://localhost:5103/failing`, as shown in Figure 8-5.</span></span>

![Başarısız olan ara yazılım simülasyonu durumunun kontrol etme ekran görüntüsü.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

<span data-ttu-id="a1ef7-164">**Şekil 8-5**.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-164">**Figure 8-5**.</span></span> <span data-ttu-id="a1ef7-165">"Başarısız" ASP.NET ara yazılım durumu denetleniyor ve bu durumda devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-165">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span>

<span data-ttu-id="a1ef7-166">Bu noktada sepet mikro hizmeti, çağırma her çağırdığınızda durum kodu 500 ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-166">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="a1ef7-167">Ara yazılım çalışmaya başladıktan sonra MVC web uygulamasından bir sıra yapmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-167">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="a1ef7-168">İstekler başarısız olduğundan, devre açılır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-168">Because the requests fail, the circuit will open.</span></span>

<span data-ttu-id="a1ef7-169">Aşağıdaki örnekte, MVC web uygulamasının bir siparişi yerleştirmek için mantığdaki bir catch bloğuna sahip olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-169">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="a1ef7-170">Kod bir açık devre özel durumu yakalarsa, kullanıcıya beklemesini isteyen kolay bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-170">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            var user = _appUserParser.Parse(HttpContext.User);
            //Http requests using the Typed Client (Service Agent)
            var vm = await _basketSvc.GetBasket(user);
            return View(vm);
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

<span data-ttu-id="a1ef7-171">İşte bir Özet.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-171">Here’s a summary.</span></span> <span data-ttu-id="a1ef7-172">Yeniden deneme ilkesi, HTTP isteğini yapmak ve HTTP hatalarını almak için birkaç kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-172">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="a1ef7-173">Yeniden deneme sayısı, devre kesici ilkesi için ayarlanan en büyük sayıya ulaştığında (Bu durumda, 5), uygulama bir Brokencırcuitexception oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-173">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="a1ef7-174">Şekil 8-6 ' de gösterildiği gibi, sonuç kolay bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-174">The result is a friendly message, as shown in Figure 8-6.</span></span>

![Sepet hizmeti hata ile MVC web uygulamasının ekran görüntüsü.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

<span data-ttu-id="a1ef7-176">**Şekil 8-6**.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-176">**Figure 8-6**.</span></span> <span data-ttu-id="a1ef7-177">Devre kesici Kullanıcı arabirimine hata döndürüyor</span><span class="sxs-lookup"><span data-stu-id="a1ef7-177">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="a1ef7-178">Devre için ne zaman açılacağı/kesilecek farklı Logic uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-178">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="a1ef7-179">Ya da bir geri dönüş veri merkezi veya yedek bir arka uç sistemi varsa, farklı bir arka uç mikro hizmetine karşı HTTP isteği de deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-179">Or you can try an HTTP request against a different back-end microservice if there's a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="a1ef7-180">Son olarak, `CircuitBreakerPolicy` başka bir olasılık `Isolate` (açık ve ayrı tutmaya zorlar devre dışı bırakmak) ve `Reset` (yeniden kapatan) kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-180">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="a1ef7-181">Bunlar, ilke üzerinde doğrudan ayırma ve sıfırlama sağlayan bir yardımcı program HTTP uç noktası oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-181">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="a1ef7-182">Bu tür bir HTTP uç noktası Ayrıca, bir aşağı akış sistemini geçici olarak yalıtmak için üretimde uygun şekilde, örneğin, yükseltmek istediğiniz zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-182">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="a1ef7-183">Ya da bir aşağı akış sisteminin hatalı olması şüpheli bir aşağı akış sistemini korumak için devreyi el ile gezti.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-183">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a1ef7-184">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a1ef7-184">Additional resources</span></span>

- <span data-ttu-id="a1ef7-185">**Devre kesici deseninin**</span><span class="sxs-lookup"><span data-stu-id="a1ef7-185">**Circuit Breaker pattern**</span></span>\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
><span data-ttu-id="a1ef7-186">[Önceki](implement-http-call-retries-exponential-backoff-polly.md)
>[İleri](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="a1ef7-186">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
