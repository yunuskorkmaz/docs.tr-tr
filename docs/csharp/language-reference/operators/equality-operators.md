---
title: Eşitlik operatörleri - C# referansı
description: C# eşitlik karşılaştırma işleçleri ve C# türü eşitliği hakkında bilgi edinin.
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
ms.openlocfilehash: 079522b18afdf86a942d502672174516d45d37fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399569"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="70c6e-103">Eşitlik operatörleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="70c6e-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="70c6e-104">[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri, operandlarının eşit olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="70c6e-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="70c6e-105">Eşitlik işleci ==</span><span class="sxs-lookup"><span data-stu-id="70c6e-105">Equality operator ==</span></span>

<span data-ttu-id="70c6e-106">Eşitlik `==` işleci, `true` operands eşitse, `false` aksi takdirde döner.</span><span class="sxs-lookup"><span data-stu-id="70c6e-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="70c6e-107">Değer türleri eşitliği</span><span class="sxs-lookup"><span data-stu-id="70c6e-107">Value types equality</span></span>

<span data-ttu-id="70c6e-108">[Yerleşik değer türlerinin](../builtin-types/value-types.md#built-in-value-types) operands değerleri eşit ise eşittir:</span><span class="sxs-lookup"><span data-stu-id="70c6e-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="70c6e-109">Için `==` [ `<`, `>`, `<=`, `>=` , ve](comparison-operators.md) operatörler, herhangi bir operands bir sayı değilse (veya<xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType>), operasyon sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="70c6e-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="70c6e-110">`NaN` Bu, değerin ne daha büyük, ne daha az, ne de dahil olmak üzere başka `double` bir (veya) `float`değere eşit olduğu anlamına `NaN`gelir.</span><span class="sxs-lookup"><span data-stu-id="70c6e-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="70c6e-111">Daha fazla bilgi ve <xref:System.Double.NaN?displayProperty=nameWithType> örnekler <xref:System.Single.NaN?displayProperty=nameWithType> için, başvuru makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="70c6e-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="70c6e-112">Altta yatan integral türünün karşılık gelen değerleri eşitse, aynı [enum](../builtin-types/enum.md) türünden iki operand eşittir.</span><span class="sxs-lookup"><span data-stu-id="70c6e-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="70c6e-113">Kullanıcı tanımlı [yapı](../builtin-types/struct.md) türleri varsayılan olarak `==` işleci desteklemez.</span><span class="sxs-lookup"><span data-stu-id="70c6e-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="70c6e-114">İşleciyi `==` desteklemek için, kullanıcı tarafından tanımlanan bir yapının [aşırı yüklenmesi](operator-overloading.md) gerekir.</span><span class="sxs-lookup"><span data-stu-id="70c6e-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="70c6e-115">C# 7.3 ile `==` başlayarak, ve `!=` işleçler C# [tuples](../../tuples.md)tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="70c6e-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="70c6e-116">Daha fazla bilgi için [C# tuple türleri](../../tuples.md) makalesinin [Eşitlik ve tuples](../../tuples.md#equality-and-tuples) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="70c6e-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="70c6e-117">Referans türleri eşitliği</span><span class="sxs-lookup"><span data-stu-id="70c6e-117">Reference types equality</span></span>

<span data-ttu-id="70c6e-118">Varsayılan olarak, aynı nesneye başvururlarsa, iki başvuru tipi operand eşittir:</span><span class="sxs-lookup"><span data-stu-id="70c6e-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="70c6e-119">Örnekte de görüldüğü gibi, kullanıcı `==` tanımlı başvuru türleri varsayılan olarak işleci destekler.</span><span class="sxs-lookup"><span data-stu-id="70c6e-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="70c6e-120">Ancak, bir başvuru türü `==` işleci aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="70c6e-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="70c6e-121">Bir başvuru türü `==` işleç aşırı <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yüklerse, bu türiki başvurunun aynı nesneye başvurup başvurmadığını denetlemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="70c6e-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="70c6e-122">Dize eşitliği</span><span class="sxs-lookup"><span data-stu-id="70c6e-122">String equality</span></span>

<span data-ttu-id="70c6e-123">İki [dize](../builtin-types/reference-types.md#the-string-type) operands her ikisi `null` de veya her iki dize örnekleri aynı uzunlukta ve her karakter konumunda aynı karakterlere sahip eşittir:</span><span class="sxs-lookup"><span data-stu-id="70c6e-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="70c6e-124">Bu büyük/küçük harf duyarlı bir ordinal karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="70c6e-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="70c6e-125">Dize karşılaştırması hakkında daha fazla bilgi için [C# dizelerini nasıl karşılaştırın.](../../how-to/compare-strings.md)</span><span class="sxs-lookup"><span data-stu-id="70c6e-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="70c6e-126">Temsilci eşitliği</span><span class="sxs-lookup"><span data-stu-id="70c6e-126">Delegate equality</span></span>

<span data-ttu-id="70c6e-127">Her [delegate](../../programming-guide/delegates/index.md) ikisi de aynı uzunlukta olduğunda `null` ve her pozisyonda eşit girişlere sahip olduklarında, aynı çalışma zamanı türünden iki temsilci operandeşittir:</span><span class="sxs-lookup"><span data-stu-id="70c6e-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="70c6e-128">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Temsilci eşitliği işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="70c6e-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="70c6e-129">Aşağıdaki örnekte görüldüğü gibi, anlamsal olarak özdeş [lambda ifadelerinin](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirilmesinden elde edilen temsilciler eşit değildir:</span><span class="sxs-lookup"><span data-stu-id="70c6e-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="70c6e-130">Eşitsizlik operatörü !=</span><span class="sxs-lookup"><span data-stu-id="70c6e-130">Inequality operator !=</span></span>

<span data-ttu-id="70c6e-131">Eşitsizlik işleci, `!=` `true` operands eşit değilse, `false` aksi takdirde döner.</span><span class="sxs-lookup"><span data-stu-id="70c6e-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="70c6e-132">[Yerleşik türlerin](../builtin-types/built-in-types.md)operands için, ifade `x != y` ifade `!(x == y)`olarak aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="70c6e-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="70c6e-133">Tür eşitliği hakkında daha fazla bilgi için [Eşitlik işleci](#equality-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="70c6e-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="70c6e-134">Aşağıdaki örnek, işleç `!=` kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="70c6e-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="70c6e-135">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="70c6e-135">Operator overloadability</span></span>

<span data-ttu-id="70c6e-136">Kullanıcı tanımlı bir tür `==` ve `!=` işleçler [aşırı yükleyebilir.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="70c6e-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="70c6e-137">Bir tür iki işleçten birini aşırı yüklenirse, başka bir işleçten de aşırı yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="70c6e-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="70c6e-138">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="70c6e-138">C# language specification</span></span>

<span data-ttu-id="70c6e-139">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İlişkisel ve tür test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="70c6e-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70c6e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70c6e-140">See also</span></span>

- [<span data-ttu-id="70c6e-141">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="70c6e-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="70c6e-142">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="70c6e-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="70c6e-143">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="70c6e-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="70c6e-144">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="70c6e-144">Comparison operators</span></span>](comparison-operators.md)
