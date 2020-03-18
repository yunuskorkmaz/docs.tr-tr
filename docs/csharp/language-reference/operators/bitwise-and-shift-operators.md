---
title: Bit yönünden ve kaydırma işleçleri - C# referansı
description: İntegral türlerinin operands ile bitwise mantıksal veya shift işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 54198368672e0c9324210a232c7851b5a90402cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399268"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="07fd5-103">Bit yönünde ve kaydırma işleçleri (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="07fd5-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="07fd5-104">Aşağıdaki işleçler, [integral sayısal türlerin intiyazları](../builtin-types/integral-numeric-types.md) veya [char](../builtin-types/char.md) türüyle bityönünde veya kaydırma işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="07fd5-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="07fd5-105">Unary [ `~` (bitwise kompleman)](#bitwise-complement-operator-) işleci</span><span class="sxs-lookup"><span data-stu-id="07fd5-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="07fd5-106">İkili [ `<<` (sol kaydırma)](#left-shift-operator-) ve [ `>>` (sağ kaydırma)](#right-shift-operator-) kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="07fd5-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="07fd5-107">İkili [ `&` (mantıksal AND)](#logical-and-operator-), [ `|` (mantıksal OR)](#logical-or-operator-)ve [ `^` (mantıksal özel OR)](#logical-exclusive-or-operator-) işleçleri</span><span class="sxs-lookup"><span data-stu-id="07fd5-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="07fd5-108">Bu işleçler `int`, `uint` `long`, `ulong` , ve türleri için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="07fd5-109">Her iki operands diğer integral`sbyte` `byte`türleri `short` `ushort`(, `char`, , , , `int` veya ), değerleri de bir işlemin sonucu türüdür, dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="07fd5-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="07fd5-110">Operandlar farklı integral türlerine sahip olduklarında, değerleri en yakın integral türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="07fd5-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="07fd5-111">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Sayısal promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="07fd5-112">`&`, `|`ve `^` işleçler de `bool` türünün operands için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="07fd5-113">Daha fazla bilgi için [Boolean mantıksal işleçleri'ne](boolean-logical-operators.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="07fd5-114">Bitwise ve shift işlemleri hiçbir zaman taşma neden ve [denetlenmiş ve işaretlenmemiş](../keywords/checked-and-unchecked.md) bağlamlarda aynı sonuçları üretmek.</span><span class="sxs-lookup"><span data-stu-id="07fd5-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="07fd5-115">Bitwise kompleman operatörü ~</span><span class="sxs-lookup"><span data-stu-id="07fd5-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="07fd5-116">Operatör, `~` her biti tersine çevirerek operand'ın biraz daha tamamlayıcısını üretir:</span><span class="sxs-lookup"><span data-stu-id="07fd5-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="07fd5-117">`~` Ayrıca sonlandırıcıları bildirmek için sembolü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07fd5-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="07fd5-118">Daha fazla bilgi için [Finalizers'a](../../programming-guide/classes-and-structs/destructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="07fd5-119">Sol kaydırma işleci\<\<</span><span class="sxs-lookup"><span data-stu-id="07fd5-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="07fd5-120">Operatör `<<` sol operand soldaki [operand'ı sağ operand'ı ile tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre kaydırır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="07fd5-121">Sol kaydırma işlemi, sonuç türünün aralığının dışında kalan yüksek sıralı bitleri atar ve aşağıdaki örnekte görüldüğü gibi düşük sıralı boş bit konumlarını sıfıra ayarlar:</span><span class="sxs-lookup"><span data-stu-id="07fd5-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="07fd5-122">Vardiya işleçleri `int`yalnızca , `uint`, `long`, `ulong` ve türleri için tanımlandıklarından, bir işlemin sonucu her zaman en az 32 bit içerir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="07fd5-123">Sol operand başka bir integral türüne`sbyte` `byte`aitse ( , `short`, , `ushort`, veya `char`, değeri aşağıdaki örnekte görüldüğü gibi, `int` türe dönüştürülür:</span><span class="sxs-lookup"><span data-stu-id="07fd5-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="07fd5-124">Operatörün `<<` sağ operand'ının vardiya sayısını nasıl tanımladığı hakkında bilgi [için, vardiya işleçleri bölümünün Shift sayısına](#shift-count-of-the-shift-operators) bakın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="07fd5-125">Sağ vites operatörü >></span><span class="sxs-lookup"><span data-stu-id="07fd5-125">Right-shift operator >></span></span>

<span data-ttu-id="07fd5-126">Operatör, `>>` sol operand'ı [sağ operand'ı tanımlayan bit sayısına](#shift-count-of-the-shift-operators)göre kaydırır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="07fd5-127">Sağ kaydırma işlemi, aşağıdaki örnekte görüldüğü gibi, düşük sıralı bitleri atar:</span><span class="sxs-lookup"><span data-stu-id="07fd5-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="07fd5-128">Yüksek sıralı boş bit konumları sol operand'ın türüne göre ayarlanır ve aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="07fd5-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="07fd5-129">Sol operand türündeyse `int` veya `long`sağ kaydırma işleci *aritmetik* bir kayma gerçekleştiriyorsa: sol operand'ın en önemli bitinin (işaret biti) değeri yüksek sıralı boş bit pozisyonlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="07fd5-130">Diğer bir süre, sol operand negatif değilse, yüksek sıralı boş bit konumları sıfıra ayarlanır ve negatifse bire ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="07fd5-131">Sol operand türündeyse `uint` veya `ulong`sağ kaydırma işleci *mantıksal* bir kayma gerçekleştiriyorsa: yüksek sıralı boş bit konumları her zaman sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="07fd5-132">Operatörün `>>` sağ operand'ının vardiya sayısını nasıl tanımladığı hakkında bilgi [için, vardiya işleçleri bölümünün Shift sayısına](#shift-count-of-the-shift-operators) bakın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="07fd5-133">Mantıksal VE işleç&amp;</span><span class="sxs-lookup"><span data-stu-id="07fd5-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="07fd5-134">İşletici, `&` bitwise mantıksal VE onun operands hesaplar:</span><span class="sxs-lookup"><span data-stu-id="07fd5-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="07fd5-135">Operands `bool` için, `&` operatör mantıksal [VE](boolean-logical-operators.md#logical-and-operator-) onun operands hesaplar.</span><span class="sxs-lookup"><span data-stu-id="07fd5-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="07fd5-136">Unary `&` [işleci, işlecin adresidir.](pointer-related-operators.md#address-of-operator-)</span><span class="sxs-lookup"><span data-stu-id="07fd5-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="07fd5-137">Mantıksal özel OR operatörü ^</span><span class="sxs-lookup"><span data-stu-id="07fd5-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="07fd5-138">İşletici, `^` bitwise mantıksal XOR olarak da bilinen bitwise mantıksal özel OR'unu operands'ını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="07fd5-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="07fd5-139">Operands `bool` için, `^` operatör onun operands [mantıksal özel OR](boolean-logical-operators.md#logical-exclusive-or-operator-) bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="07fd5-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="07fd5-140">Mantıksal OR işleci |</span><span class="sxs-lookup"><span data-stu-id="07fd5-140">Logical OR operator |</span></span>

<span data-ttu-id="07fd5-141">İşletici, `|` operandlarının bitwise mantıksal VEYA'sini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="07fd5-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="07fd5-142">Operands `bool` için, `|` operatör onun operands [mantıksal OR](boolean-logical-operators.md#logical-or-operator-) bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="07fd5-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="07fd5-143">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="07fd5-143">Compound assignment</span></span>

<span data-ttu-id="07fd5-144">Bir ikili `op`işleç için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="07fd5-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="07fd5-145">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="07fd5-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="07fd5-146">`x` bunun dışında sadece bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="07fd5-147">Aşağıdaki örnek, bitwise ve shift işleçleri ile bileşik atama kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="07fd5-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="07fd5-148">Sayısal [promosyonlar](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu dolaylı olarak türüne `T` dönüştürülebilir `x`olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="07fd5-149">Böyle bir durumda, `op` önceden tanımlanmış bir işleç ise ve işlemin sonucu açıkça `T` `x`türüne dönüştürülebilir ise `x op= y` , formun bileşik atama ifadesi eşdeğerdir `x = (T)(x op y)`, sadece bir kez değerlendirilir dışında. `x`</span><span class="sxs-lookup"><span data-stu-id="07fd5-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="07fd5-150">Aşağıdaki örnek, davranışı gösterir:</span><span class="sxs-lookup"><span data-stu-id="07fd5-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="07fd5-151">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="07fd5-151">Operator precedence</span></span>

<span data-ttu-id="07fd5-152">Aşağıdaki liste, en yüksek öncelikten en düşüke başlayarak bit yönünde ve kaydırma işleçlerini siparişleri verir:</span><span class="sxs-lookup"><span data-stu-id="07fd5-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="07fd5-153">Bitwise kompleman operatörü`~`</span><span class="sxs-lookup"><span data-stu-id="07fd5-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="07fd5-154">Shift `<<` operatörleri ve`>>`</span><span class="sxs-lookup"><span data-stu-id="07fd5-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="07fd5-155">Mantıksal VE işleç`&`</span><span class="sxs-lookup"><span data-stu-id="07fd5-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="07fd5-156">Mantıksal özel OR işleci`^`</span><span class="sxs-lookup"><span data-stu-id="07fd5-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="07fd5-157">Mantıksal VEYA işleci`|`</span><span class="sxs-lookup"><span data-stu-id="07fd5-157">Logical OR operator `|`</span></span>

<span data-ttu-id="07fd5-158">Operatör önceliği tarafından `()`dayatılan değerlendirme sırasını değiştirmek için parantez kullanın:</span><span class="sxs-lookup"><span data-stu-id="07fd5-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="07fd5-159">Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [C# işleçleri](index.md) makalesinin [Operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="07fd5-160">Vardiya operatörlerinin vardiya sayısı</span><span class="sxs-lookup"><span data-stu-id="07fd5-160">Shift count of the shift operators</span></span>

<span data-ttu-id="07fd5-161">Shift `<<` operatörleri ve `>>`, sağ operand türü veya `int` önceden tanımlanmış bir [örtülü sayısal dönüşüm](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) olan `int`bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="07fd5-162">Ve ifadeler için, gerçek kaydırma sayısı aşağıdaki gibi `x` türüne bağlıdır: `x >> count` `x << count`</span><span class="sxs-lookup"><span data-stu-id="07fd5-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="07fd5-163">Eğer `x` türü `int` veya `uint`, vardiya sayısı sağ operand düşük sıralı *beş* bit tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="07fd5-164">Diğer bir şey, vardiya sayısı `count & 0x1F` (veya) `count & 0b_1_1111`adresinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="07fd5-165">Eğer `x` türü `long` veya `ulong`, vardiya sayısı sağ operand düşük sıralı *altı* bit tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="07fd5-166">Diğer bir şey, vardiya sayısı `count & 0x3F` (veya) `count & 0b_11_1111`adresinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="07fd5-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="07fd5-167">Aşağıdaki örnek, davranışı gösterir:</span><span class="sxs-lookup"><span data-stu-id="07fd5-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="07fd5-168">Yukarıdaki örnekte de görüldüğü gibi, sağ operand değeri sol operandbit sayısından fazla olsa bile, bir kaydırma işleminin sonucu sıfır sızabilir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="07fd5-169">Numaralandırma mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="07fd5-169">Enumeration logical operators</span></span>

<span data-ttu-id="07fd5-170">, `~` `&`, `|`, `^` ve operatörler de herhangi bir [numaralandırma](../builtin-types/enum.md) türü tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="07fd5-171">Aynı numaralandırma türündeki operandlar için, altta yatan integral türünün karşılık gelen değerleri üzerinde mantıksal bir işlem gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="07fd5-172">Örneğin, altta `x` yatan `y` türü `T` `U`olan herhangi bir numaralandırma türü `x & y` için ifade, `(T)((U)x & (U)y)` ifadeyle aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="07fd5-173">Genellikle [Bayraklar](xref:System.FlagsAttribute) özniteliği ile tanımlanan bir numaralandırma türü ile bitwise mantıksal işleçleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="07fd5-174">Daha fazla bilgi için, Numaralandırma türleri makalesinin bit bayrakları bölümü [olarak Numaralandırma](../builtin-types/enum.md#enumeration-types-as-bit-flags) [türlerine](../builtin-types/enum.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="07fd5-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="07fd5-175">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="07fd5-175">Operator overloadability</span></span>

<span data-ttu-id="07fd5-176">Kullanıcı tanımlı bir `~`tür, `<<`, `>>` `&`, `|`, `^` , ve işleçleri [aşırı yükleyebilir.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="07fd5-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="07fd5-177">Bir ikili işleci aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="07fd5-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="07fd5-178">Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder.</span><span class="sxs-lookup"><span data-stu-id="07fd5-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="07fd5-179">Kullanıcı tanımlı bir `T` tür `<<` veya `>>` işleci aşırı yüklerse, sol operand'ın türü ve `T` sağ operand'ın türü olmalıdır. `int`</span><span class="sxs-lookup"><span data-stu-id="07fd5-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="07fd5-180">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="07fd5-180">C# language specification</span></span>

<span data-ttu-id="07fd5-181">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="07fd5-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="07fd5-182">Bitwise kompleman operatörü</span><span class="sxs-lookup"><span data-stu-id="07fd5-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="07fd5-183">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="07fd5-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="07fd5-184">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="07fd5-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="07fd5-185">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="07fd5-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="07fd5-186">Sayısal promosyonlar</span><span class="sxs-lookup"><span data-stu-id="07fd5-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="07fd5-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07fd5-187">See also</span></span>

- [<span data-ttu-id="07fd5-188">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="07fd5-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="07fd5-189">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="07fd5-189">C# operators</span></span>](index.md)
- [<span data-ttu-id="07fd5-190">Boole mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="07fd5-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
