---
title: Etki alanı olayları. Tasarım ve uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Toplamalar arasında iletişim kurmak için önemli bir kavram olan etki alanı olaylarının derinlemesine bir görünümünü alın.
ms.date: 10/08/2018
ms.openlocfilehash: 651d9cb98444c0729b97f523cc3d688f0f8d51d5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173383"
---
# <a name="domain-events-design-and-implementation"></a>Etki alanı olayları: tasarım ve uygulama

Etki alanınız içindeki değişikliklerin yan etkilerini açıkça uygulamak için etki alanı olaylarını kullanın. Diğer bir deyişle ve DDD terminolojisini kullanarak, birden çok toplama arasında yan etkileri açıkça uygulamak için etki alanı olaylarını kullanın. İsteğe bağlı olarak, veritabanı kilitlerinde daha iyi ölçeklenebilirlik ve daha az etki sağlamak için aynı etki alanı içindeki toplamalar arasında nihai tutarlılığı kullanın.

## <a name="what-is-a-domain-event"></a>Etki alanı olayı nedir?

Bir olay geçmişte gerçekleşen bir şeydir. Etki alanı olayı, etki alanında aynı etki alanının (işlem içi) diğer bölümlerinin farkında olmasını istediğiniz bir şeydir. Bildirilen parçalar genellikle olaylara bir şekilde tepki verir.

Etki alanı olaylarının önemli bir avantajı, yan etkilerin açık olarak ifade edilebilir.

Örneğin, yalnızca Entity Framework kullanıyorsanız ve bazı olayların yeniden eylemde olması gerekiyorsa, büyük olasılıkla olayın tetiklediği her şeyi kodlıyoruz. Bu nedenle kural, örtülü olarak, koda bağlı ve koda bakmamız gerekir. Bu durumda, kuralın burada uygulandığını fark edersiniz.

Diğer taraftan, etki alanı olaylarının kullanılması kavramı açık hale getirir, çünkü bir `DomainEvent` ve en az bir tane vardır `DomainEventHandler` .

Örneğin, eShopOnContainers uygulamasında, bir sipariş oluşturulduğunda Kullanıcı bir alıcı haline gelir ve bu nedenle `OrderStartedDomainEvent` , `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler` temel kavramda etkin hale getirilir.

Kısaca etki alanı etkinlikleri, etki alanı uzmanları tarafından sağlanan ubititous diline bağlı olarak etki alanı kurallarını hızlı bir şekilde ifade etmenize yardımcı olur. Etki alanı olayları aynı etki alanındaki sınıflar arasındaki kaygıları daha iyi bir şekilde ayırmayı de olanaklı hale getirir.

Bir veritabanı işlemi gibi, bir etki alanı olay ile ilgili tüm işlemlerin başarıyla bitmesini veya hiçbirinin bitmemesini sağlamak önemlidir.

Etki alanı olayları, önemli bir farklılık ile mesajlaşma stili olaylara benzerdir. AMQP kullanan gerçek mesajlaşma, Message Queuing, ileti aracıları veya hizmet veri yolu ile bir ileti her zaman zaman uyumsuz olarak gönderilir ve süreçler ve makineler arasında iletilir. Bu, birden çok sınırlanmış bağlamı, mikro hizmetleri ve hatta farklı uygulamaları tümleştirmek için yararlıdır. Bununla birlikte, etki alanı olayları ile, çalıştırmakta olduğunuz etki alanı işleminden bir olay yükseltmek istersiniz, ancak herhangi bir yan etkilerin aynı etki alanı içinde gerçekleşmesini istiyorsunuz.

Etki alanı olayları ve yan etkileri (daha sonra olay işleyicileri tarafından yönetilen eylemler) hemen hemen, işlem içi ve aynı etki alanı içinde gerçekleşmelidir. Bu nedenle, etki alanı olayları zaman uyumlu veya zaman uyumsuz olabilir. Ancak, tümleştirme olayları her zaman zaman uyumsuz olmalıdır.

## <a name="domain-events-versus-integration-events"></a>Etki alanı olayları ve tümleştirme olayları

Anlam, etki alanı ve tümleştirme olayları aynı şeydir: yalnızca gerçekleşen bir şey hakkında bildirimler. Ancak, bunların uygulamaları farklı olmalıdır. Etki alanı olayları yalnızca bir etki alanı olay dağıtıcısına gönderilen iletilerdir. Bu, bir IOC kapsayıcısına veya başka bir yönteme bağlı olarak bellek içi bir Mediator olarak uygulanabilir.

