---
title: Alias Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 9cf97402d0b0a6cd16dd75a970c1d29a2fcc30a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498576"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="8cf9d-102">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cf9d-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="8cf9d-103">Bir dış yordam kendi DLL'i içinde başka bir ad olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8cf9d-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cf9d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cf9d-104">Remarks</span></span>  
 <span data-ttu-id="8cf9d-105">`Alias` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8cf9d-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="8cf9d-106">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="8cf9d-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="8cf9d-107">Aşağıdaki örnekte, `Alias` advapi32.dll, işlevin adını belirtmek için kullanılan anahtar sözcüğü `GetUserNameA`, o `getUserName` yerine bu örnekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8cf9d-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="8cf9d-108">İşlev `getUserName` alt adlandırılır `getUser`, geçerli kullanıcı adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8cf9d-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8cf9d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cf9d-109">See also</span></span>
- [<span data-ttu-id="8cf9d-110">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="8cf9d-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
