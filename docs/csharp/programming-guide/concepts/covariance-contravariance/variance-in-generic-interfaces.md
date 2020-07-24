---
title: Genel Arabirimlerde Varyans (C#)
description: .NET Framework 4 ve 4,5 ' deki mevcut arabirimlerin güncelleştirilmiş bilgileri de dahil olmak üzere genel arabirimlerin fark desteği bilgilerini görüntüleyin.
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 91218742c01eeb6e65ea26d9dc41ed7c98827377
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105637"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="ce5a5-103">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-103">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="ce5a5-104">.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-104">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="ce5a5-105">Varyans desteği, bu arabirimleri uygulayan sınıfların örtük dönüştürülmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-105">Variance support enables implicit conversion of classes that implement these interfaces.</span></span>

<span data-ttu-id="ce5a5-106">.NET Framework 4 ' te başlayarak, aşağıdaki arabirimler değişkendir:</span><span class="sxs-lookup"><span data-stu-id="ce5a5-106">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="ce5a5-107"><xref:System.Collections.Generic.IEnumerable%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-107"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="ce5a5-108"><xref:System.Collections.Generic.IEnumerator%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-108"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="ce5a5-109"><xref:System.Linq.IQueryable%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-109"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="ce5a5-110"><xref:System.Linq.IGrouping%602>( `TKey` ve `TElement` değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-110"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="ce5a5-111"><xref:System.Collections.Generic.IComparer%601>(T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-111"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="ce5a5-112"><xref:System.Collections.Generic.IEqualityComparer%601>(T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-112"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="ce5a5-113"><xref:System.IComparable%601>(T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-113"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="ce5a5-114">.NET Framework 4,5 ' den başlayarak, aşağıdaki arabirimler değişkendir:</span><span class="sxs-lookup"><span data-stu-id="ce5a5-114">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="ce5a5-115"><xref:System.Collections.Generic.IReadOnlyList%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-115"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="ce5a5-116"><xref:System.Collections.Generic.IReadOnlyCollection%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-116"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="ce5a5-117">Kovaryans, bir metodun, arabirimin genel tür parametresiyle tanımlananla daha türetilmiş bir dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-117">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="ce5a5-118">Kovaryans özelliğini göstermek için şu genel arabirimleri göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>` .</span><span class="sxs-lookup"><span data-stu-id="ce5a5-118">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="ce5a5-119">`IEnumerable<String>`Arabirim, `IEnumerable<Object>` arabirimini almıyor.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-119">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="ce5a5-120">Ancak, `String` tür devralınır `Object` ve bazı durumlarda bu arabirimlerin nesnelerini birbirlerine atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-120">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="ce5a5-121">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-121">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="ce5a5-122">.NET Framework önceki sürümlerinde, bu kod C# ' de derleme hatasına ve açık ise Visual Basic ' a neden olur `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="ce5a5-122">In earlier versions of .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="ce5a5-123">Ancak, bu, `strings` `objects` Önceki örnekte gösterildiği gibi yerine kullanabilirsiniz, çünkü <xref:System.Collections.Generic.IEnumerable%601> arabirim değişkenle birlikte değişkendir.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-123">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="ce5a5-124">Değişken Varyans, bir metodun, arabirimin genel parametresiyle belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-124">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="ce5a5-125">Değişken varyansı göstermek için, `BaseComparer` sınıfının örneklerini karşılaştırmak üzere bir sınıf oluşturduğunuzu varsayalım `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="ce5a5-125">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="ce5a5-126">`BaseComparer` sınıfı, `IEqualityComparer<BaseClass>` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-126">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="ce5a5-127">Arabirim artık değişken karşıtı olduğundan <xref:System.Collections.Generic.IEqualityComparer%601> , `BaseComparer` sınıfı miras alan sınıfların örneklerini karşılaştırmak için kullanabilirsiniz `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="ce5a5-127">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="ce5a5-128">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-128">This is shown in the following code example.</span></span>

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

<span data-ttu-id="ce5a5-129">Daha fazla örnek için bkz. [Genel Koleksiyonlar Için Arabirimlerde Varyans kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="ce5a5-129">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="ce5a5-130">Genel Arabirimlerde Varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-130">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="ce5a5-131">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-131">Value types do not support variance.</span></span> <span data-ttu-id="ce5a5-132">Örneğin, `IEnumerable<int>` `IEnumerable<object>` tamsayılar bir değer türü tarafından temsil edildiği için örtük olarak öğesine dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-132">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="ce5a5-133">Ayrıca, VARIANT arabirimlerini uygulayan sınıfların hala sabit olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-133">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="ce5a5-134">Örneğin, <xref:System.Collections.Generic.List%601> covaryant arabirimini uygular <xref:System.Collections.Generic.IEnumerable%601> , ancak öğesini örtülü olarak dönüştüremezsiniz `List<String>` `List<Object>` .</span><span class="sxs-lookup"><span data-stu-id="ce5a5-134">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="ce5a5-135">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-135">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="ce5a5-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce5a5-136">See also</span></span>

- [<span data-ttu-id="ce5a5-137">Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-137">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="ce5a5-138">VARIANT genel arabirimleri oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-138">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="ce5a5-139">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="ce5a5-139">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="ce5a5-140">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="ce5a5-140">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
