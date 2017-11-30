---
title: Genel arabirimler (Visual Basic) varyans
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d05ccdc97efd5dd193bbbe0d15dd227ec71910d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="7719c-102">Genel arabirimler (Visual Basic) varyans</span><span class="sxs-lookup"><span data-stu-id="7719c-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="7719c-103">.NET framework 4 birkaç mevcut genel arabirimler sapma desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="7719c-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="7719c-104">Bu arabirimleri uygulayan sınıflar örtük dönüştürme sapma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7719c-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="7719c-105">Aşağıdaki arabirimleri şimdi değişken şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7719c-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="7719c-106"><xref:System.Collections.Generic.IEnumerable%601>(T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="7719c-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="7719c-107"><xref:System.Collections.Generic.IEnumerator%601>(T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="7719c-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="7719c-108"><xref:System.Linq.IQueryable%601>(T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="7719c-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="7719c-109"><xref:System.Linq.IGrouping%602>(`TKey` ve `TElement` eşdeğişken olan)</span><span class="sxs-lookup"><span data-stu-id="7719c-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="7719c-110"><xref:System.Collections.Generic.IComparer%601>(T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="7719c-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="7719c-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="7719c-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="7719c-112"><xref:System.IComparable%601>(T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="7719c-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="7719c-113">Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="7719c-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="7719c-114">Kovaryans özelliği göstermek için bu genel arabirimler göz önünde bulundurun: `IEnumerable(Of Object)` ve `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="7719c-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="7719c-115">`IEnumerable(Of String)` Arabirimi devralmaz `IEnumerable(Of Object)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7719c-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="7719c-116">Ancak, `String` türü devral `Object` türü ve bazı durumlarda bu arabirimleri nesnelerin birbirlerine atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7719c-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="7719c-117">Bu, aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7719c-117">This is shown in the following code example.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="7719c-118">.NET Framework önceki sürümlerinde, bu kod derleme hatası ile Visual Basic'te neden `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="7719c-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="7719c-119">Ancak artık kullanabilirsiniz `strings` yerine `objects`, çünkü önceki örnekte gösterildiği gibi <xref:System.Collections.Generic.IEnumerable%601> arabirimidir eşdeğişken.</span><span class="sxs-lookup"><span data-stu-id="7719c-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="7719c-120">Değişken karşıtı arabirimi genel parametresi tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="7719c-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="7719c-121">Değişken karşıtı göstermek için oluşturduğunuzu varsayalım bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7719c-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="7719c-122">`BaseComparer` Uygulayan sınıf `IEqualityComparer(Of BaseClass)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7719c-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="7719c-123">Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi şimdi karşıtı, kullanabileceğiniz `BaseComparer` devral sınıfların örneklerini Karşılaştırılacak `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7719c-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="7719c-124">Bu, aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7719c-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="7719c-125">Daha fazla örnek için bkz: [(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="7719c-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="7719c-126">Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7719c-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="7719c-127">Türlerin varyans desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7719c-127">Value types do not support variance.</span></span> <span data-ttu-id="7719c-128">Örneğin, `IEnumerable(Of Integer)` örtük olarak dönüştürülemiyor `IEnumerable(Of Object)`, tamsayı bir değer türü ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7719c-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 <span data-ttu-id="7719c-129">Değişken arabirimler uygulayan sınıflar hala değişmez olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7719c-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="7719c-130">Örneğin, ancak <xref:System.Collections.Generic.List%601> eşdeğişken arabirimini uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemiyor `List(Of Object)` için `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="7719c-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="7719c-131">Bu aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7719c-131">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="7719c-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7719c-132">See Also</span></span>  
 [<span data-ttu-id="7719c-133">(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="7719c-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="7719c-134">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7719c-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="7719c-135">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="7719c-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="7719c-136">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7719c-136">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
