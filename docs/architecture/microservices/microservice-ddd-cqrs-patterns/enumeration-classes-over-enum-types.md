---
title: Sabit listesi türleri yerine Sabit Listesi sınıfları kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | İkinci öğesinin bazı sınırlamalarını çözmenin bir yolu olarak, numaralandırmalar yerine numaralandırma sınıflarını nasıl kullanabileceğinizi ortadan kaldırabilirsiniz.
ms.date: 11/25/2020
ms.openlocfilehash: a45347d7cc9c3fc6378198ca1c44ba6fecfd54f5
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899534"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Sabit listesi türleri yerine numaralandırma sınıfları kullanın

[Numaralandırmalar](../../../csharp/language-reference/builtin-types/enum.md) (veya Short için *sabit listesi türleri* ), bir integral türü etrafında ince bir dil sarmalayıcısıdır. Kapalı bir değer kümesinden bir değeri depolarken, kullanımlarını sınırlamak isteyebilirsiniz. Boyutlara göre sınıflandırma (küçük, orta, büyük) iyi bir örnektir. Denetim akışı veya daha güçlü soyutlamalar için Numaralandırmaların kullanılması [kod kokusu](https://deviq.com/antipatterns/code-smells)olabilir. Bu kullanım türü, numaralandırmanın değerlerini denetleyen birçok denetim akışı deyimi ile fragla kodu doğurur.

Bunun yerine, nesne yönelimli bir dilin tüm zengin özelliklerini etkinleştiren numaralandırma sınıfları oluşturabilirsiniz.

Ancak, bu önemli bir konu değildir ve birçok durumda kolaylık sağlaması için, tercih ettiğiniz takdirde normal [numaralandırma türlerini](../../../csharp/language-reference/builtin-types/enum.md) kullanmaya devam edebilirsiniz. Sabit Listesi sınıflarının kullanımı, işle ilgili kavramlarla ilgilidir.

## <a name="implement-an-enumeration-base-class"></a>Numaralandırma temel sınıfı uygulama

EShopOnContainers 'daki sıralama mikro hizmeti, aşağıdaki örnekte gösterildiği gibi bir örnek numaralandırma temel sınıf uygulamasını sağlar:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) => (Id, Name) = (id, name);

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration =>
        typeof(T).GetFields(BindingFlags.Public |
                            BindingFlags.Static |
                            BindingFlags.DeclaredOnly)
                 .Select(f => f.GetValue(null))
                 .Cast<T>();

    public override bool Equals(object obj)
    {
        if (obj is not Enumeration otherValue)
        {
            return false;
        }

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

Bu sınıfı, aşağıdaki gibi herhangi bir varlık veya değer nesnesinde bir tür olarak kullanabilirsiniz: `CardType` `Enumeration` Sınıfı:

```csharp
public class CardType
    : Enumeration
{
    public static CardType Amex = new CardType(1, nameof(Amex));
    public static CardType Visa = new CardType(2, nameof(Visa));
    public static CardType MasterCard = new CardType(3, nameof(MasterCard));

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Ek kaynaklar

- **Jimmy Bogard. Numaralandırma sınıfları** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. C 'de sabit listesi alternatifleri #** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** EShopOnContainers içindeki temel numaralandırma sınıfı \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. EShopOnContainers içinde örnek numaralandırma sınıfı. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **Smartenum**. .NET ' te kesin olarak belirlenmiş daha akıllı numaralandırmalar üretmeye yardımcı olmak için ardın sınıfları. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Önceki](implement-value-objects.md) 
> [Sonraki](domain-model-layer-validations.md)
