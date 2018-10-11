---
title: Seedwork (yeniden kullanılabilir sınıflar ve arabirimler etki alanı modeliniz için)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Seedwork (yeniden kullanılabilir sınıflar ve arabirimler etki alanı modeliniz için)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: e377c0728ad48497c12b7a56e021067ed5dc2d93
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086122"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (yeniden kullanılabilir sınıflar ve arabirimler etki alanı modeliniz için)

Çözüm klasörü içeren bir *SeedWork* klasör. *SeedWork* klasörü, etki alanı varlıklarının ve değer nesneleri için bir temel olarak kullanabileceğiniz özel taban sınıfları içerir. Her etki alanının nesne sınıfında gereksiz kod zorunda kalmazsınız temel sınıfların kullanın. Bu tür sınıflar için klasör adını *SeedWork* gibi bir şey *Framework*. Çağrıldığı *SeedWork* gerçekten bir çerçeve düşünülmez yeniden kullanılabilir sınıfları yalnızca küçük bir alt klasör içerdiği için. *Seedwork* bir terimi tarafından tanıtılan [Michael geçiş yumuşatma](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) ve tarafından popüler [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) ancak bu klasörün ortak SharedKernel, ayrıca adlandırabilirsiniz veya benzer.

Şekil 9-12 seedwork etki alanı modeli oluşturan sıralama mikro hizmetinde sınıflarını göstermektedir. Bu varlık, ValueObject ve numaralandırma gibi birkaç özel taban sınıflar yanı sıra, birkaç arabirimleri vardır. Bu arabirimler (IRepository ve IUnitOfWork) uygulanması için gerekenler hakkında altyapı katmanını bildirin. Bu arabirimleri, aynı zamanda bağımlılık ekleme uygulama katmanından kullanılır.

![](./media/image13.PNG)

**Şekil 9-12**. Örnek etki alanı modeli "seedwork" temel sınıflar ve arabirimler ayarlayın

Birçok geliştiricinin biçimsel bir çerçeve proje arasında paylaşmak Kopyala ve Yapıştır yeniden türüdür. Herhangi bir katmanı veya kitaplık seedworks olabilir. Ancak, sınıflar ve arabirimler kümesi büyüklükte alırsa, bir tek sınıf kitaplığı oluşturmak isteyebilirsiniz.

## <a name="the-custom-entity-base-class"></a>Özel varlık temel sınıfı

Aşağıdaki kod, bir varlığı temel sınıf varlık kimliği gibi herhangi bir etki alanı varlığı ile aynı şekilde kullanılabilir kod burada yerleştirebilirsiniz örneğidir [eşitlik işleçleri](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), varlık, vb. başına bir etki alanı olay listesi.

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

Varlık başına bir etki alanı olay listesini kullanarak önceki kod, etki alanı olayları odaklandığınızda sonraki bölümde açıklanacaktır. 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Etki alanı model katmanında depo sözleşmelerinin (arabirimler)

Depo sözleşmeleri yalnızca her toplama için kullanılacak depoları sözleşme gereksinimlerini express .NET arabirimdir. 

EF Core kod veya tüm diğer altyapı bağımlılıkları ve (LINQ, SQL, vb.), kod depoları kendilerini, etki alanı modeli içinde uygulanması gereken değil; depoları tanımladığınız arabirimler yalnızca uygulamalıdır. 

(Etki alanı model katmanında deposu arabirimleri yerleştirerek) bu uygulama için ilgili bir desen ayrılmış arabirimi modelidir. Olarak [açıklanan](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler "bir arabirim tanımlamak için ayrılmış arabirimi kullanarak paket ancak başka bir uygulama. Bu şekilde arabirimine bağımlılık gerektiren bir istemci uygulamasını tamamen farkında olabilir."

Ayrılmış arabirimi düzenini izleyerek uygulama katmanında (Bu durumda, mikro hizmet için Web API projesi) etki alanı modeli içinde tanımlanan gereksinimlerini bağımlı ancak altyapı/Kalıcılık değil doğrudan bir bağımlılığa sahip olmasını sağlar Katman. Ayrıca, altyapıda uygulanan uygulama yalıtmak için bağımlılık ekleme kullanabilirsiniz / Kalıcılık katmanını kullanarak depolar.

Örneğin, aşağıdaki örnekte IOrderRepository arabirimiyle OrderRepository sınıfın altyapı katmanında uygulamak için ihtiyaç duyacağı hangi işlemleri tanımlar. Uygulamanın geçerli uygulamada kod eklemek veya sorguları Basitleştirilmiş CQRS yaklaşımı izleyerek bölünür olduğundan sipariş veritabanına güncelleştirmek yalnızca gerekir.

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

## <a name="additional-resources"></a>Ek kaynaklar

-   **Martin Fowler. Ayrılmış arabirimi.**
    [*https://www.martinfowler.com/eaaCatalog/separatedInterface.html*](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)


>[!div class="step-by-step"]
[Önceki](net-core-microservice-domain-model.md)
[İleri](implement-value-objects.md)
