---
title: '&amp;&amp; Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 82442f50275f21e0a0748951dc50628a8d7e11bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243607"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="fc1a8-102">&amp;&amp; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fc1a8-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="fc1a8-103">Koşullu mantıksal AND işlecinin `&&`, "kısa devre" mantıksal AND işleci, hesaplar, mantıksal AND olarak da bilinir, [bool](../keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="fc1a8-104">Sonucu `x && y` olduğu `true` hem `x` ve `y` vermesi `true`.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="fc1a8-105">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="fc1a8-106">Birinci işlenenin değerlendirilirse `false`, ikinci işlenenin değerlendirilmez ve işlemin sonucu olan `false`.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="fc1a8-107">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="fc1a8-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="fc1a8-108">[Mantıksal AND işlecinin](and-operator.md) `&` Ayrıca, mantıksal ve hesaplar, `bool` işlenenler, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="fc1a8-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="fc1a8-109">Operator overloadability</span></span>

<span data-ttu-id="fc1a8-110">Kullanıcı tanımlı bir tür koşullu mantıksal AND işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="fc1a8-111">Ancak, kullanıcı tanımlı bir tür aşırı [mantıksal AND](and-operator.md) ve [true ve false işleçleri](../keywords/true-false-operators.md) belirli bir şekilde `&&` işlemi, bu türündeki işlenenler için değerlendirmesi yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-111">However, if a user-defined type overloads the [logical AND](and-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="fc1a8-112">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc1a8-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fc1a8-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fc1a8-113">C# language specification</span></span>

<span data-ttu-id="fc1a8-114">Daha fazla bilgi için [koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc1a8-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc1a8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc1a8-115">See also</span></span>

- [<span data-ttu-id="fc1a8-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fc1a8-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc1a8-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc1a8-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc1a8-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="fc1a8-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="fc1a8-119">|| işleci</span><span class="sxs-lookup"><span data-stu-id="fc1a8-119">|| operator</span></span>](conditional-or-operator.md)
- [<span data-ttu-id="fc1a8-120">\! işleci</span><span class="sxs-lookup"><span data-stu-id="fc1a8-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="fc1a8-121">& işleci</span><span class="sxs-lookup"><span data-stu-id="fc1a8-121">& operator</span></span>](and-operator.md)
