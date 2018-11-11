---
title: '|| İşleci (C# Başvurusu)'
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: a391078372e4ec0a3882bed4515733adedffb547
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "42925546"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3afcc-102">|| İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3afcc-102">|| Operator (C# Reference)</span></span>

<span data-ttu-id="3afcc-103">Koşullu mantıksal OR işlecinin `||`, "kısa devre" mantıksal OR işleci, hesaplar, mantıksal OR olarak da bilinir, [bool](../keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="3afcc-103">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="3afcc-104">Sonucu `x || y` olduğu `true` ya da `x` veya `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="3afcc-104">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="3afcc-105">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="3afcc-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="3afcc-106">Birinci işlenenin değerlendirilirse `true`, ikinci işlenenin değerlendirilmez ve işlemin sonucu olan `true`.</span><span class="sxs-lookup"><span data-stu-id="3afcc-106">If the first operand evaluates to `true`, the second operand is not evaluated and the result of operation is `true`.</span></span> <span data-ttu-id="3afcc-107">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="3afcc-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

<span data-ttu-id="3afcc-108">[Mantıksal OR işlecinin](or-operator.md) `|` Ayrıca, mantıksal OR hesaplar, `bool` işlenenler, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3afcc-108">The [logical OR operator](or-operator.md) `|` also computes the logical OR of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3afcc-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="3afcc-109">Operator overloadability</span></span>

<span data-ttu-id="3afcc-110">Kullanıcı tanımlı bir tür koşullu mantıksal OR işlecinin aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="3afcc-110">A user-defined type cannot overload the conditional logical OR operator.</span></span> <span data-ttu-id="3afcc-111">Ancak, kullanıcı tanımlı bir tür aşırı [mantıksal OR](or-operator.md), [true](../keywords/true-operator.md), ve [false](../keywords/false-operator.md) işleçleri belirli bir şekilde `||` işlemi değerlendirmesi yapılamıyor için işlenen türü.</span><span class="sxs-lookup"><span data-stu-id="3afcc-111">However, if a user-defined type overloads the [logical OR](or-operator.md), [true](../keywords/true-operator.md), and [false](../keywords/false-operator.md) operators in a certain way, the `||` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="3afcc-112">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3afcc-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3afcc-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3afcc-113">C# language specification</span></span>

<span data-ttu-id="3afcc-114">Daha fazla bilgi için [koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3afcc-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3afcc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3afcc-115">See also</span></span>

- [<span data-ttu-id="3afcc-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3afcc-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3afcc-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3afcc-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3afcc-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3afcc-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="3afcc-119">& & işleci</span><span class="sxs-lookup"><span data-stu-id="3afcc-119">&& operator</span></span>](conditional-and-operator.md)
- [! işleci]<span data-ttu-id="3afcc-120">(logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="3afcc-120">(logical-negation-operator.md)</span></span>
- [<span data-ttu-id="3afcc-121">| işleci</span><span class="sxs-lookup"><span data-stu-id="3afcc-121">| operator</span></span>](or-operator.md)
