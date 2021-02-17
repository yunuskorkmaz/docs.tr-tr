---
title: Davpr hizmeti çağırma yapı taşı
description: Hizmet çağırma oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: amolenk
ms.date: 02/07/2021
ms.openlocfilehash: 1b31496bc40aebeb24716da519ed25d660242035
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639269"
---
# <a name="the-dapr-service-invocation-building-block"></a><span data-ttu-id="fc834-103">Davpr hizmeti çağırma yapı taşı</span><span class="sxs-lookup"><span data-stu-id="fc834-103">The Dapr service invocation building block</span></span>

<span data-ttu-id="fc834-104">Dağıtılmış bir sistemde, bir hizmetin genellikle bir iş işlemini tamamlaması için birbirleriyle iletişim kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc834-104">Across a distributed system, one service often needs to communicate with another to complete a business operation.</span></span> <span data-ttu-id="fc834-105">[Davpr hizmeti çağırma yapı taşı](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/) , hizmetler arasındaki iletişimi kolaylaştırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-105">The [Dapr service invocation building block](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/) can help streamline the communication between services.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="fc834-106">Ne çözdüğü</span><span class="sxs-lookup"><span data-stu-id="fc834-106">What it solves</span></span>

<span data-ttu-id="fc834-107">Dağıtılmış bir uygulamadaki hizmetler arasında çağrı yapmak kolay görünebilir, ancak ilgili birçok zorluk vardır.</span><span class="sxs-lookup"><span data-stu-id="fc834-107">Making calls between services in a distributed application may appear easy, but there are many challenges involved.</span></span> <span data-ttu-id="fc834-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc834-108">For example:</span></span>

- <span data-ttu-id="fc834-109">Diğer hizmetlerin bulunduğu yer.</span><span class="sxs-lookup"><span data-stu-id="fc834-109">Where the other services are located.</span></span>
- <span data-ttu-id="fc834-110">Hizmet adresi verildiğinde hizmeti güvenli bir şekilde çağırma.</span><span class="sxs-lookup"><span data-stu-id="fc834-110">How to call a service securely, given the service address.</span></span>
- <span data-ttu-id="fc834-111">Kısa süreli [geçici hatalar](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) oluştuğunda yeniden denemeleri işleme.</span><span class="sxs-lookup"><span data-stu-id="fc834-111">How to handle retries when short-lived [transient errors](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) occur.</span></span>

<span data-ttu-id="fc834-112">Son olarak, dağıtılmış uygulamalar birçok farklı hizmet oluştururken, hizmet çağrı grafikleri genelinde öngörüleri yakalamak, üretim sorunlarını tanılamak için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fc834-112">Lastly, as distributed applications compose many different services, capturing insights across service call graphs are critical to diagnosing production issues.</span></span>

<span data-ttu-id="fc834-113">Hizmet çağırma oluşturma bloğu, hizmetiniz için bir [ters ara sunucu](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) olarak bir davpr sepet kullanarak bu zorlukları ele alır.</span><span class="sxs-lookup"><span data-stu-id="fc834-113">The service invocation building block addresses these challenges by using a Dapr sidecar as a [reverse proxy](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) for your service.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="fc834-114">Nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="fc834-114">How it works</span></span>

<span data-ttu-id="fc834-115">Bir örnekle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="fc834-115">Let's start with an example.</span></span> <span data-ttu-id="fc834-116">"Hizmet A" ve "hizmet B" olmak üzere iki hizmeti göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="fc834-116">Consider two services, "Service A" and "Service B".</span></span> <span data-ttu-id="fc834-117">Hizmetin `catalog/items` B hizmetinde API 'yi çağırması gerekir. A hizmeti, B hizmetine bir bağımlılık alabilir ve doğrudan buna çağrı yaparsanız, bunun yerine hizmet çağırma API 'sini Davpr sidecar üzerinde çağırır.</span><span class="sxs-lookup"><span data-stu-id="fc834-117">Service A needs to call the `catalog/items` API on Service B. While Service A could take a dependency on Service B and make a direct call to it, Service A instead invokes the service invocation API on the Dapr sidecar.</span></span> <span data-ttu-id="fc834-118">Şekil 6-1, işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc834-118">Figure 6-1 shows the operation.</span></span>

![Davpr hizmeti çağrısı nasıl yapılır?](./media/service-invocation/service-invocation-flow.png)

<span data-ttu-id="fc834-120">**Şekil 6-1**.</span><span class="sxs-lookup"><span data-stu-id="fc834-120">**Figure 6-1**.</span></span> <span data-ttu-id="fc834-121">Davpr hizmeti çağırma nasıl kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc834-121">How Dapr service invocation works.</span></span>

<span data-ttu-id="fc834-122">Önceki şekildeki adımları göz önünde bulun:</span><span class="sxs-lookup"><span data-stu-id="fc834-122">Note the steps from the previous figure:</span></span>

1. <span data-ttu-id="fc834-123">A hizmeti `catalog/items` bir araç çubuğunda hizmet ÇAĞıRMA API 'sini çağırarak, hizmet B 'deki uç noktaya bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="fc834-123">Service A makes a call to the `catalog/items` endpoint in Service B by invoking the service invocation API on the Service A sidecar.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc834-124">Sepet, B hizmetinin adresini çözümlemek için takılabilir bir ad çözümleme mekanizması kullanır. Şirket içinde barındırılan modda, Davpr bunu bulmak için [MDNs](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-124">The sidecar uses a pluggable name resolution mechanism to resolve the address of Service B. In self-hosted mode, Dapr uses [mDNS](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) to find it.</span></span> <span data-ttu-id="fc834-125">Kubernetes modunda çalışırken, Kubernetes DNS hizmeti adresi belirler.</span><span class="sxs-lookup"><span data-stu-id="fc834-125">When running in Kubernetes mode, the Kubernetes DNS service determines the address.</span></span>  

1. <span data-ttu-id="fc834-126">Bir sepet hizmeti, isteği hizmet B sepet 'e iletir.</span><span class="sxs-lookup"><span data-stu-id="fc834-126">The Service A sidecar forwards the request to the Service B sidecar.</span></span>

1. <span data-ttu-id="fc834-127">Hizmet B dışarıdan arabası gerçek `catalog/items` Isteği hizmet B API 'sine karşı yapar.</span><span class="sxs-lookup"><span data-stu-id="fc834-127">The Service B sidecar makes the actual `catalog/items` request against the Service B API.</span></span>

1. <span data-ttu-id="fc834-128">B hizmeti, isteği yürütür ve kendi arabasının geri yanıtını döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc834-128">Service B executes the request and returns a response back to its sidecar.</span></span>

1. <span data-ttu-id="fc834-129">B arabası hizmeti, yanıtı bir sepet hizmetine geri iletir.</span><span class="sxs-lookup"><span data-stu-id="fc834-129">The Service B sidecar forwards the response back to the Service A sidecar.</span></span>

1. <span data-ttu-id="fc834-130">Bir sepet hizmeti, yanıtı A hizmetine geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc834-130">The Service A sidecar returns the response back to Service A.</span></span>

