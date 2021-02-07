---
description: 'Daha fazla bilgi edinin: alias tümcesi (Visual Basic)'
title: Alias Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: bf0ee1c22105b29aedb99ce45a99ba866f4b93c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674083"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="382ba-103">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="382ba-103">Alias Clause (Visual Basic)</span></span>

<span data-ttu-id="382ba-104">Bir dış yordamın DLL 'sinde başka bir ada sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="382ba-104">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="382ba-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="382ba-105">Remarks</span></span>  

 <span data-ttu-id="382ba-106">`Alias`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="382ba-106">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="382ba-107">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="382ba-107">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="382ba-108">Aşağıdaki örnekte `Alias` anahtar sözcüğü, `GetUserNameA` `getUserName` Bu örnekte yerine kullanılan advapi32.dll, işlevin adını sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="382ba-108">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="382ba-109">İşlevi `getUserName` `getUser` , geçerli kullanıcının adını görüntüleyen Sub içinde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="382ba-109">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="382ba-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="382ba-110">See also</span></span>

- [<span data-ttu-id="382ba-111">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="382ba-111">Keywords</span></span>](../keywords/index.md)