Diğer yandan, tümleştirme olaylarının amacı, diğer mikro hizmetler, sınırlı bağlamlar veya hatta dış uygulamalar gibi diğer alt sistemlere uygulanan işlem ve güncelleştirmeleri yaymaya yönelik olur. Bu nedenle, bu, yalnızca varlık başarıyla kalıcı olduğunda gerçekleşmelidir, aksi takdirde işlemin tamamı asla gerçekleşmeyebilir.

Daha önce bahsedildiği gibi, tümleştirme olayları birden çok mikro hizmet (diğer sınırlanmış bağlamlar) veya hatta dış sistem/uygulama arasındaki zaman uyumsuz iletişimi temel almalıdır.

Bu nedenle, olay veri yolu arabirimine, uzak hizmetler arasında işlemler arası ve dağıtılmış iletişime izin veren bir altyapı gerekir. Bu, ticari bir hizmet veri yoluna, kuyruklara, posta kutusu olarak kullanılan paylaşılan bir veritabanına veya diğer dağıtılmış ve ideal gönderim tabanlı mesajlaşma sistemine dayalı olabilir.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Aynı etki alanı içindeki birden çok toplama arasında yan etkileri tetiklemenin tercih edilen bir yolu olarak etki alanı olayları

Bir toplu örnekle ilişkili bir komut yürütülebilmeniz için bir veya daha fazla ek toplama üzerinde ek etki alanı kurallarının çalıştırılmasını gerektiriyorsa, bu yan etkileri, etki alanı olayları tarafından tetiklenecek şekilde tasarlamanız ve uygulamanız gerekir. Şekil 7-14 ' de gösterildiği gibi ve en önemli kullanım çalışmalarından biri olarak, aynı etki alanı modeli içindeki birden çok toplama arasında durum değişikliklerini yaymak için bir etki alanı olayının kullanılması gerekir.

![Bir alıcı toplamasına veri denetleyen bir etki alanı olayını gösteren diyagram.](./media/domain-events-design-implementation/domain-model-ordering-microservice.png)

**Şekil 7-14**. Aynı etki alanı içinde birden çok toplama arasında tutarlılığı zorlamak için etki alanı olayları

Şekil 7-14, toplamalar arasındaki tutarlılığı etki alanı olayları tarafından nasıl elde edildiğini gösterir. Kullanıcı bir sipariş başlattığında sıra toplaması bir `OrderStarted` etki alanı olayı gönderir. OrderStarted etki alanı olayı, alıcı toplama tarafından, kimlik mikro hizmetindeki özgün kullanıcı bilgilerine göre (CreateOrder komutunda belirtilen bilgiler ile) sıralama mikro hizmetinde bir alıcı nesnesi oluşturmak için işlenir.

Alternatif olarak, toplama kökünün toplamaların (alt varlıklar) üyeleri tarafından oluşturulan olaylar için abone olmasını sağlayabilirsiniz. Örneğin, her OrderItem alt varlığı, öğe fiyatı belirli bir tutardan yüksek olduğunda veya ürün öğesi miktarı çok yüksek olduğunda bir olay oluşturabilir. Toplam kök, daha sonra bu olayları alabilir ve küresel bir hesaplama veya toplama gerçekleştirebilir.

Bu olay tabanlı iletişimin doğrudan toplamalar içinde uygulanmadığını anlamak önemlidir; etki alanı olay işleyicilerini uygulamanız gerekir.

Etki alanı olaylarını işlemek bir uygulama konusudur. Etki alanı modeli katmanı yalnızca etki alanı mantığına odaklanmalıdır — bir etki alanı uzmanının, depolar gibi uygulama altyapısını ve depoları kullanarak yan etkisi Kalıcılık eylemlerini değil. Bu nedenle, uygulama katmanı düzeyi, etki alanı olayı tetiklendiğinde etki alanı olay işleyicilerinin eylemleri tetiklemedir.

Etki alanı olayları, herhangi bir sayıda uygulama eylemini tetiklemek için de kullanılabilir ve daha fazla önemli olan bu sayının gelecekte ayrılmış bir şekilde artması için açık olması gerekir. Örneğin, sipariş başlatıldığında, bu bilgileri diğer toplamalara yaymak veya bildirimler gibi uygulama eylemlerini yükseltmek için bir etki alanı olayı yayımlamak isteyebilirsiniz.

