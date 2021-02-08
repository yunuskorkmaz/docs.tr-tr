---
description: 'Hakkında daha fazla bilgi edinin: If... Sonra... Else ekstresi (Visual Basic)'
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
ms.openlocfilehash: 83850771354b95f0e2d9c1bf1360a61d5264fe2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769019"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="1ba8b-103">If...Then...Else Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ba8b-103">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="1ba8b-104">İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-104">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ba8b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ba8b-105">Syntax</span></span>

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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="1ba8b-106">Örnek koda hızlı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="1ba8b-106">Quick links to example code</span></span>

<span data-ttu-id="1ba8b-107">Bu makale, `If` .. `Then` . öğesinin kullanımını gösteren birkaç örnek içerir. ...`Else` Ekstre</span><span class="sxs-lookup"><span data-stu-id="1ba8b-107">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="1ba8b-108">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1ba8b-108">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="1ba8b-109">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1ba8b-109">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="1ba8b-110">Tek satırlık sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1ba8b-110">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="1ba8b-111">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1ba8b-111">Parts</span></span>

`condition` \
<span data-ttu-id="1ba8b-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-112">Required.</span></span> <span data-ttu-id="1ba8b-113">İfadesini.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-113">Expression.</span></span> <span data-ttu-id="1ba8b-114">`True` `False` Örtük olarak dönüştürülebilir bir veri türü veya ya da olarak değerlendirilmelidir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-114">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="1ba8b-115">İfade [](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` [hiçbir şey](../nothing.md)olarak değerlendirilen null yapılabilir bir değişkense, koşul ifade gibi değerlendirilir `False` ve bloklar varsa `ElseIf` değerlendirilir veya varsa, `Else` blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-115">If the expression is a [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="1ba8b-116">Tek satır sözdiziminde gereklidir; çok satırlı sözdiziminde isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-116">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="1ba8b-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-117">Optional.</span></span> <span data-ttu-id="1ba8b-118">Bir veya daha fazla deyimi. `If` .. `Then` , `condition` olarak değerlendirilirse yürütülür `True` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-118">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="1ba8b-119">Varsa gereklidir `ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-119">Required if `ElseIf` is present.</span></span> <span data-ttu-id="1ba8b-120">İfadesini.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-120">Expression.</span></span> <span data-ttu-id="1ba8b-121">`True` `False` Örtük olarak dönüştürülebilir bir veri türü veya ya da olarak değerlendirilmelidir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-121">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="1ba8b-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-122">Optional.</span></span> <span data-ttu-id="1ba8b-123">Bir veya daha fazla deyimi. `ElseIf` .. `Then` , `elseifcondition` olarak değerlendirilirse yürütülür `True` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-123">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="1ba8b-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-124">Optional.</span></span> <span data-ttu-id="1ba8b-125">Önceki `condition` veya `elseifcondition` ifade olarak değerlendirilen bir veya daha fazla deyim `True` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-125">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="1ba8b-126">Öğesinin çok satırlı sürümünü sonlandırır `If` ... `Then` ...`Else` engelleyin.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-126">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ba8b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ba8b-127">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="1ba8b-128">Çok satırlı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba8b-128">Multiline syntax</span></span>

<span data-ttu-id="1ba8b-129">Bir `If` .. `Then` . ...`Else` ifadesiyle karşılaşıldı, `condition` test edildi.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-129">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="1ba8b-130">`condition`İse `True` , aşağıdaki deyimler `Then` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-130">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="1ba8b-131">`condition`İse `False` , her `ElseIf` bir ifade (varsa) sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-131">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="1ba8b-132">Bir `True` `elseifcondition` oluşturulduğunda, ilişkili olan deyimler hemen sonrasında `ElseIf` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-132">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="1ba8b-133">`elseifcondition`, Olarak hesaplanırsa `True` veya `ElseIf` deyim yoksa, aşağıdaki deyimler `Else` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-133">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="1ba8b-134">, Veya sonraki deyimlerini yürüttükten sonra, `Then` `ElseIf` `Else` yürütme aşağıdaki deyimle devam eder `End If` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-134">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="1ba8b-135">`ElseIf`Ve `Else` yan tümceleri her ikisi de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-135">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="1ba8b-136">`ElseIf`Bir `If` .. `Then` . içinde istediğiniz sayıda yan tümce olabilir. ...`Else` deyimi, ancak `ElseIf` yan tümce sonrasında hiçbir yan tümce görünmeyebilir `Else` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-136">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="1ba8b-137">`If`...`Then` ...`Else` deyimler birbirini içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-137">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="1ba8b-138">Çok satırlı sözdiziminde, `If` deyimin ilk satırdaki tek bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-138">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="1ba8b-139">`ElseIf`, `Else` , Ve `End If` deyimleri önünde yalnızca bir çizgi etiketi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-139">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="1ba8b-140">`If`.. `Then` . ...`Else` Block bir `End If` ifadesiyle bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-140">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="1ba8b-141">[Seç... Case deyimi](select-case-statement.md) , birkaç olası değeri olan tek bir ifadeyi değerlendirirken daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-141">The [Select...Case Statement](select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="1ba8b-142">Single-Line sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba8b-142">Single-Line syntax</span></span>

<span data-ttu-id="1ba8b-143">Doğru ise yürütmek üzere kod ile tek bir koşul için tek satırlık sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-143">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="1ba8b-144">Ancak, çok satırlı sözdizimi daha fazla yapı ve esneklik sağlar ve okunması, bakımını yapmak ve hata ayıklaması daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-144">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="1ba8b-145">`Then`Bir deyimin tek satırlı olup olmadığını belirlemek için anahtar sözcüğü incelenir `If` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-145">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="1ba8b-146">Aynı satırdaki bir yorum dışında bir şey görünürse `Then` , ifadesi tek satırlık bir ifade olarak değerlendirilir `If` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-146">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="1ba8b-147">Yoksa `Then` , birden çok satırlık bir başlangıç olmalıdır `If` ... `Then` ...`Else`.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-147">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="1ba8b-148">Tek satır sözdiziminde, bir... kararı sonucu olarak birden çok deyim yürütülebileceğini sağlayabilirsiniz `If` `Then` .</span><span class="sxs-lookup"><span data-stu-id="1ba8b-148">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="1ba8b-149">Tüm deyimler aynı satırda olmalıdır ve iki nokta üst üste ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-149">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="1ba8b-150">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1ba8b-150">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="1ba8b-151">Aşağıdaki örnek, `If` .. `Then` . öğesinin çok satırlı sözdiziminin kullanımını gösterir. ...`Else` Ekstre.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-151">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="1ba8b-152">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1ba8b-152">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="1ba8b-153">Aşağıdaki örnek iç içe geçmiş `If` ... `Then` ...`Else` deyimler.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-153">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="1ba8b-154">Single-Line sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1ba8b-154">Single-Line syntax example</span></span>

<a name="single-line"></a> <span data-ttu-id="1ba8b-155">Aşağıdaki örnek, tek satırlık sözdiziminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-155">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="1ba8b-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba8b-156">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="1ba8b-157">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="1ba8b-157">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
- [<span data-ttu-id="1ba8b-158">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="1ba8b-158">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="1ba8b-159">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="1ba8b-159">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="1ba8b-160">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="1ba8b-160">Decision Structures</span></span>](../../programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="1ba8b-161">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="1ba8b-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="1ba8b-162">If İşleci</span><span class="sxs-lookup"><span data-stu-id="1ba8b-162">If Operator</span></span>](../operators/if-operator.md)