<span data-ttu-id="fc834-131">Çağrılardan dolayı çağrı yaptığı için, Davpr bazı kullanışlı çapraz kesme davranışları ekleyebilir:</span><span class="sxs-lookup"><span data-stu-id="fc834-131">Because the calls flow through sidecars, Dapr can inject some useful cross-cutting behaviors:</span></span>

- <span data-ttu-id="fc834-132">Hata sonrasında çağrıları otomatik olarak yeniden dene.</span><span class="sxs-lookup"><span data-stu-id="fc834-132">Automatically retry calls upon failure.</span></span>
- <span data-ttu-id="fc834-133">Otomatik Sertifika geçişi de dahil olmak üzere karşılıklı (mTLS) kimlik doğrulamasıyla hizmetler arasında çağrılar yapın.</span><span class="sxs-lookup"><span data-stu-id="fc834-133">Make calls between services secure with mutual (mTLS) authentication, including automatic certificate rollover.</span></span>
- <span data-ttu-id="fc834-134">Hangi işlemler istemcilerinin erişim denetim ilkelerini kullanarak yapabileceğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fc834-134">Control what operations clients can do using access control policies.</span></span>
- <span data-ttu-id="fc834-135">Öngörüler ve Tanılamalar sağlamak için hizmetler arasındaki tüm çağrılar için izlemeleri ve ölçümleri yakalayın.</span><span class="sxs-lookup"><span data-stu-id="fc834-135">Capture traces and metrics for all calls between services to provide insights and diagnostics.</span></span>

<span data-ttu-id="fc834-136">Herhangi bir uygulama, davpr dışarıdan **çekme API 'sini** kullanarak bir davpr sepet çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-136">Any application can invoke a Dapr sidecar by using the native **invoke** API built into Dapr.</span></span> <span data-ttu-id="fc834-137">API, HTTP ya da gRPC ile çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-137">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="fc834-138">HTTP API 'sini çağırmak için aşağıdaki URL 'YI kullanın:</span><span class="sxs-lookup"><span data-stu-id="fc834-138">Use the following URL to call the HTTP API:</span></span>

``` http
http://localhost:<dapr-port>/v1.0/invoke/<application-id>/method/<method-name>
```

- <span data-ttu-id="fc834-139">`<dapr-port>` Bapr 'nin dinlediği HTTP bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="fc834-139">`<dapr-port>` the HTTP port that Dapr is listening on.</span></span>
- <span data-ttu-id="fc834-140">`<application-id>` çağrılacak hizmetin uygulama kimliği.</span><span class="sxs-lookup"><span data-stu-id="fc834-140">`<application-id>` application id of the service to call.</span></span>
- <span data-ttu-id="fc834-141">`<method-name>` uzak hizmette çağrılacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="fc834-141">`<method-name>` name of the method to invoke on the remote service.</span></span>

<span data-ttu-id="fc834-142">Aşağıdaki örnekte,  `catalog/items` öğesinin ' Get ' uç noktası için bir kıvrımlı çağrı yapılır `Service B` :</span><span class="sxs-lookup"><span data-stu-id="fc834-142">In the following example, a *curl* call is made to the `catalog/items` 'GET' endpoint of `Service B`:</span></span>

```console
curl http://localhost:3500/v1.0/invoke/serviceb/method/catalog/items
```

> [!NOTE]
> <span data-ttu-id="fc834-143">Davpr API 'Leri, Davpr oluşturma blokları kullanmak için HTTP veya gRPC 'yi destekleyen tüm uygulama yığınlarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="fc834-143">The Dapr APIs enable any application stack that supports HTTP or gRPC to use Dapr building blocks.</span></span> <span data-ttu-id="fc834-144">Bu nedenle, hizmet çağırma yapı taşı protokoller arasında köprü işlevi görebilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-144">Therefore, the service invocation building block can act as a bridge between protocols.</span></span> <span data-ttu-id="fc834-145">Hizmetler, HTTP, gRPC veya her ikisinin birleşimini kullanarak birbirleriyle iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-145">Services can communicate with each other using HTTP, gRPC or a combination of both.</span></span>

<span data-ttu-id="fc834-146">Sonraki bölümde, hizmet çağırma çağrılarını basitleştirmek için .NET SDK 'sını nasıl kullanacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fc834-146">In the next section, you'll learn how to use the .NET SDK to simplify service invocation calls.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="fc834-147">Davpr .NET SDK 'sını kullanma</span><span class="sxs-lookup"><span data-stu-id="fc834-147">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="fc834-148">Davpr [.NET SDK](https://github.com/dapr/dotnet-sdk) , .net geliştiricilerine, davpr ile etkileşime geçmek için sezgisel ve dile özgü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-148">The Dapr [.NET SDK](https://github.com/dapr/dotnet-sdk) provides .NET developers with an intuitive and language-specific way to interact with Dapr.</span></span> <span data-ttu-id="fc834-149">SDK, geliştiricilere uzak hizmet çağırma çağrıları yapmak için üç yol sunar:</span><span class="sxs-lookup"><span data-stu-id="fc834-149">The SDK offers developers three ways of making remote service invocation calls:</span></span>

1. <span data-ttu-id="fc834-150">HttpClient kullanarak HTTP hizmetlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="fc834-150">Invoke HTTP services using HttpClient</span></span>
1. <span data-ttu-id="fc834-151">Davprclient kullanarak HTTP hizmetlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="fc834-151">Invoke HTTP services using DaprClient</span></span>
1. <span data-ttu-id="fc834-152">Davprclient kullanarak gRPC hizmetlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="fc834-152">Invoke gRPC services using DaprClient</span></span>

### <a name="invoke-http-services-using-httpclient"></a><span data-ttu-id="fc834-153">HttpClient kullanarak HTTP hizmetlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="fc834-153">Invoke HTTP services using HttpClient</span></span>

