---
title: Davpr bağlamaları yapı taşı
description: Bağlama oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: bc9c147e237e3cc27005fbf5bae25213cacfd33f
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629421"
---
# <a name="the-dapr-bindings-building-block"></a><span data-ttu-id="910c2-103">Davpr bağlamaları yapı taşı</span><span class="sxs-lookup"><span data-stu-id="910c2-103">The Dapr bindings building block</span></span>

<span data-ttu-id="910c2-104">Azure Işlevleri ve AWS Lambda gibi bulut tabanlı *sunucusuz* teklifler, dağıtılmış mimari alanı genelinde geniş bir benimseme elde etmiş.</span><span class="sxs-lookup"><span data-stu-id="910c2-104">Cloud-based *serverless* offerings, such as Azure Functions and AWS Lambda, have gained wide adoption across the distributed architecture space.</span></span> <span data-ttu-id="910c2-105">Birçok avantaj arasında, bir mikro hizmetin bir dış sistemdeki olayları *işlemesini* veya *çağırma* , temel karmaşıklık ve sıhhi tesisat sorunlarını ortadan kaldırmak üzere etkinleştirirler.</span><span class="sxs-lookup"><span data-stu-id="910c2-105">Among many benefits, they enable a microservice to *handle events from* or *invoke events in* an external system - abstracting away the underlying complexity and plumbing concerns.</span></span> <span data-ttu-id="910c2-106">Dış kaynaklar çok farklıdır: farklı platformlar ve satıcılar arasında veri depoları, ileti sistemleri ve Web kaynakları içerirler.</span><span class="sxs-lookup"><span data-stu-id="910c2-106">External resources are many: They include datastores, message systems, and web resources, across different platforms and vendors.</span></span> <span data-ttu-id="910c2-107">[Davpr bağlamaları yapı taşı](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/) , bu aynı kaynak bağlama yeteneklerini, davpr uygulamalarınızın doorstep getirir.</span><span class="sxs-lookup"><span data-stu-id="910c2-107">The [Dapr bindings building block](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/) brings these same resource binding capabilities to the doorstep of your Dapr applications.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="910c2-108">Ne çözdüğü</span><span class="sxs-lookup"><span data-stu-id="910c2-108">What it solves</span></span>

<span data-ttu-id="910c2-109">Davpr kaynak bağlamaları, hizmetlerinizin iş işlemlerini acil uygulama dışındaki dış kaynaklar arasında tümleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="910c2-109">Dapr resource bindings enable your services to integrate business operations across external resources outside of the immediate application.</span></span> <span data-ttu-id="910c2-110">Dış bir sistemden gelen bir olay, hizmetinizdeki bir işlemi bağlamsal bilgileri geçirerek tetikleyebilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-110">An event from an external system could trigger an operation in your service passing in contextual information.</span></span> <span data-ttu-id="910c2-111">Hizmetiniz daha sonra başka bir dış sistemdeki bir olayı tetikleyerek, bağlamsal yük bilgilerini geçirerek işlemi genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-111">Your service could then expand the operation by triggering an event in another external system, passing in contextual payload information.</span></span> <span data-ttu-id="910c2-112">Hizmetiniz dış kaynağın bağlantısı veya farkında olmadan iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="910c2-112">Your service communicates without coupling or awareness of the external resource.</span></span> <span data-ttu-id="910c2-113">Sıhhi tesisat, önceden tanımlanmış Davpr bileşenleri içinde kapsüllenir.</span><span class="sxs-lookup"><span data-stu-id="910c2-113">The plumbing is encapsulated inside pre-defined Dapr components.</span></span> <span data-ttu-id="910c2-114">Kullanılacak Davpr bileşeni, kod değişikliği yapılmadan çalışma zamanında kolayca değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-114">The Dapr component to use can be easily swapped at runtime without code changes.</span></span>

<span data-ttu-id="910c2-115">Örneğin, bir Kullanıcı bir anahtar sözcük olarak her seferinde bir olayı tetikleyen bir Twitter hesabı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="910c2-115">Consider, for example, a Twitter account that triggers an event whenever a user tweets a keyword.</span></span> <span data-ttu-id="910c2-116">Hizmetiniz, Tweet alıp işleyen bir olay işleyicisini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="910c2-116">Your service exposes an event handler that receives and processes the tweet.</span></span> <span data-ttu-id="910c2-117">Tamamlandıktan sonra, hizmetiniz bir dış Twilio hizmeti çağıran bir olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="910c2-117">Once complete, your service triggers an event that invokes an external Twilio service.</span></span> <span data-ttu-id="910c2-118">Twilio, Tweet içeren bir SMS iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="910c2-118">Twilio sends an SMS message that includes the tweet.</span></span> <span data-ttu-id="910c2-119">Şekil 8-1 Bu işlemin kavramsal mimarisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="910c2-119">Figure 8-1 show the conceptual architecture of this operation.</span></span>

![Giriş bağlama](media/bindings/bindings-architecture.png)

