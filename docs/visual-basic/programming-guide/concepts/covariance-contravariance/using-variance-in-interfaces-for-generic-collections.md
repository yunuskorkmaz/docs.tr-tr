---
title: Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: b762ce42215f9b24371313446637e95962677bfb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375647"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (Visual Basic)

Birlikte değişken arabirimi, yöntemlerinin arabirimde belirtilenden daha fazla türetilmiş tür döndürmesini sağlar. Değişken karşıtı bir arabirim, yöntemlerinin, arabirimde belirtilenden daha az türetilmiş türdeki parametreleri kabul etmesine olanak sağlar.

.NET Framework 4 ' te, bazı mevcut arabirimler birlikte değişken ve değişken karşıtı hale gelmiştir. Bunlar <xref:System.Collections.Generic.IEnumerable%601> ve içerir <xref:System.IComparable%601> . Bu, türetilmiş türlerin koleksiyonları için genel temel tür koleksiyonlarıyla çalışan yöntemleri yeniden kullanmanıza olanak sağlar.

.NET Framework değişken arabirimlerin listesi için bkz. [Genel Arabirimlerde Varyans (Visual Basic)](variance-in-generic-interfaces.md).

## <a name="converting-generic-collections"></a>Genel koleksiyonları dönüştürme

Aşağıdaki örnekte, arabirimindeki Kovaryans desteğinin avantajları gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601> . `PrintFullName`Yöntemi, türü bir koleksiyonu `IEnumerable(Of Person)` bir parametre olarak kabul eder. Ancak, devraldığından bir tür koleksiyonu için onu yeniden kullanabilirsiniz `IEnumerable(Of Person)` `Employee` `Person` .

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

Aşağıdaki örnek, arabirimindeki fark desteğinin avantajlarından yararlanır <xref:System.Collections.Generic.IComparer%601> . `PersonComparer` sınıfı, `IComparer(Of Person)` arabirimini uygular. Ancak, devraldığından tür bir nesne dizisini karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz `Employee` `Employee` `Person` .

```vb
' Simple hierarchy of classes.
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

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans (Visual Basic)](variance-in-generic-interfaces.md)
