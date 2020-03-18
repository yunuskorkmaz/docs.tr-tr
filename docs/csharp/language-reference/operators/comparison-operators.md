---
title: Karşılaştırma işleçleri - C# referansı
description: Sayısal değerlerin sırasını denetlemek için kullanabileceğiniz C# karşılaştırma işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399247"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="f305f-103">Karşılaştırma işleçleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f305f-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="f305f-104">[ `<` (Daha az)](#less-than-operator-) [ `>` , (büyük)](#greater-than-operator-), [ `<=` (daha az veya eşit)](#less-than-or-equal-operator-)ve [ `>=` (büyük veya eşit)](#greater-than-or-equal-operator-) karşılaştırma, ayrıca ilişkisel olarak bilinen, işleçler kendi operands karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="f305f-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="f305f-105">Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f305f-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="f305f-106">Için `==`, `<` `>`, `<=`, `>=` , ve operatörler, herhangi bir operands bir sayı değilse (veya<xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType>), operasyon sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="f305f-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="f305f-107">`NaN` Bu, değerin ne daha büyük, ne daha az, ne de dahil olmak üzere başka `double` bir (veya) `float`değere eşit olduğu anlamına `NaN`gelir.</span><span class="sxs-lookup"><span data-stu-id="f305f-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="f305f-108">Daha fazla bilgi ve <xref:System.Double.NaN?displayProperty=nameWithType> örnekler <xref:System.Single.NaN?displayProperty=nameWithType> için, başvuru makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="f305f-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="f305f-109">Numaralandırma türleri karşılaştırma işleçlerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="f305f-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="f305f-110">Aynı [enum](../builtin-types/enum.md) türündeki operandlar için, altta yatan integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="f305f-110">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="f305f-111">Ve [ `==` `!=` operatörler](equality-operators.md) operandlarının eşit olup olmadığını kontrol ederler.</span><span class="sxs-lookup"><span data-stu-id="f305f-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="f305f-112">Operatörden daha az\<</span><span class="sxs-lookup"><span data-stu-id="f305f-112">Less than operator \<</span></span>

<span data-ttu-id="f305f-113">Sol `<` operand'ı sağ operand'dan daha azsa `false` operatör geri döner, `true` aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="f305f-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="f305f-114">Operatörden daha büyük ></span><span class="sxs-lookup"><span data-stu-id="f305f-114">Greater than operator ></span></span>

<span data-ttu-id="f305f-115">Sol `>` operand'ı sağ operand'dan büyükse, işleç geri döner, `true` `false` aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="f305f-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="f305f-116">Daha az veya eşit işleç\<=</span><span class="sxs-lookup"><span data-stu-id="f305f-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="f305f-117">Sol `<=` operand'ı sağ operand'dan daha az veya eşitse, işleç geri döner, `true` `false` aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="f305f-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="f305f-118">Büyük veya eşit işleç >=</span><span class="sxs-lookup"><span data-stu-id="f305f-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="f305f-119">Sol `>=` operand'ı sağ operand'dan büyük veya eşitse, `false` işleç geri döner, `true` aksi takdirde:</span><span class="sxs-lookup"><span data-stu-id="f305f-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="f305f-120">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="f305f-120">Operator overloadability</span></span>

<span data-ttu-id="f305f-121">Kullanıcı tanımlı bir tür `<`, `>` `<=`, `>=` , ve işleçleri [aşırı yükleyebilir.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="f305f-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="f305f-122">Bir tür operatörlerden birini `<` `>` aşırı yüklenirse, her ikisini de `<` aşırı yüklemesi gerekir. `>`</span><span class="sxs-lookup"><span data-stu-id="f305f-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="f305f-123">Bir tür operatörlerden birini `<=` `>=` aşırı yüklenirse, her ikisini de `<=` aşırı yüklemesi gerekir. `>=`</span><span class="sxs-lookup"><span data-stu-id="f305f-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f305f-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f305f-124">C# language specification</span></span>

<span data-ttu-id="f305f-125">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İlişkisel ve tür test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f305f-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f305f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f305f-126">See also</span></span>

- [<span data-ttu-id="f305f-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f305f-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f305f-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="f305f-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="f305f-129">Eşitlik operatörleri</span><span class="sxs-lookup"><span data-stu-id="f305f-129">Equality operators</span></span>](equality-operators.md)
