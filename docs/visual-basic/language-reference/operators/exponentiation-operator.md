---
title: ^ İşleci
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
ms.openlocfilehash: e139becf74ae367266a23513e18d0bdbdd24cdea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371394"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bc418-102">^ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc418-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="bc418-103">Bir sayıyı, başka bir sayının kuvvetine yükseltir.</span><span class="sxs-lookup"><span data-stu-id="bc418-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc418-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc418-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="bc418-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bc418-105">Parts</span></span>

`number`\
<span data-ttu-id="bc418-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc418-106">Required.</span></span> <span data-ttu-id="bc418-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="bc418-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="bc418-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc418-108">Required.</span></span> <span data-ttu-id="bc418-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="bc418-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="bc418-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="bc418-110">Result</span></span>

<span data-ttu-id="bc418-111">Sonuç `number` `exponent` , her zaman bir değer olarak ' ın gücüne yükseltilir `Double` .</span><span class="sxs-lookup"><span data-stu-id="bc418-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="bc418-112">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="bc418-112">Supported Types</span></span>

<span data-ttu-id="bc418-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="bc418-113">`Double`.</span></span> <span data-ttu-id="bc418-114">Farklı türdeki işlenenler öğesine dönüştürülür `Double` .</span><span class="sxs-lookup"><span data-stu-id="bc418-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc418-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc418-115">Remarks</span></span>

<span data-ttu-id="bc418-116">Visual Basic her zaman [Double veri türünde](../data-types/double-data-type.md)üs gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bc418-116">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span>

<span data-ttu-id="bc418-117">Değeri `exponent` kesirli, negatif veya her ikisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc418-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="bc418-118">Tek bir ifadede birden fazla üs gerçekleştirildiğinde, `^` işleç soldan sağa ile karşılaşıldığından değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bc418-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="bc418-119">`^`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bc418-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bc418-120">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bc418-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bc418-121">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bc418-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="bc418-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc418-122">Example</span></span>

<span data-ttu-id="bc418-123">Aşağıdaki örnek, `^` bir sayının üssünü artırmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc418-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="bc418-124">Sonuç ikincinin gücüyle oluşturulan ilk işlenendir.</span><span class="sxs-lookup"><span data-stu-id="bc418-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="bc418-125">Yukarıdaki örnek aşağıdaki sonuçları üretir:</span><span class="sxs-lookup"><span data-stu-id="bc418-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="bc418-126">`exp1`4 (2 kare) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bc418-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="bc418-127">`exp2`19683 olarak ayarlanır (3 odadır, daha sonra bu değer bir değeri).</span><span class="sxs-lookup"><span data-stu-id="bc418-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="bc418-128">`exp3`-125 (-5 odaya) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bc418-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="bc418-129">`exp4`625 (-5 dördüncü güce) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bc418-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="bc418-130">`exp5`2 olarak ayarlanır (8 ' in küp kökü).</span><span class="sxs-lookup"><span data-stu-id="bc418-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="bc418-131">`exp6`0,5 olarak ayarlanır (1,0, 8 ' in küp köküne bölünür).</span><span class="sxs-lookup"><span data-stu-id="bc418-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="bc418-132">Önceki örnekteki ifadelerde parantezlerin önemini dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="bc418-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="bc418-133">*İşleç önceliği*nedeniyle, Visual Basic normalde `^` işleci diğerlerinden önce, hatta birli `–` işleçle uygular.</span><span class="sxs-lookup"><span data-stu-id="bc418-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="bc418-134">`exp4`Ve `exp6` parantez olmadan hesaplanmışsa, bunlar aşağıdaki sonuçları üretti:</span><span class="sxs-lookup"><span data-stu-id="bc418-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="bc418-135">`exp4 = -5 ^ 4`,-625 ile sonuçlanabilecek – (5 dördüncü üssü) olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="bc418-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="bc418-136">`exp6 = 8 ^ -1.0 / 3.0`, 0.041666666666666666666666666666667 ile sonuçlanarak 3,0 ile ayrılmış olan (– 1 güç veya 0,125) olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="bc418-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc418-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc418-137">See also</span></span>

- [<span data-ttu-id="bc418-138">^ = İşleci</span><span class="sxs-lookup"><span data-stu-id="bc418-138">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="bc418-139">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="bc418-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="bc418-140">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="bc418-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="bc418-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="bc418-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="bc418-142">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="bc418-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
