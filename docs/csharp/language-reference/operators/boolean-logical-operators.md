---
title: Boole mantıksal işleçler- C# başvuru
description: Mantıksal olumsuzlama, birlikte (ve) ve kapsamlı ve dışlamalı (ya da) işlemleri Boolean işlenenleriyle gerçekleştiren işleçler hakkında C# bilgi edinin.
ms.date: 09/27/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
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
ms.openlocfilehash: f711bd04aeadb584eac1ecb0b644a36e2e496d08
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72290936"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="89129-103">Boole mantıksal işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="89129-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="89129-104">Aşağıdaki işleçler [bool](../keywords/bool.md) işlenenleri ile mantıksal işlemler gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="89129-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="89129-105">Birli [`!` (mantıksal değilleme)](#logical-negation-operator-) işleci.</span><span class="sxs-lookup"><span data-stu-id="89129-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="89129-106">İkili [`&` (MANTıKSAL ve)](#logical-and-operator-), [`|` (mantıksal or)](#logical-or-operator-)ve [`^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler.</span><span class="sxs-lookup"><span data-stu-id="89129-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="89129-107">Bu operatörler her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="89129-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="89129-108">İkili [`&&` (koşullu MANTıKSAL and)](#conditional-logical-and-operator-) ve [`||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="89129-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="89129-109">Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="89129-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="89129-110">[İntegral](../builtin-types/integral-numeric-types.md) türlerinin işlenenleri için, `&`, `|` ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="89129-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="89129-111">Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="89129-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="89129-112">Mantıksal Değilleme İşleci!</span><span class="sxs-lookup"><span data-stu-id="89129-112">Logical negation operator !</span></span>

<span data-ttu-id="89129-113">@No__t-0 işleci birli önek, işleneninin mantıksal olumsuzunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="89129-114">Diğer bir deyişle, işlenen `false` olarak değerlendirilirse `false` ' yi ve işlenen `true` ' e değerlendirilirse,  ' yi üretir:</span><span class="sxs-lookup"><span data-stu-id="89129-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="89129-115">8,0 ile C# başlayarak birli sonek `!` işleci bir [null-Forin işleci](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="89129-115">Starting with C# 8.0, the unary postfix `!` operator is a [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="89129-116">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="89129-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="89129-117">@No__t-0 işleci, işlenenlerinin mantıksal ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="89129-118">@No__t-0 ' ın sonucu, hem `x` hem de `y` `true` olarak değerlendirilir `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="89129-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="89129-119">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="89129-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="89129-120">@No__t-0 işleci, sol taraftaki işlenen `false` olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece sonuç sağ işlenen değerinden bağımsız olarak `false` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89129-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="89129-121">Aşağıdaki örnekte, `&` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="89129-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="89129-122">@No__t-1 [koşullu MANTıKSAL and işleci](#conditional-logical-and-operator-) , işlenenlerinin mantıksal ve ' lerini de hesaplar, ancak sol işlenen `false` olarak değerlendirilirse sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="89129-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="89129-123">İntegral türlerinin işlenenleri için `&` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-123">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="89129-124">Birli `&` işleci [Adres işleçtir](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="89129-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="89129-125">Mantıksal dışlamalı OR işleci ^</span><span class="sxs-lookup"><span data-stu-id="89129-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="89129-126">@No__t-0 işleci, işlenenlerinin mantıksal XOR olarak da bilinen mantıksal dışlamalı veya bir şekilde hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="89129-127">@No__t-0 ' ın sonucu `true` ' dir. `x` `true` ' ü değerlendiriyor ve `false` ' i  olarak değerlendirir ya da `x` `true` ' a değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="89129-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="89129-128">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="89129-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="89129-129">Diğer bir deyişle, `bool` işlenenleri için `^` işleci, [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=` ile aynı sonucu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="89129-130">İntegral türlerinin işlenenleri için, `^` işleci, işlenenlerinin [bit düzeyinde mantıksal dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) bunların işlenenleri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-130">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="89129-131">Mantıksal OR işleci |</span><span class="sxs-lookup"><span data-stu-id="89129-131">Logical OR operator |</span></span>

<span data-ttu-id="89129-132">@No__t-0 işleci, işlenenlerinin mantıksal veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="89129-133">@No__t-2 veya `y` ' ü `true` olarak değerlendirilirse `x | y` ' ın sonucu `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="89129-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="89129-134">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="89129-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="89129-135">@No__t-0 işleci, sol taraftaki işlenen `true` olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece sonuç sağ işlenen değerinden bağımsız olarak `true` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89129-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="89129-136">Aşağıdaki örnekte, `|` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="89129-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="89129-137">@No__t-1 [koşullu MANTıKSAL or işleci](#conditional-logical-or-operator-) , işlenenlerinin MANTıKSAL veya veya işlecini de hesaplar, ancak sol işlenen `true` olarak değerlendirilirse sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="89129-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="89129-138">İntegral türlerinin işlenenleri için `|` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-138">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="89129-139">Koşullu mantıksal AND işleci &amp; @ no__t-2</span><span class="sxs-lookup"><span data-stu-id="89129-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="89129-140">"Kısa devre dışı" mantıksal AND işleci olarak da bilinen Koşullu mantıksal AND işleci `&&`, işlenenlerinin mantıksal ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="89129-141">@No__t-0 ' ın sonucu, hem `x` hem de `y` `true` olarak değerlendirilir `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="89129-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="89129-142">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="89129-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="89129-143">@No__t-0 `false` olarak değerlendirilirse `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="89129-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="89129-144">Aşağıdaki örnekte, `&&` işlecinin sağ işleneni, sol taraftaki işlenen `false` olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="89129-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="89129-145">@No__t-1 [MANTıKSAL ve işleci](#logical-and-operator-) , işlenenlerinin mantıksal ve işlecini de hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="89129-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="89129-146">Koşullu mantıksal OR işleci | |</span><span class="sxs-lookup"><span data-stu-id="89129-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="89129-147">"Kısa devre dışı" mantıksal OR işleci olarak da bilinen Koşullu mantıksal OR işleci `||`, işlenenlerinin mantıksal veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="89129-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="89129-148">@No__t-2 veya `y` ' ü `true` olarak değerlendirilirse `x || y` ' ın sonucu `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="89129-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="89129-149">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="89129-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="89129-150">@No__t-0 `true` olarak değerlendirilirse `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="89129-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="89129-151">Aşağıdaki örnekte, `||` işlecinin sağ işleneni, sol taraftaki işlenen `true` olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="89129-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="89129-152">@No__t-1 [MANTıKSAL or işleci](#logical-or-operator-) , işlenenlerinin mantıksal veya her ikisini de hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="89129-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="89129-153">Null yapılabilir Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="89129-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="89129-154">@No__t-0 işlenenleri için, `&` ve `|` işleçleri üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="89129-154">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="89129-155">Bu işleçlerin semantiği aşağıdaki tablo tarafından tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="89129-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="89129-156">x</span><span class="sxs-lookup"><span data-stu-id="89129-156">x</span></span>|<span data-ttu-id="89129-157">Iz</span><span class="sxs-lookup"><span data-stu-id="89129-157">y</span></span>|<span data-ttu-id="89129-158">x & y</span><span class="sxs-lookup"><span data-stu-id="89129-158">x&y</span></span>|<span data-ttu-id="89129-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="89129-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="89129-160">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-160">true</span></span>|<span data-ttu-id="89129-161">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-161">true</span></span>|<span data-ttu-id="89129-162">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-162">true</span></span>|<span data-ttu-id="89129-163">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-163">true</span></span>|  
|<span data-ttu-id="89129-164">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-164">true</span></span>|<span data-ttu-id="89129-165">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-165">false</span></span>|<span data-ttu-id="89129-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-166">false</span></span>|<span data-ttu-id="89129-167">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-167">true</span></span>|  
|<span data-ttu-id="89129-168">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-168">true</span></span>|<span data-ttu-id="89129-169">değer</span><span class="sxs-lookup"><span data-stu-id="89129-169">null</span></span>|<span data-ttu-id="89129-170">değer</span><span class="sxs-lookup"><span data-stu-id="89129-170">null</span></span>|<span data-ttu-id="89129-171">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-171">true</span></span>|  
|<span data-ttu-id="89129-172">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-172">false</span></span>|<span data-ttu-id="89129-173">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-173">true</span></span>|<span data-ttu-id="89129-174">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-174">false</span></span>|<span data-ttu-id="89129-175">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-175">true</span></span>|  
|<span data-ttu-id="89129-176">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-176">false</span></span>|<span data-ttu-id="89129-177">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-177">false</span></span>|<span data-ttu-id="89129-178">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-178">false</span></span>|<span data-ttu-id="89129-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-179">false</span></span>|  
|<span data-ttu-id="89129-180">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-180">false</span></span>|<span data-ttu-id="89129-181">değer</span><span class="sxs-lookup"><span data-stu-id="89129-181">null</span></span>|<span data-ttu-id="89129-182">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-182">false</span></span>|<span data-ttu-id="89129-183">değer</span><span class="sxs-lookup"><span data-stu-id="89129-183">null</span></span>|  
|<span data-ttu-id="89129-184">değer</span><span class="sxs-lookup"><span data-stu-id="89129-184">null</span></span>|<span data-ttu-id="89129-185">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-185">true</span></span>|<span data-ttu-id="89129-186">değer</span><span class="sxs-lookup"><span data-stu-id="89129-186">null</span></span>|<span data-ttu-id="89129-187">doğru</span><span class="sxs-lookup"><span data-stu-id="89129-187">true</span></span>|  
|<span data-ttu-id="89129-188">değer</span><span class="sxs-lookup"><span data-stu-id="89129-188">null</span></span>|<span data-ttu-id="89129-189">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-189">false</span></span>|<span data-ttu-id="89129-190">yanlış</span><span class="sxs-lookup"><span data-stu-id="89129-190">false</span></span>|<span data-ttu-id="89129-191">değer</span><span class="sxs-lookup"><span data-stu-id="89129-191">null</span></span>|  
|<span data-ttu-id="89129-192">değer</span><span class="sxs-lookup"><span data-stu-id="89129-192">null</span></span>|<span data-ttu-id="89129-193">değer</span><span class="sxs-lookup"><span data-stu-id="89129-193">null</span></span>|<span data-ttu-id="89129-194">değer</span><span class="sxs-lookup"><span data-stu-id="89129-194">null</span></span>|<span data-ttu-id="89129-195">değer</span><span class="sxs-lookup"><span data-stu-id="89129-195">null</span></span>|  

<span data-ttu-id="89129-196">Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="89129-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="89129-197">Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89129-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="89129-198">Bu tür bir operatör, işlenenlerinden herhangi biri `null` ise `null` üretir.</span><span class="sxs-lookup"><span data-stu-id="89129-198">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="89129-199">Ancak, `&` ve `|` işleçleri, işlenenleri `null` olsa bile null olmayan bir şekilde üretebilir.</span><span class="sxs-lookup"><span data-stu-id="89129-199">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="89129-200">Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türlerini kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesindeki [işleçler](../../programming-guide/nullable-types/using-nullable-types.md#operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="89129-200">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="89129-201">Aşağıdaki örnekte gösterildiği gibi `!` ve `^` işleçlerini `bool?` işlenenleriyle de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89129-201">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="89129-202">@No__t-0 ve `||` Koşullu mantıksal işleçler `bool?` işlenenlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="89129-202">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="89129-203">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="89129-203">Compound assignment</span></span>

<span data-ttu-id="89129-204">Bir ikili işleci için `op`, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="89129-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="89129-205">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="89129-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="89129-206">`x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="89129-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="89129-207">@No__t-0, `|` ve `^` işleçleri, aşağıdaki örnekte gösterildiği gibi bileşik atamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="89129-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="89129-208">@No__t-0 ve `||` Koşullu mantıksal işleçler bileşik atamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="89129-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="89129-209">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="89129-209">Operator precedence</span></span>

<span data-ttu-id="89129-210">Aşağıdaki liste, en yüksek öncelikten başlayarak mantıksal işleçleri en düşüğe göre sıralar:</span><span class="sxs-lookup"><span data-stu-id="89129-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="89129-211">Mantıksal Değilleme İşleci `!`</span><span class="sxs-lookup"><span data-stu-id="89129-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="89129-212">Mantıksal AND işleci `&`</span><span class="sxs-lookup"><span data-stu-id="89129-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="89129-213">Mantıksal dışlamalı OR işleci `^`</span><span class="sxs-lookup"><span data-stu-id="89129-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="89129-214">Mantıksal OR işleci `|`</span><span class="sxs-lookup"><span data-stu-id="89129-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="89129-215">Koşullu mantıksal AND işleci `&&`</span><span class="sxs-lookup"><span data-stu-id="89129-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="89129-216">Koşullu mantıksal OR işleci `||`</span><span class="sxs-lookup"><span data-stu-id="89129-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="89129-217">İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()` kullanın:</span><span class="sxs-lookup"><span data-stu-id="89129-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="89129-218">Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="89129-218">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="89129-219">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="89129-219">Operator overloadability</span></span>

<span data-ttu-id="89129-220">Kullanıcı tanımlı bir tür, `!`, `&`, `|` ve `^` işleçlerini [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="89129-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="89129-221">İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="89129-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="89129-222">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="89129-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="89129-223">Kullanıcı tanımlı bir tür, `&&` ve `||` Koşullu mantıksal işleçleri aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="89129-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="89129-224">Ancak, Kullanıcı tanımlı bir tür [doğru ve yanlış işleçleri](true-false-operators.md) ve `&` veya `|` işlecini belirli bir şekilde aşırı yükleiyorsa, sırasıyla `&&` veya `||` işlemi, bu türün işlenenleri için değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="89129-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="89129-225">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="89129-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="89129-226">C#dil belirtimi</span><span class="sxs-lookup"><span data-stu-id="89129-226">C# language specification</span></span>

<span data-ttu-id="89129-227">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="89129-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="89129-228">Mantıksal Değilleme İşleci</span><span class="sxs-lookup"><span data-stu-id="89129-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="89129-229">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="89129-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="89129-230">Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="89129-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="89129-231">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="89129-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="89129-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89129-232">See also</span></span>

- [<span data-ttu-id="89129-233">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="89129-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="89129-234">C#işletmenlerinin</span><span class="sxs-lookup"><span data-stu-id="89129-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="89129-235">Bit düzeyinde ve kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="89129-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
