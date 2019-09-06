---
title: Olaylara abone olma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Tümleştirme olaylarına yayımlama ve aboneliğin ayrıntılarını anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: c0eaacce51b186191431bf827bb84d3a2d2b7b1f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296558"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="4fa5b-103">Olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="4fa5b-103">Subscribing to events</span></span>

<span data-ttu-id="4fa5b-104">Olay veri yolunu kullanmanın ilk adımı, mikro hizmetlerin almak istedikleri olaylara abone olmadır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="4fa5b-105">Bu, alıcının mikro hizmetlerinde yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="4fa5b-106">Aşağıdaki basit kod, hizmet başlatıldığında (yani, `Startup` sınıfında), ihtiyaç duyacağı olaylara abone olmak için her bir alıcı mikro hizmetinin ne yapması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="4fa5b-107">Bu durumda, `basket.api` mikro hizmet 'e `ProductPriceChangedIntegrationEvent` abone olmalıdır ve `OrderStartedIntegrationEvent` iletileri.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="4fa5b-108">Örneğin, `ProductPriceChangedIntegrationEvent` olaya abone olurken, sepet mikro hizmetini ürün fiyatındaki herhangi bir değişikliği fark ettiğini ve bu ürün kullanıcının sepetinde olduğunda değişikliği hakkında kullanıcıyı uyarmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="4fa5b-109">Bu kod çalıştıktan sonra, abone mikro hizmeti, Kbbitmq kanalları aracılığıyla dinleme yapar.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="4fa5b-110">Productpricechangedıntemetionevent türünde herhangi bir ileti ulaştığında, kod kendisine geçirilen olay işleyicisini çağırır ve olayı işler.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="4fa5b-111">Olay veri yolu aracılığıyla olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="4fa5b-111">Publishing events through the event bus</span></span>

