---
title: Aritmetik işleçler-C# başvurusu
description: Sayısal türlerle çarpma, bölme, geri kalan, toplama ve çıkarma işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
ms.date: 05/11/2020
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
ms.openlocfilehash: 03bf7f246884fc8cd0095f0dd1375389a95e1ef0
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555480"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="dba45-103">Aritmetik işleçler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dba45-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="dba45-104">Aşağıdaki işleçler, sayısal türlerde işlenenler ile aritmetik işlemler gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="dba45-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="dba45-105">Birli [ `++` (artış)](#increment-operator-), [ `--` (azaltma)](#decrement-operator---), [ `+` (artı)](#unary-plus-and-minus-operators)ve [ `-` (eksi)](#unary-plus-and-minus-operators) işleçler</span><span class="sxs-lookup"><span data-stu-id="dba45-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="dba45-106">İkili [ `*` (çarpma)](#multiplication-operator-), [ `/` (bölme)](#division-operator-), [ `%` (geri kalan)](#remainder-operator-), [ `+` (toplama)](#addition-operator-)ve [ `-` (çıkarma)](#subtraction-operator--) işleçleri</span><span class="sxs-lookup"><span data-stu-id="dba45-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="dba45-107">Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dba45-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

<span data-ttu-id="dba45-108">İntegral türleri söz konusu olduğunda, bu işleçler ( `++` ve `--` işleçleri hariç),,, `int` `uint` `long` ve türleri için tanımlanır `ulong` .</span><span class="sxs-lookup"><span data-stu-id="dba45-108">In the case of integral types, those operators (except the `++` and `--` operators) are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="dba45-109">İşlenenler diğer integral türlerinde ( `sbyte` , `byte` , `short` , `ushort` , veya `char` ) olduğunda, değerleri `int` bir işlemin sonuç türü olan türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dba45-109">When operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="dba45-110">İşlenenler farklı integral veya kayan nokta türleri olduğunda, bu tür varsa, değerleri en yakın türe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dba45-110">When operands are of different integral or floating-point types, their values are converted to the closest containing type, if such a type exists.</span></span> <span data-ttu-id="dba45-111">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dba45-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="dba45-112">`++`Ve `--` işleçleri tüm integral ve kayan nokta sayısal türleri ve [char](../builtin-types/char.md) türü için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="dba45-112">The `++` and `--` operators are defined for all integral and floating-point numeric types and the [char](../builtin-types/char.md) type.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="dba45-113">Artış işleci + +</span><span class="sxs-lookup"><span data-stu-id="dba45-113">Increment operator ++</span></span>

<span data-ttu-id="dba45-114">Birli artış işleci, `++` işleneni 1 artırır.</span><span class="sxs-lookup"><span data-stu-id="dba45-114">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="dba45-115">İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dba45-115">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="dba45-116">Artırma işleci iki biçimde desteklenir: Sonek artışı işleci, `x++` ve önek artışı işleci, `++x` .</span><span class="sxs-lookup"><span data-stu-id="dba45-116">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="dba45-117">Sonek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-117">Postfix increment operator</span></span>

<span data-ttu-id="dba45-118">Sonucu, `x++` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *önceki* değeridir:</span><span class="sxs-lookup"><span data-stu-id="dba45-118">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="dba45-119">Ön ek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-119">Prefix increment operator</span></span>

<span data-ttu-id="dba45-120">Sonucu, `++x` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *sonraki* değerdir:</span><span class="sxs-lookup"><span data-stu-id="dba45-120">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="dba45-121">Azaltma işleci--</span><span class="sxs-lookup"><span data-stu-id="dba45-121">Decrement operator --</span></span>

<span data-ttu-id="dba45-122">Birli azaltma işleci, `--` işleneninin 1 değerini azaltır.</span><span class="sxs-lookup"><span data-stu-id="dba45-122">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="dba45-123">İşlenen bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dba45-123">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="dba45-124">Azaltma işleci iki formda desteklenir: sonek azaltma işleci, `x--` ve önek azaltma işleci, `--x` .</span><span class="sxs-lookup"><span data-stu-id="dba45-124">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="dba45-125">Sonek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-125">Postfix decrement operator</span></span>

<span data-ttu-id="dba45-126">Sonucu, `x--` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *önceki* değeridir:</span><span class="sxs-lookup"><span data-stu-id="dba45-126">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="dba45-127">Önek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-127">Prefix decrement operator</span></span>

<span data-ttu-id="dba45-128">Sonucu, `--x` `x` Aşağıdaki örnekte gösterildiği gibi, işlemden *sonraki* değerdir:</span><span class="sxs-lookup"><span data-stu-id="dba45-128">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="dba45-129">Birli artı ve eksi işleçleri</span><span class="sxs-lookup"><span data-stu-id="dba45-129">Unary plus and minus operators</span></span>

<span data-ttu-id="dba45-130">Birli `+` işleç, işleneninin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="dba45-130">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="dba45-131">Birli `-` işleç, işleneninin sayısal olumsuzunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dba45-131">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="dba45-132">[Ulong](../builtin-types/integral-numeric-types.md) türü birli `-` işleci desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="dba45-132">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="dba45-133">Çarpma işleci \*</span><span class="sxs-lookup"><span data-stu-id="dba45-133">Multiplication operator \*</span></span>

<span data-ttu-id="dba45-134">Çarpma işleci, `*` işlenenlerinin çarpımını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="dba45-134">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="dba45-135">Birli `*` işleç, [işaretçi yöneltme işleçtir](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="dba45-135">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="dba45-136">Bölme işleci/</span><span class="sxs-lookup"><span data-stu-id="dba45-136">Division operator /</span></span>

<span data-ttu-id="dba45-137">Bölme işleci, `/` sol işlenenini sağ işleneniyle böler.</span><span class="sxs-lookup"><span data-stu-id="dba45-137">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="dba45-138">Tamsayı bölme</span><span class="sxs-lookup"><span data-stu-id="dba45-138">Integer division</span></span>

<span data-ttu-id="dba45-139">Tamsayı türlerinin işlenenleri için, `/` işlecin sonucu bir tamsayı türüdür ve iki işlenenlerin sıfıra yuvarlayarak sonuna eşittir:</span><span class="sxs-lookup"><span data-stu-id="dba45-139">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="dba45-140">İki işlenenin bir kayan noktalı sayı olarak bölümünü almak için, `float` `double` veya `decimal` türünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="dba45-140">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="dba45-141">Kayan nokta bölme</span><span class="sxs-lookup"><span data-stu-id="dba45-141">Floating-point division</span></span>

<span data-ttu-id="dba45-142">`float`, `double` , Ve türleri için `decimal` `/` işlecinin sonucu iki işlenenin bir bölümü olur:</span><span class="sxs-lookup"><span data-stu-id="dba45-142">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="dba45-143">İşlenenlerden biri ise başka bir işlenen ne de, ne de `decimal` `float` örtük olarak `double` `float` `double` dönüştürülememiş olabilir `decimal` .</span><span class="sxs-lookup"><span data-stu-id="dba45-143">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="dba45-144">Ya da işleneni açıkça türüne dönüştürmeniz gerekir `float` `double` `decimal` .</span><span class="sxs-lookup"><span data-stu-id="dba45-144">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="dba45-145">Sayısal türler arasındaki dönüşümler hakkında daha fazla bilgi için bkz. [yerleşik sayısal dönüşümler](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="dba45-145">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="dba45-146">Kalan işleç yüzdesi</span><span class="sxs-lookup"><span data-stu-id="dba45-146">Remainder operator %</span></span>

<span data-ttu-id="dba45-147">Kalan işleç, `%` sol işlenenin sağ işleneniyle bölündükten sonra kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dba45-147">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="dba45-148">Tamsayı geri kalanı</span><span class="sxs-lookup"><span data-stu-id="dba45-148">Integer remainder</span></span>

<span data-ttu-id="dba45-149">Tamsayı türlerinin işlenenleri için, sonucu `a % b` tarafından üretilen değerdir `a - (a / b) * b` .</span><span class="sxs-lookup"><span data-stu-id="dba45-149">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="dba45-150">Sıfır olmayan geri kalanın işareti, aşağıdaki örnekte gösterildiği gibi, sol taraftaki işleneniyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="dba45-150">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="dba45-151"><xref:System.Math.DivRem%2A?displayProperty=nameWithType>Hem tamsayı bölme hem de kalan sonuçları hesaplamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dba45-151">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="dba45-152">Kayan nokta kalanı</span><span class="sxs-lookup"><span data-stu-id="dba45-152">Floating-point remainder</span></span>

<span data-ttu-id="dba45-153">`float`Ve işlenenleri için `double` , `x % y` sonsuz `x` `y` değeri `z` için sonuç olarak</span><span class="sxs-lookup"><span data-stu-id="dba45-153">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="dba45-154">`z`Sıfır olmayan, işareti, işaretiyle aynıdır `x` .</span><span class="sxs-lookup"><span data-stu-id="dba45-154">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="dba45-155">Öğesinin mutlak değeri, `z` tarafından üretilen `|x| - n * |y|` `n` en büyük olası tamsayı, ve `|x| / |y|` `|x|` `|y|` ' nin mutlak değerleri `x` sırasıyla ve `y` ' den daha az olan sayıdır.</span><span class="sxs-lookup"><span data-stu-id="dba45-155">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="dba45-156">Bu geri kalanı hesaplama yöntemi, tamsayı işlenenleri için kullanılan, ancak IEEE 754 belirtiminden farklı olacak şekilde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="dba45-156">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="dba45-157">IEEE 754 belirtimine uyan geri kalan işleme ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dba45-157">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="dba45-158">İşlecinin sınırlı olmayan işlenenlerle davranışı hakkında daha fazla bilgi için `%` [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [kalan işleç](~/_csharplang/spec/expressions.md#remainder-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dba45-158">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="dba45-159">İşlenenler için `decimal` , kalan işleç `%` türün [geri kalan işlecine](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) eşdeğerdir <xref:System.Decimal?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dba45-159">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="dba45-160">Aşağıdaki örnek, kayan nokta işlenenleri geri kalan işlecinin davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="dba45-160">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="dba45-161">Toplama işleci +</span><span class="sxs-lookup"><span data-stu-id="dba45-161">Addition operator +</span></span>

<span data-ttu-id="dba45-162">Toplama işleci, `+` işlenenlerinin toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="dba45-162">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="dba45-163">Ayrıca, `+` dize birleştirme ve temsilci birleşimi için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dba45-163">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="dba45-164">Daha fazla bilgi için, [ `+` ve `+=` işleçleri](addition-operator.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="dba45-164">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="dba45-165">Çıkarma işleci-</span><span class="sxs-lookup"><span data-stu-id="dba45-165">Subtraction operator -</span></span>

<span data-ttu-id="dba45-166">Çıkarma işleci, `-` sağ işlenenini sol tarafından çıkartır:</span><span class="sxs-lookup"><span data-stu-id="dba45-166">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="dba45-167">`-`Temsilci kaldırma için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dba45-167">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="dba45-168">Daha fazla bilgi için, [ `-` ve `-=` işleçleri](subtraction-operator.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="dba45-168">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="dba45-169">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="dba45-169">Compound assignment</span></span>

<span data-ttu-id="dba45-170">Bir ikili işleci için `op` , formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="dba45-170">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="dba45-171">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="dba45-171">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="dba45-172">hariç `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="dba45-172">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="dba45-173">Aşağıdaki örnek, aritmetik bir atama kullanımını Aritmetik işleçlerle gösterir:</span><span class="sxs-lookup"><span data-stu-id="dba45-173">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="dba45-174">[Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu örtük olarak türüne dönüştürülebilir olmayabilir `T` `x` .</span><span class="sxs-lookup"><span data-stu-id="dba45-174">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="dba45-175">Böyle bir durumda, `op` önceden tanımlanmış bir işleçse ve işlemin sonucu türüne açıkça dönüştürülebilir ise, `T` `x` formun bileşik atama ifadesi `x op= y` öğesine eşdeğerdir `x = (T)(x op y)` , ancak `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="dba45-175">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="dba45-176">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dba45-176">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="dba45-177">Ayrıca, `+=` `-=` sırasıyla bir olaya abone olmak ve bu [olaydan](../keywords/event.md)abonelik kaldırmak için ve işleçlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dba45-177">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="dba45-178">Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="dba45-178">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="dba45-179">İşleç önceliği ve ilişkilendirilebilirlik</span><span class="sxs-lookup"><span data-stu-id="dba45-179">Operator precedence and associativity</span></span>

<span data-ttu-id="dba45-180">Aşağıdaki liste, en yüksek öncelikten en düşüğe başlayarak aritmetik işleçleri sıralar:</span><span class="sxs-lookup"><span data-stu-id="dba45-180">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="dba45-181">Sonek artırma `x++` ve azaltma `x--` işleçleri</span><span class="sxs-lookup"><span data-stu-id="dba45-181">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="dba45-182">Ön ek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçler</span><span class="sxs-lookup"><span data-stu-id="dba45-182">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="dba45-183">Çoğultıcı `*` , `/` , ve `%` işleçler</span><span class="sxs-lookup"><span data-stu-id="dba45-183">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="dba45-184">Eklenebilir `+` ve `-` işleçler</span><span class="sxs-lookup"><span data-stu-id="dba45-184">Additive `+` and `-` operators</span></span>

<span data-ttu-id="dba45-185">İkili aritmetik işleçler sola ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dba45-185">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="dba45-186">Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="dba45-186">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="dba45-187">`()`İşleç önceliği ve ilişkilendirilebilirliği tarafından uygulanan değerlendirmenin sırasını değiştirmek için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="dba45-187">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="dba45-188">Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dba45-188">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="dba45-189">Aritmetik taşma ve sıfıra bölme</span><span class="sxs-lookup"><span data-stu-id="dba45-189">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="dba45-190">Bir aritmetik işlemin sonucu, ilgili sayısal türün olası sonlu değerler aralığının dışında olduğunda, bir aritmetik işlecin davranışı işlenenlerinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dba45-190">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="dba45-191">Tamsayı aritmetik taşması</span><span class="sxs-lookup"><span data-stu-id="dba45-191">Integer arithmetic overflow</span></span>

<span data-ttu-id="dba45-192">Sıfıra göre tam sayı bölümü her zaman bir oluşturur <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="dba45-192">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="dba45-193">Tamsayı aritmetik taşması olması durumunda, [denetlenen veya işaretlenmemiş](../keywords/checked-and-unchecked.md)bir taşma Denetim bağlamı ortaya çıkan davranışı denetler:</span><span class="sxs-lookup"><span data-stu-id="dba45-193">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="dba45-194">Denetlenen bir bağlamda, sabit bir ifadede taşma gerçekleşirse, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="dba45-194">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="dba45-195">Aksi takdirde, işlem çalışma zamanında gerçekleştirildiğinde bir oluşturulur <xref:System.OverflowException> .</span><span class="sxs-lookup"><span data-stu-id="dba45-195">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="dba45-196">İşaretlenmemiş bir bağlamda, sonuç, hedef türüne sığmayan yüksek sıralı bitleri atarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="dba45-196">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="dba45-197">[Checked ve unchecked](../keywords/checked-and-unchecked.md) deyimlerinin yanı sıra, `checked` `unchecked` bir ifadenin değerlendirildiği taşma denetimi bağlamını denetlemek için ve işleçlerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dba45-197">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="dba45-198">Varsayılan olarak, aritmetik işlemler *işaretlenmemiş* bir bağlamda oluşur.</span><span class="sxs-lookup"><span data-stu-id="dba45-198">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="dba45-199">Kayan nokta aritmetik taşması</span><span class="sxs-lookup"><span data-stu-id="dba45-199">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="dba45-200">Ve türleri ile aritmetik `float` İşlemler `double` hiçbir şekilde özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="dba45-200">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="dba45-201">Bu türlere sahip aritmetik işlemlerin sonucu, sonsuz ve bir sayı olmayan özel değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="dba45-201">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="dba45-202">Türün işlenenleri için `decimal` , aritmetik taşma her zaman <xref:System.OverflowException> sıfır tarafından bir ve bölme her zaman bir oluşturur <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="dba45-202">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="dba45-203">Yuvarlama hataları</span><span class="sxs-lookup"><span data-stu-id="dba45-203">Round-off errors</span></span>

<span data-ttu-id="dba45-204">Gerçek sayıların ve kayan nokta aritmetiğinin kayan nokta gösteriminin genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalar halinde yuvarlama hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="dba45-204">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="dba45-205">Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonucundan farklı olur.</span><span class="sxs-lookup"><span data-stu-id="dba45-205">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="dba45-206">Aşağıdaki örnekte bu gibi birkaç durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dba45-206">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="dba45-207">Daha fazla bilgi için bkz. [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)veya [System. Decimal](/dotnet/api/system.decimal#remarks) başvuru sayfalarındaki açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="dba45-207">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="dba45-208">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="dba45-208">Operator overloadability</span></span>

<span data-ttu-id="dba45-209">Kullanıcı tanımlı bir tür birli ( [overload](operator-overloading.md) `++` ,, `--` `+` , ve `-` ) ve ikili (,,, `*` `/` `%` `+` ve `-` ) aritmetik operatörlerini aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="dba45-209">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="dba45-210">İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="dba45-210">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="dba45-211">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="dba45-211">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dba45-212">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="dba45-212">C# language specification</span></span>

<span data-ttu-id="dba45-213">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="dba45-213">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dba45-214">Sonek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="dba45-214">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="dba45-215">Önek arttırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="dba45-215">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="dba45-216">Birli artı işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-216">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="dba45-217">Birli eksi işareti</span><span class="sxs-lookup"><span data-stu-id="dba45-217">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="dba45-218">Çarpma işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-218">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="dba45-219">Bölme işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-219">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="dba45-220">Kalan işleç</span><span class="sxs-lookup"><span data-stu-id="dba45-220">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="dba45-221">Toplama işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-221">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="dba45-222">Çıkarma işleci</span><span class="sxs-lookup"><span data-stu-id="dba45-222">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="dba45-223">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="dba45-223">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="dba45-224">Checked ve unchecked işleçleri</span><span class="sxs-lookup"><span data-stu-id="dba45-224">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="dba45-225">Sayısal yükseltmeler</span><span class="sxs-lookup"><span data-stu-id="dba45-225">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="dba45-226">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dba45-226">See also</span></span>

- [<span data-ttu-id="dba45-227">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="dba45-227">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dba45-228">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="dba45-228">C# operators and expressions</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="dba45-229">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="dba45-229">Numerics in .NET</span></span>](../../../standard/numerics.md)
