---
title: Aritmetik işleçler - C# referansı
description: Sayısal türleri ile çarpma, bölme, geri kama, ekleme ve çıkarma işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: ea9bf9e065b2953fd20e0503a19d1dc143064c5d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738740"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="d8c3b-103">Aritmetik işleçler (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="d8c3b-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="d8c3b-104">Aşağıdaki işleçler sayısal tiplerin operands ile aritmetik işlemleri gerçekleştirmek:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="d8c3b-105">Unary [ `++` (artış)](#increment-operator-), [ `--` (kararname)](#decrement-operator---), [ `+` (artı)](#unary-plus-and-minus-operators)ve [ `-` (eksi)](#unary-plus-and-minus-operators) işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8c3b-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="d8c3b-106">İkili [ `*` (çarpma)](#multiplication-operator-), [ `/` (bölme)](#division-operator-), [ `%` (kalan)](#remainder-operator-), [ `+` (toplama)](#addition-operator-)ve [ `-` (çıkarma) işleçleri](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="d8c3b-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="d8c3b-107">Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="d8c3b-108">Artış işleci ++</span><span class="sxs-lookup"><span data-stu-id="d8c3b-108">Increment operator ++</span></span>

<span data-ttu-id="d8c3b-109">Unary artış işleci `++` operand 1 oranında artışlar.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="d8c3b-110">Operand bir değişken, bir [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya bir [dizinleyici](../../programming-guide/indexers/index.md) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="d8c3b-111">Artış işleci iki şekilde desteklenir: postfix artış işleci `x++`ve önek artış işleci, `++x`.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="d8c3b-112">Sonek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-112">Postfix increment operator</span></span>

<span data-ttu-id="d8c3b-113">Aşağıdaki örnekte görüldüğü gibi, işlemin `x++` `x` *önceki* değerinin sonucu:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="d8c3b-114">Önek artış işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-114">Prefix increment operator</span></span>

<span data-ttu-id="d8c3b-115">Aşağıdaki örnekte görüldüğü `x` gibi, işlem den *sonraki* değerin sonucudur: `++x`</span><span class="sxs-lookup"><span data-stu-id="d8c3b-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="d8c3b-116">Kararname işleci --</span><span class="sxs-lookup"><span data-stu-id="d8c3b-116">Decrement operator --</span></span>

<span data-ttu-id="d8c3b-117">Unary kararname işleci `--` operand'ı 1 oranında azat eder.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="d8c3b-118">Operand bir değişken, bir [özellik](../../programming-guide/classes-and-structs/properties.md) erişimi veya bir [dizinleyici](../../programming-guide/indexers/index.md) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="d8c3b-119">Decrement işleci iki şekilde desteklenir: postfix decrement işleci, `x--`ve önek `--x`decrement işleci, .</span><span class="sxs-lookup"><span data-stu-id="d8c3b-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="d8c3b-120">Sonek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-120">Postfix decrement operator</span></span>

<span data-ttu-id="d8c3b-121">Aşağıdaki örnekte görüldüğü gibi, işlemin `x--` `x` *önceki* değerinin sonucu:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="d8c3b-122">Önek giderme işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-122">Prefix decrement operator</span></span>

<span data-ttu-id="d8c3b-123">Aşağıdaki örnekte görüldüğü `x` gibi, işlem den *sonraki* değerin sonucudur: `--x`</span><span class="sxs-lookup"><span data-stu-id="d8c3b-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="d8c3b-124">Unary artı ve eksi işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8c3b-124">Unary plus and minus operators</span></span>

<span data-ttu-id="d8c3b-125">Unary `+` işleci, operand değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="d8c3b-126">Unary `-` işleci, operand'ının sayısal olumsuzluğunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="d8c3b-127">[Ulong](../builtin-types/integral-numeric-types.md) türü unary `-` işleci desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="d8c3b-128">Çarpma işleci \*</span><span class="sxs-lookup"><span data-stu-id="d8c3b-128">Multiplication operator \*</span></span>

<span data-ttu-id="d8c3b-129">Çarpma işleci, `*` operandlarının ürününü hesaplar:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="d8c3b-130">Unary `*` işleci [işaretçi indirection işlecidir.](pointer-related-operators.md#pointer-indirection-operator-)</span><span class="sxs-lookup"><span data-stu-id="d8c3b-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="d8c3b-131">Bölme operatörü /</span><span class="sxs-lookup"><span data-stu-id="d8c3b-131">Division operator /</span></span>

<span data-ttu-id="d8c3b-132">Bölme işleci `/` sol operand'ını sağ operand'a böler.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="d8c3b-133">Sonsayı bölümü</span><span class="sxs-lookup"><span data-stu-id="d8c3b-133">Integer division</span></span>

<span data-ttu-id="d8c3b-134">İnteger türlerinin operandları için, işlecinin `/` sonucu bir hemşeri türüdür ve sıfıra doğru yuvarlatılmış iki operandun katibine eşittir:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="d8c3b-135">Kayan nokta sayısı olarak iki operands'ın katsayısını elde `float` `double`etmek `decimal` için , veya türü kullanın:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="d8c3b-136">Kayan nokta bölümü</span><span class="sxs-lookup"><span data-stu-id="d8c3b-136">Floating-point division</span></span>

<span data-ttu-id="d8c3b-137">`float`, , `double`ve `decimal` türleri için, `/` işleç sonucu iki operands bölüm:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="d8c3b-138">Eğer operands biri `decimal`ise , başka bir `float` operand ne ne de `double`olabilir , çünkü ne ne de `float` `double` örtülü olarak dönüştürülebilir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="d8c3b-139">Açıkça `float` `double` `decimal` veya operand türüne dönüştürmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="d8c3b-140">Sayısal türler arasındaki dönüşümler hakkında daha fazla bilgi için yerleşik [sayısal dönüşümler'e](../builtin-types/numeric-conversions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="d8c3b-141">Kalan işleç %</span><span class="sxs-lookup"><span data-stu-id="d8c3b-141">Remainder operator %</span></span>

<span data-ttu-id="d8c3b-142">Kalan işleç, `%` sol operand'ı sağ operand'a böldükten sonra geri kalanını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="d8c3b-143">İnteger geri kalanı</span><span class="sxs-lookup"><span data-stu-id="d8c3b-143">Integer remainder</span></span>

<span data-ttu-id="d8c3b-144">İnteger türlerinin operands için, `a % b` sonucu tarafından `a - (a / b) * b`üretilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="d8c3b-145">Sıfır olmayan geri kalan işareti, aşağıdaki örnekte görüldüğü gibi, sol operand ile aynıdır:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="d8c3b-146">Hem <xref:System.Math.DivRem%2A?displayProperty=nameWithType> tamsayı bölümünü hem de kalan sonuçları hesaplamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="d8c3b-147">Kayan nokta geri kalanı</span><span class="sxs-lookup"><span data-stu-id="d8c3b-147">Floating-point remainder</span></span>

<span data-ttu-id="d8c3b-148">`float` Ve `double` operands `x % y` için, sonlu `x` için sonucu `y` ve `z` değeri böyle</span><span class="sxs-lookup"><span data-stu-id="d8c3b-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="d8c3b-149">"Sıfır `z`değilse" işareti, `x`" işaretiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="d8c3b-150">Mutlak `z` değeri, `|x| - n * |y|` mümkün `n` olan en büyük tamsayı olan ve sırasıyla mutlak `|x| / |y|` `|x|` değerleri `|y|` olan ve `x` mutlak `y`değerler olan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="d8c3b-151">Bu hesaplama yöntemi, tamsayı operands için kullanılan, ancak IEEE 754 belirtimi farklı benzer.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="d8c3b-152">IEEE 754 belirtimine uygun kalan operasyona ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d8c3b-153">`%` Sonlu olmayan operands ile işlecinin davranışı hakkında bilgi için [C# dil belirtimiNin](~/_csharplang/spec/introduction.md) [Kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d8c3b-154">`decimal` Operands için, kalan `%` işleç <xref:System.Decimal?displayProperty=nameWithType> türünün kalan [işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="d8c3b-155">Aşağıdaki örnek, kalan işleç kayan nokta operands ile davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="d8c3b-156">İlave işleci +</span><span class="sxs-lookup"><span data-stu-id="d8c3b-156">Addition operator +</span></span>

<span data-ttu-id="d8c3b-157">Ek işleci, `+` operandlarının toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="d8c3b-158">Dize `+` birleşimi ve temsilci birleşimi için işleci de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-158">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="d8c3b-159">Daha fazla bilgi için, ve [ `+` `+=` operatörler](addition-operator.md) makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="d8c3b-160">Çıkarma operatörü -</span><span class="sxs-lookup"><span data-stu-id="d8c3b-160">Subtraction operator -</span></span>

<span data-ttu-id="d8c3b-161">Çıkarma işleci `-` sağ operand'ını sol operand'ından çıkarır:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="d8c3b-162">`-` Temsilci kaldırma için işleci de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-162">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="d8c3b-163">Daha fazla bilgi için, ve [ `-` `-=` operatörler](subtraction-operator.md) makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="d8c3b-164">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="d8c3b-164">Compound assignment</span></span>

<span data-ttu-id="d8c3b-165">Bir ikili `op`işleç için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="d8c3b-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="d8c3b-166">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="d8c3b-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="d8c3b-167">`x` bunun dışında sadece bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="d8c3b-168">Aşağıdaki örnek, bileşik atamanın aritmetik işleçlerle kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="d8c3b-169">Sayısal [promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu dolaylı olarak türüne `T` dönüştürülebilir `x`olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="d8c3b-170">Böyle bir durumda, `op` önceden tanımlanmış bir işleç ise ve işlemin sonucu açıkça `T` `x`türüne dönüştürülebilir ise `x op= y` , formun bileşik atama ifadesi eşdeğerdir `x = (T)(x op y)`, sadece bir kez değerlendirilir dışında. `x`</span><span class="sxs-lookup"><span data-stu-id="d8c3b-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="d8c3b-171">Aşağıdaki örnek, davranışı gösterir:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="d8c3b-172">Ayrıca, sırasıyla `-=` bir [olaya](../keywords/event.md)abone olmak ve aboneliğinizi iptal etmek için `+=` ve işleçleri de kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="d8c3b-173">Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="d8c3b-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="d8c3b-174">Operatör önceliği ve bağlantı</span><span class="sxs-lookup"><span data-stu-id="d8c3b-174">Operator precedence and associativity</span></span>

<span data-ttu-id="d8c3b-175">Aşağıdaki liste, en yüksek öncelikten en düşükbaştan başlayarak aritmetik işleçleri sıralar:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="d8c3b-176">Düzeltme artış `x++` ve decrement `x--` işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8c3b-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="d8c3b-177">Önek `++x` artış ve `--x` decrement ve `+` `-` unary ve operatörler</span><span class="sxs-lookup"><span data-stu-id="d8c3b-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="d8c3b-178">Çarpan , `*` `/`ve `%` işleçler</span><span class="sxs-lookup"><span data-stu-id="d8c3b-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="d8c3b-179">Katkı `+` `-` maddesi ve operatörler</span><span class="sxs-lookup"><span data-stu-id="d8c3b-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="d8c3b-180">İkili aritmetik işleçler sol-bağdaştırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="d8c3b-181">Diğer bir diğer olarak, aynı öncelik düzeyine sahip işleçler soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="d8c3b-182">Operatör önceliği ve `()`bağlantısı tarafından dayatılan değerlendirme sırasını değiştirmek için parantez kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="d8c3b-183">Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [C# işleçleri](index.md) makalesinin [Operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="d8c3b-184">Aritmetik taşma ve sıfır ile bölme</span><span class="sxs-lookup"><span data-stu-id="d8c3b-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="d8c3b-185">Bir aritmetik işlemin sonucu ilgili sayısal türün olası sonlu değerleri aralığının dışında olduğunda, aritmetik işleç davranışı operands türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="d8c3b-186">Tamsayı aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="d8c3b-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="d8c3b-187">Sıfır ile Tamsayı bölümü her <xref:System.DivideByZeroException>zaman bir atar .</span><span class="sxs-lookup"><span data-stu-id="d8c3b-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="d8c3b-188">Tamsayı aritmetik taşma durumunda, [denetlenebilir veya işaretlenmemiş](../keywords/checked-and-unchecked.md)bir taşma denetimi bağlamı, ortaya çıkan davranışı denetler:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="d8c3b-189">Denetlenen bir bağlamda, taşma sabit bir ifadede gerçekleşirse, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="d8c3b-190">Aksi takdirde, işlem çalışma zamanında gerçekleştirildiğinde, bir atılır. <xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="d8c3b-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="d8c3b-191">Denetlenmemiş bir bağlamda, sonuç hedef türüne sığmayacak yüksek sıralı bitler atılarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="d8c3b-192">[Denetlenen ve işaretlenmemiş](../keywords/checked-and-unchecked.md) ifadelerile birlikte, bir `checked` `unchecked` ifadenin değerlendirildiği taşma denetimi bağlamını denetlemek için ve işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="d8c3b-193">Varsayılan olarak, aritmetik işlemler *denetlenmemiş* bir bağlamda oluşur.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="d8c3b-194">Kayan nokta aritmetik taşma</span><span class="sxs-lookup"><span data-stu-id="d8c3b-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="d8c3b-195">Ve `float` `double` türleri ile aritmetik işlemler asla bir özel durum atmak.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="d8c3b-196">Bu türlerle yapılan aritmetik işlemlerin sonucu, sonsuzluğu ve sayı yı temsil etmeyen özel değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="d8c3b-197">`decimal` Türünün operands için, aritmetik taşma her <xref:System.OverflowException> zaman sıfır bir ve <xref:System.DivideByZeroException>bölünme atar her zaman bir .</span><span class="sxs-lookup"><span data-stu-id="d8c3b-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="d8c3b-198">Yuvarlama hataları</span><span class="sxs-lookup"><span data-stu-id="d8c3b-198">Round-off errors</span></span>

<span data-ttu-id="d8c3b-199">Reel sayıların kayan nokta gösteriminin genel sınırlamaları ve kayan nokta aritmetik nedeniyle, kayan nokta türleri ile hesaplamalarda yuvarlama hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="d8c3b-200">Diğer bir ifadenin üretilen sonucu beklenen matematiksel sonuçtan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="d8c3b-201">Aşağıdaki örnek, bu gibi birkaç örneği göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="d8c3b-202">Daha fazla bilgi için [System.Double,](/dotnet/api/system.double#remarks) [System.Single](/dotnet/api/system.single#remarks)veya [System.Ondalık](/dotnet/api/system.decimal#remarks) başvuru sayfalarındaki açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d8c3b-203">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="d8c3b-203">Operator overloadability</span></span>

<span data-ttu-id="d8c3b-204">Kullanıcı tanımlı bir tür, unary`++` `--` `+`(, `-`, ,`*`ve `/` `%`) `+`ve `-`ikili ( , , , , ve ) aritmetik işleçleri [aşırı yükleyebilir.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="d8c3b-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="d8c3b-205">Bir ikili işleci aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="d8c3b-206">Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d8c3b-207">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d8c3b-207">C# language specification</span></span>

<span data-ttu-id="d8c3b-208">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="d8c3b-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d8c3b-209">Düzeltme artış ve decrement işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8c3b-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="d8c3b-210">Önek artış ve decrement işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8c3b-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="d8c3b-211">Tekli artı işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="d8c3b-212">Unary eksi işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="d8c3b-213">Çarpma işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="d8c3b-214">Bölme operatörü</span><span class="sxs-lookup"><span data-stu-id="d8c3b-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="d8c3b-215">Kalan işleç</span><span class="sxs-lookup"><span data-stu-id="d8c3b-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="d8c3b-216">İlave işleci</span><span class="sxs-lookup"><span data-stu-id="d8c3b-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="d8c3b-217">Çıkarma operatörü</span><span class="sxs-lookup"><span data-stu-id="d8c3b-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="d8c3b-218">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="d8c3b-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="d8c3b-219">Denetlenen ve işaretlenmemiş işleçler</span><span class="sxs-lookup"><span data-stu-id="d8c3b-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="d8c3b-220">Sayısal promosyonlar</span><span class="sxs-lookup"><span data-stu-id="d8c3b-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="d8c3b-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8c3b-221">See also</span></span>

- [<span data-ttu-id="d8c3b-222">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d8c3b-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d8c3b-223">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8c3b-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="d8c3b-224">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="d8c3b-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
