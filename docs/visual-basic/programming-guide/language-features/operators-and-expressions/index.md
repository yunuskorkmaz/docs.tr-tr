---
title: İşleçler ve İfadeler
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: fa410a739be2da8802e76a35068448263ddec1fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343606"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="00b2f-102">Visual Basic'de İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="00b2f-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="00b2f-103">*İşleç* , değerleri tutan bir veya daha fazla kod öğesi üzerinde bir işlem gerçekleştiren bir kod öğesidir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="00b2f-104">Değer öğeleri arasında değişkenler, sabitler, sabit değerler, özellikler, `Function` ve `Operator` yordamlarından ve ifadelerden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="00b2f-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="00b2f-105">*İfade* , yeni bir değer veren işleçlerle birleştirilmiş bir değer öğeleri dizisidir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="00b2f-106">İşleçler, hesaplamalar, karşılaştırmalar veya diğer işlemleri gerçekleştirerek değer öğelerine davranır.</span><span class="sxs-lookup"><span data-stu-id="00b2f-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="00b2f-107">Işleç türleri</span><span class="sxs-lookup"><span data-stu-id="00b2f-107">Types of Operators</span></span>  
 <span data-ttu-id="00b2f-108">Visual Basic aşağıdaki işleç türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="00b2f-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="00b2f-109">[Aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) , bit desenlerini kaydırma da dahil olmak üzere sayısal değerlerde tanıdık hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="00b2f-110">[Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) iki ifadeyi karşılaştırır ve karşılaştırmanın sonucunu temsil eden bir `Boolean` değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="00b2f-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="00b2f-111">[Birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) birden çok dizeyi tek bir dizeye birleştirir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="00b2f-112">[Visual Basic mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) `Boolean` veya sayısal değerleri birleştirir ve değerlerle aynı veri türünün bir sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="00b2f-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="00b2f-113">Bir işleçle birleştirilmiş değer öğelerine, bu işlecin *işlenenleri* adı verilir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="00b2f-114">İşleç, bir *deyimi*oluşturan atama işleci dışında, değer öğeleri form ifadeleriyle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="00b2f-115">Daha fazla bilgi için bkz. [deyimler](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="00b2f-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="00b2f-116">Ifadelerin değerlendirmesi</span><span class="sxs-lookup"><span data-stu-id="00b2f-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="00b2f-117">Bir ifadenin nihai sonucu, genellikle `Boolean`, `String`veya sayısal bir tür gibi tanıdık bir veri türü olan bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00b2f-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="00b2f-118">Aşağıda ifade örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="00b2f-119">Aşağıdaki örnekte gösterildiği gibi, birkaç işleç tek bir ifadede veya deyimde eylemler gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="00b2f-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="00b2f-120">Yukarıdaki örnekte, Visual Basic atama işlecinin sağ tarafındaki ifadedeki işlemleri gerçekleştirir (`=`), ardından sonuç değerini soldaki değişkene `x` atar.</span><span class="sxs-lookup"><span data-stu-id="00b2f-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="00b2f-121">Bir ifadede birleştirilebilecek işleç sayısında pratik bir sınır yoktur, ancak istediğiniz sonuçları aldığınızdan emin olmak için [Visual Basic operatör önceliğin](../../../../visual-basic/language-reference/operators/operator-precedence.md) anlaşılmasına gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="00b2f-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="00b2f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00b2f-122">See also</span></span>

- [<span data-ttu-id="00b2f-123">işleçler</span><span class="sxs-lookup"><span data-stu-id="00b2f-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="00b2f-124">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="00b2f-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="00b2f-125">Deyimler</span><span class="sxs-lookup"><span data-stu-id="00b2f-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
