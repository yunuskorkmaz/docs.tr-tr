---
title: Genel Arabirimlerde Varyans (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 2020ea54734724de775192a1a438413a73003d17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169668"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="08ff6-102">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="08ff6-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="08ff6-103">.NET Framework 4, varolan birkaç genel arabirim için varyans desteği sundu.</span><span class="sxs-lookup"><span data-stu-id="08ff6-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="08ff6-104">Varyans desteği, bu arabirimleri uygulayan sınıfların örtülü olarak dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="08ff6-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span>

<span data-ttu-id="08ff6-105">.NET Framework 4 ile başlayarak, aşağıdaki arabirimler değişkendir:</span><span class="sxs-lookup"><span data-stu-id="08ff6-105">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="08ff6-106"><xref:System.Collections.Generic.IEnumerable%601>(T eşdeğişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="08ff6-107"><xref:System.Collections.Generic.IEnumerator%601>(T eşdeğişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="08ff6-108"><xref:System.Linq.IQueryable%601>(T eşdeğişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="08ff6-109"><xref:System.Linq.IGrouping%602>(`TKey` `TElement` ve eşdeğişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="08ff6-110"><xref:System.Collections.Generic.IComparer%601>(T zıt değişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="08ff6-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T zıt değişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="08ff6-112"><xref:System.IComparable%601>(T zıt değişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="08ff6-113">.NET Framework 4.5 ile başlayarak, aşağıdaki arabirimler değişkendir:</span><span class="sxs-lookup"><span data-stu-id="08ff6-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="08ff6-114"><xref:System.Collections.Generic.IReadOnlyList%601>(T eşdeğişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="08ff6-115"><xref:System.Collections.Generic.IReadOnlyCollection%601>(T eşdeğişkendir)</span><span class="sxs-lookup"><span data-stu-id="08ff6-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="08ff6-116">Covariance, bir yöntemin arabirimin genel türü parametresi tarafından tanımlanandan daha türetilmiş bir iade türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="08ff6-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="08ff6-117">Tutarlılık özelliğini göstermek için, bu genel arabirimleri göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="08ff6-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="08ff6-118">`IEnumerable<Object>` Arabirim, `IEnumerable<String>` arabirimi devralmaz.</span><span class="sxs-lookup"><span data-stu-id="08ff6-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="08ff6-119">Ancak, `String` `Object` tür türü devralmak yok ve bazı durumlarda bu arabirimlerin nesneleri birbirlerine atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ff6-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="08ff6-120">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="08ff6-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="08ff6-121">.NET Framework'ün önceki sürümlerinde, bu kod C#'da `Option Strict` ve üzerindeyse Visual Basic'te bir derleme hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="08ff6-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="08ff6-122">Ancak `strings` `objects`şimdi, <xref:System.Collections.Generic.IEnumerable%601> önceki örnekte gösterildiği gibi, arabirim ortak olduğundan, bunun yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ff6-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="08ff6-123">Kontravariance, arabirimin genel parametresi tarafından belirtilenden daha az türemiş bağımsız değişken türlerine sahip bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="08ff6-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="08ff6-124">Kontraşeyi göstermek için, sınıfın örneklerini `BaseComparer` karşılaştırmak için bir `BaseClass` sınıf oluşturduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="08ff6-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="08ff6-125">`BaseComparer` sınıfı, `IEqualityComparer<BaseClass>` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="08ff6-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="08ff6-126"><xref:System.Collections.Generic.IEqualityComparer%601> Arabirim artık karşıt olduğundan, `BaseComparer` `BaseClass` sınıfı devralan sınıf örneklerini karşılaştırmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ff6-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="08ff6-127">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="08ff6-127">This is shown in the following code example.</span></span>

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

<span data-ttu-id="08ff6-128">Daha fazla örnek için bkz: [Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="08ff6-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="08ff6-129">Genel arabirimlerdeki varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="08ff6-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="08ff6-130">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="08ff6-130">Value types do not support variance.</span></span> <span data-ttu-id="08ff6-131">Örneğin, `IEnumerable<int>` tamsayılar bir değer `IEnumerable<object>`türü tarafından temsil edildiğinden, dolaylı olarak dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="08ff6-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="08ff6-132">Varyant arabirimleri uygulayan sınıfların hala değişmez olduğunu da unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="08ff6-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="08ff6-133">Örneğin, ortak <xref:System.Collections.Generic.List%601> değişken <xref:System.Collections.Generic.IEnumerable%601>arabirimi uygulasa da, `List<String>` `List<Object>`örtülü olarak .</span><span class="sxs-lookup"><span data-stu-id="08ff6-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="08ff6-134">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="08ff6-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="08ff6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08ff6-135">See also</span></span>

- [<span data-ttu-id="08ff6-136">Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="08ff6-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="08ff6-137">Varyant Genel Arabirimler Oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="08ff6-137">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="08ff6-138">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="08ff6-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="08ff6-139">Temsilcilerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="08ff6-139">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
