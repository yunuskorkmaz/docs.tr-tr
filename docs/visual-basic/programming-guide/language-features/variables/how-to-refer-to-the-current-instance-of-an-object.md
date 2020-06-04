---
title: 'Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 43bfd54592fb1d26cbf7f268b7e098e01e3745d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410431"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="8fb97-102">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fb97-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="8fb97-103">Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="8fb97-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="8fb97-104">`Me`Geçerli örneğe başvurmak için anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8fb97-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="8fb97-105">Geçerli örneğe başvurmak için</span><span class="sxs-lookup"><span data-stu-id="8fb97-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="8fb97-106">`Me`Normalde bir nesne değişkeninin adını kullanacağınız anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fb97-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="8fb97-107">`Me`Bir nesne değişkeni gibi davranmakla birlikte, bunu bildiremez veya buna hiçbir şey atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8fb97-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="8fb97-108">`Me`her zaman geçerli örneğe başvurur.</span><span class="sxs-lookup"><span data-stu-id="8fb97-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb97-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb97-109">See also</span></span>

- [<span data-ttu-id="8fb97-110">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8fb97-110">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="8fb97-111">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="8fb97-111">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="8fb97-112">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="8fb97-112">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
