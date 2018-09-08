---
title: Temsilcilerde varyans (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 3dabac4e532198871cf05d639aa692751ab17ae1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128478"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="36c94-102">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="36c94-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="36c94-103">.NET framework 3.5, tüm temsilciler C# içindeki temsilci türleriyle yöntem imzalarının eşleştirilmesi için varyans desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="36c94-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="36c94-104">Yalnızca imzalarının eşleştirilmesi içeren yöntemlerin yanı sıra temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip bir parametre kabul eden ya da daha fazla türetilmiş türler (kovaryans) döndüren yöntemler için atayabileceğiniz anlamına gelir temsilciler .</span><span class="sxs-lookup"><span data-stu-id="36c94-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="36c94-105">Bu, hem genel hem de genel olmayan temsilcileri içerir.</span><span class="sxs-lookup"><span data-stu-id="36c94-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="36c94-106">Örneğin, iki sınıf ve iki temsilci olduğunda sahip aşağıdaki kodu düşünün: Genel ve genel olmayan.</span><span class="sxs-lookup"><span data-stu-id="36c94-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="36c94-107">Temsilciler, oluşturduğunuzda `SampleDelegate` veya `SampleGenericDelegate<A, R>` türleri, bu temsilcileri için aşağıdaki yöntemlerden herhangi birini atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c94-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second first)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived   
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 <span data-ttu-id="36c94-108">Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasında örtülü dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="36c94-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```csharp  
// Assigning a method with a matching signature   
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 <span data-ttu-id="36c94-109">Daha fazla örnek için bkz. [Temsilcilerde varyans (C#) kullanarak](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="36c94-109">For more examples, see [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="36c94-110">Genel tür parametreleri varyans</span><span class="sxs-lookup"><span data-stu-id="36c94-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="36c94-111">Böylece türlerini birbirinden gerektirdiği devralınırsa, genel tür parametrelerle belirtilen farklı türlere sahip genel temsilciler birbiriyle atanabilir .NET Framework 4 veya üzeri temsilciler arasında örtük dönüştürme etkinleştirebilirsiniz farkı.</span><span class="sxs-lookup"><span data-stu-id="36c94-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="36c94-112">Örtük dönüştürme etkinleştirmek için açıkça genel parametreler birlikte değişken olarak bir temsilci bildirmeniz gerekir veya kullanarak, değişken karşıtı `in` veya `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="36c94-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="36c94-113">Aşağıdaki kod örneği, bir genel birlikte değişen türde parametresi olan bir temsilci nasıl oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="36c94-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;             
}  
```  
  
 <span data-ttu-id="36c94-114">Tek farkı destek eşleştirilecek kullanırsanız birlikte yöntem imzaları temsilci türleri ve kullanmaz `in` ve `out` anahtar bulduğunuz bazen aynı lambda ifadeleri veya yöntemler ile temsilciler örneği oluşturabilir, ancak bunu yapamazsınız bir temsilci diğerine atayın.</span><span class="sxs-lookup"><span data-stu-id="36c94-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="36c94-115">Aşağıdaki kod örneğinde, `SampleGenericDelegate<String>` açıkça dönüştürülemez `SampleGenericDelegate<Object>`, ancak `String` devralan `Object`.</span><span class="sxs-lookup"><span data-stu-id="36c94-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="36c94-116">Genel parametre olarak işaretleyerek bu sorunu düzeltebilirsiniz `T` ile `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="36c94-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for   
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="36c94-117">.NET Framework tür parametreleri varyant sahip genel temsilciler</span><span class="sxs-lookup"><span data-stu-id="36c94-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="36c94-118">.NET framework 4, varolan birçok genel temsilciler genel tür parametrelerinde varyansı başlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="36c94-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="36c94-119">`Action` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Action%601> ve <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="36c94-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="36c94-120">`Func` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Func%601> ve <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="36c94-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="36c94-121"><xref:System.Predicate%601> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="36c94-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="36c94-122"><xref:System.Comparison%601> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="36c94-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="36c94-123"><xref:System.Converter%602> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="36c94-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="36c94-124">Daha fazla bilgi ve örnekler için bkz. [işlev ve eylem genel temsilcileri (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="36c94-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="36c94-125">Değişken türünde parametreler genel temsilciler bildirme</span><span class="sxs-lookup"><span data-stu-id="36c94-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="36c94-126">Genel temsilci birlikte değişken veya değişken karşıtı genel tür parametreleri, başvurulabilir olarak varsa bir *değişken Genel temsilci*.</span><span class="sxs-lookup"><span data-stu-id="36c94-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="36c94-127">Genel tür parametresi birlikte değişken Genel temsilci kullanarak bildirebilirsiniz `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="36c94-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="36c94-128">Birlikte değişken türünde yöntem bağımsız bir tür değil de, yalnızca bir yöntem dönüş türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36c94-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="36c94-129">Aşağıdaki kod örneği, birlikte değişken genel bir temsilcinin nasıl belirtileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="36c94-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="36c94-130">Genel tür parametresi değişken karşıtı Genel temsilci kullanarak bildirebilirsiniz `in` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="36c94-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="36c94-131">Değişken karşıtı türü, yöntemin dönüş türü değil de, yalnızca bir tür yöntem bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36c94-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="36c94-132">Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl belirtileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="36c94-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="36c94-133">`ref`, `in`, ve `out` C# parametreleri varyant olarak işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="36c94-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="36c94-134">Farkı hem Kovaryans aynı temsilci, ancak farklı tür parametreleri için destek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="36c94-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="36c94-135">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="36c94-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="36c94-136">Örnekleme ve bunları çağırırken değişken genel temsilciler</span><span class="sxs-lookup"><span data-stu-id="36c94-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="36c94-137">Örneği oluşturun ve yalnızca örneklemek ve sabit temsilciler çağırmak değişken temsilciler çağır.</span><span class="sxs-lookup"><span data-stu-id="36c94-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="36c94-138">Aşağıdaki örnekte, temsilci bir lambda ifadesiyle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="36c94-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="36c94-139">Değişken genel temsilciler birleştirme</span><span class="sxs-lookup"><span data-stu-id="36c94-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="36c94-140">Değişken temsilciler birleştirmemelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="36c94-140">You should not combine variant delegates.</span></span> <span data-ttu-id="36c94-141"><xref:System.Delegate.Combine%2A> Yöntemi değişken temsilci dönüştürmeyi desteklemez ve temsilciler tam olarak aynı veri türünde olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="36c94-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="36c94-142">Temsilcileri kullanarak ya da birleştirdiğinizde bu için bir çalışma zamanı özel durumuna neden olabilir <xref:System.Delegate.Combine%2A> yöntemi kullanarak veya `+` aşağıdaki kod örneğinde gösterildiği gibi işleci.</span><span class="sxs-lookup"><span data-stu-id="36c94-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="36c94-143">Değer ve başvuru türleri için genel tür parametrelerindeki varyansı</span><span class="sxs-lookup"><span data-stu-id="36c94-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="36c94-144">Varyans genel tür parametreleri için yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="36c94-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="36c94-145">Örneğin, `DVariant<int>` için örtük olarak dönüştürülemez `DVariant<Object>` veya `DVariant<long>`tamsayı değer türü olduğundan.</span><span class="sxs-lookup"><span data-stu-id="36c94-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="36c94-146">Aşağıdaki örnek, bu farkı göstermektedir genel tür parametreleri değer türleri için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="36c94-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;              
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="36c94-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36c94-147">See Also</span></span>

- [<span data-ttu-id="36c94-148">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="36c94-148">Generics</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="36c94-149">İşlev ve eylem genel temsilcileri (C#) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="36c94-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
- [<span data-ttu-id="36c94-150">Nasıl yapılır: temsilcileri (çok noktaya yayın temsilcileri) birleştirme</span><span class="sxs-lookup"><span data-stu-id="36c94-150">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
