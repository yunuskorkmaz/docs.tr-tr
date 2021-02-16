---
description: 'Daha fazla bilgi edinin: Temsilcilerde varyans (Visual Basic)'
title: Temsilcilerde Varyans
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: d47f05a5ce3f3e59223f1f37ab09fb8a21e6e7ba
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100458973"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="45632-103">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45632-103">Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="45632-104">.NET Framework 3,5, C# ve Visual Basic tüm Temsilcilerde temsilci türleriyle eşleşen yöntem imzaları için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="45632-104">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="45632-105">Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş tür (değişken varyans) içeren parametreleri kabul eden yöntemler için atama yaptığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="45632-105">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="45632-106">Bu hem genel hem de genel olmayan temsilcileri içerir.</span><span class="sxs-lookup"><span data-stu-id="45632-106">This includes both generic and non-generic delegates.</span></span>

<span data-ttu-id="45632-107">Örneğin, iki sınıfı ve iki temsilciyi olan aşağıdaki kodu düşünün: genel ve genel olmayan.</span><span class="sxs-lookup"><span data-stu-id="45632-107">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

<span data-ttu-id="45632-108">`SampleDelegate`Veya türlerinin temsilcilerini oluşturduğunuzda `SampleDelegate(Of A, R)` , aşağıdaki yöntemlerden herhangi birini bu temsilcilere atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45632-108">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

<span data-ttu-id="45632-109">Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasındaki örtük dönüştürmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="45632-109">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

