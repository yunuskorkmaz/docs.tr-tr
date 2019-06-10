---
title: Variance in Generic Interfaces (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: a2d0bcc049d62978930b4e5cdef7920349e3b894
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815953"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="f72d6-102">Variance in Generic Interfaces (C#)</span><span class="sxs-lookup"><span data-stu-id="f72d6-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="f72d6-103">.NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="f72d6-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="f72d6-104">Bu arabirimleri uygulayan sınıfların örtük dönüştürme varyansı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="f72d6-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="f72d6-105">.NET Framework 4 ile başlamanızı, aşağıdaki arabirimlerinden değişken şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f72d6-105">Staring with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="f72d6-106"><xref:System.Collections.Generic.IEnumerable%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="f72d6-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="f72d6-107"><xref:System.Collections.Generic.IEnumerator%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="f72d6-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="f72d6-108"><xref:System.Linq.IQueryable%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="f72d6-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="f72d6-109"><xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` birlikte değişken olduğu)</span><span class="sxs-lookup"><span data-stu-id="f72d6-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="f72d6-110"><xref:System.Collections.Generic.IComparer%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="f72d6-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="f72d6-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="f72d6-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="f72d6-112"><xref:System.IComparable%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="f72d6-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="f72d6-113">.NET Framework 4.5 ile başlayarak, aşağıdaki arabirimlerinden değişken şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f72d6-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="f72d6-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="f72d6-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="f72d6-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="f72d6-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="f72d6-116">Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="f72d6-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="f72d6-117">Kovaryans özelliği açıklamak için bu genel arabirimler göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="f72d6-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="f72d6-118">`IEnumerable<String>` Arabirimi devralmaz `IEnumerable<Object>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f72d6-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="f72d6-119">Ancak, `String` türü devralma `Object` türü ve bazı durumlarda bu arabirimler nesnelerin birbirleriyle atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f72d6-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="f72d6-120">Bu aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f72d6-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="f72d6-121">Önceki .NET Framework sürümlerinde, bu kod bir derleme hatasına neden olur. C# ve `Option Strict` açıktır, Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="f72d6-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="f72d6-122">Ancak artık kullanabilirsiniz `strings` yerine `objects`için önceki örnekte gösterilen şekilde <xref:System.Collections.Generic.IEnumerable%601> arabirimidir birlikte değişken.</span><span class="sxs-lookup"><span data-stu-id="f72d6-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="f72d6-123">Kontravaryans, genel arabirimi parametre olarak belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="f72d6-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="f72d6-124">Kontravaryans göstermek için oluşturduğunuz varsayılır bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f72d6-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="f72d6-125">`BaseComparer` Sınıfının Implements `IEqualityComparer<BaseClass>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f72d6-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="f72d6-126">Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi, artık değişken karşıtı, kullanabileceğiniz `BaseComparer` devralan sınıfların örneklerini karşılaştırmak için `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f72d6-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="f72d6-127">Bu aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f72d6-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="f72d6-128">Daha fazla örnek için bkz. [(C#) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="f72d6-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="f72d6-129">Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f72d6-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="f72d6-130">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f72d6-130">Value types do not support variance.</span></span> <span data-ttu-id="f72d6-131">Örneğin, `IEnumerable<int>` için örtük olarak dönüştürülemez `IEnumerable<object>`, tamsayı değer türü tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f72d6-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="f72d6-132">Değişken arabirimleri uygulayan sınıflar yine de sabit olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f72d6-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="f72d6-133">Örneğin, ancak <xref:System.Collections.Generic.List%601> birlikte değişken arabirimi uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemez `List<Object>` için `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="f72d6-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="f72d6-134">Bu aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f72d6-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="f72d6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f72d6-135">See also</span></span>

- [<span data-ttu-id="f72d6-136">Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="f72d6-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="f72d6-137">Değişken genel arabirimler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="f72d6-137">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="f72d6-138">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f72d6-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="f72d6-139">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="f72d6-139">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
