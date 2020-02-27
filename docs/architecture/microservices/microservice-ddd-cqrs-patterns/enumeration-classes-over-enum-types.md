---
title: Sabit listesi türleri yerine Sabit Listesi sınıfları kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | İkinci öğesinin bazı sınırlamalarını çözmenin bir yolu olarak, numaralandırmalar yerine numaralandırma sınıflarını nasıl kullanabileceğinizi ortadan kaldırabilirsiniz.
ms.date: 10/08/2018
ms.openlocfilehash: 82bd80d19b3b73eb2f45ede8cc7ad4593c688277
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628468"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Sabit listesi türleri yerine numaralandırma sınıfları kullanın

[Numaralandırmalar](../../../csharp/language-reference/builtin-types/enum.md) (veya Short için *sabit listesi türleri* ), bir integral türü etrafında ince bir dil sarmalayıcısıdır. Kapalı bir değer kümesinden bir değeri depolarken, kullanımlarını sınırlamak isteyebilirsiniz. Boyutlara göre sınıflandırma (küçük, orta, büyük) iyi bir örnektir. Denetim akışı veya daha güçlü soyutlamalar için Numaralandırmaların kullanılması [kod kokusu](https://deviq.com/code-smells/)olabilir. Bu kullanım türü, numaralandırmanın değerlerini denetleyen birçok denetim akışı deyimi ile fragla kodu doğurur.

Bunun yerine, nesne yönelimli bir dilin tüm zengin özelliklerini etkinleştiren numaralandırma sınıfları oluşturabilirsiniz.

Ancak, bu önemli bir konu değildir ve birçok durumda kolaylık sağlaması için, tercih ettiğiniz takdirde normal [numaralandırma türlerini](../../../csharp/language-reference/builtin-types/enum.md) kullanmaya devam edebilirsiniz. Yine de, sabit listesi sınıflarının kullanımı işle ilgili kavramlarla ilgilidir.

## <a name="implement-an-enumeration-base-class"></a>Numaralandırma temel sınıfı uygulama

EShopOnContainers 'daki sıralama mikro hizmeti, aşağıdaki örnekte gösterildiği gibi bir örnek numaralandırma temel sınıf uygulamasını sağlar:

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

Bu sınıfı, aşağıdaki `CardType` gibi, herhangi bir varlık veya değer nesnesinde bir tür olarak kullanabilirsiniz: `Enumeration` Sınıfı:

```csharp
public class CardType : Enumeration
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

- **Jimmy Bogard. Numaralandırma sınıfları** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. \ sabit listesi C# alternatifleri**
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** EShopOnContainers içindeki temel numaralandırma sınıfı \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. EShopOnContainers içinde örnek numaralandırma sınıfı. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **Smartenum**. .NET ' te kesin olarak belirlenmiş daha akıllı numaralandırmalar üretmeye yardımcı olmak için ardın sınıfları. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Önceki](implement-value-objects.md)
>[İleri](domain-model-layer-validations.md)
