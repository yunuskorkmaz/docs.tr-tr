---
title: '?: operatör - C# referansı'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399520"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f7e57-102">?: işleç (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="f7e57-102">?: operator (C# reference)</span></span>

<span data-ttu-id="f7e57-103">Koşullu işleç `?:`, üçüncül koşullu işleç olarak da bilinir, boolean ifadesini değerlendirir ve Boolean ifadesinin değerlendirip değerlendirmediğine `true` bağlı `false`olarak iki ifadeden birinin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7e57-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="f7e57-104">Koşullu işleç için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f7e57-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="f7e57-105">İfade `condition` yi `true` değerlendirmeli `false`veya .</span><span class="sxs-lookup"><span data-stu-id="f7e57-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="f7e57-106">Değerlendiriliyorsa, `condition` `consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur. `true`</span><span class="sxs-lookup"><span data-stu-id="f7e57-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="f7e57-107">Değerlendiriliyorsa, `condition` `alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur. `false`</span><span class="sxs-lookup"><span data-stu-id="f7e57-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="f7e57-108">Yalnızca `consequent` `alternative` veya değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7e57-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="f7e57-109">Türü `consequent` ve `alternative` aynı olmalıdır veya bir tür diğerine örtülü bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7e57-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="f7e57-110">Koşullu işleç sağ-bağşdırıcı, yani formun bir ifadesidir</span><span class="sxs-lookup"><span data-stu-id="f7e57-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="f7e57-111">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="f7e57-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="f7e57-112">Koşullu işleç nasıl değerlendirildiğini hatırlamak için aşağıdaki mnemonik cihazı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7e57-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="f7e57-113">Aşağıdaki örnek, koşullu işleç kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f7e57-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="f7e57-114">Koşullu ref ekspresyonu</span><span class="sxs-lookup"><span data-stu-id="f7e57-114">Conditional ref expression</span></span>

<span data-ttu-id="f7e57-115">C# 7.2 ile başlayarak, koşullu [ref](../keywords/ref.md#ref-locals) ekspresyonu ile koşullu olarak yerel veya [ref reisi yerel](../keywords/ref.md#ref-readonly-locals) değişken atanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7e57-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="f7e57-116">Koşullu ref ifadesini [referans döndürme değeri](../keywords/ref.md#reference-return-values) olarak veya [ `ref` yöntem bağımsız değişkeni](../keywords/ref.md#passing-an-argument-by-reference)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7e57-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="f7e57-117">Koşullu ref ifadesinin sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f7e57-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="f7e57-118">Özgün koşullu işleç gibi, koşullu ref ifadesi de iki ifadeden yalnızca birini değerlendirir: ya `consequent` da `alternative`.</span><span class="sxs-lookup"><span data-stu-id="f7e57-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="f7e57-119">Koşullu ref ekspresyonu durumunda, türü `consequent` `alternative` ve aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7e57-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="f7e57-120">Aşağıdaki örnek, koşullu ref ifadesinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f7e57-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="f7e57-121">Koşullu işleç `if..else` ve deyim</span><span class="sxs-lookup"><span data-stu-id="f7e57-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="f7e57-122">[If-else](../keywords/if-else.md) deyimi yerine koşullu işlecinin kullanılması, bir değeri hesaplamak için koşullu olarak ihtiyaç duyduğunuz durumlarda daha kısa koda neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7e57-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="f7e57-123">Aşağıdaki örnek, bir karşıcıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="f7e57-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="f7e57-124">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="f7e57-124">Operator overloadability</span></span>

<span data-ttu-id="f7e57-125">Kullanıcı tanımlı bir tür koşullu işleç aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="f7e57-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f7e57-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f7e57-126">C# language specification</span></span>

<span data-ttu-id="f7e57-127">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Koşullu işleci](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f7e57-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="f7e57-128">Koşullu ref ifadesi hakkında daha fazla bilgi için [özellik teklif notuna](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f7e57-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7e57-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7e57-129">See also</span></span>

- [<span data-ttu-id="f7e57-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f7e57-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f7e57-131">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="f7e57-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="f7e57-132">if-else deyimi</span><span class="sxs-lookup"><span data-stu-id="f7e57-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="f7e57-133">[?. Ve? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="f7e57-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="f7e57-134">?? Ve?? = operatörler</span><span class="sxs-lookup"><span data-stu-id="f7e57-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="f7e57-135">ref anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="f7e57-135">ref keyword</span></span>](../keywords/ref.md)
