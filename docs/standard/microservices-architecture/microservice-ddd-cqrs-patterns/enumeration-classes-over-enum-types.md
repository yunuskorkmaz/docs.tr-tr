---
title: Sabit listesi türleri yerine sabit listesi sınıfları kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Sabit listesi türleri yerine sabit listesi sınıfları kullanma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: f1b88d160d6532c2a768684b55cd236417699322
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195000"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="68f36-103">Sabit listesi türleri yerine sabit listesi sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="68f36-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="68f36-104">[Numaralandırmalar](../../../../docs/csharp/language-reference/keywords/enum.md) (veya *Numaralandırma türleri* kısaca) basit dil funcınner çevresindeki bir integral türü olan.</span><span class="sxs-lookup"><span data-stu-id="68f36-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="68f36-105">Kapalı bir değerler kümesinden bir değer depolarken, bunların kullanılması için sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68f36-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="68f36-106">(Küçük, Orta, büyük) boyutlarına göre sınıflandırma iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="68f36-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="68f36-107">Denetim akışı ya da daha sağlam soyutlama için sabit listeleri kullanarak olabilir bir [kod kokusu](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="68f36-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="68f36-108">Bu tür bir kullanım Enum değerleri denetleme birçok denetim akış deyimlerindeki ile kırılgan koduna yol açar.</span><span class="sxs-lookup"><span data-stu-id="68f36-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="68f36-109">Bunun yerine, tüm zengin bir nesne yönelimli dil özelliklerini etkinleştir sabit listesi sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68f36-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="68f36-110">Ancak, bu önemli bir konu değildir ve çoğu durumda, kolaylık olması için normal kullanmaya devam edebilirsiniz [Numaralandırma türleri](../../../../docs/csharp/language-reference/keywords/enum.md) , tercihinize ise.</span><span class="sxs-lookup"><span data-stu-id="68f36-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="68f36-111">Bir numaralandırma taban sınıfı uygulama</span><span class="sxs-lookup"><span data-stu-id="68f36-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="68f36-112">Aşağıdaki örnekte gösterildiği gibi sıralama mikro hizmetine bir örnek numaralandırması taban sınıf uygulamasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="68f36-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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
    
    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | BindingFlags.Static | BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
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

<span data-ttu-id="68f36-113">Bu sınıf, aşağıdaki CardType sabit listesi sınıfı için tüm varlık veya değer nesnesi türü olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68f36-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    {
    }

    private class AmexCardType : CardType
    {
        public AmexCardType(): base(1, "Amex")
        { }
    }
    
    private class VisaCardType : CardType
    {
        public VisaCardType(): base(2, "Visa")
        { }
    }
    
    private class MasterCardType : CardType
    {
        public MasterCardType(): base(3, "MasterCard")
        { }
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="68f36-114">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="68f36-114">Additional resources</span></span>

-   <span data-ttu-id="68f36-115">**Sabit listesine kötü — güncelleştirme**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="68f36-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="68f36-116">**Daniel Hardman. Nasıl numaralandırmalar Hastalık yayılan — Ve onu bir temizlemeye yönelik nasıl**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="68f36-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="68f36-117">**Jimmy Bogard. Sabit listesi sınıfları**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="68f36-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="68f36-118">**Steve Smith. C# sabit listesi alternatifleri**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="68f36-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="68f36-119">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="68f36-119">**Enumeration.cs.**</span></span> <span data-ttu-id="68f36-120">Hizmetine temel sabit listesi sınıfı [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="68f36-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="68f36-121">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="68f36-121">**CardType.cs**.</span></span> <span data-ttu-id="68f36-122">Hizmetine sabit listesi sınıfı örneği.</span><span class="sxs-lookup"><span data-stu-id="68f36-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="68f36-123">[Önceki](implement-value-objects.md)
[İleri](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="68f36-123">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
