---
title: '?: operator-C# başvurusu'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 8e6753a08bbd96f980b3c5901e763f2dfad055c6
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555376"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c372f-102">?: işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c372f-102">?: operator (C# reference)</span></span>

<span data-ttu-id="c372f-103">Üçlü işleç olarak da bilinen koşullu operatör, Boole ifadesi `?:` değerlendirir ve Boolean ifadesinin veya olarak değerlendirildiğine bağlı olarak iki deyimden birinin sonucunu döndürür `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="c372f-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="c372f-104">Koşullu işlecin sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c372f-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="c372f-105">`condition`İfade veya olarak değerlendirilmelidir `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="c372f-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="c372f-106">`condition`, Olarak değerlendirilirse `true` , `consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="c372f-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="c372f-107">`condition`, Olarak değerlendirilirse `false` , `alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="c372f-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="c372f-108">Yalnızca `consequent` veya `alternative` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c372f-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="c372f-109">`consequent`Ve türü aynı olmalıdır `alternative` veya bir türden diğerine örtük bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c372f-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="c372f-110">Koşullu operatör doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="c372f-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="c372f-111">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="c372f-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="c372f-112">Koşullu işlecin nasıl değerlendirildiğini anımsamak için aşağıdaki anımsatıcı cihazı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c372f-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="c372f-113">Aşağıdaki örnek, koşullu işlecin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c372f-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="c372f-114">Koşullu başvuru ifadesi</span><span class="sxs-lookup"><span data-stu-id="c372f-114">Conditional ref expression</span></span>

<span data-ttu-id="c372f-115">C# 7,2 ile başlayarak, bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkeni koşullu başvuru ifadesiyle koşullu olarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="c372f-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="c372f-116">Koşullu başvuru ifadesini [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya [ `ref` Yöntem bağımsız değişkeni](../keywords/ref.md#passing-an-argument-by-reference)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c372f-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="c372f-117">Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c372f-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="c372f-118">Özgün Koşul operatörü gibi, koşullu başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: `consequent` ya da `alternative` .</span><span class="sxs-lookup"><span data-stu-id="c372f-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="c372f-119">Koşullu başvuru ifadesi söz konusu olduğunda, `consequent` ve türü `alternative` aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c372f-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="c372f-120">Aşağıdaki örnek, koşullu başvuru ifadesinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c372f-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="c372f-121">Koşullu işleç ve bir `if..else` ifade</span><span class="sxs-lookup"><span data-stu-id="c372f-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="c372f-122">[İf-else](../keywords/if-else.md) ifadesinin yerine koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c372f-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="c372f-123">Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c372f-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="c372f-124">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="c372f-124">Operator overloadability</span></span>

<span data-ttu-id="c372f-125">Kullanıcı tanımlı bir tür, koşullu işleci aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="c372f-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c372f-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c372f-126">C# language specification</span></span>

<span data-ttu-id="c372f-127">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c372f-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="c372f-128">Koşullu başvuru ifadesi hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="c372f-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c372f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c372f-129">See also</span></span>

- [<span data-ttu-id="c372f-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c372f-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c372f-131">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c372f-131">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="c372f-132">if-else deyimi</span><span class="sxs-lookup"><span data-stu-id="c372f-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="c372f-133">[?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="c372f-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="c372f-134">?? ve?? = işleçleri</span><span class="sxs-lookup"><span data-stu-id="c372f-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="c372f-135">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c372f-135">ref keyword</span></span>](../keywords/ref.md)
