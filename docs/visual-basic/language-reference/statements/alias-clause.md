---
title: Alias Tümcesi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f61e738434ea616d751576ef21669545afc41397
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="5c7d4-102">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c7d4-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="5c7d4-103">Dış bir yordam, DLL başka bir ad sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c7d4-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c7d4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c7d4-104">Remarks</span></span>  
 <span data-ttu-id="5c7d4-105">`Alias` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5c7d4-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="5c7d4-106">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="5c7d4-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="5c7d4-107">Aşağıdaki örnekte, `Alias` advapi32.dll, işlevinde adını sağlamak için kullanılan anahtar sözcüğü `GetUserNameA`, o `getUserName` yerine bu örnekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c7d4-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="5c7d4-108">İşlev `getUserName` içinde alt adlı `getUser`, geçerli kullanıcı adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5c7d4-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5c7d4-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c7d4-109">See Also</span></span>  
 [<span data-ttu-id="5c7d4-110">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5c7d4-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
