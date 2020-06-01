---
title: Temsilcilerde varyans (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: d41c0d3d54df96031fc7989e0fdc78e9f358a40a
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241350"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="4c7f6-102">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="4c7f6-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="4c7f6-103">.NET Framework 3,5, C# ' deki tüm Temsilcilerde temsilci türleriyle eşleşen yöntem imzaları için fark desteğini kullanıma sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="4c7f6-104">Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş tür (değişken varyans) içeren parametreleri kabul eden yöntemler için atama yaptığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="4c7f6-105">Bu hem genel hem de genel olmayan temsilcileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="4c7f6-106">Örneğin, iki sınıfı ve iki temsilciyi olan aşağıdaki kodu düşünün: genel ve genel olmayan.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="4c7f6-107">`SampleDelegate`Veya türlerinin temsilcilerini oluşturduğunuzda `SampleGenericDelegate<A, R>` , aşağıdaki yöntemlerden herhangi birini bu temsilcilere atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
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
  
 <span data-ttu-id="4c7f6-108">Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasındaki örtük dönüştürmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="4c7f6-109">Daha fazla örnek için bkz. [Temsilciler Içinde varyans kullanma (c#)](./using-variance-in-delegates.md) ve [Func ve ACTION genel temsilcileri için varyans kullanma (c#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4c7f6-109">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="4c7f6-110">Genel tür parametrelerindeki varyans</span><span class="sxs-lookup"><span data-stu-id="4c7f6-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="4c7f6-111">.NET Framework 4 veya sonraki sürümlerde temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz; böylece türler, genel tür parametreleri tarafından belirtilen farklı türlere sahip olan genel temsilcilerin birbirini fark eden her bir öğeden devralınabileceği her birine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="4c7f6-112">Örtük dönüştürmeyi etkinleştirmek için, `in` veya anahtar sözcüğünü kullanarak bir temsilcinin genel parametrelerini birlikte değişken veya değişken karşıtı olarak açıkça bildirmeniz gerekir `out` .</span><span class="sxs-lookup"><span data-stu-id="4c7f6-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="4c7f6-113">Aşağıdaki kod örneği, birlikte değişken genel tür parametresine sahip olan bir temsilciyi nasıl oluşturabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="4c7f6-114">Yöntem imzalarını temsilci türleriyle eşleştirmek için yalnızca varyans desteğini kullanırsanız ve `in` ve `out` anahtar sözcüklerini kullanmıyorsanız, bazen aynı lambda ifadeleri veya yöntemlerine sahip temsilciler örnekleyebilirsiniz, ancak bir temsilciyi başka bir temsilciye atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="4c7f6-115">Aşağıdaki kod örneğinde, `SampleGenericDelegate<String>` açıkça öğesine dönüştürülemez `SampleGenericDelegate<Object>` , ancak `String` devralır `Object` .</span><span class="sxs-lookup"><span data-stu-id="4c7f6-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="4c7f6-116">Genel parametreyi anahtar sözcüğüyle işaretleyerek bu sorunu çözebilirsiniz `T` `out` .</span><span class="sxs-lookup"><span data-stu-id="4c7f6-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-net"></a><span data-ttu-id="4c7f6-117">.NET 'te değişken tür parametrelerine sahip genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="4c7f6-117">Generic Delegates That Have Variant Type Parameters in .NET</span></span>

<span data-ttu-id="4c7f6-118">.NET Framework 4, çeşitli genel temsilcilerde genel tür parametrelerine yönelik varyans desteği getirmiştir:</span><span class="sxs-lookup"><span data-stu-id="4c7f6-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="4c7f6-119">`Action`ad alanından temsilciler, <xref:System> Örneğin <xref:System.Action%601> ve<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="4c7f6-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="4c7f6-120">`Func`ad alanından temsilciler, <xref:System> Örneğin <xref:System.Func%601> ve<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="4c7f6-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="4c7f6-121"><xref:System.Predicate%601>Temsilci</span><span class="sxs-lookup"><span data-stu-id="4c7f6-121">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="4c7f6-122"><xref:System.Comparison%601>Temsilci</span><span class="sxs-lookup"><span data-stu-id="4c7f6-122">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="4c7f6-123"><xref:System.Converter%602>Temsilci</span><span class="sxs-lookup"><span data-stu-id="4c7f6-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="4c7f6-124">Daha fazla bilgi ve örnek için bkz. [Func ve eylem genel temsilcileri Için varyans kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4c7f6-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="4c7f6-125">Genel Temsilcilerde değişken tür parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="4c7f6-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="4c7f6-126">Genel bir temsilcinin birlikte değişken veya değişken karşıtı genel tür parametreleri varsa, bu, *VARIANT genel temsilcisi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="4c7f6-127">Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi ortak değişkeni bildirebilirsiniz `out` .</span><span class="sxs-lookup"><span data-stu-id="4c7f6-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="4c7f6-128">Covaryant türü, yöntem bağımsız değişkenlerinin türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="4c7f6-129">Aşağıdaki kod örneği, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="4c7f6-130">Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi değişken değişkeni bildirebilirsiniz `in` .</span><span class="sxs-lookup"><span data-stu-id="4c7f6-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="4c7f6-131">Değişken karşıtı türü, yöntem dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="4c7f6-132">Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="4c7f6-133">`ref`, `in` ve `out` C# içindeki parametreler değişken olarak işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="4c7f6-134">Aynı temsilci, ancak farklı tür parametreleri için hem varyansı hem de kovaryansı desteklemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="4c7f6-135">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="4c7f6-136">VARIANT genel temsilcileri örnekleme ve çağırma</span><span class="sxs-lookup"><span data-stu-id="4c7f6-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="4c7f6-137">Sabit temsilcileri örneklediğinizde ve çağırdığınızda değişken temsilcileri örnek oluşturabilir ve çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="4c7f6-138">Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="4c7f6-139">Değişken genel temsilcileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="4c7f6-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="4c7f6-140">Değişken temsilcileri birleştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-140">You should not combine variant delegates.</span></span> <span data-ttu-id="4c7f6-141"><xref:System.Delegate.Combine%2A>Yöntem, değişken temsilci dönüştürmeyi desteklemez ve temsilcilerin tamamen aynı türde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="4c7f6-142">Bu, <xref:System.Delegate.Combine%2A> `+` Aşağıdaki kod örneğinde gösterildiği gibi, veya işlecini kullanarak temsilcileri birleştirdiğinizde bir çalışma zamanı özel durumuna yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="4c7f6-143">Değer ve başvuru türleri için genel tür parametrelerinin varyansı</span><span class="sxs-lookup"><span data-stu-id="4c7f6-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="4c7f6-144">Genel tür parametrelerinin varyansı yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="4c7f6-145">Örneğin, `DVariant<int>` `DVariant<Object>` tamsayı bir değer türü olduğundan, örtülü olarak veya `DVariant<long>` türüne dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="4c7f6-146">Aşağıdaki örnek, genel tür parametrelerinin farkının değer türleri için desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c7f6-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c7f6-147">See also</span></span>

- [<span data-ttu-id="4c7f6-148">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="4c7f6-148">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="4c7f6-149">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="4c7f6-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="4c7f6-150">Temsilcileri birleştirme (çok noktaya yayın temsilcileri)</span><span class="sxs-lookup"><span data-stu-id="4c7f6-150">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
