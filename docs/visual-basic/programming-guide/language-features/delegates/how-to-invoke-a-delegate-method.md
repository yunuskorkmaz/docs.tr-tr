---
title: 'Nasıl yapılır: (Visual Basic) temsilci yöntemi çağırma'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: ac3e32010e7c20ba76e39915d694b11ab3a65d40
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319618"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="455bc-102">Nasıl yapılır: (Visual Basic) temsilci yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="455bc-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="455bc-103">Bu örnek, bir yöntem bir temsilci ile ilişkilendirin ve ardından o yöntemi temsilci aracılığıyla çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="455bc-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="455bc-104">Temsilci ve eşleşen yordamlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="455bc-104">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="455bc-105">Adlı bir temsilci oluşturmak `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="455bc-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2. <span data-ttu-id="455bc-106">Temsilci olarak aynı imzaya sahip bir yöntemi içeren bir sınıfı bildirir.</span><span class="sxs-lookup"><span data-stu-id="455bc-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3. <span data-ttu-id="455bc-107">Temsilci örneği oluşturur ve temsilci ile yerleşik çağırarak ilişkili yöntemi çağırır bir yöntemi tanımlamak `Invoke` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="455bc-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="455bc-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="455bc-108">See also</span></span>

- [<span data-ttu-id="455bc-109">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="455bc-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="455bc-110">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="455bc-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="455bc-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="455bc-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="455bc-112">Çok İş Parçacıklı Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="455bc-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
