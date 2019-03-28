---
title: Eşitlik işleçleri - C# başvurusu
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 98b96f5b4c6d6ea70687a97c849e89573c67c37e
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545881"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="7fef7-102">Eşitlik işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7fef7-102">Equality operators (C# Reference)</span></span>

<span data-ttu-id="7fef7-103">[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenleri eşit olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7fef7-103">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="7fef7-104">Eşitlik işleci ==</span><span class="sxs-lookup"><span data-stu-id="7fef7-104">Equality operator ==</span></span>

<span data-ttu-id="7fef7-105">Eşitlik işleci `==` döndürür `true` işlenenleri eşitse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="7fef7-105">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="7fef7-106">Değer türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="7fef7-106">Value types equality</span></span>

<span data-ttu-id="7fef7-107">İşlenen [yerleşik türlerin](../keywords/value-types-table.md) değerlerine eşitse eşit:</span><span class="sxs-lookup"><span data-stu-id="7fef7-107">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="7fef7-108">Eşitlik ve operatörler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlem sonucu `false`.</span><span class="sxs-lookup"><span data-stu-id="7fef7-108">For equality and relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="7fef7-109">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`.</span><span class="sxs-lookup"><span data-stu-id="7fef7-109">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="7fef7-110">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="7fef7-110">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="7fef7-111">İki işleneni de aynı [enum](../keywords/enum.md) türü temel alınan integral türünün karşılık gelen değerler eşitse eşit.</span><span class="sxs-lookup"><span data-stu-id="7fef7-111">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="7fef7-112">Kullanıcı tanımlı [yapı](../keywords/struct.md) türleri desteklemez `==` varsayılan işleci.</span><span class="sxs-lookup"><span data-stu-id="7fef7-112">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="7fef7-113">Desteklemek için `==` işleci, bir kullanıcı tarafından tanımlanan yapı gerekir [aşırı](#operator-overloadability) bu.</span><span class="sxs-lookup"><span data-stu-id="7fef7-113">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="7fef7-114">İle başlayarak C# 7.3, `==` ve `!=` işleçleri tarafından desteklenen C# [diziler](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="7fef7-114">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="7fef7-115">Daha fazla bilgi için [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümünü [ C# tanımlama grubu türleri](../../tuples.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="7fef7-115">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="7fef7-116">Dize eşitliği</span><span class="sxs-lookup"><span data-stu-id="7fef7-116">String equality</span></span>

<span data-ttu-id="7fef7-117">İki [dize](../keywords/string.md) işlenenler, bunların her ikisi de eşit `null` veya her iki dize örnekleri aynı uzunluktadır ve aynı karakterlerin her karakter konumunda vardır:</span><span class="sxs-lookup"><span data-stu-id="7fef7-117">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="7fef7-118">Büyük/küçük harfe sıralı karşılaştırma olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7fef7-118">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="7fef7-119">Dize karşılaştırması hakkında daha fazla bilgi için bkz: [dizeleri karşılaştırmak nasıl C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="7fef7-119">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="7fef7-120">Başvuru türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="7fef7-120">Reference types equality</span></span>

<span data-ttu-id="7fef7-121">İki dışında `string` başvuru türü işlenen, bunlar aynı nesneye başvurduğunuzda eşit:</span><span class="sxs-lookup"><span data-stu-id="7fef7-121">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="7fef7-122">Örnekte gösterildiği gibi destek kullanıcı tarafından tanımlanan başvuru türleri `==` varsayılan işleci.</span><span class="sxs-lookup"><span data-stu-id="7fef7-122">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="7fef7-123">Ancak, bir kullanıcı tarafından tanımlanan başvuru türü aşırı yüklenebilir `==` işleci.</span><span class="sxs-lookup"><span data-stu-id="7fef7-123">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="7fef7-124">Bir başvuru türü aşırı `==` işleci, kullanım <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> iki başvuru türü aynı nesneye başvuruyorsa, denetlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7fef7-124">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="7fef7-125">Eşitsizlik işleci! =</span><span class="sxs-lookup"><span data-stu-id="7fef7-125">Inequality operator !=</span></span>

<span data-ttu-id="7fef7-126">Eşitsizlik işleci `!=` döndürür `true` işlenenleri eşit değilse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="7fef7-126">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="7fef7-127">İşlenen için [yerleşik türler](../keywords/built-in-types-table.md), ifade `x != y` ifade aynı sonucu üretir `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="7fef7-127">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="7fef7-128">Tür eşitlik hakkında daha fazla bilgi için bkz: [eşitlik işleci](#equality-operator-) bölümü.</span><span class="sxs-lookup"><span data-stu-id="7fef7-128">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="7fef7-129">Aşağıdaki örnek, kullanımını gösterir. `!=` işleci:</span><span class="sxs-lookup"><span data-stu-id="7fef7-129">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="7fef7-130">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="7fef7-130">Operator overloadability</span></span>

<span data-ttu-id="7fef7-131">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `==` ve `!=` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="7fef7-131">User-defined types can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="7fef7-132">Bir tür iki işleçlerden aşırı de başka bir aşırı gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fef7-132">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7fef7-133">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7fef7-133">C# language specification</span></span>

<span data-ttu-id="7fef7-134">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7fef7-134">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7fef7-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fef7-135">See also</span></span>

- [<span data-ttu-id="7fef7-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7fef7-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7fef7-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7fef7-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7fef7-138">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="7fef7-138">C# Operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7fef7-139">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="7fef7-139">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
