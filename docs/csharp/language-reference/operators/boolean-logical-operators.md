---
title: Boole mantıksal işleçler- C# başvuru
description: Mantıksal olumsuzlama, birlikte (ve) ve kapsamlı ve dışlamalı (ya da) işlemleri Boolean işlenenleriyle gerçekleştiren işleçler hakkında C# bilgi edinin.
ms.date: 04/08/2019
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
ms.openlocfilehash: 39f5be7a667b4e37e84246ef0bfeb03c0099d4b7
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353368"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="bad17-103">Boole mantıksal işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="bad17-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="bad17-104">Aşağıdaki işleçler [bool](../keywords/bool.md) işlenenleri ile mantıksal işlemler gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="bad17-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="bad17-105">Birli [`!` (mantıksal değilleme)](#logical-negation-operator-) işleci.</span><span class="sxs-lookup"><span data-stu-id="bad17-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="bad17-106">İkili [`&` (MANTıKSAL ve)](#logical-and-operator-), [`|` (mantıksal or)](#logical-or-operator-)ve [`^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler.</span><span class="sxs-lookup"><span data-stu-id="bad17-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="bad17-107">Bu operatörler her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="bad17-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="bad17-108">İkili [`&&` (koşullu MANTıKSAL and)](#conditional-logical-and-operator-) ve [`||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="bad17-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="bad17-109">Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="bad17-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="bad17-110">[İntegral](../builtin-types/integral-numeric-types.md) türlerinin işlenenleri için, `&`, `|` ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bad17-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="bad17-111">Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="bad17-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="bad17-112">Mantıksal Değilleme İşleci!</span><span class="sxs-lookup"><span data-stu-id="bad17-112">Logical negation operator !</span></span>

<span data-ttu-id="bad17-113">@No__t-0 işleci, işleneninin mantıksal olumsuzunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="bad17-114">Diğer bir deyişle, işlenen `false` olarak değerlendirilirse `false` ' yi ve işlenen `true` ' e değerlendirilirse,  ' yi üretir:</span><span class="sxs-lookup"><span data-stu-id="bad17-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-"></a><span data-ttu-id="bad17-115">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="bad17-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="bad17-116">@No__t-0 işleci, işlenenlerinin mantıksal ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="bad17-117">@No__t-0 ' ın sonucu, hem `x` hem de `y` `true` olarak değerlendirilir `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="bad17-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="bad17-118">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="bad17-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="bad17-119">@No__t-0 işleci, sol taraftaki işlenen `false` olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece sonuç sağ işlenen değerinden bağımsız olarak `false` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bad17-119">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="bad17-120">Aşağıdaki örnekte, `&` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="bad17-120">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="bad17-121">@No__t-1 [koşullu MANTıKSAL and işleci](#conditional-logical-and-operator-) , işlenenlerinin mantıksal ve ' lerini de hesaplar, ancak sol işlenen `false` olarak değerlendirilirse sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="bad17-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="bad17-122">İntegral türlerinin işlenenleri için `&` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="bad17-123">Birli `&` işleci [Adres işleçtir](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="bad17-123">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="bad17-124">Mantıksal dışlamalı OR işleci ^</span><span class="sxs-lookup"><span data-stu-id="bad17-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="bad17-125">@No__t-0 işleci, işlenenlerinin mantıksal XOR olarak da bilinen mantıksal dışlamalı veya bir şekilde hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="bad17-126">@No__t-0 ' ın sonucu `true` ' dir. `x` `true` ' ü değerlendiriyor ve `false` ' i  olarak değerlendirir ya da `x` `true` ' a değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bad17-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="bad17-127">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="bad17-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="bad17-128">Diğer bir deyişle, `bool` işlenenleri için `^` işleci, [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=` ile aynı sonucu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="bad17-129">İntegral türlerinin işlenenleri için, `^` işleci, işlenenlerinin [bit düzeyinde mantıksal dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) bunların işlenenleri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="bad17-130">Mantıksal OR işleci |</span><span class="sxs-lookup"><span data-stu-id="bad17-130">Logical OR operator |</span></span>

<span data-ttu-id="bad17-131">@No__t-0 işleci, işlenenlerinin mantıksal veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="bad17-132">@No__t-2 veya `y` ' ü `true` olarak değerlendirilirse `x | y` ' ın sonucu `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="bad17-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="bad17-133">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="bad17-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="bad17-134">@No__t-0 işleci, sol taraftaki işlenen `true` olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece sonuç sağ işlenen değerinden bağımsız olarak `true` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bad17-134">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="bad17-135">Aşağıdaki örnekte, `|` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="bad17-135">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="bad17-136">@No__t-1 [koşullu MANTıKSAL or işleci](#conditional-logical-or-operator-) , işlenenlerinin MANTıKSAL veya veya işlecini de hesaplar, ancak sol işlenen `true` olarak değerlendirilirse sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="bad17-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="bad17-137">İntegral türlerinin işlenenleri için `|` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="bad17-138">Koşullu mantıksal AND işleci &amp; @ no__t-2</span><span class="sxs-lookup"><span data-stu-id="bad17-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="bad17-139">"Kısa devre dışı" mantıksal AND işleci olarak da bilinen Koşullu mantıksal AND işleci `&&`, işlenenlerinin mantıksal ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="bad17-140">@No__t-0 ' ın sonucu, hem `x` hem de `y` `true` olarak değerlendirilir `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="bad17-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="bad17-141">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="bad17-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="bad17-142">@No__t-0 `false` olarak değerlendirilirse `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="bad17-142">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="bad17-143">Aşağıdaki örnekte, `&&` işlecinin sağ işleneni, sol taraftaki işlenen `false` olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="bad17-143">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="bad17-144">@No__t-1 [MANTıKSAL ve işleci](#logical-and-operator-) , işlenenlerinin mantıksal ve işlecini de hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="bad17-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="bad17-145">Koşullu mantıksal OR işleci | |</span><span class="sxs-lookup"><span data-stu-id="bad17-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="bad17-146">"Kısa devre dışı" mantıksal OR işleci olarak da bilinen Koşullu mantıksal OR işleci `||`, işlenenlerinin mantıksal veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bad17-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="bad17-147">@No__t-2 veya `y` ' ü `true` olarak değerlendirilirse `x || y` ' ın sonucu `true` ' dir.</span><span class="sxs-lookup"><span data-stu-id="bad17-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="bad17-148">Aksi takdirde, sonuç `false` ' dır.</span><span class="sxs-lookup"><span data-stu-id="bad17-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="bad17-149">@No__t-0 `true` olarak değerlendirilirse `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="bad17-149">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="bad17-150">Aşağıdaki örnekte, `||` işlecinin sağ işleneni, sol taraftaki işlenen `true` olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="bad17-150">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="bad17-151">@No__t-1 [MANTıKSAL or işleci](#logical-or-operator-) , işlenenlerinin mantıksal veya her ikisini de hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="bad17-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="bad17-152">Null yapılabilir Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="bad17-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="bad17-153">@No__t-0 işlenenleri için, `&` ve `|` işleçleri üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="bad17-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="bad17-154">Bu işleçlerin semantiği aşağıdaki tablo tarafından tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="bad17-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="bad17-155">x</span><span class="sxs-lookup"><span data-stu-id="bad17-155">x</span></span>|<span data-ttu-id="bad17-156">Y</span><span class="sxs-lookup"><span data-stu-id="bad17-156">y</span></span>|<span data-ttu-id="bad17-157">x & y</span><span class="sxs-lookup"><span data-stu-id="bad17-157">x&y</span></span>|<span data-ttu-id="bad17-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="bad17-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="bad17-159">true</span><span class="sxs-lookup"><span data-stu-id="bad17-159">true</span></span>|<span data-ttu-id="bad17-160">true</span><span class="sxs-lookup"><span data-stu-id="bad17-160">true</span></span>|<span data-ttu-id="bad17-161">true</span><span class="sxs-lookup"><span data-stu-id="bad17-161">true</span></span>|<span data-ttu-id="bad17-162">true</span><span class="sxs-lookup"><span data-stu-id="bad17-162">true</span></span>|  
|<span data-ttu-id="bad17-163">true</span><span class="sxs-lookup"><span data-stu-id="bad17-163">true</span></span>|<span data-ttu-id="bad17-164">false</span><span class="sxs-lookup"><span data-stu-id="bad17-164">false</span></span>|<span data-ttu-id="bad17-165">false</span><span class="sxs-lookup"><span data-stu-id="bad17-165">false</span></span>|<span data-ttu-id="bad17-166">true</span><span class="sxs-lookup"><span data-stu-id="bad17-166">true</span></span>|  
|<span data-ttu-id="bad17-167">true</span><span class="sxs-lookup"><span data-stu-id="bad17-167">true</span></span>|<span data-ttu-id="bad17-168">null</span><span class="sxs-lookup"><span data-stu-id="bad17-168">null</span></span>|<span data-ttu-id="bad17-169">null</span><span class="sxs-lookup"><span data-stu-id="bad17-169">null</span></span>|<span data-ttu-id="bad17-170">true</span><span class="sxs-lookup"><span data-stu-id="bad17-170">true</span></span>|  
|<span data-ttu-id="bad17-171">false</span><span class="sxs-lookup"><span data-stu-id="bad17-171">false</span></span>|<span data-ttu-id="bad17-172">true</span><span class="sxs-lookup"><span data-stu-id="bad17-172">true</span></span>|<span data-ttu-id="bad17-173">false</span><span class="sxs-lookup"><span data-stu-id="bad17-173">false</span></span>|<span data-ttu-id="bad17-174">true</span><span class="sxs-lookup"><span data-stu-id="bad17-174">true</span></span>|  
|<span data-ttu-id="bad17-175">false</span><span class="sxs-lookup"><span data-stu-id="bad17-175">false</span></span>|<span data-ttu-id="bad17-176">false</span><span class="sxs-lookup"><span data-stu-id="bad17-176">false</span></span>|<span data-ttu-id="bad17-177">false</span><span class="sxs-lookup"><span data-stu-id="bad17-177">false</span></span>|<span data-ttu-id="bad17-178">false</span><span class="sxs-lookup"><span data-stu-id="bad17-178">false</span></span>|  
|<span data-ttu-id="bad17-179">false</span><span class="sxs-lookup"><span data-stu-id="bad17-179">false</span></span>|<span data-ttu-id="bad17-180">null</span><span class="sxs-lookup"><span data-stu-id="bad17-180">null</span></span>|<span data-ttu-id="bad17-181">false</span><span class="sxs-lookup"><span data-stu-id="bad17-181">false</span></span>|<span data-ttu-id="bad17-182">null</span><span class="sxs-lookup"><span data-stu-id="bad17-182">null</span></span>|  
|<span data-ttu-id="bad17-183">null</span><span class="sxs-lookup"><span data-stu-id="bad17-183">null</span></span>|<span data-ttu-id="bad17-184">true</span><span class="sxs-lookup"><span data-stu-id="bad17-184">true</span></span>|<span data-ttu-id="bad17-185">null</span><span class="sxs-lookup"><span data-stu-id="bad17-185">null</span></span>|<span data-ttu-id="bad17-186">true</span><span class="sxs-lookup"><span data-stu-id="bad17-186">true</span></span>|  
|<span data-ttu-id="bad17-187">null</span><span class="sxs-lookup"><span data-stu-id="bad17-187">null</span></span>|<span data-ttu-id="bad17-188">false</span><span class="sxs-lookup"><span data-stu-id="bad17-188">false</span></span>|<span data-ttu-id="bad17-189">false</span><span class="sxs-lookup"><span data-stu-id="bad17-189">false</span></span>|<span data-ttu-id="bad17-190">null</span><span class="sxs-lookup"><span data-stu-id="bad17-190">null</span></span>|  
|<span data-ttu-id="bad17-191">null</span><span class="sxs-lookup"><span data-stu-id="bad17-191">null</span></span>|<span data-ttu-id="bad17-192">null</span><span class="sxs-lookup"><span data-stu-id="bad17-192">null</span></span>|<span data-ttu-id="bad17-193">null</span><span class="sxs-lookup"><span data-stu-id="bad17-193">null</span></span>|<span data-ttu-id="bad17-194">null</span><span class="sxs-lookup"><span data-stu-id="bad17-194">null</span></span>|  

<span data-ttu-id="bad17-195">Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="bad17-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="bad17-196">Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bad17-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="bad17-197">Bu tür bir operatör, işlenenlerinden herhangi biri `null` ise `null` üretir.</span><span class="sxs-lookup"><span data-stu-id="bad17-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="bad17-198">Ancak, `&` ve `|` işleçleri, işlenenleri `null` olsa bile null olmayan bir şekilde üretebilir.</span><span class="sxs-lookup"><span data-stu-id="bad17-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="bad17-199">Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türlerini kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesindeki [işleçler](../../programming-guide/nullable-types/using-nullable-types.md#operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bad17-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="bad17-200">Aşağıdaki örnekte gösterildiği gibi `!` ve `^` işleçlerini `bool?` işlenenleriyle de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bad17-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="bad17-201">@No__t-0 ve `||` Koşullu mantıksal işleçler `bool?` işlenenlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bad17-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="bad17-202">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="bad17-202">Compound assignment</span></span>

<span data-ttu-id="bad17-203">Bir ikili işleci `op`için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="bad17-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="bad17-204">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="bad17-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="bad17-205">`x` hariç yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bad17-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="bad17-206">@No__t-0, `|` ve `^` işleçleri, aşağıdaki örnekte gösterildiği gibi bileşik atamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="bad17-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="bad17-207">@No__t-0 ve `||` Koşullu mantıksal işleçler bileşik atamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bad17-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="bad17-208">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="bad17-208">Operator precedence</span></span>

<span data-ttu-id="bad17-209">Aşağıdaki liste, en yüksek öncelikten başlayarak mantıksal işleçleri en düşüğe göre sıralar:</span><span class="sxs-lookup"><span data-stu-id="bad17-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="bad17-210">Mantıksal Değilleme İşleci`!`</span><span class="sxs-lookup"><span data-stu-id="bad17-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="bad17-211">Mantıksal AND işleci `&`</span><span class="sxs-lookup"><span data-stu-id="bad17-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="bad17-212">Mantıksal dışlamalı OR işleci `^`</span><span class="sxs-lookup"><span data-stu-id="bad17-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="bad17-213">Mantıksal OR işleci `|`</span><span class="sxs-lookup"><span data-stu-id="bad17-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="bad17-214">Koşullu mantıksal AND işleci `&&`</span><span class="sxs-lookup"><span data-stu-id="bad17-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="bad17-215">Koşullu mantıksal OR işleci `||`</span><span class="sxs-lookup"><span data-stu-id="bad17-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="bad17-216">İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()` kullanın:</span><span class="sxs-lookup"><span data-stu-id="bad17-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="bad17-217">Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="bad17-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="bad17-218">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="bad17-218">Operator overloadability</span></span>

<span data-ttu-id="bad17-219">Kullanıcı tanımlı bir tür, `!`, `&`, `|` ve `^` işleçlerini [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bad17-219">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="bad17-220">İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bad17-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="bad17-221">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="bad17-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="bad17-222">Kullanıcı tanımlı bir tür, `&&` ve `||` Koşullu mantıksal işleçleri aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="bad17-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="bad17-223">Ancak, Kullanıcı tanımlı bir tür [doğru ve yanlış işleçleri](true-false-operators.md) ve `&` veya `|` işlecini belirli bir şekilde aşırı yükleiyorsa, sırasıyla `&&` veya `||` işlemi, bu türün işlenenleri için değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bad17-223">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="bad17-224">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bad17-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bad17-225">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="bad17-225">C# language specification</span></span>

<span data-ttu-id="bad17-226">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="bad17-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bad17-227">Mantıksal Değilleme İşleci</span><span class="sxs-lookup"><span data-stu-id="bad17-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="bad17-228">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="bad17-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="bad17-229">Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="bad17-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="bad17-230">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="bad17-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="bad17-231">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bad17-231">See also</span></span>

- [<span data-ttu-id="bad17-232">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="bad17-232">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bad17-233">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="bad17-233">C# operators</span></span>](index.md)
- [<span data-ttu-id="bad17-234">Bit düzeyinde ve kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="bad17-234">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
