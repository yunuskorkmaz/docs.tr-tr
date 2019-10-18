---
title: Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: a85d6ae2fa32547958e557bbe45b9405e9b660ef
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524249"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)

Bu örnekler, `Func` Kovaryans ve karşıtlık farkının nasıl kullanılacağını ve yöntemlerin yeniden kullanımını etkinleştirmek ve kodunuzda daha fazla esneklik sağlamak için genel Temsilciler `Action` gösterir.

Kovaryans ve değişken varyans hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).

## <a name="using-delegates-with-covariant-type-parameters"></a>Birlikte değişken tür parametrelerine sahip temsilciler kullanma

Aşağıdaki örnekte, genel `Func` temsilcilerde kovaryans desteğinin avantajları gösterilmektedir. @No__t_0 yöntemi `String` türünün bir parametresini alır ve `Employee` türünün bir nesnesini döndürür. Ancak, `Employee` `Person` devraldığı için bu yöntemi `Func(Of String, Person)` temsilcisine atayabilirsiniz.

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

Aşağıdaki örnekte, genel `Action` Temsilcilerde değişken olmayan varyans desteğinin avantajları gösterilmektedir. @No__t_0 yöntemi `Person` türünün bir parametresini alır. Ancak, `Employee` `Person` devraldığı için bu yöntemi `Action(Of Employee)` temsilcisine atayabilirsiniz.

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

- [Kovaryans ve değişken varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Genel Türler](../../../../standard/generics/index.md)
