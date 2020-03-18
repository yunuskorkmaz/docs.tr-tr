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
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="f5755-103">Enum türleri yerine numaralandırma sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="f5755-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="f5755-104">[Sayısallaştırmalar](../../../csharp/language-reference/builtin-types/enum.md) (veya kısaca *şun türleri)* integral bir tür etrafında ince bir dil sarıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f5755-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="f5755-105">Kapalı bir değer kümesinden bir değer depolarken kullanımlarını sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5755-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="f5755-106">Boyutlara göre sınıflandırma (küçük, orta, büyük) iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f5755-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="f5755-107">Kontrol akışı veya daha sağlam soyutlamalar için enums kullanarak bir [kod kokusu](https://deviq.com/code-smells/)olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5755-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="f5755-108">Bu tür kullanım, enumun değerlerini kontrol eden birçok kontrol akışı ekstresiyle kırılgan koda yol açar.</span><span class="sxs-lookup"><span data-stu-id="f5755-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="f5755-109">Bunun yerine, nesne yönelimli bir dilin tüm zengin özelliklerini etkinleştiren Numaralandırma sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5755-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="f5755-110">Ancak, bu kritik bir konu değildir ve birçok durumda, basitlik için, tercihiniz buysa düzenli [enum türlerini](../../../csharp/language-reference/builtin-types/enum.md) kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5755-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="f5755-111">Her neyse, numaralandırma sınıflarının kullanımı daha çok işle ilgili kavramlarla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="f5755-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="f5755-112">Numaralandırma taban sınıfı uygulama</span><span class="sxs-lookup"><span data-stu-id="f5755-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="f5755-113">eShopOnContainers'daki sipariş microservice, aşağıdaki örnekte gösterildiği gibi örnek bir Numaralandırma taban sınıfı uygulaması sağlar:</span><span class="sxs-lookup"><span data-stu-id="f5755-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="f5755-114">`CardType` Aşağıdaki: `Enumeration` sınıf gibi, herhangi bir varlık veya değer nesnesinde bu sınıfı bir tür olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5755-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="f5755-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f5755-115">Additional resources</span></span>

- <span data-ttu-id="f5755-116">**Jimmy Bogard' ı. Numaralandırma sınıfları** </span><span class="sxs-lookup"><span data-stu-id="f5755-116">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="f5755-117">**Steve Smith' i. C'de Enum Alternatifleri #** </span><span class="sxs-lookup"><span data-stu-id="f5755-117">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="f5755-118">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="f5755-118">**Enumeration.cs.**</span></span> <span data-ttu-id="f5755-119">eShopOnContainers 'da Taban Numaralandırma sınıfı </span><span class="sxs-lookup"><span data-stu-id="f5755-119">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="f5755-120">**CardType.cs.**</span><span class="sxs-lookup"><span data-stu-id="f5755-120">**CardType.cs**.</span></span> <span data-ttu-id="f5755-121">Örnek Numaralandırma sınıfı eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f5755-121">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="f5755-122">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="f5755-122">**SmartEnum**.</span></span> <span data-ttu-id="f5755-123">Ardalis - .NET'te güçlü bir şekilde yazılan akıllı enumların üretilemelerine yardımcı olacak sınıflar.</span><span class="sxs-lookup"><span data-stu-id="f5755-123">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="f5755-124">[Önceki](implement-value-objects.md)
>[Sonraki](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="f5755-124">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
