---
title: ^ İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 8cdfbec917608211e19c39eb37bd12dbc7c4d33f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592218"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="36c4f-102">^ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36c4f-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="36c4f-103">Bir sayıyı, başka bir sayının kuvvetine yükseltir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="36c4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36c4f-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="36c4f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="36c4f-105">Parts</span></span>

`number`\
<span data-ttu-id="36c4f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="36c4f-106">Required.</span></span> <span data-ttu-id="36c4f-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="36c4f-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="36c4f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="36c4f-108">Required.</span></span> <span data-ttu-id="36c4f-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="36c4f-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="36c4f-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="36c4f-110">Result</span></span>

<span data-ttu-id="36c4f-111">Sonuç `number` `exponent` ' in gücünden, her zaman `Double` değeri olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="36c4f-112">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="36c4f-112">Supported Types</span></span>

<span data-ttu-id="36c4f-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="36c4f-113">`Double`.</span></span> <span data-ttu-id="36c4f-114">Farklı türdeki işlenenler `Double` ' a dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="36c4f-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="36c4f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36c4f-115">Remarks</span></span>

<span data-ttu-id="36c4f-116">Visual Basic her zaman [Double veri türünde](../../../visual-basic/language-reference/data-types/double-data-type.md)üs gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>

<span data-ttu-id="36c4f-117">@No__t-0 değeri kesirli, negatif veya her ikisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="36c4f-118">Tek bir ifadede birden fazla üs işlemi gerçekleştirildiğinde, soldan sağa ile karşılaşıldığından `^` işleci değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="36c4f-119">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="36c4f-120">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="36c4f-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="36c4f-121">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="36c4f-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="36c4f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="36c4f-122">Example</span></span>

<span data-ttu-id="36c4f-123">Aşağıdaki örnek, bir sayının üssünü artırmak için `^` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="36c4f-124">Sonuç ikincinin gücüyle oluşturulan ilk işlenendir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="36c4f-125">Yukarıdaki örnek aşağıdaki sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="36c4f-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="36c4f-126">`exp1`, 4 (2 kare) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="36c4f-127">`exp2`, 19683 (3 odaya, sonra da bu değer) olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="36c4f-128">`exp3`-125 (-5 odaya) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="36c4f-129">`exp4`, 625 (-5 dördüncü güce) olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="36c4f-130">`exp5`, 2 olarak ayarlanır (8. küp kökü).</span><span class="sxs-lookup"><span data-stu-id="36c4f-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="36c4f-131">`exp6`, 0,5 (1,0 ' nin küp köküne bölünmüş olarak bölünür) olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="36c4f-132">Önceki örnekteki ifadelerde parantezlerin önemini dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="36c4f-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="36c4f-133">*İşleç önceliği*nedeniyle, Visual Basic normalde `^` işlecini, birli `–` işleci bile diğer bir şekilde gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="36c4f-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="36c4f-134">@No__t-0 ve `exp6` parantez olmadan hesaplanmışsa, bunlar aşağıdaki sonuçları üretti:</span><span class="sxs-lookup"><span data-stu-id="36c4f-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="36c4f-135">`exp4 = -5 ^ 4` – (5 dördüncü güce) olarak hesaplanacak ve bu,-625 ile sonuçlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="36c4f-136">`exp6 = 8 ^ -1.0 / 3.0`, 3,0 ' ye bölünecek şekilde (8 ' e kadar 1 güç veya 0,125), 0.041666666666666666666666666666667 ile sonuçlanabilecek şekilde hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="36c4f-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="36c4f-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36c4f-137">See also</span></span>

- [<span data-ttu-id="36c4f-138">^= İşleci</span><span class="sxs-lookup"><span data-stu-id="36c4f-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="36c4f-139">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="36c4f-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="36c4f-140">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="36c4f-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="36c4f-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="36c4f-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="36c4f-142">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="36c4f-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
