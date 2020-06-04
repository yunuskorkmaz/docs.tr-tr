---
title: Alias Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408477"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="c2354-102">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2354-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="c2354-103">Bir dış yordamın DLL 'sinde başka bir ada sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2354-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2354-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2354-104">Remarks</span></span>  
 <span data-ttu-id="c2354-105">`Alias`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c2354-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="c2354-106">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c2354-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="c2354-107">Aşağıdaki örnekte `Alias` anahtar sözcüğü, `GetUserNameA` `getUserName` Bu örnekte yerine kullanılan Advapi32. dll içinde işlevin adını sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2354-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="c2354-108">İşlevi `getUserName` `getUser` , geçerli kullanıcının adını görüntüleyen Sub içinde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c2354-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="c2354-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2354-109">See also</span></span>

- [<span data-ttu-id="c2354-110">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c2354-110">Keywords</span></span>](../keywords/index.md)
