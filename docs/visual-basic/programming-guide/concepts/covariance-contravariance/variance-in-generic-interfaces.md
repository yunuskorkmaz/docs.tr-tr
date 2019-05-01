---
title: Variance in Generic Interfaces (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 50a1aeb5c17a0f193b9e90ca2167ef298f7ed237
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787224"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="b9909-102">Variance in Generic Interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9909-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="b9909-103">.NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="b9909-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="b9909-104">Bu arabirimleri uygulayan sınıfların örtük dönüştürme varyansı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9909-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="b9909-105">Aşağıdaki arabirimlerinden şimdi değişken şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b9909-105">The following interfaces are now variant:</span></span>  
  
- <span data-ttu-id="b9909-106"><xref:System.Collections.Generic.IEnumerable%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="b9909-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
- <span data-ttu-id="b9909-107"><xref:System.Collections.Generic.IEnumerator%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="b9909-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
- <span data-ttu-id="b9909-108"><xref:System.Linq.IQueryable%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="b9909-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
- <span data-ttu-id="b9909-109"><xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` birlikte değişken olduğu)</span><span class="sxs-lookup"><span data-stu-id="b9909-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
- <span data-ttu-id="b9909-110"><xref:System.Collections.Generic.IComparer%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="b9909-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
- <span data-ttu-id="b9909-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="b9909-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
- <span data-ttu-id="b9909-112"><xref:System.IComparable%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="b9909-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="b9909-113">Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9909-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="b9909-114">Kovaryans özelliği açıklamak için bu genel arabirimler göz önünde bulundurun: `IEnumerable(Of Object)` ve `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="b9909-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="b9909-115">`IEnumerable(Of String)` Arabirimi devralmaz `IEnumerable(Of Object)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b9909-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="b9909-116">Ancak, `String` türü devralma `Object` türü ve bazı durumlarda bu arabirimler nesnelerin birbirleriyle atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9909-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="b9909-117">Bu aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b9909-117">This is shown in the following code example.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="b9909-118">Önceki .NET Framework sürümlerinde, bu kod Visual Basic ile bir derleme hatasına neden olur. `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="b9909-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="b9909-119">Ancak artık kullanabilirsiniz `strings` yerine `objects`için önceki örnekte gösterilen şekilde <xref:System.Collections.Generic.IEnumerable%601> arabirimidir birlikte değişken.</span><span class="sxs-lookup"><span data-stu-id="b9909-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="b9909-120">Kontravaryans, genel arabirimi parametre olarak belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="b9909-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="b9909-121">Kontravaryans göstermek için oluşturduğunuz varsayılır bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b9909-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="b9909-122">`BaseComparer` Sınıfının Implements `IEqualityComparer(Of BaseClass)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b9909-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="b9909-123">Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi, artık değişken karşıtı, kullanabileceğiniz `BaseComparer` devralan sınıfların örneklerini karşılaştırmak için `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b9909-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="b9909-124">Bu aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b9909-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="b9909-125">Daha fazla örnek için bkz. [(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="b9909-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="b9909-126">Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b9909-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="b9909-127">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b9909-127">Value types do not support variance.</span></span> <span data-ttu-id="b9909-128">Örneğin, `IEnumerable(Of Integer)` için örtük olarak dönüştürülemez `IEnumerable(Of Object)`, tamsayı değer türü tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="b9909-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 <span data-ttu-id="b9909-129">Değişken arabirimleri uygulayan sınıflar yine de sabit olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b9909-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="b9909-130">Örneğin, ancak <xref:System.Collections.Generic.List%601> birlikte değişken arabirimi uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemez `List(Of Object)` için `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="b9909-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="b9909-131">Bu aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b9909-131">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9909-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9909-132">See also</span></span>

- [<span data-ttu-id="b9909-133">(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="b9909-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="b9909-134">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9909-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="b9909-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b9909-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="b9909-136">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9909-136">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
