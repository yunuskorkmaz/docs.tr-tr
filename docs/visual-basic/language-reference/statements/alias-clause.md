---
title: Alias Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 77d4685f242864842e5a84b3a3de3ba1793e9aa4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866690"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="7022d-102">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7022d-102">Alias Clause (Visual Basic)</span></span>

<span data-ttu-id="7022d-103">Bir dış yordamın DLL 'sinde başka bir ada sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7022d-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7022d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7022d-104">Remarks</span></span>  

 <span data-ttu-id="7022d-105">`Alias`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7022d-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="7022d-106">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="7022d-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="7022d-107">Aşağıdaki örnekte `Alias` anahtar sözcüğü, `GetUserNameA` `getUserName` Bu örnekte yerine kullanılan advapi32.dll, işlevin adını sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7022d-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="7022d-108">İşlevi `getUserName` `getUser` , geçerli kullanıcının adını görüntüleyen Sub içinde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="7022d-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="7022d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7022d-109">See also</span></span>

- [<span data-ttu-id="7022d-110">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="7022d-110">Keywords</span></span>](../keywords/index.md)