Anahtar noktası, bir etki alanı olayı gerçekleştiğinde yürütülecek eylemlerin açık sayısıdır. Sonuç olarak, etki alanı ve uygulamadaki eylemler ve kurallar büyüyecektir. Bir şeyin anlamı artar, ancak kodunuz "tutkalla" (diğer bir deyişle, ile belirli nesneler oluşturma) ile birlikte kullanıldığında, `new` çalışan ve test edilmiş kodu değiştirmeniz gerekir. Ayrıca, çalışma ve test edilen kodu değiştirmeniz gerekir.

Bu değişiklik yeni hatalara neden olabilir ve bu yaklaşım da [kesintisiz](https://en.wikipedia.org/wiki/SOLID) [açık/kapalı ilkesine](https://en.wikipedia.org/wiki/Open/closed_principle) karşı gider. Yalnızca, işlemleri düzenleyen özgün sınıf, [tek sorumluluk prensibi (SRP) Ile aynı](https://en.wikipedia.org/wiki/Single_responsibility_principle)şekilde büyütülür ve büyümeye devam edecektir.

Diğer taraftan, etki alanı olaylarını kullanıyorsanız, sorumlulukları Bu yaklaşımla ayırarak ayrıntılı ve ayrılmış bir uygulama oluşturabilirsiniz:

1. Bir komut (örneğin, CreateOrder) gönderin.
2. Komutu bir komut işleyicisinde alın.
   - Tek bir toplamanın işlemini yürütün.
   - Seçim Yan etkilere yönelik etki alanı olaylarını yükseltin (örneğin, OrderStartedDomainEvent).
3. Çoklu toplamalarda veya uygulama eylemlerinde açık sayıda yan efekt yürütecek olan etki alanı olaylarını (geçerli işlem dahilinde) işleyin. Örneğin:
   - Alıcı ve ödeme yöntemini doğrulayın veya oluşturun.
   - Olayları mikro hizmetlere yaymak veya alıcıya e-posta gönderme gibi dış eylemleri tetiklemek için olay veri yoluna ilgili bir tümleştirme olayı oluşturun ve gönderin.
   - Diğer yan etkileri işleyin.

Şekil 7-15 ' de gösterildiği gibi, aynı etki alanı olayından başlayarak, etki alanındaki diğer toplalarla ilgili birden çok eylemi veya tümleştirme olayları ve olay veri yolu ile bağlantı kurarak mikro hizmetler genelinde gerçekleştirmeniz gereken ek uygulama eylemlerini işleyebilirsiniz.

![Birkaç olay işleyicisine veri geçiren bir etki alanı olayını gösteren diyagram.](./media/domain-events-design-implementation/aggregate-domain-event-handlers.png)

**Şekil 7-15**. Etki alanı başına birden çok eylemi işleme

Uygulama katmanında aynı etki alanı olayı için birkaç işleyici olabilir. bir işleyici, toplamalar arasındaki tutarlılığı çözebileceği gibi, başka bir işleyici de bir tümleştirme olayı yayımlayabilir, böylece diğer mikro hizmetler onunla ilgili bir işlem yapabilir. Olay işleyicileri genellikle uygulama katmanında bulunur çünkü, mikro hizmet davranışı için depolar veya bir uygulama API 'SI gibi altyapı nesneleri kullanacaksınız. Bu anlamda, olay işleyicileri komut işleyicileriyle benzerdir, bu nedenle her ikisi de uygulama katmanının bir parçasıdır. Önemli fark, bir komutun yalnızca bir kez işlenmesi gerektiğidir. Her işleyici için farklı bir amaçla birden çok alıcı veya olay işleyicisi tarafından alınabileceğinden, bir etki alanı olayı sıfır veya *n* kez işlenebilir.

Etki alanı başına açık sayıda işleyicinin olması, mevcut kodu etkilemeden gereken sayıda etki alanı kuralı eklemenize olanak sağlar. Örneğin, aşağıdaki iş kuralının uygulanması çok sayıda olay işleyicisi (ya da yalnızca bir tane) eklemek kadar kolay olabilir:

> Mağazadaki bir müşteri tarafından satın alınan toplam miktar, herhangi bir sayıda sipariş için $6.000 değerini aşarsa, her yeni siparişe %10 kapalı indirimi uygular ve gelecekteki siparişler için bu indirimle ilgili bir e-posta ile müşteriyi bilgilendirir.

## <a name="implement-domain-events"></a>Etki alanı olaylarını uygulama

C# ' de, bir etki alanı olayı, aşağıdaki örnekte gösterildiği gibi, etki alanında gerçekleşdiklerle ilgili tüm bilgileri içeren bir veri tutan yapı veya sınıf olur.

```csharp
public class OrderStartedDomainEvent : INotification
{
    public string UserId { get; }
    public int CardTypeId { get; }
    public string CardNumber { get; }
    public string CardSecurityNumber { get; }
    public string CardHolderName { get; }
    public DateTime CardExpiration { get; }
    public Order Order { get; }

    public OrderStartedDomainEvent(Order order,
                                   int cardTypeId, string cardNumber,
                                   string cardSecurityNumber, string cardHolderName,
                                   DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

Bu aslında, OrderStarted olayı ile ilgili tüm verileri tutan bir sınıftır.

Etki alanının ubititous dili açısından, bir olay geçmişte gerçekleşen bir şey olduğundan, olayın sınıf adı OrderStartedDomainEvent veya OrderShippedDomainEvent gibi bir geçmiş-zaman hali fiili olarak temsil edilmelidir. Bu, etki alanı olayının eShopOnContainers 'daki sıralama mikro hizmetinde nasıl uygulandığı.

Daha önce belirtildiği gibi, olayların önemli bir özelliği, bir olayın geçmişte gerçekleşen bir şey olduğundan, değişmemelidir. Bu nedenle, sabit bir sınıf olmalıdır. Önceki kodda, özelliklerin salt okunurdur. Nesneyi güncelleştirmenin bir yolu yoktur, yalnızca oluşturma sırasında değerleri ayarlayabilirsiniz.

Burada, etki alanı olaylarının zaman uyumsuz olarak işlenebileceği, olay nesnelerinin serileştirilmesi ve serisini kaldırmada gerekli olan bir kuyruk kullanılarak, özelliklerin salt okuma yerine "özel küme" olması gerekir, bu nedenle seri hale getirici, kaldırma işlemleri sonrasında değerleri atayabilecektir. Etki alanı olay pub/Sub, MediatR kullanılarak eşzamanlı olarak uygulandığından, bu sıralama mikro hizmetindeki bir sorun değildir.

### <a name="raise-domain-events"></a>Etki alanı olaylarını Yükselt

Sonraki soru, bir etki alanı olayının ilgili olay işleyicilerine ulaşmasını sağlayacak şekilde nasıl tetiklemedir. Birden çok yaklaşımdan yararlanabilirsiniz.

UDI Dahan başlangıçta önerilir (örneğin, [etki alanı olayları](https://udidahan.com/2008/08/25/domain-events-take-2/)gibi bazı ilgili gönderilerde) olayları yönetmek ve yükseltmek için statik bir sınıf kullanın. Bu, DomainEvents adlı statik bir sınıfı içerebilir ve bu, etki alanı olaylarını, çağrıldığında, gibi bir sözdizimi kullanarak bir şekilde doğrudan tetikleyebilir `DomainEvents.Raise(Event myEvent)` . Jimmy Bogard, benzer bir yaklaşım öneren bir blog gönderisi ([etki alanınızı güçleyebilirsiniz: etki alanı olayları](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) yazdı.

Ancak, etki alanı olayları sınıfı statikse, Ayrıca, işleyiciler için hemen de dağıtım yapılır. Bu, test ve hata ayıklamayı daha zor hale getirir, çünkü yan etkileri olan olay işleyicileri olay oluşturulduktan hemen sonra yürütülür. Test ve hata ayıklama yaparken, yalnızca geçerli toplama sınıflarında neler olduğunu odaklanmak istersiniz; başka toplamalar veya uygulama mantığı ile ilgili yan etkileri için aniden başka olay işleyicilerine yeniden yönlendirilmek istemezsiniz. Sonraki bölümde açıklandığı gibi diğer yaklaşımların gelişmesinin nedeni budur.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Olayları yükseltme ve gönderme için ertelenmiş yaklaşım

Bir etki alanı olay işleyicisine hemen dağıtım yapmak yerine, etki alanı olaylarını bir koleksiyona eklemek ve ardından işlem *tamamlandıktan sonra* bu etki alanı olaylarını *doğrudan* veya *sağ* bir şekilde göndermek için daha iyi bir yaklaşım vardır. (Bu yaklaşım [daha Iyi bir etki alanı olayları deseninin](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)bulunduğu bu postadaki cemy Bogard tarafından açıklanmıştı.)

Aynı işlemin parçası olarak veya farklı işlemlerde yan etkileri dahil edilip edilmeyeceğini belirlediği için, işlem tamamlandıktan sonra etki alanı olaylarını hemen önce veya sağa göndermenizden karar vermek önemlidir. İkinci durumda, birden çok toplama arasında nihai tutarlılık ile uğraşmanız gerekir. Bu konu, sonraki bölümde ele alınmıştır.

Ertelenmiş yaklaşım eShopOnContainers 'ın kullandığı şeydir. İlk olarak, varlıklarınızda oluşan olayları, varlık başına bir koleksiyona veya olay listesine eklersiniz. Bu liste, varlık temel sınıfının aşağıdaki örneğinde gösterildiği gibi, temel varlık sınıfınızın bir parçası olan varlık nesnesinin bir parçası olmalıdır:

```csharp
public abstract class Entity
{
     //...
     private List<INotification> _domainEvents;
     public List<INotification> DomainEvents => _domainEvents;

     public void AddDomainEvent(INotification eventItem)
     {
         _domainEvents = _domainEvents ?? new List<INotification>();
         _domainEvents.Add(eventItem);
     }

     public void RemoveDomainEvent(INotification eventItem)
     {
         _domainEvents?.Remove(eventItem);
     }
     //... Additional code
}
```

Bir olayı yükseltmek istediğinizde, bunu yalnızca toplu kök varlığın herhangi bir yöntemindeki koddan olay koleksiyonuna eklersiniz.

Aşağıdaki kod, [eShopOnContainers 'Da Order Aggregate kökünün](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)bir parçası olarak bir örnek gösterir:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

AddDomainEvent yönteminin yaptığı tek şey listeye bir olay eklemediğine dikkat edin. Henüz hiçbir olay dağıtılamadı ve henüz hiçbir olay işleyicisi çağrılmamıştır.

İşlemleri veritabanına kaydederken, gerçekten üzerine olayları göndermek istersiniz. Entity Framework Core kullanıyorsanız, bu, aşağıdaki kodda olduğu gibi EF DbContext 'in SaveChanges yönteminde olduğu anlamına gelir:

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<bool> SaveEntitiesAsync(CancellationToken cancellationToken = default(CancellationToken))
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);

        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be committed
        var result = await base.SaveChangesAsync();
    }
}
```

Bu kodla, varlık olaylarını ilgili olay işleyicileriyle birlikte ileolursunuz.

Genel sonuç olarak, bir etki alanı olayının (bellekte bir listeye basit bir ekleme) bir olay işleyicisine gönderdikten sonra bir etki alanı olayının dağıtımını ayırmıştır. Ayrıca, kullanmakta olduğunuz Dispatcher türüne bağlı olarak olayları zaman uyumlu veya zaman uyumsuz olarak dağıtabilirsiniz.

İşlem sınırlarının burada önemli bir şekilde oynatılmakta olduğunu unutmayın. İş biriminiz ve işlem, birden fazla toplama yayılabildiği zaman (EF Core ve ilişkisel bir veritabanı kullanırken olduğu gibi), bu da iyi çalışabilir. Ancak işlem toplamalara yayılamaz, örneğin Azure CosmosDB gibi bir NoSQL veritabanı kullanırken, tutarlılığı sağlamak için ek adımlar uygulamanız gerekir. Bu, kalıcılık Ignorance 'in evrensel olmadığı başka bir nedendir; Bu, kullandığınız depolama sistemine bağlıdır.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Toplamalar genelinde tek bir işlem, toplamalar arasında nihai tutarlılığa karşı

Toplamalar genelinde tek bir işlem yapılıp yapılmayacağını ve bu toplamalar genelinde nihai tutarlılığa bağlı olarak, bir controversıal. Eric Evans ve Vaughn Verone gibi birçok DDD yazarı, bir işlemin = bir toplama olduğunu ve bu nedenle toplamalar arasında nihai tutarlılığın sonunda olduğunu belirten kuralı kabul ediyorum. Örneğin, kitabın *etki alanı odaklı tasarımında*, Eric Evans şöyle diyor:

> Toplamaları kapsayan herhangi bir kuralın her zaman güncel olması beklenmez. Olay işleme, toplu işlem veya diğer güncelleştirme mekanizmaları aracılığıyla, diğer bağımlılıklar belirli bir süre içinde çözülebilir. (sayfa 128)

Vaughn versuz, aşağıdaki etkili toplama tasarımında şunu söylemiştir [. Bölüm II: toplamalar birlikte çalışır hale getirme](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

> Bu nedenle, bir toplu örnek üzerinde bir komut yürütülerek bir veya daha fazla toplamada ek iş kurallarının yürütülmesi gerekir, nihai tutarlılık kullanın \[ ... \] Bir DDD modelinde nihai tutarlılığı desteklemeye yönelik pratik bir yöntem vardır. Toplama yöntemi bir veya daha fazla zaman uyumsuz aboneye teslim edilen zaman bir etki alanı olayını yayımlar.

Bu kalationale, birçok toplama veya varlığı kapsayan işlemler yerine hassas işlemleri benimseme tabanlıdır. İkinci durumda, veritabanı kilitlerinin sayısının yüksek ölçeklenebilirlik gereksinimlerine sahip büyük ölçekli uygulamalarda önemli olacağı fikir. Yüksek düzeyde ölçeklenebilir uygulamaların birden çok toplama arasında anlık işlem tutarlılığı olmaması, nihai tutarlılık kavramını kabul etmenize yardımcı olur. Atomik değişiklikler genellikle işletme tarafından gerekli değildir ve belirli işlemler için atomik işlemler gerekip gerekmediğini söylemek için etki alanı uzmanlarının sorumluluğunda olması gerekir. Bir işlemin her zaman birden çok toplama arasında atomik bir işleme ihtiyacı varsa, toplamanız büyük veya doğru şekilde tasarlanmamalıdır.

Ancak, Jimmy Bogard gibi diğer geliştiriciler ve mimarlar, tek bir işlemi birkaç toplama arasında dağıtmayı, ancak yalnızca bu ek toplamalar aynı orijinal komutun yan etkileri ile ilgili olduğunda geçerlidir. Örneğin, [daha Iyi bir etki alanı olayları](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)düzeninde Bogard şöyle diyor:

> Genellikle, bir etki alanı olayının yan etkilerinin aynı mantıksal işlem içinde gerçekleşmesini istiyorum, ancak etki alanı olayını yükseltmek için aynı kapsamda olması gerekmez \[ ... \] İşleminizi işlemeden hemen önce, olaylarımızı ilgili işleyicilerle gönderiyoruz.

İlk işlemi gerçekleştirmeden *önce* etki alanı olaylarını dağıtırsanız, bu olayların yan etkilerinin aynı işleme dahil edilmesini istiyor olabilirsiniz. Örneğin, EF DbContext SaveChanges yöntemi başarısız olursa işlem, ilgili etki alanı olay işleyicileri tarafından uygulanan herhangi bir yan efekt işleminin sonucu da dahil olmak üzere tüm değişiklikleri geri alınacaktır. Bunun nedeni, DbContext yaşam kapsamının varsayılan olarak "kapsamlıdır" olarak tanımlanmış olmasından kaynaklanır. Bu nedenle, DbContext nesnesi aynı kapsam veya nesne grafiğinde oluşturulan birden çok depo nesnesi arasında paylaşılır. Bu saatle çakışan Web API 'SI veya MVC uygulamaları geliştirirken HttpRequest kapsamıyla birlikte.

Aslında, her iki yaklaşım (tek atomik işlem ve nihai tutarlılık) doğru olabilir. Bu, etki alanı veya iş gereksinimlerinize ve etki alanı uzmanlarına sizi nasıl söylediğinize bağlıdır. Ayrıca, hizmetin ne kadar ölçeklenebilir olduğuna da bağlıdır (daha ayrıntılı işlemler veritabanı kilitleri açısından daha az etkiye sahiptir). Ve bu, son tutarlılık, toplamalar genelinde olası tutarsızlıkları tespit etmek için daha karmaşık kod gerektirdiğinden ve telafi etme eylemlerini uygulama ihtiyacı olduğundan kodunuzda ne kadar yatırım yapmaya ihtiyacınız olduğuna bağlıdır. Değişiklikleri orijinal toplamalarda yürütmeniz ve daha sonra olaylar dağıtıldığınızda, bir sorun varsa ve olay işleyicileri yan etkileri işleiyorsa, toplamalar arasında tutarsızlıklara sahip olursunuz.

Telafi eylemlerine izin veren bir yol, etki alanı olaylarını, özgün işlemin bir parçası olacak şekilde ek veritabanı tablolarında depolarlar. Daha sonra, tutarsızlıkları algılayan ve maaş eylemlerini çalıştıran bir toplu işlem, toplamların listesini toplamaların geçerli durumuyla karşılaştırarak gerçekleştirir. Telafi eylemleri, iş kullanıcısı ve etki alanı uzmanları ile tartışmak dahil olmak üzere, sizin tarafınızdan derin analiz gerektiren bir karmaşık konunun parçasıdır.

Herhangi bir durumda, ihtiyacınız olan yaklaşımı seçebilirsiniz. Ancak ilk ertelenmiş yaklaşım — işlemeden önce olayları oluştururken tek bir işlem kullanmanız gerekir. EF Core ve ilişkisel bir veritabanı kullanırken en basit yaklaşım olur. Birçok iş durumunda uygulanması ve geçerli olması daha kolaydır. Ayrıca, eShopOnContainers 'daki sıralama mikro hizmetinde kullanılan yaklaşımdır.

Ancak bu olayları ilgili olay işleyicileriyle nasıl gerçekten gönderir? `_mediator`Önceki örnekte gördüğünüz nesne nedir? Olaylar ile olay işleyicileri arasında eşleme yapmak için kullandığınız teknikler ve yapıtlar ile aynı olması gerekir.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Etki alanı olay dağıtıcısı: olaylardan olay işleyicilerine eşleme

Olayları dağıtmak veya yayımlamak için, her ilgili işleyicinin bu olaya göre onu alabilmesi ve yan etkileri işleyebilmesi için olayı yayımlayabilecek bir tür yapıya ihtiyacınız vardır.

Bir yaklaşım, büyük olasılıkla bellek içi olaylara karşı bir hizmet veri yolu temel alınarak gerçek bir mesajlaşma sistemidir veya hatta bir olay veri yolundan biridir. Ancak, bu olayları yalnızca aynı işlem içinde (diğer bir deyişle, aynı etki alanı ve uygulama katmanında) işlemeniz gerektiğinden, ilk durumda, gerçek mesajlaşma, etki alanı olaylarını işlemek için fazla sonlandırılmalıdır.

Olayları birden çok olay işleyicisine eşlemenin bir diğer yolu da bir IOC kapsayıcısına kayıt türlerini kullanarak olayların nereye gönderdiğini dinamik olarak çıkarılabilmenizi sağlar. Diğer bir deyişle, belirli bir olayı hangi olay işleyicilerinin almak gerektiğini bilmeniz gerekir. Şekil 7-16, bu yaklaşım için basitleştirilmiş bir yaklaşım gösterir.

![Uygun işleyicilere olay gönderen bir etki alanı olay dağıtıcısı gösteren diyagram.](./media/domain-events-design-implementation/domain-event-dispatcher.png)

**Şekil 7-16**. IOC kullanarak etki alanı olay dağıtıcısı

Bu yaklaşımı kendiniz uygulamak için tüm sıhhi tesisat ve yapıtları oluşturabilirsiniz. Ancak, kapsamakta olan IFC kapsayıcınızı kullanan [mediaTR](https://github.com/jbogard/MediatR) gibi kullanılabilir kitaplıkları da kullanabilirsiniz. Bu nedenle, önceden tanımlanmış arabirimleri ve Mediator nesnesinin yayımlama/dağıtma yöntemlerini doğrudan kullanabilirsiniz.

Kodda, ilk olarak olay işleyicisi türlerini IOC kapsayıcısına kaydetmeniz gerekir, [Eshoponcontainers sıralama mikro hizmeti](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)' nde aşağıdaki örnekte gösterildiği gibi:

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement IAsyncNotificationHandler<>)
        // in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
                                       .GetTypeInfo().Assembly)
                                         .AsClosedTypesOf(typeof(IAsyncNotificationHandler<>));
        // Other registrations ...
    }
}
```

Kod önce işleyicileri (typeof (ValidateOrAddBuyerAggregateWhenXxxx) kullanarak etki alanı olay işleyicilerini içeren derlemeyi tanımlar, ancak derlemeyi bulmak için başka herhangi bir olay işleyicisini seçmiş olabilirsiniz). Tüm olay işleyicileri ıasyncnotificationhandler arabirimini kullandığından, kod yalnızca bu türleri arar ve tüm olay işleyicilerini kaydeder.

### <a name="how-to-subscribe-to-domain-events"></a>Etki alanı olaylarına abone olma

MediatR kullandığınızda, her olay işleyicisi aşağıdaki kodda görebileceğiniz gibi ınocertificate parametresinin genel parametresinde sağlanmış bir olay türü kullanmalıdır:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Abonelik olarak kabul edilebilir olay ve olay işleyicisi arasındaki ilişkiye bağlı olarak, MediatR yapıtı her olay için tüm olay işleyicilerini bulabilir ve bu olay işleyicilerinin her birini tetikleyebilir.

### <a name="how-to-handle-domain-events"></a>Etki alanı olaylarını işleme

Son olarak, olay işleyicisi genellikle gerekli ek toplamaları elde etmek ve yan etki alanı mantığını yürütmek için altyapı depoları kullanan uygulama katmanı kodunu uygular. [EShopOnContainers 'daki aşağıdaki etki alanı olay işleyicisi kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)bir uygulama örneği gösterir.

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
                   : INotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;

    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // ...Parameter validations...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ? orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;

        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }

        buyer.VerifyOrAddPaymentMethod(cardTypeId,
                                       $"Payment Method on {DateTime.UtcNow}",
                                       orderStartedEvent.CardNumber,
                                       orderStartedEvent.CardSecurityNumber,
                                       orderStartedEvent.CardHolderName,
                                       orderStartedEvent.CardExpiration,
                                       orderStartedEvent.Order.Id);

        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer)
                                                                      : _buyerRepository.Add(buyer);

        await _buyerRepository.UnitOfWork
                .SaveEntitiesAsync();

        // Logging code using buyerUpdated info, etc.
    }
}
```

