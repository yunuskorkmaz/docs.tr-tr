---
title: Etki alanı olayları. tasarım ve uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Agregalar arasında iletişim kurmak için önemli bir kavram olan etki alanı olaylarının ayrıntılı bir görünümünü alın.
ms.date: 10/08/2018
ms.openlocfilehash: e03abba66945a6434f6a81eaa9f50d53998f346c
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988723"
---
# <a name="domain-events-design-and-implementation"></a>Etki alanı olayları: tasarım ve uygulama

Etki alanınızdaki değişikliklerin yan etkilerini açıkça uygulamak için etki alanı olaylarını kullanın. Başka bir deyişle, ve DDD terminolojisi kullanarak, birden çok agrega arasında yan etkileri açıkça uygulamak için etki alanı olaylarını kullanın. İsteğe bağlı olarak, veritabanı kilitlerinde daha iyi ölçeklenebilirlik ve daha az etki için, aynı etki alanındaki agregalar arasında nihai tutarlılık kullanın.

## <a name="what-is-a-domain-event"></a>Etki alanı olayı nedir?

Bir olay geçmişte olan bir şeydir. Etki alanı olayı, aynı etki alanının diğer bölümlerinin (işlem içi) farkında olmasını istediğiniz etki alanında gerçekleşen bir şeydir. Bildirilen parçalar genellikle olaylara bir şekilde tepki verir.

Etki alanı olaylarının önemli bir yararı, yan etkilerin açıkça ifade edilebilmektedir.

Örneğin, varlık framework'u kullanıyorsanız ve bazı olaya tepki vermek zorundaysanız, büyük olasılıkla olayı tetikleyen şeye yakın bir şekilde ne gerekiyorsa kodlarsınız. Yani kural, dolaylı olarak, kodla birleşir ve kodun içine bakmanız gerekir, umarım, kuralın orada uygulandığını fark etmek için.

Öte yandan, etki alanı olaylarının kullanılması kavramı açık `DomainEvent` hale getirir, çünkü en az bir `DomainEventHandler` tane söz konusudur.

Örneğin, eShopOnContainers uygulamasında, bir sipariş oluşturulduğunda, kullanıcı bir alıcı `OrderStartedDomainEvent` olur, bu nedenle `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`bir yükseltilir ve ele alınır , böylece temel kavramı açıktır.

Kısacası, etki alanı olayları, etki alanı uzmanları tarafından sağlanan her yerde bulunan dilde dayalı etki alanı kurallarını açıkça ifade etmenize yardımcı olur. Etki alanı olayları da aynı etki alanındaki sınıflar arasında endişelerin daha iyi ayrılmasını sağlar.

Bir veritabanı hareketi gibi, bir etki alanı olayıyla ilgili tüm işlemlerin başarılı bir şekilde sona ermesini veya hiçbirinin bunu yapmamasını sağlamak önemlidir.

Etki alanı olayları, önemli bir farkla mesajlaşma tarzı olaylara benzer. Gerçek mesajlaşma, ileti sıraya alma, ileti aracıları veya AMQP kullanan bir servis veri birimi yle, bir ileti her zaman eşzamanlı olarak gönderilir ve süreçler ve makineler arasında iletilir. Bu, birden çok Bağlı Bağlamları, mikro hizmetleri ve hatta farklı uygulamaları tümleştirmek için yararlıdır. Ancak, etki alanı olayları ile, şu anda çalıştırmakta olduğunuz etki alanı işleminden bir olay yükseltmek istiyorsunuz, ancak aynı etki alanı içinde herhangi bir yan efektin oluşmasını istiyorsunuz.

Etki alanı olayları ve bunların yan etkileri (olay işleyicileri tarafından yönetilen daha sonra tetiklenen eylemler) hemen, genellikle süreç içinde ve aynı etki alanı içinde meydana gelmelidir. Böylece, etki alanı olayları senkron veya eşzamanlı olabilir. Ancak tümleştirme olayları her zaman eşzamanlı olmalıdır.

## <a name="domain-events-versus-integration-events"></a>Etki alanı olayları ve tümleştirme olayları

