---
title: Devre kesici desenini uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Http yeniden tamamlayıcı bir sisteme olarak devre kesici desenini uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 8cd3564e5240ec5a8783edb336957549be27ea6a
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479643"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="5b440-103">Devre kesici desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="5b440-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="5b440-104">Daha önce belirtildiği gibi bir uzak hizmete veya kaynağa bağlanmaya çalıştığınızda oluşabilir gibi kurtarmak için değişken bir süre gereken değişiklik gösterebileceği hataları işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="5b440-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="5b440-105">Bu tür bir hata işleme kararlılığını ve dayanıklılığını uygulamanın artırabilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="5b440-106">Dağıtılmış bir ortamda uzak kaynak ve hizmetlere çağrılar yavaş ağ bağlantıları ve zaman aşımları, gibi geçici hatalardan dolayı başarısız olabilir veya kaynaklar yavaş yanıt vermiyor veya geçici olarak kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5b440-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="5b440-107">Kısa bir süre sonra kendilerini genellikle bu hataları düzeltin ve sağlam bir bulut uygulaması "yeniden deneme düzenini" gibi bir strateji kullanarak işlemek için hazırlıklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b440-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span> 

<span data-ttu-id="5b440-108">Ancak, olabilir hataları düzeltmek çok daha uzun sürebilir, beklenmedik olaylardan kaynaklanır olduğu durumlar.</span><span class="sxs-lookup"><span data-stu-id="5b440-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="5b440-109">Bu hataların önem derecesi kısmi bağlantı kaybı gelen bir hizmetin tamamen çökmesi arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="5b440-110">Bu durumda, bir uygulama başarılı olma ihtimali düşük bir işlemi sürekli yeniden denemesi anlamsız olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> 

