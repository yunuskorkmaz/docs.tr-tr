---
title: GoTo Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a><span data-ttu-id="c8849-102">GoTo Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8849-102">GoTo Statement</span></span>
<span data-ttu-id="c8849-103">Belirtilen satır yordamdaki koşulsuz olarak dallara.</span><span class="sxs-lookup"><span data-stu-id="c8849-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8849-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8849-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="c8849-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="c8849-105">Part</span></span>  
 `line`  
 <span data-ttu-id="c8849-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c8849-106">Required.</span></span> <span data-ttu-id="c8849-107">Herhangi bir satır etiketi.</span><span class="sxs-lookup"><span data-stu-id="c8849-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8849-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8849-108">Remarks</span></span>  
 <span data-ttu-id="c8849-109">`GoTo` Deyimi göründüğü yordamdaki satırlar için dal.</span><span class="sxs-lookup"><span data-stu-id="c8849-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="c8849-110">Satır etiketi bir satırda olmalıdır `GoTo` başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8849-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="c8849-111">Daha fazla bilgi için bkz: [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="c8849-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8849-112">`GoTo`deyimleri kodu okuma ve korumak zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="c8849-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="c8849-113">Mümkün olduğunda, bir denetim yapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8849-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="c8849-114">Daha fazla bilgi için bkz: [akış denetimi](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8849-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="c8849-115">Kullanarak bir `GoTo` daldan dışında ifadesine bir `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya `Using`... `End Using` içinde bir etiket oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c8849-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="c8849-116">Dal oluşturma ve kurulumlarını deneyin</span><span class="sxs-lookup"><span data-stu-id="c8849-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="c8849-117">İçinde bir `Try`... `Catch`... `Finally` oluşturma, aşağıdaki kurallar geçerli ile dallanma `GoTo` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c8849-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="c8849-118">Blok veya bölge</span><span class="sxs-lookup"><span data-stu-id="c8849-118">Block or region</span></span>|<span data-ttu-id="c8849-119">Dallara ayırma, gelen dışında</span><span class="sxs-lookup"><span data-stu-id="c8849-119">Branching in from outside</span></span>|<span data-ttu-id="c8849-120">Dallara ayırma çıkışı gelen içinde</span><span class="sxs-lookup"><span data-stu-id="c8849-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="c8849-121">`Try`engelle</span><span class="sxs-lookup"><span data-stu-id="c8849-121">`Try` block</span></span>|<span data-ttu-id="c8849-122">Yalnızca bir `Catch` aynı Yapı bloğu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c8849-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="c8849-123">Yalnızca tüm yapım dışında</span><span class="sxs-lookup"><span data-stu-id="c8849-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="c8849-124">`Catch`engelle</span><span class="sxs-lookup"><span data-stu-id="c8849-124">`Catch` block</span></span>|<span data-ttu-id="c8849-125">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="c8849-125">Never allowed</span></span>|<span data-ttu-id="c8849-126">Yalnızca tüm yapım dışında veya çok `Try` aynı Yapı bloğu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c8849-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="c8849-127">`Finally`engelle</span><span class="sxs-lookup"><span data-stu-id="c8849-127">`Finally` block</span></span>|<span data-ttu-id="c8849-128">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="c8849-128">Never allowed</span></span>|<span data-ttu-id="c8849-129">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="c8849-129">Never allowed</span></span>|  
  
 <span data-ttu-id="c8849-130"><sup>1</sup> varsa `Try`... `Catch`... `Finally` yapım iç içe başka içinde bir `Catch` bloğu dallanma içine `Try` blok kendi iç içe geçmiş düzeyinde, ancak diğer `Try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="c8849-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="c8849-131">İç içe bir `Try`... `Catch`... `Finally` yapım tamamen buna içerilmelidir bir `Try` veya `Catch` içinde bu iç içe geçmiş yapım bloğu.</span><span class="sxs-lookup"><span data-stu-id="c8849-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="c8849-132">Aşağıdaki çizimde bir gösterir `Try` yapı içinde başka bir iç içe.</span><span class="sxs-lookup"><span data-stu-id="c8849-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="c8849-133">İki kurulumlarını bloklarını arasında çeşitli dalları geçerli veya geçersiz olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c8849-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="c8849-134">![Try kurulumlarını dallanma grafik diyagramı](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="c8849-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="c8849-135">Try kurulumlarını geçersiz ve geçerli dal</span><span class="sxs-lookup"><span data-stu-id="c8849-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8849-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8849-136">Example</span></span>  
 <span data-ttu-id="c8849-137">Aşağıdaki örnek kullanır `GoTo` satır etiketleri yordamdaki dala ifadesine.</span><span class="sxs-lookup"><span data-stu-id="c8849-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c8849-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8849-138">See Also</span></span>  
 [<span data-ttu-id="c8849-139">Yapın... Loop deyimi</span><span class="sxs-lookup"><span data-stu-id="c8849-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="c8849-140">İçin... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="c8849-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="c8849-141">For Each... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="c8849-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="c8849-142">If... Then... Else deyimi</span><span class="sxs-lookup"><span data-stu-id="c8849-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="c8849-143">Seçin... Case deyimi</span><span class="sxs-lookup"><span data-stu-id="c8849-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="c8849-144">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="c8849-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="c8849-145">While... End While deyimi</span><span class="sxs-lookup"><span data-stu-id="c8849-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="c8849-146">İle... End With deyimi</span><span class="sxs-lookup"><span data-stu-id="c8849-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