<span data-ttu-id="4fa5b-112">Son olarak, ileti gönderici (Origin mikro hizmeti), tümleştirme olaylarını aşağıdaki örneğe benzer kodla yayımlar.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="4fa5b-113">(Bu, hesapta kararlılık olmayan basitleştirilmiş bir örnektir.) Her bir olayın birden fazla mikro hizmette yayılması gerektiğinde, genellikle kaynak mikro hizmetinden veri veya işlem gerçekleştirildikten sonra, benzer bir kod uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="4fa5b-114">İlk olarak, aşağıdaki kodda olduğu gibi, olay veri yolu uygulama nesnesi (Kbbitmq veya bir Service Bus tabanlı olarak) denetleyici oluşturucusuna eklenir:</span><span class="sxs-lookup"><span data-stu-id="4fa5b-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="4fa5b-115">Bu durumda, UpdateProduct yönteminde olduğu gibi denetleyicinin yöntemlerinden yararlanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4fa5b-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="4fa5b-116">Bu durumda, kaynak mikro hizmet basit bir CRUD mikro hizmet olduğundan, bu kod bir Web API denetleyicisine doğrudan yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="4fa5b-117">Daha gelişmiş mikro hizmetlerde, CQRS yaklaşımları kullanırken olduğu gibi, `CommandHandler` `Handle()` yöntemi içinde sınıfında uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="4fa5b-118">Olay veri yoluna yayımlarken kararlılık ve dayanıklılık tasarlama</span><span class="sxs-lookup"><span data-stu-id="4fa5b-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="4fa5b-119">Olay veri yolu gibi dağıtılmış bir mesajlaşma sistemi aracılığıyla tümleştirme olaylarını yayımladığınızda, özgün veritabanını otomatik olarak güncelleştirme ve bir olay yayımlama (yani, her iki işlem de tamamlanmamış ya da hiçbiri) ile ilgili sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="4fa5b-120">Örneğin, daha önce gösterilen Basitleştirilmiş örnekte kod, ürün fiyatı değiştirildiğinde verileri veritabanına kaydeder ve sonra bir Productpricechangedıntegrationevent iletisi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="4fa5b-121">Başlangıçta, bu iki işlemin otomatik olarak gerçekleştirilmesi için önemli görünebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="4fa5b-122">Bununla birlikte, [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)gibi eski sistemlerde yaptığınız gibi, veritabanı ve ileti Aracısı ile ilgili dağıtılmış bir işlem kullanıyorsanız, bu, bu [sınır](https://www.quora.com/What-Is-CAP-Theorem-1)sonunda açıklanan nedenlerden dolayı önerilmez.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="4fa5b-123">Temel olarak, mikro hizmetleri, ölçeklenebilir ve yüksek oranda kullanılabilir sistemler oluşturmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="4fa5b-124">Biraz basitleşerek, CAP 'ler sürekli olarak kullanılabilir, güçlü tutarlı *ve* herhangi bir bölüme dayanıklı bir (dağıtılmış) veritabanı (veya modeline sahip bir mikro hizmet) oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="4fa5b-125">Bu üç özelliklerden ikisini de seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="4fa5b-126">Mikro hizmet tabanlı mimarilerde kullanılabilirlik ve tolerans ' i seçmeniz gerekir ve güçlü tutarlılığı vurgulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="4fa5b-127">Bu nedenle, çoğu modern mikro hizmet tabanlı uygulamalarda, Windows Dağıtılmış İşlem Düzenleyicisi (DTC) tabanlı [Dağıtılmış işlemler](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) uyguladığınızda yaptığınız gibi genellikle mesajlaşma 'da dağıtılmış işlemleri kullanmak istemezsiniz. [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)ile.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="4fa5b-128">İlk soruna ve bu örneğe geri dönelim.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="4fa5b-129">Veritabanı güncelleştirildikten sonra hizmet çöktüğünde (Bu durumda, \_bağlamdaki kod satırından hemen sonra). SaveChangesAsync ()), ancak tümleştirme olayı yayımlanmadan önce genel sistem tutarsız hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="4fa5b-130">Bu, ilgilendiğiniz belirli iş işlemine bağlı olarak iş açısından kritik olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="4fa5b-131">Mimari bölümünde daha önce bahsedildiği gibi, bu sorunla ilgilenirken çeşitli yaklaşımlara sahip olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4fa5b-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="4fa5b-132">Tam olay kaynağını belirleme [düzenini](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)kullanma.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="4fa5b-133">[İşlem günlüğü madenciliği](https://www.scoop.it/t/sql-server-transaction-log-mining)kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="4fa5b-134">[Giden kutusu deseninin](http://gistlabs.com/2014/05/the-outbox/)kullanımı.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="4fa5b-135">Bu, tümleştirme olaylarını depolamak için (yerel işlemi genişletme) bir işlem tablosudur.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="4fa5b-136">Bu senaryo için tam olay kaynağını belirleme (ES) deseni en iyi yaklaşımlardan biri değilse kullanmaktır *en* iyi.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="4fa5b-137">Bununla birlikte, birçok uygulama senaryosunda, bir tam ES sistemi uygulamaımayabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="4fa5b-138">ES, geçerli durum verilerini depolamak yerine yalnızca işlem veritabanınızda bulunan etki alanı olaylarını depolayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="4fa5b-139">Yalnızca etki alanı olaylarının depolanması, sisteminizin geçmişini ve geçmişteki bir zamanda sisteminizin durumunu tespit etmek gibi harika avantajlar elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="4fa5b-140">Ancak, bir tam ES sisteminin uygulanması sisteminizin çoğunu yeniden mimararak birçok karmaşıklığın ve gereksinimin tanıtılmasının yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="4fa5b-141">Örneğin, Event [Store](https://eventstore.org/)veya Azure Cosmos DB, MongoDB, Cassandra, couşdb veya ırvendb gibi belge yönelimli bir veritabanı için özel olarak oluşturulan bir veritabanını kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="4fa5b-142">Daha önce olay kaynağını öğrenmediğiniz müddetçe, bu soruna yönelik harika bir yaklaşım, ancak en kolay çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="4fa5b-143">İşlem günlüğü madenciliği ilk başta kullanma seçeneği çok saydam görünüyor.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="4fa5b-144">Ancak, bu yaklaşımı kullanmak için mikro hizmetin SQL Server işlem günlüğü gibi RDBMS işlem günlüğü ile bağlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="4fa5b-145">Bu muhtemelen istenmez.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-145">This is probably not desirable.</span></span> <span data-ttu-id="4fa5b-146">Diğer bir sakıncası, işlem günlüğünde kayıtlı olan alt düzey güncelleştirmelerin, üst düzey tümleştirme olaylarınız ile aynı düzeyde olmaması olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="4fa5b-147">Bu durumda, bu işlem günlüğü işlemlerinin tersine mühendislik işlemi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="4fa5b-148">Dengeli yaklaşım, bir işlem veritabanı tablosu ve Basitleştirilmiş ES deseninin bir karışımıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="4fa5b-149">Tümleştirme olayları tablosuna kaydettiğinizde, özgün olayında ayarladığınız "olayı yayımlamaya hazırlanma" gibi bir durum kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="4fa5b-150">Daha sonra olayı olay veri yoluna yayımlamayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="4fa5b-151">Yayımla-olay eylemi başarılı olursa, kaynak hizmetinde başka bir işlem başlatır ve durumu "olayı yayımlanmaya hazırlanıyor" olarak "olay zaten yayımlandı" olarak taşırsınız.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="4fa5b-152">Olay veri yolundaki Yayımla-olay eylemi başarısız olursa, veriler yine de kaynak mikro hizmeti içinde tutarsız olmaz — yine de "olay yayımlanmaya hazırlanıyor" olarak işaretlenir ve hizmetin geri kalanına göre, sonuçta tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="4fa5b-153">Her zaman arka plan işlerinin işlem durumunu veya tümleştirme olaylarını denetlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="4fa5b-154">İş "olay yayımlamaya hazırlanıyor" durumunda bir olay bulursa, bu olayı olay veri yoluna yeniden yayımlamayı deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="4fa5b-155">Bu yaklaşımda, yalnızca her bir kaynak mikro hizmeti için tümleştirme olaylarını ve yalnızca diğer mikro hizmetlerle veya dış sistemlerle iletişim kurmak istediğiniz olayları kalıcı hale getirmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="4fa5b-156">Buna karşılık, bir tam ES sisteminde, tüm etki alanı olaylarını da depoladığınızda.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="4fa5b-157">Bu nedenle, bu dengeli yaklaşım basitleştirilmiş bir sistemdir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="4fa5b-158">Tümleştirme olaylarının bir listesine ("yayımlamaya hazırlanın" ve "yayımlanmış") sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="4fa5b-159">Ancak yalnızca tümleştirme olayları için bu durumları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="4fa5b-160">Bu yaklaşımda, tüm etki alanı verilerinizi, tam ES sisteminde yaptığınız gibi işlem veritabanına olay olarak depolamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="4fa5b-161">Zaten ilişkisel bir veritabanı kullanıyorsanız, tümleştirme olaylarını depolamak için bir işlemsel tablo kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="4fa5b-162">Uygulamanızda kararlılık elde etmek için, yerel işlemlere göre iki adımlı bir işlem kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="4fa5b-163">Temel olarak, etki alanı varlıklarınızın bulunduğu veritabanında bir ıntegrationevent tablonuz vardır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="4fa5b-164">Bu tablo, etki alanı verilerinizi yürüten işlemlere kalıcı tümleştirme olayları dahil etmeniz için, kararlılık elde etmek üzere bir sigorta olarak çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="4fa5b-165">Adım adım, işlem şöyle gider:</span><span class="sxs-lookup"><span data-stu-id="4fa5b-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="4fa5b-166">Uygulama, yerel bir veritabanı işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="4fa5b-167">Ardından, etki alanı varlıklarınızın durumunu güncelleştirir ve tümleştirme olay tablosuna bir olay ekler.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="4fa5b-168">Son olarak, işlem, istenen kararlılık 'i ve ardından</span><span class="sxs-lookup"><span data-stu-id="4fa5b-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="4fa5b-169">Olayı bir şekilde yayımlarsınız (ileri).</span><span class="sxs-lookup"><span data-stu-id="4fa5b-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="4fa5b-170">Olayları yayımlama adımlarını uygularken şu seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="4fa5b-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="4fa5b-171">İşlem tamamlandıktan sonra tümleştirme olayını yayımlayın ve tablodaki olayları yayımlanmakta olarak işaretlemek için başka bir yerel işlem kullanın.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="4fa5b-172">Daha sonra, uzak mikro hizmetlerde sorun olması durumunda tümleştirme olaylarını izlemek ve depolanan tümleştirme olaylarına göre telafi işlemleri gerçekleştirmek için, tabloyu yapıt olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="4fa5b-173">Tabloyu kuyruk türü olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="4fa5b-174">Ayrı bir uygulama iş parçacığı veya işlemi, tümleştirme olay tablosunu sorgular, olayları olay veri yoluna yayımlar ve sonra olayları yayımlandı olarak işaretlemek için yerel bir işlem kullanır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="4fa5b-175">Şekil 6-22, bu yaklaşımların ilki için mimari gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Olayları yayımlarken kararlılık 'i işlemeye yönelik bir yaklaşım: bir olay günlüğü tablosuna olay yürütmek için bir işlem kullanın ve ardından yayımlanacak başka bir işlem (eshoponcontainers 'da kullanılır)](./media/image23.png)

<span data-ttu-id="4fa5b-177">**Şekil 6-22**.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-177">**Figure 6-22**.</span></span> <span data-ttu-id="4fa5b-178">Olay veri yoluna olay yayımlarken Atomicity</span><span class="sxs-lookup"><span data-stu-id="4fa5b-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="4fa5b-179">Şekil 6-22 ' de gösterilen yaklaşımda, yayımlanan tümleştirme olaylarının başarısını denetleme ve onaylama aşamasında olan ek bir çalışan mikro hizmeti eksik.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="4fa5b-180">Hata durumunda ek denetleyici Worker mikro hizmeti, tablodaki olayları okuyabilir ve yeniden yayımlayabilir, diğer bir deyişle adım 2 ' yi tekrarlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="4fa5b-181">İkinci yaklaşım hakkında: olay günlüğü tablosunu kuyruk olarak kullanın ve iletileri yayımlamak için her zaman bir çalışan mikro hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="4fa5b-182">Bu durumda, işlem Şekil 6-23 ' de gösterilenle benzer.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="4fa5b-183">Bu, ek bir mikro hizmet gösterir ve olaylar yayımlandığında tablo tek kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Atomicity 'i işlemeye yönelik başka bir yaklaşım: Olay günlüğü tablosuna yayımlayın ve sonra başka bir mikro hizmet (arka plan çalışanı) olayını yayımlayın.](./media/image24.png)

