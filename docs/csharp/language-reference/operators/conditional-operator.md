---
title: '?: operator- C# Reference'
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
ms.openlocfilehash: 7397c5b2b2278f487a98b029b00924d3151913db
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036301"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2921f-102">?: işleç (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="2921f-102">?: operator (C# reference)</span></span>

<span data-ttu-id="2921f-103">Üçlü işleç olarak da bilinen koşullu operatör `?:`, Boolean ifadesinin `true` veya `false`olarak değerlendirildiğine bağlı olarak bir Boole ifadesi değerlendirir ve iki ifadeden birinin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2921f-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="2921f-104">7,2 ile C# başlayarak, [koşullu başvuru ifadesi](#conditional-ref-expression) iki ifadeden birinin sonucuna başvuruyu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2921f-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="2921f-105">Koşullu işlecin sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="2921f-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="2921f-106">`condition` ifadesi `true` veya `false`olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2921f-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="2921f-107">`condition` `true`değerlendirilirse, `consequent` ifadesi değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="2921f-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="2921f-108">`condition` `false`değerlendirilirse, `alternative` ifadesi değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="2921f-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="2921f-109">Yalnızca `consequent` veya `alternative` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2921f-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="2921f-110">`consequent` ve `alternative` türü aynı olmalıdır veya bir türden diğerine örtük bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2921f-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="2921f-111">Koşullu operatör doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="2921f-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="2921f-112">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="2921f-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="2921f-113">Koşullu işlecin nasıl değerlendirildiğini anımsamak için aşağıdaki anımsatıcı cihazı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2921f-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="2921f-114">Aşağıdaki örnek, koşullu işlecin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2921f-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="2921f-115">Koşullu başvuru ifadesi</span><span class="sxs-lookup"><span data-stu-id="2921f-115">Conditional ref expression</span></span>

<span data-ttu-id="2921f-116">7,2 ' C# den başlayarak, iki ifadeden birinin sonucuna başvuruyu döndürmek için koşullu başvuru ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2921f-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="2921f-117">Bu başvuruyu bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenine atayabilir veya bir [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya [`ref` yöntemi parametresi](../keywords/ref.md#passing-an-argument-by-reference)olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2921f-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="2921f-118">Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2921f-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="2921f-119">Özgün koşullu operatör gibi, koşullu başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: `consequent` ya da `alternative`.</span><span class="sxs-lookup"><span data-stu-id="2921f-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="2921f-120">Koşullu başvuru ifadesi durumunda `consequent` ve `alternative` türü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2921f-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="2921f-121">Aşağıdaki örnek, koşullu başvuru ifadesinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2921f-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="2921f-122">Koşullu işleç ve bir `if..else` ekstresi</span><span class="sxs-lookup"><span data-stu-id="2921f-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="2921f-123">[İf-else](../keywords/if-else.md) ifadesinin yerine koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2921f-123">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="2921f-124">Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2921f-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="2921f-125">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="2921f-125">Operator overloadability</span></span>

<span data-ttu-id="2921f-126">Kullanıcı tanımlı bir tür, koşullu işleci aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="2921f-126">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2921f-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2921f-127">C# language specification</span></span>

<span data-ttu-id="2921f-128">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2921f-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="2921f-129">Koşullu başvuru ifadesi hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="2921f-129">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2921f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2921f-130">See also</span></span>

- [<span data-ttu-id="2921f-131">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="2921f-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2921f-132">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="2921f-132">C# operators</span></span>](index.md)
- [<span data-ttu-id="2921f-133">if-else beyanı</span><span class="sxs-lookup"><span data-stu-id="2921f-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="2921f-134">[?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="2921f-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="2921f-135">?? ve?? = işleçleri</span><span class="sxs-lookup"><span data-stu-id="2921f-135">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="2921f-136">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="2921f-136">ref keyword</span></span>](../keywords/ref.md)
