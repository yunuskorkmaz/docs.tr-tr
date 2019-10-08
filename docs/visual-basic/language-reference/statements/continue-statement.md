---
title: Continue Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005110"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="ef5bf-102">Continue Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef5bf-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="ef5bf-103">Denetimi bir döngünün sonraki yinelemesine hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef5bf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef5bf-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="ef5bf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef5bf-105">Remarks</span></span>  
 <span data-ttu-id="ef5bf-106">@No__t-0, `For` veya `While` döngüsünün içinden bu döngünün bir sonraki yinelemesine aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="ef5bf-107">Denetim, `For` veya `While` ifadesine veya `Until` veya `While` yan tümcesini içeren @no__t 2 veya `Loop` bildirimine aktarılmaya eşdeğer olan döngü koşulu testine anında geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="ef5bf-108">@No__t-0 ' yı döngüdeki aktarımlara izin veren herhangi bir konumda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="ef5bf-109">Denetimin aktarılmasına izin veren kurallar [goto ifadesiyle](../../../visual-basic/language-reference/statements/goto-statement.md)aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="ef5bf-110">Örneğin, bir döngü tamamen bir `Try` bloğu, `Catch` bloğu veya `Finally` bloğu içinde yer alıyorsa, döngünün dışına aktarmak için `Continue` ' ü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="ef5bf-111">Diğer taraftan, `Try`... `End Try` yapısı döngü içinde yer alıyorsa, `Finally` bloğundan denetimi aktarmak için `Continue` ' yi kullanamazsınız ve bunu yalnızca tamamen dışarı aktarırsanız, `Try` veya `Catch` bloğunun dışına aktarmak için kullanabilirsiniz. _T-6... `End Try` yapısı.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="ef5bf-112">Aynı türde iç içe geçmiş döngülerine sahipseniz, örneğin başka bir `Do` döngüsünde `Do` döngüsü varsa, `Continue Do` bir ifade kendisini içeren en içteki `Do` döngüsünün bir sonraki yinelemesine atlar.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="ef5bf-113">Aynı türdeki bir kapsayan döngünün sonraki yinelemesine atlamak için `Continue` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="ef5bf-114">Farklı türlerde iç içe geçmiş döngülerine sahipseniz (örneğin, bir `For` döngüsünde `Do` döngüsü), `Continue Do` veya `Continue For` ' ü kullanarak iki döngünün bir sonraki yinelemesine atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef5bf-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef5bf-115">Example</span></span>  
 <span data-ttu-id="ef5bf-116">Aşağıdaki kod örneği, bir bölen sıfırsa bir dizinin sonraki sütununa atlamak için `Continue While` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="ef5bf-117">@No__t-0 bir `For` döngüsü içinde.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="ef5bf-118">@No__t-2 döngüsünü içeren en içteki `While` döngüsünün bir sonraki yinelemesi olan `While col < lastcol` ifadesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="ef5bf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef5bf-119">See also</span></span>

- [<span data-ttu-id="ef5bf-120">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="ef5bf-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="ef5bf-121">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="ef5bf-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="ef5bf-122">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="ef5bf-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="ef5bf-123">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="ef5bf-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
