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
ms.openlocfilehash: d8fe68fc04300b65bea9b66a6dc6c20e3c69abf4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239449"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="75cac-103">Boole mantıksal işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="75cac-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="75cac-104">Aşağıdaki işleçler [bool](../builtin-types/bool.md) işlenenleri olan mantıksal işlemler gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="75cac-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="75cac-105">Birli [`!` (mantıksal değilleme)](#logical-negation-operator-) işleci.</span><span class="sxs-lookup"><span data-stu-id="75cac-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="75cac-106">İkili [`&` (MANTıKSAL ve)](#logical-and-operator-), [`|` (mantıksal or)](#logical-or-operator-)ve [`^` (mantıksal dışlamalı veya)](#logical-exclusive-or-operator-) işleçler.</span><span class="sxs-lookup"><span data-stu-id="75cac-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="75cac-107">Bu operatörler her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="75cac-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="75cac-108">İkili [`&&` (koşullu MANTıKSAL and)](#conditional-logical-and-operator-) ve [`||` (Koşullu mantıksal or)](#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="75cac-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="75cac-109">Bu işleçler yalnızca gerekli olması durumunda sağ işleneni değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="75cac-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="75cac-110">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için, `&`, `|`ve `^` işleçleri bit düzeyinde mantıksal işlemler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="75cac-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="75cac-111">Daha fazla bilgi için bkz. [bit düzeyinde and SHIFT işleçleri](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="75cac-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="75cac-112">Mantıksal Değilleme İşleci!</span><span class="sxs-lookup"><span data-stu-id="75cac-112">Logical negation operator !</span></span>

<span data-ttu-id="75cac-113">Birli önek `!` işleci, işleneninin mantıksal olumsuzunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="75cac-114">Diğer bir deyişle, işlenen `false`değerlendirilirse `true`üretir ve işlenen `true`olarak değerlendirilirse `false`:</span><span class="sxs-lookup"><span data-stu-id="75cac-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="75cac-115">8,0 ile C# başlayarak birli sonek `!` işleci [null-forverme işleçtir](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="75cac-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="75cac-116">Mantıksal AND işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="75cac-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="75cac-117">`&` işleci, işlenenlerinin mantıksal ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="75cac-118">`x & y` sonucu, hem `x` hem de `y` `true`olarak değerlendirilir `true`.</span><span class="sxs-lookup"><span data-stu-id="75cac-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="75cac-119">Aksi takdirde, sonuç `false`.</span><span class="sxs-lookup"><span data-stu-id="75cac-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="75cac-120">`&` işleci, sol taraftaki işlenen `false`olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece işlem sonucu sağ işlenen değerden bağımsız olarak `false`.</span><span class="sxs-lookup"><span data-stu-id="75cac-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="75cac-121">Aşağıdaki örnekte, `&` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="75cac-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="75cac-122">[Koşullu MANTıKSAL and işleci](#conditional-logical-and-operator-) `&&` Ayrıca, işlenenlerinin mantıksal ve işlecini hesaplar, ancak sol işlenen `false`olarak değerlendirilirse sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="75cac-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="75cac-123">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `&` işleci, işlenenlerinin [BIT düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="75cac-124">Birli `&` işleci, [Adres işleçtir](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="75cac-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="75cac-125">Mantıksal dışlamalı OR işleci ^</span><span class="sxs-lookup"><span data-stu-id="75cac-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="75cac-126">`^` işleci, işlenenlerinin mantıksal XOR olarak da bilinen mantıksal dışlamalı veya bir şekilde hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="75cac-127">`x ^ y` sonucu, `x` `true` olarak değerlendirilir ve `y` `false`olarak değerlendirilir ve `x` `false` olarak değerlendirilir `true`.`y``true`</span><span class="sxs-lookup"><span data-stu-id="75cac-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="75cac-128">Aksi takdirde, sonuç `false`.</span><span class="sxs-lookup"><span data-stu-id="75cac-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="75cac-129">Diğer bir deyişle, `bool` işlenenleri için `^` işleci, [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=`aynı sonucu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="75cac-130">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için, `^` işleci, işlenenlerinin [bit düzeyinde MANTıKSAL dışlamalı veya](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) bunların işlenenleri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="75cac-131">Mantıksal OR işleci |</span><span class="sxs-lookup"><span data-stu-id="75cac-131">Logical OR operator |</span></span>

<span data-ttu-id="75cac-132">`|` işleci, işlenenlerinin mantıksal veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="75cac-133">`x | y` sonucu, `x` veya `y` `true`olarak değerlendirilirse `true`.</span><span class="sxs-lookup"><span data-stu-id="75cac-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="75cac-134">Aksi takdirde, sonuç `false`.</span><span class="sxs-lookup"><span data-stu-id="75cac-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="75cac-135">`|` işleci, sol taraftaki işlenen `true`olarak değerlendirilse bile her iki işleneni de değerlendirir, böylece işlem sonucu sağ işlenen değerden bağımsız olarak `true`.</span><span class="sxs-lookup"><span data-stu-id="75cac-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="75cac-136">Aşağıdaki örnekte, `|` işlecinin sağ işleneni, sol işlenenin değerinden bağımsız olarak gerçekleştirilen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="75cac-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="75cac-137">[Koşullu MANTıKSAL or işleci](#conditional-logical-or-operator-) `||` Ayrıca, işlenenlerinin mantıksal veya işlecini hesaplar, ancak sol işlenen `true`olarak değerlendirilirse sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="75cac-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="75cac-138">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)işlenenleri için `|` işleci, işlenenlerinin [BIT düzeyinde mantıksal veya](bitwise-and-shift-operators.md#logical-or-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="75cac-139">Koşullu mantıksal AND işleci &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="75cac-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="75cac-140">"Kısa devre dışı" mantıksal AND işleci olarak da bilinen Koşullu mantıksal ve işleç `&&`, işlenenlerinin mantıksal ve işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="75cac-141">`x && y` sonucu, hem `x` hem de `y` `true`olarak değerlendirilir `true`.</span><span class="sxs-lookup"><span data-stu-id="75cac-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="75cac-142">Aksi takdirde, sonuç `false`.</span><span class="sxs-lookup"><span data-stu-id="75cac-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="75cac-143">`x` `false`değerlendirilirse `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="75cac-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="75cac-144">Aşağıdaki örnekte, `&&` işlecinin sağ işleneni, sol taraftaki işlenen `false`olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="75cac-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="75cac-145">[MANTıKSAL and işleci](#logical-and-operator-) `&` Ayrıca IŞLENENLERININ mantıksal ve ' lerini hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="75cac-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="75cac-146">Koşullu mantıksal OR işleci | |</span><span class="sxs-lookup"><span data-stu-id="75cac-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="75cac-147">"Kısa devre dışı" mantıksal OR işleci olarak da bilinen Koşullu mantıksal OR işleci `||`, işlenenlerinin mantıksal veya işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="75cac-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="75cac-148">`x || y` sonucu, `x` veya `y` `true`olarak değerlendirilirse `true`.</span><span class="sxs-lookup"><span data-stu-id="75cac-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="75cac-149">Aksi takdirde, sonuç `false`.</span><span class="sxs-lookup"><span data-stu-id="75cac-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="75cac-150">`x` `true`değerlendirilirse `y` değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="75cac-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="75cac-151">Aşağıdaki örnekte, `||` işlecinin sağ işleneni, sol taraftaki işlenen `true`olarak değerlendirilirse gerçekleştirilmeyen bir yöntem çağrıdır:</span><span class="sxs-lookup"><span data-stu-id="75cac-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="75cac-152">Ayrıca, [MANTıKSAL or işleci](#logical-or-operator-) `|` işlenenlerini de hesaplar, ancak her iki işleneni de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="75cac-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="75cac-153">Null yapılabilir Boolean mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="75cac-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="75cac-154">`bool?` işlenenleri için, `&` ve `|` işleçleri üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="75cac-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="75cac-155">Bu işleçlerin semantiği aşağıdaki tablo tarafından tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="75cac-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="75cac-156">x</span><span class="sxs-lookup"><span data-stu-id="75cac-156">x</span></span>|<span data-ttu-id="75cac-157">y</span><span class="sxs-lookup"><span data-stu-id="75cac-157">y</span></span>|<span data-ttu-id="75cac-158">x & y</span><span class="sxs-lookup"><span data-stu-id="75cac-158">x&y</span></span>|<span data-ttu-id="75cac-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="75cac-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="75cac-160">true</span><span class="sxs-lookup"><span data-stu-id="75cac-160">true</span></span>|<span data-ttu-id="75cac-161">true</span><span class="sxs-lookup"><span data-stu-id="75cac-161">true</span></span>|<span data-ttu-id="75cac-162">true</span><span class="sxs-lookup"><span data-stu-id="75cac-162">true</span></span>|<span data-ttu-id="75cac-163">true</span><span class="sxs-lookup"><span data-stu-id="75cac-163">true</span></span>|  
|<span data-ttu-id="75cac-164">true</span><span class="sxs-lookup"><span data-stu-id="75cac-164">true</span></span>|<span data-ttu-id="75cac-165">false</span><span class="sxs-lookup"><span data-stu-id="75cac-165">false</span></span>|<span data-ttu-id="75cac-166">false</span><span class="sxs-lookup"><span data-stu-id="75cac-166">false</span></span>|<span data-ttu-id="75cac-167">true</span><span class="sxs-lookup"><span data-stu-id="75cac-167">true</span></span>|  
|<span data-ttu-id="75cac-168">true</span><span class="sxs-lookup"><span data-stu-id="75cac-168">true</span></span>|<span data-ttu-id="75cac-169">null</span><span class="sxs-lookup"><span data-stu-id="75cac-169">null</span></span>|<span data-ttu-id="75cac-170">null</span><span class="sxs-lookup"><span data-stu-id="75cac-170">null</span></span>|<span data-ttu-id="75cac-171">true</span><span class="sxs-lookup"><span data-stu-id="75cac-171">true</span></span>|  
|<span data-ttu-id="75cac-172">false</span><span class="sxs-lookup"><span data-stu-id="75cac-172">false</span></span>|<span data-ttu-id="75cac-173">true</span><span class="sxs-lookup"><span data-stu-id="75cac-173">true</span></span>|<span data-ttu-id="75cac-174">false</span><span class="sxs-lookup"><span data-stu-id="75cac-174">false</span></span>|<span data-ttu-id="75cac-175">true</span><span class="sxs-lookup"><span data-stu-id="75cac-175">true</span></span>|  
|<span data-ttu-id="75cac-176">false</span><span class="sxs-lookup"><span data-stu-id="75cac-176">false</span></span>|<span data-ttu-id="75cac-177">false</span><span class="sxs-lookup"><span data-stu-id="75cac-177">false</span></span>|<span data-ttu-id="75cac-178">false</span><span class="sxs-lookup"><span data-stu-id="75cac-178">false</span></span>|<span data-ttu-id="75cac-179">false</span><span class="sxs-lookup"><span data-stu-id="75cac-179">false</span></span>|  
|<span data-ttu-id="75cac-180">false</span><span class="sxs-lookup"><span data-stu-id="75cac-180">false</span></span>|<span data-ttu-id="75cac-181">null</span><span class="sxs-lookup"><span data-stu-id="75cac-181">null</span></span>|<span data-ttu-id="75cac-182">false</span><span class="sxs-lookup"><span data-stu-id="75cac-182">false</span></span>|<span data-ttu-id="75cac-183">null</span><span class="sxs-lookup"><span data-stu-id="75cac-183">null</span></span>|  
|<span data-ttu-id="75cac-184">null</span><span class="sxs-lookup"><span data-stu-id="75cac-184">null</span></span>|<span data-ttu-id="75cac-185">true</span><span class="sxs-lookup"><span data-stu-id="75cac-185">true</span></span>|<span data-ttu-id="75cac-186">null</span><span class="sxs-lookup"><span data-stu-id="75cac-186">null</span></span>|<span data-ttu-id="75cac-187">true</span><span class="sxs-lookup"><span data-stu-id="75cac-187">true</span></span>|  
|<span data-ttu-id="75cac-188">null</span><span class="sxs-lookup"><span data-stu-id="75cac-188">null</span></span>|<span data-ttu-id="75cac-189">false</span><span class="sxs-lookup"><span data-stu-id="75cac-189">false</span></span>|<span data-ttu-id="75cac-190">false</span><span class="sxs-lookup"><span data-stu-id="75cac-190">false</span></span>|<span data-ttu-id="75cac-191">null</span><span class="sxs-lookup"><span data-stu-id="75cac-191">null</span></span>|  
|<span data-ttu-id="75cac-192">null</span><span class="sxs-lookup"><span data-stu-id="75cac-192">null</span></span>|<span data-ttu-id="75cac-193">null</span><span class="sxs-lookup"><span data-stu-id="75cac-193">null</span></span>|<span data-ttu-id="75cac-194">null</span><span class="sxs-lookup"><span data-stu-id="75cac-194">null</span></span>|<span data-ttu-id="75cac-195">null</span><span class="sxs-lookup"><span data-stu-id="75cac-195">null</span></span>|  

<span data-ttu-id="75cac-196">Bu işleçlerin davranışı, null yapılabilir değer türleriyle tipik işleç davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="75cac-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="75cac-197">Genellikle, bir değer türünün işlenenleri için tanımlanan bir işleç, karşılık gelen Nullable değer türünün işlenenleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75cac-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="75cac-198">Bu tür bir operatör, işlenenleri `null`değerlendirilirse `null` üretir.</span><span class="sxs-lookup"><span data-stu-id="75cac-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="75cac-199">Ancak, `&` ve `|` işleçleri, işlenenlerden biri `null`olarak değerlendirilse bile null olmayan üretebilir.</span><span class="sxs-lookup"><span data-stu-id="75cac-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="75cac-200">Null yapılabilir değer türleriyle operatör davranışı hakkında daha fazla bilgi için, [Nullable değer türleri](../builtin-types/nullable-value-types.md) makalesinin [yükseltilmemiş işleçleri](../builtin-types/nullable-value-types.md#lifted-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="75cac-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="75cac-201">Aşağıdaki örnekte gösterildiği gibi, `!` ve `^` işleçlerini `bool?` işlenenleriyle de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="75cac-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="75cac-202">Koşullu mantıksal işleçler `&&` ve `||` `bool?` işlenenleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="75cac-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="75cac-203">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="75cac-203">Compound assignment</span></span>

<span data-ttu-id="75cac-204">Bir ikili işleç `op`için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="75cac-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="75cac-205">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="75cac-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="75cac-206">`x` hariç, yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="75cac-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="75cac-207">`&`, `|`ve `^` işleçleri, aşağıdaki örnekte gösterildiği gibi bileşik atamayı destekler:</span><span class="sxs-lookup"><span data-stu-id="75cac-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="75cac-208">Koşullu mantıksal işleçler `&&` ve `||` bileşik atamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="75cac-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="75cac-209">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="75cac-209">Operator precedence</span></span>

<span data-ttu-id="75cac-210">Aşağıdaki liste, en yüksek öncelikten başlayarak mantıksal işleçleri en düşüğe göre sıralar:</span><span class="sxs-lookup"><span data-stu-id="75cac-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="75cac-211">Mantıksal Değilleme İşleci `!`</span><span class="sxs-lookup"><span data-stu-id="75cac-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="75cac-212">Mantıksal AND işleci `&`</span><span class="sxs-lookup"><span data-stu-id="75cac-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="75cac-213">Mantıksal dışlamalı OR işleci `^`</span><span class="sxs-lookup"><span data-stu-id="75cac-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="75cac-214">Mantıksal OR işleci `|`</span><span class="sxs-lookup"><span data-stu-id="75cac-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="75cac-215">Koşullu mantıksal AND işleci `&&`</span><span class="sxs-lookup"><span data-stu-id="75cac-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="75cac-216">Koşullu mantıksal OR işleci `||`</span><span class="sxs-lookup"><span data-stu-id="75cac-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="75cac-217">İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez, `()`kullanın:</span><span class="sxs-lookup"><span data-stu-id="75cac-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="75cac-218">Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için, [ C# işleçler](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="75cac-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="75cac-219">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="75cac-219">Operator overloadability</span></span>

<span data-ttu-id="75cac-220">Kullanıcı tanımlı bir tür `!`, `&`, `|`ve `^` işleçlerini [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="75cac-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="75cac-221">İkili işleç aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="75cac-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="75cac-222">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="75cac-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="75cac-223">Kullanıcı tanımlı bir tür koşullu mantıksal işleçleri `&&` ve `||`aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="75cac-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="75cac-224">Ancak, Kullanıcı tanımlı bir tür [true ve false işleçlerini](true-false-operators.md) ve `&` ya da `|` işlecini belirli bir şekilde aşırı yükleiyorsa, sırasıyla `&&` veya `||` işlemi bu türün işlenenleri için değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="75cac-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="75cac-225">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="75cac-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="75cac-226">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="75cac-226">C# language specification</span></span>

<span data-ttu-id="75cac-227">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="75cac-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="75cac-228">Mantıksal Değilleme İşleci</span><span class="sxs-lookup"><span data-stu-id="75cac-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="75cac-229">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="75cac-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="75cac-230">Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="75cac-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="75cac-231">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="75cac-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="75cac-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75cac-232">See also</span></span>

- [<span data-ttu-id="75cac-233">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="75cac-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="75cac-234">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="75cac-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="75cac-235">Bit düzeyinde ve kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="75cac-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
