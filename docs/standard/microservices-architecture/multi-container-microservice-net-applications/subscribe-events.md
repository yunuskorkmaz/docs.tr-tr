---
title: Olaylara abone olma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Olaylara abone olma
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7538c760d396349fe9b1e93a21839e3e59d7f046
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="subscribing-to-events"></a><span data-ttu-id="07ad3-104">Olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="07ad3-104">Subscribing to events</span></span>

<span data-ttu-id="07ad3-105">Olay veri yolu kullanarak ilk mikro almak istediği olaylara abone olma adımdır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-105">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="07ad3-106">Alıcı mikro yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-106">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="07ad3-107">Aşağıdaki basit kod her alıcı mikro hizmet başlatılırken uygulamak gereken gösterir (diğer bir deyişle, `Startup` sınıfı) şekilde bu olayları, ihtiyaçlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="07ad3-107">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="07ad3-108">Bu durumda, `basket.api` mikro hizmet abone olmak için gereksinim duyduğu `ProductPriceChangedIntegrationEvent` ve `OrderStartedIntegrationEvent` iletileri.</span><span class="sxs-lookup"><span data-stu-id="07ad3-108">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span> 

<span data-ttu-id="07ad3-109">Örneğin, abone olduğunda `ProductPriceChangedIntegrationEvent` Sepeti mikro hizmet herhangi farkında yapan olay Ürün Fiyat değiştirir ve bu ürünün kullanıcının sepetteki ise değişiklik hakkında kullanıcıyı uyarmak etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07ad3-109">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="07ad3-110">Bu kod çalıştıktan sonra abone mikro hizmet RabbitMQ kanallardan dinleme.</span><span class="sxs-lookup"><span data-stu-id="07ad3-110">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="07ad3-111">Her ileti türü ProductPriceChangedIntegrationEvent geldiğinde kodu kendisine geçirilen ve olay işleyen olay işleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-111">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="07ad3-112">Olay veri yolu üzerinden olay yayımlama</span><span class="sxs-lookup"><span data-stu-id="07ad3-112">Publishing events through the event bus</span></span>

<span data-ttu-id="07ad3-113">Son olarak, aşağıdaki örneğe benzer bir kod tümleştirme olaylarla (kaynak mikro) iletiyi gönderenin yayımlar.</span><span class="sxs-lookup"><span data-stu-id="07ad3-113">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="07ad3-114">(Bu kararlılık dikkate almaz basitleştirilmiş bir örnek niteliğindedir.) Birden çok mikro, verileri veya kaynak mikro hizmet hareketleri uyguladıktan sonra genellikle sağ arasında bir olay dağıtılmalıdır her benzer bir kod uygulamak.</span><span class="sxs-lookup"><span data-stu-id="07ad3-114">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="07ad3-115">İlk olarak, aşağıdaki kod olduğu gibi denetleyicisi Oluşturucusu en (RabbitMQ üzerinde temel veya bir service bus tabanlı) olay veri yolu uygulama nesnesi eklenemeyebilir:</span><span class="sxs-lookup"><span data-stu-id="07ad3-115">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="07ad3-116">Ardından, onu denetleyicinizin yöntemleri, gibi UpdateProduct yöntemi kullanın:</span><span class="sxs-lookup"><span data-stu-id="07ad3-116">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("update")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="07ad3-117">Bu durumda, basit bir CRUD mikro hizmet kaynak mikro hizmet olduğuna göre bu kodu bir Web API denetleyicisi sağ yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-117">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> 
 
