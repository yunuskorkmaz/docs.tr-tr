---
title: Mikro hizmet etki alanı modeli .NET Core ile uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet etki alanı modeli .NET Core ile uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: e0c931405b8b7e3b52bdcbd511737b449dc74273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579569"
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="f41ae-103">Mikro hizmet etki alanı modeli .NET Core ile uygulama</span><span class="sxs-lookup"><span data-stu-id="f41ae-103">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="f41ae-104">Önceki bölümde temel tasarım ilkeleri ve etki alanı modeli tasarlama modeller açıklandığı.</span><span class="sxs-lookup"><span data-stu-id="f41ae-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="f41ae-105">.NET Core kullanarak etki alanı modeli uygulamak için olası yollarını keşfetmek şimdi (düz C\# kodu) ve EF çekirdek.</span><span class="sxs-lookup"><span data-stu-id="f41ae-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="f41ae-106">Etki alanı modeli yalnızca kodunuzu oluşan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f41ae-106">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="f41ae-107">EF üzerinde yalnızca EF çekirdek modeli gereksinimleri ancak değil gerçek bağımlılıkları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="f41ae-108">Etki alanı modelinizde sabit bağımlılıklar veya EF çekirdek veya diğer ORM başvuruları olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="f41ae-109">Özel bir .NET standart Kitaplığı'nda etki alanı modeli yapısı</span><span class="sxs-lookup"><span data-stu-id="f41ae-109">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="f41ae-110">EShopOnContainers başvuru uygulaması için kullanılan klasör kuruluş uygulama DDD modeli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="f41ae-111">Farklı bir klasör kuruluş uygulamanız için yapılan tasarım seçenekleri daha net bir şekilde iletişim kurar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f41ae-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="f41ae-112">Şekil 9-10'gördüğünüz sıralama etki alanı modelinde var. iki toplamalar, sipariş toplama ve alıcı toplama</span><span class="sxs-lookup"><span data-stu-id="f41ae-112">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="f41ae-113">Bir tek etki alanı varlığı (Birleşik kök veya kök varlık) de oluşan bir toplama olabilir ancak her toplama etki alanı varlıkları ve değer nesnelerin grubudur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="f41ae-114">**Şekil 9-10**.</span><span class="sxs-lookup"><span data-stu-id="f41ae-114">**Figure 9-10**.</span></span> <span data-ttu-id="f41ae-115">EShopOnContainers içinde sıralama mikro hizmet için etki alanı modeli yapısı</span><span class="sxs-lookup"><span data-stu-id="f41ae-115">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="f41ae-116">Ayrıca, etki alanı modeli katmanı, etki alanı modelinin altyapı gereksinimleri olan depo sözleşmeleri (arabirimler) içerir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-116">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="f41ae-117">Diğer bir deyişle, bu arabirimleri altyapısı katmanından uygulanmalı hangi depoları express ve nasıl.</span><span class="sxs-lookup"><span data-stu-id="f41ae-117">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="f41ae-118">Etki alanı modeli katmanı "API veya Entity Framework gibi altyapısı teknolojileri sınıflardan contaminated olmayan şekilde" depoları uygulama etki alanı modeli katmanı altyapı Katmanı kitaplığı dışında yerleştirilen önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-118">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="f41ae-119">Ayrıca bkz bir [SeedWork](https://martinfowler.com/bliki/Seedwork.html) etki alanı varlıkları ve değeri için temel olarak kullanabileceğiniz özel temel sınıflar içeren klasörü nesneleri, her etki alanının nesne sınıfında yedekli kodu içermeyen şekilde.</span><span class="sxs-lookup"><span data-stu-id="f41ae-119">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="f41ae-120">Özel bir .NET standart kitaplığında toplamalar yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f41ae-120">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="f41ae-121">Bir toplama etki alanı nesnelerini işlemsel tutarlılık eşleştirmek için bir arada gruplandırılmış bir kümeye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="f41ae-121">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="f41ae-122">Bu nesneler (biri toplama kök veya kök varlık olan) varlıkları herhangi bir ek değer nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-122">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="f41ae-123">İşlemsel tutarlılık toplama tutarlı ve bir iş eylemi sonunda güncel olması sağlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-123">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="f41ae-124">Örneğin, Şekil 9-11'de gösterildiği gibi sipariş toplama mikro hizmet etki alanı modeli sıralama eShopOnContainers öğesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-124">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="f41ae-125">**Şekil 9-11**.</span><span class="sxs-lookup"><span data-stu-id="f41ae-125">**Figure 9-11**.</span></span> <span data-ttu-id="f41ae-126">Visual Studio çözümünde toplama sırası</span><span class="sxs-lookup"><span data-stu-id="f41ae-126">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="f41ae-127">Birleşik bir klasörde bulunan dosyalardan herhangi birinin açarsanız, nasıl özel bir temel sınıf ya da varlık veya değer nesnesi gibi arabirimi olarak işaretlenmiş uygulanan gibi gördüğünüz [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) klasör.</span><span class="sxs-lookup"><span data-stu-id="f41ae-127">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="f41ae-128">Etki alanı varlıklar POCO sınıflarını uygulama</span><span class="sxs-lookup"><span data-stu-id="f41ae-128">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="f41ae-129">Etki alanı varlıklarınızı uygulamak POCO sınıfları oluşturarak .NET içinde bir etki alanı modeli uygular.</span><span class="sxs-lookup"><span data-stu-id="f41ae-129">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="f41ae-130">Aşağıdaki örnekte, sipariş sınıfı bir varlık ve ayrıca bir toplama kök olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-130">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="f41ae-131">Sipariş sınıfı varlık temel sınıfından türetilen çünkü varlıklarla ilgili ortak kodun yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f41ae-131">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="f41ae-132">Bu nedenle kodu, olmayan bir ORM EF gibi altyapı kod bu temel sınıflar ve arabirimler sizin tarafınızdan etki alanı modeli projesi tanımlandığından emin aklınızda size aittir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-132">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

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

