---
title: 'Nasıl yapılır: Temsilci Yöntemi Çağırma'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: f319727c007b93c7b334af0598f1b9f7c034144d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410727"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="8c104-102">Nasıl yapılır: Temsilci Yöntemi Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c104-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="8c104-103">Bu örnek, bir yöntemin bir temsilciyle nasıl ilişkilendirileceğini gösterir ve ardından bu yöntemi temsilci aracılığıyla çağırır.</span><span class="sxs-lookup"><span data-stu-id="8c104-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="8c104-104">Temsilci ve eşleştirme yordamlarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c104-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="8c104-105">Adlı bir temsilci oluşturun `MySubDelegate` .</span><span class="sxs-lookup"><span data-stu-id="8c104-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="8c104-106">Temsilciyle aynı imzaya sahip bir yöntem içeren bir sınıf bildirin.</span><span class="sxs-lookup"><span data-stu-id="8c104-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="8c104-107">Temsilcinin bir örneğini oluşturan ve yerleşik metodu çağırarak temsilciyle ilişkili yöntemi çağıran bir yöntem tanımlayın `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="8c104-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="8c104-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c104-108">See also</span></span>

- [<span data-ttu-id="8c104-109">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="8c104-109">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="8c104-110">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="8c104-110">Delegates</span></span>](index.md)
- [<span data-ttu-id="8c104-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8c104-111">Events</span></span>](../events/index.md)
- [<span data-ttu-id="8c104-112">Çok İş Parçacıklı Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="8c104-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
