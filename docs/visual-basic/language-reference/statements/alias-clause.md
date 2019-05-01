---
title: Alias Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 84c8f39e632eebbe5382492669820910b38bc360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053359"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="bb651-102">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb651-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="bb651-103">Bir dış yordam kendi DLL'i içinde başka bir ad olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb651-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb651-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb651-104">Remarks</span></span>  
 <span data-ttu-id="bb651-105">`Alias` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="bb651-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="bb651-106">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="bb651-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="bb651-107">Aşağıdaki örnekte, `Alias` advapi32.dll, işlevin adını belirtmek için kullanılan anahtar sözcüğü `GetUserNameA`, o `getUserName` yerine bu örnekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb651-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="bb651-108">İşlev `getUserName` alt adlandırılır `getUser`, geçerli kullanıcı adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb651-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="bb651-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb651-109">See also</span></span>

- [<span data-ttu-id="bb651-110">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="bb651-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
