---
title: Olaylara abone olma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Olaylara abone olma
keywords: Docker, mikro, ASP.NET, kapsayıcı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 279dd4ea2ffb36e13a22f366ece145174918b759
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="subscribing-to-events"></a>Olaylara abone olma

Olay veri yolu kullanarak ilk mikro almak istediği olaylara abone olma adımdır. Alıcı mikro yapılmalıdır.

Aşağıdaki basit kod her alıcı mikro hizmet başlatılırken uygulamak gereken gösterir (diğer bir deyişle, `Startup` sınıfı) şekilde bu olayları, ihtiyaçlarını kaydeder. Bu durumda, `basket.api` mikro hizmet abone olmak için gereksinim duyduğu `ProductPriceChangedIntegrationEvent` ve `OrderStartedIntegrationEvent` iletileri. 

Örneğin, abone olduğunda `ProductPriceChangedIntegrationEvent` Sepeti mikro hizmet herhangi farkında yapan olay Ürün Fiyat değiştirir ve bu ürünün kullanıcının sepetteki ise değişiklik hakkında kullanıcıyı uyarmak etmenizi sağlar.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

Bu kod çalıştıktan sonra abone mikro hizmet RabbitMQ kanallardan dinleme. Her ileti türü ProductPriceChangedIntegrationEvent geldiğinde kodu kendisine geçirilen ve olay işleyen olay işleyiciyi çağırır.

## <a name="publishing-events-through-the-event-bus"></a>Olay veri yolu üzerinden olay yayımlama

Son olarak, aşağıdaki örneğe benzer bir kod tümleştirme olaylarla (kaynak mikro) iletiyi gönderenin yayımlar. (Bu kararlılık dikkate almaz basitleştirilmiş bir örnek niteliğindedir.) Birden çok mikro, verileri veya kaynak mikro hizmet hareketleri uyguladıktan sonra genellikle sağ arasında bir olay dağıtılmalıdır her benzer bir kod uygulamak.

İlk olarak, aşağıdaki kod olduğu gibi denetleyicisi Oluşturucusu en (RabbitMQ üzerinde temel veya bir service bus tabanlı) olay veri yolu uygulama nesnesi eklenemeyebilir:

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

Ardından, onu denetleyicinizin yöntemleri, gibi UpdateProduct yöntemi kullanın:

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

Bu durumda, basit bir CRUD mikro hizmet kaynak mikro hizmet olduğuna göre bu kodu bir Web API denetleyicisi sağ yerleştirilir. 
 
CQRS yaklaşımlar kullanırken gibi daha gelişmiş mikro onu içinde uygulanabilir `CommandHandler` sınıfı, içinde `Handle()` yöntemi. 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Kararlılık ve dayanıklılık olay yoluna yayımlarken tasarlama

