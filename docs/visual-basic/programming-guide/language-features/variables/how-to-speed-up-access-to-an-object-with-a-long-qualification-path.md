---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: uzun bir nitelik yolu olan bir nesneye erişimi hızlandırma (Visual Basic)'
title: 'Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 8e0b5dc2ab6c23d57a4e9d905cfd711a79843185
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467049"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="e48af-103">Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e48af-103">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="e48af-104">Birçok yöntem ve özellik için bir nitelik yolu gerektiren bir nesneye sık sık erişiyorsanız, nitelik yolunu tekrarlayarak kodunuzun hızını hızlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e48af-104">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="e48af-105">Nitelik yolunu tekrardan kaçınmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e48af-105">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="e48af-106">Nesnesini bir değişkene atayabilir veya bir `With` ... `End With` bloğunda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e48af-106">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="e48af-107">Büyük ölçüde nitelikli bir nesneye erişimi bir değişkene atayarak hızlandırmak için</span><span class="sxs-lookup"><span data-stu-id="e48af-107">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="e48af-108">Sıklıkla eriştiğiniz nesnenin türünde bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="e48af-108">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="e48af-109">Bildirimin başlatma bölümünde nitelik yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="e48af-109">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="e48af-110">Nesnenin üyelerine erişmek için değişkenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e48af-110">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="e48af-111">Ile bir Ile kullanarak bir büyük ölçüde nitelenmiş nesneye erişimi hızlandırmak için... Blokla bitir</span><span class="sxs-lookup"><span data-stu-id="e48af-111">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="e48af-112">Nitelik yolunu bir `With` deyime koyun.</span><span class="sxs-lookup"><span data-stu-id="e48af-112">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="e48af-113">`With`Deyimden önce nesnenin blok içindeki üyelerine erişin `End With` .</span><span class="sxs-lookup"><span data-stu-id="e48af-113">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="e48af-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e48af-114">See also</span></span>

- [<span data-ttu-id="e48af-115">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e48af-115">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e48af-116">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="e48af-116">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
