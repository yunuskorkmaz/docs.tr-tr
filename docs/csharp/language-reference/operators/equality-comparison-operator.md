---
title: == İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655965"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ef481-102">== İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ef481-102">== Operator (C# Reference)</span></span>

<span data-ttu-id="ef481-103">Eşitlik işleci `==` döndürür `true` işlenenleri eşitse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="ef481-103">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

## <a name="value-types-equality"></a><span data-ttu-id="ef481-104">Değer türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="ef481-104">Value types equality</span></span>

<span data-ttu-id="ef481-105">İşlenen [yerleşik türlerin](../keywords/value-types-table.md) değerlerine eşitse eşit:</span><span class="sxs-lookup"><span data-stu-id="ef481-105">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="ef481-106">İlişkisel işleçler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>) işleminin sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="ef481-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="ef481-107">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) değeri.</span><span class="sxs-lookup"><span data-stu-id="ef481-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="ef481-108">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="ef481-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="ef481-109">İki işleneni de aynı [enum](../keywords/enum.md) türü temel alınan integral türünün karşılık gelen değerler eşitse eşit.</span><span class="sxs-lookup"><span data-stu-id="ef481-109">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="ef481-110">Varsayılan olarak, `==` işleci bir kullanıcı tanımlı tanımlanmamış [yapı](../keywords/struct.md) türü.</span><span class="sxs-lookup"><span data-stu-id="ef481-110">By default, the `==` operator is not defined for a user-defined [struct](../keywords/struct.md) type.</span></span> <span data-ttu-id="ef481-111">Kullanıcı tanımlı bir tür için [aşırı](#operator-overloadability) `==` işleci.</span><span class="sxs-lookup"><span data-stu-id="ef481-111">A user-defined type can [overload](#operator-overloadability) the `==` operator.</span></span>

<span data-ttu-id="ef481-112">İle başlayarak C# 7.3, `==` ve [ `!=` ](not-equal-operator.md) işleçleri tarafından desteklenen C# [diziler](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="ef481-112">Beginning with C# 7.3, the `==` and [`!=`](not-equal-operator.md) operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="ef481-113">Daha fazla bilgi için [eşitlik ve diziler](../../tuples.md#equality-and-tuples) bölümünü [ C# tanımlama grubu türleri](../../tuples.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="ef481-113">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

## <a name="string-equality"></a><span data-ttu-id="ef481-114">Dize eşitliği</span><span class="sxs-lookup"><span data-stu-id="ef481-114">String equality</span></span>

<span data-ttu-id="ef481-115">İki [dize](../keywords/string.md) işlenenler, bunların her ikisi de eşit `null` veya her iki dize örnekleri aynı uzunluktadır ve aynı karakterlerin her karakter konumunda vardır:</span><span class="sxs-lookup"><span data-stu-id="ef481-115">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="ef481-116">Büyük/küçük harfe sıralı karşılaştırma olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef481-116">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="ef481-117">Dizeleri karşılaştırmak hakkında daha fazla bilgi için bkz. [dizeleri karşılaştırmak nasıl C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="ef481-117">For more information about how to compare strings, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

## <a name="reference-types-equality"></a><span data-ttu-id="ef481-118">Başvuru türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="ef481-118">Reference types equality</span></span>

<span data-ttu-id="ef481-119">İki dışında `string` başvuru türü işlenen, bunlar aynı nesneye başvurduğunuzda eşit:</span><span class="sxs-lookup"><span data-stu-id="ef481-119">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="ef481-120">Bu örnek, gösterir `==` işleci, kullanıcı tarafından tanımlanan başvuru türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ef481-120">The example shows that the `==` operator is supported by user-defined reference types.</span></span> <span data-ttu-id="ef481-121">Ancak, bir kullanıcı tarafından tanımlanan başvuru türü aşırı yüklenebilir `==` işleci.</span><span class="sxs-lookup"><span data-stu-id="ef481-121">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="ef481-122">Bir başvuru türü aşırı `==` işleci, kullanım <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> iki başvuru türü aynı nesneye başvuruyorsa, denetlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ef481-122">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ef481-123">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="ef481-123">Operator overloadability</span></span>

<span data-ttu-id="ef481-124">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `==` işleci.</span><span class="sxs-lookup"><span data-stu-id="ef481-124">User-defined types can [overload](../keywords/operator.md) the `==` operator.</span></span> <span data-ttu-id="ef481-125">Bir tür eşitlik işlecini aşırı `==`, ayrıca aşırı gerekir [eşitsizlik işleci](not-equal-operator.md) `!=`.</span><span class="sxs-lookup"><span data-stu-id="ef481-125">If a type overloads the equality operator `==`, it must also overload the [inequality operator](not-equal-operator.md) `!=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ef481-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ef481-126">C# language specification</span></span>

<span data-ttu-id="ef481-127">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef481-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef481-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef481-128">See also</span></span>

- [<span data-ttu-id="ef481-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ef481-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ef481-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ef481-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ef481-131">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ef481-131">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ef481-132">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="ef481-132">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