<span data-ttu-id="f41ae-133">Bu bir POCO sınıfı olarak uygulanan bir etki alanı varlığı olduğunu dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-133">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="f41ae-134">Entity Framework Çekirdek doğrudan bağımlılıkları veya başka bir altyapı framework yok.</span><span class="sxs-lookup"><span data-stu-id="f41ae-134">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="f41ae-135">GGG, yalnızca C olması gerektiği kadar bu uygulamasıdır\# etki alanı modeli uygulama kodu.</span><span class="sxs-lookup"><span data-stu-id="f41ae-135">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="f41ae-136">Ayrıca, sınıf IAggregateRoot adlı bir arabirim ile donatılmış.</span><span class="sxs-lookup"><span data-stu-id="f41ae-136">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="f41ae-137">Bu arabirim bazen adlı boş bir arabirim olduğundan bir *işaret arabirimi*, yani yalnızca bu varlık sınıfı ayrıca bir toplama kök olduğunu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-137">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="f41ae-138">Bir işaretçi arabirimi bazen koruma deseni olarak değerlendirilir. Ancak, bu da bu arabirimi özellikle gelişen sonra bir sınıf olarak işaretlemek için bir temiz yoludur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-138">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="f41ae-139">Bir öznitelik işaret için diğer seçim olabilir, ancak bir toplama özniteliği işaretleyici sınıfı yukarıda koyma yerine IAggregate arabirimi yanındaki taban sınıfı (varlık) görmek hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-139">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="f41ae-140">Metter Tercihler, herhangi bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="f41ae-140">It is a metter of preferences, in any case.</span></span>

<span data-ttu-id="f41ae-141">Bu kod çoğunu tutarlılık için ilgili iş kuralları toplama 's varlıkların sipariş toplama kök sınıfı (toplama ÖgeSipariş nesneyi eklerken, örneğin, AddOrderItem) yöntemleri olarak uygulanmalıdır bir toplama kök anlamına sahip .</span><span class="sxs-lookup"><span data-stu-id="f41ae-141">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="f41ae-142">Oluşturma veya gerekir OrderItems nesneleri bağımsız olarak veya doğrudan güncelleştirme; AggregateRoot sınıfı, Denetim ve onun alt varlıkları karşı herhangi bir güncelleştirme işlemi tutarlılığını tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-142">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulating-data-in-the-domain-entities"></a><span data-ttu-id="f41ae-143">Etki alanı varlıklardaki veri şifreleme</span><span class="sxs-lookup"><span data-stu-id="f41ae-143">Encapsulating data in the Domain Entities</span></span>

<span data-ttu-id="f41ae-144">Bir ortak varlık modelleri koleksiyon Gezinti özellikleri genel olarak erişilebilir liste türleri olarak kullanıma sorunudur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-144">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="f41ae-145">Bu, büyük olasılıkla nesnesi geçersiz bir durumda bırakarak, koleksiyonla ilgili önemli iş kurallarını atlamak, bu koleksiyon türleri, içeriğini işlemek herhangi bir ortak çalışanı Geliştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="f41ae-145">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="f41ae-146">Bu çözüme olduğu ilgili koleksiyonlar salt okunur erişimi kullanıma ve açıkça istemcileri işleyebileceğiniz bunları yolları tanımlayan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f41ae-146">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="f41ae-147">Önceki kodda birçok öznitelikleri salt okunur veya özel bağlıdır ve yalnızca bu nedenle her güncelleştirme hesap iş etki alanı invariants ve sınıf yöntemlerini içinde belirtilen mantığı alır sınıfı yöntemleri tarafından güncelleştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f41ae-147">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update takes into account business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="f41ae-148">Örneğin, DDD düzenleri, aşağıdakileri yapmalısınız *değil* herhangi bir sınıftan komut işleyici yöntemi veya uygulama katmanı aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="f41ae-148">For example, following DDD patterns, you should *not* do the following from any command handler method or application layer class:</span></span>

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

