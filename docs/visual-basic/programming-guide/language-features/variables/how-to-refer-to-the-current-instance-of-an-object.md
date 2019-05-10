---
title: 'Nasıl yapılır: (Visual Basic) bir nesnenin geçerli örneğine başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 70955cd55dfb91d4111e59ae58bfe409a4470433
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663538"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="430a6-102">Nasıl yapılır: (Visual Basic) bir nesnenin geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="430a6-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="430a6-103">*Geçerli örneğin* nesnenin hangi kod şu anda Yürütülüyor örneğidir.</span><span class="sxs-lookup"><span data-stu-id="430a6-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="430a6-104">Kullandığınız `Me` geçerli örneğine başvurma anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="430a6-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="430a6-105">Geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="430a6-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="430a6-106">Kullanma `Me` anahtar sözcüğü nerede normalde kullandığınız bir nesne değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="430a6-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="430a6-107">Olsa da `Me` davranacağını gibi bir nesne değişkeni, bildirmek veya herhangi bir şey atayın.</span><span class="sxs-lookup"><span data-stu-id="430a6-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="430a6-108">`Me` her zaman geçerli örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="430a6-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430a6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="430a6-109">See also</span></span>

- [<span data-ttu-id="430a6-110">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="430a6-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="430a6-111">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="430a6-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="430a6-112">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="430a6-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