Dağıtılmış ileti aracılığıyla tümleştirme olaylarını yayımladığınızda, olay veri yolu gibi sistem, otomatik olarak özgün veritabanını güncelleştirme ve olay yayımlama sorununuz. Ürün Fiyat değiştirilir ve bir ProductPriceChangedIntegrationEvent ileti yayımlar örneği için daha önce gösterilen Basitleştirilmiş örnekte kodu verileri veritabanına kaydeder. Başlangıçta, bu iki işlemleri otomatik olarak gerçekleştirilmesi temel görünebilir. İlgili bir dağıtılmış işlem kullanıyorsanız gibi eski sistemlerinde olduğu gibi ancak, veritabanı ve iletiyi, Aracısı [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), bu tarafındanaçıklanannedenleriyleönerilmez[CAP Teoremi](https://www.quora.com/What-Is-CAP-Theorem-1).

Temel olarak, mikro ölçeklenebilir ve yüksek oranda kullanılabilir sistemleri oluşturmak için kullanın. CAP Teoremi bir veritabanının (veya kendi modelini sahip bir mikro) oluşturamaz diyor biraz basitleştirme, sürekli olarak kullanılabilir, kesinlikle tutarlı *ve* dayanıklı herhangi bir bölümü için. Bu üç özellik ikilisi seçmeniz gerekir.

Mikro tabanlı mimari, kullanılabilirlik ve dayanıklılık seçmeniz gerekir ve, güçlü tutarlılık devamlı müşterilerine göre ayarlayabilirler. Uyguladığınızda, yaptığınız gibi bu nedenle, çoğu modern mikro hizmet tabanlı uygulamalarda genellikle mesajlaşmada, dağıtılmış işlemler kullanmak istediğiniz değil [dağıtılmış işlemler](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) Windows Dağıtılmış İşlem üzerinde dayalı Düzenleyicisi (DTC) ile [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).

İlk sorun ve kendi örnek edelim. Veritabanı güncelleştirildikten sonra hizmetin çökmesi durumunda (Bu durumda, kodla satırından sonra sağ \_bağlamı. SaveChangesAsync()), ancak tümleştirme olay yayımlanmadan önce genel sistem tutarsız hale gelebilir. Bu iş ilgilendiğiniz belirli iş işleme bağlı olarak önemli olabilir.

Mimari bölümünde daha önce belirtildiği gibi bu sorunla ilgili çeşitli yaklaşımlar sahip olabilir:

-   Tam kullanarak [olay kaynak Hizmeti'nden düzeni](https://msdn.microsoft.com/library/dn589792.aspx).

-   Kullanarak [işlem oturum araştırma](https://www.scoop.it/t/sql-server-transaction-log-mining).

-   Kullanarak [Giden kutusu düzeni](http://gistlabs.com/2014/05/the-outbox/). (Yerel işlem genişletme) tümleştirme olayları depolamak üzere bir işlem tablo budur.

Bu senaryo için tam olay kaynak Hizmeti'nden (ES) deseni en iyi yaklaşımlardan birini değilse kullanmaktır *en* iyi. Ancak, çok sayıda uygulama senaryolarında, tam bir ES sistemi uygulayabilirsiniz olmayabilir. ES geçerli durumu verilerinin depolanması yerine, işlemsel veritabanında yalnızca etki alanı olayları depolamak anlamına gelir. Yalnızca etki alanı olayları depolamak geçmişini sisteminizin kullanılabilir olması ve geçmişteki herhangi bir anda, sistem durumunu belirlemek mümkün gibi çok yarar olabilir. Ancak, tam bir ES sistemi uygulama sisteminizi çoğunu rearchitect gerektirir ve diğer birçok karmaşıklık ve gereksinimleri sunar. Örneğin, özellikle olay kaynak için gibi yapılan bir veritabanını kullanmak istersiniz [olay deposuna](https://geteventstore.com/), veya Azure Cosmos DB, MongoDB, Cassandra, CouchDB veya RavenDB gibi belge yönelimli veritabanı. Olay kaynak Hizmeti'nden ile bilginiz sürece ES Bu sorun, ancak en kolay çözüm için harika bir yaklaşımdır.

İşlem günlüğü başlangıçta araştırma kullanma seçeneği çok saydam arar. Ancak, bu yaklaşımı kullanmak için SQL Server işlem günlüğü gibi RDBMS işlem günlüğü için eşleştirilmek üzere mikro hizmet vardır. Bu arzu büyük olasılıkla değil. Başka bir dezavantajı, işlem günlüğüne alt düzey güncelleştirmeleri, üst düzey tümleştirme olayları ile aynı düzeyde olmayabilir olmasıdır. Ters mühendislik işlemi varsa, bu işlem günlüğü işlemler zor olabilir.

Dengeli bir yaklaşım, bir işlemsel veritabanı tablosu ve Basitleştirilmiş ES düzeni karışımıdır. "Tümleştirme olayları tabloya yaparsanız özgün olayda belirlenen olay yayımlamaya hazır" gibi bir durumda kullanabilirsiniz. Ardından olay veri yoluna olayı yayımlamak deneyin. Yayımla olayı eylemi başarılı olursa, başka bir işlem kaynak hizmetini ve durumu "hazır'dan olayı yayımlamak" "zaten yayınlanmış olaya." taşıma

Yayımla olay eylem başarısız olay veri yolu, veri hala kaynak mikro hizmet içinde tutarsız olmaz — yine "hazır olarak olayı yayımlamak" işaretlendiğinden ve Hizmetleri rest göre sonunda tutarlı hale gelecektir. Her zaman işlemler veya tümleştirme olaylarını durumunu denetleme arka plan işleri sahip olabilir. İş "olay yayımlamaya hazır" durumda bir olay bulursa, bu olay olay veri yoluna yeniden yayımlamayı deneyebilirsiniz.

Bu yaklaşımda, yalnızca her kaynak mikro hizmet tümleştirme olaylarını ve diğer mikro veya dış sistemleri ile iletişim kurmak istediğiniz olayları kalıcı olduğunu dikkat edin. Buna karşılık, tam bir ES sistemde, tüm etki alanı olayları de depolar.

Bu nedenle, bu dengeli bir Basitleştirilmiş ES sistemi yaklaşımdır. Bunların geçerli durumu ile tümleştirme olaylarının bir listesi gerekir ("yayımlamak için"yayımlanan karşı"hazır"). Ancak bu durumu tümleştirme olaylarını uygulamak yeterlidir. Ve tam bir ES sisteminde olduğu gibi bu yaklaşım, işlemsel veritabanında olayları olarak tüm etki alanı verilerini depolamak gerekmez.

İlişkisel veritabanı zaten kullanıyorsanız, tümleştirme olayları depolamak için bir işlem tablo kullanabilirsiniz. Uygulamanızdaki kararlılık elde etmek için yerel hareketlerini temel alarak iki adımlı bir işlem kullanın. Temel olarak, etki alanı varlıklarınızı sahip olduğu aynı veritabanında bir IntegrationEvent tablo sahip. Bu tablo dahil böylece kararlılık elde etmek için bir sigorta tümleştirme olaylarını etki alanı verilerinizi yürütülmekte olan aynı işlemleri kalıcı olarak çalışır.

Adım adım işlemi aşağıdaki gibi gider: uygulama yerel veritabanı işlemi başlar. Etki alanı varlıklarınızı durumunu güncelleştirir ve bir olay tümleştirme olay tabloya ekler. Son olarak, işlem kaydeder. İstenen kararlılık alın.

Olayları yayımlama adımları uygularken bu seçeneğiniz vardır:

-   Sağa hareket uyguladıktan sonra tümleştirme olay yayımlayın ve başka bir yerel işlem yayımlanmakta olarak tablo olayları işaretlemek için kullanın. Sonra uzak mikro sorunları durumunda tümleştirme olaylarını izlemek için yalnızca bir yapı tabloyu kullanın ve saklı tümleştirme olaylara dayanarak telafi izin eylemleri gerçekleştirin.

-   Tablo, kuyruk bir tür olarak kullanın. Ayrı uygulama iş parçacığı veya işlem tümleştirme olay tablo sorguları, olayları olay veri yoluna yayımlar ve olayları yayımlanmış olarak işaretlemek için yerel bir işlem kullanır.

Şekil 8-22 Bu yaklaşımlardan biri için Mimari gösterilmektedir.

![](./media/image23.png)

**Şekil 8-22**. Olayları olay yoluna yayımlarken Atom oranı

Şekil 8-22'de gösterilen yaklaşım denetleme ve yayımlanan tümleştirme olaylarını başarısını onaylayan sorumlu olduğu bir ek çalışan mikro hizmet eksik. Başarısız olması durumunda, bu ek denetleyicisi çalışan mikro hizmet tablosundan olayları okumak ve bunları yeniden yayımlayın.

İkinci yaklaşımı hakkında: sırası olarak olay günlüğüne tabloyu kullanın ve her zaman bir çalışan mikro hizmet iletileri yayımlamak için kullanın. Bu durumda, işlem Şekil 8-23'te gibi gösterilir. Tek kaynak olayları yayımlarken tablodur ve bu ek mikro hizmet gösterir.

![](./media/image24.png)

**Şekil 8-23**. Olayları olay veri yoluna çalışan mikro hizmet ile yayımlarken Atom oranı

Kolaylık olması için eShopOnContainers örnek olay bus ilk yaklaşımda (hiçbir ek işlemler veya denetleyicisi mikro) kullanır. Ancak, eShopOnContainers tüm olası hata durumları işlenmemesinin. Buluta dağıtılan gerçek bir uygulamada denetleyip mantığı yeniden sorunları sonuçta ortaya çıkar ve uygulamanız gereken olgu çekirdeğin gerekir. Tek bir olay veri yolu yayımlarken, olayları kaynağı olarak bu tabloyu varsa sırası olarak tabloyu kullanarak ilk yaklaşım daha etkili olabilir.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Olay Veriyolu aracılığıyla tümleştirme olaylarını yayımlarken kararlılık uygulama

Aşağıdaki kod, birden çok DbContext nesnelerini içeren tek bir işlem nasıl oluşturabileceğinizi gösterir — güncelleştirilmekte özgün veri ile ilgili bir içerik ve IntegrationEventLog tabloya ilgili ikinci bağlamı.

Aşağıdaki örnek kod işlemde veritabanı bağlantılarını kodun çalıştığı zaman herhangi bir sorun varsa esnek olmaz unutmayın. Veritabanlarını sunucular arasında taşıma Azure SQL DB gibi bulut tabanlı sistemlerde gerçekleşebilir. Birden çok bağlamlarında dayanıklı işlemleri uygulamak için bkz: [dayanıklı Entity Framework Çekirdek SQL bağlantıları uygulama](#implementing_resilient_EFCore_SQL_conns) bu kılavuzda daha sonra bölüm.

Daha anlaşılır olması için aşağıdaki örnek kod tek bir parça tüm işlem gösterir. Ancak, eShopOnContainers uygulama gerçekte bulunanad ve sürdürmek daha kolay şekilde bu mantığı birden çok sınıflara bölme.

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

ProductPriceChangedIntegrationEvent tümleştirme olay oluşturulduktan sonra özgün etki alanı işlemi (güncelleştirme katalog öğesi) depolar işlem Kalıcılık olayın olay günlüğüne tabloda de içerir. Bu tek bir işlem yapar ve, her zaman gönderilen olay iletileri olup olmadığını denetlemek kullanamazsınız.

Olay günlüğü tablosu, aynı veritabanında yerel bir işlem kullanarak özgün veritabanı işlemi ile otomatik olarak güncelleştirilir. İşlemleri başarısız olursa, bir özel durum ve işlem bu nedenle etki alanı işlemleri ve gönderilen olay iletileri arasında tutarlılığı koruma herhangi bir Tamamlanan işlem geri alınır.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Aboneliklerden ileti alma: alıcı mikro olay işleyicileri

Olay aboneliği mantığı ek olarak (örneğin, bir geri çağırma yöntemi) tümleştirme olay işleyicileri için iç kod uygulamanız gerekir. Belirli bir türde olay iletileri nereye alınan ve işlenen belirlediğiniz olay işleyicisidir.

Olay işleyici ilk olay yolundan olay örneğini alır. Ardından yayılıyor ve alıcı mikro hizmet durumunda bir değişiklik olarak olayı kalıcı tümleştirme olay, ilgili işlenmek üzere bileşen bulur. Örneğin, ProductPriceChanged olay Kataloğu mikro kaynaklanıyorsa Sepeti mikro ele alınır ve aşağıdaki kodda gösterildiği gibi bu alıcı Sepeti mikro hizmet olarak iyi durumda değiştirir.

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

Ürün Sepeti örnekleri hiçbirinde var olup olmadığını doğrulamak olay işleyicisini gerekir. Ayrıca, her ilgili Sepeti satır maddesi için madde fiyatı güncelleştirir. Son olarak, Şekil 8-24'te gösterildiği gibi fiyat değişikliği hakkında kullanıcıya görüntülenecek bir uyarı oluşturur.

![](./media/image25.png)

**Şekil 8-24**. Bir öğe fiyat değişikliği bir sepetteki tümleştirme olaylar tarafından iletilen olarak görüntüleme

## <a name="idempotency-in-update-message-events"></a>Güncelleştirme iletisini olayları benzersizlik

Bir önemli güncelleştirme iletisi olayları denenmek üzere ileti iletişimde herhangi bir noktada başarısız olmasına neden yönüdür. Aksi halde bir arka plan görevi zaten, bir yarış durumu oluşturma yayımlanmış bir olay yayımlamayı deneyebilirsiniz. Idempotent veya bir yinelenen algılayabilir emin olmak için yeterli bilgi sağladıkları güncelleştirmelerin emin olmak için atmak ve geri tek bir yanıt gönderir.

Daha önce belirtildiği gibi sonuç değiştirmeden bir işlem birden çok kez gerçekleştirilebilir benzersizlik anlamına gelir. İleti bir ortamda, birden çok kez alıcı mikro hizmet için sonucu değiştirmeden teslim edilebilir olayları iletişim kurarken bir olay ıdempotent ise gibi. Bu olay yapısı nedeniyle gerekli olabilir veya yol nedeniyle sistem olayını işler. İleti benzersizlik Mesajlaşma deposu kullanan herhangi bir uygulama, yalnızca olay bus deseni uygulayan uygulamaları önemlidir.

Yalnızca bu verileri tabloda değilse, bir tabloya veri ekleyen bir SQL deyimi bir ıdempotent işlem örnektir. SQL deyimini ekleyin çalıştırdığınız kaç kez önemli değildir; Sonuç aynı olacaktır — tablo verileri içerir. Bu gibi benzersizlik iletilerin potansiyel olarak gönderilebilir, iletileri ile ilgilenirken gerekirse ve bu nedenle işlenen defadan de olabilir. Örneğin, bir gönderici tam olarak aynı iletiyi birden çok kez göndermek yeniden deneme mantığı neden olursa, ıdempotent olduğundan emin olmak gerekir.

Tasarım ıdempotent iletileri mümkündür. Örneğin, bildiren bir olay oluşturabilirsiniz "Ürün Fiyat kümesine \$25" yerine "eklemek \$Ürün Fiyat 5." İlk kez herhangi bir sayıda güvenli bir şekilde işlem gerçekleştirilemedi ve sonucu aynı olacaktır. Bu ikinci bir ileti için doğru değil. Ancak, hatta ilk durumda, ilk olay sistem da daha yeni bir fiyat değişiklik olayı gönderilen ve yeni fiyat üzerine çünkü işlem istemeyebilirsiniz.

Başka bir örnek, birden çok aboneye yayılmasını sipariş tamamlanan olay olabilir. Aynı sırada tamamlandı olayı için yinelenen ileti olayları olsa bile sipariş bilgilerini yalnızca bir kez, diğer sistemlere güncelleştirilmesi önemlidir.

Her olay alıcı yalnızca bir kez işlenir zorlar mantığı oluşturabilmesi için olay başına kimlik çeşit sağlamak kullanışlıdır.

Bazı ileti kendiliğinden ıdempotent işlemesidir. Bir sistem görüntüsü küçük resimleri oluşturursa, örneğin, ileti hakkında ve oluşturulan küçük işlenir kaç kez önemli değil; sonucu küçük resimler oluşturulur ve her zaman aynıdır. ' dir. Diğer taraftan, kredi kartı kaydedilecek ödeme ağ geçidi çağırma gibi işlemler ıdempotent hiç olmayabilir. Bu durumlarda, birden çok kez ileti işlenirken beklediğiniz etkin olduğundan emin olmak gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

-   **İleti benzersizlik uygularken** (Bu sayfadaki alt başlık) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>Yinelenenleri tümleştirme olay iletileri

Message olayları gönderilen ve farklı düzeylerde abonelik başına yalnızca bir kez işlenir emin olabilirsiniz. Kullanmakta olduğunuz Mesajlaşma altyapısı tarafından sunulan bir yinelenenleri kaldırma özelliğini kullanan bir yoludur. Başka bir özel mantık, hedef mikro uygulamaktır. Hem aktarım düzeyinde ve uygulama düzeyinde doğrulamaları sahip en iyi sonucu istenir.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Message olayları EventHandler düzeyinde yinelenenleri

Bir olay herhangi bir alıcı tarafından yalnızca bir kez işlenir emin olmak için bir olay işleyicileri ileti olayları işlerken belirli mantığı uygulayarak yoludur. Örneğin, olan eShopOnContainers uygulamada kullanılan yaklaşımı nde gördüğünüz [kaynak kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) CreateOrderCommand komutu aldığında OrdersController sınıfının. (Bu durumda değil ileti tabanlı komutu bir HTTP isteği komutu kullanırız ancak ileti tabanlı komut ıdempotent yapmanız mantığı benzer.)

### <a name="deduplicating-messages-when-using-rabbitmq"></a>RabbitMQ kullanırken yinelenenleri iletileri

Aralıklı ağ hataları oluştuğunda iletileri çoğaltılabilir ve ileti alıcı bu yinelenen iletileri işlemek hazır olması gerekir. Mümkünse, alıcılar iletileri bunları yinelenenleri kaldırma ile açıkça işleme daha iyi bir ıdempotent şekilde işlemelidir.

Göre [RabbitMQ belgelerine](https://www.rabbitmq.com/reliability.html#consumer), "bir ileti bir tüketici teslim ve (tüketici bağlantı kesildi, örneğin önce onu onaylanan değil çünkü) daha sonra yeniden kuyruğa alınması durumunda RabbitMQ üzerinde redelivered bayrağı ayarlayacak Bunu (', aynı tüketici ya da farklı bir olup olmadığını) yeniden teslim edildiğinde.

"Redelivered" bayrağı ayarlarsanız, ileti zaten işlenmiş çünkü alıcı, dikkate almanız gerekir. Ancak bu garanti edilmez; ağ sorunları nedeniyle ileti Aracısı belki de sol sonra ileti hiçbir zaman alıcı ulaştı. "Redelivered" bayrağı ayarlanmamış olduğundan, diğer yandan, bu iletiyi birden çok kez gönderildiğini değil sağlanır. Bu nedenle, yalnızca ileti "redelivered" bayrağı ayarlarsanız iletileri veya işlem iletileri ıdempotent şekilde yararlanmanın alıcı gerekir.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Çatallanmış eShopOnContainers NServiceBus (belirli yazılım) kullanma**
    [*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)

-   **Olay tabanlı Mesajlaşma**
    [*http://soapatterns.org/design\_desen/olay\_güdümlü\_Mesajlaşma*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard. Esnekliği doğru yeniden düzenleme: Bağlantı değerlendirme**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Kanal yayımlama-abone olma**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Sınırlanmış bağlamları arasında iletişim**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Nihai tutarlılık**
    [*https://en.wikipedia.org/wiki/Eventual\_tutarlılık*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Elmas kahverengi. Tümleştirme stratejileri bağlamları sınırlanmış**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Chris Uludağ. Toplamalar, olay kaynak belirleme ve CQRS - bölüm 2 kullanarak işlem mikro geliştirme**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Chris Uludağ. Olay Sourcing düzeni**
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)

-   **Olay kaynak Hizmeti'nden Tanıtımı**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)

-   **Olay deposu veritabanı**. Resmi sitesi.
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Can Nommensen. Mikro için olay denetimli veri yönetimi**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   **CAP Teoremi**
    [*https://en.wikipedia.org/wiki/CAP\_Teoremi*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **CAP Teoremi nedir?**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Veri tutarlılığı Primer**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Saling rick. CAP Teoremi: "Her şeyi farklı Bulut ve Internet olmasının"**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric Brewer. CAP üzeri on iki yıllık: "Kurallar" nasıl değiştiğini**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Dış (DTC) işlemlere katılan** (MSMQ) [  *https://msdn.microsoft.com/library/ms978430.aspx \#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Azure hizmet veri yolu. Aracılı Mesajlaşma: Yinelenen algılama**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Güvenilirlik Kılavuzu** (RabbitMQ belge) [  *https://www.rabbitmq.com/reliability.html \#tüketici*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[Önceki] (rabbitmq-event-bus-development-test-environment.md) [sonraki] (test-aspnet-core-services-web-apps.md)
