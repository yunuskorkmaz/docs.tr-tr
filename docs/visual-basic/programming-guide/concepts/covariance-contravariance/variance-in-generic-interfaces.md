---
title: Genel Arabirimlerde Varyans
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: df28a9f24518f24d1be89acba726da7dfbbf9570
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375596"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="8cfb1-102">Genel Arabirimlerde Varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-102">Variance in Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="8cfb1-103">.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="8cfb1-104">Varyans desteği, bu arabirimleri uygulayan sınıfların örtük dönüştürülmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="8cfb1-105">Aşağıdaki arabirimler artık değişkendir:</span><span class="sxs-lookup"><span data-stu-id="8cfb1-105">The following interfaces are now variant:</span></span>

- <span data-ttu-id="8cfb1-106"><xref:System.Collections.Generic.IEnumerable%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="8cfb1-107"><xref:System.Collections.Generic.IEnumerator%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="8cfb1-108"><xref:System.Linq.IQueryable%601>(T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="8cfb1-109"><xref:System.Linq.IGrouping%602>( `TKey` ve `TElement` değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="8cfb1-110"><xref:System.Collections.Generic.IComparer%601>(T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="8cfb1-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="8cfb1-112"><xref:System.IComparable%601>(T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="8cfb1-113">Kovaryans, bir metodun, arabirimin genel tür parametresiyle tanımlananla daha türetilmiş bir dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="8cfb1-114">Kovaryans özelliğini göstermek için şu genel arabirimleri göz önünde bulundurun: `IEnumerable(Of Object)` ve `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="8cfb1-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="8cfb1-115">`IEnumerable(Of String)`Arabirim, `IEnumerable(Of Object)` arabirimini almıyor.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="8cfb1-116">Ancak, `String` tür devralınır `Object` ve bazı durumlarda bu arabirimlerin nesnelerini birbirlerine atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="8cfb1-117">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-117">This is shown in the following code example.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="8cfb1-118">.NET Framework önceki sürümlerinde bu kod, ile Visual Basic derleme hatasına neden olur `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="8cfb1-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="8cfb1-119">Ancak, bu, `strings` `objects` Önceki örnekte gösterildiği gibi yerine kullanabilirsiniz, çünkü <xref:System.Collections.Generic.IEnumerable%601> arabirim değişkenle birlikte değişkendir.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="8cfb1-120">Değişken Varyans, bir metodun, arabirimin genel parametresiyle belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="8cfb1-121">Değişken varyansı göstermek için, `BaseComparer` sınıfının örneklerini karşılaştırmak üzere bir sınıf oluşturduğunuzu varsayalım `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="8cfb1-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="8cfb1-122">`BaseComparer` sınıfı, `IEqualityComparer(Of BaseClass)` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="8cfb1-123">Arabirim artık değişken karşıtı olduğundan <xref:System.Collections.Generic.IEqualityComparer%601> , `BaseComparer` sınıfı miras alan sınıfların örneklerini karşılaştırmak için kullanabilirsiniz `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="8cfb1-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="8cfb1-124">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-124">This is shown in the following code example.</span></span>

```vb
' Simple hierarchy of classes.
Class BaseClass
End Class

Class DerivedClass
    Inherits BaseClass
End Class

' Comparer class.
Class BaseComparer
    Implements IEqualityComparer(Of BaseClass)

    Public Function Equals1(ByVal x As BaseClass,
                            ByVal y As BaseClass) As Boolean _
                            Implements IEqualityComparer(Of BaseClass).Equals
        Return (x.Equals(y))
    End Function

    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _
        Implements IEqualityComparer(Of BaseClass).GetHashCode
        Return obj.GetHashCode
    End Function
End Class
Sub Test()
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to
    ' IEqualityComparer(Of DerivedClass).
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer
End Sub
```

<span data-ttu-id="8cfb1-125">Daha fazla örnek için bkz. [Genel Koleksiyonlar Için Arabirimlerde Varyans kullanma (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="8cfb1-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="8cfb1-126">Genel Arabirimlerde Varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="8cfb1-127">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-127">Value types do not support variance.</span></span> <span data-ttu-id="8cfb1-128">Örneğin, `IEnumerable(Of Integer)` `IEnumerable(Of Object)` tamsayılar bir değer türü tarafından temsil edildiği için örtük olarak öğesine dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

<span data-ttu-id="8cfb1-129">Ayrıca, VARIANT arabirimlerini uygulayan sınıfların hala sabit olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="8cfb1-130">Örneğin, <xref:System.Collections.Generic.List%601> covaryant arabirimini uygular <xref:System.Collections.Generic.IEnumerable%601> , ancak öğesini örtülü olarak dönüştüremezsiniz `List(Of Object)` `List(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="8cfb1-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="8cfb1-131">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-131">This is illustrated in the following code example.</span></span>

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a><span data-ttu-id="8cfb1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cfb1-132">See also</span></span>

- [<span data-ttu-id="8cfb1-133">Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="8cfb1-134">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)
- [<span data-ttu-id="8cfb1-135">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="8cfb1-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="8cfb1-136">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cfb1-136">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)