Semantically, etki alanı ve tümleştirme olayları aynı şey: sadece oldu bir şey hakkında bildirimler. Ancak, bunların uygulanması farklı olmalıdır. Etki alanı olayları, ioC kapsayıcısına veya başka bir yönteme dayalı bellek içi aracı olarak uygulanabilen bir etki alanı olay göndericisine itilen iletilerdir.

Diğer taraftan, tümleştirme olaylarının amacı, diğer mikro hizmetler, Sınırlı Bağlamlar ve hatta dış uygulamalar olsun, taahhüt edilen işlemleri ve güncelleştirmeleri ek alt sistemlere yaymaktır. Bu nedenle, bunlar yalnızca varlık başarıyla devam ederse meydana gelmelidir, aksi takdirde tüm işlem hiç olmamış gibi olur.

Daha önce de belirtildiği gibi, tümleştirme olayları birden çok mikro hizmet (diğer Sınırlı Bağlamlar) ve hatta dış sistemler/uygulamalar arasındaki eşzamanlı iletişimi temel almalıdır.

Bu nedenle, olay veri birimi arabiriminin, olası uzak hizmetler arasında süreçler arası ve dağıtılmış iletişimsağlayan bazı altyapıya ihtiyacı vardır. Ticari hizmet veri yolunda, kuyruklara, posta kutusu olarak kullanılan paylaşılan bir veritabanına veya dağıtılmış ve ideal olarak itilen herhangi bir ileti sistemine dayalı olabilir.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Etki alanı olayları, aynı etki alanı içinde birden fazla agrega arasında yan etkileri tetiklemek için tercih edilen bir yol olarak

Bir toplu örnekle ilgili bir komutun yürütülmesi, bir veya daha fazla ek toplamda çalıştırılması için ek etki alanı kuralları gerektiriyorsa, etki alanı olayları tarafından tetiklenecek bu yan efektleri tasarlamalı ve uygulamalısınız. Şekil 7-14'te gösterildiği gibi ve en önemli kullanım örneklerinden biri olarak, aynı etki alanı modelinde durum değişikliklerini birden çok agrega da yaymak için bir etki alanı olayı kullanılmalıdır.

![Alıcı toplamına verileri denetleyen bir etki alanı olayını gösteren diyagram.](./media/domain-events-design-implementation/domain-model-ordering-microservice.png)

**Şekil 7-14**. Aynı etki alanı içinde birden fazla agrega arasında tutarlılık zorlamak için etki alanı olayları

Şekil 7-14, etki alanı olayları tarafından agregalar arasındaki tutarlılığın nasıl sağlandığını gösterir. Kullanıcı bir sipariş başlattığında, Sipariş Toplamı `OrderStarted` bir etki alanı olayı gönderir. OrderStarted etki alanı olayı, kimlik microservice'in orijinal kullanıcı bilgilerine (CreateOrder komutunda sağlanan bilgilerle) dayalı olarak, sipariş mikrohizmetinde bir Alıcı nesnesi oluşturmak için Alıcı Toplamı tarafından işlenir.

Alternatif olarak, toplam kökün, onun toplamlarının (alt varlıklar) üyeleri tarafından yükseltilen olaylar için abone olması gerekir. Örneğin, her OrderItem alt varlık, madde fiyatı belirli bir tutardan yüksek olduğunda veya ürün madde miktarı çok yüksekolduğunda bir olay yükseltebilir. Daha sonra toplu kök bu olayları alabilir ve genel bir hesaplama veya toplama gerçekleştirebilir.

Bu olay tabanlı iletişimin doğrudan toplamlar içinde uygulanmadığını anlamak önemlidir; etki alanı olay işleyicileri uygulamak gerekir.

Etki alanı olayları işleme bir uygulama endişe. Etki alanı modeli katmanı yalnızca etki alanı mantığına odaklanmalıdır— etki alanı uzmanının anlayacağı şeyler, depoları kullanarak işleyiciler ve yan etki kalıcılığı eylemleri gibi uygulama altyapısı değil. Bu nedenle, uygulama katmanı düzeyi, etki alanı olayı yükseltildiğinde eylemleri tetikleyen etki alanı olay işleyicileri olması gereken yerdir.

