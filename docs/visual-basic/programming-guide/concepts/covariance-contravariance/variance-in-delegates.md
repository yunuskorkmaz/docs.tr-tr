---
title: Temsilcilerde varyans (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 6d341c7c2b5adeebcafc5b0787b132ab6bd57e41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787237"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="5aa2f-102">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aa2f-102">Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="5aa2f-103">.NET framework 3.5 sunulan tüm temsilcileri içindeki temsilci türleriyle yöntem imzalarının eşleştirilmesi için varyans Destek C# ve Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="5aa2f-104">Yalnızca imzalarının eşleştirilmesi içeren yöntemlerin yanı sıra temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip bir parametre kabul eden ya da daha fazla türetilmiş türler (kovaryans) döndüren yöntemler için atayabileceğiniz anlamına gelir temsilciler .</span><span class="sxs-lookup"><span data-stu-id="5aa2f-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="5aa2f-105">Bu, hem genel hem de genel olmayan temsilcileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-105">This includes both generic and non-generic delegates.</span></span>

<span data-ttu-id="5aa2f-106">Örneğin, iki sınıf ve iki temsilci olduğunda sahip aşağıdaki kodu düşünün: Genel ve genel olmayan.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

<span data-ttu-id="5aa2f-107">Temsilciler, oluşturduğunuzda `SampleDelegate` veya `SampleDelegate(Of A, R)` türleri, bu temsilcileri için aşağıdaki yöntemlerden herhangi birini atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>

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

<span data-ttu-id="5aa2f-108">Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasında örtülü dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>

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

<span data-ttu-id="5aa2f-109">Daha fazla örnek için bkz. [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="5aa2f-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="5aa2f-110">Genel tür parametreleri varyans</span><span class="sxs-lookup"><span data-stu-id="5aa2f-110">Variance in Generic Type Parameters</span></span>

<span data-ttu-id="5aa2f-111">Böylece türlerini birbirinden gerektirdiği devralınırsa, genel tür parametrelerle belirtilen farklı türlere sahip genel temsilciler birbiriyle atanabilir .NET Framework 4 ve üzeri temsilciler arasında örtük dönüştürme etkinleştirebilirsiniz farkı.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>

<span data-ttu-id="5aa2f-112">Örtük dönüştürme etkinleştirmek için açıkça genel parametreler birlikte değişken olarak bir temsilci bildirmeniz gerekir veya kullanarak, değişken karşıtı `in` veya `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>

<span data-ttu-id="5aa2f-113">Aşağıdaki kod örneği, bir genel birlikte değişen türde parametresi olan bir temsilci nasıl oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>

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

<span data-ttu-id="5aa2f-114">Tek farkı destek eşleştirilecek kullanırsanız birlikte yöntem imzaları temsilci türleri ve kullanmaz `in` ve `out` anahtar bulduğunuz bazen aynı lambda ifadeleri veya yöntemler ile temsilciler örneği oluşturabilir, ancak bunu yapamazsınız bir temsilci diğerine atayın.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>

<span data-ttu-id="5aa2f-115">Aşağıdaki kod örneğinde, `SampleGenericDelegate(Of String)` açıkça dönüştürülemez `SampleGenericDelegate(Of Object)`, ancak `String` devralan `Object`.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="5aa2f-116">Genel parametre olarak işaretleyerek bu sorunu düzeltebilirsiniz `T` ile `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>

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

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="5aa2f-117">.NET Framework tür parametreleri varyant sahip genel temsilciler</span><span class="sxs-lookup"><span data-stu-id="5aa2f-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>

<span data-ttu-id="5aa2f-118">.NET framework 4, varolan birçok genel temsilciler genel tür parametrelerinde varyansı başlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="5aa2f-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>

- <span data-ttu-id="5aa2f-119">`Action` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Action%601> ve <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="5aa2f-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>

- <span data-ttu-id="5aa2f-120">`Func` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Func%601> ve <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="5aa2f-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>

- <span data-ttu-id="5aa2f-121"><xref:System.Predicate%601> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="5aa2f-121">The <xref:System.Predicate%601> delegate</span></span>

- <span data-ttu-id="5aa2f-122"><xref:System.Comparison%601> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="5aa2f-122">The <xref:System.Comparison%601> delegate</span></span>

- <span data-ttu-id="5aa2f-123"><xref:System.Converter%602> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="5aa2f-123">The <xref:System.Converter%602> delegate</span></span>

<span data-ttu-id="5aa2f-124">Daha fazla bilgi ve örnekler için bkz. [işlev ve eylem genel temsilcileri (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="5aa2f-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="5aa2f-125">Değişken türünde parametreler genel temsilciler bildirme</span><span class="sxs-lookup"><span data-stu-id="5aa2f-125">Declaring Variant Type Parameters in Generic Delegates</span></span>

<span data-ttu-id="5aa2f-126">Genel temsilci birlikte değişken veya değişken karşıtı genel tür parametreleri, başvurulabilir olarak varsa bir *değişken Genel temsilci*.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>

<span data-ttu-id="5aa2f-127">Genel tür parametresi birlikte değişken Genel temsilci kullanarak bildirebilirsiniz `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="5aa2f-128">Birlikte değişken türünde yöntem bağımsız bir tür değil de, yalnızca bir yöntem dönüş türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="5aa2f-129">Aşağıdaki kod örneği, birlikte değişken genel bir temsilcinin nasıl belirtileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-129">The following code example shows how to declare a covariant generic delegate.</span></span>

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

<span data-ttu-id="5aa2f-130">Genel tür parametresi değişken karşıtı Genel temsilci kullanarak bildirebilirsiniz `in` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="5aa2f-131">Değişken karşıtı türü, yöntemin dönüş türü değil de, yalnızca bir tür yöntem bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="5aa2f-132">Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl belirtileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-132">The following code example shows how to declare a contravariant generic delegate.</span></span>

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> <span data-ttu-id="5aa2f-133">`ByRef` Visual Basic'te parametreleri varyant olarak işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>

<span data-ttu-id="5aa2f-134">Farkı hem Kovaryans aynı temsilci, ancak farklı tür parametreleri için destek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="5aa2f-135">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-135">This is shown in the following example.</span></span>

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="5aa2f-136">Örnekleme ve bunları çağırırken değişken genel temsilciler</span><span class="sxs-lookup"><span data-stu-id="5aa2f-136">Instantiating and Invoking Variant Generic Delegates</span></span>

<span data-ttu-id="5aa2f-137">Örneği oluşturun ve yalnızca örneklemek ve sabit temsilciler çağırmak değişken temsilciler çağır.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="5aa2f-138">Aşağıdaki örnekte, temsilci bir lambda ifadesiyle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="5aa2f-139">Değişken genel temsilciler birleştirme</span><span class="sxs-lookup"><span data-stu-id="5aa2f-139">Combining Variant Generic Delegates</span></span>

<span data-ttu-id="5aa2f-140">Değişken temsilciler birleştirmemelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-140">You should not combine variant delegates.</span></span> <span data-ttu-id="5aa2f-141"><xref:System.Delegate.Combine%2A> Yöntemi değişken temsilci dönüştürmeyi desteklemez ve temsilciler tam olarak aynı veri türünde olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="5aa2f-142">Temsilcileri kullanarak ya da birleştirdiğinizde bu için bir çalışma zamanı özel durumuna neden olabilir <xref:System.Delegate.Combine%2A> yöntemi (içinde C# ve Visual Basic) veya kullanarak `+` işleci (içinde C#), aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="5aa2f-143">Değer ve başvuru türleri için genel tür parametrelerindeki varyansı</span><span class="sxs-lookup"><span data-stu-id="5aa2f-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>

<span data-ttu-id="5aa2f-144">Varyans genel tür parametreleri için yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="5aa2f-145">Örneğin, `DVariant(Of Int)`için örtük olarak dönüştürülemez `DVariant(Of Object)` veya `DVariant(Of Long)`tamsayı değer türü olduğundan.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>

<span data-ttu-id="5aa2f-146">Aşağıdaki örnek, bu farkı göstermektedir genel tür parametreleri değer türleri için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>

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

## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="5aa2f-147">Visual Basic'te gevşek temsilci dönüşümü</span><span class="sxs-lookup"><span data-stu-id="5aa2f-147">Relaxed Delegate Conversion in Visual Basic</span></span>

<span data-ttu-id="5aa2f-148">Gevşek temsilci dönüşümü temsilci türleriyle yöntem imzalarının eşleştirilmesi daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="5aa2f-149">Örneğin, parametre belirtimleri çıkarın ve bir yöntem temsilciye atadığınızda işlevi dönüş değerleri çıkarın olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="5aa2f-150">Daha fazla bilgi için [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="5aa2f-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5aa2f-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa2f-151">See also</span></span>

- [<span data-ttu-id="5aa2f-152">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5aa2f-152">Generics</span></span>](~/docs/standard/generics/index.md)
- [<span data-ttu-id="5aa2f-153">İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="5aa2f-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
