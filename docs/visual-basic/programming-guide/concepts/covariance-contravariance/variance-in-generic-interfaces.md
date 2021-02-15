---
description: 'Hakkında daha fazla bilgi edinin: Genel Arabirimlerde Varyans (Visual Basic)'
title: Genel Arabirimlerde Varyans
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 42257f80cb929756583b1e488cd315450b9db35e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469844"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="e7846-103">Genel Arabirimlerde Varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7846-103">Variance in Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="e7846-104">.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7846-104">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="e7846-105">Varyans desteği, bu arabirimleri uygulayan sınıfların örtük dönüştürülmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="e7846-105">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="e7846-106">Aşağıdaki arabirimler artık değişkendir:</span><span class="sxs-lookup"><span data-stu-id="e7846-106">The following interfaces are now variant:</span></span>

- <span data-ttu-id="e7846-107"><xref:System.Collections.Generic.IEnumerable%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="e7846-107"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="e7846-108"><xref:System.Collections.Generic.IEnumerator%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="e7846-108"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="e7846-109"><xref:System.Linq.IQueryable%601> (T değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="e7846-109"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="e7846-110"><xref:System.Linq.IGrouping%602> ( `TKey` ve `TElement` değişkenle birlikte)</span><span class="sxs-lookup"><span data-stu-id="e7846-110"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="e7846-111"><xref:System.Collections.Generic.IComparer%601> (T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="e7846-111"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="e7846-112"><xref:System.Collections.Generic.IEqualityComparer%601> (T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="e7846-112"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="e7846-113"><xref:System.IComparable%601> (T değişken karşıtı)</span><span class="sxs-lookup"><span data-stu-id="e7846-113"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="e7846-114">Kovaryans, bir metodun, arabirimin genel tür parametresiyle tanımlananla daha türetilmiş bir dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7846-114">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="e7846-115">Kovaryans özelliğini göstermek için şu genel arabirimleri göz önünde bulundurun: `IEnumerable(Of Object)` ve `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="e7846-115">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="e7846-116">`IEnumerable(Of String)`Arabirim, `IEnumerable(Of Object)` arabirimini almıyor.</span><span class="sxs-lookup"><span data-stu-id="e7846-116">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="e7846-117">Ancak, `String` tür devralınır `Object` ve bazı durumlarda bu arabirimlerin nesnelerini birbirlerine atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7846-117">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="e7846-118">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7846-118">This is shown in the following code example.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="e7846-119">.NET Framework önceki sürümlerinde bu kod, ile Visual Basic derleme hatasına neden olur `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="e7846-119">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="e7846-120">Ancak, bu, `strings` `objects` Önceki örnekte gösterildiği gibi yerine kullanabilirsiniz, çünkü <xref:System.Collections.Generic.IEnumerable%601> arabirim değişkenle birlikte değişkendir.</span><span class="sxs-lookup"><span data-stu-id="e7846-120">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="e7846-121">Değişken Varyans, bir metodun, arabirimin genel parametresiyle belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7846-121">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="e7846-122">Değişken varyansı göstermek için, `BaseComparer` sınıfının örneklerini karşılaştırmak üzere bir sınıf oluşturduğunuzu varsayalım `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="e7846-122">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="e7846-123">`BaseComparer` sınıfı, `IEqualityComparer(Of BaseClass)` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="e7846-123">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="e7846-124">Arabirim artık değişken karşıtı olduğundan <xref:System.Collections.Generic.IEqualityComparer%601> , `BaseComparer` sınıfı miras alan sınıfların örneklerini karşılaştırmak için kullanabilirsiniz `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="e7846-124">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="e7846-125">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7846-125">This is shown in the following code example.</span></span>

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

<span data-ttu-id="e7846-126">Daha fazla örnek için bkz. [Genel Koleksiyonlar Için Arabirimlerde Varyans kullanma (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="e7846-126">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="e7846-127">Genel Arabirimlerde Varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e7846-127">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="e7846-128">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e7846-128">Value types do not support variance.</span></span> <span data-ttu-id="e7846-129">Örneğin, `IEnumerable(Of Integer)` `IEnumerable(Of Object)` tamsayılar bir değer türü tarafından temsil edildiği için örtük olarak öğesine dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="e7846-129">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

<span data-ttu-id="e7846-130">Ayrıca, VARIANT arabirimlerini uygulayan sınıfların hala sabit olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e7846-130">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="e7846-131">Örneğin, <xref:System.Collections.Generic.List%601> covaryant arabirimini uygular <xref:System.Collections.Generic.IEnumerable%601> , ancak öğesini örtülü olarak dönüştüremezsiniz `List(Of Object)` `List(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="e7846-131">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="e7846-132">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7846-132">This is illustrated in the following code example.</span></span>

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a><span data-ttu-id="e7846-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7846-133">See also</span></span>

- [<span data-ttu-id="e7846-134">Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7846-134">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="e7846-135">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7846-135">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)
- [<span data-ttu-id="e7846-136">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="e7846-136">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="e7846-137">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7846-137">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)
