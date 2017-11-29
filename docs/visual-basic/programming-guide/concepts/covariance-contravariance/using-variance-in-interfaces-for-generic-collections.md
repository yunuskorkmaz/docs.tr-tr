---
title: "(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b8944bf8f6377ddc633f81dccd9f379bf176d9f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma
Eşdeğişken arabirimi arabiriminde belirtilenlerden daha türetilmiş türler döndürülecek yöntemlerini sağlar. Karşıtı arabirimi belirtilenlerden daha az türetilmiş türler arabiriminde parametrelerinin kabul etmek yöntemlerini sağlar.  
  
 .NET Framework 4'te birkaç varolan arabirimleri eşdeğişken hale geldi ve karşıtı. Bunlar <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601>. Genel koleksiyonlar türetilen türler için temel türleri çalışır yöntemleri yeniden kullanmanıza olanak sağlar.  
  
 .NET Framework'teki değişken arabirimler listesi için bkz: [genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Genel koleksiyonlar dönüştürme  
 Aşağıdaki örnek Kovaryans desteği yararları gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601> arabirimi. `PrintFullName` Yöntemi kabul koleksiyonu `IEnumerable(Of Person)` türünü bir parametre olarak. Ancak, onu bir koleksiyonu için tekrar kullanabilirsiniz `IEnumerable(Of Person)` yazın, çünkü `Employee` devralır `Person`.  
  
```vb  
' Simple hierarchy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
' The method has a parameter of the IEnumerable(Of Person) type.  
Public Sub PrintFullName(ByVal persons As IEnumerable(Of Person))  
    For Each person As Person In persons  
        Console.WriteLine(  
            "Name: " & person.FirstName & " " & person.LastName)  
    Next  
End Sub  
  
Sub Main()  
    Dim employees As IEnumerable(Of Employee) = New List(Of Employee)  
  
    ' You can pass IEnumerable(Of Employee),   
    ' although the method expects IEnumerable(Of Person).  
  
    PrintFullName(employees)  
  
End Sub  
```  
  
## <a name="comparing-generic-collections"></a>Genel koleksiyonları karşılaştırma  
 Aşağıdaki örnekte, değişken karşıtı desteği yararları gösterilmektedir <xref:System.Collections.Generic.IComparer%601> arabirimi. `PersonComparer` Uygulayan sınıf `IComparer(Of Person)` arabirimi. Ancak, bir dizi nesnelerin karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz `Employee` yazın, çünkü `Employee` devralır `Person`.  
  
```vb  
' Simple hierarhcy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
' The custom comparer for the Person type  
' with standard implementations of Equals()  
' and GetHashCode() methods.  
Class PersonComparer  
    Implements IEqualityComparer(Of Person)  
  
    Public Function Equals1(  
        ByVal x As Person,  
        ByVal y As Person) As Boolean _  
        Implements IEqualityComparer(Of Person).Equals  
  
        If x Is y Then Return True  
        If x Is Nothing OrElse y Is Nothing Then Return False  
        Return (x.FirstName = y.FirstName) AndAlso  
            (x.LastName = y.LastName)  
    End Function  
    Public Function GetHashCode1(  
        ByVal person As Person) As Integer _  
        Implements IEqualityComparer(Of Person).GetHashCode  
  
        If person Is Nothing Then Return 0  
        Dim hashFirstName =  
            If(person.FirstName Is Nothing,  
            0, person.FirstName.GetHashCode())  
        Dim hashLastName = person.LastName.GetHashCode()  
        Return hashFirstName Xor hashLastName  
    End Function  
End Class  
  
Sub Main()  
    Dim employees = New List(Of Employee) From {  
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},  
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}  
    }  
  
    ' You can pass PersonComparer,   
    ' which implements IEqualityComparer(Of Person),  
    ' although the method expects IEqualityComparer(Of Employee)  
  
    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())  
  
    For Each employee In noduplicates  
        Console.WriteLine(employee.FirstName & " " & employee.LastName)  
    Next  
End Sub  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