<span data-ttu-id="07ad3-118">CQRS yaklaşımlar kullanırken gibi daha gelişmiş mikro onu içinde uygulanabilir `CommandHandler` sınıfı, içinde `Handle()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07ad3-118">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span> 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="07ad3-119">Kararlılık ve dayanıklılık olay yoluna yayımlarken tasarlama</span><span class="sxs-lookup"><span data-stu-id="07ad3-119">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="07ad3-120">Dağıtılmış ileti aracılığıyla tümleştirme olaylarını yayımladığınızda, olay veri yolu gibi sistem, otomatik olarak özgün veritabanını güncelleştirme ve olay yayımlama sorununuz.</span><span class="sxs-lookup"><span data-stu-id="07ad3-120">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="07ad3-121">Ürün Fiyat değiştirilir ve bir ProductPriceChangedIntegrationEvent ileti yayımlar örneği için daha önce gösterilen Basitleştirilmiş örnekte kodu verileri veritabanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="07ad3-121">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="07ad3-122">Başlangıçta, bu iki işlemleri otomatik olarak gerçekleştirilmesi temel görünebilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-122">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="07ad3-123">İlgili bir dağıtılmış işlem kullanıyorsanız gibi eski sistemlerinde olduğu gibi ancak, veritabanı ve iletiyi, Aracısı [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), bu tarafındanaçıklanannedenleriyleönerilmez[CAP Teoremi](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="07ad3-123">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="07ad3-124">Temel olarak, mikro ölçeklenebilir ve yüksek oranda kullanılabilir sistemleri oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-124">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="07ad3-125">CAP Teoremi bir veritabanının (veya kendi modelini sahip bir mikro) oluşturamaz diyor biraz basitleştirme, sürekli olarak kullanılabilir, kesinlikle tutarlı *ve* dayanıklı herhangi bir bölümü için.</span><span class="sxs-lookup"><span data-stu-id="07ad3-125">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="07ad3-126">Bu üç özellik ikilisi seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-126">You must choose two of these three properties.</span></span>

<span data-ttu-id="07ad3-127">Mikro tabanlı mimari, kullanılabilirlik ve dayanıklılık seçmeniz gerekir ve, güçlü tutarlılık devamlı müşterilerine göre ayarlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="07ad3-127">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="07ad3-128">Uyguladığınızda, yaptığınız gibi bu nedenle, çoğu modern mikro hizmet tabanlı uygulamalarda genellikle mesajlaşmada, dağıtılmış işlemler kullanmak istediğiniz değil [dağıtılmış işlemler](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) Windows Dağıtılmış İşlem üzerinde dayalı Düzenleyicisi (DTC) ile [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="07ad3-128">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="07ad3-129">İlk sorun ve kendi örnek edelim.</span><span class="sxs-lookup"><span data-stu-id="07ad3-129">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="07ad3-130">Veritabanı güncelleştirildikten sonra hizmetin çökmesi durumunda (Bu durumda, kodla satırından sonra sağ \_bağlamı. SaveChangesAsync()), ancak tümleştirme olay yayımlanmadan önce genel sistem tutarsız hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-130">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="07ad3-131">Bu iş ilgilendiğiniz belirli iş işleme bağlı olarak önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-131">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="07ad3-132">Mimari bölümünde daha önce belirtildiği gibi bu sorunla ilgili çeşitli yaklaşımlar sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="07ad3-132">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="07ad3-133">Tam kullanarak [olay kaynak Hizmeti'nden düzeni](https://msdn.microsoft.com/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="07ad3-133">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="07ad3-134">Kullanarak [işlem oturum araştırma](http://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="07ad3-134">Using [transaction log mining](http://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="07ad3-135">Kullanarak [Giden kutusu düzeni](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="07ad3-135">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="07ad3-136">(Yerel işlem genişletme) tümleştirme olayları depolamak üzere bir işlem tablo budur.</span><span class="sxs-lookup"><span data-stu-id="07ad3-136">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="07ad3-137">Bu senaryo için tam olay kaynak Hizmeti'nden (ES) deseni en iyi yaklaşımlardan birini değilse kullanmaktır *en* iyi.</span><span class="sxs-lookup"><span data-stu-id="07ad3-137">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="07ad3-138">Ancak, çok sayıda uygulama senaryolarında, tam bir ES sistemi uygulayabilirsiniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-138">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="07ad3-139">ES geçerli durumu verilerinin depolanması yerine, işlemsel veritabanında yalnızca etki alanı olayları depolamak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-139">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="07ad3-140">Yalnızca etki alanı olayları depolamak geçmişini sisteminizin kullanılabilir olması ve geçmişteki herhangi bir anda, sistem durumunu belirlemek mümkün gibi çok yarar olabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-140">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="07ad3-141">Ancak, tam bir ES sistemi uygulama sisteminizi çoğunu rearchitect gerektirir ve diğer birçok karmaşıklık ve gereksinimleri sunar.</span><span class="sxs-lookup"><span data-stu-id="07ad3-141">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="07ad3-142">Örneğin, özellikle olay kaynak için gibi yapılan bir veritabanını kullanmak istersiniz [olay deposuna](https://geteventstore.com/), veya Azure Cosmos DB, MongoDB, Cassandra, CouchDB veya RavenDB gibi belge yönelimli veritabanı.</span><span class="sxs-lookup"><span data-stu-id="07ad3-142">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="07ad3-143">Olay kaynak Hizmeti'nden ile bilginiz sürece ES Bu sorun, ancak en kolay çözüm için harika bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-143">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="07ad3-144">İşlem günlüğü başlangıçta araştırma kullanma seçeneği çok saydam arar.</span><span class="sxs-lookup"><span data-stu-id="07ad3-144">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="07ad3-145">Ancak, bu yaklaşımı kullanmak için SQL Server işlem günlüğü gibi RDBMS işlem günlüğü için eşleştirilmek üzere mikro hizmet vardır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-145">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="07ad3-146">Bu arzu büyük olasılıkla değil.</span><span class="sxs-lookup"><span data-stu-id="07ad3-146">This is probably not desirable.</span></span> <span data-ttu-id="07ad3-147">Başka bir dezavantajı, işlem günlüğüne alt düzey güncelleştirmeleri, üst düzey tümleştirme olayları ile aynı düzeyde olmayabilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-147">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="07ad3-148">Ters mühendislik işlemi varsa, bu işlem günlüğü işlemler zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-148">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="07ad3-149">Dengeli bir yaklaşım, bir işlemsel veritabanı tablosu ve Basitleştirilmiş ES düzeni karışımıdır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-149">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="07ad3-150">"Tümleştirme olayları tabloya yaparsanız özgün olayda belirlenen olay yayımlamaya hazır" gibi bir durumda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ad3-150">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="07ad3-151">Ardından olay veri yoluna olayı yayımlamak deneyin.</span><span class="sxs-lookup"><span data-stu-id="07ad3-151">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="07ad3-152">Yayımla olayı eylemi başarılı olursa, başka bir işlem kaynak hizmetini ve durumu "hazır'dan olayı yayımlamak" "zaten yayınlanmış olaya." taşıma</span><span class="sxs-lookup"><span data-stu-id="07ad3-152">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="07ad3-153">Yayımla olay eylem başarısız olay veri yolu, veri hala kaynak mikro hizmet içinde tutarsız olmaz — yine "hazır olarak olayı yayımlamak" işaretlendiğinden ve Hizmetleri rest göre sonunda tutarlı hale gelecektir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-153">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="07ad3-154">Her zaman işlemler veya tümleştirme olaylarını durumunu denetleme arka plan işleri sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-154">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="07ad3-155">İş "olay yayımlamaya hazır" durumda bir olay bulursa, bu olay olay veri yoluna yeniden yayımlamayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ad3-155">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="07ad3-156">Bu yaklaşımda, yalnızca her kaynak mikro hizmet tümleştirme olaylarını ve diğer mikro veya dış sistemleri ile iletişim kurmak istediğiniz olayları kalıcı olduğunu dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="07ad3-156">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="07ad3-157">Buna karşılık, tam bir ES sistemde, tüm etki alanı olayları de depolar.</span><span class="sxs-lookup"><span data-stu-id="07ad3-157">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="07ad3-158">Bu nedenle, bu dengeli bir Basitleştirilmiş ES sistemi yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-158">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="07ad3-159">Bunların geçerli durumu ile tümleştirme olaylarının bir listesi gerekir ("yayımlamak için"yayımlanan karşı"hazır").</span><span class="sxs-lookup"><span data-stu-id="07ad3-159">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="07ad3-160">Ancak bu durumu tümleştirme olaylarını uygulamak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-160">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="07ad3-161">Ve tam bir ES sisteminde olduğu gibi bu yaklaşım, işlemsel veritabanında olayları olarak tüm etki alanı verilerini depolamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="07ad3-161">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="07ad3-162">İlişkisel veritabanı zaten kullanıyorsanız, tümleştirme olayları depolamak için bir işlem tablo kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ad3-162">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="07ad3-163">Uygulamanızdaki kararlılık elde etmek için yerel hareketlerini temel alarak iki adımlı bir işlem kullanın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-163">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="07ad3-164">Temel olarak, etki alanı varlıklarınızı sahip olduğu aynı veritabanında bir IntegrationEvent tablo sahip.</span><span class="sxs-lookup"><span data-stu-id="07ad3-164">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="07ad3-165">Bu tablo dahil böylece kararlılık elde etmek için bir sigorta tümleştirme olaylarını etki alanı verilerinizi yürütülmekte olan aynı işlemleri kalıcı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-165">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="07ad3-166">Adım adım işlemi aşağıdaki gibi gider: uygulama yerel veritabanı işlemi başlar.</span><span class="sxs-lookup"><span data-stu-id="07ad3-166">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="07ad3-167">Etki alanı varlıklarınızı durumunu güncelleştirir ve bir olay tümleştirme olay tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="07ad3-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="07ad3-168">Son olarak, işlem kaydeder.</span><span class="sxs-lookup"><span data-stu-id="07ad3-168">Finally, it commits the transaction.</span></span> <span data-ttu-id="07ad3-169">İstenen kararlılık alın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-169">You get the desired atomicity.</span></span>

<span data-ttu-id="07ad3-170">Olayları yayımlama adımları uygularken bu seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="07ad3-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="07ad3-171">Sağa hareket uyguladıktan sonra tümleştirme olay yayımlayın ve başka bir yerel işlem yayımlanmakta olarak tablo olayları işaretlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="07ad3-172">Sonra uzak mikro sorunları durumunda tümleştirme olaylarını izlemek için yalnızca bir yapı tabloyu kullanın ve saklı tümleştirme olaylara dayanarak telafi izin eylemleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="07ad3-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="07ad3-173">Tablo, kuyruk bir tür olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="07ad3-174">Ayrı uygulama iş parçacığı veya işlem tümleştirme olay tablo sorguları, olayları olay veri yoluna yayımlar ve olayları yayımlanmış olarak işaretlemek için yerel bir işlem kullanır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="07ad3-175">Şekil 8-22 Bu yaklaşımlardan biri için Mimari gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-175">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="07ad3-176">**Şekil 8-22**.</span><span class="sxs-lookup"><span data-stu-id="07ad3-176">**Figure 8-22**.</span></span> <span data-ttu-id="07ad3-177">Olayları olay yoluna yayımlarken Atom oranı</span><span class="sxs-lookup"><span data-stu-id="07ad3-177">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="07ad3-178">Şekil 8-22'de gösterilen yaklaşım denetleme ve yayımlanan tümleştirme olaylarını başarısını onaylayan sorumlu olduğu bir ek çalışan mikro hizmet eksik.</span><span class="sxs-lookup"><span data-stu-id="07ad3-178">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="07ad3-179">Başarısız olması durumunda, bu ek denetleyicisi çalışan mikro hizmet tablosundan olayları okumak ve bunları yeniden yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-179">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="07ad3-180">İkinci yaklaşımı hakkında: sırası olarak olay günlüğüne tabloyu kullanın ve her zaman bir çalışan mikro hizmet iletileri yayımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-180">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="07ad3-181">Bu durumda, işlem Şekil 8-23'te gibi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-181">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="07ad3-182">Tek kaynak olayları yayımlarken tablodur ve bu ek mikro hizmet gösterir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-182">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="07ad3-183">**Şekil 8-23**.</span><span class="sxs-lookup"><span data-stu-id="07ad3-183">**Figure 8-23**.</span></span> <span data-ttu-id="07ad3-184">Olayları olay veri yoluna çalışan mikro hizmet ile yayımlarken Atom oranı</span><span class="sxs-lookup"><span data-stu-id="07ad3-184">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="07ad3-185">Kolaylık olması için eShopOnContainers örnek olay bus ilk yaklaşımda (hiçbir ek işlemler veya denetleyicisi mikro) kullanır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-185">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="07ad3-186">Ancak, eShopOnContainers tüm olası hata durumları işlenmemesinin.</span><span class="sxs-lookup"><span data-stu-id="07ad3-186">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="07ad3-187">Buluta dağıtılan gerçek bir uygulamada denetleyip mantığı yeniden sorunları sonuçta ortaya çıkar ve uygulamanız gereken olgu çekirdeğin gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-187">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="07ad3-188">Tek bir olay veri yolu yayımlarken, olayları kaynağı olarak bu tabloyu varsa sırası olarak tabloyu kullanarak ilk yaklaşım daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-188">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="07ad3-189">Olay Veriyolu aracılığıyla tümleştirme olaylarını yayımlarken kararlılık uygulama</span><span class="sxs-lookup"><span data-stu-id="07ad3-189">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="07ad3-190">Aşağıdaki kod, birden çok DbContext nesnelerini içeren tek bir işlem nasıl oluşturabileceğinizi gösterir — güncelleştirilmekte özgün veri ile ilgili bir içerik ve IntegrationEventLog tabloya ilgili ikinci bağlamı.</span><span class="sxs-lookup"><span data-stu-id="07ad3-190">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="07ad3-191">Aşağıdaki örnek kod işlemde veritabanı bağlantılarını kodun çalıştığı zaman herhangi bir sorun varsa esnek olmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="07ad3-191">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="07ad3-192">Veritabanlarını sunucular arasında taşıma Azure SQL DB gibi bulut tabanlı sistemlerde gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-192">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="07ad3-193">Birden çok bağlamlarında dayanıklı işlemleri uygulamak için bkz: [dayanıklı Entity Framework Çekirdek SQL bağlantıları uygulama](#implementing_resilient_EFCore_SQL_conns) bu kılavuzda daha sonra bölüm.</span><span class="sxs-lookup"><span data-stu-id="07ad3-193">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](#implementing_resilient_EFCore_SQL_conns) section later in this guide.</span></span>

<span data-ttu-id="07ad3-194">Daha anlaşılır olması için aşağıdaki örnek kod tek bir parça tüm işlem gösterir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-194">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="07ad3-195">Ancak, eShopOnContainers uygulama gerçekte bulunanad ve sürdürmek daha kolay şekilde bu mantığı birden çok sınıflara bölme.</span><span class="sxs-lookup"><span data-stu-id="07ad3-195">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate) 
{
  var catalogItem = 
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id == 
                                                               productToUpdate.Id); 
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false; 
  IntegrationEvent priceChangedEvent = null; 

  if (catalogItem.Price != productToUpdate.Price) 
          raiseProductPriceChangedEvent = true; 

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price; 
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price, 
                                                                  oldPrice); 
  }
  // Update current product
  catalogItem = productToUpdate; 

  // Just save the updated product if the Product's Price hasn't changed.
  if !(raiseProductPriceChangedEvent) 
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog 
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem); 
           await _catalogContext.SaveChangesAsync();

           // Save to EventLog only if product price changed
           if(raiseProductPriceChangedEvent) 
               await _integrationEventLogService.SaveEventAsync(priceChangedEvent); 

           transaction.Commit();
        }   

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

<span data-ttu-id="07ad3-196">ProductPriceChangedIntegrationEvent tümleştirme olay oluşturulduktan sonra özgün etki alanı işlemi (güncelleştirme katalog öğesi) depolar işlem Kalıcılık olayın olay günlüğüne tabloda de içerir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-196">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="07ad3-197">Bu tek bir işlem yapar ve, her zaman gönderilen olay iletileri olup olmadığını denetlemek kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="07ad3-197">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="07ad3-198">Olay günlüğü tablosu, aynı veritabanında yerel bir işlem kullanarak özgün veritabanı işlemi ile otomatik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-198">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="07ad3-199">İşlemleri başarısız olursa, bir özel durum ve işlem bu nedenle etki alanı işlemleri ve gönderilen olay iletileri arasında tutarlılığı koruma herhangi bir Tamamlanan işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-199">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="07ad3-200">Aboneliklerden ileti alma: alıcı mikro olay işleyicileri</span><span class="sxs-lookup"><span data-stu-id="07ad3-200">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="07ad3-201">Olay aboneliği mantığı ek olarak (örneğin, bir geri çağırma yöntemi) tümleştirme olay işleyicileri için iç kod uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-201">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="07ad3-202">Belirli bir türde olay iletileri nereye alınan ve işlenen belirlediğiniz olay işleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-202">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="07ad3-203">Olay işleyici ilk olay yolundan olay örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-203">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="07ad3-204">Ardından yayılıyor ve alıcı mikro hizmet durumunda bir değişiklik olarak olayı kalıcı tümleştirme olay, ilgili işlenmek üzere bileşen bulur.</span><span class="sxs-lookup"><span data-stu-id="07ad3-204">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="07ad3-205">Örneğin, ProductPriceChanged olay Kataloğu mikro kaynaklanıyorsa Sepeti mikro ele alınır ve aşağıdaki kodda gösterildiği gibi bu alıcı Sepeti mikro hizmet olarak iyi durumda değiştirir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-205">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="07ad3-206">Ürün Sepeti örnekleri hiçbirinde var olup olmadığını doğrulamak olay işleyicisini gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-206">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="07ad3-207">Ayrıca, her ilgili Sepeti satır maddesi için madde fiyatı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-207">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="07ad3-208">Son olarak, Şekil 8-24'te gösterildiği gibi fiyat değişikliği hakkında kullanıcıya görüntülenecek bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="07ad3-208">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="07ad3-209">**Şekil 8-24**.</span><span class="sxs-lookup"><span data-stu-id="07ad3-209">**Figure 8-24**.</span></span> <span data-ttu-id="07ad3-210">Bir öğe fiyat değişikliği bir sepetteki tümleştirme olaylar tarafından iletilen olarak görüntüleme</span><span class="sxs-lookup"><span data-stu-id="07ad3-210">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="07ad3-211">Güncelleştirme iletisini olayları benzersizlik</span><span class="sxs-lookup"><span data-stu-id="07ad3-211">Idempotency in update message events</span></span>

<span data-ttu-id="07ad3-212">Bir önemli güncelleştirme iletisi olayları denenmek üzere ileti iletişimde herhangi bir noktada başarısız olmasına neden yönüdür.</span><span class="sxs-lookup"><span data-stu-id="07ad3-212">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="07ad3-213">Aksi halde bir arka plan görevi zaten, bir yarış durumu oluşturma yayımlanmış bir olay yayımlamayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ad3-213">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="07ad3-214">Idempotent veya bir yinelenen algılayabilir emin olmak için yeterli bilgi sağladıkları güncelleştirmelerin emin olmak için atmak ve geri tek bir yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-214">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="07ad3-215">Daha önce belirtildiği gibi sonuç değiştirmeden bir işlem birden çok kez gerçekleştirilebilir benzersizlik anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-215">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="07ad3-216">İleti bir ortamda, birden çok kez alıcı mikro hizmet için sonucu değiştirmeden teslim edilebilir olayları iletişim kurarken bir olay ıdempotent ise gibi.</span><span class="sxs-lookup"><span data-stu-id="07ad3-216">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="07ad3-217">Bu olay yapısı nedeniyle gerekli olabilir veya yol nedeniyle sistem olayını işler.</span><span class="sxs-lookup"><span data-stu-id="07ad3-217">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="07ad3-218">İleti benzersizlik Mesajlaşma deposu kullanan herhangi bir uygulama, yalnızca olay bus deseni uygulayan uygulamaları önemlidir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-218">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="07ad3-219">Yalnızca bu verileri tabloda değilse, bir tabloya veri ekleyen bir SQL deyimi bir ıdempotent işlem örnektir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-219">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="07ad3-220">SQL deyimini ekleyin çalıştırdığınız kaç kez önemli değildir; Sonuç aynı olacaktır — tablo verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-220">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="07ad3-221">Bu gibi benzersizlik iletilerin potansiyel olarak gönderilebilir, iletileri ile ilgilenirken gerekirse ve bu nedenle işlenen defadan de olabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-221">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="07ad3-222">Örneğin, bir gönderici tam olarak aynı iletiyi birden çok kez göndermek yeniden deneme mantığı neden olursa, ıdempotent olduğundan emin olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-222">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="07ad3-223">Tasarım ıdempotent iletileri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="07ad3-223">It is possible to design idempotent messages.</span></span> <span data-ttu-id="07ad3-224">Örneğin, bildiren bir olay oluşturabilirsiniz "Ürün Fiyat kümesine \$25" yerine "eklemek \$Ürün Fiyat 5."</span><span class="sxs-lookup"><span data-stu-id="07ad3-224">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="07ad3-225">İlk kez herhangi bir sayıda güvenli bir şekilde işlem gerçekleştirilemedi ve sonucu aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-225">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="07ad3-226">Bu ikinci bir ileti için doğru değil.</span><span class="sxs-lookup"><span data-stu-id="07ad3-226">That is not true for the second message.</span></span> <span data-ttu-id="07ad3-227">Ancak, hatta ilk durumda, ilk olay sistem da daha yeni bir fiyat değişiklik olayı gönderilen ve yeni fiyat üzerine çünkü işlem istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ad3-227">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="07ad3-228">Başka bir örnek, birden çok aboneye yayılmasını sipariş tamamlanan olay olabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-228">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="07ad3-229">Aynı sırada tamamlandı olayı için yinelenen ileti olayları olsa bile sipariş bilgilerini yalnızca bir kez, diğer sistemlere güncelleştirilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-229">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="07ad3-230">Her olay alıcı yalnızca bir kez işlenir zorlar mantığı oluşturabilmesi için olay başına kimlik çeşit sağlamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-230">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="07ad3-231">Bazı ileti kendiliğinden ıdempotent işlemesidir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-231">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="07ad3-232">Bir sistem görüntüsü küçük resimleri oluşturursa, örneğin, ileti hakkında ve oluşturulan küçük işlenir kaç kez önemli değil; sonucu küçük resimler oluşturulur ve her zaman aynıdır. ' dir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-232">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="07ad3-233">Diğer taraftan, kredi kartı kaydedilecek ödeme ağ geçidi çağırma gibi işlemler ıdempotent hiç olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-233">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="07ad3-234">Bu durumlarda, birden çok kez ileti işlenirken beklediğiniz etkin olduğundan emin olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-234">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="07ad3-235">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="07ad3-235">Additional resources</span></span>

-   <span data-ttu-id="07ad3-236">**İleti benzersizlik uygularken** (Bu sayfadaki alt başlık) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="07ad3-236">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="07ad3-237">Yinelenenleri tümleştirme olay iletileri</span><span class="sxs-lookup"><span data-stu-id="07ad3-237">Deduplicating integration event messages</span></span>

<span data-ttu-id="07ad3-238">Message olayları gönderilen ve farklı düzeylerde abonelik başına yalnızca bir kez işlenir emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ad3-238">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="07ad3-239">Kullanmakta olduğunuz Mesajlaşma altyapısı tarafından sunulan bir yinelenenleri kaldırma özelliğini kullanan bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="07ad3-239">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="07ad3-240">Başka bir özel mantık, hedef mikro uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-240">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="07ad3-241">Hem aktarım düzeyinde ve uygulama düzeyinde doğrulamaları sahip en iyi sonucu istenir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-241">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="07ad3-242">Message olayları EventHandler düzeyinde yinelenenleri</span><span class="sxs-lookup"><span data-stu-id="07ad3-242">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="07ad3-243">Bir olay herhangi bir alıcı tarafından yalnızca bir kez işlenir emin olmak için bir olay işleyicileri ileti olayları işlerken belirli mantığı uygulayarak yoludur.</span><span class="sxs-lookup"><span data-stu-id="07ad3-243">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="07ad3-244">Örneğin, olan eShopOnContainers uygulamada kullanılan yaklaşımı nde gördüğünüz [kaynak kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) CreateOrderCommand komutu aldığında OrdersController sınıfının.</span><span class="sxs-lookup"><span data-stu-id="07ad3-244">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="07ad3-245">(Bu durumda değil ileti tabanlı komutu bir HTTP isteği komutu kullanırız ancak ileti tabanlı komut ıdempotent yapmanız mantığı benzer.)</span><span class="sxs-lookup"><span data-stu-id="07ad3-245">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="07ad3-246">RabbitMQ kullanırken yinelenenleri iletileri</span><span class="sxs-lookup"><span data-stu-id="07ad3-246">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="07ad3-247">Aralıklı ağ hataları oluştuğunda iletileri çoğaltılabilir ve ileti alıcı bu yinelenen iletileri işlemek hazır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-247">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="07ad3-248">Mümkünse, alıcılar iletileri bunları yinelenenleri kaldırma ile açıkça işleme daha iyi bir ıdempotent şekilde işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-248">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="07ad3-249">Göre [RabbitMQ belgelerine](https://www.rabbitmq.com/reliability.html#consumer), "bir ileti bir tüketici teslim ve (tüketici bağlantı kesildi, örneğin önce onu onaylanan değil çünkü) daha sonra yeniden kuyruğa alınması durumunda RabbitMQ üzerinde redelivered bayrağı ayarlayacak Bunu (', aynı tüketici ya da farklı bir olup olmadığını) yeniden teslim edildiğinde.</span><span class="sxs-lookup"><span data-stu-id="07ad3-249">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="07ad3-250">"Redelivered" bayrağı ayarlarsanız, ileti zaten işlenmiş çünkü alıcı, dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-250">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="07ad3-251">Ancak bu garanti edilmez; ağ sorunları nedeniyle ileti Aracısı belki de sol sonra ileti hiçbir zaman alıcı ulaştı.</span><span class="sxs-lookup"><span data-stu-id="07ad3-251">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="07ad3-252">"Redelivered" bayrağı ayarlanmamış olduğundan, diğer yandan, bu iletiyi birden çok kez gönderildiğini değil sağlanır.</span><span class="sxs-lookup"><span data-stu-id="07ad3-252">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="07ad3-253">Bu nedenle, yalnızca ileti "redelivered" bayrağı ayarlarsanız iletileri veya işlem iletileri ıdempotent şekilde yararlanmanın alıcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="07ad3-253">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="07ad3-254">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="07ad3-254">Additional resources</span></span>

-   <span data-ttu-id="07ad3-255">**Çatallanmış eShopOnContainers NServiceBus (belirli yazılım) kullanma**
    [*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="07ad3-255">**Forked eShopOnContainers using NServiceBus (Particular Software)**
[*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)</span></span>

-   <span data-ttu-id="07ad3-256">**Olay tabanlı Mesajlaşma**
    [*http://soapatterns.org/design\_desen/olay\_güdümlü\_Mesajlaşma*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="07ad3-256">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="07ad3-257">**Jimmy Bogard. Esnekliği doğru yeniden düzenleme: Bağlantı değerlendirme**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="07ad3-257">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="07ad3-258">**Kanal yayımlama-abone olma**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="07ad3-258">**Publish-Subscribe channel**
[*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="07ad3-259">**Sınırlanmış bağlamları arasında iletişim**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="07ad3-259">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="07ad3-260">**Nihai tutarlılık**
    [*https://en.wikipedia.org/wiki/Eventual\_tutarlılık*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="07ad3-260">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="07ad3-261">**Elmas kahverengi. Tümleştirme stratejileri bağlamları sınırlanmış**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="07ad3-261">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="07ad3-262">**Chris Richardson. Toplamalar, olay kaynak belirleme ve CQRS - bölüm 2 kullanarak işlem mikro geliştirme**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="07ad3-262">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="07ad3-263">**Chris Richardson. Olay Sourcing düzeni**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="07ad3-263">**Chris Richardson. Event Sourcing pattern**
[*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="07ad3-264">**Olay kaynak Hizmeti'nden Tanıtımı**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="07ad3-264">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="07ad3-265">**Olay deposu veritabanı**.</span><span class="sxs-lookup"><span data-stu-id="07ad3-265">**Event Store database**.</span></span> <span data-ttu-id="07ad3-266">Resmi sitesi.</span><span class="sxs-lookup"><span data-stu-id="07ad3-266">Official site.</span></span>
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   <span data-ttu-id="07ad3-267">**Can Nommensen. Mikro için olay denetimli veri yönetimi**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span><span class="sxs-lookup"><span data-stu-id="07ad3-267">**Patrick Nommensen. Event-Driven Data Management for Microservices**
*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span></span>

-   <span data-ttu-id="07ad3-268">**CAP Teoremi**
    [*https://en.wikipedia.org/wiki/CAP\_Teoremi*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="07ad3-268">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="07ad3-269">**CAP Teoremi nedir?**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="07ad3-269">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="07ad3-270">**Veri tutarlılığı Primer**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="07ad3-270">**Data Consistency Primer**
[*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="07ad3-271">**Saling rick. CAP Teoremi: "Her şeyi farklı Bulut ve Internet olmasının"**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="07ad3-271">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="07ad3-272">**Eric Brewer. CAP üzeri on iki yıllık: "Kurallar" nasıl değiştiğini**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="07ad3-272">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="07ad3-273">**Dış (DTC) işlemlere katılan** (MSMQ) [  *https://msdn.microsoft.com/library/ms978430.aspx \#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="07ad3-273">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="07ad3-274">**Azure Service Bus. Aracılı Mesajlaşma: Yinelenen algılama**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="07ad3-274">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="07ad3-275">**Güvenilirlik Kılavuzu** (RabbitMQ belge) [  *https://www.rabbitmq.com/reliability.html \#tüketici*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="07ad3-275">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="07ad3-276">[Önceki] (rabbitmq-event-bus-development-test-environment.md) [sonraki] (test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="07ad3-276">[Previous] (rabbitmq-event-bus-development-test-environment.md) [Next] (test-aspnet-core-services-web-apps.md)</span></span>
