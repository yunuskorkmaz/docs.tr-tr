---
title: Genel Arabirimlerde Varyans
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 1f6913b322e2d3d9ec2234e556e63d67324277e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348988"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Genel Arabirimlerde Varyans (Visual Basic)

.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir. Varyans desteği, bu arabirimleri uygulayan sınıfların örtük dönüştürülmesini mümkün. Aşağıdaki arabirimler artık değişkendir:

- <xref:System.Collections.Generic.IEnumerable%601> (T birlikte değişken)

- <xref:System.Collections.Generic.IEnumerator%601> (T birlikte değişken)

- <xref:System.Linq.IQueryable%601> (T birlikte değişken)

- <xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` birlikte değişken)

- <xref:System.Collections.Generic.IComparer%601> (T değişken karşıtı)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T değişken karşıtı)

- <xref:System.IComparable%601> (T değişken karşıtı)

Kovaryans, bir metodun, arabirimin genel tür parametresiyle tanımlananla daha türetilmiş bir dönüş türüne sahip olmasını sağlar. Kovaryans özelliğini göstermek için şu genel arabirimleri göz önünde bulundurun: `IEnumerable(Of Object)` ve `IEnumerable(Of String)`. `IEnumerable(Of String)` arabirimi `IEnumerable(Of Object)` arabirimini almıyor. Ancak `String` türü `Object` türünü devralınır ve bazı durumlarda bu arabirimlerin nesnelerini birbirlerine atamak isteyebilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

.NET Framework önceki sürümlerinde bu kod, Visual Basic `Option Strict On`derleme hatasına neden olur. Ancak artık, <xref:System.Collections.Generic.IEnumerable%601> arabirimi birlikte değişken olduğundan, önceki örnekte gösterildiği gibi `objects`yerine `strings` kullanabilirsiniz.

Değişken Varyans, bir metodun, arabirimin genel parametresiyle belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasını sağlar. Değişken varyansı göstermek için, `BaseClass` sınıfının örneklerini karşılaştırmak üzere bir `BaseComparer` sınıfı oluşturduğunuzu varsayalım. `BaseComparer` sınıfı `IEqualityComparer(Of BaseClass)` arabirimini uygular. <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi artık değişken karşıtı olduğundan, `BaseClass` sınıfını devraldığı sınıfların örneklerini karşılaştırmak için `BaseComparer` kullanabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```vb
' Simple hierarchy of classes.
Class BaseClass
End Class

Class DerivedClass
    Inherits BaseClass
End Class

' Comparer class.
Class BaseComparer
    Implements IEqualityComparer(Of BaseClass)

    Public Function Equals1(ByVal x As BaseClass,
                            ByVal y As BaseClass) As Boolean _
                            Implements IEqualityComparer(Of BaseClass).Equals
        Return (x.Equals(y))
    End Function

    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _
        Implements IEqualityComparer(Of BaseClass).GetHashCode
        Return obj.GetHashCode
    End Function
End Class
Sub Test()
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to
    ' IEqualityComparer(Of DerivedClass).
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer
End Sub
```

Daha fazla örnek için bkz. [Genel Koleksiyonlar Için Arabirimlerde Varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).

Genel Arabirimlerde Varyans yalnızca başvuru türleri için desteklenir. Değer türleri varyansı desteklemez. Örneğin, tamsayılar bir değer türüyle temsil edildiği için `IEnumerable(Of Integer)` örtük olarak `IEnumerable(Of Object)`dönüştürülemez.

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

Ayrıca, VARIANT arabirimlerini uygulayan sınıfların hala sabit olduğunu unutmamak önemlidir. Örneğin, <xref:System.Collections.Generic.List%601> covaryant arabirimini <xref:System.Collections.Generic.IEnumerable%601>uygular, ancak `List(Of Object)` örtük olarak `List(Of String)`dönüştürebilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Değişken genel arabirimler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Genel Arabirimler](../../../../standard/generics/interfaces.md)
- [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
