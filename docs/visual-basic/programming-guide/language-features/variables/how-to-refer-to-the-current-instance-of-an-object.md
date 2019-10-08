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
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005659"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="eccf6-102">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eccf6-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="eccf6-103">Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="eccf6-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="eccf6-104">Geçerli örneğe başvurmak için `Me` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="eccf6-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="eccf6-105">Geçerli örneğe başvurmak için</span><span class="sxs-lookup"><span data-stu-id="eccf6-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="eccf6-106">Normalde bir nesne değişkeninin adını kullanacağınız `Me` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="eccf6-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="eccf6-107">@No__t-0 bir nesne değişkeni gibi davransa da, bunu bildiremez veya buna hiçbir şey atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="eccf6-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="eccf6-108">`Me` her zaman geçerli örneğe başvurur.</span><span class="sxs-lookup"><span data-stu-id="eccf6-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eccf6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eccf6-109">See also</span></span>

- [<span data-ttu-id="eccf6-110">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="eccf6-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="eccf6-111">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="eccf6-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="eccf6-112">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="eccf6-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
