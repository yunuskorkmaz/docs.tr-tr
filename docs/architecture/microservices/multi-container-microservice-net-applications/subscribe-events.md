---
title: Olaylara abone olma
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Tümleştirme etkinliklerini yayımlama ve abone etme ayrıntılarını anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: 544af8035ed23dd6507dfed4944b0c327c81d943
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501804"
---
# <a name="subscribing-to-events"></a>Olaylara abone olma

Etkinlik veri toplarını kullanmanın ilk adımı, mikro hizmetlere almak istedikleri etkinliklere abone olmaktır. Bu alıcı mikro hizmetler yapılmalıdır.

Aşağıdaki basit kod, hizmeti başlatırken her alıcı mikro hizmetinin ne `Startup` leri uygulaması gerektiğini (yani sınıfta) gösterir, böylece ihtiyaç duyduğu olaylara abone olur. Bu durumda, `basket-api` mikro hizmet `ProductPriceChangedIntegrationEvent` ve `OrderStartedIntegrationEvent` mesajları abone olması gerekir.

Örneğin, `ProductPriceChangedIntegrationEvent` etkinliğe abone olurken, sepet mikro hizmetini ürün fiyatındaki herhangi bir değişiklikten haberdar eder ve bu ürün kullanıcının sepetindeyse kullanıcıyı değişiklik konusunda uyarmasını sağlar.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Bu kod çalıştırdıktan sonra, abone microservice RabbitMQ kanalları üzerinden dinliyor olacak. ProductPriceChangedIntegrationEvent türünden herhangi bir ileti geldiğinde, kod kendisine geçirilen olay işleyicisini çağırır ve olayı işler.

## <a name="publishing-events-through-the-event-bus"></a>Etkinlik otobüslerinden etkinlikleri yayımlama

Son olarak, ileti gönderen (başlangıç mikrohizmeti) aşağıdaki örneğe benzer kodile tümleştirme olaylarını yayımlar. (Bu, atomikliği hesaba katmayan basitleştirilmiş bir örnektir.) Bir olay, genellikle kaynak mikrohizmetten veri veya işlem işledikten hemen sonra, birden çok mikro hizmet arasında yayılması gerektiğinde benzer bir kod uygularsınız.