<span data-ttu-id="4fa5b-185">**Şekil 6-23**.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-185">**Figure 6-23**.</span></span> <span data-ttu-id="4fa5b-186">Bir çalışan mikro hizmeti ile olay veri yoluna olay yayımlarken Atomicity</span><span class="sxs-lookup"><span data-stu-id="4fa5b-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="4fa5b-187">Basitlik için eShopOnContainers örneği, ilk yaklaşımı (ek işlem veya denetleyici mikro hizmetleri olmadan) ve olay veri yolunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="4fa5b-188">Ancak eShopOnContainers, olası tüm hata durumlarını işlemez.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="4fa5b-189">Buluta dağıtılan gerçek bir uygulamada, sorunların sonunda ortaya çıkması ve bu denetimi ve yeniden gönder mantığını uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="4fa5b-190">Tabloyu bir sıra olarak kullanmak, bu tabloyu olay veri yolundan yayımlalarken (çalışan ile) tek bir olay kaynağı olarak kullandığınızda ilk yaklaşımdan daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="4fa5b-191">Olay veri yolu aracılığıyla tümleştirme olaylarını yayımlarken kararlılık uygulama</span><span class="sxs-lookup"><span data-stu-id="4fa5b-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="4fa5b-192">Aşağıdaki kod, birden çok DbContext nesnesi içeren tek bir işlem oluşturabileceğiniz gibi, güncelleştirilmekte olan özgün verilerle ilgili bir bağlam ve ıntegrationeventlog tablosu ile ilgili ikinci bağlam.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="4fa5b-193">Aşağıdaki örnek kodundaki işlemin, veritabanı bağlantıları, kodun çalıştığı sırada herhangi bir sorun varsa, bu işlem için dayanıklı olmaz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="4fa5b-194">Bu durum, veritabanlarını sunucular arasında taşıyabilecek Azure SQL VERITABANı gibi bulut tabanlı sistemlerde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="4fa5b-195">Birden çok bağlamdaki esnek işlemleri uygulamak için, bu kılavuzun ilerleyen kısımlarında dayanıklı [ENTITY Framework Core SQL bağlantıları uygulama](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="4fa5b-196">Açıklık açısından aşağıdaki örnek tek bir kod parçası olarak tüm işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="4fa5b-197">Ancak eShopOnContainers uygulamasının gerçekten yeniden düzenlenmiş ve bu mantığı birden çok sınıfa bölerek daha kolay korunması kolaylaşır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="4fa5b-198">Productpricechangedıntegrationevent Integration olayı oluşturulduktan sonra, özgün etki alanı işlemini depolayan işlem (Katalog öğesini Güncelleştir) Ayrıca olay günlüğü tablosunda olayın kalıcılığını da içerir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="4fa5b-199">Bu, tek bir işlem yapar ve olay iletilerinin gönderilip gönderilmeyeceğini her zaman kontrol edebileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="4fa5b-200">Aynı veritabanına karşı yerel bir işlem kullanılarak olay günlüğü tablosu, özgün veritabanı işlemiyle otomatik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="4fa5b-201">İşlemlerden herhangi biri başarısız olursa, bir özel durum oluşturulur ve işlem tüm tamamlanmış işlemleri geri alır, böylece etki alanı işlemleri ile tabloya kaydedilen olay iletileri arasındaki tutarlılığı koruyun.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="4fa5b-202">Aboneliklerden ileti alma: alıcı mikro hizmetlerindeki olay işleyicileri</span><span class="sxs-lookup"><span data-stu-id="4fa5b-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="4fa5b-203">Olay aboneliği mantığına ek olarak, tümleştirme olay işleyicileri için iç kodu uygulamanız gerekir (geri çağırma yöntemi gibi).</span><span class="sxs-lookup"><span data-stu-id="4fa5b-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="4fa5b-204">Olay işleyicisi, belirli bir türdeki olay iletilerinin nerede alındığını ve işleneceğini belirlediğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="4fa5b-205">Olay işleyicisi önce olay veri yolundan bir olay örneği alır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="4fa5b-206">Daha sonra bu tümleştirme olayı ile ilgili işlenecek bileşeni konumlandırır, alıcı mikro hizmetindeki durum değişikliği olarak olayı yayın ve kalıcı hale getirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="4fa5b-207">Örneğin, bir ProductPriceChanged olayının kataloğu mikro hizmetinde kaynağı varsa, bu, sepet mikro hizmetinde işlenir ve aşağıdaki kodda gösterildiği gibi bu alıcı Sepeti mikro hizmetindeki durumu da değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="4fa5b-208">Olay işleyicisinin, ürünün sepet örneklerinde mevcut olup olmadığını doğrulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="4fa5b-209">Ayrıca ilgili her sepet satırı öğesi için öğe fiyatını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="4fa5b-210">Son olarak, Şekil 6-24 ' de gösterildiği gibi, kullanıcıya fiyat değişikliği hakkında görüntülenmek üzere bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Kullanıcı sepetindeki işlem değişikliği bildiriminin tarayıcı görünümü.](./media/image25.png)

