---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: bir nesnenin geçerli örneğine başvurma (Visual Basic)'
title: 'Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 84a52c9d0a8b1f588630b31d022490f37595850d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481746"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="036ed-103">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="036ed-103">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>

<span data-ttu-id="036ed-104">Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="036ed-104">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="036ed-105">`Me`Geçerli örneğe başvurmak için anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="036ed-105">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="036ed-106">Geçerli örneğe başvurmak için</span><span class="sxs-lookup"><span data-stu-id="036ed-106">To refer to the current instance</span></span>  
  
- <span data-ttu-id="036ed-107">`Me`Normalde bir nesne değişkeninin adını kullanacağınız anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="036ed-107">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="036ed-108">`Me`Bir nesne değişkeni gibi davranmakla birlikte, bunu bildiremez veya buna hiçbir şey atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="036ed-108">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="036ed-109">`Me` her zaman geçerli örneğe başvurur.</span><span class="sxs-lookup"><span data-stu-id="036ed-109">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036ed-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="036ed-110">See also</span></span>

- [<span data-ttu-id="036ed-111">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="036ed-111">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="036ed-112">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="036ed-112">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="036ed-113">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="036ed-113">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
