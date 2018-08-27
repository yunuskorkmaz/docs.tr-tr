---
title: Sabit listesi türleri yerine sabit listesi sınıfları kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Sabit listesi türleri yerine sabit listesi sınıfları kullanma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: f1b88d160d6532c2a768684b55cd236417699322
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933394"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>Sabit listesi türleri yerine sabit listesi sınıfları kullanma

[Numaralandırmalar](../../../../docs/csharp/language-reference/keywords/enum.md) (veya *Numaralandırma türleri* kısaca) basit dil funcınner çevresindeki bir integral türü olan. Kapalı bir değerler kümesinden bir değer depolarken, bunların kullanılması için sınırlamak isteyebilirsiniz. (Küçük, Orta, büyük) boyutlarına göre sınıflandırma iyi bir örnektir. Denetim akışı ya da daha sağlam soyutlama için sabit listeleri kullanarak olabilir bir [kod kokusu](http://deviq.com/code-smells/). Bu tür bir kullanım Enum değerleri denetleme birçok denetim akış deyimlerindeki ile kırılgan koduna yol açar.

Bunun yerine, tüm zengin bir nesne yönelimli dil özelliklerini etkinleştir sabit listesi sınıfları oluşturabilirsiniz.

Ancak, bu önemli bir konu değildir ve çoğu durumda, kolaylık olması için normal kullanmaya devam edebilirsiniz [Numaralandırma türleri](../../../../docs/csharp/language-reference/keywords/enum.md) , tercihinize ise.

## <a name="implementing-an-enumeration-base-class"></a>Bir numaralandırma taban sınıfı uygulama

Aşağıdaki örnekte gösterildiği gibi sıralama mikro hizmetine bir örnek numaralandırması taban sınıf uygulamasını sağlar:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; }
    public int Id { get; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }
    
    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | BindingFlags.Static | BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

Bu sınıf, aşağıdaki CardType sabit listesi sınıfı için tüm varlık veya değer nesnesi türü olarak kullanabilirsiniz:

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    {
    }

    private class AmexCardType : CardType
    {
        public AmexCardType(): base(1, "Amex")
        { }
    }
    
    private class VisaCardType : CardType
    {
        public VisaCardType(): base(2, "Visa")
        { }
    }
    
    private class MasterCardType : CardType
    {
        public MasterCardType(): base(3, "MasterCard")
        { }
    }
}
```

## <a name="additional-resources"></a>Ek kaynaklar

-   **Sabit listesine kötü — güncelleştirme**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Daniel Hardman. Nasıl numaralandırmalar Hastalık yayılan — Ve onu bir temizlemeye yönelik nasıl**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Sabit listesi sınıfları**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. C# sabit listesi alternatifleri**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Hizmetine temel sabit listesi sınıfı [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Hizmetine sabit listesi sınıfı örneği.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Önceki](implement-value-objects.md)
[İleri](domain-model-layer-validations.md)
