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
ms.openlocfilehash: de621b26334bbc9679ba7e48a9d5a0cbaec67eab
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427324"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="581ce-103">Boolean mantıksal işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="581ce-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="581ce-104">Aşağıdaki işleçleri ile mantıksal işlemleri [bool](../keywords/bool.md) işlenenler:</span><span class="sxs-lookup"><span data-stu-id="581ce-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="581ce-105">Birli [ `!` (mantıksal olumsuzlama)](#logical-negation-operator-) işleci.</span><span class="sxs-lookup"><span data-stu-id="581ce-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="581ce-106">İkili [ `&` (mantıksal ve)](#logical-and-operator-), [ `|` (mantıksal veya)](#logical-or-operator-), ve [ `^` (mantıksal XOR)](#logical-exclusive-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="581ce-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="581ce-107">Bu işleçler, her iki işlenen de her zaman değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="581ce-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="581ce-108">İkili [ `&&` (koşullu mantıksal ve)](#conditional-logical-and-operator-) ve [ `||` (koşullu mantıksal veya)](#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="581ce-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="581ce-109">Bu işleçler, yalnızca gerekli olduğunda ikinci işlenenin değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="581ce-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="581ce-110">İşlenen için [integral](../keywords/integral-types-table.md) türleri `&`, `|`, ve `^` işleçleri mantıksal bit düzeyinde işlemler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="581ce-110">For the operands of [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="581ce-111">Mantıksal değilleme işleci!</span><span class="sxs-lookup"><span data-stu-id="581ce-111">Logical negation operator !</span></span>

<span data-ttu-id="581ce-112">`!` İşleci, işlenenin mantıksal olumsuzlama hesaplar.</span><span class="sxs-lookup"><span data-stu-id="581ce-112">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="581ce-113">Diğer bir deyişle, ürettiği `true`, işlenenin değerlendirilirse `false`, ve `false`, işlenenin değerlendirilirse `true`:</span><span class="sxs-lookup"><span data-stu-id="581ce-113">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="581ce-114">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="581ce-114">Logical AND operator &amp;</span></span>

<span data-ttu-id="581ce-115">`&` İşlenenleri, mantıksal AND işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="581ce-115">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="581ce-116">Sonucu `x & y` olduğu `true` hem `x` ve `y` vermesi `true`.</span><span class="sxs-lookup"><span data-stu-id="581ce-116">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="581ce-117">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="581ce-117">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="581ce-118">`&` İşleci, birinci işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `false`, sonuç olmalıdır böylece `false` ikinci işlenenin değerinden bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="581ce-118">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="581ce-119">Aşağıdaki örnekte, ikinci işleneni `&` işleci, birinci işlenenin değerini bağımsız olarak gerçekleştirilen bir yöntem çağrısının:</span><span class="sxs-lookup"><span data-stu-id="581ce-119">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="581ce-120">[Koşullu mantıksal AND işlecinin](#conditional-logical-and-operator-) `&&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak değerlendirme sonucu ilk işlenen ikinci işlenende değerlendirmez `false`.</span><span class="sxs-lookup"><span data-stu-id="581ce-120">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="581ce-121">İntegral türündeki işlenenler için `&` işleci hesaplar [mantıksal bit düzeyinde AND](and-operator.md#integer-logical-bitwise-and-operator) işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="581ce-121">For the operands of integral types, the `&` operator computes [bitwise logical AND](and-operator.md#integer-logical-bitwise-and-operator) of its operands.</span></span> <span data-ttu-id="581ce-122">Birli `&` işleci [address-of işleci](and-operator.md#unary-address-of-operator).</span><span class="sxs-lookup"><span data-stu-id="581ce-122">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="581ce-123">Mantıksal Dışlayıcı veya işlecini ^</span><span class="sxs-lookup"><span data-stu-id="581ce-123">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="581ce-124">`^` Mantıksal Dışlayıcı veya olarak da bilinir, işlenenleri mantıksal XOR işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="581ce-124">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="581ce-125">Sonucu `x ^ y` olduğu `true` varsa `x` değerlendiren `true` ve `y` değerlendiren `false`, veya `x` değerlendiren `false` ve `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="581ce-125">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="581ce-126">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="581ce-126">Otherwise, the result is `false`.</span></span> <span data-ttu-id="581ce-127">Diğer bir deyişle, için `bool` işlenenini `^` işleci aynı sonucu hesaplar [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="581ce-127">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="581ce-128">İntegral türündeki işlenenler için `^` işleci hesaplar [mantıksal bit düzeyinde dışlamalı OR](xor-operator.md) işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="581ce-128">For the operands of integral types, the `^` operator computes [bitwise logical exclusive OR](xor-operator.md) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="581ce-129">Mantıksal OR işlecinin |</span><span class="sxs-lookup"><span data-stu-id="581ce-129">Logical OR operator |</span></span>

<span data-ttu-id="581ce-130">`|` İşlenenleri, mantıksal OR işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="581ce-130">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="581ce-131">Sonucu `x | y` olduğu `true` ya da `x` veya `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="581ce-131">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="581ce-132">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="581ce-132">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="581ce-133">`|` İşleci, birinci işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `true`, sonuç olmalıdır böylece `true` ikinci işlenenin değerinden bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="581ce-133">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="581ce-134">Aşağıdaki örnekte, ikinci işleneni `|` işleci, birinci işlenenin değerini bağımsız olarak gerçekleştirilen bir yöntem çağrısının:</span><span class="sxs-lookup"><span data-stu-id="581ce-134">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="581ce-135">[Koşullu mantıksal OR işlecinin](#conditional-logical-or-operator-) `||` ayrıca mantıksal OR işlenenleri, hesaplar, ancak değerlendirme sonucu ilk işlenen ikinci işlenende değerlendirmez `true`.</span><span class="sxs-lookup"><span data-stu-id="581ce-135">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="581ce-136">İntegral türündeki işlenenler için `|` işleci hesaplar [mantıksal bit düzeyinde OR](or-operator.md) işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="581ce-136">For the operands of integral types, the `|` operator computes [bitwise logical OR](or-operator.md) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="581ce-137">Koşullu mantıksal AND işleci &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="581ce-137">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="581ce-138">Koşullu mantıksal AND işlecinin `&&`, mantıksal ve işlenenleri, "kısa devre" mantıksal AND işleci, hesaplar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="581ce-138">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="581ce-139">Sonucu `x && y` olduğu `true` hem `x` ve `y` vermesi `true`.</span><span class="sxs-lookup"><span data-stu-id="581ce-139">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="581ce-140">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="581ce-140">Otherwise, the result is `false`.</span></span> <span data-ttu-id="581ce-141">Birinci işlenenin değerlendirilirse `false`, ikinci işlenenin değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="581ce-141">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="581ce-142">Aşağıdaki örnekte, ikinci işleneni `&&` işleci, birinci işlenenin değerlendirilirse yapılamaz bir yöntem çağrısının `false`:</span><span class="sxs-lookup"><span data-stu-id="581ce-142">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="581ce-143">[Mantıksal AND işlecinin](#logical-and-operator-) `&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="581ce-143">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="581ce-144">Mantıksal OR işlecinin koşullu ||</span><span class="sxs-lookup"><span data-stu-id="581ce-144">Conditional logical OR operator ||</span></span>

<span data-ttu-id="581ce-145">Koşullu mantıksal OR işlecinin `||`, "kısa devre" mantıksal OR işleci, işlenenleri, mantıksal OR hesaplar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="581ce-145">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="581ce-146">Sonucu `x || y` olduğu `true` ya da `x` veya `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="581ce-146">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="581ce-147">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="581ce-147">Otherwise, the result is `false`.</span></span> <span data-ttu-id="581ce-148">Birinci işlenenin değerlendirilirse `true`, ikinci işlenenin değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="581ce-148">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="581ce-149">Aşağıdaki örnekte, ikinci işleneni `||` işleci, birinci işlenenin değerlendirilirse yapılamaz bir yöntem çağrısının `true`:</span><span class="sxs-lookup"><span data-stu-id="581ce-149">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="581ce-150">[Mantıksal OR işlecinin](#logical-or-operator-) `|` ayrıca mantıksal OR işlenenleri, hesaplar, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="581ce-150">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="581ce-151">Boş değer atanabilir Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="581ce-151">Nullable Boolean logical operators</span></span>

<span data-ttu-id="581ce-152">İçin `bool?` işlenenini `&` ve `|` üç değerli mantıksal işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="581ce-152">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="581ce-153">Bu işleçler semantiği aşağıdaki tabloda tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="581ce-153">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="581ce-154">x</span><span class="sxs-lookup"><span data-stu-id="581ce-154">x</span></span>|<span data-ttu-id="581ce-155">y</span><span class="sxs-lookup"><span data-stu-id="581ce-155">y</span></span>|<span data-ttu-id="581ce-156">x & y</span><span class="sxs-lookup"><span data-stu-id="581ce-156">x&y</span></span>|<span data-ttu-id="581ce-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="581ce-157">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="581ce-158">true</span><span class="sxs-lookup"><span data-stu-id="581ce-158">true</span></span>|<span data-ttu-id="581ce-159">true</span><span class="sxs-lookup"><span data-stu-id="581ce-159">true</span></span>|<span data-ttu-id="581ce-160">true</span><span class="sxs-lookup"><span data-stu-id="581ce-160">true</span></span>|<span data-ttu-id="581ce-161">true</span><span class="sxs-lookup"><span data-stu-id="581ce-161">true</span></span>|  
|<span data-ttu-id="581ce-162">true</span><span class="sxs-lookup"><span data-stu-id="581ce-162">true</span></span>|<span data-ttu-id="581ce-163">false</span><span class="sxs-lookup"><span data-stu-id="581ce-163">false</span></span>|<span data-ttu-id="581ce-164">false</span><span class="sxs-lookup"><span data-stu-id="581ce-164">false</span></span>|<span data-ttu-id="581ce-165">true</span><span class="sxs-lookup"><span data-stu-id="581ce-165">true</span></span>|  
|<span data-ttu-id="581ce-166">true</span><span class="sxs-lookup"><span data-stu-id="581ce-166">true</span></span>|<span data-ttu-id="581ce-167">null</span><span class="sxs-lookup"><span data-stu-id="581ce-167">null</span></span>|<span data-ttu-id="581ce-168">null</span><span class="sxs-lookup"><span data-stu-id="581ce-168">null</span></span>|<span data-ttu-id="581ce-169">true</span><span class="sxs-lookup"><span data-stu-id="581ce-169">true</span></span>|  
|<span data-ttu-id="581ce-170">false</span><span class="sxs-lookup"><span data-stu-id="581ce-170">false</span></span>|<span data-ttu-id="581ce-171">true</span><span class="sxs-lookup"><span data-stu-id="581ce-171">true</span></span>|<span data-ttu-id="581ce-172">false</span><span class="sxs-lookup"><span data-stu-id="581ce-172">false</span></span>|<span data-ttu-id="581ce-173">true</span><span class="sxs-lookup"><span data-stu-id="581ce-173">true</span></span>|  
|<span data-ttu-id="581ce-174">false</span><span class="sxs-lookup"><span data-stu-id="581ce-174">false</span></span>|<span data-ttu-id="581ce-175">false</span><span class="sxs-lookup"><span data-stu-id="581ce-175">false</span></span>|<span data-ttu-id="581ce-176">false</span><span class="sxs-lookup"><span data-stu-id="581ce-176">false</span></span>|<span data-ttu-id="581ce-177">false</span><span class="sxs-lookup"><span data-stu-id="581ce-177">false</span></span>|  
|<span data-ttu-id="581ce-178">false</span><span class="sxs-lookup"><span data-stu-id="581ce-178">false</span></span>|<span data-ttu-id="581ce-179">null</span><span class="sxs-lookup"><span data-stu-id="581ce-179">null</span></span>|<span data-ttu-id="581ce-180">false</span><span class="sxs-lookup"><span data-stu-id="581ce-180">false</span></span>|<span data-ttu-id="581ce-181">null</span><span class="sxs-lookup"><span data-stu-id="581ce-181">null</span></span>|  
|<span data-ttu-id="581ce-182">null</span><span class="sxs-lookup"><span data-stu-id="581ce-182">null</span></span>|<span data-ttu-id="581ce-183">true</span><span class="sxs-lookup"><span data-stu-id="581ce-183">true</span></span>|<span data-ttu-id="581ce-184">null</span><span class="sxs-lookup"><span data-stu-id="581ce-184">null</span></span>|<span data-ttu-id="581ce-185">true</span><span class="sxs-lookup"><span data-stu-id="581ce-185">true</span></span>|  
|<span data-ttu-id="581ce-186">null</span><span class="sxs-lookup"><span data-stu-id="581ce-186">null</span></span>|<span data-ttu-id="581ce-187">false</span><span class="sxs-lookup"><span data-stu-id="581ce-187">false</span></span>|<span data-ttu-id="581ce-188">false</span><span class="sxs-lookup"><span data-stu-id="581ce-188">false</span></span>|<span data-ttu-id="581ce-189">null</span><span class="sxs-lookup"><span data-stu-id="581ce-189">null</span></span>|  
|<span data-ttu-id="581ce-190">null</span><span class="sxs-lookup"><span data-stu-id="581ce-190">null</span></span>|<span data-ttu-id="581ce-191">null</span><span class="sxs-lookup"><span data-stu-id="581ce-191">null</span></span>|<span data-ttu-id="581ce-192">null</span><span class="sxs-lookup"><span data-stu-id="581ce-192">null</span></span>|<span data-ttu-id="581ce-193">null</span><span class="sxs-lookup"><span data-stu-id="581ce-193">null</span></span>|  

<span data-ttu-id="581ce-194">Bu işleçlerin davranışını boş değer atanabilen değer türleri ile tipik işleci davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="581ce-194">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="581ce-195">Genellikle, bir değer türündeki işlenenler için tanımlanan bir işleç işlenenleri karşılık gelen null yapılabilir değer türü ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="581ce-195">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="581ce-196">Böyle bir işleç üretir `null` işlenenleri biri `null`.</span><span class="sxs-lookup"><span data-stu-id="581ce-196">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="581ce-197">Ancak, `&` ve `|` işleçleri işlenenlerden olsa bile, null olmayan üretebilir `null`.</span><span class="sxs-lookup"><span data-stu-id="581ce-197">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="581ce-198">Boş değer atanabilen değer türleri ile işleci davranış hakkında daha fazla bilgi için bkz. [işleçleri](../../programming-guide/nullable-types/using-nullable-types.md#operators) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="581ce-198">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="581ce-199">Ayrıca `!` ve `^` işleçlerle `bool?` aşağıdaki örnekte gösterildiği gibi işlenenler:</span><span class="sxs-lookup"><span data-stu-id="581ce-199">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="581ce-200">Koşullu mantıksal işleçler `&&` ve `||` desteklemeyen `bool?` işlenen.</span><span class="sxs-lookup"><span data-stu-id="581ce-200">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="581ce-201">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="581ce-201">Compound assignment</span></span>

<span data-ttu-id="581ce-202">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="581ce-202">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="581ce-203">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="581ce-203">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="581ce-204">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="581ce-204">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="581ce-205">`&`, `|`, Ve `^` aşağıdaki örnekte gösterildiği gibi bileşik atama işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="581ce-205">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="581ce-206">Koşullu mantıksal işleçler `&&` ve `||` bileşik atama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="581ce-206">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="581ce-207">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="581ce-207">Operator precedence</span></span>

<span data-ttu-id="581ce-208">Aşağıdaki liste, en yüksek öncelikten en düşük başlangıç mantıksal işleçler sıralar:</span><span class="sxs-lookup"><span data-stu-id="581ce-208">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="581ce-209">Mantıksal değilleme işleci</span><span class="sxs-lookup"><span data-stu-id="581ce-209">Logical negation operator</span></span> `!`
- <span data-ttu-id="581ce-210">Mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="581ce-210">Logical AND operator</span></span> `&`
- <span data-ttu-id="581ce-211">Özel mantıksal OR işleci</span><span class="sxs-lookup"><span data-stu-id="581ce-211">Logical exclusive OR operator</span></span> `^`
- <span data-ttu-id="581ce-212">Mantıksal OR işleci</span><span class="sxs-lookup"><span data-stu-id="581ce-212">Logical OR operator</span></span> `|`
- <span data-ttu-id="581ce-213">Koşullu mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="581ce-213">Conditional logical AND operator</span></span> `&&`
- <span data-ttu-id="581ce-214">Koşullu mantıksal OR işleci</span><span class="sxs-lookup"><span data-stu-id="581ce-214">Conditional logical OR operator</span></span> `||`

<span data-ttu-id="581ce-215">Parantez kullanın `()`İşleç önceliği tarafından belirlenen değerlendirmenin sırasını değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="581ce-215">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="581ce-216">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="581ce-216">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="581ce-217">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="581ce-217">Operator overloadability</span></span>

<span data-ttu-id="581ce-218">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `!`, `&`, `|`, ve `^` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="581ce-218">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="581ce-219">İkili İşleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="581ce-219">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="581ce-220">Kullanıcı tanımlı bir türe açıkça bir bileşik atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="581ce-220">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="581ce-221">Kullanıcı tanımlı bir tür koşullu mantıksal işleçler aşırı yüklenemez `&&` ve `||`.</span><span class="sxs-lookup"><span data-stu-id="581ce-221">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="581ce-222">Ancak, kullanıcı tanımlı bir tür aşırı [true ve false işleçleri](../keywords/true-false-operators.md) ve `&` veya `|` işleci belirli bir şekilde `&&` veya `||` işlemi, sırasıyla değerlendirmesi yapılamıyor için işlenen türü.</span><span class="sxs-lookup"><span data-stu-id="581ce-222">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="581ce-223">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="581ce-223">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="581ce-224">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="581ce-224">C# language specification</span></span>

<span data-ttu-id="581ce-225">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="581ce-225">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="581ce-226">Mantıksal değilleme işleci</span><span class="sxs-lookup"><span data-stu-id="581ce-226">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="581ce-227">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="581ce-227">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="581ce-228">Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="581ce-228">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)

## <a name="see-also"></a><span data-ttu-id="581ce-229">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="581ce-229">See also</span></span>

- [<span data-ttu-id="581ce-230">C# Başvurusu</span><span class="sxs-lookup"><span data-stu-id="581ce-230">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="581ce-231">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="581ce-231">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="581ce-232">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="581ce-232">C# Operators</span></span>](index.md)
