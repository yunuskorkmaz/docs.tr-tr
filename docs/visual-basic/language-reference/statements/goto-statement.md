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
ms.openlocfilehash: 4b7a5cce56dfdd2bdc7e068aadbc18b92bba269d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581813"
---
# <a name="goto-statement"></a><span data-ttu-id="82d59-102">GoTo Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-102">GoTo Statement</span></span>
<span data-ttu-id="82d59-103">Bir yordamda belirtilen satıra koşulsuz olarak dallandırır.</span><span class="sxs-lookup"><span data-stu-id="82d59-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82d59-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="82d59-105">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="82d59-105">Part</span></span>  
 `line`  
 <span data-ttu-id="82d59-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="82d59-106">Required.</span></span> <span data-ttu-id="82d59-107">Herhangi bir satır etiketi.</span><span class="sxs-lookup"><span data-stu-id="82d59-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82d59-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82d59-108">Remarks</span></span>  
 <span data-ttu-id="82d59-109">@No__t_0 ifadesi yalnızca göründüğü yordamdaki satırlara dallandırır.</span><span class="sxs-lookup"><span data-stu-id="82d59-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="82d59-110">Çizgi, `GoTo` başvurabileceği bir çizgi etiketine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82d59-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="82d59-111">Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="82d59-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82d59-112">`GoTo` deyimleri kodun okunmasını ve bakımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="82d59-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="82d59-113">Mümkün olduğunda, bunun yerine bir denetim yapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="82d59-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="82d59-114">Daha fazla bilgi için bkz. [Denetim akışı](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="82d59-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="82d59-115">@No__t_1 dışından dallandırmak için `GoTo` ifadesini kullanamazsınız... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `For`0... 1 veya 2... içindeki bir etikete 3 oluşturma.</span><span class="sxs-lookup"><span data-stu-id="82d59-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="82d59-116">Dallandırma ve TRY kurulumlarını</span><span class="sxs-lookup"><span data-stu-id="82d59-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="82d59-117">@No__t_0 içinde... `Catch`... `Finally` oluşturma, aşağıdaki kurallar `GoTo` ifadesiyle dallandırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="82d59-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="82d59-118">Blok veya bölge</span><span class="sxs-lookup"><span data-stu-id="82d59-118">Block or region</span></span>|<span data-ttu-id="82d59-119">Dışarıdan içinde dallanma</span><span class="sxs-lookup"><span data-stu-id="82d59-119">Branching in from outside</span></span>|<span data-ttu-id="82d59-120">İçinden dallanma</span><span class="sxs-lookup"><span data-stu-id="82d59-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="82d59-121">`Try` bloğu</span><span class="sxs-lookup"><span data-stu-id="82d59-121">`Try` block</span></span>|<span data-ttu-id="82d59-122">Yalnızca aynı yapı <sup>1</sup> ' in `Catch` bloğundan</span><span class="sxs-lookup"><span data-stu-id="82d59-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="82d59-123">Yalnızca tüm oluşturma dışında</span><span class="sxs-lookup"><span data-stu-id="82d59-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="82d59-124">`Catch` bloğu</span><span class="sxs-lookup"><span data-stu-id="82d59-124">`Catch` block</span></span>|<span data-ttu-id="82d59-125">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="82d59-125">Never allowed</span></span>|<span data-ttu-id="82d59-126">Yalnızca tüm oluşturma veya aynı yapı <sup>1</sup> ' in `Try` bloğunun dışında</span><span class="sxs-lookup"><span data-stu-id="82d59-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="82d59-127">`Finally` bloğu</span><span class="sxs-lookup"><span data-stu-id="82d59-127">`Finally` block</span></span>|<span data-ttu-id="82d59-128">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="82d59-128">Never allowed</span></span>|<span data-ttu-id="82d59-129">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="82d59-129">Never allowed</span></span>|  
  
 <span data-ttu-id="82d59-130"><sup>1</sup> `Try`... `Catch`... `Finally` oluşturma diğeri içinde iç içe geçmiş `Catch` bir blok, `Try` bloğunu kendi iç içe düzeyinde (başka bir `Try` bloğunda değil) dallandırır.</span><span class="sxs-lookup"><span data-stu-id="82d59-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="82d59-131">İç içe geçmiş `Try`... `Catch`... `Finally` oluşturma, iç içe geçmiş bir `Try` veya `Catch` bloğunda tamamen bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82d59-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="82d59-132">Aşağıdaki çizimde, başka bir `Try` oluşturma bir diğeri içinde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82d59-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="82d59-133">İki kurulumlarını blokları arasındaki çeşitli dallar geçerli veya geçersiz olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="82d59-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![TRY kurulumlarını içinde dallanma grafik Diyagramı](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="82d59-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="82d59-135">Example</span></span>  
 <span data-ttu-id="82d59-136">Aşağıdaki örnek, bir yordamdaki çizgi etiketlerine dallandırmak için `GoTo` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="82d59-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="82d59-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82d59-137">See also</span></span>

- [<span data-ttu-id="82d59-138">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="82d59-139">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="82d59-140">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="82d59-141">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="82d59-142">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="82d59-143">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="82d59-144">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="82d59-145">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="82d59-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
