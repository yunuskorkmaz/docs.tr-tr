---
title: Numaralandırma türleri yerine numaralandırma sınıflarını kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Numaralandırma türleri yerine numaralandırma sınıflarını kullanma
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 57ff60ea01421f1a2a0466b7de9716b72b02d2c1
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="df01f-104">Numaralandırma türleri yerine numaralandırma sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="df01f-104">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="df01f-105">[Numaralandırmalar](../../../../docs/csharp/language-reference/keywords/enum.md) (veya *enum türleri* kısaca) bir tam sayı türü çevresinde bir ince dil sarmalayıcı şunlardır.</span><span class="sxs-lookup"><span data-stu-id="df01f-105">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="df01f-106">Kapalı bir değerler kümesinden bir değer depolarken kullanımları sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df01f-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="df01f-107">Cinsiyeti (örneğin, erkek, kadın, bilinmeyen) veya boyutları (küçük, Orta, büyük) temel alan sınıflandırma iyi örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df01f-107">Classification based on gender (for example, male, female, unknown) or sizes (small, medium, large) are good examples.</span></span> <span data-ttu-id="df01f-108">Denetim akışı veya daha sağlam soyutlamalar numaralandırmaları kullanmak olabilir bir [kod kokusu](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="df01f-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="df01f-109">Bu tür kullanımı kırılacak kodu Enum değerleri denetleme birçok denetim akışı deyimleri ile yol açar.</span><span class="sxs-lookup"><span data-stu-id="df01f-109">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="df01f-110">Bunun yerine, tüm zengin bir nesne yönelimli dil özelliklerini etkinleştirmek numaralandırması sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df01f-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="df01f-111">Ancak, bu önemli bir konu değildir ve çoğu durumda, kolaylık sağlamak için normal kullanmaya devam edebilirsiniz [enum türleri](../../../../docs/csharp/language-reference/keywords/enum.md) tercihinizi olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="df01f-111">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="df01f-112">Bir numaralandırma taban sınıfı uygulama</span><span class="sxs-lookup"><span data-stu-id="df01f-112">Implementing an Enumeration base class</span></span>

<span data-ttu-id="df01f-113">Sıralama mikro hizmet eShopOnContainers içinde aşağıdaki örnekte gösterildiği gibi bir örnek numaralandırması temel sınıf uygulamasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="df01f-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="df01f-114">Bu sınıf, aşağıdaki CardType numaralandırma sınıfı için olduğu gibi tüm varlık veya değer nesnesindeki türü olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df01f-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="df01f-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="df01f-115">Additional resources</span></span>

-   <span data-ttu-id="df01f-116">**Enum'ın kötü — güncelleştirme**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="df01f-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="df01f-117">**Daniel Hardman. Nasıl numaralandırmaları Hastalık yayılan — Ve onu temizlemeye yönelik nasıl**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="df01f-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="df01f-118">**Jimmy Bogard. Numaralandırma sınıfları**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="df01f-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="df01f-119">**Steve Smith. C# Enum alternatifleri**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="df01f-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="df01f-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="df01f-120">**Enumeration.cs.**</span></span> <span data-ttu-id="df01f-121">EShopOnContainers temel numaralandırma sınıfında [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="df01f-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="df01f-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="df01f-122">**CardType.cs**.</span></span> <span data-ttu-id="df01f-123">EShopOnContainers örnek numaralandırma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="df01f-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="df01f-124">[Önceki] (uygulama-değer-objects.md) [sonraki] (etki alanı-model-katman-validations.md)</span><span class="sxs-lookup"><span data-stu-id="df01f-124">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