<span data-ttu-id="fc834-154">HTTP uç noktasını çağırmak için tercih edilen yol, ile birlikte, Davpr 'nin zengin tümleştirmesini kullanmaktır `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="fc834-154">The preferred way to call an HTTP endpoint is to use Dapr's rich integration with `HttpClient`.</span></span> <span data-ttu-id="fc834-155">Aşağıdaki örnek, uygulamanın yöntemini çağırarak bir sıra gönderir `submit` `orderservice` :</span><span class="sxs-lookup"><span data-stu-id="fc834-155">The following example submits an order by calling the `submit` method of the `orderservice` application:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient();
await httpClient.PostAsJsonAsync("http://orderservice/submit", order);
```

<span data-ttu-id="fc834-156">Örnekte, `DaprClient.CreateHttpClient` `HttpClient` davpr hizmeti çağrısı yapmak için kullanılan bir örnek döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc834-156">In the example, `DaprClient.CreateHttpClient` returns an `HttpClient` instance that is used to perform Dapr service invocation.</span></span> <span data-ttu-id="fc834-157">Döndürülen, `HttpClient` giden Isteklerin URI 'lerini yeniden yazar özel bir Davpr ileti işleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-157">The returned `HttpClient` uses a special Dapr message handler that rewrites URIs of outgoing requests.</span></span> <span data-ttu-id="fc834-158">Ana bilgisayar adı, çağrılacak hizmetin uygulama kimliği olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-158">The host name is interpreted as the application id of the service to call.</span></span> <span data-ttu-id="fc834-159">Aslında Çağrılmakta olan yeniden yazan istek şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fc834-159">The rewritten request that's actually being called is:</span></span>

```http
http://127.0.0.1:3500/v1/invoke/orderservice/method/submit
```

<span data-ttu-id="fc834-160">Bu örnek, bir olan Davpr HTTP uç noktası için varsayılan değeri kullanır `http://127.0.0.1:<dapr-http-port>/` .</span><span class="sxs-lookup"><span data-stu-id="fc834-160">This example uses the default value for the Dapr HTTP endpoint, which is `http://127.0.0.1:<dapr-http-port>/`.</span></span> <span data-ttu-id="fc834-161">Değeri `dapr-http-port` `DAPR_HTTP_PORT` ortam değişkeninden alınır.</span><span class="sxs-lookup"><span data-stu-id="fc834-161">The value of `dapr-http-port` is taken from the `DAPR_HTTP_PORT` environment variable.</span></span> <span data-ttu-id="fc834-162">Ayarlanmamışsa, varsayılan bağlantı noktası numarası `3500` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc834-162">If it's not set, the default port number `3500` is used.</span></span>

<span data-ttu-id="fc834-163">Alternatif olarak, çağrısında özel bir uç nokta yapılandırabilirsiniz `DaprClient.CreateHttpClient` :</span><span class="sxs-lookup"><span data-stu-id="fc834-163">Alternatively, you can configure a custom endpoint in the call to `DaprClient.CreateHttpClient`:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient(daprEndpoint = "localhost:4000");
```

<span data-ttu-id="fc834-164">Ayrıca, uygulama kimliğini belirterek taban adresini doğrudan ayarlayabilirsiniz. Bu, bir çağrı yaparken göreli URI 'Leri kullanmayı mümkün kılar:</span><span class="sxs-lookup"><span data-stu-id="fc834-164">You can also directly set the base address by specifying the application id. This makes it possible to use relative URIs when making a call:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient("orderservice");
await httpClient.PostAsJsonAsync("/submit");
```

<span data-ttu-id="fc834-165">`HttpClient`Nesne uzun süreli olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fc834-165">The `HttpClient` object is intended to be long-lived.</span></span> <span data-ttu-id="fc834-166">`HttpClient`Uygulamanın ömrü için tek bir örnek yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-166">A single `HttpClient` instance can be reused for the lifetime of the application.</span></span> <span data-ttu-id="fc834-167">Sonraki senaryoda bir `OrderServiceClient` sınıfın bir Davpr örneğini yeniden nasıl yeniden kullandığı gösterilmektedir `HttpClient` :</span><span class="sxs-lookup"><span data-stu-id="fc834-167">The next scenario demonstrates how an `OrderServiceClient` class reuses a Dapr `HttpClient` instance:</span></span>  

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddSingleton<IOrderServiceClient, OrderServiceClient>(
        _ => new OrderServiceClient(DaprClient.CreateInvokeHttpClient("orderservice")));
}
```

<span data-ttu-id="fc834-168">Yukarıdaki kod parçacığında, `OrderServiceClient` ASP.NET Core bağımlılık ekleme sistemiyle tek bir olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-168">In the snippet above, the `OrderServiceClient` is registered as a singleton with the ASP.NET Core dependency injection system.</span></span> <span data-ttu-id="fc834-169">Uygulama fabrikası, çağırarak yeni bir `HttpClient` örnek oluşturur `DaprClient.CreateInvokeHttpClient` .</span><span class="sxs-lookup"><span data-stu-id="fc834-169">An implementation factory creates a new `HttpClient` instance by calling `DaprClient.CreateInvokeHttpClient`.</span></span> <span data-ttu-id="fc834-170">Daha sonra nesneyi başlatmak için yeni oluşturulan ' ı kullanır `HttpClient` `OrderServiceClient` .</span><span class="sxs-lookup"><span data-stu-id="fc834-170">It then uses the newly created `HttpClient` to instantiate the `OrderServiceClient` object.</span></span> <span data-ttu-id="fc834-171">`OrderServiceClient`Tek bir olarak kaydederek uygulamanın ömrü için yeniden kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc834-171">By registering the `OrderServiceClient` as a singleton, it will be reused for the lifetime of the application.</span></span>

<span data-ttu-id="fc834-172">`OrderServiceClient`Kendisinin hiçbir Davpr 'e özgü kodu yoktur.</span><span class="sxs-lookup"><span data-stu-id="fc834-172">The `OrderServiceClient` itself has no Dapr-specific code.</span></span> <span data-ttu-id="fc834-173">PAPR hizmeti çağrısı, birlikte kullanıldığında, Davpr HttpClient 'ı diğer bir HttpClient gibi kabul edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fc834-173">Even though Dapr service invocation is used under the hood, you can treat the Dapr HttpClient like any other HttpClient:</span></span>

```csharp
public class OrderServiceClient : IOrderServiceClient
{
    private readonly HttpClient _httpClient;

