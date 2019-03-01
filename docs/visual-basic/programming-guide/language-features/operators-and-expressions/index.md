---
title: Visual Basic'de İşleçler ve İfadeler
ms.date: 07/20/2015
helpviewer_keywords:
  - 'operators [Visual Basic], operands'
  - 'operators [Visual Basic]'
  - 'operands [Visual Basic], definition'
  - 'Visual Basic code, operators'
  - 'Visual Basic code, expressions'
  - operands
  - 'expressions [Visual Basic]'
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="5b735-102">Visual Basic'de İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="5b735-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="5b735-103">Bir *işleci* değerlerini tutan bir veya daha fazla kod öğeleri üzerinde bir işlem gerçekleştiren bir kod öğedir.</span><span class="sxs-lookup"><span data-stu-id="5b735-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="5b735-104">Değişkenleri, sabitleri, sabit değerleri, özellikleri, değeri öğeleri dahil döndürür `Function` ve `Operator` yordamları ve ifadeler.</span><span class="sxs-lookup"><span data-stu-id="5b735-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="5b735-105">Bir *ifade* yeni bir değer veren bir dizi değeri öğeleri işleçleri ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="5b735-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="5b735-106">İşleçler, değeri öğeleri üzerinde hesaplamalar, karşılaştırmaları veya diğer işlemleri gerçekleştirerek işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="5b735-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="5b735-107">Tür işleç</span><span class="sxs-lookup"><span data-stu-id="5b735-107">Types of Operators</span></span>  
 <span data-ttu-id="5b735-108">Visual Basic işleçleri aşağıdaki türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="5b735-108">Visual Basic provides the following types of operators:</span></span>  
  
-   <span data-ttu-id="5b735-109">[Aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) , bit düzenleri kaydırma gibi sayısal değerleri üzerinde tanıdık hesaplamalar.</span><span class="sxs-lookup"><span data-stu-id="5b735-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
-   <span data-ttu-id="5b735-110">[Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) iki ifadeden karşılaştırın ve dönüş bir `Boolean` Karşılaştırmanın sonucu temsil eden değer.</span><span class="sxs-lookup"><span data-stu-id="5b735-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
-   <span data-ttu-id="5b735-111">[Birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) tek bir dize olarak birden çok dizeyi birleştirme.</span><span class="sxs-lookup"><span data-stu-id="5b735-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
-   <span data-ttu-id="5b735-112">[Mantıksal ve bit düzeyinde işleçler Visual Basic'te](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) birleştirmek `Boolean` veya sayısal değerler ve değerlerin aynı veri türünde bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b735-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="5b735-113">Operatör ile birleştirilmiş değer öğeleri adlı *işlenenler* bu işleci.</span><span class="sxs-lookup"><span data-stu-id="5b735-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="5b735-114">İşleçleri birleşik atama işleci hariç değer öğeleri form ifadeleri ile hangi formların bir *deyimi*.</span><span class="sxs-lookup"><span data-stu-id="5b735-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="5b735-115">Daha fazla bilgi için [deyimleri](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="5b735-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="5b735-116">İfade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="5b735-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="5b735-117">Bir ifadenin sonuç genellikle tanıdık veri türünde olduğu gibi bir değeri temsil eder `Boolean`, `String`, veya bir sayısal tür.</span><span class="sxs-lookup"><span data-stu-id="5b735-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="5b735-118">Örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b735-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="5b735-119">Aşağıdaki örnekte gösterildiği gibi birkaç işleç bir tek ifadesi veya deyimi, eylemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b735-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="5b735-120">Önceki örnekte, Visual Basic ifade işlemlerinde atama işlecinin sağ tarafında gerçekleştirir (`=`), ardından sonuç değerini değişkenine atar `x` soldaki.</span><span class="sxs-lookup"><span data-stu-id="5b735-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="5b735-121">Bir ifade ancak bir anlayış birleştirilebilir işleçleri dizi pratik bir sınır yoktur [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md) beklediğiniz sonuçları aldığınızdan emin olmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5b735-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="5b735-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b735-122">See also</span></span>
- [<span data-ttu-id="5b735-123">İşleçler</span><span class="sxs-lookup"><span data-stu-id="5b735-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="5b735-124">İşleçlerin Etkili Bileşimi</span><span class="sxs-lookup"><span data-stu-id="5b735-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="5b735-125">Deyimler</span><span class="sxs-lookup"><span data-stu-id="5b735-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
