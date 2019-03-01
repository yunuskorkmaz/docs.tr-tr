---
title: Alias Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 3b1a66ecfd3c023a12ac62191ca3671a195b45a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978234"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="2de83-102">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2de83-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="2de83-103">Bir dış yordam kendi DLL'i içinde başka bir ad olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2de83-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2de83-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2de83-104">Remarks</span></span>  
 <span data-ttu-id="2de83-105">`Alias` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2de83-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="2de83-106">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="2de83-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="2de83-107">Aşağıdaki örnekte, `Alias` advapi32.dll, işlevin adını belirtmek için kullanılan anahtar sözcüğü `GetUserNameA`, o `getUserName` yerine bu örnekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2de83-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="2de83-108">İşlev `getUserName` alt adlandırılır `getUser`, geçerli kullanıcı adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2de83-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="2de83-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2de83-109">See also</span></span>
- [<span data-ttu-id="2de83-110">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2de83-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
