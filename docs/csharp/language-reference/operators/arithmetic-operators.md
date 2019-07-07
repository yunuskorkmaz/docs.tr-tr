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
ms.openlocfilehash: 4108583a5f97d1349fb54c335d55252352ea4883
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610001"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="8ab9e-103">Aritmetik işleçler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ab9e-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="8ab9e-104">Aşağıdaki işleçleri ile sayısal türleri aritmetik işlemleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="8ab9e-105">Birli [ `++` (artırma)](#increment-operator-), [ `--` (azaltma)](#decrement-operator---), [ `+` (artı)](#unary-plus-and-minus-operators), ve [ `-` (eksi)](#unary-plus-and-minus-operators) işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="8ab9e-106">İkili [ `*` (çarpma)](#multiplication-operator-), [ `/` (bölme)](#division-operator-), [ `%` (kalanını)](#remainder-operator-), [ `+` () ek olarak)](#addition-operator-), ve [ `-` (çıkarma)](#subtraction-operator--) işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="8ab9e-107">Tüm bu işleçleri destekler [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../keywords/floating-point-types-table.md) sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-107">Those operators support all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="8ab9e-108">Artış işleci ++</span><span class="sxs-lookup"><span data-stu-id="8ab9e-108">Increment operator ++</span></span>

<span data-ttu-id="8ab9e-109">Tekli artırma işleci `++` işleneniyle 1 artar.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="8ab9e-110">İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="8ab9e-111">Artırım işleci iki biçimde desteklenir: sonek artırma işlecini `x++`ve önek artırma işleci `++x`.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="8ab9e-112">Sonek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-112">Postfix increment operator</span></span>

<span data-ttu-id="8ab9e-113">Sonucu `x++` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="8ab9e-114">Önek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-114">Prefix increment operator</span></span>

<span data-ttu-id="8ab9e-115">Sonucu `++x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="8ab9e-116">Azaltma işleci--</span><span class="sxs-lookup"><span data-stu-id="8ab9e-116">Decrement operator --</span></span>

<span data-ttu-id="8ab9e-117">Birli azaltma işleci `--` azaltır işleneniyle 1.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="8ab9e-118">İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="8ab9e-119">Azaltma işleci iki biçimde desteklenir: sonek azaltma işlecinin `x--`ve önek azaltma işleci `--x`.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="8ab9e-120">Sonek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-120">Postfix decrement operator</span></span>

<span data-ttu-id="8ab9e-121">Sonucu `x--` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="8ab9e-122">Önek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-122">Prefix decrement operator</span></span>

<span data-ttu-id="8ab9e-123">Sonucu `--x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="8ab9e-124">Birli artı ve eksi işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-124">Unary plus and minus operators</span></span>

<span data-ttu-id="8ab9e-125">Birli `+` işleci, işlenenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="8ab9e-126">Birli `-` işleci, işlenenin sayısal olumsuzlama hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="8ab9e-127">Birli `-` işleci desteklemez [ulong](../builtin-types/integral-numeric-types.md) türü.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-127">The unary `-` operator doesn't support the [ulong](../builtin-types/integral-numeric-types.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="8ab9e-128">Çarpma işleci \*</span><span class="sxs-lookup"><span data-stu-id="8ab9e-128">Multiplication operator \*</span></span>

