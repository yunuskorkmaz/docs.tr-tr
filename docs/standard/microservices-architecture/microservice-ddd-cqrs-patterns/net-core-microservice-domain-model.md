---
title: "Mikro hizmet etki alanı modeli .NET Core ile uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet etki alanı modeli .NET Core ile uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 07a79f3d52db400d1539fb4172166cccf8905fb8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>Mikro hizmet etki alanı modeli .NET Core ile uygulama 

Önceki bölümde temel tasarım ilkeleri ve etki alanı modeli tasarlama modeller açıklandığı. .NET Core kullanarak etki alanı modeli uygulamak için olası yollarını keşfetmek şimdi (düz C\# kodu) ve EF çekirdek. Etki alanı modeli yalnızca kodunuzu oluşan unutmayın. EF üzerinde yalnızca EF çekirdek modeli gereksinimleri ancak değil gerçek bağımlılıkları gerekir. Etki alanı modelinizde sabit bağımlılıklar veya EF çekirdek veya diğer ORM başvuruları olmamalıdır.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Özel bir .NET standart Kitaplığı'nda etki alanı modeli yapısı

EShopOnContainers başvuru uygulaması için kullanılan klasör kuruluş uygulama DDD modeli gösterilmektedir. Farklı bir klasör kuruluş uygulamanız için yapılan tasarım seçenekleri daha net bir şekilde iletişim kurar bulabilirsiniz. Şekil 9-10'gördüğünüz sıralama etki alanı modelinde var. iki toplamalar, sipariş toplama ve alıcı toplama Bir tek etki alanı varlığı (Birleşik kök veya kök varlık) de oluşan bir toplama olabilir ancak her toplama etki alanı varlıkları ve değer nesnelerin grubudur.

![](./media/image11.png)

**Şekil 9-10**. EShopOnContainers içinde sıralama mikro hizmet için etki alanı modeli yapısı

Ayrıca, etki alanı modeli katmanı, etki alanı modelinin altyapı gereksinimleri olan depo sözleşmeleri (arabirimler) içerir. Diğer bir deyişle, bu arabirimleri altyapısı katmanından uygulanmalı hangi depoları express ve nasıl. Etki alanı modeli katmanı "API veya Entity Framework gibi altyapısı teknolojileri sınıflardan contaminated olmayan şekilde" depoları uygulama etki alanı modeli katmanı altyapı Katmanı kitaplığı dışında yerleştirilen önemlidir.

Ayrıca bkz bir [SeedWork](https://martinfowler.com/bliki/Seedwork.html) etki alanı varlıkları ve değeri için temel olarak kullanabileceğiniz özel temel sınıflar içeren klasörü nesneleri, her etki alanının nesne sınıfında yedekli kodu içermeyen şekilde.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Özel bir .NET standart kitaplığında toplamalar yapılandırma

Bir toplama etki alanı nesnelerini işlemsel tutarlılık eşleştirmek için bir arada gruplandırılmış bir kümeye başvuruyor. Bu nesneler (biri toplama kök veya kök varlık olan) varlıkları herhangi bir ek değer nesne olabilir.

İşlemsel tutarlılık toplama tutarlı ve bir iş eylemi sonunda güncel olması sağlanır anlamına gelir. Örneğin, Şekil 9-11'de gösterildiği gibi sipariş toplama mikro hizmet etki alanı modeli sıralama eShopOnContainers öğesinden oluşur.

![](./media/image12.png)

**Şekil 9-11**. Visual Studio çözümünde toplama sırası

Birleşik bir klasörde bulunan dosyalardan herhangi birinin açarsanız, nasıl özel bir temel sınıf ya da varlık veya değer nesnesi gibi arabirimi olarak işaretlenmiş uygulanan gibi gördüğünüz [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) klasör.

## <a name="implementing-domain-entities-as-poco-classes"></a>Etki alanı varlıklar POCO sınıflarını uygulama

Etki alanı varlıklarınızı uygulamak POCO sınıfları oluşturarak .NET içinde bir etki alanı modeli uygular. Aşağıdaki örnekte, sipariş sınıfı bir varlık ve ayrıca bir toplama kök olarak tanımlanır. Sipariş sınıfı varlık temel sınıfından türetilen çünkü varlıklarla ilgili ortak kodun yeniden kullanabilirsiniz. Bu nedenle kodu, olmayan bir ORM EF gibi altyapı kod bu temel sınıflar ve arabirimler sizin tarafınızdan etki alanı modeli projesi tanımlandığından emin aklınızda size aittir.

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

Bu bir POCO sınıfı olarak uygulanan bir etki alanı varlığı olduğunu dikkate almak önemlidir. Entity Framework Çekirdek doğrudan bağımlılıkları veya başka bir altyapı framework yok. GGG, yalnızca C olması gerektiği kadar bu uygulamasıdır\# etki alanı modeli uygulama kodu.

Ayrıca, sınıf IAggregateRoot adlı bir arabirim ile donatılmış. Bu arabirim bazen adlı boş bir arabirim olduğundan bir *işaret arabirimi*, yani yalnızca bu varlık sınıfı ayrıca bir toplama kök olduğunu göstermek için kullanılır.

Bir işaretçi arabirimi bazen koruma deseni olarak değerlendirilir. Ancak, bu da bu arabirimi özellikle gelişen sonra bir sınıf olarak işaretlemek için bir temiz yoludur. Bir öznitelik işaret için diğer seçim olabilir, ancak bir toplama özniteliği işaretleyici sınıfı yukarıda koyma yerine IAggregate arabirimi yanındaki taban sınıfı (varlık) görmek hızlıdır. Metter Tercihler, herhangi bir durumda değil.

Bu kod çoğunu tutarlılık için ilgili iş kuralları toplama 's varlıkların sipariş toplama kök sınıfı (toplama ÖgeSipariş nesneyi eklerken, örneğin, AddOrderItem) yöntemleri olarak uygulanmalıdır bir toplama kök anlamına sahip . Oluşturma veya gerekir OrderItems nesneleri bağımsız olarak veya doğrudan güncelleştirme; AggregateRoot sınıfı, Denetim ve onun alt varlıkları karşı herhangi bir güncelleştirme işlemi tutarlılığını tutmanız gerekir.

## <a name="encapsulating-data-in-the-domain-entities"></a>Etki alanı varlıklardaki veri şifreleme

Bir ortak varlık modelleri koleksiyon Gezinti özellikleri genel olarak erişilebilir liste türleri olarak kullanıma sorunudur. Bu, büyük olasılıkla nesnesi geçersiz bir durumda bırakarak, koleksiyonla ilgili önemli iş kurallarını atlamak, bu koleksiyon türleri, içeriğini işlemek herhangi bir ortak çalışanı Geliştirici sağlar. Bu çözüme olduğu ilgili koleksiyonlar salt okunur erişimi kullanıma ve açıkça istemcileri işleyebileceğiniz bunları yolları tanımlayan yöntemleri sağlar.

Önceki kodda birçok öznitelikleri salt okunur veya özel bağlıdır ve yalnızca bu nedenle her güncelleştirme hesap iş etki alanı invariants ve sınıf yöntemlerini içinde belirtilen mantığı alır sınıfı yöntemleri tarafından güncelleştirilebilir unutmayın.

Örneğin, DDD düzenleri, aşağıdakileri yapmalısınız *değil* herhangi bir sınıftan komut işleyici yöntemi veya uygulama katmanı aşağıdakileri yapın:

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

Bu durumda, ekleme yöntemi OrderItems koleksiyona doğrudan erişimi olan veri eklemek için yalnızca bir işlemidir. Bu nedenle, etki alanı mantığı, kurallar veya doğrulamaları en alt varlıkları işlemiyle uygulama katmanı (komut işleyicileri ve Web API denetleyicilerinin) yayılan ilgili.

Toplama kök giderseniz, toplama kök kendi invariants, kendi geçerlilik ya da kendi tutarlılığı garanti edemez. Sonunda spaghetti kod veya işlem bir kod sahip olur.

DDD desenleri izlemek için varlıkları ortak ayarlayıcılar herhangi bir varlık özellik olmaması gerekir. Bir varlık değişiklikleri varlıkta performans gösterdiğini değişikliği açık bulunabilen dil açık yöntemleriyle yönlendirilir.

Ayrıca, varlık (örneğin, sipariş öğeleri) içindeki koleksiyonlar salt okunur özellikler olmalıdır (daha sonra AsReadOnly yöntemi açıklanmıştır). Birleşik kök sınıf yöntemlerini ya da alt varlık yöntemleri içinde yalnızca güncelleştirmeniz.

Sipariş toplama kök kodunda görebileceğiniz gibi varlık sınıfı yöntemleri aracılığıyla gerçekleştirilmek üzere varlığın veri ya da kendi alt varlıkları karşı herhangi bir işlem sahip olması tüm ayarlayıcılar harici olarak özel veya salt okunur en az olmalıdır. Bu işlem komut dosyası kod uygulama yerine denetimli ve nesne yönelimli bir yolla tutarlılık tutar.

Aşağıdaki kod parçacığını sipariş toplama ÖgeSipariş nesne ekleme görevini kod için uygun şekilde gösterir.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

Bu parçacığında, sipariş toplama kök denetiminde doğrulamaları ya da bir ÖgeSipariş nesnesinin oluşturulmasını ilişkili mantığını çoğu olacaktır — AddOrderItem yönteminde — özellikle doğrulamaları ve mantığı ilgili diğer öğelere toplama. Örneğin, AddOrderItem için birden fazla çağrı sonucunu ile aynı ürün alabilirsiniz. Bu yöntemde, ürün öğeleri inceleyin ve birkaç birimleri ile tek bir ÖgeSipariş nesne aynı ürün öğeleri birleştirir. Ayrıca, farklı iskonto tutarlarının vardır, ancak ürün kimliği aynı olduğundan, büyük olasılıkla daha yüksek indirim uygular. Bu ilkeyi ÖgeSipariş nesne için başka bir etki alanı mantığı uygular.

Ayrıca, yeni OrderItem(params) işlemi de denetimli ve olması sipariş toplama kök AddOrderItem yöntemi tarafından gerçekleştirilen. Bu nedenle, mantığı ya da doğrulamaları çoğunu işlemi (özellikle her şey, diğer alt varlıklar arasında tutarlılığı etkiler) toplama kök içinde tek bir yerde olacağını ilgili. Birleşik kök düzeni nihai amacı olmasıdır.

Entity Framework Çekirdek 1.1 veya kullandığınızda, izin verdiğinden daha sonra bir DDD varlık daha iyi ifade edilebilir [alanlarına eşleme](https://docs.microsoft.com/ef/core/modeling/backing-field) özellikleri yanı sıra. Bu, alt varlıkları veya değer nesnelerini koleksiyonları korurken faydalı olur. Bu geliştirme ile özellikleri yerine basit özel alanlar kullanabilirsiniz ve herhangi bir güncelleştirme alan koleksiyonuna ortak yöntemleri uygulamak ve AsReadOnly yöntemi aracılığıyla salt okunur erişim sağlar.

Yöntemleri herhangi değişmeyen ve veri tutarlılığını denetlemek için varlık (veya oluşturucusu) aracılığıyla yalnızca varlık güncelleştirmek istediğiniz GGG böylece yalnızca bir get erişimcisine özellikleri tanımlanır. Özellikler özel alanları tarafından desteklenir. Özel üyelerin yalnızca sınıf içinde erişilebilir. Ancak, burada bir özel durum: EF çekirdek de bu alanları ayarlayın gerekiyor.


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Eşleme özellikleri yalnızca alanları veritabanı tablosunda get erişimcileri

Veritabanı tablo sütunları eşleme özellikleri bir etki alanı sorumluluğu ancak altyapı ve kalıcılığı katmanının bir parçası değil. Biz bu burada EF çekirdek 1.1'nda yeni özelliklerden haberdar; bu nedenle yalnızca ya da daha sonra ilgili varlıklar nasıl modellemek için Bahsediyor. Bu konu hakkında daha fazla ayrıntı altyapı ve kalıcılığı bölümünde açıklanmıştır.

DbContext içinde EF çekirdek 1.0 kullandığınızda, yalnızca veritabanı tablosunun gerçek alanlarla alıcıları ile tanımlanmış özellikleri eşlemek gerekir. Bu DataGrid'i sınıfı HasField yöntemi ile gerçekleştirilir.

### <a name="mapping-fields-without-properties"></a>Özellikleri olmayan alanlarını eşleme

Sütunları alanlarına eşlemek için özellikle EF çekirdek 1.1 veya sonraki sürümlerde, ayrıca özellikleri kullanmamayı mümkündür. Bunun yerine, yalnızca bir tablodaki sütunların alanlara eşleyebilirsiniz. Bu genel bir kullanım örneği özel alanlar için varlık erişilecek gerekmez bir iç durum modudur.

Örneğin, önceki OrderAggregate kod örneğinde, birkaç özel alanlar vardır, gibi `_paymentMethodId` ayarlayıcı veya alıcı için ilgili bir özellik olan alan. Bu alan de sipariş iş mantığı içinde hesaplanan ve sipariş yöntemleri kullanılır, ancak veritabanında kalıcı hale getirmek gerekiyor. Bu nedenle EF çekirdek (itibaren v1.1) içinde ilişkili bir özellik olmayan bir alan veritabanında bir sütunun eşlemek için bir yolu yoktur. Bu ayrıca içinde açıklanan [altyapısı katmanından](#the-infrastructure-layer) başlığına bakın.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Vaughn Vernon. Toplamalar DDD ve Entity Framework ile modelleme.** Bu Not *değil* Entity Framework Çekirdek.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Etki alanı Odaklı Tasarım kodlama: Veri odaklı Devs için ipuçları**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **UDI Dahan. Etki alanı modelleri tam oluşturma kapsüllenmiş**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Önceki] (mikro hizmet-etki-model.md) [sonraki] (seedwork-domain-model-base-classes-interfaces.md)
