---
title: "Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="e6ced-102">Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6ced-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="e6ced-103">Çeşitli yöntemleri ve özellikleri nitelenmiş yolunu gerektirir nesneyi sık erişirse, nitelenmiş yola tekrarlayarak değil, kod hızlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="e6ced-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="e6ced-104">Nitelenmiş yola kaçınmanızı iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e6ced-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="e6ced-105">Nesneyi bir değişkene atayın veya içinde kullanabileceğiniz bir `With`... `End With` bloğu.</span><span class="sxs-lookup"><span data-stu-id="e6ced-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="e6ced-106">Bir değişkene atayarak yoğun olarak tam bir nesneye erişimi hızlandırma için</span><span class="sxs-lookup"><span data-stu-id="e6ced-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="e6ced-107">Sık sık eriştiğiniz nesne türünde bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="e6ced-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="e6ced-108">Nitelenmiş yola bildirimi başlatma parçası belirtin.</span><span class="sxs-lookup"><span data-stu-id="e6ced-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="e6ced-109">Nesnenin üyelere erişmek için değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6ced-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="e6ced-110">Bir WITH kullanarak yoğun olarak tam bir nesneye erişimi hızlandırma için... End With bloğu</span><span class="sxs-lookup"><span data-stu-id="e6ced-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="e6ced-111">Nitelenmiş yola yerleştirecek bir `With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e6ced-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="e6ced-112">Nesnenin üyeleri içinde erişim `With` önce bloğunu `End With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e6ced-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6ced-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ced-113">See Also</span></span>  
 [<span data-ttu-id="e6ced-114">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e6ced-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="e6ced-115">İle... End With deyimi</span><span class="sxs-lookup"><span data-stu-id="e6ced-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
