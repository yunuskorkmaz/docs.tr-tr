---
title: Continue Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 7aa0bda9c87553a5c9dae38517b5d546f782bed0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974087"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="d65f6-102">Continue Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d65f6-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="d65f6-103">Hemen bir döngünün sonraki yinelemesine için aktarımları denetimi.</span><span class="sxs-lookup"><span data-stu-id="d65f6-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d65f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d65f6-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="d65f6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d65f6-105">Remarks</span></span>  
 <span data-ttu-id="d65f6-106">Aktarabilir miyim içinde bir `Do`, `For`, veya `While` Bu döngünün sonraki yinelemesine döngü.</span><span class="sxs-lookup"><span data-stu-id="d65f6-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="d65f6-107">Denetim aktarma için eşdeğer olan hemen döngü koşul testi geçer `For` veya `While` deyimi veya `Do` veya `Loop` içeren ifade `Until` veya `While` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d65f6-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="d65f6-108">Kullanabileceğiniz `Continue` aktarımlarına izin veren döngü herhangi bir konumda.</span><span class="sxs-lookup"><span data-stu-id="d65f6-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="d65f6-109">Aktarım Denetimi verme kuralları ile aynıdır [GoTo deyimi](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d65f6-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="d65f6-110">Örneğin, bir döngü içinde tamamen bağımsız bir `Try` bloğu bir `Catch` bloğu veya `Finally` bloğu kullanabilirsiniz `Continue` döngü dışına aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="d65f6-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="d65f6-111">Diğer yandan Eğer `Try`... `End Try` yapısı döngü içinde bulunan, kullanamazsınız `Continue` kontrolünü dışarı aktarmak için `Finally` bloğunda kullanabilirsiniz, dışarı aktarmak için bir `Try` veya `Catch` yalnızca tamamen tanesi aktarırsanız engelle `Try`... `End Try` yapısı.</span><span class="sxs-lookup"><span data-stu-id="d65f6-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="d65f6-112">İç içe döngüleri aynı tür, örneğin varsa bir `Do` döngü içindeki başka `Do` döngüsü, bir `Continue Do` ifade en içteki bir sonraki yinelemesine atlar `Do` içerdiği döngü.</span><span class="sxs-lookup"><span data-stu-id="d65f6-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="d65f6-113">Kullanamazsınız `Continue` aynı tür içeren bir döngünün sonraki yinelemesine atlanacak.</span><span class="sxs-lookup"><span data-stu-id="d65f6-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="d65f6-114">Farklı türlerde iç içe döngüleri örnek varsa bir `Do` döngü içinde bir `For` döngüsü kullanarak ya da döngünün sonraki yinelemesine atlayabilirsiniz `Continue Do` veya `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="d65f6-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d65f6-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d65f6-115">Example</span></span>  
 <span data-ttu-id="d65f6-116">Aşağıdaki kod örneğinde `Continue While` bölen sıfırsa bir dizi için bir sonraki sütununu atlama deyimi.</span><span class="sxs-lookup"><span data-stu-id="d65f6-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="d65f6-117">`Continue While` İçinde bir `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="d65f6-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="d65f6-118">İçin aktarır `While col < lastcol` en içteki sonraki yinelemesine deyimi `While` içeren döngü `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="d65f6-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="d65f6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d65f6-119">See also</span></span>
- [<span data-ttu-id="d65f6-120">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="d65f6-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="d65f6-121">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="d65f6-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="d65f6-122">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="d65f6-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="d65f6-123">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="d65f6-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
