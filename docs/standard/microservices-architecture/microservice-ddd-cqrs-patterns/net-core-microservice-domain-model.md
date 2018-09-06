---
title: .NET Core ile mikro hizmet etki alanı modeli uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET Core ile mikro hizmet etki alanı modeli uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: bb11d87cacf5bb6cbc980c879b0c42fae76f6246
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032468"
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>.NET Core ile mikro hizmet etki alanı modeli uygulama 

Önceki bölümde açıklanan temel tasarım ilkeleri ve etki alanı modeli tasarlamaya yönelik Desenler. .NET Core kullanarak etki alanı modeli uygulamak için kullanılabilecek yöntemler keşfedin artık (düz C\# kod) ve EF Core. Etki alanı modeliniz basitçe kodunuzu oluşan unutmayın. EF üzerinde yalnızca EF Core model gereksinimleri ancak değil gerçek bağımlılıkları olacaktır. Etki alanı modelinizdeki sabit bağımlılıkları veya EF Core veya diğer bir ORM olmamalıdır.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Özel bir .NET Standard Kitaplığı'nda etki alanı modeli yapısı

Hizmetine başvuru uygulaması için kullanılan klasör kuruluş uygulama DDD modelini gösterir. Farklı bir klasöre kuruluş uygulamanız için tasarım seçimlerinizi daha net bir şekilde iletişim kuran bulabilirsiniz. Şekil 9-10'da görüldüğü gibi sıralama etki alanı modeli içinde var. iki toplamlar, sipariş toplama ve alıcı toplama Bir tek etki alanı varlığı (toplama kök veya kök varlık) de oluşan bir toplama sahip, ancak her toplam değer nesneleri ile etki alanı varlıklarının ve grubudur.

![](./media/image11.png)

**Şekil 9-10**. Sıralama mikro hizmetine için etki alanı modeli yapısı

Ayrıca, etki alanı model katmanında, etki alanı modelinin altyapı gereksinimleri olan depo anlaşmalar (arabirimler) içerir. Bu arabirimler altyapı katmanını uygulanmalı hangi depoları başka bir deyişle, express ve nasıl. Etki alanı model katmanında "API veya Entity Framework gibi altyapı teknolojilerine sınıflardan contaminated değil için" depoları uygulamasını etki alanı model katmanında altyapı katman kitaplığı dışında yerleştirilmiş önemlidir.

Ayrıca bkz bir [SeedWork](https://martinfowler.com/bliki/Seedwork.html) etki alanı varlıklarının ve değer için bir temel olarak kullanan özel temel sınıflar içeren klasörü nesneler, her etki alanının nesne sınıfında gereksiz kod zorunda kalmazsınız.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Özel bir .NET Standard kitaplığı toplamalar yapılandırma

Toplama işlem tutarlılığı eşleştirilecek gruplanmış etki alanı nesnelerini bir kümeye başvuruyor. Bu nesneler (biri toplama kök veya kök varlık olan) varlıklar örneklerini herhangi bir ek değer nesnesi olabilir.

İşlemsel tutarlılık, bir toplama tutarlı ve bir iş eylemi sonunda güncel olması sağlanır anlamına gelir. Örneğin, mikro hizmet etki alanı modeli sıralama hizmetine sipariş toplam Şekil 9-11'de gösterildiği gibi oluşur.

![](./media/image12.png)

**Şekil 9-11**. Visual Studio çözümü içinde toplama sırası

Birleşik bir klasörde bulunan dosyalardan herhangi biri açarsanız, nasıl özel bir temel sınıf veya arabirim, varlık veya değer nesnesi olarak işaretlenmiş içinde uygulandığı şekilde gördüğünüz [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) klasör.

## <a name="implementing-domain-entities-as-poco-classes"></a>Uygulama etki alanı varlıklarının POCO sınıflar olarak

. NET'te, etki alanı varlıklarınızı uygulayan POCO sınıflar oluşturarak bir etki alanı modeli uygular. Aşağıdaki örnekte sipariş sınıfı bir varlık olarak ve ayrıca bir toplama kök olarak tanımlanır. Sipariş sınıfı varlık temel sınıftan türetildiğinden, varlıkla ilgili ortak kodun yeniden kullanabilirsiniz. Unutmayın, bu nedenle, kod, olmayan bir ORM EF gibi altyapı kodunu bu sınıflar ve arabirimler sizin tarafınızdan etki alanı model projesinde tanımlandığından emin size aittir.

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

POCO sınıfı olarak uygulanan bir etki alanı varlığı olduğuna dikkat edin önemlidir. Entity Framework Core doğrudan bağımlılıkları veya herhangi bir altyapı çerçeveyi yok. DDD, yalnızca C olması gerektiği gibi bu uygulamasıdır\# bir etki alanı modeli uygulama kodu.

Ayrıca, sınıf IAggregateRoot adlı bir arabirim ile sunulur. Bu arabirim bazen adlı boş bir arabirim olduğundan bir *işaret arabirimi*, yani yalnızca bu varlık sınıfı bir toplama kök olduğunu belirtmek için kullanılır.

Bir işaretleyici arabirimi bazen önleyici bir deseni olarak kabul edilir; Ancak, bu da özellikle arabirimin gelişen, bir sınıfı işaretlemek için bir temiz yoludur. Bir öznitelik işaretçisi için diğer bir seçenek olabilir, ancak temel sınıfı (varlık) yerine sınıf üzerinde bir toplama özniteliği işaret IAggregate arabirimi yanındaki bkz daha hızlıdır. Tercihleri sağlasa da her durumda olur.

Tutarlılık için kodun en ilgili ve toplama'nın varlık iş kuralları sipariş toplama kök sınıfı (Orderıtem nesnesi için toplama eklerken gibi AddOrderItem) yöntemleri olarak uygulanması gereken bir toplama kök yol sahip . Size oluşturamadı veya güncelleştiremedi OrderItems nesneleri bağımsız olarak veya doğrudan; AggregateRoot sınıfı, Denetim ve onun alt varlıklar karşı herhangi bir güncelleştirme işlem tutarlılığını tutmanız gerekir.

## <a name="encapsulating-data-in-the-domain-entities"></a>Etki alanı varlıklarda veri şifreleme

Koleksiyon Gezinti özellikleri genel olarak erişilebilir liste türleri olarak ortaya varlık modelleri yaygın görülen bir sorun var. Bu, büyük olasılıkla Nesne geçersiz bir durumda bırakarak koleksiyona ilgili önemli iş kuralları kullanmayan, bu koleksiyon türleri, içeriğini işlemek herhangi bir ortak çalışanı Geliştirici sağlar. Bu salt okunur erişim için ilgili koleksiyonları ve açıkça istemcileri işleyebileceğiniz bunları yolları tanımlayan yöntemleri sağlar çözümüdür.

Önceki kodda, birçok öznitelikleri salt okunur veya özel ve yalnızca bu nedenle her hesap iş etki alanı okuduğunuzda ve mantıksal sınıfı yöntemler içinde belirtilen güncelleştirme alan sınıfı yöntemleri tarafından güncelleştirilebilir unutmayın.

Örneğin, DDD deseni, aşağıdakileri yapmalısınız *değil* herhangi bir sınıftan komut işleyicisi yöntemi veya uygulama katmanı aşağıdakileri yapın:

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

Bu durumda, Add yöntemi OrderItems koleksiyona doğrudan erişimi olan bir veri eklemek için yalnızca bir işlemidir. Bu nedenle, etki alanı mantığı, kurallar veya doğrulamaları çoğu işlemi alt varlıklar ile uygulama katmanı arasında (komut işleyicileri ve Web APİ'si denetleyicilerinin) yayılacak ilgili.

Toplama kök giderseniz, toplama kök kendi okuduğunuzda, geçerliliğini veya kendi tutarlılığı garanti edemez. Sonunda spaghetti kodu veya işlem bir kod olacaktır.

DDD desenlerini izlemek için varlıklar genel ayarlayıcılar içinde herhangi bir varlık özelliği olmaması gerekir. Bir varlıktaki değişiklikleri varlıkta gerçekleştirdiği değişikliği hakkında açık bulunabilen diliyle açık yöntemlerle dikkate alınmalıdır.

Ayrıca, (örneğin sırada öğeleri) varlık koleksiyon salt okunur özellikler olmalıdır (daha sonra AsReadOnly yöntemi açıklanmıştır). Alt varlık yöntemlerini veya toplama kök sınıfı yöntemleri içinde yalnızca güncelleştirmeniz.

Sipariş toplama kök kodunda gördüğünüz gibi varlık sınıfı yöntemleri aracılığıyla gerçekleştirilmek üzere herhangi bir işlem varlığın verilerine ya da kendi alt varlıklar karşı sahip olacak şekilde tüm ayarlayıcılar dışarıdan, özel veya en azından salt okunur olmalıdır. Bu işlem kod uygulamak yerine denetimli ve nesne yönelimli bir şekilde tutarlılığı korur.

Aşağıdaki kod parçacığı, Orderıtem nesne için sipariş toplama ekleme görevini kod en uygun yolu gösterir.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

Bu kod parçacığında, çoğu doğrulamaları veya Orderıtem nesneyi oluşturulmasını ilgili mantıksal sırası toplama kök denetimi altında olacaktır — AddOrderItem yönteminde — özellikle doğrulamaları ve mantıksal ilgili diğer öğelere toplama. Örneğin, birden çok çağrı AddOrderItem sonucu ile aynı ürün alabilirsiniz. Bu yöntemde, ürün öğeleri inceleyin ve aynı ürün öğeleri birkaç birimleri ile tek bir Orderıtem nesne birleştirir. Ek olarak, farklı indirim miktarları vardır, ancak ürün kimliği aynı olan, büyük olasılıkla daha yüksek indirim uygulanacak. Bu ilke, Orderıtem nesne için başka bir etki alanı mantığı uygular.

Ayrıca, yeni OrderItem(params) işlemi ayrıca denetlenen ve sipariş toplama kökünden AddOrderItem yöntemi tarafından gerçekleştirilen. Bu nedenle, çoğu mantığı veya doğrulama işlemi (özellikle her şey, diğer alt varlıklar arasında tutarlılık etkiler), toplama kök içinde tek bir yerde olacaktır ilgili. Ultimate amacı, toplama kök desen olmasıdır.

Entity Framework Core 1.1 veya kullandığınızda bu izin verdiğinden daha sonra bir DDD varlık daha iyi ifade edilebilir [alanlarına eşleme](https://docs.microsoft.com/ef/core/modeling/backing-field) ek özellikler. Bu, alt varlıklar değer nesneleri ve koleksiyonları korurken kullanışlıdır. Bu geliştirme ile basit özel alanları yerine özellikleri kullanın ve alan koleksiyonu için herhangi bir güncelleştirme genel yöntemleri uygulayan ve AsReadOnly yöntemi aracılığıyla salt okunur erişim sağlar.

Herhangi bir değişmez değer ve veri tutarlılığını denetlemek için varlık (veya Oluşturucu) yöntemleri aracılığıyla yalnızca varlık güncelleştirmek istediğiniz DDD içinde bu nedenle özellikleri yalnızca bir alma erişimcisi ile tanımlanır. Özel alanlarla özellikleri desteklenir. Özel üyeler yalnızca sınıfın içinden erişilebilir. Bununla birlikte, burada bir özel durum: EF Core de bu alanları ayarlayın gerekir.


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Eşleme özellikleri yalnızca alanları veritabanı tablosu, get erişimcileri

Veritabanı tablo sütunları özellikleri eşleme bir etki alanı sorumluluğu ancak altyapı ve Kalıcılık katmanının bir parçası değil. Biz, bunu buradan EF Core 1.1 yeni özelliklerin farkında olduklarından yalnızca veya varlıkların nasıl model daha sonra ilgili bahsedebilirsiniz. Bu konu hakkında daha fazla ayrıntı altyapı ve Kalıcılık bölümünde açıklanmıştır.

DbContext içinde EF Core 1.0 kullandığınızda, yalnızca veritabanı tablosundaki gerçek alanlara alıcıları ile tanımlanmış özellikler eşleşmesi gerekir. Bu DataGrid'i sınıfının HasField yöntemi ile gerçekleştirilir.

### <a name="mapping-fields-without-properties"></a>Özellikleri olmayan alanlarını eşleme

Alanlarına sütunları eşlemek için özelliğiyle EF Core 1.1 veya daha sonra da özelliklerini kullanmayı mümkündür. Bunun yerine, yalnızca bir tablodaki sütunların alanlarına eşleyebilirsiniz. Bu yaygın bir kullanım durumu dışında varlık erişilmesi gerekmeyen bir iç durum için özel alanlar var.

Örneğin, önceki OrderAggregate kod örneğinde, birkaç özel alanlar vardır, gibi `_paymentMethodId` ilgili özellik alıcı veya ayarlayıcı için olan alan. Bu alan ayrıca sipariş iş mantığı içinde hesaplanan ve sipariş yöntemleri kullanılır, ancak veritabanında kalıcı hale getirmek gerekir. Bu nedenle EF Core (itibaren v1.1) içinde bir veritabanı sütununa ilgili özelliği olmayan bir alan eşlemek için bir yolu yoktur. Bu da açıklanan [altyapı katmanını](#the-infrastructure-layer) başlığına.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Vaughn Vernon. Toplamlar DDD ve Entity Framework ile model.** Bu Not *değil* Entity Framework Core.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Etki alanı odaklı tasarım için kodlama: Veri odaklı geliştiriciler için ipuçları**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **UDI Dahan. Etki alanı modellerini oluşturma tam olarak kapsüllenmiş**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Önceki](microservice-domain-model.md)
[İleri](seedwork-domain-model-base-classes-interfaces.md)
