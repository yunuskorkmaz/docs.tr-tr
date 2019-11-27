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
ms.openlocfilehash: 62b22a54904a45380052d3d81d9415517d4f8d3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346891"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="c81b7-102">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c81b7-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="c81b7-103">Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="c81b7-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="c81b7-104">Geçerli örneğe başvurmak için `Me` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c81b7-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="c81b7-105">Geçerli örneğe başvurmak için</span><span class="sxs-lookup"><span data-stu-id="c81b7-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="c81b7-106">Bir nesne değişkeninin adını normalde kullandığınız `Me` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="c81b7-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="c81b7-107">`Me` bir nesne değişkeni gibi davransa da, bunu bildiremez veya buna hiçbir şey atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c81b7-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="c81b7-108">`Me` her zaman geçerli örneğe başvurur.</span><span class="sxs-lookup"><span data-stu-id="c81b7-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81b7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c81b7-109">See also</span></span>

- [<span data-ttu-id="c81b7-110">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c81b7-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="c81b7-111">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="c81b7-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="c81b7-112">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="c81b7-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
