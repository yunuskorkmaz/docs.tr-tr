---
title: Sabit listesi türleri yerine Sabit Listesi sınıfları kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Temizle nasıl numaralandırma sınıflar, numaralandırmalar yerine, ikincisi bazı sınırlamalar çözmenin bir yolu kullanabilirsiniz.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: d2d4b191ed4cb8f2f8b9b0a34fe99e65d4596a72
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61818020"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Sabit listesi türleri yerine sabit listesi sınıfları kullanma

[Numaralandırmalar](../../../../docs/csharp/language-reference/keywords/enum.md) (veya *Numaralandırma türleri* kısaca) basit dil funcınner çevresindeki bir integral türü olan. Kapalı bir değerler kümesinden bir değer depolarken, bunların kullanılması için sınırlamak isteyebilirsiniz. (Küçük, Orta, büyük) boyutlarına göre sınıflandırma iyi bir örnektir. Denetim akışı ya da daha sağlam soyutlama için sabit listeleri kullanarak olabilir bir [kod kokusu](https://deviq.com/code-smells/). Bu tür bir kullanım Enum değerleri denetleme birçok denetim akış deyimlerindeki ile kırılgan koduna yol açar.

Bunun yerine, tüm zengin bir nesne yönelimli dil özelliklerini etkinleştir sabit listesi sınıfları oluşturabilirsiniz.

Ancak, bu önemli bir konu değildir ve çoğu durumda, kolaylık olması için normal kullanmaya devam edebilirsiniz [Numaralandırma türleri](../../../csharp/language-reference/keywords/enum.md) , tercihinize ise. Yine de sabit listesi sınıfları kullanımı için işle ilgili kavramları daha ilişkilidir.

## <a name="implement-an-enumeration-base-class"></a>Bir numaralandırma taban sınıfı uygulama

Aşağıdaki örnekte gösterildiği gibi sıralama mikro hizmetine bir örnek numaralandırması taban sınıf uygulamasını sağlar:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) 
    {
        Id = id; 
        Name = name; 
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | 
                                         BindingFlags.Static | 
                                         BindingFlags.DeclaredOnly); 

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj) 
    {
        var otherValue = obj as Enumeration; 

        if (otherValue == null) 
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id); 

    // Other utility methods ... 
}
```

Bu sınıf aşağıdaki gibi bir varlık veya değer nesnesindeki bir tür olarak kullanabileceğiniz `CardType` : `Enumeration` sınıfı:

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Ek kaynaklar

- **Sabit listesine kötü — güncelleştirme** \
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- **Daniel Hardman. Nasıl numaralandırmalar Hastalık yayılan — Ve onu bir temizlemeye yönelik nasıl** \
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- **Jimmy Bogard. Sabit listesi sınıfları** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. C# sabit listesi alternatifleri** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Sabit listesi sınıfı hizmetine temel \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Hizmetine sabit listesi sınıfı örneği. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- **SmartEnum**. Ardalis - .NET türü kesin belirlenmiş akıllı listelerinde elde etmeye yardımcı sınıflar. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Önceki](implement-value-objects.md)
>[İleri](domain-model-layer-validations.md)
