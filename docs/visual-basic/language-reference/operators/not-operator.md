---
title: Not İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 29e2b159e4c6261a62e788b537102b9b457fe0c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955831"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="0d3b8-102">Not İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d3b8-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="0d3b8-103">Bir `Boolean` ifadede mantıksal Olumsuzlaştırma veya sayısal ifadede bit tabanlı Olumsuzlaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d3b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d3b8-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0d3b8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0d3b8-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0d3b8-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-106">Required.</span></span> <span data-ttu-id="0d3b8-107">Herhangi `Boolean` bir veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="0d3b8-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-108">Required.</span></span> <span data-ttu-id="0d3b8-109">Herhangi `Boolean` bir veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d3b8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d3b8-110">Remarks</span></span>  
 <span data-ttu-id="0d3b8-111">İfadeler `Boolean` için aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0d3b8-112">`expression` İse</span><span class="sxs-lookup"><span data-stu-id="0d3b8-112">If `expression` is</span></span>|<span data-ttu-id="0d3b8-113">Öğesinin `result` değeri</span><span class="sxs-lookup"><span data-stu-id="0d3b8-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="0d3b8-114">Sayısal ifadeler `Not` için işleç, herhangi bir sayısal ifadenin bit değerlerini tersine çevirir ve karşılık gelen `result` biti aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="0d3b8-115">Eğer bit `expression` ise</span><span class="sxs-lookup"><span data-stu-id="0d3b8-115">If bit in `expression` is</span></span>|<span data-ttu-id="0d3b8-116">İçindeki `result` bit</span><span class="sxs-lookup"><span data-stu-id="0d3b8-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="0d3b8-117">1\.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-117">1</span></span>|<span data-ttu-id="0d3b8-118">0</span><span class="sxs-lookup"><span data-stu-id="0d3b8-118">0</span></span>|  
|<span data-ttu-id="0d3b8-119">0</span><span class="sxs-lookup"><span data-stu-id="0d3b8-119">0</span></span>|<span data-ttu-id="0d3b8-120">1\.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0d3b8-121">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="0d3b8-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="0d3b8-122">Data Types</span></span>  
 <span data-ttu-id="0d3b8-123">Boolean Olumsuzlaştırma için sonucun veri türü olur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="0d3b8-124">Bit düzeyinde olumsuzlama için sonuç veri türü, ile `expression`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="0d3b8-125">Ancak, ifadesi `Decimal`ise sonuç olur `Long`.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0d3b8-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="0d3b8-126">Overloading</span></span>  
 <span data-ttu-id="0d3b8-127">İşleç aşırı yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `Not`</span><span class="sxs-lookup"><span data-stu-id="0d3b8-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="0d3b8-128">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0d3b8-129">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0d3b8-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d3b8-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d3b8-130">Example</span></span>  
 <span data-ttu-id="0d3b8-131">Aşağıdaki örnek, bir `Not` `Boolean` ifadede mantıksal olumsuzlama gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="0d3b8-132">Sonuç, ifadenin değerinin `Boolean` ters çevrilme değerini temsil eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="0d3b8-133">Yukarıdaki örnek sırasıyla `False` ve `True`, sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d3b8-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d3b8-134">Example</span></span>  
 <span data-ttu-id="0d3b8-135">Aşağıdaki örnek, bir sayısal `Not` ifadenin ayrı bitlerinin mantıksal olumsuzunu gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="0d3b8-136">Sonuç deseninin biti, işaret biti dahil olmak üzere işlenen deseninin karşılık gelen bitin ters olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="0d3b8-137">Yukarıdaki örnek sırasıyla – 11, – 9 ve – 7 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d3b8-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d3b8-138">See also</span></span>

- [<span data-ttu-id="0d3b8-139">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d3b8-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="0d3b8-140">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="0d3b8-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0d3b8-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="0d3b8-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0d3b8-142">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="0d3b8-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
