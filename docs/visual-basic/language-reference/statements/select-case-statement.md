---
description: 'Daha fazla bilgi edinin: Select... Case ekstresi (Visual Basic)'
title: Select...Case Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 4f8edecd0a0b1afd59e182a372e308c3829a9b93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741139"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="23d80-103">Select...Case Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23d80-103">Select...Case Statement (Visual Basic)</span></span>

<span data-ttu-id="23d80-104">Bir ifadenin değerine bağlı olarak çeşitli deyim gruplarından birini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="23d80-104">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d80-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23d80-105">Syntax</span></span>  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="23d80-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="23d80-106">Parts</span></span>  
  
|<span data-ttu-id="23d80-107">Süre</span><span class="sxs-lookup"><span data-stu-id="23d80-107">Term</span></span>|<span data-ttu-id="23d80-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="23d80-108">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="23d80-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="23d80-109">Required.</span></span> <span data-ttu-id="23d80-110">İfadesini.</span><span class="sxs-lookup"><span data-stu-id="23d80-110">Expression.</span></span> <span data-ttu-id="23d80-111">Tek bir veri türü ( `Boolean` , `Byte` ,,,, `Char` `Date` `Double` `Decimal` , `Integer` , `Long` , `Object` , `SByte` , `Short` , `Single` , `String` , `UInteger` , `ULong` , ve `UShort` ) olarak değerlendirilmelidir</span><span class="sxs-lookup"><span data-stu-id="23d80-111">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="23d80-112">Bir bildirimde gereklidir `Case` .</span><span class="sxs-lookup"><span data-stu-id="23d80-112">Required in a `Case` statement.</span></span> <span data-ttu-id="23d80-113">İçin eşleşme değerlerini temsil eden ifade yan tümceleri listesi `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="23d80-113">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="23d80-114">Birden çok ifade yan tümceleri virgüller ile ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="23d80-114">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="23d80-115">Her yan tümce aşağıdaki formlardan birini alabilir:</span><span class="sxs-lookup"><span data-stu-id="23d80-115">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="23d80-116">-   *İfade1* `To` *İfade2*</span><span class="sxs-lookup"><span data-stu-id="23d80-116">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="23d80-117">-[ `Is` ] *ComparisonOperator* *ifadesi*</span><span class="sxs-lookup"><span data-stu-id="23d80-117">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="23d80-118">-   *ifadesini*</span><span class="sxs-lookup"><span data-stu-id="23d80-118">-   *expression*</span></span><br /><br /> <span data-ttu-id="23d80-119">`To`İçin bir eşleşme değerleri aralığının sınırlarını belirtmek için anahtar sözcüğünü kullanın `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="23d80-119">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="23d80-120">Değeri değerine `expression1` eşit veya ondan küçük olmalıdır `expression2` .</span><span class="sxs-lookup"><span data-stu-id="23d80-120">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="23d80-121">`Is` `=` `<>` `<` `<=` `>` `>=` Eşleştirme değerlerinde bir kısıtlama belirtmek için bir karşılaştırma işleci (,,,,, veya) ile anahtar sözcüğünü kullanın `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="23d80-121">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="23d80-122">`Is`Anahtar sözcüğü sağlanmazsa, *ComparisonOperator* öğesinden önce otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="23d80-122">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="23d80-123">Yalnızca belirten form, `expression` `Is` *ComparisonOperator* 'in eşittir işareti () olduğu formun özel durumu olarak değerlendirilir `=` .</span><span class="sxs-lookup"><span data-stu-id="23d80-123">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="23d80-124">Bu form olarak değerlendirilir `testexpression`  =  `expression` .</span><span class="sxs-lookup"><span data-stu-id="23d80-124">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="23d80-125">İçindeki ifadeler `expressionlist` herhangi bir veri türünde olabilir, bu, türüne örtülü olarak dönüştürülebilir `testexpression` ve uygun olan `comparisonoperator` iki tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="23d80-125">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="23d80-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="23d80-126">Optional.</span></span> <span data-ttu-id="23d80-127">`Case` `testexpression` ' Deki herhangi bir yan tümcesiyle eşleşiyorsa, çalıştıran bir veya daha fazla deyim `expressionlist` .</span><span class="sxs-lookup"><span data-stu-id="23d80-127">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="23d80-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="23d80-128">Optional.</span></span> <span data-ttu-id="23d80-129">Bir veya daha fazla deyimi, hiçbir `Case Else` `testexpression` deyimin içindeki herhangi bir yan tümce ile eşleşmezse çalışır `expressionlist` `Case` .</span><span class="sxs-lookup"><span data-stu-id="23d80-129">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="23d80-130">`Select`... Oluşturma tanımını sonlandırır `Case` .</span><span class="sxs-lookup"><span data-stu-id="23d80-130">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23d80-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23d80-131">Remarks</span></span>  

 <span data-ttu-id="23d80-132">`testexpression`Any `Case` `expressionlist` yan tümcesiyle eşleşirse, bu `Case` deyimden sonraki deyimler Next `Case` , `Case Else` , veya deyimi ile çalışır `End Select` .</span><span class="sxs-lookup"><span data-stu-id="23d80-132">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="23d80-133">Sonra Denetim aşağıdaki ifadeye geçer `End Select` .</span><span class="sxs-lookup"><span data-stu-id="23d80-133">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="23d80-134">Birden `testexpression` `expressionlist` fazla yan tümcedeki bir yan tümcesiyle eşleşiyorsa `Case` , yalnızca ilk eşleşmeyi izleyen deyimler çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="23d80-134">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="23d80-135">`Case Else`Deyimi, `elsestatements` `testexpression` `expressionlist` diğer deyimlerden herhangi birinde ve yan tümcesi arasında eşleşme bulunmazsa çalıştırmak için öğesini tanıtmak için kullanılır `Case` .</span><span class="sxs-lookup"><span data-stu-id="23d80-135">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="23d80-136">Gerekli olmasa da, `Case Else` `Select Case` öngörülenmeyen değerleri işlemek için oluşturma konusunda bir ifadeye sahip olmak iyi bir fikirdir `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="23d80-136">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="23d80-137">Hiçbir `Case` `expressionlist` yan tümce eşleşmez `testexpression` ve hiçbir deyimi yoksa `Case Else` , Denetim aşağıdaki deyime geçer `End Select` .</span><span class="sxs-lookup"><span data-stu-id="23d80-137">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="23d80-138">Her bir yan tümcesinde birden çok ifade veya Aralık kullanabilirsiniz `Case` .</span><span class="sxs-lookup"><span data-stu-id="23d80-138">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="23d80-139">Örneğin, aşağıdaki satır geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="23d80-139">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> <span data-ttu-id="23d80-140">`Is`Ve deyimlerde kullanılan anahtar sözcük, `Case` `Case Else` nesne başvuru karşılaştırması Için kullanılan [, işleç işleci](../operators/is-operator.md)ile aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="23d80-140">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="23d80-141">Karakter dizeleri için aralıklar ve birden çok ifade belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23d80-141">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="23d80-142">Aşağıdaki örnekte, `Case` "elmalar" ile tam olarak eşit olan herhangi bir dizeyle eşleşir, alfabetik düzende "nut" ve "Soup" arasında bir değere sahiptir veya geçerli değeri ile tam olarak aynı değeri içerir `testItem` .</span><span class="sxs-lookup"><span data-stu-id="23d80-142">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="23d80-143">Ayarı, `Option Compare` dize karşılaştırmaları etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="23d80-143">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="23d80-144">Altında `Option Compare Text` , "elmalar" ve "elmalar" dizeleri eşit olarak karşılaştırılır, ancak altında `Option Compare Binary` değildir.</span><span class="sxs-lookup"><span data-stu-id="23d80-144">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23d80-145">`Case`Birden çok yan tümcesini içeren bir ifade, kısa devre *dışı* olarak bilinen davranışları ortaya kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="23d80-145">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="23d80-146">Visual Basic yan tümceleri soldan sağa değerlendirir ve biri ile eşleşme üretiyorsa `testexpression` , kalan yan tümceler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="23d80-146">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="23d80-147">Kısa devre, performansı iyileştirebilir, ancak içindeki her ifadenin değerlendirilmesi bekleniyorsa beklenmeyen sonuçlar üretebilir `expressionlist` .</span><span class="sxs-lookup"><span data-stu-id="23d80-147">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="23d80-148">Kısa devre dışı hakkında daha fazla bilgi için bkz. [Boolean ifadeleri](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="23d80-148">For more information on short-circuiting, see [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="23d80-149">Bir `Case` veya `Case Else` deyim bloğundaki kodun bloğunda daha fazla deyim çalıştırması gerekmiyorsa, deyimi kullanılarak bloğundan çıkabilir `Exit Select` .</span><span class="sxs-lookup"><span data-stu-id="23d80-149">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="23d80-150">Bu, denetimi izleyen deyime hemen aktarır `End Select` .</span><span class="sxs-lookup"><span data-stu-id="23d80-150">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="23d80-151">`Select Case` kurulumlarını iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="23d80-151">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="23d80-152">İç içe yerleştirilmiş her `Select Case` oluşturma bir eşleşen `End Select` deyime sahip olmalı ve `Case` `Case Else` `Select Case` içinde iç içe olduğu dış oluşturma işleminin tek veya ifade bloğunda tamamen yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="23d80-152">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d80-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="23d80-153">Example</span></span>  

 <span data-ttu-id="23d80-154">Aşağıdaki örnek, `Select Case` değişkeninin değerine karşılık gelen bir satırı yazmak için bir oluşturma kullanır `number` .</span><span class="sxs-lookup"><span data-stu-id="23d80-154">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="23d80-155">İkinci `Case` ifade, geçerli değeri ile eşleşen değeri içerir `number` , bu nedenle "6 Ile 8 arasında", dahil "yazan bir ifade çalışır.</span><span class="sxs-lookup"><span data-stu-id="23d80-155">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a><span data-ttu-id="23d80-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23d80-156">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [<span data-ttu-id="23d80-157">End ekstresi</span><span class="sxs-lookup"><span data-stu-id="23d80-157">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="23d80-158">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="23d80-158">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="23d80-159">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="23d80-159">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="23d80-160">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="23d80-160">Exit Statement</span></span>](exit-statement.md)
