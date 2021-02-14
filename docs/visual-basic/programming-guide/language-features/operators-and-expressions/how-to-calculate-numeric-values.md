---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sayısal değerleri hesaplama (Visual Basic)'
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
ms.openlocfilehash: 35acd7b9b1732514a8fe4399b6a815dce62b2468
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435596"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="868a3-103">Nasıl yapılır: Sayısal Değerleri Hesaplama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="868a3-103">How to: Calculate Numeric Values (Visual Basic)</span></span>

<span data-ttu-id="868a3-104">Sayısal değerleri sayısal ifadeler kullanılarak hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868a3-104">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="868a3-105">*Sayısal bir ifade* , sayısal değerleri temsil eden sabit değerler, sabitler ve değişkenleri ve bu değerler üzerinde işlem yapan işleçleri içeren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="868a3-105">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="868a3-106">Sayısal değerleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="868a3-106">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="868a3-107">Sayısal bir değer hesaplamak için</span><span class="sxs-lookup"><span data-stu-id="868a3-107">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="868a3-108">Bir veya daha fazla sayısal sabit değer, sabitler ve değişkenleri sayısal bir ifadede birleştirin.</span><span class="sxs-lookup"><span data-stu-id="868a3-108">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="868a3-109">Aşağıdaki örnekte bazı geçerli sayısal ifadeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="868a3-109">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="868a3-110">İlk üç satır bir sabit değer, bir sabit ve bir değişken gösterir.</span><span class="sxs-lookup"><span data-stu-id="868a3-110">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="868a3-111">Her biri kendi kendine geçerli bir sayısal ifade oluşturur.</span><span class="sxs-lookup"><span data-stu-id="868a3-111">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="868a3-112">Son satır iki değişmez değer içeren bir değişkenin birleşimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="868a3-112">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="868a3-113">Sayısal bir ifadenin kendi başına bir Visual Basic deyimi oluşturmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="868a3-113">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="868a3-114">Deyimi, tüm deyimin bir parçası olarak kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="868a3-114">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="868a3-115">Sayısal bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="868a3-115">To store a numeric value</span></span>  
  
- <span data-ttu-id="868a3-116">Aşağıdaki örnekte gösterildiği gibi, sayısal bir ifade ile temsil edilen değeri bir değişkene atamak için bir atama deyimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868a3-116">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="868a3-117">Önceki örnekte, eşittir işlecinin () sağ tarafındaki ifadenin değeri, `=` `j` işlecin sol tarafındaki değişkenine atanır, bu nedenle `j` 276 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="868a3-117">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="868a3-118">Daha fazla bilgi için bkz. [deyimler](../../../language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="868a3-118">For more information, see [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="868a3-119">Birden çok Işleç</span><span class="sxs-lookup"><span data-stu-id="868a3-119">Multiple Operators</span></span>  

 <span data-ttu-id="868a3-120">Sayısal ifade birden fazla işleç içeriyorsa, değerlendirildikleri sıra, işleç önceliği kurallarına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="868a3-120">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="868a3-121">İşleç önceliği kurallarını geçersiz kılmak için, ifadeleri Yukarıdaki örnekte olduğu gibi parantez içine almalısınız; içine alınan ifadeler önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="868a3-121">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="868a3-122">Normal operatör önceliğini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="868a3-122">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="868a3-123">Önce gerçekleştirilmesini istediğiniz işlemleri kapsamak için ayraçları kullanın.</span><span class="sxs-lookup"><span data-stu-id="868a3-123">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="868a3-124">Aşağıdaki örnekte, aynı işlenen ve işleçlere sahip iki farklı sonuç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="868a3-124">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="868a3-125">Önceki örnekte, için hesaplama, `j` ekleme işlecini () ilk olarak gerçekleştirir, `+` çünkü etrafındaki parantezler `(67 + i)` Normal önceliği geçersiz kılar ve şuna atanan değer `j` 276 ' dir (4 kez 69).</span><span class="sxs-lookup"><span data-stu-id="868a3-125">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="868a3-126">İçin hesaplama, `k` işleçleri normal önceliğinde ( `*` önce `+` ) gerçekleştirir ve atanan değer 270 ' `k` dir (268 Plus 2).</span><span class="sxs-lookup"><span data-stu-id="868a3-126">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="868a3-127">Daha fazla bilgi için [Visual Basic operatör önceliği](../../../language-reference/operators/operator-precedence.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="868a3-127">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868a3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="868a3-128">See also</span></span>

- [<span data-ttu-id="868a3-129">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="868a3-129">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="868a3-130">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="868a3-130">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="868a3-131">Deyimler</span><span class="sxs-lookup"><span data-stu-id="868a3-131">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="868a3-132">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="868a3-132">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="868a3-133">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="868a3-133">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="868a3-134">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="868a3-134">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
