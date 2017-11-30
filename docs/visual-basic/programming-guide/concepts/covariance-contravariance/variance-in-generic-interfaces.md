---
title: Genel arabirimler (Visual Basic) varyans
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d05ccdc97efd5dd193bbbe0d15dd227ec71910d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Genel arabirimler (Visual Basic) varyans
.NET framework 4 birkaç mevcut genel arabirimler sapma desteği sunmuştur. Bu arabirimleri uygulayan sınıflar örtük dönüştürme sapma desteği sağlar. Aşağıdaki arabirimleri şimdi değişken şunlardır:  
  
-   <xref:System.Collections.Generic.IEnumerable%601>(T değişkendir)  
  
-   <xref:System.Collections.Generic.IEnumerator%601>(T değişkendir)  
  
-   <xref:System.Linq.IQueryable%601>(T değişkendir)  
  
-   <xref:System.Linq.IGrouping%602>(`TKey` ve `TElement` eşdeğişken olan)  
  
-   <xref:System.Collections.Generic.IComparer%601>(T karşıtıdır)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601>(T karşıtıdır)  
  
-   <xref:System.IComparable%601>(T karşıtıdır)  
  
 Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem izin verir. Kovaryans özelliği göstermek için bu genel arabirimler göz önünde bulundurun: `IEnumerable(Of Object)` ve `IEnumerable(Of String)`. `IEnumerable(Of String)` Arabirimi devralmaz `IEnumerable(Of Object)` arabirimi. Ancak, `String` türü devral `Object` türü ve bazı durumlarda bu arabirimleri nesnelerin birbirlerine atamak isteyebilirsiniz. Bu, aşağıdaki kod örneğinde gösterilir.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 .NET Framework önceki sürümlerinde, bu kod derleme hatası ile Visual Basic'te neden `Option Strict On`. Ancak artık kullanabilirsiniz `strings` yerine `objects`, çünkü önceki örnekte gösterildiği gibi <xref:System.Collections.Generic.IEnumerable%601> arabirimidir eşdeğişken.  
  
 Değişken karşıtı arabirimi genel parametresi tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir. Değişken karşıtı göstermek için oluşturduğunuzu varsayalım bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı. `BaseComparer` Uygulayan sınıf `IEqualityComparer(Of BaseClass)` arabirimi. Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi şimdi karşıtı, kullanabileceğiniz `BaseComparer` devral sınıfların örneklerini Karşılaştırılacak `BaseClass` sınıfı. Bu, aşağıdaki kod örneğinde gösterilir.  
  
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
  
 Daha fazla örnek için bkz: [(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir. Türlerin varyans desteklemez. Örneğin, `IEnumerable(Of Integer)` örtük olarak dönüştürülemiyor `IEnumerable(Of Object)`, tamsayı bir değer türü ile temsil edilir.  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 Değişken arabirimler uygulayan sınıflar hala değişmez olduğunu unutmamak önemlidir. Örneğin, ancak <xref:System.Collections.Generic.List%601> eşdeğişken arabirimini uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemiyor `List(Of Object)` için `List(Of String)`. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [Değişken genel arabirimler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [Genel arabirimler](../../../../standard/generics/interfaces.md)  
 [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