<span data-ttu-id="910c2-121">**Şekil 8-1**.</span><span class="sxs-lookup"><span data-stu-id="910c2-121">**Figure 8-1**.</span></span> <span data-ttu-id="910c2-122">Bir Davpr kaynak bağlamasının kavramsal mimarisi.</span><span class="sxs-lookup"><span data-stu-id="910c2-122">Conceptual architecture of a Dapr resource binding.</span></span>

<span data-ttu-id="910c2-123">İlk bakışta, kaynak bağlama davranışı bu kitapta daha önce açıklanan [Yayımla/abone ol düzenine](publish-subscribe.md) benzer şekilde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-123">At first glance, resource binding behavior may appear similar to the [Publish/Subscribe pattern](publish-subscribe.md) described earlier in this book.</span></span> <span data-ttu-id="910c2-124">Benzerlikler paylaştıkları sırada farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="910c2-124">While they share similarities, there are differences.</span></span> <span data-ttu-id="910c2-125">Yayımlama/abone olma, Davpr Hizmetleri arasındaki zaman uyumsuz iletişime odaklanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-125">Publish/subscribe focuses on asynchronous communication between Dapr services.</span></span> <span data-ttu-id="910c2-126">Kaynak bağlama çok daha geniş bir kapsama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="910c2-126">Resource binding has a much wider scope.</span></span> <span data-ttu-id="910c2-127">Yazılım platformları arasında sistem birlikte çalışabilirliğine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-127">It focuses on system interoperability across software platforms.</span></span> <span data-ttu-id="910c2-128">Mikro hizmet uygulamanızın dışındaki farklı uygulamalar, veri depoları ve hizmetler arasında bilgi alışverişi yapın.</span><span class="sxs-lookup"><span data-stu-id="910c2-128">Exchanging information between disparate applications, datastores, and services outside your microservice application.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="910c2-129">Nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="910c2-129">How it works</span></span>

<span data-ttu-id="910c2-130">Davpr kaynak bağlama bir bileşen yapılandırma dosyası ile başlar.</span><span class="sxs-lookup"><span data-stu-id="910c2-130">Dapr resource binding starts with a component configuration file.</span></span> <span data-ttu-id="910c2-131">Bu YAML dosyası, yapılandırma ayarlarıyla birlikte bağlayacağınız kaynak türünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="910c2-131">This YAML file describes the type of resource to which you'll bind along with its configuration settings.</span></span> <span data-ttu-id="910c2-132">Bir kez yapılandırıldıktan sonra, hizmetiniz kaynaktaki olayları alabilir veya üzerindeki olayları tetikleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="910c2-132">Once configured, your service can receive events from the resource or trigger events on it.</span></span>

> [!NOTE]
> <span data-ttu-id="910c2-133">Bağlama yapılandırması, daha sonra *Bileşenler* bölümünde ayrıntılı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="910c2-133">Binding configurations are presented in detail later in the *Components* section.</span></span>

### <a name="input-bindings"></a><span data-ttu-id="910c2-134">Giriş bağlamaları</span><span class="sxs-lookup"><span data-stu-id="910c2-134">Input bindings</span></span>

<span data-ttu-id="910c2-135">Giriş bağlamaları kodunuzu dış kaynaklardaki gelen olaylar ile tetikler.</span><span class="sxs-lookup"><span data-stu-id="910c2-135">Input bindings trigger your code with incoming events from external resources.</span></span> <span data-ttu-id="910c2-136">Olayları ve verileri almak için, hizmetinize *olay işleyicisi* haline gelen bir genel uç nokta kaydedersiniz.</span><span class="sxs-lookup"><span data-stu-id="910c2-136">To receive events and data, you register a public endpoint from your service that becomes the *event handler*.</span></span> <span data-ttu-id="910c2-137">Şekil 8-2, akışı gösterir:</span><span class="sxs-lookup"><span data-stu-id="910c2-137">Figure 8-2 shows the flow:</span></span>

![Davpr giriş bağlama akışı](media/bindings/input-binding-flow.png)

<span data-ttu-id="910c2-139">**Şekil 8-2**.</span><span class="sxs-lookup"><span data-stu-id="910c2-139">**Figure 8-2**.</span></span> <span data-ttu-id="910c2-140">Davpr giriş bağlama akışı.</span><span class="sxs-lookup"><span data-stu-id="910c2-140">Dapr input binding flow.</span></span>

<span data-ttu-id="910c2-141">Şekil 8,2, bir dış Twitter hesabından olay alma adımlarını açıklar:</span><span class="sxs-lookup"><span data-stu-id="910c2-141">Figure 8.2 describes the steps for receiving events from an external Twitter account:</span></span>

