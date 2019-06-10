---
title: Eşitlik işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# eşitlik Karşılaştırma işleçleri.
ms.date: 03/28/2019
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
ms.openlocfilehash: 3b2aeceae8371f0728da2bcebbbe597ee135f256
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758270"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="13db7-103">Eşitlik işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="13db7-103">Equality operators (C# Reference)</span></span>

<span data-ttu-id="13db7-104">[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenleri eşit olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="13db7-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="13db7-105">Eşitlik işleci ==</span><span class="sxs-lookup"><span data-stu-id="13db7-105">Equality operator ==</span></span>

<span data-ttu-id="13db7-106">Eşitlik işleci `==` döndürür `true` işlenenleri eşitse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="13db7-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="13db7-107">Değer türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="13db7-107">Value types equality</span></span>

<span data-ttu-id="13db7-108">İşlenen [yerleşik türlerin](../keywords/value-types-table.md) değerlerine eşitse eşit:</span><span class="sxs-lookup"><span data-stu-id="13db7-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="13db7-109">İçin `==`, [ `<`, `>`, `<=`, ve `>=` ](comparison-operators.md) herhangi işlenenden değilse, birkaç işleçleri (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlemin sonucunu olduğu`false`.</span><span class="sxs-lookup"><span data-stu-id="13db7-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="13db7-110">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`.</span><span class="sxs-lookup"><span data-stu-id="13db7-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="13db7-111">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="13db7-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="13db7-112">İki işleneni de aynı [enum](../keywords/enum.md) türü temel alınan integral türünün karşılık gelen değerler eşitse eşit.</span><span class="sxs-lookup"><span data-stu-id="13db7-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="13db7-113">Kullanıcı tanımlı [yapı](../keywords/struct.md) türleri desteklemez `==` varsayılan işleci.</span><span class="sxs-lookup"><span data-stu-id="13db7-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="13db7-114">Desteklemek için `==` işleci, bir kullanıcı tarafından tanımlanan yapı gerekir [aşırı](#operator-overloadability) bu.</span><span class="sxs-lookup"><span data-stu-id="13db7-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="13db7-115">İle başlayarak C# 7.3, `==` ve `!=` işleçleri tarafından desteklenen C# [diziler](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="13db7-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="13db7-116">Daha fazla bilgi için [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümünü [ C# tanımlama grubu türleri](../../tuples.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="13db7-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="13db7-117">Dize eşitliği</span><span class="sxs-lookup"><span data-stu-id="13db7-117">String equality</span></span>

<span data-ttu-id="13db7-118">İki [dize](../keywords/string.md) işlenenler, bunların her ikisi de eşit `null` veya her iki dize örnekleri aynı uzunluktadır ve aynı karakterlerin her karakter konumunda vardır:</span><span class="sxs-lookup"><span data-stu-id="13db7-118">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="13db7-119">Büyük/küçük harfe sıralı karşılaştırma olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="13db7-119">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="13db7-120">Dize karşılaştırması hakkında daha fazla bilgi için bkz: [dizeleri karşılaştırmak nasıl C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="13db7-120">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="13db7-121">Başvuru türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="13db7-121">Reference types equality</span></span>

<span data-ttu-id="13db7-122">İki dışında `string` başvuru türü işlenen, bunlar aynı nesneye başvurduğunuzda eşit:</span><span class="sxs-lookup"><span data-stu-id="13db7-122">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="13db7-123">Örnekte gösterildiği gibi destek kullanıcı tarafından tanımlanan başvuru türleri `==` varsayılan işleci.</span><span class="sxs-lookup"><span data-stu-id="13db7-123">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="13db7-124">Ancak, bir kullanıcı tarafından tanımlanan başvuru türü aşırı yüklenebilir `==` işleci.</span><span class="sxs-lookup"><span data-stu-id="13db7-124">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="13db7-125">Bir başvuru türü aşırı `==` işleci, kullanım <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> iki başvuru türü aynı nesneye başvuruyorsa, denetlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="13db7-125">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="13db7-126">Eşitsizlik işleci! =</span><span class="sxs-lookup"><span data-stu-id="13db7-126">Inequality operator !=</span></span>

<span data-ttu-id="13db7-127">Eşitsizlik işleci `!=` döndürür `true` işlenenleri eşit değilse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="13db7-127">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="13db7-128">İşlenen için [yerleşik türler](../keywords/built-in-types-table.md), ifade `x != y` ifade aynı sonucu üretir `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="13db7-128">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="13db7-129">Tür eşitlik hakkında daha fazla bilgi için bkz: [eşitlik işleci](#equality-operator-) bölümü.</span><span class="sxs-lookup"><span data-stu-id="13db7-129">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="13db7-130">Aşağıdaki örnek, kullanımını gösterir. `!=` işleci:</span><span class="sxs-lookup"><span data-stu-id="13db7-130">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="13db7-131">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="13db7-131">Operator overloadability</span></span>

<span data-ttu-id="13db7-132">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `==` ve `!=` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="13db7-132">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="13db7-133">Bir tür iki işleçlerden aşırı de başka bir aşırı gerekir.</span><span class="sxs-lookup"><span data-stu-id="13db7-133">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="13db7-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="13db7-134">C# language specification</span></span>

<span data-ttu-id="13db7-135">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="13db7-135">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13db7-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13db7-136">See also</span></span>

- [<span data-ttu-id="13db7-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="13db7-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13db7-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="13db7-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13db7-139">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="13db7-139">C# Operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="13db7-140">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="13db7-140">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="13db7-141">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="13db7-141">Comparison operators</span></span>](comparison-operators.md)
