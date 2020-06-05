---
title: Continue Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382100"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="d432a-102">Continue Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d432a-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="d432a-103">Denetimi bir döngünün sonraki yinelemesine hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="d432a-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d432a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d432a-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="d432a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d432a-105">Remarks</span></span>  
 <span data-ttu-id="d432a-106">Bir `Do` , `For` veya `While` döngüsünün içinden bu döngünün bir sonraki yinelemesine aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d432a-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="d432a-107">Denetim, or ifadesine ya da `For` `While` `Do` `Loop` `Until` OR yan tümcesini içeren or ifadesine `While` ya da içine aktarılmaya denk olan döngü koşulu testine doğrudan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d432a-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="d432a-108">`Continue`Döngüde, aktarımlara izin veren herhangi bir konumda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d432a-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="d432a-109">Denetimin aktarılmasına izin veren kurallar [goto ifadesiyle](goto-statement.md)aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d432a-109">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="d432a-110">Örneğin, bir döngü bir `Try` blok, blok veya blok içinde tamamen içerilmediği takdirde `Catch` `Finally` `Continue` döngüyü dışarı aktarmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d432a-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="d432a-111">Diğer taraftan, `Try` ... `End Try` yapısı döngü içinde yer alıyorsa, `Continue` denetimi bloğunun dışına aktarmak için kullanamazsınız `Finally` ve `Try` `Catch` yalnızca... yapısından tamamen dışarı aktarırsanız bir veya bloğunun dışına aktarmak için kullanabilirsiniz `Try` `End Try` .</span><span class="sxs-lookup"><span data-stu-id="d432a-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="d432a-112">Aynı türde iç içe geçmiş döngülerine sahipseniz (örneğin, başka bir `Do` döngü içindeki bir döngü) `Do` , bir `Continue Do` ifade kendisini içeren en içteki döngünün bir sonraki yinelemesine atlar `Do` .</span><span class="sxs-lookup"><span data-stu-id="d432a-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="d432a-113">`Continue`Aynı türdeki bir kapsayan döngünün sonraki yinelemesine atlamak için öğesini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d432a-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="d432a-114">Farklı türlerde iç içe geçmiş döngülerine sahipseniz (örneğin, `Do` döngü içindeki bir döngü), ya da `For` kullanarak iki döngünün bir sonraki yinelemesine atlayabilirsiniz `Continue Do` `Continue For` .</span><span class="sxs-lookup"><span data-stu-id="d432a-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d432a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d432a-115">Example</span></span>  
 <span data-ttu-id="d432a-116">Aşağıdaki kod örneği, `Continue While` bir bölen sıfırsa bir dizinin sonraki sütununa atlamak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d432a-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="d432a-117">`Continue While`Bir `For` döngü içinde.</span><span class="sxs-lookup"><span data-stu-id="d432a-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="d432a-118">Bu, `While col < lastcol` döngüsünü içeren en içteki döngünün bir sonraki yinelemesi olan ifadesine aktarır `While` `For` .</span><span class="sxs-lookup"><span data-stu-id="d432a-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="d432a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d432a-119">See also</span></span>

- [<span data-ttu-id="d432a-120">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="d432a-120">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="d432a-121">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="d432a-121">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="d432a-122">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="d432a-122">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="d432a-123">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="d432a-123">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
