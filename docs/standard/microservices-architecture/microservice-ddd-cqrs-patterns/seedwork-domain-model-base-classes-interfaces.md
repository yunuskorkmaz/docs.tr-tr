---
title: "Seedwork (yeniden kullanılabilir temel sınıflar ve arabirimler etki alanı modeliniz için)"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Seedwork (yeniden kullanılabilir temel sınıflar ve arabirimler etki alanı modeliniz için)"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0754ba124cbc37c6c6e3aedd90dc860e16c21d73
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="f15a4-104">Seedwork (yeniden kullanılabilir temel sınıflar ve arabirimler etki alanı modeliniz için)</span><span class="sxs-lookup"><span data-stu-id="f15a4-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="f15a4-105">Çözüm klasörü içeren bir *SeedWork* klasör.</span><span class="sxs-lookup"><span data-stu-id="f15a4-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="f15a4-106">*SeedWork* klasörü etki alanı varlıkları ve değer nesneler için temel olarak kullanabileceğiniz özel temel sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="f15a4-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="f15a4-107">Temel sınıflar kullandığından, her etki alanının nesne sınıfında yedekli koduna sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f15a4-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="f15a4-108">Bu tür sınıflar için klasör adında *SeedWork* bir şey yok gibi ve *Framework*.</span><span class="sxs-lookup"><span data-stu-id="f15a4-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="f15a4-109">Çağrılır *SeedWork* bir çerçeve gerçekten kabul edilemez yeniden kullanılabilir sınıfların yalnızca küçük bir alt klasör içerdiği için.</span><span class="sxs-lookup"><span data-stu-id="f15a4-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="f15a4-110">*Seedwork* bir terim tarafından sunulan [Michael geçiş yumuşatma](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) ve tarafından popularized [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) ancak bu klasöre ortak SharedKernel, ad veya benzer.</span><span class="sxs-lookup"><span data-stu-id="f15a4-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="f15a4-111">Şekil 9-12 sıralama mikro hizmet içinde etki alanı modeli seedwork form sınıflarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15a4-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="f15a4-112">Varlık, ValueObject ve numaralandırma gibi birkaç özel taban sınıfları yanı sıra, birkaç arabirimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f15a4-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="f15a4-113">Bu arabirimleri (IRepository ve IUnitOfWork) uygulanması gerekenler hakkında altyapısı katmanından bildirin.</span><span class="sxs-lookup"><span data-stu-id="f15a4-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="f15a4-114">Bu arabirimleri de uygulama katmanı bağımlılık ekleme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f15a4-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="f15a4-115">**Şekil 9-12**.</span><span class="sxs-lookup"><span data-stu-id="f15a4-115">**Figure 9-12**.</span></span> <span data-ttu-id="f15a4-116">Örnek bir etki alanı modeli "seedwork" temel sınıfları ve arabirimleri ayarlayın</span><span class="sxs-lookup"><span data-stu-id="f15a4-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="f15a4-117">Çoğu geliştiricinin bir resmi framework projeler arasında paylaşmak Kopyala ve Yapıştır yeniden türüdür.</span><span class="sxs-lookup"><span data-stu-id="f15a4-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="f15a4-118">Herhangi bir katman veya kitaplık seedworks olabilir.</span><span class="sxs-lookup"><span data-stu-id="f15a4-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="f15a4-119">Ancak, sınıflar ve arabirimler kümesi yeterince büyük alırsa, bir tek sınıf kitaplığı oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15a4-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="f15a4-120">Özel varlık taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="f15a4-120">The custom Entity base class</span></span>

<span data-ttu-id="f15a4-121">Aşağıdaki kod bir varlık temel sınıfı aynı şekilde varlık kimliği gibi herhangi bir etki alanı varlık tarafından kullanılan kod burada yerleştirebilirsiniz örneğidir [eşitlik işleçleri](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), varlık, vb. bir etki alanı olay listesi.</span><span class="sxs-lookup"><span data-stu-id="f15a4-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), a domain event list per entity, etc.</span></span>

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
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

<span data-ttu-id="f15a4-122">Varlık başına etki alanı olay listesini kullanarak önceki kod, etki alanı olaylarına odaklanan olduğunda sonraki bölümlerde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f15a4-122">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span> 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="f15a4-123">Etki alanı modeli katmanda deposu sözleşmeleri (arabirimi)</span><span class="sxs-lookup"><span data-stu-id="f15a4-123">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="f15a4-124">Depo sözleşmeleri yalnızca her toplama için kullanılacak depoları sözleşme gereksinimlerini express .NET arabirimlerdir.</span><span class="sxs-lookup"><span data-stu-id="f15a4-124">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> 

<span data-ttu-id="f15a4-125">EF çekirdek kodu veya diğer altyapı bağımlılıkları ve kod (LINQ, SQL, vb.) ile depoları kendileri içinde etki alanı modeli uygulanmalı değil; depoları tanımladığınız arabirimleri yalnızca uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f15a4-125">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span> 

<span data-ttu-id="f15a4-126">(Etki alanı modeli katmanda deposu arabirimleri yerleştirerek) bu uygulama için ilgili bir desen ayrılmış arabirimi düzeni ' dir.</span><span class="sxs-lookup"><span data-stu-id="f15a4-126">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="f15a4-127">Olarak [açıklandığı](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler "bir arabirim birinde tanımlamak için kullanım ayrılmış arabirimi paketini ancak başka bir programda uygulamak.</span><span class="sxs-lookup"><span data-stu-id="f15a4-127">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="f15a4-128">Bu şekilde arabirimi bağımlılığı gerektiren bir istemci uygulaması tamamen farkında olabilir."</span><span class="sxs-lookup"><span data-stu-id="f15a4-128">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="f15a4-129">Ayrılmış arabirimi desen aşağıdaki uygulama katmanında (Bu durumda, Web API projesi mikro hizmet için) etki alanı modelinde tanımlanan gereksinimlerle bir bağımlılığı ancak altyapı/Kalıcılık değil doğrudan bir bağımlılığa sahip olmasını sağlar katmanı.</span><span class="sxs-lookup"><span data-stu-id="f15a4-129">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="f15a4-130">Ayrıca, altyapısında uygulanan uygulama yalıtmak için bağımlılık ekleme kullanabilirsiniz / saklama katmanını kullanarak depoları.</span><span class="sxs-lookup"><span data-stu-id="f15a4-130">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="f15a4-131">Örneğin, aşağıdaki örnekte IOrderRepository arabirimiyle OrderRepository sınıfın altyapı katmanında uygulamak için ihtiyaç duyacağı hangi işlemlerin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f15a4-131">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="f15a4-132">Uygulama geçerli uygulama, kod eklemek veya sorguları Basitleştirilmiş CQRS yaklaşımı izleyerek bölünür beri siparişleri veritabanına güncelleştirmek yalnızca gerekir.</span><span class="sxs-lookup"><span data-stu-id="f15a4-132">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="f15a4-133">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f15a4-133">Additional resources</span></span>

-   <span data-ttu-id="f15a4-134">**Martin Fowler. Ayrılmış arabirimi. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span><span class="sxs-lookup"><span data-stu-id="f15a4-134">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f15a4-135">[Önceki] (net-core-mikro hizmet-etki-model.md) [sonraki] (uygulama değeri objects.md)</span><span class="sxs-lookup"><span data-stu-id="f15a4-135">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
