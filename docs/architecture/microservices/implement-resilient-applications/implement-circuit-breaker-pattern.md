---
title: Devre Kesici desenini uygulama
description: Http yeniden denemelerine tamamlayıcı bir sistem olarak Devre Kesici deseni nasıl uygulayacağınızı öğrenin.
ms.date: 03/03/2020
ms.openlocfilehash: bebe0b4a622db928175f78f8d3e303d3d7adf170
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988891"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="6e2ef-103">Devre Kesici desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="6e2ef-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="6e2ef-104">Daha önce de belirtildiği gibi, uzak bir hizmete veya kaynağa bağlanmaya çalıştığınızda olabileceği gibi, kurtarması değişken miktarda zaman alabilecek hataları işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="6e2ef-105">Bu tür bir hatanın işlenmesi, bir uygulamanın kararlılığını ve esnekliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="6e2ef-106">Dağıtılmış bir ortamda, uzak kaynaklara ve hizmetlere yapılan çağrılar, yavaş ağ bağlantıları ve zaman zaman ekmeleri gibi geçici hatalar veya kaynakların yavaş yanıt verdiği veya geçici olarak kullanılamaması nedeniyle başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="6e2ef-107">Bu hatalar genellikle kısa bir süre sonra kendilerini düzeltir ve "Yeniden Deneme deseni" gibi bir strateji kullanarak bunları işlemek için sağlam bir bulut uygulaması hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span>

<span data-ttu-id="6e2ef-108">Ancak, hataların düzeltilmesi çok daha uzun sürebilecek beklenmeyen olaylardan kaynaklandığı durumlar da olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="6e2ef-109">Bu hataların önem derecesi kısmi bağlantı kaybıyla bir hizmetin tamamen çökmesi arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="6e2ef-110">Bu gibi durumlarda, bir uygulamanın sürekli olarak başarılı olması beklenmeyen bir işlemi yeniden denemesi anlamsız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-110">In these situations, it might be pointless for an application to continually retry an operation that's unlikely to succeed.</span></span>

