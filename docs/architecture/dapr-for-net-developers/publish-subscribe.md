---
title: Davpr yayımlama & abonelik oluşturma bloğu
description: '& abonelik oluşturma-bloğunun ve bu uygulamayı nasıl uygulayacağınız için bir açıklama'
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 3d00c5a3171dd5a7287d07675f5a3742697e784b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258006"
---
# <a name="the-dapr-publish--subscribe-building-block"></a><span data-ttu-id="828c9-103">Davpr yayımlama & abonelik oluşturma bloğu</span><span class="sxs-lookup"><span data-stu-id="828c9-103">The Dapr publish & subscribe building block</span></span>

<span data-ttu-id="828c9-104">[Yayımla-abone ol](/azure/architecture/patterns/publisher-subscriber) (genellikle "pub/Sub" olarak adlandırılır), iyi bilinen ve yaygın olarak kullanılan bir mesajlaşma modelidir.</span><span class="sxs-lookup"><span data-stu-id="828c9-104">The [Publish-Subscribe pattern](/azure/architecture/patterns/publisher-subscriber) (often referred to as "pub/sub") is a well-known and widely used messaging pattern.</span></span> <span data-ttu-id="828c9-105">Mimarlar, dağıtılmış uygulamalarda yaygın olarak bu şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-105">Architects commonly embrace it in distributed applications.</span></span> <span data-ttu-id="828c9-106">Ancak, bunu uygulamak için bir sıhhi tesisat karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-106">However, the plumbing to implement it can be complex.</span></span> <span data-ttu-id="828c9-107">Farklı mesajlaşma ürünleri arasında genellikle hafif özellik farklılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="828c9-107">There are often subtle feature differences across different messaging products.</span></span> <span data-ttu-id="828c9-108">Davpr, yayın/alt işlevleri uygulamayı önemli ölçüde kolaylaştıran bir yapı taşı sunar.</span><span class="sxs-lookup"><span data-stu-id="828c9-108">Dapr offers a building block that significantly simplifies implementing pub/sub functionality.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="828c9-109">Ne çözdüğü</span><span class="sxs-lookup"><span data-stu-id="828c9-109">What it solves</span></span>

