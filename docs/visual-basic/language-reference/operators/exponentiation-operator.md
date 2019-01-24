---
title: ^ İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 2fb52a57a9d96f93c31ab1419e81e7f05967f831
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659728"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bfbb5-102">^ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfbb5-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="bfbb5-103">Bir sayıyı diğer bir sayının başlatır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfbb5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfbb5-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="bfbb5-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bfbb5-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="bfbb5-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-106">Required.</span></span> <span data-ttu-id="bfbb5-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="bfbb5-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-108">Required.</span></span> <span data-ttu-id="bfbb5-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="bfbb5-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="bfbb5-110">Result</span></span>  
 <span data-ttu-id="bfbb5-111">Sonuç `number` üssünü `exponent`, her zaman olarak bir `Double` değeri.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="bfbb5-112">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="bfbb5-112">Supported Types</span></span>  
 <span data-ttu-id="bfbb5-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-113">`Double`.</span></span> <span data-ttu-id="bfbb5-114">Tüm farklı türündeki işlenenler için dönüştürülür `Double`.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfbb5-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfbb5-115">Remarks</span></span>  
 <span data-ttu-id="bfbb5-116">Visual Basic içinde üs her zaman gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="bfbb5-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="bfbb5-117">Değerini `exponent` kesir olabilir negatif veya her ikisini de.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="bfbb5-118">Tek bir deyimde birden fazla üs gerçekleştirildiğinde `^` işleci soldan sağa karşılaşılanaa olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfbb5-119">`^` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bfbb5-120">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bfbb5-121">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bfbb5-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfbb5-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfbb5-122">Example</span></span>  
 <span data-ttu-id="bfbb5-123">Aşağıdaki örnekte `^` birkaç üs değerini artırmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="bfbb5-124">İkinci üssü birinci işlenenin sonucudur.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="bfbb5-125">Yukarıdaki örnekte, aşağıdaki sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="bfbb5-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="bfbb5-126">`exp1` (2 kare) 4'e ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="bfbb5-127">`exp2` (3 üssüne, ardından bu değeri üssüne) 19683 için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="bfbb5-128">`exp3` -125 (üssüne -5) için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="bfbb5-129">`exp4` 625'in (Dördüncü gücüne -5) ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="bfbb5-130">`exp5` 2 (8 kökünde küpü)'ye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="bfbb5-131">`exp6` 0,5 (8'in küpü kök tarafından ayrılmış 1.0) ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="bfbb5-132">Önceki örnekte ifadelerde parantezler önemini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="bfbb5-133">Nedeniyle *İşleç önceliği*, Visual Basic normalde gerçekleştirir `^` işlecinden önce diğer tüm abonelikler, hatta birli `–` işleci.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="bfbb5-134">Varsa `exp4` ve `exp6` parantez olmadan, bunlar üretilen aşağıdaki sonuçları hesaplanmadığını:</span><span class="sxs-lookup"><span data-stu-id="bfbb5-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="bfbb5-135">`exp4 = -5 ^ 4` (5 – olarak dördüncü güç), hesaplanacaktı-625 içinde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="bfbb5-136">`exp6 = 8 ^ -1.0 / 3.0` (8 – 1 güç veya 0,125) olarak hesaplanacaktı 0.041666666666666666666666666666667 içinde oluşacak 3.0, bölü.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfbb5-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfbb5-137">See also</span></span>
- [<span data-ttu-id="bfbb5-138">^= İşleci</span><span class="sxs-lookup"><span data-stu-id="bfbb5-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="bfbb5-139">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="bfbb5-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="bfbb5-140">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="bfbb5-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bfbb5-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="bfbb5-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="bfbb5-142">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="bfbb5-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
