---
title: Etki alanı olayları. Tasarım ve uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Etki alanı olayları, tasarım ve uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 3daab93a97c57521ae6f16ea2498c3f36f30d795
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937133"
---
# <a name="domain-events-design-and-implementation"></a>Etki alanı olayları: tasarım ve uygulama

Açıkça yan etkilerini etki alanınız içindeki değişiklikler, uygulama için etki alanı olaylarını kullanın. Başka bir deyişle ve DDD terminolojiyi kullanarak, yan etkileri arasında birden çok toplamalar açıkça uygulamak için etki alanı olaylarını kullanın. İsteğe bağlı olarak daha iyi ölçeklenebilirlik ve veritabanı kilitlerini etkileri daha az nihai tutarlılık arasında aynı etki alanı içinde toplamlar kullanın.

## <a name="what-is-a-domain-event"></a>Bir etki alanı olayı nedir?

Bir olay geçmişte gerçekleşen bir şeydir. Bir etki alanı olayı, mantıksal olarak, belirli bir etki alanında gerçekleşen bir şeydir ve diğer bölümleri farkında olmanız ve olası tepki aynı etki alanının (işlem içi) istediğiniz bir şey.

Önemli bir avantajı, etki alanı olayları, bir etki alanında bir sorun oluştu sonra etkilere açıkça yerine örtük olarak ifade edilebilir ' dir. Bu yan etkileri iş görevle ilgili ya da tüm işlemler gerçekleştirilir böylece tutarlı olmalıdır, ya da bunların hiçbiri. Ayrıca, bir daha iyi görev ayrımı nettir sınıfların aynı etki alanındaki etki alanı olayları etkinleştirin.

Var. varsa, yan etkileri bir kullanım örneği tarafından provoked olmasını sadece Entity Framework ve varlıklar veya hatta toplamalar kullanıyorsanız, bir sorun oluştu sonra Örneğin, bu bağlı kod içinde örtük bir kavram olarak uygulanacaktır. Ancak, yalnızca bu kodu bilmiyor (yan etkisi) kodu ana işleminin bir parçası ise ya da bir yan etkisi gerçekten ise görürseniz. Öte yandan, etki alanı olaylarını kullanarak kavramı açık ve bulunabilen dil parçası olmasını sağlar. Örneğin, hizmetine uygulamada, bir sipariş oluşturma konusunda sırası değildir; yerinde bir sipariş kadar kullanıcı bir alıcısı olmadığından, özgün kullanıcıya, bağlı bir alıcı toplama oluşturur veya güncelleştirir. Etki alanı olayları kullanırsanız, etki alanı uzmanları tarafından sağlanan bulunabilen dilde dayalı olarak, etki alanı kuralı açıkça ifade edebilirsiniz.

Etki alanı olayları, önemli bir farkla Mesajlaşma stili olayları biraz benzerdir. Gerçek Mesajlaşma, message queuing, ileti aracıları veya AMPQ kullanarak service bus ile bir ileti her zaman zaman uyumsuz olarak gönderilen ve işlemleri ve makineler iletilir. Bu, birden çok sınırlanmış Bağlamlar, mikro hizmetler veya hatta farklı uygulamalara tümleştirmek için kullanışlıdır. Ancak, etki alanı olayları, çalışmakta olan etki alanı işlemi bir olaydan yükseltmek istediğiniz, ancak aynı etki alanı içinde gerçekleşmesi için tüm yan etkileri istediğiniz.

Etki alanı olayları ve yan etkileri (olay işleyicileri tarafından yönetilen daha sonra tetiklenen eylemler) neredeyse anında gerçekleşmelidir genellikle işlem içinde ve aynı etki alanı içinde. Bu nedenle, etki alanı olayları zaman uyumlu veya zaman uyumsuz olabilir. Tümleştirme olayları, ancak her zaman uyumsuz olması gerekir.

## <a name="domain-events-versus-integration-events"></a>Etki alanı olayları tümleştirme olayları karşılaştırması

Anlamsal olarak, etki alanı ve tümleştirme olayları aynı şeydir: hakkında bir şey mi oldu bildirimleri. Ancak, kendi uygulama farklı olmalıdır. Etki alanı, bir bellek içi Dünyası IOC kapsayıcı veya başka bir yöntem dayalı olarak uygulanabilir bir etki alanı olay dağıtıcısı depoya yalnızca iletileri olaylardır.

