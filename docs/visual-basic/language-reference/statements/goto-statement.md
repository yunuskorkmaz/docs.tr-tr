---
title: GoTo deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 9d2cec7f9cd2cc9d8985c9add103748583c25dc9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968939"
---
# <a name="goto-statement"></a><span data-ttu-id="9639e-102">GoTo Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-102">GoTo Statement</span></span>
<span data-ttu-id="9639e-103">Bir yordam içinde belirtilen bir satıra koşulsuz dallara.</span><span class="sxs-lookup"><span data-stu-id="9639e-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9639e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9639e-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="9639e-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="9639e-105">Part</span></span>  
 `line`  
 <span data-ttu-id="9639e-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9639e-106">Required.</span></span> <span data-ttu-id="9639e-107">Herhangi bir satır etiketi.</span><span class="sxs-lookup"><span data-stu-id="9639e-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9639e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9639e-108">Remarks</span></span>  
 <span data-ttu-id="9639e-109">`GoTo` Deyimi göründüğü yordamdaki satırlar için dal.</span><span class="sxs-lookup"><span data-stu-id="9639e-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="9639e-110">Satır etiketi bir satırı olmalıdır `GoTo` başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="9639e-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="9639e-111">Daha fazla bilgi için [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="9639e-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9639e-112">`GoTo` deyimleri kod okunması ve düzenlenmesi zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="9639e-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="9639e-113">Mümkün olduğunda, bir denetim yapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9639e-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="9639e-114">Daha fazla bilgi için [akış denetimi](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="9639e-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="9639e-115">Kullanamazsınız bir `GoTo` daldan dışında deyimi bir `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya `Using`... `End Using` içinde bir etikete oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9639e-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="9639e-116">Dallandırma ve yapılarını deneyin</span><span class="sxs-lookup"><span data-stu-id="9639e-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="9639e-117">İçinde bir `Try`... `Catch`... `Finally` oluşturma, aşağıdaki kurallar geçerli ile dallandırma `GoTo` deyimi.</span><span class="sxs-lookup"><span data-stu-id="9639e-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="9639e-118">Blok veya bölge</span><span class="sxs-lookup"><span data-stu-id="9639e-118">Block or region</span></span>|<span data-ttu-id="9639e-119">Dallanma, gelen dışında</span><span class="sxs-lookup"><span data-stu-id="9639e-119">Branching in from outside</span></span>|<span data-ttu-id="9639e-120">Dallanma çıkış alanından içinde</span><span class="sxs-lookup"><span data-stu-id="9639e-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="9639e-121">`Try` Blok</span><span class="sxs-lookup"><span data-stu-id="9639e-121">`Try` block</span></span>|<span data-ttu-id="9639e-122">Yalnızca bir `Catch` aynı yapı bloğunu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9639e-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="9639e-123">Yalnızca tüm yapı dışında</span><span class="sxs-lookup"><span data-stu-id="9639e-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="9639e-124">`Catch` Blok</span><span class="sxs-lookup"><span data-stu-id="9639e-124">`Catch` block</span></span>|<span data-ttu-id="9639e-125">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="9639e-125">Never allowed</span></span>|<span data-ttu-id="9639e-126">Yalnızca tüm yapı dışında veya çok `Try` aynı yapı bloğunu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9639e-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="9639e-127">`Finally` Blok</span><span class="sxs-lookup"><span data-stu-id="9639e-127">`Finally` block</span></span>|<span data-ttu-id="9639e-128">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="9639e-128">Never allowed</span></span>|<span data-ttu-id="9639e-129">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="9639e-129">Never allowed</span></span>|  
  
 <span data-ttu-id="9639e-130"><sup>1</sup> varsa `Try`... `Catch`... `Finally` yapımı iç içe başka içinde bir `Catch` blok dal içine `Try` blok kendi iç içe geçme düzeyindeki, ancak diğer `Try` blok.</span><span class="sxs-lookup"><span data-stu-id="9639e-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="9639e-131">İç içe bir `Try`... `Catch`... `Finally` yapım tamamen içinde içerilmeli bir `Try` veya `Catch` içinde bunu iç içe Yapı bloğu.</span><span class="sxs-lookup"><span data-stu-id="9639e-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="9639e-132">Aşağıdaki çizim bir gösterir `Try` yapı içinde başka bir iç içe.</span><span class="sxs-lookup"><span data-stu-id="9639e-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="9639e-133">Çeşitli dallar arasında iki yapılarını bloklarını, geçerli ya da geçersiz olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9639e-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="9639e-134">![Deneme yapılarındaki dallanmanın grafik diyagramı](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="9639e-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="9639e-135">Try yapılarını geçerli ve geçersiz dalları</span><span class="sxs-lookup"><span data-stu-id="9639e-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="9639e-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="9639e-136">Example</span></span>  
 <span data-ttu-id="9639e-137">Aşağıdaki örnekte `GoTo` satır etiketleri bir yordamda dala deyimi.</span><span class="sxs-lookup"><span data-stu-id="9639e-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="9639e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9639e-138">See also</span></span>
- [<span data-ttu-id="9639e-139">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="9639e-140">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="9639e-141">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="9639e-142">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="9639e-143">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="9639e-144">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="9639e-145">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="9639e-146">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="9639e-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
