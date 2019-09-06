---
title: .NET Core ile bir mikro hizmet etki alanı modeli uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | DDD-odaklı bir etki alanı modelinin uygulama ayrıntılarına ulaşın.
ms.date: 10/08/2018
ms.openlocfilehash: b2ad62c2a16dd3993b9624ec14f0070e934ac2de
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296758"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>.NET Core ile bir mikro hizmet etki alanı modeli uygulama

Önceki bölümde, bir etki alanı modeli tasarlamaya yönelik temel tasarım ilkeleri ve desenleri açıklanmıştı. Artık, .NET Core (düz C\# kodu) ve EF Core kullanarak etki alanı modelini uygulamak için olası yolları keşfetmeye yönelik bir zaman vardır. Etki alanı modelinizin yalnızca kodunuzun oluşyacağını unutmayın. Yalnızca EF Core model gereksinimlerine sahip olur ancak EF üzerinde gerçek bağımlılıklara sahip olmaz. Etki alanı modelinizdeki EF Core veya başka bir ORM için sabit bağımlılıklara veya başvuru içermemelidir.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Özel bir .NET Standard kitaplığındaki etki alanı model yapısı

EShopOnContainers başvuru uygulaması için kullanılan klasör organizasyonu, uygulamanın DDD modelini gösterir. Farklı bir klasör kuruluşun, uygulamanız için yapılan tasarım seçimlerini daha net bir şekilde iletişim kuracağını fark edebilirsiniz. Şekil 7-10 ' de görebileceğiniz gibi, sıralama etki alanı modelinde, sipariş toplama ve alıcı toplama olmak üzere iki toplama vardır. Her toplama, bir etki alanı varlıkları ve değer nesneleri grubudur, ancak tek bir etki alanı varlığından (Toplam kök veya kök varlık) oluşan bir toplama işlemi de olabilir.

![BuyerAggregate ve OrderAggregate klasörlerini içeren AggregatesModel klasörünü gösteren sıralama. Domain projesi için Çözüm Gezgini görünümü, her biri varlık sınıflarını, değer nesne dosyalarını ve bu şekilde devam eder. ](./media/image11.png)

**Şekil 7-10**. EShopOnContainers 'da sıralama mikro hizmeti için etki alanı model yapısı

Ayrıca, etki alanı modeli katmanı, etki alanı modelinizin altyapı gereksinimleri olan depo sözleşmelerini (arabirimler) içerir. Diğer bir deyişle, bu arabirimler hangi depoların ve altyapı katmanının uygulamanız gereken yöntemleri ifade ediyor. Depoların uygulanması, altyapı katmanı kitaplığındaki etki alanı modeli katmanının dışına yerleştirilmesi açısından önemli bir öneme sahiptir. bu nedenle, etki alanı model katmanı, Entity Framework gibi altyapı teknolojilerinde API veya sınıflar tarafından "ayrılmış" değildir.

Ayrıca, etki alanı varlıklarınız ve değer nesneleri için temel olarak kullanabileceğiniz özel temel sınıflar içeren bir [Seedwork](https://martinfowler.com/bliki/Seedwork.html) klasörü görebilirsiniz, bu nedenle her bir etki alanının nesne sınıfında gereksiz kodunuz yoktur.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Özel bir .NET Standard kitaplığındaki yapı toplamaları

Bir toplama, işlem tutarlılığını eşleştirmek için birlikte gruplanmış bir etki alanı nesneleri kümesini ifade eder. Bu nesneler, varlıkların örnekleri (biri toplam kök veya kök varlık) ve ek değer nesneleri olabilir.

İşlemsel tutarlılık, bir toplamanın bir iş eyleminin sonunda tutarlı ve güncel olmasını garanti edilir. Örneğin, eShopOnContainers sıralama mikro hizmet etki alanı modelinden sıra toplaması, Şekil 7-11 ' de gösterildiği gibi oluşturulur.

![OrderAggregate klasörünün ayrıntılı bir görünümü: Address.cs bir değer nesnesidir, ıorderrepository bir depo arabirimidir, Order.cs bir toplama köküdür, OrderItem.cs ise bir alt varlıktır ve OrderStatus.cs bir numaralandırma sınıfıdır.](./media/image12.png)

**Şekil 7-11**. Visual Studio çözümünde sıra toplaması

Bir toplama klasöründeki dosyalardan herhangi birini açarsanız, [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) klasöründe uygulandığı şekilde varlık veya değer nesnesi gibi özel bir temel sınıf veya arabirim olarak nasıl işaretlendiğini görebilirsiniz.

## <a name="implement-domain-entities-as-poco-classes"></a>POCO sınıfları olarak etki alanı varlıklarını uygulama

Etki alanı varlıklarınızı uygulayan POCO sınıfları oluşturarak .NET içinde bir etki alanı modeli uygulayabilirsiniz. Aşağıdaki örnekte, Order sınıfı bir varlık olarak ve ayrıca bir toplam kök olarak tanımlanır. Order sınıfı varlık temel sınıfından türetildiğinden, varlıklarla ilgili ortak kodu yeniden kullanabilir. Bu temel sınıfların ve arabirimlerin, etki alanı modeli projesinde sizin tarafınızdan tanımlandığını göz önünde bulundurun. bu nedenle, f gibi bir ORM 'den altyapı kodu değil kodunuz olur.

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName,
                            decimal unitPrice, decimal discount,
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);

        _orderItems.Add(orderItem);

    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

Bu, POCO sınıfı olarak uygulanan bir etki alanı varlığı olduğunu unutmamak önemlidir. Entity Framework Core veya başka bir altyapı çerçevesine doğrudan bağımlılığı yoktur. Bu uygulama, ddd, yalnızca bir etki alanı modeli uygulayan C\# koduna sahip olmalıdır.

Ayrıca, sınıfı IAggregateRoot adlı bir arabirimle birlikte tasarlanmıştır. Bu arabirim, bazen yalnızca bu varlık sınıfının de bir toplam kök olduğunu göstermek için kullanılan *boş bir arabirimdir*.

İşaretleyici arabirimi bazen bir anti-model olarak kabul edilir; Ancak, özellikle de bu arabirim gelişiyor olabileceği gibi, bir sınıfı işaretlemek için de temiz bir yoldur. Bir öznitelik, işaretleyici için diğer seçim olabilir, ancak sınıfın üzerine bir toplama özniteliği işareti koymak yerine ıaggregate arabiriminin yanındaki temel sınıfı (varlık) görmek daha hızlıdır. Bu, herhangi bir durumda tercihlerden bağımsız olur.

Toplam bir köke sahip olmak, toplamanın varlıkların tutarlılık ve iş kurallarıyla ilgili kodların büyük bir kısmının sıra toplama kök sınıfında (örneğin, toplama için bir OrderItem nesnesi eklenirken Addorderıtem) Yöntemler olarak uygulanmasıdır. . OrderItems nesnelerini bağımsız olarak veya doğrudan oluşturmanız veya güncelleştirmemelisiniz; AggregateRoot sınıfı, alt varlıklara karşı herhangi bir güncelleştirme işleminin denetimini ve tutarlılığını tutmalıdır.

## <a name="encapsulate-data-in-the-domain-entities"></a>Etki alanı varlıklarındaki verileri yalıtma

Varlık modellerindeki yaygın bir sorun, koleksiyon gezinti özelliklerini herkese açık olarak erişilebilen liste türleri olarak kullanıma sunmasıdır. Bu, tüm ortak çalışan geliştiricisinin bu koleksiyon türlerinin içeriğini işlemesini sağlar. Bu, koleksiyonda ilgili önemli iş kurallarını atlayabilir ve bu da nesneyi geçersiz bir durumda bırakabilir. Bunun çözümü, ilgili koleksiyonlara salt okuma erişimi sunmak ve istemcilerin bunları işleyebilecekleri yolları tanımlayan yöntemleri açıkça sağlamaktır.

Önceki kodda, pek çok özniteliğin salt okunurdur veya Private olduğunu ve yalnızca sınıf yöntemleri tarafından güncelleştirilebilir olduğunu, bu nedenle tüm güncelleştirmeler, iş etki alanı iç türevlerini ve sınıf yöntemleri içinde belirtilen mantığı kabul eder.

Örneğin, DDD desenlerinin ardından, herhangi bir komut işleyici yönteminden veya uygulama katmanı sınıfından **şunları yapmanız**  gerekmez (Aslında bunun sizin için imkansız olması gerekir):

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems collection directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

Bu durumda, Add yöntemi yalnızca OrderItems koleksiyonuna doğrudan erişim ile veri eklemek için bir işlemdir. Bu nedenle, alt varlıklar ile ilgili etki alanı mantığının, kuralların veya bu işlemle ilgili doğrulamaların çoğu uygulama katmanında (komut işleyicileri ve Web API denetleyicileri) yayalınacaktır.

Toplama kökünün çevresine giderseniz, toplam kök, onun geçerliliğini, geçerliliğini veya tutarlılığını garanti edemez. Sonuç olarak, istenmeyen bir kod ya da işlemsel betik kodunuz olacaktır.

DDD desenlerini izlemek için, varlıkların herhangi bir varlık özelliğinde ortak ayarlayıcılarına sahip olmaması gerekir. Bir varlıktaki değişiklikler, varlıkta gerçekleştirdikleri değişiklik hakkında açık olan açık yöntemlerle birlikte kullanılmalıdır.

Ayrıca, varlık içindeki Koleksiyonlar (Order Items gibi) salt okunur özellikler olmalıdır (daha sonra açıklanan AsReadOnly yöntemi). Yalnızca toplam kök sınıf yöntemleri veya alt varlık yöntemlerinden içinden güncelleştirme yapabilmelisiniz.

Sipariş toplama kökünün kodunda görebileceğiniz gibi, tüm ayarlayıcılar özel veya en azından Salt okunabilir olmalıdır, böylece varlığın verilerine veya alt varlıklarına karşı herhangi bir işlem varlık sınıfındaki yöntemlerle gerçekleştirilmelidir. Bu işlem, işlemsel betik kodu uygulamak yerine denetimli ve nesne odaklı bir şekilde tutarlılık sağlar.

Aşağıdaki kod parçacığı, sıra toplamasına bir OrderItem nesnesi ekleme görevini kodun doğru yolunu gösterir.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

Bu kod parçacığında, bir OrderItem nesnesinin oluşturulmasıyla ilgili doğrulamaları veya mantığın çoğu, Addorderıtem yönteminde, özellikle de toplamadaki diğer öğelerle ilgili doğrulamalar ve mantık olan sıra toplama kökünün denetimi altında olacaktır. Örneğin, birden çok Addorderıtem çağrısının sonucuyla aynı ürün öğesini elde edebilirsiniz. Bu yöntemde, ürün öğelerini inceleyebilir ve aynı ürün öğelerini birçok birim ile tek bir OrderItem nesnesi halinde birleştirebilirsiniz. Ayrıca, farklı indirim miktarları varsa ancak ürün KIMLIĞI aynıysa, büyük olasılıkla daha yüksek iskontoyu uygularsınız. Bu ilke, OrderItem nesnesinin diğer tüm etki alanı mantığına yöneliktir.

Ayrıca, yeni OrderItem (params) işlemi de düzen toplama kökünden Addorderıtem yöntemi tarafından denetlenir ve gerçekleştirilir. Bu nedenle, bu işlemle ilgili mantık veya doğrulamaların çoğu (özellikle diğer alt varlıklar arasındaki tutarlılığı etkileyen her şey), toplam kökte tek bir yerde olacaktır. Bu, toplam kök deseninin nihai amacı olur.

Entity Framework Core 1,1 veya sonraki bir sürümü kullandığınızda, özelliklere ek olarak [alanlarla eşleştirmeye](https://docs.microsoft.com/ef/core/modeling/backing-field) ızın verdiğinden ddd varlığı daha iyi ifade edilebilir. Bu, alt varlıkların veya değer nesnelerinin koleksiyonlarını koruurken yararlı olur. Bu geliştirmelerden bazıları özellikler yerine basit özel alanları kullanabilir ve genel yöntemlerde alan koleksiyonuna herhangi bir güncelleştirmeyi uygulayabilir ve AsReadOnly yöntemi aracılığıyla salt okunur erişim sağlayabilirsiniz.

DDD 'da, verilerin herhangi bir kısmını ve tutarlılığını denetlemek için yalnızca varlıktaki yöntemler aracılığıyla varlığı (veya Oluşturucu) güncellemek isteyebilirsiniz, böylece özellikler yalnızca bir get erişimcisi ile tanımlanmıştır. Özellikler özel alanlarla desteklenir. Özel üyelere yalnızca sınıfının içinden erişilebilir. Ancak, bir özel durum vardır: EF Core bu alanları da ayarlaması gerekir (Bu nedenle nesneyi doğru değerlerle döndürebilir).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Özellikleri veritabanı tablosundaki alanlara yalnızca get erişimcileri ile eşleyin

Özellikleri veritabanı tablosu sütunlarına eşleme, altyapı ve kalıcılık katmanının bir parçası olarak bir etki alanı sorumluluğu değildir. Burada, varlıkların nasıl modellemeytireceğiniz ile ilgili EF Core 1,1 veya sonraki sürümlerde yeni yetenekler hakkında farkında olmanız gerekir. Bu konuyla ilgili ek ayrıntılar altyapı ve kalıcılık bölümünde açıklanmaktadır.

EF Core 1,0 veya sonraki bir sürümü kullandığınızda, DbContext içinde, yalnızca alıcıları ile tanımlanan özellikleri veritabanı tablosundaki gerçek alanlarla eşlemeniz gerekir. Bu, PropertyBuilder sınıfının HasField yöntemiyle yapılır.

### <a name="map-fields-without-properties"></a>Özellikleri olmayan harita alanları

Sütunları alanlarla eşlemek için EF Core 1,1 veya sonraki bir sürüme sahip bir özellik ile, özellikler de kullanılamaz. Bunun yerine, sütunları yalnızca bir tablodan alanlarla eşleyebilirsiniz. Bunun için ortak kullanım örneği, varlığın dışından erişilmesi gerekmeyen iç durum için özel alanlardır.

Örneğin, önceki orderaggregate kod örneğinde, bir ayarlayıcı veya alıcı için ilgili özelliği olmayan, `_paymentMethodId` alanı gibi birkaç özel alan vardır. Bu alan Ayrıca, siparişin iş mantığı dahilinde hesaplanabilecek ve siparişin yöntemlerinden, ancak veritabanında kalıcı olması gerekir. Bu nedenle EF Core (v 1.1 ' den itibaren), ilgili bir özellik olmadan bir alanı veritabanındaki bir sütuna eşlemek için bir yol vardır. Bu, bu kılavuzun [altyapı katmanı](ddd-oriented-microservice.md#the-infrastructure-layer) bölümünde de açıklanmaktadır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Vaughn versuz. DDD ve Entity Framework ile toplamalar Modellendirme.** Bunun *Entity Framework Core olmadığına* unutmayın. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman. Veri noktaları-etki alanı odaklı tasarım için kodlama: Veri odaklı Devs ipuçları** \
  <https://msdn.microsoft.com/magazine/dn342868.aspx>

- **UDI Dahan. Tamamen kapsüllenmiş etki alanı modelleri oluşturma** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Önceki](microservice-domain-model.md)İleri
> [](seedwork-domain-model-base-classes-interfaces.md)
