---
description: 'Daha fazla bilgi: değer karşılaştırmaları (Visual Basic)'
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
ms.openlocfilehash: b5d2228b5bb6be18aecebcd0247a1e29e29df9ec
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472715"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="b2717-103">Değer Karşılaştırmaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2717-103">Value Comparisons (Visual Basic)</span></span>

<span data-ttu-id="b2717-104">Karşılaştırma işleçleri, sayısal değişkenlerin değerlerini karşılaştıran ifadeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2717-104">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="b2717-105">Bu ifadeler `Boolean` , karşılaştırmanın doğru veya yanlış olduğunu temel alarak bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2717-105">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="b2717-106">Bu tür bir ifadeye örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b2717-106">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="b2717-107">`True`45, 26 ' dan büyük olduğu için ilk ifade olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b2717-107">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="b2717-108">İkinci örnek olarak değerlendirilir `False` , çünkü 26 45 ' den büyük değildir.</span><span class="sxs-lookup"><span data-stu-id="b2717-108">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="b2717-109">Ayrıca, sayısal ifadeleri bu şekilde karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2717-109">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="b2717-110">Karşılaştırılan ifadeler, aşağıdaki örnekte olduğu gibi karmaşık ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2717-110">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="b2717-111">Önceki karmaşık ifade, değişmez değerler, değişkenler ve işlev çağrıları içerir.</span><span class="sxs-lookup"><span data-stu-id="b2717-111">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="b2717-112">Karşılaştırma işlecinin her iki tarafındaki ifadeler değerlendirilir ve elde edilen değerler `>=` karşılaştırma işleci kullanılarak karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="b2717-112">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="b2717-113">Sol taraftaki ifadenin değeri sağdaki ifadenin değerinden büyükse veya eşitse, tüm ifade olarak değerlendirilir `True` ; Aksi takdirde, olarak değerlendirilir `False` .</span><span class="sxs-lookup"><span data-stu-id="b2717-113">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="b2717-114">Değerleri karşılaştıran ifadeler `If...Then` , aşağıdaki örnekte olduğu gibi en yaygın olarak kurulumlarını ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2717-114">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="b2717-115">İşaret, bir `=` karşılaştırma operatörünün yanı sıra bir atama işleçtir.</span><span class="sxs-lookup"><span data-stu-id="b2717-115">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="b2717-116">Karşılaştırma işleci olarak kullanıldığında, aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değere eşit olup olmadığını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b2717-116">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="b2717-117">Bir karşılaştırma ifadesini, bir `Boolean` `If` ,, veya deyiminde, ya da bir `While` `Loop` `ElseIf` değişkene atama ya da bir değere geçirilerek olduğu `Boolean` gibi her yerde bir değer gerekli olduğunda da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2717-117">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="b2717-118">Aşağıdaki örnekte, karşılaştırma ifadesinin döndürdüğü değer bir `Boolean` değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="b2717-118">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="b2717-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2717-119">See also</span></span>

- [<span data-ttu-id="b2717-120">Boole Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b2717-120">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="b2717-121">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="b2717-121">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="b2717-122">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b2717-122">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="b2717-123">Nasıl yapılır: Sayısal Değerleri Hesaplama</span><span class="sxs-lookup"><span data-stu-id="b2717-123">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="b2717-124">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="b2717-124">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
