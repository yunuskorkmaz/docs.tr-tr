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
ms.openlocfilehash: dcf52c6200193f81070f323c8037ad82d747942d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403439"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="41dcd-102">Visual Basic'de İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="41dcd-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="41dcd-103">*İşleç* , değerleri tutan bir veya daha fazla kod öğesi üzerinde bir işlem gerçekleştiren bir kod öğesidir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="41dcd-104">Değer öğeleri arasında değişkenler, sabitler, sabit değerler, özellikler, dönüş `Function` ve `Operator` yordamlar ve ifadeler bulunur.</span><span class="sxs-lookup"><span data-stu-id="41dcd-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="41dcd-105">*İfade* , yeni bir değer veren işleçlerle birleştirilmiş bir değer öğeleri dizisidir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="41dcd-106">İşleçler, hesaplamalar, karşılaştırmalar veya diğer işlemleri gerçekleştirerek değer öğelerine davranır.</span><span class="sxs-lookup"><span data-stu-id="41dcd-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="41dcd-107">Işleç türleri</span><span class="sxs-lookup"><span data-stu-id="41dcd-107">Types of Operators</span></span>  
 <span data-ttu-id="41dcd-108">Visual Basic aşağıdaki işleç türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="41dcd-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="41dcd-109">[Aritmetik işleçler](arithmetic-operators.md) , bit desenlerini kaydırma da dahil olmak üzere sayısal değerlerde tanıdık hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-109">[Arithmetic Operators](arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="41dcd-110">[Karşılaştırma işleçleri](comparison-operators.md) iki ifadeyi karşılaştırır ve `Boolean` karşılaştırmanın sonucunu temsil eden bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="41dcd-110">[Comparison Operators](comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="41dcd-111">[Birleştirme işleçleri](concatenation-operators.md) birden çok dizeyi tek bir dizeye birleştirir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-111">[Concatenation Operators](concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="41dcd-112">[Visual Basic birleştiren mantıksal ve bit düzeyinde işleçler](logical-and-bitwise-operators.md) `Boolean` ve değerler ile aynı veri türünde bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="41dcd-112">[Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="41dcd-113">Bir işleçle birleştirilmiş değer öğelerine, bu işlecin *işlenenleri* adı verilir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="41dcd-114">İşleç, bir *deyimi*oluşturan atama işleci dışında, değer öğeleri form ifadeleriyle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="41dcd-115">Daha fazla bilgi için bkz. [deyimler](../statements.md).</span><span class="sxs-lookup"><span data-stu-id="41dcd-115">For more information, see [Statements](../statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="41dcd-116">Ifadelerin değerlendirmesi</span><span class="sxs-lookup"><span data-stu-id="41dcd-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="41dcd-117">Bir ifadenin nihai sonucu, genellikle,, veya sayısal bir tür gibi tanıdık bir veri türü olan bir değeri temsil eder `Boolean` `String` .</span><span class="sxs-lookup"><span data-stu-id="41dcd-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="41dcd-118">Aşağıda ifade örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="41dcd-119">Aşağıdaki örnekte gösterildiği gibi, birkaç işleç tek bir ifadede veya deyimde eylemler gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="41dcd-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="41dcd-120">Yukarıdaki örnekte, Visual Basic atama işlecinin () sağ tarafındaki ifadedeki işlemleri gerçekleştirir `=` , ardından sonuç değerini soldaki değişkene atar `x` .</span><span class="sxs-lookup"><span data-stu-id="41dcd-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="41dcd-121">Bir ifadede birleştirilebilecek işleç sayısında pratik bir sınır yoktur, ancak istediğiniz sonuçları aldığınızdan emin olmak için [Visual Basic operatör önceliğin](../../../language-reference/operators/operator-precedence.md) anlaşılmasına gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="41dcd-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="41dcd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41dcd-122">See also</span></span>

- [<span data-ttu-id="41dcd-123">İşleçler</span><span class="sxs-lookup"><span data-stu-id="41dcd-123">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="41dcd-124">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="41dcd-124">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="41dcd-125">Deyimler</span><span class="sxs-lookup"><span data-stu-id="41dcd-125">Statements</span></span>](../../../language-reference/statements/index.md)
