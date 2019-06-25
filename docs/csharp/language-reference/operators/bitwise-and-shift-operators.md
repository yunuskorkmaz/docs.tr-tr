---
title: Bit düzeyinde ve kaydırma işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# gerçekleştirmek bit düzeyinde işleçler mantıksal veya tam sayı türleri olan işlenenler kaydırma işleçlerini.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 1f98435aba6994aaca76127cc20b5ffa29df455f
ms.sourcegitcommit: d9c4808739c8c606957dd0964d952b98ea7b6533
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67349768"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="77678-103">Bit düzeyinde ve kaydırma işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="77678-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="77678-104">Aşağıdaki işleçler bit düzeyinde gerçekleştirmek veya işlenenleri işlemleriyle kaydırmak [tam sayı türleri](../keywords/integral-types-table.md):</span><span class="sxs-lookup"><span data-stu-id="77678-104">The following operators perform bitwise or shift operations with operands of the [integral types](../keywords/integral-types-table.md):</span></span>

- <span data-ttu-id="77678-105">Birli [ `~` (bit düzeyinde tamamlayıcı)](#bitwise-complement-operator-) işleci</span><span class="sxs-lookup"><span data-stu-id="77678-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="77678-106">İkili [ `<<` (sola kaydırma)](#left-shift-operator-) ve [ `>>` (sağa kaydırma)](#right-shift-operator-) kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="77678-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="77678-107">İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal veya)](#logical-or-operator-), ve [ `^` (mantıksal XOR)](#logical-exclusive-or-operator-) işleçleri</span><span class="sxs-lookup"><span data-stu-id="77678-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="77678-108">Bu işleçler için tanımlanan `int`, `uint`, `long`, ve `ulong` türleri.</span><span class="sxs-lookup"><span data-stu-id="77678-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="77678-109">Her iki işlenen de integral türde olduğunda (`sbyte`, `byte`, `short`, `ushort`, veya `char`), değerlerine dönüştürülür `int` aynı zamanda bir işlemin sonuç türü olan türü.</span><span class="sxs-lookup"><span data-stu-id="77678-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="77678-110">Değerleri, işlenenleri farklı tamsayı türleri olduğunda, en yakın kapsayan integral türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="77678-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="77678-111">Daha fazla bilgi için [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="77678-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="77678-112">`&`, `|`, Ve `^` işleçleri için işlenenler de tanımlanır `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="77678-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="77678-113">Daha fazla bilgi için [Boolean mantıksal işleçler](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="77678-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="77678-114">Bit düzeyinde kaydırma işleçlerini asla taşmaya neden ve aynı sonuçlar [checked ve unchecked](../keywords/checked-and-unchecked.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="77678-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="77678-115">Bit düzeyinde tamamlama işleci ~</span><span class="sxs-lookup"><span data-stu-id="77678-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="77678-116">`~` İşleci her bit ters çevirerek bir bit düzeyinde tamamlayıcı işlenenin üretir:</span><span class="sxs-lookup"><span data-stu-id="77678-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="77678-117">Ayrıca `~` sonlandırıcılar bildirmek için Sembol.</span><span class="sxs-lookup"><span data-stu-id="77678-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="77678-118">Daha fazla bilgi için [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="77678-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="77678-119">Sola kaydırma işleci \<\<</span><span class="sxs-lookup"><span data-stu-id="77678-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="77678-120">`<<` İşleci sol işleneniyle tarafından sağ işlenen tarafından tanımlanan bit sayısı kadar sola kaydırır.</span><span class="sxs-lookup"><span data-stu-id="77678-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="77678-121">Sola kaydırma işleminin sonucu türü aralığının dışında olan ve düşük düzey boş bit konumları sıfır, aşağıdaki örnekte gösterildiği gibi ayarlar yüksek sıra bitleri atar:</span><span class="sxs-lookup"><span data-stu-id="77678-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="77678-122">Kaydırma işleçleri yalnızca tanımlandığından `int`, `uint`, `long`, ve `ulong` türlerini, her zaman bir işlemin sonucunu içeren en az 32 bit.</span><span class="sxs-lookup"><span data-stu-id="77678-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="77678-123">Sol işlenen başka bir integral türü ise (`sbyte`, `byte`, `short`, `ushort`, veya `char`), değeri dönüştürülür `int` türü, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="77678-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="77678-124">Hakkında bilgi için sağ işleneni `<<` işleci tanımlar kaydırma sayısı, bkz: [kaydırma işleçlerinin sayısı](#shift-count-of-the-shift-operators) bölümü.</span><span class="sxs-lookup"><span data-stu-id="77678-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="77678-125">Sağa kaydırma işleci >></span><span class="sxs-lookup"><span data-stu-id="77678-125">Right-shift operator >></span></span>

<span data-ttu-id="77678-126">`>>` İşleci kaydırır sol işleneniyle sağ tarafından sağ işlenen tarafından tanımlanan bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="77678-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="77678-127">Sağa kaydırma işlemi aşağıdaki örnekte gösterildiği gibi alt sıra bitleri atar:</span><span class="sxs-lookup"><span data-stu-id="77678-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="77678-128">Yüksek düzeyli boş bit konumları sol işlenenin türü üzerinde aşağıdaki gibi temel ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="77678-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="77678-129">Sol işlenen türü ise [int](../keywords/int.md) veya [uzun](../keywords/long.md), sağa kaydırma işleci gerçekleştiren bir *aritmetik* shift: en anlamlı biti (imza biti) değeri sol işlenen, yüksek sıralı boş bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="77678-129">If the left-hand operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="77678-130">Diğer bir deyişle, sol işlenen negatif ise yüksek düzeyli boş bit konumları sıfır olarak ayarlanır ve negatif ise birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="77678-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="77678-131">Sol işlenen türü ise [uint](../keywords/uint.md) veya [ulong](../keywords/ulong.md), sağa kaydırma işleci gerçekleştiren bir *mantıksal* shift: yüksek düzeyli boş bit konumları her zaman sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="77678-131">If the left-hand operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="77678-132">Hakkında bilgi için sağ işleneni `>>` işleci tanımlar kaydırma sayısı, bkz: [kaydırma işleçlerinin sayısı](#shift-count-of-the-shift-operators) bölümü.</span><span class="sxs-lookup"><span data-stu-id="77678-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="77678-133">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="77678-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="77678-134">`&` Kendi işlenenden bit seviyesinde mantıksal ve işlecini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="77678-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="77678-135">İşlenen için `bool` türü `&` işleci hesaplar [mantıksal AND](boolean-logical-operators.md#logical-and-operator-) işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="77678-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="77678-136">Birli `&` işleci [address-of işleci](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="77678-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="77678-137">Mantıksal Dışlayıcı veya işlecini ^</span><span class="sxs-lookup"><span data-stu-id="77678-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="77678-138">`^` İşleci hesaplar. bit düzeyinde mantıksal özel veya olarak da bilinen kendi işlenenden bit seviyesinde mantıksal XOR:</span><span class="sxs-lookup"><span data-stu-id="77678-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="77678-139">İşlenen için `bool` türü `^` işleci hesaplar [mantıksal XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="77678-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="77678-140">Mantıksal OR işlecinin |</span><span class="sxs-lookup"><span data-stu-id="77678-140">Logical OR operator |</span></span>

<span data-ttu-id="77678-141">`|` Kendi işlenenden bit seviyesinde mantıksal veya işlecini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="77678-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="77678-142">İşlenen için `bool` türü `|` işleci hesaplar [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="77678-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="77678-143">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="77678-143">Compound assignment</span></span>

<span data-ttu-id="77678-144">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="77678-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="77678-145">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="77678-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="77678-146">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="77678-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="77678-147">Aşağıdaki örnek, kaydırma işleçleri ve bileşik atama ile bit kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="77678-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="77678-148">Nedeniyle [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions), sonucunu `op` işlemi olabilir değil türe örtük olarak dönüştürülebilir `T` , `x`.</span><span class="sxs-lookup"><span data-stu-id="77678-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="77678-149">Böyle bir durumda ise `op` önceden tanımlanmış bir işleç ve işlemin sonucu türüne açıkça dönüştürülebilir ise `T` , `x`, formun bir bileşik atama ifadesi `x op= y` eşdeğerdir `x = (T)(x op y)`, dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="77678-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="77678-150">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="77678-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="77678-151">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="77678-151">Operator precedence</span></span>

<span data-ttu-id="77678-152">Aşağıdaki liste siparişleri bit düzeyinde ve en yüksek öncelikten en düşük başlangıç kaydırma işleçleri:</span><span class="sxs-lookup"><span data-stu-id="77678-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="77678-153">Bit düzeyinde tamamlama işleci `~`</span><span class="sxs-lookup"><span data-stu-id="77678-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="77678-154">Kaydırma işleçleri `<<` ve `>>`</span><span class="sxs-lookup"><span data-stu-id="77678-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="77678-155">Mantıksal AND işleci `&`</span><span class="sxs-lookup"><span data-stu-id="77678-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="77678-156">Özel mantıksal OR işleci `^`</span><span class="sxs-lookup"><span data-stu-id="77678-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="77678-157">Mantıksal OR işleci `|`</span><span class="sxs-lookup"><span data-stu-id="77678-157">Logical OR operator `|`</span></span>

<span data-ttu-id="77678-158">Parantez kullanın `()`İşleç önceliği tarafından belirlenen değerlendirmenin sırasını değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="77678-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="77678-159">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="77678-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="77678-160">Kaydırma işleçleri kaydırma sayısı</span><span class="sxs-lookup"><span data-stu-id="77678-160">Shift count of the shift operators</span></span>

<span data-ttu-id="77678-161">Kaydırma işleçleri için `<<` ve `>>`, sağ işlenenin türünde olmalıdır [int](../keywords/int.md) veya olan bir türü bir [örtülü sayısal dönüştürme önceden tanımlanmış](../keywords/implicit-numeric-conversions-table.md) için `int`.</span><span class="sxs-lookup"><span data-stu-id="77678-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="77678-162">İçin `x << count` ve `x >> count` ifadeleri, gerçek kaydırma sayısı türüne bağlıdır `x` gibi:</span><span class="sxs-lookup"><span data-stu-id="77678-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="77678-163">Varsa türünü `x` olduğu [int](../keywords/int.md) veya [uint](../keywords/uint.md), kaydırma sayısı düşük düzey tarafından tanımlanan *beş* sağ işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="77678-163">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="77678-164">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x1F` (veya `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="77678-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="77678-165">Varsa türünü `x` olduğu [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md), kaydırma sayısı düşük düzey tarafından tanımlanan *altı* sağ işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="77678-165">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="77678-166">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x3F` (veya `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="77678-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="77678-167">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="77678-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="77678-168">Mantıksal işleçler numaralandırması</span><span class="sxs-lookup"><span data-stu-id="77678-168">Enumeration logical operators</span></span>

<span data-ttu-id="77678-169">`~`, `&`, `|`, Ve `^` işleçleri de tanımlanır için [numaralandırma](../keywords/enum.md) türü.</span><span class="sxs-lookup"><span data-stu-id="77678-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="77678-170">İşlenenler aynı numaralandırma türü için bir mantıksal işlemi temel tamsayı türüne karşılık gelen değerleri üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="77678-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="77678-171">Örneğin, tüm `x` ve `y` bir numaralandırma türünün `T` bir temel türü ile `U`, `x & y` ifade aynı sonucu üretir `(T)((U)x & (U)y)` ifade.</span><span class="sxs-lookup"><span data-stu-id="77678-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="77678-172">İle tanımlanmış bir numaralandırma türü ile mantıksal bit düzeyinde işleçler kullanın [bayrakları](xref:System.FlagsAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="77678-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="77678-173">Daha fazla bilgi için [bit bayrakları olarak numaralandırma türleri](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) bölümünü [Numaralandırma türleri](../../programming-guide/enumeration-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="77678-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="77678-174">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="77678-174">Operator overloadability</span></span>

<span data-ttu-id="77678-175">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `~`, `<<`, `>>`, `&`, `|`, ve `^` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="77678-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="77678-176">İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="77678-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="77678-177">Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="77678-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="77678-178">Kullanıcı tanımlı bir tür ederse `T` aşırı `<<` veya `>>` işleci sol işlenenin türü olmalıdır `T` ve sağ işleneninin türü olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="77678-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="77678-179">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="77678-179">C# language specification</span></span>

<span data-ttu-id="77678-180">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="77678-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="77678-181">Bit düzeyinde tamamlama işleci</span><span class="sxs-lookup"><span data-stu-id="77678-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="77678-182">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="77678-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="77678-183">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="77678-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="77678-184">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="77678-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="77678-185">Sayısal promosyonlar</span><span class="sxs-lookup"><span data-stu-id="77678-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="77678-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77678-186">See also</span></span>

- [<span data-ttu-id="77678-187">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="77678-187">C# reference</span></span>](../index.md)
- [<span data-ttu-id="77678-188">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="77678-188">C# operators</span></span>](index.md)
- [<span data-ttu-id="77678-189">Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="77678-189">Boolean logical operators</span></span>](boolean-logical-operators.md)
