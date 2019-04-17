---
title: Sabit listesi türleri yerine Sabit Listesi sınıfları kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Temizle nasıl numaralandırma sınıflar, numaralandırmalar yerine, ikincisi bazı sınırlamalar çözmenin bir yolu kullanabilirsiniz.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: d2d4b191ed4cb8f2f8b9b0a34fe99e65d4596a72
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613570"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="3700e-103">Sabit listesi türleri yerine sabit listesi sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="3700e-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="3700e-104">[Numaralandırmalar](../../../../docs/csharp/language-reference/keywords/enum.md) (veya *Numaralandırma türleri* kısaca) basit dil funcınner çevresindeki bir integral türü olan.</span><span class="sxs-lookup"><span data-stu-id="3700e-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="3700e-105">Kapalı bir değerler kümesinden bir değer depolarken, bunların kullanılması için sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3700e-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="3700e-106">(Küçük, Orta, büyük) boyutlarına göre sınıflandırma iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="3700e-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="3700e-107">Denetim akışı ya da daha sağlam soyutlama için sabit listeleri kullanarak olabilir bir [kod kokusu](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="3700e-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="3700e-108">Bu tür bir kullanım Enum değerleri denetleme birçok denetim akış deyimlerindeki ile kırılgan koduna yol açar.</span><span class="sxs-lookup"><span data-stu-id="3700e-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="3700e-109">Bunun yerine, tüm zengin bir nesne yönelimli dil özelliklerini etkinleştir sabit listesi sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3700e-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="3700e-110">Ancak, bu önemli bir konu değildir ve çoğu durumda, kolaylık olması için normal kullanmaya devam edebilirsiniz [Numaralandırma türleri](../../../csharp/language-reference/keywords/enum.md) , tercihinize ise.</span><span class="sxs-lookup"><span data-stu-id="3700e-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/keywords/enum.md) if that's your preference.</span></span> <span data-ttu-id="3700e-111">Yine de sabit listesi sınıfları kullanımı için işle ilgili kavramları daha ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="3700e-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="3700e-112">Bir numaralandırma taban sınıfı uygulama</span><span class="sxs-lookup"><span data-stu-id="3700e-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="3700e-113">Aşağıdaki örnekte gösterildiği gibi sıralama mikro hizmetine bir örnek numaralandırması taban sınıf uygulamasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="3700e-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="3700e-114">Bu sınıf aşağıdaki gibi bir varlık veya değer nesnesindeki bir tür olarak kullanabileceğiniz `CardType` : `Enumeration` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="3700e-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="3700e-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3700e-115">Additional resources</span></span>

- <span data-ttu-id="3700e-116">**Sabit listesine kötü — güncelleştirme** \\</span><span class="sxs-lookup"><span data-stu-id="3700e-116">**Enum’s are evil—update** \\</span></span>
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="3700e-117">**Daniel Hardman. Nasıl numaralandırmalar Hastalık yayılan — Ve onu bir temizlemeye yönelik nasıl** \\</span><span class="sxs-lookup"><span data-stu-id="3700e-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** \\</span></span>
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="3700e-118">**Jimmy Bogard. Sabit listesi sınıfları** \\</span><span class="sxs-lookup"><span data-stu-id="3700e-118">**Jimmy Bogard. Enumeration classes** \\</span></span>
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="3700e-119">**Steve Smith. C# sabit listesi alternatifleri** \\</span><span class="sxs-lookup"><span data-stu-id="3700e-119">**Steve Smith. Enum Alternatives in C#** \\</span></span>
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="3700e-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="3700e-120">**Enumeration.cs.**</span></span> <span data-ttu-id="3700e-121">Sabit listesi sınıfı hizmetine temel \\</span><span class="sxs-lookup"><span data-stu-id="3700e-121">Base Enumeration class in eShopOnContainers \\</span></span>
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="3700e-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="3700e-122">**CardType.cs**.</span></span> <span data-ttu-id="3700e-123">Hizmetine sabit listesi sınıfı örneği.</span><span class="sxs-lookup"><span data-stu-id="3700e-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- <span data-ttu-id="3700e-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="3700e-124">**SmartEnum**.</span></span> <span data-ttu-id="3700e-125">Ardalis - .NET türü kesin belirlenmiş akıllı listelerinde elde etmeye yardımcı sınıflar.</span><span class="sxs-lookup"><span data-stu-id="3700e-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="3700e-126">[Önceki](implement-value-objects.md)
>[İleri](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="3700e-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
