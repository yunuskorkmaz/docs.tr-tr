---
title: Olaylara abone olma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Yayımlama ve tümleştirme olayları için abonelik ayrıntılarını anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: eef1ad347cb621e1f26c9c65d46d71e83a2c3a23
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971786"
---
# <a name="subscribing-to-events"></a>Olaylara abone olma

Olay veri yolu kullanmanın ilk adımı, mikro hizmetler almak istediği olaylara abone olmaktır. Alıcı mikro Hizmetleri yapılmalıdır.

Aşağıdaki basit kod her alıcı mikro hizmete uygulamak gereken gösterir (diğer bir deyişle, `Startup` sınıfı) şekilde bu olayları, ihtiyaçlarını kaydeder. Bu durumda, `basket.api` mikro hizmet abone olmak için gereksinim duyduğu `ProductPriceChangedIntegrationEvent` ve `OrderStartedIntegrationEvent` iletileri. 

Örneğin, abone olduğunda `ProductPriceChangedIntegrationEvent` sepet mikro hizmet herhangi farkında sağlayan bir olay ürün fiyatı değiştirir ve bu ürünün kullanıcının sepetteki ise değişiklik hakkında kullanıcıyı uyarmak olanak tanır.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

Bu kod çalıştırıldıktan sonra abone mikro hizmet RabbitMQ kanallar aracılığıyla dinleniyor olması. ProductPriceChangedIntegrationEvent türünde herhangi bir ileti geldiğinde, ona iletilen ve olayı işleyen olayı işleyicisi kodu çağırır.

## <a name="publishing-events-through-the-event-bus"></a>Olay veri yolu üzerinden olayları yayımlama

Son olarak, aşağıdaki örneğe benzer bir kod ile tümleştirme olayları (kaynak mikro hizmet) iletiyi gönderenin yayımlar. (Bu kararlılık dikkate almaz basitleştirilmiş bir örnek niteliğindedir.) Her olaya birden fazla mikro hizmetler, veri veya kaynak mikro hizmet içi işlemlerden uyguladıktan sonra genellikle doğru arasında dağıtılmalıdır benzer bir kod uygulayabilir.

İlk olarak, (RabbitMQ alarak veya temel bir service bus üzerinde) olay veri yolu uygulama nesnesi denetleyici Oluşturucu aşağıdaki kodu olduğu gibi eklenen:

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

Ardından, bu denetleyicinizin yöntemlerinden gibi UpdateProduct yöntemi kullanın:

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

Bu durumda, kaynak mikro hizmet basit CRUD mikro hizmeti olduğundan, bu kodu bir Web API denetleyicisi sağ yerleştirilir. 
 
Mikro hizmetlerde CQRS yaklaşımı kullanırken gibi daha gelişmiş, onu uygulanabilen `CommandHandler` içinde sınıf `Handle()` yöntemi. 

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Kararlılık ve dayanıklılık olay veri yoluna yayımlanırken tasarlama