Altyapı kalıcılığı katmanının sonraki bölümünde açıklandığı gibi, önceki etki alanı olay işleyicisi kodu, uygulama katmanı kodu olarak kabul edilir. Olay işleyicileri de diğer altyapı bileşenlerini kullanabilir.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Etki alanı olayları, mikro hizmet sınırlarının dışında yayımlanacak tümleştirme olayları oluşturabilir

Son olarak, bazı durumlarda olayları birden fazla mikro hizmette yaymaya isteyebileceğiniz bir bahsetmek önemlidir. Bu yayma bir tümleştirme olayıdır ve belirli bir etki alanı olay işleyicisinden bir olay veri yolundan yayımlanabilir.

## <a name="conclusions-on-domain-events"></a>Etki alanı olaylarında ekibinizle

Belirtildiği gibi, etki alanınız içindeki değişikliklerin yan etkilerini açıkça uygulamak için etki alanı olaylarını kullanın. DDD terminolojisini kullanmak için etki alanı olaylarını kullanarak bir veya birden çok toplama arasında yan etkileri açıkça uygulayın. Ayrıca, daha iyi ölçeklenebilirlik ve veritabanı kilitleri üzerinde daha az etki sağlamak için aynı etki alanı içindeki toplamalar arasında nihai tutarlılığı kullanın.

