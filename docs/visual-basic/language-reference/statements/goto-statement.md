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
ms.openlocfilehash: c4dd249620ba1bf445642ce4600498f6beb30461
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61637976"
---
# <a name="goto-statement"></a><span data-ttu-id="beb25-102">GoTo Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-102">GoTo Statement</span></span>
<span data-ttu-id="beb25-103">Bir yordam içinde belirtilen bir satıra koşulsuz dallara.</span><span class="sxs-lookup"><span data-stu-id="beb25-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="beb25-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="beb25-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="beb25-105">Part</span></span>  
 `line`  
 <span data-ttu-id="beb25-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="beb25-106">Required.</span></span> <span data-ttu-id="beb25-107">Herhangi bir satır etiketi.</span><span class="sxs-lookup"><span data-stu-id="beb25-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beb25-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="beb25-108">Remarks</span></span>  
 <span data-ttu-id="beb25-109">`GoTo` Deyimi göründüğü yordamdaki satırlar için dal.</span><span class="sxs-lookup"><span data-stu-id="beb25-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="beb25-110">Satır etiketi bir satırı olmalıdır `GoTo` başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="beb25-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="beb25-111">Daha fazla bilgi için [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="beb25-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="beb25-112">`GoTo` deyimleri kod okunması ve düzenlenmesi zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="beb25-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="beb25-113">Mümkün olduğunda, bir denetim yapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="beb25-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="beb25-114">Daha fazla bilgi için [akış denetimi](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="beb25-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="beb25-115">Kullanamazsınız bir `GoTo` daldan dışında deyimi bir `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya `Using`... `End Using` içinde bir etikete oluşturma.</span><span class="sxs-lookup"><span data-stu-id="beb25-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="beb25-116">Dallandırma ve yapılarını deneyin</span><span class="sxs-lookup"><span data-stu-id="beb25-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="beb25-117">İçinde bir `Try`... `Catch`... `Finally` oluşturma, aşağıdaki kurallar geçerli ile dallandırma `GoTo` deyimi.</span><span class="sxs-lookup"><span data-stu-id="beb25-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="beb25-118">Blok veya bölge</span><span class="sxs-lookup"><span data-stu-id="beb25-118">Block or region</span></span>|<span data-ttu-id="beb25-119">Dallanma, gelen dışında</span><span class="sxs-lookup"><span data-stu-id="beb25-119">Branching in from outside</span></span>|<span data-ttu-id="beb25-120">Dallanma çıkış alanından içinde</span><span class="sxs-lookup"><span data-stu-id="beb25-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="beb25-121">`Try` Blok</span><span class="sxs-lookup"><span data-stu-id="beb25-121">`Try` block</span></span>|<span data-ttu-id="beb25-122">Yalnızca bir `Catch` aynı yapı bloğunu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="beb25-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="beb25-123">Yalnızca tüm yapı dışında</span><span class="sxs-lookup"><span data-stu-id="beb25-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="beb25-124">`Catch` Blok</span><span class="sxs-lookup"><span data-stu-id="beb25-124">`Catch` block</span></span>|<span data-ttu-id="beb25-125">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="beb25-125">Never allowed</span></span>|<span data-ttu-id="beb25-126">Yalnızca tüm yapı dışında veya çok `Try` aynı yapı bloğunu <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="beb25-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="beb25-127">`Finally` Blok</span><span class="sxs-lookup"><span data-stu-id="beb25-127">`Finally` block</span></span>|<span data-ttu-id="beb25-128">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="beb25-128">Never allowed</span></span>|<span data-ttu-id="beb25-129">Hiçbir zaman izin verilir</span><span class="sxs-lookup"><span data-stu-id="beb25-129">Never allowed</span></span>|  
  
 <span data-ttu-id="beb25-130"><sup>1</sup> varsa `Try`... `Catch`... `Finally` yapımı iç içe başka içinde bir `Catch` blok dal içine `Try` blok kendi iç içe geçme düzeyindeki, ancak diğer `Try` blok.</span><span class="sxs-lookup"><span data-stu-id="beb25-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="beb25-131">İç içe bir `Try`... `Catch`... `Finally` yapım tamamen içinde içerilmeli bir `Try` veya `Catch` içinde bunu iç içe Yapı bloğu.</span><span class="sxs-lookup"><span data-stu-id="beb25-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="beb25-132">Aşağıdaki çizim bir gösterir `Try` yapı içinde başka bir iç içe.</span><span class="sxs-lookup"><span data-stu-id="beb25-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="beb25-133">Çeşitli dallar arasında iki yapılarını bloklarını, geçerli ya da geçersiz olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="beb25-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Deneme yapılarındaki dallanmanın grafik diyagramı](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="beb25-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="beb25-135">Example</span></span>  
 <span data-ttu-id="beb25-136">Aşağıdaki örnekte `GoTo` satır etiketleri bir yordamda dala deyimi.</span><span class="sxs-lookup"><span data-stu-id="beb25-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="beb25-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beb25-137">See also</span></span>

- [<span data-ttu-id="beb25-138">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="beb25-139">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="beb25-140">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="beb25-141">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="beb25-142">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="beb25-143">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="beb25-144">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="beb25-145">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="beb25-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