1. <span data-ttu-id="910c2-142">Davpr sepet, bağlama yapılandırma dosyasını okur ve dış kaynak için belirtilen olaya abone olur.</span><span class="sxs-lookup"><span data-stu-id="910c2-142">The Dapr sidecar reads the binding configuration file and subscribes to the event specified for the external resource.</span></span> <span data-ttu-id="910c2-143">Örnekte, olay kaynağı bir Twitter hesabıdır.</span><span class="sxs-lookup"><span data-stu-id="910c2-143">In the example, the event source is a Twitter account.</span></span>
1. <span data-ttu-id="910c2-144">Twitter 'da eşleşen bir tweet yayımlandığında, davpr sepet 'de çalışan bağlama bileşeni onu seçer ve bir olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="910c2-144">When a matching Tweet is published on Twitter, the binding component running in the Dapr sidecar picks it up and triggers an event.</span></span>
1. <span data-ttu-id="910c2-145">Davpr sepet bağlama için yapılandırılmış uç noktayı (olay işleyicisi) çağırır.</span><span class="sxs-lookup"><span data-stu-id="910c2-145">The Dapr sidecar invokes the endpoint (that is, event handler) configured for the binding.</span></span> <span data-ttu-id="910c2-146">Bu örnekte hizmet, `/tweet` 6000 numaralı bağlantı noktasındaki uç noktada BIR http gönderisi dinler.</span><span class="sxs-lookup"><span data-stu-id="910c2-146">In the example, the service listens for an HTTP POST on the `/tweet` endpoint on port 6000.</span></span> <span data-ttu-id="910c2-147">Bir HTTP POST işlemi olduğundan, olayın JSON yükü istek gövdesine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-147">Because it's an HTTP POST operation, the JSON payload for the event is passed in the request body.</span></span>
1. <span data-ttu-id="910c2-148">Olay işlendikten sonra hizmet bir HTTP durum kodu döndürür `200 OK` .</span><span class="sxs-lookup"><span data-stu-id="910c2-148">After handling the event, the service returns an HTTP status code `200 OK`.</span></span>

<span data-ttu-id="910c2-149">Aşağıdaki ASP.NET Core denetleyicisi Twitter bağlaması tarafından tetiklenen bir olayın işlenmesine bir örnek sağlar:</span><span class="sxs-lookup"><span data-stu-id="910c2-149">The following ASP.NET Core controller provides an example of handling an event triggered by the Twitter binding:</span></span>

```csharp
[ApiController]
public class SomeController : ControllerBase
{
    public class TwitterTweet
    {
        [JsonPropertyName("id_str")]
        public string ID {get; set; }

        [JsonPropertyName("text")]
        public string Text {get; set; }
    }

    [HttpPost("/tweet")]
    public ActionResult Post(TwitterTweet tweet)
    {
        // Handle tweet
        Console.WriteLine("Tweet received: {0}: {1}", tweet.ID, tweet.Text);

        // ...

        // Acknowledge message
        return Ok();
    }
}
```

<span data-ttu-id="910c2-150">İşlem hata içeriyorsa, uygun 400 veya 500 düzeyinde HTTP durum kodunu geri döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="910c2-150">If the operation should error, you would return the appropriate 400 or 500 level HTTP status code.</span></span> <span data-ttu-id="910c2-151">*En az bir kez teslim* garantisi sunan bağlamalar için, davpr sepet Tetikleyiciyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="910c2-151">For bindings that feature *at-least-once-delivery* guarantees, the Dapr sidecar will retry the trigger.</span></span> <span data-ttu-id="910c2-152">En *az bir kez* veya *tam bir kez* teslim garantisi sunmanın gerekip gerekmediğini görmek için [kaynak bağlamaları için davpr belgeleri] [1] göz atın.</span><span class="sxs-lookup"><span data-stu-id="910c2-152">Check out [Dapr documentation for resource bindings][1] to see whether they offer *at-least-once* or *exactly-once* delivery guarantees.</span></span>

### <a name="output-bindings"></a><span data-ttu-id="910c2-153">Çıkış bağlamaları</span><span class="sxs-lookup"><span data-stu-id="910c2-153">Output bindings</span></span>

<span data-ttu-id="910c2-154">Davpr Ayrıca *Çıkış bağlama* özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="910c2-154">Dapr also includes *output binding* capabilities.</span></span> <span data-ttu-id="910c2-155">Bunlar, hizmetinizin bir dış kaynağı çağıran bir olayı tetiklemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-155">They enable your service to trigger an event that invokes an external resource.</span></span> <span data-ttu-id="910c2-156">Yine, çıkış bağlamayı açıklayan bir bağlama yapılandırması YAML dosyası yapılandırarak başlar.</span><span class="sxs-lookup"><span data-stu-id="910c2-156">Again, you start by configuring a binding configuration YAML file that describes the output binding.</span></span> <span data-ttu-id="910c2-157">Bir kez daha olduktan sonra, uygulamanızın davpr sepet üzerinde Bindings API 'sini çağıran bir olayı tetiklersiniz.</span><span class="sxs-lookup"><span data-stu-id="910c2-157">Once in place, you trigger an event that invokes the bindings API on the Dapr sidecar of your application.</span></span> <span data-ttu-id="910c2-158">Şekil 8-3, çıkış bağlamasının akışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="910c2-158">Figure 8-3 shows the flow of an output binding:</span></span>