Öte yandan, diğer mikro hizmetler, sınırlanmış Bağlamlar veya hatta dış uygulama olup olmadığını kaydedilen işlem sayısı ve ek alt sistemler, güncelleştirmeleri yayılması tümleştirme olayları amacı olan. Bu nedenle, gerçekleşmesi gerektiğini yalnızca varlık başarıyla kalıcıysa beri pek çok senaryoda bu başarısız olursa tüm operasyon etkili bir şekilde hiçbir zaman oldu.

Buna ek olarak ve belirtilen, tümleştirme olayları birden çok mikro hizmetler (diğer sınırlanmış Bağlamlar) veya hatta dış sistemler/uygulamalar arasında zaman uyumsuz iletişim temel gerekir. Bu nedenle, olay veri yolu arabirimini arası işlem sağlar ve potansiyel olarak uzak hizmetler arasındaki iletişimi dağıtılan bazı altyapı gerekir. Ticari bir service bus, kuyruklar, bir posta kutusu kullanılan paylaşılan bir veritabanı veya diğer dağıtılmış temel alabilir ve ideal tabanlı bir Mesajlaşma sistemi gönderin.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Aynı etki alanı içinde birden çok toplamları arasında yan etkileri tetiklemek için tercih edilen yol olarak etki alanı olayları

Toplama örneği bir veya daha fazla ek toplamalarda çalıştırılacak ek bir etki alanına yönelik kurallardan gerektirir birine ilgili komut yürütme, tasarım ve uygulama etki alanı olayları tarafından tetiklenmesi için bu yan etkileri gerekir. Şekil 9-14 gösterilen şekilde ve en önemli biri olarak kullanım örnekleri, aynı etki alanı modeli içinde birden çok toplamları arasında durum değişikliklerinin yayılması bir etki alanı olayı kullanılmalıdır.

![](./media/image15.png)

**Şekil 9-14**. Aynı etki alanı içinde birden çok toplamları arasında tutarlılığı zorlamak için etki alanı olayları

Kullanıcı, bir sipariş başlattığında şekilde, özgün kimlik mikro hizmet kullanıcı bilgisi (bilgilerle CreateOrder komutunda sağlanan) göre sıralama mikro hizmet, bir alıcı nesnesinde oluşturulmasını OrderStarted etki alanı olayı tetikler. Başlangıçta oluşturulduğunda, etki alanı olay sırası toplama tarafından oluşturulur.

Alternatif olarak, toplama kök alt toplamlar (alt varlıklar) bir üyesi tarafından oluşturulan olaylara abone olabilir. Örneğin, her Orderıtem alt varlık öğesi fiyat belirli bir miktar alt sınırından daha yüksek olduğunda veya ürün öğesi miktarı çok yüksek olduğunda bir olay yükseltebilirsiniz. Toplama kök bu olayları alma ve genel hesaplama veya toplama gerçekleştirir.

Bu olay tabanlı iletişim doğrudan içinde toplamlar uygulanmadı anlaşılması önemlidir; etki alanı olay işleyicileri uygulanması gerekir. Etki alanı olaylarını işleme bir uygulamanın konusudur. Etki alanı model katmanında yalnızca etki alanı mantığı üzerinde durmalısınız — bir etki alanı uzmanı öğrenmesi şey, işleyiciler ve depolarını kullanarak yan etkisi Kalıcılık eylemler gibi uygulama altyapıya değil. Bu nedenle, uygulama katmanı düzeyinde, bir etki alanı olayı ortaya çıktığında eylemleri tetikleyen etki alanı olay işleyicileri burada olmalıdır.

Etki alanı olayları herhangi bir sayıda uygulama eylemleri tetiklemek için de kullanılabilir ve daha önemli bir ayrılmış şekilde gelecekte bu sayıyı artırmak için açık olmalıdır. Örneği için sipariş başlatıldığında, bu bilgileri diğer toplamalara yayılması veya hatta bildirimleri gibi uygulama eylemleri yükseltmek için bir etki alanı olayı yayımlamak isteyebilirsiniz.

