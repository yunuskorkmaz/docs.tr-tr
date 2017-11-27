---
title: "Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="f1024-102">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1024-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="f1024-103">*Geçerli örnek* bir nesne, kod şu anda Yürütülüyor örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f1024-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="f1024-104">Kullandığınız `Me` geçerli örneğine başvurma anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f1024-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="f1024-105">Geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="f1024-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="f1024-106">Kullanmak `Me` anahtar sözcüğü burada normalde kullandığınız bir nesne değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="f1024-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="f1024-107">Ancak `Me` bir nesne gibi davranır değişken, edemezsiniz bildirirken veya hiçbir şey atayın.</span><span class="sxs-lookup"><span data-stu-id="f1024-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="f1024-108">`Me`her zaman geçerli örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="f1024-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1024-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1024-109">See Also</span></span>  
 [<span data-ttu-id="f1024-110">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f1024-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="f1024-111">Nesne değişkeni ataması</span><span class="sxs-lookup"><span data-stu-id="f1024-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="f1024-112">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="f1024-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
