---
description: 'Daha fazla bilgi edinin: GoTo deyimleri'
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
ms.openlocfilehash: 804baec130111562225b09cbdc7b5fb2d73adba5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769058"
---
# <a name="goto-statement"></a><span data-ttu-id="909d8-103">GoTo Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-103">GoTo Statement</span></span>

<span data-ttu-id="909d8-104">Bir yordamda belirtilen satıra koşulsuz olarak dallandırır.</span><span class="sxs-lookup"><span data-stu-id="909d8-104">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="909d8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="909d8-105">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="909d8-106">Bölüm</span><span class="sxs-lookup"><span data-stu-id="909d8-106">Part</span></span>  

 `line`  
 <span data-ttu-id="909d8-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="909d8-107">Required.</span></span> <span data-ttu-id="909d8-108">Herhangi bir satır etiketi.</span><span class="sxs-lookup"><span data-stu-id="909d8-108">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="909d8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="909d8-109">Remarks</span></span>  

 <span data-ttu-id="909d8-110">`GoTo`İfadesi yalnızca, göründüğü yordamdaki satırlara dallandırır.</span><span class="sxs-lookup"><span data-stu-id="909d8-110">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="909d8-111">Çizginin, başvurabilen bir çizgi etiketi olmalıdır `GoTo` .</span><span class="sxs-lookup"><span data-stu-id="909d8-111">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="909d8-112">Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](../../programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="909d8-112">For more information, see [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="909d8-113">`GoTo` deyimler kodun okunmasını ve bakımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="909d8-113">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="909d8-114">Mümkün olduğunda, bunun yerine bir denetim yapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="909d8-114">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="909d8-115">Daha fazla bilgi için bkz. [Denetim akışı](../../programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="909d8-115">For more information, see [Control Flow](../../programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="909d8-116">Bir... `GoTo` `For` `Next` , `For Each` ... `Next` , `SyncLock` ... `End SyncLock` , `Try` .. `Catch` .,... dışında dallandırmak için bir ifade kullanamazsınız ... `Finally` , `With` ... `End With` , veya `Using` ... `End Using` oluşturma içindeki bir etikete.</span><span class="sxs-lookup"><span data-stu-id="909d8-116">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="909d8-117">Dallandırma ve TRY kurulumlarını</span><span class="sxs-lookup"><span data-stu-id="909d8-117">Branching and Try Constructions</span></span>  

 <span data-ttu-id="909d8-118">Bir `Try` . `Catch` .. içinde ...`Finally` oluşturma, aşağıdaki kurallar ifadesiyle dallandırma için geçerlidir `GoTo` .</span><span class="sxs-lookup"><span data-stu-id="909d8-118">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="909d8-119">Blok veya bölge</span><span class="sxs-lookup"><span data-stu-id="909d8-119">Block or region</span></span>|<span data-ttu-id="909d8-120">Dışarıdan içinde dallanma</span><span class="sxs-lookup"><span data-stu-id="909d8-120">Branching in from outside</span></span>|<span data-ttu-id="909d8-121">İçinden dallanma</span><span class="sxs-lookup"><span data-stu-id="909d8-121">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="909d8-122">`Try` engelleyin</span><span class="sxs-lookup"><span data-stu-id="909d8-122">`Try` block</span></span>|<span data-ttu-id="909d8-123">Yalnızca `Catch` aynı yapım <sup>1</sup> bloğundan</span><span class="sxs-lookup"><span data-stu-id="909d8-123">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="909d8-124">Yalnızca tüm oluşturma dışında</span><span class="sxs-lookup"><span data-stu-id="909d8-124">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="909d8-125">`Catch` engelleyin</span><span class="sxs-lookup"><span data-stu-id="909d8-125">`Catch` block</span></span>|<span data-ttu-id="909d8-126">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="909d8-126">Never allowed</span></span>|<span data-ttu-id="909d8-127">Yalnızca tüm oluşturma veya `Try` aynı yapı <sup>1</sup> bloğunun dışında</span><span class="sxs-lookup"><span data-stu-id="909d8-127">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="909d8-128">`Finally` engelleyin</span><span class="sxs-lookup"><span data-stu-id="909d8-128">`Finally` block</span></span>|<span data-ttu-id="909d8-129">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="909d8-129">Never allowed</span></span>|<span data-ttu-id="909d8-130">Hiçbir izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="909d8-130">Never allowed</span></span>|  
  
 <span data-ttu-id="909d8-131"><sup>1</sup> varsa `Try` ... `Catch` ...`Finally` oluşturma diğeri içinde iç içe yerleştirilmiş bir `Catch` blok, `Try` bloğa kendi iç içe geçme düzeyinde dallandırır, ancak başka bir blok içinde yer alamaz `Try` .</span><span class="sxs-lookup"><span data-stu-id="909d8-131"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="909d8-132">İç içe geçmiş `Try` ... `Catch` ...`Finally` oluşturma `Try` `Catch` , içinde iç içe olan bir veya bir blok içinde tamamen bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="909d8-132">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="909d8-133">Aşağıdaki çizimde, `Try` bir oluşturma diğeri içinde iç içe gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="909d8-133">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="909d8-134">İki kurulumlarını blokları arasındaki çeşitli dallar geçerli veya geçersiz olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="909d8-134">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![TRY kurulumlarını içinde dallanma grafik Diyagramı](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="909d8-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="909d8-136">Example</span></span>  

 <span data-ttu-id="909d8-137">Aşağıdaki örnek, `GoTo` bir yordamdaki çizgi etiketlerine dallandırmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="909d8-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="909d8-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="909d8-138">See also</span></span>

- [<span data-ttu-id="909d8-139">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-139">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="909d8-140">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-140">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="909d8-141">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-141">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="909d8-142">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-142">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="909d8-143">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-143">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="909d8-144">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-144">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="909d8-145">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-145">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="909d8-146">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="909d8-146">With...End With Statement</span></span>](with-end-with-statement.md)
