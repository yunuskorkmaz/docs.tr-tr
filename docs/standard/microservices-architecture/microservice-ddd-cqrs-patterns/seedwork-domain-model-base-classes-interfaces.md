---
title: Seedwork (yeniden kullanılabilir sınıflar ve arabirimler etki alanı modeliniz için)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Seedwork kavramı, uygulama için bir etki alanı DDD odaklı modeli başlatmak için bir başlangıç noktası olarak kullanın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 38de5d686c17810f406a57d58554046ba2d888d9
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545734"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="a0db2-103">Seedwork (yeniden kullanılabilir sınıflar ve arabirimler etki alanı modeliniz için)</span><span class="sxs-lookup"><span data-stu-id="a0db2-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="a0db2-104">Çözüm klasörü içeren bir *SeedWork* klasör.</span><span class="sxs-lookup"><span data-stu-id="a0db2-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="a0db2-105">Bu klasör, etki alanı varlıklarının ve değer nesneleri için bir temel olarak kullanabileceğiniz özel taban sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a0db2-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="a0db2-106">Her etki alanının nesne sınıfında gereksiz kod zorunda kalmazsınız temel sınıfların kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0db2-106">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="a0db2-107">Bu tür sınıflar için klasör adını *SeedWork* gibi bir şey *Framework*.</span><span class="sxs-lookup"><span data-stu-id="a0db2-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="a0db2-108">Çağrıldığı *SeedWork* gerçekten bir çerçeve düşünülmez yeniden kullanılabilir sınıfları yalnızca küçük bir alt klasör içerdiği için.</span><span class="sxs-lookup"><span data-stu-id="a0db2-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="a0db2-109">*Seedwork* bir terimi tarafından tanıtılan [Michael geçiş yumuşatma](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) ve tarafından popüler [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) ancak bu klasörün ortak SharedKernel, ayrıca adlandırabilirsiniz veya benzer.</span><span class="sxs-lookup"><span data-stu-id="a0db2-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="a0db2-110">Şekil 7-12 seedwork etki alanı modeli oluşturan sıralama mikro hizmetinde sınıflarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a0db2-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="a0db2-111">Bu varlık, ValueObject ve numaralandırma gibi birkaç özel taban sınıflar yanı sıra, birkaç arabirimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="a0db2-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="a0db2-112">Bu arabirimler (IRepository ve IUnitOfWork) uygulanması için gerekenler hakkında altyapı katmanını bildirin.</span><span class="sxs-lookup"><span data-stu-id="a0db2-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="a0db2-113">Bu arabirimleri, aynı zamanda bağımlılık ekleme uygulama katmanından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0db2-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![Sınıflar ve arabirimler içeren SeedWork klasörünün ayrıntılı içeriği: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs ve ValueObject.cs](./media/image13.PNG)

<span data-ttu-id="a0db2-115">**Şekil 7-12**.</span><span class="sxs-lookup"><span data-stu-id="a0db2-115">**Figure 7-12**.</span></span> <span data-ttu-id="a0db2-116">Örnek etki alanı modeli "seedwork" temel sınıflar ve arabirimler ayarlayın</span><span class="sxs-lookup"><span data-stu-id="a0db2-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="a0db2-117">Birçok geliştiricinin biçimsel bir çerçeve proje arasında paylaşmak Kopyala ve Yapıştır yeniden türüdür.</span><span class="sxs-lookup"><span data-stu-id="a0db2-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="a0db2-118">Herhangi bir katmanı veya kitaplık seedworks olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0db2-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="a0db2-119">Ancak, sınıflar ve arabirimler kümesi büyüklükte alırsa, bir tek sınıf kitaplığı oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0db2-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="a0db2-120">Özel varlık temel sınıfı</span><span class="sxs-lookup"><span data-stu-id="a0db2-120">The custom Entity base class</span></span>

