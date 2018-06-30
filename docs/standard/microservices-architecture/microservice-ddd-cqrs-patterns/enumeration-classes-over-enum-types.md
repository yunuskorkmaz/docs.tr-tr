---
title: Numaralandırma türleri yerine numaralandırma sınıflarını kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Numaralandırma türleri yerine numaralandırma sınıflarını kullanma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: eff87dbfad84ba5521f029064115a5fc54ee574b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106116"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="5fd89-103">Numaralandırma türleri yerine numaralandırma sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="5fd89-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="5fd89-104">[Numaralandırmalar](../../../../docs/csharp/language-reference/keywords/enum.md) (veya *enum türleri* kısaca) bir tam sayı türü çevresinde bir ince dil sarmalayıcı şunlardır.</span><span class="sxs-lookup"><span data-stu-id="5fd89-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="5fd89-105">Kapalı bir değerler kümesinden bir değer depolarken kullanımları sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fd89-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="5fd89-106">(Küçük, Orta, büyük) boyutlarına göre sınıflandırma iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="5fd89-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="5fd89-107">Denetim akışı veya daha sağlam soyutlamalar numaralandırmaları kullanmak olabilir bir [kod kokusu](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="5fd89-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="5fd89-108">Bu tür kullanımı kırılacak kodu Enum değerleri denetleme birçok denetim akışı deyimleri ile yol açar.</span><span class="sxs-lookup"><span data-stu-id="5fd89-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="5fd89-109">Bunun yerine, tüm zengin bir nesne yönelimli dil özelliklerini etkinleştirmek numaralandırması sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fd89-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="5fd89-110">Ancak, bu önemli bir konu değildir ve çoğu durumda, kolaylık sağlamak için normal kullanmaya devam edebilirsiniz [enum türleri](../../../../docs/csharp/language-reference/keywords/enum.md) tercihinizi olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="5fd89-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="5fd89-111">Bir numaralandırma taban sınıfı uygulama</span><span class="sxs-lookup"><span data-stu-id="5fd89-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="5fd89-112">Sıralama mikro hizmet eShopOnContainers içinde aşağıdaki örnekte gösterildiği gibi bir örnek numaralandırması temel sınıf uygulamasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="5fd89-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
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

<span data-ttu-id="5fd89-113">Bu sınıf, aşağıdaki CardType numaralandırma sınıfı için olduğu gibi tüm varlık veya değer nesnesindeki türü olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5fd89-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }

    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a><span data-ttu-id="5fd89-114">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5fd89-114">Additional resources</span></span>

-   <span data-ttu-id="5fd89-115">**Enum'ın kötü — güncelleştirme**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="5fd89-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="5fd89-116">**Daniel Hardman. Nasıl numaralandırmaları Hastalık yayılan — Ve onu temizlemeye yönelik nasıl**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="5fd89-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="5fd89-117">**Jimmy Bogard. Numaralandırma sınıfları**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="5fd89-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="5fd89-118">**Steve Smith. C# Enum alternatifleri**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="5fd89-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="5fd89-119">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="5fd89-119">**Enumeration.cs.**</span></span> <span data-ttu-id="5fd89-120">EShopOnContainers temel numaralandırma sınıfında [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="5fd89-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="5fd89-121">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="5fd89-121">**CardType.cs**.</span></span> <span data-ttu-id="5fd89-122">EShopOnContainers örnek numaralandırma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5fd89-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="5fd89-123">[Önceki](implement-value-objects.md)
[sonraki](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="5fd89-123">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