<span data-ttu-id="f41ae-149">Bu durumda, ekleme yöntemi OrderItems koleksiyona doğrudan erişimi olan veri eklemek için yalnızca bir işlemidir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-149">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="f41ae-150">Bu nedenle, etki alanı mantığı, kurallar veya doğrulamaları en alt varlıkları işlemiyle uygulama katmanı (komut işleyicileri ve Web API denetleyicilerinin) yayılan ilgili.</span><span class="sxs-lookup"><span data-stu-id="f41ae-150">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="f41ae-151">Toplama kök giderseniz, toplama kök kendi invariants, kendi geçerlilik ya da kendi tutarlılığı garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="f41ae-151">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="f41ae-152">Sonunda spaghetti kod veya işlem bir kod sahip olur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-152">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="f41ae-153">DDD desenleri izlemek için varlıkları ortak ayarlayıcılar herhangi bir varlık özellik olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-153">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="f41ae-154">Bir varlık değişiklikleri varlıkta performans gösterdiğini değişikliği açık bulunabilen dil açık yöntemleriyle yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-154">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="f41ae-155">Ayrıca, varlık (örneğin, sipariş öğeleri) içindeki koleksiyonlar salt okunur özellikler olmalıdır (daha sonra AsReadOnly yöntemi açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="f41ae-155">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="f41ae-156">Birleşik kök sınıf yöntemlerini ya da alt varlık yöntemleri içinde yalnızca güncelleştirmeniz.</span><span class="sxs-lookup"><span data-stu-id="f41ae-156">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="f41ae-157">Sipariş toplama kök kodunda görebileceğiniz gibi varlık sınıfı yöntemleri aracılığıyla gerçekleştirilmek üzere varlığın veri ya da kendi alt varlıkları karşı herhangi bir işlem sahip olması tüm ayarlayıcılar harici olarak özel veya salt okunur en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-157">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="f41ae-158">Bu işlem komut dosyası kod uygulama yerine denetimli ve nesne yönelimli bir yolla tutarlılık tutar.</span><span class="sxs-lookup"><span data-stu-id="f41ae-158">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="f41ae-159">Aşağıdaki kod parçacığını sipariş toplama ÖgeSipariş nesne ekleme görevini kod için uygun şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-159">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="f41ae-160">Bu parçacığında, sipariş toplama kök denetiminde doğrulamaları ya da bir ÖgeSipariş nesnesinin oluşturulmasını ilişkili mantığını çoğu olacaktır — AddOrderItem yönteminde — özellikle doğrulamaları ve mantığı ilgili diğer öğelere toplama.</span><span class="sxs-lookup"><span data-stu-id="f41ae-160">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="f41ae-161">Örneğin, AddOrderItem için birden fazla çağrı sonucunu ile aynı ürün alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f41ae-161">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="f41ae-162">Bu yöntemde, ürün öğeleri inceleyin ve birkaç birimleri ile tek bir ÖgeSipariş nesne aynı ürün öğeleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-162">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="f41ae-163">Ayrıca, farklı iskonto tutarlarının vardır, ancak ürün kimliği aynı olduğundan, büyük olasılıkla daha yüksek indirim uygular.</span><span class="sxs-lookup"><span data-stu-id="f41ae-163">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="f41ae-164">Bu ilkeyi ÖgeSipariş nesne için başka bir etki alanı mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="f41ae-164">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="f41ae-165">Ayrıca, yeni OrderItem(params) işlemi de denetimli ve olması sipariş toplama kök AddOrderItem yöntemi tarafından gerçekleştirilen.</span><span class="sxs-lookup"><span data-stu-id="f41ae-165">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="f41ae-166">Bu nedenle, mantığı ya da doğrulamaları çoğunu işlemi (özellikle her şey, diğer alt varlıklar arasında tutarlılığı etkiler) toplama kök içinde tek bir yerde olacağını ilgili.</span><span class="sxs-lookup"><span data-stu-id="f41ae-166">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="f41ae-167">Birleşik kök düzeni nihai amacı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-167">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="f41ae-168">Entity Framework Çekirdek 1.1 veya kullandığınızda, izin verdiğinden daha sonra bir DDD varlık daha iyi ifade edilebilir [alanlarına eşleme](https://docs.microsoft.com/ef/core/modeling/backing-field) özellikleri yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="f41ae-168">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="f41ae-169">Bu, alt varlıkları veya değer nesnelerini koleksiyonları korurken faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-169">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="f41ae-170">Bu geliştirme ile özellikleri yerine basit özel alanlar kullanabilirsiniz ve herhangi bir güncelleştirme alan koleksiyonuna ortak yöntemleri uygulamak ve AsReadOnly yöntemi aracılığıyla salt okunur erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f41ae-170">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="f41ae-171">Yöntemleri herhangi değişmeyen ve veri tutarlılığını denetlemek için varlık (veya oluşturucusu) aracılığıyla yalnızca varlık güncelleştirmek istediğiniz GGG böylece yalnızca bir get erişimcisine özellikleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-171">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="f41ae-172">Özellikler özel alanları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-172">The properties are backed by private fields.</span></span> <span data-ttu-id="f41ae-173">Özel üyelerin yalnızca sınıf içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-173">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="f41ae-174">Ancak, burada bir özel durum: EF çekirdek de bu alanları ayarlayın gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="f41ae-174">However, there one exception: EF Core needs to set these fields as well.</span></span>


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="f41ae-175">Eşleme özellikleri yalnızca alanları veritabanı tablosunda get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="f41ae-175">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="f41ae-176">Veritabanı tablo sütunları eşleme özellikleri bir etki alanı sorumluluğu ancak altyapı ve kalıcılığı katmanının bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="f41ae-176">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="f41ae-177">Biz bu burada EF çekirdek 1.1'nda yeni özelliklerden haberdar; bu nedenle yalnızca ya da daha sonra ilgili varlıklar nasıl modellemek için Bahsediyor.</span><span class="sxs-lookup"><span data-stu-id="f41ae-177">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="f41ae-178">Bu konu hakkında daha fazla ayrıntı altyapı ve kalıcılığı bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f41ae-178">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="f41ae-179">DbContext içinde EF çekirdek 1.0 kullandığınızda, yalnızca veritabanı tablosunun gerçek alanlarla alıcıları ile tanımlanmış özellikleri eşlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-179">When you use EF Core 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="f41ae-180">Bu DataGrid'i sınıfı HasField yöntemi ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f41ae-180">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="f41ae-181">Özellikleri olmayan alanlarını eşleme</span><span class="sxs-lookup"><span data-stu-id="f41ae-181">Mapping fields without properties</span></span>

<span data-ttu-id="f41ae-182">Sütunları alanlarına eşlemek için özellikle EF çekirdek 1.1 veya sonraki sürümlerde, ayrıca özellikleri kullanmamayı mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f41ae-182">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="f41ae-183">Bunun yerine, yalnızca bir tablodaki sütunların alanlara eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f41ae-183">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="f41ae-184">Bu genel bir kullanım örneği özel alanlar için varlık erişilecek gerekmez bir iç durum modudur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-184">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="f41ae-185">Örneğin, önceki OrderAggregate kod örneğinde, birkaç özel alanlar vardır, gibi `_paymentMethodId` ayarlayıcı veya alıcı için ilgili bir özellik olan alan.</span><span class="sxs-lookup"><span data-stu-id="f41ae-185">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="f41ae-186">Bu alan de sipariş iş mantığı içinde hesaplanan ve sipariş yöntemleri kullanılır, ancak veritabanında kalıcı hale getirmek gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="f41ae-186">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="f41ae-187">Bu nedenle EF çekirdek (itibaren v1.1) içinde ilişkili bir özellik olmayan bir alan veritabanında bir sütunun eşlemek için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="f41ae-187">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="f41ae-188">Bu ayrıca içinde açıklanan [altyapısı katmanından](#the-infrastructure-layer) başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="f41ae-188">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f41ae-189">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f41ae-189">Additional resources</span></span>

-   <span data-ttu-id="f41ae-190">**Vaughn Vernon. Toplamalar DDD ve Entity Framework ile modelleme.**</span><span class="sxs-lookup"><span data-stu-id="f41ae-190">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="f41ae-191">Bu Not *değil* Entity Framework Çekirdek.</span><span class="sxs-lookup"><span data-stu-id="f41ae-191">Note that this is *not* Entity Framework Core.</span></span>
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="f41ae-192">**Julie Lerman. Etki alanı Odaklı Tasarım kodlama: Veri odaklı Devs için ipuçları**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="f41ae-192">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="f41ae-193">**UDI Dahan. Etki alanı modelleri tam oluşturma kapsüllenmiş**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="f41ae-193">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f41ae-194">[Önceki] (mikro hizmet-etki-model.md) [sonraki] (seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="f41ae-194">[Previous] (microservice-domain-model.md) [Next] (seedwork-domain-model-base-classes-interfaces.md)</span></span>
