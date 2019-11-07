---
title: Seedwork (etki alanı modeliniz için yeniden kullanılabilir kök sınıflar ve arabirimler)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | DDD tabanlı bir etki alanı modeline yönelik uygulamayı başlatmak için başlangıç noktası olarak seedwork kavramını kullanın.
ms.date: 10/08/2018
ms.openlocfilehash: f53988b92a05fb54f3f05d9f463450d1a11a0843
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737228"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (etki alanı modeliniz için yeniden kullanılabilir kök sınıflar ve arabirimler)

Çözüm klasörü bir *Seedwork* klasörü içerir. Bu klasör, etki alanı varlıklarınız ve değer nesneleriniz için temel olarak kullanabileceğiniz özel temel sınıflar içerir. Bu temel sınıfları kullanarak her bir etki alanının nesne sınıfında gereksiz kodunuz olamaz. Bu sınıf türlerinin klasörü, *Framework*gibi bir şey değil *seedwork* olarak adlandırılır. Bu, bir çerçeve olarak kabul edilmeden önce yeniden kullanılabilir sınıfların yalnızca küçük bir alt kümesini içerdiğinden *Seedwork* olarak adlandırılır. *Seedwork* , [Marwler](https://martinfowler.com/bliki/Seedwork.html) tarafından sunulan [Michael feassileri](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) ve populartarafından sunulan bir terimdir, ancak bu klasörün ortak, sharedkernel veya benzer bir şekilde adını da değiştirebilirsiniz.

Şekil 7-12, etki alanı modelinin sıralama mikro hizmetindeki seedwork 'i oluşturan sınıfları gösterir. Varlık, ValueObject ve numaralandırma gibi bazı özel temel sınıflara ek olarak birkaç arabirim vardır. Bu arabirimler (ırepository ve IUnitOfWork) altyapı katmanını uygulanması gerekenler hakkında bilgilendirir. Bu arabirimler, uygulama katmanından bağımlılık ekleme yoluyla da kullanılır.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="SeedWork klasöründe bulunan sınıfların ekran görüntüsü.":::
Temel sınıfları ve arabirimleri içeren SeedWork klasörünün ayrıntılı içeriği: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs ve ValueObject.cs.
:::image-end:::

**Şekil 7-12**. "Seedwork" temel sınıfları ve arabirimleri için örnek bir etki alanı modeli kümesi

Bu, birçok geliştiricinin bir biçimsel çerçeve değil projeler arasında paylaştığı kopyalama ve yapıştırma yeniden kullanımının türüdür. Seedçalışmalardan herhangi bir katmanda veya kitaplıkta sahip olabilirsiniz. Ancak, sınıf ve arabirimlerin kümesi yeterince büyük olursa, tek bir sınıf kitaplığı oluşturmak isteyebilirsiniz.

## <a name="the-custom-entity-base-class"></a>Özel varlık temel sınıfı

Aşağıdaki kod, varlık KIMLIĞI, [eşitlik işleçleri](../../../csharp/language-reference/operators/equality-operators.md), varlık başına bir etki alanı olay listesi vb. gibi herhangi bir etki alanı varlığı tarafından aynı şekilde kullanılabilecek kodu yerleştirebileceğiniz bir varlık temel sınıfı örneğidir.

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

Varlık başına bir etki alanı olay listesi kullanan önceki kod, etki alanı olaylarına odaklanıldığında sonraki bölümlerde açıklanacaktır.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Etki alanı modeli katmanındaki depo sözleşmeleri (arabirimler)

Depo sözleşmeleri, her toplama için kullanılacak depoların sözleşme gereksinimlerini ifade eden .NET arayüzleridir.

Depoların kendisi, EF Core kodla veya başka herhangi bir altyapı bağımlılığı ve kodla (LINQ, SQL vb.), etki alanı modeli içinde uygulanmamalıdır; depolar yalnızca etki alanı modelinde tanımladığınız arabirimleri uygulamalıdır.

Bu yöntemle ilgili bir örüntü (depo arabirimlerini etki alanı model katmanına yerleştirme), ayrılmış arabirim deseninin bir sıdır. Marwler tarafından [açıklandığı](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) gibi, "bir pakette arabirim tanımlamak, ancak başka bir pakette uygulamak Için ayrılmış arabirim kullanın. Bu şekilde, arabirime bağımlılığı gerektiren bir istemci, uygulamanın tamamen farkında olabilir. "

Ayrılmış arabirim deseninin ardından uygulama katmanının (Bu durumda, mikro hizmet için Web API Projesi) etki alanı modelinde tanımlanan gereksinimlere bağımlılığı olması, ancak altyapıya/kalıcılığı doğrudan bağımlılığı yoktur katmanı. Buna ek olarak, havuzları kullanarak altyapı/Kalıcılık katmanında uygulanan uygulamayı yalıtmak için bağımlılık ekleme 'yi de kullanabilirsiniz.

Örneğin, ıorderrepository arabirimine sahip aşağıdaki örnek, OrderRepository sınıfının altyapı katmanında uygulamanız gereken işlemleri tanımlar. Uygulamanın geçerli uygulamasında, sorgular Basitleştirilmiş CQRS yaklaşımını takip altına göre bölündüğü için, bu kodun yalnızca veritabanına sipariş eklemesi veya güncelleştirilmesi gerekir.

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

- **Marwler. Ayrılmış arabirim.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Önceki](net-core-microservice-domain-model.md)
>[İleri](implement-value-objects.md)
