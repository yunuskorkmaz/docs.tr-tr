---
title: 'Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: fe93e7bac2a21f1060d1f93765eb35e1ad0c7eb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410418"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="74cbc-102">Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74cbc-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="74cbc-103">Birçok yöntem ve özellik için bir nitelik yolu gerektiren bir nesneye sık sık erişiyorsanız, nitelik yolunu tekrarlayarak kodunuzun hızını hızlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74cbc-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="74cbc-104">Nitelik yolunu tekrardan kaçınmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="74cbc-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="74cbc-105">Nesnesini bir değişkene atayabilir veya bir `With` ... `End With` bloğunda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74cbc-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="74cbc-106">Büyük ölçüde nitelikli bir nesneye erişimi bir değişkene atayarak hızlandırmak için</span><span class="sxs-lookup"><span data-stu-id="74cbc-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="74cbc-107">Sıklıkla eriştiğiniz nesnenin türünde bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="74cbc-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="74cbc-108">Bildirimin başlatma bölümünde nitelik yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="74cbc-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="74cbc-109">Nesnenin üyelerine erişmek için değişkenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="74cbc-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="74cbc-110">Ile bir Ile kullanarak bir büyük ölçüde nitelenmiş nesneye erişimi hızlandırmak için... Blokla bitir</span><span class="sxs-lookup"><span data-stu-id="74cbc-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="74cbc-111">Nitelik yolunu bir `With` deyime koyun.</span><span class="sxs-lookup"><span data-stu-id="74cbc-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="74cbc-112">`With`Deyimden önce nesnenin blok içindeki üyelerine erişin `End With` .</span><span class="sxs-lookup"><span data-stu-id="74cbc-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="74cbc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74cbc-113">See also</span></span>

- [<span data-ttu-id="74cbc-114">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="74cbc-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="74cbc-115">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="74cbc-115">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
