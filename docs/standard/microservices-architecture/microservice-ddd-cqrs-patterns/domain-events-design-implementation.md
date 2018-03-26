---
title: Etki alanı olaylar. Tasarım ve uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Etki alanı olayları, tasarım ve uygulama
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
ms.openlocfilehash: 5840c2f7692d81f193c7d659aea6eb42a431369e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="domain-events-design-and-implementation"></a>Etki alanı olayları: tasarım ve uygulama

Açıkça yan etkileri etki alanınızda değişiklikleri uygulamak için etki alanı olayları kullanın. Diğer sözcükleri ve DDD terminolojisi kullanarak, açıkça yan etkileri arasında birden çok toplamalar uygulama için etki alanı olaylarını kullanın. İsteğe bağlı olarak, daha iyi ölçeklenebilirlik ve daha az veritabanı kilitleri etkileri aynı etki alanındaki toplamalar arasında nihai tutarlılık kullanın.

## <a name="what-is-a-domain-event"></a>Bir etki alanı olay nedir?

Bir olay geçmişteki şeydir. Bir etki alanı, mantıksal olarak, belirli bir etki alanında gerçekleşen bir şey olayıdır ve şeyin farkında olmanız ve olası tepki için aynı etki alanında (işlemdeki) diğer bölümleri istiyorsunuz.

Etki alanı olayların önemli bir avantajı, bir şeyler bir etki alanında olduğu sonra etkilerinin açıkça yerine örtük olarak ifade edilebilir ' dir. Bu yan etkileri iş görevle ilgili ya da tüm işlemleri gerçekleşecek şekilde tutarlı olmalıdır, veya bunların hiçbiri. Ayrıca, etki alanı olayları sorunları aynı etki alanındaki sınıflar arasında daha iyi ayrılması etkinleştirir.

Yan etkileri kullanım örneği tarafından provoked olmasını var. varsa, yalnızca Entity Framework ve varlıklar veya hatta toplamalar kullanıyorsanız, bir şeyler olduğu sonra Örneğin, bu bağlı kodda örtük bir kavram olarak uygulanacaktır. Ancak, bu kod yalnızca görürseniz, bu kodu (yan etkisi) ana işleminin bir parçası ise veya gerçekten bir yan etkisi ise anlamayabilirsiniz. Diğer taraftan, etki alanı olayları kullanarak kavramı açık ve her yerden dil parçası hale getirir. Örneğin, eShopOnContainers uygulamada bir sıra oluşturma neredeyse sırası değildir; güncelleştirmeleri veya yerine bir sipariş kadar kullanıcı bir alıcı olmadığından özgün kullanıcıyı temel alarak bir alıcı toplama oluşturur. Etki alanı olayları kullanırsanız, etki alanı uzmanlar tarafından sağlanan bulunabilen dilde göre bu etki alanı kural açıkça hızlı.

Etki alanı olayları, önemli bir farkla Mesajlaşma stili olayları biraz benzer. Gerçek Mesajlaşma, message queuing, ileti aracıları veya AMPQ kullanarak bir hizmet veri yolu ile bir ileti her zaman zaman uyumsuz olarak gönderilir ve işlemleri ve makineler arasında iletişim. Bu, birden çok ilişkisindeki bağlamları, mikro veya hatta farklı uygulamaları tümleştirmek için kullanışlıdır. Ancak, etki alanı olaylarla çalıştırmakta olduğunuz etki alanı işlemi bir olaydan yükseltmek istediğiniz ancak aynı etki alanı içinde gerçekleşmesi için hiçbir yan etkileri istiyor.

Etki alanı olayları ve bunların yan etkileri (olay işleyicileri tarafından yönetilen sonradan tetiklenen eylemler) hemen hemen gerçekleşeceğini genellikle işlem içinde ve aynı etki alanı içinde. Bu nedenle, etki alanı olayları zaman uyumlu veya zaman uyumsuz olabilir. Tümleştirme olayları, ancak her zaman zaman uyumsuz olması gerekir.

## <a name="domain-events-versus-integration-events"></a>Etki alanı olayları tümleştirme olaylarını karşılaştırması

Anlam olarak, etki alanı ve tümleştirme olaylarını aynı şeydir: yalnızca gerçekleşen bir şey hakkında bildirimler. Ancak, kendi uygulama farklı olmalıdır. Etki alanı, bir bellek içi Dünyası IOC kapsayıcı veya başka bir yöntem dayalı olarak uygulanabilir bir etki alanı olay dağıtıcıya gönderilen yalnızca ileti olaylardır.

