---
title: Temsilcilerde varyans (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9fe76a32f76f760497021289ec1c6ce673cec1b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="feacd-102">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feacd-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="feacd-103">.NET framework 3.5 yöntem imzaları bulunan tüm temsilcileri C# ve Visual Basic temsilci türleriyle eşleşen farkı desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="feacd-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="feacd-104">Yalnızca imzalar eşleşen yöntemleri, aynı zamanda daha fazla türetilmiş tür (kovaryans) veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul döndüren yöntemler için atayabilirsiniz Bunun anlamı temsilciler .</span><span class="sxs-lookup"><span data-stu-id="feacd-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="feacd-105">Bu, hem genel hem de genel olmayan temsilciler içerir.</span><span class="sxs-lookup"><span data-stu-id="feacd-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="feacd-106">Örneğin, iki sınıf ve iki temsilciler aşağıdaki kodu göz önünde bulundurun: Genel ve genel olmayan.</span><span class="sxs-lookup"><span data-stu-id="feacd-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="feacd-107">Temsilciler, oluşturduğunuzda `SampleDelegate` veya `SampleDelegate(Of A, R)` türleri, aşağıdaki yöntemlerden birini bu temsilcileri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="feacd-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="feacd-108">Aşağıdaki kod örneğinde yöntem imzası ve temsilci türü arasında örtük dönüşüm gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feacd-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="feacd-109">Daha fazla örnek için bkz: [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [işlev ve eylem genel temsilciler (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="feacd-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="feacd-110">Genel tür parametreleri varyans</span><span class="sxs-lookup"><span data-stu-id="feacd-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="feacd-111">Böylece türlerini birbirinden gerektirdiği şekilde devralınırsa, genel tür parametresi tarafından belirtilen farklı türlerine sahip genel temsilciler birbirine atanabilir .NET Framework 4 ve üzeri temsilciler arasında örtük dönüştürmeye etkinleştirebilirsiniz sapması.</span><span class="sxs-lookup"><span data-stu-id="feacd-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="feacd-112">Örtük dönüştürme etkinleştirmek için açıkça bir temsilci eşdeğişken olarak genel parametreleri bildirmeniz gerekir veya kullanarak karşıtı `in` veya `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="feacd-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="feacd-113">Aşağıdaki kod örneğinde eşdeğişken genel tür parametresi var. bir temsilci nasıl oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="feacd-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="feacd-114">Eşleştirilecek tek farkı destek kullanırsanız, yöntemi imzalarla temsilci türleri'yı ve kullanmayın `in` ve `out` anahtar sözcüklerini bulduğunuz bazen aynı lambda ifadeleri veya yöntemleri ile temsilciler örneğini oluşturabilirsiniz, ancak yapamazsınız bir temsilci diğerine atayın.</span><span class="sxs-lookup"><span data-stu-id="feacd-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="feacd-115">Aşağıdaki kod örneğinde, `SampleGenericDelegate(Of String)` açıkça dönüştürülemiyor `SampleGenericDelegate(Of Object)`, ancak `String` devralır `Object`.</span><span class="sxs-lookup"><span data-stu-id="feacd-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="feacd-116">Genel parametresini işaretleyerek bu sorunu düzeltebilirsiniz `T` ile `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="feacd-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="feacd-117">.NET Framework değişken sahip genel temsilciler tür parametreleri</span><span class="sxs-lookup"><span data-stu-id="feacd-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="feacd-118">.NET framework 4 birkaç mevcut genel temsilciler genel tür parametreleri sapma desteği sunulur:</span><span class="sxs-lookup"><span data-stu-id="feacd-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="feacd-119">`Action`gelen Temsilciler <xref:System> ad alanı, örneğin, <xref:System.Action%601> ve<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="feacd-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="feacd-120">`Func`gelen Temsilciler <xref:System> ad alanı, örneğin, <xref:System.Func%601> ve<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="feacd-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="feacd-121"><xref:System.Predicate%601> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="feacd-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="feacd-122"><xref:System.Comparison%601> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="feacd-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="feacd-123"><xref:System.Converter%602> Temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="feacd-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="feacd-124">Daha fazla bilgi ve örnekler için bkz: [işlev ve eylem genel temsilciler (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="feacd-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="feacd-125">Genel temsilciler değişken türü parametrelerinde bildirme</span><span class="sxs-lookup"><span data-stu-id="feacd-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="feacd-126">Genel temsilci eşdeğişken varsa veya karşıtı genel tür parametreleri, onu başvurulabilir için farklı bir *değişken Genel temsilci*.</span><span class="sxs-lookup"><span data-stu-id="feacd-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="feacd-127">Genel tür parametresi bir genel temsilci eşdeğişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="feacd-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="feacd-128">Eşdeğişken türü yöntem bağımsız değişkenleri bir tür değil de, yalnızca bir yöntemin dönüş türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="feacd-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="feacd-129">Aşağıdaki kod örneğinde eşdeğişken Genel temsilci bildirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feacd-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 <span data-ttu-id="feacd-130">Kullanarak bir genel tür parametresi karşıtı genel temsilcisi de bildirebilirsiniz `in` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="feacd-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="feacd-131">Karşıtı türü yönteminin dönüş türü olarak değil de yalnızca yöntem bağımsız değişkenleri bir tür olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="feacd-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="feacd-132">Aşağıdaki kod örneğinde karşıtı Genel temsilci bildirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feacd-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="feacd-133">`ByRef`Visual Basic'te parametreleri değişken işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="feacd-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="feacd-134">Aynı temsilci, ancak farklı tür parametreleri için sapması ve Kovaryans desteklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="feacd-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="feacd-135">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="feacd-135">This is shown in the following example.</span></span>  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="feacd-136">Örnek oluşturma ve değişken genel temsilciler çağırma</span><span class="sxs-lookup"><span data-stu-id="feacd-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="feacd-137">Örneği ve yalnızca örneği ve sabit temsilciler çağırma değişken temsilciler çağırma.</span><span class="sxs-lookup"><span data-stu-id="feacd-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="feacd-138">Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="feacd-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="feacd-139">Değişken genel temsilciler birleştirme</span><span class="sxs-lookup"><span data-stu-id="feacd-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="feacd-140">Değişken temsilciler birleştirmelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="feacd-140">You should not combine variant delegates.</span></span> <span data-ttu-id="feacd-141"><xref:System.Delegate.Combine%2A> Yöntemi değişken temsilci dönüşümü desteklemez ve temsilciler tam olarak aynı türünde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="feacd-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="feacd-142">Ya da kullanarak temsilcileri birleştirme olduğunda bu bir çalışma zamanı özel yol açabilir <xref:System.Delegate.Combine%2A> yöntemi (C# ve Visual Basic) kullanarak veya `+` işleci (C#), aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="feacd-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="feacd-143">Genel tür parametreleri varyans değer ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="feacd-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="feacd-144">Genel tür parametreleri için varyansı yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="feacd-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="feacd-145">Örneğin, `DVariant(Of Int)`örtük olarak dönüştürülemiyor `DVariant(Of Object)` veya `DVariant(Of Long)`, çünkü tamsayı değer türü.</span><span class="sxs-lookup"><span data-stu-id="feacd-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="feacd-146">Aşağıdaki örnek, bu farkı gösterir genel tür parametreleri değer türleri için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="feacd-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="feacd-147">Visual Basic'te gevşek temsilci dönüşümü</span><span class="sxs-lookup"><span data-stu-id="feacd-147">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="feacd-148">Gevşek temsilci dönüşümü yöntem imzaları temsilci türleri ile eşleşen daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="feacd-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="feacd-149">Örneğin, bir temsilci için bir yöntem atadığınızda işlevi dönüş değerleri atlayın ve parametre belirtimleri atlarsanız olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="feacd-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="feacd-150">Daha fazla bilgi için bkz: [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="feacd-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feacd-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feacd-151">See Also</span></span>  
 [<span data-ttu-id="feacd-152">Genel türler</span><span class="sxs-lookup"><span data-stu-id="feacd-152">Generics</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="feacd-153">İşlev ve eylem genel temsilciler (Visual Basic) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="feacd-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
