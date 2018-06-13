---
title: GoTo Deyimi
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
ms.openlocfilehash: 27ebc677bab8b7f61a02408fddb30a6ec21c43cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604750"
---
# <a name="goto-statement"></a><span data-ttu-id="6ee4f-102">GoTo Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-102">GoTo Statement</span></span>
<span data-ttu-id="6ee4f-103">Belirtilen satır yordamdaki koşulsuz olarak dallara.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="6ee4f-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="6ee4f-105">Part</span></span>  
 `line`  
 <span data-ttu-id="6ee4f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-106">Required.</span></span> <span data-ttu-id="6ee4f-107">Herhangi bir satır etiketi.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ee4f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ee4f-108">Remarks</span></span>  
 <span data-ttu-id="6ee4f-109">`GoTo` Deyimi göründüğü yordamdaki satırlar için dal.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="6ee4f-110">Satır etiketi bir satırda olmalıdır `GoTo` başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="6ee4f-111">Daha fazla bilgi için bkz: [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="6ee4f-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ee4f-112">`GoTo` deyimleri kodu okuma ve korumak zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="6ee4f-113">Mümkün olduğunda, bir denetim yapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="6ee4f-114">Daha fazla bilgi için bkz: [akış denetimi](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="6ee4f-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="6ee4f-115">Kullanarak bir `GoTo` daldan dışında ifadesine bir `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya `Using`... `End Using` içinde bir etiket oluşturma.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="6ee4f-116">Dal oluşturma ve kurulumlarını deneyin</span><span class="sxs-lookup"><span data-stu-id="6ee4f-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="6ee4f-117">İçinde bir `Try`... `Catch`... `Finally` oluşturma, aşağıdaki kurallar geçerli ile dallanma `GoTo` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="6ee4f-118">Blok veya bölge</span><span class="sxs-lookup"><span data-stu-id="6ee4f-118">Block or region</span></span>|<span data-ttu-id="6ee4f-119">Dallara ayırma, gelen dışında</span><span class="sxs-lookup"><span data-stu-id="6ee4f-119">Branching in from outside</span></span>|<span data-ttu-id="6ee4f-120">Dallara ayırma çıkışı gelen içinde</span><span class="sxs-lookup"><span data-stu-id="6ee4f-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="6ee4f-121">`Try` Engelle</span><span class="sxs-lookup"><span data-stu-id="6ee4f-121">`Try` block</span></span>|<span data-ttu-id="6ee4f-122">Yalnızca bir `Catch` aynı Yapı bloğu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6ee4f-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="6ee4f-123">Yalnızca tüm yapım dışında</span><span class="sxs-lookup"><span data-stu-id="6ee4f-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="6ee4f-124">`Catch` Engelle</span><span class="sxs-lookup"><span data-stu-id="6ee4f-124">`Catch` block</span></span>|<span data-ttu-id="6ee4f-125">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="6ee4f-125">Never allowed</span></span>|<span data-ttu-id="6ee4f-126">Yalnızca tüm yapım dışında veya çok `Try` aynı Yapı bloğu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6ee4f-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="6ee4f-127">`Finally` Engelle</span><span class="sxs-lookup"><span data-stu-id="6ee4f-127">`Finally` block</span></span>|<span data-ttu-id="6ee4f-128">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="6ee4f-128">Never allowed</span></span>|<span data-ttu-id="6ee4f-129">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="6ee4f-129">Never allowed</span></span>|  
  
 <span data-ttu-id="6ee4f-130"><sup>1</sup> varsa `Try`... `Catch`... `Finally` yapım iç içe başka içinde bir `Catch` bloğu dallanma içine `Try` blok kendi iç içe geçmiş düzeyinde, ancak diğer `Try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="6ee4f-131">İç içe bir `Try`... `Catch`... `Finally` yapım tamamen buna içerilmelidir bir `Try` veya `Catch` içinde bu iç içe geçmiş yapım bloğu.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="6ee4f-132">Aşağıdaki çizimde bir gösterir `Try` yapı içinde başka bir iç içe.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="6ee4f-133">İki kurulumlarını bloklarını arasında çeşitli dalları geçerli veya geçersiz olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="6ee4f-134">![Try kurulumlarını dallanma grafik diyagramı](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="6ee4f-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="6ee4f-135">Try kurulumlarını geçersiz ve geçerli dal</span><span class="sxs-lookup"><span data-stu-id="6ee4f-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ee4f-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ee4f-136">Example</span></span>  
 <span data-ttu-id="6ee4f-137">Aşağıdaki örnek kullanır `GoTo` satır etiketleri yordamdaki dala ifadesine.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6ee4f-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ee4f-138">See Also</span></span>  
 [<span data-ttu-id="6ee4f-139">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="6ee4f-140">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="6ee4f-141">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="6ee4f-142">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="6ee4f-143">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="6ee4f-144">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="6ee4f-145">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="6ee4f-146">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ee4f-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