Dağıtılmış Mesajlaşma aracılığıyla tümleştirme olayları yayımladığınızda, olay veri yolu gibi sistem, başarısızlığa uğrar özgün veritabanının güncelleştirilmesi ve olay (diğer bir deyişle, hem tam işlemleri veya bunların hiçbiri) yayımlama sorununu vardır. Ürün fiyatı değiştirilir ve ardından bir ProductPriceChangedIntegrationEvent ileti yayımlar örneği için Basitleştirilmiş örnekte, daha önce gösterilen kodu verilerini veritabanına kaydeder. Başlangıçta, bu iki işlemler atomik olarak gerçekleştirilmesini temel görünebilir. İlgili bir dağıtılmış işlem kullanıyorsanız gibi eski sistemlerde olduğu gibi ancak, veritabanı ve ileti, aracı [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), bu tarafındanaçıklanannedenleriyleönerilmez[CAP Teoremi](https://www.quora.com/What-Is-CAP-Theorem-1).

Temelde, mikro hizmetler, ölçeklenebilir ve yüksek oranda kullanılabilir sistemleri oluşturmak için kullanın. CAP Teoremi (dağıtılmış) bir veritabanı (veya kendi modelini sahibi olan bir mikro hizmet) derlenemiyor diyor biraz basitleştirme, sürekli olarak kullanılabilir ve son derece tutarlı *ve* dayanıklı herhangi bir bölümü için. Bu üç özellik ikilisi seçmeniz gerekir.

Mikro hizmet tabanlı mimariler, kullanılabilirlik ve dayanıklılık seçmelisiniz ve, güçlü tutarlılık devamlı müşterilerine göre ayarlayabilirler. Uygulamanız olarak bu nedenle, çoğu modern mikro hizmet tabanlı uygulamalar, genellikle mesajlaşmada, dağıtılmış işlemler kullanmak istediğiniz değil [dağıtılmış işlemler](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) Windows Dağıtılmış İşlem üzerinde temel Düzenleyicisi (DTC) ile [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Şimdi ilk sorun ve kendi örnek geçelim. Veritabanı güncelleştirildikten sonra hizmetin kilitlenmesi durumunda (Bu durumda, kod satırının sonra sağ \_bağlamı. SaveChangesAsync()), ancak tümleştirme olay yayımlanmadan önce sistemin tutarsız hale gelebilir. Bu, ilgilendiğiniz belirli iş işleme bağlı olarak kritik bir iş olabilir.

Mimari bölümünde daha önce bahsedildiği gibi bu sorunu uğraşmanızı için çeşitli yaklaşımlar olabilir:

-   Tam kullanarak [olay kaynağını belirleme düzeni](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

-   Kullanarak [işlem oturum araştırma](https://www.scoop.it/t/sql-server-transaction-log-mining).

-   Kullanarak [giden deseni](http://gistlabs.com/2014/05/the-outbox/). (Yerel işlem genişletme) tümleştirme olayları depolamak için bu işlem bir tablodur.

Bu senaryo için tam olay kaynağını belirleme (ES) deseni en iyi yaklaşımlardan biri değilse kullanmaktır *en* iyi. Ancak, birçok uygulama senaryolarında, tam bir ES sistemi uygulamak mümkün olmayabilir. Geçerli durumu verilerini depolamak yerine işlemsel veritabanı, yalnızca etki alanı olayları depolamak ES anlamına gelir. Yalnızca etki alanı olayları depolamadan gibi sistem geçmişini sahip olunması ve geçmişteki herhangi bir anda, sistem durumunu belirlemek için harika avantajlar, olabilir. Ancak, tam bir ES sistemi uygulama sisteminizi çoğunu yeniden oluşturma gerektiren ve diğer birçok karmaşıklık ve gereksinimler sunar. Örneğin, özellikle olay kaynağını belirleme için gibi yapılan bir veritabanı kullanmak isteyebilirsiniz [olay Store](https://eventstore.org/), veya bir Azure Cosmos DB, MongoDB, Cassandra, CouchDB veya RavenDB gibi belge yönelimli veritabanı. Olay kaynağını belirleme ile bilginiz sürece ES Bu sorun, ancak kolay çözümü için harika bir yaklaşımdır.

İşlem günlüğü başlangıçta araştırma kullanma seçeneği çok saydam arar. Ancak, bu yaklaşımı kullanmak için SQL Server işlem günlüğü gibi RDBMS işlem günlüğü için eşleştirilmek mikro hizmet vardır. Bu tercih edilir olmayabilir. Başka bir dezavantajı, işlem günlüğüne kaydedilen bir alt düzey güncelleştirmeleri, üst düzey tümleştirme olayları ile aynı düzeyde olmayabilir olmasıdır. Bu durumda, bu işlem günlüğü işlemleri tersine mühendislik işlemi zor olabilir.

İşlemsel veritabanı tablosu ve Basitleştirilmiş bir ES deseni bir karışımını buna dengeli bir yaklaşımdır. "Tümleştirme olayları tabloya işlerseniz özgün olay ayarlanan olayı yayımlamak için hazır" gibi bir durum kullanabilirsiniz. Ardından, olay, olay veri yoluna yayımlayamadı deneyin. Yayımlama olayı eylem başarılı olursa, başka bir işlem kaynağını hizmetini ve durumu "den olay yayımlanmaya hazır" taşıma "zaten yayımlanan olaya."

Yayımlama olayı eylem başarısız olay veri yolu, veriler yine de kaynak mikro hizmet içinde tutarsız olmaz; yine de "hazır olarak olayı yayımlamak" işaretlenmiş olması ve ilgili rest Hizmetleri sonunda tutarlı olur. Her zaman, işlemler veya tümleştirme olayları durumunu denetleme arka plan işleri de sahip olabilir. İş "olayı yayımlamak hazır" durumunda bir olay bulunursa, bu olay Olay Bus yeniden yayımlamayı deneyebilirsiniz.

Bu yaklaşımda, yalnızca tümleştirme olayları için her kaynak mikro hizmet ve diğer mikro hizmetler veya dış sistemler için kurmak istediğiniz olayları kalıcı hale getirmeniz dikkat edin. Buna karşılık, tam bir ES sistemde, tüm etki alanı olayları de depolar.

Bu nedenle, dengeli bu yaklaşım bir Basitleştirilmiş ES sistemidir. Tümleştirme olayları ile bunların geçerli durumunu listesi gerekir ("yayımlamak"yayımlanan "hazır"). Ancak bu durumlar için tümleştirme olayları uygulamak yeterlidir. Ve tam bir ES sisteminde olduğu gibi Bu yaklaşımda, olaylar işlemsel veritabanında olarak tüm etki alanı verileri depolamak ihtiyacınız yoktur.

İlişkisel bir veritabanı zaten kullanıyorsanız, tümleştirme olayları depolamak için bir işlem tablo kullanabilirsiniz. Kararlılık, uygulamanızda elde etmek için iki adımlı bir işlem yerel işlemlerden yola çıkarak kullanın. Temel olarak, etki alanı varlıklarınızı sahip olduğu aynı veritabanında IntegrationEvent tablo sahip. Bu tablo, bir sigorta dahil bir kararlılık elde etmek için etki alanı verilerinizi yürütülmekte olan aynı işlemleri tümleştirme olayları kalıcı olarak çalışır.

Adım adım işlemi şu şekilde geçer:

1.  Uygulama yerel veritabanı işlemi başlar.

2.  Etki alanı varlıklarınızın durumunu güncelleştirir ve bir olay tümleştirme olay tablosuna ekler.

3.  Son olarak, bu işlem işlemeler istenen kararlılık alabilmeniz ve ardından

4.  Olayı şekilde yayımlamak (İleri).

Olayları yayımlama adımları uygularken bu seçeneğiniz vardır:

-   Tümleştirme olay sağ işlem uyguladıktan sonra yayımlayın ve yayımlanan olarak tablo olayları işaretlemek için başka bir yerel işlem'ı kullanın. Ardından uzak mikro hizmetler sorunları yaşanması tümleştirme olayları izlemek için yalnızca bir yapıt tabloyu kullanın ve saklı tümleştirme etkinliklere göre telafi izin eylemleri gerçekleştirin.

-   Tablo, kuyruk bir tür olarak kullanın. Ayrı uygulama iş parçacığı veya işlem tümleştirme olay tablo sorguları, olayları olay veri yoluna yayımlar ve olayları yayınlanan olarak işaretlemek için bir yerel işlem'i kullanır.

Şekil 6-22 Bu yaklaşımların ilk mimarisi gösterilmektedir.

![Kararlılık olayları yayımlarken işlemek için bir yaklaşım: (kullanılan hizmetine) yayımlamak için bir işlem tamamlama olayına bir olay günlüğü tablosu ve başka bir işlem kullanma](./media/image23.png)

**Şekil 6-22**. Olaylar olay veri yoluna yayımlanırken kararlılık

Şekil 6-22'de gösterilen yaklaşımına denetleniyor ve yayımlanan tümleştirme olayları başarısını onaylayan sorumlu ek çalışan mikro hizmet eksik. Hata oluşması halinde, bu ek denetleyicisi çalışan mikro hizmet olayları tablodan okuyabilir ve bunları, 2. adımı yineleyin sayısı diğer bir deyişle, yeniden yayımlayın.

İkinci yaklaşım hakkında: olay günlüğü tablosu bir kuyruk kullanın ve her zaman iletileri yayımlamak için bir çalışan mikro hizmet kullanın. Bu durumda, işlem gibi Şekil 6-23 gösterilir. Bu ek bir mikro hizmet gösterir ve tek kaynak olayları yayımlarken tablosudur.

![Kararlılık işlemek için başka bir yaklaşım için: Bir olay günlüğü tabloya yayımlayın ve ardından olan başka bir mikro hizmet (arka plan çalışanı) yayımlama olayı.](./media/image24.png)

**Şekil 6-23**. Olayları çalışan mikro hizmet ile olay veri yoluna yayımlanırken kararlılık

Kolaylık olması için hizmetine örnek olay veri yolu (ile hiçbir ek işlemler veya denetleyicisi mikro hizmetler) ilk yaklaşımı kullanır. Ancak, hizmetine tüm olası hata koşulları işlenmiyor. Buluta dağıtılan gerçek bir uygulamada denetleyin ve yeniden mantıksal sorunları sonuçta ortaya çıkar ve uygulamanız gereken gerçeği benimseyin gerekir. Bunları (ile çalışan) olay veri yolu yayımlarken olay tek bir kaynak olarak bu tablonuz varsa tabloyu sırası olarak kullanarak bir ilk yaklaşım daha etkili olabilir.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Kararlılık tümleştirme olayları olay veri yolu üzerinden yayımlarken uygulama

Aşağıdaki kod, birden çok DbContext nesnelerini içeren tek bir işlem nasıl oluşturabileceğinizi gösterir; güncelleştirilen özgün verilerle ilgili bir içerik ve ilgili IntegrationEventLog tablonun ikinci bağlam.

Aşağıdaki örnek kod işlemde veritabanı bağlantılarını kodun çalıştığı sırada herhangi bir sorun varsa esnek olmayacağını unutmayın. Veritabanlarını sunucular arasında taşınmasını gerektirecek Azure SQL veritabanı gibi bulut tabanlı sistemlerde oluşabilir. Dayanıklı işlemler arasında birden fazla bağlamı uygulamak için bkz: [dayanıklı Entity Framework Core SQL bağlantıları uygulama](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) bu kılavuzun devamında bölümü.

Daha anlaşılır olması için aşağıdaki örnek, bu işlem tek bir kod parçasını gösterir. Ancak, hizmetine uygulama gerçekten bulunanad ve sürdürmek daha kolay olacak şekilde bu mantığı birden çok sınıflara bölme.

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

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

ProductPriceChangedIntegrationEvent tümleştirme olayı oluşturulduktan sonra özgün etki alanı işlemi (katalog öğesi güncelleştirme) depolayan işlem olayın Kalıcılık EventLog tabloda da içerir. Bu tek bir işlem yapar ve her zaman gönderilen olay iletileri olup olmadığını denetlemek mümkün olacaktır.

Olay günlüğü tablosu ile aynı veritabanında yerel bir işlem kullanarak özgün veritabanı işlemi, atomik olarak güncelleştirilir. İşlemleri başarısız olursa, bir özel durum ve işlem bu nedenle etki alanı işlemleri ve tabloya kaydedilen olay iletileri arasında tutarlılığı koruma herhangi bir tamamlanmış işlem geri alınır.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Aboneliklerden iletiler almaya: alıcısı, mikro hizmetler olay işleyicileri

Olay aboneliği mantığı ek olarak, iç kod (örneğin, bir geri arama yöntemi) tümleştirme olay işleyicileri için uygulamanız gerekir. Burada belirli bir türde olay iletileri işlenen ve alınacak belirttiğiniz olay işleyicisidir.

Bir olay işleyicisi, olay örneği ilk olay veri yolundan iletiyi alır. Ardından bu tümleştirme, yayma ve olay alıcısı mikro hizmet durumunda bir değişiklik olarak kalıcı hale olay, ilgili işlenecek bileşeni bulur. Örneğin, ProductPriceChanged olay Kataloğu mikro kaynaklanıyorsa, sepet mikro hizmet içinde işlenir ve aşağıdaki kodda gösterildiği gibi bu alıcı sepet mikro hizmet olarak iyi durumda değiştirir.

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

Ürün sepet örneği hiçbirinde var olup olmadığını doğrulamak olay işleyicisi gerekir. Ayrıca, her ilgili sepet satır öğesi için öğe fiyat güncelleştirir. Son olarak, Şekil 6-24'te gösterildiği gibi fiyat değişikliği hakkında kullanıcıya görüntülenecek bir uyarı oluşturur.

![İşlem Tarayıcı Görünümü Kullanıcı sepet bildirim değiştirin.](./media/image25.png)

**Şekil 6-24**. Bir öğe fiyat değişikliği sepet, tümleştirme olayları tarafından iletilen olarak görüntüleme

## <a name="idempotency-in-update-message-events"></a>Teklik update ileti olayları içinde

Update ileti olayları önemli bir yönüdür iletişimde herhangi bir noktada bir arıza denenmesi için iletiyi neden olmamalıdır olup. Aksi takdirde bir arka plan görevi, bir yarış durumu oluşturma yayımlanmış olduğu bir olay yayımlaması deneyebilir. Güncelleştirmelerin etkili veya yinelenen bir algılayabilir emin olmak için yeterli bilgi sağladıkları olduğunu emin olmak için atmak ve tek geri yanıt gönderir.

Daha önce belirtildiği gibi sonuç değiştirmeden bir işlem birden çok kez gerçekleştirilebilir Teklik anlamına gelir. İleti bir ortamda, birden çok kez alıcı mikro hizmet için sonucu değiştirmeden edinebilir, olayları iletişim kurarken, bir olay etkili olduğu gibi. Bu olayın yapısı nedeniyle gerekli olabilir veya şekli nedeniyle sistem olayını işler. İleti Teklik Mesajlaşma deposu kullanan herhangi bir uygulama, yalnızca olay veri yolu tasarımın uygulamalarda önemlidir.

Yalnızca bu veri tablosunda yoksa bir tabloya veri ekleyen bir SQL deyimi bir kez etkili işlem örneğidir. SQL deyimi ekleyin kaç kez çalıştırdığınız önemli değildir; Sonuç aynı olacaktır — tablo verileri içerir. Bu gibi Teklik, iletilerin potansiyel olarak gönderilebilir, iletileri ile ilgilenirken gerekirse ve bu nedenle işlenen defadan de olabilir. Örneğin, bir gönderici tam olarak aynı iletiyi birden çok kez göndermek yeniden deneme mantığı neden olursa, kez etkili olduğundan emin olmak gerekir.

Tasarım ıdempotent iletileri mümkündür. Örneğin, "25 ABD Doları ürün fiyatı"$5 ürün fiyatı eklemek yerine."set" ifadesini içeren bir olay oluşturabilirsiniz. İlk iletinin herhangi sayıda güvenli bir şekilde işleyebilir ve sonuç aynı olacaktır. Bu ikinci bir ileti için doğru değil. Ancak, hatta ilk durumda, sistem, daha yeni bir fiyat değişikliği olay gönderebilmesini ve yeni fiyatın üzerine yazılması çünkü ilk olayı işlemek istemeyebilirsiniz.

Başka bir örnek, bir sipariş tamamlandı olay birden fazla aboneye yayılmamış olmasından olabilir. Sipariş tamamlandı aynı etkinlik için yinelenen ileti olayları olsa bile, sipariş bilgilerini yalnızca bir kez, diğer sistemler güncelleştirilmesi önemlidir.

Bir tür olay başına kimlik her olay alıcı yalnızca bir kez işlenir zorlar mantıksal oluşturabilmesi uygundur.

Bazı ileti işleme kendiliğinden etkilidir. Bir sistem görüntüsü küçük resimler oluşturur, örneğin, kaç kez oluşturulan küçük resim hakkında bir ileti işlendikten önemli değil; küçük resimler oluşturulur ve her seferinde oldukları aynı sonuç elde edilir. Öte yandan, bir kredi kartından çekim ödeme ağ geçidi çağırma gibi işlemler ıdempotent hiç olmayabilir. Bu gibi durumlarda birden çok kez bir iletiyi işlemeyi beklediğiniz etkin olduğundan emin olmak gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

-   **İleti Teklik uygularken** <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Tümleştirme olay iletileri alanında yinelenenleri kaldırma

İleti olayları gönderilen ve farklı düzeylerde abonelik başına yalnızca bir kez işlenen emin olmak isteyebilirsiniz. Kullanmakta olduğunuz Mesajlaşma altyapısı tarafından sunulan bir yinelenenleri kaldırma özelliğini kullanan bir yoludur. Başka bir özel mantığı, hedef mikro uygulamaktır. Hem aktarım düzeyi ve uygulama düzeyinde doğrulamaları sahip, en iyi sonucu var.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>İleti olayları EventHandler düzeyinde alanında yinelenenleri kaldırma

Bir olay yalnızca bir kez herhangi bir alıcı tarafından işlendiğinden emin olmak için bir olay işleyicileri ileti olayları işlerken belirli mantığı uygulayarak yoludur. Örneğin, olan hizmetine uygulamada kullanılan yaklaşım de görebileceğiniz gibi [kaynak kodu UserCheckoutAcceptedIntegrationEventHandler sınıfın](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) bir UserCheckoutAcceptedIntegrationEvent aldığında Tümleştirme olay. (Bu durumda biz CreateOrderCommand eventMsg.RequestId komut işleyicisi için göndermeden önce bir tanımlayıcı olarak kullanarak, bir IdentifiedCommand ile sarmalamanız).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>RabbitMQ kullanırken alanında yinelenenleri kaldırma iletileri

Aralıklı ağ hataları meydana geldiğinde iletileri çoğaltılabilir ve ileti alıcısı şu yinelenen iletileri işlemeye hazır olmalıdır. Mümkünse, alıcılar, bunları yinelenenleri kaldırma ile açıkça işlenmesi daha iyidir bir kere etkili olacak şekilde iletileri işlemesi gerekir.

Şunlara göre [RabbitMQ belgeleri](https://www.rabbitmq.com/reliability.html#consumer), "ileti bir tüketici teslim ve ardından (tüketici bağlantı kesildi, örneğin önce onu onaylanır değil çünkü) yeniden kuyruğa durumunda RabbitMQ üzerinde redelivered bayrağı ayarlayacak Bu (aynı tüketici mı farklı bir için) yeniden iletildiğinde.

"Redelivered" bayrağı ayarlandıysa, ileti zaten işlenmiş çünkü alıcı, dikkate almalısınız. Ancak bu garanti edilmez. ağ sorunları nedeniyle ileti Aracısı, belki de sol sonra yapılacak hiçbir zaman alıcı ulaşmış olabilir. "Redelivered" bayrak ayarlanmazsa, diğer yandan, bu iletiyi birden çok kez gönderildiğini değil garanti edilir. Bu nedenle, yalnızca "redelivered" bayrak iletisinde ayarlanırsa iletiler veya işlem iletileri bir kere etkili olacak şekilde alanında yinelenenleri kaldırma alıcı gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Çatalı hizmetine NServiceBus (yazılım) kullanma** <br/>
    [*https://go.particular.net/eShopOnContainers*](https://go.particular.net/eShopOnContainers)

-   **Mesajlaşma typu EventDriven** <br/>
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard. Doğru dayanıklılığı yeniden düzenleme: Bağlantı değerlendirme** <br/>
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Kanal Yayımla-abone ol** <br/>
    [*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Sınırlanmış Bağlamlar arasında iletişim kurma** <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

-   **Son tutarlılık** <br/>
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Philip Brown. Tümleştirmeye yönelik stratejiler sınırlanmış bağlamlar** <br/>
    [*https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Chris Richardson. Toplamlar, olay kaynağını belirleme ve CQRS - bölüm 2 kullanarak işlem mikro Hizmetleri Geliştirme** <br/>
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Chris Richardson. Olay kaynağını belirleme düzeni** <br/>
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)

-   **Olay kaynağını belirleme ile tanışın** <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

-   **Olay Store veritabanı**. Resmi sitesi. <br/>
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen. Mikro hizmetlere yönelik olay odaklı veri yönetimi** <br/>
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   **CAP Teoremi** <br/>
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **CAP Teoremi nedir?** <br/>
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Veri tutarlılığı temel bilgileri** <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

-   **Saling rick. CAP Teoremi: "Her şey farklı Bulut ve Internet ile budur"** <br/>
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric Brewer. CAP on yıl: "Kurallar" nasıl değişti** <br/>
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Azure hizmet veri yolu. Aracılı Mesajlaşma: Yinelenen algılama**  <br/>
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Güvenilirlik Kılavuzu** (RabbitMQ belgeleri) * <br/>
    [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html#consumer)

-   **Azure hizmet veri yolu. Aracılı Mesajlaşma: Yinelenen algılama** <br/>
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Güvenilirlik Kılavuzu** (RabbitMQ belgeler) <br/>
    [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)

>[!div class="step-by-step"]
>[Önceki](rabbitmq-event-bus-development-test-environment.md)
>[İleri](test-aspnet-core-services-web-apps.md)
