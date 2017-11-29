---
title: "Numaralandırma türleri yerine numaralandırma sınıflarını kullanma"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Numaralandırma türleri yerine numaralandırma sınıflarını kullanma"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1745198720fd12a9d26aab2d2afb2c5dd6b6b49d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="9c579-104">Numaralandırma türleri yerine numaralandırma sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="9c579-104">Using Enumeration classes instead of enum types</span></span>

<span data-ttu-id="9c579-105">[Numaralandırmalar](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*numaralandırmaları* kısaca) bir tam sayı türü çevresinde bir ince dil sarmalayıcı şunlardır.</span><span class="sxs-lookup"><span data-stu-id="9c579-105">[Enumerations](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="9c579-106">Kapalı bir değerler kümesinden bir değer depolarken kullanımları sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c579-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="9c579-107">Cinsiyeti (örneğin, erkek, kadın, bilinmeyen) veya boyutları (S, M, L, XL) temel alan sınıflandırma iyi örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9c579-107">Classification based on gender (for example, male, female, unknown), or sizes (S, M, L, XL) are good examples.</span></span> <span data-ttu-id="9c579-108">Denetim akışı veya daha sağlam soyutlamalar numaralandırmaları kullanmak olabilir bir [kod kokusu](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="9c579-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="9c579-109">Bu tür kullanımı kırılacak kodu Enum değerleri denetleme birçok denetim akışı deyimleri ile götürür.</span><span class="sxs-lookup"><span data-stu-id="9c579-109">This type of usage will lead to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="9c579-110">Bunun yerine, tüm zengin bir nesne yönelimli dil özelliklerini etkinleştirmek numaralandırması sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c579-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span> <span data-ttu-id="9c579-111">Ancak, bu kritik bir sorun değildir ve tercihinizi ise, çoğu durumda, kolaylık sağlamak için normal numaralandırmaları kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c579-111">However, this is not a critical issue and in many cases, for simplicity, you can still use regular enums if that is your preference.</span></span>

## <a name="implementing-enumeration-classes"></a><span data-ttu-id="9c579-112">Numaralandırma sınıflarını uygulama</span><span class="sxs-lookup"><span data-stu-id="9c579-112">Implementing Enumeration classes</span></span>

<span data-ttu-id="9c579-113">Sıralama mikro hizmet eShopOnContainers içinde aşağıdaki örnekte gösterildiği gibi bir örnek numaralandırması temel sınıf uygulamasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="9c579-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

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

<span data-ttu-id="9c579-114">Bu sınıf, aşağıdaki CardType numaralandırma sınıfı için olduğu gibi tüm varlık veya değer nesnesindeki türü olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c579-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="9c579-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9c579-115">Additional resources</span></span>

-   <span data-ttu-id="9c579-116">**Enum'ın kötü — güncelleştirme**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="9c579-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="9c579-117">**Daniel Hardman. Nasıl numaralandırmaları Hastalık yayılan — Ve onu temizlemeye yönelik nasıl**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="9c579-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="9c579-118">**Jimmy Bogard. Numaralandırma sınıflarını**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="9c579-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="9c579-119">**Steve Smith. C# Enum alternatifleri**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="9c579-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="9c579-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="9c579-120">**Enumeration.cs.**</span></span> <span data-ttu-id="9c579-121">EShopOnContainers numaralandırma sınıfında temel [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="9c579-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="9c579-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="9c579-122">**CardType.cs**.</span></span> <span data-ttu-id="9c579-123">EShopOnContainers örnek numaralandırma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9c579-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [<span data-ttu-id="9c579-124">*https://github.com/dotnet/eShopOnContainers/BLOB/master/src/Services/Ordering/Ordering.domain/AggregatesModel/BuyerAggregate/CardType.cs*</span><span class="sxs-lookup"><span data-stu-id="9c579-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="9c579-125">[Önceki] (uygulama-değer-objects.md) [sonraki] (etki alanı-model-katman-validations.md)</span><span class="sxs-lookup"><span data-stu-id="9c579-125">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