![Davpr çıkış bağlama akışı](media/bindings/output-binding-flow.png)

<span data-ttu-id="910c2-160">**Şekil 8-3**.</span><span class="sxs-lookup"><span data-stu-id="910c2-160">**Figure 8-3**.</span></span> <span data-ttu-id="910c2-161">Davpr çıkış bağlama akışı.</span><span class="sxs-lookup"><span data-stu-id="910c2-161">Dapr output binding flow.</span></span>

1. <span data-ttu-id="910c2-162">Davpr sepet, bağlama yapılandırma dosyasını dış kaynağa bağlanma hakkındaki bilgilerle okur.</span><span class="sxs-lookup"><span data-stu-id="910c2-162">The Dapr sidecar reads the binding configuration file with the information on how to connect to the external resource.</span></span> <span data-ttu-id="910c2-163">Örnekte, dış kaynak bir Twilio SMS hesabıdır.</span><span class="sxs-lookup"><span data-stu-id="910c2-163">In the example, the external resource is a Twilio SMS account.</span></span>
1. <span data-ttu-id="910c2-164">Uygulamanız, `/v1.0/bindings/sms` uç noktayı Davpr sidecar üzerinde çağırır.</span><span class="sxs-lookup"><span data-stu-id="910c2-164">Your application invokes the `/v1.0/bindings/sms` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="910c2-165">Bu durumda, API 'yi çağırmak için bir HTTP POST kullanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-165">In this case, it uses an HTTP POST to invoke the API.</span></span> <span data-ttu-id="910c2-166">GRPC kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="910c2-166">It's also possible to use gRPC.</span></span>
1. <span data-ttu-id="910c2-167">Davpr sepet içinde çalışan bağlama bileşeni, iletiyi göndermek için harici mesajlaşma sistemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="910c2-167">The binding component running in the Dapr sidecar calls the external messaging system to send the message.</span></span> <span data-ttu-id="910c2-168">İleti, POST isteğine geçirilen yükü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="910c2-168">The message will contain the payload passed in the POST request.</span></span>

<span data-ttu-id="910c2-169">Örnek olarak, kıvrımlı kullanarak bir çıkış bağlamayı çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="910c2-169">As an example, you can invoke an output binding by invoking the Dapr API using curl:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/bindings/sms \
  -H "Content-Type: application/json" \
  -d '{
        "data": "Welcome to this awesome service",
        "metadata": {
          "toNumber": "555-3277"
        },
        "operation": "create"
      }'
