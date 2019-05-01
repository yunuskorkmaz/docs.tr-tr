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
ms.openlocfilehash: 4e54fdca9123ad5595eb9a8c5e2ac5bc303a8f6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936623"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="190cd-102">Not İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="190cd-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="190cd-103">Mantıksal değilleme gerçekleştiren bir `Boolean` ifadesi veya sayısal bir ifadenin bit tabanlı değil işlecini uygular.</span><span class="sxs-lookup"><span data-stu-id="190cd-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="190cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="190cd-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="190cd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="190cd-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="190cd-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="190cd-106">Required.</span></span> <span data-ttu-id="190cd-107">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="190cd-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="190cd-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="190cd-108">Required.</span></span> <span data-ttu-id="190cd-109">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="190cd-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="190cd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="190cd-110">Remarks</span></span>  
 <span data-ttu-id="190cd-111">İçin `Boolean` ifadeleri, aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="190cd-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="190cd-112">Varsa `expression` olduğu</span><span class="sxs-lookup"><span data-stu-id="190cd-112">If `expression` is</span></span>|<span data-ttu-id="190cd-113">Değerini `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="190cd-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="190cd-114">Sayısal ifadeler için `Not` işleci herhangi bir sayısal ifadeye bit değerleri tersine çevirir ve karşılık gelen, bit ayarlar `result` aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="190cd-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="190cd-115">Varsa, bit `expression` olduğu</span><span class="sxs-lookup"><span data-stu-id="190cd-115">If bit in `expression` is</span></span>|<span data-ttu-id="190cd-116">Bit `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="190cd-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="190cd-117">1.</span><span class="sxs-lookup"><span data-stu-id="190cd-117">1</span></span>|<span data-ttu-id="190cd-118">0</span><span class="sxs-lookup"><span data-stu-id="190cd-118">0</span></span>|  
|<span data-ttu-id="190cd-119">0</span><span class="sxs-lookup"><span data-stu-id="190cd-119">0</span></span>|<span data-ttu-id="190cd-120">1.</span><span class="sxs-lookup"><span data-stu-id="190cd-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="190cd-121">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçler düşük önceliğe sahip olduğundan, herhangi bir bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="190cd-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="190cd-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="190cd-122">Data Types</span></span>  
 <span data-ttu-id="190cd-123">Bir mantıksal olumsuzlama için sonuç verileri türüdür `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="190cd-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="190cd-124">Bit tabanlı değil işlecini için sonuç veri türü, aynı olduğu `expression`.</span><span class="sxs-lookup"><span data-stu-id="190cd-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="190cd-125">Ancak, ifade ise `Decimal`, sonuç `Long`.</span><span class="sxs-lookup"><span data-stu-id="190cd-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="190cd-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="190cd-126">Overloading</span></span>  
 <span data-ttu-id="190cd-127">`Not` İşleci olabilir *aşırı*, kendi işleneninin türü, sınıfın veya yapının olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="190cd-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="190cd-128">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="190cd-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="190cd-129">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="190cd-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="190cd-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="190cd-130">Example</span></span>  
 <span data-ttu-id="190cd-131">Aşağıdaki örnekte `Not` gerçekleştirmeniz mantıksal olumsuzlama işleci bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="190cd-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="190cd-132">Sonuç bir `Boolean` ifade değerinin ters gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="190cd-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="190cd-133">Yukarıdaki örnekte sonuçlarını üretir `False` ve `True`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="190cd-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="190cd-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="190cd-134">Example</span></span>  
 <span data-ttu-id="190cd-135">Aşağıdaki örnekte `Not` mantıksal olumsuzlaştırma tek bit sayısal ifadenin için işleci.</span><span class="sxs-lookup"><span data-stu-id="190cd-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="190cd-136">Karşılık gelen bit imza biti dahil işlenen deseninde, geriye doğru sonuç deseninde bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="190cd-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="190cd-137">Yukarıdaki örnekte sırasıyla –11 –9 ve –7, sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="190cd-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190cd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="190cd-138">See also</span></span>

- [<span data-ttu-id="190cd-139">Mantıksal/bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="190cd-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="190cd-140">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="190cd-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="190cd-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="190cd-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="190cd-142">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="190cd-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