<span data-ttu-id="a0db2-121">Aşağıdaki kod, bir varlığı temel sınıf varlık kimliği gibi herhangi bir etki alanı varlığı ile aynı şekilde kullanılabilir kod burada yerleştirebilirsiniz örneğidir [eşitlik işleçleri](~/docs/csharp/language-reference/operators/equality-operators.md), varlık, vb. başına bir etki alanı olay listesi.</span><span class="sxs-lookup"><span data-stu-id="a0db2-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](~/docs/csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;    
    private List<INotification> _domainEvents;
    public virtual int Id 
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

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

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }

    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() ^ 31;
            // XOR for random distribution. See:
            // https://blogs.msdn.microsoft.com/ericlippert/2011/02/28/guidelines-and-rules-for-gethashcode/
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null));
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

<span data-ttu-id="a0db2-122">Varlık başına bir etki alanı olay listesini kullanarak önceki kod, etki alanı olayları odaklandığınızda sonraki bölümde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a0db2-122">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="a0db2-123">Etki alanı model katmanında depo sözleşmelerinin (arabirimler)</span><span class="sxs-lookup"><span data-stu-id="a0db2-123">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="a0db2-124">Depo sözleşmeleri yalnızca her toplama için kullanılacak depoları sözleşme gereksinimlerini express .NET arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="a0db2-124">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="a0db2-125">EF Core kod veya tüm diğer altyapı bağımlılıkları ve (LINQ, SQL, vb.), kod depoları kendilerini, etki alanı modeli içinde uygulanması gereken değil; depoları, yalnızca etki alanı modeli içinde tanımladığınız arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0db2-125">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="a0db2-126">(Etki alanı model katmanında deposu arabirimleri yerleştirerek) bu uygulama için ilgili bir desen ayrılmış arabirimi modelidir.</span><span class="sxs-lookup"><span data-stu-id="a0db2-126">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="a0db2-127">Olarak [açıklanan](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler "bir arabirim tanımlamak için ayrılmış arabirimi kullanarak paket ancak başka bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a0db2-127">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="a0db2-128">Bu şekilde arabirimine bağımlılık gerektiren bir istemci uygulamasını tamamen farkında olabilir."</span><span class="sxs-lookup"><span data-stu-id="a0db2-128">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="a0db2-129">Ayrılmış arabirimi düzenini izleyerek uygulama katmanında (Bu durumda, mikro hizmet için Web API projesi) etki alanı modeli içinde tanımlanan gereksinimlerini bağımlı ancak altyapı/Kalıcılık değil doğrudan bir bağımlılığa sahip olmasını sağlar Katman.</span><span class="sxs-lookup"><span data-stu-id="a0db2-129">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="a0db2-130">Ayrıca, altyapıda uygulanan uygulama yalıtmak için bağımlılık ekleme kullanabilirsiniz / Kalıcılık katmanını kullanarak depolar.</span><span class="sxs-lookup"><span data-stu-id="a0db2-130">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="a0db2-131">Örneğin, aşağıdaki örnekte IOrderRepository arabirimiyle OrderRepository sınıfın altyapı katmanında uygulamak için ihtiyaç duyacağı hangi işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a0db2-131">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="a0db2-132">Uygulamanın geçerli uygulamada kod eklemek veya sorguları Basitleştirilmiş CQRS yaklaşımı izleyerek bölünür olduğundan sipariş veritabanına güncelleştirmek yalnızca gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0db2-132">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);

    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="a0db2-133">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a0db2-133">Additional resources</span></span>

- <span data-ttu-id="a0db2-134">**Martin Fowler. Ayrılmış arabirimi.**</span><span class="sxs-lookup"><span data-stu-id="a0db2-134">**Martin Fowler. Separated Interface.**</span></span> \
  [https://www.martinfowler.com/eaaCatalog/separatedInterface.html](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)

>[!div class="step-by-step"]
><span data-ttu-id="a0db2-135">[Önceki](net-core-microservice-domain-model.md)
>[İleri](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="a0db2-135">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
