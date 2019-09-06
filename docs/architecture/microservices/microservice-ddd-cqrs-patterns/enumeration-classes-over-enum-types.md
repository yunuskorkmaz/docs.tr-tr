---
title: Sabit listesi türleri yerine Sabit Listesi sınıfları kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | İkinci öğesinin bazı sınırlamalarını çözmenin bir yolu olarak, numaralandırmalar yerine numaralandırma sınıflarını nasıl kullanabileceğinizi ortadan kaldırabilirsiniz.
ms.date: 10/08/2018
ms.openlocfilehash: ba687b700d7a6105baf71aa08a0d888afc9a8ec3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70296862"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="e6e36-103">Sabit listesi türleri yerine numaralandırma sınıfları kullanın</span><span class="sxs-lookup"><span data-stu-id="e6e36-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="e6e36-104">[Numaralandırmalar](../../../csharp/language-reference/keywords/enum.md) (veya Short için *enum Types* ), bir integral türünün çevresindeki bir ince dil sarmalayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="e6e36-104">[Enumerations](../../../csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="e6e36-105">Kapalı bir değer kümesinden bir değeri depolarken, kullanımlarını sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e36-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="e6e36-106">Boyutlara göre sınıflandırma (küçük, orta, büyük) iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e6e36-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="e6e36-107">Denetim akışı veya daha güçlü soyutlamalar için Numaralandırmaların kullanılması [kod kokusu](https://deviq.com/code-smells/)olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6e36-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="e6e36-108">Bu kullanım türü, numaralandırmanın değerlerini denetleyen birçok denetim akışı deyimi ile fragla kodu doğurur.</span><span class="sxs-lookup"><span data-stu-id="e6e36-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="e6e36-109">Bunun yerine, nesne yönelimli bir dilin tüm zengin özelliklerini etkinleştiren numaralandırma sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e36-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="e6e36-110">Ancak, bu önemli bir konu değildir ve birçok durumda kolaylık sağlaması için, tercih ettiğiniz takdirde normal [numaralandırma türlerini](../../../csharp/language-reference/keywords/enum.md) kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e36-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/keywords/enum.md) if that's your preference.</span></span> <span data-ttu-id="e6e36-111">Yine de, sabit listesi sınıflarının kullanımı işle ilgili kavramlarla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="e6e36-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="e6e36-112">Numaralandırma temel sınıfı uygulama</span><span class="sxs-lookup"><span data-stu-id="e6e36-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="e6e36-113">EShopOnContainers 'daki sıralama mikro hizmeti, aşağıdaki örnekte gösterildiği gibi bir örnek numaralandırma temel sınıf uygulamasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="e6e36-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="e6e36-114">Bu sınıfı, aşağıdaki `CardType` `Enumeration` gibi herhangi bir varlık veya değer nesnesinde bir tür olarak kullanabilirsiniz: Sınıfı:</span><span class="sxs-lookup"><span data-stu-id="e6e36-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="e6e36-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e6e36-115">Additional resources</span></span>

- <span data-ttu-id="e6e36-116">**Sabit listesinin Evil olması — güncelleştirme** </span><span class="sxs-lookup"><span data-stu-id="e6e36-116">**Enum’s are evil—update** </span></span>\
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="e6e36-117">**Daniel Hardman. Numaralandırmaların nasıl dağılacağı ve nasıl bulunduğu** </span><span class="sxs-lookup"><span data-stu-id="e6e36-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** </span></span>\
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="e6e36-118">**Jimmy Bogard. Numaralandırma sınıfları** </span><span class="sxs-lookup"><span data-stu-id="e6e36-118">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="e6e36-119">**Steve Smith. İçindeki sabit listesi alternatifleriC#**  </span><span class="sxs-lookup"><span data-stu-id="e6e36-119">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="e6e36-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="e6e36-120">**Enumeration.cs.**</span></span> <span data-ttu-id="e6e36-121">EShopOnContainers içindeki temel numaralandırma sınıfı </span><span class="sxs-lookup"><span data-stu-id="e6e36-121">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="e6e36-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="e6e36-122">**CardType.cs**.</span></span> <span data-ttu-id="e6e36-123">EShopOnContainers içinde örnek numaralandırma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e6e36-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- <span data-ttu-id="e6e36-124">**Smartenum**.</span><span class="sxs-lookup"><span data-stu-id="e6e36-124">**SmartEnum**.</span></span> <span data-ttu-id="e6e36-125">.NET ' te kesin olarak belirlenmiş daha akıllı numaralandırmalar üretmeye yardımcı olmak için ardın sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e6e36-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="e6e36-126">[Önceki](implement-value-objects.md)İleri
>[](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="e6e36-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
