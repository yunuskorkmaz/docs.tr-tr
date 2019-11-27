---
title: If...Then...Else Deyimi
ms.date: 04/16/2018
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
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351157"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="5fc82-102">If...Then...Else Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fc82-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="5fc82-103">İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.</span><span class="sxs-lookup"><span data-stu-id="5fc82-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fc82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fc82-104">Syntax</span></span>

```vb
' Multiline syntax:
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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="5fc82-105">Örnek koda hızlı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="5fc82-105">Quick links to example code</span></span>

<span data-ttu-id="5fc82-106">Bu makale `If`...`Then`...`Else` deyimin kullanımını gösteren birkaç örnek içerir:</span><span class="sxs-lookup"><span data-stu-id="5fc82-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="5fc82-107">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="5fc82-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="5fc82-108">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="5fc82-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="5fc82-109">Tek satırlık sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="5fc82-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="5fc82-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5fc82-110">Parts</span></span>

`condition` \
<span data-ttu-id="5fc82-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5fc82-111">Required.</span></span> <span data-ttu-id="5fc82-112">İfadesini.</span><span class="sxs-lookup"><span data-stu-id="5fc82-112">Expression.</span></span> <span data-ttu-id="5fc82-113">`True` veya `False`veya `Boolean`örtük olarak dönüştürülebilir bir veri türü olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="5fc82-114">İfade [hiçbir şey](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilen [null yapılabilir](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değişkense, koşul, ifade `False`gibi değerlendirilir ve `ElseIf` blokları varsa değerlendirilir veya varsa `Else` bloğu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5fc82-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="5fc82-115">Tek satır sözdiziminde gereklidir; çok satırlı sözdiziminde isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fc82-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="5fc82-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fc82-116">Optional.</span></span> <span data-ttu-id="5fc82-117">`condition` `True`olarak değerlendiriliyorsa yürütülen`Then` `If`... izleyen bir veya daha fazla deyim.</span><span class="sxs-lookup"><span data-stu-id="5fc82-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="5fc82-118">`ElseIf` varsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="5fc82-119">İfadesini.</span><span class="sxs-lookup"><span data-stu-id="5fc82-119">Expression.</span></span> <span data-ttu-id="5fc82-120">`True` veya `False`veya `Boolean`örtük olarak dönüştürülebilir bir veri türü olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="5fc82-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fc82-121">Optional.</span></span> <span data-ttu-id="5fc82-122">`elseifcondition` `True`olarak değerlendiriliyorsa yürütülen`Then` `ElseIf`... izleyen bir veya daha fazla deyim.</span><span class="sxs-lookup"><span data-stu-id="5fc82-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="5fc82-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fc82-123">Optional.</span></span> <span data-ttu-id="5fc82-124">Önceki `condition` veya `elseifcondition` ifadesi `True`olarak değerlendiriliyorsa yürütülen bir veya daha fazla deyim.</span><span class="sxs-lookup"><span data-stu-id="5fc82-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="5fc82-125">`If`...`Then`...`Else` bloğunun çok satırlı sürümünü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="5fc82-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fc82-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fc82-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="5fc82-127">Çok satırlı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fc82-127">Multiline syntax</span></span>

<span data-ttu-id="5fc82-128">Bir `If`...`Then`...`Else` ifadesiyle karşılaşıldığında, `condition` test edilir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="5fc82-129">`condition` `True`, `Then` Aşağıdaki deyimler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5fc82-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="5fc82-130">`condition` `False`, her `ElseIf` deyimin (varsa) sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="5fc82-131">Bir `True` `elseifcondition` bulunduğunda, ilişkili `ElseIf` hemen sonraki deyimler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5fc82-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="5fc82-132">`elseifcondition` `True`olarak değerlendiriliyorsa veya `ElseIf` deyim yoksa, `Else` Aşağıdaki deyimler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5fc82-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="5fc82-133">`Then`, `ElseIf`veya `Else`sonraki deyimlerini yürüttükten sonra, yürütme `End If`aşağıdaki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="5fc82-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="5fc82-134">`ElseIf` ve `Else` yan tümceleri her ikisi de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc82-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="5fc82-135">Bir `If`...`Then`...`Else` ifadesinde istediğiniz sayıda `ElseIf` yan tümcesine sahip olabilirsiniz, ancak bir `ElseIf` yan tümcesi sonrasında hiçbir `Else` yan tümcesi görünebilirler.</span><span class="sxs-lookup"><span data-stu-id="5fc82-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="5fc82-136">`If`...`Then`...`Else` deyimleri birbirini içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="5fc82-137">Çok satırlı sözdiziminde, `If` deyimin ilk satırdaki tek bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="5fc82-138">`ElseIf`, `Else`ve `End If` deyimleri önünde yalnızca bir çizgi etiketi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="5fc82-139">`If`...`Then`...`Else` bloğunun bir `End If` ifadesiyle bitmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="5fc82-140">[Seç... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) , birkaç olası değeri olan tek bir ifadeyi değerlendirirken daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="5fc82-141">Tek satır sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fc82-141">Single-Line syntax</span></span>

<span data-ttu-id="5fc82-142">Doğru ise yürütmek üzere kod ile tek bir koşul için tek satırlık sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc82-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="5fc82-143">Ancak, çok satırlı sözdizimi daha fazla yapı ve esneklik sağlar ve okunması, bakımını yapmak ve hata ayıklaması daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="5fc82-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="5fc82-144">Bir deyimin tek satırlı bir `If`olup olmadığını belirlemek için `Then` anahtar sözcüğünün incelenmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="5fc82-145">Aynı satırdaki `Then` sonrasında açıklama dışında bir şey görünürse, ifadesi tek satırlık bir `If` ifadesi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="5fc82-146">`Then` yoksa, birden çok satırlık bir `If`...`Then`...`Else`başlangıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc82-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="5fc82-147">Tek satır sözdiziminde, bir `If`...`Then` kararının sonucu olarak birden çok deyim yürütülebileceğini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fc82-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="5fc82-148">Tüm deyimler aynı satırda olmalıdır ve iki nokta üst üste ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fc82-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="5fc82-149">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="5fc82-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="5fc82-150">Aşağıdaki örnek, `If`...`Then`...`Else` ifadesinin çok satırlı sözdiziminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="5fc82-151">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="5fc82-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="5fc82-152">Aşağıdaki örnek iç içe geçmiş `If`...`Then`...`Else` deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="5fc82-153">Tek satırlık sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="5fc82-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="5fc82-154">Aşağıdaki örnek, tek satırlık sözdiziminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fc82-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="5fc82-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fc82-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="5fc82-156">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5fc82-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="5fc82-157">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="5fc82-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="5fc82-158">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="5fc82-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="5fc82-159">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="5fc82-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="5fc82-160">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="5fc82-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="5fc82-161">If İşleci</span><span class="sxs-lookup"><span data-stu-id="5fc82-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