Etki alanı olayları da uygulama eylemleri herhangi bir sayı tetiklemek için kullanılabilir ve daha da önemlisi, ayrılmış bir şekilde gelecekte bu sayıyı artırmak için açık olmalıdır. Örneğin, sipariş başlatıldığında, bu bilgileri diğer toplamlara yaymak ve hatta bildirimler gibi uygulama eylemlerini yükseltmek için bir etki alanı olayı yayımlamak isteyebilirsiniz.

Önemli nokta, bir etki alanı olayı oluştuğunda yürütülecek açık eylem sayısıdır. Sonunda, etki alanı ve uygulama eylemleri ve kuralları büyüyecek. Bir şey olduğunda yan etki eylemlerinin karmaşıklığı veya sayısı büyür, ancak kodunuz "tutkal" ile birleştiğinde (diğer bir şekilde, belirli nesneler `new`oluşturma), yeni bir eylem eklemek için gereken her zaman da çalışma ve test kodu değiştirmeniz gerekir.

Bu değişiklik yeni hatalara neden olabilir ve bu yaklaşım [SOLID'in](https://en.wikipedia.org/wiki/SOLID) [Açık/Kapalı ilkesine](https://en.wikipedia.org/wiki/Open/closed_principle) de aykırıdır. Sadece bu değil, operasyonları düzenleyen orijinal sınıf büyümek ve tek [sorumluluk ilkesi (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)aykırı büyüyecek.

Diğer taraftan, etki alanı olayları kullanıyorsanız, bu yaklaşımı kullanarak sorumlulukları ayırarak ince taneli ve ayrılmış bir uygulama oluşturabilirsiniz:

1. Komut gönderin (örneğin, CreateOrder).
2. Komut işleyicisi komutu alın.
   - Tek bir toplamın işlemini yürütün.
   - (İsteğe bağlı) Yan etkiler için etki alanı olaylarını yükseltin (örneğin, OrderStartedDomainEvent).
3. Birden çok toplama veya uygulama eyleminde açık sayıda yan etki yürütecek etki alanı olaylarını (geçerli işlem içinde) işleyebilir. Örneğin:
   - Doğrulayın veya alıcı ve ödeme yöntemi oluşturun.
   - Durumları mikro hizmetler arasında yaymak veya alıcıya e-posta göndermek gibi dış eylemleri tetiklemek için ilgili bir tümleştirme olayı oluşturun ve olay veri tonuna gönderin.
   - Diğer yan etkileri ele alın.

Şekil 7-15'te gösterildiği gibi, aynı etki alanı olayından başlayarak, etki alanındaki diğer toplamlarla ilgili birden çok eylemi veya tümleştirme olayları ve olay veri yolunu birbirine bağlayan mikro hizmetler de gerçekleştirmeniz gereken ek uygulama eylemlerini işleyebilirsiniz.

![Birkaç olay işleyicisine veri aktaran bir etki alanı olayını gösteren diyagram.](./media/domain-events-design-implementation/aggregate-domain-event-handlers.png)

**Şekil 7-15**. Etki alanı başına birden çok eylemi işleme

Uygulama Katmanı'nda aynı etki alanı olayı için birkaç işleyici olabilir, bir işleyici agregalar arasındaki tutarlılığı çözebilir ve başka bir işleyici bir tümleştirme olayı yayımlayabilir, böylece diğer mikro hizmetler onunla bir şeyler yapabilir. Mikro hizmetin davranışı için depolar veya uygulama API'si gibi altyapı nesnelerini kullanacağınız için olay işleyicileri genellikle uygulama katmanındadır. Bu anlamda, olay işleyicileri komut işleyicileri benzer, bu nedenle her ikisi de uygulama katmanının bir parçasıdır. Önemli fark, bir komutun yalnızca bir kez işlenmesidir. Etki alanı olayı, her işleyici için farklı bir amaca sahip birden çok alıcı veya olay işleyicisi tarafından alınabileceğinden, sıfır veya *n* kez işlenebilir.

Etki alanı olayı başına açık sayıda işleyiciolması, geçerli kodu etkilemeden gerektiği kadar etki alanı kuralı eklemenize olanak tanır. Örneğin, aşağıdaki iş kuralını uygulamak birkaç olay işleyicisi eklemek kadar kolay olabilir (hatta sadece bir tane):

> Mağazada bir müşteri tarafından satın alınan toplam tutar, herhangi bir sayıda sipariş te 6.000 TL'yi aştığında, her yeni siparişe %10 indirim uygulayın ve müşteriye gelecekteki siparişler için bu indirim hakkında bir e-posta ile bildirin.

## <a name="implement-domain-events"></a>Etki alanı etkinliklerini uygulama

C#'da, etki alanı olayı, aşağıdaki örnekte gösterildiği gibi, etki alanında olanlarla ilgili tüm bilgileri içeren, dto gibi basit bir veri tutma yapısı veya sınıfıdır:

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

Bu aslında OrderStarted olayıyla ilgili tüm verileri tutan bir sınıftır.

Etki alanının her yerde bulunan dili açısından, bir olay geçmişte olan bir şey olduğundan, olayın sınıf adı OrderStartedDomainEvent veya OrderShippedDomainEvent gibi geçmiş zamanlı bir fiil olarak temsil edilmelidir. Etki alanı olayı, eShopOnContainers'da sipariş mikrohizmetinde bu şekilde uygulanır.

Daha önce de belirtildiği gibi, olayların önemli bir özelliği, bir olay geçmişte olan bir şey olduğundan, bu değişmemesi gerektiğidir. Bu nedenle, değişmez bir sınıf olmalıdır. Önceki kodda özelliklerin salt okunur olduğunu görebilirsiniz. Nesneyi güncelleştirmenin bir yolu yoktur, değerleri yalnızca oluşturduğunuzda ayarlayabilirsiniz.

Burada vurgulamak önemlidir, eğer etki alanı olayları olay nesnelerini serihale ve deserialize gerektiren bir sıra kullanarak eş zamanlı olarak ele alınacaksa, özelliklerin salt okunur yerine "özel küme" olması gerekir, böylece deserializer değerleri dequeuing üzerine atayabilir. Etki alanı olay pub / alt MediatR kullanılarak eşzamanlı olarak uygulandığından, bu Sipariş microservice bir sorun değildir.

### <a name="raise-domain-events"></a>Etki alanı olaylarını yükseltme

Bir sonraki soru, ilgili olay işleyicilerine ulaşması için bir etki alanı olayının nasıl yükseltilen olduğudur. Birden çok yaklaşım kullanabilirsiniz.

Udi Dahan başlangıçta olayları yönetmek ve yükseltmek için statik bir sınıf kullanarak (örneğin, [Etki Alanı Etkinlikleri – Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)gibi ilgili birkaç gönderide) önerilmiştir. Bu, etki alanı olaylarını çağrıldığında hemen yükseltecek Etki Alanı Etkinlikleri `DomainEvents.Raise(Event myEvent)`adlı statik bir sınıf içerebilir, '' gibi sözdizimi kullanarak. Jimmy Bogard benzer bir yaklaşım önerir bir blog yazısı yazdı ([Etki alanı güçlendirilmesi: Etki Alanı Olaylar)](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/).

Ancak, etki alanı olayları sınıfı statik olduğunda, işleyicilere de hemen gönderir. Bu, yan efekt mantığına sahip olay işleyicileri olay yükseltildikten hemen sonra yürütüldolduğundan, sınama ve hata ayıklamayı zorlaştırır. Test ederken ve hata ayıklarken, şu anki toplam sınıflarda neler olup bittiğine odaklanmak istersiniz; aniden diğer agregalar veya uygulama mantığı ile ilgili yan etkileri için diğer olay işleyicileri yönlendirilmeye istemiyorum. Bu nedenle, bir sonraki bölümde açıklandığı gibi diğer yaklaşımlar da gelişmiştir.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Olayları yükseltmek ve göndermek için ertelenmiş yaklaşım

Bir etki alanı olay işleyicisine hemen göndermek yerine, daha iyi bir yaklaşım etki alanı olaylarını bir koleksiyona eklemek ve bu etki alanı olaylarını işlemi gerçekleştirmeden *hemen önce* veya *hemen* *sonra* göndermektir (EF'deki SaveChanges'ta olduğu gibi). (Bu yaklaşım Jimmy Bogard tarafından bu yazı [daha iyi bir etki alanı olayları desen](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)açıklanmıştır.)

Etki alanı olaylarını işlemi gerçekleştirmeden hemen önce veya hemen önce mi gönderdiğinizönemli, çünkü yan etkileri aynı işlemin bir parçası olarak mı yoksa farklı hareketlere mi dahil edeceğiniz belirlenir. İkinci durumda, birden çok agrega arasında nihai tutarlılık ile uğraşmak gerekir. Bu konu sonraki bölümde ele alınmıştır.

Ertelenmiş yaklaşım eShopOnContainers ne kullanır. İlk olarak, varlıklarınızda meydana gelen olayları bir koleksiyona veya varlık başına olaylar listesine eklersiniz. Bu liste, Varlık taban sınıfının aşağıdaki örneğinde gösterildiği gibi, varlık nesnesinin veya daha iyisi, taban varlık sınıfının bir parçası olmalıdır:

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

Bir olayı yükseltmek istediğinizde, toplu kök varlığın herhangi bir yönteminde koddan olay koleksiyonuna eklemeniz önemlidir.

Aşağıdaki kod, [eShopOnContainers sipariş toplam kök](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)parçası, bir örnek gösterir:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

AddDomainEvent yönteminin yaptığı tek şeyin listeye bir olay eklemek olduğuna dikkat edin. Henüz olay gönderilmedi ve henüz hiçbir olay işleyicisi çağrılmadı.

Aslında, hareketi veritabanına işlediğinde olayları daha sonra göndermek istiyorsunuz. Varlık Framework Core kullanıyorsanız, bu, EF DbContext'ınızın SaveChanges yönteminde aşağıdaki kodda olduğu gibi anlamına gelir:

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

Bu kodla, varlık olaylarını ilgili olay işleyicilerine gönderirsiniz.

Genel sonuç, bir etki alanı olayının yükseltilmesini (bellekteki bir listeye basit bir ekleme) bir olay işleyicisine göndermekten ayırmanızdır. Buna ek olarak, ne tür bir sevk irsaliyesi kullandığınıza bağlı olarak, olayları eşzamanlı veya eşzamanlı olarak gönderebilirsiniz.

İşlemsel sınırların burada önemli bir oyuna girdiğini unutmayın. Çalışma ve işlem biriminiz birden fazla toplama (EF Core ve ilişkisel veritabanı kullanırken olduğu gibi) yayılabilirse, bu iyi çalışabilir. Ancak, Azure CosmosDB gibi bir NoSQL veritabanı kullanıyorsanız gibi işlem toplamlara yayılamıyorsa, tutarlılık elde etmek için ek adımlar uygulamanız gerekir. Bu, sebat cehalet evrensel değildir başka bir nedenidir; kullandığınız depolama sistemine bağlıdır.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Agregalar arasında tek işlem ve agregalar arasında nihai tutarlılık

Bu toplamlar arasında nihai tutarlılığa güvenmek yerine agregalar arasında tek bir işlem gerçekleştirip gerçekleştirmeyeceği sorusu tartışmalıdır. Eric Evans ve Vaughn Vernon gibi birçok DDD yazarları bir işlem = bir toplam ve bu nedenle toplamlar arasında nihai tutarlılık için tartışmak kuralı savunucusu. Örneğin, kitabında *Etki Alanı Odaklı Tasarım*, Eric Evans bu diyor:

> Toplamları kapsayan herhangi bir kuralın her zaman güncel olması beklenmez. Olay işleme, toplu iş işleme veya diğer güncelleştirme mekanizmaları sayesinde, diğer bağımlılıklar belirli bir süre içinde çözülebilir. (sayfa 128)

Vaughn Vernon Etkili [Agrega Tasarım aşağıdaki diyor. Bölüm II: Agregaların Birlikte Çalışmasını Sağlamak](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

> Bu nedenle, bir komutu toplu bir örnekte yürütmek, ek iş kurallarının bir \[veya daha fazla toplamda yürütülmesini gerektiriyorsa, nihai tutarlılığı kullanın ... \] Bir DDD modelinde nihai tutarlılığı desteklemenin pratik bir yolu vardır. Toplu yöntem, bir veya daha fazla eşzamanlı aboneye zamanında teslim edilen bir etki alanı olayı yayımlar.

Bu mantık, birçok agrega veya varlığı kapsayan işlemler yerine ince taneli hareketleri kucaklamaya dayanır. Fikir ikinci durumda, veritabanı kilitleri sayısı yüksek ölçeklenebilirlik gereksinimleri ile büyük ölçekli uygulamalarda önemli olacaktır. Yüksek ölçeklenebilir uygulamaların birden fazla agrega arasında anlık işlem tutarlılığına sahip olmaması gerektiği gerçeğini benimsemek, nihai tutarlılık kavramını kabul etmeye yardımcı olur. Atomik değişiklikler genellikle işletme tarafından gerekli değildir ve her durumda belirli işlemlerin atomik işlemlere gerek olup olmadığını söylemek etki alanı uzmanlarının sorumluluğundadır. Bir işlemin her zaman birden çok agrega arasında atomik bir işlem eihtiyacı varsa, agreganızın daha büyük mü yoksa doğru şekilde tasarlanmaması mı gerektiğini sorabilirsiniz.

Ancak, Jimmy Bogard gibi diğer geliştiriciler ve mimarlar birkaç agrega arasında tek bir işlem yayılan tamam-ama sadece bu ek toplamlar aynı orijinal komut için yan etkileri ile ilgili olduğunda. Örneğin, [daha iyi bir etki alanı olayları desen,](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)Bogard bu diyor:

> Genellikle, bir etki alanı olayının yan etkilerinin aynı mantıksal işlem içinde gerçekleşmesini istiyorum, ancak etki \[alanı olayını yükseltme kapsamında olması gerekmez ... \] İşlemimizi gerçekleştirmeden hemen önce, etkinliklerimizi ilgili amirlerine göndeririz.

İlk işlemi gerçekleştirmeden *hemen önce* etki alanı olaylarını gönderirseniz, bunun nedeni bu olayların yan etkilerinin aynı işleme dahil olmasını istemenizdir. Örneğin, EF DbContext SaveChanges yöntemi başarısız olursa, hareket, ilgili etki alanı olay işleyicileri tarafından uygulanan herhangi bir yan etki işlemlerinin sonucu da dahil olmak üzere tüm değişiklikleri geri alır. Bunun nedeni, DbContext yaşam kapsamının varsayılan olarak "kapsamlı" olarak tanımlanmasıdır. Bu nedenle, DbContext nesnesi, aynı kapsam veya nesne grafiği içinde anlık olarak bulunan birden çok depo nesnesi arasında paylaşılır. Bu, Web API veya MVC uygulamaları geliştirirken HttpRequest kapsamıyla çakışıyor.

Aslında, her iki yaklaşım (tek atomik işlem ve nihai tutarlılık) doğru olabilir. Bu gerçekten etki alanı veya iş gereksinimleri ve etki alanı uzmanları size ne söyler bağlıdır. Ayrıca, hizmetin ne kadar ölçeklenebilir olmasına da bağlıdır (daha ayrıntılı işlemlerveritabanı kilitlerine göre daha az etkiye sahiptir). Ve bu, agregalar arasında olası tutarsızlıkları ve telafi edici eylemleri uygulama gereksinimini algılamak için daha karmaşık kod gerektirdiğinden, kodunuza ne kadar yatırım yapmak istediğinize bağlıdır. Orijinal toplamda değişiklikler yaparsanız ve daha sonra, olaylar gönderilirken, bir sorun varsa ve olay işleyicileri yan etkilerini gerçekleştiremiyorsa, toplamlar arasında tutarsızlıklar olacağını düşünün.

Telafi edici eylemlere izin vermenin bir yolu, etki alanı olaylarını özgün işlemin bir parçası olabilmesi için ek veritabanı tablolarında depolamak olacaktır. Daha sonra, tutarsızlıkları algılayan ve olayların listesini agregaların geçerli durumuyla karşılaştırarak telafi edici eylemler çalıştıran bir toplu işlem olabilir. Telafi edici eylemler, iş kullanıcısı ve etki alanı uzmanlarıyla tartışmayı da içeren, sizin tarafınızdan derin analizler gerektiren karmaşık bir konunun parçasıdır.

Her durumda, ihtiyacınız olan yaklaşımı seçebilirsiniz. Ancak, işlemeden önce olayları yükselten ilk ertelenmiş yaklaşım, böylece tek bir işlem kullanırsanız, EF Core ve ilişkisel bir veritabanı nı kullanırken en basit yaklaşımdır. Birçok iş durumunda uygulanması daha kolaydır ve geçerlidir. Aynı zamanda eShopOnContainers sipariş microservice kullanılan bir yaklaşımdır.

Ama bu olayları kendi etkinlik işleyicilerine nasıl gönderirsiniz? Önceki örnekte `_mediator` gördüğünüz nesne nedir? Olaylar ve olay işleyicileri arasında harita kullanmak teknikleri ve eserler ile ilgili.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Etki alanı olay gönderici: olaylardan olay işleyicilerine eşleme

Olayları gönderebildiğinizde veya yayımlayabildiğinizde, ilgili her işleyicinin olayı alabilmeleri ve bu olaya göre yan efektleri işleyebilmeleri için olayı yayımlayacak bir tür yapıya ihtiyacınız vardır.

Bir yaklaşım gerçek bir mesajlaşma sistemi ya da muhtemelen bellek olayların aksine bir servis verime dayalı bir olay otobüsü vardır. Ancak, ilk durumda, gerçek ileti etki alanı olaylarını işlemek için aşırı yayılacak, çünkü bu olayları aynı işlem içinde işlemeniz gerekir (diğer bir süre aynı etki alanı ve uygulama katmanı içinde).

Olayları birden çok olay işleyicisi ile eşlemenin başka bir yolu da, olayları nereye göndereceğinizi dinamik olarak çıkarabilmeniz için bir IoC kapsayıcısındaki tür kaydını kullanmaktır. Başka bir deyişle, belirli bir olayı elde etmek için hangi olay işleyicilerinin neye ihtiyacı olduğunu bilmeniz gerekir. Şekil 7-16 bu yaklaşım için basitleştirilmiş bir yaklaşım gösterir.

![Olayları uygun işleyicilere gönderen etki alanı olay göndericisini gösteren diyagram.](./media/domain-events-design-implementation/domain-event-dispatcher.png)

**Şekil 7-16.** IoC kullanarak etki alanı olay gönderici

Tüm sıhhi tesisat ve eserler kendiniz bu yaklaşımı uygulamak için inşa edebilirsiniz. Ancak, IoC kapsayıcınızı kapakların altında kullanan [MediatR](https://github.com/jbogard/MediatR) gibi kullanılabilir kitaplıkları da kullanabilirsiniz. Bu nedenle, önceden tanımlanmış arabirimleri ve aracı nesnenin yayımlama/gönderme yöntemlerini doğrudan kullanabilirsiniz.

Kod olarak, öncelikle ioC kapsayıcınızda olay işleyicisi türlerini kaydetmeniz gerekir, aşağıdaki örnekte gösterildiği gibi [eShopOnContainers Sipariş mikroservice:](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)

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

Kod ilk olarak işleyicilerden herhangi birini tutan derlemeyi (typeof(ValidateOrAddBuyerAggregateXxxx kullanarak) bularak etki alanı olay işleyicilerini içeren derlemeyi tanımlar, ancak derlemeyi bulmak için başka bir olay işleyicisi seçmiş olabilirsiniz. Tüm olay işleyicileri IAsyncNotificationHandler arabirimini uyguladığından, kod yalnızca bu türleri arar ve tüm olay işleyicilerini kaydeder.

### <a name="how-to-subscribe-to-domain-events"></a>Etki alanı etkinliklerine nasıl abone olunur?

MediatR'ı kullandığınızda, her olay işleyicisi aşağıdaki kodda görebileceğiniz gibi INotificationHandler arabiriminin genel parametresinde sağlanan bir olay türü kullanmalıdır:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Etkinlik ve olay işleyicisi arasındaki ve abonelik olarak kabul edilebilen ilişkiye bağlı olarak, MediatR artifakı her olay için tüm olay işleyicilerini keşfedebilir ve bu olay işleyicilerinin her birini tetikleyebilir.

### <a name="how-to-handle-domain-events"></a>Etki alanı olayları nasıl işleyebilir

Son olarak, olay işleyicisi genellikle gerekli ek agregaları elde etmek ve yan etki alanı mantığını yürütmek için altyapı depolarını kullanan uygulama katmanı kodu uygular. [eShopOnContainers aşağıdaki etki alanı olay işleyici kodu,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)bir uygulama örneği gösterir.

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

Altyapı kalıcılığı katmanının bir sonraki bölümünde açıklandığı gibi altyapı depolarını kullandığından, önceki etki alanı olay işleyicisi kodu uygulama katmanı kodu olarak kabul edilir. Olay işleyicileri diğer altyapı bileşenlerini de kullanabilir.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Etki alanı olayları, mikro hizmet sınırları dışında yayımlanacak tümleştirme olayları oluşturabilir

Son olarak, olayları bazen birden çok mikro hizmete yaymak isteyebileceğini belirtmek önemlidir. Bu yayılma bir tümleştirme olayıdır ve belirli bir etki alanı olay işleyicisinden bir olay veri günü aracılığıyla yayınlanabilir.

## <a name="conclusions-on-domain-events"></a>Etki alanı olayları yla ilgili sonuçlar

Belirtildiği gibi, etki alanınızdaki değişikliklerin yan etkilerini açıkça uygulamak için etki alanı olaylarını kullanın. DDD terminolojisini kullanmak için, bir veya birden çok agrega da yan etkileri açıkça uygulamak için etki alanı olaylarını kullanın. Ayrıca, daha iyi ölçeklenebilirlik ve veritabanı kilitleri üzerinde daha az etki için, aynı etki alanındaki agregalar arasında nihai tutarlılık kullanın.

Başvuru uygulaması, etki alanı olaylarını tek bir işlem içinde, toplu olarak eşzamanlı olarak yaymak için [MediatR'ı](https://github.com/jbogard/MediatR) kullanır. Ancak, etki alanı olaylarını eşzamanlı olarak yaymak için [RabbitMQ](https://www.rabbitmq.com/) veya [Azure Hizmet Veri Servisi](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) gibi bazı AMQP uygulamalarını da kullanabilirsiniz, ancak yukarıda da belirtildiği gibi, hata durumunda telafi edici eylemlere ihtiyaç duymanız gerekir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Greg Young' ı. Etki Alanı Etkinliği nedir?** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Jan Stenberg. Etki Alanı Olayları ve Nihai Tutarlılık** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard' ı. Daha iyi bir etki alanı olayları deseni** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon' u. Etkili Agrega Tasarımı Bölüm II: Agregaların Birlikte Çalışmasını Sağlamak** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard' ı. Etki alanınızı güçlendirme: Etki Alanı Etkinlikleri** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Tony Truong' ı. Etki Alanı Olayları Desen Örneği** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **Udi Dahan. Tam kapsüllü Etki Alanı Modelleri nasıl oluşturulur?** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **Udi Dahan. Etki Alanı Etkinlikleri – Take 2** \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **Udi Dahan. Etki Alanı Etkinlikleri – Kurtuluş** \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan Kronquist. Etki Alanı Etkinlikleri'ni yayımlamayın, iade edin!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de la Torre. DDD ve mikro hizmet mimarilerinde Etki Alanı Etkinlikleri ve Tümleştirme Etkinlikleri** \
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Önceki](client-side-validation.md)
>[Sonraki](infrastructure-persistence-layer-design.md)