```

<span data-ttu-id="910c2-170">HTTP bağlantı noktasının, davpr sepet (Bu durumda, varsayılan davpr http bağlantı noktası) tarafından kullanılan ile aynı olduğunu unutmayın `3500` .</span><span class="sxs-lookup"><span data-stu-id="910c2-170">Note that the HTTP port is the same as used by the Dapr sidecar (in this case, the default Dapr HTTP port `3500`).</span></span>

<span data-ttu-id="910c2-171">Yükün (yani, gönderilen mesaj) yapısı, bağlama başına farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="910c2-171">The structure of the payload (that is, message sent) will vary per binding.</span></span> <span data-ttu-id="910c2-172">Yukarıdaki örnekte, yük `data` bir ileti içeren bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="910c2-172">In the example above, the payload contains a `data` element with a message.</span></span> <span data-ttu-id="910c2-173">Diğer dış kaynak türlerine olan bağlamalar, özellikle gönderilen meta veriler için farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-173">Bindings to other types of external resources can be different, especially for the metadata that is sent.</span></span> <span data-ttu-id="910c2-174">Her yük `operation` , bağlamanın yürütemeyeceği işlemi tanımlayan bir alan de içermelidir.</span><span class="sxs-lookup"><span data-stu-id="910c2-174">Each payload must also contain an `operation` field, that defines the operation the binding will execute.</span></span> <span data-ttu-id="910c2-175">Yukarıdaki örnekte `create` SMS iletisini oluşturan bir işlem belirtilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-175">The above example specifies a `create` operation that creates the SMS message.</span></span> <span data-ttu-id="910c2-176">Ortak işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="910c2-176">Common operations include:</span></span>

- <span data-ttu-id="910c2-177">oluşturmaya</span><span class="sxs-lookup"><span data-stu-id="910c2-177">create</span></span>
- <span data-ttu-id="910c2-178">get</span><span class="sxs-lookup"><span data-stu-id="910c2-178">get</span></span>
- <span data-ttu-id="910c2-179">silme</span><span class="sxs-lookup"><span data-stu-id="910c2-179">delete</span></span>
- <span data-ttu-id="910c2-180">list</span><span class="sxs-lookup"><span data-stu-id="910c2-180">list</span></span>

<span data-ttu-id="910c2-181">Bu, bağlamanın desteklediği işlemleri bağlayan bağlamanın yazarına kadar olur.</span><span class="sxs-lookup"><span data-stu-id="910c2-181">It's up to the author of the binding which operations the binding supports.</span></span> <span data-ttu-id="910c2-182">Her bağlamaya yönelik belgeler, kullanılabilir işlemleri ve bunların nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="910c2-182">The documentation for each binding describes the available operations and how to invoke them.</span></span>

## <a name="using-the-dapr-net-sdk"></a><span data-ttu-id="910c2-183">Davpr .NET SDK 'sını kullanma</span><span class="sxs-lookup"><span data-stu-id="910c2-183">Using the Dapr .NET SDK</span></span>

<span data-ttu-id="910c2-184">Davpr .NET SDK, .NET Core geliştiricileri için dile özgü destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="910c2-184">The Dapr .NET SDK provides language-specific support for .NET Core developers.</span></span> <span data-ttu-id="910c2-185">Aşağıdaki örnekte, öğesine yapılan çağrı `HttpClient.PostAsync()` `DaprClient.InvokeBindingAsync()` yöntemiyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="910c2-185">In the following example, the call to the `HttpClient.PostAsync()` is replaced with the `DaprClient.InvokeBindingAsync()` method.</span></span> <span data-ttu-id="910c2-186">Bu özelleştirilmiş Yöntem yapılandırılmış bir çıkış bağlamasını çağırma işlemini basitleştirir:</span><span class="sxs-lookup"><span data-stu-id="910c2-186">This specialized method simplifies invoking a configured output binding:</span></span>

```csharp
private async Task SendSMSAsync([FromServices] DaprClient daprClient)
{
    var message = "Welcome to this awesome service";
    var metadata = new Dictionary<string, string> 
    { 
      { "toNumber", "555-3277" } 
    };
    await daprClient.InvokeBindingAsync("sms", "create", message, metadata);
}
```

<span data-ttu-id="910c2-187">Yöntemi `metadata` ve `message` değerlerini bekler.</span><span class="sxs-lookup"><span data-stu-id="910c2-187">The method expects the `metadata` and `message` values.</span></span>

<span data-ttu-id="910c2-188">Bir bağlamayı çağırmak için kullanıldığında, `DaprClient` davpr sidecar üzerinde DAVPR API 'sini çağırmak Için gRPC 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-188">When used to invoke a binding, the `DaprClient` uses gRPC to call the Dapr API on the Dapr sidecar.</span></span>

## <a name="binding-components"></a><span data-ttu-id="910c2-189">Bileşenleri bağlama</span><span class="sxs-lookup"><span data-stu-id="910c2-189">Binding components</span></span>

<span data-ttu-id="910c2-190">Kaynak bağlamaları, aynı şekilde, Davpr bağlama bileşenleri ile uygulanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-190">Under the hood, resource bindings are implemented with Dapr binding components.</span></span> <span data-ttu-id="910c2-191">Bunlar, topluluk tarafından katkıda bulunuyoruz ve go 'da yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="910c2-191">They're contributed by the community and written in Go.</span></span> <span data-ttu-id="910c2-192">Henüz hiçbir Davpr bağlamasının olmadığı bir dış kaynakla tümleştirmeniz gerekiyorsa, kendiniz oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="910c2-192">If you need to integrate with an external resource for which no Dapr binding exists yet, you can create it yourself.</span></span> <span data-ttu-id="910c2-193">Bağlama nasıl katkıda bulunabileceğinizi görmek için, [Davpr bileşenleri-contrib depoya](https://github.com/dapr/components-contrib) göz atın.</span><span class="sxs-lookup"><span data-stu-id="910c2-193">Check out the [Dapr components-contrib repo](https://github.com/dapr/components-contrib) to see how you can contribute a binding.</span></span>

> [!NOTE]
> <span data-ttu-id="910c2-194">DAPR ve tüm bileşenleri [Golang](https://golang.org/) (go) dilinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="910c2-194">Dapr and all of its components are written in the [Golang](https://golang.org/) (Go) language.</span></span> <span data-ttu-id="910c2-195">Go, modern, bulutta yerel bir programlama platformu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-195">Go is considered a modern, cloud-native programming platform.</span></span>

<span data-ttu-id="910c2-196">YAML yapılandırma dosyası kullanarak bağlamaları yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="910c2-196">You configure bindings using a YAML configuration file.</span></span> <span data-ttu-id="910c2-197">Twitter bağlamasına yönelik örnek bir yapılandırma aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="910c2-197">Here's an example configuration for the Twitter binding:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: twitter-mention
  namespace: default
spec:
  type: bindings.twitter
  version: v1
  metadata:
  - name: consumerKey
    value: "****" # twitter api consumer key, required
  - name: consumerSecret
    value: "****" # twitter api consumer secret, required
  - name: accessToken
    value: "****" # twitter api access token, required
  - name: accessSecret
    value: "****" # twitter api access secret, required
  - name: query
    value: "dapr" # your search query, required
```