<span data-ttu-id="45632-110">Daha fazla örnek için bkz. [Temsilcilerde varyans kullanma (Visual Basic)](using-variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="45632-110">For more examples, see [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="45632-111">Genel tür parametrelerindeki varyans</span><span class="sxs-lookup"><span data-stu-id="45632-111">Variance in Generic Type Parameters</span></span>

<span data-ttu-id="45632-112">.NET Framework 4 ' te ve daha sonra temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz. böylece türler, genel tür parametreleri tarafından belirtilen farklı türlere sahip olan genel temsilcilerin birbirini fark eden her bir öğeden devralınabileceği her diğerine atanabilmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="45632-112">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>

<span data-ttu-id="45632-113">Örtük dönüştürmeyi etkinleştirmek için, `in` veya anahtar sözcüğünü kullanarak bir temsilcinin genel parametrelerini birlikte değişken veya değişken karşıtı olarak açıkça bildirmeniz gerekir `out` .</span><span class="sxs-lookup"><span data-stu-id="45632-113">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>

<span data-ttu-id="45632-114">Aşağıdaki kod örneği, birlikte değişken genel tür parametresine sahip olan bir temsilciyi nasıl oluşturabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="45632-114">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

<span data-ttu-id="45632-115">Yöntem imzalarını temsilci türleriyle eşleştirmek için yalnızca varyans desteğini kullanırsanız ve `in` ve `out` anahtar sözcüklerini kullanmıyorsanız, bazen aynı lambda ifadeleri veya yöntemlerine sahip temsilciler örnekleyebilirsiniz, ancak bir temsilciyi başka bir temsilciye atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="45632-115">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>

<span data-ttu-id="45632-116">Aşağıdaki kod örneğinde, `SampleGenericDelegate(Of String)` açıkça öğesine dönüştürülemez `SampleGenericDelegate(Of Object)` , ancak `String` devralır `Object` .</span><span class="sxs-lookup"><span data-stu-id="45632-116">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="45632-117">Genel parametreyi anahtar sözcüğüyle işaretleyerek bu sorunu çözebilirsiniz `T` `out` .</span><span class="sxs-lookup"><span data-stu-id="45632-117">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="45632-118">.NET Framework değişken tür parametrelerine sahip genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="45632-118">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>

<span data-ttu-id="45632-119">.NET Framework 4, çeşitli genel temsilcilerde genel tür parametrelerine yönelik varyans desteği getirmiştir:</span><span class="sxs-lookup"><span data-stu-id="45632-119">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>

- <span data-ttu-id="45632-120">`Action` ad alanından temsilciler, <xref:System> Örneğin <xref:System.Action%601> ve <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="45632-120">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>

- <span data-ttu-id="45632-121">`Func` ad alanından temsilciler, <xref:System> Örneğin <xref:System.Func%601> ve <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="45632-121">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>

- <span data-ttu-id="45632-122"><xref:System.Predicate%601>Temsilci</span><span class="sxs-lookup"><span data-stu-id="45632-122">The <xref:System.Predicate%601> delegate</span></span>

- <span data-ttu-id="45632-123"><xref:System.Comparison%601>Temsilci</span><span class="sxs-lookup"><span data-stu-id="45632-123">The <xref:System.Comparison%601> delegate</span></span>

- <span data-ttu-id="45632-124"><xref:System.Converter%602>Temsilci</span><span class="sxs-lookup"><span data-stu-id="45632-124">The <xref:System.Converter%602> delegate</span></span>

<span data-ttu-id="45632-125">Daha fazla bilgi ve örnek için bkz. [Func ve eylem genel temsilcileri Için varyans kullanma (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="45632-125">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="45632-126">Genel Temsilcilerde değişken tür parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="45632-126">Declaring Variant Type Parameters in Generic Delegates</span></span>

<span data-ttu-id="45632-127">Genel bir temsilcinin birlikte değişken veya değişken karşıtı genel tür parametreleri varsa, bu, *VARIANT genel temsilcisi* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="45632-127">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>

<span data-ttu-id="45632-128">Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi ortak değişkeni bildirebilirsiniz `out` .</span><span class="sxs-lookup"><span data-stu-id="45632-128">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="45632-129">Covaryant türü, yöntem bağımsız değişkenlerinin türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45632-129">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="45632-130">Aşağıdaki kod örneği, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="45632-130">The following code example shows how to declare a covariant generic delegate.</span></span>

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

<span data-ttu-id="45632-131">Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi değişken değişkeni bildirebilirsiniz `in` .</span><span class="sxs-lookup"><span data-stu-id="45632-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="45632-132">Değişken karşıtı türü, yöntem dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45632-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="45632-133">Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="45632-133">The following code example shows how to declare a contravariant generic delegate.</span></span>

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> <span data-ttu-id="45632-134">`ByRef` Visual Basic parametreler değişken olarak işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="45632-134">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>

<span data-ttu-id="45632-135">Aynı temsilci, ancak farklı tür parametreleri için hem varyansı hem de kovaryansı desteklemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="45632-135">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="45632-136">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="45632-136">This is shown in the following example.</span></span>

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="45632-137">VARIANT genel temsilcileri örnekleme ve çağırma</span><span class="sxs-lookup"><span data-stu-id="45632-137">Instantiating and Invoking Variant Generic Delegates</span></span>

<span data-ttu-id="45632-138">Sabit temsilcileri örneklediğinizde ve çağırdığınızda değişken temsilcileri örnek oluşturabilir ve çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45632-138">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="45632-139">Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45632-139">In the following example, the delegate is instantiated by a lambda expression.</span></span>

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="45632-140">Değişken genel temsilcileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="45632-140">Combining Variant Generic Delegates</span></span>

<span data-ttu-id="45632-141">Değişken temsilcileri birleştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="45632-141">You should not combine variant delegates.</span></span> <span data-ttu-id="45632-142"><xref:System.Delegate.Combine%2A>Yöntem, değişken temsilci dönüştürmeyi desteklemez ve temsilcilerin tamamen aynı türde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="45632-142">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="45632-143">Bu, <xref:System.Delegate.Combine%2A> `+` Aşağıdaki kod örneğinde gösterildiği gibi, (c# ve Visual Basic) ya da işlecini kullanarak (c# ' de), temsilcileri birleştirdiğinizde bir çalışma zamanı özel durumuna yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="45632-143">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="45632-144">Değer ve başvuru türleri için genel tür parametrelerinin varyansı</span><span class="sxs-lookup"><span data-stu-id="45632-144">Variance in Generic Type Parameters for Value and Reference Types</span></span>

<span data-ttu-id="45632-145">Genel tür parametrelerinin varyansı yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="45632-145">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="45632-146">Örneğin, `DVariant(Of Int)` `DVariant(Of Object)` tamsayı bir değer türü olduğundan, örtülü olarak veya `DVariant(Of Long)` türüne dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="45632-146">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>

<span data-ttu-id="45632-147">Aşağıdaki örnek, genel tür parametrelerinin farkının değer türleri için desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="45632-147">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="45632-148">Visual Basic için gevşek temsilci dönüştürme</span><span class="sxs-lookup"><span data-stu-id="45632-148">Relaxed Delegate Conversion in Visual Basic</span></span>

<span data-ttu-id="45632-149">Gevşek temsilci dönüştürme, temsilci türleriyle eşleşen Yöntem imzalarında daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="45632-149">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="45632-150">Örneğin, bir temsilciye bir yöntem atarken parametre belirtimlerini ve işlev dönüş değerlerini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="45632-150">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="45632-151">Daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../../language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="45632-151">For more information, see [Relaxed Delegate Conversion](../../language-features/delegates/relaxed-delegate-conversion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45632-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45632-152">See also</span></span>

- [<span data-ttu-id="45632-153">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="45632-153">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="45632-154">Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45632-154">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)
