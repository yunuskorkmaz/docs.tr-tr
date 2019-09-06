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
# <a name="subscribing-to-events"></a>Olaylara abone olma

Olay veri yolunu kullanmanın ilk adımı, mikro hizmetlerin almak istedikleri olaylara abone olmadır. Bu, alıcının mikro hizmetlerinde yapılmalıdır.

Aşağıdaki basit kod, hizmet başlatıldığında (yani, `Startup` sınıfında), ihtiyaç duyacağı olaylara abone olmak için her bir alıcı mikro hizmetinin ne yapması gerektiğini gösterir. Bu durumda, `basket.api` mikro hizmet 'e `ProductPriceChangedIntegrationEvent` abone olmalıdır ve `OrderStartedIntegrationEvent` iletileri.

Örneğin, `ProductPriceChangedIntegrationEvent` olaya abone olurken, sepet mikro hizmetini ürün fiyatındaki herhangi bir değişikliği fark ettiğini ve bu ürün kullanıcının sepetinde olduğunda değişikliği hakkında kullanıcıyı uyarmasını sağlar.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Bu kod çalıştıktan sonra, abone mikro hizmeti, Kbbitmq kanalları aracılığıyla dinleme yapar. Productpricechangedıntemetionevent türünde herhangi bir ileti ulaştığında, kod kendisine geçirilen olay işleyicisini çağırır ve olayı işler.

## <a name="publishing-events-through-the-event-bus"></a>Olay veri yolu aracılığıyla olayları yayımlama

Son olarak, ileti gönderici (Origin mikro hizmeti), tümleştirme olaylarını aşağıdaki örneğe benzer kodla yayımlar. (Bu, hesapta kararlılık olmayan basitleştirilmiş bir örnektir.) Her bir olayın birden fazla mikro hizmette yayılması gerektiğinde, genellikle kaynak mikro hizmetinden veri veya işlem gerçekleştirildikten sonra, benzer bir kod uygulamalısınız.

İlk olarak, aşağıdaki kodda olduğu gibi, olay veri yolu uygulama nesnesi (Kbbitmq veya bir Service Bus tabanlı olarak) denetleyici oluşturucusuna eklenir:

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

Bu durumda, UpdateProduct yönteminde olduğu gibi denetleyicinin yöntemlerinden yararlanabilirsiniz:

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

Bu durumda, kaynak mikro hizmet basit bir CRUD mikro hizmet olduğundan, bu kod bir Web API denetleyicisine doğrudan yerleştirilir.

Daha gelişmiş mikro hizmetlerde, CQRS yaklaşımları kullanırken olduğu gibi, `CommandHandler` `Handle()` yöntemi içinde sınıfında uygulanabilir.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Olay veri yoluna yayımlarken kararlılık ve dayanıklılık tasarlama

Olay veri yolu gibi dağıtılmış bir mesajlaşma sistemi aracılığıyla tümleştirme olaylarını yayımladığınızda, özgün veritabanını otomatik olarak güncelleştirme ve bir olay yayımlama (yani, her iki işlem de tamamlanmamış ya da hiçbiri) ile ilgili sorun oluşur. Örneğin, daha önce gösterilen Basitleştirilmiş örnekte kod, ürün fiyatı değiştirildiğinde verileri veritabanına kaydeder ve sonra bir Productpricechangedıntegrationevent iletisi yayımlar. Başlangıçta, bu iki işlemin otomatik olarak gerçekleştirilmesi için önemli görünebilir. Bununla birlikte, [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)gibi eski sistemlerde yaptığınız gibi, veritabanı ve ileti Aracısı ile ilgili dağıtılmış bir işlem kullanıyorsanız, bu, bu [sınır](https://www.quora.com/What-Is-CAP-Theorem-1)sonunda açıklanan nedenlerden dolayı önerilmez.

Temel olarak, mikro hizmetleri, ölçeklenebilir ve yüksek oranda kullanılabilir sistemler oluşturmak için kullanırsınız. Biraz basitleşerek, CAP 'ler sürekli olarak kullanılabilir, güçlü tutarlı *ve* herhangi bir bölüme dayanıklı bir (dağıtılmış) veritabanı (veya modeline sahip bir mikro hizmet) oluşturamazsınız. Bu üç özelliklerden ikisini de seçmeniz gerekir.

Mikro hizmet tabanlı mimarilerde kullanılabilirlik ve tolerans ' i seçmeniz gerekir ve güçlü tutarlılığı vurgulamalısınız. Bu nedenle, çoğu modern mikro hizmet tabanlı uygulamalarda, Windows Dağıtılmış İşlem Düzenleyicisi (DTC) tabanlı [Dağıtılmış işlemler](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) uyguladığınızda yaptığınız gibi genellikle mesajlaşma 'da dağıtılmış işlemleri kullanmak istemezsiniz. [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)ile.

İlk soruna ve bu örneğe geri dönelim. Veritabanı güncelleştirildikten sonra hizmet çöktüğünde (Bu durumda, \_bağlamdaki kod satırından hemen sonra). SaveChangesAsync ()), ancak tümleştirme olayı yayımlanmadan önce genel sistem tutarsız hale gelebilir. Bu, ilgilendiğiniz belirli iş işlemine bağlı olarak iş açısından kritik olabilir.

