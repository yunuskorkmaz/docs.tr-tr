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
ms.openlocfilehash: 38a273210e769b8c764c8b67640063e44026f0f3
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504662"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="4b9ec-103">Aritmetik işleçler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4b9ec-103">Arithmetic operators (C# Reference)</span></span>

<span data-ttu-id="4b9ec-104">Aşağıdaki işleçleri ile sayısal türleri aritmetik işlemleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="4b9ec-105">Birli `++` (artırma) `--` (azaltma) `+` (artı), ve `-` (eksi) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-105">Unary `++` (increment), `--` (decrement), `+` (plus), and `-` (minus) operators.</span></span>
- <span data-ttu-id="4b9ec-106">İkili `*` (çarpma) `/` (bölme) `%` (kalanını) `+` (toplama) ve `-` (çıkarma) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-106">Binary `*` (multiplication), `/` (division), `%` (remainder), `+` (addition), and `-` (subtraction) operators.</span></span>

<span data-ttu-id="4b9ec-107">Tüm bu işleçleri destekler [integral](../keywords/integral-types-table.md) ve [kayan nokta](../keywords/floating-point-types-table.md) sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-107">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="4b9ec-108">Artış işleci ++</span><span class="sxs-lookup"><span data-stu-id="4b9ec-108">Increment operator ++</span></span>

<span data-ttu-id="4b9ec-109">Tekli artırma işleci `++` işleneniyle 1 artar.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="4b9ec-110">İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="4b9ec-111">Artırım işleci iki biçimde desteklenir: sonek artırma işlecini `x++`ve önek artırma işleci `++x`.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="4b9ec-112">Sonek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-112">Postfix increment operator</span></span>

<span data-ttu-id="4b9ec-113">Sonucu `x++` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="4b9ec-114">Önek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-114">Prefix increment operator</span></span>

<span data-ttu-id="4b9ec-115">Sonucu `++x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="4b9ec-116">Azaltma işleci--</span><span class="sxs-lookup"><span data-stu-id="4b9ec-116">Decrement operator --</span></span>

<span data-ttu-id="4b9ec-117">Birli azaltma işleci `--` azaltır işleneniyle 1.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="4b9ec-118">İşlenen, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="4b9ec-119">Azaltma işleci iki biçimde desteklenir: sonek azaltma işlecinin `x--`ve önek azaltma işleci `--x`.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="4b9ec-120">Sonek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-120">Postfix decrement operator</span></span>

<span data-ttu-id="4b9ec-121">Sonucu `x--` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="4b9ec-122">Önek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-122">Prefix decrement operator</span></span>

<span data-ttu-id="4b9ec-123">Sonucu `--x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="4b9ec-124">Birli artı ve eksi işleçleri</span><span class="sxs-lookup"><span data-stu-id="4b9ec-124">Unary plus and minus operators</span></span>

<span data-ttu-id="4b9ec-125">Birli `+` işleci, işlenenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="4b9ec-126">Birli `-` işleci, işlenenin sayısal olumsuzlama hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="4b9ec-127">Birli `-` işleci desteklemez [ulong](../keywords/ulong.md) türü.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-127">The unary `-` operator doesn't support the [ulong](../keywords/ulong.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="4b9ec-128">Çarpma işleci \*</span><span class="sxs-lookup"><span data-stu-id="4b9ec-128">Multiplication operator \*</span></span>

<span data-ttu-id="4b9ec-129">Çarpma işleci `*` işlenenleri çarpımını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="4b9ec-130">Birli `*` işleci, bir [işaretçi yöneltme işleci](multiplication-operator.md#pointer-indirection-operator).</span><span class="sxs-lookup"><span data-stu-id="4b9ec-130">The unary `*` operator is a [pointer indirection operator](multiplication-operator.md#pointer-indirection-operator).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="4b9ec-131">Bölme işleci /</span><span class="sxs-lookup"><span data-stu-id="4b9ec-131">Division operator /</span></span>

<span data-ttu-id="4b9ec-132">Bölme işleci `/` ilk işlenenin ikinci işleneni olarak böler.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-132">The division operator `/` divides its first operand by its second operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="4b9ec-133">Tamsayı bölme</span><span class="sxs-lookup"><span data-stu-id="4b9ec-133">Integer division</span></span>

<span data-ttu-id="4b9ec-134">Tamsayı türleri sonucunu işlenenleri için `/` işleci bir tamsayı türüdür ve sayının yuvarlanmış sıfır iki işlenenden eşittir:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="4b9ec-135">İki işlenenden bölümü bir kayan noktalı sayı olarak almak için kullanın `float`, `double`, veya `decimal` türü:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="4b9ec-136">Kayan nokta bölme</span><span class="sxs-lookup"><span data-stu-id="4b9ec-136">Floating-point division</span></span>

<span data-ttu-id="4b9ec-137">İçin `float`, `double`, ve `decimal` türleri, sonucunu `/` işleci, iki işlenenden bölümü:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="4b9ec-138">İşlenenler ise `decimal`, başka bir işleç ne olabilir `float` ya da `double`, çünkü ne `float` ya da `double` örtük olarak dönüştürülebilir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="4b9ec-139">Açıkça dönüştürmelisiniz `float` veya `double` işleneni `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="4b9ec-140">Sayısal türler arasında örtük dönüştürme hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="4b9ec-140">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="4b9ec-141">Kalan işleci %</span><span class="sxs-lookup"><span data-stu-id="4b9ec-141">Remainder operator %</span></span>

<span data-ttu-id="4b9ec-142">Kalan işleci `%` ilk işlenenin ikinci işleneni tarafından bölme işleminden kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-142">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="4b9ec-143">Tamsayı kalan</span><span class="sxs-lookup"><span data-stu-id="4b9ec-143">Integer remainder</span></span>
  
<span data-ttu-id="4b9ec-144">Tamsayı türleri sonucunu işlenenleri için `a % b` değeri tarafından üretilen `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="4b9ec-145">Sıfır olmayan kalanı oturum, ilk işlenen, aşağıdaki örnekte gösterildiği gibi aynıdır:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-145">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="4b9ec-146">Kullanım <xref:System.Math.DivRem%2A?displayProperty=nameWithType> tamsayı bölme hem kalan sonuçları hesaplamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="4b9ec-147">Kayan nokta kalanını</span><span class="sxs-lookup"><span data-stu-id="4b9ec-147">Floating-point remainder</span></span>

<span data-ttu-id="4b9ec-148">İçin `float` ve `double` işlenenler, sonucunu `x % y` sınırlı için `x` ve `y` değer `z` gibi</span><span class="sxs-lookup"><span data-stu-id="4b9ec-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="4b9ec-149">İşaretini `z`, sıfır olmayan, işaretini aynı `x`.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="4b9ec-150">mutlak değerini `z` değeri tarafından üretilen `|x| - n * |y|` burada `n` küçük veya eşit en büyük olası tamsayı `|x| / |y|` ve `|x|` ve `|y|` mutlak değerleri `x` ve `y`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="4b9ec-151">Kalanı hesaplama, bu yöntem, tamsayı işlenenler için kullanılan benzer, ancak IEEE 754 farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="4b9ec-152">IEEE 754 ile uyumlu işlemini ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4b9ec-153">Davranışı hakkında bilgi için `%` sonlu olmayan işlenenler işleç bkz [kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4b9ec-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="4b9ec-154">İçin `decimal` işlenenler, kalan işleci `%` eşdeğerdir [kalan işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) , <xref:System.Decimal?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="4b9ec-155">Aşağıdaki örnek, kayan nokta işlenenler ile kalan işleci davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="4b9ec-156">Toplama işleci +</span><span class="sxs-lookup"><span data-stu-id="4b9ec-156">Addition operator +</span></span>

<span data-ttu-id="4b9ec-157">Toplama işleci `+` işlenenleri toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="4b9ec-158">Ayrıca `+` dize birleştirme ve temsilci birleşimi için işleç.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="4b9ec-159">Daha fazla bilgi için [ `+` işleci](addition-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-159">For more information, see the [`+` operator](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="4b9ec-160">Çıkarma işleci-</span><span class="sxs-lookup"><span data-stu-id="4b9ec-160">Subtraction operator -</span></span>

<span data-ttu-id="4b9ec-161">Çıkarma işleci `-` gelen ilk işlenenin ikinci işleneni çıkarır:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-161">The subtraction operator `-` subtracts its second operand from its first operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="4b9ec-162">Ayrıca `-` temsilci kaldırma işleci.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="4b9ec-163">Daha fazla bilgi için [ `-` işleci](subtraction-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="4b9ec-164">İşleç önceliği ve ilişkiselliği</span><span class="sxs-lookup"><span data-stu-id="4b9ec-164">Operator precedence and associativity</span></span>

<span data-ttu-id="4b9ec-165">Aşağıdaki liste, en yüksek öncelikten en düşük başlangıç aritmetik işleçler sıralar:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-165">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="4b9ec-166">Sonek artırma `x++` ve azaltma `x--` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-166">Postfix increment `x++` and decrement `x--` operators.</span></span>
- <span data-ttu-id="4b9ec-167">Önek artırma `++x` ve azaltma `--x` ve birli `+` ve `-` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-167">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators.</span></span>
- <span data-ttu-id="4b9ec-168">Çarpma `*`, `/`, ve `%` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-168">Multiplicative `*`, `/`, and `%` operators.</span></span>
- <span data-ttu-id="4b9ec-169">Eklenebilir `+` ve `-` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-169">Additive `+` and `-` operators.</span></span>

<span data-ttu-id="4b9ec-170">İkili aritmetik işleçler ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-170">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="4b9ec-171">Diğer bir deyişle, aynı öncelik düzeyine sahip işleçler, soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-171">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="4b9ec-172">Parantez kullanın `()`, İşleç önceliği ve ilişkilendirilebilirlik tarafından dayatılan Değerlendirme sırasını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-172">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="4b9ec-173">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="4b9ec-173">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="4b9ec-174">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="4b9ec-174">Compound assignment</span></span>

<span data-ttu-id="4b9ec-175">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="4b9ec-175">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="4b9ec-176">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="4b9ec-176">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="4b9ec-177">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-177">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="4b9ec-178">Aşağıdaki örnek, aritmetik işleçlere sahip bileşik atama kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-178">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="4b9ec-179">Ayrıca `+=` ve `-=` abone ve aboneliği iptal edin işleçleri [olayları](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="4b9ec-179">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="4b9ec-180">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="4b9ec-180">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="4b9ec-181">Aritmetik Taşma ve sıfıra bölme</span><span class="sxs-lookup"><span data-stu-id="4b9ec-181">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="4b9ec-182">Aritmetik işlemin sonucu dahil olan sayısal türde olası sınırlı değerler aralığı dışında olduğunda davranışı bir aritmetik işlecinin işlenenleri türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-182">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="4b9ec-183">Tamsayı aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="4b9ec-183">Integer arithmetic overflow</span></span>

<span data-ttu-id="4b9ec-184">Sıfır ile tamsayı bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-184">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="4b9ec-185">Olabilen tamsayı aritmetik taşma durumunda, bağlam, denetimi taşma [işaretli veya işaretsiz](../keywords/checked-and-unchecked.md), sonuçta elde edilen davranışı denetler:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-185">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="4b9ec-186">Sabit bir ifadede taşma meydana gelirse denetlenen bir bağlamda, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-186">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="4b9ec-187">Aksi durumda, çalışma zamanında işlemi gerçekleştirilirken bir <xref:System.OverflowException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-187">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="4b9ec-188">İşaretlenmemiş bir bağlamda sonucu hedef türüne uygun olmayan herhangi bir yüksek düzeyli BITS atarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-188">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="4b9ec-189">İle birlikte [checked ve unchecked](../keywords/checked-and-unchecked.md) kullanabileceğiniz deyimleri `checked` ve `unchecked` işleçler bağlam bir ifade değerlendirme, taşma denetimini için:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-189">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="4b9ec-190">Varsayılan olarak, aritmetik işlemler oluşan bir *denetlenmeyen* bağlamı.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-190">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="4b9ec-191">Kayan nokta aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="4b9ec-191">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="4b9ec-192">Aritmetik işlemler `float` ve `double` türleri hiçbir zaman bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-192">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="4b9ec-193">Bu türleri aritmetik işlemler sonucu sonsuzluk ve sayı değil temsil eden özel değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-193">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="4b9ec-194">İşlenen için `decimal` türü, aritmetik taşma her zaman oluşturur bir <xref:System.OverflowException> ve sıfır ile bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-194">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="4b9ec-195">Yuvarlama hataları</span><span class="sxs-lookup"><span data-stu-id="4b9ec-195">Round-off errors</span></span>

<span data-ttu-id="4b9ec-196">Gerçek sayıları ve kayan nokta aritmetiği kayan nokta temsili genel sınırlamaları nedeniyle, kayan nokta türleriyle hesaplamalarda yuvarlama hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-196">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="4b9ec-197">Diğer bir deyişle, bir ifadenin üretilen sonucu beklenen matematik sonuç farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-197">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="4b9ec-198">Aşağıdaki örnek, bu gibi durumlarda gösterir:</span><span class="sxs-lookup"><span data-stu-id="4b9ec-198">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

## <a name="operator-overloadability"></a><span data-ttu-id="4b9ec-199">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="4b9ec-199">Operator overloadability</span></span>

<span data-ttu-id="4b9ec-200">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) birli (`++`, `--`, `+`, ve `-`) ve ikili (`*`, `/`, `%`, `+`ve `-`) Aritmetik işleçler.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-200">User-defined types can [overload](../keywords/operator.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="4b9ec-201">İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-201">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="4b9ec-202">Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-202">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4b9ec-203">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4b9ec-203">C# language specification</span></span>

<span data-ttu-id="4b9ec-204">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4b9ec-204">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4b9ec-205">Sonek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="4b9ec-205">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="4b9ec-206">Önek artırma ve azaltma işleçleri</span><span class="sxs-lookup"><span data-stu-id="4b9ec-206">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="4b9ec-207">Birli artı işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-207">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="4b9ec-208">Birli eksi işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-208">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="4b9ec-209">Çarpma işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-209">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="4b9ec-210">Bölme işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-210">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="4b9ec-211">Kalan işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-211">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="4b9ec-212">Toplama işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-212">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="4b9ec-213">Çıkarma işleci</span><span class="sxs-lookup"><span data-stu-id="4b9ec-213">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="4b9ec-214">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="4b9ec-214">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="4b9ec-215">Checked ve unchecked işleçleri</span><span class="sxs-lookup"><span data-stu-id="4b9ec-215">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)

## <a name="see-also"></a><span data-ttu-id="4b9ec-216">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b9ec-216">See also</span></span>

- [<span data-ttu-id="4b9ec-217">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4b9ec-217">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4b9ec-218">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4b9ec-218">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4b9ec-219">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="4b9ec-219">C# Operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="4b9ec-220">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="4b9ec-220">Numerics in .NET</span></span>](../../../standard/numerics.md)