<span data-ttu-id="6e2ef-111">Bunun yerine, uygulama işlemin başarısız olduğunu kabul etmek ve buna göre başarısızlığı işlemek için kodlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="6e2ef-112">Http yeniden denemelerini dikkatsizce kullanmak, kendi yazılımınızda Bir Hizmet Reddi[(DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)saldırısı oluşturmaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="6e2ef-113">Bir microservice başarısız olduğunda veya yavaş yavaş performans gösterdiğinde, birden çok istemci başarısız istekleri tekrar tekrar yeniden deneebilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="6e2ef-114">Bu, başarısız hizmeti hedefleyen trafiği katlanarak artırma konusunda tehlikeli bir risk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="6e2ef-115">Bu nedenle, aşırı istekleri denemeye devam etmeye değer olmadığında durdurmak böylece savunma bariyeri çeşit gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it isn't worth to keep trying.</span></span> <span data-ttu-id="6e2ef-116">Bu savunma bariyeri tam olarak devre kesici.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="6e2ef-117">Devre Kesici deseni "Retry deseni"nden farklı bir amaca sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="6e2ef-118">"Yeniden Deneme deseni", bir uygulamanın, işlemin sonunda başarılı olacağı beklentisiyle bir işlemi yeniden denemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="6e2ef-119">Devre Kesici deseni, bir uygulamanın başarısız olma olasılığı olan bir işlemi gerçekleştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-119">The Circuit Breaker pattern prevents an application from performing an operation that's likely to fail.</span></span> <span data-ttu-id="6e2ef-120">Bir uygulama bu iki desen birleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-120">An application can combine these two patterns.</span></span> <span data-ttu-id="6e2ef-121">Ancak, yeniden deneme mantığı devre kesici tarafından döndürülen herhangi bir özel durum duyarlı olmalı ve devre kesici bir hata geçici olmadığını gösterirse yeniden deneme girişimleri terk etmelidir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a><span data-ttu-id="6e2ef-122">Ve Polly `IHttpClientFactory` ile Devre Kesici deseni uygulayın</span><span class="sxs-lookup"><span data-stu-id="6e2ef-122">Implement Circuit Breaker pattern with `IHttpClientFactory` and Polly</span></span>

<span data-ttu-id="6e2ef-123">Yeniden denemeler icra ederken olduğu gibi, devre kesiciler için önerilen yaklaşım Polly ve onun `IHttpClientFactory`yerel entegrasyonu gibi kanıtlanmış .NET kitaplıklarından yararlanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with `IHttpClientFactory`.</span></span>

<span data-ttu-id="6e2ef-124">Giden ara yazılım ardışık alan içine `IHttpClientFactory` bir devre kesici ilkesi eklemek, kullanırken `IHttpClientFactory`zaten sahip olduğunuz kodlara tek bir artımlı kod eklemek kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-124">Adding a circuit breaker policy into your `IHttpClientFactory` outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using `IHttpClientFactory`.</span></span>

<span data-ttu-id="6e2ef-125">HTTP çağrı yeniden denemeleri için kullanılan koda burada eklenen tek ek, ConfigureServices() yönteminin bir parçası olan aşağıdaki artımlı kodda gösterildiği gibi, Devre Kesici ilkesini kullanılacak ilkeler listesine eklediğiniz koddur.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="6e2ef-126">Yöntem, `AddPolicyHandler()` kullanacağınız `HttpClient` nesnelere ilkeler ekleyen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-126">The `AddPolicyHandler()` method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="6e2ef-127">Bu durumda, bir devre kesici için Polly politikası ekliyor.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-127">In this case, it's adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="6e2ef-128">Daha modüler bir yaklaşıma sahip olmak için, Devre `GetCircuitBreakerPolicy()`Kesici Politikası aşağıdaki kodda gösterildiği gibi ayrı bir yöntemle tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="6e2ef-128">To have a more modular approach, the Circuit Breaker Policy is defined in a separate method called `GetCircuitBreakerPolicy()`, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="6e2ef-129">Yukarıdaki kod örneğinde, devre kesici ilkesi, Http isteklerini yeniden denerken ardışık beş hata olduğunda devreyi kıracak veya açar şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="6e2ef-130">Bu durumda, devre 30 saniye boyunca kırılır: bu dönemde, aramalar aslında yerine devre kesici tarafından hemen başarısız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="6e2ef-131">İlke, ilgili [özel durumları ve HTTP durum kodlarını](/aspnet/core/fundamentals/http-requests#handle-transient-faults) otomatik olarak hata olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-131">The policy automatically interprets [relevant exceptions and HTTP status codes](/aspnet/core/fundamentals/http-requests#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="6e2ef-132">Devre kesiciler, http çağrısını gerçekleştiren istemci uygulamasından veya hizmetten farklı bir ortamda dağıtılan belirli bir kaynakta sorunlar varsa, istekleri geri dönüş altyapısına yönlendirmek için de kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that's deployed in a different environment than the client application or service that's performing the HTTP call.</span></span> <span data-ttu-id="6e2ef-133">Bu şekilde, veri merkezinde yalnızca arka uç mikro hizmetlerinizi etkileyen ancak istemci uygulamalarınızı etkilemeyen bir kesinti olursa, istemci uygulamaları geri dönüş hizmetlerine yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-133">That way, if there's an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="6e2ef-134">Polly bu [başarısız ilke](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryosuotomatikleştirmek için yeni bir ilke planlıyor.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="6e2ef-135">Tüm bu özellikler, yer saydamlığıyla azure tarafından sizin için otomatik olarak yönetilmesinin aksine, .NET kodu içinden başarısızlığı yönettiğiniz durumlar içindir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

<span data-ttu-id="6e2ef-136">Kullanım açısından bakıldığında, HttpClient'ı kullanırken, kod önceki bölümlerde gösterildiği `HttpClient` `IHttpClientFactory`gibi, kod ile aynı olduğundan buraya yeni bir şey eklemenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using `HttpClient` with `IHttpClientFactory`, as shown in previous sections.</span></span>

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="6e2ef-137">Test Http retries ve devre kesiciler eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="6e2ef-137">Test Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="6e2ef-138">Bir Docker ana bilgisayarda eShopOnContainers çözüm başlattığınızda, birden fazla kapsayıcı başlatmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="6e2ef-139">Bazı kapsayıcılar, SQL Server kapsayıcısı gibi başlatmak ve başlatmak için daha yavaş.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="6e2ef-140">Bu özellikle görüntüleri ve veritabanıkurmak için gereken çünkü Docker içine eShopOnContainers uygulaması dağıtmak ilk kez doğrudur.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-140">This is especially true the first time you deploy the eShopOnContainers application into Docker because it needs to set up the images and the database.</span></span> <span data-ttu-id="6e2ef-141">Bazı kapsayıcıların diğerlerinden daha yavaş başlaması, önceki bölümlerde açıklandığı gibi, konteynerler arasındaki bağımlılıkları docker-comoluşturma düzeyinde ayarlasanız bile, hizmetlerin geri kalanının başlangıçta HTTP özel durumları oluşturmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="6e2ef-142">Kapsayıcılar arasındaki docker-com-com-bağımlılıkları sadece işlem düzeyindedir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="6e2ef-143">Kapsayıcının giriş noktası işlemi başlatılabilir, ancak SQL Server sorgular için hazır olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-143">The container's entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="6e2ef-144">Sonuç, bir hata basamaklı olabilir ve uygulama, belirli bir kapsayıcıyı tüketmeye çalışırken bir özel durum alabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="6e2ef-145">Uygulama buluta dağıtılırken başlangıçta de bu tür bir hata görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="6e2ef-146">Bu durumda, orkestratörler kümenin düğümleri üzerinde kapsayıcı sayısını dengeleme yaparken bir düğüm veya VM'den diğerine (diğer bir deyişle yeni örnekler başlatArak) kapsayıcıları taşıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster's nodes.</span></span>

<span data-ttu-id="6e2ef-147">'eShopOnContainers' tüm kapsayıcılar başlatırken bu sorunları çözer yolu daha önce gösterildiği Retry desen kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span>

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="6e2ef-148">eShopOnContainers devre kesici test</span><span class="sxs-lookup"><span data-stu-id="6e2ef-148">Test the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="6e2ef-149">Devreyi kırmanın/açmanın ve eShopOnContainers ile test etmenin birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="6e2ef-150">Bir seçenek, devre kesici ilkesinde izin verilen yeniden deneme sayısını 1'e düşürmek ve tüm çözümü Docker'a yeniden dağıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="6e2ef-151">Tek bir yeniden denemede, bir HTTP isteğinin dağıtım sırasında başarısız olma olasılığı yüksektir, devre kesici açılır ve bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-151">With a single retry, there's a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="6e2ef-152">Başka bir seçenek **Sepet** microservice uygulanan özel ara yazılım kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-152">Another option is to use custom middleware that's implemented in the **Basket** microservice.</span></span> <span data-ttu-id="6e2ef-153">Bu ara yazılım etkinleştirildiğinde, tüm HTTP isteklerini yakalar ve durum kodu 500 döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="6e2ef-154">Aşağıdaki gibi başarısız URI'ye GET isteğinde bulunarak ara yazılımı etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6e2ef-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`\
  <span data-ttu-id="6e2ef-155">Bu istek, ara yazılımın geçerli durumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="6e2ef-156">Ara yazılım etkinse, istek iade durum kodu 500.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="6e2ef-157">Ara yazılım devre dışı bırakılırsa, yanıt yoktur.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-157">If the middleware is disabled, there's no response.</span></span>

- `GET http://localhost:5103/failing?enable`\
  <span data-ttu-id="6e2ef-158">Bu istek ara yazılımı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-158">This request enables the middleware.</span></span>

- `GET http://localhost:5103/failing?disable`\
  <span data-ttu-id="6e2ef-159">Bu istek ara yazılımı devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-159">This request disables the middleware.</span></span>

<span data-ttu-id="6e2ef-160">Örneğin, uygulama çalışmaya başladığında, herhangi bir tarayıcıda aşağıdaki URI'yi kullanarak istekte bulunarak ara yazılımı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="6e2ef-161">Sipariş microservice port 5103 kullanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable`

<span data-ttu-id="6e2ef-162">Daha sonra Şekil 8-5'te gösterildiği gibi URI'yi `http://localhost:5103/failing`kullanarak durumu kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-162">You can then check the status using the URI `http://localhost:5103/failing`, as shown in Figure 8-5.</span></span>

![Başarısız ara yazılım simülasyonunun durumunun kontrol edilmesi ekran görüntüsü.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

<span data-ttu-id="6e2ef-164">**Şekil 8-5**.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-164">**Figure 8-5**.</span></span> <span data-ttu-id="6e2ef-165">"Failing" ASP.NET aracının durumunu kontrol etmek – Bu durumda devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-165">Checking the state of the "Failing" ASP.NET middleware – In this case, disabled.</span></span>

<span data-ttu-id="6e2ef-166">Bu noktada, Sepet microservice çağrı her çağrıda durum kodu 500 ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-166">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="6e2ef-167">Ara yazılım lar çalışmaya başladığında, MVC web uygulamasından sipariş yapmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-167">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="6e2ef-168">İstekler başarısız olduğu için devre açılır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-168">Because the requests fail, the circuit will open.</span></span>

<span data-ttu-id="6e2ef-169">Aşağıdaki örnekte, MVC web uygulamasının sipariş vermek için mantıkta bir catch bloğu olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-169">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="6e2ef-170">Kod açık devre özel durum yakalarsa, kullanıcıya beklemelerini söyleyen bir ileti gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-170">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="6e2ef-171">İşte özeti.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-171">Here's a summary.</span></span> <span data-ttu-id="6e2ef-172">Yeniden Deneme ilkesi, HTTP isteğini gerçekleştirmek için birkaç kez çalışır ve HTTP hatalarını alır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-172">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="6e2ef-173">Yeniden deneme sayısı Devre Kesici ilkesi için belirlenen maksimum sayıya ulaştığında (bu durumda, 5), uygulama bir BrokenCircuitException atar.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-173">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="6e2ef-174">Sonuç, Şekil 8-6'da gösterildiği gibi dostça bir mesajdır.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-174">The result is a friendly message, as shown in Figure 8-6.</span></span>

![Sepet hizmeti inoperative hata ile MVC web uygulaması ekran görüntüsü.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

<span data-ttu-id="6e2ef-176">**Şekil 8-6**.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-176">**Figure 8-6**.</span></span> <span data-ttu-id="6e2ef-177">Devre kesici UI'ye hata döndürür</span><span class="sxs-lookup"><span data-stu-id="6e2ef-177">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="6e2ef-178">Devreyi ne zaman açacağınız/kıracağınız için farklı mantık uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-178">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="6e2ef-179">Ya da bir geri dönüş veri merkezi veya gereksiz arka uç sistemi varsa farklı bir arka uç microservice karşı bir HTTP isteği deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-179">Or you can try an HTTP request against a different back-end microservice if there's a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="6e2ef-180">Son olarak, başka `CircuitBreakerPolicy` bir `Isolate` olasılık kullanmaktır (hangi kuvvetler açık `Reset` ve açık devre tutar) ve (tekrar kapatır).</span><span class="sxs-lookup"><span data-stu-id="6e2ef-180">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="6e2ef-181">Bunlar, doğrudan ilke üzerinde Yalıtma ve Sıfırlama çağıran bir yardımcı program HTTP bitiş noktası oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-181">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="6e2ef-182">Böyle bir HTTP bitiş noktası, yükseltme yapmak istediğinizde olduğu gibi, bir akış aşağı sistemi geçici olarak yalıtmak için üretimde de kullanılabilir, uygun şekilde güvenli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-182">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="6e2ef-183">Ya da hatalı olduğundan şüphelendiğiniz bir aşağı sistemi korumak için devreyi manuel olarak titretebilir.</span><span class="sxs-lookup"><span data-stu-id="6e2ef-183">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6e2ef-184">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6e2ef-184">Additional resources</span></span>

- <span data-ttu-id="6e2ef-185">**Devre Kesici deseni**</span><span class="sxs-lookup"><span data-stu-id="6e2ef-185">**Circuit Breaker pattern**</span></span>\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
><span data-ttu-id="6e2ef-186">[Önceki](implement-http-call-retries-exponential-backoff-polly.md)
>[Sonraki](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="6e2ef-186">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