Diğer mikro, sınırlanmış bağlamları ve hatta dış uygulamaları olup diğer yandan, tümleştirme olayların yürütülen işlemler ve ek alt sistemleri, güncelleştirmelerinin yayılması amaçtır. Bu nedenle, gerçekleşeceğini yalnızca varlık başarıyla kalıcı değilse bu yana birçok senaryoda bu başarısız olursa, tüm işlem etkili bir şekilde asla oldu.

Buna ek olarak ve belirtilen, tümleştirme olarak olayları birden çok mikro (diğer ilişkisindeki bağlamlarda) ya da hatta dış sistemler/uygulamalar arasında zaman uyumsuz iletişim temel gerekir. Bu nedenle, olay veri yolu arabirimi arası işlem sağlar ve büyük olasılıkla uzak Hizmetleri arasındaki iletişimi dağıtılan bazı altyapı gerekir. Ticari service bus, kuyruklar, bir posta kutusu olarak kullanılan paylaşılan bir veritabanı veya diğer dağıtılmış göre ve ideal olarak temel ileti sistemini gönderme.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Aynı etki alanı içinde birden çok toplamalar arasında yan etkileri tetiklemek için tercih edilen bir yolu olarak etki alanı olayları

Bir veya daha fazla ek toplamalar çalıştırılacak ek etki alanı kuralları toplama örneği gerektirir için ilgili bir komutu yürütülürken, tasarım ve etki alanı olaylar tarafından tetiklenen bu yan etkileri uygulamak. Şekil 9-14'de gösterildiği gibi ve en önemli biri olarak kullanım, bir etki alanı olay aynı etki alanı modeli içinde birden çok toplamalar arasında durum değişiklikleri yaymak için kullanılmalıdır.

![](./media/image15.png)

**Şekil 9-14**. Aynı etki alanı içinde birden çok toplamalar arasında tutarlılığı zorlamak için etki alanı olayları

Kullanıcı bir sipariş başlattığında şekilde, özgün kimlik mikro hizmet kullanıcı bilgisi (bilgilerle CreateOrder komutta sağlanan) göre sıralama mikro hizmet alıcı nesnesinde oluşturulmasını OrderStarted etki alanı olay tetiklenir. İlk başta oluşturulduğunda, etki alanı olayı sırası toplama tarafından oluşturulur.

Alternatif olarak, kendi toplamalar (alt varlıkları) üyeleri tarafından oluşturulan olaylara abone birleşik kök olabilir. Örneğin, her ÖgeSipariş alt varlık öğesi fiyat belirli miktardan daha yüksek olduğunda ya da ürün öğesi tutarı çok yüksek olduğunda bir olay yükseltebilirsiniz. Birleşik kök sonra bu olayları almak ve bir genel hesaplama veya toplama gerçekleştirin.

Bu olay tabanlı iletişim doğrudan içinde toplamalar uygulanmadı anlamak önemlidir; etki alanı olay işleyicileri uygulamanız gerekir. Etki alanı olayları işleme bir uygulama konusudur. Etki alanı modeli katmanı, yalnızca etki alanı mantığı odaklanmanız gerekir — bir etki alanı Uzman öğrenmesi şey, uygulama altyapısı işleyicileri ve depoları kullanarak yan etkisi Kalıcılık eylemleri gibi değil. Bu nedenle, uygulama katmanı düzeyi bir etki alanı olay oluşturulduğunda eylemleri tetikleyen etki alanı olay işleyicileri, sahip değil.

Etki alanı olaylar ayrıca herhangi bir sayıda uygulama eylemleri tetiklemek için kullanılabilir ve daha önemli bir ayrılmış şekilde gelecekte bu sayıyı artırmak için açık olmalıdır. Örneğin, sipariş başlatıldığında, bir etki alanı olay başka Toplamalar için bu bilgileri yayılmasına veya hatta bildirimleri gibi uygulama eylemleri yükseltmek için yayımlama isteyebilirsiniz.

