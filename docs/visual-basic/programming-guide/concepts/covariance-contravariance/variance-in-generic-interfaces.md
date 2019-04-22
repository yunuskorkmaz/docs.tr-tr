---
title: Variance in Generic Interfaces (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 50a1aeb5c17a0f193b9e90ca2167ef298f7ed237
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828114"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Variance in Generic Interfaces (Visual Basic)
.NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur. Bu arabirimleri uygulayan sınıfların örtük dönüştürme varyansı desteği sağlar. Aşağıdaki arabirimlerinden şimdi değişken şunlardır:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T değişkendir)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T değişkendir)  
  
-   <xref:System.Linq.IQueryable%601> (T değişkendir)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` birlikte değişken olduğu)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T karşıtıdır)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T karşıtıdır)  
  
-   <xref:System.IComparable%601> (T karşıtıdır)  
  
 Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem sağlar. Kovaryans özelliği açıklamak için bu genel arabirimler göz önünde bulundurun: `IEnumerable(Of Object)` ve `IEnumerable(Of String)`. `IEnumerable(Of String)` Arabirimi devralmaz `IEnumerable(Of Object)` arabirimi. Ancak, `String` türü devralma `Object` türü ve bazı durumlarda bu arabirimler nesnelerin birbirleriyle atamak isteyebilirsiniz. Bu aşağıdaki kod örneğinde gösterilir.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Önceki .NET Framework sürümlerinde, bu kod Visual Basic ile bir derleme hatasına neden olur. `Option Strict On`. Ancak artık kullanabilirsiniz `strings` yerine `objects`için önceki örnekte gösterilen şekilde <xref:System.Collections.Generic.IEnumerable%601> arabirimidir birlikte değişken.  
  
 Kontravaryans, genel arabirimi parametre olarak belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir. Kontravaryans göstermek için oluşturduğunuz varsayılır bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı. `BaseComparer` Sınıfının Implements `IEqualityComparer(Of BaseClass)` arabirimi. Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi, artık değişken karşıtı, kullanabileceğiniz `BaseComparer` devralan sınıfların örneklerini karşılaştırmak için `BaseClass` sınıfı. Bu aşağıdaki kod örneğinde gösterilir.  
  
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
  
 Daha fazla örnek için bkz. [(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir. Değer türleri varyansı desteklemez. Örneğin, `IEnumerable(Of Integer)` için örtük olarak dönüştürülemez `IEnumerable(Of Object)`, tamsayı değer türü tarafından temsil edilir.  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 Değişken arabirimleri uygulayan sınıflar yine de sabit olduğunu unutmamak önemlidir. Örneğin, ancak <xref:System.Collections.Generic.List%601> birlikte değişken arabirimi uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemez `List(Of Object)` için `List(Of String)`. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Değişken genel arabirimler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Genel Arabirimler](../../../../standard/generics/interfaces.md)
- [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
