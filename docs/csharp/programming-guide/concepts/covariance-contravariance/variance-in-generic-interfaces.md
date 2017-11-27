---
title: Genel arabirimler (C#) varyans
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fe009e89d5d8f6619b406c8c08f47620a881d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="7684e-102">Genel arabirimler (C#) varyans</span><span class="sxs-lookup"><span data-stu-id="7684e-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="7684e-103">.NET framework 4 birkaç mevcut genel arabirimler sapma desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="7684e-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="7684e-104">Bu arabirimleri uygulayan sınıflar örtük dönüştürme sapma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7684e-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="7684e-105">Aşağıdaki arabirimleri şimdi değişken şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7684e-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="7684e-106"><xref:System.Collections.Generic.IEnumerable%601>(T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="7684e-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="7684e-107"><xref:System.Collections.Generic.IEnumerator%601>(T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="7684e-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="7684e-108"><xref:System.Linq.IQueryable%601>(T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="7684e-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="7684e-109"><xref:System.Linq.IGrouping%602>(`TKey` ve `TElement` eşdeğişken olan)</span><span class="sxs-lookup"><span data-stu-id="7684e-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="7684e-110"><xref:System.Collections.Generic.IComparer%601>(T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="7684e-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="7684e-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="7684e-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="7684e-112"><xref:System.IComparable%601>(T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="7684e-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="7684e-113">Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="7684e-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="7684e-114">Kovaryans özelliği göstermek için bu genel arabirimler göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="7684e-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="7684e-115">`IEnumerable<String>` Arabirimi devralmaz `IEnumerable<Object>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7684e-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="7684e-116">Ancak, `String` türü devral `Object` türü ve bazı durumlarda bu arabirimleri nesnelerin birbirlerine atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7684e-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="7684e-117">Bu, aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7684e-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="7684e-118">.NET Framework önceki sürümlerinde, bu kod derleme hatası C# ile neden `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="7684e-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="7684e-119">Ancak artık kullanabilirsiniz `strings` yerine `objects`, çünkü önceki örnekte gösterildiği gibi <xref:System.Collections.Generic.IEnumerable%601> arabirimidir eşdeğişken.</span><span class="sxs-lookup"><span data-stu-id="7684e-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="7684e-120">Değişken karşıtı arabirimi genel parametresi tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="7684e-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="7684e-121">Değişken karşıtı göstermek için oluşturduğunuzu varsayalım bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7684e-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="7684e-122">`BaseComparer` Uygulayan sınıf `IEqualityComparer<BaseClass>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7684e-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="7684e-123">Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi şimdi karşıtı, kullanabileceğiniz `BaseComparer` devral sınıfların örneklerini Karşılaştırılacak `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7684e-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="7684e-124">Bu, aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7684e-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="7684e-125">Daha fazla örnek için bkz: [(C#) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="7684e-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="7684e-126">Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7684e-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="7684e-127">Türlerin varyans desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7684e-127">Value types do not support variance.</span></span> <span data-ttu-id="7684e-128">Örneğin, `IEnumerable<int>` örtük olarak dönüştürülemiyor `IEnumerable<object>`, tamsayı bir değer türü ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7684e-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="7684e-129">Değişken arabirimler uygulayan sınıflar hala değişmez olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7684e-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="7684e-130">Örneğin, ancak <xref:System.Collections.Generic.List%601> eşdeğişken arabirimini uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemiyor `List<Object>` için `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="7684e-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="7684e-131">Bu aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7684e-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="7684e-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7684e-132">See Also</span></span>  
 [<span data-ttu-id="7684e-133">Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="7684e-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="7684e-134">Değişken genel arabirimler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="7684e-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="7684e-135">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="7684e-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="7684e-136">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="7684e-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
