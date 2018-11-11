---
title: '&amp;&amp; İşleci (C# Başvurusu)'
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: d0e6d9a5aedc7dc87393e3dea070bf442b3268dc
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529241"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="a9dee-102">&amp;&amp; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a9dee-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="a9dee-103">Koşullu mantıksal AND işlecinin `&&`, "kısa devre" mantıksal AND işleci, hesaplar, mantıksal AND olarak da bilinir, [bool](../keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="a9dee-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="a9dee-104">Sonucu `x && y` olduğu `true` hem `x` ve `y` vermesi `true`.</span><span class="sxs-lookup"><span data-stu-id="a9dee-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="a9dee-105">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="a9dee-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="a9dee-106">Birinci işlenenin değerlendirilirse `false`, ikinci işlenenin değerlendirilmez ve işlemin sonucu olan `false`.</span><span class="sxs-lookup"><span data-stu-id="a9dee-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="a9dee-107">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="a9dee-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="a9dee-108">[Mantıksal AND işlecinin](and-operator.md) `&` Ayrıca, mantıksal ve hesaplar, `bool` işlenenler, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a9dee-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a9dee-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="a9dee-109">Operator overloadability</span></span>

<span data-ttu-id="a9dee-110">Kullanıcı tanımlı bir tür koşullu mantıksal AND işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="a9dee-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="a9dee-111">Ancak, kullanıcı tanımlı bir tür aşırı [mantıksal AND](and-operator.md), [true](../keywords/true-operator.md), ve [false](../keywords/false-operator.md) işleçleri belirli bir şekilde `&&` işlemi değerlendirmesi yapılamıyor için işlenen türü.</span><span class="sxs-lookup"><span data-stu-id="a9dee-111">However, if a user-defined type overloads the [logical AND](and-operator.md), [true](../keywords/true-operator.md), and [false](../keywords/false-operator.md) operators in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="a9dee-112">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9dee-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a9dee-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a9dee-113">C# language specification</span></span>

<span data-ttu-id="a9dee-114">Daha fazla bilgi için [koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9dee-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9dee-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9dee-115">See also</span></span>

- [<span data-ttu-id="a9dee-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a9dee-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a9dee-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a9dee-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a9dee-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="a9dee-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="a9dee-119">|| işleci</span><span class="sxs-lookup"><span data-stu-id="a9dee-119">|| operator</span></span>](conditional-or-operator.md)
- [! işleci]<span data-ttu-id="a9dee-120">(logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="a9dee-120">(logical-negation-operator.md)</span></span>
- [<span data-ttu-id="a9dee-121">& işleci</span><span class="sxs-lookup"><span data-stu-id="a9dee-121">& operator</span></span>](and-operator.md)
