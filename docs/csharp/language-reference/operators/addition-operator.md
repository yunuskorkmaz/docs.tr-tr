---
title: + Operator - C# başvurusu
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504476"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="593d4-102">+ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="593d4-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="593d4-103">`+` İşleci iki biçimde desteklenir: bir birli artı işleci veya bir ikili Toplama işleci.</span><span class="sxs-lookup"><span data-stu-id="593d4-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="593d4-104">Tekli artı işleci</span><span class="sxs-lookup"><span data-stu-id="593d4-104">Unary plus operator</span></span>

<span data-ttu-id="593d4-105">Birli `+` işleci, işlenenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="593d4-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="593d4-106">Tüm sayısal türler tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="593d4-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="593d4-107">Sayısal toplama</span><span class="sxs-lookup"><span data-stu-id="593d4-107">Numeric addition</span></span>

<span data-ttu-id="593d4-108">Sayısal türlerin `+` işleci işlenenleri toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="593d4-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

<span data-ttu-id="593d4-109">Aritmetik işleçler hakkında daha fazla bilgi için bkz: [aritmetik işleçler](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="593d4-109">For more information about arithmetic operators, see [Arithmetic operators](arithmetic-operators.md).</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="593d4-110">Dize birleştirme</span><span class="sxs-lookup"><span data-stu-id="593d4-110">String concatenation</span></span>

<span data-ttu-id="593d4-111">Bir veya iki işlenenin türünde olduğunda [dize](../keywords/string.md), `+` işleci, işlenenleri dize temsillerini art arda ekler:</span><span class="sxs-lookup"><span data-stu-id="593d4-111">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="593d4-112">İle başlayarak C# 6, [dize ilişkilendirme](../tokens/interpolated.md) biçim dizeleri için daha kolay bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="593d4-112">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="593d4-113">Temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="593d4-113">Delegate combination</span></span>

<span data-ttu-id="593d4-114">İçin [temsilci](../keywords/delegate.md) türleri `+` işleci döndüren yeni bir temsilci örneği, çağrılır, birinci işlenenin çağırır ve ardından ikinci işlenenin çağırır.</span><span class="sxs-lookup"><span data-stu-id="593d4-114">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="593d4-115">İşlenenden ise `null`, `+` işleci, başka bir işlenenin değerini döndürür (Ayrıca olabilen `null`).</span><span class="sxs-lookup"><span data-stu-id="593d4-115">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="593d4-116">Aşağıdaki örnek, temsilciler ne birleştirilebilir gösterir `+` işleci:</span><span class="sxs-lookup"><span data-stu-id="593d4-116">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="593d4-117">Temsilci türleri hakkında daha fazla bilgi için bkz: [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="593d4-117">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="593d4-118">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="593d4-118">Operator overloadability</span></span>

<span data-ttu-id="593d4-119">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) tekli veya ikili `+` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="593d4-119">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="593d4-120">Bir ikili olduğunda `+` işleci aşırı yüklenmiş, [toplama atama işleci](addition-assignment-operator.md) `+=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="593d4-120">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="593d4-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="593d4-121">C# language specification</span></span>

<span data-ttu-id="593d4-122">Daha fazla bilgi için [birli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="593d4-122">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="593d4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="593d4-123">See also</span></span>

- [<span data-ttu-id="593d4-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="593d4-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="593d4-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="593d4-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="593d4-126">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="593d4-126">C# Operators</span></span>](index.md)
- [<span data-ttu-id="593d4-127">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="593d4-127">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="593d4-128">Nasıl yapılır: Birden çok dizeyi birleştirme</span><span class="sxs-lookup"><span data-stu-id="593d4-128">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="593d4-129">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="593d4-129">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="593d4-130">Checked ve unchecked</span><span class="sxs-lookup"><span data-stu-id="593d4-130">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
