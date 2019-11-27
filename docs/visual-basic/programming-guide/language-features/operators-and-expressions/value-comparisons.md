---
title: Değer Karşılaştırmaları
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346282"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="87dad-102">Değer Karşılaştırmaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87dad-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="87dad-103">Karşılaştırma işleçleri, sayısal değişkenlerin değerlerini karşılaştıran ifadeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87dad-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="87dad-104">Bu ifadeler, karşılaştırmanın doğru veya yanlış olduğunu temel alarak bir `Boolean` değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="87dad-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="87dad-105">Bu tür bir ifadeye örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87dad-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="87dad-106">45, 26 ' dan büyük olduğundan, ilk ifade `True`olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="87dad-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="87dad-107">`False`, 26 ' 45 dan büyük olmadığından, ikinci örnek olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="87dad-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="87dad-108">Ayrıca, sayısal ifadeleri bu şekilde karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87dad-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="87dad-109">Karşılaştırılan ifadeler, aşağıdaki örnekte olduğu gibi karmaşık ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="87dad-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="87dad-110">Önceki karmaşık ifade, değişmez değerler, değişkenler ve işlev çağrıları içerir.</span><span class="sxs-lookup"><span data-stu-id="87dad-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="87dad-111">Karşılaştırma işlecinin her iki tarafındaki ifadeler değerlendirilir ve elde edilen değerler `>=` karşılaştırma işleci kullanılarak karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="87dad-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="87dad-112">Sol taraftaki ifadenin değeri sağdaki ifadenin değerinden büyükse veya eşitse, tüm ifade `True`olarak değerlendirilir. Aksi takdirde, `False`olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="87dad-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="87dad-113">Değerleri karşılaştıran ifadeler, aşağıdaki örnekte olduğu gibi `If...Then` kurulumlarını ' de en yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87dad-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="87dad-114">`=` işareti, bir karşılaştırma operatörünün yanı sıra atama işleçtir.</span><span class="sxs-lookup"><span data-stu-id="87dad-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="87dad-115">Karşılaştırma işleci olarak kullanıldığında, aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değere eşit olup olmadığını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="87dad-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="87dad-116">Karşılaştırma ifadesini, bir `If`, `While`, `Loop`veya `ElseIf` deyiminde olduğu gibi `Boolean` değerin her yerinde, ya da bir `Boolean` değişkenine atama ya da bir değere geçirilerek de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87dad-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="87dad-117">Aşağıdaki örnekte, karşılaştırma ifadesi tarafından döndürülen değer bir `Boolean` değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="87dad-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="87dad-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87dad-118">See also</span></span>

- [<span data-ttu-id="87dad-119">Boole İfadeleri</span><span class="sxs-lookup"><span data-stu-id="87dad-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="87dad-120">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="87dad-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="87dad-121">Visual Basic karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="87dad-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="87dad-122">Nasıl yapılır: Sayısal Değerleri Hesaplama</span><span class="sxs-lookup"><span data-stu-id="87dad-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="87dad-123">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="87dad-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