<span data-ttu-id="910c2-198">Her bağlama yapılandırması `metadata` `name` , ve alanı içeren genel bir öğesi içerir `namespace` .</span><span class="sxs-lookup"><span data-stu-id="910c2-198">Each binding configuration contains a general `metadata` element with a `name` and `namespace` field.</span></span> <span data-ttu-id="910c2-199">Davpr, yapılandırılmış alana göre hizmetinizi çağırmak için uç noktayı tespit eder `name` .</span><span class="sxs-lookup"><span data-stu-id="910c2-199">Dapr will determine the endpoint to invoke your service based upon the configured `name` field.</span></span> <span data-ttu-id="910c2-200">Yukarıdaki örnekte, Davpr bir olay gerçekleştiğinde hizmetinize açıklama eklenmiş yöntemi çağırır `/twitter-mention` .</span><span class="sxs-lookup"><span data-stu-id="910c2-200">In the above example, Dapr will invoke the method annotated with `/twitter-mention` in your service when an event occurs.</span></span>

<span data-ttu-id="910c2-201">Öğesinde, bağlamayı `spec` ve bağlamaya özel ' i belirtirsiniz `type` `metadata` .</span><span class="sxs-lookup"><span data-stu-id="910c2-201">In the `spec` element, you specify the `type` of the binding along with binding specific `metadata`.</span></span> <span data-ttu-id="910c2-202">Örnek, API 'sini kullanarak bir Twitter hesabına erişim için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="910c2-202">The example specifies credentials for accessing a Twitter account using its API.</span></span> <span data-ttu-id="910c2-203">Meta veriler, giriş ve çıkış bağlamaları arasında farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-203">The metadata can differ between input and output bindings.</span></span> <span data-ttu-id="910c2-204">Örneğin, Twitter 'yı bir giriş bağlama olarak kullanmak için, alanı kullanarak ara, arayanları aramak üzere metni belirtmeniz gerekir `query` .</span><span class="sxs-lookup"><span data-stu-id="910c2-204">For example, to use Twitter as an input binding, you need to specify the text to search for in tweets using the `query` field.</span></span> <span data-ttu-id="910c2-205">Eşleşen bir tweet her gönderildiğinde, davpr sepet `/twitter-mention` hizmette uç noktayı çağırır.</span><span class="sxs-lookup"><span data-stu-id="910c2-205">Every time a matching tweet is sent, the Dapr sidecar will invoke the `/twitter-mention` endpoint on the service.</span></span> <span data-ttu-id="910c2-206">Ayrıca, Tweet içeriğini de teslim eder.</span><span class="sxs-lookup"><span data-stu-id="910c2-206">It will also deliver the contents of the tweet.</span></span>

<span data-ttu-id="910c2-207">Bağlama, giriş, çıkış veya her ikisi için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-207">A binding can be configured for input, output, or both.</span></span> <span data-ttu-id="910c2-208">Intergelme, bağlama açıkça giriş veya çıkış yapılandırması belirtmez.</span><span class="sxs-lookup"><span data-stu-id="910c2-208">Interestingly, the binding doesn't explicitly specify input or output configuration.</span></span> <span data-ttu-id="910c2-209">Bunun yerine, yönü yapılandırma değerleriyle birlikte bağlamanın kullanımı tarafından algılanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-209">Instead, the direction is inferred by the usage of the binding along with configuration values.</span></span>

