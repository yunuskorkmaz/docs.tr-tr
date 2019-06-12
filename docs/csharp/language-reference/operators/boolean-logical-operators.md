---
title: Boolean mantıksal işleçler - C# başvurusu
description: Hakkında bilgi edinin C# mantıksal olumsuzlama, (ve) birlikte ve Boole işlenenler dahil ve hariç ayrım (veya) işlemleri gerçekleştiren işleçleri.
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
ms.openlocfilehash: 37fe329026c16043abb20f8a9f030d877469951d
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025233"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="7a061-103">Boolean mantıksal işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7a061-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="7a061-104">Aşağıdaki işleçleri ile mantıksal işlemleri [bool](../keywords/bool.md) işlenenler:</span><span class="sxs-lookup"><span data-stu-id="7a061-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="7a061-105">Birli [ `!` (mantıksal olumsuzlama)](#logical-negation-operator-) işleci.</span><span class="sxs-lookup"><span data-stu-id="7a061-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="7a061-106">İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal veya)](#logical-or-operator-), ve [ `^` (mantıksal XOR)](#logical-exclusive-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="7a061-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="7a061-107">Bu işleçler, her iki işlenen de her zaman değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="7a061-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="7a061-108">İkili [ `&&` (koşullu mantıksal ve)](#conditional-logical-and-operator-) ve [ `||` (koşullu mantıksal veya)](#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="7a061-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="7a061-109">Bu işleçler, yalnızca gerekli olduğunda ikinci işlenenin değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="7a061-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="7a061-110">İşlenen için [integral](../keywords/integral-types-table.md) türleri `&`, `|`, ve `^` işleçleri mantıksal bit düzeyinde işlemler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="7a061-110">For the operands of the [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="7a061-111">Daha fazla bilgi için [işleçler bit düzeyinde and -shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7a061-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="7a061-112">Mantıksal değilleme işleci!</span><span class="sxs-lookup"><span data-stu-id="7a061-112">Logical negation operator !</span></span>

<span data-ttu-id="7a061-113">`!` İşleci, işlenenin mantıksal olumsuzlama hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7a061-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="7a061-114">Diğer bir deyişle, ürettiği `true`, işlenenin değerlendirilirse `false`, ve `false`, işlenenin değerlendirilirse `true`:</span><span class="sxs-lookup"><span data-stu-id="7a061-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="7a061-115">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="7a061-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="7a061-116">`&` İşlenenleri, mantıksal AND işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7a061-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="7a061-117">Sonucu `x & y` olduğu `true` hem `x` ve `y` vermesi `true`.</span><span class="sxs-lookup"><span data-stu-id="7a061-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="7a061-118">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="7a061-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="7a061-119">`&` İşleci, birinci işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `false`, sonuç olmalıdır böylece `false` ikinci işlenenin değerinden bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="7a061-119">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="7a061-120">Aşağıdaki örnekte, ikinci işleneni `&` işleci, birinci işlenenin değerini bağımsız olarak gerçekleştirilen bir yöntem çağrısının:</span><span class="sxs-lookup"><span data-stu-id="7a061-120">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="7a061-121">[Koşullu mantıksal AND işlecinin](#conditional-logical-and-operator-) `&&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak değerlendirme sonucu ilk işlenen ikinci işlenende değerlendirmez `false`.</span><span class="sxs-lookup"><span data-stu-id="7a061-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="7a061-122">İntegral türündeki işlenenler için `&` işleci hesaplar [mantıksal bit düzeyinde AND](bitwise-and-shift-operators.md#logical-and-operator-) işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="7a061-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="7a061-123">Birli `&` işleci [address-of işleci](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="7a061-123">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="7a061-124">Mantıksal Dışlayıcı veya işlecini ^</span><span class="sxs-lookup"><span data-stu-id="7a061-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="7a061-125">`^` Mantıksal Dışlayıcı veya olarak da bilinir, işlenenleri mantıksal XOR işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7a061-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="7a061-126">Sonucu `x ^ y` olduğu `true` varsa `x` değerlendiren `true` ve `y` değerlendiren `false`, veya `x` değerlendiren `false` ve `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="7a061-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="7a061-127">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="7a061-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="7a061-128">Diğer bir deyişle, için `bool` işlenenini `^` işleci aynı sonucu hesaplar [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="7a061-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="7a061-129">İntegral türündeki işlenenler için `^` işleci hesaplar [mantıksal bit düzeyinde dışlamalı OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="7a061-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="7a061-130">Mantıksal OR işlecinin |</span><span class="sxs-lookup"><span data-stu-id="7a061-130">Logical OR operator |</span></span>

<span data-ttu-id="7a061-131">`|` İşlenenleri, mantıksal OR işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7a061-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="7a061-132">Sonucu `x | y` olduğu `true` ya da `x` veya `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="7a061-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="7a061-133">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="7a061-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="7a061-134">`|` İşleci, birinci işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `true`, sonuç olmalıdır böylece `true` ikinci işlenenin değerinden bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="7a061-134">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="7a061-135">Aşağıdaki örnekte, ikinci işleneni `|` işleci, birinci işlenenin değerini bağımsız olarak gerçekleştirilen bir yöntem çağrısının:</span><span class="sxs-lookup"><span data-stu-id="7a061-135">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="7a061-136">[Koşullu mantıksal OR işlecinin](#conditional-logical-or-operator-) `||` ayrıca mantıksal OR işlenenleri, hesaplar, ancak değerlendirme sonucu ilk işlenen ikinci işlenende değerlendirmez `true`.</span><span class="sxs-lookup"><span data-stu-id="7a061-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="7a061-137">İntegral türündeki işlenenler için `|` işleci hesaplar [mantıksal bit düzeyinde OR](bitwise-and-shift-operators.md#logical-or-operator-) işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="7a061-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="7a061-138">Koşullu mantıksal AND işleci &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="7a061-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="7a061-139">Koşullu mantıksal AND işlecinin `&&`, mantıksal ve işlenenleri, "kısa devre" mantıksal AND işleci, hesaplar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="7a061-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="7a061-140">Sonucu `x && y` olduğu `true` hem `x` ve `y` vermesi `true`.</span><span class="sxs-lookup"><span data-stu-id="7a061-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="7a061-141">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="7a061-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="7a061-142">Birinci işlenenin değerlendirilirse `false`, ikinci işlenenin değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="7a061-142">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="7a061-143">Aşağıdaki örnekte, ikinci işleneni `&&` işleci, birinci işlenenin değerlendirilirse yapılamaz bir yöntem çağrısının `false`:</span><span class="sxs-lookup"><span data-stu-id="7a061-143">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="7a061-144">[Mantıksal AND işlecinin](#logical-and-operator-) `&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7a061-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="7a061-145">Mantıksal OR işlecinin koşullu ||</span><span class="sxs-lookup"><span data-stu-id="7a061-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="7a061-146">Koşullu mantıksal OR işlecinin `||`, "kısa devre" mantıksal OR işleci, işlenenleri, mantıksal OR hesaplar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="7a061-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="7a061-147">Sonucu `x || y` olduğu `true` ya da `x` veya `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="7a061-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="7a061-148">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="7a061-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="7a061-149">Birinci işlenenin değerlendirilirse `true`, ikinci işlenenin değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="7a061-149">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="7a061-150">Aşağıdaki örnekte, ikinci işleneni `||` işleci, birinci işlenenin değerlendirilirse yapılamaz bir yöntem çağrısının `true`:</span><span class="sxs-lookup"><span data-stu-id="7a061-150">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="7a061-151">[Mantıksal OR işlecinin](#logical-or-operator-) `|` ayrıca mantıksal OR işlenenleri, hesaplar, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7a061-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="7a061-152">Boş değer atanabilir Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="7a061-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="7a061-153">İçin `bool?` işlenenini `&` ve `|` üç değerli mantıksal işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="7a061-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="7a061-154">Bu işleçler semantiği aşağıdaki tabloda tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="7a061-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="7a061-155">x</span><span class="sxs-lookup"><span data-stu-id="7a061-155">x</span></span>|<span data-ttu-id="7a061-156">y</span><span class="sxs-lookup"><span data-stu-id="7a061-156">y</span></span>|<span data-ttu-id="7a061-157">x & y</span><span class="sxs-lookup"><span data-stu-id="7a061-157">x&y</span></span>|<span data-ttu-id="7a061-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="7a061-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="7a061-159">true</span><span class="sxs-lookup"><span data-stu-id="7a061-159">true</span></span>|<span data-ttu-id="7a061-160">true</span><span class="sxs-lookup"><span data-stu-id="7a061-160">true</span></span>|<span data-ttu-id="7a061-161">true</span><span class="sxs-lookup"><span data-stu-id="7a061-161">true</span></span>|<span data-ttu-id="7a061-162">true</span><span class="sxs-lookup"><span data-stu-id="7a061-162">true</span></span>|  
|<span data-ttu-id="7a061-163">true</span><span class="sxs-lookup"><span data-stu-id="7a061-163">true</span></span>|<span data-ttu-id="7a061-164">false</span><span class="sxs-lookup"><span data-stu-id="7a061-164">false</span></span>|<span data-ttu-id="7a061-165">false</span><span class="sxs-lookup"><span data-stu-id="7a061-165">false</span></span>|<span data-ttu-id="7a061-166">true</span><span class="sxs-lookup"><span data-stu-id="7a061-166">true</span></span>|  
|<span data-ttu-id="7a061-167">true</span><span class="sxs-lookup"><span data-stu-id="7a061-167">true</span></span>|<span data-ttu-id="7a061-168">null</span><span class="sxs-lookup"><span data-stu-id="7a061-168">null</span></span>|<span data-ttu-id="7a061-169">null</span><span class="sxs-lookup"><span data-stu-id="7a061-169">null</span></span>|<span data-ttu-id="7a061-170">true</span><span class="sxs-lookup"><span data-stu-id="7a061-170">true</span></span>|  
|<span data-ttu-id="7a061-171">false</span><span class="sxs-lookup"><span data-stu-id="7a061-171">false</span></span>|<span data-ttu-id="7a061-172">true</span><span class="sxs-lookup"><span data-stu-id="7a061-172">true</span></span>|<span data-ttu-id="7a061-173">false</span><span class="sxs-lookup"><span data-stu-id="7a061-173">false</span></span>|<span data-ttu-id="7a061-174">true</span><span class="sxs-lookup"><span data-stu-id="7a061-174">true</span></span>|  
|<span data-ttu-id="7a061-175">false</span><span class="sxs-lookup"><span data-stu-id="7a061-175">false</span></span>|<span data-ttu-id="7a061-176">false</span><span class="sxs-lookup"><span data-stu-id="7a061-176">false</span></span>|<span data-ttu-id="7a061-177">false</span><span class="sxs-lookup"><span data-stu-id="7a061-177">false</span></span>|<span data-ttu-id="7a061-178">false</span><span class="sxs-lookup"><span data-stu-id="7a061-178">false</span></span>|  
|<span data-ttu-id="7a061-179">false</span><span class="sxs-lookup"><span data-stu-id="7a061-179">false</span></span>|<span data-ttu-id="7a061-180">null</span><span class="sxs-lookup"><span data-stu-id="7a061-180">null</span></span>|<span data-ttu-id="7a061-181">false</span><span class="sxs-lookup"><span data-stu-id="7a061-181">false</span></span>|<span data-ttu-id="7a061-182">null</span><span class="sxs-lookup"><span data-stu-id="7a061-182">null</span></span>|  
|<span data-ttu-id="7a061-183">null</span><span class="sxs-lookup"><span data-stu-id="7a061-183">null</span></span>|<span data-ttu-id="7a061-184">true</span><span class="sxs-lookup"><span data-stu-id="7a061-184">true</span></span>|<span data-ttu-id="7a061-185">null</span><span class="sxs-lookup"><span data-stu-id="7a061-185">null</span></span>|<span data-ttu-id="7a061-186">true</span><span class="sxs-lookup"><span data-stu-id="7a061-186">true</span></span>|  
|<span data-ttu-id="7a061-187">null</span><span class="sxs-lookup"><span data-stu-id="7a061-187">null</span></span>|<span data-ttu-id="7a061-188">false</span><span class="sxs-lookup"><span data-stu-id="7a061-188">false</span></span>|<span data-ttu-id="7a061-189">false</span><span class="sxs-lookup"><span data-stu-id="7a061-189">false</span></span>|<span data-ttu-id="7a061-190">null</span><span class="sxs-lookup"><span data-stu-id="7a061-190">null</span></span>|  
|<span data-ttu-id="7a061-191">null</span><span class="sxs-lookup"><span data-stu-id="7a061-191">null</span></span>|<span data-ttu-id="7a061-192">null</span><span class="sxs-lookup"><span data-stu-id="7a061-192">null</span></span>|<span data-ttu-id="7a061-193">null</span><span class="sxs-lookup"><span data-stu-id="7a061-193">null</span></span>|<span data-ttu-id="7a061-194">null</span><span class="sxs-lookup"><span data-stu-id="7a061-194">null</span></span>|  

<span data-ttu-id="7a061-195">Bu işleçlerin davranışını boş değer atanabilen değer türleri ile tipik işleci davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7a061-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="7a061-196">Genellikle, bir değer türündeki işlenenler için tanımlanan bir işleç işlenenleri karşılık gelen null yapılabilir değer türü ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a061-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="7a061-197">Böyle bir işleç üretir `null` işlenenleri biri `null`.</span><span class="sxs-lookup"><span data-stu-id="7a061-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="7a061-198">Ancak, `&` ve `|` işleçleri işlenenlerden olsa bile, null olmayan üretebilir `null`.</span><span class="sxs-lookup"><span data-stu-id="7a061-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="7a061-199">Boş değer atanabilen değer türleri ile işleci davranış hakkında daha fazla bilgi için bkz. [işleçleri](../../programming-guide/nullable-types/using-nullable-types.md#operators) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="7a061-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="7a061-200">Ayrıca `!` ve `^` işleçlerle `bool?` aşağıdaki örnekte gösterildiği gibi işlenenler:</span><span class="sxs-lookup"><span data-stu-id="7a061-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="7a061-201">Koşullu mantıksal işleçler `&&` ve `||` desteklemeyen `bool?` işlenen.</span><span class="sxs-lookup"><span data-stu-id="7a061-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="7a061-202">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="7a061-202">Compound assignment</span></span>

<span data-ttu-id="7a061-203">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="7a061-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="7a061-204">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="7a061-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="7a061-205">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7a061-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="7a061-206">`&`, `|`, Ve `^` aşağıdaki örnekte gösterildiği gibi bileşik atama işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="7a061-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="7a061-207">Koşullu mantıksal işleçler `&&` ve `||` bileşik atama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7a061-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="7a061-208">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="7a061-208">Operator precedence</span></span>

<span data-ttu-id="7a061-209">Aşağıdaki liste, en yüksek öncelikten en düşük başlangıç mantıksal işleçler sıralar:</span><span class="sxs-lookup"><span data-stu-id="7a061-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="7a061-210">Mantıksal değilleme işleci `!`</span><span class="sxs-lookup"><span data-stu-id="7a061-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="7a061-211">Mantıksal AND işleci `&`</span><span class="sxs-lookup"><span data-stu-id="7a061-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="7a061-212">Özel mantıksal OR işleci `^`</span><span class="sxs-lookup"><span data-stu-id="7a061-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="7a061-213">Mantıksal OR işleci `|`</span><span class="sxs-lookup"><span data-stu-id="7a061-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="7a061-214">Koşullu mantıksal AND işleci `&&`</span><span class="sxs-lookup"><span data-stu-id="7a061-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="7a061-215">Koşullu mantıksal OR işleci `||`</span><span class="sxs-lookup"><span data-stu-id="7a061-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="7a061-216">Parantez kullanın `()`İşleç önceliği tarafından belirlenen değerlendirmenin sırasını değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="7a061-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="7a061-217">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="7a061-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7a061-218">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="7a061-218">Operator overloadability</span></span>

<span data-ttu-id="7a061-219">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `!`, `&`, `|`, ve `^` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="7a061-219">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="7a061-220">İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="7a061-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="7a061-221">Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="7a061-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="7a061-222">Kullanıcı tanımlı bir tür koşullu mantıksal işleçler aşırı yüklenemez `&&` ve `||`.</span><span class="sxs-lookup"><span data-stu-id="7a061-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="7a061-223">Ancak, kullanıcı tanımlı bir tür aşırı [true ve false işleçleri](true-false-operators.md) ve `&` veya `|` işleci belirli bir şekilde `&&` veya `||` işlemi, sırasıyla değerlendirmesi yapılamıyor için işlenen türü.</span><span class="sxs-lookup"><span data-stu-id="7a061-223">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="7a061-224">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7a061-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7a061-225">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7a061-225">C# language specification</span></span>

<span data-ttu-id="7a061-226">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="7a061-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7a061-227">Mantıksal değilleme işleci</span><span class="sxs-lookup"><span data-stu-id="7a061-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="7a061-228">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="7a061-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="7a061-229">Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="7a061-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="7a061-230">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="7a061-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="7a061-231">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a061-231">See also</span></span>

- [<span data-ttu-id="7a061-232">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="7a061-232">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7a061-233">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="7a061-233">C# operators</span></span>](index.md)
- [<span data-ttu-id="7a061-234">Bit düzeyinde ve kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="7a061-234">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
