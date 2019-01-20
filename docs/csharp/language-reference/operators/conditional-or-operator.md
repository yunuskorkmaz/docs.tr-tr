---
title: '|| Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 079c021eb68ece097c7f644416f1e9469a82dcea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415435"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b792c-102">|| İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b792c-102">|| Operator (C# Reference)</span></span>

<span data-ttu-id="b792c-103">Koşullu mantıksal OR işlecinin `||`, "kısa devre" mantıksal OR işleci, hesaplar, mantıksal OR olarak da bilinir, [bool](../keywords/bool.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="b792c-103">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="b792c-104">Sonucu `x || y` olduğu `true` ya da `x` veya `y` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="b792c-104">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="b792c-105">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="b792c-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="b792c-106">Birinci işlenenin değerlendirilirse `true`, ikinci işlenenin değerlendirilmez ve işlemin sonucu olan `true`.</span><span class="sxs-lookup"><span data-stu-id="b792c-106">If the first operand evaluates to `true`, the second operand is not evaluated and the result of operation is `true`.</span></span> <span data-ttu-id="b792c-107">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="b792c-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

<span data-ttu-id="b792c-108">[Mantıksal OR işlecinin](or-operator.md) `|` Ayrıca, mantıksal OR hesaplar, `bool` işlenenler, ancak her iki işlenen de her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b792c-108">The [logical OR operator](or-operator.md) `|` also computes the logical OR of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="b792c-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="b792c-109">Operator overloadability</span></span>

<span data-ttu-id="b792c-110">Kullanıcı tanımlı bir tür koşullu mantıksal OR işlecinin aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="b792c-110">A user-defined type cannot overload the conditional logical OR operator.</span></span> <span data-ttu-id="b792c-111">Ancak, kullanıcı tanımlı bir tür aşırı [mantıksal OR](or-operator.md) ve [true ve false işleçleri](../keywords/true-false-operators.md) belirli bir şekilde `||` işlemi, bu türündeki işlenenler için değerlendirmesi yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b792c-111">However, if a user-defined type overloads the [logical OR](or-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `||` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="b792c-112">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b792c-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b792c-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b792c-113">C# language specification</span></span>

<span data-ttu-id="b792c-114">Daha fazla bilgi için [koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b792c-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b792c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b792c-115">See also</span></span>

- [<span data-ttu-id="b792c-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b792c-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b792c-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b792c-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b792c-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b792c-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="b792c-119">& & işleci</span><span class="sxs-lookup"><span data-stu-id="b792c-119">&& operator</span></span>](conditional-and-operator.md)
- [<span data-ttu-id="b792c-120">\! İşleci</span><span class="sxs-lookup"><span data-stu-id="b792c-120">\! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="b792c-121">| işleci</span><span class="sxs-lookup"><span data-stu-id="b792c-121">| operator</span></span>](or-operator.md)
