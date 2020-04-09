---
title: .NET Core ile bir mikro hizmet etki alanı modeli uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | DDD yönelimli etki alanı modelinin uygulama ayrıntılarına girin.
ms.date: 10/08/2018
ms.openlocfilehash: 24f700b371d998cf99cbcf260a5278d797cb39d4
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988433"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>.NET Core ile microservice etki alanı modeli uygulayın

Bir önceki bölümde, bir etki alanı modeli tasarlamak için temel tasarım ilkeleri ve desenleri açıklanmıştır. Şimdi .NET Core (düz C\# kodu) ve EF Core kullanarak etki alanı modelini uygulamanın olası yollarını keşfetme zamanı. Etki alanı modelinizin yalnızca kodunuzdan oluşacağını unutmayın. Sadece EF Core modeli gereksinimleri olacak, ancak EF gerçek bağımlılıkları. Etki alanı modelinizde EF Core veya başka bir ORM'a zor bağımlılıklar veya referanslar olmamalıdır.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Özel .NET Standart Kitaplıkta etki alanı modeli yapısı

eShopOnContainers başvuru uygulaması için kullanılan klasör organizasyonu, uygulama için DDD modelini gösterir. Farklı bir klasör kuruluşunun uygulamanız için yapılan tasarım seçeneklerini daha net bir şekilde ilettiğini görebilirsiniz. Şekil 7-10'da görebileceğiniz gibi, sipariş etki alanı modelinde iki toplam vardır: sipariş toplamı ve alıcı toplamı. Her bir agrega, tek bir etki alanı varlığından (toplam kök veya kök varlık) oluşan bir agreganız olsa da, etki alanı varlıkları ve değer nesneleri grubudur.

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="Solution Explorer'daki Ordering.Domain projesinin ekran görüntüsü.":::
Ordering.Domain projesiiçin Solution Explorer görünümü, Her biri varlık sınıflarını, değer nesne siniflerini ve benzeri bilgileri içeren BuyerAggregate ve OrderAggregate klasörlerini içeren AggregatesModel klasörünü gösterir.
:::image-end:::

**Şekil 7-10**. eShopOnContainers sipariş microservice için etki alanı modeli yapısı

Ayrıca, etki alanı modeli katmanı, etki alanı modelinizin altyapı gereksinimleri olan depo sözleşmelerini (arabirimleri) içerir. Başka bir deyişle, bu arabirimler hangi depoları ve altyapı katmanının uygulaması gereken yöntemleri ifade eder. Depoların uygulanmasının etki alanı modeli katmanının dışına, altyapı katmanı kitaplığına yerleştirilmesi önemlidir, bu nedenle etki alanı modeli katmanı API veya Entity Framework gibi altyapı teknolojilerinden gelen sınıflar tarafından "kirlenmemiş" değildir.

Ayrıca, etki alanı varlıklarınız ve değer nesneleriniz için taban olarak kullanabileceğiniz özel taban sınıfları içeren bir [SeedWork](https://martinfowler.com/bliki/Seedwork.html) klasörü de görebilirsiniz, böylece her etki alanının nesne sınıfında gereksiz kodunuz yoktur.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Özel bir .NET Standart kitaplıkta yapı agregaları

Toplam, işlem tutarlılığı yla eşleşmek için birlikte gruplanmış bir etki alanı nesnesi kümesini ifade eder. Bu nesneler varlıkların örnekleri (biri toplam kök veya kök varlık) artı herhangi bir ek değer nesneleri olabilir.

İşlemsel tutarlılık, bir topluişlemin bir iş eyleminin sonunda tutarlı ve güncel olması nın garanti olduğu anlamına gelir. Örneğin, mikrohizmet etki alanı modelini sipariş eden eShopOnContainers'tan gelen sipariş toplamı Şekil 7-11'de gösterildiği gibi oluşturulur.

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="OrderAggregate klasörünün ve sınıflarının ekran görüntüsü.":::
OrderAggregate klasörünün ayrıntılı görünümü: Address.cs bir değer nesnesidir, IOrderRepository bir repo arabirimidir, Order.cs bir toplu köktür, OrderItem.cs bir alt varlıktır ve OrderStatus.cs bir numaralandırma sınıfıdır.
:::image-end:::

**Şekil 7-11.** Visual Studio çözümünde sipariş toplamı

Dosyaları toplu bir klasörde açarsanız, [bunun SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) klasöründe uygulandığı gibi özel bir taban sınıf veya varlık veya değer nesnesi gibi arabirim olarak nasıl işaretlendiğini görebilirsiniz.

## <a name="implement-domain-entities-as-poco-classes"></a>Etki alanı varlıklarını POCO sınıfları olarak uygulama

Etki alanı varlıklarınızı uygulayan POCO sınıfları oluşturarak .NET'te bir etki alanı modeli uygularsınız. Aşağıdaki örnekte, Sipariş sınıfı bir varlık ve aynı zamanda bir toplam kök olarak tanımlanır. Sipariş sınıfı Varlık taban sınıfından türediği için, varlıklarla ilgili ortak kodu yeniden kullanabilir. Bu temel sınıfların ve arabirimlerin etki alanı modeli projesinde sizin adınıza tanımlandığını unutmayın, bu nedenle ef gibi bir ORM'den gelen altyapı kodu değil, kodunuzdur.

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

Bunun POCO sınıfı olarak uygulanan bir etki alanı varlığı olduğunu unutmayın. Varlık Çerçeve Çekirdeği'ne veya başka bir altyapı çerçevesine doğrudan bağımlılığı yoktur. Bu uygulama DDD olması gerektiği gibi,\# sadece C kodu bir etki alanı modeli uygulayarak.

Buna ek olarak, sınıf IAggregateRoot adlı bir arayüz ile dekore edilmiştir. Bu arabirim, bazen *işaretleme arabirimi*olarak adlandırılan boş bir arabirimdir, bu arabirim sınıfının da bir toplu kök olduğunu belirtmek için kullanılır.

İşaretleme arabirimi bazen bir anti-desen olarak kabul edilir; ancak, özellikle bu arabirim gelişmekte olabilir, bir sınıf işaretlemek için temiz bir yoldur. Bir öznitelik işaretçi için diğer seçenek olabilir, ancak sınıfın üzerine bir Toplu öznitelik işaretçisi koymak yerine IAggregate arabiriminin yanındaki taban sınıf (Varlık) görmek daha hızlıdır. Bu tercihleri meselesi, her durumda.

Toplu köke sahip olmak, agrega varlıklarının tutarlılık ve iş kurallarıyla ilgili kodun çoğunun Sipariş toplu kök sınıfında yöntem olarak uygulanması gerektiği anlamına gelir (örneğin, bir Sipariş Öğesi nesnesi toplamına eklerken AddOrderItem). OrderItems nesnelerini bağımsız olarak veya doğrudan oluşturmamalı veya güncelleştirmemelisiniz; AggregateRoot sınıfı, alt varlıklarına karşı herhangi bir güncelleştirme işleminin denetimini ve tutarlılığını korumalıdır.

## <a name="encapsulate-data-in-the-domain-entities"></a>Etki Alanı Varlıklarındaki verileri kapsülle

Varlık modellerinde sık karşılaşılan bir sorun, koleksiyon gezinti özelliklerini genel olarak erişilebilir liste türleri olarak ortaya çıkarmalarıdır. Bu, herhangi bir ortak geliştiricinin, koleksiyonla ilgili önemli iş kurallarını atlayarak nesneyi geçersiz bir durumda bırakabilecek bu koleksiyon türlerinin içeriğini işlemesine olanak tanır. Bunun çözümü, ilgili koleksiyonlara salt okunur erişimi ortaya çıkarmak ve istemcilerin bunları işleme yollarını tanımlayan yöntemler açıkça sağlamaktır.

Önceki kodda, birçok özniteliklerin salt okunur veya özel olduğunu ve yalnızca sınıf yöntemleri tarafından güncelleştirilebilen olduğunu unutmayın, bu nedenle herhangi bir güncelleştirme iş etki alanı değişkenlerini ve sınıf yöntemleri içinde belirtilen mantığı dikkate alır.

Örneğin, DDD desenleri aşağıdaki aşağıdaki **leri yapmak gerekir *not* ** herhangi bir komut işleyicisi yöntemi veya uygulama katmanı sınıfından (aslında, bunu yapmak için imkansız olmalıdır):

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

Bu durumda, Ekle yöntemi yalnızca Sipariş Öğeleri koleksiyonuna doğrudan erişim ile veri eklemek için bir işlemdir. Bu nedenle, alt varlıklarla bu işlemle ilgili etki alanı mantığının, kurallarının veya doğrulamalarının çoğu uygulama katmanına (komut işleyicileri ve Web API denetleyicileri) yayılır.

Toplam kökün etrafından dolaşırsanız, toplam kök değişmezlerini, geçerliliğini veya tutarlılığını garanti edemez. Sonunda spagetti kodu veya işlem komut dosyası kodu olacaktır.

DDD modellerini izlemek için, varlıkların herhangi bir varlık özelliğinde ortak ayarlayıcıları olmamalıdır. Bir varlıktaki değişiklikler, varlıkta gerçekleştirdikleri değişiklik hakkında açık bir şekilde her yerde bulunan bir dille açık yöntemlerle yönlendirilmelidir.

Ayrıca, varlık içindeki koleksiyonlar (sipariş öğeleri gibi) salt okunur özellikler olmalıdır (AsReadOnly yöntemi daha sonra açıklanır). Yalnızca toplu kök sınıf yöntemleri veya alt varlık yöntemleri içinden güncelleştirebilirsiniz.

Sipariş toplu kökü için kodda görebileceğiniz gibi, varlığın verilerine veya alt varlıklarına karşı herhangi bir işlemin varlık sınıfındaki yöntemlerle gerçekleştirilebilmesi için tüm ayarlayıcıların özel veya en azından salt okunur dıştan olması gerekir. Bu, işlem komut dosyası kodunu uygulamak yerine tutarlılığı denetimli ve nesne yönelimli bir şekilde korur.

Aşağıdaki kod snippet Sipariş toplamına bir Sipariş Öğesi nesnesi ekleme görevini kodlamak için uygun yolu gösterir.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object's business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

Bu snippet'te, Bir OrderItem nesnesinin oluşturulmasıyla ilgili doğrulamaların veya mantığın çoğu, AddOrderItem yönteminde Sipariş toplu kökü nün denetimi altında olacaktır- özellikle doğrulamalar ve toplamdaki diğer öğelerle ilgili mantık. Örneğin, AddOrderItem'e yapılan birden çok arama sonucunda aynı ürün öğesini alabilirsiniz. Bu yöntemde, ürün öğelerini inceleyebilir ve aynı ürün öğelerini birkaç birimiçeren tek bir OrderItem nesnesi içinde birleştirebilirsiniz. Ayrıca, farklı indirim tutarları varsa ancak ürün kimliği aynıysa, büyük olasılıkla daha yüksek iskonto uygularsınız. Bu ilke, OrderItem nesnesi için başka bir etki alanı mantığı için geçerlidir.

Buna ek olarak, yeni OrderItem(params) işlemi de denetlenecek ve AddOrderItem yöntemi tarafından Sipariş toplam kökünden gerçekleştirilir. Bu nedenle, bu işlemle ilgili mantık veya doğrulamaların çoğu (özellikle diğer alt varlıklar arasındaki tutarlılığı etkileyen her şey) toplam kök içinde tek bir yerde olacaktır. Bu toplam kök deseni nihai amacıdır.

Varlık Framework Core 1.1 veya daha sonra kullandığınızda, özellikler ek olarak [alanlara eşleme](https://docs.microsoft.com/ef/core/modeling/backing-field) sağlar, çünkü bir DDD varlık daha iyi ifade edilebilir. Bu, alt varlıkların veya değer nesnelerinin koleksiyonlarını korurken yararlıdır. Bu geliştirme yle, özellikler yerine basit özel alanlar kullanabilir ve ortak yöntemlerle alan koleksiyonuna herhangi bir güncelleştirme uygulayabilir ve AsReadOnly yöntemi yle salt okunur erişim sağlayabilirsiniz.

DDD'de, herhangi bir değişmezi ve verilerin tutarlılığını denetlemek için varlığı yalnızca varlık (veya oluşturucu) yöntemleri yle güncelleştirmek istersiniz, bu nedenle özellikler yalnızca get accessor ile tanımlanır. Özellikler özel alanlar tarafından desteklenen. Özel üyelere yalnızca sınıf içinden erişilebilir. Ancak, bir istisna vardır: EF Core bu alanları da ayarlamak gerekiyor (böylece nesneyi uygun değerlerle döndürebilir).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Yalnızca veritabanı tablosundaki alanlara erişim elde eden özellikleri eşle

Özellikleri veritabanı tablo sütunlarına eşleme bir etki alanı sorumluluğu değil, altyapı ve kalıcılık katmanının bir parçasıdır. EF Core 1.1'deki yeni yeteneklerin farkında olmak için burada bundan söz ediyoruz veya daha sonra varlıkları nasıl modelleebileceğinizle ilgili. Bu konudaki ek ayrıntılar altyapı ve kalıcılık bölümünde açıklanmıştır.

EF Core 1.0 veya daha sonra kullandığınızda, DbContext içinde yalnızca getters ile tanımlanan özellikleri veritabanı tablosundaki gerçek alanlara eşleniz gerekir. Bu PropertyBuilder sınıfının HasField yöntemi ile yapılır.

### <a name="map-fields-without-properties"></a>Özellikleri olmayan alanları haritala

EF Core 1.1 veya daha sonraki özelliklerle sütunları alanlara eşlemek için özellikleri kullanmamak da mümkündür. Bunun yerine, sütunları bir tablodan alanlara eşleyebilirsiniz. Bunun için ortak kullanım örneği, varlığın dışından erişilmesi gerekmeyen bir iç durum için özel alanlardır.

Örneğin, önceki OrderAggregate kod örneğinde, `_paymentMethodId` alan gibi ayarlayıcı veya getter için ilgili özelliği olmayan birkaç özel alan vardır. Bu alan, siparişin iş mantığı içinde de hesaplanabilir ve siparişin yöntemlerinden kullanılabilir, ancak veritabanında da kalıcı olması gerekir. Yani EF Core 'da (v1.1'den beri) veritabanındaki bir sütunla ilgili bir özelliği olmayan bir alanı haritalamak için bir yol vardır. Bu, bu kılavuzun [Altyapı katmanı](ddd-oriented-microservice.md#the-infrastructure-layer) bölümünde de açıklanmıştır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Vaughn Vernon' u. DDD ve Entity Framework ile Agregaların Modelleme.** Bunun Varlık Framework Core *olmadığını* unutmayın. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman. Veri Noktaları - Etki Alanı Odaklı Tasarım için Kodlama: Veri Odaklı Devs Için İpuçları** \
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- **Udi Dahan. Tam kapsüllü Etki Alanı Modelleri nasıl oluşturulur?** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Önceki](microservice-domain-model.md)
> [Sonraki](seedwork-domain-model-base-classes-interfaces.md)
