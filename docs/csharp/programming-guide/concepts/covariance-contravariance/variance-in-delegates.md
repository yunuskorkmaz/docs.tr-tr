---
title: Temsilcilerde Varyans (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: fd1b4824dc3d8f12347e01b804a6e39fe2e086c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169720"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="dc38e-102">Temsilcilerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="dc38e-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="dc38e-103">.NET Framework 3.5, C#'daki tüm temsilcilerdeki temsilci türleri ile eşleşen yöntem imzaları için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="dc38e-104">Bu, yalnızca eşleşen imzalara sahip yöntemlere değil, aynı zamanda daha fazla türemiş türleri (tutarlılık) döndüren veya temsilci türütarafından belirtilenden daha az türemiş türe (kontravariance) olan parametreleri kabul eden yöntemleri de temsilciatamak anlamına gelir .</span><span class="sxs-lookup"><span data-stu-id="dc38e-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="dc38e-105">Bu, hem genel hem de genel olmayan temsilcileri içerir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="dc38e-106">Örneğin, iki sınıfı ve iki temsilcisi olan aşağıdaki kodu göz önünde bulundurun: genel ve genel olmayan.</span><span class="sxs-lookup"><span data-stu-id="dc38e-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="dc38e-107">`SampleDelegate` Veya `SampleGenericDelegate<A, R>` türlerden temsilciler oluşturduğunuzda, bu temsilcilere aşağıdaki yöntemlerden birini atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="dc38e-108">Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasındaki örtük dönüştürmeyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="dc38e-109">Daha fazla örnek için bkz: [Varyans Kullanarak Temsilciler (C#)](./using-variance-in-delegates.md) ve [Func ve Eylem Genel Delegeler (C# için Varyans kullanma).](./using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="dc38e-109">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="dc38e-110">Genel Tip Parametrelerinde Varyans</span><span class="sxs-lookup"><span data-stu-id="dc38e-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="dc38e-111">.NET Framework 4 veya sonraki durumlarda, genel tür parametreleri tarafından belirlenen farklı türlere sahip genel temsilcilerin birbirlerinden gerektiği gibi devralınması durumunda, genel tür parametreleri tarafından belirtilen genel temsilcilertarafından atanabilmesi için, temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz Varyans.</span><span class="sxs-lookup"><span data-stu-id="dc38e-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="dc38e-112">Örtük dönüştürmeyi etkinleştirmek için, genel parametreleri bir temsilcideki genel `in` parametreleri veya `out` anahtar sözcüğü kullanarak ortak değişken veya karşıt değişken olarak açıkça beyan etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="dc38e-113">Aşağıdaki kod örneği, ortak değişken genel tür parametresi olan bir temsilciyi nasıl oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="dc38e-114">Yöntem imzalarını temsilci türleri ile eşleştirmek için yalnızca varyans `in` `out` desteği kullanırsanız ve anahtar kelimeleri kullanmazsanız, bazen aynı lambda ifadeleri veya yöntemleriyle temsilcileri anında atayabileceğinizi, ancak bir temsilciyi diğerine atayamayacağınızı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="dc38e-115">Aşağıdaki kod `SampleGenericDelegate<String>` örneğinde, devralınmasına rağmen `SampleGenericDelegate<Object>` `String` açıkça `Object`"ne ş"ye dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="dc38e-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="dc38e-116">Genel parametreyi `T` `out` anahtar kelimeyle işaretleyerek bu sorunu çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="dc38e-117">.NET Çerçevesinde Varyant Türü Parametreleri Olan Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="dc38e-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="dc38e-118">.NET Framework 4, varolan birkaç genel temsilcide genel tür parametreleri için varyans desteği getirmiştir:</span><span class="sxs-lookup"><span data-stu-id="dc38e-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="dc38e-119">`Action`<xref:System> ad alanından delegeler, örneğin <xref:System.Action%601> ve<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="dc38e-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="dc38e-120">`Func`<xref:System> ad alanından delegeler, örneğin <xref:System.Func%601> ve<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="dc38e-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="dc38e-121">Temsilci <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="dc38e-121">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="dc38e-122">Temsilci <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="dc38e-122">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="dc38e-123">Temsilci <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="dc38e-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="dc38e-124">Daha fazla bilgi ve örnekler [için Func ve Action Generic Delegates (C#) için Varyans Kullanma'ya](./using-variance-for-func-and-action-generic-delegates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="dc38e-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="dc38e-125">Genel Temsilcilerde Varyant Türü Parametrelerinin Açıklanması</span><span class="sxs-lookup"><span data-stu-id="dc38e-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="dc38e-126">Genel bir temsilcinin ortak veya zıt genel tür parametreleri varsa, bu *türvaryant genel temsilci*olarak adlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="dc38e-127">Genel bir temsilcide anahtar sözcüğü kullanarak genel bir `out` tür parametre eşdeğişkenini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="dc38e-128">Ortak varyant türü, yöntem bağımsız değişkenleri türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="dc38e-129">Aşağıdaki kod örneği, bir ortak genel temsilcinin nasıl bildirilen gösteriş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="dc38e-130">`in` Anahtar sözcüğü kullanarak genel bir temsilcide genel tür parametre karşıtlığı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="dc38e-131">Karşıt tür, yöntem dönüş türü olarak değil, yalnızca yöntem bağımsız değişkenleri türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="dc38e-132">Aşağıdaki kod örneği, karşıt genel temsilcinin nasıl bildirilen şekli gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="dc38e-133">`ref`, `in`, `out` ve C# parametreleri varyant olarak işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="dc38e-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="dc38e-134">Aynı temsilcide hem varyans hem de covariance desteklemek de mümkündür, ancak farklı tür parametreleri için.</span><span class="sxs-lookup"><span data-stu-id="dc38e-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="dc38e-135">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="dc38e-136">Varyant Genel Temsilcileri Anında Ve Çağıran</span><span class="sxs-lookup"><span data-stu-id="dc38e-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="dc38e-137">Değişmez delegeleri anında anlayıp çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="dc38e-138">Aşağıdaki örnekte, temsilci bir lambda ifadesi ile anında.</span><span class="sxs-lookup"><span data-stu-id="dc38e-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="dc38e-139">Varyant Genel Temsilcileri Birleştirme</span><span class="sxs-lookup"><span data-stu-id="dc38e-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="dc38e-140">Varyant temsilcilerini birleştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-140">You should not combine variant delegates.</span></span> <span data-ttu-id="dc38e-141">Yöntem <xref:System.Delegate.Combine%2A> varyant temsilci dönüşümdesteklemez ve delegelertam olarak aynı türde olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="dc38e-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="dc38e-142">Bu, aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Delegate.Combine%2A> yöntemi kullanarak veya `+` işleci kullanarak temsilcileri birleştirdiğinizde çalışma zamanı özel bir durum neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="dc38e-143">Değer ve Referans Türleri için Genel Tip Parametrelerde Varyans</span><span class="sxs-lookup"><span data-stu-id="dc38e-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="dc38e-144">Genel tür parametreleri için varyans yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="dc38e-145">Örneğin, `DVariant<int>` tamsayı bir değer türü `DVariant<Object>` olduğundan, örtülü olarak dönüştürülemez veya `DVariant<long>`,</span><span class="sxs-lookup"><span data-stu-id="dc38e-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="dc38e-146">Aşağıdaki örnek, genel tür parametrelerindeki varyansın değer türleri için desteklenmediğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dc38e-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc38e-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc38e-147">See also</span></span>

- [<span data-ttu-id="dc38e-148">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="dc38e-148">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="dc38e-149">Func ve Action Generic Delegeler için Varyans Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="dc38e-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="dc38e-150">Temsilciler nasıl birleştirilir (Çok Noktaya Yayın Temsilcileri)</span><span class="sxs-lookup"><span data-stu-id="dc38e-150">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