<span data-ttu-id="910c2-210">[1] kaynak bağlamaları için [Davpr belgeleri, kullanılabilir bağlamaların ve bunlara özgü yapılandırma ayarlarının tamamen bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="910c2-210">The [Dapr documentation for resource bindings][1] provides a complete list of the available bindings and their specific configuration settings.</span></span>

### <a name="cron-binding"></a><span data-ttu-id="910c2-211">Cron bağlama</span><span class="sxs-lookup"><span data-stu-id="910c2-211">Cron binding</span></span>

<span data-ttu-id="910c2-212">Davpr 'nin cron bağlamasının dikkatini hemen ödeyin.</span><span class="sxs-lookup"><span data-stu-id="910c2-212">Pay close attention to Dapr's Cron binding.</span></span> <span data-ttu-id="910c2-213">Bir dış sistemden olaylara abone olmaz.</span><span class="sxs-lookup"><span data-stu-id="910c2-213">It doesn't subscribe to events from an external system.</span></span> <span data-ttu-id="910c2-214">Bunun yerine, bu bağlama uygulamanızı tetiklemek için yapılandırılabilir bir Aralık zamanlaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-214">Instead, this binding uses a configurable interval schedule to trigger your application.</span></span> <span data-ttu-id="910c2-215">Bağlama, bir arka plan çalışanını daha sonra, bir zaman için, yapılandırılabilir bir gecikmeyle sonsuz bir döngüye uygulama gerekmeden, bir arka plan çalışanı uygulamak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="910c2-215">The binding provides a simple way to implement a background worker to wake up and do some work at a regular interval, without the need to implement an endless loop with a configurable delay.</span></span> <span data-ttu-id="910c2-216">Bir cron bağlama yapılandırmasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="910c2-216">Here's an example of a Cron binding configuration:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: checkOrderBacklog
  namespace: default
spec:
  type: bindings.cron
  version: v1
  metadata:
  - name: schedule
    value: "@every 30m"
```

<span data-ttu-id="910c2-217">Bu örnekte, Davpr, `/checkOrderBacklog` uç noktayı her 30 dakikada bir çağırarak bir hizmeti tetikler.</span><span class="sxs-lookup"><span data-stu-id="910c2-217">In this example, Dapr triggers a service by invoking the `/checkOrderBacklog` endpoint every 30 minutes.</span></span> <span data-ttu-id="910c2-218">Değer belirtmek için kullanılabilecek çeşitli desenler vardır `schedule` .</span><span class="sxs-lookup"><span data-stu-id="910c2-218">There are several patterns available for specifying the `schedule` value.</span></span> <span data-ttu-id="910c2-219">Daha fazla bilgi için [cron bağlama belgelerine](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/)bakın.</span><span class="sxs-lookup"><span data-stu-id="910c2-219">For more information, see the [Cron binding documentation](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/).</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="910c2-220">Başvuru uygulaması: Eshopondadpr</span><span class="sxs-lookup"><span data-stu-id="910c2-220">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="910c2-221">Eşlik eden Eshopondadpr başvuru uygulaması, çıkış bağlama örneği uygular.</span><span class="sxs-lookup"><span data-stu-id="910c2-221">The accompanying eShopOnDapr reference application implements an output binding example.</span></span> <span data-ttu-id="910c2-222">Yeni bir sipariş yerleştirildiğinde kullanıcıya bir e-posta göndermek için DAPR [SendGrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) bağlamasını tetikler.</span><span class="sxs-lookup"><span data-stu-id="910c2-222">It triggers the Dapr [SendGrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) binding to send a user an email when a new order is placed.</span></span> <span data-ttu-id="910c2-223">Bu bağlamayı `eshop-email.yaml` dosya içinde bileşenler klasöründe bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="910c2-223">You can find this binding in the `eshop-email.yaml` file in the components folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: sendmail
  namespace: eshop
spec:
  type: bindings.twilio.sendgrid
  version: v1
  metadata:
  - name: apiKey
    secretKeyRef:
      name: sendGridAPIKey
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="910c2-224">Bu yapılandırma [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) bağlama bileşenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-224">This configuration uses the [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) binding component.</span></span> <span data-ttu-id="910c2-225">Hizmetine bağlanmak için API anahtarının bir Davpr gizli başvurusu kullandığını aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="910c2-225">Note how the API key for connecting to the service consumes a Dapr secret reference.</span></span> <span data-ttu-id="910c2-226">Bu yaklaşım, yapılandırma dosyasının dışında gizli dizileri tutar.</span><span class="sxs-lookup"><span data-stu-id="910c2-226">This approach keeps secrets outside of the configuration file.</span></span> <span data-ttu-id="910c2-227">Davpr gizli dizileri hakkında daha fazla bilgi edinmek için [gizli dizi derleme bloğu](secrets.md) bölümünü okuyun.</span><span class="sxs-lookup"><span data-stu-id="910c2-227">Read the [secrets building block chapter](secrets.md) to learn more about Dapr secrets.</span></span>

<span data-ttu-id="910c2-228">Bağlama yapılandırması, `/sendmail` Davpr sidecar üzerinde uç nokta kullanılarak çağrılabilecek bir bağlama bileşeni belirtir.</span><span class="sxs-lookup"><span data-stu-id="910c2-228">The binding configuration specifies a binding component that can be invoked using the `/sendmail` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="910c2-229">Aşağıda, bir sipariş her başlatıldığında e-postanın gönderildiği bir kod parçacığı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="910c2-229">Here's a code snippet in which an email is sent whenever an order is started:</span></span>

```csharp
public Task Handle(OrderStartedDomainEvent notification, CancellationToken cancellationToken)
{
    var string message = CreateEmailBody(notification);
    var metadata = new Dictionary<string, string>
    { 
        {"emailFrom", "eShopOn@dapr.io"},
        {"emailTo", notification.UserName},
        {"subject", $"Your eShopOnDapr order #{notification.Order.Id}"}
    };
    return _daprClient.InvokeBindingAsync("sendmail", "create", message, metadata, cancellationToken);
}
```

<span data-ttu-id="910c2-230">Bu örnekte gördüğünüz gibi, `message` ileti gövdesini içerir.</span><span class="sxs-lookup"><span data-stu-id="910c2-230">As you can see in this example, `message` contains the message body.</span></span> <span data-ttu-id="910c2-231">`CreateEmailBody`Yöntemi yalnızca gövde metniyle bir dizeyi biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="910c2-231">The `CreateEmailBody` method simply formats a string with the body text.</span></span> <span data-ttu-id="910c2-232">E-posta `metadata` Göndericisini, alıcıyı ve e-posta iletisinin konusunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="910c2-232">The `metadata` specifies the email sender, recipient, and the subject for the email message.</span></span> <span data-ttu-id="910c2-233">Bu değerler statikse, yapılandırma dosyasındaki meta veri alanlarına da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="910c2-233">If these values are static, they can also be included in the metadata fields in the configuration file.</span></span> <span data-ttu-id="910c2-234">Çağrılacak bağlamanın adı `sendmail` ve işlem `create` .</span><span class="sxs-lookup"><span data-stu-id="910c2-234">The name of the binding to invoke is `sendmail` and the operation is `create`.</span></span>

## <a name="summary"></a><span data-ttu-id="910c2-235">Özet</span><span class="sxs-lookup"><span data-stu-id="910c2-235">Summary</span></span>

<span data-ttu-id="910c2-236">Davpr kaynak bağlamaları, kitaplıkları veya SDK 'lerinde bağımlılıklar almadan farklı dış kaynaklarla ve sistemlerle tümleştirmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-236">Dapr resource bindings enable you to integrate with different external resources and systems without taking dependencies on their libraries or SDKs.</span></span> <span data-ttu-id="910c2-237">Bu dış sistemlerin hizmet veri yolu veya ileti Aracısı gibi mesajlaşma sistemleri olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="910c2-237">These external systems don't necessarily have to be messaging systems like a service bus or message broker.</span></span> <span data-ttu-id="910c2-238">Veri depoları ve Twitter ya da SendGrid gibi Web kaynakları için bağlamalar de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="910c2-238">Bindings also exist for datastores and web resources like Twitter or SendGrid.</span></span>

<span data-ttu-id="910c2-239">Giriş bağlamaları (veya Tetikleyicileri), bir dış sistemde gerçekleşen olaylara tepki verir.</span><span class="sxs-lookup"><span data-stu-id="910c2-239">Input bindings (or triggers) react to events occurring in an external system.</span></span> <span data-ttu-id="910c2-240">Uygulamanızda önceden yapılandırılmış genel HTTP uç noktalarını çağırır.</span><span class="sxs-lookup"><span data-stu-id="910c2-240">They invoke the public HTTP endpoints pre-configured in your application.</span></span> <span data-ttu-id="910c2-241">Davpr, uygulamanızda çağrılacak uç noktayı öğrenmek için yapılandırmadaki bağlamanın adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-241">Dapr uses the name of the binding in the configuration to determine the endpoint to call in your application.</span></span>

<span data-ttu-id="910c2-242">Çıkış bağlamaları, bir dış sisteme iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="910c2-242">Output bindings will send messages to an external system.</span></span> <span data-ttu-id="910c2-243">Bir çıkış bağlamayı `/v1.0/bindings/<binding-name>` , Davpr sidecar üzerindeki uç noktada BIR http gönderisi yaparak tetiklersiniz.</span><span class="sxs-lookup"><span data-stu-id="910c2-243">You trigger an output binding by doing an HTTP POST on the `/v1.0/bindings/<binding-name>` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="910c2-244">Ayrıca, bağlamayı çağırmak için gRPC 'yi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="910c2-244">You can also use gRPC to invoke the binding.</span></span> <span data-ttu-id="910c2-245">.NET SDK, `InvokeBindingAsync` gRPC kullanarak Davpr bağlamalarını çağırmak için bir yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="910c2-245">The .NET SDK offers a `InvokeBindingAsync` method to invoke Dapr bindings using gRPC.</span></span>

<span data-ttu-id="910c2-246">Bir bağlantı, bir Davpr bileşeniyle birlikte uygulanır.</span><span class="sxs-lookup"><span data-stu-id="910c2-246">You implement a binding with a Dapr component.</span></span> <span data-ttu-id="910c2-247">Bu bileşenler, topluluk tarafından katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="910c2-247">These components are contributed by the community.</span></span> <span data-ttu-id="910c2-248">Her bağlama bileşeninin yapılandırmasında, soyutlayan dış sisteme özgü meta veriler bulunur.</span><span class="sxs-lookup"><span data-stu-id="910c2-248">Each binding component's configuration has metadata that is specific for the external system it abstracts.</span></span> <span data-ttu-id="910c2-249">Ayrıca, desteklediği komutlar ve yük yapısı bağlama bileşenine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="910c2-249">Also, the commands it supports and the structure of the payload will differ per binding component.</span></span>

### <a name="references"></a><span data-ttu-id="910c2-250">Başvurular</span><span class="sxs-lookup"><span data-stu-id="910c2-250">References</span></span>

- [<span data-ttu-id="910c2-251">Kaynak bağlamaları için davpr belgeleri</span><span class="sxs-lookup"><span data-stu-id="910c2-251">Dapr documentation for resource bindings</span></span>](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/)

>[!div class="step-by-step"]
><span data-ttu-id="910c2-252">[Önceki](publish-subscribe.md) 
> [Sonraki](observability.md)</span><span class="sxs-lookup"><span data-stu-id="910c2-252">[Previous](publish-subscribe.md)
[Next](observability.md)</span></span>
