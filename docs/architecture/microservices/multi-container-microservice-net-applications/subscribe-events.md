---
title: Olaylara abone olma
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Tümleştirme etkinliklerini yayımlama ve abone etme ayrıntılarını anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: 426dcebe175e9db9a02bcdb2f21ad039154a7bda
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888221"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="f7feb-103">Olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="f7feb-103">Subscribing to events</span></span>

<span data-ttu-id="f7feb-104">Etkinlik veri toplarını kullanmanın ilk adımı, mikro hizmetlere almak istedikleri etkinliklere abone olmaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="f7feb-105">Bu alıcı mikro hizmetler yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="f7feb-106">Aşağıdaki basit kod, hizmeti başlatırken her alıcı mikro hizmetinin ne `Startup` leri uygulaması gerektiğini (yani sınıfta) gösterir, böylece ihtiyaç duyduğu olaylara abone olur.</span><span class="sxs-lookup"><span data-stu-id="f7feb-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="f7feb-107">Bu durumda, `basket-api` mikro hizmet `ProductPriceChangedIntegrationEvent` ve `OrderStartedIntegrationEvent` mesajları abone olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-107">In this case, the `basket-api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="f7feb-108">Örneğin, `ProductPriceChangedIntegrationEvent` etkinliğe abone olurken, sepet mikro hizmetini ürün fiyatındaki herhangi bir değişiklikten haberdar eder ve bu ürün kullanıcının sepetindeyse kullanıcıyı değişiklik konusunda uyarmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7feb-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user's basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="f7feb-109">Bu kod çalıştırdıktan sonra, abone microservice RabbitMQ kanalları üzerinden dinliyor olacak.</span><span class="sxs-lookup"><span data-stu-id="f7feb-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="f7feb-110">ProductPriceChangedIntegrationEvent türünden herhangi bir ileti geldiğinde, kod kendisine geçirilen olay işleyicisini çağırır ve olayı işler.</span><span class="sxs-lookup"><span data-stu-id="f7feb-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="f7feb-111">Etkinlik otobüslerinden etkinlikleri yayımlama</span><span class="sxs-lookup"><span data-stu-id="f7feb-111">Publishing events through the event bus</span></span>

<span data-ttu-id="f7feb-112">Son olarak, ileti gönderen (başlangıç mikrohizmeti) aşağıdaki örneğe benzer kodile tümleştirme olaylarını yayımlar.</span><span class="sxs-lookup"><span data-stu-id="f7feb-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="f7feb-113">(Bu, atomikliği hesaba katmayan basitleştirilmiş bir örnektir.) Bir olay, genellikle kaynak mikrohizmetten veri veya işlem işledikten hemen sonra, birden çok mikro hizmet arasında yayılması gerektiğinde benzer bir kod uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="f7feb-114">İlk olarak, olay veri merkezi uygulama nesnesi (RabbitMQ'ye veya servis veri yolundan dayalı olarak) aşağıdaki kodda olduğu gibi denetleyici oluşturucuya enjekte edilir:</span><span class="sxs-lookup"><span data-stu-id="f7feb-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="f7feb-115">Daha sonra, UpdateProduct yönteminde olduğu gibi, denetleyicinizin yöntemlerinden kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="f7feb-115">Then you use it from your controller's methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("items")]
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

<span data-ttu-id="f7feb-116">Bu durumda, başlangıç microservice basit bir CRUD microservice olduğundan, bu kod bir Web API denetleyicisi içine doğru yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="f7feb-117">CQRS yaklaşımları kullanırken olduğu gibi daha gelişmiş mikrohizmetlerde, `CommandHandler` `Handle()` yöntem içinde sınıfta uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="f7feb-118">Etkinlik otobüsüne yayın yaparken atomiklik ve esneklik tasarlama</span><span class="sxs-lookup"><span data-stu-id="f7feb-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="f7feb-119">Tümleştirme olaylarını olay veri tobununuz gibi dağıtılmış bir ileti sistemi üzerinden yayımladığınızda, özgün veritabanını atomik olarak güncelleştirme ve bir olayı yayımlama sorunu yla karşı lanırsınız (diğer bir şekilde, her iki işlem de tamamlanır veya hiçbiri).</span><span class="sxs-lookup"><span data-stu-id="f7feb-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="f7feb-120">Örneğin, daha önce gösterilen basitleştirilmiş örnekte, ürün fiyatı değiştirildiğinde kod veritabanına veri adatır ve ardından bir ProductPriceChangedIntegrationEvent iletisi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="f7feb-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="f7feb-121">Başlangıçta, bu iki operasyonun atomik olarak yapılması gerekli görünebilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="f7feb-122">Ancak, [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)gibi eski sistemlerde yaptığınız gibi veritabanı ve ileti aracısını içeren dağıtılmış bir işlem kullanıyorsanız, [bu, CAP teoremi](https://www.quora.com/What-Is-CAP-Theorem-1)tarafından açıklanan nedenlerle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f7feb-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="f7feb-123">Temel olarak, ölçeklenebilir ve yüksek kullanılabilir sistemler oluşturmak için mikro hizmetleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7feb-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="f7feb-124">Biraz basitleştiren CAP teoremi, sürekli olarak kullanılabilir, güçlü bir şekilde tutarlı *ve* herhangi bir bölüme karşı toleranslı bir (dağıtılmış) veritabanı (veya kendi modeline sahip bir microservice) oluşturamayacağınızı söyler.</span><span class="sxs-lookup"><span data-stu-id="f7feb-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that's continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="f7feb-125">Bu üç özelliklerden ikisini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="f7feb-126">Mikro hizmetler tabanlı mimarilerde kullanılabilirlik ve toleransı seçmeli ve güçlü tutarlılığı vurgulamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-126">In microservices-based architectures, you should choose availability and tolerance, and you should de-emphasize strong consistency.</span></span> <span data-ttu-id="f7feb-127">Bu nedenle, çoğu modern mikrohizmet tabanlı uygulamalarda, [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)ile Windows Dağıtılmış İşlem Koordinatörü'ne (DTC) dayalı dağıtılmış hareketleri uyguladığınızda yaptığınız gibi, genellikle iletide [dağıtılmış hareketleri](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) kullanmak istemezsinüz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="f7feb-128">İlk sayıya ve onun örneğine geri dönelim.</span><span class="sxs-lookup"><span data-stu-id="f7feb-128">Let's go back to the initial issue and its example.</span></span> <span data-ttu-id="f7feb-129">Veritabanı güncelleştirildikten sonra hizmet çöküyorsa (bu durumda, kod `_context.SaveChangesAsync()`satırından hemen sonra), ancak tümleştirme olayı yayımlanmadan önce, genel sistem tutarsız olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-129">If the service crashes after the database is updated (in this case, right after the line of code with `_context.SaveChangesAsync()`), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="f7feb-130">Bu, uğraştığınız belirli iş işlemine bağlı olarak iş açısından kritik olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="f7feb-131">Mimari bölümünde daha önce de belirtildiği gibi, bu sorunla başa çıkmak için çeşitli yaklaşımlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="f7feb-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="f7feb-132">Tam [Olay Kaynak desen](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)kullanarak .</span><span class="sxs-lookup"><span data-stu-id="f7feb-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="f7feb-133">[İşlem günlüğü madenciliği kullanma.](https://www.scoop.it/t/sql-server-transaction-log-mining)</span><span class="sxs-lookup"><span data-stu-id="f7feb-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="f7feb-134">Giden [Kutusu deseni](https://www.kamilgrzybek.com/design/the-outbox-pattern/)kullanma.</span><span class="sxs-lookup"><span data-stu-id="f7feb-134">Using the [Outbox pattern](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span></span> <span data-ttu-id="f7feb-135">Bu, tümleştirme olaylarını depolamak (yerel hareketi genişletmek) için bir işlem tablosudur.</span><span class="sxs-lookup"><span data-stu-id="f7feb-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="f7feb-136">Bu senaryo için, tam Olay Kaynak (ES) desen kullanarak en iyi yaklaşımlardan biridir, değilse *en* iyi.</span><span class="sxs-lookup"><span data-stu-id="f7feb-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="f7feb-137">Ancak, birçok uygulama senaryosunda, tam bir ES sistemi uygulayamayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="f7feb-138">ES, geçerli durum verilerini depolamak yerine yalnızca etki alanı olaylarını işlem veritabanınızda depolamak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="f7feb-139">Yalnızca etki alanı olaylarını depolamanın, sisteminizin geçmişine sahip olması ve geçmişte herhangi bir anda sisteminizin durumunu belirleyebilmesi gibi büyük avantajları olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="f7feb-140">Ancak, tam bir ES sistemi uygulamak, sisteminizin çoğunu yeniden yeniden mimarlandırmanızı gerektirir ve diğer birçok karmaşıklığı ve gereksinimi sunar.</span><span class="sxs-lookup"><span data-stu-id="f7feb-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="f7feb-141">Örneğin, [Olay Mağazası](https://eventstore.org/)gibi olay kaynağı için özel olarak yapılmış bir veritabanı veya Azure Cosmos DB, MongoDB, Cassandra, CouchDB veya RavenDB gibi belge yönelimli bir veritabanı kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="f7feb-142">ES bu sorun için harika bir yaklaşımdır, ancak olay kaynak konusunda zaten aşina değilseniz en kolay çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="f7feb-143">Hareket günlüğü madenciliği kullanma seçeneği başlangıçta saydam görünüyor.</span><span class="sxs-lookup"><span data-stu-id="f7feb-143">The option to use transaction log mining initially looks transparent.</span></span> <span data-ttu-id="f7feb-144">Ancak, bu yaklaşımı kullanmak için, mikro hizmetIN SQL Server işlem günlüğü gibi RDBMS işlem günlüğünüze birleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="f7feb-145">Bu muhtemelen arzu edilmez.</span><span class="sxs-lookup"><span data-stu-id="f7feb-145">This is probably not desirable.</span></span> <span data-ttu-id="f7feb-146">Başka bir dezavantajı, işlem günlüğüne kaydedilen alt düzey güncelleştirmelerin üst düzey tümleştirme olaylarınızla aynı düzeyde olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="f7feb-147">Bu nedenle, bu işlem günlüğü işlemleri ters mühendislik işlemi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="f7feb-148">Dengeli bir yaklaşım, işlem veritabanı tablosu nun ve basitleştirilmiş ES deseninin bir karışımıdır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="f7feb-149">Tümleştirme olayları tablosuna işledirirken özgün olayda ayarlayacağınız "olayı yayımlamaya hazır" gibi bir durum kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-149">You can use a state such as "ready to publish the event," which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="f7feb-150">Daha sonra etkinliği etkinlik otobüsüne yayımlamaya çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="f7feb-151">Yayımlama olayı eylemi başarılı olursa, kaynak hizmetinde başka bir işlem başlatın ve durumu "etkinliği yayımlamaya hazır"dan "zaten yayımlanmış olay"a taşırsınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from "ready to publish the event" to "event already published."</span></span>

<span data-ttu-id="f7feb-152">Veri veri sayında yayımlama olayı eylemi başarısız olursa, veriler yine de başlangıç mikrohizmeti nde tutarsız olmayacaktır-yine de "etkinliği yayımlamaya hazır" olarak işaretlenir ve hizmetlerin geri kalanıyla ilgili olarak, sonunda tutarlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as "ready to publish the event," and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="f7feb-153">Her zaman geçmiş işleri işlemlerin veya tümleştirme olaylarıdurumunu denetleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="f7feb-154">İş "olayı yayımlamaya hazır" durumunda bir olay bulursa, bu olayı olay veri netosu yla yeniden yayımlamayı deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-154">If the job finds an event in the "ready to publish the event" state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="f7feb-155">Bu yaklaşımla, yalnızca her başlangıç mikro hizmeti için tümleştirme olaylarını ve yalnızca diğer mikro hizmetlere veya harici sistemlere iletmek istediğiniz olayları devam ettirebildiğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7feb-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="f7feb-156">Buna karşılık, tam bir ES sisteminde, tüm etki alanı olaylarını da saklarsınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="f7feb-157">Bu nedenle, bu dengeli yaklaşım basitleştirilmiş bir ES sistemidir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="f7feb-158">Geçerli durumları yla tümleştirme olaylarının bir listesine ihtiyacınız vardır ("yayımlamaya hazır" ile "yayımlanmış").</span><span class="sxs-lookup"><span data-stu-id="f7feb-158">You need a list of integration events with their current state ("ready to publish" versus "published").</span></span> <span data-ttu-id="f7feb-159">Ancak, tümleştirme olayları için bu durumları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="f7feb-160">Ve bu yaklaşımda, tüm etki alanı verilerinizi tam bir ES sisteminde olduğu gibi işlem veritabanında olay olarak depolamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f7feb-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="f7feb-161">İlişkisel bir veritabanı zaten kullanıyorsanız, tümleştirme olaylarını depolamak için bir işlem tablosu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="f7feb-162">Uygulamanızda atomikliği sağlamak için yerel işlemlere dayalı iki aşamalı bir işlem kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="f7feb-163">Temel olarak, etki alanı varlıklarınızın bulunduğu aynı veritabanında bir IntegrationEvent tablonuz vardır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="f7feb-164">Bu tablo, kalıcı tümleştirme olaylarını etki alanı verilerinizi işleyen aynı işlemlere dahil etmek için atomikliğe ulaşmak için bir sigorta olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="f7feb-165">Adım adım, süreç şöyle devam eder:</span><span class="sxs-lookup"><span data-stu-id="f7feb-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="f7feb-166">Uygulama yerel bir veritabanı hareketi başlar.</span><span class="sxs-lookup"><span data-stu-id="f7feb-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="f7feb-167">Daha sonra etki alanı varlıklarınızın durumunu güncelleştirir ve tümleştirme olayı tablosuna bir olay ekler.</span><span class="sxs-lookup"><span data-stu-id="f7feb-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="f7feb-168">Son olarak, bu işlem yapar, böylece istenilen atomiklik olsun ve sonra</span><span class="sxs-lookup"><span data-stu-id="f7feb-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="f7feb-169">Olayı bir şekilde (sonraki) yayımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="f7feb-170">Olayları yayımlama adımlarını uygularken şu seçeneklere sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7feb-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="f7feb-171">İşlemi işledikten hemen sonra tümleştirme olayını yayımlayın ve tablodaki olayları yayımlanmış gibi işaretlemek için başka bir yerel işlem kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7feb-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="f7feb-172">Ardından, uzak mikro hizmetlerdeki sorunlar durumunda tümleştirme olaylarını izlemek ve depolanan tümleştirme olaylarını temel alan telafi edici eylemler gerçekleştirmek için tabloyu yalnızca bir yapı olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7feb-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="f7feb-173">Tabloyu sıra türü olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7feb-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="f7feb-174">Ayrı bir uygulama iş parçacığı veya işlem tümleştirme olay tablosunu sorgular, olayları olay veri yoluna yayınlar ve sonra olayları yayımlanmış olarak işaretlemek için yerel bir işlem kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="f7feb-175">Şekil 6-22 bu yaklaşımların ilkinin mimarisini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Bir işçi microservice olmadan yayımlarken atomiklik diyagramı.](./media/subscribe-events/atomicity-publish-event-bus.png)

<span data-ttu-id="f7feb-177">**Şekil 6-22**.</span><span class="sxs-lookup"><span data-stu-id="f7feb-177">**Figure 6-22**.</span></span> <span data-ttu-id="f7feb-178">Etkinlik otobüsüne etkinlik yayınlarken atomiklik</span><span class="sxs-lookup"><span data-stu-id="f7feb-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="f7feb-179">Şekil 6-22'de gösterilen yaklaşım, yayınlanan tümleştirme olaylarının başarısını kontrol etmek ve onaylamaktan sorumlu ek bir işçi microservice eksiktir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="f7feb-180">Hata durumunda, bu ek dama işçisi microservice tablodan olayları okuyabilir ve bunları yeniden yayımlayabilir, yani 2 numaralı adımı tekrarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="f7feb-181">İkinci yaklaşım hakkında: EventLog tablosunu sıra olarak kullanır ve iletileri yayımlamak için her zaman bir işçi mikro hizmeti kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f7feb-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="f7feb-182">Bu durumda, işlem Şekil 6-23'te gösterilen gibidir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="f7feb-183">Bu ek bir microservice gösterir ve tablo olayları yayımlarken tek kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Bir işçi microservice ile yayımlarken atomiklik diyagramı.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

<span data-ttu-id="f7feb-185">**Şekil 6-23**.</span><span class="sxs-lookup"><span data-stu-id="f7feb-185">**Figure 6-23**.</span></span> <span data-ttu-id="f7feb-186">Bir işçi microservice ile olay otobüsüne etkinlik yayınlarken atomiklik</span><span class="sxs-lookup"><span data-stu-id="f7feb-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="f7feb-187">Basitlik için, eShopOnContainers örnek ilk yaklaşım (hiçbir ek süreçler veya denetleyici microservices ile) artı olay veri meskenkullanır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="f7feb-188">Ancak, eShopOnContainers örnek tüm olası arıza durumlarda işleme değildir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-188">However, the eShopOnContainers sample is not handling all possible failure cases.</span></span> <span data-ttu-id="f7feb-189">Buluta dağıtılan gerçek bir uygulamada, sorunların eninde sonunda ortaya çıkacağı gerçeğini benimsemeli ve bu denetimi ve yeniden gönderme mantığını uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="f7feb-190">Tabloyu sıra olarak kullanmak, bu tabloyu olay veri tobus aracılığıyla (işçiyle) yayımlarken tek bir olay kaynağı olarak kullanıyorsanız, ilk yaklaşımdan daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="f7feb-191">Tümleştirme olaylarını etkinlik verine aracılığıyla yayınlarken atomikliğin uygulanması</span><span class="sxs-lookup"><span data-stu-id="f7feb-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="f7feb-192">Aşağıdaki kod, birden çok DbContext nesnesini içeren tek bir işlemi (bir bağlam orijinal verilerle ilgili bir bağlam ve IntegrationEventLog tablosuyla ilgili ikinci bağlam) nasıl oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="f7feb-193">Aşağıdaki örnek koddaki işlem, kod çalışırken veritabanına bağlantılarda herhangi bir sorun varsa esnek olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-193">The transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="f7feb-194">Bu, veritabanlarını sunucular arasında taşıyabilecek Azure SQL DB gibi bulut tabanlı sistemlerde gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="f7feb-195">Birden çok bağlam boyunca esnek hareketler uygulamak için, daha sonra bu kılavuzda [esnek Entity Framework SQL bağlantıları uygulama](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f7feb-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="f7feb-196">Netlik için aşağıdaki örnek, tüm işlemi tek bir kod parçasında gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="f7feb-197">Ancak, eShopOnContainers uygulaması refactored ve korumak için daha kolay böylece birden fazla sınıfa bu mantığı böler.</span><span class="sxs-lookup"><span data-stu-id="f7feb-197">However, the eShopOnContainers implementation is refactored and splits this logic into multiple classes so it's easier to maintain.</span></span>

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
  if (!raiseProductPriceChangedEvent)
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

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      _integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="f7feb-198">ProductPriceChangedIntegrationEvent tümleştirme olayı oluşturulduktan sonra, özgün etki alanı işlemini depolayan işlem (katalog öğesini güncelleştirme) olayın EventLog tablosundaki kalıcılığını da içerir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="f7feb-199">Bu, tek bir işlem yapar ve olay iletilerinin gönderilip gönderilmediğini her zaman denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="f7feb-200">Olay günlüğü tablosu, aynı veritabanına karşı yerel bir işlem kullanılarak özgün veritabanı işlemiyle atomik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="f7feb-201">İşlemlerden herhangi biri başarısız olursa, bir özel durum atılır ve işlem tamamlanan herhangi bir işlemi geri alır, böylece etki alanı işlemleri ile tabloya kaydedilen olay iletileri arasında tutarlılık korunur.</span><span class="sxs-lookup"><span data-stu-id="f7feb-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="f7feb-202">Aboneliklerden ileti alma: alıcı mikro hizmetlerdeki olay işleyicileri</span><span class="sxs-lookup"><span data-stu-id="f7feb-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="f7feb-203">Olay abonelik mantığına ek olarak, tümleştirme olay işleyicileri (geri arama yöntemi gibi) için iç kodu uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="f7feb-204">Olay işleyicisi, belirli bir türdeki olay iletilerinin alınıp işlenmeyi nerede belirttiğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="f7feb-205">Olay işleyicisi önce olay veri tonundan bir olay örneği alır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="f7feb-206">Daha sonra, alıcı mikrohizmetinde durum değişikliği olarak olayı yaymak ve sürdürmek, bu tümleştirme olayıyla ilgili olarak işlenecek bileşeni bulur.</span><span class="sxs-lookup"><span data-stu-id="f7feb-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="f7feb-207">Örneğin, Bir ProductPriceChanged olayı katalog microservice kaynaklanıyorsa, sepet microservice ele alınır ve aşağıdaki kodda gösterildiği gibi, bu alıcı sepeti microservice de durumu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="f7feb-208">Olay işleyicisinin, ürünün sepet örneklerinin herhangi birinde bulunup bulunmadığından doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="f7feb-209">Ayrıca, ilgili her sepet satırı öğesi için madde fiyatını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="f7feb-210">Son olarak, Şekil 6-24'te gösterildiği gibi fiyat değişikliği hakkında kullanıcıya görüntülenecek bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7feb-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Kullanıcı sepetindeki fiyat değişikliği bildirimini gösteren bir tarayıcının ekran görüntüsü.](./media/subscribe-events/display-item-price-change.png)

<span data-ttu-id="f7feb-212">**Şekil 6-24**.</span><span class="sxs-lookup"><span data-stu-id="f7feb-212">**Figure 6-24**.</span></span> <span data-ttu-id="f7feb-213">Tümleştirme olayları tarafından iletildiği gibi, bir sepette madde fiyat değişikliğini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f7feb-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="f7feb-214">İleti olaylarını güncelleştirmede idempotency</span><span class="sxs-lookup"><span data-stu-id="f7feb-214">Idempotency in update message events</span></span>

<span data-ttu-id="f7feb-215">İleti olaylarını güncelleştirmenin önemli bir yönü, iletişimin herhangi bir noktasındaki bir hatanın iletinin yeniden denenmesine neden olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="f7feb-216">Aksi takdirde, arka plandaki bir görev, bir yarış koşulu oluşturarak zaten yayımlanmış bir olayı yayımlamaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="f7feb-217">Güncelleştirmelerin iktidarlı olduğundan veya bir yinelenen algılayabildiğinizden, atabildiğinizden ve yalnızca bir yanıt gönderebildiğinizden emin olmak için yeterli bilgi sağladıklarından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f7feb-217">Make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="f7feb-218">Daha önce de belirtildiği gibi, idempotency bir işlem sonucu değiştirmeden birden çok kez yapılabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="f7feb-219">İleti ortamında, olayları iletirken olduğu gibi, bir olay alıcı mikrohizmetinin sonucunu değiştirmeden birden çok kez teslim edilebiliyorsa, idempotenttir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="f7feb-220">Bu, olayın doğası nedeniyle veya sistemin olayı işleme biçimi nedeniyle gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="f7feb-221">İleti idempotency, yalnızca olay veri çileti deseni uygulayan uygulamalarda değil, ileti kullanan her uygulamada önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="f7feb-222">Idempotent bir işlem örneği, yalnızca bu veriler tabloda yoksa, tabloya veri ekleyen bir SQL deyimidir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="f7feb-223">Bu insert SQL deyimini kaç kez çalıştırdığınızın bir önemi yok; sonuç aynı olacaktır-tablo bu verileri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="f7feb-224">İletiler potansiyel olarak gönderilebiliyorsa ve bu nedenle birden fazla kez işlenebilirse, bu gibi idempotency de iletileri ile ilgili olarak gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="f7feb-225">Örneğin, yeniden deneme mantığı gönderenin aynı iletiyi birden çok kez göndermesine neden oluyorsa, bunun etkili olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="f7feb-226">İktidara gelen iletiler tasarlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f7feb-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="f7feb-227">Örneğin, "ürün fiyatına 5 TL eklemek" yerine "ürün fiyatını 25 TL olarak ayarlayın" yazan bir etkinlik oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="f7feb-228">İlk iletiyi herhangi bir kez güvenli bir şekilde işleyebilir ve sonuç aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="f7feb-229">Bu ikinci mesaj için doğru değil.</span><span class="sxs-lookup"><span data-stu-id="f7feb-229">That is not true for the second message.</span></span> <span data-ttu-id="f7feb-230">Ancak ilk durumda bile, ilk olayı işlemek istemeyebilirsiniz, çünkü sistem daha yeni bir fiyat değişikliği olayı da göndermiş olabilir ve yeni fiyatın üzerine bir yazı yazmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="f7feb-231">Başka bir örnek, birden çok aboneye yayılan sipariş tamamlanmış bir olay olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-231">Another example might be an order-completed event that's propagated to multiple subscribers.</span></span> <span data-ttu-id="f7feb-232">Uygulama, aynı sipariş le tamamlanan olay için yinelenen ileti olayları olsa bile, sipariş bilgilerinin diğer sistemlerde yalnızca bir kez güncelleştirdiğinden emin olmak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-232">The app has to make sure that order information is updated in other systems only once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="f7feb-233">Her olayın alıcı başına yalnızca bir kez işlenmesini gerektiren bir mantık oluşturabilmeniz için olay başına bir tür kimliğe sahip olmak uygundur.</span><span class="sxs-lookup"><span data-stu-id="f7feb-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="f7feb-234">Bazı ileti işleme doğal olarak idempotent olduğunu.</span><span class="sxs-lookup"><span data-stu-id="f7feb-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="f7feb-235">Örneğin, bir sistem resim küçük resimleri oluşturuyorsa, oluşturulan küçük resimle ilgili iletinin kaç kez işlendiğiönemli olmayabilir; sonuç küçük resimler oluşturulur ve her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="f7feb-236">Öte yandan, kredi kartından ücret almak için ödeme ağ geçidi aramak gibi işlemler hiç de dedempotent olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="f7feb-237">Bu gibi durumlarda, bir iletiyi birden çok kez işlemenin beklediğiniz etkiye sahip olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f7feb-238">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f7feb-238">Additional resources</span></span>

- <span data-ttu-id="f7feb-239">**Onur mesajı idempotency** </span><span class="sxs-lookup"><span data-stu-id="f7feb-239">**Honoring message idempotency** </span></span>\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="f7feb-240">Tümleştirme olay iletilerini deduplicating</span><span class="sxs-lookup"><span data-stu-id="f7feb-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="f7feb-241">İleti olaylarının farklı düzeylerde abone başına yalnızca bir kez gönderildiğinden ve işlendiğinden emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7feb-241">You can make sure that message events are sent and processed only once per subscriber at different levels.</span></span> <span data-ttu-id="f7feb-242">Bir yol, kullanmakta olduğunuz mesajlaşma altyapısı tarafından sunulan bir çoğaltma özelliğikullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="f7feb-243">Başka bir hedef microservice özel mantık uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="f7feb-244">Hem taşıma düzeyinde hem de uygulama düzeyinde doğrulamalara sahip olmak en iyi bahistir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="f7feb-245">EventHandler düzeyinde ileti olaylarını deduplicating</span><span class="sxs-lookup"><span data-stu-id="f7feb-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="f7feb-246">Bir olayın herhangi bir alıcı tarafından yalnızca bir kez işlendiğinden emin olmak için bir yolu olay işleyicileri ileti olayları işlerken belirli bir mantık uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-246">One way to make sure that an event is processed only once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="f7feb-247">Örneğin, bir `UserCheckoutAcceptedIntegrationEvent` tümleştirme olayı aldığında [UserCheckoutAcceptedIntegrationEventHandler sınıfının kaynak kodunda](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) görebileceğiniz gibi, eShopOnContainers uygulamasında kullanılan yaklaşım bu.</span><span class="sxs-lookup"><span data-stu-id="f7feb-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives a `UserCheckoutAcceptedIntegrationEvent` integration event.</span></span> <span data-ttu-id="f7feb-248">(Bu durumda, `CreateOrderCommand` komut işleyicisine `IdentifiedCommand`göndermeden `eventMsg.RequestId` önce tanımlayıcı olarak bir , bir ile sarılır).</span><span class="sxs-lookup"><span data-stu-id="f7feb-248">(In this case, the `CreateOrderCommand` is wrapped with an `IdentifiedCommand`, using the `eventMsg.RequestId` as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="f7feb-249">RabbitMQ kullanırken iletileri boyama</span><span class="sxs-lookup"><span data-stu-id="f7feb-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="f7feb-250">Aralıklı ağ hataları olduğunda, iletiler çoğaltılabilir ve ileti alıcısının bu yinelenen iletileri işlemek için hazır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="f7feb-251">Mümkünse, alıcılar iletileri açık bir şekilde çoğaltma ile işlemek daha iyi bir idempotent bir şekilde ele almalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="f7feb-252">[RabbitMQ belgelerine](https://www.rabbitmq.com/reliability.html#consumer)göre , "Bir ileti bir tüketiciye teslim edilir ve sonra yeniden sıraya girilirse (örneğin, tüketici bağlantısı düşmeden önce kabul edilmediği için) RabbitMQ yeniden teslim edildiğinde (aynı tüketiciye veya farklı bir mesaja) yeniden teslim edilen bayrağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7feb-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), "If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="f7feb-253">"Yeniden teslim" bayrağı ayarlanmışsa, ileti zaten işlenmiş olabileceğinden alıcı bunu dikkate almalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7feb-253">If the "redelivered" flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="f7feb-254">Ama bu garanti edilmez; ileti, ileti aracısını bıraktıktan sonra, belki de ağ sorunları nedeniyle alıcıya hiç ulaşmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="f7feb-255">Diğer taraftan, "yeniden teslim" bayrağı ayarlanmadıysa, iletinin birden fazla gönderilmediği garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-255">On the other hand, if the "redelivered" flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="f7feb-256">Bu nedenle, alıcının iletileri yalnızca iletide "yeniden teslim" bayrağı ayarlanırsa, iletileri veya işlemleri idempotent bir şekilde devreden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7feb-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the "redelivered" flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f7feb-257">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f7feb-257">Additional resources</span></span>

- <span data-ttu-id="f7feb-258">**NServiceBus (Özel Yazılım) kullanarak Çatallı eShopOnContainers** </span><span class="sxs-lookup"><span data-stu-id="f7feb-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="f7feb-259">**Olay Odaklı Mesajlaşma** </span><span class="sxs-lookup"><span data-stu-id="f7feb-259">**Event Driven Messaging** </span></span>\
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- <span data-ttu-id="f7feb-260">**Jimmy Bogard' ı. Esneklik Doğru Refactoring: Bağlantı Değerlendirme** </span><span class="sxs-lookup"><span data-stu-id="f7feb-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="f7feb-261">**Yayınla-Abone Ol** </span><span class="sxs-lookup"><span data-stu-id="f7feb-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="f7feb-262">**Sınırlı Bağlamlar Arasında İletişim** </span><span class="sxs-lookup"><span data-stu-id="f7feb-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="f7feb-263">**Nihai Tutarlılık** </span><span class="sxs-lookup"><span data-stu-id="f7feb-263">**Eventual Consistency** </span></span>\
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- <span data-ttu-id="f7feb-264">**Philip Brown' ı. Sınırlı Bağlamları Bütünleştirme Stratejileri** </span><span class="sxs-lookup"><span data-stu-id="f7feb-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="f7feb-265">**Chris Richardson' ı. Agregalar, Olay Kaynak ve CQRS Kullanarak İşlemsel Mikrohizmetler Geliştirme - Bölüm 2** </span><span class="sxs-lookup"><span data-stu-id="f7feb-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="f7feb-266">**Chris Richardson' ı. Olay Kaynak deseni** </span><span class="sxs-lookup"><span data-stu-id="f7feb-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="f7feb-267">**Tanıtıcı Etkinlik Kaynak** </span><span class="sxs-lookup"><span data-stu-id="f7feb-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="f7feb-268">**Olay Deposu veritabanı.**</span><span class="sxs-lookup"><span data-stu-id="f7feb-268">**Event Store database**.</span></span> <span data-ttu-id="f7feb-269">Resmi site.</span><span class="sxs-lookup"><span data-stu-id="f7feb-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="f7feb-270">**Patrick Nommensen' ı. Mikro hizmetler için Etkinlik Odaklı Veri Yönetimi** </span><span class="sxs-lookup"><span data-stu-id="f7feb-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="f7feb-271">**CAP Teoremi** </span><span class="sxs-lookup"><span data-stu-id="f7feb-271">**The CAP Theorem** </span></span>\
    <https://en.wikipedia.org/wiki/CAP_theorem>

- <span data-ttu-id="f7feb-272">**CAP Teoremi Nedir?**</span><span class="sxs-lookup"><span data-stu-id="f7feb-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="f7feb-273">**Veri Tutarlılığı Astarı** </span><span class="sxs-lookup"><span data-stu-id="f7feb-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="f7feb-274">**Rick Saling. CAP Teoremi: Neden "Her Şey Farklı" Bulut ve İnternet ile** </span><span class="sxs-lookup"><span data-stu-id="f7feb-274">**Rick Saling. The CAP Theorem: Why "Everything is Different" with the Cloud and Internet** </span></span>\
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="f7feb-275">**Eric Brewer' ı. CAP On iki Yıl Sonra: Nasıl "Kurallar" Değişti** </span><span class="sxs-lookup"><span data-stu-id="f7feb-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="f7feb-276">**Azure Servis Veri Servisi. Aracılı Mesajlaşma: Yinelenen Algılama**  </span><span class="sxs-lookup"><span data-stu-id="f7feb-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="f7feb-277">**Güvenilirlik Kılavuzu** (RabbitMQ belgeleri) </span><span class="sxs-lookup"><span data-stu-id="f7feb-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> <span data-ttu-id="f7feb-278">[Önceki](rabbitmq-event-bus-development-test-environment.md)
> [Sonraki](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="f7feb-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