Bir etki alanı olay gerçekleştiğinde yürütülecek eylem açık sayısı anahtar noktasıdır. Sonuç olarak, etki alanı ve uygulama kuralları ve eylemleri büyüyecektir. Kodunuzu "Yapıştır" ile bağlı ancak karmaşıklığa veya bir şey olduğunda yan etkisi eylemlerin sayısını, büyüyecektir (diğer bir deyişle, yalnızca C yeni anahtar sözcüğüyle örnek oluşturma nesneleri\#), yeni bir eylem eklemek için gereken her zaman için gerekir Özgün kod değiştirin. Her yeni gereksinimi özgün kod akış değiştirmeniz gerekir çünkü bu yeni hataları neden olabilir. Bu karşı gider [açık/kapalı ilkesine](https://en.wikipedia.org/wiki/Open/closed_principle) gelen [DÜZ](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)). Hangi karşı gider yalnızca, işlemleri yönetme özgün sınıf ve büyümesine büyüme, not [tek sorumluluk İlkesi'ni (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Diğer taraftan, etki alanı olayları kullanırsanız, bu yaklaşımı kullanarak sorumlulukları ayrıştırarak hassas ve ayrılmış bir uygulama oluşturabilirsiniz:

1.  Bir komutu (örneğin, CreateOrder) gönderin.
2.  Komutu bir komut işleyici alır.
    -   Tek bir toplama 's işlem yürütün.
    -   (İsteğe bağlı) Yan etkiler (örneğin, OrderStartedDomainEvent) için etki alanı olayları yükseltin.
1.  Açık bir yan etkileri sayısı birden çok toplamalar veya uygulama eylemleri yürütecek etki alanı olayları (geçerli işlemdeki) idare eder. Örneğin:
    -   Doğrulamak veya alıcı ve ödeme yöntemini oluşturun.
    -   Oluşturun ve olay veri yoluna alıcıya e-posta gönderme gibi mikro veya tetikleyici dış eylemler arasında durumları yaymak için ilgili tümleştirme olay gönderin.
    -   Diğer yan etkileri işleyin.

Şekil 9-15'te gösterildiği gibi aynı etki alanı olayından başlangıç başka toplamalar etki alanındaki veya tümleştirme olayların ve olay veri yolu ile bağlanma mikro arasında gerçekleştirmeniz gereken ek uygulama eylemleri ilgili birden çok eylem işleyebilir.

![](./media/image16.png)

**Şekil 9-15**. Etki alanı başına birden çok eylem işleme

Mikro hizmet'in davranışını depoları veya bir uygulama API gibi altyapı nesnelerinden kullanacağından olay işleyicileri genellikle uygulama katmanında yayımlanır. Bu anlamda olay işleyicileri hem de uygulama katmanı parçası olacak şekilde, komut işleyicilerine benzer. Bir komutu yalnızca bir kez işlenmesi önemli farktır. Bir etki alanı olay olabileceğinden sıfır işlenen veya *n* , çünkü zaman, birden çok alıcıya veya farklı bir amaç için her işleyici ile olay işleyicileri tarafından alınan.

Açık bir etki alanı olay başına işleyici sayısı olasılığını geçerli kodunuzu etkilemeden pek çok daha fazla etki alanı kural eklemenize olanak sağlar. Örneğin, bir olaydan sonra sağ gerçekleştirileceğini aşağıdaki iş kuralı uygulama birkaç olay işleyicileri (veya tek bile) ekleme olarak kadar kolay olabilir:

Deposunda bir müşteri tarafından siparişler, herhangi bir sayıda satın alınan toplam miktarı $6,000 aşarsa, her yeni siparişe % 10 indirim kapalı uygulamak ve müşteri bu indirim gelecekteki siparişleri hakkında bir e-posta ile bildir.

## <a name="implementing-domain-events"></a>Etki alanı olayları uygulama

C# ' ta bir etki alanı yalnızca bir veri bekletme yapısı veya yalnızca etki alanında ne için aşağıdaki örnekte gösterildiği gibi ilgili tüm bilgileri içeren bir DTO gibi sınıfına olayıdır:

```csharp
public class OrderStartedDomainEvent : INotification
{
    public string UserId { get; private set; }
    public int CardTypeId { get; private set; }
    public string CardNumber { get; private set; }
    public string CardSecurityNumber { get; private set; }
    public string CardHolderName { get; private set; }
    public DateTime CardExpiration { get; private set; }
    public Order Order { get; private set; }

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

Bu OrderStarted olaya ilgili tüm verileri tutan aslında bir sınıftır.

Bir olay, geçmişteki bir şey olduğundan bakımından bulunabilen dil etki alanının OrderStartedDomainEvent veya OrderShippedDomainEvent gibi bir geçmiş zamanın fiili olarak olay sınıf adını temsil. Etki alanı olay sıralama mikro hizmet eShopOnContainers içinde nasıl uygulandığını olmasıdır.

Bir olay, değil değiştirmelisiniz geçmişteki bir şey olduğundan daha önce belirtildiği gibi bir önemli olayları, özelliğidir. Bu nedenle sabit bir sınıf olmalıdır. Özellikleri dışında nesne salt okunur yerine önceki kod görebilirsiniz. Olay nesnesi oluşturduğunuzda, nesneyi güncelleştirmek için yalnızca oluşturucu kullanılarak yoludur.

### <a name="raising-domain-events"></a>Etki alanı olaylar oluşturma

Sonraki soruya kendi ilgili olay işleyicileri eriştiği için bir etki alanı olayını Başlat şeklidir. Birden çok yaklaşımlar kullanabilirsiniz.

UDI Dahan Başlangıçta önerilen (örneğin, birkaç içinde postaları, gibi ilgili [etki alanı olayları – alın 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) olaylar oluşturma ve yönetme için statik bir sınıf kullanma. Bu DomainEvents.Raise (olay myEvent) gibi sözdizimini kullanarak hemen çağrıldığında, etki alanı olaylar oluşturacak DomainEvents adlı bir statik sınıf içerebilir. Jimmy Bogard yazdı bir blog gönderisini ([etki alanınızın güçlendirme: etki alanı olayları](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) benzer bir yaklaşım önerir.

Etki alanı olayları sınıfı statik olduğunda, ancak, bu da işleyicilere hemen gönderir. Olay tetiklenir hemen sonra yan etkileri mantığı ile olay işleyicileri çalıştırıldığı için bu test ve hata ayıklama daha zor hale getirir. Test ve hata ayıklama odaklanır ve geçerli toplama sınıflarda neler olduğunu yalnızca istediğinizden; aniden yan etkileri diğer toplamalar veya uygulama mantığını ilgili diğer olay işleyicileri yeniden yönlendirilmesini istediğiniz değil. Diğer yaklaşımlar gelişim göstermiştir nedeni bir sonraki bölümde açıklandığı gibi budur.

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>Oluşturma ve olayları gönderme için ertelenmiş yaklaşımı

Bir etki alanı olay işleyicisine hemen göndermeyi yerine etki alanı olayları bir koleksiyona eklemek için daha iyi bir yaklaşım olduğu ve bu etki alanı olayları gönderme *önceki* veya *sağ*  *sonra* (ile gibi SaveChanges EF içinde) işlemi sonlandırdı. (Bu yaklaşım Jimmy Bogard tarafından bu gönderisinde açıklanan [daha iyi bir etki alanı olayları düzeni](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Aynı işlem veya farklı işlemlerin parçası olarak yan etkileri içerecektir olup olmadığını belirler etki alanı olayları gönderip göndermeyeceğini karar vermeden önce veya sağa hareket uygulamadan sonra sağ, önemlidir. İkinci durumda, nihai tutarlılık arasında birden çok toplamalar ilgilenmeniz gereken. Bu konuda bir sonraki bölümde ele alınmıştır.

Hangi eShopOnContainers kullanan ertelenmiş yaklaşımdır. İlk olarak, bir koleksiyonu veya varlık başına olayların listesini içine varlıklarınızı içinde gerçekleşen etkinlikler ekleyin. Bu liste, varlık nesnesinin bir parçası veya bile daha iyi temel varlık sınıfınız parçası varlık temel sınıfı aşağıdaki örnekte gösterildiği gibi olmalıdır:

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

Bir olayı oluşturmak istediğinizde, bu olay toplama toplama kök varlık herhangi bir yöntemi sırasında koddan eklemeniz yeterlidir.

Aşağıdaki kod, parçası [eShopOnContainers agregate kök sipariş](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), bir örnek gösterilmektedir:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

AddDomainEvent yöntemi yaparsanız tek şey listeye olay ekleme dikkat edin. Henüz hiç olay gönderilir ve hiçbir olay işleyici henüz çağrılır.

Gerçekte veritabanına işlem yaparsanız olayları daha sonra gönderme istiyorsunuz. Entity Framework Çekirdek kullanıyorsanız, aşağıdaki kod olduğu gibi EF DbContext SaveChanges yönteminde anlamına gelir:

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
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

Bu kodu ile kendi ilgili olay işleyicileri varlık olaylarına gönderme.

(Basit bir ekleme bellekte listeye) bir etki alanı olay oluşturma bir olay işleyicisi göndermeyi gelen ayrılmış olduğunu genel sonucudur. Buna ek olarak, ne tür bir dağıtıcı kullandığınıza bağlı olarak, size olayları eşzamanlı veya zaman uyumsuz olarak gönderme.

İşlem sınırları içine önemli gelen Burada Yürüt unutmayın. İş ve işlem, birimi birden fazla toplama yayılabilir varsa (as EF çekirdek ve ilişkisel veritabanı kullanılırken), bu da çalışabilir. Ancak işlem Azure DocumentDB gibi bir NoSQL veritabanı kullanırken gibi toplamalar yayılıyorsa tutarlılık sağlamak için ek adımlar uygulamanız gerekir. Neden Kalıcılık kullanmayan Evrensel değil başka bir neden de budur; kullandığınız depolama sistemine bağlıdır.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Nihai tutarlılık toplamalar arasında karşı toplamalar arasında tek bir işlem

Sorunun olup üzerinde nihai tutarlılık bu toplamalara bağlı olan karşı toplamalar arasında tek bir işlem gerçekleştirmek tartışmalı bir adrestir. Eric Evans ve Vaughn Vernon kuralı, bir işlem advocate gibi birçok DDD yazarları bir toplama = ve bu nedenle nihai tutarlılık için toplamalar arasında karşıdır. Örneğin, kendi kitaptaki *Domain-Driven tasarım*, Eric Evans diyor bu:

Toplamalar yayılan herhangi bir kural her zaman güncel olması beklenen değil. Olay işleme, toplu işleme veya diğer güncelleştirme mekanizmaları belirli bir süre içinde başka bir bağımlılık çözülebilir. (sayfa 128)

Vaughn Vernon aşağıdakileri belirten [etkili toplama tasarımı. Bölüm II: Yapma toplayan iş birlikte](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

Bu nedenle, bir toplama örneği gerektirir ek iş kuralları bir veya daha fazla toplamalarda yürütmek bir komut yürütülürken, nihai tutarlılık kullanırsanız \[...\] Nihai tutarlılık DDD modelinde desteklemek için kullanışlı bir yol yoktur. Bir veya daha fazla zaman uyumsuz abonelere teslim saati olan bir etki alanı olay toplama yöntemi yayımlar.

Bu stratejinin yayılan birçok toplamalar veya varlıklar işlemleri yerine hassas işlemler benimsemenin temel alır. İkinci durumda, veritabanı kilit sayısı yüksek ölçeklenebilirlik gereksinimlerini ile büyük ölçekli uygulamalarında önemli olacağını olur. Yüksek düzeyde ölçeklenebilir uygulamalar birden çok toplamalar arasında anlık işlemsel tutarlılık olmaması gereken olgu benimsemenin kavramı nihai tutarlılık, kabul etme ile yardımcı olur. Atomik değişikliklerin iş tarafından gerekli genelde ve bunu her durumda belirli işlemleri atomik işlemleri olup olmadığını gereksinim söylemek için etki alanı uzmanlar sorumluluğundadır. Her zaman bir işlem birden çok toplamalar arasında atomik bir işlem gerekiyorsa, toplama daha büyük olmalıdır, veya doğru şekilde tasarlanmamış isteyebilir.

Ancak, diğer geliştiriciler ve mimarları Jimmy Bogard gibi tek bir işlem arasında birkaç toplamalar kapsayıcı ile teşkil — ancak yalnızca zaman bu ek toplamalar yan etkileri aynı özgün komutu için ilgili. Örneğin, [daha iyi bir etki alanı olayları düzeni](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard bu diyor:

Genellikle, aynı mantıksal işlem içinde olmasa da, etki alanı olayı tetiklenmeden aynı kapsamda gerçekleşmesi için bir etki alanı olayının yan etkileri istiyorum \[...\] Yalnızca şu bizim hareketi önce biz bizim olayları kendi ilgili işleyicilere gönderme.

Etki alanı olayları sağ gönderme varsa *önce* yan etkileri bu olayların aynı işlemde dahil edilmesini istediğiniz özgün işlemi sonlandırdı, demektir. EF DbContext SaveChanges yöntem başarısız olursa, örneğin, işlem ilgili etki alanı olay işleyicileri tarafından uygulanan herhangi bir yan etkisi işlem sonucu dahil olmak üzere tüm değişiklikleri geri döner. DbContext yaşam kapsamı varsayılan olarak tanımlı olduğundan bu "kapsamlıdır." Bu nedenle, DbContext nesnesi aynı kapsamı veya Nesne grafiği içinde oluşturulmasını birden çok havuz nesneleri arasında paylaşılır. Web API veya MVC uygulamaları geliştirirken HttpRequest kapsamıyla örtüşür.

Gerçekte, her iki yaklaşımın (tek bir atomik işlem ve nihai tutarlılık) doğru olabilir. Gerçekten, etki alanı veya iş gereksinimlerinize ve hangi etki alanı uzmanların size bağlıdır. Bu ayrıca nasıl ölçeklenebilir, hizmeti gereksinimlerine göre değişir (daha ayrıntılı işlemler sahip veritabanı kilitleri göre daha az etkiyle). Ve ne kadar yatırım, nihai tutarlılık, olası tutarsızlıklar toplar ve telafi izin eylemlerini uygulamak için gereken arasında saptamak amacıyla daha karmaşık kod gerektirdiğinden, kodunuzda yapmaya hazır olduğunuz üzerinde bağlıdır. Özgün toplama ve olayların ne zaman gönderilen için daha sonra değişiklikleri, olduğunu sorunu dikkate alın ve olay işleyicileri kendi yan etkileri tamamlanamaz, toplamalar arasında tutarsızlıklar olacaktır.

Telafi izin eylemlere izin vermek için bir yol özgün işlemin bir parçası olabilir ek veritabanı tablolarında etki alanı olayları depolamak için olacaktır. Daha sonra tutarsızlıklarını algılayan ve toplamalar geçerli durumuyla olayların listesini karşılaştırarak telafi izin eylemleri çalıştırır toplu işlem olabilir. Telafi izin Eylemler iş kullanıcısı ve etki alanı uzmanlarıyla birlikte ele içerir, taraftaki derin çözümleme gerektiren karmaşık bir konu bir parçasıdır.

Herhangi bir durumda, gereksinim duyduğunuz yaklaşım seçebilirsiniz. Ancak ilk yaklaşım ertelenmiş — tek bir işlem kullanmanız kaydetmeden önce olaylar oluşturma — basit EF çekirdek ve ilişkisel veritabanı kullanılırken bir yaklaşımdır. Bu uygulama daha kolay ve birçok iş durumda geçerli olur. Bu da sipariş mikro hizmet eShopOnContainers içinde kullanılan yaklaşımdır.

Ancak nasıl aslında kendi ilgili olay işleyicileri için olaylar gönderme? Nedir \_önceki örnekte bkz Dünyası nesne? Teknikleri ve olayları ve bunların olay işleyicileri arasında eşleme için kullanabileceğiniz yapıları ile yapmak sahip.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Etki alanı olay dağıtıcısının: olay işleyicilerini olaylarından eşleme

Gönderme veya olayları yayımlama sonra ilgili her işleyici alın ve bu olaya göre yan etkileri işlemek ve böylece olay yayımlayacak yapı çeşit gerekir.

Gerçek ileti sistemi veya hizmet veri yolu bellek içi olayları aksine büyük olasılıkla dayalı bile bir olay veri yolu, bunun bir yaklaşımdır. Ancak, ilk bu durum, gerçek Mesajlaşma yalnızca aynı işlem içinde olayları işlemek gerekli olduğundan, etki alanı olayları işlemek için gereğinden fazla olacaktır (diğer bir deyişle, aynı etki alanı ve uygulama katman içinde).

Birden çok olay işleyicilerine olayları eşlemek için başka bir dinamik olarak olayları gönderileceği yeri çıkarımını türleri kayıt IOC kapsayıcısında kullanarak yoludur. Diğer bir deyişle, belirli bir olay almak olay işleyicileri gerekenler bilmeniz gerekir. Şekil 9-16 basitleştirilmiş bir yaklaşım için gösterir.

![](./media/image17.png)

**Şekil 9-16**. Etki alanı olay dağıtıcısının IOC kullanma

Tüm tesisat ve bu yaklaşımı kendiniz uygulamak için yapıları oluşturabilirsiniz. Ancak, aynı zamanda gibi kullanılabilir kitaplıkları kullanabilirsiniz [MediatR](https://github.com/jbogard/MediatR), perde altında kullanan IOC kapsayıcı. Bu nedenle doğrudan önceden tanımlanmış arabirimleri ve Dünyası nesnenin yayımlama/dağıtma yöntemleri kullanabilirsiniz.

Kod içinde ilk olay işleyici türlerini, IOC kapsayıcısında kaydetmek aşağıdaki örnekte gösterildiği gibi ihtiyacınız [eShopOnContainers sıralama mikro hizmet](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kod ilk etki alanı olay işleyicileri herhangi bir işleyici tutan derleme bularak içeren derlemenin tanımlar (typeof(ValidateOrAddBuyerAggregateWhenXxxx), ancak kullanarak seçtiniz derleme bulmak için herhangi başka bir olay işleyicisini). Tüm olay işleyicileri IAsyncNotificationHandler arabirimini uygulayan olduğundan, kod sonra olanlar için yalnızca aramaları türleri ve tüm olay işleyicileri kaydeder.

### <a name="how-to-subscribe-to-domain-events"></a>Etki alanı olaylarına abone olma

MediatR kullandığınızda, aşağıdaki kodda görebileceğiniz gibi her olay işleyicisi INotificationHandler arabiriminin genel parametresinde sağlanan bir olay türü kullanmanız gerekir:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Olay ve abonelik kabul edilebilir, olay işleyici arasındaki ilişkiyi göre MediatR yapı her olay için tüm olay işleyicileri bulun ve her biri bu olay işleyicileri tetikler.

### <a name="how-to-handle-domain-events"></a>Etki alanı olayları işlemek nasıl

Son olarak, olay işleyicisi genellikle gerekli ek toplamalar edinme ve yan etkisi etki alanı mantığı yürütmek için altyapı depoları kullanan uygulama katmanı kodu uygular. Aşağıdaki [eShopOnContainers etki alanı olay işleyici kodu](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), bir uygulama örneği gösterir.

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

Altyapı depoları kullandığından önceki etki alanı olay işleyicisini altyapı Kalıcılık katmanda sonraki bölümde açıklandığı gibi uygulama katmanı kodu kabul edilir. Olay işleyicileri diğer altyapı bileşenlerini de kullanabilirsiniz.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Etki alanı olayları mikro hizmet sınırları dışında yayımlanmasını tümleştirme olaylarını oluşturulmasına neden olabilir

Son olarak, bazı durumlarda olayları arasında birden çok mikro yaymak istediğiniz belirtmeyi önemlidir. Bir tümleştirme olay kabul edilir ve herhangi bir özel etki alanı olay işleyicisini olay yolundan aracılığıyla yayınlanabilir.

## <a name="conclusions-on-domain-events"></a>Etki alanı olaylarına sonuçları

Belirtildiği gibi açıkça yan etkileri etki alanınızda değişiklikleri uygulamak için etki alanı olayları kullanın. DDD terminolojisi kullanmak için açıkça bir veya birden çok toplamalar arasında yan etkileri uygulamak için etki alanı olayları kullanın. Ayrıca, daha iyi ölçeklenebilirlik için ve veritabanı kilitleri etkisini daha az aynı etki alanındaki toplamalar arasında nihai tutarlılık kullanın.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Greg Young. Bir etki alanı olay nedir?**
    [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg. Etki alanı olayları ve nihai tutarlılık**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard. Daha iyi bir etki alanı olayları düzeni**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon. Etkin Toplama tasarımı Bölüm II: Toplamalar iş birlikte yapma**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_makaleleri/Vernon\_2011\_2. pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard. Etki alanınızı güçlendirme: etki alanı olayları**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *

-   **Tony Truong. Etki alanı olayları desen örneği**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)

-   **Udi Dahan. Etki alanı modelleri tam oluşturma kapsüllenmiş**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **Udi Dahan. Etki alanı olayları – alın 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **Udi Dahan. Etki alanı olayları – Salvation**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist. Olmayan etki alanı olayları yayınlamak için bunları döndüren!**
    [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesar de la Torre. Etki alanı olayları vs. DDD ve mikro mimarileri tümleştirme olayları**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[Önceki] (istemci-tarafı-validation.md) [sonraki] (altyapı-Kalıcılık-katman-design.md)
