---
title: 'Nasıl yapılır: (Visual Basic) sayısal değerleri hesaplama'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 7bbc3bcadb318203688a3b8ecae18e723e82c8ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560760"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="6bfaf-102">Nasıl yapılır: (Visual Basic) sayısal değerleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="6bfaf-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="6bfaf-103">Sayısal değerlerin sayısal ifadeler kullanarak hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="6bfaf-104">A *sayısal ifadenin* değişmez değerleri, sabitleri ve değişkenleri temsil eden sayısal değerleri içeren ifade ve bu değerleri üzerinde işlem işleçleri.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="6bfaf-105">Sayısal değerlerini hesaplama</span><span class="sxs-lookup"><span data-stu-id="6bfaf-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="6bfaf-106">Bir sayısal değer hesaplamak için</span><span class="sxs-lookup"><span data-stu-id="6bfaf-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="6bfaf-107">Bir veya daha fazla sayısal değişmez değerleri, sabitleri ve değişkenleri sayısal bir ifadenin birleştirin.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="6bfaf-108">Aşağıdaki örnek, bazı geçerli bir sayısal ifadeye gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="6bfaf-109">Bir sabit değer, bir sabit ve değişken ilk üç satırını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="6bfaf-110">Her biri geçerli bir sayısal ifade tek başına oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="6bfaf-111">Son satırı bir değişken iki değişmez değerleri ile birlikte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="6bfaf-112">Sayısal bir ifadenin tam bir Visual Basic ifade tek başına form değil olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="6bfaf-113">Tam bir deyim bir parçası olarak ifade kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="6bfaf-114">Sayısal bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="6bfaf-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="6bfaf-115">Aşağıdaki örnekte de gösterildiği gibi bir değişken için bir sayısal ifade tarafından temsil edilen değeri atamak, atama deyiminin kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     <span data-ttu-id="6bfaf-116">Yukarıdaki örnekte, eşit işlecin sağ tarafındaki ifadenin değerine (`=`) değişkenine atanan `j` işlecinin sol tarafındaki şekilde `j` için 276 değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="6bfaf-117">Daha fazla bilgi için [deyimleri](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bfaf-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="6bfaf-118">Birden çok işleç</span><span class="sxs-lookup"><span data-stu-id="6bfaf-118">Multiple Operators</span></span>  
 <span data-ttu-id="6bfaf-119">Sayısal ifade birden fazla işleci içeriyorsa, bunlar değerlendirilme sırası İşleç önceliği kuralları tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="6bfaf-120">İşleç önceliği kurallarına geçersiz kılmak için yukarıdaki örnekte olduğu gibi parantez içinde ifadeleri alın. Kapalı ifadeleri, ilk olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="6bfaf-121">Normal İşleç önceliği geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="6bfaf-121">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="6bfaf-122">İlk gerçekleştirmek istediğiniz işlemleri kapsamak için ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="6bfaf-123">Aşağıdaki örnek, iki farklı sonuçlar aynı işleçler ve işlenenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     <span data-ttu-id="6bfaf-124">Yukarıdaki örnekte, hesaplama için `j` toplama işlecini gerçekleştirir (`+`) ilk çünkü parantezler `(67 + i)` atanan değer ve normal öncelik geçersiz kılma `j` 276 (4 kez 69) olan.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="6bfaf-125">Hesaplama için `k` içinde normal öncelik işleçleri gerçekleştirir (`*` önce `+`) ve atanan değer `k` 270 (268 artı 2) olan.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="6bfaf-126">Daha fazla bilgi için [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="6bfaf-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bfaf-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bfaf-127">See also</span></span>
- [<span data-ttu-id="6bfaf-128">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="6bfaf-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="6bfaf-129">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="6bfaf-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="6bfaf-130">Deyimler</span><span class="sxs-lookup"><span data-stu-id="6bfaf-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="6bfaf-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="6bfaf-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6bfaf-132">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="6bfaf-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="6bfaf-133">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="6bfaf-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