Başvuru uygulaması, tek bir işlem içinde etki alanı olaylarını, toplamalar arasında zaman uyumlu olarak yaymak için [mediaTR](https://github.com/jbogard/MediatR) kullanır. Ancak, son tutarlılığı kullanarak etki alanı olaylarını zaman uyumsuz olarak yaymak için [Kbbitmq](https://www.rabbitmq.com/) veya [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) gibi bazı AMQP uygulamasını da kullanabilirsiniz, ancak Yukarıda bahsedildiği gibi, bir başarısızlık durumunda telafi eylemlerine yönelik ihtiyacı göz önünde bulundurmanız gerekir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Greg başak. Etki alanı olayı nedir?** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Jan Stenberg. Etki alanı olayları ve nihai tutarlılık** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard. Daha iyi bir etki alanı olayları deseninin** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn versuz. Etkili toplu tasarım bölümü II: toplamalar birlikte çalışır hale getirme** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard. Etki alanınızı güçlendirerek: etki alanı etkinlikleri** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Üzerinde bulunan Truong. Etki alanı olayları deseninin örneği** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **UDI Dahan. Tamamen kapsüllenmiş etki alanı modelleri oluşturma** \
  <https://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **UDI Dahan. Etki alanı olayları – 2. alın** \
  <https://udidahan.com/2008/08/25/domain-events-take-2/>

- **UDI Dahan. Etki alanı olayları-sallanmayı** \
  <https://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan kroni. Etki alanı olaylarını yayımlamayın, döndürün!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de La Torre. Etki alanı olayları ile DDD ve mikro hizmet mimarilerinde tümleştirme olayları** \
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Önceki](client-side-validation.md) 
> [Sonraki](infrastructure-persistence-layer-design.md)
