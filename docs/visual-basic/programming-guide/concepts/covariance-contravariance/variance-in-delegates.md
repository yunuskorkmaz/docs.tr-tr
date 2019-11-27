---
title: Temsilcilerde Varyans
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 11146bc4a60f55fc0373f0b5dfa5d44dcf748a5b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349009"
---
# <a name="variance-in-delegates-visual-basic"></a>Temsilcilerde varyans (Visual Basic)

.NET Framework 3,5, C# ve Visual Basic tüm Temsilcilerde temsilci türleriyle eşleşen yöntem imzaları için varyans desteği getirmiştir. Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (değişken varyans) döndüren parametreleri kabul eden yöntemlere atayabileceğiniz anlamına gelir. . Bu hem genel hem de genel olmayan temsilcileri içerir.

Örneğin, iki sınıfı ve iki temsilciyi olan aşağıdaki kodu düşünün: genel ve genel olmayan.

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

`SampleDelegate` veya `SampleDelegate(Of A, R)` türlerinin temsilcilerini oluşturduğunuzda, aşağıdaki yöntemlerden herhangi birini bu temsilcilere atayabilirsiniz.

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

Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasındaki örtük dönüştürmeyi gösterir.

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

Daha fazla örnek için bkz. [Temsilcilerde varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

## <a name="variance-in-generic-type-parameters"></a>Genel tür parametrelerindeki varyans

.NET Framework 4 ' te ve daha sonraki sürümlerde temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz, böylece türler, her biri için gerekli olan genel tür parametreleri tarafından belirtilen genel temsilcilerin birbirlerine atanabilmesini sağlar. denetlemesini.

Örtük dönüştürmeyi etkinleştirmek için, `in` veya `out` anahtar sözcüğünü kullanarak bir temsilcinin genel parametrelerini ortak değişken veya değişken karşıtı olarak açıkça bildirmeniz gerekir.

Aşağıdaki kod örneği, birlikte değişken genel tür parametresine sahip olan bir temsilciyi nasıl oluşturabileceğiniz gösterilmektedir.

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

Yöntem imzalarını temsilci türleriyle eşleştirmek için yalnızca varyans desteğini kullanırsanız ve `in` ve `out` anahtar sözcüklerini kullanmıyorsanız, bazen aynı lambda ifadeleri veya yöntemlerine sahip temsilciler örnekleyebilirsiniz, ancak bir temsilciyi diğerine atayamazsınız.

Aşağıdaki kod örneğinde, `String` `Object`devramla birlikte `SampleGenericDelegate(Of String)` açıkça `SampleGenericDelegate(Of Object)`dönüştürülemiyor. Genel parametre `T` `out` anahtar sözcüğüyle işaretleyerek bu sorunu çözebilirsiniz.

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

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework değişken tür parametrelerine sahip genel Temsilciler

.NET Framework 4, çeşitli genel temsilcilerde genel tür parametrelerine yönelik varyans desteği getirmiştir:

- <xref:System> ad alanından temsilciler `Action`, örneğin <xref:System.Action%601> ve <xref:System.Action%602>

- <xref:System> ad alanından temsilciler `Func`, örneğin <xref:System.Func%601> ve <xref:System.Func%602>

- <xref:System.Predicate%601> temsilcisi

- <xref:System.Comparison%601> temsilcisi

- <xref:System.Converter%602> temsilcisi

Daha fazla bilgi ve örnek için bkz. [Func ve eylem genel temsilcileri Için varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Genel Temsilcilerde değişken tür parametreleri bildirme

Genel bir temsilcinin birlikte değişken veya değişken karşıtı genel tür parametreleri varsa, bu, *VARIANT genel temsilcisi*olarak adlandırılır.

`out` anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi ortak değişkeni bildirebilirsiniz. Covaryant türü, yöntem bağımsız değişkenlerinin türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir. Aşağıdaki kod örneği, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini gösterir.

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

`in` anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi değişken değişkeni bildirebilirsiniz. Değişken karşıtı türü, yöntem dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir. Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini gösterir.

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> Visual Basic `ByRef` parametreler değişken olarak işaretlenemez.

Aynı temsilci, ancak farklı tür parametreleri için hem varyansı hem de kovaryansı desteklemek de mümkündür. Bu, aşağıdaki örnekte gösterilir.

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>VARIANT genel temsilcileri örnekleme ve çağırma

Sabit temsilcileri örneklediğinizde ve çağırdığınızda değişken temsilcileri örnek oluşturabilir ve çağırabilirsiniz. Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından oluşturulur.

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>Değişken genel temsilcileri birleştirme

Değişken temsilcileri birleştirmemelisiniz. <xref:System.Delegate.Combine%2A> yöntemi, VARIANT temsilci dönüştürmeyi desteklemez ve temsilcilerin tamamen aynı türde olmasını bekler. Bu, aşağıdaki kod örneğinde gösterildiği gibi, temsilcileri <xref:System.Delegate.Combine%2A> yöntemi ( C# ve Visual Basic) veya `+` işlecini (içinde C#) kullanarak birleştirdiğinizde bir çalışma zamanı özel durumuna yol açabilir.

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Değer ve başvuru türleri için genel tür parametrelerinin varyansı

Genel tür parametrelerinin varyansı yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant(Of Int)`örtük olarak `DVariant(Of Object)` veya `DVariant(Of Long)`dönüştürülemez, çünkü tamsayı bir değer türüdür.

Aşağıdaki örnek, genel tür parametrelerinin farkının değer türleri için desteklenmediğini gösterir.

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

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Visual Basic için gevşek temsilci dönüştürme

Gevşek temsilci dönüştürme, temsilci türleriyle eşleşen Yöntem imzalarında daha fazla esneklik sağlar. Örneğin, bir temsilciye bir yöntem atarken parametre belirtimlerini ve işlev dönüş değerlerini atlamanızı sağlar. Daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](../../../../standard/generics/index.md)
- [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
