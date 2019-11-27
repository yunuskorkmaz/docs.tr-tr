---
title: 'Nasıl yapılır: Sayısal Değerleri Hesaplama'
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
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348961"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="bd2dd-102">Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd2dd-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="bd2dd-103">Sayısal değerleri sayısal ifadeler kullanılarak hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="bd2dd-104">*Sayısal bir ifade* , sayısal değerleri temsil eden sabit değerler, sabitler ve değişkenleri ve bu değerler üzerinde işlem yapan işleçleri içeren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="bd2dd-105">Sayısal değerleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="bd2dd-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="bd2dd-106">Sayısal bir değer hesaplamak için</span><span class="sxs-lookup"><span data-stu-id="bd2dd-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="bd2dd-107">Bir veya daha fazla sayısal sabit değer, sabitler ve değişkenleri sayısal bir ifadede birleştirin.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="bd2dd-108">Aşağıdaki örnekte bazı geçerli sayısal ifadeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="bd2dd-109">İlk üç satır bir sabit değer, bir sabit ve bir değişken gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="bd2dd-110">Her biri kendi kendine geçerli bir sayısal ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="bd2dd-111">Son satır iki değişmez değer içeren bir değişkenin birleşimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="bd2dd-112">Sayısal bir ifadenin kendi başına bir Visual Basic deyimi oluşturmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="bd2dd-113">Deyimi, tüm deyimin bir parçası olarak kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="bd2dd-114">Sayısal bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="bd2dd-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="bd2dd-115">Aşağıdaki örnekte gösterildiği gibi, sayısal bir ifade ile temsil edilen değeri bir değişkene atamak için bir atama deyimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="bd2dd-116">Önceki örnekte, eşittir işlecinin (`=`) sağ tarafındaki ifadenin değeri, işlecin sol tarafındaki `j` değişkenine atanır, bu nedenle `j` 276 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="bd2dd-117">Daha fazla bilgi için bkz. [deyimler](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="bd2dd-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="bd2dd-118">Birden çok Işleç</span><span class="sxs-lookup"><span data-stu-id="bd2dd-118">Multiple Operators</span></span>  
 <span data-ttu-id="bd2dd-119">Sayısal ifade birden fazla işleç içeriyorsa, değerlendirildikleri sıra, işleç önceliği kurallarına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="bd2dd-120">İşleç önceliği kurallarını geçersiz kılmak için, ifadeleri Yukarıdaki örnekte olduğu gibi parantez içine almalısınız; içine alınan ifadeler önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="bd2dd-121">Normal operatör önceliğini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="bd2dd-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="bd2dd-122">Önce gerçekleştirilmesini istediğiniz işlemleri kapsamak için ayraçları kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="bd2dd-123">Aşağıdaki örnekte, aynı işlenen ve işleçlere sahip iki farklı sonuç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="bd2dd-124">Yukarıdaki örnekte, `j` için hesaplama, normal önceliği geçersiz kıldığından ve `j` atanan değer 276 (4 kez 69) `(67 + i)` olduğundan, önce ekleme işlecini (`+`) uygular.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="bd2dd-125">`k` hesaplama, işleçleri normal önceliğinde (`+`önce`*`) gerçekleştirir ve `k` atanan değer 270 (268 Plus 2) olur.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="bd2dd-126">Daha fazla bilgi için [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2dd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd2dd-127">See also</span></span>

- [<span data-ttu-id="bd2dd-128">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="bd2dd-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="bd2dd-129">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="bd2dd-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="bd2dd-130">Deyimler</span><span class="sxs-lookup"><span data-stu-id="bd2dd-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="bd2dd-131">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="bd2dd-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bd2dd-132">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="bd2dd-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="bd2dd-133">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="bd2dd-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
