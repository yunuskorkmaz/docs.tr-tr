---
title: Variance in Generic Interfaces (C#)
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 11d0c8665412bb513cb68d58203a454b7c97e052
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038763"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="feaf2-102">Variance in Generic Interfaces (C#)</span><span class="sxs-lookup"><span data-stu-id="feaf2-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="feaf2-103">.NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="feaf2-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="feaf2-104">Bu arabirimleri uygulayan sınıfların örtük dönüştürme varyansı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="feaf2-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="feaf2-105">Aşağıdaki arabirimlerinden şimdi değişken şunlardır:</span><span class="sxs-lookup"><span data-stu-id="feaf2-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="feaf2-106"><xref:System.Collections.Generic.IEnumerable%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="feaf2-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="feaf2-107"><xref:System.Collections.Generic.IEnumerator%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="feaf2-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="feaf2-108"><xref:System.Linq.IQueryable%601> (T değişkendir)</span><span class="sxs-lookup"><span data-stu-id="feaf2-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="feaf2-109"><xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` birlikte değişken olduğu)</span><span class="sxs-lookup"><span data-stu-id="feaf2-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="feaf2-110"><xref:System.Collections.Generic.IComparer%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="feaf2-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="feaf2-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="feaf2-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="feaf2-112"><xref:System.IComparable%601> (T karşıtıdır)</span><span class="sxs-lookup"><span data-stu-id="feaf2-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="feaf2-113">Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="feaf2-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="feaf2-114">Kovaryans özelliği açıklamak için bu genel arabirimler göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="feaf2-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="feaf2-115">`IEnumerable<String>` Arabirimi devralmaz `IEnumerable<Object>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="feaf2-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="feaf2-116">Ancak, `String` türü devralma `Object` türü ve bazı durumlarda bu arabirimler nesnelerin birbirleriyle atamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="feaf2-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="feaf2-117">Bu aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="feaf2-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="feaf2-118">Önceki .NET Framework sürümlerinde bu kodu C# ile bir derleme hatasına neden olur. `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="feaf2-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="feaf2-119">Ancak artık kullanabilirsiniz `strings` yerine `objects`için önceki örnekte gösterilen şekilde <xref:System.Collections.Generic.IEnumerable%601> arabirimidir birlikte değişken.</span><span class="sxs-lookup"><span data-stu-id="feaf2-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="feaf2-120">Kontravaryans, genel arabirimi parametre olarak belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="feaf2-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="feaf2-121">Kontravaryans göstermek için oluşturduğunuz varsayılır bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="feaf2-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="feaf2-122">`BaseComparer` Sınıfının Implements `IEqualityComparer<BaseClass>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="feaf2-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="feaf2-123">Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi, artık değişken karşıtı, kullanabileceğiniz `BaseComparer` devralan sınıfların örneklerini karşılaştırmak için `BaseClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="feaf2-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="feaf2-124">Bu aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="feaf2-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="feaf2-125">Daha fazla örnek için bkz. [(C#) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="feaf2-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="feaf2-126">Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="feaf2-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="feaf2-127">Değer türleri varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="feaf2-127">Value types do not support variance.</span></span> <span data-ttu-id="feaf2-128">Örneğin, `IEnumerable<int>` için örtük olarak dönüştürülemez `IEnumerable<object>`, tamsayı değer türü tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="feaf2-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="feaf2-129">Değişken arabirimleri uygulayan sınıflar yine de sabit olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="feaf2-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="feaf2-130">Örneğin, ancak <xref:System.Collections.Generic.List%601> birlikte değişken arabirimi uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemez `List<Object>` için `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="feaf2-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="feaf2-131">Bu aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="feaf2-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="feaf2-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feaf2-132">See Also</span></span>

- [<span data-ttu-id="feaf2-133">Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="feaf2-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
- [<span data-ttu-id="feaf2-134">Değişken genel arabirimler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="feaf2-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
- [<span data-ttu-id="feaf2-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="feaf2-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
- [<span data-ttu-id="feaf2-136">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="feaf2-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
