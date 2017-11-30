---
title: If...Then...Else Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="a25b8-102">If...Then...Else Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a25b8-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="a25b8-103">İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.</span><span class="sxs-lookup"><span data-stu-id="a25b8-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a25b8-104">Syntax</span></span>  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="a25b8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a25b8-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="a25b8-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a25b8-106">Required.</span></span> <span data-ttu-id="a25b8-107">İfade.</span><span class="sxs-lookup"><span data-stu-id="a25b8-107">Expression.</span></span> <span data-ttu-id="a25b8-108">Değerlendirilmelidir `True` veya `False`, ya da örtük olarak parametresinin veri türü için `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-108">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="a25b8-109">İfade ise bir [null atanabilir](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değerlendiren değişkeni [hiçbir şey](../../../visual-basic/language-reference/nothing.md), koşul ifadesi gibi değilse kabul `True`ve `Else` bloğu. yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="a25b8-109">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is not `True`, and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="a25b8-110">Tek satırlı sözdiziminde gerekli; birden çok satırlı sözdiziminde isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a25b8-110">Required in the single-line syntax; optional in the multiple-line syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="a25b8-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a25b8-111">Optional.</span></span> <span data-ttu-id="a25b8-112">Bir veya daha fazla deyimleri aşağıdaki `If`... `Then` varsa yürütülme `condition` değerlendiren `True`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-112">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="a25b8-113">Gerekli olursa `ElseIf` mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a25b8-113">Required if `ElseIf` is present.</span></span> <span data-ttu-id="a25b8-114">İfade.</span><span class="sxs-lookup"><span data-stu-id="a25b8-114">Expression.</span></span> <span data-ttu-id="a25b8-115">Değerlendirilmelidir `True` veya `False`, ya da örtük olarak parametresinin veri türü için `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-115">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="a25b8-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a25b8-116">Optional.</span></span> <span data-ttu-id="a25b8-117">Bir veya daha fazla deyimleri aşağıdaki `ElseIf`... `Then` varsa yürütülme `elseifcondition` değerlendiren `True`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-117">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="a25b8-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a25b8-118">Optional.</span></span> <span data-ttu-id="a25b8-119">Hayır önceki varsa yürütülen bir veya daha fazla deyimleri `condition` veya `elseifcondition` ifadeyi hesaplar için `True`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-119">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="a25b8-120">Sonlandırır `If`... `Then`... `Else` bloğu.</span><span class="sxs-lookup"><span data-stu-id="a25b8-120">Terminates the `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a25b8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a25b8-121">Remarks</span></span>  
  
## <a name="multiple-line-syntax"></a><span data-ttu-id="a25b8-122">Birden çok satırlı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a25b8-122">Multiple-Line Syntax</span></span>  
 <span data-ttu-id="a25b8-123">Zaman bir `If`... `Then`... `Else` deyimi karşılaştı, `condition` test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a25b8-123">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="a25b8-124">Varsa `condition` olan `True`, aşağıdaki deyimleri `Then` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a25b8-124">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="a25b8-125">Varsa `condition` olan `False`, her `ElseIf` deyimi (varsa) değerlendirildiği sırayla.</span><span class="sxs-lookup"><span data-stu-id="a25b8-125">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="a25b8-126">Zaman bir `True``elseifcondition` , hemen ilişkili aşağıdaki deyimleri bulunan `ElseIf` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a25b8-126">When a `True``elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="a25b8-127">Öyle değilse `elseifcondition` değerlendiren `True`, veya varsa hiçbir `ElseIf` deyimleri, aşağıdaki deyimleri `Else` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a25b8-127">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="a25b8-128">Deyimlerini aşağıdaki yürütme sonrasında `Then`, `ElseIf`, veya `Else`, yürütülmeye deyimi aşağıdaki `End If`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-128">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="a25b8-129">`ElseIf` Ve `Else` yan tümceleri olan isteğe bağlı hem de.</span><span class="sxs-lookup"><span data-stu-id="a25b8-129">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="a25b8-130">Kadar olabilir `ElseIf` yan tümceleri aynı istediğiniz bir `If`... `Then`... `Else` deyimi ancak hiçbir `ElseIf` yan tümcesi sonra görünebilir bir `Else` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a25b8-130">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="a25b8-131">`If`... `Then`... `Else` deyimleri iç içe geçirilemez diğer içinde.</span><span class="sxs-lookup"><span data-stu-id="a25b8-131">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="a25b8-132">Birden çok satırlı sözdiziminde `If` deyimi, ilk satırda yegane deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a25b8-132">In the multiple-line syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="a25b8-133">`ElseIf`, `Else`, Ve `End If` deyimleri yalnızca bir satır etiketle öncesinde.</span><span class="sxs-lookup"><span data-stu-id="a25b8-133">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="a25b8-134">`If`... `Then`... `Else` bloğu ile bitmelidir bir `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a25b8-134">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="a25b8-135">[Seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) birkaç olası değerlere sahip tek bir ifade değerlendirme daha yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a25b8-135">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
## <a name="single-line-syntax"></a><span data-ttu-id="a25b8-136">Tek satırlı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a25b8-136">Single-Line Syntax</span></span>  
 <span data-ttu-id="a25b8-137">Tek satırlı sözdizimi kısa, basit testler için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a25b8-137">You can use the single-line syntax for short, simple tests.</span></span> <span data-ttu-id="a25b8-138">Ancak, birden çok satırlı sözdizimi yapısı ve daha fazla esneklik sağlar ve okuma, korumanıza ve hata ayıklama daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="a25b8-138">However, the multiple-line syntax provides more structure and flexibility and is usually easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="a25b8-139">Hangi aşağıdaki `Then` anahtar sözcüğü bir deyim tek satırlı olup olmadığını belirlemek için incelenir `If`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-139">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="a25b8-140">Bir yorum dışında her şey sonra görünürse `Then` aynı satırda deyim tek satırlı kabul edilir `If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a25b8-140">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="a25b8-141">Varsa `Then` yoksa, birden çok satırlı başlangıcı olmalıdır `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="a25b8-141">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="a25b8-142">Tek satırlı sözdiziminde sonucu olarak yürütülen birden çok deyime olabilir bir `If`... `Then` karar.</span><span class="sxs-lookup"><span data-stu-id="a25b8-142">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="a25b8-143">Tüm ifadeler aynı satırda olmalıdır ve virgüllerle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="a25b8-143">All statements must be on the same line and be separated by colons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25b8-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="a25b8-144">Example</span></span>  
 <span data-ttu-id="a25b8-145">Aşağıdaki örnek birden çok satırlı sözdizimi kullanımı gösterilmektedir `If`... `Then`... `Else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a25b8-145">The following example illustrates the use of the multiple-line syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="a25b8-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="a25b8-146">Example</span></span>  
 <span data-ttu-id="a25b8-147">Aşağıdaki örnek içeren iç içe geçmiş `If`... `Then`... `Else` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="a25b8-147">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a25b8-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="a25b8-148">Example</span></span>  
 <span data-ttu-id="a25b8-149">Aşağıdaki örnek, tek satırlı sözdizimi kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a25b8-149">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a25b8-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a25b8-150">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [<span data-ttu-id="a25b8-151">#If... Then... #Else yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a25b8-151">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="a25b8-152">Seçin... Case deyimi</span><span class="sxs-lookup"><span data-stu-id="a25b8-152">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="a25b8-153">İç içe geçmiş denetim yapıları</span><span class="sxs-lookup"><span data-stu-id="a25b8-153">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="a25b8-154">Karar yapıları</span><span class="sxs-lookup"><span data-stu-id="a25b8-154">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="a25b8-155">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="a25b8-155">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="a25b8-156">Varsa işleci</span><span class="sxs-lookup"><span data-stu-id="a25b8-156">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