Mimari bölümünde daha önce bahsedildiği gibi, bu sorunla ilgilenirken çeşitli yaklaşımlara sahip olabilirsiniz:

- Tam olay kaynağını belirleme [düzenini](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)kullanma.

- [İşlem günlüğü madenciliği](https://www.scoop.it/t/sql-server-transaction-log-mining)kullanılıyor.

- [Giden kutusu deseninin](http://gistlabs.com/2014/05/the-outbox/)kullanımı. Bu, tümleştirme olaylarını depolamak için (yerel işlemi genişletme) bir işlem tablosudur.

Bu senaryo için tam olay kaynağını belirleme (ES) deseni en iyi yaklaşımlardan biri değilse kullanmaktır *en* iyi. Bununla birlikte, birçok uygulama senaryosunda, bir tam ES sistemi uygulamaımayabilir. ES, geçerli durum verilerini depolamak yerine yalnızca işlem veritabanınızda bulunan etki alanı olaylarını depolayan anlamına gelir. Yalnızca etki alanı olaylarının depolanması, sisteminizin geçmişini ve geçmişteki bir zamanda sisteminizin durumunu tespit etmek gibi harika avantajlar elde edebilir. Ancak, bir tam ES sisteminin uygulanması sisteminizin çoğunu yeniden mimararak birçok karmaşıklığın ve gereksinimin tanıtılmasının yapılmasını gerektirir. Örneğin, Event [Store](https://eventstore.org/)veya Azure Cosmos DB, MongoDB, Cassandra, couşdb veya ırvendb gibi belge yönelimli bir veritabanı için özel olarak oluşturulan bir veritabanını kullanmak isteyebilirsiniz. Daha önce olay kaynağını öğrenmediğiniz müddetçe, bu soruna yönelik harika bir yaklaşım, ancak en kolay çözüm değildir.

İşlem günlüğü madenciliği ilk başta kullanma seçeneği çok saydam görünüyor. Ancak, bu yaklaşımı kullanmak için mikro hizmetin SQL Server işlem günlüğü gibi RDBMS işlem günlüğü ile bağlanmış olması gerekir. Bu muhtemelen istenmez. Diğer bir sakıncası, işlem günlüğünde kayıtlı olan alt düzey güncelleştirmelerin, üst düzey tümleştirme olaylarınız ile aynı düzeyde olmaması olabilir. Bu durumda, bu işlem günlüğü işlemlerinin tersine mühendislik işlemi zor olabilir.

Dengeli yaklaşım, bir işlem veritabanı tablosu ve Basitleştirilmiş ES deseninin bir karışımıdır. Tümleştirme olayları tablosuna kaydettiğinizde, özgün olayında ayarladığınız "olayı yayımlamaya hazırlanma" gibi bir durum kullanabilirsiniz. Daha sonra olayı olay veri yoluna yayımlamayı deneyin. Yayımla-olay eylemi başarılı olursa, kaynak hizmetinde başka bir işlem başlatır ve durumu "olayı yayımlanmaya hazırlanıyor" olarak "olay zaten yayımlandı" olarak taşırsınız.

Olay veri yolundaki Yayımla-olay eylemi başarısız olursa, veriler yine de kaynak mikro hizmeti içinde tutarsız olmaz — yine de "olay yayımlanmaya hazırlanıyor" olarak işaretlenir ve hizmetin geri kalanına göre, sonuçta tutarlı olur. Her zaman arka plan işlerinin işlem durumunu veya tümleştirme olaylarını denetlemesini sağlayabilirsiniz. İş "olay yayımlamaya hazırlanıyor" durumunda bir olay bulursa, bu olayı olay veri yoluna yeniden yayımlamayı deneyebilir.

Bu yaklaşımda, yalnızca her bir kaynak mikro hizmeti için tümleştirme olaylarını ve yalnızca diğer mikro hizmetlerle veya dış sistemlerle iletişim kurmak istediğiniz olayları kalıcı hale getirmeniz gerektiğini unutmayın. Buna karşılık, bir tam ES sisteminde, tüm etki alanı olaylarını da depoladığınızda.

Bu nedenle, bu dengeli yaklaşım basitleştirilmiş bir sistemdir. Tümleştirme olaylarının bir listesine ("yayımlamaya hazırlanın" ve "yayımlanmış") sahip olmanız gerekir. Ancak yalnızca tümleştirme olayları için bu durumları uygulamanız gerekir. Bu yaklaşımda, tüm etki alanı verilerinizi, tam ES sisteminde yaptığınız gibi işlem veritabanına olay olarak depolamanız gerekmez.

Zaten ilişkisel bir veritabanı kullanıyorsanız, tümleştirme olaylarını depolamak için bir işlemsel tablo kullanabilirsiniz. Uygulamanızda kararlılık elde etmek için, yerel işlemlere göre iki adımlı bir işlem kullanırsınız. Temel olarak, etki alanı varlıklarınızın bulunduğu veritabanında bir ıntegrationevent tablonuz vardır. Bu tablo, etki alanı verilerinizi yürüten işlemlere kalıcı tümleştirme olayları dahil etmeniz için, kararlılık elde etmek üzere bir sigorta olarak çalışmaktadır.

Adım adım, işlem şöyle gider:

1. Uygulama, yerel bir veritabanı işlemi başlatır.

2. Ardından, etki alanı varlıklarınızın durumunu güncelleştirir ve tümleştirme olay tablosuna bir olay ekler.

3. Son olarak, işlem, istenen kararlılık 'i ve ardından

4. Olayı bir şekilde yayımlarsınız (ileri).

Olayları yayımlama adımlarını uygularken şu seçeneklere sahip olursunuz:

- İşlem tamamlandıktan sonra tümleştirme olayını yayımlayın ve tablodaki olayları yayımlanmakta olarak işaretlemek için başka bir yerel işlem kullanın. Daha sonra, uzak mikro hizmetlerde sorun olması durumunda tümleştirme olaylarını izlemek ve depolanan tümleştirme olaylarına göre telafi işlemleri gerçekleştirmek için, tabloyu yapıt olarak kullanın.

- Tabloyu kuyruk türü olarak kullanın. Ayrı bir uygulama iş parçacığı veya işlemi, tümleştirme olay tablosunu sorgular, olayları olay veri yoluna yayımlar ve sonra olayları yayımlandı olarak işaretlemek için yerel bir işlem kullanır.

Şekil 6-22, bu yaklaşımların ilki için mimari gösterir.

![Olayları yayımlarken kararlılık 'i işlemeye yönelik bir yaklaşım: bir olay günlüğü tablosuna olay yürütmek için bir işlem kullanın ve ardından yayımlanacak başka bir işlem (eshoponcontainers 'da kullanılır)](./media/image23.png)

**Şekil 6-22**. Olay veri yoluna olay yayımlarken Atomicity

Şekil 6-22 ' de gösterilen yaklaşımda, yayımlanan tümleştirme olaylarının başarısını denetleme ve onaylama aşamasında olan ek bir çalışan mikro hizmeti eksik. Hata durumunda ek denetleyici Worker mikro hizmeti, tablodaki olayları okuyabilir ve yeniden yayımlayabilir, diğer bir deyişle adım 2 ' yi tekrarlayabilirler.

İkinci yaklaşım hakkında: olay günlüğü tablosunu kuyruk olarak kullanın ve iletileri yayımlamak için her zaman bir çalışan mikro hizmetini kullanın. Bu durumda, işlem Şekil 6-23 ' de gösterilenle benzer. Bu, ek bir mikro hizmet gösterir ve olaylar yayımlandığında tablo tek kaynaktır.

![Atomicity 'i işlemeye yönelik başka bir yaklaşım: Olay günlüğü tablosuna yayımlayın ve sonra başka bir mikro hizmet (arka plan çalışanı) olayını yayımlayın.](./media/image24.png)

**Şekil 6-23**. Bir çalışan mikro hizmeti ile olay veri yoluna olay yayımlarken Atomicity

Basitlik için eShopOnContainers örneği, ilk yaklaşımı (ek işlem veya denetleyici mikro hizmetleri olmadan) ve olay veri yolunu kullanır. Ancak eShopOnContainers, olası tüm hata durumlarını işlemez. Buluta dağıtılan gerçek bir uygulamada, sorunların sonunda ortaya çıkması ve bu denetimi ve yeniden gönder mantığını uygulamanız gerekir. Tabloyu bir sıra olarak kullanmak, bu tabloyu olay veri yolundan yayımlalarken (çalışan ile) tek bir olay kaynağı olarak kullandığınızda ilk yaklaşımdan daha etkili olabilir.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Olay veri yolu aracılığıyla tümleştirme olaylarını yayımlarken kararlılık uygulama

Aşağıdaki kod, birden çok DbContext nesnesi içeren tek bir işlem oluşturabileceğiniz gibi, güncelleştirilmekte olan özgün verilerle ilgili bir bağlam ve ıntegrationeventlog tablosu ile ilgili ikinci bağlam.

Aşağıdaki örnek kodundaki işlemin, veritabanı bağlantıları, kodun çalıştığı sırada herhangi bir sorun varsa, bu işlem için dayanıklı olmaz. Bu durum, veritabanlarını sunucular arasında taşıyabilecek Azure SQL VERITABANı gibi bulut tabanlı sistemlerde meydana gelebilir. Birden çok bağlamdaki esnek işlemleri uygulamak için, bu kılavuzun ilerleyen kısımlarında dayanıklı [ENTITY Framework Core SQL bağlantıları uygulama](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) bölümüne bakın.

Açıklık açısından aşağıdaki örnek tek bir kod parçası olarak tüm işlemi gösterir. Ancak eShopOnContainers uygulamasının gerçekten yeniden düzenlenmiş ve bu mantığı birden çok sınıfa bölerek daha kolay korunması kolaylaşır.

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

Productpricechangedıntegrationevent Integration olayı oluşturulduktan sonra, özgün etki alanı işlemini depolayan işlem (Katalog öğesini Güncelleştir) Ayrıca olay günlüğü tablosunda olayın kalıcılığını da içerir. Bu, tek bir işlem yapar ve olay iletilerinin gönderilip gönderilmeyeceğini her zaman kontrol edebileceksiniz.

Aynı veritabanına karşı yerel bir işlem kullanılarak olay günlüğü tablosu, özgün veritabanı işlemiyle otomatik olarak güncelleştirilir. İşlemlerden herhangi biri başarısız olursa, bir özel durum oluşturulur ve işlem tüm tamamlanmış işlemleri geri alır, böylece etki alanı işlemleri ile tabloya kaydedilen olay iletileri arasındaki tutarlılığı koruyun.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Aboneliklerden ileti alma: alıcı mikro hizmetlerindeki olay işleyicileri

Olay aboneliği mantığına ek olarak, tümleştirme olay işleyicileri için iç kodu uygulamanız gerekir (geri çağırma yöntemi gibi). Olay işleyicisi, belirli bir türdeki olay iletilerinin nerede alındığını ve işleneceğini belirlediğiniz yerdir.

Olay işleyicisi önce olay veri yolundan bir olay örneği alır. Daha sonra bu tümleştirme olayı ile ilgili işlenecek bileşeni konumlandırır, alıcı mikro hizmetindeki durum değişikliği olarak olayı yayın ve kalıcı hale getirmeyi sağlar. Örneğin, bir ProductPriceChanged olayının kataloğu mikro hizmetinde kaynağı varsa, bu, sepet mikro hizmetinde işlenir ve aşağıdaki kodda gösterildiği gibi bu alıcı Sepeti mikro hizmetindeki durumu da değiştirir.

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

Olay işleyicisinin, ürünün sepet örneklerinde mevcut olup olmadığını doğrulaması gerekir. Ayrıca ilgili her sepet satırı öğesi için öğe fiyatını güncelleştirir. Son olarak, Şekil 6-24 ' de gösterildiği gibi, kullanıcıya fiyat değişikliği hakkında görüntülenmek üzere bir uyarı oluşturur.

![Kullanıcı sepetindeki işlem değişikliği bildiriminin tarayıcı görünümü.](./media/image25.png)

**Şekil 6-24**. Bir sepetteki bir öğe fiyat değişikliğini tümleştirme olayları tarafından iletilen şekilde görüntüleme

## <a name="idempotency-in-update-message-events"></a>Güncelleştirme iletisi olaylarında ıdempot

Güncelleştirme iletisi olaylarının önemli bir yönü, iletişimin herhangi bir noktasında başarısız olmasının iletinin yeniden denenmesine neden olması gerekir. Aksi halde, bir arka plan görevi zaten yayımlanmış olan bir olayı yayımlamayı deneyebilir, bir yarış durumu oluşturuyor olabilir. Güncelleştirmelerin ıdempotent olduğundan ya da bir yinelemeyi tespit edip yalnızca bir yanıt gönderdiğinizden emin olmak için yeterli bilgi sağladıklarından emin olmanız gerekir.

Daha önce belirtildiği gibi, ıdempot, bir işlemin sonucu değiştirmeksizin birden çok kez gerçekleştirilebileceği anlamına gelir. Bir mesajlaşma ortamında, olayları kullanırken olduğu gibi, alıcı mikro hizmeti için sonucu değiştirmeden birden çok kez teslim edilebilir bir olay ıdempotent olur. Bu, olayın kendisinin doğası veya sistemin olayı işleme biçimi nedeniyle gerekli olabilir. İleti ıdempoti, yalnızca olay veri yolu modelini uygulayan uygulamalarda değil, mesajlaşma kullanan herhangi bir uygulamada önemlidir.

Bir ıdempotent işlemine örnek olarak, yalnızca bu veriler tabloda yoksa tabloya veri ekleyen bir SQL deyimidir. Bu, SQL ifadesini eklemek için kaç kez çalıştırılcağınızı değil; Sonuç aynı olacaktır — tablo bu verileri içerir. Benzer şekilde, iletiler gönderilebileceği ve bu nedenle birden çok kez işlenen iletilerle ilgilenirken bu da gerekli olabilir. Örneğin, yeniden deneme mantığı bir göndericinin aynı iletiyi birden çok kez göndermesini sağlar, bunun ıdempotent olduğundan emin olmanız gerekir.

Idempotent iletilerini tasarlamak mümkündür. Örneğin, "ürün fiyatını $25 olarak ayarla" $5 yerine "ürün fiyatını" olarak belirten bir olay oluşturabilirsiniz. İlk iletiyi herhangi bir sayıda kez güvenli bir şekilde işleyebilir ve sonuç aynı olacaktır. Bu, ikinci ileti için doğru değildir. Ancak ilk durumda da, sistem daha yeni bir fiyat değişikliği olayı göndermiş olabileceğinden ve yeni fiyatın üzerine yazılabileceğinden, ilk olayı işlemek istemeyebilirsiniz.

Diğer bir örnek, birden çok aboneye yayılmakta olan sıralı tamamlanmış bir olay olabilir. Aynı sipariş tamamlandı olayı için yinelenen ileti olayları olsa bile, yalnızca bir kez diğer sistemlerdeki sipariş bilgilerinin güncelleştirilmesini önemlidir.

Her olayın her alıcı için yalnızca bir kez işlenmesini zorlayan mantık oluşturabilmeniz için olay başına bir tür kimliğe sahip olmak kullanışlıdır.

Bazı ileti işleme, kendiliğinden ıdempotent. Örneğin, bir sistem görüntü küçük resimleri oluşturursa, oluşturulan küçük resim ile ilgili iletinin kaç kez işlendiğine bakılmaksızın bu durum oluşabilir. Sonuç olarak, küçük resimlerin oluşturulması ve her seferinde aynı olması önemlidir. Diğer taraftan, kredi kartı ücreti almak için ödeme ağ geçidini çağırma gibi işlemler ıdempotent olmayabilir. Bu durumlarda, bir iletiyi birden çok kez işlemenin bekleeceğiniz etkiye sahip olduğundan emin olmanız gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

- **İleti tekisliliği** <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Tümleştirme olayı iletilerini Çoğaltma kaldırma

İleti olaylarının her abone için farklı düzeylerde yalnızca bir kez gönderilmesini ve işlenmesini sağlayabilirsiniz. Tek yönlü, kullanmakta olduğunuz mesajlaşma altyapısı tarafından sunulan yinelenenleri kaldırma özelliğini kullanmaktır. Diğer bir deyişle, hedef mikro hizmetinize özel mantık uyguğıdır. Hem Aktarım düzeyinde hem de uygulama düzeyinde doğrulamaları olan en iyi sonuç.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>EventHandler düzeyinde ileti olaylarını kaldırma

Bir olayın her alıcı tarafından yalnızca bir kez işlendiğinden emin olmanın bir yolu, olay işleyicilerindeki ileti olaylarını işlerken belirli bir mantığı uygulamalardır. Örneğin, eShopOnContainers uygulamasında kullanılan yaklaşım, bir Usercheckoutacceptedinteıntionevent tümleştirme olayı aldığında [Usercheckoutacceptedınteuttioneventhandler sınıfının kaynak kodunda](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) görebileceğiniz gibi. (Bu durumda, komut işleyicisine göndermeden önce eventMsg. RequestId öğesini tanımlayıcı olarak kullanarak CreateOrderCommand öğesini bir IdentifiedCommand sardık.

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Kbbitmq kullanırken iletilerin Çoğaltma kaldırma

Aralıklı ağ arızalarının meydana gelmesi durumunda iletiler yinelenebilir ve ileti alıcısı bu yinelenen iletileri işlemeye hazırlanmalıdır. Mümkünse, alıcıların iletileri ıdempotent bir şekilde işlemesi gerekir ve bu, onları yinelenenleri kaldırma ile açıkça işlemenin daha iyi bir yoludur.

[Kbbitmq belgelerine](https://www.rabbitmq.com/reliability.html#consumer)göre, "bir ileti tüketiciye teslim edildiğinde ve sonra yeniden kuyruğa (tüketici bağlantısı bırakılmadan önce onaylanmadığı için), Kbbitmq, teslim edildiğinde yeniden teslim edilen bayrağını ayarlar yeniden (aynı tüketici mi yoksa farklı bir tane mi olduğunu).

"Yeniden teslim edildi" bayrağı ayarlandıysa, ileti zaten işlenmiş olabileceğinden alıcı bu hesabı dikkate almalıdır. Ancak bu garanti edilmez; ileti, ağ sorunları nedeniyle ileti aracısından ayrıldıktan sonra alıcıya hiçbir şekilde ulaşmamış olabilir. Öte yandan, "yeniden teslim edildi" bayrağı ayarlanmamışsa, iletinin birden çok kez gönderilmediği garanti edilir. Bu nedenle, alıcının iletileri yinebir ıdempotent şekilde işlemesi veya ileti içinde "yeniden teslim edildi" bayrağı ayarlandıysa iletileri işlemesi gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

- **NServiceBus (belirli yazılımlar) kullanılarak forlenmiş eShopOnContainers** \
    <https://go.particular.net/eShopOnContainers>

- **Olay odaklı mesajlaşma** \
    [http://soapatterns.org/design\_patterns/event\_driven\_messaging](http://soapatterns.org/design_patterns/event_driven_messaging)

- **Jimmy Bogard. Esnekliği doğru yeniden düzenleme: Kupın değerlendirmesi** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **Yayımla-abone ol kanalı** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Sınırlanmış bağlamlar arasında iletişim kurma** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Nihai tutarlılık** \
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- **Philip kahverengi. Sınırlı bağlamlara tümleştirme stratejileri** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson. Toplamaları kullanarak Işlem mikro hizmetleri geliştirme, olay kaynağını belirleme ve CQRS-2. Bölüm** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson. Olay kaynağını belirleme kalıbı** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Olay kaynağını belirleme** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Olay deposu veritabanı**. Resmi site. \
    <https://geteventstore.com/>

- **Patrick Nmmensen. Mikro hizmetler için olay odaklı Veri Yönetimi** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **Üst sınır** \
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- **SıNıR nedir?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Veri tutarlılığı öncü** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick sallama. CAP 'ler: Bulut ve Internet ile neden "her şey farklıdır"**  \
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewer. BÜYÜK on Iki yıl sonra: "Kurallar" nasıl değişmiştir** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Aracılı mesajlaşma: Yinelenen algılama**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Güvenilirlik Kılavuzu** (Oybbitmq belgeleri) \
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

> [!div class="step-by-step"]
> [Önceki](rabbitmq-event-bus-development-test-environment.md)İleri
> [](test-aspnet-core-services-web-apps.md)
