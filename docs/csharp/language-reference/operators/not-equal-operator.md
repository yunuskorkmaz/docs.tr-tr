---
title: '! = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610183"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="235c3-102">!= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="235c3-102">!= Operator (C# Reference)</span></span>

<span data-ttu-id="235c3-103">Eşitsizlik işleci `!=` döndürür `true` işlenenleri eşit değilse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="235c3-103">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="235c3-104">İşlenen için [yerleşik türler](../keywords/built-in-types-table.md), ifade `x != y` ifade aynı sonucu üretir `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="235c3-104">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="235c3-105">Daha fazla bilgi için [== işleci](equality-comparison-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="235c3-105">For more information, see the [== Operator](equality-comparison-operator.md) article.</span></span>

<span data-ttu-id="235c3-106">Aşağıdaki örnek, kullanımını gösterir. `!=` işleci:</span><span class="sxs-lookup"><span data-stu-id="235c3-106">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="235c3-107">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="235c3-107">Operator overloadability</span></span>

<span data-ttu-id="235c3-108">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `!=` işleci.</span><span class="sxs-lookup"><span data-stu-id="235c3-108">User-defined types can [overload](../keywords/operator.md) the `!=` operator.</span></span> <span data-ttu-id="235c3-109">Bir tür eşitsizlik işleci aşırı `!=`, ayrıca aşırı gerekir [eşitlik işleci](equality-comparison-operator.md) `==`.</span><span class="sxs-lookup"><span data-stu-id="235c3-109">If a type overloads the inequality operator `!=`, it must also overload the [equality operator](equality-comparison-operator.md) `==`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="235c3-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="235c3-110">C# language specification</span></span>

<span data-ttu-id="235c3-111">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="235c3-111">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="235c3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="235c3-112">See also</span></span>

- [<span data-ttu-id="235c3-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="235c3-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="235c3-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="235c3-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="235c3-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="235c3-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="235c3-116">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="235c3-116">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
