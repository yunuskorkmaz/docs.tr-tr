---
title: '?: Operator - C# başvurusu'
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
ms.openlocfilehash: c3c875cf5b8d1b5e69cd76cb0ee4df0a989a35a0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202905"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ba7a1-102">?: İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ba7a1-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="ba7a1-103">Koşullu işleç `?:`Üçlü koşullu işleç, yaygın olarak bilinen bir Boole ifadesini değerlendirir ve bir Boole ifadesi mi değerlendiren bağlı olarak iki ifadenin değerlendirme sonucu döndürür `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="ba7a1-104">İle başlayarak C# 7.2, [ref koşullu ifadesi](#conditional-ref-expression) başvuru iki ifadeden birini sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="ba7a1-105">Koşullu işlecin sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ba7a1-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequence : alternative
```

<span data-ttu-id="ba7a1-106">`condition` İfade gerekir değerlendirmek için `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="ba7a1-107">Varsa `condition` değerlendiren `true`, `consequence` ifade değerlendirilir ve sonuç işleminin sonucu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-107">If `condition` evaluates to `true`, the `consequence` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="ba7a1-108">Varsa `condition` değerlendiren `false`, `alternative` ifade değerlendirilir ve sonuç işleminin sonucu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="ba7a1-109">Yalnızca `consequence` veya `alternative` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-109">Only `consequence` or `alternative` is evaluated.</span></span>

<span data-ttu-id="ba7a1-110">Türünü `consequence` ve `alternative` aynı veya orada bir türden diğerine örtülü bir dönüştürme diğerine olmalıdır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-110">The type of `consequence` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="ba7a1-111">Koşullu işleç sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="ba7a1-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="ba7a1-112">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="ba7a1-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

<span data-ttu-id="ba7a1-113">Aşağıdaki örnek, koşullu işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ba7a1-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="ba7a1-114">Ref koşullu ifadesi</span><span class="sxs-lookup"><span data-stu-id="ba7a1-114">Conditional ref expression</span></span>

<span data-ttu-id="ba7a1-115">İle başlayarak C# 7.2, iki ifadeden birini sonucu başvuru döndürmek için koşullu ref ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-115">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="ba7a1-116">Bu başvuru atayabilirsiniz bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni veya olarak bir [başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya farklı bir [ `ref` yöntemi parametre](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="ba7a1-116">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="ba7a1-117">Ref koşullu ifadesi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ba7a1-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequence : ref alternative
```

<span data-ttu-id="ba7a1-118">Ref koşullu ifadesi iki ifadeden yalnızca biri özgün koşullu işleç gibi değerlendirilir: ya da `consequence` veya `alternative`.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequence` or `alternative`.</span></span>

<span data-ttu-id="ba7a1-119">Ref koşullu ifadenin türü söz konusu olduğunda `consequence` ve `alternative` aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-119">In the case of the conditional ref expression, the type of `consequence` and `alternative` must be the same.</span></span>

<span data-ttu-id="ba7a1-120">Aşağıdaki örnek, ref koşullu ifadesi kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="ba7a1-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

<span data-ttu-id="ba7a1-121">Daha fazla bilgi için [özellik teklif Not](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="ba7a1-121">For more information, see the [feature proposal note](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="ba7a1-122">Koşullu işleç ve bir `if..else` deyimi</span><span class="sxs-lookup"><span data-stu-id="ba7a1-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="ba7a1-123">Üzerinde koşullu işlecinin kullanımı bir [if-else](../keywords/if-else.md) deyimi neden olabilir durumlarda daha kısa kodu koşullu olarak bir değeri hesaplamak gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-123">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="ba7a1-124">Aşağıdaki örnek, negatif veya negatif olmayan tamsayı sınıflandırmak için iki yolunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="ba7a1-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="ba7a1-125">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="ba7a1-125">Operator overloadability</span></span>

<span data-ttu-id="ba7a1-126">Koşullu işleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-126">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ba7a1-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ba7a1-127">C# language specification</span></span>

<span data-ttu-id="ba7a1-128">Daha fazla bilgi için [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba7a1-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba7a1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba7a1-129">See also</span></span>

- [<span data-ttu-id="ba7a1-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ba7a1-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ba7a1-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ba7a1-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ba7a1-132">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ba7a1-132">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ba7a1-133">if-else deyimi</span><span class="sxs-lookup"><span data-stu-id="ba7a1-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="ba7a1-134">[?. and ?[] İşleçleri](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="ba7a1-134">[?. and ?[] Operators](null-conditional-operators.md)</span></span>
- [<span data-ttu-id="ba7a1-135">?? İşleç</span><span class="sxs-lookup"><span data-stu-id="ba7a1-135">?? Operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="ba7a1-136">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="ba7a1-136">ref keyword</span></span>](../keywords/ref.md)
