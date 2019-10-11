---
title: Genel Arabirimlerde Varyans (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 71225814a11074f52e4937dec88ca5e27114d6c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179056"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="27e39-102">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="27e39-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="27e39-103">.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="27e39-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="27e39-104">Varyans desteği, bu arabirimleri uygulayan sınıfların örtük dönüştürülmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="27e39-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="27e39-105">.NET Framework 4 ' te başlayarak, aşağıdaki arabirimler değişkendir:</span><span class="sxs-lookup"><span data-stu-id="27e39-105">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="27e39-106"><xref:System.Collections.Generic.IEnumerable%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="27e39-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="27e39-107"><xref:System.Collections.Generic.IEnumerator%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="27e39-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="27e39-108"><xref:System.Linq.IQueryable%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="27e39-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="27e39-109"><xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="27e39-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="27e39-110"><xref:System.Collections.Generic.IComparer%601> (T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="27e39-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="27e39-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="27e39-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="27e39-112"><xref:System.IComparable%601> (T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="27e39-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="27e39-113">.NET Framework 4,5 ' den başlayarak, aşağıdaki arabirimler değişkendir:</span><span class="sxs-lookup"><span data-stu-id="27e39-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="27e39-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="27e39-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="27e39-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="27e39-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="27e39-116">Kovaryans, bir metodun, arabirimin genel tür parametresiyle tanımlananla daha türetilmiş bir dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="27e39-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="27e39-117">Kovaryans özelliğini göstermek için şu genel arabirimleri göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="27e39-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="27e39-118">@No__t-0 arabirimi `IEnumerable<Object>` arabirimini almıyor.</span><span class="sxs-lookup"><span data-stu-id="27e39-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="27e39-119">Ancak `String` türü `Object` türünü devralınır ve bazı durumlarda bu arabirimlerin nesnelerini birbirlerine atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27e39-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="27e39-120">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="27e39-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="27e39-121">.NET Framework önceki sürümlerinde, bu kod, ' de `Option Strict` varsa, C# Visual Basic içinde derleme hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="27e39-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="27e39-122">Ancak artık, <xref:System.Collections.Generic.IEnumerable%601> arabirimi birlikte değişken olduğu için, önceki örnekte gösterildiği gibi `objects` yerine `strings` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27e39-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="27e39-123">Değişken Varyans, bir metodun, arabirimin genel parametresiyle belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="27e39-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="27e39-124">Değişken varyansı göstermek için, `BaseClass` sınıfının örneklerini karşılaştırmak üzere bir `BaseComparer` sınıfı oluşturduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="27e39-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="27e39-125">`BaseComparer` sınıfı, `IEqualityComparer<BaseClass>` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="27e39-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="27e39-126">@No__t-0 arabirimi artık değişken karşıtı olduğundan, `BaseClass` sınıfını devraldığı sınıfların örneklerini karşılaştırmak için `BaseComparer` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27e39-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="27e39-127">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="27e39-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="27e39-128">Daha fazla örnek için bkz. [Genel Koleksiyonlar Için Arabirimlerde Varyans kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="27e39-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="27e39-129">Genel Arabirimlerde Varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="27e39-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="27e39-130">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="27e39-130">Value types do not support variance.</span></span> <span data-ttu-id="27e39-131">Örneğin, `IEnumerable<int>` örtük olarak `IEnumerable<object>` ' e dönüştürülemez, çünkü tamsayılar bir değer türü ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="27e39-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="27e39-132">Ayrıca, VARIANT arabirimlerini uygulayan sınıfların hala sabit olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="27e39-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="27e39-133">Örneğin, <xref:System.Collections.Generic.List%601> covaryant arabirimini <xref:System.Collections.Generic.IEnumerable%601> ' i uygularsa, `List<String>` ' yi `List<Object>` ' e örtülü olarak dönüştüremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="27e39-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="27e39-134">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="27e39-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="27e39-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27e39-135">See also</span></span>

- [<span data-ttu-id="27e39-136">Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="27e39-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="27e39-137">Değişken genel arabirimler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="27e39-137">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="27e39-138">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="27e39-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="27e39-139">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="27e39-139">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
