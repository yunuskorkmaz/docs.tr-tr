---
title: + İşleci (C# Başvurusu)
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 27ea47d698b20f112880750ec0bc931f1917f142
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192310"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f3f7b-102">+ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f3f7b-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="f3f7b-103">`+` İşleci iki biçimde desteklenir: bir birli artı işleci veya bir ikili Toplama işleci.</span><span class="sxs-lookup"><span data-stu-id="f3f7b-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="f3f7b-104">Tekli artı işleci</span><span class="sxs-lookup"><span data-stu-id="f3f7b-104">Unary plus operator</span></span>

<span data-ttu-id="f3f7b-105">Birli `+` işleci, işlenenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3f7b-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="f3f7b-106">Tüm sayısal türler tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f3f7b-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="f3f7b-107">Sayısal toplama</span><span class="sxs-lookup"><span data-stu-id="f3f7b-107">Numeric addition</span></span>

<span data-ttu-id="f3f7b-108">Sayısal türlerin `+` işleci işlenenleri toplamını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="f3f7b-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="f3f7b-109">Dize birleştirme</span><span class="sxs-lookup"><span data-stu-id="f3f7b-109">String concatenation</span></span>

<span data-ttu-id="f3f7b-110">Bir veya iki işlenenin türünde olduğunda [dize](../keywords/string.md), `+` işleci, işlenenleri dize temsillerini art arda ekler:</span><span class="sxs-lookup"><span data-stu-id="f3f7b-110">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="f3f7b-111">İle başlayarak C# 6, [dize ilişkilendirme](../tokens/interpolated.md) biçim dizeleri için daha kolay bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="f3f7b-111">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="f3f7b-112">Temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="f3f7b-112">Delegate combination</span></span>

<span data-ttu-id="f3f7b-113">İçin [temsilci](../keywords/delegate.md) türleri `+` işleci döndüren yeni bir temsilci örneği, çağrılır, birinci işlenenin çağırır ve ardından ikinci işlenenin çağırır.</span><span class="sxs-lookup"><span data-stu-id="f3f7b-113">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="f3f7b-114">İşlenenden ise `null`, `+` işleci, başka bir işlenenin değerini döndürür (Ayrıca olabilen `null`).</span><span class="sxs-lookup"><span data-stu-id="f3f7b-114">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="f3f7b-115">Aşağıdaki örnek, temsilciler ne birleştirilebilir gösterir `+` işleci:</span><span class="sxs-lookup"><span data-stu-id="f3f7b-115">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="f3f7b-116">Temsilci türleri hakkında daha fazla bilgi için bkz: [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="f3f7b-116">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f3f7b-117">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="f3f7b-117">Operator overloadability</span></span>

<span data-ttu-id="f3f7b-118">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) tekli veya ikili `+` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="f3f7b-118">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="f3f7b-119">Bir ikili olduğunda `+` işleci aşırı yüklenmiş, [toplama atama işleci](addition-assignment-operator.md) `+=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="f3f7b-119">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f3f7b-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f3f7b-120">C# language specification</span></span>

<span data-ttu-id="f3f7b-121">Daha fazla bilgi için [birli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f3f7b-121">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3f7b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3f7b-122">See also</span></span>

- [<span data-ttu-id="f3f7b-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f3f7b-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f3f7b-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f3f7b-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f3f7b-125">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f3f7b-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="f3f7b-126">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="f3f7b-126">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="f3f7b-127">Nasıl yapılır: Birden Çok Dizeyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="f3f7b-127">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="f3f7b-128">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f3f7b-128">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="f3f7b-129">Checked ve unchecked</span><span class="sxs-lookup"><span data-stu-id="f3f7b-129">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
