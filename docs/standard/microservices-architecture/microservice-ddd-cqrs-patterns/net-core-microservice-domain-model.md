---
title: .NET Core ile mikro hizmet etki alanı modeli uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET Core ile mikro hizmet etki alanı modeli uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: bb11d87cacf5bb6cbc980c879b0c42fae76f6246
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45744045"
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="0e532-103">.NET Core ile mikro hizmet etki alanı modeli uygulama</span><span class="sxs-lookup"><span data-stu-id="0e532-103">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="0e532-104">Önceki bölümde açıklanan temel tasarım ilkeleri ve etki alanı modeli tasarlamaya yönelik Desenler.</span><span class="sxs-lookup"><span data-stu-id="0e532-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="0e532-105">.NET Core kullanarak etki alanı modeli uygulamak için kullanılabilecek yöntemler keşfedin artık (düz C\# kod) ve EF Core.</span><span class="sxs-lookup"><span data-stu-id="0e532-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="0e532-106">Etki alanı modeliniz basitçe kodunuzu oluşan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e532-106">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="0e532-107">EF üzerinde yalnızca EF Core model gereksinimleri ancak değil gerçek bağımlılıkları olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e532-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="0e532-108">Etki alanı modelinizdeki sabit bağımlılıkları veya EF Core veya diğer bir ORM olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e532-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="0e532-109">Özel bir .NET Standard Kitaplığı'nda etki alanı modeli yapısı</span><span class="sxs-lookup"><span data-stu-id="0e532-109">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="0e532-110">Hizmetine başvuru uygulaması için kullanılan klasör kuruluş uygulama DDD modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e532-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="0e532-111">Farklı bir klasöre kuruluş uygulamanız için tasarım seçimlerinizi daha net bir şekilde iletişim kuran bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e532-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="0e532-112">Şekil 9-10'da görüldüğü gibi sıralama etki alanı modeli içinde var. iki toplamlar, sipariş toplama ve alıcı toplama</span><span class="sxs-lookup"><span data-stu-id="0e532-112">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="0e532-113">Bir tek etki alanı varlığı (toplama kök veya kök varlık) de oluşan bir toplama sahip, ancak her toplam değer nesneleri ile etki alanı varlıklarının ve grubudur.</span><span class="sxs-lookup"><span data-stu-id="0e532-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="0e532-114">**Şekil 9-10**.</span><span class="sxs-lookup"><span data-stu-id="0e532-114">**Figure 9-10**.</span></span> <span data-ttu-id="0e532-115">Sıralama mikro hizmetine için etki alanı modeli yapısı</span><span class="sxs-lookup"><span data-stu-id="0e532-115">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="0e532-116">Ayrıca, etki alanı model katmanında, etki alanı modelinin altyapı gereksinimleri olan depo anlaşmalar (arabirimler) içerir.</span><span class="sxs-lookup"><span data-stu-id="0e532-116">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="0e532-117">Bu arabirimler altyapı katmanını uygulanmalı hangi depoları başka bir deyişle, express ve nasıl.</span><span class="sxs-lookup"><span data-stu-id="0e532-117">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="0e532-118">Etki alanı model katmanında "API veya Entity Framework gibi altyapı teknolojilerine sınıflardan contaminated değil için" depoları uygulamasını etki alanı model katmanında altyapı katman kitaplığı dışında yerleştirilmiş önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0e532-118">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="0e532-119">Ayrıca bkz bir [SeedWork](https://martinfowler.com/bliki/Seedwork.html) etki alanı varlıklarının ve değer için bir temel olarak kullanan özel temel sınıflar içeren klasörü nesneler, her etki alanının nesne sınıfında gereksiz kod zorunda kalmazsınız.</span><span class="sxs-lookup"><span data-stu-id="0e532-119">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="0e532-120">Özel bir .NET Standard kitaplığı toplamalar yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0e532-120">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="0e532-121">Toplama işlem tutarlılığı eşleştirilecek gruplanmış etki alanı nesnelerini bir kümeye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="0e532-121">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="0e532-122">Bu nesneler (biri toplama kök veya kök varlık olan) varlıklar örneklerini herhangi bir ek değer nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e532-122">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="0e532-123">İşlemsel tutarlılık, bir toplama tutarlı ve bir iş eylemi sonunda güncel olması sağlanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0e532-123">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="0e532-124">Örneğin, mikro hizmet etki alanı modeli sıralama hizmetine sipariş toplam Şekil 9-11'de gösterildiği gibi oluşur.</span><span class="sxs-lookup"><span data-stu-id="0e532-124">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="0e532-125">**Şekil 9-11**.</span><span class="sxs-lookup"><span data-stu-id="0e532-125">**Figure 9-11**.</span></span> <span data-ttu-id="0e532-126">Visual Studio çözümü içinde toplama sırası</span><span class="sxs-lookup"><span data-stu-id="0e532-126">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="0e532-127">Birleşik bir klasörde bulunan dosyalardan herhangi biri açarsanız, nasıl özel bir temel sınıf veya arabirim, varlık veya değer nesnesi olarak işaretlenmiş içinde uygulandığı şekilde gördüğünüz [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) klasör.</span><span class="sxs-lookup"><span data-stu-id="0e532-127">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="0e532-128">Uygulama etki alanı varlıklarının POCO sınıflar olarak</span><span class="sxs-lookup"><span data-stu-id="0e532-128">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="0e532-129">. NET'te, etki alanı varlıklarınızı uygulayan POCO sınıflar oluşturarak bir etki alanı modeli uygular.</span><span class="sxs-lookup"><span data-stu-id="0e532-129">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="0e532-130">Aşağıdaki örnekte sipariş sınıfı bir varlık olarak ve ayrıca bir toplama kök olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0e532-130">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="0e532-131">Sipariş sınıfı varlık temel sınıftan türetildiğinden, varlıkla ilgili ortak kodun yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e532-131">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="0e532-132">Unutmayın, bu nedenle, kod, olmayan bir ORM EF gibi altyapı kodunu bu sınıflar ve arabirimler sizin tarafınızdan etki alanı model projesinde tanımlandığından emin size aittir.</span><span class="sxs-lookup"><span data-stu-id="0e532-132">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

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

