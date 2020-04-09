---
title: Seedwork (etki alanı modeliniz için yeniden kullanılabilir kök sınıflar ve arabirimler)
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | DDD yönelimli etki alanı modeli için uygulamayı başlatmak için tohum çalışması kavramını başlangıç noktası olarak kullanın.
ms.date: 10/08/2018
ms.openlocfilehash: 545be2723ba468a5fd65f81978799328234ca113
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988316"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (etki alanı modeliniz için yeniden kullanılabilir kök sınıflar ve arabirimler)

Çözüm klasörü bir *SeedWork* klasörü içerir. Bu klasör, etki alanı varlıklarınız ve değer nesneleriniz için taban olarak kullanabileceğiniz özel taban sınıfları içerir. Her etki alanının nesne sınıfında gereksiz kodunuz olmayacak şekilde bu temel sınıfları kullanın. Bu tür sınıflar için klasör *SeedWork* *değil, Framework*gibi bir şey denir. *SeedWork* olarak adlandırılır, çünkü klasör gerçekten bir çerçeve olarak kabul edilemeyecek yeniden kullanılabilir sınıfların yalnızca küçük bir alt kümesini içerir. *Seedwork* bir terim [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) tarafından tanıtıldı ve [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) tarafından popüler ama aynı zamanda bu klasör Ortak, SharedKernel veya benzer adlandırabilirsiniz.

Şekil 7-12, sipariş mikrohizmetinde etki alanı modelinin tohum çalışmasını oluşturan sınıfları gösterir. Varlık, ValueObject ve Numaralandırma gibi birkaç özel taban sınıfı nın yanı sıra birkaç arabirimi vardır. Bu arabirimler (IRepository ve IUnitOfWork) ne uygulanması gerektiği hakkında altyapı katmanı nı bilgilendirir. Bu arabirimler, uygulama katmanından Bağımlılık Enjeksiyonu ile de kullanılır.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="SeedWork klasöründe bulunan sınıfların ekran görüntüsü.":::
Temel sınıfları ve arabirimleri içeren SeedWork klasörünün ayrıntılı içeriği: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs ve ValueObject.cs.
:::image-end:::

**Şekil 7-12**. Etki alanı modeli "seedwork" temel sınıfları ve arabirimleri örnek kümesi

Bu, birçok geliştiricinin resmi bir çerçeve değil, projeler arasında paylaştığı kopyalama ve yapıştırma türüdür. Herhangi bir katmanda veya kütüphanede tohum işleri olabilir. Ancak, sınıflar ve arabirimler kümesi yeterince büyürse, tek bir sınıf kitaplığı oluşturmak isteyebilirsiniz.

## <a name="the-custom-entity-base-class"></a>Özel Varlık taban sınıfı

Aşağıdaki kod, varlık kimliği, [eşitlik işleçleri,](../../../csharp/language-reference/operators/equality-operators.md)varlık başına etki alanı olay listesi, vb. gibi herhangi bir etki alanı varlığı tarafından aynı şekilde kullanılabilecek kodu yerleştirebileceğiniz varlık taban sınıfının bir örneğidir.

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

Varlık başına bir etki alanı olay listesi kullanan önceki kod, etki alanı olaylarına odaklanırken sonraki bölümlerde açıklanacaktır.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Etki alanı modeli katmanındaki depo sözleşmeleri (arabirimler)

Depo sözleşmeleri, her bir toplam için kullanılacak depoların sözleşme gereksinimlerini ifade eden basitçe .NET arabirimleridir.

EF Core kodu veya diğer altyapı bağımlılıkları ve kodları (Linq, SQL, vb.) ile depoların kendileri etki alanı modeli içinde uygulanmamalıdır; depolar yalnızca etki alanı modelinde tanımladığınız arabirimleri uygulamalıdır.

Bu uygulamayla ilgili bir desen (depo arabirimlerini etki alanı modeli katmanına yerleştirme) Ayrılmış Arabirim desenidir. Martin Fowler tarafından [açıklandığı](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) gibi, "Bir pakette bir arabirim tanımlamak için Ayrılmış Arabirim kullanın ama başka bir uygulama. Bu şekilde arabirime bağımlı bir istemci uygulamadan tamamen habersiz olabilir."

Ayrılmış Arabirim deseni izleyerek uygulama katmanı (bu durumda, mikro hizmet için Web API projesi) etki alanı modelinde tanımlanan gereksinimleri bir bağımlılık var, ancak altyapı / kalıcılık katmanı na doğrudan bağımlılık sağlar. Buna ek olarak, depoları kullanarak altyapı/ kalıcılık katmanında uygulanan uygulamayı yalıtmak için Bağımlılık Enjeksiyonu'nu kullanabilirsiniz.

Örneğin, IOrderRepository arabirimindeki aşağıdaki örnek, OrderRepository sınıfının altyapı katmanında uygulamak için hangi işlemleri gerçekleştirmesi gerekeceğini tanımlar. Basitleştirilmiş CQRS yaklaşımına göre sorgular bölündüğünden, uygulamanın geçerli uygulamasında, kodun veri tabanına sipariş eklemesi veya güncelleştirmesi gerekir.

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

- **Martin Fowler' ı. Ayrılmış Arayüz.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Önceki](net-core-microservice-domain-model.md)
>[Sonraki](implement-value-objects.md)