    public OrderServiceClient(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public async Task SubmitOrder(Order order)
    {
        var response = await _httpClient.PostAsJsonAsync("submit", order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="fc834-174">HttpClient sınıfının Davpr hizmeti çağrısı ile kullanılması birçok avantaj sağlar:</span><span class="sxs-lookup"><span data-stu-id="fc834-174">Using the HttpClient class with Dapr service invocation has many benefits:</span></span>

- <span data-ttu-id="fc834-175">HttpClient birçok geliştiricinin kodda zaten kullandığı iyi bilinen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="fc834-175">HttpClient is a well known class that many developers already use in their code.</span></span> <span data-ttu-id="fc834-176">Davpr hizmeti çağrısı için HttpClient kullanılması, geliştiricilerin mevcut becerilerini yeniden kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="fc834-176">Using HttpClient for Dapr service invocation allows developers to reuse their existing skills.</span></span>
- <span data-ttu-id="fc834-177">HttpClient özel üstbilgiler, istek ve yanıt iletileri üzerinde tam denetim gibi gelişmiş senaryoları destekler.</span><span class="sxs-lookup"><span data-stu-id="fc834-177">HttpClient supports advanced scenarios, such as custom headers, and full control over request and response messages.</span></span>
- <span data-ttu-id="fc834-178">.NET 5 ' te HttpClient, System.Text.Jskullanarak otomatik serileştirme ve seri durumdan çıkarma destekler.</span><span class="sxs-lookup"><span data-stu-id="fc834-178">In .NET 5, HttpClient supports automatic serialization and deserialization using System.Text.Json.</span></span>
- <span data-ttu-id="fc834-179">HttpClient, [Refit](https://github.com/reactiveui/refit), [Restsharp](https://restsharp.dev/getting-started/getting-started.html#basic-usage)ve [Polly](https://github.com/App-vNext/Polly)gibi birçok mevcut çerçeve ve kitaplık ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="fc834-179">HttpClient integrates with many existing frameworks and libraries, such as [Refit](https://github.com/reactiveui/refit), [RestSharp](https://restsharp.dev/getting-started/getting-started.html#basic-usage), and [Polly](https://github.com/App-vNext/Polly).</span></span>

### <a name="invoke-http-services-using-daprclient"></a><span data-ttu-id="fc834-180">Davprclient kullanarak HTTP hizmetlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="fc834-180">Invoke HTTP services using DaprClient</span></span>

<span data-ttu-id="fc834-181">HttpClient, HTTP semantiğini kullanarak hizmetleri çağırmak için tercih edilen yol olsa da, `DaprClient.InvokeMethodAsync` Yöntem ailesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc834-181">While HttpClient is the preferred way to invoke services using HTTP semantics, you can also use the `DaprClient.InvokeMethodAsync` family of methods.</span></span> <span data-ttu-id="fc834-182">Aşağıdaki örnek, uygulamanın yöntemini çağırarak bir sıra gönderir `submit` `orderservice` :</span><span class="sxs-lookup"><span data-stu-id="fc834-182">The following example submits an order by calling the `submit` method of the `orderservice` application:</span></span>

``` csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation =
        await daprClient.InvokeMethodAsync<Order, OrderConfirmation>(
            "orderservice", "submit", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

<span data-ttu-id="fc834-183">Bir nesnesi olan üçüncü bağımsız değişken `order` dahili olarak serileştirilir (ile `System.Text.JsonSerializer` ) ve istek yükü olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-183">The third argument, an `order` object, is serialized internally (with `System.Text.JsonSerializer`) and sent as the request payload.</span></span> <span data-ttu-id="fc834-184">.NET SDK, sidecar çağrısını üstlenir.</span><span class="sxs-lookup"><span data-stu-id="fc834-184">The .NET SDK takes care of the call to the sidecar.</span></span> <span data-ttu-id="fc834-185">Ayrıca, bir nesneye yapılan yanıtı da serileştirir `OrderConfirmation` .</span><span class="sxs-lookup"><span data-stu-id="fc834-185">It also deserializes the response to an `OrderConfirmation` object.</span></span> <span data-ttu-id="fc834-186">HTTP yöntemi belirtilmediğinden, istek bir HTTP POST olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="fc834-186">Because no HTTP method is specified, the request is executed as an HTTP POST.</span></span>

<span data-ttu-id="fc834-187">Sonraki örnekte şunu belirterek bir HTTP GET isteği nasıl yapabileceğiniz gösterilmektedir `HttpMethod` :</span><span class="sxs-lookup"><span data-stu-id="fc834-187">The next example demonstrates how you can make an HTTP GET request by specifying the `HttpMethod`:</span></span>

```csharp
var catalogItems = await daprClient.InvokeMethodAsync<IEnumerable<CatalogItem>>(HttpMethod.Get, "catalogservice", "items");
```

<span data-ttu-id="fc834-188">Bazı senaryolarda istek iletisi üzerinde daha fazla denetime ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc834-188">For some scenarios, you may require more control over the request message.</span></span> <span data-ttu-id="fc834-189">Örneğin, istek üst bilgilerini belirtmeniz gerektiğinde veya yük için özel bir seri hale getirici kullanmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="fc834-189">For example, when you need to specify request headers, or you want to use a custom serializer for the payload.</span></span> <span data-ttu-id="fc834-190">`DaprClient.CreateInvokeMethodRequest` oluşturur `HttpRequestMessage` .</span><span class="sxs-lookup"><span data-stu-id="fc834-190">`DaprClient.CreateInvokeMethodRequest` creates an `HttpRequestMessage`.</span></span> <span data-ttu-id="fc834-191">Aşağıdaki örnek, bir istek iletisine HTTP yetkilendirme üst bilgisinin nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="fc834-191">The following example demonstrates how to add an HTTP authorization header to a request message:</span></span>

```csharp
var request = daprClient.CreateInvokeMethodRequest("orderservice", "submit", order);
request.Headers.Authorization = new AuthenticationHeaderValue("bearer", token);
```

<span data-ttu-id="fc834-192">`HttpRequestMessage`Şimdi aşağıdaki özellikler ayarlanmış:</span><span class="sxs-lookup"><span data-stu-id="fc834-192">The `HttpRequestMessage` now has the following properties set:</span></span>

- <span data-ttu-id="fc834-193">URL = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`</span><span class="sxs-lookup"><span data-stu-id="fc834-193">Url = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`</span></span>
- <span data-ttu-id="fc834-194">HttpMethod = GÖNDERI</span><span class="sxs-lookup"><span data-stu-id="fc834-194">HttpMethod = POST</span></span>
- <span data-ttu-id="fc834-195">Content =  `JsonContent` JSON seri hale getirilmiş nesneyi içeren nesne `order`</span><span class="sxs-lookup"><span data-stu-id="fc834-195">Content =  `JsonContent` object containing the JSON-serialized `order`</span></span>
- <span data-ttu-id="fc834-196">Headers. Authorization = "taşıyıcı \<token> "</span><span class="sxs-lookup"><span data-stu-id="fc834-196">Headers.Authorization = "bearer \<token>"</span></span>

<span data-ttu-id="fc834-197">İsteği istediğiniz şekilde ayarladıktan sonra `DaprClient.InvokeMethodAsync` göndermek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="fc834-197">Once you've got the request set up the way you want, use `DaprClient.InvokeMethodAsync` to send it:</span></span>

```csharp
var orderConfirmation = await daprClient.InvokeMethodAsync<OrderConfirmation>(request);
```

<span data-ttu-id="fc834-198">`DaprClient.InvokeMethodAsync` istek başarılı olursa, bir nesneye yapılan yanıtı seri hale getirir `OrderConfirmation` .</span><span class="sxs-lookup"><span data-stu-id="fc834-198">`DaprClient.InvokeMethodAsync` deserializes the response to an `OrderConfirmation` object if the request is succesful.</span></span> <span data-ttu-id="fc834-199">Alternatif olarak, `DaprClient.InvokeMethodWithResponseAsync` temeldeki öğesine tam erişim sağlamak için kullanabilirsiniz `HttpResponseMessage` :</span><span class="sxs-lookup"><span data-stu-id="fc834-199">Alternatively, you can use `DaprClient.InvokeMethodWithResponseAsync` to get full access to the underlying `HttpResponseMessage`:</span></span>

```csharp
var response = await daprClient.InvokeMethodWithResponseAsync(request);
response.EnsureSuccessStatusCode();

var orderConfirmation = response.Content.ReadFromJsonAsync<OrderConfirmation>();
```

> [!NOTE]
> <span data-ttu-id="fc834-200">HTTP kullanan hizmet çağrısı çağrıları için, önceki bölümde sunulan Davpr HttpClient Tümleştirmesini kullanmayı göz önünde bulundurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc834-200">For service invocation calls using HTTP, it's worth considering using the Dapr HttpClient integration presented in the previous section.</span></span> <span data-ttu-id="fc834-201">HttpClient kullanımı, mevcut çerçeveler ve kitaplıklarla tümleştirme gibi ek avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-201">Using HttpClient gives you additional benefits such as integration with existing frameworks and libraries.</span></span>

### <a name="invoke-grpc-services-using-daprclient"></a><span data-ttu-id="fc834-202">Davprclient kullanarak gRPC hizmetlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="fc834-202">Invoke gRPC services using DaprClient</span></span>

<span data-ttu-id="fc834-203">Davprclient, `InvokeMethodGrpcAsync` gRPC uç noktaları çağırmak için bir yöntem ailesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-203">DaprClient provides a family of `InvokeMethodGrpcAsync` methods for calling gRPC endpoints.</span></span> <span data-ttu-id="fc834-204">HTTP yöntemleriyle ilgili temel fark, JSON yerine Protoseri hale getirici kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="fc834-204">The main difference with the HTTP methods is the use of a Protobuf serializer instead of JSON.</span></span> <span data-ttu-id="fc834-205">Aşağıdaki örnek `submitOrder` `orderservice` GRPC Over metodunu çağırır.</span><span class="sxs-lookup"><span data-stu-id="fc834-205">The following example invokes the `submitOrder` method of the `orderservice` over gRPC.</span></span>

```csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation = await daprClient.InvokeMethodGrpcAsync<Order, OrderConfirmation>("orderservice", "submitOrder", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

<span data-ttu-id="fc834-206">Yukarıdaki örnekte, Davprclient, `order` [protoarabelleğe](https://developers.google.com/protocol-buffers) kullanarak verilen nesneyi serileştirir ve sonucu GRPC istek gövdesi olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-206">In the example above, DaprClient serializes the given `order` object using [Protobuf](https://developers.google.com/protocol-buffers) and uses the result as the gRPC request body.</span></span> <span data-ttu-id="fc834-207">Benzer şekilde, yanıt gövdesi seri durumdan çıkarılmış olur ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fc834-207">Likewise, the response body is Protobuf deserialized and returned to the caller.</span></span> <span data-ttu-id="fc834-208">Prototip genellikle HTTP hizmeti çağrısında kullanılan JSON yüklerinden daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-208">Protobuf typically provides better performance than the JSON payloads used in HTTP service invocation.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="fc834-209">Başvuru uygulaması: Eshopondadpr</span><span class="sxs-lookup"><span data-stu-id="fc834-209">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="fc834-210">Microsoft 'un orijinal [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) mikro hizmet başvuru mımarısı, http/REST ve GRPC hizmetlerinin bir karışımını kullandı.</span><span class="sxs-lookup"><span data-stu-id="fc834-210">The original [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) microservice reference architecture from Microsoft used a mix of HTTP/REST and gRPC services.</span></span> <span data-ttu-id="fc834-211">GRPC kullanımı, [Toplayıcı hizmeti](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) ile çekirdek arka uç hizmetleri arasındaki iletişim ile sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fc834-211">The use of gRPC was limited to communication between an [aggregator service](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) and core backend services.</span></span> <span data-ttu-id="fc834-212">Şekil 6-2 mimariyi gösterme:</span><span class="sxs-lookup"><span data-stu-id="fc834-212">Figure 6-2 show the architecture:</span></span>

![eShopOnContainers 'da gRPC ve HTTP/REST çağrıları](./media/service-invocation/eshop-on-containers.png)

<span data-ttu-id="fc834-214">**Şekil 6-2**.</span><span class="sxs-lookup"><span data-stu-id="fc834-214">**Figure 6-2**.</span></span> <span data-ttu-id="fc834-215">eShopOnContainers 'da gRPC ve HTTP/REST çağrıları.</span><span class="sxs-lookup"><span data-stu-id="fc834-215">gRPC and HTTP/REST calls in eShopOnContainers.</span></span>

<span data-ttu-id="fc834-216">Önceki şekildeki adımları göz önünde bulun:</span><span class="sxs-lookup"><span data-stu-id="fc834-216">Note the steps from the previous figure:</span></span>

1. <span data-ttu-id="fc834-217">Ön uç, HTTP/REST kullanarak [API ağ geçidini](https://docs.microsoft.com/azure/architecture/microservices/design/gateway) çağırır.</span><span class="sxs-lookup"><span data-stu-id="fc834-217">The frontend calls the [API gateway](https://docs.microsoft.com/azure/architecture/microservices/design/gateway) using HTTP/REST.</span></span>

1. <span data-ttu-id="fc834-218">API Gateway basit [CRUD](https://www.sumologic.com/glossary/crud/) (oluşturma, okuma, güncelleştirme, silme) isteklerini http/Rest kullanarak doğrudan bir çekirdek arka uç hizmetine iletir.</span><span class="sxs-lookup"><span data-stu-id="fc834-218">The API gateway forwards simple [CRUD](https://www.sumologic.com/glossary/crud/) (Create, Read, Update, Delete) requests directly to a core backend service using HTTP/REST.</span></span>

1. <span data-ttu-id="fc834-219">API Gateway, birden fazla arka uç hizmetine yönelik Eşgüdümlü çağrıları içeren karmaşık istekleri Web alışveriş toplayıcısı hizmeti 'ne iletir.</span><span class="sxs-lookup"><span data-stu-id="fc834-219">The API gateway forwards complex requests that involve coordinated calls to multiple backend services to the web shopping aggregator service.</span></span>

1. <span data-ttu-id="fc834-220">Toplayıcı hizmeti, çekirdek arka uç hizmetlerini çağırmak için gRPC 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-220">The aggregator service uses gRPC to call core backend services.</span></span>

<span data-ttu-id="fc834-221">Son güncellenen Eshopondadpr uygulamasında, hizmet ve API ağ geçidine Davpr sıfları eklenir.</span><span class="sxs-lookup"><span data-stu-id="fc834-221">In the recently updated eShopOnDapr implementation, Dapr sidecars are added to the services and API gateway.</span></span> <span data-ttu-id="fc834-222">Şekil 6-3 güncelleştirilmiş mimariyi göster:</span><span class="sxs-lookup"><span data-stu-id="fc834-222">Figure 6-3 show the updated architecture:</span></span>

![eShopOnContainers 'da sıdecars ile gRPC ve HTTP/REST çağrıları](./media/service-invocation/eshop-on-dapr.png)

<span data-ttu-id="fc834-224">**Şekil 6-3**.</span><span class="sxs-lookup"><span data-stu-id="fc834-224">**Figure 6-3**.</span></span> <span data-ttu-id="fc834-225">Davpr kullanılarak eShop mimarisi güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="fc834-225">Updated eShop architecture using Dapr.</span></span>

<span data-ttu-id="fc834-226">Önceki şekildeki güncelleştirilmiş adımlara göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="fc834-226">Note the updated steps from the previous figure:</span></span>

1. <span data-ttu-id="fc834-227">Ön uç hala API ağ geçidini çağırmak için HTTP/REST kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-227">The frontend still uses HTTP/REST to call the API gateway.</span></span>

1. <span data-ttu-id="fc834-228">API Gateway, HTTP isteklerini Davpr sidecar 'e iletir.</span><span class="sxs-lookup"><span data-stu-id="fc834-228">The API gateway forwards HTTP requests to its Dapr sidecar.</span></span>

1. <span data-ttu-id="fc834-229">API ağ geçidi sepet, isteği toplayıcı veya arka uç hizmetinin sepet 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="fc834-229">The API gateway sidecar sends the request to the sidecar of the aggregator or backend service.</span></span>

1. <span data-ttu-id="fc834-230">Toplayıcı hizmeti, arka uç hizmetlerini dışarıdan çekme mimarisiyle çağırmak için, Davpr .NET SDK 'sını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-230">The aggregator service uses the Dapr .NET SDK to call backend services through their sidecar architecture.</span></span>

<span data-ttu-id="fc834-231">Davpr, gRPC ile sıfları arasındaki çağrıları uygular.</span><span class="sxs-lookup"><span data-stu-id="fc834-231">Dapr implements calls between sidecars with gRPC.</span></span> <span data-ttu-id="fc834-232">Bu nedenle, uzak bir hizmeti HTTP/REST semantiğinin gerçekleştirseniz bile, taşımanın bir parçası gRPC kullanılarak gene de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-232">So even if you're invoking a remote service with HTTP/REST semantics, a part of the transport is still implemented using gRPC.</span></span>

<span data-ttu-id="fc834-233">Eshopondadpr başvuru uygulaması avantajlarından yararlanın.</span><span class="sxs-lookup"><span data-stu-id="fc834-233">The eShopOnDapr reference application benefits from the Dapr service invocation building block.</span></span> <span data-ttu-id="fc834-234">Avantajlara hizmet bulma, otomatik mTLS ve Observability dahildir.</span><span class="sxs-lookup"><span data-stu-id="fc834-234">The benefits include service discovery, automatic mTLS, and observability.</span></span>

### <a name="forward-http-requests-using-envoy-and-dapr"></a><span data-ttu-id="fc834-235">Envoy ve Davpr kullanarak HTTP isteklerini ilet</span><span class="sxs-lookup"><span data-stu-id="fc834-235">Forward HTTP requests using Envoy and Dapr</span></span>

<span data-ttu-id="fc834-236">Hem özgün hem de güncelleştirilmiş eShop uygulaması, bir API ağ geçidi olarak [Envoy proxy](https://www.envoyproxy.io/) 'sinden faydalanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-236">Both the original and updated eShop application leverage the [Envoy proxy](https://www.envoyproxy.io/) as an API gateway.</span></span> <span data-ttu-id="fc834-237">Envoy, modern dağıtılmış uygulamalar arasında popüler bir açık kaynaklı ara sunucu ve iletişim veri yolu.</span><span class="sxs-lookup"><span data-stu-id="fc834-237">Envoy is an open-source proxy and communication bus that is popular across modern distributed applications.</span></span> <span data-ttu-id="fc834-238">Lyft 'den kaynaklanan Envoy, [bulutta yerel bilgi Işlem altyapısı](https://www.cncf.io/)tarafından sahiplenilir ve korunur.</span><span class="sxs-lookup"><span data-stu-id="fc834-238">Originating from Lyft, Envoy is owned and maintained by the [Cloud-Native Computing Foundation](https://www.cncf.io/).</span></span>

<span data-ttu-id="fc834-239">Özgün eShopOnContainers uygulamasında, Envoy API Gateway gelen HTTP isteklerini doğrudan toplayıcı veya arka uç hizmetlerine iletti.</span><span class="sxs-lookup"><span data-stu-id="fc834-239">In the original eShopOnContainers implementation, the Envoy API gateway forwarded incoming HTTP requests directly to aggregator or backend services.</span></span> <span data-ttu-id="fc834-240">New Eshopondadpr 'de, Envoy proxy, isteği bir Davpr sidecar 'e iletir.</span><span class="sxs-lookup"><span data-stu-id="fc834-240">In the new eShopOnDapr, the Envoy proxy forwards the request to a Dapr sidecar.</span></span> <span data-ttu-id="fc834-241">Sepet hizmet çağrısı, mTLS ve Observability sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-241">The sidecar provides service invocation, mTLS, and observability.</span></span>

<span data-ttu-id="fc834-242">Envoy, proxy 'nin davranışını denetlemek için bir YAML tanım dosyası kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="fc834-242">Envoy is configured using a YAML definition file to control the proxy's behavior.</span></span> <span data-ttu-id="fc834-243">HTTP isteklerini bir davpr sepet kapsayıcısına iletmek için Envoy özelliğini etkinleştirmek için, `dapr` yapılandırmaya bir küme eklenir.</span><span class="sxs-lookup"><span data-stu-id="fc834-243">To enable Envoy to forward HTTP requests to a Dapr sidecar container, a `dapr` cluster is added to the configuration.</span></span> <span data-ttu-id="fc834-244">Küme yapılandırması, ' de, Davpr dışarıdan arabasının dinlediği HTTP bağlantı noktasını gösteren bir konak içerir:</span><span class="sxs-lookup"><span data-stu-id="fc834-244">The cluster configuration contains a host that points to the HTTP port on which the Dapr sidecar is listening:</span></span>

``` yaml
clusters:
- name: dapr
  connect_timeout: 0.25s
  type: strict_dns
  hosts:
  - socket_address:
    address: 127.0.0.1
    port_value: 3500
```

<span data-ttu-id="fc834-245">Envoy rotalar yapılandırması, gelen istekleri davpr sepet çağrısı olarak yeniden yazmak üzere güncelleştirilir ( `prefix_rewrite` anahtar/değer çiftine ödeme için dikkat edin):</span><span class="sxs-lookup"><span data-stu-id="fc834-245">The Envoy routes configuration is updated to rewrite incoming requests as calls to the Dapr sidecar (pay close attention to the `prefix_rewrite` key/value pair):</span></span>

``` yaml
- name: "c-short"
  match:
    prefix: "/c/"
  route:
    auto_host_rewrite: true
    prefix_rewrite: "/v1.0/invoke/catalog-api/method/"
    cluster: dapr
```

<span data-ttu-id="fc834-246">Ön uç istemcisinin Katalog öğelerinin bir listesini almak istediği bir senaryo düşünün.</span><span class="sxs-lookup"><span data-stu-id="fc834-246">Consider a scenario where the frontend client wants to retrieve a list of catalog items.</span></span> <span data-ttu-id="fc834-247">Katalog API 'SI, katalog öğelerini almak için bir uç nokta sağlar:</span><span class="sxs-lookup"><span data-stu-id="fc834-247">The Catalog API provides an endpoint for getting the catalog items:</span></span>

``` csharp
[Route("api/v1/[controller]")]
[ApiController]
public class CatalogController : ControllerBase
{
    [HttpGet("items")]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery] int pageSize = 10,
        [FromQuery] int pageIndex = 0)
    {
        // ...
    }
```

<span data-ttu-id="fc834-248">İlk olarak, ön uç, Envoy API ağ geçidine doğrudan HTTP çağrısı yapar.</span><span class="sxs-lookup"><span data-stu-id="fc834-248">First, the front end makes a direct HTTP call to the Envoy API gateway.</span></span>

```
GET http://<api-gateway>/c/api/v1/catalog/items?pageSize=20
```

<span data-ttu-id="fc834-249">Envoy proxy 'si rotayla eşleşir, HTTP isteğini yeniden yazar ve bunu, `invoke` Davpr sidecar 'in API 'sine iletir:</span><span class="sxs-lookup"><span data-stu-id="fc834-249">The Envoy proxy matches the route, rewrites the HTTP request, and forwards it to the `invoke` API of its Dapr sidecar:</span></span>

```
GET http://127.0.0.1:3500/v1.0/invoke/catalog-api/method/api/v1/catalog/items?pageSize=20
```

<span data-ttu-id="fc834-250">Sepet, hizmet bulmayı işler ve isteği katalog API 'SI araç çubuğu 'na yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="fc834-250">The sidecar handles service discovery and routes the request to the Catalog API sidecar.</span></span> <span data-ttu-id="fc834-251">Son olarak, sepet, isteği yürütmek, katalog öğelerini getirmek ve bir yanıt döndürmek için katalog API 'sini çağırır:</span><span class="sxs-lookup"><span data-stu-id="fc834-251">Finally, the sidecar calls the Catalog API to execute the request, fetch catalog items, and return a response:</span></span>

```
GET http://localhost/api/v1/catalog/items?pageSize=20
```

### <a name="make-aggregated-service-calls-using-the-net-sdk"></a><span data-ttu-id="fc834-252">.NET SDK kullanarak toplu hizmet çağrıları yapma</span><span class="sxs-lookup"><span data-stu-id="fc834-252">Make aggregated service calls using the .NET SDK</span></span>

<span data-ttu-id="fc834-253">EShop ön ucu 'ndan çoğu çağrı basit CRUD çağrılardır.</span><span class="sxs-lookup"><span data-stu-id="fc834-253">Most calls from the eShop frontend are simple CRUD calls.</span></span> <span data-ttu-id="fc834-254">API Gateway, bunları işlenmek üzere tek bir hizmete iletir.</span><span class="sxs-lookup"><span data-stu-id="fc834-254">The API gateway forwards them to a single service for processing.</span></span> <span data-ttu-id="fc834-255">Ancak, bazı senaryolar, bir isteği tamamlamaya yönelik birden fazla arka uç hizmetinin birlikte çalışmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fc834-255">Some scenarios, however, require multiple backend services to work together to complete a request.</span></span> <span data-ttu-id="fc834-256">Bu daha karmaşık çağrılar için eShop, iş akışını birden çok hizmet arasında aracılık için Web alışveriş Toplayıcısı hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-256">For these more complex calls, eShop uses the web shopping aggregator service to mediate the workflow across multiple services.</span></span> <span data-ttu-id="fc834-257">Şekil 6-4, alışveriş sepetinize bir öğe eklemenin işlem dizisini gösterir:</span><span class="sxs-lookup"><span data-stu-id="fc834-257">Figure 6-4 show the processing sequence of adding an item to your shopping basket:</span></span>

![Sepet sırası diyagramını Güncelleştir](./media/service-invocation/complex-call.png)

<span data-ttu-id="fc834-259">**Şekil 6-4**.</span><span class="sxs-lookup"><span data-stu-id="fc834-259">**Figure 6-4**.</span></span> <span data-ttu-id="fc834-260">Alışveriş sepeti sırasını güncelleştir.</span><span class="sxs-lookup"><span data-stu-id="fc834-260">Update shopping basket sequence.</span></span>

<span data-ttu-id="fc834-261">Toplayıcı hizmeti ilk olarak katalog API 'sinden katalog öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="fc834-261">The aggregator service first retrieves catalog items from the Catalog API.</span></span> <span data-ttu-id="fc834-262">Daha sonra öğe kullanılabilirliğini ve fiyatlandırmayı doğrular.</span><span class="sxs-lookup"><span data-stu-id="fc834-262">It then validates item availability and pricing.</span></span> <span data-ttu-id="fc834-263">Son olarak, Toplayıcı hizmeti, sepet API 'sini çağırarak güncelleştirilmiş alışveriş sepetini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fc834-263">Finally, the aggregator service saves the updated shopping basket by calling the Basket API.</span></span>

<span data-ttu-id="fc834-264">Toplayıcı hizmeti, `BasketController` alışveriş sepetini güncelleştirmek için bir uç nokta sağlayan bir içerir:</span><span class="sxs-lookup"><span data-stu-id="fc834-264">The aggregator service contains a `BasketController` that provides an endpoint for updating the shopping basket:</span></span>

``` csharp
[Route("api/v1/[controller]")]
[Authorize]
[ApiController]
public class BasketController : ControllerBase
{
    private readonly ICatalogService _catalog;
    private readonly IBasketService _basket;

    [HttpPost]
    [HttpPut]
    public async Task<ActionResult<BasketData>> UpdateAllBasketAsync(
        [FromBody] UpdateBasketRequest data, [FromHeader] string authorization)
    {
        // Get the item details from the catalog API.
        var catalogItems = await _catalog.GetCatalogItemsAsync(
            data.Items.Select(x => x.ProductId));

        // Check item availability and prices; store results in basket object.
        var basket = CreateValidatedBasket(data, catalogItems);

        // Save the shopping basket.
        await _basket.UpdateAsync(basket, authorization);

        return basket;
    }

    // ...
}
```

<span data-ttu-id="fc834-265">`UpdateAllBasketAsync`Yöntemi, gelen Isteğin *Yetkilendirme* üst bilgisini bir özniteliği kullanarak alır `FromHeader` .</span><span class="sxs-lookup"><span data-stu-id="fc834-265">The `UpdateAllBasketAsync` method gets the *Authorization* header of the incoming request using a `FromHeader` attribute.</span></span> <span data-ttu-id="fc834-266">*Yetkilendirme* üst bilgisi, korumalı arka uç hizmetlerini çağırmak için gereken erişim belirtecini içerir.</span><span class="sxs-lookup"><span data-stu-id="fc834-266">The *Authorization* header contains the access token that is needed to call protected backend services.</span></span>

<span data-ttu-id="fc834-267">Sepeti güncelleştirme isteği aldıktan sonra Toplayıcı hizmeti, öğe ayrıntılarını almak için katalog API 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fc834-267">After receiving a request to update the basket, the aggregator service calls the Catalog API to get the item details.</span></span> <span data-ttu-id="fc834-268">Sepet denetleyicisi, `ICatalogService` Bu çağrıyı yapmak ve Katalog API 'siyle iletişim kurmak için eklenen bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc834-268">The Basket controller uses an injected `ICatalogService` object to make that call and communicate with the Catalog API.</span></span> <span data-ttu-id="fc834-269">Uygulamanın orijinal uygulama çağrısı yapmak için gRPC kullandı.</span><span class="sxs-lookup"><span data-stu-id="fc834-269">The original implementation of the interface used gRPC to make the call.</span></span> <span data-ttu-id="fc834-270">Güncelleştirilmiş uygulama HttpClient desteğiyle Davpr hizmeti çağrısını kullanır:</span><span class="sxs-lookup"><span data-stu-id="fc834-270">The updated implementation uses Dapr service invocation with HttpClient support:</span></span>

``` csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public Task<IEnumerable<CatalogItem>> GetCatalogItemsAsync(IEnumerable<int> ids)
    {
        var requestUri = $"api/v1/catalog/items?ids={string.Join(",", ids)}";
      
        return _httpClient.GetFromJsonAsync<IEnumerable<CatalogItem>>(requestUri);
    }

    // ...
}
```

<span data-ttu-id="fc834-271">Hizmet çağırma çağrısını yapmak için hiçbir hiçbir Davpr özel kodu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fc834-271">Notice how no Dapr specific code is required to make the service invocation call.</span></span> <span data-ttu-id="fc834-272">Tüm iletişimler standart HttpClient nesnesi kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="fc834-272">All communication is done using the standard HttpClient object.</span></span>

<span data-ttu-id="fc834-273">Davpr HttpClient, `CatalogService` yönteminde sınıfına eklenir `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="fc834-273">The Dapr HttpClient is injected into the `CatalogService` class in the `Startup.ConfigureServices` method:</span></span>

```csharp
services.AddSingleton<ICatalogService, CatalogService>(
    _ => new CatalogService(DaprClient.CreateInvokeHttpClient("catalog-api")));
```

<span data-ttu-id="fc834-274">Toplayıcı hizmeti tarafından yapılan diğer çağrı sepet API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="fc834-274">The other call made by the aggregator service is to the Basket API.</span></span> <span data-ttu-id="fc834-275">Yalnızca yetkili isteklere izin verir.</span><span class="sxs-lookup"><span data-stu-id="fc834-275">It only allows authorized requests.</span></span> <span data-ttu-id="fc834-276">Çağrı başarılı olduğundan emin olmak için, erişim belirteci bir *Yetkilendirme* isteği üst bilgisinde iletilir:</span><span class="sxs-lookup"><span data-stu-id="fc834-276">The access token is passed along in an *Authorization* request header to ensure the call succeeds:</span></span>

``` csharp
public class BasketService : IBasketService
{
    public Task UpdateAsync(BasketData currentBasket, string accessToken)
    {
        var request = new HttpRequestMessage(HttpMethod.Post, "api/v1/basket")
        {
            Content = JsonContent.Create(currentBasket)
        };
        request.Headers.Authorization = new AuthenticationHeaderValue(accessToken);
       
        var response = await _httpClient.SendAsync(request);
        response.EnsureSuccessStatusCode();
    }

    // ...
}
```

<span data-ttu-id="fc834-277">Bu örnekte, hizmeti çağırmak için yalnızca standart HttpClient işlevselliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc834-277">In this example too, only standard HttpClient functionality is used to call the service.</span></span> <span data-ttu-id="fc834-278">Bu, HttpClient 'ı zaten bildiğiniz geliştiricilerin mevcut becerilerini yeniden kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-278">This allows developers who are already familiar with HttpClient to reuse their existing skills.</span></span> <span data-ttu-id="fc834-279">Bu, mevcut HttpClient kodunun hiçbir değişiklik yapmadan PAPR hizmeti çağrısını kullanmasına de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-279">It even enables existing HttpClient code to utilize Dapr service invocation without making any changes.</span></span>

## <a name="summary"></a><span data-ttu-id="fc834-280">Özet</span><span class="sxs-lookup"><span data-stu-id="fc834-280">Summary</span></span>

<span data-ttu-id="fc834-281">Bu bölümde, hizmet çağırma yapı taşı hakkında bilgi edindiniz.</span><span class="sxs-lookup"><span data-stu-id="fc834-281">In this chapter, you learned about the service invocation building block.</span></span> <span data-ttu-id="fc834-282">Hem Davpr dışarıdan çekme hem de Davpr .NET SDK kullanarak uzak yöntemlerin nasıl çağralınacağını gördünüz.</span><span class="sxs-lookup"><span data-stu-id="fc834-282">You saw how to invoke remote methods both by making direct HTTP calls to the Dapr sidecar, and by using the Dapr .NET SDK.</span></span>

<span data-ttu-id="fc834-283">Davpr .NET SDK 'Sı, uzak yöntemleri çağırmak için birden çok yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-283">The Dapr .NET SDK provides multiple ways to invoke remote methods.</span></span> <span data-ttu-id="fc834-284">HttpClient desteği, var olan becerileri yeniden kullanmak isteyen geliştiriciler için harika ve mevcut birçok çerçeve ve kitaplık ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="fc834-284">HttpClient support is great for developers wanting to reuse existing skills and is compatible with many existing frameworks and libraries.</span></span> <span data-ttu-id="fc834-285">Davprclient, HTTP veya gRPC semantiğini kullanarak doğrudan Davpr hizmeti çağırma API 'sini kullanma desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="fc834-285">DaprClient offers support for directly using the Dapr service invocation API using either HTTP or gRPC semantics.</span></span>

<span data-ttu-id="fc834-286">Eshopondadpr başvuru mimarisi, eski eShopOnContainers çözümünün, Davpr hizmeti çağrısı kullanılarak nasıl modernleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc834-286">The eShopOnDapr reference architecture shows how the original eShopOnContainers solution is modernized by using Dapr service invocation.</span></span> <span data-ttu-id="fc834-287">Davpr 'ye eShop eklemek, otomatik yeniden denemeler, mTLS kullanarak ileti şifreleme ve geliştirilmiş Observability gibi avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc834-287">Adding Dapr to eShop provides benefits such as automatic retries, message encryption using mTLS, and improved observability.</span></span>

### <a name="references"></a><span data-ttu-id="fc834-288">Başvurular</span><span class="sxs-lookup"><span data-stu-id="fc834-288">References</span></span>

- [<span data-ttu-id="fc834-289">Davpr hizmeti çağırma yapı taşı</span><span class="sxs-lookup"><span data-stu-id="fc834-289">Dapr service invocation building block</span></span>](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/)

- [<span data-ttu-id="fc834-290">Dağıtılmış bulutta yerel uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="fc834-290">Monitoring distributed cloud-native applications</span></span>](../cloud-native/observability-patterns.md)

> [!div class="step-by-step"]
> <span data-ttu-id="fc834-291">[Önceki](state-management.md) 
>  [Sonraki](publish-subscribe.md)</span><span class="sxs-lookup"><span data-stu-id="fc834-291">[Previous](state-management.md)
[Next](publish-subscribe.md)</span></span>
