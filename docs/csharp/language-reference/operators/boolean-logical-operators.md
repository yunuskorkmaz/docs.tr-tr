---
title: Boolean mantıksal işleçler-C# başvurusu
description: Mantıksal olumsuzlama, birlikte (ve) ve kapsamlı ve dışlamalı (veya) işlemleri Boolean işlenenleriyle gerçekleştiren C# işleçleri hakkında bilgi edinin.
ms.date: 06/29/2020
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
- '|=_CSharpKeyword'
- ^=_CSharpKeyword
- '&=_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 2a67542e25ddb258602b4005a71b565cf6522917
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855146"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="c624d-103">Boole mantıksal işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c624d-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="c624d-104">Aşağıdaki işleçler [bool](../builtin-types/bool.md) işlenenleri olan mantıksal işlemler gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="c624d-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="c624d-105">Birli [ `!` (mantıksal değilleme)](#logical-negation-operator-) işleci.</span><span class="sxs-lookup"><span data-stu-id="c624d-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="c624d-106">İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal or)](#logical-or-operator-)ve [ `^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler.</span><span class="sxs-lookup"><span data-stu-id="c624d-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="c624d-107">Bu operatörler her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c624d-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="c624d-108">İkili [ `&&` (Koşullu mantıksal and)](#conditional-logical-and-operator-) ve [ `||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="c624d-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="c624d-109">Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c624d-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="c624d-110">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için,, `&` `|` ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c624d-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="c624d-111">Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c624d-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="c624d-112">Mantıksal Değilleme İşleci!</span><span class="sxs-lookup"><span data-stu-id="c624d-112">Logical negation operator !</span></span>

<span data-ttu-id="c624d-113">Birli önek `!` işleci, işleneninin mantıksal olumsuzunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="c624d-114">Diğer bir deyişle, `true` işlenen olarak değerlendirilirse, ve işleneni şunu değerleniyorsa üretir `false` `false` `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="c624d-115">C# 8,0 ' den başlayarak birli sonek `!` operatörü [null-forverme işleçtir](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="c624d-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="c624d-116">Mantıksal AND işleci&amp;</span><span class="sxs-lookup"><span data-stu-id="c624d-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="c624d-117">`&`İşleci, işlenenlerinin MANTıKSAL ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="c624d-118">Sonucu `x & y` `true` her ikisi de olarak değerlendirilir `x` `y` `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="c624d-119">Aksi takdirde, sonuç olur `false` .</span><span class="sxs-lookup"><span data-stu-id="c624d-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="c624d-120">`&`İşleç, sol işlenen olarak değerlendirilse bile her iki işleneni de değerlendirir `false` , böylece işlem sonucu `false` sağ işlenen değerden bağımsız olarak olur.</span><span class="sxs-lookup"><span data-stu-id="c624d-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="c624d-121">Aşağıdaki örnekte, işlecinin sağ işleneni, `&` sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="c624d-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="c624d-122">[Koşullu MANTıKSAL and işleci](#conditional-logical-and-operator-) `&&` Ayrıca IŞLENENLERININ mantıksal ve işlecini hesaplar, ancak sol işlenen olarak değerlendirilirse sağ işleneni değerlendirmez `false` .</span><span class="sxs-lookup"><span data-stu-id="c624d-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="c624d-123">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `&` işleç, işlenenlerinin [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="c624d-124">Birli `&` işleç [Adres işleçtir](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="c624d-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="c624d-125">Mantıksal dışlamalı OR işleci ^</span><span class="sxs-lookup"><span data-stu-id="c624d-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="c624d-126">`^`İşleci, işlenenlerinin MANTıKSAL XOR 'ı olarak da bilinen mantıksal dışlamalı veya hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="c624d-127">Sonucu olarak `x ^ y` değerlendirilir ve değerlendiriyor ya da olarak değerlendirilir ve olarak değerlendirilir `true` `x` `true` `y` `false` `x` `false` `y` `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="c624d-128">Aksi takdirde, sonuç olur `false` .</span><span class="sxs-lookup"><span data-stu-id="c624d-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="c624d-129">Diğer bir deyişle, `bool` işleç, işlenenleri `^` [eşitsizlik işleciyle](equality-operators.md#inequality-operator-) aynı sonucu hesaplar `!=` .</span><span class="sxs-lookup"><span data-stu-id="c624d-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="c624d-130">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için, `^` işleç [bit DÜZEYINDE mantıksal dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işlenenleri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="c624d-131">Mantıksal OR işleci |</span><span class="sxs-lookup"><span data-stu-id="c624d-131">Logical OR operator |</span></span>

<span data-ttu-id="c624d-132">`|`İşleci, işlenenlerinin MANTıKSAL veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="c624d-133">Sonucu, ya `x | y` `true` da `x` `y` olarak değerlendirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="c624d-134">Aksi takdirde, sonuç olur `false` .</span><span class="sxs-lookup"><span data-stu-id="c624d-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="c624d-135">`|`İşleç, sol işlenen olarak değerlendirilse bile her iki işleneni de değerlendirir `true` , böylece işlem sonucu `true` sağ işlenen değerden bağımsız olarak olur.</span><span class="sxs-lookup"><span data-stu-id="c624d-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="c624d-136">Aşağıdaki örnekte, işlecinin sağ işleneni, `|` sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="c624d-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="c624d-137">[Koşullu MANTıKSAL or işleci](#conditional-logical-or-operator-) `||` Ayrıca, işlenenlerinin mantıksal veya işlecini hesaplar, ancak sol işlenen olarak değerlendirilirse sağ işleneni değerlendirmez `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="c624d-138">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `|` işleç, işlenenlerinin [bit düzeyinde mantıksal veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a><span data-ttu-id="c624d-139">Koşullu mantıksal AND işleci&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="c624d-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="c624d-140">`&&`"Kısa devre dışı" MANTıKSAL and işleci olarak da bilinen koşullu MANTıKSAL and işleci, işlenenlerinin MANTıKSAL ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="c624d-141">Sonucu `x && y` `true` her ikisi de olarak değerlendirilir `x` `y` `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="c624d-142">Aksi takdirde, sonuç olur `false` .</span><span class="sxs-lookup"><span data-stu-id="c624d-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="c624d-143">`x`, Olarak değerlendirilirse `false` , `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c624d-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="c624d-144">Aşağıdaki örnekte, işlecinin sağ işleneni, `&&` sol taraftaki işlenen şu şekilde değerlendirildiğinde gerçekleştirilmeyen bir yöntem çağrıdır `false` :</span><span class="sxs-lookup"><span data-stu-id="c624d-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="c624d-145">[MANTıKSAL and işleci](#logical-and-operator-) , `&` işlenenlerinin mantıksal ve işlecini de hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c624d-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="c624d-146">Koşullu mantıksal OR işleci | |</span><span class="sxs-lookup"><span data-stu-id="c624d-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="c624d-147">`||`"Kısa devre dışı" MANTıKSAL or işleci olarak da bilinen koşullu MANTıKSAL or işleci, işlenenlerinin MANTıKSAL veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c624d-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="c624d-148">Sonucu, ya `x || y` `true` da `x` `y` olarak değerlendirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="c624d-149">Aksi takdirde, sonuç olur `false` .</span><span class="sxs-lookup"><span data-stu-id="c624d-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="c624d-150">`x`, Olarak değerlendirilirse `true` , `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c624d-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="c624d-151">Aşağıdaki örnekte, işlecinin sağ işleneni, `||` sol taraftaki işlenen şu şekilde değerlendirildiğinde gerçekleştirilmeyen bir yöntem çağrıdır `true` :</span><span class="sxs-lookup"><span data-stu-id="c624d-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="c624d-152">[MANTıKSAL or işleci](#logical-or-operator-) `|` Ayrıca işlenenlerinin mantıksal veya ' lerini hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c624d-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="c624d-153">Null yapılabilir Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="c624d-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="c624d-154">`bool?`İşlenenler için [ `&` (mantıksal ve)](#logical-and-operator-) ve [ `|` (mantıksal or)](#logical-or-operator-) işleçleri aşağıdaki gibi üç değerli mantığı destekler:</span><span class="sxs-lookup"><span data-stu-id="c624d-154">For `bool?` operands, the [`&` (logical AND)](#logical-and-operator-) and [`|` (logical OR)](#logical-or-operator-) operators support the three-valued logic as follows:</span></span>

- <span data-ttu-id="c624d-155">`&`İşleci `true` yalnızca işlenenlerinin değerlendirmesi durumunda üretir `true` .</span><span class="sxs-lookup"><span data-stu-id="c624d-155">The `&` operator produces `true` only if both its operands evaluate to `true`.</span></span> <span data-ttu-id="c624d-156">Ya da `x` `y` olarak değerlendirilirse `false` , `x & y` `false` (başka bir işlenen olarak değerlendirilen bile) üretir `null` .</span><span class="sxs-lookup"><span data-stu-id="c624d-156">If either `x` or `y` evaluates to `false`, `x & y` produces `false` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="c624d-157">Aksi takdirde, sonucu `x & y` olur `null` .</span><span class="sxs-lookup"><span data-stu-id="c624d-157">Otherwise, the result of `x & y` is `null`.</span></span>

- <span data-ttu-id="c624d-158">`|`İşleci `false` yalnızca işlenenlerinin değerlendirmesi durumunda üretir `false` .</span><span class="sxs-lookup"><span data-stu-id="c624d-158">The `|` operator produces `false` only if both its operands evaluate to `false`.</span></span> <span data-ttu-id="c624d-159">Ya da `x` `y` olarak değerlendirilirse `true` , `x | y` `true` (başka bir işlenen olarak değerlendirilen bile) üretir `null` .</span><span class="sxs-lookup"><span data-stu-id="c624d-159">If either `x` or `y` evaluates to `true`, `x | y` produces `true` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="c624d-160">Aksi takdirde, sonucu `x | y` olur `null` .</span><span class="sxs-lookup"><span data-stu-id="c624d-160">Otherwise, the result of `x | y` is `null`.</span></span>

<span data-ttu-id="c624d-161">Aşağıdaki tabloda bu anlambilimi sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="c624d-161">The following table presents that semantics:</span></span>

|<span data-ttu-id="c624d-162">x</span><span class="sxs-lookup"><span data-stu-id="c624d-162">x</span></span>|<span data-ttu-id="c624d-163">y</span><span class="sxs-lookup"><span data-stu-id="c624d-163">y</span></span>|<span data-ttu-id="c624d-164">x&y</span><span class="sxs-lookup"><span data-stu-id="c624d-164">x&y</span></span>|<span data-ttu-id="c624d-165">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="c624d-165">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="c624d-166">true</span><span class="sxs-lookup"><span data-stu-id="c624d-166">true</span></span>|<span data-ttu-id="c624d-167">true</span><span class="sxs-lookup"><span data-stu-id="c624d-167">true</span></span>|<span data-ttu-id="c624d-168">true</span><span class="sxs-lookup"><span data-stu-id="c624d-168">true</span></span>|<span data-ttu-id="c624d-169">true</span><span class="sxs-lookup"><span data-stu-id="c624d-169">true</span></span>|  
|<span data-ttu-id="c624d-170">true</span><span class="sxs-lookup"><span data-stu-id="c624d-170">true</span></span>|<span data-ttu-id="c624d-171">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-171">false</span></span>|<span data-ttu-id="c624d-172">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-172">false</span></span>|<span data-ttu-id="c624d-173">true</span><span class="sxs-lookup"><span data-stu-id="c624d-173">true</span></span>|  
|<span data-ttu-id="c624d-174">true</span><span class="sxs-lookup"><span data-stu-id="c624d-174">true</span></span>|<span data-ttu-id="c624d-175">null</span><span class="sxs-lookup"><span data-stu-id="c624d-175">null</span></span>|<span data-ttu-id="c624d-176">null</span><span class="sxs-lookup"><span data-stu-id="c624d-176">null</span></span>|<span data-ttu-id="c624d-177">true</span><span class="sxs-lookup"><span data-stu-id="c624d-177">true</span></span>|  
|<span data-ttu-id="c624d-178">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-178">false</span></span>|<span data-ttu-id="c624d-179">true</span><span class="sxs-lookup"><span data-stu-id="c624d-179">true</span></span>|<span data-ttu-id="c624d-180">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-180">false</span></span>|<span data-ttu-id="c624d-181">true</span><span class="sxs-lookup"><span data-stu-id="c624d-181">true</span></span>|  
|<span data-ttu-id="c624d-182">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-182">false</span></span>|<span data-ttu-id="c624d-183">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-183">false</span></span>|<span data-ttu-id="c624d-184">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-184">false</span></span>|<span data-ttu-id="c624d-185">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-185">false</span></span>|  
|<span data-ttu-id="c624d-186">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-186">false</span></span>|<span data-ttu-id="c624d-187">null</span><span class="sxs-lookup"><span data-stu-id="c624d-187">null</span></span>|<span data-ttu-id="c624d-188">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-188">false</span></span>|<span data-ttu-id="c624d-189">null</span><span class="sxs-lookup"><span data-stu-id="c624d-189">null</span></span>|  
|<span data-ttu-id="c624d-190">null</span><span class="sxs-lookup"><span data-stu-id="c624d-190">null</span></span>|<span data-ttu-id="c624d-191">true</span><span class="sxs-lookup"><span data-stu-id="c624d-191">true</span></span>|<span data-ttu-id="c624d-192">null</span><span class="sxs-lookup"><span data-stu-id="c624d-192">null</span></span>|<span data-ttu-id="c624d-193">true</span><span class="sxs-lookup"><span data-stu-id="c624d-193">true</span></span>|  
|<span data-ttu-id="c624d-194">null</span><span class="sxs-lookup"><span data-stu-id="c624d-194">null</span></span>|<span data-ttu-id="c624d-195">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-195">false</span></span>|<span data-ttu-id="c624d-196">yanlış</span><span class="sxs-lookup"><span data-stu-id="c624d-196">false</span></span>|<span data-ttu-id="c624d-197">null</span><span class="sxs-lookup"><span data-stu-id="c624d-197">null</span></span>|  
|<span data-ttu-id="c624d-198">null</span><span class="sxs-lookup"><span data-stu-id="c624d-198">null</span></span>|<span data-ttu-id="c624d-199">null</span><span class="sxs-lookup"><span data-stu-id="c624d-199">null</span></span>|<span data-ttu-id="c624d-200">null</span><span class="sxs-lookup"><span data-stu-id="c624d-200">null</span></span>|<span data-ttu-id="c624d-201">null</span><span class="sxs-lookup"><span data-stu-id="c624d-201">null</span></span>|  

<span data-ttu-id="c624d-202">Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c624d-202">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="c624d-203">Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c624d-203">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="c624d-204">Böyle bir işleç `null` , işlenenlerinin herhangi biri olarak değerlendirilirse üretir `null` .</span><span class="sxs-lookup"><span data-stu-id="c624d-204">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="c624d-205">Ancak, `&` ve `|` işleçleri işlenenlerden biri olarak değerlendirilse bile null olmayan bir üretebilir `null` .</span><span class="sxs-lookup"><span data-stu-id="c624d-205">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="c624d-206">Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türleri](../builtin-types/nullable-value-types.md) makalesinin [yükseltilmemiş işleçleri](../builtin-types/nullable-value-types.md#lifted-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c624d-206">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="c624d-207">Ayrıca, `!` `^` `bool?` Aşağıdaki örnekte gösterildiği gibi işlenenlerle birlikte ve işleçlerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c624d-207">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="c624d-208">Koşullu mantıksal işleçler `&&` ve `||` `bool?` işlenenleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c624d-208">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="c624d-209">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="c624d-209">Compound assignment</span></span>

<span data-ttu-id="c624d-210">Bir ikili işleci için `op` , formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="c624d-210">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="c624d-211">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="c624d-211">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="c624d-212">hariç `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c624d-212">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="c624d-213">`&` `|` `^` Aşağıdaki örnekte gösterildiği gibi,, ve işleçleri bileşik atamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="c624d-213">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="c624d-214">Koşullu mantıksal işleçler `&&` ve `||` bileşik atamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c624d-214">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="c624d-215">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="c624d-215">Operator precedence</span></span>

<span data-ttu-id="c624d-216">Aşağıdaki liste, en yüksek öncelikten başlayarak mantıksal işleçleri en düşüğe göre sıralar:</span><span class="sxs-lookup"><span data-stu-id="c624d-216">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="c624d-217">Mantıksal Değilleme İşleci`!`</span><span class="sxs-lookup"><span data-stu-id="c624d-217">Logical negation operator `!`</span></span>
- <span data-ttu-id="c624d-218">Mantıksal AND işleci`&`</span><span class="sxs-lookup"><span data-stu-id="c624d-218">Logical AND operator `&`</span></span>
- <span data-ttu-id="c624d-219">Mantıksal dışlamalı OR işleci`^`</span><span class="sxs-lookup"><span data-stu-id="c624d-219">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="c624d-220">Mantıksal OR işleci`|`</span><span class="sxs-lookup"><span data-stu-id="c624d-220">Logical OR operator `|`</span></span>
- <span data-ttu-id="c624d-221">Koşullu mantıksal AND işleci`&&`</span><span class="sxs-lookup"><span data-stu-id="c624d-221">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="c624d-222">Koşullu mantıksal OR işleci`||`</span><span class="sxs-lookup"><span data-stu-id="c624d-222">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="c624d-223">`()`İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantezleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="c624d-223">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="c624d-224">Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c624d-224">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c624d-225">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="c624d-225">Operator overloadability</span></span>

<span data-ttu-id="c624d-226">Kullanıcı tanımlı bir tür,, [overload](operator-overloading.md) , `!` `&` `|` ve işleçlerini aşırı yükleyebilir `^` .</span><span class="sxs-lookup"><span data-stu-id="c624d-226">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="c624d-227">İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c624d-227">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="c624d-228">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="c624d-228">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="c624d-229">Kullanıcı tanımlı bir tür koşullu mantıksal işleçleri `&&` ve ' i aşırı yükleyemez `||` .</span><span class="sxs-lookup"><span data-stu-id="c624d-229">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="c624d-230">Ancak, Kullanıcı tanımlı bir tür [true ve false işleçlerini](true-false-operators.md) ve `&` ya da işlecini belirli bir şekilde aşırı yükleiyorsa, `|` `&&` veya `||` işlemi sırasıyla bu türün işlenenleri için değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c624d-230">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="c624d-231">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c624d-231">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c624d-232">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c624d-232">C# language specification</span></span>

<span data-ttu-id="c624d-233">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="c624d-233">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c624d-234">Mantıksal değilleme işleci</span><span class="sxs-lookup"><span data-stu-id="c624d-234">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="c624d-235">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="c624d-235">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="c624d-236">Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="c624d-236">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="c624d-237">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="c624d-237">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="c624d-238">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c624d-238">See also</span></span>

- [<span data-ttu-id="c624d-239">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c624d-239">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c624d-240">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c624d-240">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="c624d-241">Bit düzeyinde ve kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="c624d-241">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
