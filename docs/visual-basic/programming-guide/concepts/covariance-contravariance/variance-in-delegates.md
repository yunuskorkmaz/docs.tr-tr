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
# <a name="variance-in-delegates-visual-basic"></a>Temsilcilerde varyans (Visual Basic)
.NET framework 3.5 yöntem imzaları bulunan tüm temsilcileri C# ve Visual Basic temsilci türleriyle eşleşen farkı desteği sunmuştur. Yalnızca imzalar eşleşen yöntemleri, aynı zamanda daha fazla türetilmiş tür (kovaryans) veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul döndüren yöntemler için atayabilirsiniz Bunun anlamı temsilciler . Bu, hem genel hem de genel olmayan temsilciler içerir.  
  
 Örneğin, iki sınıf ve iki temsilciler aşağıdaki kodu göz önünde bulundurun: Genel ve genel olmayan.  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 Temsilciler, oluşturduğunuzda `SampleDelegate` veya `SampleDelegate(Of A, R)` türleri, aşağıdaki yöntemlerden birini bu temsilcileri atayabilirsiniz.  
  
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
  
 Aşağıdaki kod örneğinde yöntem imzası ve temsilci türü arasında örtük dönüşüm gösterilmektedir.  
  
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
  
 Daha fazla örnek için bkz: [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [işlev ve eylem genel temsilciler (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Genel tür parametreleri varyans  
 Böylece türlerini birbirinden gerektirdiği şekilde devralınırsa, genel tür parametresi tarafından belirtilen farklı türlerine sahip genel temsilciler birbirine atanabilir .NET Framework 4 ve üzeri temsilciler arasında örtük dönüştürmeye etkinleştirebilirsiniz sapması.  
  
 Örtük dönüştürme etkinleştirmek için açıkça bir temsilci eşdeğişken olarak genel parametreleri bildirmeniz gerekir veya kullanarak karşıtı `in` veya `out` anahtar sözcüğü.  
  
 Aşağıdaki kod örneğinde eşdeğişken genel tür parametresi var. bir temsilci nasıl oluşturabileceğinizi gösterir.  
  
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
  
 Eşleştirilecek tek farkı destek kullanırsanız, yöntemi imzalarla temsilci türleri'yı ve kullanmayın `in` ve `out` anahtar sözcüklerini bulduğunuz bazen aynı lambda ifadeleri veya yöntemleri ile temsilciler örneğini oluşturabilirsiniz, ancak yapamazsınız bir temsilci diğerine atayın.  
  
 Aşağıdaki kod örneğinde, `SampleGenericDelegate(Of String)` açıkça dönüştürülemiyor `SampleGenericDelegate(Of Object)`, ancak `String` devralır `Object`. Genel parametresini işaretleyerek bu sorunu düzeltebilirsiniz `T` ile `out` anahtar sözcüğü.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework değişken sahip genel temsilciler tür parametreleri  
 .NET framework 4 birkaç mevcut genel temsilciler genel tür parametreleri sapma desteği sunulur:  
  
-   `Action`gelen Temsilciler <xref:System> ad alanı, örneğin, <xref:System.Action%601> ve<xref:System.Action%602>  
  
-   `Func`gelen Temsilciler <xref:System> ad alanı, örneğin, <xref:System.Func%601> ve<xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Temsilci seçme  
  
-   <xref:System.Comparison%601> Temsilci seçme  
  
-   <xref:System.Converter%602> Temsilci seçme  
  
 Daha fazla bilgi ve örnekler için bkz: [işlev ve eylem genel temsilciler (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Genel temsilciler değişken türü parametrelerinde bildirme  
 Genel temsilci eşdeğişken varsa veya karşıtı genel tür parametreleri, onu başvurulabilir için farklı bir *değişken Genel temsilci*.  
  
 Genel tür parametresi bir genel temsilci eşdeğişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Eşdeğişken türü yöntem bağımsız değişkenleri bir tür değil de, yalnızca bir yöntemin dönüş türü olarak kullanılabilir. Aşağıdaki kod örneğinde eşdeğişken Genel temsilci bildirme gösterilmektedir.  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 Kullanarak bir genel tür parametresi karşıtı genel temsilcisi de bildirebilirsiniz `in` anahtar sözcüğü. Karşıtı türü yönteminin dönüş türü olarak değil de yalnızca yöntem bağımsız değişkenleri bir tür olarak kullanılabilir. Aşağıdaki kod örneğinde karşıtı Genel temsilci bildirme gösterilmektedir.  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  `ByRef`Visual Basic'te parametreleri değişken işaretlenemez.  
  
 Aynı temsilci, ancak farklı tür parametreleri için sapması ve Kovaryans desteklemek mümkündür. Bu, aşağıdaki örnekte gösterilir.  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Örnek oluşturma ve değişken genel temsilciler çağırma  
 Örneği ve yalnızca örneği ve sabit temsilciler çağırma değişken temsilciler çağırma. Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından başlatılmış.  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a>Değişken genel temsilciler birleştirme  
 Değişken temsilciler birleştirmelisiniz değil. <xref:System.Delegate.Combine%2A> Yöntemi değişken temsilci dönüşümü desteklemez ve temsilciler tam olarak aynı türünde olmasını bekler. Ya da kullanarak temsilcileri birleştirme olduğunda bu bir çalışma zamanı özel yol açabilir <xref:System.Delegate.Combine%2A> yöntemi (C# ve Visual Basic) kullanarak veya `+` işleci (C#), aşağıdaki kod örneğinde gösterildiği gibi.  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Genel tür parametreleri varyans değer ve başvuru türleri  
 Genel tür parametreleri için varyansı yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant(Of Int)`örtük olarak dönüştürülemiyor `DVariant(Of Object)` veya `DVariant(Of Long)`, çünkü tamsayı değer türü.  
  
 Aşağıdaki örnek, bu farkı gösterir genel tür parametreleri değer türleri için desteklenmiyor.  
  
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
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Visual Basic'te gevşek temsilci dönüşümü  
 Gevşek temsilci dönüşümü yöntem imzaları temsilci türleri ile eşleşen daha fazla esneklik sağlar. Örneğin, bir temsilci için bir yöntem atadığınızda işlevi dönüş değerleri atlayın ve parametre belirtimleri atlarsanız olanak sağlar. Daha fazla bilgi için bkz: [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel türler](~/docs/standard/generics/index.md)  
 [İşlev ve eylem genel temsilciler (Visual Basic) için varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
