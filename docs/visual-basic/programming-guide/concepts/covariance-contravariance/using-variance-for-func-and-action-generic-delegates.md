---
title: Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: ce560f6246469620032ececa4afeeffe69baf407
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664355"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="b094f-102">Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b094f-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="b094f-103">Bu örnekler, `Func` ve ' de yöntemlerin yeniden kullanımını etkinleştirmek ve kodunuzda daha `Action` fazla esneklik sağlamak için ve genel temsilcilerde kovaryans ve değişken varyans kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b094f-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="b094f-104">Kovaryans ve değişken varyans hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b094f-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="b094f-105">Birlikte değişken tür parametrelerine sahip temsilciler kullanma</span><span class="sxs-lookup"><span data-stu-id="b094f-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="b094f-106">Aşağıdaki örnekte, genel `Func` temsilcilerde kovaryans desteğinin avantajları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b094f-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="b094f-107">Yöntemi, `String` türünün bir parametresini alır ve `Employee` türünün bir nesnesini döndürür. `FindByTitle`</span><span class="sxs-lookup"><span data-stu-id="b094f-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="b094f-108">Ancak, devraldığından `Func(Of String, Person)` `Employee` `Person`bu yöntemi temsilciye atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b094f-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="b094f-109">Değişken karşıtı tür parametreleriyle temsilciler kullanma</span><span class="sxs-lookup"><span data-stu-id="b094f-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="b094f-110">Aşağıdaki örnekte, genel `Action` Temsilcilerde değişken varyans desteğinin avantajları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b094f-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="b094f-111">Yöntemi, `Person` türünün bir parametresini alır. `AddToContacts`</span><span class="sxs-lookup"><span data-stu-id="b094f-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="b094f-112">Ancak, devraldığından `Action(Of Employee)` `Employee` `Person`bu yöntemi temsilciye atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b094f-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b094f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b094f-113">See also</span></span>

- [<span data-ttu-id="b094f-114">Kovaryans ve değişken varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b094f-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="b094f-115">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b094f-115">Generics</span></span>](../../../../standard/generics/index.md)