<span data-ttu-id="0e532-133">POCO sınıfı olarak uygulanan bir etki alanı varlığı olduğuna dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0e532-133">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="0e532-134">Entity Framework Core doğrudan bağımlılıkları veya herhangi bir altyapı çerçeveyi yok.</span><span class="sxs-lookup"><span data-stu-id="0e532-134">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="0e532-135">DDD, yalnızca C olması gerektiği gibi bu uygulamasıdır\# bir etki alanı modeli uygulama kodu.</span><span class="sxs-lookup"><span data-stu-id="0e532-135">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="0e532-136">Ayrıca, sınıf IAggregateRoot adlı bir arabirim ile sunulur.</span><span class="sxs-lookup"><span data-stu-id="0e532-136">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="0e532-137">Bu arabirim bazen adlı boş bir arabirim olduğundan bir *işaret arabirimi*, yani yalnızca bu varlık sınıfı bir toplama kök olduğunu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e532-137">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="0e532-138">Bir işaretleyici arabirimi bazen önleyici bir deseni olarak kabul edilir; Ancak, bu da özellikle arabirimin gelişen, bir sınıfı işaretlemek için bir temiz yoludur.</span><span class="sxs-lookup"><span data-stu-id="0e532-138">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="0e532-139">Bir öznitelik işaretçisi için diğer bir seçenek olabilir, ancak temel sınıfı (varlık) yerine sınıf üzerinde bir toplama özniteliği işaret IAggregate arabirimi yanındaki bkz daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e532-139">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="0e532-140">Tercihleri sağlasa da her durumda olur.</span><span class="sxs-lookup"><span data-stu-id="0e532-140">It is a matter of preferences, in any case.</span></span>

<span data-ttu-id="0e532-141">Tutarlılık için kodun en ilgili ve toplama'nın varlık iş kuralları sipariş toplama kök sınıfı (Orderıtem nesnesi için toplama eklerken gibi AddOrderItem) yöntemleri olarak uygulanması gereken bir toplama kök yol sahip .</span><span class="sxs-lookup"><span data-stu-id="0e532-141">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="0e532-142">Size oluşturamadı veya güncelleştiremedi OrderItems nesneleri bağımsız olarak veya doğrudan; AggregateRoot sınıfı, Denetim ve onun alt varlıklar karşı herhangi bir güncelleştirme işlem tutarlılığını tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e532-142">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulating-data-in-the-domain-entities"></a><span data-ttu-id="0e532-143">Etki alanı varlıklarda veri şifreleme</span><span class="sxs-lookup"><span data-stu-id="0e532-143">Encapsulating data in the Domain Entities</span></span>

<span data-ttu-id="0e532-144">Koleksiyon Gezinti özellikleri genel olarak erişilebilir liste türleri olarak ortaya varlık modelleri yaygın görülen bir sorun var.</span><span class="sxs-lookup"><span data-stu-id="0e532-144">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="0e532-145">Bu, büyük olasılıkla Nesne geçersiz bir durumda bırakarak koleksiyona ilgili önemli iş kuralları kullanmayan, bu koleksiyon türleri, içeriğini işlemek herhangi bir ortak çalışanı Geliştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e532-145">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="0e532-146">Bu salt okunur erişim için ilgili koleksiyonları ve açıkça istemcileri işleyebileceğiniz bunları yolları tanımlayan yöntemleri sağlar çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="0e532-146">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="0e532-147">Önceki kodda, birçok öznitelikleri salt okunur veya özel ve yalnızca bu nedenle her hesap iş etki alanı okuduğunuzda ve mantıksal sınıfı yöntemler içinde belirtilen güncelleştirme alan sınıfı yöntemleri tarafından güncelleştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e532-147">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update takes into account business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="0e532-148">Örneğin, DDD deseni, aşağıdakileri yapmalısınız *değil* herhangi bir sınıftan komut işleyicisi yöntemi veya uygulama katmanı aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="0e532-148">For example, following DDD patterns, you should *not* do the following from any command handler method or application layer class:</span></span>

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

