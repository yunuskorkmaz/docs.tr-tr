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
ms.openlocfilehash: 5ebc5f9dbf674a9a6560bd96b3e8c9edcae08a81
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701076"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="2cb85-102">Not İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cb85-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="2cb85-103">@No__t-0 ifadesinde mantıksal Olumsuzlaştırma veya sayısal bir ifadede bit tabanlı Olumsuzlaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cb85-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2cb85-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2cb85-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="2cb85-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2cb85-106">Required.</span></span> <span data-ttu-id="2cb85-107">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="2cb85-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="2cb85-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2cb85-108">Required.</span></span> <span data-ttu-id="2cb85-109">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="2cb85-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb85-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cb85-110">Remarks</span></span>  
 <span data-ttu-id="2cb85-111">@No__t-0 ifadeleri için aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="2cb85-112">@No__t-0 ise</span><span class="sxs-lookup"><span data-stu-id="2cb85-112">If `expression` is</span></span>|<span data-ttu-id="2cb85-113">@No__t-0 değeri</span><span class="sxs-lookup"><span data-stu-id="2cb85-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="2cb85-114">Sayısal ifadeler için `Not` işleci herhangi bir sayısal ifadenin bit değerlerini tersine çevirir ve aşağıdaki tabloya göre `result` ' de karşılık gelen biti ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2cb85-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="2cb85-115">Bit `expression` ise</span><span class="sxs-lookup"><span data-stu-id="2cb85-115">If bit in `expression` is</span></span>|<span data-ttu-id="2cb85-116">@No__t-0 ' daki bit</span><span class="sxs-lookup"><span data-stu-id="2cb85-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="2cb85-117">1\.</span><span class="sxs-lookup"><span data-stu-id="2cb85-117">1</span></span>|<span data-ttu-id="2cb85-118">0</span><span class="sxs-lookup"><span data-stu-id="2cb85-118">0</span></span>|  
|<span data-ttu-id="2cb85-119">0</span><span class="sxs-lookup"><span data-stu-id="2cb85-119">0</span></span>|<span data-ttu-id="2cb85-120">1\.</span><span class="sxs-lookup"><span data-stu-id="2cb85-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2cb85-121">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="2cb85-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="2cb85-122">Data Types</span></span>  
 <span data-ttu-id="2cb85-123">Boolean Olumsuzlaştırma için sonucun veri türü `Boolean` ' dır.</span><span class="sxs-lookup"><span data-stu-id="2cb85-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="2cb85-124">Bit düzeyinde olumsuzlama için, sonuç veri türü `expression` ' y i ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2cb85-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="2cb85-125">Ancak, ifade `Decimal` ise sonuç `Long` ' dir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2cb85-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="2cb85-126">Overloading</span></span>  
 <span data-ttu-id="2cb85-127">@No__t-0 işleci *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="2cb85-128">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2cb85-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2cb85-129">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2cb85-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb85-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cb85-130">Example</span></span>  
 <span data-ttu-id="2cb85-131">Aşağıdaki örnek, bir `Boolean` ifadesinde mantıksal olumsuzlama gerçekleştirmek için `Not` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cb85-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="2cb85-132">Sonuç, ifadenin değerinin ters çevirmeyi temsil eden bir `Boolean` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="2cb85-133">Yukarıdaki örnek sırasıyla `False` ve `True` sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb85-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cb85-134">Example</span></span>  
 <span data-ttu-id="2cb85-135">Aşağıdaki örnek, sayısal bir ifadenin ayrı bitlerini mantıksal olarak gerçekleştirmek için `Not` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cb85-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="2cb85-136">Sonuç deseninin biti, işaret biti dahil olmak üzere işlenen deseninin karşılık gelen bitin ters olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2cb85-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="2cb85-137">Yukarıdaki örnek sırasıyla – 11, – 9 ve – 7 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="2cb85-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb85-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cb85-138">See also</span></span>

- [<span data-ttu-id="2cb85-139">Mantıksal/bit düzeyinde Işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cb85-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="2cb85-140">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="2cb85-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="2cb85-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="2cb85-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="2cb85-142">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="2cb85-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
