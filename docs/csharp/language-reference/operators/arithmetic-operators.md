---
title: Aritmetik işleçler- C# başvuru
description: Sayısal türlerle C# çarpma, bölme, geri kalan, toplama ve çıkarma işlemleri gerçekleştiren işleçler hakkında bilgi edinin.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 9d4b0123211388e9590ea3b7910a35d8480ff487
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239618"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="9253d-103">Aritmetik işleçler (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="9253d-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="9253d-104">Aşağıdaki işleçler, sayısal türlerde işlenenler ile aritmetik işlemler gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="9253d-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="9253d-105">Birli [`++` (artış)](#increment-operator-), [`--` (azaltma)](#decrement-operator---), [`+` (artı)](#unary-plus-and-minus-operators)ve [`-` (eksi)](#unary-plus-and-minus-operators) işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="9253d-106">İkili [`*` (çarpma)](#multiplication-operator-), [`/` (bölme)](#division-operator-), [`%` (kalan)](#remainder-operator-), [`+` (toplama)](#addition-operator-)ve [`-` (çıkarma)](#subtraction-operator--) işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="9253d-107">Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9253d-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="9253d-108">Artış işleci + +</span><span class="sxs-lookup"><span data-stu-id="9253d-108">Increment operator ++</span></span>

<span data-ttu-id="9253d-109">Birli artış işleci `++` işlenenini 1 artırır.</span><span class="sxs-lookup"><span data-stu-id="9253d-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="9253d-110">İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9253d-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="9253d-111">Artırma işleci iki biçimde desteklenir: sonek artırma işleci, `x++`ve önek artışı işleci, `++x`.</span><span class="sxs-lookup"><span data-stu-id="9253d-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="9253d-112">Sonek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-112">Postfix increment operator</span></span>

<span data-ttu-id="9253d-113">Aşağıdaki örnekte gösterildiği gibi, `x++` sonucu işlemden *önce* `x` değeridir:</span><span class="sxs-lookup"><span data-stu-id="9253d-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="9253d-114">Ön ek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-114">Prefix increment operator</span></span>

<span data-ttu-id="9253d-115">Aşağıdaki örnekte gösterildiği gibi, `++x` sonucu işlemden *sonra* `x` değeridir:</span><span class="sxs-lookup"><span data-stu-id="9253d-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="9253d-116">Azaltma işleci--</span><span class="sxs-lookup"><span data-stu-id="9253d-116">Decrement operator --</span></span>

<span data-ttu-id="9253d-117">Birli azaltma işleci `--` işlenenini 1 azaltır.</span><span class="sxs-lookup"><span data-stu-id="9253d-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="9253d-118">İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9253d-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="9253d-119">Azaltma işleci iki formda desteklenir: sonek azaltma işleci, `x--`ve ön ek azaltma işleci, `--x`.</span><span class="sxs-lookup"><span data-stu-id="9253d-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="9253d-120">Sonek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-120">Postfix decrement operator</span></span>

<span data-ttu-id="9253d-121">Aşağıdaki örnekte gösterildiği gibi, `x--` sonucu işlemden *önce* `x` değeridir:</span><span class="sxs-lookup"><span data-stu-id="9253d-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="9253d-122">Önek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-122">Prefix decrement operator</span></span>

<span data-ttu-id="9253d-123">Aşağıdaki örnekte gösterildiği gibi, `--x` sonucu işlemden *sonra* `x` değeridir:</span><span class="sxs-lookup"><span data-stu-id="9253d-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="9253d-124">Birli artı ve eksi işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-124">Unary plus and minus operators</span></span>

<span data-ttu-id="9253d-125">Birli `+` işleci, işleneninin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9253d-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="9253d-126">Birli `-` işleci, işleneninin sayısal olumsuzunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="9253d-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="9253d-127">[Ulong](../builtin-types/integral-numeric-types.md) türü birli `-` işlecini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9253d-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="9253d-128">Çarpma işleci \*</span><span class="sxs-lookup"><span data-stu-id="9253d-128">Multiplication operator \*</span></span>

