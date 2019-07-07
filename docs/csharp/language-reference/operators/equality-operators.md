---
title: Eşitlik işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# eşitlik Karşılaştırma işleçleri ve C# eşitlik yazın.
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
ms.openlocfilehash: 3caacf8628e6ab07b731f0574ca3a0f7e973adcd
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609884"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="d2db0-103">Eşitlik işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d2db0-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="d2db0-104">[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenleri eşit olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d2db0-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="d2db0-105">Eşitlik işleci ==</span><span class="sxs-lookup"><span data-stu-id="d2db0-105">Equality operator ==</span></span>

<span data-ttu-id="d2db0-106">Eşitlik işleci `==` döndürür `true` işlenenleri eşitse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="d2db0-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="d2db0-107">Değer türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="d2db0-107">Value types equality</span></span>

<span data-ttu-id="d2db0-108">İşlenen [yerleşik türlerin](../keywords/value-types-table.md) değerlerine eşitse eşit:</span><span class="sxs-lookup"><span data-stu-id="d2db0-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="d2db0-109">İçin `==`, [ `<`, `>`, `<=`, ve `>=` ](comparison-operators.md) herhangi işlenenden değilse, birkaç işleçleri (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlemin sonucunu olduğu`false`.</span><span class="sxs-lookup"><span data-stu-id="d2db0-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="d2db0-110">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`.</span><span class="sxs-lookup"><span data-stu-id="d2db0-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="d2db0-111">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="d2db0-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="d2db0-112">İki işleneni de aynı [enum](../keywords/enum.md) türü temel alınan integral türünün karşılık gelen değerler eşitse eşit.</span><span class="sxs-lookup"><span data-stu-id="d2db0-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="d2db0-113">Kullanıcı tanımlı [yapı](../keywords/struct.md) türleri desteklemez `==` varsayılan işleci.</span><span class="sxs-lookup"><span data-stu-id="d2db0-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="d2db0-114">Desteklemek için `==` işleci, bir kullanıcı tarafından tanımlanan yapı gerekir [aşırı](#operator-overloadability) bu.</span><span class="sxs-lookup"><span data-stu-id="d2db0-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="d2db0-115">İle başlayarak C# 7.3, `==` ve `!=` işleçleri tarafından desteklenen C# [diziler](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="d2db0-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="d2db0-116">Daha fazla bilgi için [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümünü [ C# tanımlama grubu türleri](../../tuples.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="d2db0-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="d2db0-117">Başvuru türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="d2db0-117">Reference types equality</span></span>

<span data-ttu-id="d2db0-118">Varsayılan olarak, iki başvuru türü işlenen, bunlar aynı nesneye başvuruyorsa eşitse:</span><span class="sxs-lookup"><span data-stu-id="d2db0-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="d2db0-119">Örnekte gösterildiği gibi destek kullanıcı tarafından tanımlanan başvuru türleri `==` varsayılan işleci.</span><span class="sxs-lookup"><span data-stu-id="d2db0-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="d2db0-120">Ancak, bir başvuru türü aşırı yüklenebilir `==` işleci.</span><span class="sxs-lookup"><span data-stu-id="d2db0-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="d2db0-121">Bir başvuru türü aşırı `==` işleci, kullanım <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> iki başvuru türü aynı nesneye başvuruyorsa, denetlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d2db0-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="d2db0-122">Dize eşitliği</span><span class="sxs-lookup"><span data-stu-id="d2db0-122">String equality</span></span>

<span data-ttu-id="d2db0-123">İki [dize](../keywords/string.md) işlenenler, bunların her ikisi de eşit `null` veya her iki dize örnekleri aynı uzunluktadır ve aynı karakterlerin her karakter konumunda vardır:</span><span class="sxs-lookup"><span data-stu-id="d2db0-123">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="d2db0-124">Büyük/küçük harfe sıralı karşılaştırma olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d2db0-124">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="d2db0-125">Dize karşılaştırması hakkında daha fazla bilgi için bkz: [dizeleri karşılaştırmak nasıl C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="d2db0-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="d2db0-126">Temsilci eşitlik</span><span class="sxs-lookup"><span data-stu-id="d2db0-126">Delegate equality</span></span>

<span data-ttu-id="d2db0-127">İki [temsilci](../../programming-guide/delegates/index.md) işlenenler aynı çalışma zamanı tür, bunların her ikisi de eşit `null` veya çağırma listelerini aynı uzunluktadır ve her konumda eşit girdiniz:</span><span class="sxs-lookup"><span data-stu-id="d2db0-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="d2db0-128">Daha fazla bilgi için [temsilci eşitlik işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d2db0-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d2db0-129">Anlamsal olarak özdeş bir değerlendirmesinden gelen üretilen Temsilciler [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) aşağıdaki örnekte gösterildiği gibi eşit değilse:</span><span class="sxs-lookup"><span data-stu-id="d2db0-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="d2db0-130">Eşitsizlik işleci! =</span><span class="sxs-lookup"><span data-stu-id="d2db0-130">Inequality operator !=</span></span>

<span data-ttu-id="d2db0-131">Eşitsizlik işleci `!=` döndürür `true` işlenenleri eşit değilse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="d2db0-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="d2db0-132">İşlenen için [yerleşik türler](../keywords/built-in-types-table.md), ifade `x != y` ifade aynı sonucu üretir `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="d2db0-132">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="d2db0-133">Tür eşitlik hakkında daha fazla bilgi için bkz: [eşitlik işleci](#equality-operator-) bölümü.</span><span class="sxs-lookup"><span data-stu-id="d2db0-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="d2db0-134">Aşağıdaki örnek, kullanımını gösterir. `!=` işleci:</span><span class="sxs-lookup"><span data-stu-id="d2db0-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="d2db0-135">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="d2db0-135">Operator overloadability</span></span>

<span data-ttu-id="d2db0-136">Kullanıcı tanımlı bir tür için [aşırı](operator-overloading.md) `==` ve `!=` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="d2db0-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="d2db0-137">Bir tür iki işleçlerden aşırı de başka bir aşırı gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2db0-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d2db0-138">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d2db0-138">C# language specification</span></span>

<span data-ttu-id="d2db0-139">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d2db0-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2db0-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2db0-140">See also</span></span>

- [<span data-ttu-id="d2db0-141">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="d2db0-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d2db0-142">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="d2db0-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d2db0-143">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="d2db0-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="d2db0-144">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="d2db0-144">Comparison operators</span></span>](comparison-operators.md)
