---
title: Karşılaştırma işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# sayısal değerlerin sırasını denetlemek için kullanabileceğiniz bir Karşılaştırma işleçleri.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 3b123ea1ae57735cdcb763087f12c30b8008dc11
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758202"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="d9e21-103">Karşılaştırma işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d9e21-103">Comparison operators (C# Reference)</span></span>

<span data-ttu-id="d9e21-104">[ `<` (Küçüktür)](#less-than-operator-), [ `>` (büyüktür)](#greater-than-operator-), [ `<=` (küçüktür veya eşittir)](#less-than-or-equal-operator-), ve [ `>=` () büyüktür veya eşittir)](#greater-than-or-equal-operator-) karşılaştırması, işlenenleri Karşılaştırma işleçleri olarak ilişkisel'da bilinir.</span><span class="sxs-lookup"><span data-stu-id="d9e21-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="d9e21-105">Tüm bu işleçleri destekler [integral](../keywords/integral-types-table.md) ve [kayan nokta](../keywords/floating-point-types-table.md) sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="d9e21-105">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="d9e21-106">İçin `==`, `<`, `>`, `<=`, ve `>=` herhangi işlenenden değilse, birkaç işleçleri (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlem sonucu `false`.</span><span class="sxs-lookup"><span data-stu-id="d9e21-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="d9e21-107">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`.</span><span class="sxs-lookup"><span data-stu-id="d9e21-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="d9e21-108">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="d9e21-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="d9e21-109">Numaralandırma türleri, Karşılaştırma işleçleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="d9e21-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="d9e21-110">Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="d9e21-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="d9e21-111">[ `==` Ve `!=` işleçleri](equality-operators.md) işlenenlerini eşit olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d9e21-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="d9e21-112">Küçüktür işleci \<</span><span class="sxs-lookup"><span data-stu-id="d9e21-112">Less than operator \<</span></span>

<span data-ttu-id="d9e21-113">`<` İşleci döndürür `true` ilk işleneni küçükse değerinden ikinci işleneniyle `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="d9e21-113">The `<` operator returns `true` if its first operand is less than its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="d9e21-114">Büyüktür işleci ></span><span class="sxs-lookup"><span data-stu-id="d9e21-114">Greater than operator ></span></span>

<span data-ttu-id="d9e21-115">`>` İşleci döndürür `true` , ikinci işlenenin ilk işlenenin büyükse `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="d9e21-115">The `>` operator returns `true` if its first operand is greater than its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="d9e21-116">Küçüktür veya eşittir işleci \<=</span><span class="sxs-lookup"><span data-stu-id="d9e21-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="d9e21-117">`<=` İşleci döndürür `true` ilk işlenenin ikinci işleneni, küçük veya ona eşit olup olmadığını `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="d9e21-117">The `<=` operator returns `true` if its first operand is less than or equal to its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="d9e21-118">Büyüktür veya eşittir işleci > =</span><span class="sxs-lookup"><span data-stu-id="d9e21-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="d9e21-119">`>=` İşleci döndürür `true` ilk işlenenin değerinden büyük veya eşittir, ikinci işleneni ise `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="d9e21-119">The `>=` operator returns `true` if its first operand is greater than or equal to its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="d9e21-120">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="d9e21-120">Operator overloadability</span></span>

<span data-ttu-id="d9e21-121">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `<`, `>`, `<=`, ve `>=` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="d9e21-121">A user-defined type can [overload](../keywords/operator.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="d9e21-122">Bir tür birini aşırı `<` veya `>` operatörleri onu gerekir aşırı yükleme hem de `<` ve `>`.</span><span class="sxs-lookup"><span data-stu-id="d9e21-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="d9e21-123">Bir tür birini aşırı `<=` veya `>=` operatörleri onu gerekir aşırı yükleme hem de `<=` ve `>=`.</span><span class="sxs-lookup"><span data-stu-id="d9e21-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d9e21-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d9e21-124">C# language specification</span></span>

<span data-ttu-id="d9e21-125">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d9e21-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9e21-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9e21-126">See also</span></span>

- [<span data-ttu-id="d9e21-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d9e21-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d9e21-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d9e21-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d9e21-129">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d9e21-129">C# Operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="d9e21-130">Eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="d9e21-130">Equality operators</span></span>](equality-operators.md)
