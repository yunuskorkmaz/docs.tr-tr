---
title: 'Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: c1b79f1b6a9768941d6fe966c5b5886ea742f808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648365"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="2685a-102">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2685a-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="2685a-103">*Geçerli örnek* bir nesne, kod şu anda Yürütülüyor örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2685a-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="2685a-104">Kullandığınız `Me` geçerli örneğine başvurma anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2685a-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="2685a-105">Geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="2685a-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="2685a-106">Kullanmak `Me` anahtar sözcüğü burada normalde kullandığınız bir nesne değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="2685a-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="2685a-107">Ancak `Me` bir nesne gibi davranır değişken, edemezsiniz bildirirken veya hiçbir şey atayın.</span><span class="sxs-lookup"><span data-stu-id="2685a-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="2685a-108">`Me` her zaman geçerli örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="2685a-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2685a-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2685a-109">See Also</span></span>  
 [<span data-ttu-id="2685a-110">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="2685a-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="2685a-111">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="2685a-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="2685a-112">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="2685a-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