<span data-ttu-id="4fa5b-212">**Şekil 6-24**.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-212">**Figure 6-24**.</span></span> <span data-ttu-id="4fa5b-213">Bir sepetteki bir öğe fiyat değişikliğini tümleştirme olayları tarafından iletilen şekilde görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4fa5b-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="4fa5b-214">Güncelleştirme iletisi olaylarında ıdempot</span><span class="sxs-lookup"><span data-stu-id="4fa5b-214">Idempotency in update message events</span></span>

<span data-ttu-id="4fa5b-215">Güncelleştirme iletisi olaylarının önemli bir yönü, iletişimin herhangi bir noktasında başarısız olmasının iletinin yeniden denenmesine neden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="4fa5b-216">Aksi halde, bir arka plan görevi zaten yayımlanmış olan bir olayı yayımlamayı deneyebilir, bir yarış durumu oluşturuyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="4fa5b-217">Güncelleştirmelerin ıdempotent olduğundan ya da bir yinelemeyi tespit edip yalnızca bir yanıt gönderdiğinizden emin olmak için yeterli bilgi sağladıklarından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="4fa5b-218">Daha önce belirtildiği gibi, ıdempot, bir işlemin sonucu değiştirmeksizin birden çok kez gerçekleştirilebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="4fa5b-219">Bir mesajlaşma ortamında, olayları kullanırken olduğu gibi, alıcı mikro hizmeti için sonucu değiştirmeden birden çok kez teslim edilebilir bir olay ıdempotent olur.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="4fa5b-220">Bu, olayın kendisinin doğası veya sistemin olayı işleme biçimi nedeniyle gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="4fa5b-221">İleti ıdempoti, yalnızca olay veri yolu modelini uygulayan uygulamalarda değil, mesajlaşma kullanan herhangi bir uygulamada önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="4fa5b-222">Bir ıdempotent işlemine örnek olarak, yalnızca bu veriler tabloda yoksa tabloya veri ekleyen bir SQL deyimidir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="4fa5b-223">Bu, SQL ifadesini eklemek için kaç kez çalıştırılcağınızı değil; Sonuç aynı olacaktır — tablo bu verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="4fa5b-224">Benzer şekilde, iletiler gönderilebileceği ve bu nedenle birden çok kez işlenen iletilerle ilgilenirken bu da gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="4fa5b-225">Örneğin, yeniden deneme mantığı bir göndericinin aynı iletiyi birden çok kez göndermesini sağlar, bunun ıdempotent olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="4fa5b-226">Idempotent iletilerini tasarlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="4fa5b-227">Örneğin, "ürün fiyatını $25 olarak ayarla" $5 yerine "ürün fiyatını" olarak belirten bir olay oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="4fa5b-228">İlk iletiyi herhangi bir sayıda kez güvenli bir şekilde işleyebilir ve sonuç aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="4fa5b-229">Bu, ikinci ileti için doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-229">That is not true for the second message.</span></span> <span data-ttu-id="4fa5b-230">Ancak ilk durumda da, sistem daha yeni bir fiyat değişikliği olayı göndermiş olabileceğinden ve yeni fiyatın üzerine yazılabileceğinden, ilk olayı işlemek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="4fa5b-231">Diğer bir örnek, birden çok aboneye yayılmakta olan sıralı tamamlanmış bir olay olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="4fa5b-232">Aynı sipariş tamamlandı olayı için yinelenen ileti olayları olsa bile, yalnızca bir kez diğer sistemlerdeki sipariş bilgilerinin güncelleştirilmesini önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="4fa5b-233">Her olayın her alıcı için yalnızca bir kez işlenmesini zorlayan mantık oluşturabilmeniz için olay başına bir tür kimliğe sahip olmak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="4fa5b-234">Bazı ileti işleme, kendiliğinden ıdempotent.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="4fa5b-235">Örneğin, bir sistem görüntü küçük resimleri oluşturursa, oluşturulan küçük resim ile ilgili iletinin kaç kez işlendiğine bakılmaksızın bu durum oluşabilir. Sonuç olarak, küçük resimlerin oluşturulması ve her seferinde aynı olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="4fa5b-236">Diğer taraftan, kredi kartı ücreti almak için ödeme ağ geçidini çağırma gibi işlemler ıdempotent olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="4fa5b-237">Bu durumlarda, bir iletiyi birden çok kez işlemenin bekleeceğiniz etkiye sahip olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4fa5b-238">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4fa5b-238">Additional resources</span></span>

