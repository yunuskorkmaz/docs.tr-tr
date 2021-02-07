---
description: 'Daha fazla bilgi edinin: Mod işleci (Visual Basic)'
title: Mod İşleci
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: bfec39f54041714258e21f087a044dce24edcb6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665438"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="f8f9a-103">Mod işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8f9a-103">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="f8f9a-104">İki sayıyı böler ve yalnızca kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-104">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8f9a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8f9a-105">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="f8f9a-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f8f9a-106">Parts</span></span>

`result` \
<span data-ttu-id="f8f9a-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-107">Required.</span></span> <span data-ttu-id="f8f9a-108">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-108">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="f8f9a-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-109">Required.</span></span> <span data-ttu-id="f8f9a-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-110">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="f8f9a-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-111">Required.</span></span> <span data-ttu-id="f8f9a-112">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-112">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="f8f9a-113">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="f8f9a-113">Supported types</span></span>

<span data-ttu-id="f8f9a-114">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-114">All numeric types.</span></span> <span data-ttu-id="f8f9a-115">Bu, imzasız ve kayan nokta türlerini içerir `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="f8f9a-115">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="f8f9a-116">Sonuç</span><span class="sxs-lookup"><span data-stu-id="f8f9a-116">Result</span></span>

<span data-ttu-id="f8f9a-117">Sonuç, öğesinden `number1` bölündükten sonra kalanı `number2` .</span><span class="sxs-lookup"><span data-stu-id="f8f9a-117">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="f8f9a-118">Örneğin, ifade `14 Mod 4` 2 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-118">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="f8f9a-119">Olumsuz ve mod arasında negatif sayıların farklı sonuçlarıyla birlikte *kalan* ve *mod* arasında bir farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-119">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="f8f9a-120">`Mod`Visual Basic işleci, .NET Framework `op_Modulus` işleci ve temeldeki [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il yönergesinin hepsi bir geri kalan işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-120">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="f8f9a-121">Bir işlemin sonucu, `Mod` bölünün işaretini korur, `number1` ve bu nedenle pozitif veya negatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-121">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="f8f9a-122">Sonuç her zaman (- `number2` , `number2` ), hariç değişir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-122">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="f8f9a-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f8f9a-123">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="f8f9a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8f9a-124">Remarks</span></span>

<span data-ttu-id="f8f9a-125">Ya da `number1` `number2` bir kayan nokta değeri ise, bölmenin kayan nokta geri kalanı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-125">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="f8f9a-126">Sonucun veri türü, ve veri türleri ile bölme işleminden kaynaklanan tüm olası değerleri tutabilecek en küçük veri türüdür `number1` `number2` .</span><span class="sxs-lookup"><span data-stu-id="f8f9a-126">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="f8f9a-127">`number1`Ya da `number2` [hiçbir şey](../nothing.md)değerlendirilirse, sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-127">If `number1` or `number2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="f8f9a-128">İlgili işleçler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="f8f9a-128">Related operators include the following:</span></span>

- <span data-ttu-id="f8f9a-129">[\ İşleci (Visual Basic)](integer-division-operator.md) bir bölmenin tamsayı bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-129">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="f8f9a-130">Örneğin, ifade `14 \ 4` 3 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-130">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="f8f9a-131">[/İşleci (Visual Basic)](floating-point-division-operator.md) , kayan noktalı bir sayı olarak kalanı dahil olmak üzere tam bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-131">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="f8f9a-132">Örneğin, ifade `14 / 4` 3,5 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-132">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="f8f9a-133">Sıfıra bölme denendi</span><span class="sxs-lookup"><span data-stu-id="f8f9a-133">Attempted division by zero</span></span>

<span data-ttu-id="f8f9a-134">`number2`Sıfır olarak değerlendirilirse, `Mod` işlecin davranışı işlenenlerinin veri türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="f8f9a-134">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>

- <span data-ttu-id="f8f9a-135">Derleme zamanında belirlenemiyorsa integral bölüm bir <xref:System.DivideByZeroException> özel durum `number2` oluşturur ve derleme zamanında `BC30542 Division by zero occurred while evaluating this expression` sıfır olarak değerlendirilirse bir derleme zamanı hatası oluşturur `number2` .</span><span class="sxs-lookup"><span data-stu-id="f8f9a-135">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="f8f9a-136">Kayan nokta bölmesi döndürülür <xref:System.Double.NaN?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f8f9a-136">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="f8f9a-137">Denk formül</span><span class="sxs-lookup"><span data-stu-id="f8f9a-137">Equivalent formula</span></span>

<span data-ttu-id="f8f9a-138">İfade `a Mod b` aşağıdaki formüllerden birine eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="f8f9a-138">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="f8f9a-139">Kayan nokta noktasında kesinlik eksikliği</span><span class="sxs-lookup"><span data-stu-id="f8f9a-139">Floating-point imprecision</span></span>

<span data-ttu-id="f8f9a-140">Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir ondalık gösterimine sahip olmadıkları unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-140">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="f8f9a-141">Bu, değer karşılaştırması ve işleç gibi belirli işlemlerden beklenmeyen sonuçlara neden olabilir `Mod` .</span><span class="sxs-lookup"><span data-stu-id="f8f9a-141">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="f8f9a-142">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="f8f9a-142">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="f8f9a-143">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="f8f9a-143">Overloading</span></span>

<span data-ttu-id="f8f9a-144">`Mod`İşleç *aşırı* yüklenebilir, yani bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-144">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="f8f9a-145">Kodunuz `Mod` , bu tür bir aşırı yükleme içeren bir sınıf veya yapının örneği için geçerliyse, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-145">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f8f9a-146">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f8f9a-146">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8f9a-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8f9a-147">Example</span></span>

<span data-ttu-id="f8f9a-148">Aşağıdaki örnek, `Mod` iki sayıyı bölmek ve yalnızca geri kalanı döndürmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-148">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="f8f9a-149">Her iki sayı de bir kayan noktalı sayı ise sonuç, kalanı temsil eden bir kayan noktalı sayıdır.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-149">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="f8f9a-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8f9a-150">Example</span></span>

<span data-ttu-id="f8f9a-151">Aşağıdaki örnek, kayan nokta işlenenlerinin olası noktasında kesinlik eksikliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-151">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="f8f9a-152">İlk ifadede işlenen `Double` ve 0,2, saklı bir değeri 0.20000000000000001 olan sonsuz bir yinelenen ikili kesirdir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-152">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="f8f9a-153">İkinci ifadede, değişmez değer türü karakteri `D` her iki işleneni olarak zorlar `Decimal` ve 0,2 kesin bir gösterimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-153">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="f8f9a-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8f9a-154">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="f8f9a-155">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="f8f9a-155">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="f8f9a-156">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="f8f9a-156">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f8f9a-157">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="f8f9a-157">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f8f9a-158">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="f8f9a-158">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="f8f9a-159">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="f8f9a-159">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="f8f9a-160">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8f9a-160">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
