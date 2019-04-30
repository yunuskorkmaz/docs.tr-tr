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
ms.openlocfilehash: df696b9b9462f1a844d43043b968f30404da586d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660105"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="8db0b-103">Bit düzeyinde ve kaydırma işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8db0b-103">Bitwise and shift operators (C# Reference)</span></span>

<span data-ttu-id="8db0b-104">Aşağıdaki işleçler bit düzeyinde gerçekleştirmek veya işlenenleri işlemleriyle kaydırmak [tam sayı türleri](../keywords/integral-types-table.md):</span><span class="sxs-lookup"><span data-stu-id="8db0b-104">The following operators perform bitwise or shift operations with operands of the [integral types](../keywords/integral-types-table.md):</span></span>

- <span data-ttu-id="8db0b-105">Birli [ `~` (bit düzeyinde tamamlayıcı)](#bitwise-complement-operator-) işleci</span><span class="sxs-lookup"><span data-stu-id="8db0b-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="8db0b-106">İkili [ `<<` (sola kaydırma)](#left-shift-operator-) ve [ `>>` (sağa kaydırma)](#right-shift-operator-) kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="8db0b-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="8db0b-107">İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal veya)](#logical-or-operator-), ve [ `^` (mantıksal XOR)](#logical-exclusive-or-operator-) işleçleri</span><span class="sxs-lookup"><span data-stu-id="8db0b-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="8db0b-108">Bu işleçler için tanımlanan `int`, `uint`, `long`, ve `ulong` türleri.</span><span class="sxs-lookup"><span data-stu-id="8db0b-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="8db0b-109">Her iki işlenen de integral türde olduğunda (`sbyte`, `byte`, `short`, `ushort`, veya `char`), değerlerine dönüştürülür `int` aynı zamanda bir işlemin sonuç türü olan türü.</span><span class="sxs-lookup"><span data-stu-id="8db0b-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="8db0b-110">Değerleri, işlenenleri farklı tamsayı türleri olduğunda, en yakın kapsayan integral türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8db0b-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="8db0b-111">Daha fazla bilgi için [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8db0b-112">`&`, `|`, Ve `^` işleçleri için işlenenler de tanımlanır `bool` türü.</span><span class="sxs-lookup"><span data-stu-id="8db0b-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="8db0b-113">Daha fazla bilgi için [Boolean mantıksal işleçler](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="8db0b-114">Bit düzeyinde kaydırma işleçlerini asla taşmaya neden ve aynı sonuçlar [checked ve unchecked](../keywords/checked-and-unchecked.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="8db0b-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="8db0b-115">Bit düzeyinde tamamlama işleci ~</span><span class="sxs-lookup"><span data-stu-id="8db0b-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="8db0b-116">`~` İşleci her bit ters çevirerek bir bit düzeyinde tamamlayıcı işlenenin üretir:</span><span class="sxs-lookup"><span data-stu-id="8db0b-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="8db0b-117">Ayrıca `~` sonlandırıcılar bildirmek için Sembol.</span><span class="sxs-lookup"><span data-stu-id="8db0b-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="8db0b-118">Daha fazla bilgi için [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="8db0b-119">Sola kaydırma işleci \<\<</span><span class="sxs-lookup"><span data-stu-id="8db0b-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="8db0b-120">`<<` İşleci, ilk işlenen tarafından ikinci işleneni tarafından tanımlanan bit sayısı kadar sola kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8db0b-120">The `<<` operator shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="8db0b-121">Sola kaydırma işleminin sonucu türü aralığının dışında olan ve düşük düzey boş bit konumları sıfır, aşağıdaki örnekte gösterildiği gibi ayarlar yüksek sıra bitleri atar:</span><span class="sxs-lookup"><span data-stu-id="8db0b-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="8db0b-122">Kaydırma işleçleri yalnızca tanımlandığından `int`, `uint`, `long`, ve `ulong` türlerini, her zaman bir işlemin sonucunu içeren en az 32 bit.</span><span class="sxs-lookup"><span data-stu-id="8db0b-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="8db0b-123">Birinci işlenenin başka bir integral türü ise (`sbyte`, `byte`, `short`, `ushort`, veya `char`), değeri dönüştürülür `int` türü, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="8db0b-123">If the first operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="8db0b-124">Hakkında bilgi için ikinci işleneni `<<` işleci tanımlar kaydırma sayısı, bkz: [kaydırma işleçlerinin sayısı](#shift-count-of-the-shift-operators) bölümü.</span><span class="sxs-lookup"><span data-stu-id="8db0b-124">For information about how the second operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="8db0b-125">Sağa kaydırma işleci >></span><span class="sxs-lookup"><span data-stu-id="8db0b-125">Right-shift operator >></span></span>

<span data-ttu-id="8db0b-126">`>>` İşleci kaydırır ilk işleneni sağ ikinci işleneni tarafından tanımlanan bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="8db0b-126">The `>>` operator shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="8db0b-127">Sağa kaydırma işlemi aşağıdaki örnekte gösterildiği gibi alt sıra bitleri atar:</span><span class="sxs-lookup"><span data-stu-id="8db0b-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="8db0b-128">Yüksek düzeyli boş bit konumları birinci işlenenin türünde şu şekilde göre ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="8db0b-128">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="8db0b-129">Birinci işlenenin türü ise [int](../keywords/int.md) veya [uzun](../keywords/long.md), sağa kaydırma işleci gerçekleştiren bir *aritmetik* shift: ilk en önemli bite (imza biti) değeri işlenen, yüksek sıralı boş bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="8db0b-129">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="8db0b-130">Diğer bir deyişle, ilk işlenen negatif ise yüksek düzeyli boş bit konumları sıfır olarak ayarlanır ve negatif ise birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8db0b-130">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="8db0b-131">Birinci işlenenin türü ise [uint](../keywords/uint.md) veya [ulong](../keywords/ulong.md), sağa kaydırma işleci gerçekleştiren bir *mantıksal* shift: yüksek düzeyli boş bit konumları her zaman sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8db0b-131">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="8db0b-132">Hakkında bilgi için ikinci işleneni `>>` işleci tanımlar kaydırma sayısı, bkz: [kaydırma işleçlerinin sayısı](#shift-count-of-the-shift-operators) bölümü.</span><span class="sxs-lookup"><span data-stu-id="8db0b-132">For information about how the second operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><span data-ttu-id="8db0b-133">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="8db0b-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="8db0b-134">`&` Kendi işlenenden bit seviyesinde mantıksal ve işlecini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="8db0b-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="8db0b-135">İşlenen için `bool` türü `&` işleci hesaplar [mantıksal AND](boolean-logical-operators.md#logical-and-operator-) işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="8db0b-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="8db0b-136">Birli `&` işleci [address-of işleci](and-operator.md#unary-address-of-operator).</span><span class="sxs-lookup"><span data-stu-id="8db0b-136">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="8db0b-137">Mantıksal Dışlayıcı veya işlecini ^</span><span class="sxs-lookup"><span data-stu-id="8db0b-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="8db0b-138">`^` İşleci hesaplar. bit düzeyinde mantıksal özel veya olarak da bilinen kendi işlenenden bit seviyesinde mantıksal XOR:</span><span class="sxs-lookup"><span data-stu-id="8db0b-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="8db0b-139">İşlenen için `bool` türü `^` işleci hesaplar [mantıksal XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="8db0b-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="8db0b-140">Mantıksal OR işlecinin |</span><span class="sxs-lookup"><span data-stu-id="8db0b-140">Logical OR operator |</span></span>

<span data-ttu-id="8db0b-141">`|` Kendi işlenenden bit seviyesinde mantıksal veya işlecini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="8db0b-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="8db0b-142">İşlenen için `bool` türü `|` işleci hesaplar [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="8db0b-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="8db0b-143">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="8db0b-143">Compound assignment</span></span>

<span data-ttu-id="8db0b-144">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="8db0b-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="8db0b-145">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="8db0b-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="8db0b-146">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8db0b-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="8db0b-147">Aşağıdaki örnek, kaydırma işleçleri ve bileşik atama ile bit kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8db0b-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="8db0b-148">Nedeniyle [sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions), sonucunu `op` işlemi olabilir değil türe örtük olarak dönüştürülebilir `T` , `x`.</span><span class="sxs-lookup"><span data-stu-id="8db0b-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="8db0b-149">Böyle bir durumda ise `op` önceden tanımlanmış bir işleç ve işlemin sonucu türüne açıkça dönüştürülebilir ise `T` , `x`, formun bir bileşik atama ifadesi `x op= y` eşdeğerdir `x = (T)(x op y)`, dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8db0b-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="8db0b-150">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="8db0b-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="8db0b-151">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="8db0b-151">Operator precedence</span></span>

<span data-ttu-id="8db0b-152">Aşağıdaki liste siparişleri bit düzeyinde ve en yüksek öncelikten en düşük başlangıç kaydırma işleçleri:</span><span class="sxs-lookup"><span data-stu-id="8db0b-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="8db0b-153">Bit düzeyinde tamamlama işleci `~`</span><span class="sxs-lookup"><span data-stu-id="8db0b-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="8db0b-154">Kaydırma işleçleri `<<` ve `>>`</span><span class="sxs-lookup"><span data-stu-id="8db0b-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="8db0b-155">Mantıksal AND işleci `&`</span><span class="sxs-lookup"><span data-stu-id="8db0b-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="8db0b-156">Özel mantıksal OR işleci `^`</span><span class="sxs-lookup"><span data-stu-id="8db0b-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="8db0b-157">Mantıksal OR işleci `|`</span><span class="sxs-lookup"><span data-stu-id="8db0b-157">Logical OR operator `|`</span></span>

<span data-ttu-id="8db0b-158">Parantez kullanın `()`İşleç önceliği tarafından belirlenen değerlendirmenin sırasını değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="8db0b-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="8db0b-159">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="8db0b-160">Kaydırma işleçleri kaydırma sayısı</span><span class="sxs-lookup"><span data-stu-id="8db0b-160">Shift count of the shift operators</span></span>

<span data-ttu-id="8db0b-161">Kaydırma işleçleri için `<<` ve `>>`, ikinci işlenenin türünde olmalıdır [int](../keywords/int.md) veya olan bir türü bir [örtülü sayısal dönüştürme önceden tanımlanmış](../keywords/implicit-numeric-conversions-table.md) için `int`.</span><span class="sxs-lookup"><span data-stu-id="8db0b-161">For the shift operators `<<` and `>>`, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="8db0b-162">İçin `x << count` ve `x >> count` ifadeleri, gerçek kaydırma sayısı türüne bağlıdır `x` gibi:</span><span class="sxs-lookup"><span data-stu-id="8db0b-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="8db0b-163">Varsa türünü `x` olduğu [int](../keywords/int.md) veya [uint](../keywords/uint.md), kaydırma sayısı düşük düzey tarafından tanımlanan *beş* ikinci işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="8db0b-163">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is defined by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="8db0b-164">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x1F` (veya `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="8db0b-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="8db0b-165">Varsa türünü `x` olduğu [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md), kaydırma sayısı düşük düzey tarafından tanımlanan *altı* ikinci işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="8db0b-165">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is defined by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="8db0b-166">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x3F` (veya `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="8db0b-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="8db0b-167">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="8db0b-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="8db0b-168">Mantıksal işleçler numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8db0b-168">Enumeration logical operators</span></span>

<span data-ttu-id="8db0b-169">`~`, `&`, `|`, Ve `^` işleçleri de tanımlanır için [numaralandırma](../keywords/enum.md) türü.</span><span class="sxs-lookup"><span data-stu-id="8db0b-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="8db0b-170">İşlenenler aynı numaralandırma türü için bir mantıksal işlemi temel tamsayı türüne karşılık gelen değerleri üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8db0b-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="8db0b-171">Örneğin, tüm `x` ve `y` bir numaralandırma türünün `T` bir temel türü ile `U`, `x & y` ifade aynı sonucu üretir `(T)((U)x & (U)y)` ifade.</span><span class="sxs-lookup"><span data-stu-id="8db0b-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="8db0b-172">İle tanımlanmış bir numaralandırma türü ile mantıksal bit düzeyinde işleçler kullanın [bayrakları](xref:System.FlagsAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8db0b-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="8db0b-173">Daha fazla bilgi için [bit bayrakları olarak numaralandırma türleri](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) bölümünü [Numaralandırma türleri](../../programming-guide/enumeration-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="8db0b-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8db0b-174">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="8db0b-174">Operator overloadability</span></span>

<span data-ttu-id="8db0b-175">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `~`, `<<`, `>>`, `&`, `|`, ve `^` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="8db0b-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="8db0b-176">İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8db0b-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="8db0b-177">Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="8db0b-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="8db0b-178">Kullanıcı tanımlı bir tür ederse `T` aşırı `<<` veya `>>` işleci, birinci işlenenin türü olmalıdır `T` ve ikinci işlenenin türünde olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="8db0b-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8db0b-179">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8db0b-179">C# language specification</span></span>

<span data-ttu-id="8db0b-180">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8db0b-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8db0b-181">Bit düzeyinde tamamlama işleci</span><span class="sxs-lookup"><span data-stu-id="8db0b-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="8db0b-182">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="8db0b-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="8db0b-183">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="8db0b-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="8db0b-184">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="8db0b-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="8db0b-185">Sayısal promosyonlar</span><span class="sxs-lookup"><span data-stu-id="8db0b-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="8db0b-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8db0b-186">See also</span></span>

- [<span data-ttu-id="8db0b-187">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8db0b-187">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8db0b-188">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8db0b-188">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8db0b-189">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8db0b-189">C# Operators</span></span>](index.md)
- [<span data-ttu-id="8db0b-190">Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="8db0b-190">Boolean logical operators</span></span>](boolean-logical-operators.md)