<span data-ttu-id="9253d-129">Çarpma işleci `*` işlenenlerinin çarpımını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="9253d-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="9253d-130">Birli `*` işleci, [işaretçi yöneltme işleçtir](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="9253d-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="9253d-131">Bölme işleci/</span><span class="sxs-lookup"><span data-stu-id="9253d-131">Division operator /</span></span>

<span data-ttu-id="9253d-132">Bölme işleci `/` sol tarafından sağ işleneniyle böler.</span><span class="sxs-lookup"><span data-stu-id="9253d-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="9253d-133">Tamsayı bölme</span><span class="sxs-lookup"><span data-stu-id="9253d-133">Integer division</span></span>

<span data-ttu-id="9253d-134">Tamsayı türlerinin işlenenleri için, `/` işlecinin sonucu bir tamsayı türüdür ve iki işlenenlerin sıfıra yuvarlayarak Bu bölüm eşittir:</span><span class="sxs-lookup"><span data-stu-id="9253d-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="9253d-135">İki işlenenin bir kayan noktalı sayı olarak bölümünü almak için `float`, `double`veya `decimal` türünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="9253d-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="9253d-136">Kayan nokta bölme</span><span class="sxs-lookup"><span data-stu-id="9253d-136">Floating-point division</span></span>

<span data-ttu-id="9253d-137">`float`, `double`ve `decimal` türlerinde, `/` işlecinin sonucu iki işlenenin bir bölümü olur:</span><span class="sxs-lookup"><span data-stu-id="9253d-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="9253d-138">İşlenenlerden biri `decimal`, başka bir işlenen `float` veya `double`olamaz, çünkü hiçbir `float` veya `double` örtük olarak `decimal`dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="9253d-139">`float` veya `double` işlenenini `decimal` türüne açıkça dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9253d-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="9253d-140">Sayısal türler arasındaki dönüşümler hakkında daha fazla bilgi için bkz. [yerleşik sayısal dönüşümler](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="9253d-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="9253d-141">Kalan işleç yüzdesi</span><span class="sxs-lookup"><span data-stu-id="9253d-141">Remainder operator %</span></span>

<span data-ttu-id="9253d-142">Geri kalan işleç `%` sol taraftaki işleneni sağ tarafıyla ayırarak kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="9253d-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="9253d-143">Tamsayı geri kalanı</span><span class="sxs-lookup"><span data-stu-id="9253d-143">Integer remainder</span></span>

<span data-ttu-id="9253d-144">Tamsayı türlerinin işlenenleri için `a % b` sonucu, `a - (a / b) * b`tarafından oluşturulan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9253d-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="9253d-145">Sıfır olmayan geri kalanın işareti, aşağıdaki örnekte gösterildiği gibi, sol taraftaki işleneniyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="9253d-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="9253d-146">Hem tamsayı bölme hem de kalan sonuçları hesaplamak için <xref:System.Math.DivRem%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9253d-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="9253d-147">Kayan nokta kalanı</span><span class="sxs-lookup"><span data-stu-id="9253d-147">Floating-point remainder</span></span>

