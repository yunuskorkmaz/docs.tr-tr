---
title: Visual Basic'de İşleçler ve İfadeler
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dae47988e27ed4b1a714943ce1fbffe3b815066b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="83568-102">Visual Basic'de İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="83568-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="83568-103">Bir *işleci* değerlerini tutan bir veya daha fazla kod öğeleri üzerinde bir işlemi gerçekleştiren bir kod öğedir.</span><span class="sxs-lookup"><span data-stu-id="83568-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="83568-104">Değer öğeleri dahil değişkenlerinin, sabitleri, değişmez değerleri, özellikler, döndürür `Function` ve `Operator` yordamları ve ifadeler.</span><span class="sxs-lookup"><span data-stu-id="83568-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="83568-105">Bir *ifade* yeni bir değer veren bir dizi işleçleri ile birleştirilmiş değer öğeleri.</span><span class="sxs-lookup"><span data-stu-id="83568-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="83568-106">İşleçler hesaplamalar, karşılaştırmaları veya diğer işlemleri gerçekleştirerek değeri öğeleri görür.</span><span class="sxs-lookup"><span data-stu-id="83568-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="83568-107">İşleçler türleri</span><span class="sxs-lookup"><span data-stu-id="83568-107">Types of Operators</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="83568-108">Aşağıdaki işleçleri türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="83568-108"> provides the following types of operators:</span></span>  
  
-   <span data-ttu-id="83568-109">[Aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) bunların bit şekillerine kaydırma dahil olmak üzere sayısal değerleri tanıdık hesaplamalar.</span><span class="sxs-lookup"><span data-stu-id="83568-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
-   <span data-ttu-id="83568-110">[Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) iki ifadeye karşılaştırır ve dönüş bir `Boolean` karşılaştırma sonucunu temsil eden değer.</span><span class="sxs-lookup"><span data-stu-id="83568-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
-   <span data-ttu-id="83568-111">[Birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) tek bir dize halinde birden çok dizeyi birleştirme.</span><span class="sxs-lookup"><span data-stu-id="83568-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
-   <span data-ttu-id="83568-112">[Mantıksal ve bit düzeyinde işleçler Visual Basic'te](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) birleştirmek `Boolean` veya sayısal değerler ve değerlerin aynı veri türünde bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="83568-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="83568-113">Bir operatör ile birleştirilmiş değer öğeleri adlı *işlenenler* bu işleç.</span><span class="sxs-lookup"><span data-stu-id="83568-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="83568-114">İşleçler atama işleci dışında değer öğeleri form ifadeleri hangi formların birlikte bir *deyimi*.</span><span class="sxs-lookup"><span data-stu-id="83568-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="83568-115">Daha fazla bilgi için bkz: [deyimleri](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="83568-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="83568-116">İfade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="83568-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="83568-117">Sonuç ifade genellikle tanıdık veri türü gibi bir değeri temsil eder `Boolean`, `String`, veya sayısal bir tür.</span><span class="sxs-lookup"><span data-stu-id="83568-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="83568-118">İfadeleri örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="83568-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="83568-119">Aşağıdaki örnekte gösterildiği gibi çeşitli işleçler bir tek ifadesi veya deyimi, eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83568-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 <span data-ttu-id="83568-120">Önceki örnekte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] atama işlecinin sağ tarafındaki ifade işlemleri gerçekleştirir (`=`), ardından sonuç değeri değişkenine atar `x` soldaki.</span><span class="sxs-lookup"><span data-stu-id="83568-120">In the preceding example, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="83568-121">Bir ifade, ancak bir anlayış birleştirilebilir işleçleri sayısına pratik bir sınır yoktur [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md) beklediğiniz sonuçları aldığından emin olmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="83568-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  
  
 <span data-ttu-id="83568-122">Daha fazla bilgi ve örnekler için bkz: [İşleç aşırı yüklemesi Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="83568-122">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83568-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83568-123">See Also</span></span>  
 [<span data-ttu-id="83568-124">İşleçler</span><span class="sxs-lookup"><span data-stu-id="83568-124">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)  
 [<span data-ttu-id="83568-125">İşleçlerin etkili bileşimi</span><span class="sxs-lookup"><span data-stu-id="83568-125">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [<span data-ttu-id="83568-126">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="83568-126">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
