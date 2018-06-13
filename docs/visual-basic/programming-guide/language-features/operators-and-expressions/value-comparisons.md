---
title: Değer Karşılaştırmaları (Visual Basic)
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
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649613"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="569c7-102">Değer Karşılaştırmaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="569c7-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="569c7-103">Karşılaştırma işleçleri sayısal değişkenlerin değerleri karşılaştırma ifadeleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="569c7-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="569c7-104">Bu deyimler dönüş bir `Boolean` değeri temel karşılaştırma doğru olup ya da yanlış.</span><span class="sxs-lookup"><span data-stu-id="569c7-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="569c7-105">Bu tür bir ifade örnekleri aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="569c7-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="569c7-106">İlk ifade değerlendiren `True`, 45 26 büyük olduğu için.</span><span class="sxs-lookup"><span data-stu-id="569c7-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="569c7-107">İkinci örnek değerlendiren `False`26 45 büyük olmadığından.</span><span class="sxs-lookup"><span data-stu-id="569c7-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="569c7-108">Bu şekilde sayısal ifadeler de karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="569c7-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="569c7-109">Karşılaştırma ifadeleri kendilerini aşağıdaki örnekteki gibi karmaşık ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="569c7-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="569c7-110">Önceki karmaşık ifade değişmez değerleri, değişkenler ve işlev çağrılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="569c7-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="569c7-111">Her iki tarafında ifadeleri karşılaştırma işlecinin değerlendirilir ve kullanılarak elde edilen değerleri karşılaştırılır `>=` karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="569c7-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="569c7-112">Sol tarafındaki ifade değerini değerinden daha büyük ya da için sağ taraftaki ifadenin değerine eşit, tüm ifadeyi hesaplar `True`; Aksi takdirde için değerlendirir `False`.</span><span class="sxs-lookup"><span data-stu-id="569c7-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="569c7-113">Değerleri karşılaştırma ifadeleri en sık kullanıldığı `If...Then` aşağıdaki örnekteki gibi kurulumlarını.</span><span class="sxs-lookup"><span data-stu-id="569c7-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 <span data-ttu-id="569c7-114">`=` İşaretidir atama işleci yanı sıra bir karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="569c7-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="569c7-115">Aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değerine eşit olup olmadığını bir karşılaştırma işleci kullanıldığında, değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="569c7-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 <span data-ttu-id="569c7-116">Bir karşılaştırma ifadesi yerde kullanabilir bir `Boolean` değerdir gerekli, gibi bir `If`, `While`, `Loop`, veya `ElseIf` deyimi, ya da atama veya bir değere geçirme bir `Boolean` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="569c7-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="569c7-117">Aşağıdaki örnekte, karşılaştırma ifadesi tarafından döndürülen değer atanmış bir `Boolean` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="569c7-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="569c7-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="569c7-118">See Also</span></span>  
 [<span data-ttu-id="569c7-119">Boole İfadeleri</span><span class="sxs-lookup"><span data-stu-id="569c7-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="569c7-120">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="569c7-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="569c7-121">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="569c7-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="569c7-122">Nasıl yapılır: Sayısal Değerleri Hesaplama</span><span class="sxs-lookup"><span data-stu-id="569c7-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="569c7-123">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="569c7-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
