---
title: Eşitlik işleçleri- C# başvuru
description: Eşitlik karşılaştırma C# işleçleri ve C# tür eşitlik hakkında bilgi edinin.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 6771edcca8159b0805018c16167b25c287d3152c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743737"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="bc3c6-103">Eşitlik işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="bc3c6-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="bc3c6-104">[`==` (eşitlik)](#equality-operator-) ve [`!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenlerinin eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="bc3c6-105">Eşitlik işleci = =</span><span class="sxs-lookup"><span data-stu-id="bc3c6-105">Equality operator ==</span></span>

<span data-ttu-id="bc3c6-106">`==` eşitlik işleci, işlenenleri eşitse `true` döndürür `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="bc3c6-107">Değer türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="bc3c6-107">Value types equality</span></span>

<span data-ttu-id="bc3c6-108">[Yerleşik değer türlerinin](../builtin-types/value-types.md#built-in-value-types) işlenenleri, değerleri eşitse eşittir:</span><span class="sxs-lookup"><span data-stu-id="bc3c6-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="bc3c6-109">`==`, [`<`, `>`, `<=`ve `>=`](comparison-operators.md) işleçleri için, işlenenlerin herhangi biri bir sayı değilse (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlemin sonucu `false`olur.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="bc3c6-110">Diğer bir deyişle, `NaN` değeri, `NaN`dahil herhangi bir `double` (veya `float`) değerinden daha fazla, daha küçüktür veya eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="bc3c6-111">Daha fazla bilgi ve örnek için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesi.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="bc3c6-112">Temeldeki integral türünün karşılık gelen değerleri eşitse aynı [sabit listesi](../builtin-types/enum.md) türünün iki işleneni eşittir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="bc3c6-113">Kullanıcı tanımlı [Yapı](../keywords/struct.md) türleri, varsayılan olarak `==` işlecini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="bc3c6-114">`==` işlecini desteklemek için Kullanıcı tanımlı bir yapının onu [tekrar yüklemesi](operator-overloading.md) gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="bc3c6-115">7,3 ile C# başlayarak, `==` ve `!=` işleçleri C# [diziler](../../tuples.md)tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="bc3c6-116">Daha fazla bilgi için [ C# demet türleri](../../tuples.md) makalesinin [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="bc3c6-117">Başvuru türleri eşitliği</span><span class="sxs-lookup"><span data-stu-id="bc3c6-117">Reference types equality</span></span>

<span data-ttu-id="bc3c6-118">Varsayılan olarak, iki başvuru türü işlenen aynı nesneye başvurduklarında eşittir:</span><span class="sxs-lookup"><span data-stu-id="bc3c6-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="bc3c6-119">Örnekte gösterildiği gibi, Kullanıcı tanımlı başvuru türleri varsayılan olarak `==` işlecini destekler.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="bc3c6-120">Ancak, bir başvuru türü `==` işlecini aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="bc3c6-121">Bir başvuru türü `==` işlecini aşırı yükle, bu türden iki başvurunun aynı nesneye başvurmasını denetlemek için <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="bc3c6-122">Dize eşitlik</span><span class="sxs-lookup"><span data-stu-id="bc3c6-122">String equality</span></span>

<span data-ttu-id="bc3c6-123">İki [dize](../builtin-types/reference-types.md#the-string-type) işleneni her ikisi de `null` veya her iki dize örneği de aynı uzunluktadır ve her bir karakter konumunda aynı karakterlere sahip olduğunda eşittir:</span><span class="sxs-lookup"><span data-stu-id="bc3c6-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="bc3c6-124">Bu, büyük/küçük harfe duyarlı bir sıra karşılaştırmasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="bc3c6-125">Dize karşılaştırması hakkında daha fazla bilgi için bkz. [dizeleri C#karşılaştırma ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="bc3c6-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="bc3c6-126">Temsilci eşitlik</span><span class="sxs-lookup"><span data-stu-id="bc3c6-126">Delegate equality</span></span>

<span data-ttu-id="bc3c6-127">Aynı çalışma zamanı türünün iki [temsilci](../../programming-guide/delegates/index.md) işleneni, her ikisi de `null`, ya da çağrı listeleri aynı uzunluktadır ve her konumda eşit girdilere sahip olduğunda eşittir:</span><span class="sxs-lookup"><span data-stu-id="bc3c6-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="bc3c6-128">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md), [eşitlik işleçlerini devretmek](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="bc3c6-129">Anlamsal olarak özdeş [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirmesinden üretilen temsilciler, aşağıdaki örnekte gösterildiği gibi eşit değildir:</span><span class="sxs-lookup"><span data-stu-id="bc3c6-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="bc3c6-130">Eşitsizlik işleci! =</span><span class="sxs-lookup"><span data-stu-id="bc3c6-130">Inequality operator !=</span></span>

<span data-ttu-id="bc3c6-131">Eşitsizlik işleci `!=`, işlenenleri eşit değilse `true` döndürür `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="bc3c6-132">[Yerleşik türlerin](../keywords/built-in-types-table.md)işlenenleri için ifade `x != y`, ifade `!(x == y)`aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-132">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="bc3c6-133">Tür eşitliği hakkında daha fazla bilgi için [eşitlik işleci](#equality-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="bc3c6-134">Aşağıdaki örnek `!=` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="bc3c6-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="bc3c6-135">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="bc3c6-135">Operator overloadability</span></span>

<span data-ttu-id="bc3c6-136">Kullanıcı tanımlı bir tür `==` ve `!=` işleçlerini [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="bc3c6-137">Bir tür iki işleçten birini aşırı yüklediğinden, başka bir tane de aşırı yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bc3c6-138">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="bc3c6-138">C# language specification</span></span>

<span data-ttu-id="bc3c6-139">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc3c6-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc3c6-140">See also</span></span>

- [<span data-ttu-id="bc3c6-141">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="bc3c6-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bc3c6-142">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="bc3c6-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc3c6-143">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="bc3c6-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="bc3c6-144">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="bc3c6-144">Comparison operators</span></span>](comparison-operators.md)