Açık bir etki alanı olay meydana geldiğinde yürütülecek eylemlerin sayısını anahtar noktasıdır. Sonuç olarak, etki alanınızı ve uygulama kuralları ve eylemleri çıkarılır. "Yapıştırıcı" ile kodunuzu bağlantısı varsa ancak bir şey olduğunda yan etkisi işlemlerinin sayısı ve karmaşıklığı, büyüyecektir (diğer bir deyişle, yalnızca yeni C anahtar sözcüğüyle nesneleri örnekleme\#), sonra da yeni bir eylem eklemek için gereken her zaman gerekecektir özgün koda değiştirin. Her yeni gereksinimi özgün kod akışını değiştirmeniz gerekir çünkü bu yeni hataları neden olabilir. Bu karşı gider [açık/kapalı İlkesi](https://en.wikipedia.org/wiki/Open/closed_principle) gelen [DÜZ](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)). Karşı ase'nizden yalnızca, işlemleri işlemlerini özgün sınıf ve büyüme büyütün, not [tek sorumluluk İlkesi'ni (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Öte yandan, etki alanı olayları kullanırsanız, bu yaklaşımı kullanarak sorumlulukları ayrıştırarak ayrıntılı ve ayrılmış bir uygulama oluşturabilirsiniz:

1.  (Örneğin, CreateOrder) komut gönderebilirsiniz.
2.  Komutu komut işleyici alır.
    -   Tek bir toplamada ait işlem yürütün.
    -   (İsteğe bağlı) Yan etkiler (örneğin, OrderStartedDomainEvent) için etki alanı olayları tetikleyebilir.
1.  Açık bir yan etkileri sayısı birden çok toplamalar veya uygulama eylemleri yürütülür (geçerli işlemdeki) etki alanı olayları işleyin. Örneğin:
    -   Doğrulayın veya alıcı ve ödeme yöntemini oluşturun.
    -   Oluşturup durumları alıcıya e-posta gönderme gibi mikro hizmetler veya tetikleyici dış eylemler arasında yaymak için olay veri yolu için ilgili tümleştirme olay gönderebilirsiniz.
    -   Diğer yan etkileri işleyin.

Şekil 9-15'te gösterildiği gibi aynı etki alanı olayından başlayarak birden fazla eylem bağlama tümleştirme olayları ve olay veri yolu ile mikro hizmetler arasında gerçekleştirmeniz gereken ek uygulama eylemleri ve etki alanı içinde başka toplamalar ilgili işleyebilir.

![](./media/image16.png)

**Şekil 9-15**. Etki alanı başına birden fazla eylem işleme

Mikro hizmet'ın davranışını depoları veya bir uygulama API gibi altyapı nesnelerinden kullanacağınız için olay işleyicileri, genellikle uygulama katmanında cihazlardır. Her ikisi de uygulama katmanının bir parçası olduğundan bu anlamda olay işleyicileri komut işleyicilerine benzer. Bir komutu yalnızca bir kez işlenmesi gerektiğini önemli fark vardır. Bir etki alanı olayı olabilir işlenen sıfır veya *n* zaman birden çok alıcılar veya farklı bir amaç için her işleyicisi ile olay işleyicileri tarafından alınabilir olduğundan.

Olasılığını başına etki alanı olay işleyicileri açık bir dizi geçerli kodunuzu etkilemeden çok daha fazla etki alanı kuralları eklemenize olanak sağlar. Örneğin, bir olaydan sonra sağ gerçekleştirilecek olan aşağıdaki iş kuralı uygulama birkaç olay işleyicileri (veya hatta yalnızca bir tane) eklemek kadar kolaydır olabilir:

$6.000 deposundaki bir müşteriye göre siparişler, herhangi bir sayıda satın alınan toplam tutarı aşarsa, indirim % bir 10 her yeni sipariş için geçerlidir ve müşteri bu indirim tarihteki siparişlere hakkında bir e-posta ile bildir.

## <a name="implementing-domain-events"></a>Uygulama etki alanı olayları

C# içinde bir etki alanı olayı yalnızca bir veri bekletme yapısı sınıfına, aşağıdaki örnekte gösterildiği gibi yalnızca etki alanında ne için ilgili tüm bilgileri içeren bir DTO gibi mı:

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

Aslında OrderStarted olayla ilişkili tüm verileri içeren bir sınıf budur.

Bir olay geçmişte gerçekleşen bir sorun olduğundan açısından bulunabilen dil etki alanının OrderStartedDomainEvent veya OrderShippedDomainEvent gibi bir geçmiş şimdiki fiili olarak olay sınıfı adını temsil edilmelidir. Etki alanı olay sıralama mikro hizmetine nasıl uygulandığını olmasıdır.

Bir olay değil değiştirmelisiniz geçmişte gerçekleşen bir sorun olduğundan daha önce belirtildiği gibi bir önemli olayları, özelliğidir. Bu nedenle sabit bir sınıf olması gerekir. Önceki kodda dışında nesne salt okunur yerine özellikleri görebilirsiniz. Olay nesnesi oluşturduğunuzda, nesneyi güncelleştirmek için yalnızca Oluşturucu üzerinden yoludur.

### <a name="raising-domain-events"></a>Etki alanı olayları oluşturma

Sonraki soruya kendi ilgili olay işleyicileri ulaşacak şekilde bir etki alanı olayı Tetikle bağlanmasıdır. Birden çok yaklaşımın kullanabilirsiniz.

UDI Dahan Başlangıçta önerilen (örneğin, çeşitli gönderileri, gibi ilgili [etki alanı etkinlikleri alın 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) olaylar oluşturma ve yönetme için statik bir sınıf kullanarak. Bu DomainEvents.Raise (Event myEvent) gibi bir söz dizimi kullanarak hemen çağrıldığında, etki alanı olayları oluşturacak DomainEvents adlı statik bir sınıf içerebilir. Jimmy Bogard yazdığı blog gönderisini ([etki alanınızı güçlendirme: etki alanı olayları](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) benzer bir yaklaşım önerir.

Etki alanı olayları sınıfı statik olduğunda, ancak bunu ayrıca işleyicilerini hemen gönderir. Olay işleyicileri yan etkileri mantığı ile olay oluştuktan hemen sonra yürütülür çünkü bu test ve hata ayıklama daha zor hale getirir. Test ve hata ayıklama odaklanır ve geçerli toplama sınıflarda neler olduğunu yalnızca istediğiniz; aniden yan etkileri diğer toplamalar veya uygulama mantığı ile ilgili diğer olay işleyicileri yeniden yönlendirilmesini istediğiniz değil. Diğer yaklaşımlar gelişim göstermiştir nedeni, sonraki bölümde açıklandığı gibi budur.

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>Ertelenmiş bir yaklaşım oluşturma ve olayları gönderme

Bir etki alanı olay işleyicisine hemen gönderme yerine etki alanı olayları bir koleksiyona eklemek için daha iyi bir yaklaşım olan ve bu etki alanı olayları gönderme *hemen önce* veya *doğru*  *sonra* (ile gibi SaveChanges EF içinde) işlemi yürütülüyor. (Bu yaklaşım Jimmy Bogard tarafından bu gönderisinde açıklanan [daha iyi bir etki alanı olayları deseni](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Farklı işlemlerde veya aynı işlemin parçası olarak yan etkileri içerecektir olup olmadığını belirler. bu yana etki alanı olayları göndermek, karar sonra işlem Sistemi'ne sağ önce veya sağ önemlidir. İkinci durumda, nihai tutarlılık arasında birden çok toplamalar işlem gerekir. Bu konu, sonraki bölümde ele alınmıştır.

Hangi hizmetine kullanan ertelenmiş yaklaşımdır. İlk olarak, bir koleksiyonunu veya varlık başına olayların listesi, varlıklarda geçekleşmiş olaylar ekleyin. Bu liste, varlık temel sınıfın aşağıdaki örnekte gösterildiği gibi varlık nesnesinin bir parçası veya daha da iyi temel varlık sınıfınızın bir parçası olmalıdır:

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
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

Bir olayı oluşturmak istediğinizde, bu olay toplaması için toplama kök varlığın herhangi bir yöntemi en koddan eklemeniz yeterlidir.

Aşağıdaki kod, parçası [toplama kök hizmetine sipariş](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), bir örnek gösterilmektedir:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

AddDomainEvent yöntemi yapılması gereken tek şey listesine olay ekleme dikkat edin. Hiçbir olay henüz gönderilir ve hiçbir olay işleyicisi henüz çağrılır.

Aslında, işlem veritabanına yaparsanız olayları daha sonra gönderme istiyorsunuz. Entity Framework Core kullanıyorsanız, aşağıdaki kodda gösterildiği gibi EF DbContext SaveChanges yöntemi içinde anlamına gelir:

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

Bu kod ile ilgili olay işleyicilerini varlık olaylara gönderme.

Genel sonuç, (basit bir ekleme bellekte listeye) bir etki alanı olayı oluşturma, bir olay işleyicisi gönderme ayrılmış emin olur. Ayrıca, ne tür bir dağıtıcı kullanmakta olduğunuz bağlı olarak, olayları zaman uyumlu veya zaman uyumsuz olarak gönderme.

İşlem sınırları içine önemli gelen buradan Oynat dikkat edin. Varsa, iş ve işlem birimi, birden fazla toplama kapsayabilir (olarak EF Core ve ilişkisel bir veritabanı kullanılırken), bu iyi çalışabilir. Ancak işlem toplamalar, Azure DocumentDB gibi NoSQL veritabanı kullanırken olduğu gibi dağıtılamaz, tutarlılık elde etmek için ek adımlar uygulamanız gerekir. Neden Kalıcılık ignorance Evrensel değil başka bir nedeni budur; Bu, kullandığınız depolama sistemine bağlıdır.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Toplamlar ve nihai tutarlılık arasında toplamalar arasında tek bir işlem

Tek bir işlem üzerinde nihai tutarlılık arasında bu toplamalara bağlı olan ve toplamları arasında gerçekleştirilip soru tartışmalı bir bilgisayardır. Eric Evans ve Vaughn Vernon kural, bir işlem Danışmanı gibi birçok DDD yazarları bir toplama = ve bu nedenle için nihai tutarlılık arasında toplamalar buna. Örneğin, kendi kitaptaki *etki alanı Odaklı Tasarım*, Eric Evans belirten bu:

Toplamlar yayılan herhangi bir kural her zaman güncel olması beklenen değil. Olay işleme, toplu işlem veya diğer güncelleştirme mekanizmaları, belirli bir süre içinde diğer bağımlılıkları çözülebilir. (128 sayfa)

Vaughn Vernon bildiren aşağıdaki [etkili toplama tasarımı. Kısım II: Yapma toplayan iş birlikte](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

Bu nedenle, bir toplama örneği gerektirir ek iş kuralları üzerinde bir veya daha fazla toplamalar yürütme komut yürütme, son tutarlılık kullanın \[...\] DDD modelinde nihai tutarlılığı destekleyecek şekilde pratik bir yolu yoktur. Bir toplama yöntemi, bir veya daha fazla zaman uyumsuz abonelere teslim zaman içinde bir etki alanı olayı yayımlar.

Bu stratejinin birçok toplamalar veya varlıkları kapsayan işlemler yerine ayrıntılı işlemler benimsemenin üzerinde temel alır. İkinci durumda, veritabanı kilit sayısı yüksek ölçeklenebilirlik gereksinimlerini ile büyük ölçekli uygulamalarda önemli olacağını olur. Yüksek düzeyde ölçeklenebilir uygulamalar birden çok toplamları arasında anlık bir işlem tutarlılığı sahip olmaması gereken olgu benimsemenin kavramı, son tutarlılık kabul ile yardımcı olur. Atomik değişikliklerin iş için gerekli değildir ve herhangi bir durumda, belirli işlemler atomik işlemler olmadığını gerektiğini söylüyor için etki alanı uzmanları sorumluluğundadır. Her zaman bir işlem birden çok toplamları arasında atomik bir işlem gerekiyorsa, toplama daha büyük olmalıdır veya doğru şekilde tasarlanmamış isteyebilir.

Diğer geliştiriciler ve mimarlara Jimmy Bogard gibi ancak birkaç toplamları arasında tek bir işlem yayma ile sorunsuz — ancak yalnızca zaman bu ek toplamalar yan etkileri aynı özgün komutu için ilgilidir. Örneğin, [daha iyi bir etki alanı olayları deseni](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard belirten bu:

Genellikle, aynı mantıksal işlem içinde ancak etki alanı olayı, aynı kapsamda gerçekleşmesi için bir etki alanı olayı yan etkilerini istiyorum \[...\] Sadece biz bizim işlem göndermeden önce size sunduğumuz ilgili işleyicilerini olaylara gönderme.

Etki alanı olayları sağ gönderme, *önce* aynı işlemde dahil edilecek olayların yan etkileri istediğiniz özgün işlemlerinin, olmasıdır. EF DbContext SaveChanges yöntem başarısız olursa, örneğin, işlem sonucu ilgili etki alanı olay işleyicileri tarafından uygulanan herhangi bir yan etkisi işlemi dahil olmak üzere tüm değişiklikleri geri döner. DbContext ömrü kapsam olarak tanımlanan varsayılan olduğundan bu "kapsamlıdır." Bu nedenle, DbContext nesnesini örneği oluşturulan nesne grafiği ve aynı kapsam içinde birden çok depo nesneleri arasında paylaşılır. Bu, Web API'si ve MVC uygulamaları geliştirirken HttpRequest kapsamı ile örtüşür.

Gerçekte (tek bir atomik işlem ve nihai tutarlılık) her iki yaklaşım uygun olabilir. Ayrıca, etki alanı veya iş gereksinimlerinize ve etki alanı uzmanları, ne yapacağımı gerçekten bağlıdır. Ayrıca nasıl ölçeklenebilir hizmeti yapmanız gereken bağlıdır (daha ayrıntılı işlemler sahip veritabanı kilitlerini göre daha az etkileyebilir). Ve bunu ne kadar yatırım, nihai tutarlılık, olası tutarsızlıklar toplamalara ve telafi izin eylemlerini uygulamak için gereken arasında saptamak amacıyla daha karmaşık kod gerektirdiğinden, kodunuzda olun iradeye sahip olduğunuza bağlıdır. Özgün toplama ve olayların ne zaman gönderilen için daha sonra değişiklikleri, bir sorun olduğunun dikkate alın ve olay işleyicileri yan etkileri tamamlanamaz, tutarsızlıklar toplamalara arasında olacaktır.

Özgün işlemin bir parçası olmaları için etki alanı olayları ek veritabanı tablolarında depolama telafi izin eylemleri izin vermenin bir yolu olabilir. Daha sonra tutarsızlıklarını algılayan ve olayların geçerli durumdaki bir toplama listesini karşılaştırarak telafi izin eylemleri çalıştıran bir toplu işlem olabilir. Telafi izin eylemleri ayrıntılı analiz iş kullanıcısı ve etki alanı uzmanları ile görüştükten içerir, taraftan gerektiren karmaşık bir konu bir parçasıdır.

Herhangi bir durumda, gereksinim duyduğunuz yaklaşımı seçebilirsiniz. Ancak ilk yaklaşım ertelenmiş — tek bir işlem kullanmak için olayları kaydetmeden önce oluşturma — en basit EF Core ve ilişkisel bir veritabanı kullanılırken yaklaşımdır. Bu uygulama daha kolay ve birçok iş durumlarda geçerli olur. Ayrıca sıralama mikro hizmetine kullanılan yaklaşım değildir.

Ancak nasıl aslında bu olaylarla ilgili olay işleyicilerini gönderme? Nedir \_önceki örnekte gördüğünüz Dünyası nesne? Olayları ve olay işleyicilerini arasında eşleme için kullanmanız yapıtlar ve teknikleri ile yapmak, sahip.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Etki alanı olay dağıtıcısı rolü: olayları için olay işleyicileri eşleme

Gönderme veya olayları yayımlayabilirsiniz, böylece her ilgili işleyici alın ve bu olayı temel alan yan etkileri işlem bu olayı yayımlar yapıt tür gerekir.

Bir gerçek bir Mesajlaşma sistemi veya muhtemelen bellek içi olayları aksine service bus temel bile bir olay veri yolu, bunun bir yaklaşımdır. Ancak, ilk örneği için gerçek Mesajlaşma aynı işlem içinde bu cihazdaki olayları işlemeye olması gerektiğinden, etki alanı olaylarını işlemek için düşünülecek olacaktır (diğer bir deyişle, aynı etki alanınızı ve uygulama katmanı içinde).

Birden çok olay işleyicilerine olayları eşleştirmek için başka bir yol olayları gönderme nerede dinamik olarak çıkarabilir, bir IOC kapsayıcısındaki türleri kayıt kullanmaktır. Diğer bir deyişle, belirli bir olay almak olay işleyicileri gerekenler bilmeniz gerekir. Şekil 9-16 için basitleştirilmiş bir yaklaşım gösterilmektedir.

![](./media/image17.png)

**Şekil 9-16**. Etki alanı olay dağıtıcısı rolü IOC kullanma

Teknik işlemleri ve yapıtları kendiniz bu yaklaşımı uygulamak için oluşturabilirsiniz. Ancak, ayrıca gibi kullanılabilir kitaplıkları kullanabilirsiniz [MediatR](https://github.com/jbogard/MediatR), IOC kapsayıcınızı, aslında kullanır. Bu nedenle doğrudan önceden tanımlanmış arabirimler ve Dünyası nesnenin yayımlama/dağıtma yöntemleri kullanabilirsiniz.

Kod içinde ilk olay işleyici türlerini IOC kapsayıcınızı kaydetmek aşağıdaki örnekte gösterildiği gibi ihtiyacınız [hizmetine sıralama mikro hizmet](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kod ilk etki alanı olay işleyicileri işleyicilerin tutan derleme bularak içeren derlemeyi tanımlar (typeof(ValidateOrAddBuyerAggregateWhenXxxx), ancak kullanarak seçebilirdiniz diğer tüm olay işleyicisi derlemeyi bulmak için). Tüm olay işleyicilerine IAsyncNotificationHandler arabirimini uygulama olduğundan, kod ardından yalnızca bu arar türleri ve tüm olay işleyicilerine kaydeder.

### <a name="how-to-subscribe-to-domain-events"></a>Etki alanı olaylarına abone olma

MediatR kullandığınızda, aşağıdaki kodda gördüğünüz gibi her bir olay işleyicisi INotificationHandler arabirimin genel parametresinde sağlanan bir olay türü kullanmanız gerekir:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Olay aboneliği kabul edilebilir, olay işleyicisi, arasındaki ilişkiye bağlı MediatR yapıt, tüm olay işleyicilerine her olay için keşfetmek ve her biri bu olay işleyicileri tetikleyin.

### <a name="how-to-handle-domain-events"></a>Etki alanı olaylarını işlemek nasıl

Son olarak, olay işleyicisi genellikle yan etkisi etki alanı mantığı yürütmek için gerekli ek toplamları elde etmek için altyapı depoları kullanan uygulama katmanı kodu uygular. Aşağıdaki [hizmetine etki alanı olay işleyici kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), bir uygulama örneği gösterilmektedir.

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

Altyapı depoları kullandığından önceki etki alanı olay işleyici kodunu uygulama katmanı kod üzerinde altyapı Kalıcılık katmanını sonraki bölümde açıklandığı gibi değerlendirilir. Olay işleyicileri, diğer altyapı bileşenlerini de kullanabilirsiniz.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Etki alanı olayları mikro hizmet sınırları dışına yayımlanacak tümleştirme olayları oluşturmak

Son olarak, bazı durumlarda olayları birden çok mikro hizmetler yaymak isteyebileceğiniz, bahsetmek önemlidir. Bir tümleştirme olay kabul edilir ve hiçbir özel etki alanı olay işleyicisinden bir olay veri yolu üzerinden yayınlanabilir.

## <a name="conclusions-on-domain-events"></a>Etki alanı olayları sonuçları

Belirtildiği gibi açıkça yan etkilerini, etki alanınızda değişiklikleri uygulamak için etki alanı olaylarını kullanın. DDD terminolojisi kullanmak için açıkça bir veya birden çok toplamları arasında yan etkileri uygulamak için etki alanı olayları kullanın. Ayrıca, daha iyi ölçeklendirilebilirlik için ve veritabanı kilitlerini etkisini daha az nihai tutarlılık arasında aynı etki alanı içinde toplamlar kullanın.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Greg Young. Bir etki alanı olayı nedir?**
    [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg. Etki alanı olayları ve nihai tutarlılık**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard. Daha iyi bir etki alanı olay deseni**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon. Etkili toplama tasarımı Bölüm II: Birlikte yapma toplamalar çalışma**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard. Etki alanınızı güçlendirme: etki alanı olayları**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *

-   **Tony Truong. Etki alanı olayları desen örneği**
    [*https://www.tonytruong.net/domain-events-pattern-example/*](https://www.tonytruong.net/domain-events-pattern-example/)

-   **UDI Dahan. Etki alanı modellerini oluşturma tam olarak kapsüllenmiş**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **UDI Dahan. Etki alanı etkinlikleri alın 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **UDI Dahan. Etki alanı etkinlikleri Salvation**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist. Yoksa, etki alanı olayları yayımlama, döndürülmeleri!**
    [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesar de la Torre. Etki alanı olayları vs. DDD ve mikro hizmet mimarileri tümleştirme olayları**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[Önceki](client-side-validation.md)
[İleri](infrastructure-persistence-layer-design.md)
