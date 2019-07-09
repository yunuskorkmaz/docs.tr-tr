---
title: Aritmetik işleçler - C# başvurusu
description: Hakkında bilgi edinin C# sayısal türlerle çarpma, bölme, kalan, toplama ve çıkarma işlemleri gerçekleştiren işleçleri.
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
ms.openlocfilehash: 02b27270c93550278308900382ae05091edb2543
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661542"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="11bf9-103">Aritmetik işleçler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="11bf9-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="11bf9-104">Aşağıdaki işleçleri ile sayısal türleri aritmetik işlemleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="11bf9-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="11bf9-105">Birli [ `++` (artırma)](#increment-operator-), [ `--` (azaltma)](#decrement-operator---), [ `+` (artı)](#unary-plus-and-minus-operators), ve [ `-` (eksi)](#unary-plus-and-minus-operators) işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="11bf9-106">İkili [ `*` (çarpma)](#multiplication-operator-), [ `/` (bölme)](#division-operator-), [ `%` (kalanını)](#remainder-operator-), [ `+` () ek olarak)](#addition-operator-), ve [ `-` (çıkarma)](#subtraction-operator--) işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="11bf9-107">Tüm bu işleçleri destekler [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="11bf9-107">Those operators support all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="11bf9-108">Artış işleci ++</span><span class="sxs-lookup"><span data-stu-id="11bf9-108">Increment operator ++</span></span>

<span data-ttu-id="11bf9-109">Tekli artırma işleci `++` işleneniyle 1 artar.</span><span class="sxs-lookup"><span data-stu-id="11bf9-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="11bf9-110">İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="11bf9-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="11bf9-111">Artırım işleci iki biçimde desteklenir: sonek artırma işlecini `x++`ve önek artırma işleci `++x`.</span><span class="sxs-lookup"><span data-stu-id="11bf9-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="11bf9-112">Sonek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-112">Postfix increment operator</span></span>

<span data-ttu-id="11bf9-113">Sonucu `x++` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="11bf9-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="11bf9-114">Önek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-114">Prefix increment operator</span></span>

<span data-ttu-id="11bf9-115">Sonucu `++x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="11bf9-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="11bf9-116">Azaltma işleci--</span><span class="sxs-lookup"><span data-stu-id="11bf9-116">Decrement operator --</span></span>

<span data-ttu-id="11bf9-117">Birli azaltma işleci `--` azaltır işleneniyle 1.</span><span class="sxs-lookup"><span data-stu-id="11bf9-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="11bf9-118">İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="11bf9-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="11bf9-119">Azaltma işleci iki biçimde desteklenir: sonek azaltma işlecinin `x--`ve önek azaltma işleci `--x`.</span><span class="sxs-lookup"><span data-stu-id="11bf9-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="11bf9-120">Sonek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-120">Postfix decrement operator</span></span>

<span data-ttu-id="11bf9-121">Sonucu `x--` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="11bf9-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="11bf9-122">Önek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-122">Prefix decrement operator</span></span>

<span data-ttu-id="11bf9-123">Sonucu `--x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="11bf9-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="11bf9-124">Birli artı ve eksi işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-124">Unary plus and minus operators</span></span>

<span data-ttu-id="11bf9-125">Birli `+` işleci, işlenenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="11bf9-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="11bf9-126">Birli `-` işleci, işlenenin sayısal olumsuzlama hesaplar.</span><span class="sxs-lookup"><span data-stu-id="11bf9-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="11bf9-127">Birli `-` işleci desteklemez [ulong](../builtin-types/integral-numeric-types.md) türü.</span><span class="sxs-lookup"><span data-stu-id="11bf9-127">The unary `-` operator doesn't support the [ulong](../builtin-types/integral-numeric-types.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="11bf9-128">Çarpma işleci \*</span><span class="sxs-lookup"><span data-stu-id="11bf9-128">Multiplication operator \*</span></span>

