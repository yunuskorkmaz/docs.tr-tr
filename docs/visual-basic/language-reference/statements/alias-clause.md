---
title: Alias Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: a7f67224c5d26816bdc1974dc4aa82d796c41284
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349143"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="4a94c-102">Alias Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a94c-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="4a94c-103">Bir dış yordamın DLL 'sinde başka bir ada sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a94c-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a94c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a94c-104">Remarks</span></span>  
 <span data-ttu-id="4a94c-105">`Alias` anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4a94c-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="4a94c-106">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="4a94c-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="4a94c-107">Aşağıdaki örnekte, `Alias` anahtar sözcüğü, bu örnekte `getUserName` kullanılan Advapi32. dll ' deki işlevin adını sağlamak için kullanılır `GetUserNameA`.</span><span class="sxs-lookup"><span data-stu-id="4a94c-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="4a94c-108">`getUserName` işlevi, geçerli kullanıcının adını görüntüleyen Sub `getUser`içinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4a94c-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4a94c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a94c-109">See also</span></span>

- [<span data-ttu-id="4a94c-110">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4a94c-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