<span data-ttu-id="8ab9e-129">Çarpma işleci `*` işlenenleri çarpımını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="8ab9e-130">Birli `*` işleci [işaretçi yöneltme işleci](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="8ab9e-131">Bölme işleci /</span><span class="sxs-lookup"><span data-stu-id="8ab9e-131">Division operator /</span></span>

<span data-ttu-id="8ab9e-132">Bölme işleci `/` sol işleneniyle sağ işleneni olarak böler.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="8ab9e-133">Tamsayı bölme</span><span class="sxs-lookup"><span data-stu-id="8ab9e-133">Integer division</span></span>

<span data-ttu-id="8ab9e-134">Tamsayı türleri sonucunu işlenenleri için `/` işleci bir tamsayı türüdür ve sayının yuvarlanmış sıfır iki işlenenden eşittir:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="8ab9e-135">İki işlenenden bölümü bir kayan noktalı sayı olarak almak için kullanın `float`, `double`, veya `decimal` türü:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="8ab9e-136">Kayan nokta bölme</span><span class="sxs-lookup"><span data-stu-id="8ab9e-136">Floating-point division</span></span>

<span data-ttu-id="8ab9e-137">İçin `float`, `double`, ve `decimal` türleri, sonucunu `/` işleci, iki işlenenden bölümü:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="8ab9e-138">İşlenenler ise `decimal`, başka bir işleç ne olabilir `float` ya da `double`, çünkü ne `float` ya da `double` örtük olarak dönüştürülebilir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="8ab9e-139">Açıkça dönüştürmelisiniz `float` veya `double` işleneni `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="8ab9e-140">Sayısal türler arasında örtük dönüştürme hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-140">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="8ab9e-141">Kalan işleci %</span><span class="sxs-lookup"><span data-stu-id="8ab9e-141">Remainder operator %</span></span>

<span data-ttu-id="8ab9e-142">Kalan işleci `%` sol işleneniyle sağ işleneni tarafından bölme işleminden kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="8ab9e-143">Tamsayı kalan</span><span class="sxs-lookup"><span data-stu-id="8ab9e-143">Integer remainder</span></span>
  
<span data-ttu-id="8ab9e-144">Tamsayı türleri sonucunu işlenenleri için `a % b` değeri tarafından üretilen `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="8ab9e-145">Sıfır olmayan kalan'in sol işlenenin aşağıdaki örnekte gösterildiği gibi aynıdır:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="8ab9e-146">Kullanım <xref:System.Math.DivRem%2A?displayProperty=nameWithType> tamsayı bölme hem kalan sonuçları hesaplamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="8ab9e-147">Kayan nokta kalanını</span><span class="sxs-lookup"><span data-stu-id="8ab9e-147">Floating-point remainder</span></span>

<span data-ttu-id="8ab9e-148">İçin `float` ve `double` işlenenler, sonucunu `x % y` sınırlı için `x` ve `y` değer `z` gibi</span><span class="sxs-lookup"><span data-stu-id="8ab9e-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="8ab9e-149">İşaretini `z`, sıfır olmayan, işaretini aynı `x`.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="8ab9e-150">mutlak değerini `z` değeri tarafından üretilen `|x| - n * |y|` burada `n` küçük veya eşit en büyük olası tamsayı `|x| / |y|` ve `|x|` ve `|y|` mutlak değerleri `x` ve `y`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="8ab9e-151">Kalanı hesaplama, bu yöntem, tamsayı işlenenler için kullanılan benzer, ancak IEEE 754 farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="8ab9e-152">IEEE 754 ile uyumlu işlemini ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="8ab9e-153">Davranışı hakkında bilgi için `%` sonlu olmayan işlenenler işleç bkz [kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8ab9e-154">İçin `decimal` işlenenler, kalan işleci `%` eşdeğerdir [kalan işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) , <xref:System.Decimal?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="8ab9e-155">Aşağıdaki örnek, kayan nokta işlenenler ile kalan işleci davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="8ab9e-156">Toplama işleci +</span><span class="sxs-lookup"><span data-stu-id="8ab9e-156">Addition operator +</span></span>

<span data-ttu-id="8ab9e-157">Toplama işleci `+` işlenenleri toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="8ab9e-158">Ayrıca `+` dize birleştirme ve temsilci birleşimi için işleç.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="8ab9e-159">Daha fazla bilgi için [ `+` ve `+=` işleçleri](addition-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="8ab9e-160">Çıkarma işleci-</span><span class="sxs-lookup"><span data-stu-id="8ab9e-160">Subtraction operator -</span></span>

<span data-ttu-id="8ab9e-161">Çıkarma işleci `-` sağ, sol işleneniyle işlenenden çıkarır:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="8ab9e-162">Ayrıca `-` temsilci kaldırma işleci.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="8ab9e-163">Daha fazla bilgi için [ `-` işleci](subtraction-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="8ab9e-164">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="8ab9e-164">Compound assignment</span></span>

<span data-ttu-id="8ab9e-165">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="8ab9e-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="8ab9e-166">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="8ab9e-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="8ab9e-167">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="8ab9e-168">Aşağıdaki örnek, aritmetik işleçlere sahip bileşik atama kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="8ab9e-169">Nedeniyle [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions), sonucunu `op` işlemi olabilir değil türe örtük olarak dönüştürülebilir `T` , `x`.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="8ab9e-170">Böyle bir durumda ise `op` önceden tanımlanmış bir işleç ve işlemin sonucu türüne açıkça dönüştürülebilir ise `T` , `x`, formun bir bileşik atama ifadesi `x op= y` eşdeğerdir `x = (T)(x op y)`, dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="8ab9e-171">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="8ab9e-172">Ayrıca `+=` ve `-=` abone ve aboneliği iptal edin işleçleri [olayları](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="8ab9e-173">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-173">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="8ab9e-174">İşleç önceliği ve ilişkiselliği</span><span class="sxs-lookup"><span data-stu-id="8ab9e-174">Operator precedence and associativity</span></span>

<span data-ttu-id="8ab9e-175">Aşağıdaki liste, en yüksek öncelikten en düşük başlangıç aritmetik işleçler sıralar:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="8ab9e-176">Sonek artırma `x++` ve azaltma `x--` işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="8ab9e-177">Önek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="8ab9e-178">Çarpma `*`, `/`, ve `%` işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="8ab9e-179">Eklenebilir `+` ve `-` işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="8ab9e-180">İkili aritmetik işleçler ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="8ab9e-181">Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler, soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="8ab9e-182">Parantez kullanın `()`, İşleç önceliği ve ilişkilendirilebilirlik tarafından dayatılan Değerlendirme sırasını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="8ab9e-183">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="8ab9e-184">Aritmetik Taşma ve sıfıra bölme</span><span class="sxs-lookup"><span data-stu-id="8ab9e-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="8ab9e-185">Aritmetik işlemin sonucu dahil olan sayısal türde olası sınırlı değerler aralığı dışında olduğunda davranışı bir aritmetik işlecinin işlenenleri türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="8ab9e-186">Tamsayı aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="8ab9e-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="8ab9e-187">Sıfır ile tamsayı bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="8ab9e-188">Olabilen tamsayı aritmetik taşma durumunda, bağlam, denetimi taşma [işaretli veya işaretsiz](../keywords/checked-and-unchecked.md), sonuçta elde edilen davranışı denetler:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="8ab9e-189">Sabit bir ifadede taşma meydana gelirse denetlenen bir bağlamda, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="8ab9e-190">Aksi durumda, çalışma zamanında işlemi gerçekleştirilirken bir <xref:System.OverflowException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="8ab9e-191">İşaretlenmemiş bir bağlamda sonucu hedef türüne uygun olmayan herhangi bir yüksek düzeyli BITS atarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="8ab9e-192">İle birlikte [checked ve unchecked](../keywords/checked-and-unchecked.md) kullanabileceğiniz deyimleri `checked` ve `unchecked` işleçler bağlam bir ifade değerlendirme, taşma denetimini için:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="8ab9e-193">Varsayılan olarak, aritmetik işlemler oluşan bir *denetlenmeyen* bağlamı.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="8ab9e-194">Kayan nokta aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="8ab9e-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="8ab9e-195">Aritmetik işlemler `float` ve `double` türleri hiçbir zaman bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="8ab9e-196">Bu türleri aritmetik işlemler sonucu sonsuzluk ve sayı değil temsil eden özel değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="8ab9e-197">İşlenen için `decimal` türü, aritmetik taşma her zaman oluşturur bir <xref:System.OverflowException> ve sıfır ile bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="8ab9e-198">Yuvarlama hataları</span><span class="sxs-lookup"><span data-stu-id="8ab9e-198">Round-off errors</span></span>

<span data-ttu-id="8ab9e-199">Gerçek sayıları ve kayan nokta aritmetiği kayan nokta temsili genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalarda yuvarlama hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="8ab9e-200">Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonuç farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="8ab9e-201">Aşağıdaki örnek, bu gibi durumlarda gösterir:</span><span class="sxs-lookup"><span data-stu-id="8ab9e-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="8ab9e-202">Açıklamalar, daha fazla bilgi için bkz. [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), veya [System.Decimal](/dotnet/api/system.decimal#remarks) başvuru sayfalarına.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-202">For more information, see remarks at [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8ab9e-203">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="8ab9e-203">Operator overloadability</span></span>

<span data-ttu-id="8ab9e-204">Kullanıcı tanımlı bir tür için [aşırı](operator-overloading.md) birli (`++`, `--`, `+`, ve `-`) ve ikili (`*`, `/`, `%`, `+`ve `-`) Aritmetik işleçler.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="8ab9e-205">İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="8ab9e-206">Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8ab9e-207">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8ab9e-207">C# language specification</span></span>

<span data-ttu-id="8ab9e-208">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8ab9e-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8ab9e-209">Sonek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="8ab9e-210">Önek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="8ab9e-211">Birli artı işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="8ab9e-212">Birli eksi işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="8ab9e-213">Çarpma işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="8ab9e-214">Bölme işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="8ab9e-215">Kalan işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="8ab9e-216">Toplama işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="8ab9e-217">Çıkarma işleci</span><span class="sxs-lookup"><span data-stu-id="8ab9e-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="8ab9e-218">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="8ab9e-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="8ab9e-219">Checked ve unchecked işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="8ab9e-220">Sayısal promosyonlar</span><span class="sxs-lookup"><span data-stu-id="8ab9e-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="8ab9e-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-221">See also</span></span>

- [<span data-ttu-id="8ab9e-222">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="8ab9e-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8ab9e-223">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="8ab9e-224">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="8ab9e-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