- <span data-ttu-id="4fa5b-239">**İleti tekisliliği**</span><span class="sxs-lookup"><span data-stu-id="4fa5b-239">**Honoring message idempotency**</span></span> <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="4fa5b-240">Tümleştirme olayı iletilerini Çoğaltma kaldırma</span><span class="sxs-lookup"><span data-stu-id="4fa5b-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="4fa5b-241">İleti olaylarının her abone için farklı düzeylerde yalnızca bir kez gönderilmesini ve işlenmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="4fa5b-242">Tek yönlü, kullanmakta olduğunuz mesajlaşma altyapısı tarafından sunulan yinelenenleri kaldırma özelliğini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="4fa5b-243">Diğer bir deyişle, hedef mikro hizmetinize özel mantık uyguğıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="4fa5b-244">Hem Aktarım düzeyinde hem de uygulama düzeyinde doğrulamaları olan en iyi sonuç.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="4fa5b-245">EventHandler düzeyinde ileti olaylarını kaldırma</span><span class="sxs-lookup"><span data-stu-id="4fa5b-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="4fa5b-246">Bir olayın her alıcı tarafından yalnızca bir kez işlendiğinden emin olmanın bir yolu, olay işleyicilerindeki ileti olaylarını işlerken belirli bir mantığı uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="4fa5b-247">Örneğin, eShopOnContainers uygulamasında kullanılan yaklaşım, bir Usercheckoutacceptedinteıntionevent tümleştirme olayı aldığında [Usercheckoutacceptedınteuttioneventhandler sınıfının kaynak kodunda](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) görebileceğiniz gibi.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="4fa5b-248">(Bu durumda, komut işleyicisine göndermeden önce eventMsg. RequestId öğesini tanımlayıcı olarak kullanarak CreateOrderCommand öğesini bir IdentifiedCommand sardık.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="4fa5b-249">Kbbitmq kullanırken iletilerin Çoğaltma kaldırma</span><span class="sxs-lookup"><span data-stu-id="4fa5b-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="4fa5b-250">Aralıklı ağ arızalarının meydana gelmesi durumunda iletiler yinelenebilir ve ileti alıcısı bu yinelenen iletileri işlemeye hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="4fa5b-251">Mümkünse, alıcıların iletileri ıdempotent bir şekilde işlemesi gerekir ve bu, onları yinelenenleri kaldırma ile açıkça işlemenin daha iyi bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="4fa5b-252">[Kbbitmq belgelerine](https://www.rabbitmq.com/reliability.html#consumer)göre, "bir ileti tüketiciye teslim edildiğinde ve sonra yeniden kuyruğa (tüketici bağlantısı bırakılmadan önce onaylanmadığı için), Kbbitmq, teslim edildiğinde yeniden teslim edilen bayrağını ayarlar yeniden (aynı tüketici mi yoksa farklı bir tane mi olduğunu).</span><span class="sxs-lookup"><span data-stu-id="4fa5b-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="4fa5b-253">"Yeniden teslim edildi" bayrağı ayarlandıysa, ileti zaten işlenmiş olabileceğinden alıcı bu hesabı dikkate almalıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="4fa5b-254">Ancak bu garanti edilmez; ileti, ağ sorunları nedeniyle ileti aracısından ayrıldıktan sonra alıcıya hiçbir şekilde ulaşmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="4fa5b-255">Öte yandan, "yeniden teslim edildi" bayrağı ayarlanmamışsa, iletinin birden çok kez gönderilmediği garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="4fa5b-256">Bu nedenle, alıcının iletileri yinebir ıdempotent şekilde işlemesi veya ileti içinde "yeniden teslim edildi" bayrağı ayarlandıysa iletileri işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4fa5b-257">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4fa5b-257">Additional resources</span></span>

- <span data-ttu-id="4fa5b-258">**NServiceBus (belirli yazılımlar) kullanılarak forlenmiş eShopOnContainers** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="4fa5b-259">**Olay odaklı mesajlaşma** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-259">**Event Driven Messaging** </span></span>\
    [http://soapatterns.org/design\_patterns/event\_driven\_messaging](http://soapatterns.org/design_patterns/event_driven_messaging)

- <span data-ttu-id="4fa5b-260">**Jimmy Bogard. Esnekliği doğru yeniden düzenleme: Kupın değerlendirmesi** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="4fa5b-261">**Yayımla-abone ol kanalı** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="4fa5b-262">**Sınırlanmış bağlamlar arasında iletişim kurma** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="4fa5b-263">**Nihai tutarlılık** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-263">**Eventual Consistency** </span></span>\
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- <span data-ttu-id="4fa5b-264">**Philip kahverengi. Sınırlı bağlamlara tümleştirme stratejileri** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="4fa5b-265">**Chris Richardson. Toplamaları kullanarak Işlem mikro hizmetleri geliştirme, olay kaynağını belirleme ve CQRS-2. Bölüm** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="4fa5b-266">**Chris Richardson. Olay kaynağını belirleme kalıbı** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="4fa5b-267">**Olay kaynağını belirleme** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="4fa5b-268">**Olay deposu veritabanı**.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-268">**Event Store database**.</span></span> <span data-ttu-id="4fa5b-269">Resmi site.</span><span class="sxs-lookup"><span data-stu-id="4fa5b-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="4fa5b-270">**Patrick Nmmensen. Mikro hizmetler için olay odaklı Veri Yönetimi** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="4fa5b-271">**Üst sınır** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-271">**The CAP Theorem** </span></span>\
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- <span data-ttu-id="4fa5b-272">**SıNıR nedir?**</span><span class="sxs-lookup"><span data-stu-id="4fa5b-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="4fa5b-273">**Veri tutarlılığı öncü** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="4fa5b-274">**Rick sallama. CAP 'ler: Bulut ve Internet ile neden "her şey farklıdır"**  </span><span class="sxs-lookup"><span data-stu-id="4fa5b-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span></span>\
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="4fa5b-275">**Eric Brewer. BÜYÜK on Iki yıl sonra: "Kurallar" nasıl değişmiştir** </span><span class="sxs-lookup"><span data-stu-id="4fa5b-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="4fa5b-276">**Azure Service Bus. Aracılı mesajlaşma: Yinelenen algılama**  </span><span class="sxs-lookup"><span data-stu-id="4fa5b-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="4fa5b-277">**Güvenilirlik Kılavuzu** (Oybbitmq belgeleri) </span><span class="sxs-lookup"><span data-stu-id="4fa5b-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

> [!div class="step-by-step"]
> <span data-ttu-id="4fa5b-278">[Önceki](rabbitmq-event-bus-development-test-environment.md)İleri
> [](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="4fa5b-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
