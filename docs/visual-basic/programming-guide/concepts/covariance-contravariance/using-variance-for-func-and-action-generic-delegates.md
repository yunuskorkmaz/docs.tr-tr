---
title: İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f2f45a9b6536859499f882b4cd585595176208f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814312"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="6b6c2-102">İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="6b6c2-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="6b6c2-103">Bu örnekler Kovaryans ve kontravaryans nasıl kazandırabileceğinizi `Func` ve `Action` yöntemleri kullanılmasını etkinleştirin ve kodunuzu daha fazla esneklik sağlamak için genel temsilciler.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="6b6c2-104">Kovaryans ve kontravaryans hakkında daha fazla bilgi için bkz: [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6b6c2-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="6b6c2-105">Birlikte değişken tür parametreleri ile kullanma</span><span class="sxs-lookup"><span data-stu-id="6b6c2-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="6b6c2-106">Kovaryans genel destek avantajları aşağıdaki örnekte `Func` temsilciler.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="6b6c2-107">`FindByTitle` Yöntemi, bir parametre alır `String` yazın ve bir nesne döndürür `Employee` türü.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="6b6c2-108">Ancak, bu yönteme atayabilirsiniz `Func(Of String, Person)` çünkü temsilci `Employee` devralan `Person`.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="6b6c2-109">Değişken karşıtı tür parametreleri ile kullanma</span><span class="sxs-lookup"><span data-stu-id="6b6c2-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="6b6c2-110">Aşağıdaki örnekte genel kontravaryans destek avantajlarını `Action` temsilciler.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="6b6c2-111">`AddToContacts` Yöntemi, bir parametre alır `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="6b6c2-112">Ancak, bu yönteme atayabilirsiniz `Action(Of Employee)` çünkü temsilci `Employee` devralan `Person`.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b6c2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b6c2-113">See also</span></span>

- [<span data-ttu-id="6b6c2-114">Kovaryans ve kontravaryans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b6c2-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="6b6c2-115">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="6b6c2-115">Generics</span></span>](~/docs/standard/generics/index.md)