<span data-ttu-id="5b440-111">Bunun yerine uygulama işlemin başarısız olduğunu kabul edin ve hatayı uygun şekilde işlemek için kodlanmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b440-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="5b440-112">HTTP yeniden carelessly kullanarak neden olabilir bir hizmet reddi oluşturmak ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) saldırı kendi yazılımınızı içinde.</span><span class="sxs-lookup"><span data-stu-id="5b440-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="5b440-113">Bir mikro hizmet başarısız olursa veya yavaş çalışıyor gibi birden çok istemci art arda başarısız istekleri yeniden deneme.</span><span class="sxs-lookup"><span data-stu-id="5b440-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="5b440-114">Başarısız olan hizmetine yönelik trafiği katlanarak artan tehlikeli riski oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b440-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="5b440-115">Bu nedenle, çalışırken değer tutma olmadığında aşırı isteklerini durdurmak için savunma engel tür gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b440-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it is not worth keeping trying.</span></span> <span data-ttu-id="5b440-116">Kesin olarak devre kesici, savunma engel olur.</span><span class="sxs-lookup"><span data-stu-id="5b440-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="5b440-117">Devre kesici düzeni, "yeniden deneme düzenini" farklı bir amaca sahip.</span><span class="sxs-lookup"><span data-stu-id="5b440-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="5b440-118">"Yeniden deneme düzenini" bir işlem sonunda başarılı beklentisi işleminde yeniden denemek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b440-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="5b440-119">Devre kesici düzeni uygulamanın başarısız olma olasılığı yüksek bir işlemi gerçekleştirilirken engeller.</span><span class="sxs-lookup"><span data-stu-id="5b440-119">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="5b440-120">Bir uygulama, bu iki Düzen birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b440-120">An application can combine these two patterns.</span></span> <span data-ttu-id="5b440-121">Ancak, yeniden deneme mantığının devre kesici tarafından döndürülen herhangi bir özel durum duyarlı olması gerekir ve devre kesici bir hataya geçici olmadığını gösteriyorsa, yeniden denemeyi bırakması.</span><span class="sxs-lookup"><span data-stu-id="5b440-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="5b440-122">HttpClientFactory ve Polly devre kesici desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="5b440-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="5b440-123">Yeniden denemeler yaparken, devre Kesiciler önerilen yaklaşım Polly ve yerel tümleştirmesi sayesinde HttpClientFactory gibi kendini kanıtlamış .NET kitaplıkları yararlanmak için olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="5b440-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="5b440-124">Bir devre kesici İlkesi, HttpClientFactory ekleme giden ara yazılım ardışık düzenini HttpClientFactory kullanırken olduğunuz için artımlı tek kod parçasını eklemek kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="5b440-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="5b440-125">Yalnızca Burada HTTP çağrı yeniden için kullanılan kod için kod devre kesici İlkesi kullanmak için ilkeleri listesine aşağıdaki artımlı kodda ConfigureServices() yöntemi parçası gösterildiği eklediğiniz ektir.</span><span class="sxs-lookup"><span data-stu-id="5b440-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="5b440-126">`AddPolicyHandler()`Yöntemdir hangi ilkeleri kullanacağınız HttpClient nesneleri ekler.</span><span class="sxs-lookup"><span data-stu-id="5b440-126">The `AddPolicyHandler()`method is what adds policies to the HttpClient objects you will use.</span></span> <span data-ttu-id="5b440-127">Bu durumda, devre kesici Polly ilke eklemektir.</span><span class="sxs-lookup"><span data-stu-id="5b440-127">In this case, it is adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="5b440-128">Daha modüler bir yaklaşım sahip olmak için aşağıdaki kod olarak GetCircuitBreakerPolicy() adlı ayrı bir yöntem devre kesici İlkesi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5b440-128">In order to have a more modular approach, the Circuit Breaker Policy is defined in a separate method named GetCircuitBreakerPolicy(), as the following code.</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="5b440-129">Yukarıdaki kod örneğinde, keser veya olduğunda beş art arda hatalar Http isteklerini kurulmaya çalışılırken bağlantı hattını açılır devre kesici İlkesi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5b440-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="5b440-130">Bu durum oluştuğunda, bağlantı hattı için 30 saniye çalışmamasına neden olur: Bu dönemde çağrıları devre kesici tarafından hemen başarısız yerine gerçekten yerleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="5b440-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="5b440-131">İlke otomatik olarak yorumlar [ilgili özel durumları ve HTTP durum kodları](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) hataları olarak.</span><span class="sxs-lookup"><span data-stu-id="5b440-131">The policy automatically interprets [relevant exceptions and HTTP status codes](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="5b440-132">Devre Kesiciler, istekleri, bir istemci uygulamadan daha farklı bir ortamda dağıtılan belirli bir kaynağa veya HTTP çağrısı gerçekleştiriyor hizmet sorunları varsa, bir geri dönüş altyapısını yeniden yönlendirmek için de kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b440-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="5b440-133">Bu şekilde, yalnızca arka uç mikro hizmetlerin ancak, istemci uygulamaları etkileyen veri merkezinde bir kesinti oluşursa istemci uygulamaları için geri dönüş Hizmetleri yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b440-133">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="5b440-134">Polly bu otomatik hale getirmek için yeni bir ilke planlama [yük devretme İlkesi](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) senaryo.</span><span class="sxs-lookup"><span data-stu-id="5b440-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span> 

<span data-ttu-id="5b440-135">Tüm durumlarda nereye yük aksine, sizin için konum saydamlığı olan Azure tarafından otomatik olarak yönetilen sahip .NET kod içinde yönetiyor olsanız özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="5b440-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span> 

<span data-ttu-id="5b440-136">Bir kullanım HttpClient kullanırken açısından, önceki bölümlerde gösterildiği gibi kod HttpClient HttpClientFactory ile kullanırken daha aynı olduğu için yeni bir şey burada eklemenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="5b440-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span> 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="5b440-137">Test Http yeniden ve hizmetine devre Kesiciler</span><span class="sxs-lookup"><span data-stu-id="5b440-137">Testing Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="5b440-138">Bir Docker konağı hizmetine çözüm başlattığınızda, birden çok kapsayıcı başlatmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b440-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="5b440-139">Bazı kapsayıcıları başlatmak ve, gibi SQL sunucu kapsayıcısı başlatmak daha yavaş.</span><span class="sxs-lookup"><span data-stu-id="5b440-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="5b440-140">Görüntüleri ve veritabanını ayarlamak gerektiğinden bu Docker'ı hizmetine uygulamasına dağıtmak ilk kez özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="5b440-140">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="5b440-141">Bazı kapsayıcıları kapsayıcılar arasındaki bağımlılıkları ayarlasanız bile diğerleri rest Hizmetleri HTTP özel durumlar, başlangıçta throw çıkabilir daha yavaş Başlat olgu önceki bölümlerde açıklandığı gibi düzeyi docker-compose.</span><span class="sxs-lookup"><span data-stu-id="5b440-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="5b440-142">Bu docker kapsayıcılar arasındaki bağımlılıkları compose olan işlem düzeyinde yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5b440-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="5b440-143">Kapsayıcının giriş noktası işlemi başlatıldı, ancak SQL Server sorguları için hazır olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="5b440-144">Sonucu bir art arda hatalar olabilir ve uygulamanın, bu belirli bir kapsayıcıda tüketmeye çalışırken bir özel durum elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b440-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span> 

<span data-ttu-id="5b440-145">Buluta Uygulama dağıtırken, bu tür başlangıçta görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b440-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="5b440-146">Bu durumda, Düzenleyicileri kapsayıcıları bir düğüm veya VM (yani yeni örnekleri başlatılıyor) diğerine taşıma, kapsayıcı sayısı küme düğümleri arasında dengeleme.</span><span class="sxs-lookup"><span data-stu-id="5b440-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="5b440-147">Tüm kapsayıcıları başlatılıyor daha önce gösterilen yeniden deneme düzenini kullanarak olduğunda 'hizmetine' yolu bu sorunları çözer.</span><span class="sxs-lookup"><span data-stu-id="5b440-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span> 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="5b440-148">Devre kesici hizmetine test etme</span><span class="sxs-lookup"><span data-stu-id="5b440-148">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="5b440-149">Bağlantı hattı kesme/açık ve onu hizmetine ile test edebilirsiniz birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="5b440-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="5b440-150">Bir seçenek olduğu için izin verilen yeniden deneme sayısı 1 devre kesici ilkesinde düşürün ve çözümün tamamının Docker yeniden dağıtın.</span><span class="sxs-lookup"><span data-stu-id="5b440-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="5b440-151">Tek bir yeniden deneme ile dağıtım sırasında bir HTTP isteği başarısız olur şansı yoktur, devre kesici açılır ve bir hata alıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="5b440-151">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="5b440-152">Başka bir seçenek, sepet mikro hizmet içinde uygulanan özel bir ara yazılım kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="5b440-152">Another option is to use custom middleware that is implemented in the Basket microservice.</span></span> <span data-ttu-id="5b440-153">Bu ara yazılım etkinleştirildiğinde, tüm HTTP isteklerini yakalar ve 500 durum kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b440-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="5b440-154">Ara yazılım için başarısız olan bir GET isteği yaparak etkinleştirebilirsiniz aşağıdaki gibi bir URI'si:</span><span class="sxs-lookup"><span data-stu-id="5b440-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`

<span data-ttu-id="5b440-155">Bu istek, ara yazılımın geçerli durumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b440-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="5b440-156">Ara yazılım etkinleştirilirse, istek 500 durum kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b440-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="5b440-157">Ara yazılım devre dışıysa, yanıt yok.</span><span class="sxs-lookup"><span data-stu-id="5b440-157">If the middleware is disabled, there is no response.</span></span> 

- `GET http://localhost:5103/failing?enable`

<span data-ttu-id="5b440-158">Bu istek, ara yazılım sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b440-158">This request enables the middleware.</span></span> 

- `GET http://localhost:5103/failing?disable`

<span data-ttu-id="5b440-159">Bu istek Ara devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5b440-159">This request disables the middleware.</span></span> 

<span data-ttu-id="5b440-160">Örneğin, uygulama çalışmaya başladıktan sonra herhangi bir tarayıcıda aşağıdaki URI kullanılarak bir isteği yaparak ara yazılım etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b440-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="5b440-161">Sıralama mikro hizmet bağlantı noktası 5103 oluşturun kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5b440-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable` 

<span data-ttu-id="5b440-162">Daha sonra URI'yi kullanarak durumu denetleyebilirsiniz http://localhost:5103/failingŞekil 10-4'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5b440-162">You can then check the status using the URI http://localhost:5103/failing, as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="5b440-163">**Şekil 10-4**.</span><span class="sxs-lookup"><span data-stu-id="5b440-163">**Figure 10-4**.</span></span> <span data-ttu-id="5b440-164">"Başarısız" durumu denetimi devre dışı ASP.NET ara yazılım – bu durumda.</span><span class="sxs-lookup"><span data-stu-id="5b440-164">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="5b440-165">Bu noktada, sepet mikro hizmet yanıt durum koduyla çağırmanızı her 500 onu çağırır.</span><span class="sxs-lookup"><span data-stu-id="5b440-165">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="5b440-166">Ara yazılım çalıştırıldıktan sonra MVC web uygulamasında bir sipariş oluşturmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b440-166">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="5b440-167">İstekleri başarısız olduğundan, bağlantı hattının açılır.</span><span class="sxs-lookup"><span data-stu-id="5b440-167">Because the requests fail, the circuit will open.</span></span> 

<span data-ttu-id="5b440-168">Aşağıdaki örnekte, MVC web uygulaması bir catch olduğunu görebilir sipariş verme mantığı açma işlemini engelleyin.</span><span class="sxs-lookup"><span data-stu-id="5b440-168">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="5b440-169">Kod devre açın istisna yakalarsa kullanıcı beklenecek bildiren kolay bir ileti gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-169">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="5b440-170">Bir özeti aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b440-170">Here’s a summary.</span></span> <span data-ttu-id="5b440-171">Yeniden deneme ilkesi, HTTP hataları alır ve HTTP isteği yapmak için birkaç kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="5b440-171">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="5b440-172">Yeniden deneme sayısı (Bu durumda, 5) devre kesici ilkesi için en fazla sayı kümesini eriştiğinde, uygulamanın bir BrokenCircuitException oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b440-172">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="5b440-173">Kolay bir ileti Şekil 10-5'te gösterildiği gibi sonucudur.</span><span class="sxs-lookup"><span data-stu-id="5b440-173">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="5b440-174">**Şekil 10-5**.</span><span class="sxs-lookup"><span data-stu-id="5b440-174">**Figure 10-5**.</span></span> <span data-ttu-id="5b440-175">Devre kesici kullanıcı Arabirimi için bir hata döndürüyor</span><span class="sxs-lookup"><span data-stu-id="5b440-175">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="5b440-176">Ne zaman açık/bağlantı hattı kesme farklı mantığı uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-176">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="5b440-177">Ya da geri dönüş datacenter veya yedekli arka uç sistemine ise farklı bir arka uç mikro hizmet karşı HTTP isteği deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b440-177">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span> 

<span data-ttu-id="5b440-178">Son olarak, başka bir olasılık için `CircuitBreakerPolicy` kullanmaktır `Isolate` (açık zorlar ve bağlantı hattı açık tutar) ve `Reset` (hangi kapatır, yeniden).</span><span class="sxs-lookup"><span data-stu-id="5b440-178">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="5b440-179">Bu ilkenin üzerine ayırma ve sıfırlama doğrudan çağıran bir yardımcı programı HTTP uç noktası oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-179">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="5b440-180">Bu tür, bir HTTP uç nokta da, uygun şekilde, geçici olarak yükseltmek istediğinizde gibi bir aşağı akış sistem yalıtmak için üretim ortamında güvenli kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b440-180">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="5b440-181">Veya bir aşağı akış sistem hatalı olması şüphelendiğiniz el ile korunacak bağlantı hattını geçirmek.</span><span class="sxs-lookup"><span data-stu-id="5b440-181">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>


## <a name="additional-resources"></a><span data-ttu-id="5b440-182">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5b440-182">Additional resources</span></span>


-   <span data-ttu-id="5b440-183">**Devre kesici düzeni**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="5b440-183">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5b440-184">[Önceki](implement-http-call-retries-exponential-backoff-polly.md)
[İleri](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="5b440-184">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
