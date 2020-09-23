---
title: Boole İfadeleri
ms.date: 07/20/2015
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
ms.openlocfilehash: 51340bf95795d837c055df796424f3cad912adc7
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085756"
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="9fda0-102">Boolean İfadeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fda0-102">Boolean Expressions (Visual Basic)</span></span>

<span data-ttu-id="9fda0-103">*Boole ifadesi* , [Boolean veri türü](../../../language-reference/data-types/boolean-data-type.md)değeri olarak değerlendirilen bir ifadedir: `True` veya `False` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="9fda0-104">`Boolean` ifadeler birkaç form alabilir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="9fda0-105">En basit, `Boolean` `Boolean` Aşağıdaki örnekte gösterildiği gibi, bir değişkenin değerinin bir sabit değere doğrudan karşılaştırılmasının en kolayıdır.</span><span class="sxs-lookup"><span data-stu-id="9fda0-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="9fda0-106">= Işlecinin iki anlamı</span><span class="sxs-lookup"><span data-stu-id="9fda0-106">Two Meanings of the = Operator</span></span>  

 <span data-ttu-id="9fda0-107">Atama deyiminin `newCustomer = True` önceki örnekteki ifadeyle aynı göründüğünü, ancak farklı bir işlev gerçekleştirdiğini ve farklı şekilde kullanıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9fda0-107">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="9fda0-108">Yukarıdaki örnekte, ifadesi `newCustomer = True` bir Boolean değeri temsil eder ve `=` işaret bir karşılaştırma işleci olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="9fda0-108">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="9fda0-109">Bağımsız bir ifadede, `=` işaret atama işleci olarak yorumlanır ve sağdaki değeri soldaki değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="9fda0-109">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="9fda0-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 <span data-ttu-id="9fda0-111">Daha fazla bilgi için bkz. [değer karşılaştırmaları](value-comparisons.md) ve [deyimleri](../../../language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="9fda0-111">For further information, see [Value Comparisons](value-comparisons.md) and [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="9fda0-112">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9fda0-112">Comparison Operators</span></span>  

 <span data-ttu-id="9fda0-113">,,,, Ve gibi karşılaştırma işleçleri, `=` `<` `>` `<>` `<=` `>=` işlecin sol tarafındaki ifadesini işlecin sağ tarafındaki ifadeye karşılaştıran ve sonucu veya olarak değerlendiren Boolean ifadeler üretir `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-113">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="9fda0-114">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-114">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="9fda0-115">42, 81 ' den az olduğu için, önceki örnekteki Boole ifadesi olarak değerlendirilir `True` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-115">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="9fda0-116">Bu tür bir ifade hakkında daha fazla bilgi için bkz. [değer karşılaştırmaları](value-comparisons.md).</span><span class="sxs-lookup"><span data-stu-id="9fda0-116">For more information on this kind of expression, see [Value Comparisons](value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="9fda0-117">Mantıksal Işleçlerle birleştirilmiş karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="9fda0-117">Comparison Operators Combined with Logical Operators</span></span>  

 <span data-ttu-id="9fda0-118">Karşılaştırma ifadeleri, daha karmaşık Boole ifadeleri oluşturmak için mantıksal işleçler kullanılarak birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-118">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="9fda0-119">Aşağıdaki örnek, bir mantıksal işleçle birlikte karşılaştırma işleçleri kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-119">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="9fda0-120">Yukarıdaki örnekte, genel ifadenin değeri, işlecin her tarafındaki ifadelerin değerlerine bağlıdır `And` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-120">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="9fda0-121">Her iki ifade de ise `True` , genel ifade olarak değerlendirilir `True` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-121">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="9fda0-122">Her iki ifade ise `False` , tüm ifade olarak değerlendirilir `False` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-122">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="9fda0-123">Kısa devre dışı Işleçler</span><span class="sxs-lookup"><span data-stu-id="9fda0-123">Short-Circuiting Operators</span></span>  

 <span data-ttu-id="9fda0-124">Mantıksal işleçler `AndAlso` ve `OrElse` *kısa*devre olarak bilinen bir davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-124">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="9fda0-125">Kısa devre dışı bir işleç, önce sol işleneni değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-125">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="9fda0-126">Sol işlenen tüm ifadenin değerini belirlerse, program yürütmesi, doğru ifadeyi değerlendirmeden devam eder.</span><span class="sxs-lookup"><span data-stu-id="9fda0-126">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="9fda0-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-127">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 <span data-ttu-id="9fda0-128">Önceki örnekte, işleç sol ifadeyi değerlendirir `45 < 12` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-128">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="9fda0-129">Sol ifade olarak değerlendirdiği için `False` , mantıksal ifadenin tamamı olarak değerlendirilmelidir `False` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-129">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="9fda0-130">Böylece program yürütme `If` , sağ ifadeyi değerlendirmeksizin blok içindeki kodun yürütülmesini atlar `testFunction(3)` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-130">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="9fda0-131">`testFunction()`Sol ifade tüm ifadeyi aştığından bu örnek çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="9fda0-131">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="9fda0-132">Benzer şekilde, bir mantıksal ifadedeki sol ifade `OrElse` olarak değerlendirilir `True` ,, sol ifade ifadenin tamamını zaten doğrulayan, yürütme, doğru ifadeyi değerlendirmeden bir sonraki kod satırına geçer.</span><span class="sxs-lookup"><span data-stu-id="9fda0-132">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="9fda0-133">Kısa devre dışı özellikli Işleçlerle karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="9fda0-133">Comparison with Non-Short-Circuiting Operators</span></span>  

 <span data-ttu-id="9fda0-134">Buna karşılık, mantıksal işlecin her iki tarafı da mantıksal işleçler ve kullanıldığı zaman değerlendirilir `And` `Or` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-134">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="9fda0-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 <span data-ttu-id="9fda0-136">Yukarıdaki örnek, `testFunction()` sol ifade olarak değerlendirilse de çağırır `False` .</span><span class="sxs-lookup"><span data-stu-id="9fda0-136">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="9fda0-137">Parantez içinde Ifadeler</span><span class="sxs-lookup"><span data-stu-id="9fda0-137">Parenthetical Expressions</span></span>  

 <span data-ttu-id="9fda0-138">Boolean ifadelerin değerlendirilme sırasını denetlemek için parantezleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fda0-138">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="9fda0-139">Parantez içine alınmış ifadeler ilk olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-139">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="9fda0-140">Birden çok iç içe geçme düzeyi için, en derin iç içe ifadelere öncelik verilir.</span><span class="sxs-lookup"><span data-stu-id="9fda0-140">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="9fda0-141">Parantez içinde, değerlendirme işleç önceliği kurallarına göre devam eder.</span><span class="sxs-lookup"><span data-stu-id="9fda0-141">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="9fda0-142">Daha fazla bilgi için [Visual Basic operatör önceliği](../../../language-reference/operators/operator-precedence.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9fda0-142">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fda0-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fda0-143">See also</span></span>

- [<span data-ttu-id="9fda0-144">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="9fda0-144">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="9fda0-145">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="9fda0-145">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="9fda0-146">Deyimler</span><span class="sxs-lookup"><span data-stu-id="9fda0-146">Statements</span></span>](../statements.md)
- [<span data-ttu-id="9fda0-147">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="9fda0-147">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="9fda0-148">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="9fda0-148">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="9fda0-149">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="9fda0-149">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9fda0-150">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9fda0-150">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)
