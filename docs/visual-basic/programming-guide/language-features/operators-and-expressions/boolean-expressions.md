---
title: "Boolean İfadeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 48071c6833f9841fa42311dda59d6959c0645ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="84f62-102">Boolean İfadeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84f62-102">Boolean Expressions (Visual Basic)</span></span>
<span data-ttu-id="84f62-103">A *Boole ifadesi* değeri veren ifade [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="84f62-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="84f62-104">`Boolean`ifadeler çeşitli biçimlerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="84f62-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="84f62-105">Değerini doğrudan karşılaştırması kolayıdır bir `Boolean` için değişken bir `Boolean` değişmez değeri, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="84f62-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="84f62-106">İki anlamı = işleci</span><span class="sxs-lookup"><span data-stu-id="84f62-106">Two Meanings of the = Operator</span></span>  
 <span data-ttu-id="84f62-107">Dikkat atama ifadesi `newCustomer = True` aynı önceki örnekte ifade olarak görünür, ancak farklı bir işlevi gerçekleştirir ve farklı bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84f62-107">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="84f62-108">Önceki örnekte, ifade `newCustomer = True` bir Boole değeri temsil eder ve `=` oturum bir karşılaştırma işleci yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="84f62-108">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="84f62-109">Tek başına bir deyimde `=` oturum atama işleci yorumlanır ve değer sağındaki soldaki değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="84f62-109">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="84f62-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84f62-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 <span data-ttu-id="84f62-111">Daha fazla bilgi için bkz: [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) ve [deyimleri](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="84f62-111">For further information, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) and [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="84f62-112">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="84f62-112">Comparison Operators</span></span>  
 <span data-ttu-id="84f62-113">Karşılaştırma işleçleri gibi `=`, `<`, `>`, `<>`, `<=`, ve `>=` sol tarafındaki ifade işlecinin sağ tarafında ifadeye karşılaştırarak Boole ifadeleri oluşturmak işleç ve sonuç olarak değerlendiriliyor `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="84f62-113">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="84f62-114">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84f62-114">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="84f62-115">Önceki örnekte Boole ifadesi 42 81'den az olduğundan, değerlendiren `True`.</span><span class="sxs-lookup"><span data-stu-id="84f62-115">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="84f62-116">Bu tür bir ifade hakkında daha fazla bilgi için bkz: [değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span><span class="sxs-lookup"><span data-stu-id="84f62-116">For more information on this kind of expression, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="84f62-117">Mantıksal işleçlerle birleştirilmiş Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="84f62-117">Comparison Operators Combined with Logical Operators</span></span>  
 <span data-ttu-id="84f62-118">Karşılaştırma ifadeleri, daha karmaşık Boole ifadeleri oluşturmak için mantıksal işleçleri kullanılarak birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="84f62-118">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="84f62-119">Aşağıdaki örnek, bir mantıksal işleç ile birlikte Karşılaştırma işleçleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84f62-119">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="84f62-120">Önceki örnekte, her tarafında ifadelerin değerlerini genel ifadesinin değerini bağlıdır `And` işleci.</span><span class="sxs-lookup"><span data-stu-id="84f62-120">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="84f62-121">Her iki ifadeler `True`, genel ifade değerlendiren sonra `True`.</span><span class="sxs-lookup"><span data-stu-id="84f62-121">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="84f62-122">Ya da ifade ise `False`, tüm deyimin değerlendiren sonra `False`.</span><span class="sxs-lookup"><span data-stu-id="84f62-122">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="84f62-123">İşleçler kısa devre</span><span class="sxs-lookup"><span data-stu-id="84f62-123">Short-Circuiting Operators</span></span>  
 <span data-ttu-id="84f62-124">Mantıksal işleçler `AndAlso` ve `OrElse` olarak bilinen davranışlar *kısa devre*.</span><span class="sxs-lookup"><span data-stu-id="84f62-124">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="84f62-125">Short-circuiting işleci sol işleneni önce değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="84f62-125">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="84f62-126">Tüm ifadenin değerini sol işleneni karar verirse, program yürütme sağ ifade değerlendirmeden ilerler.</span><span class="sxs-lookup"><span data-stu-id="84f62-126">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="84f62-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84f62-127">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 <span data-ttu-id="84f62-128">Önceki örnekte, sol ifade işleci değerlendirir `45 < 12`.</span><span class="sxs-lookup"><span data-stu-id="84f62-128">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="84f62-129">Sol ifade için değerlendirildiği `False`, tüm mantıksal ifade değerlendirilmelidir `False`.</span><span class="sxs-lookup"><span data-stu-id="84f62-129">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="84f62-130">Program yürütme böylece içindeki kod yürütülmesi atlanıyor `If` sağ ifade değerlendirme olmadan blok `testFunction(3)`.</span><span class="sxs-lookup"><span data-stu-id="84f62-130">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="84f62-131">Bu örnek arama `testFunction()` tüm deyimin sol ifade falsifies olduğundan.</span><span class="sxs-lookup"><span data-stu-id="84f62-131">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="84f62-132">Benzer şekilde, mantıksal ifade kullanarak sol ifade `OrElse` değerlendiren `True`, yürütme devam eder kodunun bir sonraki satıra sağ ifade değerlendirmeden sol ifade zaten tüm doğruladı olduğundan ifade.</span><span class="sxs-lookup"><span data-stu-id="84f62-132">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="84f62-133">Olmayan--kestirmeler işleçleri ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="84f62-133">Comparison with Non-Short-Circuiting Operators</span></span>  
 <span data-ttu-id="84f62-134">Bunun aksine, mantıksal işlecinin iki tarafı da değerlendirilir zaman mantıksal işleçler `And` ve `Or` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84f62-134">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="84f62-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84f62-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 <span data-ttu-id="84f62-136">Yukarıdaki örnek çağrıları `testFunction()` sol ifade değerlendiren olsa bile `False`.</span><span class="sxs-lookup"><span data-stu-id="84f62-136">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="84f62-137">Parantez içinde ifadeler</span><span class="sxs-lookup"><span data-stu-id="84f62-137">Parenthetical Expressions</span></span>  
 <span data-ttu-id="84f62-138">Boole ifadeleri Değerlendirme sırasını denetlemek için parantez kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84f62-138">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="84f62-139">Parantez ifadeleri ilk değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="84f62-139">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="84f62-140">Birden çok iç içe geçme düzeyi için en fazla iç içe geçmiş ifadeler öncelik verilir.</span><span class="sxs-lookup"><span data-stu-id="84f62-140">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="84f62-141">Parantez içinde İşleç önceliği kurallarına göre değerlendirme devam eder.</span><span class="sxs-lookup"><span data-stu-id="84f62-141">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="84f62-142">Daha fazla bilgi için bkz: [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="84f62-142">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f62-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84f62-143">See Also</span></span>  
 [<span data-ttu-id="84f62-144">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="84f62-144">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="84f62-145">Değer karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="84f62-145">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="84f62-146">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="84f62-146">Statements</span></span>](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="84f62-147">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="84f62-147">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="84f62-148">İşleçlerin etkili bileşimi</span><span class="sxs-lookup"><span data-stu-id="84f62-148">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [<span data-ttu-id="84f62-149">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="84f62-149">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="84f62-150">Boole veri türü</span><span class="sxs-lookup"><span data-stu-id="84f62-150">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
