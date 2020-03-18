---
title: Sabit listesi türleri yerine Sabit Listesi sınıfları kullanma
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Lear nasıl numaralandırma sınıfları kullanabilirsiniz, yerine numaralandırma, ikincisi bazı sınırlamaları çözmek için bir yol olarak.
ms.date: 10/08/2018
ms.openlocfilehash: fb2cbcd744f29c70a86e6f3300721934192eb752
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847186"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Enum türleri yerine numaralandırma sınıflarını kullanma

[Sayısallaştırmalar](../../../csharp/language-reference/builtin-types/enum.md) (veya kısaca *şun türleri)* integral bir tür etrafında ince bir dil sarıcıdır. Kapalı bir değer kümesinden bir değer depolarken kullanımlarını sınırlamak isteyebilirsiniz. Boyutlara göre sınıflandırma (küçük, orta, büyük) iyi bir örnektir. Kontrol akışı veya daha sağlam soyutlamalar için enums kullanarak bir [kod kokusu](https://deviq.com/code-smells/)olabilir. Bu tür kullanım, enumun değerlerini kontrol eden birçok kontrol akışı ekstresiyle kırılgan koda yol açar.

Bunun yerine, nesne yönelimli bir dilin tüm zengin özelliklerini etkinleştiren Numaralandırma sınıfları oluşturabilirsiniz.

Ancak, bu kritik bir konu değildir ve birçok durumda, basitlik için, tercihiniz buysa düzenli [enum türlerini](../../../csharp/language-reference/builtin-types/enum.md) kullanmaya devam edebilirsiniz. Her neyse, numaralandırma sınıflarının kullanımı daha çok işle ilgili kavramlarla ilgilidir.

## <a name="implement-an-enumeration-base-class"></a>Numaralandırma taban sınıfı uygulama

eShopOnContainers'daki sipariş microservice, aşağıdaki örnekte gösterildiği gibi örnek bir Numaralandırma taban sınıfı uygulaması sağlar:

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

`CardType` Aşağıdaki: `Enumeration` sınıf gibi, herhangi bir varlık veya değer nesnesinde bu sınıfı bir tür olarak kullanabilirsiniz:

```csharp
public class CardType : Enumeration
{
    public static readonly CardType Amex = new CardType(1, "Amex");
    public static readonly CardType Visa = new CardType(2, "Visa");
    public static readonly CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Ek kaynaklar

- **Jimmy Bogard' ı. Numaralandırma sınıfları** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith' i. C'de Enum Alternatifleri #** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** eShopOnContainers 'da Taban Numaralandırma sınıfı \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs.** Örnek Numaralandırma sınıfı eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis - .NET'te güçlü bir şekilde yazılan akıllı enumların üretilemelerine yardımcı olacak sınıflar. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Önceki](implement-value-objects.md)
>[Sonraki](domain-model-layer-validations.md)
