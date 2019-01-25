---
title: Temsilcilerde varyans (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 350f8d6b317f6a82d5b5a718a3d49a4b9ee3e4b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631548"
---
# <a name="variance-in-delegates-visual-basic"></a>Temsilcilerde varyans (Visual Basic)
.NET framework 3.5 sunulan tüm temsilcileri içindeki temsilci türleriyle yöntem imzalarının eşleştirilmesi için varyans Destek C# ve Visual Basic. Yalnızca imzalarının eşleştirilmesi içeren yöntemlerin yanı sıra temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip bir parametre kabul eden ya da daha fazla türetilmiş türler (kovaryans) döndüren yöntemler için atayabileceğiniz anlamına gelir temsilciler . Bu, hem genel hem de genel olmayan temsilcileri içerir.  
  
 Örneğin, iki sınıf ve iki temsilci olduğunda sahip aşağıdaki kodu düşünün: Genel ve genel olmayan.  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 Temsilciler, oluşturduğunuzda `SampleDelegate` veya `SampleDelegate(Of A, R)` türleri, bu temsilcileri için aşağıdaki yöntemlerden herhangi birini atayabilirsiniz.  
  
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
  
 Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasında örtülü dönüştürme gösterilmektedir.  
  
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
  
 Daha fazla örnek için bkz. [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Genel tür parametreleri varyans  
 Böylece türlerini birbirinden gerektirdiği devralınırsa, genel tür parametrelerle belirtilen farklı türlere sahip genel temsilciler birbiriyle atanabilir .NET Framework 4 ve üzeri temsilciler arasında örtük dönüştürme etkinleştirebilirsiniz farkı.  
  
 Örtük dönüştürme etkinleştirmek için açıkça genel parametreler birlikte değişken olarak bir temsilci bildirmeniz gerekir veya kullanarak, değişken karşıtı `in` veya `out` anahtar sözcüğü.  
  
 Aşağıdaki kod örneği, bir genel birlikte değişen türde parametresi olan bir temsilci nasıl oluşturabileceğinizi gösterir.  
  
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
  
 Tek farkı destek eşleştirilecek kullanırsanız birlikte yöntem imzaları temsilci türleri ve kullanmaz `in` ve `out` anahtar bulduğunuz bazen aynı lambda ifadeleri veya yöntemler ile temsilciler örneği oluşturabilir, ancak bunu yapamazsınız bir temsilci diğerine atayın.  
  
 Aşağıdaki kod örneğinde, `SampleGenericDelegate(Of String)` açıkça dönüştürülemez `SampleGenericDelegate(Of Object)`, ancak `String` devralan `Object`. Genel parametre olarak işaretleyerek bu sorunu düzeltebilirsiniz `T` ile `out` anahtar sözcüğü.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework tür parametreleri varyant sahip genel temsilciler  
 .NET framework 4, varolan birçok genel temsilciler genel tür parametrelerinde varyansı başlanmıştır:  
  
-   `Action` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Action%601> ve <xref:System.Action%602>  
  
-   `Func` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Func%601> ve <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Temsilci seçme  
  
-   <xref:System.Comparison%601> Temsilci seçme  
  
-   <xref:System.Converter%602> Temsilci seçme  
  
 Daha fazla bilgi ve örnekler için bkz. [işlev ve eylem genel temsilcileri (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Değişken türünde parametreler genel temsilciler bildirme  
 Genel temsilci birlikte değişken veya değişken karşıtı genel tür parametreleri, başvurulabilir olarak varsa bir *değişken Genel temsilci*.  
  
 Genel tür parametresi birlikte değişken Genel temsilci kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Birlikte değişken türünde yöntem bağımsız bir tür değil de, yalnızca bir yöntem dönüş türü olarak kullanılabilir. Aşağıdaki kod örneği, birlikte değişken genel bir temsilcinin nasıl belirtileceğini gösterir.  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 Genel tür parametresi değişken karşıtı Genel temsilci kullanarak bildirebilirsiniz `in` anahtar sözcüğü. Değişken karşıtı türü, yöntemin dönüş türü değil de, yalnızca bir tür yöntem bağımsız olarak kullanılabilir. Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl belirtileceğini gösterir.  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  `ByRef` Visual Basic'te parametreleri varyant olarak işaretlenemez.  
  
 Farkı hem Kovaryans aynı temsilci, ancak farklı tür parametreleri için destek de mümkündür. Bu, aşağıdaki örnekte gösterilir.  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Örnekleme ve bunları çağırırken değişken genel temsilciler  
 Örneği oluşturun ve yalnızca örneklemek ve sabit temsilciler çağırmak değişken temsilciler çağır. Aşağıdaki örnekte, temsilci bir lambda ifadesiyle başlatılır.  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a>Değişken genel temsilciler birleştirme  
 Değişken temsilciler birleştirmemelisiniz değil. <xref:System.Delegate.Combine%2A> Yöntemi değişken temsilci dönüştürmeyi desteklemez ve temsilciler tam olarak aynı veri türünde olmasını bekliyor. Temsilcileri kullanarak ya da birleştirdiğinizde bu için bir çalışma zamanı özel durumuna neden olabilir <xref:System.Delegate.Combine%2A> yöntemi (içinde C# ve Visual Basic) veya kullanarak `+` işleci (içinde C#), aşağıdaki kod örneğinde gösterildiği gibi.  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Değer ve başvuru türleri için genel tür parametrelerindeki varyansı  
 Varyans genel tür parametreleri için yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant(Of Int)`için örtük olarak dönüştürülemez `DVariant(Of Object)` veya `DVariant(Of Long)`tamsayı değer türü olduğundan.  
  
 Aşağıdaki örnek, bu farkı göstermektedir genel tür parametreleri değer türleri için desteklenmiyor.  
  
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
 Gevşek temsilci dönüşümü temsilci türleriyle yöntem imzalarının eşleştirilmesi daha fazla esneklik sağlar. Örneğin, parametre belirtimleri çıkarın ve bir yöntem temsilciye atadığınızda işlevi dönüş değerleri çıkarın olanak tanır. Daha fazla bilgi için [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Genel Türler](~/docs/standard/generics/index.md)
- [İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