<span data-ttu-id="0e532-149">Bu durumda, Add yöntemi OrderItems koleksiyona doğrudan erişimi olan bir veri eklemek için yalnızca bir işlemidir.</span><span class="sxs-lookup"><span data-stu-id="0e532-149">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="0e532-150">Bu nedenle, etki alanı mantığı, kurallar veya doğrulamaları çoğu işlemi alt varlıklar ile uygulama katmanı arasında (komut işleyicileri ve Web APİ'si denetleyicilerinin) yayılacak ilgili.</span><span class="sxs-lookup"><span data-stu-id="0e532-150">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="0e532-151">Toplama kök giderseniz, toplama kök kendi okuduğunuzda, geçerliliğini veya kendi tutarlılığı garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="0e532-151">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="0e532-152">Sonunda spaghetti kodu veya işlem bir kod olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e532-152">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="0e532-153">DDD desenlerini izlemek için varlıklar genel ayarlayıcılar içinde herhangi bir varlık özelliği olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e532-153">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="0e532-154">Bir varlıktaki değişiklikleri varlıkta gerçekleştirdiği değişikliği hakkında açık bulunabilen diliyle açık yöntemlerle dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e532-154">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="0e532-155">Ayrıca, (örneğin sırada öğeleri) varlık koleksiyon salt okunur özellikler olmalıdır (daha sonra AsReadOnly yöntemi açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="0e532-155">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="0e532-156">Alt varlık yöntemlerini veya toplama kök sınıfı yöntemleri içinde yalnızca güncelleştirmeniz.</span><span class="sxs-lookup"><span data-stu-id="0e532-156">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="0e532-157">Sipariş toplama kök kodunda gördüğünüz gibi varlık sınıfı yöntemleri aracılığıyla gerçekleştirilmek üzere herhangi bir işlem varlığın verilerine ya da kendi alt varlıklar karşı sahip olacak şekilde tüm ayarlayıcılar dışarıdan, özel veya en azından salt okunur olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e532-157">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="0e532-158">Bu işlem kod uygulamak yerine denetimli ve nesne yönelimli bir şekilde tutarlılığı korur.</span><span class="sxs-lookup"><span data-stu-id="0e532-158">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="0e532-159">Aşağıdaki kod parçacığı, Orderıtem nesne için sipariş toplama ekleme görevini kod en uygun yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e532-159">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="0e532-160">Bu kod parçacığında, çoğu doğrulamaları veya Orderıtem nesneyi oluşturulmasını ilgili mantıksal sırası toplama kök denetimi altında olacaktır — AddOrderItem yönteminde — özellikle doğrulamaları ve mantıksal ilgili diğer öğelere toplama.</span><span class="sxs-lookup"><span data-stu-id="0e532-160">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="0e532-161">Örneğin, birden çok çağrı AddOrderItem sonucu ile aynı ürün alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e532-161">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="0e532-162">Bu yöntemde, ürün öğeleri inceleyin ve aynı ürün öğeleri birkaç birimleri ile tek bir Orderıtem nesne birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0e532-162">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="0e532-163">Ek olarak, farklı indirim miktarları vardır, ancak ürün kimliği aynı olan, büyük olasılıkla daha yüksek indirim uygulanacak.</span><span class="sxs-lookup"><span data-stu-id="0e532-163">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="0e532-164">Bu ilke, Orderıtem nesne için başka bir etki alanı mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="0e532-164">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="0e532-165">Ayrıca, yeni OrderItem(params) işlemi ayrıca denetlenen ve sipariş toplama kökünden AddOrderItem yöntemi tarafından gerçekleştirilen.</span><span class="sxs-lookup"><span data-stu-id="0e532-165">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="0e532-166">Bu nedenle, çoğu mantığı veya doğrulama işlemi (özellikle her şey, diğer alt varlıklar arasında tutarlılık etkiler), toplama kök içinde tek bir yerde olacaktır ilgili.</span><span class="sxs-lookup"><span data-stu-id="0e532-166">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="0e532-167">Ultimate amacı, toplama kök desen olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0e532-167">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="0e532-168">Entity Framework Core 1.1 veya kullandığınızda bu izin verdiğinden daha sonra bir DDD varlık daha iyi ifade edilebilir [alanlarına eşleme](https://docs.microsoft.com/ef/core/modeling/backing-field) ek özellikler.</span><span class="sxs-lookup"><span data-stu-id="0e532-168">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="0e532-169">Bu, alt varlıklar değer nesneleri ve koleksiyonları korurken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e532-169">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="0e532-170">Bu geliştirme ile basit özel alanları yerine özellikleri kullanın ve alan koleksiyonu için herhangi bir güncelleştirme genel yöntemleri uygulayan ve AsReadOnly yöntemi aracılığıyla salt okunur erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e532-170">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="0e532-171">Herhangi bir değişmez değer ve veri tutarlılığını denetlemek için varlık (veya Oluşturucu) yöntemleri aracılığıyla yalnızca varlık güncelleştirmek istediğiniz DDD içinde bu nedenle özellikleri yalnızca bir alma erişimcisi ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0e532-171">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="0e532-172">Özel alanlarla özellikleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0e532-172">The properties are backed by private fields.</span></span> <span data-ttu-id="0e532-173">Özel üyeler yalnızca sınıfın içinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e532-173">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="0e532-174">Bununla birlikte, burada bir özel durum: EF Core de bu alanları ayarlayın gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e532-174">However, there one exception: EF Core needs to set these fields as well.</span></span>


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="0e532-175">Eşleme özellikleri yalnızca alanları veritabanı tablosu, get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="0e532-175">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="0e532-176">Veritabanı tablo sütunları özellikleri eşleme bir etki alanı sorumluluğu ancak altyapı ve Kalıcılık katmanının bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="0e532-176">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="0e532-177">Biz, bunu buradan EF Core 1.1 yeni özelliklerin farkında olduklarından yalnızca veya varlıkların nasıl model daha sonra ilgili bahsedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e532-177">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="0e532-178">Bu konu hakkında daha fazla ayrıntı altyapı ve Kalıcılık bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e532-178">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="0e532-179">DbContext içinde EF Core 1.0 kullandığınızda, yalnızca veritabanı tablosundaki gerçek alanlara alıcıları ile tanımlanmış özellikler eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e532-179">When you use EF Core 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="0e532-180">Bu DataGrid'i sınıfının HasField yöntemi ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0e532-180">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="0e532-181">Özellikleri olmayan alanlarını eşleme</span><span class="sxs-lookup"><span data-stu-id="0e532-181">Mapping fields without properties</span></span>

<span data-ttu-id="0e532-182">Alanlarına sütunları eşlemek için özelliğiyle EF Core 1.1 veya daha sonra da özelliklerini kullanmayı mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0e532-182">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="0e532-183">Bunun yerine, yalnızca bir tablodaki sütunların alanlarına eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e532-183">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="0e532-184">Bu yaygın bir kullanım durumu dışında varlık erişilmesi gerekmeyen bir iç durum için özel alanlar var.</span><span class="sxs-lookup"><span data-stu-id="0e532-184">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="0e532-185">Örneğin, önceki OrderAggregate kod örneğinde, birkaç özel alanlar vardır, gibi `_paymentMethodId` ilgili özellik alıcı veya ayarlayıcı için olan alan.</span><span class="sxs-lookup"><span data-stu-id="0e532-185">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="0e532-186">Bu alan ayrıca sipariş iş mantığı içinde hesaplanan ve sipariş yöntemleri kullanılır, ancak veritabanında kalıcı hale getirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e532-186">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="0e532-187">Bu nedenle EF Core (itibaren v1.1) içinde bir veritabanı sütununa ilgili özelliği olmayan bir alan eşlemek için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="0e532-187">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="0e532-188">Bu da açıklanan [altyapı katmanını](#the-infrastructure-layer) başlığına.</span><span class="sxs-lookup"><span data-stu-id="0e532-188">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0e532-189">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0e532-189">Additional resources</span></span>

-   <span data-ttu-id="0e532-190">**Vaughn Vernon. Toplamlar DDD ve Entity Framework ile model.**</span><span class="sxs-lookup"><span data-stu-id="0e532-190">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="0e532-191">Bu Not *değil* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="0e532-191">Note that this is *not* Entity Framework Core.</span></span>
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="0e532-192">**Julie Lerman. Etki alanı odaklı tasarım için kodlama: Veri odaklı geliştiriciler için ipuçları**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="0e532-192">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="0e532-193">**UDI Dahan. Etki alanı modellerini oluşturma tam olarak kapsüllenmiş**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="0e532-193">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0e532-194">[Önceki](microservice-domain-model.md)
[İleri](seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="0e532-194">[Previous](microservice-domain-model.md)
[Next](seedwork-domain-model-base-classes-interfaces.md)</span></span>
