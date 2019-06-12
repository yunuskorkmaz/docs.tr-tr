---
title: '?: işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 2717505a0a09b9ac1c6ad43153c52771c13f7b5c
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025202"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1136f-102">?: işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1136f-102">?: operator (C# reference)</span></span>

<span data-ttu-id="1136f-103">Koşullu işleç `?:`Üçlü koşullu işleç, yaygın olarak bilinen bir Boole ifadesini değerlendirir ve bir Boole ifadesi mi değerlendiren bağlı olarak iki ifadenin değerlendirme sonucu döndürür `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="1136f-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="1136f-104">İle başlayarak C# 7.2, [ref koşullu ifadesi](#conditional-ref-expression) başvuru iki ifadeden birini sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1136f-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="1136f-105">Koşullu işlecin sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1136f-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="1136f-106">`condition` İfade gerekir değerlendirmek için `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="1136f-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="1136f-107">Varsa `condition` değerlendiren `true`, `consequent` ifade değerlendirilir ve sonuç işleminin sonucu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1136f-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="1136f-108">Varsa `condition` değerlendiren `false`, `alternative` ifade değerlendirilir ve sonuç işleminin sonucu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1136f-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="1136f-109">Yalnızca `consequent` veya `alternative` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1136f-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="1136f-110">Türünü `consequent` ve `alternative` aynı veya orada bir türden diğerine örtülü bir dönüştürme diğerine olmalıdır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1136f-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="1136f-111">Koşullu işleç sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="1136f-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="1136f-112">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="1136f-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="1136f-113">Koşullu işleç nasıl değerlendirilir hatırlamak şu anımsatıcı cihazı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1136f-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="1136f-114">Aşağıdaki örnek, koşullu işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1136f-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="1136f-115">Ref koşullu ifadesi</span><span class="sxs-lookup"><span data-stu-id="1136f-115">Conditional ref expression</span></span>

<span data-ttu-id="1136f-116">İle başlayarak C# 7.2, iki ifadeden birini sonucu başvuru döndürmek için koşullu ref ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1136f-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="1136f-117">Bu başvuru atayabilirsiniz bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni veya olarak bir [başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya farklı bir [ `ref` yöntemi parametre](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="1136f-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="1136f-118">Ref koşullu ifadesi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1136f-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="1136f-119">Ref koşullu ifadesi iki ifadeden yalnızca biri özgün koşullu işleç gibi değerlendirilir: ya da `consequent` veya `alternative`.</span><span class="sxs-lookup"><span data-stu-id="1136f-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="1136f-120">Ref koşullu ifadenin türü söz konusu olduğunda `consequent` ve `alternative` aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1136f-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="1136f-121">Aşağıdaki örnek, ref koşullu ifadesi kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="1136f-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

<span data-ttu-id="1136f-122">Daha fazla bilgi için [özellik teklif Not](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="1136f-122">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="1136f-123">Koşullu işleç ve bir `if..else` deyimi</span><span class="sxs-lookup"><span data-stu-id="1136f-123">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="1136f-124">Üzerinde koşullu işlecinin kullanımı bir [if-else](../keywords/if-else.md) deyimi neden olabilir durumlarda daha kısa kodu koşullu olarak bir değeri hesaplamak gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="1136f-124">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="1136f-125">Aşağıdaki örnek, negatif veya negatif olmayan tamsayı sınıflandırmak için iki yolunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="1136f-125">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="1136f-126">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="1136f-126">Operator overloadability</span></span>

<span data-ttu-id="1136f-127">Koşullu işleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="1136f-127">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1136f-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1136f-128">C# language specification</span></span>

<span data-ttu-id="1136f-129">Daha fazla bilgi için [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1136f-129">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1136f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1136f-130">See also</span></span>

- [<span data-ttu-id="1136f-131">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="1136f-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1136f-132">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="1136f-132">C# operators</span></span>](index.md)
- [<span data-ttu-id="1136f-133">if-else deyimi</span><span class="sxs-lookup"><span data-stu-id="1136f-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="1136f-134">[?. ve? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="1136f-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="1136f-135">?? işleci</span><span class="sxs-lookup"><span data-stu-id="1136f-135">?? operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="1136f-136">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="1136f-136">ref keyword</span></span>](../keywords/ref.md)
