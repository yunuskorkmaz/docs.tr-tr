---
title: GoTo ekstresi (Visual Basic)
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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912458"
---
# <a name="goto-statement"></a><span data-ttu-id="4f00f-102">GoTo Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-102">GoTo Statement</span></span>
<span data-ttu-id="4f00f-103">Bir yordamda belirtilen satıra koşulsuz olarak dallandırır.</span><span class="sxs-lookup"><span data-stu-id="4f00f-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f00f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="4f00f-105">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="4f00f-105">Part</span></span>  
 `line`  
 <span data-ttu-id="4f00f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4f00f-106">Required.</span></span> <span data-ttu-id="4f00f-107">Herhangi bir satır etiketi.</span><span class="sxs-lookup"><span data-stu-id="4f00f-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f00f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f00f-108">Remarks</span></span>  
 <span data-ttu-id="4f00f-109">`GoTo` İfadesi yalnızca, göründüğü yordamdaki satırlara dallandırır.</span><span class="sxs-lookup"><span data-stu-id="4f00f-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="4f00f-110">Çizginin, `GoTo` başvurabilen bir çizgi etiketi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f00f-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="4f00f-111">Daha fazla bilgi için [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="4f00f-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f00f-112">`GoTo`deyimler kodun okunmasını ve bakımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="4f00f-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="4f00f-113">Mümkün olduğunda, bunun yerine bir denetim yapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f00f-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="4f00f-114">Daha fazla bilgi için bkz. [Denetim akışı](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f00f-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="4f00f-115">`For`... Dışında `GoTo` dallandırmak için bir ifade kullanamazsınız `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya`Using`... `End Using` içindeki bir etikete oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4f00f-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="4f00f-116">Dallandırma ve TRY kurulumlarını</span><span class="sxs-lookup"><span data-stu-id="4f00f-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="4f00f-117">Bir `Try`... içinde `Catch`... oluşturma, aşağıdaki kurallar `GoTo` ifadesiyle dallandırma için geçerlidir. `Finally`</span><span class="sxs-lookup"><span data-stu-id="4f00f-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="4f00f-118">Blok veya bölge</span><span class="sxs-lookup"><span data-stu-id="4f00f-118">Block or region</span></span>|<span data-ttu-id="4f00f-119">Dışarıdan içinde dallanma</span><span class="sxs-lookup"><span data-stu-id="4f00f-119">Branching in from outside</span></span>|<span data-ttu-id="4f00f-120">İçinden dallanma</span><span class="sxs-lookup"><span data-stu-id="4f00f-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="4f00f-121">`Try`engelleyin</span><span class="sxs-lookup"><span data-stu-id="4f00f-121">`Try` block</span></span>|<span data-ttu-id="4f00f-122">Yalnızca aynı yapım <sup>1 bloğundan</sup> `Catch`</span><span class="sxs-lookup"><span data-stu-id="4f00f-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="4f00f-123">Yalnızca tüm oluşturma dışında</span><span class="sxs-lookup"><span data-stu-id="4f00f-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="4f00f-124">`Catch`engelleyin</span><span class="sxs-lookup"><span data-stu-id="4f00f-124">`Catch` block</span></span>|<span data-ttu-id="4f00f-125">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="4f00f-125">Never allowed</span></span>|<span data-ttu-id="4f00f-126">Yalnızca tüm oluşturma veya `Try` aynı yapı <sup>1</sup> bloğunun dışında</span><span class="sxs-lookup"><span data-stu-id="4f00f-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="4f00f-127">`Finally`engelleyin</span><span class="sxs-lookup"><span data-stu-id="4f00f-127">`Finally` block</span></span>|<span data-ttu-id="4f00f-128">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="4f00f-128">Never allowed</span></span>|<span data-ttu-id="4f00f-129">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="4f00f-129">Never allowed</span></span>|  
  
 <span data-ttu-id="4f00f-130"><sup>1</sup> varsa `Try`... `Catch`... oluşturma diğeri içinde iç içe yerleştirilmiş bir `Catch` `Try` blok, bloğa kendi iç içe geçme düzeyinde dallandırır, ancak başka `Try` bir blok içinde yer alamaz. `Finally`</span><span class="sxs-lookup"><span data-stu-id="4f00f-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="4f00f-131">İç içe `Try`geçmiş... `Catch`... oluşturma, içinde iç içe olan bir `Try` veya `Catch` bir blok içinde tamamen bulunmalıdır. `Finally`</span><span class="sxs-lookup"><span data-stu-id="4f00f-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="4f00f-132">Aşağıdaki çizimde, bir `Try` oluşturma diğeri içinde iç içe gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f00f-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="4f00f-133">İki kurulumlarını blokları arasındaki çeşitli dallar geçerli veya geçersiz olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4f00f-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![TRY kurulumlarını içinde dallanma grafik Diyagramı](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="4f00f-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f00f-135">Example</span></span>  
 <span data-ttu-id="4f00f-136">Aşağıdaki örnek, bir yordamdaki `GoTo` çizgi etiketlerine dallandırmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f00f-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="4f00f-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f00f-137">See also</span></span>

- [<span data-ttu-id="4f00f-138">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="4f00f-139">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="4f00f-140">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="4f00f-141">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="4f00f-142">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="4f00f-143">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="4f00f-144">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="4f00f-145">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f00f-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
