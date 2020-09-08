---
title: Bit düzeyinde and Shift işleçleri-C# başvurusu
description: İntegral türlerindeki işlenenleri olan bit düzeyinde mantıksal veya SHIFT işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- <<=_CSharpKeyword
- '>>=_CSharpKeyword'
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
ms.openlocfilehash: 061abc8bc37d166a3683be1d2ad920a083a8ea3b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515949"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="971d1-103">Bit düzeyinde and Shift işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="971d1-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="971d1-104">Aşağıdaki işleçler [integral sayısal türlerin](../builtin-types/integral-numeric-types.md) veya [char](../builtin-types/char.md) türünün işlenenleri ile bit düzeyinde veya SHIFT işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="971d1-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="971d1-105">Birli [ `~` (bit düzeyinde tamamlama)](#bitwise-complement-operator-) işleci</span><span class="sxs-lookup"><span data-stu-id="971d1-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="971d1-106">İkili [ `<<` (sol SHIFT)](#left-shift-operator-) ve [ `>>` (sağ SHIFT)](#right-shift-operator-) kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="971d1-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="971d1-107">İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal or)](#logical-or-operator-)ve [ `^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler</span><span class="sxs-lookup"><span data-stu-id="971d1-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="971d1-108">Bu işleçler,,, `int` `uint` `long` ve türleri için tanımlanır `ulong` .</span><span class="sxs-lookup"><span data-stu-id="971d1-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="971d1-109">Her iki işlenen de diğer integral türlerinde ( `sbyte` , `byte` ,, `short` `ushort` veya `char` ) olduğunda, değerleri `int` bir işlemin sonuç türü olan türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="971d1-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="971d1-110">İşlenenler farklı integral türlerindiğinde, değerleri, en yakın integral türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="971d1-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="971d1-111">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="971d1-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="971d1-112">`&`, `|` Ve `^` işleçleri tür işlenenleri için de tanımlanmıştır `bool` .</span><span class="sxs-lookup"><span data-stu-id="971d1-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="971d1-113">Daha fazla bilgi için bkz. [Boolean mantıksal işleçler](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="971d1-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="971d1-114">Bit düzeyinde ve kaydırma işlemleri hiçbir şekilde taşmaya neden olmaz ve [denetlenen ve işaretlenmeyen](../keywords/checked-and-unchecked.md) bağlamlarda aynı sonuçları üretir.</span><span class="sxs-lookup"><span data-stu-id="971d1-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="971d1-115">Bit düzeyinde tamamlama işleci ~</span><span class="sxs-lookup"><span data-stu-id="971d1-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="971d1-116">`~`İşleci her bir biti ters çevirerek işleneni bir bit düzeyinde tamamlayıcı üretir:</span><span class="sxs-lookup"><span data-stu-id="971d1-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="971d1-117">`~`Sonlandırıcıları bildirmek için sembolünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="971d1-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="971d1-118">Daha fazla bilgi için bkz. [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="971d1-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="971d1-119">Sola kaydırma işleci \<\<</span><span class="sxs-lookup"><span data-stu-id="971d1-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="971d1-120">`<<`İşleci sol taraftaki işlenenini [sağ işleneni tarafından tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre sola kaydırır.</span><span class="sxs-lookup"><span data-stu-id="971d1-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="971d1-121">Aşağıdaki örnekte gösterildiği gibi, sol SHIFT işlemi, sonuç türü aralığının dışındaki yüksek sıralı bitleri atar ve düşük sıralı boş bit konumlarını sıfıra ayarlar:</span><span class="sxs-lookup"><span data-stu-id="971d1-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](snippets/shared/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="971d1-122">SHIFT işleçleri yalnızca,, ve türleri için tanımlandığından `int` , `uint` `long` `ulong` bir işlemin sonucu her zaman en az 32 bit içerir.</span><span class="sxs-lookup"><span data-stu-id="971d1-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="971d1-123">Sol işlenen başka bir integral türü ( `sbyte` , `byte` ,, `short` `ushort` , veya `char` ) ise, `int` Aşağıdaki örnekte gösterildiği gibi, değeri türüne dönüştürülür:</span><span class="sxs-lookup"><span data-stu-id="971d1-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](snippets/shared/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="971d1-124">İşlecin sağ işleneninin kaydırma sayısını tanımladığı hakkında daha fazla bilgi için `<<` [SHIFT Operators bölümünün kaydırma](#shift-count-of-the-shift-operators) sayısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="971d1-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="971d1-125">Sağa kaydırma işleci >></span><span class="sxs-lookup"><span data-stu-id="971d1-125">Right-shift operator >></span></span>

<span data-ttu-id="971d1-126">`>>`İşleci, sol işlenenin [sağ işleneni tarafından tanımlanan bit sayısına](#shift-count-of-the-shift-operators)göre sağa kayar.</span><span class="sxs-lookup"><span data-stu-id="971d1-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="971d1-127">Aşağıdaki örnekte gösterildiği gibi, doğru kaydırma işlemi düşük sıralı bitleri atar:</span><span class="sxs-lookup"><span data-stu-id="971d1-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](snippets/shared/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="971d1-128">Yüksek sıralı boş bit konumları, sol taraftaki işlenenin türüne göre aşağıdaki gibi ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="971d1-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="971d1-129">Sol işlenen türü `int` veya ise `long` , sağ SHIFT işleci bir *Aritmetik* kaydırma gerçekleştirir: sol işlenenin en önemli bit (işaret biti) değeri, yüksek sıralı boş bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="971d1-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="971d1-130">Diğer bir deyişle, sol işlenen negatif olmayan ve negatifse bir tane olarak ayarlandıysa, yüksek sıralı boş bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="971d1-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](snippets/shared/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="971d1-131">Sol işlenen veya türünde ise `uint` `ulong` , sağ SHIFT işleci bir *mantıksal* kaydırma gerçekleştirir: yüksek sıralı boş bit konumları her zaman sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="971d1-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](snippets/shared/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="971d1-132">İşlecin sağ işleneninin kaydırma sayısını tanımladığı hakkında daha fazla bilgi için `>>` [SHIFT Operators bölümünün kaydırma](#shift-count-of-the-shift-operators) sayısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="971d1-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a> <span data-ttu-id="971d1-133">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="971d1-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="971d1-134">`&`İşleci, tam sayı işlenenlerinin bit düzeyinde MANTıKSAL ve işlecini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="971d1-134">The `&` operator computes the bitwise logical AND of its integral operands:</span></span>

[!code-csharp-interactive[bitwise AND](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="971d1-135">`bool`İşlenenler için işleç, `&` işlenenlerinin [mantıksal ve](boolean-logical-operators.md#logical-and-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="971d1-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="971d1-136">Birli `&` işleç [Adres işleçtir](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="971d1-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="971d1-137">Mantıksal dışlamalı OR işleci ^</span><span class="sxs-lookup"><span data-stu-id="971d1-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="971d1-138">`^`İşleci, tam bit düzeyinde mantıksal dışlamalı veya tam sayı işlenenlerinin bit düzeyinde MANTıKSAL XOR olarak da bilinen değerini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="971d1-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its integral operands:</span></span>

[!code-csharp-interactive[bitwise XOR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="971d1-139">`bool`İşlenenler için işleç, `^` işlenenlerinin [MANTıKSAL dışlamalı veya](boolean-logical-operators.md#logical-exclusive-or-operator-) ' ı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="971d1-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="971d1-140">Mantıksal OR işleci |</span><span class="sxs-lookup"><span data-stu-id="971d1-140">Logical OR operator |</span></span>

<span data-ttu-id="971d1-141">`|`İşleci, tamsayı işlenenlerinin bit düzeyinde MANTıKSAL veya bir değerini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="971d1-141">The `|` operator computes the bitwise logical OR of its integral operands:</span></span>

[!code-csharp-interactive[bitwise OR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="971d1-142">`bool`İşlenenler için işleç, `|` işlenenlerinin [mantıksal veya](boolean-logical-operators.md#logical-or-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="971d1-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="971d1-143">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="971d1-143">Compound assignment</span></span>

<span data-ttu-id="971d1-144">Bir ikili işleci için `op` , formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="971d1-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="971d1-145">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="971d1-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="971d1-146">hariç `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="971d1-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="971d1-147">Aşağıdaki örnek, bileşik atamanın bit düzeyinde ve kaydırma işleçleriyle kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="971d1-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="971d1-148">[Sayısal yükseltmeler](~/_csharplang/spec/expressions.md#numeric-promotions)nedeniyle, `op` işlemin sonucu örtük olarak türüne dönüştürülebilir olmayabilir `T` `x` .</span><span class="sxs-lookup"><span data-stu-id="971d1-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="971d1-149">Böyle bir durumda, `op` önceden tanımlanmış bir işleçse ve işlemin sonucu türüne açıkça dönüştürülebilir ise, `T` `x` formun bileşik atama ifadesi `x op= y` öğesine eşdeğerdir `x = (T)(x op y)` , ancak `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="971d1-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="971d1-150">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="971d1-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="971d1-151">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="971d1-151">Operator precedence</span></span>

<span data-ttu-id="971d1-152">Aşağıdaki liste, en yüksek öncelikten en düşüğe başlayarak bit düzeyinde ve kaydırma işleçlerini sıralar:</span><span class="sxs-lookup"><span data-stu-id="971d1-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="971d1-153">Bit düzeyinde tamamlama işleci `~`</span><span class="sxs-lookup"><span data-stu-id="971d1-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="971d1-154">SHIFT işleçleri `<<` ve `>>`</span><span class="sxs-lookup"><span data-stu-id="971d1-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="971d1-155">Mantıksal AND işleci `&`</span><span class="sxs-lookup"><span data-stu-id="971d1-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="971d1-156">Mantıksal dışlamalı OR işleci `^`</span><span class="sxs-lookup"><span data-stu-id="971d1-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="971d1-157">Mantıksal OR işleci `|`</span><span class="sxs-lookup"><span data-stu-id="971d1-157">Logical OR operator `|`</span></span>

<span data-ttu-id="971d1-158">`()`İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantezleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="971d1-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/shared/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="971d1-159">Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="971d1-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="971d1-160">Kaydırma işleçlerinin kaydırma sayısı</span><span class="sxs-lookup"><span data-stu-id="971d1-160">Shift count of the shift operators</span></span>

<span data-ttu-id="971d1-161">SHIFT işleçleri ve için `<<` `>>` sağ işlenen türü `int` veya [önceden tanımlanmış örtük sayısal dönüştürmeye](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) sahip bir tür olmalıdır `int` .</span><span class="sxs-lookup"><span data-stu-id="971d1-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="971d1-162">`x << count`Ve ifadeleri için `x >> count` , gerçek kaydırma sayısı `x` aşağıdaki şekilde türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="971d1-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="971d1-163">Türü `x` `int` veya ise `uint` , kaydırma sayısı sağ işlenenin düşük sıralı *beş* biti tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="971d1-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="971d1-164">Diğer bir deyişle, kaydırma sayısı `count & 0x1F` (veya) öğesinden hesaplanır `count & 0b_1_1111` .</span><span class="sxs-lookup"><span data-stu-id="971d1-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="971d1-165">Türü `x` `long` veya ise `ulong` , kaydırma sayısı sağ işlenenin alt-sırası *altı* bitsiyle tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="971d1-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="971d1-166">Diğer bir deyişle, kaydırma sayısı `count & 0x3F` (veya) öğesinden hesaplanır `count & 0b_11_1111` .</span><span class="sxs-lookup"><span data-stu-id="971d1-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="971d1-167">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="971d1-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](snippets/shared/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="971d1-168">Yukarıdaki örnekte gösterildiği gibi, sağ işlenenin değeri sol işlenendeki bit sayısından büyük olsa da, bir vardiya işleminin sonucu sıfır olmayan bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="971d1-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="971d1-169">Sabit listesi mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="971d1-169">Enumeration logical operators</span></span>

<span data-ttu-id="971d1-170">`~`,, `&` `|` Ve `^` işleçleri her bir [numaralandırma](../builtin-types/enum.md) türü tarafından da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="971d1-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="971d1-171">Aynı numaralandırma türünün işlenenleri için, temel alınan integral türünün karşılık gelen değerlerinde bir mantıksal işlem gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="971d1-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="971d1-172">Örneğin, `x` `y` temel alınan bir tür ve bir numaralandırma türü için `T` ifade, `U` `x & y` ifadesiyle aynı sonucu üretir `(T)((U)x & (U)y)` .</span><span class="sxs-lookup"><span data-stu-id="971d1-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="971d1-173">Genellikle, [Flags](xref:System.FlagsAttribute) özniteliğiyle tanımlanan bir numaralandırma türü ile bit düzeyinde mantıksal işleçler kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="971d1-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="971d1-174">Daha fazla bilgi için [Listeleme türleri](../builtin-types/enum.md) makalesinin [numaralandırma türleri bit bayrakları](../builtin-types/enum.md#enumeration-types-as-bit-flags) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="971d1-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="971d1-175">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="971d1-175">Operator overloadability</span></span>

<span data-ttu-id="971d1-176">Kullanıcı tanımlı bir tür,, [overload](operator-overloading.md) ,, `~` , `<<` `>>` `&` `|` ve `^` işleçlerini aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="971d1-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="971d1-177">İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="971d1-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="971d1-178">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="971d1-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="971d1-179">Kullanıcı tanımlı bir tür `T` `<<` veya işlecini aşırı `>>` yükletir, sol taraftaki işlenenin türü olmalıdır `T` ve sağ işlenen türü olmalıdır `int` .</span><span class="sxs-lookup"><span data-stu-id="971d1-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="971d1-180">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="971d1-180">C# language specification</span></span>

<span data-ttu-id="971d1-181">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="971d1-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="971d1-182">Bit düzeyinde tamamlama işleci</span><span class="sxs-lookup"><span data-stu-id="971d1-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="971d1-183">Kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="971d1-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="971d1-184">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="971d1-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="971d1-185">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="971d1-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="971d1-186">Sayısal yükseltmeler</span><span class="sxs-lookup"><span data-stu-id="971d1-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="971d1-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="971d1-187">See also</span></span>

- [<span data-ttu-id="971d1-188">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="971d1-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="971d1-189">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="971d1-189">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="971d1-190">Boole mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="971d1-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