<span data-ttu-id="11bf9-129">Çarpma işleci `*` işlenenleri çarpımını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="11bf9-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="11bf9-130">Birli `*` işleci [işaretçi yöneltme işleci](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="11bf9-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="11bf9-131">Bölme işleci /</span><span class="sxs-lookup"><span data-stu-id="11bf9-131">Division operator /</span></span>

<span data-ttu-id="11bf9-132">Bölme işleci `/` sol işleneniyle sağ işleneni olarak böler.</span><span class="sxs-lookup"><span data-stu-id="11bf9-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="11bf9-133">Tamsayı bölme</span><span class="sxs-lookup"><span data-stu-id="11bf9-133">Integer division</span></span>

<span data-ttu-id="11bf9-134">Tamsayı türleri sonucunu işlenenleri için `/` işleci bir tamsayı türüdür ve sayının yuvarlanmış sıfır iki işlenenden eşittir:</span><span class="sxs-lookup"><span data-stu-id="11bf9-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="11bf9-135">İki işlenenden bölümü bir kayan noktalı sayı olarak almak için kullanın `float`, `double`, veya `decimal` türü:</span><span class="sxs-lookup"><span data-stu-id="11bf9-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="11bf9-136">Kayan nokta bölme</span><span class="sxs-lookup"><span data-stu-id="11bf9-136">Floating-point division</span></span>

<span data-ttu-id="11bf9-137">İçin `float`, `double`, ve `decimal` türleri, sonucunu `/` işleci, iki işlenenden bölümü:</span><span class="sxs-lookup"><span data-stu-id="11bf9-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="11bf9-138">İşlenenler ise `decimal`, başka bir işleç ne olabilir `float` ya da `double`, çünkü ne `float` ya da `double` örtük olarak dönüştürülebilir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="11bf9-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="11bf9-139">Açıkça dönüştürmelisiniz `float` veya `double` işleneni `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="11bf9-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="11bf9-140">Sayısal türler arasında örtük dönüştürme hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="11bf9-140">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="11bf9-141">Kalan işleci %</span><span class="sxs-lookup"><span data-stu-id="11bf9-141">Remainder operator %</span></span>

<span data-ttu-id="11bf9-142">Kalan işleci `%` sol işleneniyle sağ işleneni tarafından bölme işleminden kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="11bf9-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="11bf9-143">Tamsayı kalan</span><span class="sxs-lookup"><span data-stu-id="11bf9-143">Integer remainder</span></span>
  
<span data-ttu-id="11bf9-144">Tamsayı türleri sonucunu işlenenleri için `a % b` değeri tarafından üretilen `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="11bf9-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="11bf9-145">Sıfır olmayan kalan'in sol işlenenin aşağıdaki örnekte gösterildiği gibi aynıdır:</span><span class="sxs-lookup"><span data-stu-id="11bf9-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="11bf9-146">Kullanım <xref:System.Math.DivRem%2A?displayProperty=nameWithType> tamsayı bölme hem kalan sonuçları hesaplamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="11bf9-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="11bf9-147">Kayan nokta kalanını</span><span class="sxs-lookup"><span data-stu-id="11bf9-147">Floating-point remainder</span></span>

<span data-ttu-id="11bf9-148">İçin `float` ve `double` işlenenler, sonucunu `x % y` sınırlı için `x` ve `y` değer `z` gibi</span><span class="sxs-lookup"><span data-stu-id="11bf9-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="11bf9-149">İşaretini `z`, sıfır olmayan, işaretini aynı `x`.</span><span class="sxs-lookup"><span data-stu-id="11bf9-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="11bf9-150">mutlak değerini `z` değeri tarafından üretilen `|x| - n * |y|` burada `n` küçük veya eşit en büyük olası tamsayı `|x| / |y|` ve `|x|` ve `|y|` mutlak değerleri `x` ve `y`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="11bf9-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="11bf9-151">Kalanı hesaplama, bu yöntem, tamsayı işlenenler için kullanılan benzer, ancak IEEE 754 farklıdır.</span><span class="sxs-lookup"><span data-stu-id="11bf9-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="11bf9-152">IEEE 754 ile uyumlu işlemini ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="11bf9-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="11bf9-153">Davranışı hakkında bilgi için `%` sonlu olmayan işlenenler işleç bkz [kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="11bf9-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="11bf9-154">İçin `decimal` işlenenler, kalan işleci `%` eşdeğerdir [kalan işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) , <xref:System.Decimal?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="11bf9-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="11bf9-155">Aşağıdaki örnek, kayan nokta işlenenler ile kalan işleci davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="11bf9-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="11bf9-156">Toplama işleci +</span><span class="sxs-lookup"><span data-stu-id="11bf9-156">Addition operator +</span></span>