<span data-ttu-id="9253d-148">`float` ve `double` işlenenleri için `x % y` sonucu sınırlı `x` ve `y` için `z` değer</span><span class="sxs-lookup"><span data-stu-id="9253d-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="9253d-149">Sıfır olmayan `z`işareti, `x`işaretiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9253d-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="9253d-150">`z` mutlak değeri, `n` `|x| - n * |y|` tarafından üretilen en büyük tamsayı olan `|x| / |y|` ve `|x|` `|y|` ve `x` mutlak değerleri sırasıyla `y`ve.</span><span class="sxs-lookup"><span data-stu-id="9253d-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="9253d-151">Bu geri kalanı hesaplama yöntemi, tamsayı işlenenleri için kullanılan, ancak IEEE 754 belirtiminden farklı olacak şekilde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="9253d-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="9253d-152">IEEE 754 belirtimine uyan geri kalan işleme ihtiyacınız varsa <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9253d-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9253d-153">`%` işlecinin sonlu olmayan işlenenlerle davranışı hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [geri kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9253d-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="9253d-154">`decimal` işlenenleri için, `%` kalan işleç <xref:System.Decimal?displayProperty=nameWithType> türünün [kalan işlecine](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9253d-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="9253d-155">Aşağıdaki örnek, kayan nokta işlenenleri geri kalan işlecinin davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9253d-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="9253d-156">Toplama işleci +</span><span class="sxs-lookup"><span data-stu-id="9253d-156">Addition operator +</span></span>

<span data-ttu-id="9253d-157">Toplama işleci `+` işlenenlerinin toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="9253d-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="9253d-158">Dize birleştirme ve temsilci birleşimi için `+` işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9253d-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="9253d-159">Daha fazla bilgi için [`+` ve `+=` İşletmenleri](addition-operator.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="9253d-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="9253d-160">Çıkarma işleci-</span><span class="sxs-lookup"><span data-stu-id="9253d-160">Subtraction operator -</span></span>

<span data-ttu-id="9253d-161">Çıkarma işleci `-` sağ işlenenini sol tarafından çıkartır:</span><span class="sxs-lookup"><span data-stu-id="9253d-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="9253d-162">Temsilci kaldırma için `-` işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9253d-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="9253d-163">Daha fazla bilgi için [`-` ve `-=` İşletmenleri](subtraction-operator.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="9253d-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="9253d-164">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="9253d-164">Compound assignment</span></span>

<span data-ttu-id="9253d-165">Bir ikili işleç `op`için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="9253d-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="9253d-166">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="9253d-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="9253d-167">`x` hariç, yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="9253d-168">Aşağıdaki örnek, aritmetik bir atama kullanımını Aritmetik işleçlerle gösterir:</span><span class="sxs-lookup"><span data-stu-id="9253d-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="9253d-169">[Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle `op` işleminin sonucu `x``T` türüne örtülü olarak dönüştürülebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="9253d-170">Böyle bir durumda, `op` önceden tanımlanmış bir işleçse ve işlemin sonucu `x``T` türüne açıkça dönüştürülesiyse, `x = (T)(x op y)`yalnızca bir kez değerlendirilmemesi dışında, form `x op= y` bir bileşik atama ifadesi `x` değerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9253d-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="9253d-171">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9253d-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="9253d-172">Ayrıca, sırasıyla bir [olaya](../keywords/event.md)abone olmak ve aboneliği kaldırmak için `+=` ve `-=` işleçlerini da kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9253d-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="9253d-173">Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="9253d-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="9253d-174">İşleç önceliği ve ilişkilendirilebilirlik</span><span class="sxs-lookup"><span data-stu-id="9253d-174">Operator precedence and associativity</span></span>

<span data-ttu-id="9253d-175">Aşağıdaki liste, en yüksek öncelikten en düşüğe başlayarak aritmetik işleçleri sıralar:</span><span class="sxs-lookup"><span data-stu-id="9253d-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="9253d-176">Sonek artırma `x++` ve azaltma `x--` işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="9253d-177">Önek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="9253d-178">Çarpma `*`, `/`ve `%` işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="9253d-179">Adli `+` ve `-` işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="9253d-180">İkili aritmetik işleçler sola ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="9253d-181">Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="9253d-182">İşleç önceliği ve ilişkilendirilebilirliği tarafından uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()`kullanın.</span><span class="sxs-lookup"><span data-stu-id="9253d-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="9253d-183">Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için, [ C# işleçler](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9253d-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="9253d-184">Aritmetik taşma ve sıfıra bölme</span><span class="sxs-lookup"><span data-stu-id="9253d-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="9253d-185">Bir aritmetik işlemin sonucu, ilgili sayısal türün olası sonlu değerler aralığının dışında olduğunda, bir aritmetik işlecin davranışı işlenenlerinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9253d-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="9253d-186">Tamsayı aritmetik taşması</span><span class="sxs-lookup"><span data-stu-id="9253d-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="9253d-187">Sayı sıfıra bölme her zaman bir <xref:System.DivideByZeroException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9253d-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="9253d-188">Tamsayı aritmetik taşması olması durumunda, [denetlenen veya işaretlenmemiş](../keywords/checked-and-unchecked.md)bir taşma Denetim bağlamı ortaya çıkan davranışı denetler:</span><span class="sxs-lookup"><span data-stu-id="9253d-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="9253d-189">Denetlenen bir bağlamda, sabit bir ifadede taşma gerçekleşirse, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="9253d-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="9253d-190">Aksi takdirde, işlem çalışma zamanında gerçekleştirildiğinde bir <xref:System.OverflowException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9253d-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="9253d-191">İşaretlenmemiş bir bağlamda, sonuç, hedef türüne sığmayan yüksek sıralı bitleri atarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="9253d-192">[Checked ve unchecked](../keywords/checked-and-unchecked.md) deyimlerinin yanı sıra, bir ifadenin değerlendirildiği taşma denetimi bağlamını denetlemek için `checked` ve `unchecked` işleçlerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9253d-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="9253d-193">Varsayılan olarak, aritmetik işlemler *işaretlenmemiş* bir bağlamda oluşur.</span><span class="sxs-lookup"><span data-stu-id="9253d-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="9253d-194">Kayan nokta aritmetik taşması</span><span class="sxs-lookup"><span data-stu-id="9253d-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="9253d-195">`float` ve `double` türleriyle aritmetik işlemler hiçbir şekilde özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="9253d-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="9253d-196">Bu türlere sahip aritmetik işlemlerin sonucu, sonsuz ve bir sayı olmayan özel değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="9253d-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="9253d-197">`decimal` türünün işlenenleri için aritmetik taşma her zaman bir <xref:System.OverflowException> oluşturur ve sıfıra bölme her zaman bir <xref:System.DivideByZeroException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9253d-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="9253d-198">Yuvarlama hataları</span><span class="sxs-lookup"><span data-stu-id="9253d-198">Round-off errors</span></span>

<span data-ttu-id="9253d-199">Gerçek sayıların ve kayan nokta aritmetiğinin kayan nokta gösteriminin genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalar halinde yuvarlama hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="9253d-200">Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonucundan farklı olur.</span><span class="sxs-lookup"><span data-stu-id="9253d-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="9253d-201">Aşağıdaki örnekte bu gibi birkaç durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9253d-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="9253d-202">Daha fazla bilgi için bkz. [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)veya [System. Decimal](/dotnet/api/system.decimal#remarks) başvuru sayfalarındaki açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="9253d-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="9253d-203">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="9253d-203">Operator overloadability</span></span>

<span data-ttu-id="9253d-204">Kullanıcı tanımlı bir tür birli (`++`, `--`, `+`ve `-`) ve ikili (`*`, `/`, `%`, `+`ve `-`) aritmetik operatörlerini [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9253d-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="9253d-205">İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9253d-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="9253d-206">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="9253d-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9253d-207">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9253d-207">C# language specification</span></span>

<span data-ttu-id="9253d-208">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="9253d-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="9253d-209">Sonek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="9253d-210">Ön ek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="9253d-211">Birli Plus işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="9253d-212">Birli eksi işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="9253d-213">Çarpma işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="9253d-214">Bölme işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="9253d-215">Kalan işleç</span><span class="sxs-lookup"><span data-stu-id="9253d-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="9253d-216">Toplama işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="9253d-217">Çıkarma işleci</span><span class="sxs-lookup"><span data-stu-id="9253d-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="9253d-218">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="9253d-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="9253d-219">Checked ve unchecked işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="9253d-220">Sayısal yükseltmeler</span><span class="sxs-lookup"><span data-stu-id="9253d-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="9253d-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9253d-221">See also</span></span>

- [<span data-ttu-id="9253d-222">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="9253d-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9253d-223">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="9253d-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="9253d-224">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="9253d-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