İlk olarak, olay veri merkezi uygulama nesnesi (RabbitMQ'ye veya servis veri yolundan dayalı olarak) aşağıdaki kodda olduğu gibi denetleyici oluşturucuya enjekte edilir:

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

Daha sonra, UpdateProduct yönteminde olduğu gibi, denetleyicinizin yöntemlerinden kullanırsınız:

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

Bu durumda, başlangıç microservice basit bir CRUD microservice olduğundan, bu kod bir Web API denetleyicisi içine doğru yerleştirilir.

CQRS yaklaşımları kullanırken olduğu gibi daha gelişmiş mikrohizmetlerde, `CommandHandler` `Handle()` yöntem içinde sınıfta uygulanabilir.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Etkinlik otobüsüne yayın yaparken atomiklik ve esneklik tasarlama

Tümleştirme olaylarını olay veri tobununuz gibi dağıtılmış bir ileti sistemi üzerinden yayımladığınızda, özgün veritabanını atomik olarak güncelleştirme ve bir olayı yayımlama sorunu yla karşı lanırsınız (diğer bir şekilde, her iki işlem de tamamlanır veya hiçbiri). Örneğin, daha önce gösterilen basitleştirilmiş örnekte, ürün fiyatı değiştirildiğinde kod veritabanına veri adatır ve ardından bir ProductPriceChangedIntegrationEvent iletisi yayımlar. Başlangıçta, bu iki operasyonun atomik olarak yapılması gerekli görünebilir. Ancak, [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)gibi eski sistemlerde yaptığınız gibi veritabanı ve ileti aracısını içeren dağıtılmış bir işlem kullanıyorsanız, [bu, CAP teoremi](https://www.quora.com/What-Is-CAP-Theorem-1)tarafından açıklanan nedenlerle önerilmez.

Temel olarak, ölçeklenebilir ve yüksek kullanılabilir sistemler oluşturmak için mikro hizmetleri kullanın. Biraz basitleştiren CAP teoremi, sürekli olarak kullanılabilir, güçlü tutarlı *ve* herhangi bir bölüme toleranslı bir (dağıtılmış) veritabanı (veya kendi modeline sahip bir microservice) oluşturamayacağınızı söyler. Bu üç özelliklerden ikisini seçmeniz gerekir.

Mikro hizmetler tabanlı mimarilerde kullanılabilirlik ve toleransı seçmeli ve güçlü tutarlılığı vurgulamanız gerekir. Bu nedenle, çoğu modern mikrohizmet tabanlı uygulamalarda, [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)ile Windows Dağıtılmış İşlem Koordinatörü'ne (DTC) dayalı dağıtılmış hareketleri uyguladığınızda yaptığınız gibi, genellikle iletide [dağıtılmış hareketleri](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) kullanmak istemezsinüz.

İlk sayıya ve onun örneğine geri dönelim. Hizmet veritabanı güncelleştirildikten sonra çatlarsa (bu durumda, bağlamlı \_kod satırından hemen sonra. SaveChangesAsync()), ancak tümleştirme olayı yayımlanmadan önce, genel sistem tutarsız olabilir. Bu, uğraştığınız belirli iş işlemine bağlı olarak iş açısından kritik olabilir.

Mimari bölümünde daha önce de belirtildiği gibi, bu sorunla başa çıkmak için çeşitli yaklaşımlar olabilir:

- Tam [Olay Kaynak desen](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)kullanarak .

- [İşlem günlüğü madenciliği kullanma.](https://www.scoop.it/t/sql-server-transaction-log-mining)

- Giden [Kutusu deseni](https://www.kamilgrzybek.com/design/the-outbox-pattern/)kullanma. Bu, tümleştirme olaylarını depolamak (yerel hareketi genişletmek) için bir işlem tablosudur.

Bu senaryo için, tam Olay Kaynak (ES) desen kullanarak en iyi yaklaşımlardan biridir, değilse *en* iyi. Ancak, birçok uygulama senaryosunda, tam bir ES sistemi uygulayamayabilirsiniz. ES, geçerli durum verilerini depolamak yerine yalnızca etki alanı olaylarını işlem veritabanınızda depolamak anlamına gelir. Yalnızca etki alanı olaylarını depolamanın, sisteminizin geçmişine sahip olması ve geçmişte herhangi bir anda sisteminizin durumunu belirleyebilmesi gibi büyük avantajları olabilir. Ancak, tam bir ES sistemi uygulamak, sisteminizin çoğunu yeniden yeniden mimarlandırmanızı gerektirir ve diğer birçok karmaşıklığı ve gereksinimi sunar. Örneğin, [Olay Mağazası](https://eventstore.org/)gibi olay kaynağı için özel olarak yapılmış bir veritabanı veya Azure Cosmos DB, MongoDB, Cassandra, CouchDB veya RavenDB gibi belge yönelimli bir veritabanı kullanmak isteyebilirsiniz. ES bu sorun için harika bir yaklaşımdır, ancak olay kaynak konusunda zaten aşina değilseniz en kolay çözüm değildir.

Hareket günlüğü madenciliği kullanma seçeneği başlangıçta çok saydam görünüyor. Ancak, bu yaklaşımı kullanmak için, mikro hizmetIN SQL Server işlem günlüğü gibi RDBMS işlem günlüğünüze birleştirilmesi gerekir. Bu muhtemelen arzu edilmez. Başka bir dezavantajı, işlem günlüğüne kaydedilen alt düzey güncelleştirmelerin üst düzey tümleştirme olaylarınızla aynı düzeyde olmamasıdır. Bu nedenle, bu işlem günlüğü işlemleri ters mühendislik işlemi zor olabilir.

Dengeli bir yaklaşım, işlem veritabanı tablosu nun ve basitleştirilmiş ES deseninin bir karışımıdır. Tümleştirme olayları tablosuna işledirirken özgün olayda ayarlayacağınız "olayı yayımlamaya hazır" gibi bir durum kullanabilirsiniz. Daha sonra etkinliği etkinlik otobüsüne yayımlamaya çalışırsınız. Yayımlama olayı eylemi başarılı olursa, kaynak hizmetinde başka bir işlem başlatın ve durumu "etkinliği yayımlamaya hazır"dan "zaten yayımlanmış olay"a taşırsınız.

Veri veri sayında yayımlama olayı eylemi başarısız olursa, veriler yine de başlangıç mikrohizmeti nde tutarsız olmayacaktır-yine de "etkinliği yayımlamaya hazır" olarak işaretlenir ve hizmetlerin geri kalanıyla ilgili olarak, sonunda tutarlı olacaktır. Her zaman geçmiş işleri işlemlerin veya tümleştirme olaylarıdurumunu denetleme olabilir. İş "olayı yayımlamaya hazır" durumunda bir olay bulursa, bu olayı olay veri netosu yla yeniden yayımlamayı deneyebilir.

Bu yaklaşımla, yalnızca her başlangıç mikro hizmeti için tümleştirme olaylarını ve yalnızca diğer mikro hizmetlere veya harici sistemlere iletmek istediğiniz olayları devam ettirebildiğinize dikkat edin. Buna karşılık, tam bir ES sisteminde, tüm etki alanı olaylarını da saklarsınız.

Bu nedenle, bu dengeli yaklaşım basitleştirilmiş bir ES sistemidir. Geçerli durumları yla tümleştirme olaylarının bir listesine ihtiyacınız vardır ("yayımlamaya hazır" ile "yayımlanmış"). Ancak, tümleştirme olayları için bu durumları uygulamanız gerekir. Ve bu yaklaşımda, tüm etki alanı verilerinizi tam bir ES sisteminde olduğu gibi işlem veritabanında olay olarak depolamanız gerekmez.

İlişkisel bir veritabanı zaten kullanıyorsanız, tümleştirme olaylarını depolamak için bir işlem tablosu kullanabilirsiniz. Uygulamanızda atomikliği sağlamak için yerel işlemlere dayalı iki aşamalı bir işlem kullanırsınız. Temel olarak, etki alanı varlıklarınızın bulunduğu aynı veritabanında bir IntegrationEvent tablonuz vardır. Bu tablo, kalıcı tümleştirme olaylarını etki alanı verilerinizi işleyen aynı işlemlere dahil etmek için atomikliğe ulaşmak için bir sigorta olarak çalışır.

Adım adım, süreç şöyle devam eder:

1. Uygulama yerel bir veritabanı hareketi başlar.

2. Daha sonra etki alanı varlıklarınızın durumunu güncelleştirir ve tümleştirme olayı tablosuna bir olay ekler.

3. Son olarak, bu işlem yapar, böylece istenilen atomiklik olsun ve sonra

4. Olayı bir şekilde (sonraki) yayımlarsınız.

Olayları yayımlama adımlarını uygularken şu seçeneklere sahipsiniz:

- İşlemi işledikten hemen sonra tümleştirme olayını yayımlayın ve tablodaki olayları yayımlanmış gibi işaretlemek için başka bir yerel işlem kullanın. Ardından, uzak mikro hizmetlerdeki sorunlar durumunda tümleştirme olaylarını izlemek ve depolanan tümleştirme olaylarını temel alan telafi edici eylemler gerçekleştirmek için tabloyu yalnızca bir yapı olarak kullanın.

- Tabloyu sıra türü olarak kullanın. Ayrı bir uygulama iş parçacığı veya işlem tümleştirme olay tablosunu sorgular, olayları olay veri yoluna yayınlar ve sonra olayları yayımlanmış olarak işaretlemek için yerel bir işlem kullanır.

Şekil 6-22 bu yaklaşımların ilkinin mimarisini göstermektedir.

![Bir işçi microservice olmadan yayımlarken atomiklik diyagramı.](./media/subscribe-events/atomicity-publish-event-bus.png)

**Şekil 6-22**. Etkinlik otobüsüne etkinlik yayınlarken atomiklik

Şekil 6-22'de gösterilen yaklaşım, yayınlanan tümleştirme olaylarının başarısını kontrol etmek ve onaylamaktan sorumlu ek bir işçi microservice eksiktir. Hata durumunda, bu ek dama işçisi microservice tablodan olayları okuyabilir ve bunları yeniden yayımlayabilir, yani 2 numaralı adımı tekrarlayabilir.

İkinci yaklaşım hakkında: EventLog tablosunu sıra olarak kullanır ve iletileri yayımlamak için her zaman bir işçi mikro hizmeti kullanırsınız. Bu durumda, işlem Şekil 6-23'te gösterilen gibidir. Bu ek bir microservice gösterir ve tablo olayları yayımlarken tek kaynaktır.

![Bir işçi microservice ile yayımlarken atomiklik diyagramı.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

**Şekil 6-23**. Bir işçi microservice ile olay otobüsüne etkinlik yayınlarken atomiklik

Basitlik için, eShopOnContainers örnek ilk yaklaşım (hiçbir ek süreçler veya denetleyici microservices ile) artı olay veri meskenkullanır. Ancak, eShopOnContainers tüm olası arıza durumlarını ele değildir. Buluta dağıtılan gerçek bir uygulamada, sorunların eninde sonunda ortaya çıkacağı gerçeğini benimsemeli ve bu denetimi ve yeniden gönderme mantığını uygulamanız gerekir. Tabloyu sıra olarak kullanmak, bu tabloyu olay veri tobus aracılığıyla (işçiyle) yayımlarken tek bir olay kaynağı olarak kullanıyorsanız, ilk yaklaşımdan daha etkili olabilir.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Tümleştirme olaylarını etkinlik verine aracılığıyla yayınlarken atomikliğin uygulanması

Aşağıdaki kod, birden çok DbContext nesnesini içeren tek bir işlemi (bir bağlam orijinal verilerle ilgili bir bağlam ve IntegrationEventLog tablosuyla ilgili ikinci bağlam) nasıl oluşturabileceğinizi gösterir.

Aşağıdaki örnek koddaki işlemin, kod çalışırken veritabanına bağlantılarda herhangi bir sorun varsa esnek olmayacağını unutmayın. Bu, veritabanlarını sunucular arasında taşıyabilecek Azure SQL DB gibi bulut tabanlı sistemlerde gerçekleşebilir. Birden çok bağlam boyunca esnek hareketler uygulamak için, daha sonra bu kılavuzda [esnek Entity Framework SQL bağlantıları uygulama](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) bölümüne bakın.

Netlik için aşağıdaki örnek, tüm işlemi tek bir kod parçasında gösterir. Ancak, eShopOnContainers uygulaması aslında refactored ve korumak için daha kolay böylece birden fazla sınıfa bu mantığı bölmek.

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

ProductPriceChangedIntegrationEvent tümleştirme olayı oluşturulduktan sonra, özgün etki alanı işlemini depolayan işlem (katalog öğesini güncelleştirme) olayın EventLog tablosundaki kalıcılığını da içerir. Bu, tek bir işlem yapar ve olay iletilerinin gönderilip gönderilmediğini her zaman denetleyebilirsiniz.

Olay günlüğü tablosu, aynı veritabanına karşı yerel bir işlem kullanılarak özgün veritabanı işlemiyle atomik olarak güncelleştirilir. İşlemlerden herhangi biri başarısız olursa, bir özel durum atılır ve işlem tamamlanan herhangi bir işlemi geri alır, böylece etki alanı işlemleri ile tabloya kaydedilen olay iletileri arasında tutarlılık korunur.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Aboneliklerden ileti alma: alıcı mikro hizmetlerdeki olay işleyicileri

Olay abonelik mantığına ek olarak, tümleştirme olay işleyicileri (geri arama yöntemi gibi) için iç kodu uygulamanız gerekir. Olay işleyicisi, belirli bir türdeki olay iletilerinin alınıp işlenmeyi nerede belirttiğiniz yerdir.

Olay işleyicisi önce olay veri tonundan bir olay örneği alır. Daha sonra, alıcı mikrohizmetinde durum değişikliği olarak olayı yaymak ve sürdürmek, bu tümleştirme olayıyla ilgili olarak işlenecek bileşeni bulur. Örneğin, Bir ProductPriceChanged olayı katalog microservice kaynaklanıyorsa, sepet microservice ele alınır ve aşağıdaki kodda gösterildiği gibi, bu alıcı sepeti microservice de durumu değiştirir.

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

Olay işleyicisinin, ürünün sepet örneklerinin herhangi birinde bulunup bulunmadığından doğrulanması gerekir. Ayrıca, ilgili her sepet satırı öğesi için madde fiyatını güncelleştirir. Son olarak, Şekil 6-24'te gösterildiği gibi fiyat değişikliği hakkında kullanıcıya görüntülenecek bir uyarı oluşturur.

![Kullanıcı sepetindeki fiyat değişikliği bildirimini gösteren bir tarayıcının ekran görüntüsü.](./media/subscribe-events/display-item-price-change.png)

**Şekil 6-24**. Tümleştirme olayları tarafından iletildiği gibi, bir sepette madde fiyat değişikliğini görüntüleme

## <a name="idempotency-in-update-message-events"></a>İleti olaylarını güncelleştirmede idempotency

İleti olaylarını güncelleştirmenin önemli bir yönü, iletişimin herhangi bir noktasındaki bir hatanın iletinin yeniden denenmesine neden olmasıdır. Aksi takdirde, arka plandaki bir görev, bir yarış koşulu oluşturarak zaten yayımlanmış bir olayı yayımlamaya çalışabilir. Güncelleştirmelerin iktidara geldiklerinden veya bir yinelenenalgılayabilmenizi, atabilmenizi ve yalnızca bir yanıt gönderebilmenizi sağlamak için yeterli bilgi sağladıklarından emin olmanız gerekir.

Daha önce de belirtildiği gibi, idempotency bir işlem sonucu değiştirmeden birden çok kez yapılabilir anlamına gelir. İleti ortamında, olayları iletirken olduğu gibi, bir olay alıcı mikrohizmetinin sonucunu değiştirmeden birden çok kez teslim edilebiliyorsa, idempotenttir. Bu, olayın doğası nedeniyle veya sistemin olayı işleme biçimi nedeniyle gerekli olabilir. İleti idempotency, yalnızca olay veri çileti deseni uygulayan uygulamalarda değil, ileti kullanan her uygulamada önemlidir.

Idempotent bir işlem örneği, yalnızca bu veriler tabloda yoksa, tabloya veri ekleyen bir SQL deyimidir. Bu insert SQL deyimini kaç kez çalıştırdığınızın bir önemi yok; sonuç aynı olacaktır-tablo bu verileri içerecektir. İletiler potansiyel olarak gönderilebiliyorsa ve bu nedenle birden fazla kez işlenebilirse, bu gibi idempotency de iletileri ile ilgili olarak gerekli olabilir. Örneğin, yeniden deneme mantığı gönderenin aynı iletiyi birden çok kez göndermesine neden oluyorsa, bunun etkili olduğundan emin olmanız gerekir.

İktidara gelen iletiler tasarlamak mümkündür. Örneğin, "ürün fiyatına 5 TL eklemek" yerine "ürün fiyatını 25 TL olarak ayarlayın" yazan bir etkinlik oluşturabilirsiniz. İlk iletiyi herhangi bir kez güvenli bir şekilde işleyebilir ve sonuç aynı olacaktır. Bu ikinci mesaj için doğru değil. Ancak ilk durumda bile, ilk olayı işlemek istemeyebilirsiniz, çünkü sistem daha yeni bir fiyat değişikliği olayı da göndermiş olabilir ve yeni fiyatın üzerine bir yazı yazmış olabilirsiniz.

Başka bir örnek, birden çok aboneye yayılan sipariş tamamlanmış bir olay olabilir. Aynı sipariş tamamlanan olay için yinelenen ileti olayları olsa bile, sipariş bilgilerinin diğer sistemlerde yalnızca bir kez güncellenmesi önemlidir.

Her olayın alıcı başına yalnızca bir kez işlenmesini gerektiren bir mantık oluşturabilmeniz için olay başına bir tür kimliğe sahip olmak uygundur.

Bazı ileti işleme doğal olarak idempotent olduğunu. Örneğin, bir sistem resim küçük resimleri oluşturuyorsa, oluşturulan küçük resimle ilgili iletinin kaç kez işlendiğiönemli olmayabilir; sonuç küçük resimler oluşturulur ve her zaman aynıdır. Öte yandan, kredi kartından ücret almak için ödeme ağ geçidi aramak gibi işlemler hiç de dedempotent olmayabilir. Bu gibi durumlarda, bir iletiyi birden çok kez işlemenin beklediğiniz etkiye sahip olduğundan emin olmanız gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Onur mesajı idempotency** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Tümleştirme olay iletilerini deduplicating

İleti olaylarının farklı düzeylerde abone başına sadece bir kez gönderildiğinden ve işlendiğinden emin olabilirsiniz. Bir yol, kullanmakta olduğunuz mesajlaşma altyapısı tarafından sunulan bir çoğaltma özelliğikullanmaktır. Başka bir hedef microservice özel mantık uygulamaktır. Hem taşıma düzeyinde hem de uygulama düzeyinde doğrulamalara sahip olmak en iyi bahistir.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>EventHandler düzeyinde ileti olaylarını deduplicating

Bir olayın herhangi bir alıcı tarafından sadece bir kez işlendiğinden emin olmak için bir yolu olay işleyicileri ileti olayları işlerken belirli bir mantık uygulamaktır. Örneğin, [usercheckoutAcceptedIntegrationHandler sınıfının kaynak kodunda](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) gördüğünüz gibi, eShopOnContainers uygulamasında kullanılan yaklaşım, usercheckoutAcceptedIntegrationEvent event olay olayını aldığında. (Bu durumda, komut işleyicisine göndermeden önce eventMsg.RequestId'i tanımlayıcı olarak kullanarak CreateOrderCommand'ı bir IdentifiedCommand ile sarıyoruz).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>RabbitMQ kullanırken iletileri boyama

Aralıklı ağ hataları olduğunda, iletiler çoğaltılabilir ve ileti alıcısının bu yinelenen iletileri işlemek için hazır olması gerekir. Mümkünse, alıcılar iletileri açık bir şekilde çoğaltma ile işlemek daha iyi bir idempotent bir şekilde ele almalıdır.

[RabbitMQ belgelerine](https://www.rabbitmq.com/reliability.html#consumer)göre , "Bir ileti bir tüketiciye teslim edilir ve sonra yeniden sıraya girilirse (örneğin, tüketici bağlantısı düşmeden önce kabul edilmediği için) RabbitMQ yeniden teslim edildiğinde (aynı tüketiciye veya farklı bir mesaja) yeniden teslim edilen bayrağı ayarlar.

"Yeniden teslim" bayrağı ayarlanmışsa, ileti zaten işlenmiş olabileceğinden alıcı bunu dikkate almalıdır. Ama bu garanti edilmez; ileti, ileti aracısını bıraktıktan sonra, belki de ağ sorunları nedeniyle alıcıya hiç ulaşmamış olabilir. Diğer taraftan, "yeniden teslim" bayrağı ayarlanmadıysa, iletinin birden fazla gönderilmediği garanti edilir. Bu nedenle, alıcının iletileri yalnızca iletide "yeniden teslim" bayrağı ayarlanırsa, iletileri veya işlemleri idempotent bir şekilde devreden olması gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

- **NServiceBus (Özel Yazılım) kullanarak Çatallı eShopOnContainers** \
    <https://go.particular.net/eShopOnContainers>

- **Olay Odaklı Mesajlaşma** \
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- **Jimmy Bogard' ı. Esneklik Doğru Refactoring: Bağlantı Değerlendirme** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **Yayınla-Abone Ol** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Sınırlı Bağlamlar Arasında İletişim** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Nihai Tutarlılık** \
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Philip Brown' ı. Sınırlı Bağlamları Bütünleştirme Stratejileri** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson' ı. Agregalar, Olay Kaynak ve CQRS Kullanarak İşlemsel Mikrohizmetler Geliştirme - Bölüm 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson' ı. Olay Kaynak deseni** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Tanıtıcı Etkinlik Kaynak** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Olay Deposu veritabanı.** Resmi site. \
    <https://geteventstore.com/>

- **Patrick Nommensen' ı. Mikro hizmetler için Etkinlik Odaklı Veri Yönetimi** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **CAP Teoremi** \
    <https://en.wikipedia.org/wiki/CAP_theorem>

- **CAP Teoremi Nedir?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Veri Tutarlılığı Astarı** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. CAP Teoremi: Neden "Her Şey Farklı" Bulut ve İnternet ile** \
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewer' ı. CAP On iki Yıl Sonra: Nasıl "Kurallar" Değişti** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Servis Veri Servisi. Aracılı Mesajlaşma: Yinelenen Algılama**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Güvenilirlik Kılavuzu** (RabbitMQ belgeleri) \
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> [Önceki](rabbitmq-event-bus-development-test-environment.md)
> [Sonraki](test-aspnet-core-services-web-apps.md)
