---
description: '?: operator-C# başvurusu'
title: '?: operator-C# başvurusu'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: b6add045983619169bed0cd9f32eb27dba0a0338
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738885"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e963d-103">?: işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e963d-103">?: operator (C# reference)</span></span>

<span data-ttu-id="e963d-104">Üçlü işleç olarak da bilinen koşullu operatör, Boole ifadesi `?:` değerlendirir ve Boolean ifadesinin veya olarak değerlendirildiğine bağlı olarak iki deyimden birinin sonucunu döndürür `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="e963d-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="e963d-105">Koşullu işlecin sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="e963d-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="e963d-106">`condition`İfade veya olarak değerlendirilmelidir `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="e963d-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="e963d-107">`condition`, Olarak değerlendirilirse `true` , `consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="e963d-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="e963d-108">`condition`, Olarak değerlendirilirse `false` , `alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="e963d-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="e963d-109">Yalnızca `consequent` veya `alternative` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e963d-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="e963d-110">C# 9,0 ' den başlayarak Koşullu ifadeler Target türünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e963d-110">Beginning with C# 9.0, conditional expressions are target-typed.</span></span> <span data-ttu-id="e963d-111">Diğer bir deyişle, koşullu bir ifadenin hedef türü biliniyorsa, `consequent` `alternative` Aşağıdaki örnekte gösterildiği gibi, ve türlerinin hedef türüne örtülü olarak dönüştürülebilir olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e963d-111">That is, if a target type of a conditional expression is known, the types of `consequent` and `alternative` must be implicitly convertible to the target type, as the following example shows:</span></span>

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

<span data-ttu-id="e963d-112">Koşullu ifadenin hedef türü bilinmiyorsa (örneğin, [`var`](../keywords/var.md) anahtar sözcüğünü kullandığınızda) veya C# 8,0 ve önceki sürümlerde, türü `consequent` ve `alternative` aynı olmalıdır veya bir türden diğerine örtük bir dönüştürme olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e963d-112">If a target type of a conditional expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword) or in C# 8.0 and earlier, the type of `consequent` and `alternative` must be the same or there must be an implicit conversion from one type to the other:</span></span>

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

<span data-ttu-id="e963d-113">Koşullu operatör doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="e963d-113">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="e963d-114">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="e963d-114">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="e963d-115">Koşullu işlecin nasıl değerlendirildiğini anımsamak için aşağıdaki anımsatıcı cihazı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e963d-115">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="e963d-116">Aşağıdaki örnek, koşullu işlecin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e963d-116">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="e963d-117">Koşullu başvuru ifadesi</span><span class="sxs-lookup"><span data-stu-id="e963d-117">Conditional ref expression</span></span>

<span data-ttu-id="e963d-118">C# 7,2 ile başlayarak, bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkeni koşullu bir başvuru ifadesiyle koşullu olarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="e963d-118">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with a conditional ref expression.</span></span> <span data-ttu-id="e963d-119">Ayrıca, bir [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya [ `ref` Yöntem bağımsız değişkeni](../keywords/ref.md#passing-an-argument-by-reference)olarak bir koşullu başvuru ifadesi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e963d-119">You can also use a conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="e963d-120">Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e963d-120">The syntax for a conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="e963d-121">Özgün koşullu operatör gibi, koşullu bir başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: `consequent` ya da `alternative` .</span><span class="sxs-lookup"><span data-stu-id="e963d-121">Like the original conditional operator, a conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="e963d-122">Koşullu başvuru ifadesi durumunda, `consequent` ve türü `alternative` aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e963d-122">In the case of a conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span> <span data-ttu-id="e963d-123">Koşullu başvuru ifadeleri Target türünde değil.</span><span class="sxs-lookup"><span data-stu-id="e963d-123">Conditional ref expressions are not target-typed.</span></span>

<span data-ttu-id="e963d-124">Aşağıdaki örnek, bir koşullu başvuru ifadesinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e963d-124">The following example demonstrates the usage of a conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="e963d-125">Koşullu işleç ve bir `if..else` ifade</span><span class="sxs-lookup"><span data-stu-id="e963d-125">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="e963d-126">[İf-else](../keywords/if-else.md) ifadesinin yerine koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e963d-126">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="e963d-127">Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e963d-127">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="e963d-128">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="e963d-128">Operator overloadability</span></span>

<span data-ttu-id="e963d-129">Kullanıcı tanımlı bir tür, koşullu işleci aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="e963d-129">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e963d-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e963d-130">C# language specification</span></span>

<span data-ttu-id="e963d-131">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e963d-131">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e963d-132">C# 7,2 ve üzeri sürümlerde eklenen özellikler hakkında daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:</span><span class="sxs-lookup"><span data-stu-id="e963d-132">For more information about features added in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="e963d-133">Koşullu başvuru ifadeleri (C# 7,2)</span><span class="sxs-lookup"><span data-stu-id="e963d-133">Conditional ref expressions (C# 7.2)</span></span>](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [<span data-ttu-id="e963d-134">Target türü belirtilmiş koşullu ifade (C# 9,0)</span><span class="sxs-lookup"><span data-stu-id="e963d-134">Target-typed conditional expression (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a><span data-ttu-id="e963d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e963d-135">See also</span></span>

- [<span data-ttu-id="e963d-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e963d-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e963d-137">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e963d-137">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="e963d-138">if-else deyimi</span><span class="sxs-lookup"><span data-stu-id="e963d-138">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="e963d-139">[?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="e963d-139">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="e963d-140">?? ve?? = işleçleri</span><span class="sxs-lookup"><span data-stu-id="e963d-140">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="e963d-141">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="e963d-141">ref keyword</span></span>](../keywords/ref.md)
