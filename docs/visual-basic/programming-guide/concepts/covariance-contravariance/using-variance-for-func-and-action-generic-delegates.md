---
title: İşlev ve Eylem Genel Temsilcileri için Varyans Kullanma
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f824d2422d67f1395d21a0863ca8c95d9f108989
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375764"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)

Bu örnekler, ve ' de `Func` `Action` yöntemlerin yeniden kullanımını etkinleştirmek ve kodunuzda daha fazla esneklik sağlamak için ve genel temsilcilerde kovaryans ve değişken varyans kullanımını gösterir.

Kovaryans ve değişken varyans hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı (Visual Basic)](variance-in-delegates.md).

## <a name="using-delegates-with-covariant-type-parameters"></a>Birlikte değişken tür parametrelerine sahip temsilciler kullanma

Aşağıdaki örnekte, genel temsilcilerde kovaryans desteğinin avantajları gösterilmektedir `Func` . `FindByTitle`Yöntemi, türünün bir parametresini alır `String` ve türünün bir nesnesini döndürür `Employee` . Ancak, `Func(Of String, Person)` devraldığından bu yöntemi temsilciye atayabilirsiniz `Employee` `Person` .

```vb
' Simple hierarchy of classes.
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class Finder
    Public Shared Function FindByTitle(
        ByVal title As String) As Employee
        ' This is a stub for a method that returns
        ' an employee that has the specified title.
        Return New Employee
    End Function

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim findEmployee As Func(Of String, Employee) =
            AddressOf FindByTitle

        ' The delegate expects a method to return Person,
        ' but you can assign it a method that returns Employee.
        Dim findPerson As Func(Of String, Person) =
            AddressOf FindByTitle

        ' You can also assign a delegate
        ' that returns a more derived type to a delegate
        ' that returns a less derived type.
        findPerson = findEmployee
    End Sub
End Class
```

## <a name="using-delegates-with-contravariant-type-parameters"></a>Değişken karşıtı tür parametreleriyle temsilciler kullanma

Aşağıdaki örnekte, genel Temsilcilerde değişken varyans desteğinin avantajları gösterilmektedir `Action` . `AddToContacts`Yöntemi, türünün bir parametresini alır `Person` . Ancak, `Action(Of Employee)` devraldığından bu yöntemi temsilciye atayabilirsiniz `Employee` `Person` .

```vb
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class AddressBook
    Shared Sub AddToContacts(ByVal person As Person)
        ' This method adds a Person object
        ' to a contact list.
    End Sub

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim addPersonToContacts As Action(Of Person) =
            AddressOf AddToContacts

        ' The Action delegate expects
        ' a method that has an Employee parameter,
        ' but you can assign it a method that has a Person parameter
        ' because Employee derives from Person.
        Dim addEmployeeToContacts As Action(Of Employee) =
            AddressOf AddToContacts

        ' You can also assign a delegate
        ' that accepts a less derived parameter
        ' to a delegate that accepts a more derived parameter.
        addEmployeeToContacts = addPersonToContacts
    End Sub
End Class
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kovaryans ve değişken varyans (Visual Basic)](index.md)
- [Genel Türler](../../../../standard/generics/index.md)
