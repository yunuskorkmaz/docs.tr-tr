---
title: Seedwork (etki alanı modeliniz için yeniden kullanılabilir kök sınıflar ve arabirimler)
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | DDD yönelimli etki alanı modeli için uygulamayı başlatmak için tohum çalışması kavramını başlangıç noktası olarak kullanın.
ms.date: 10/08/2018
ms.openlocfilehash: ab0aadc28dbd1175c75b04dadca29b7b0947f29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116576"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="21439-103">Seedwork (etki alanı modeliniz için yeniden kullanılabilir kök sınıflar ve arabirimler)</span><span class="sxs-lookup"><span data-stu-id="21439-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="21439-104">Çözüm klasörü bir *SeedWork* klasörü içerir.</span><span class="sxs-lookup"><span data-stu-id="21439-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="21439-105">Bu klasör, etki alanı varlıklarınız ve değer nesneleriniz için taban olarak kullanabileceğiniz özel taban sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="21439-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="21439-106">Her etki alanının nesne sınıfında gereksiz kodunuz olmayacak şekilde bu temel sınıfları kullanın.</span><span class="sxs-lookup"><span data-stu-id="21439-106">Use these base classes so you don't have redundant code in each domain’s object class.</span></span> <span data-ttu-id="21439-107">Bu tür sınıflar için klasör *SeedWork* *değil, Framework*gibi bir şey denir.</span><span class="sxs-lookup"><span data-stu-id="21439-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="21439-108">*SeedWork* olarak adlandırılır, çünkü klasör gerçekten bir çerçeve olarak kabul edilemeyecek yeniden kullanılabilir sınıfların yalnızca küçük bir alt kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="21439-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes that cannot really be considered a framework.</span></span> <span data-ttu-id="21439-109">*Seedwork* bir terim [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) tarafından tanıtıldı ve [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) tarafından popüler ama aynı zamanda bu klasör Ortak, SharedKernel veya benzer adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21439-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="21439-110">Şekil 7-12, sipariş mikrohizmetinde etki alanı modelinin tohum çalışmasını oluşturan sınıfları gösterir.</span><span class="sxs-lookup"><span data-stu-id="21439-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="21439-111">Varlık, ValueObject ve Numaralandırma gibi birkaç özel taban sınıfı nın yanı sıra birkaç arabirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="21439-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="21439-112">Bu arabirimler (IRepository ve IUnitOfWork) ne uygulanması gerektiği hakkında altyapı katmanı nı bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="21439-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="21439-113">Bu arabirimler, uygulama katmanından Bağımlılık Enjeksiyonu ile de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21439-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="SeedWork klasöründe bulunan sınıfların ekran görüntüsü.":::
<span data-ttu-id="21439-115">Temel sınıfları ve arabirimleri içeren SeedWork klasörünün ayrıntılı içeriği: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs ve ValueObject.cs.</span><span class="sxs-lookup"><span data-stu-id="21439-115">The detailed contents of the SeedWork folder, containing base classes and interfaces: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs, and ValueObject.cs.</span></span>
:::image-end:::

<span data-ttu-id="21439-116">**Şekil 7-12**.</span><span class="sxs-lookup"><span data-stu-id="21439-116">**Figure 7-12**.</span></span> <span data-ttu-id="21439-117">Etki alanı modeli "seedwork" temel sınıfları ve arabirimleri örnek kümesi</span><span class="sxs-lookup"><span data-stu-id="21439-117">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="21439-118">Bu, birçok geliştiricinin resmi bir çerçeve değil, projeler arasında paylaştığı kopyalama ve yapıştırma türüdür.</span><span class="sxs-lookup"><span data-stu-id="21439-118">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="21439-119">Herhangi bir katmanda veya kütüphanede tohum işleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="21439-119">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="21439-120">Ancak, sınıflar ve arabirimler kümesi yeterince büyürse, tek bir sınıf kitaplığı oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21439-120">However, if the set of classes and interfaces gets large enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="21439-121">Özel Varlık taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="21439-121">The custom Entity base class</span></span>

<span data-ttu-id="21439-122">Aşağıdaki kod, varlık kimliği, [eşitlik işleçleri,](../../../csharp/language-reference/operators/equality-operators.md)varlık başına etki alanı olay listesi, vb. gibi herhangi bir etki alanı varlığı tarafından aynı şekilde kullanılabilecek kodu yerleştirebileceğiniz varlık taban sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="21439-122">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](../../../csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

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
            // https://docs.microsoft.com/archive/blogs/ericlippert/guidelines-and-rules-for-gethashcode
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

<span data-ttu-id="21439-123">Varlık başına bir etki alanı olay listesi kullanan önceki kod, etki alanı olaylarına odaklanırken sonraki bölümlerde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="21439-123">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="21439-124">Etki alanı modeli katmanındaki depo sözleşmeleri (arabirimler)</span><span class="sxs-lookup"><span data-stu-id="21439-124">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="21439-125">Depo sözleşmeleri, her bir toplam için kullanılacak depoların sözleşme gereksinimlerini ifade eden basitçe .NET arabirimleridir.</span><span class="sxs-lookup"><span data-stu-id="21439-125">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="21439-126">EF Core kodu veya diğer altyapı bağımlılıkları ve kodları (Linq, SQL, vb.) ile depoların kendileri etki alanı modeli içinde uygulanmamalıdır; depolar yalnızca etki alanı modelinde tanımladığınız arabirimleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="21439-126">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="21439-127">Bu uygulamayla ilgili bir desen (depo arabirimlerini etki alanı modeli katmanına yerleştirme) Ayrılmış Arabirim desenidir.</span><span class="sxs-lookup"><span data-stu-id="21439-127">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="21439-128">Martin Fowler tarafından [açıklandığı](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) gibi, "Bir pakette bir arabirim tanımlamak için Ayrılmış Arabirim kullanın ama başka bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="21439-128">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="21439-129">Bu şekilde arabirime bağımlı bir istemci uygulamadan tamamen habersiz olabilir."</span><span class="sxs-lookup"><span data-stu-id="21439-129">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="21439-130">Ayrılmış Arabirim deseni izleyerek uygulama katmanı (bu durumda, mikro hizmet için Web API projesi) etki alanı modelinde tanımlanan gereksinimleri bir bağımlılık var, ancak altyapı / kalıcılık katmanı na doğrudan bağımlılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="21439-130">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="21439-131">Buna ek olarak, depoları kullanarak altyapı/ kalıcılık katmanında uygulanan uygulamayı yalıtmak için Bağımlılık Enjeksiyonu'nu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21439-131">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="21439-132">Örneğin, IOrderRepository arabirimindeki aşağıdaki örnek, OrderRepository sınıfının altyapı katmanında uygulamak için hangi işlemleri gerçekleştirmesi gerekeceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21439-132">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="21439-133">Basitleştirilmiş CQRS yaklaşımına göre sorgular bölündüğünden, uygulamanın geçerli uygulamasında, kodun veri tabanına sipariş eklemesi veya güncelleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="21439-133">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="21439-134">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="21439-134">Additional resources</span></span>

- <span data-ttu-id="21439-135">**Martin Fowler' ı. Ayrılmış Arayüz.**</span><span class="sxs-lookup"><span data-stu-id="21439-135">**Martin Fowler. Separated Interface.**</span></span> \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
><span data-ttu-id="21439-136">[Önceki](net-core-microservice-domain-model.md)
>[Sonraki](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="21439-136">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
