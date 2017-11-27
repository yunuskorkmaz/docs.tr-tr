---
title: "^ İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="409a7-102">^ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="409a7-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="409a7-103">Bir sayıyı diğer bir sayının kuvvetine yükseltir.</span><span class="sxs-lookup"><span data-stu-id="409a7-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="409a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="409a7-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="409a7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="409a7-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="409a7-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="409a7-106">Required.</span></span> <span data-ttu-id="409a7-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="409a7-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="409a7-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="409a7-108">Required.</span></span> <span data-ttu-id="409a7-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="409a7-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="409a7-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="409a7-110">Result</span></span>  
 <span data-ttu-id="409a7-111">Sonuç `number` üssünü `exponent`, her zaman olarak bir `Double` değeri.</span><span class="sxs-lookup"><span data-stu-id="409a7-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="409a7-112">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="409a7-112">Supported Types</span></span>  
 <span data-ttu-id="409a7-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="409a7-113">`Double`.</span></span> <span data-ttu-id="409a7-114">Tüm farklı türündeki işlenenler için dönüştürülür `Double`.</span><span class="sxs-lookup"><span data-stu-id="409a7-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="409a7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="409a7-115">Remarks</span></span>  
 <span data-ttu-id="409a7-116">Visual Basic her zaman içinde üs gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="409a7-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="409a7-117">Değeri `exponent` kesir olabilir negatif veya her ikisi de.</span><span class="sxs-lookup"><span data-stu-id="409a7-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="409a7-118">Tek bir deyimde birden fazla üs gerçekleştirildiğinde `^` işleci soldan sağa karşılaşılana olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="409a7-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="409a7-119">`^` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="409a7-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="409a7-120">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="409a7-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="409a7-121">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="409a7-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="409a7-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="409a7-122">Example</span></span>  
 <span data-ttu-id="409a7-123">Aşağıdaki örnek kullanır `^` işleci üs gücünü sayıya yükseltin.</span><span class="sxs-lookup"><span data-stu-id="409a7-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="409a7-124">İkinci üssünün ilk işlenen sonucudur.</span><span class="sxs-lookup"><span data-stu-id="409a7-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="409a7-125">Önceki örnekte aşağıdaki sonuçları verir:</span><span class="sxs-lookup"><span data-stu-id="409a7-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="409a7-126">`exp1`(2 kare) 4'e ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="409a7-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="409a7-127">`exp2`19683 (3 küpünü, ardından küpünü bu değere) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="409a7-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="409a7-128">`exp3`-125 (küpünü -5) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="409a7-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="409a7-129">`exp4`625'in (Dördüncü gücüne -5) ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="409a7-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="409a7-130">`exp5`2 (8 kökündeki küpü)'ye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="409a7-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="409a7-131">`exp6`0,5 (8 küp kök tarafından bölünmüş 1.0) ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="409a7-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="409a7-132">Önceki örnekte ifadelerde parantez önemini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="409a7-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="409a7-133">Nedeniyle *İşleç önceliği*, Visual Basic normalde gerçekleştirir `^` herhangi diğer önce işleci birli bile `–` işleci.</span><span class="sxs-lookup"><span data-stu-id="409a7-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="409a7-134">Varsa `exp4` ve `exp6` hesaplanan parantez olmadan, bunlar üretilen aşağıdaki sonuçları:</span><span class="sxs-lookup"><span data-stu-id="409a7-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="409a7-135">`exp4 = -5 ^ 4`(5 olarak – dördüncü güç), hesaplanan-625 içinde sonuçlanacak.</span><span class="sxs-lookup"><span data-stu-id="409a7-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="409a7-136">`exp6 = 8 ^ -1.0 / 3.0`(8 – 1 güç veya 0,125) olarak hesaplanır 0.041666666666666666666666666666667 içinde oluşturacağı 3.0 bölü.</span><span class="sxs-lookup"><span data-stu-id="409a7-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409a7-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="409a7-137">See Also</span></span>  
 [<span data-ttu-id="409a7-138">^ = İşleci</span><span class="sxs-lookup"><span data-stu-id="409a7-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="409a7-139">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="409a7-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="409a7-140">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="409a7-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="409a7-141">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="409a7-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="409a7-142">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="409a7-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
