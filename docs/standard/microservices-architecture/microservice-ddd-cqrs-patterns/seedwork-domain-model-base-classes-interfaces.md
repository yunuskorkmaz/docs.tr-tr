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
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (yeniden kullanılabilir temel sınıflar ve arabirimler etki alanı modeliniz için)

Çözüm klasörü içeren bir *SeedWork* klasör. *SeedWork* klasörü etki alanı varlıkları ve değer nesneler için temel olarak kullanabileceğiniz özel temel sınıflar içerir. Temel sınıflar kullandığından, her etki alanının nesne sınıfında yedekli koduna sahip değil. Bu tür sınıflar için klasör adında *SeedWork* bir şey yok gibi ve *Framework*. Çağrılır *SeedWork* bir çerçeve gerçekten kabul edilemez yeniden kullanılabilir sınıfların yalnızca küçük bir alt klasör içerdiği için. *Seedwork* bir terim tarafından sunulan [Michael geçiş yumuşatma](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) ve tarafından popularized [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) ancak bu klasöre ortak SharedKernel, ad veya benzer.

Şekil 9-12 sıralama mikro hizmet içinde etki alanı modeli seedwork form sınıflarını gösterir. Varlık, ValueObject ve numaralandırma gibi birkaç özel taban sınıfları yanı sıra, birkaç arabirimleri vardır. Bu arabirimleri (IRepository ve IUnitOfWork) uygulanması gerekenler hakkında altyapısı katmanından bildirin. Bu arabirimleri de uygulama katmanı bağımlılık ekleme kullanılır.

![](./media/image13.PNG)

**Şekil 9-12**. Örnek bir etki alanı modeli "seedwork" temel sınıfları ve arabirimleri ayarlayın

Çoğu geliştiricinin bir resmi framework projeler arasında paylaşmak Kopyala ve Yapıştır yeniden türüdür. Herhangi bir katman veya kitaplık seedworks olabilir. Ancak, sınıflar ve arabirimler kümesi yeterince büyük alırsa, bir tek sınıf kitaplığı oluşturmak isteyebilirsiniz.

## <a name="the-custom-entity-base-class"></a>Özel varlık taban sınıfı

Aşağıdaki kod bir varlık temel sınıfı aynı şekilde varlık kimliği gibi herhangi bir etki alanı varlık tarafından kullanılan kod burada yerleştirebilirsiniz örneğidir [eşitlik işleçleri](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), varlık, vb. bir etki alanı olay listesi.

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

Varlık başına etki alanı olay listesini kullanarak önceki kod, etki alanı olaylarına odaklanan olduğunda sonraki bölümlerde açıklanacaktır. 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Etki alanı modeli katmanda deposu sözleşmeleri (arabirimi)

Depo sözleşmeleri yalnızca her toplama için kullanılacak depoları sözleşme gereksinimlerini express .NET arabirimlerdir. 

EF çekirdek kodu veya diğer altyapı bağımlılıkları ve kod (LINQ, SQL, vb.) ile depoları kendileri içinde etki alanı modeli uygulanmalı değil; depoları tanımladığınız arabirimleri yalnızca uygulamanız gerekir. 

(Etki alanı modeli katmanda deposu arabirimleri yerleştirerek) bu uygulama için ilgili bir desen ayrılmış arabirimi düzeni ' dir. Olarak [açıklandığı](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler "bir arabirim birinde tanımlamak için kullanım ayrılmış arabirimi paketini ancak başka bir programda uygulamak. Bu şekilde arabirimi bağımlılığı gerektiren bir istemci uygulaması tamamen farkında olabilir."

Ayrılmış arabirimi desen aşağıdaki uygulama katmanında (Bu durumda, Web API projesi mikro hizmet için) etki alanı modelinde tanımlanan gereksinimlerle bir bağımlılığı ancak altyapı/Kalıcılık değil doğrudan bir bağımlılığa sahip olmasını sağlar katmanı. Ayrıca, altyapısında uygulanan uygulama yalıtmak için bağımlılık ekleme kullanabilirsiniz / saklama katmanını kullanarak depoları.

Örneğin, aşağıdaki örnekte IOrderRepository arabirimiyle OrderRepository sınıfın altyapı katmanında uygulamak için ihtiyaç duyacağı hangi işlemlerin tanımlar. Uygulama geçerli uygulama, kod eklemek veya sorguları Basitleştirilmiş CQRS yaklaşımı izleyerek bölünür beri siparişleri veritabanına güncelleştirmek yalnızca gerekir.

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

-   **Martin Fowler. Ayrılmış arabirimi. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)


>[!div class="step-by-step"]
[Önceki] (net-core-mikro hizmet-etki-model.md) [sonraki] (uygulama değeri objects.md)