<span data-ttu-id="828c9-110">Publish-Subscribe deseninin birincil avantajı, bazen zamana bağlı [ayırma olarak adlandırılan](/azure/architecture/guide/technology-choices/messaging#decoupling) **gevşek** bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="828c9-110">The primary advantage of the Publish-Subscribe pattern is **loose coupling**, sometimes referred to as [temporal decoupling](/azure/architecture/guide/technology-choices/messaging#decoupling).</span></span> <span data-ttu-id="828c9-111">Model, iletileri ( **aboneler**) kullanan hizmetlerden iletiler ( **yayımcılar**) Gönderen Hizmetleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-111">The pattern decouples services that send messages (the **publishers**) from services that consume messages (the **subscribers**).</span></span> <span data-ttu-id="828c9-112">Hem yayımcılar hem de aboneler birbirleriyle uyumlu değildir, her ikisi de iletileri dağıtan merkezi bir **ileti aracısına** bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="828c9-112">Both publishers and subscribers are unaware of each other - both are dependent on a centralized **message broker** that distributes the messages.</span></span>

<span data-ttu-id="828c9-113">Şekil 7-1, pub/Sub deseninin üst düzey mimarisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="828c9-113">Figure 7-1 shows the high-level architecture of the pub/sub pattern.</span></span>

![Yayın/alt model](./media/publish-subscribe/pub-sub-pattern.png)

<span data-ttu-id="828c9-115">**Şekil 7-1**.</span><span class="sxs-lookup"><span data-stu-id="828c9-115">**Figure 7-1**.</span></span> <span data-ttu-id="828c9-116">Yayın/alt model.</span><span class="sxs-lookup"><span data-stu-id="828c9-116">The pub/sub pattern.</span></span>

<span data-ttu-id="828c9-117">Önceki şekilden, düzenin adımlarını aklınızda bir değer:</span><span class="sxs-lookup"><span data-stu-id="828c9-117">From the previous figure, note the steps of the pattern:</span></span>

1. <span data-ttu-id="828c9-118">Yayımcılar ileti aracısına iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="828c9-118">Publishers send messages to the message broker.</span></span>
1. <span data-ttu-id="828c9-119">Aboneler ileti aracısıdır bir aboneliğe bağlanır.</span><span class="sxs-lookup"><span data-stu-id="828c9-119">Subscribers bind to a subscription on the message broker.</span></span>
1. <span data-ttu-id="828c9-120">İleti Aracısı iletinin bir kopyasını ilgi aboneliklerine iletir.</span><span class="sxs-lookup"><span data-stu-id="828c9-120">The message broker forwards a copy of the message to interested subscriptions.</span></span>
1. <span data-ttu-id="828c9-121">Aboneler aboneliklerinden iletileri tüketir.</span><span class="sxs-lookup"><span data-stu-id="828c9-121">Subscribers consume messages from their subscriptions.</span></span>

<span data-ttu-id="828c9-122">Çoğu ileti aracıları, alındıktan sonra iletileri kalıcı hale getirebileceği bir sıraya alma mekanizması kapsülleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-122">Most message brokers encapsulate a queueing mechanism that can persist messages once received.</span></span> <span data-ttu-id="828c9-123">Bu, ileti Aracısı iletiyi depolayarak **dayanıklılığı** güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="828c9-123">With it, the message broker guarantees **durability** by storing the message.</span></span> <span data-ttu-id="828c9-124">Bir yayımcı bir ileti gönderdiğinde abonelerin hemen kullanılabilir veya hatta çevrimiçi olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="828c9-124">Subscribers don't need to be immediately available or even online when a publisher sends a message.</span></span> <span data-ttu-id="828c9-125">Bir kez varsa, abone iletiyi alır ve işler.</span><span class="sxs-lookup"><span data-stu-id="828c9-125">Once available, the subscriber receives and processes the message.</span></span>  <span data-ttu-id="828c9-126">Davpr ileti teslimi için **en az bir kez** semantiğini garanti eder.</span><span class="sxs-lookup"><span data-stu-id="828c9-126">Dapr guarantees **At-Least-Once** semantics for message delivery.</span></span> <span data-ttu-id="828c9-127">Bir ileti yayımlandıktan sonra, ilgili aboneye en az bir kez gönderilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-127">Once a message is published, it will be delivered at least once to any interested subscriber.</span></span>

 > <span data-ttu-id="828c9-128">Hizmetiniz yalnızca bir iletiyi bir kez işleyebilir, aynı iletinin birden çok kez işlenmemesini sağlamak için bir [Ise denetimi](/azure/architecture/microservices/design/api-design#idempotent-operations) sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-128">If your service can only process a message once, you'll need to provide an [idempotency check](/azure/architecture/microservices/design/api-design#idempotent-operations) to ensure that the same message is not processed multiple times.</span></span> <span data-ttu-id="828c9-129">Böyle bir mantık kodlanırken, Azure Service Bus gibi bazı ileti aracıları yerleşik olarak *yinelenen algılama* mesajlaşma özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-129">While such logic can be coded, some message brokers, such as Azure Service Bus, provide built-in *duplicate detection* messaging capabilities.</span></span>

<span data-ttu-id="828c9-130">Hem ticari hem de açık kaynaklı çeşitli ileti Aracısı ürünleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="828c9-130">There are several message broker products available - both commercially and open-source.</span></span> <span data-ttu-id="828c9-131">Her birinin avantajları ve dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="828c9-131">Each has advantages and drawbacks.</span></span> <span data-ttu-id="828c9-132">İşiniz, sistem gereksinimlerinizi uygun aracı ile eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="828c9-132">Your job is to match your system requirements to the appropriate broker.</span></span> <span data-ttu-id="828c9-133">Seçildiğinde, uygulamanızı ileti Aracısı sıhhi bir şekilde ayırmak en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="828c9-133">Once selected, it's a best practice to decouple your application from message broker plumbing.</span></span> <span data-ttu-id="828c9-134">Aracıyı bir *soyutlama* içinde sarmalayarak bu işlevselliği elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-134">You achieve this functionality by wrapping the broker inside an *abstraction*.</span></span> <span data-ttu-id="828c9-135">Soyutlama, ileti sıhhi tesisat düzeyini kapsüller ve kodunuza genel yayın/alt işlemleri sunar.</span><span class="sxs-lookup"><span data-stu-id="828c9-135">The abstraction encapsulates the message plumbing and exposes generic pub/sub operations to your code.</span></span> <span data-ttu-id="828c9-136">Kodunuz gerçek ileti aracısıdır değil soyutlama ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="828c9-136">Your code communicates with the abstraction, not the actual message broker.</span></span> <span data-ttu-id="828c9-137">Bir Wise kararı verirken, soyutlamayı ve onun temelindeki uygulamayı yazmanız ve korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-137">While a wise decision, you'll have to write and maintain the abstraction and its underlying implementation.</span></span> <span data-ttu-id="828c9-138">Bu yaklaşım karmaşık, yinelenen ve hataya açık olabilecek özel kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="828c9-138">This approach requires custom code that can be complex, repetitive, and error-prone.</span></span>

<span data-ttu-id="828c9-139">Davpr Yayımla & abone ol yapı taşı, mesajlaşma soyutlamasını ve kullanıma hazır uygulamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-139">The Dapr publish & subscribe building block provides the messaging abstraction and implementation out-of-the-box.</span></span> <span data-ttu-id="828c9-140">Yazmak zorunda olduğunuz özel kod, Davpr yapı bloğunun içinde önceden oluşturulup kapsüllenir.</span><span class="sxs-lookup"><span data-stu-id="828c9-140">The custom code you would have had to write is prebuilt and encapsulated inside the Dapr building block.</span></span> <span data-ttu-id="828c9-141">Bağlayın ve onu kullanın.</span><span class="sxs-lookup"><span data-stu-id="828c9-141">You bind to it and consume it.</span></span> <span data-ttu-id="828c9-142">İleti sıhhi tesisat kodu yazmak yerine siz ve takımınız, müşterilerinize değer ekleyen iş işlevleri oluşturmaya odaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="828c9-142">Instead of writing messaging plumbing code, you and your team focus on creating business functionality that adds value to your customers.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="828c9-143">Nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="828c9-143">How it works</span></span>

<span data-ttu-id="828c9-144">Davpr Publish & Subscribe yapı taşı, ileti göndermek ve almak için platformdan bağımsız bir API altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-144">The Dapr publish & subscribe building block provides a platform-agnostic API framework to send and receive messages.</span></span> <span data-ttu-id="828c9-145">Hizmetleriniz bir adlandırılmış [konuya](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions)ileti yayımlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-145">Your services publish messages to a named [topic](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions).</span></span> <span data-ttu-id="828c9-146">Hizmetleriniz iletileri tüketmek için bir konuya abone olur.</span><span class="sxs-lookup"><span data-stu-id="828c9-146">Your services subscribe to a topic to consume messages.</span></span>

<span data-ttu-id="828c9-147">Hizmet, Davpr sidecar üzerinde pub/Sub API 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-147">The service calls the pub/sub API on the Dapr sidecar.</span></span> <span data-ttu-id="828c9-148">Sonra sepet, belirli bir ileti Aracısı ürününü kapsülleyen önceden tanımlanmış bir Davpr pub/Sub bileşenine çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="828c9-148">The sidecar then makes calls into a pre-defined Dapr pub/sub component that encapsulates a specific message broker product.</span></span> <span data-ttu-id="828c9-149">Şekil 7-2, Davpr pub/Sub mesajlaşma yığınını gösterir.</span><span class="sxs-lookup"><span data-stu-id="828c9-149">Figure 7-2 shows the Dapr pub/sub messaging stack.</span></span>

![Yayın/alt yığın](./media/publish-subscribe/pub-sub-buildingblock.png)

<span data-ttu-id="828c9-151">**Şekil 7-2**.</span><span class="sxs-lookup"><span data-stu-id="828c9-151">**Figure 7-2**.</span></span> <span data-ttu-id="828c9-152">Davpr yayımlama/alt yığını.</span><span class="sxs-lookup"><span data-stu-id="828c9-152">The Dapr pub/sub stack.</span></span>

<span data-ttu-id="828c9-153">Davpr Publish & Subscribe derleme bloğu birçok şekilde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-153">The Dapr publish & subscribe building block can be invoked in many ways.</span></span>

<span data-ttu-id="828c9-154">En düşük düzeyde, tüm programlama platformları, **Davpr NATIVE API**'SINI kullanarak http veya GRPC üzerinden yapı bloğunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-154">At the lowest level, any programming platform can invoke the building block over HTTP or gRPC using the **Dapr native API**.</span></span> <span data-ttu-id="828c9-155">Bir ileti yayımlamak için aşağıdaki API çağrısını yaparsınız:</span><span class="sxs-lookup"><span data-stu-id="828c9-155">To publish a message, you make the following API call:</span></span>

``` http
http://localhost:<dapr-port>/v1.0/publish/<pub-sub-name>/<topic>
```

<span data-ttu-id="828c9-156">Yukarıdaki çağrıda birkaç Davpr özel URL kesimi vardır:</span><span class="sxs-lookup"><span data-stu-id="828c9-156">There are several Dapr specific URL segments in the above call:</span></span>

- <span data-ttu-id="828c9-157">`<dapr-port>` , davpr sepet 'nin dinlediği bağlantı noktası numarasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-157">`<dapr-port>` provides the port number upon which the Dapr sidecar is listening.</span></span>
- <span data-ttu-id="828c9-158">`<pub-sub-name>` Seçilen Davpr pub/Sub bileşeninin adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-158">`<pub-sub-name>` provides the name of the selected Dapr pub/sub component.</span></span>
- <span data-ttu-id="828c9-159">`<topic>` iletinin yayımlandığı konunun adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-159">`<topic>` provides the name of the topic to which the message is published.</span></span>

<span data-ttu-id="828c9-160">Bir iletiyi yayımlamak için *kıvrımlı* komut satırı aracını kullanarak, bunu deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="828c9-160">Using the *curl* command-line tool to publish a message, you can try it out:</span></span>

``` curl
curl -X POST http://localhost:3500/v1.0/publish/pubsub/newOrder \
  -H "Content-Type: application/json" \
  -d '{ "orderId": "1234", "productId": "5678", "amount": 2 }'
```

<span data-ttu-id="828c9-161">Bir konuya abone olarak ileti alırsınız.</span><span class="sxs-lookup"><span data-stu-id="828c9-161">You receive messages by subscribing to a topic.</span></span> <span data-ttu-id="828c9-162">Başlangıç sırasında, Davpr çalışma zamanı, gerekli abonelikleri belirlemek ve oluşturmak için uygulamayı iyi bilinen bir uç noktada çağırır:</span><span class="sxs-lookup"><span data-stu-id="828c9-162">At startup, the Dapr runtime will call the application on a well-known endpoint to identify and create the required subscriptions:</span></span>

``` http
http://localhost:<appPort>/dapr/subscribe
```

- <span data-ttu-id="828c9-163">`<appPort>` uygulamanın dinlediği bağlantı noktasının Davpr dışarıdan arabası olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="828c9-163">`<appPort>` informs the Dapr sidecar of the port upon which the application is listening.</span></span>

<span data-ttu-id="828c9-164">Bu uç noktayı kendiniz uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-164">You can implement this endpoint yourself.</span></span> <span data-ttu-id="828c9-165">Ancak, Davpr bunu uygulamaya yönelik daha sezgisel yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="828c9-165">But Dapr provides more intuitive ways of implementing it.</span></span> <span data-ttu-id="828c9-166">Bu işlevselliği daha sonra bu bölümde ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="828c9-166">We'll address this functionality later in this chapter.</span></span>

<span data-ttu-id="828c9-167">Çağrıdan gelen yanıt, uygulamaların abone olacağı konuların bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="828c9-167">The response from the call contains a list of topics to which the applications will subscribe.</span></span> <span data-ttu-id="828c9-168">, Konusu bir ileti aldığında çağrılacak bir uç nokta içerir.</span><span class="sxs-lookup"><span data-stu-id="828c9-168">Each includes an endpoint to call when the topic receives a message.</span></span> <span data-ttu-id="828c9-169">Yanıt örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="828c9-169">Here's an example of a response:</span></span>

```json
[
  {
    "pubsubname": "pubsub",
    "topic": "newOrder",
    "route": "/orders"
  },
  {
    "pubsubname": "pubsub",
    "topic": "newProduct",
    "route": "/productCatalog/products"
  }
]
```

<span data-ttu-id="828c9-170">JSON yanıtında, uygulamanın konulara ve konuların abone olmak istediğini görebilirsiniz `newOrder` `newProduct` .</span><span class="sxs-lookup"><span data-stu-id="828c9-170">In the JSON response, you can see the application wants to subscribe to topics `newOrder` and `newProduct`.</span></span> <span data-ttu-id="828c9-171">Sırasıyla uç noktaları `/orders` ve `/productCatalog/products` her biri için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="828c9-171">It registers the endpoints `/orders` and `/productCatalog/products` for each, respectively.</span></span> <span data-ttu-id="828c9-172">Her iki abonelik için de uygulama, adlı bir Davpr bileşenine bağlanıyor `pubsub` .</span><span class="sxs-lookup"><span data-stu-id="828c9-172">For both subscriptions, the application is binding to the Dapr component named `pubsub`.</span></span>

<span data-ttu-id="828c9-173">Şekil 7-3, örneğin akışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="828c9-173">Figure 7-3 presents the flow of the example.</span></span>

![Davpr ile örnek yayın/alt akış](media/publish-subscribe/pub-sub-flow.png)

<span data-ttu-id="828c9-175">**Şekil 7-3**.</span><span class="sxs-lookup"><span data-stu-id="828c9-175">**Figure 7-3**.</span></span> <span data-ttu-id="828c9-176">Davpr ile yayımlama/alt akış.</span><span class="sxs-lookup"><span data-stu-id="828c9-176">pub/sub flow with Dapr.</span></span>

<span data-ttu-id="828c9-177">Önceki şekilde, akışa göz önünde bulunan:</span><span class="sxs-lookup"><span data-stu-id="828c9-177">From the previous figure, note the flow:</span></span>

1. <span data-ttu-id="828c9-178">Hizmet B için bir Davpr sepet `/dapr/subscribe` uç noktasını, hizmet b 'den (tüketici) çağırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-178">The Dapr sidecar for Service B calls the `/dapr/subscribe` endpoint from Service B (the consumer).</span></span> <span data-ttu-id="828c9-179">Hizmet, oluşturmak istediği abonelikler ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="828c9-179">The service responds with the subscriptions it wants to create.</span></span>
1. <span data-ttu-id="828c9-180">Hizmet B için Davpr sepet, ileti aracısıdır istenen abonelikleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="828c9-180">The Dapr sidecar for Service B creates the requested subscriptions on the message broker.</span></span>
1. <span data-ttu-id="828c9-181">A hizmeti `/v1.0/publish/<pub-sub-name>/<topic>` , vapr hizmeti bir sepet olan uç noktada bir ileti yayımlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-181">Service A publishes a message at the `/v1.0/publish/<pub-sub-name>/<topic>` endpoint on the Dapr Service A sidecar.</span></span>
1. <span data-ttu-id="828c9-182">Bir sepet hizmeti iletiyi ileti aracısına yayınlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-182">The Service A sidecar publishes the message to the message broker.</span></span>
1. <span data-ttu-id="828c9-183">İleti Aracısı, iletinin bir kopyasını hizmet B araç çubuğu 'na gönderir.</span><span class="sxs-lookup"><span data-stu-id="828c9-183">The message broker sends a copy of the message to the Service B sidecar.</span></span>
1. <span data-ttu-id="828c9-184">Hizmet B araç çubuğu, B hizmetinde aboneliğe (Bu durumda) karşılık gelen uç noktayı çağırır `/orders` . Hizmet bir HTTP durum kodu ile yanıt verir `200 OK` , böylece sepet iletiyi başarıyla işlendiği şekilde kabul eder.</span><span class="sxs-lookup"><span data-stu-id="828c9-184">The Service B sidecar calls the endpoint corresponding to the subscription (in this case `/orders`) on Service B. The service responds with an HTTP status-code `200 OK` so the sidecar will consider the message as being handled successfully.</span></span>

<span data-ttu-id="828c9-185">Örnekte ileti başarıyla işlenir.</span><span class="sxs-lookup"><span data-stu-id="828c9-185">In the example, the message is handled successfully.</span></span> <span data-ttu-id="828c9-186">Ancak, hizmet B isteği gerçekleştirirken bir sorun ortaya geçtiğinde, iletiyle ne olması gerektiğini belirtmek için yanıtı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-186">But if something goes wrong while Service B is handling the request, it can use the response to specify what needs to happen with the message.</span></span> <span data-ttu-id="828c9-187">Bir HTTP durum kodu döndürdüğünde bir `404` hata günlüğe kaydedilir ve ileti bırakılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-187">When it returns an HTTP status-code `404`, an error is logged and the message is dropped.</span></span> <span data-ttu-id="828c9-188">Ya da diğer herhangi bir durum kodu `200` ile `404` , bir uyarı günlüğe kaydedilir ve ileti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="828c9-188">With any other status-code than `200` or `404`, a warning is logged and the message is retried.</span></span> <span data-ttu-id="828c9-189">Alternatif olarak, hizmet B, yanıt gövdesine bir JSON yükü ekleyerek, iletiyle ne olması gerektiğini açıkça belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="828c9-189">Alternatively, Service B can explicitly specify what needs to happen with the message by including a JSON payload in the body of the response:</span></span>

```json
{
  "status": "<status>"
}
```

<span data-ttu-id="828c9-190">Aşağıdaki tabloda kullanılabilir `status` değerler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="828c9-190">The following table shows the available `status` values:</span></span>

| <span data-ttu-id="828c9-191">Durum</span><span class="sxs-lookup"><span data-stu-id="828c9-191">Status</span></span>           | <span data-ttu-id="828c9-192">Eylem</span><span class="sxs-lookup"><span data-stu-id="828c9-192">Action</span></span>                                                       |
| ---------------- | ------------------------------------------------------------ |
| <span data-ttu-id="828c9-193">BAŞARıLı</span><span class="sxs-lookup"><span data-stu-id="828c9-193">SUCCESS</span></span>          | <span data-ttu-id="828c9-194">İleti başarıyla işlendi ve bırakıldı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-194">The message is considered as processed successfully and dropped.</span></span> |
| <span data-ttu-id="828c9-195">RETRY</span><span class="sxs-lookup"><span data-stu-id="828c9-195">RETRY</span></span>            | <span data-ttu-id="828c9-196">İleti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="828c9-196">The message is retried.</span></span>                                      |
| <span data-ttu-id="828c9-197">DROP</span><span class="sxs-lookup"><span data-stu-id="828c9-197">DROP</span></span>             | <span data-ttu-id="828c9-198">Günlüğe bir uyarı kaydedilir ve ileti bırakılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-198">A warning is logged and the message is dropped.</span></span>              |
| <span data-ttu-id="828c9-199">Başka herhangi bir durum</span><span class="sxs-lookup"><span data-stu-id="828c9-199">Any other status</span></span> | <span data-ttu-id="828c9-200">İleti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="828c9-200">The message is retried.</span></span>                                      |

### <a name="competing-consumers"></a><span data-ttu-id="828c9-201">Rekabet müşterileri</span><span class="sxs-lookup"><span data-stu-id="828c9-201">Competing consumers</span></span>

<span data-ttu-id="828c9-202">Bir konuya abone olan bir uygulamayı ölçeklendirirken, rekabet eden tüketicilerle uğraşmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-202">When scaling out an application that subscribes to a topic, you have to deal with competing consumers.</span></span> <span data-ttu-id="828c9-203">Yalnızca bir uygulama örneği, konuya gönderilen bir iletiyi işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="828c9-203">Only one application instance should handle a message sent to the topic.</span></span> <span data-ttu-id="828c9-204">Luckily, Davpr bu sorunu işler.</span><span class="sxs-lookup"><span data-stu-id="828c9-204">Luckily, Dapr handles that problem.</span></span> <span data-ttu-id="828c9-205">Aynı uygulama kimliğine sahip bir hizmetin birden çok örneği bir konuya abone olduğunda, Davpr her iletiyi yalnızca birine gönderir.</span><span class="sxs-lookup"><span data-stu-id="828c9-205">When multiple instances of a service with the same application-id subscribe to a topic, Dapr delivers each message to only one of them.</span></span>

### <a name="sdks"></a><span data-ttu-id="828c9-206">SDK</span><span class="sxs-lookup"><span data-stu-id="828c9-206">SDKs</span></span>

<span data-ttu-id="828c9-207">Yerel Davpr API 'Lerine HTTP çağrıları yapmak zaman alan ve soyuttur.</span><span class="sxs-lookup"><span data-stu-id="828c9-207">Making HTTP calls to the native Dapr APIs is time-consuming and abstract.</span></span> <span data-ttu-id="828c9-208">Çağrılarınız HTTP düzeyinde oluşturulur ve serileştirme ve HTTP yanıt kodları gibi sıhhi tesisat kaygılarını işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-208">Your calls are crafted at the HTTP level, and you'll need to handle plumbing concerns such as serialization and HTTP response codes.</span></span> <span data-ttu-id="828c9-209">Neyse ki, daha sezgisel bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="828c9-209">Fortunately, there's a more intuitive way.</span></span> <span data-ttu-id="828c9-210">Davpr, popüler geliştirme platformları için dile özgü birkaç SDK sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-210">Dapr provides several language-specific SDKs for popular development platforms.</span></span> <span data-ttu-id="828c9-211">Bu yazma sırasında, Go, Node.js, Python, .NET, Java ve JavaScript kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-211">At the time of this writing, Go, Node.js, Python, .NET, Java, and JavaScript are available.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="828c9-212">Davpr .NET SDK 'sını kullanma</span><span class="sxs-lookup"><span data-stu-id="828c9-212">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="828c9-213">.NET geliştiricileri için, [davpr .NET SDK 'sı](https://www.nuget.org/packages/Dapr.Client) , davpr ile çalışmanın daha üretken bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-213">For .NET Developers, the [Dapr .NET SDK](https://www.nuget.org/packages/Dapr.Client) provides a more productive way of working with Dapr.</span></span> <span data-ttu-id="828c9-214">SDK, `DaprClient` doğrudan Davpr işlevini çağırabileceğiniz bir sınıf sunar.</span><span class="sxs-lookup"><span data-stu-id="828c9-214">The SDK exposes a `DaprClient` class through which you can directly invoke Dapr functionality.</span></span> <span data-ttu-id="828c9-215">Sezgisel ve kullanımı kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="828c9-215">It's intuitive and easy to use.</span></span>

<span data-ttu-id="828c9-216">Bir ileti yayımlamak için, `DaprClient` bir yöntemi sunar `PublishEventAsync` .</span><span class="sxs-lookup"><span data-stu-id="828c9-216">To publish a message, the `DaprClient` exposes a `PublishEventAsync` method.</span></span>

```csharp
var data = new OrderData
{
  orderId = "123456",
  productId = "67890",
  amount = 2
};

var daprClient = new DaprClientBuilder().Build();

await daprClient.PublishEventAsync<OrderData>("pubsub", "newOrder", data);
```

- <span data-ttu-id="828c9-217">İlk bağımsız değişken, `pubsub` ileti Aracısı uygulamasını sağlayan Davpr bileşeninin adıdır.</span><span class="sxs-lookup"><span data-stu-id="828c9-217">The first argument `pubsub` is the name of the Dapr component that provides the message broker implementation.</span></span> <span data-ttu-id="828c9-218">Bu bölümün ilerleyen kısımlarında bileşenleri ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="828c9-218">We'll address components later in this chapter.</span></span>
- <span data-ttu-id="828c9-219">İkinci bağımsız değişken `neworder` iletinin gönderileceği konunun adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-219">The second argument `neworder` provides the name of the topic to send the message to.</span></span>
- <span data-ttu-id="828c9-220">Üçüncü bağımsız değişken iletinin yüküyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="828c9-220">The third argument is the payload of the message.</span></span>
- <span data-ttu-id="828c9-221">Yönteminin genel tür parametresini kullanarak iletinin .NET türünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-221">You can specify the .NET type of the message using the generic type parameter of the method.</span></span>

<span data-ttu-id="828c9-222">İleti almak için, kayıtlı bir konu için bir uç noktayı bir aboneliğe bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="828c9-222">To receive messages, you bind an endpoint to a subscription for a registered topic.</span></span> <span data-ttu-id="828c9-223">Davpr için AspNetCore kitaplığı bu önemsiz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="828c9-223">The AspNetCore library for Dapr makes this trivial.</span></span> <span data-ttu-id="828c9-224">Örneğin, var olan bir ASP.NET WebAPI eylem yöntemine sahip olduğunu varsayalım `CreateOrder` :</span><span class="sxs-lookup"><span data-stu-id="828c9-224">Assume, for example, that you have an existing ASP.NET WebAPI action method entitled `CreateOrder`:</span></span>

```csharp
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

 > <span data-ttu-id="828c9-225">CPR [. AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) NuGet paketine, davpr ASP.NET Core tümleştirmesini kullanmak için bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-225">You must add a reference to the [Dapr.AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) NuGet package in your project to consume the Dapr ASP.NET Core integration.</span></span>

<span data-ttu-id="828c9-226">Bu eylem yöntemini bir konuya bağlamak için, özniteliği ile süslemeyi oluşturursunuz `Topic` :</span><span class="sxs-lookup"><span data-stu-id="828c9-226">To bind this action method to a topic, you decorate it with the `Topic` attribute:</span></span>

```csharp
[Topic("pubsub", "newOrder")]
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

<span data-ttu-id="828c9-227">Bu öznitelikle iki anahtar öğesi belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="828c9-227">You specify two key elements with this attribute:</span></span>

- <span data-ttu-id="828c9-228">Hedeflenecek Davpr pub/Sub bileşeni (Bu durumda `pubsub` ).</span><span class="sxs-lookup"><span data-stu-id="828c9-228">The Dapr pub/sub component to target (in this case `pubsub`).</span></span>
- <span data-ttu-id="828c9-229">Abone olunacak konu (Bu durumda `newOrder` ).</span><span class="sxs-lookup"><span data-stu-id="828c9-229">The topic to subscribe to (in this case `newOrder`).</span></span>

<span data-ttu-id="828c9-230">Daha sonra, bu konu için iletileri aldığından bu eylem yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-230">Dapr then invokes that action method as it receives messages for that topic.</span></span>

<span data-ttu-id="828c9-231">Ayrıca, ASP.NET Core Davpr 'yi kullanmak için etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-231">You'll also need to enable ASP.NET Core to use Dapr.</span></span> <span data-ttu-id="828c9-232">Davpr .NET SDK, sınıfında çağrılabilecek çeşitli uzantı yöntemleri sağlar `Startup` .</span><span class="sxs-lookup"><span data-stu-id="828c9-232">The Dapr .NET SDK provides several extension methods that can be invoked in the `Startup` class.</span></span>

<span data-ttu-id="828c9-233">`ConfigureServices`Yönteminde aşağıdaki genişletme yöntemini eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="828c9-233">In the `ConfigureServices` method, you must add the following extension method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddControllers().AddDapr();
}
```

<span data-ttu-id="828c9-234">Genişletme yöntemine uzantı-yöntemi eklemek, `AddDapr` `AddControllers` DAVPR 'yi MVC işlem hattına bütünleştirmek için gerekli hizmetleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="828c9-234">Appending the `AddDapr` extension-method to the `AddControllers` extension-method registers the necessary services to integrate Dapr into the MVC pipeline.</span></span> <span data-ttu-id="828c9-235">Ayrıca `DaprClient` , bir örneği bağımlılık ekleme kapsayıcısına kaydeder ve bu da hizmetinize herhangi bir yere eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-235">It also registers a `DaprClient` instance into the dependency injection container, which then can be injected anywhere into your service.</span></span>

<span data-ttu-id="828c9-236">`Configure`Yönteminde, Davpr 'yi etkinleştirmek için aşağıdaki ara yazılım bileşenlerini eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="828c9-236">In the `Configure` method, you must add the following middleware components to enable Dapr:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // ...
    app.UseCloudEvents();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapSubscribeHandler();
        // ...
    });
}
```

<span data-ttu-id="828c9-237">' A çağrı, `UseCloudEvents` ASP.NET Core ara yazılım ardışık düzenine **Cloudevents** ara yazılımı ekler.</span><span class="sxs-lookup"><span data-stu-id="828c9-237">The call to `UseCloudEvents` adds **CloudEvents** middleware into to the ASP.NET Core middleware pipeline.</span></span> <span data-ttu-id="828c9-238">Bu ara yazılım, CloudEvents yapılandırılmış biçimini kullanan istekleri geri sarmaz, bu nedenle alma yöntemi doğrudan olay yükünü okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-238">This middleware will unwrap requests that use the CloudEvents structured format, so the receiving method can read the event payload directly.</span></span>

> <span data-ttu-id="828c9-239">[Cloudevents](https://cloudevents.io/) , platformlar arasında olay bilgilerini tanımlamanın yaygın bir yolunu sağlayan standartlaştırılmış bir mesajlaşma biçimidir.</span><span class="sxs-lookup"><span data-stu-id="828c9-239">[CloudEvents](https://cloudevents.io/) is a standardized messaging format, providing a common way to describe event information across platforms.</span></span> <span data-ttu-id="828c9-240">Davpr emayraçları CloudEvents.</span><span class="sxs-lookup"><span data-stu-id="828c9-240">Dapr embraces CloudEvents.</span></span> <span data-ttu-id="828c9-241">CloudEvents hakkında daha fazla bilgi için bkz. [cloudevents belirtimi](https://github.com/cloudevents/spec/tree/v1.0).</span><span class="sxs-lookup"><span data-stu-id="828c9-241">For more information about CloudEvents, see the [cloudevents specification](https://github.com/cloudevents/spec/tree/v1.0).</span></span>

<span data-ttu-id="828c9-242">`MapSubscribeHandler`Uç nokta yönlendirme yapılandırmasındaki çağrısı uygulamaya bir Davpr abonelik uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="828c9-242">The call to `MapSubscribeHandler` in the endpoint routing configuration will add a Dapr subscribe endpoint to the application.</span></span> <span data-ttu-id="828c9-243">Bu uç nokta, üzerindeki isteklere yanıt verir `/dapr/subscribe` .</span><span class="sxs-lookup"><span data-stu-id="828c9-243">This endpoint will respond to requests on `/dapr/subscribe`.</span></span> <span data-ttu-id="828c9-244">Bu uç nokta çağrıldığında, özniteliğiyle birlikte bulunan tüm WebAPI eylem yöntemlerini otomatik olarak bulur ve bu işlem `Topic` için bir abonelik oluşturmak üzere Davpr 'yi yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="828c9-244">When this endpoint is called, it will automatically find all WebAPI action methods decorated with the `Topic` attribute and instruct Dapr to create subscriptions for them.</span></span>

## <a name="pubsub-components"></a><span data-ttu-id="828c9-245">Pub/Sub bileşenleri</span><span class="sxs-lookup"><span data-stu-id="828c9-245">Pub/sub components</span></span>

<span data-ttu-id="828c9-246">Davpr [pub/Sub bileşenleri](https://github.com/dapr/components-contrib/tree/master/pubsub) , iletilerin gerçek aktarımını işler.</span><span class="sxs-lookup"><span data-stu-id="828c9-246">Dapr [pub/sub components](https://github.com/dapr/components-contrib/tree/master/pubsub) handle the actual transport of the messages.</span></span> <span data-ttu-id="828c9-247">Bazıları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-247">Several are available.</span></span> <span data-ttu-id="828c9-248">Her biri, yayın/alt işlevselliği uygulamak için belirli bir ileti Aracısı ürününü kapsüller.</span><span class="sxs-lookup"><span data-stu-id="828c9-248">Each encapsulates a specific message broker product to implement the pub/sub functionality.</span></span> <span data-ttu-id="828c9-249">Yazma sırasında, aşağıdaki yayın/alt bileşenler kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="828c9-249">At the time of writing, the following pub/sub components were available:</span></span>

- <span data-ttu-id="828c9-250">Apache Kafka</span><span class="sxs-lookup"><span data-stu-id="828c9-250">Apache Kafka</span></span>
- <span data-ttu-id="828c9-251">Azure Event Hubs</span><span class="sxs-lookup"><span data-stu-id="828c9-251">Azure Event Hubs</span></span>
- <span data-ttu-id="828c9-252">Azure Service Bus</span><span class="sxs-lookup"><span data-stu-id="828c9-252">Azure Service Bus</span></span>
- <span data-ttu-id="828c9-253">AWS SNS/SQS</span><span class="sxs-lookup"><span data-stu-id="828c9-253">AWS SNS/SQS</span></span>
- <span data-ttu-id="828c9-254">GCP yayımlama/Sub</span><span class="sxs-lookup"><span data-stu-id="828c9-254">GCP Pub/Sub</span></span>
- <span data-ttu-id="828c9-255">Tehlikeli elcast</span><span class="sxs-lookup"><span data-stu-id="828c9-255">Hazelcast</span></span>
- <span data-ttu-id="828c9-256">MQTT</span><span class="sxs-lookup"><span data-stu-id="828c9-256">MQTT</span></span>
- <span data-ttu-id="828c9-257">NAT</span><span class="sxs-lookup"><span data-stu-id="828c9-257">NATS</span></span>
- <span data-ttu-id="828c9-258">Pulöib</span><span class="sxs-lookup"><span data-stu-id="828c9-258">Pulsar</span></span>
- <span data-ttu-id="828c9-259">RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="828c9-259">RabbitMQ</span></span>
- <span data-ttu-id="828c9-260">Redsıs akışları</span><span class="sxs-lookup"><span data-stu-id="828c9-260">Redis Streams</span></span>

> [!NOTE]
> <span data-ttu-id="828c9-261">Azure bulut yığınında hem mesajlaşma işlevselliği (Azure Service Bus) hem de olay akışı (Azure Event hub) kullanılabilirliği vardır.</span><span class="sxs-lookup"><span data-stu-id="828c9-261">The Azure cloud stack has both messaging functionality (Azure Service Bus) and event streaming (Azure Event Hub) availability.</span></span>

<span data-ttu-id="828c9-262">Bu bileşenler, [GitHub 'da bir bileşen-Contrib deposunda](https://github.com/dapr/components-contrib/tree/master/pubsub)topluluk tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="828c9-262">These components are created by the community in a [component-contrib repository on GitHub](https://github.com/dapr/components-contrib/tree/master/pubsub).</span></span> <span data-ttu-id="828c9-263">Henüz desteklenmeyen bir ileti Aracısı için kendi Davpr bileşenini yazmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-263">You're encouraged to write your own Dapr component for a message broker that isn't yet supported.</span></span>

### <a name="configure-pubsub-components"></a><span data-ttu-id="828c9-264">Yayın/alt bileşenleri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="828c9-264">Configure pub/sub components</span></span>

<span data-ttu-id="828c9-265">Bir Davpr yapılandırma dosyası kullanarak, kullanılacak yayın/alt bileşenleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-265">Using a Dapr configuration file, you can specify the pub/sub component(s) to use.</span></span> <span data-ttu-id="828c9-266">Bu yapılandırma birkaç alan içerir.</span><span class="sxs-lookup"><span data-stu-id="828c9-266">This configuration contains several fields.</span></span> <span data-ttu-id="828c9-267">`name`Alan, kullanmak istediğiniz yayın/alt bileşeni belirtir.</span><span class="sxs-lookup"><span data-stu-id="828c9-267">The `name` field specifies the pub/sub component that you want to use.</span></span> <span data-ttu-id="828c9-268">İleti gönderirken veya alırken, bu adı belirtmeniz gerekir (daha önce `PublishEventAsync` Yöntem imzasında gördüğünüz gibi).</span><span class="sxs-lookup"><span data-stu-id="828c9-268">When sending or receiving a message, you need to specify this name (as you saw earlier in the `PublishEventAsync` method signature).</span></span>

<span data-ttu-id="828c9-269">Aşağıda, bir Kbbitmq ileti Aracısı bileşeni yapılandırmak için bir Davpr yapılandırma dosyası örneği görülmektedir:</span><span class="sxs-lookup"><span data-stu-id="828c9-269">Below you see an example of a Dapr configuration file for configuring a RabbitMQ message broker component:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub-rq
spec:
  type: pubsub.rabbitmq
  version: v1
  metadata:
  - name: host
    value: "amqp://localhost:5672"
  - name: durable
    value: true
```

<span data-ttu-id="828c9-270">Bu örnekte, bloğunda herhangi bir ileti aracısına özgü yapılandırma belirtebilirsiniz `metadata` .</span><span class="sxs-lookup"><span data-stu-id="828c9-270">In this example, you can see that you can specify any message broker-specific configuration in the `metadata` block.</span></span> <span data-ttu-id="828c9-271">Bu durumda, Kbbitmq dayanıklı kuyruklar oluşturmak için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-271">In this case, RabbitMQ is configured to create durable queues.</span></span> <span data-ttu-id="828c9-272">Ancak, Kbbitmq bileşeninin daha fazla yapılandırma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="828c9-272">But the RabbitMQ component has more configuration options.</span></span> <span data-ttu-id="828c9-273">Her bir bileşenin yapılandırması kendi olası alanları kümesine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="828c9-273">Each of the components' configuration will have its own set of possible fields.</span></span> <span data-ttu-id="828c9-274">Her bir [yayın/alt bileşen](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/)belgelerindeki hangi alanların kullanılabilir olduğunu okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-274">You can read which fields are available in the documentation of each [pub/sub component](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/).</span></span>

<span data-ttu-id="828c9-275">Koddan bir konuya abone olmanın programlama yolunun yanında, Davpr pub/Sub da bir konuya abone olmak için bildirim temelli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-275">Next to the programmatic way of subscribing to a topic from code, Dapr pub/sub also provides a declarative way of subscribing to a topic.</span></span> <span data-ttu-id="828c9-276">Bu yaklaşım, uygulama kodundan gelen Davpr bağımlılığını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-276">This approach removes the Dapr dependency from the application code.</span></span> <span data-ttu-id="828c9-277">Bu nedenle, var olan bir uygulamanın kodda herhangi bir değişiklik yapmadan konulara abone olma imkanı de sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-277">Therefore, it also enables an existing application to subscribe to topics without any changes to the code.</span></span> <span data-ttu-id="828c9-278">Aşağıdaki örnek, bir aboneliği yapılandırmak için bir Davpr yapılandırma dosyası göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="828c9-278">The following example shows a Dapr configuration file for configuring a subscription:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Subscription
metadata:
  name: newOrder-subscription
spec:
  pubsubname: pubsub
  topic: newOrder
  route: /orders
scopes:
- ServiceB
- ServiceC
```

<span data-ttu-id="828c9-279">Her abonelikle birkaç öğe belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="828c9-279">You have to specify several elements with every subscription:</span></span>

- <span data-ttu-id="828c9-280">Kullanmak istediğiniz Davpr pub/Sub bileşeninin adı (Bu durumda `pubsub` ).</span><span class="sxs-lookup"><span data-stu-id="828c9-280">The name of the Dapr pub/sub component you want to use (in this case `pubsub`).</span></span>
- <span data-ttu-id="828c9-281">Abone olunacak konunun adı (Bu durumda `newOrder` ).</span><span class="sxs-lookup"><span data-stu-id="828c9-281">The name of the topic to subscribe to (in this case `newOrder`).</span></span>
- <span data-ttu-id="828c9-282">Bu konu için çağrılması gereken API işlemi (Bu durumda `/orders` ).</span><span class="sxs-lookup"><span data-stu-id="828c9-282">The API operation that needs to be called for this topic (in this case `/orders`).</span></span>
- <span data-ttu-id="828c9-283">[Kapsam](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/) , hangi hizmetlerin bir konuya yayımlayabileceği ve abone olabileceği belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-283">The [scope](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/) can specify which services can publish and subscribe to a topic.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="828c9-284">Başvuru uygulaması: Eshopondadpr</span><span class="sxs-lookup"><span data-stu-id="828c9-284">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="828c9-285">Eşlik eden [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr) uygulaması, davpr uygulayan bir mikro Hizmetler uygulaması oluşturmak için uçtan uca bir başvuru mimarisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-285">The accompanying [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) app provides an end-to-end reference architecture for constructing a microservices application implementing Dapr.</span></span> <span data-ttu-id="828c9-286">Eshopondadpr, çok sayıda yıl önce oluşturulmuş yaygın olarak popüler [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainer) uygulamasının bir evrimi.</span><span class="sxs-lookup"><span data-stu-id="828c9-286">eShopOnDapr is an evolution of the widely popular [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainer) app, created several years ago.</span></span> <span data-ttu-id="828c9-287">Her iki sürüm de mikro hizmetler genelinde [tümleştirme olaylarını](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) iletişim kurmak için yayımlama/alt modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="828c9-287">Both versions use the pub/sub pattern for communicating [integration events](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) across microservices.</span></span> <span data-ttu-id="828c9-288">Tümleştirme olayları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="828c9-288">Integration events include:</span></span>

- <span data-ttu-id="828c9-289">Bir Kullanıcı bir alışveriş sepetini denetlediğinde.</span><span class="sxs-lookup"><span data-stu-id="828c9-289">When a user checks-out a shopping basket.</span></span>
- <span data-ttu-id="828c9-290">Bir sipariş için ödeme başarılı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="828c9-290">When a payment for an order has succeeded.</span></span>
- <span data-ttu-id="828c9-291">Bir satınalmanın yetkisiz kullanım süresi dolduğunda.</span><span class="sxs-lookup"><span data-stu-id="828c9-291">When the grace-period of a purchase has expired.</span></span>

<span data-ttu-id="828c9-292">EShopOnContainers içindeki olay aşağıdaki `IEventBus` arabirime dayalıdır:</span><span class="sxs-lookup"><span data-stu-id="828c9-292">Eventing in eShopOnContainers is based on the following `IEventBus` interface:</span></span>

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent integrationEvent);

    void Subscribe<T, THandler>()
        where TEvent : IntegrationEvent
        where THandler : IIntegrationEventHandler<T>;
}
```

<span data-ttu-id="828c9-293">Bu arabirimin somut uygulamaları, hem Kbbitmq hem de Azure Service Bus için eShopOnContainers içinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="828c9-293">Concrete implementations of this interface exist in eShopOnContainers for both RabbitMQ and Azure Service Bus.</span></span> <span data-ttu-id="828c9-294">Her uygulama, anlaşılması ve bakımının zor olması karmaşık olan özel bir sıhhi tesisat kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="828c9-294">Each implementation included a great deal of custom plumbing code that was complex to understand and difficult to maintain.</span></span>

<span data-ttu-id="828c9-295">Yeni Eshopondadpr, Davpr kullanarak yayın/alt davranışını önemli ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="828c9-295">The newer eShopOnDapr significantly simplifies pub/sub behavior by using Dapr.</span></span> <span data-ttu-id="828c9-296">Örneğin, `IEventBus` arabirim tek bir yönteme düşürüldü:</span><span class="sxs-lookup"><span data-stu-id="828c9-296">For example, the `IEventBus` interface was reduced to a single method:</span></span>

```csharp
public interface IEventBus
{
    Task PublishAsync(IntegrationEvent integrationEvent);
}
```

### <a name="publish-events"></a><span data-ttu-id="828c9-297">Olayları Yayımla</span><span class="sxs-lookup"><span data-stu-id="828c9-297">Publish events</span></span>

<span data-ttu-id="828c9-298">Güncelleştirilmiş Eshopondadpr 'de, tek bir `DaprEventBus` uygulama herhangi bir Davpr tarafından desteklenen ileti Aracısı 'nı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-298">In the updated eShopOnDapr, a single `DaprEventBus` implementation can support any Dapr-supported message broker.</span></span> <span data-ttu-id="828c9-299">Aşağıdaki kod bloğu Basitleştirilmiş yayımlama yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="828c9-299">The following code block shows the simplified Publish method.</span></span> <span data-ttu-id="828c9-300">`PublishAsync`Yönteminin bir olay yayımlamak için bir Davpr istemcisini nasıl kullandığını aklınızda edin:</span><span class="sxs-lookup"><span data-stu-id="828c9-300">Note how the `PublishAsync` method uses the Dapr client to publish an event:</span></span>

```csharp
public class DaprEventBus : IEventBus
{
    private const string PubSubName = "pubsub";

    private readonly DaprClient _daprClient;
    private readonly ILogger<DaprEventBus> _logger;

    public DaprEventBus(DaprClient daprClient, ILogger<DaprEventBus> logger)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task PublishAsync(IntegrationEvent integrationEvent)
    {
        var topicName = integrationEvent.GetType().Name;

        // Dapr uses System.Text.Json which does not support serialization of a
        // polymorphic type hierarchy by default. Using object as the type
        // parameter causes all properties to be serialized.
        await _daprClient.PublishEventAsync<object>(PubSubName, topicName, integrationEvent);
    }
}
```

<span data-ttu-id="828c9-301">Kod parçacığında görebileceğiniz gibi, konu adı olay türünün adından türetilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-301">As you can see in the code snippet, the topic name is derived from event type's name.</span></span> <span data-ttu-id="828c9-302">Tüm eShop Hizmetleri `IEventBus` soyutlama kullandığından, geriye doğru ekleme davpr, ana hat uygulama kodunda *kesinlikle hiçbir değişiklik* gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="828c9-302">Because all eShop services use the `IEventBus` abstraction, retrofitting Dapr required *absolutely no change* to the mainline application code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="828c9-303">Davpr SDK, `System.Text.Json` iletileri seri hale getirmek/seri durumdan çıkarmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="828c9-303">The Dapr SDK uses `System.Text.Json` to serialize/deserialize messages.</span></span> <span data-ttu-id="828c9-304">Ancak, `System.Text.Json` türetilmiş sınıfların özelliklerini varsayılan olarak serileştirmez.</span><span class="sxs-lookup"><span data-stu-id="828c9-304">However, `System.Text.Json` doesn't serialize properties of derived classes by default.</span></span> <span data-ttu-id="828c9-305">EShop kodunda, bazen `IntegrationEvent` tümleştirme olayları için temel sınıf olarak açıkça bir olay olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="828c9-305">In the eShop code, an event is sometimes explicitly declared as an `IntegrationEvent`, the base class for integration events.</span></span> <span data-ttu-id="828c9-306">Bu işlem, somut olay türü iş mantığını temel alan çalışma zamanında dinamik olarak belirlendiği için yapılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-306">This is done because the concrete event type is determined dynamically at run time based on business logic.</span></span> <span data-ttu-id="828c9-307">Sonuç olarak, olay, türetilmiş sınıf değil, temel sınıfın tür bilgileri kullanılarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="828c9-307">As a result, the event is serialized using the type information of the base class and not the derived class.</span></span> <span data-ttu-id="828c9-308">`System.Text.Json`Bu durumda türetilmiş sınıfın tüm özelliklerini Serileştirmeye zorlamak için, kod `object` genel tür parametresi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-308">To force `System.Text.Json` to serialize all properties of the derived class in this case, the code uses `object` as the generic type parameter.</span></span> <span data-ttu-id="828c9-309">Daha fazla bilgi için bkz. [.net belgeleri](../../standard/serialization/system-text-json-polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="828c9-309">For more information, see the [.NET documentation](../../standard/serialization/system-text-json-polymorphism.md).</span></span>

<span data-ttu-id="828c9-310">Davpr ile altyapı kodu **önemli ölçüde basitleştirilmiştir**.</span><span class="sxs-lookup"><span data-stu-id="828c9-310">With Dapr, the infrastructure code is **dramatically simplified**.</span></span> <span data-ttu-id="828c9-311">Farklı ileti aracıları arasında ayrım yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="828c9-311">It doesn't need to distinguish between the different message brokers.</span></span> <span data-ttu-id="828c9-312">Davpr sizin için bu soyutlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="828c9-312">Dapr provides this abstraction for you.</span></span> <span data-ttu-id="828c9-313">Gerekirse, ileti aracılarını kolayca takas edebilir veya birden çok ileti Aracısı bileşeni yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-313">And if needed, you can easily swap out message brokers or configure multiple message broker components.</span></span>

### <a name="subscribe-to-events"></a><span data-ttu-id="828c9-314">Olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="828c9-314">Subscribe to events</span></span>

<span data-ttu-id="828c9-315">Önceki eShopOnContainers uygulaması, her ileti aracısının abonelik uygulamasını işleyecek olan *subscriptionapps* 'i içerir.</span><span class="sxs-lookup"><span data-stu-id="828c9-315">The earlier eShopOnContainers app contains *SubscriptionManagers* to handle the subscription implementation for each message broker.</span></span> <span data-ttu-id="828c9-316">Her yönetici, abonelik olaylarını işlemek için karmaşık ileti aracısına özgü kod içerir.</span><span class="sxs-lookup"><span data-stu-id="828c9-316">Each manager contains complex message broker-specific code for handling subscription events.</span></span> <span data-ttu-id="828c9-317">Olayları almak için her hizmetin her bir olay türü için açıkça bir işleyici kaydetmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-317">To receive events, each service has to explicitly register a handler for each event-type.</span></span>

<span data-ttu-id="828c9-318">Eshopondadpr, Davpr ASP.NET Core kitaplıklarını kullanarak olay aboneliklerine yönelik sıhhi tesisat kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-318">eShopOnDapr streamlines the plumbing for event subscriptions by using Dapr ASP.NET Core libraries.</span></span> <span data-ttu-id="828c9-319">Her olay denetleyicisindeki bir eylem yöntemiyle işlenir.</span><span class="sxs-lookup"><span data-stu-id="828c9-319">Each event is handled by an action method in the controller.</span></span> <span data-ttu-id="828c9-320">Bir `Topic` öznitelik, öğesine abone olmak için ilgili konunun adı ile eylem yöntemini dekorayırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-320">A `Topic` attribute decorates the action method with the name of the corresponding topic to subscribe to.</span></span> <span data-ttu-id="828c9-321">Aşağıda, öğesinden alınan bir kod parçacığı verilmiştir `PaymentService` :</span><span class="sxs-lookup"><span data-stu-id="828c9-321">Here's a code snippet taken from the `PaymentService`:</span></span>

```csharp
[Route("api/v1/[controller]")]
[ApiController]
public class IntegrationEventController : ControllerBase
{
    private const string DAPR_PUBSUB_NAME = "pubsub";

    private readonly IServiceProvider _serviceProvider;

    public IntegrationEventController(IServiceProvider serviceProvider)
    {
        _serviceProvider = serviceProvider;
    }

    [HttpPost("OrderStatusChangedToValidated")]
    [Topic(DAPR_PUBSUB_NAME, "OrderStatusChangedToValidatedIntegrationEvent")]
    public async Task OrderStarted(OrderStatusChangedToValidatedIntegrationEvent integrationEvent)
    {
        var handler = _serviceProvider.GetRequiredService<OrderStatusChangedToValidatedIntegrationEventHandler>();
        await handler.Handle(integrationEvent);
    }
}
```

<span data-ttu-id="828c9-322">`Topic`Özniteliğinde, etkinliğin .NET türünün adı, konu adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-322">In the `Topic` attribute, the name of the .NET type of the event is used as the topic name.</span></span> <span data-ttu-id="828c9-323">Olayı işlemek için önceki eShopOnContainers kod tabanında zaten varolan bir olay işleyicisi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="828c9-323">For handling the event, an event handler that already existed in the earlier eShopOnContainers code base is invoked.</span></span> <span data-ttu-id="828c9-324">Önceki örnekte, konudan alınan iletiler `OrderStatusChangedToValidatedIntegrationEvent` var olan `OrderStatusChangedToValidatedIntegrationEventHandler` olay işleyicisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="828c9-324">In the previous example, messages received from the `OrderStatusChangedToValidatedIntegrationEvent` topic invoke the existing `OrderStatusChangedToValidatedIntegrationEventHandler` event-handler.</span></span> <span data-ttu-id="828c9-325">Davpr, abonelikler ve ileti aracıları için temeldeki sıhhi tesisat uyguladığından, büyük miktarda orijinal kod kullanılmıyor olur ve kod tabanından kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="828c9-325">Because Dapr implements the underlying plumbing for subscriptions and message brokers, a large amount of original code became obsolete and was removed from the code-base.</span></span> <span data-ttu-id="828c9-326">Bu kodun büyük bölümü anlaşılması ve bakımının zorlayıcı olması karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="828c9-326">Much of this code was complex to understand and challenging to maintain.</span></span>

### <a name="use-pubsub-components"></a><span data-ttu-id="828c9-327">Yayın/alt bileşenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="828c9-327">Use pub/sub components</span></span>

<span data-ttu-id="828c9-328">EShopOnDapr deposunda, bir klasör, `deployment` farklı dağıtım modları kullanılarak uygulamayı dağıtmaya yönelik dosyaları içerir: `Docker Compose` ve `Kubernetes` .</span><span class="sxs-lookup"><span data-stu-id="828c9-328">Within the eShopOnDapr repository, a `deployment` folder contains files for deploying the application using different deployment modes: `Docker Compose` and `Kubernetes`.</span></span> <span data-ttu-id="828c9-329">`dapr`Bir klasörü tutan bu klasörlerin her birinde bir klasör bulunur `components` .</span><span class="sxs-lookup"><span data-stu-id="828c9-329">A `dapr` folder exists within each of these folders that holds a `components` folder.</span></span> <span data-ttu-id="828c9-330">Bu klasör, `eshop-pubsub.yaml` uygulamanın pub/Sub davranışı için kullanacağı DAPR pub/Sub bileşeninin yapılandırmasını içeren bir dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="828c9-330">This folder holds a file `eshop-pubsub.yaml` containing the configuration of the Dapr pub/sub component that the application will use for pub/sub behavior.</span></span> <span data-ttu-id="828c9-331">Önceki kod parçacıklarında gördüğünüz gibi, kullanılan yayın/alt bileşen adı da olur `pubsub` .</span><span class="sxs-lookup"><span data-stu-id="828c9-331">As you saw in the earlier code snippets, the name of the pub/sub component used is `pubsub`.</span></span> <span data-ttu-id="828c9-332">Dosyanın içeriği şu şekildedir `eshop-pubsub.yaml` `deployment/compose/dapr/components` :</span><span class="sxs-lookup"><span data-stu-id="828c9-332">Here's the content of the `eshop-pubsub.yaml` file in the `deployment/compose/dapr/components` folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: default
spec:
  type: pubsub.nats
  version: v1
  metadata:
  - name: natsURL
    value: nats://demo.nats.io:4222
```

<span data-ttu-id="828c9-333">Önceki yapılandırma Bu örnek için istenen [NAT ileti Aracısı](https://nats.io/) 'nı belirtir.</span><span class="sxs-lookup"><span data-stu-id="828c9-333">The preceding configuration specifies the desired [NATS message broker](https://nats.io/) for this example.</span></span> <span data-ttu-id="828c9-334">İleti aracılarını değiştirmek için, yalnızca Korbbitmq veya Azure Service Bus gibi farklı bir ileti Aracısı yapılandırmanız ve YAML dosyasını güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="828c9-334">To change message brokers, you need only to configure a different message broker, such as RabbitMQ or Azure Service Bus and update the yaml file.</span></span> <span data-ttu-id="828c9-335">Davpr ile, ana hat hizmeti kodunuzda ileti aracılarını değiştirirken hiçbir değişiklik yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="828c9-335">With Dapr, there are no changes to your mainline service code when switching message brokers.</span></span>

<span data-ttu-id="828c9-336">Son olarak, "Neden bir uygulamada birden çok ileti aracısın gerekir?" sorabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-336">Finally, you might ask, "Why would I need multiple message brokers in an application?".</span></span> <span data-ttu-id="828c9-337">Bir sistem, farklı özelliklere sahip iş yüklerini işleyecek birçok kez.</span><span class="sxs-lookup"><span data-stu-id="828c9-337">Many times a system will handle workloads with different characteristics.</span></span> <span data-ttu-id="828c9-338">Bir olay günde 10 kez gerçekleşebilir, ancak saniyede 5.000 kez bir olay oluşur.</span><span class="sxs-lookup"><span data-stu-id="828c9-338">One event may occur 10 times a day, but another event occurs 5,000 times per second.</span></span> <span data-ttu-id="828c9-339">Mesajlaşma trafiğini farklı ileti aracılarına bölümleyerek yarar sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-339">You may benefit by partitioning messaging traffic to different message brokers.</span></span> <span data-ttu-id="828c9-340">Davpr ile, her biri farklı bir ada sahip birden çok yayın/alt bileşen yapılandırması ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-340">With Dapr, you can add multiple pub/sub component configurations, each with a different name.</span></span>

## <a name="summary"></a><span data-ttu-id="828c9-341">Özet</span><span class="sxs-lookup"><span data-stu-id="828c9-341">Summary</span></span>

<span data-ttu-id="828c9-342">Yayın/alt model dağıtılmış bir uygulamada Hizmetleri ayırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="828c9-342">The pub/sub pattern helps you decouple services in a distributed application.</span></span> <span data-ttu-id="828c9-343">CPR Publish & Subscribe derleme bloğu uygulamanızda bu davranışı uygulamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="828c9-343">The Dapr publish & subscribe building block simplifies implementing this behavior in your application.</span></span>

<span data-ttu-id="828c9-344">Davpr pub/Sub aracılığıyla belirli bir *konuya* ileti yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-344">Through Dapr pub/sub, you can publish messages to a specific *topic*.</span></span> <span data-ttu-id="828c9-345">Ayrıca yapı taşı, hangi konunun abone olunacağını öğrenmek için hizmetinizi sorgular.</span><span class="sxs-lookup"><span data-stu-id="828c9-345">As well, the building block will query your service to determine which topic(s) to subscribe to.</span></span>

<span data-ttu-id="828c9-346">HTTP üzerinden veya Davpr için .NET SDK gibi dile özgü SDK 'Lardan birini kullanarak, Davpr pub/Sub 'ı yerel olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-346">You can use Dapr pub/sub natively over HTTP or by using one of the language-specific SDKs, such as the .NET SDK for Dapr.</span></span> <span data-ttu-id="828c9-347">.NET SDK, ASP.NET Core platformu ile sıkı bir şekilde tümleşir.</span><span class="sxs-lookup"><span data-stu-id="828c9-347">The .NET SDK tightly integrates with the ASP.NET core platform.</span></span>

<span data-ttu-id="828c9-348">Davpr ile desteklenen bir ileti Aracısı ürününü uygulamanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-348">With Dapr, you can plug a supported message broker product into your application.</span></span> <span data-ttu-id="828c9-349">Daha sonra, uygulamanızda kod değişikliğine gerek duymadan ileti aracılarını takas edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828c9-349">You can then swap message brokers without requiring code changes to your application.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="828c9-350">[Önceki](service-invocation.md) 
>  [Sonraki](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="828c9-350">[Previous](service-invocation.md)
[Next](bindings.md)</span></span>
