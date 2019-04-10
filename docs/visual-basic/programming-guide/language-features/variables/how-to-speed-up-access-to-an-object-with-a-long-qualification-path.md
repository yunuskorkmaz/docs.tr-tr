---
title: 'Nasıl yapılır: Uzun bir nitelenmiş yola (Visual Basic) sahip nesneye erişimi hızlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299143"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="664b4-102">Nasıl yapılır: Uzun bir nitelenmiş yola (Visual Basic) sahip nesneye erişimi hızlandırma</span><span class="sxs-lookup"><span data-stu-id="664b4-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="664b4-103">Bir nitelenmiş yola çeşitli yöntemleri ve özellikleri gerektiren bir nesne sık erişirseniz, kodunuzu oluşturan nitelenmiş yola tekrarlayarak değil hızlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="664b4-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="664b4-104">Nitelenmiş yola kaçınmanızı iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="664b4-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="664b4-105">Nesneyi bir değişkene atayın ya da içinde kullanabileceğiniz bir `With`... `End With` blok.</span><span class="sxs-lookup"><span data-stu-id="664b4-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="664b4-106">Bir değişkene atayarak yoğun tam bir nesneye erişimi hızlandırma için</span><span class="sxs-lookup"><span data-stu-id="664b4-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1. <span data-ttu-id="664b4-107">Sık sık eriştiğiniz nesne türünde bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="664b4-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="664b4-108">Nitelenmiş yola bildirimi başlatma kısmında belirtin.</span><span class="sxs-lookup"><span data-stu-id="664b4-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="664b4-109">Bir nesnenin üyelerine erişmek için bu değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="664b4-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="664b4-110">Bir ile kullanarak, yoğun bir şekilde tam bir nesneye erişimi hızlandırma için... End With bloğu</span><span class="sxs-lookup"><span data-stu-id="664b4-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1. <span data-ttu-id="664b4-111">Nitelenmiş yola yerleştirecek bir `With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="664b4-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="664b4-112">İçinde bir nesnenin üyelerine erişmek `With` önce bloğunda `End With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="664b4-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="664b4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="664b4-113">See also</span></span>

- [<span data-ttu-id="664b4-114">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="664b4-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="664b4-115">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="664b4-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
