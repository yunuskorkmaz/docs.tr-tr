---
title: Karşılaştırma işleçleri-C# başvurusu
description: Sayısal değerlerin sırasını denetlemek için kullanabileceğiniz C# karşılaştırma işleçleri hakkında bilgi edinin.
ms.date: 05/11/2020
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
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207220"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="52553-103">Karşılaştırma işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="52553-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="52553-104">İlişkisel olarak da bilinen [ `<` (küçüktür)](#less-than-operator-), [ `>` (büyüktür)](#greater-than-operator-), [ `<=` (küçüktür veya eşittir](#less-than-or-equal-operator-)) ve [ `>=` (büyüktür veya eşittir)](#greater-than-or-equal-operator-) karşılaştırması, işleçlerini karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="52553-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="52553-105">Bu işleçler tüm [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="52553-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="52553-106">,, `==` , `<` `>` `<=` Ve `>=` işleçleri için İşlenenlerden herhangi biri bir sayı ( <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> ) değilse, işlemin sonucu olur `false` .</span><span class="sxs-lookup"><span data-stu-id="52553-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="52553-107">Bu, değeri, `NaN` dahil olmak üzere herhangi bir değerden büyük, küçüktür veya eşit olmayan bir değere eşit değil anlamına gelir `double` `float` `NaN` .</span><span class="sxs-lookup"><span data-stu-id="52553-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="52553-108">Daha fazla bilgi ve örnek için bkz <xref:System.Double.NaN?displayProperty=nameWithType> . veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesi.</span><span class="sxs-lookup"><span data-stu-id="52553-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="52553-109">[Char](../builtin-types/char.md) türü de karşılaştırma işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="52553-109">The [char](../builtin-types/char.md) type also supports comparison operators.</span></span> <span data-ttu-id="52553-110">İşlenenler söz konusu olduğunda `char` , karşılık gelen karakter kodları karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="52553-110">In the case of `char` operands, the corresponding character codes are compared.</span></span>

<span data-ttu-id="52553-111">Numaralandırma türleri de karşılaştırma işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="52553-111">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="52553-112">Aynı [sabit listesi](../builtin-types/enum.md) türünün işlenenleri için, temeldeki integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="52553-112">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="52553-113">[ `==` Ve `!=` işleçleri](equality-operators.md) , işlenenleri eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="52553-113">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="52553-114">Küçüktür işleci\<</span><span class="sxs-lookup"><span data-stu-id="52553-114">Less than operator \<</span></span>

<span data-ttu-id="52553-115">`<`İşleci, `true` sol işlenenin sağ tarafından daha az ise, `false` tersi durumda, döndürür:</span><span class="sxs-lookup"><span data-stu-id="52553-115">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="52553-116">Büyüktür işleci ></span><span class="sxs-lookup"><span data-stu-id="52553-116">Greater than operator ></span></span>

<span data-ttu-id="52553-117">`>`İşleci, `true` sol işleneni sağ işleneninden büyükse, `false` Aksi takdirde döndürür:</span><span class="sxs-lookup"><span data-stu-id="52553-117">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="52553-118">Küçüktür veya eşittir işleci\<=</span><span class="sxs-lookup"><span data-stu-id="52553-118">Less than or equal operator \<=</span></span>

<span data-ttu-id="52553-119">`<=`İşleci, `true` sol işlenenin sağ işleneninden küçük veya ona eşit ise, `false` Aksi takdirde döndürür:</span><span class="sxs-lookup"><span data-stu-id="52553-119">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="52553-120">Büyüktür veya eşittir işleci >=</span><span class="sxs-lookup"><span data-stu-id="52553-120">Greater than or equal operator >=</span></span>

<span data-ttu-id="52553-121">`>=`İşleci, `true` sol işlenenin sağ işleneninden büyük veya ona eşitse, `false` Aksi takdirde, döndürür:</span><span class="sxs-lookup"><span data-stu-id="52553-121">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="52553-122">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="52553-122">Operator overloadability</span></span>

<span data-ttu-id="52553-123">Kullanıcı tanımlı bir tür,, [overload](operator-overloading.md) , `<` `>` `<=` ve işleçlerini aşırı yükleyebilir `>=` .</span><span class="sxs-lookup"><span data-stu-id="52553-123">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="52553-124">Bir tür veya işleçlerden birini aşırı yüklerinde `<` `>` , hem hem de aşırı yüklemesi gerekir `<` `>` .</span><span class="sxs-lookup"><span data-stu-id="52553-124">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="52553-125">Bir tür veya işleçlerden birini aşırı yüklerinde `<=` `>=` , hem hem de aşırı yüklemesi gerekir `<=` `>=` .</span><span class="sxs-lookup"><span data-stu-id="52553-125">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="52553-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="52553-126">C# language specification</span></span>

<span data-ttu-id="52553-127">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="52553-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52553-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52553-128">See also</span></span>

- [<span data-ttu-id="52553-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="52553-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="52553-130">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="52553-130">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="52553-131">Eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="52553-131">Equality operators</span></span>](equality-operators.md)
