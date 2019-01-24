---
title: If...Then...Else Deyimi (Visual Basic)
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
ms.openlocfilehash: ceca58b2d69d72e079a9f2e2791f7f586c459167
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743653"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="7e9c3-102">If...Then...Else Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e9c3-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="7e9c3-103">İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e9c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e9c3-104">Syntax</span></span>  
  
```  
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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="7e9c3-105">Örnek kod için hızlı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="7e9c3-105">Quick links to example code</span></span>

<span data-ttu-id="7e9c3-106">Bu makalede kullanımlarını gösteren birkaç örnek içeren `If`... `Then`... `Else` deyimi:</span><span class="sxs-lookup"><span data-stu-id="7e9c3-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

* [<span data-ttu-id="7e9c3-107">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="7e9c3-107">Multiline syntax example</span></span>](#multi-line)
* [<span data-ttu-id="7e9c3-108">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="7e9c3-108">Nested syntax example</span></span>](#nested)
* [<span data-ttu-id="7e9c3-109">Tek satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="7e9c3-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="7e9c3-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7e9c3-110">Parts</span></span>  
 `condition`  
 <span data-ttu-id="7e9c3-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-111">Required.</span></span> <span data-ttu-id="7e9c3-112">Expression.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-112">Expression.</span></span> <span data-ttu-id="7e9c3-113">Değerlendirilmelidir `True` veya `False`, ya da örtük olarak dönüştürülebilir bir veri türüne `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="7e9c3-114">İfade ise bir [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değerlendiren değişkeni [hiçbir şey](../../../visual-basic/language-reference/nothing.md), ifade ise, koşulu kabul edilir `False` ve `Else` bloğu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False` and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="7e9c3-115">Tek satırlı sözdiziminde gerekli; çok satırlı sözdiziminde isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="7e9c3-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-116">Optional.</span></span> <span data-ttu-id="7e9c3-117">Bir veya daha fazla deyimlerini aşağıdaki `If`... `Then` durumunda yürütülen `condition` değerlendiren `True`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="7e9c3-118">Gerekli if `ElseIf` mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="7e9c3-119">Expression.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-119">Expression.</span></span> <span data-ttu-id="7e9c3-120">Değerlendirilmelidir `True` veya `False`, ya da örtük olarak dönüştürülebilir bir veri türüne `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="7e9c3-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-121">Optional.</span></span> <span data-ttu-id="7e9c3-122">Bir veya daha fazla deyimlerini aşağıdaki `ElseIf`... `Then` durumunda yürütülen `elseifcondition` değerlendiren `True`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="7e9c3-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-123">Optional.</span></span> <span data-ttu-id="7e9c3-124">Hayır önceki durumunda yürütülen bir veya daha fazla deyimleri `condition` veya `elseifcondition` ifadeyi hesaplar için `True`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="7e9c3-125">Çok satırlı sürümünü sonlandırır `If`... `Then`... `Else` blok.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e9c3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e9c3-126">Remarks</span></span>  
  
### <a name="multiline-syntax"></a><span data-ttu-id="7e9c3-127">Çok satırlı söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e9c3-127">Multiline syntax</span></span>  
 <span data-ttu-id="7e9c3-128">Olduğunda bir `If`... `Then`... `Else` deyimi karşılaştı, `condition` test edilir.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="7e9c3-129">Varsa `condition` olduğu `True`, aşağıdaki deyimleri `Then` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="7e9c3-130">Varsa `condition` olduğu `False`, her `ElseIf` deyimi (varsa) değerlendirilir sırada.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="7e9c3-131">Olduğunda bir `True` `elseifcondition` hemen ilişkili aşağıdaki deyimleri bulunana `ElseIf` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="7e9c3-132">Hayır ise `elseifcondition` değerlendiren `True`, veya varsa hiçbir `ElseIf` ifadeleri, aşağıdaki deyimleri `Else` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="7e9c3-133">Deyimler yürütüldükten sonra `Then`, `ElseIf`, veya `Else`, yürütme devam eder, deyimi aşağıdaki `End If`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="7e9c3-134">`ElseIf` Ve `Else` yan tümceleri olan hem de isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="7e9c3-135">Kadar olabilir `ElseIf` istediğiniz şekilde yan tümceleri bir `If`... `Then`... `Else` deyimi, ancak Hayır `ElseIf` yan tümcesi, sonra görünebilir bir `Else` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="7e9c3-136">`If`... `Then`... `Else` ifadeleri iç içe geçirilemez diğer içinde.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="7e9c3-137">Çok satırlı sözdiziminde `If` deyimi ilk satırda tek deyim olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="7e9c3-138">`ElseIf`, `Else`, Ve `End If` deyimleri yalnızca bir satır etiketi tarafından öncesinde.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="7e9c3-139">`If`... `Then`... `Else` blok sonlanmalı bir `End If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="7e9c3-140">[Seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) birkaç olası değerleri içeren tek bir ifade değerlendirirken daha kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
### <a name="single-line-syntax"></a><span data-ttu-id="7e9c3-141">Tek satırlı söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e9c3-141">Single-Line syntax</span></span>  
 <span data-ttu-id="7e9c3-142">True ise yürütmek için kod ile tek bir koşul için tek satır sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="7e9c3-143">Ancak, çok satırlı söz dizimi daha fazla yapısı ve esneklik sağlar ve daha kolay okumak, güncelleştirmek ve hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="7e9c3-144">Aşağıda `Then` anahtar sözcüğü bir deyim tek satırlı olup olmadığını belirlemek için incelenir `If`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="7e9c3-145">Bir açıklama dışındaki herhangi bir şey sonra görünürse `Then` aynı satırda deyimi tek satır kabul edilir `If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="7e9c3-146">Varsa `Then` eksik, çok satırlı başlangıcını olmalıdır `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="7e9c3-147">Tek satırlı sözdiziminde sonucu olarak çalıştırılan birden çok deyime sahip bir `If`... `Then` karar.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="7e9c3-148">Tüm ifadeler aynı satırda olmalıdır ve virgüllerle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-148">All statements must be on the same line and be separated by colons.</span></span>  

## <a name="multiline-syntax-example"></a><span data-ttu-id="7e9c3-149">Çok satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="7e9c3-149">Multiline syntax example</span></span>

<a name="multi-line"></a>
 
 <span data-ttu-id="7e9c3-150">Çok satırlı söz diziminin kullanılması aşağıdaki örnekte `If`... `Then`... `Else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb?highlight=11,14,17,19)]

## <a name="nested-syntax-example"></a><span data-ttu-id="7e9c3-151">İç içe geçmiş sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="7e9c3-151">Nested syntax example</span></span>

<a name="nested"></a>

 <span data-ttu-id="7e9c3-152">Aşağıdaki örnek içeren iç içe geçmiş `If`... `Then`... `Else` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb?highlight=14,15,17,19,20,21,23,25,26,28)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="7e9c3-153">Tek satırlı sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="7e9c3-153">Single-Line syntax example</span></span>
  
<a name="single-line"></a> <span data-ttu-id="7e9c3-154">Aşağıdaki örnek, tek satırlı söz dizimi kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-154">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb?highlight=18)]
  
## <a name="see-also"></a><span data-ttu-id="7e9c3-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e9c3-155">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="7e9c3-156">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="7e9c3-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="7e9c3-157">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="7e9c3-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="7e9c3-158">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="7e9c3-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="7e9c3-159">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="7e9c3-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="7e9c3-160">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="7e9c3-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="7e9c3-161">If İşleci</span><span class="sxs-lookup"><span data-stu-id="7e9c3-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
