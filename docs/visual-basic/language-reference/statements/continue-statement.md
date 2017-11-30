---
title: Continue Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="ae9db-102">Continue Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae9db-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="ae9db-103">Aktarımları denetimi hemen sonraki yineleme döngüsü.</span><span class="sxs-lookup"><span data-stu-id="ae9db-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae9db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae9db-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae9db-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae9db-105">Remarks</span></span>  
 <span data-ttu-id="ae9db-106">Alan aktarabilirsiniz içinde bir `Do`, `For`, veya `While` Bu döngü sonraki yinelemeye döngü.</span><span class="sxs-lookup"><span data-stu-id="ae9db-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="ae9db-107">Denetim aktarma için eşdeğer olan hemen döngü koşulunu test, geçişleri `For` veya `While` deyimi veya `Do` veya `Loop` içeren ifade `Until` veya `While` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ae9db-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="ae9db-108">Kullanabileceğiniz `Continue` aktarımları sağlar döngüsünde herhangi bir konumdaki.</span><span class="sxs-lookup"><span data-stu-id="ae9db-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="ae9db-109">Denetim aktarımını izin verme kuralları ile aynıdır [GoTo deyimi](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ae9db-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="ae9db-110">Örneğin, bir döngü içinde tamamen kapsanan ise bir `Try` blok, bir `Catch` bloğu veya bir `Finally` bloğu kullanabilirsiniz `Continue` döngü dışına aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="ae9db-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="ae9db-111">Eğer, diğer yandan `Try`... `End Try` yapısı döngü içinde bulunan, kullanamazsınız `Continue` kontrolünü dışarı aktarmak için `Finally` bloğu ve kullanabilirsiniz, dışarı aktarmak için bir `Try` veya `Catch` yalnızca, tamamen dışında aktarırsanız engelle `Try`... `End Try` yapısı.</span><span class="sxs-lookup"><span data-stu-id="ae9db-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="ae9db-112">Aynı türde iç içe geçmiş döngüler örneğin varsa bir `Do` döngü başka içinde `Do` döngü, bir `Continue Do` deyimi atlar ise en içteki sonraki yinelemeye `Do` içerdiği döngü.</span><span class="sxs-lookup"><span data-stu-id="ae9db-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="ae9db-113">Kullanamazsınız `Continue` aynı türde içeren bir döngü sonraki yinelemeye atlanacak.</span><span class="sxs-lookup"><span data-stu-id="ae9db-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="ae9db-114">Farklı türlerdeki iç içe geçmiş döngüler örneğin varsa bir `Do` içinde döngü bir `For` döngüsü kullanarak ya da döngü sonraki yinelemeye atlayabilirsiniz `Continue Do` veya `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="ae9db-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae9db-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae9db-115">Example</span></span>  
 <span data-ttu-id="ae9db-116">Aşağıdaki kod örneğinde `Continue While` bölen sıfır ise, bir dizi sonraki sütuna atlamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="ae9db-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="ae9db-117">`Continue While` İçinde bir `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="ae9db-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="ae9db-118">İçin aktarır `While col < lastcol` ise en içteki sonraki yinelemesi olduğunu deyimi `While` içeren döngü `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="ae9db-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ae9db-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae9db-119">See Also</span></span>  
 [<span data-ttu-id="ae9db-120">Yapın... Loop deyimi</span><span class="sxs-lookup"><span data-stu-id="ae9db-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="ae9db-121">İçin... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="ae9db-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="ae9db-122">While... End While deyimi</span><span class="sxs-lookup"><span data-stu-id="ae9db-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="ae9db-123">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="ae9db-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