<span data-ttu-id="11bf9-157">Toplama işleci `+` işlenenleri toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="11bf9-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="11bf9-158">Ayrıca `+` dize birleştirme ve temsilci birleşimi için işleç.</span><span class="sxs-lookup"><span data-stu-id="11bf9-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="11bf9-159">Daha fazla bilgi için [ `+` ve `+=` işleçleri](addition-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="11bf9-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="11bf9-160">Çıkarma işleci-</span><span class="sxs-lookup"><span data-stu-id="11bf9-160">Subtraction operator -</span></span>

<span data-ttu-id="11bf9-161">Çıkarma işleci `-` sağ, sol işleneniyle işlenenden çıkarır:</span><span class="sxs-lookup"><span data-stu-id="11bf9-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="11bf9-162">Ayrıca `-` temsilci kaldırma işleci.</span><span class="sxs-lookup"><span data-stu-id="11bf9-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="11bf9-163">Daha fazla bilgi için [ `-` işleci](subtraction-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="11bf9-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="11bf9-164">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="11bf9-164">Compound assignment</span></span>

<span data-ttu-id="11bf9-165">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="11bf9-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="11bf9-166">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="11bf9-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="11bf9-167">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="11bf9-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="11bf9-168">Aşağıdaki örnek, aritmetik işleçlere sahip bileşik atama kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="11bf9-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="11bf9-169">Nedeniyle [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions), sonucunu `op` işlemi olabilir değil türe örtük olarak dönüştürülebilir `T` , `x`.</span><span class="sxs-lookup"><span data-stu-id="11bf9-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="11bf9-170">Böyle bir durumda ise `op` önceden tanımlanmış bir işleç ve işlemin sonucu türüne açıkça dönüştürülebilir ise `T` , `x`, formun bir bileşik atama ifadesi `x op= y` eşdeğerdir `x = (T)(x op y)`, dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="11bf9-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="11bf9-171">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="11bf9-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="11bf9-172">Ayrıca `+=` ve `-=` abone ve aboneliği iptal edin işleçleri [olayları](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="11bf9-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="11bf9-173">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="11bf9-173">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="11bf9-174">İşleç önceliği ve ilişkiselliği</span><span class="sxs-lookup"><span data-stu-id="11bf9-174">Operator precedence and associativity</span></span>

<span data-ttu-id="11bf9-175">Aşağıdaki liste, en yüksek öncelikten en düşük başlangıç aritmetik işleçler sıralar:</span><span class="sxs-lookup"><span data-stu-id="11bf9-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="11bf9-176">Sonek artırma `x++` ve azaltma `x--` işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="11bf9-177">Önek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="11bf9-178">Çarpma `*`, `/`, ve `%` işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="11bf9-179">Eklenebilir `+` ve `-` işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="11bf9-180">İkili aritmetik işleçler ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="11bf9-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="11bf9-181">Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler, soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="11bf9-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="11bf9-182">Parantez kullanın `()`, İşleç önceliği ve ilişkilendirilebilirlik tarafından dayatılan Değerlendirme sırasını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="11bf9-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="11bf9-183">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="11bf9-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="11bf9-184">Aritmetik Taşma ve sıfıra bölme</span><span class="sxs-lookup"><span data-stu-id="11bf9-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="11bf9-185">Aritmetik işlemin sonucu dahil olan sayısal türde olası sınırlı değerler aralığı dışında olduğunda davranışı bir aritmetik işlecinin işlenenleri türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="11bf9-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="11bf9-186">Tamsayı aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="11bf9-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="11bf9-187">Sıfır ile tamsayı bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="11bf9-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="11bf9-188">Olabilen tamsayı aritmetik taşma durumunda, bağlam, denetimi taşma [işaretli veya işaretsiz](../keywords/checked-and-unchecked.md), sonuçta elde edilen davranışı denetler:</span><span class="sxs-lookup"><span data-stu-id="11bf9-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="11bf9-189">Sabit bir ifadede taşma meydana gelirse denetlenen bir bağlamda, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="11bf9-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="11bf9-190">Aksi durumda, çalışma zamanında işlemi gerçekleştirilirken bir <xref:System.OverflowException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="11bf9-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="11bf9-191">İşaretlenmemiş bir bağlamda sonucu hedef türüne uygun olmayan herhangi bir yüksek düzeyli BITS atarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="11bf9-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="11bf9-192">İle birlikte [checked ve unchecked](../keywords/checked-and-unchecked.md) kullanabileceğiniz deyimleri `checked` ve `unchecked` işleçler bağlam bir ifade değerlendirme, taşma denetimini için:</span><span class="sxs-lookup"><span data-stu-id="11bf9-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="11bf9-193">Varsayılan olarak, aritmetik işlemler oluşan bir *denetlenmeyen* bağlamı.</span><span class="sxs-lookup"><span data-stu-id="11bf9-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="11bf9-194">Kayan nokta aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="11bf9-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="11bf9-195">Aritmetik işlemler `float` ve `double` türleri hiçbir zaman bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11bf9-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="11bf9-196">Bu türleri aritmetik işlemler sonucu sonsuzluk ve sayı değil temsil eden özel değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="11bf9-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="11bf9-197">İşlenen için `decimal` türü, aritmetik taşma her zaman oluşturur bir <xref:System.OverflowException> ve sıfır ile bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="11bf9-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="11bf9-198">Yuvarlama hataları</span><span class="sxs-lookup"><span data-stu-id="11bf9-198">Round-off errors</span></span>

<span data-ttu-id="11bf9-199">Gerçek sayıları ve kayan nokta aritmetiği kayan nokta temsili genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalarda yuvarlama hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="11bf9-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="11bf9-200">Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonuç farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="11bf9-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="11bf9-201">Aşağıdaki örnek, bu gibi durumlarda gösterir:</span><span class="sxs-lookup"><span data-stu-id="11bf9-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="11bf9-202">Açıklamalar, daha fazla bilgi için bkz. [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), veya [System.Decimal](/dotnet/api/system.decimal#remarks) başvuru sayfalarına.</span><span class="sxs-lookup"><span data-stu-id="11bf9-202">For more information, see remarks at [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="11bf9-203">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="11bf9-203">Operator overloadability</span></span>

<span data-ttu-id="11bf9-204">Kullanıcı tanımlı bir tür için [aşırı](operator-overloading.md) birli (`++`, `--`, `+`, ve `-`) ve ikili (`*`, `/`, `%`, `+`ve `-`) Aritmetik işleçler.</span><span class="sxs-lookup"><span data-stu-id="11bf9-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="11bf9-205">İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="11bf9-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="11bf9-206">Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="11bf9-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="11bf9-207">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="11bf9-207">C# language specification</span></span>

<span data-ttu-id="11bf9-208">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="11bf9-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="11bf9-209">Sonek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="11bf9-210">Önek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="11bf9-211">Birli artı işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="11bf9-212">Birli eksi işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="11bf9-213">Çarpma işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="11bf9-214">Bölme işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="11bf9-215">Kalan işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="11bf9-216">Toplama işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="11bf9-217">Çıkarma işleci</span><span class="sxs-lookup"><span data-stu-id="11bf9-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="11bf9-218">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="11bf9-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="11bf9-219">Checked ve unchecked işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="11bf9-220">Sayısal promosyonlar</span><span class="sxs-lookup"><span data-stu-id="11bf9-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="11bf9-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11bf9-221">See also</span></span>

- [<span data-ttu-id="11bf9-222">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="11bf9-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="11bf9-223">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="11bf9-224">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="11bf9-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
