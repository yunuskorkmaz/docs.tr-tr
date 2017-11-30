---
title: "Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="ce277-102">Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce277-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="ce277-103">Sayısal ifadeler kullanımıyla sayısal değerleri hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce277-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="ce277-104">A *sayısal ifade* değişmez değerleri, sabitleri ve değişkenleri sayısal değerleri temsil eden içeren bir ifade ve bu değerlere göre hareket işleçler.</span><span class="sxs-lookup"><span data-stu-id="ce277-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="ce277-105">Sayısal değerlerini hesaplama</span><span class="sxs-lookup"><span data-stu-id="ce277-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="ce277-106">Sayısal bir değeri hesaplamak için</span><span class="sxs-lookup"><span data-stu-id="ce277-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="ce277-107">Bir veya daha fazla sayısal değişmez değerleri, sabitleri ve değişkenleri bir sayısal ifadeye birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ce277-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="ce277-108">Aşağıdaki örnek, geçerli bazı sayısal ifadeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce277-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="ce277-109">İlk üç satırını bir hazır değer, bir sabit ve değişken gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce277-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="ce277-110">Her biri geçerli bir sayısal ifade tek başına oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce277-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="ce277-111">Son satırı iki değişmez değerleri sahip bir değişken bileşimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce277-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="ce277-112">Sayısal ifade tam bir form değil, Not [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deyimi kendisi tarafından.</span><span class="sxs-lookup"><span data-stu-id="ce277-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statement by itself.</span></span> <span data-ttu-id="ce277-113">Tam bir deyim bir parçası olarak ifade kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce277-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="ce277-114">Sayısal bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="ce277-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="ce277-115">Aşağıdaki örnekte gösterilmiştir gibi bir değişken için sayısal bir ifade tarafından temsil edilen değer atamak için bir atama deyimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce277-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     <span data-ttu-id="ce277-116">Önceki örnekte, eşit işlecinin sağ tarafında ifadesinin değerini (`=`) değişkenine atanan `j` işlecinin sol tarafındaki şekilde `j` 276 için değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="ce277-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="ce277-117">Daha fazla bilgi için bkz: [deyimleri](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce277-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="ce277-118">Birden çok işleç</span><span class="sxs-lookup"><span data-stu-id="ce277-118">Multiple Operators</span></span>  
 <span data-ttu-id="ce277-119">Sayısal ifade birden fazla işleci içeriyorsa, bunlar değerlendirilme sırasını İşleç önceliği kurallara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ce277-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="ce277-120">İşleç önceliği kuralları geçersiz kılmak için yukarıdaki örnekte olduğu gibi parantez içinde ifadeler alın; Kapalı ifadeleri önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ce277-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="ce277-121">Normal İşleç önceliği geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="ce277-121">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="ce277-122">İlk gerçekleştirilmesini istediğiniz işlemleri kapsamak için ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce277-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="ce277-123">Aşağıdaki örnek aynı işlenenler ve işleçleri ile iki farklı sonuçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ce277-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     <span data-ttu-id="ce277-124">Önceki örnekte, hesaplama için `j` Toplama işleci gerçekleştirir (`+`) ilk çünkü parantezler `(67 + i)` normal öncelik ve atanan değer geçersiz kılmak `j` 276 (4 kez 69) değil.</span><span class="sxs-lookup"><span data-stu-id="ce277-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="ce277-125">Hesaplama için `k` kendi normal öncelik işleçleri gerçekleştirir (`*` önce `+`) ve atanan değer `k` 270 (268 artı 2) değil.</span><span class="sxs-lookup"><span data-stu-id="ce277-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="ce277-126">Daha fazla bilgi için bkz: [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ce277-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce277-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce277-127">See Also</span></span>  
 [<span data-ttu-id="ce277-128">İşleçler ve ifadeler</span><span class="sxs-lookup"><span data-stu-id="ce277-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="ce277-129">Değer karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="ce277-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="ce277-130">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="ce277-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="ce277-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="ce277-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="ce277-132">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="ce277-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="ce277-133">İşleçlerin etkili bileşimi</span><span class="sxs-lookup"><span data-stu-id="ce277-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
