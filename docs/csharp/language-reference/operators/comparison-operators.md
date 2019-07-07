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
ms.openlocfilehash: d354a1e899e6ea72ac1e65634e5cc1267d41fb07
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609893"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="5f632-103">Karşılaştırma işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5f632-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="5f632-104">[ `<` (Küçüktür)](#less-than-operator-), [ `>` (büyüktür)](#greater-than-operator-), [ `<=` (küçüktür veya eşittir)](#less-than-or-equal-operator-), ve [ `>=` () büyüktür veya eşittir)](#greater-than-or-equal-operator-) karşılaştırması, işlenenleri Karşılaştırma işleçleri olarak ilişkisel'da bilinir.</span><span class="sxs-lookup"><span data-stu-id="5f632-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="5f632-105">Tüm bu işleçleri destekler [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../keywords/floating-point-types-table.md) sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="5f632-105">Those operators support all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="5f632-106">İçin `==`, `<`, `>`, `<=`, ve `>=` herhangi işlenenden değilse, birkaç işleçleri (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlem sonucu `false`.</span><span class="sxs-lookup"><span data-stu-id="5f632-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="5f632-107">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) dahil olmak üzere, değer `NaN`.</span><span class="sxs-lookup"><span data-stu-id="5f632-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="5f632-108">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="5f632-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="5f632-109">Numaralandırma türleri, Karşılaştırma işleçleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="5f632-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="5f632-110">Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="5f632-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="5f632-111">[ `==` Ve `!=` işleçleri](equality-operators.md) işlenenlerini eşit olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5f632-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="5f632-112">Küçüktür işleci \<</span><span class="sxs-lookup"><span data-stu-id="5f632-112">Less than operator \<</span></span>

<span data-ttu-id="5f632-113">`<` İşleci döndürür `true` sol işleneni, sağ işlenen altındaysa `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="5f632-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="5f632-114">Büyüktür işleci ></span><span class="sxs-lookup"><span data-stu-id="5f632-114">Greater than operator ></span></span>

<span data-ttu-id="5f632-115">`>` İşleci döndürür `true` sol işleneni, sağ işlenen büyükse `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="5f632-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="5f632-116">Küçüktür veya eşittir işleci \<=</span><span class="sxs-lookup"><span data-stu-id="5f632-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="5f632-117">`<=` İşleci döndürür `true` sol işleneni, sağ işlenen küçük veya ona eşit olup olmadığını `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="5f632-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="5f632-118">Büyüktür veya eşittir işleci > =</span><span class="sxs-lookup"><span data-stu-id="5f632-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="5f632-119">`>=` İşleci döndürür `true` sol işlenenin değerinden büyük veya eşittir, sağ işlenen ise `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="5f632-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="5f632-120">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="5f632-120">Operator overloadability</span></span>

<span data-ttu-id="5f632-121">Kullanıcı tanımlı bir tür için [aşırı](operator-overloading.md) `<`, `>`, `<=`, ve `>=` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="5f632-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="5f632-122">Bir tür birini aşırı `<` veya `>` operatörleri onu gerekir aşırı yükleme hem de `<` ve `>`.</span><span class="sxs-lookup"><span data-stu-id="5f632-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="5f632-123">Bir tür birini aşırı `<=` veya `>=` operatörleri onu gerekir aşırı yükleme hem de `<=` ve `>=`.</span><span class="sxs-lookup"><span data-stu-id="5f632-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5f632-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5f632-124">C# language specification</span></span>

<span data-ttu-id="5f632-125">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5f632-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f632-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f632-126">See also</span></span>

- [<span data-ttu-id="5f632-127">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="5f632-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5f632-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="5f632-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="5f632-129">Eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="5f632-129">Equality operators</span></span>](equality-operators.md)
