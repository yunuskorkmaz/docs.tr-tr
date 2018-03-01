---
title: "&#39; &lt;anahtar sözcüğü&gt;&#39; yalnızca bir örnek yöntemi içinde geçerli değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="9638b-102">&#39; &lt;anahtar sözcüğü&gt;&#39; yalnızca bir örnek yöntemi içinde geçerli değil</span><span class="sxs-lookup"><span data-stu-id="9638b-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="9638b-103">`Me`, `MyClass`, Ve `MyBase` anahtar sözcükleri belirli bir sınıfın örneklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="9638b-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="9638b-104">Bunları paylaşılan içinde kullanamazsınız `Function` veya `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="9638b-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="9638b-105">**Hata Kimliği:** BC30043</span><span class="sxs-lookup"><span data-stu-id="9638b-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9638b-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9638b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="9638b-107">Anahtar sözcüğü yordamdan kaldırın veya kaldırın `Shared` yordamı bildirimi anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="9638b-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9638b-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9638b-108">See Also</span></span>  
 [<span data-ttu-id="9638b-109">Nesne değişkeni ataması</span><span class="sxs-lookup"><span data-stu-id="9638b-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="9638b-110">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="9638b-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="9638b-111">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="9638b-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
