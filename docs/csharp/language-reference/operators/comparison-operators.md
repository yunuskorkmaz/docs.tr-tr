---
title: Karşılaştırma işleçleri- C# başvuru
description: Sayısal değerlerin C# sırasını denetlemek için kullanabileceğiniz karşılaştırma işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 86f557d0575b440455fd6363f0d0d6783a9e7acc
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345325"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="11000-103">Karşılaştırma işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="11000-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="11000-104">İlişkisel olarak da bilinen [`<` (küçüktür)](#less-than-operator-), [`>` (büyüktür)](#greater-than-operator-), [`<=` (küçüktür veya eşittir](#less-than-or-equal-operator-)) ve [`>=` (büyüktür veya eşittir)](#greater-than-or-equal-operator-) karşılaştırması.</span><span class="sxs-lookup"><span data-stu-id="11000-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="11000-105">Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="11000-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="11000-106">`==`, `<`, `>`, `<=`ve `>=` işleçleri için, işlenenlerin herhangi biri bir sayı değilse (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>), işlemin sonucu `false`olur.</span><span class="sxs-lookup"><span data-stu-id="11000-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="11000-107">Diğer bir deyişle, `NaN` değeri, `NaN`dahil herhangi bir `double` (veya `float`) değerinden daha fazla, daha küçüktür veya eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="11000-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="11000-108">Daha fazla bilgi ve örnek için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesi.</span><span class="sxs-lookup"><span data-stu-id="11000-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="11000-109">Numaralandırma türleri de karşılaştırma işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="11000-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="11000-110">Aynı [sabit listesi](../builtin-types/enum.md) türünün işlenenleri için, temeldeki integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="11000-110">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="11000-111">[`==` ve `!=` işleçleri](equality-operators.md) işlenenlerinin eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="11000-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="11000-112">Küçüktür işleci \<</span><span class="sxs-lookup"><span data-stu-id="11000-112">Less than operator \<</span></span>

<span data-ttu-id="11000-113">`<` işleci, sol işlenenin sağ işleneninden daha küçükse `true` döndürür `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="11000-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="11000-114">Büyüktür işleci ></span><span class="sxs-lookup"><span data-stu-id="11000-114">Greater than operator ></span></span>

<span data-ttu-id="11000-115">`>` işleci, sol işleneni sağ işleneninden büyükse `true` döndürür `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="11000-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="11000-116">Küçüktür veya eşittir işleci \<=</span><span class="sxs-lookup"><span data-stu-id="11000-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="11000-117">`<=` işleci, sol işlenenin sağ işleneninden küçük veya ona eşit olması durumunda `true` döndürür `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="11000-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="11000-118">Büyüktür veya eşittir işleci > =</span><span class="sxs-lookup"><span data-stu-id="11000-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="11000-119">`>=` işleci, sol işlenenin sağ işleneninden büyük veya ona eşit olması durumunda `true` döndürür `false` Aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="11000-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="11000-120">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="11000-120">Operator overloadability</span></span>

<span data-ttu-id="11000-121">Kullanıcı tanımlı bir tür `<`, `>`, `<=`ve `>=` işleçlerini [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="11000-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="11000-122">Bir tür `<` veya `>` işleçlerinden birini aşırı yüklerinde, hem `<` hem de `>`aşırı yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="11000-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="11000-123">Bir tür `<=` veya `>=` işleçlerinden birini aşırı yüklerinde, hem `<=` hem de `>=`aşırı yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="11000-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="11000-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="11000-124">C# language specification</span></span>

<span data-ttu-id="11000-125">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="11000-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11000-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11000-126">See also</span></span>

- [<span data-ttu-id="11000-127">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="11000-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="11000-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="11000-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="11000-129">Eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="11000-129">Equality operators</span></span>](equality-operators.md)
