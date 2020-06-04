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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404595"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="54438-102">If...Then...Else Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54438-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="54438-103">İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.</span><span class="sxs-lookup"><span data-stu-id="54438-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="54438-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54438-104">Syntax</span></span>

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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="54438-105">Örnek koda hızlı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="54438-105">Quick links to example code</span></span>

<span data-ttu-id="54438-106">Bu makale, `If` .. `Then` . öğesinin kullanımını gösteren birkaç örnek içerir. ...`Else` Ekstre</span><span class="sxs-lookup"><span data-stu-id="54438-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="54438-107">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="54438-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="54438-108">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="54438-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="54438-109">Tek satırlık sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="54438-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="54438-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="54438-110">Parts</span></span>

`condition` \
<span data-ttu-id="54438-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54438-111">Required.</span></span> <span data-ttu-id="54438-112">İfadesini.</span><span class="sxs-lookup"><span data-stu-id="54438-112">Expression.</span></span> <span data-ttu-id="54438-113">`True` `False` Örtük olarak dönüştürülebilir bir veri türü veya ya da olarak değerlendirilmelidir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="54438-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="54438-114">İfade [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` [hiçbir şey](../nothing.md)olarak değerlendirilen null yapılabilir bir değişkense, koşul ifade gibi değerlendirilir `False` ve bloklar varsa `ElseIf` değerlendirilir veya varsa, `Else` blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="54438-114">If the expression is a [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="54438-115">Tek satır sözdiziminde gereklidir; çok satırlı sözdiziminde isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="54438-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="54438-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="54438-116">Optional.</span></span> <span data-ttu-id="54438-117">Bir veya daha fazla deyimi. `If` .. `Then` , `condition` olarak değerlendirilirse yürütülür `True` .</span><span class="sxs-lookup"><span data-stu-id="54438-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="54438-118">Varsa gereklidir `ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="54438-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="54438-119">İfadesini.</span><span class="sxs-lookup"><span data-stu-id="54438-119">Expression.</span></span> <span data-ttu-id="54438-120">`True` `False` Örtük olarak dönüştürülebilir bir veri türü veya ya da olarak değerlendirilmelidir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="54438-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="54438-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="54438-121">Optional.</span></span> <span data-ttu-id="54438-122">Bir veya daha fazla deyimi. `ElseIf` .. `Then` , `elseifcondition` olarak değerlendirilirse yürütülür `True` .</span><span class="sxs-lookup"><span data-stu-id="54438-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="54438-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="54438-123">Optional.</span></span> <span data-ttu-id="54438-124">Önceki `condition` veya `elseifcondition` ifade olarak değerlendirilen bir veya daha fazla deyim `True` .</span><span class="sxs-lookup"><span data-stu-id="54438-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="54438-125">Öğesinin çok satırlı sürümünü sonlandırır `If` ... `Then` ...`Else` engelleyin.</span><span class="sxs-lookup"><span data-stu-id="54438-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="54438-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54438-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="54438-127">Çok satırlı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54438-127">Multiline syntax</span></span>

<span data-ttu-id="54438-128">Bir `If` .. `Then` . ...`Else` ifadesiyle karşılaşıldı, `condition` test edildi.</span><span class="sxs-lookup"><span data-stu-id="54438-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="54438-129">`condition`İse `True` , aşağıdaki deyimler `Then` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="54438-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="54438-130">`condition`İse `False` , her `ElseIf` bir ifade (varsa) sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="54438-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="54438-131">Bir `True` `elseifcondition` oluşturulduğunda, ilişkili olan deyimler hemen sonrasında `ElseIf` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="54438-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="54438-132">`elseifcondition`, Olarak hesaplanırsa `True` veya `ElseIf` deyim yoksa, aşağıdaki deyimler `Else` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="54438-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="54438-133">, Veya sonraki deyimlerini yürüttükten sonra, `Then` `ElseIf` `Else` yürütme aşağıdaki deyimle devam eder `End If` .</span><span class="sxs-lookup"><span data-stu-id="54438-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="54438-134">`ElseIf`Ve `Else` yan tümceleri her ikisi de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="54438-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="54438-135">`ElseIf`Bir `If` .. `Then` . içinde istediğiniz sayıda yan tümce olabilir. ...`Else` deyimi, ancak `ElseIf` yan tümce sonrasında hiçbir yan tümce görünmeyebilir `Else` .</span><span class="sxs-lookup"><span data-stu-id="54438-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="54438-136">`If`...`Then` ...`Else` deyimler birbirini içinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="54438-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="54438-137">Çok satırlı sözdiziminde, `If` deyimin ilk satırdaki tek bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54438-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="54438-138">`ElseIf`, `Else` , Ve `End If` deyimleri önünde yalnızca bir çizgi etiketi olabilir.</span><span class="sxs-lookup"><span data-stu-id="54438-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="54438-139">`If`.. `Then` . ...`Else` Block bir `End If` ifadesiyle bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="54438-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="54438-140">[Seç... Case deyimi](select-case-statement.md) , birkaç olası değeri olan tek bir ifadeyi değerlendirirken daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54438-140">The [Select...Case Statement](select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="54438-141">Tek satır sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54438-141">Single-Line syntax</span></span>

<span data-ttu-id="54438-142">Doğru ise yürütmek üzere kod ile tek bir koşul için tek satırlık sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54438-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="54438-143">Ancak, çok satırlı sözdizimi daha fazla yapı ve esneklik sağlar ve okunması, bakımını yapmak ve hata ayıklaması daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="54438-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="54438-144">`Then`Bir deyimin tek satırlı olup olmadığını belirlemek için anahtar sözcüğü incelenir `If` .</span><span class="sxs-lookup"><span data-stu-id="54438-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="54438-145">Aynı satırdaki bir yorum dışında bir şey görünürse `Then` , ifadesi tek satırlık bir ifade olarak değerlendirilir `If` .</span><span class="sxs-lookup"><span data-stu-id="54438-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="54438-146">Yoksa `Then` , birden çok satırlık bir başlangıç olmalıdır `If` ... `Then` ...`Else`.</span><span class="sxs-lookup"><span data-stu-id="54438-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="54438-147">Tek satır sözdiziminde, bir... kararı sonucu olarak birden çok deyim yürütülebileceğini sağlayabilirsiniz `If` `Then` .</span><span class="sxs-lookup"><span data-stu-id="54438-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="54438-148">Tüm deyimler aynı satırda olmalıdır ve iki nokta üst üste ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54438-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="54438-149">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="54438-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="54438-150">Aşağıdaki örnek, `If` .. `Then` . öğesinin çok satırlı sözdiziminin kullanımını gösterir. ...`Else` Ekstre.</span><span class="sxs-lookup"><span data-stu-id="54438-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="54438-151">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="54438-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="54438-152">Aşağıdaki örnek iç içe geçmiş `If` ... `Then` ...`Else` deyimler.</span><span class="sxs-lookup"><span data-stu-id="54438-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="54438-153">Tek satırlık sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="54438-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="54438-154">Aşağıdaki örnek, tek satırlık sözdiziminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54438-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="54438-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54438-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="54438-156">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="54438-156">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
- [<span data-ttu-id="54438-157">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="54438-157">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="54438-158">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="54438-158">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="54438-159">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="54438-159">Decision Structures</span></span>](../../programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="54438-160">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="54438-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="54438-161">If İşleci</span><span class="sxs-lookup"><span data-stu-id="54438-161">If Operator</span></span>](../operators/if-operator.md)
