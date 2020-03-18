---
title: Boolean mantıksal işleçleri - C# referansı
description: Boolean operands ile mantıksal olumsuzlama, bağlaç (AND) ve kapsayıcı ve özel ayırma (OR) işlemleri gerçekleştiren C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399499"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="aea1b-103">Boolean mantıksal işleçleri (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="aea1b-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="aea1b-104">Aşağıdaki işleçler [bool](../builtin-types/bool.md) operands ile mantıksal işlemler gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="aea1b-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="aea1b-105">Unary [ `!` (mantıksal olumsuzlama)](#logical-negation-operator-) işleci.</span><span class="sxs-lookup"><span data-stu-id="aea1b-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="aea1b-106">İkili [ `&` (mantıksal AND)](#logical-and-operator-), [ `|` (mantıksal OR)](#logical-or-operator-)ve [ `^` (mantıksal özel OR)](#logical-exclusive-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="aea1b-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="aea1b-107">Bu operatörler her zaman her iki operands değerlendirmek.</span><span class="sxs-lookup"><span data-stu-id="aea1b-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="aea1b-108">İkili [ `&&` (koşullu mantıksal AND)](#conditional-logical-and-operator-) ve [ `||` (koşullu mantıksal OR)](#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="aea1b-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="aea1b-109">Bu operatörler sağ operve sadece gerekli olduğunda değerlendirirler.</span><span class="sxs-lookup"><span data-stu-id="aea1b-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="aea1b-110">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `&`için `|`, `^` , ve operatörler bitwise mantıksal işlemler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="aea1b-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="aea1b-111">Daha fazla bilgi için [Bitwise ve shift işleçleri'ne](bitwise-and-shift-operators.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="aea1b-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="aea1b-112">Mantıksal olumsuzlama operatörü!</span><span class="sxs-lookup"><span data-stu-id="aea1b-112">Logical negation operator !</span></span>

<span data-ttu-id="aea1b-113">Unary önek `!` işleci, operand'ının mantıksal olumsuzluğunu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="aea1b-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="aea1b-114">Yani, `true`üretir , eğer operand değerlendirir `false`, `false`ve , eğer operand `true`değerlendirir:</span><span class="sxs-lookup"><span data-stu-id="aea1b-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="aea1b-115">C# 8.0 ile başlayarak, `!` unary postfix işleci [null-affgiving işlecidir.](null-forgiving.md)</span><span class="sxs-lookup"><span data-stu-id="aea1b-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="aea1b-116">Mantıksal VE işleç&amp;</span><span class="sxs-lookup"><span data-stu-id="aea1b-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="aea1b-117">İşletici, `&` operandlarının mantıksal ve mantıksal ve hesaplamalarını.</span><span class="sxs-lookup"><span data-stu-id="aea1b-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="aea1b-118">Bunun sonucu `x & y` `true` ise `x` her `y` ikisi `true`de ve değerlendirmek .</span><span class="sxs-lookup"><span data-stu-id="aea1b-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="aea1b-119">Aksi takdirde, `false`sonuç .</span><span class="sxs-lookup"><span data-stu-id="aea1b-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="aea1b-120">Operatör, `&` sol daki operand'ı değerlendirse bile, operasyon `false`sonucunun sağ operand'ın `false` değerine bakılmaksızın her iki operandı da değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="aea1b-121">Aşağıdaki örnekte, `&` işleç sağ operand sol operand değeri ne olursa olsun gerçekleştirilen bir yöntem çağrısıdır:</span><span class="sxs-lookup"><span data-stu-id="aea1b-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="aea1b-122">[Koşullu mantıksal VE işleci](#conditional-logical-and-operator-) `&&` de mantıksal VE onun operands hesaplamak, ancak sağ operand değerlendirmek değil eğer sol `false`operand değerlendirir .</span><span class="sxs-lookup"><span data-stu-id="aea1b-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="aea1b-123">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `&` için, operatör [bitwise mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) onun operands hesaplar.</span><span class="sxs-lookup"><span data-stu-id="aea1b-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="aea1b-124">Unary `&` [işleci, işlecin adresidir.](pointer-related-operators.md#address-of-operator-)</span><span class="sxs-lookup"><span data-stu-id="aea1b-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="aea1b-125">Mantıksal özel OR operatörü ^</span><span class="sxs-lookup"><span data-stu-id="aea1b-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="aea1b-126">İşletici, `^` operandlarının mantıksal XOR olarak da bilinen mantıksal özel veya'sini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="aea1b-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="aea1b-127">Bunun `x ^ y` sonucu, `true` `x` `true` eğer değerlendirirve `y` `false`değerlendirirse, `x` ya `false` da `y` değerlendirir `true`ve değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="aea1b-128">Aksi takdirde, `false`sonuç .</span><span class="sxs-lookup"><span data-stu-id="aea1b-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="aea1b-129">Diğer bir `bool` deyişle, operands `^` için, operatör [eşitsizlik işleci](equality-operators.md#inequality-operator-) `!=`olarak aynı sonucu hesaplamak.</span><span class="sxs-lookup"><span data-stu-id="aea1b-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="aea1b-130">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `^` için, operatör [bitwise mantıksal özel VEYA](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) operands bilgisayara.</span><span class="sxs-lookup"><span data-stu-id="aea1b-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="aea1b-131">Mantıksal OR işleci |</span><span class="sxs-lookup"><span data-stu-id="aea1b-131">Logical OR operator |</span></span>

<span data-ttu-id="aea1b-132">İşletici, `|` operandlarının mantıksal VEYA'sini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="aea1b-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="aea1b-133">`x | y` Bunun sonucu, `true` eğer `x` `y` ya da `true`değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="aea1b-134">Aksi takdirde, `false`sonuç .</span><span class="sxs-lookup"><span data-stu-id="aea1b-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="aea1b-135">Operatör, `|` sol daki operand'ı değerlendirse bile, operasyon `true`sonucunun sağ operand'ın `true` değerine bakılmaksızın her iki operandı da değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="aea1b-136">Aşağıdaki örnekte, `|` işleç sağ operand sol operand değeri ne olursa olsun gerçekleştirilen bir yöntem çağrısıdır:</span><span class="sxs-lookup"><span data-stu-id="aea1b-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="aea1b-137">[Koşullu mantıksal OR işleci](#conditional-logical-or-operator-) `||` de onun operands mantıksal OR bilgisayar, ancak sağ operand değerlendirmek değil eğer sol operand `true`değerlendirir .</span><span class="sxs-lookup"><span data-stu-id="aea1b-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="aea1b-138">[İntegral sayısal türlerin](../builtin-types/integral-numeric-types.md)operands `|` için, operatör [bitwise mantıksal VEYA](bitwise-and-shift-operators.md#logical-or-operator-) operands bilgisayara.</span><span class="sxs-lookup"><span data-stu-id="aea1b-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="aea1b-139">Koşullu mantıksal VE işleç&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="aea1b-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="aea1b-140">Koşullu mantıksal VE `&&`işleç , aynı zamanda "kısa devre" mantıksal VE işleci olarak bilinen, mantıksal VE onun operands hesaplamak.</span><span class="sxs-lookup"><span data-stu-id="aea1b-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="aea1b-141">Bunun sonucu `x && y` `true` ise `x` her `y` ikisi `true`de ve değerlendirmek .</span><span class="sxs-lookup"><span data-stu-id="aea1b-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="aea1b-142">Aksi takdirde, `false`sonuç .</span><span class="sxs-lookup"><span data-stu-id="aea1b-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="aea1b-143">`x` Değerlendiriliyorsa, `y` `false`değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="aea1b-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="aea1b-144">Aşağıdaki örnekte, `&&` işleç sağ operand sol el operand değerlendirirse yapılmaz bir yöntem çağrısı `false`vardır:</span><span class="sxs-lookup"><span data-stu-id="aea1b-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="aea1b-145">[Mantıksal VE işleci](#logical-and-operator-) `&` de mantıksal VE onun operands bilgisayara, ama her zaman her iki operands değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="aea1b-146">Koşullu mantıksal OR işleci ||</span><span class="sxs-lookup"><span data-stu-id="aea1b-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="aea1b-147">Koşullu mantıksal OR `||`işleci , "kısa devre" mantıksal OR işleci olarak da bilinir, onun operands mantıksal VEYA bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="aea1b-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="aea1b-148">`x || y` Bunun sonucu, `true` eğer `x` `y` ya da `true`değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="aea1b-149">Aksi takdirde, `false`sonuç .</span><span class="sxs-lookup"><span data-stu-id="aea1b-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="aea1b-150">`x` Değerlendiriliyorsa, `y` `true`değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="aea1b-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="aea1b-151">Aşağıdaki örnekte, `||` işleç sağ operand sol el operand değerlendirirse yapılmaz bir yöntem çağrısı `true`vardır:</span><span class="sxs-lookup"><span data-stu-id="aea1b-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="aea1b-152">[Mantıksal OR işleci](#logical-or-operator-) `|` de onun operands mantıksal OR bilgisayar, ama her zaman her iki operands değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="aea1b-153">Nullable Boolean mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="aea1b-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="aea1b-154">Operands `bool?` için, `&` `|` ve operatörler üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="aea1b-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="aea1b-155">Bu işleçlerin anlambilimi aşağıdaki tablo ile tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="aea1b-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="aea1b-156">x</span><span class="sxs-lookup"><span data-stu-id="aea1b-156">x</span></span>|<span data-ttu-id="aea1b-157">y</span><span class="sxs-lookup"><span data-stu-id="aea1b-157">y</span></span>|<span data-ttu-id="aea1b-158">x&y</span><span class="sxs-lookup"><span data-stu-id="aea1b-158">x&y</span></span>|<span data-ttu-id="aea1b-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="aea1b-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="aea1b-160">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-160">true</span></span>|<span data-ttu-id="aea1b-161">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-161">true</span></span>|<span data-ttu-id="aea1b-162">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-162">true</span></span>|<span data-ttu-id="aea1b-163">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-163">true</span></span>|  
|<span data-ttu-id="aea1b-164">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-164">true</span></span>|<span data-ttu-id="aea1b-165">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-165">false</span></span>|<span data-ttu-id="aea1b-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-166">false</span></span>|<span data-ttu-id="aea1b-167">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-167">true</span></span>|  
|<span data-ttu-id="aea1b-168">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-168">true</span></span>|<span data-ttu-id="aea1b-169">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-169">null</span></span>|<span data-ttu-id="aea1b-170">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-170">null</span></span>|<span data-ttu-id="aea1b-171">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-171">true</span></span>|  
|<span data-ttu-id="aea1b-172">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-172">false</span></span>|<span data-ttu-id="aea1b-173">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-173">true</span></span>|<span data-ttu-id="aea1b-174">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-174">false</span></span>|<span data-ttu-id="aea1b-175">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-175">true</span></span>|  
|<span data-ttu-id="aea1b-176">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-176">false</span></span>|<span data-ttu-id="aea1b-177">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-177">false</span></span>|<span data-ttu-id="aea1b-178">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-178">false</span></span>|<span data-ttu-id="aea1b-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-179">false</span></span>|  
|<span data-ttu-id="aea1b-180">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-180">false</span></span>|<span data-ttu-id="aea1b-181">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-181">null</span></span>|<span data-ttu-id="aea1b-182">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-182">false</span></span>|<span data-ttu-id="aea1b-183">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-183">null</span></span>|  
|<span data-ttu-id="aea1b-184">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-184">null</span></span>|<span data-ttu-id="aea1b-185">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-185">true</span></span>|<span data-ttu-id="aea1b-186">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-186">null</span></span>|<span data-ttu-id="aea1b-187">true</span><span class="sxs-lookup"><span data-stu-id="aea1b-187">true</span></span>|  
|<span data-ttu-id="aea1b-188">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-188">null</span></span>|<span data-ttu-id="aea1b-189">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-189">false</span></span>|<span data-ttu-id="aea1b-190">yanlış</span><span class="sxs-lookup"><span data-stu-id="aea1b-190">false</span></span>|<span data-ttu-id="aea1b-191">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-191">null</span></span>|  
|<span data-ttu-id="aea1b-192">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-192">null</span></span>|<span data-ttu-id="aea1b-193">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-193">null</span></span>|<span data-ttu-id="aea1b-194">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-194">null</span></span>|<span data-ttu-id="aea1b-195">null</span><span class="sxs-lookup"><span data-stu-id="aea1b-195">null</span></span>|  

<span data-ttu-id="aea1b-196">Bu işleçlerin davranışı, nullable değer türleri ile tipik işleç davranışı farklıdır.</span><span class="sxs-lookup"><span data-stu-id="aea1b-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="aea1b-197">Tipik olarak, bir değer türünün operands için tanımlanan bir işleç de karşılık gelen nullable değer türü operands ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="aea1b-198">Böyle bir `null` operatör, herhangi bir operands `null`değerlendirirse üretir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="aea1b-199">Ancak, `&` operands biri değerlendirilse bile ve `|` operatörler non-null `null`üretebilir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="aea1b-200">Nullable değer türleri ile işleç davranışı hakkında daha fazla bilgi için, [Nullable değer türleri](../builtin-types/nullable-value-types.md) makalenin [Kaldırılan işleçler](../builtin-types/nullable-value-types.md#lifted-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="aea1b-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="aea1b-201">Aşağıdaki örnekte `!` görüldüğü `^` gibi, operandlu ve operandlu `bool?` işleçleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aea1b-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="aea1b-202">Koşullu mantıksal `&&` işleçler `||` ve `bool?` operands destekyok.</span><span class="sxs-lookup"><span data-stu-id="aea1b-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="aea1b-203">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="aea1b-203">Compound assignment</span></span>

<span data-ttu-id="aea1b-204">Bir ikili `op`işleç için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="aea1b-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="aea1b-205">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="aea1b-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="aea1b-206">`x` bunun dışında sadece bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="aea1b-207">, `&` `|`, `^` ve işleçler bileşik atamayı destekler, aşağıdaki örnekte görüldüğü gibi:</span><span class="sxs-lookup"><span data-stu-id="aea1b-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="aea1b-208">Koşullu mantıksal `&&` işleçler ve `||` bileşik atama desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="aea1b-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="aea1b-209">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="aea1b-209">Operator precedence</span></span>

<span data-ttu-id="aea1b-210">Aşağıdaki liste, mantıksal işleçleri en yüksek öncelikten en düşüke doğru sipariş verir:</span><span class="sxs-lookup"><span data-stu-id="aea1b-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="aea1b-211">Mantıksal olumsuzlama işleci`!`</span><span class="sxs-lookup"><span data-stu-id="aea1b-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="aea1b-212">Mantıksal VE işleç`&`</span><span class="sxs-lookup"><span data-stu-id="aea1b-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="aea1b-213">Mantıksal özel OR işleci`^`</span><span class="sxs-lookup"><span data-stu-id="aea1b-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="aea1b-214">Mantıksal VEYA işleci`|`</span><span class="sxs-lookup"><span data-stu-id="aea1b-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="aea1b-215">Koşullu mantıksal VE işleç`&&`</span><span class="sxs-lookup"><span data-stu-id="aea1b-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="aea1b-216">Koşullu mantıksal OR işleci`||`</span><span class="sxs-lookup"><span data-stu-id="aea1b-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="aea1b-217">Operatör önceliği tarafından `()`dayatılan değerlendirme sırasını değiştirmek için parantez kullanın:</span><span class="sxs-lookup"><span data-stu-id="aea1b-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="aea1b-218">Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [C# işleçleri](index.md) makalesinin [Operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="aea1b-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="aea1b-219">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="aea1b-219">Operator overloadability</span></span>

<span data-ttu-id="aea1b-220">Kullanıcı tanımlı bir tür `!`, `&` `|`, `^` , ve işleçleri [aşırı yükleyebilir.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="aea1b-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="aea1b-221">Bir ikili işleci aşırı yüklendiğinde, karşılık gelen bileşik atama işleci de örtülü olarak aşırı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="aea1b-222">Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder.</span><span class="sxs-lookup"><span data-stu-id="aea1b-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="aea1b-223">Kullanıcı tanımlı bir tür koşullu mantıksal `&&` `||`işleçleri aşırı yükleyemez ve .</span><span class="sxs-lookup"><span data-stu-id="aea1b-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="aea1b-224">Ancak, kullanıcı tanımlı bir tür doğru ve yanlış `&` `|` [işleçleri](true-false-operators.md) ve veya `&&` `||` işleci belirli bir şekilde aşırı yüklerse, sırasıyla işlem veya işlem, bu tür operands için değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="aea1b-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="aea1b-225">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı koşullu mantıksal işleçleri](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="aea1b-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aea1b-226">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="aea1b-226">C# language specification</span></span>

<span data-ttu-id="aea1b-227">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="aea1b-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="aea1b-228">Mantıksal olumsuzlama işleci</span><span class="sxs-lookup"><span data-stu-id="aea1b-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="aea1b-229">Mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="aea1b-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="aea1b-230">Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="aea1b-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="aea1b-231">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="aea1b-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="aea1b-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aea1b-232">See also</span></span>

- [<span data-ttu-id="aea1b-233">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aea1b-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="aea1b-234">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="aea1b-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="aea1b-235">Bit düzeyinde ve kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="aea1b-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
