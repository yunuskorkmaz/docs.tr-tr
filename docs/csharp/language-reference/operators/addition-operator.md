---
title: + ve += operators - C# başvurusu
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 2c99065dacbf391e94c97092336f5dda3adda5b0
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815990"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="c95f5-102">+ ve += işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c95f5-102">+ and += operators (C# Reference)</span></span>

<span data-ttu-id="c95f5-103">`+` İşleci yerleşik sayısal türler tarafından desteklenen [dize](../keywords/string.md) türü ve [temsilci](../keywords/delegate.md) türleri.</span><span class="sxs-lookup"><span data-stu-id="c95f5-103">The `+` operator is supported by the built-in numeric types, [string](../keywords/string.md) type, and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="c95f5-104">Aritmetik hakkında bilgi için `+` işleci bkz [birli artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [Toplama işleci +](arithmetic-operators.md#addition-operator-) bölümlerini [aritmetik işleçler](arithmetic-operators.md)makalesi.</span><span class="sxs-lookup"><span data-stu-id="c95f5-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="c95f5-105">Dize birleştirme</span><span class="sxs-lookup"><span data-stu-id="c95f5-105">String concatenation</span></span>

<span data-ttu-id="c95f5-106">Bir veya iki işlenenin türünde olduğunda [dize](../keywords/string.md), `+` işleci, işlenenleri dize temsillerini art arda ekler:</span><span class="sxs-lookup"><span data-stu-id="c95f5-106">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="c95f5-107">İle başlayarak C# 6, [dize ilişkilendirme](../tokens/interpolated.md) biçim dizeleri için daha kolay bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="c95f5-107">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="c95f5-108">Temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="c95f5-108">Delegate combination</span></span>

<span data-ttu-id="c95f5-109">Aynı işlenenleri için [temsilci](../keywords/delegate.md) türü `+` işleci döndüren yeni bir temsilci örneği, çağrılır, birinci işlenenin çağırır ve ardından ikinci işlenenin çağırır.</span><span class="sxs-lookup"><span data-stu-id="c95f5-109">For operands of the same [delegate](../keywords/delegate.md) type, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="c95f5-110">İşlenenden ise `null`, `+` işleci, başka bir işlenenin değerini döndürür (Ayrıca olabilen `null`).</span><span class="sxs-lookup"><span data-stu-id="c95f5-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="c95f5-111">Aşağıdaki örnek, temsilciler ne birleştirilebilir gösterir `+` işleci:</span><span class="sxs-lookup"><span data-stu-id="c95f5-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="c95f5-112">Temsilci kaldırma gerçekleştirmek için [ `-` işleci](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="c95f5-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="c95f5-113">Temsilci türleri hakkında daha fazla bilgi için bkz: [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="c95f5-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="c95f5-114">Toplama atama işleci +=</span><span class="sxs-lookup"><span data-stu-id="c95f5-114">Addition assignment operator +=</span></span>

<span data-ttu-id="c95f5-115">Bir ifade kullanarak `+=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="c95f5-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="c95f5-116">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="c95f5-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="c95f5-117">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c95f5-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="c95f5-118">Aşağıdaki örnek, kullanımını gösterir. `+=` işleci:</span><span class="sxs-lookup"><span data-stu-id="c95f5-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="c95f5-119">Ayrıca `+=` a abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="c95f5-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="c95f5-120">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="c95f5-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c95f5-121">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="c95f5-121">Operator overloadability</span></span>

<span data-ttu-id="c95f5-122">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="c95f5-122">A user-defined type can [overload](../keywords/operator.md) the `+` operator.</span></span> <span data-ttu-id="c95f5-123">Bir ikili olduğunda `+` işleci aşırı yüklenmiş, `+=` işleci örtük olarak aşırı yüklenmiş, ayrıca.</span><span class="sxs-lookup"><span data-stu-id="c95f5-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="c95f5-124">Kullanıcı tanımlı bir türe açıkça aşırı yüklenemez `+=` işleci.</span><span class="sxs-lookup"><span data-stu-id="c95f5-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c95f5-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c95f5-125">C# language specification</span></span>

<span data-ttu-id="c95f5-126">Daha fazla bilgi için [birli artı işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [Toplama işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerini [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c95f5-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c95f5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c95f5-127">See also</span></span>

- [<span data-ttu-id="c95f5-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c95f5-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c95f5-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c95f5-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c95f5-130">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c95f5-130">C# Operators</span></span>](index.md)
- [<span data-ttu-id="c95f5-131">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="c95f5-131">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="c95f5-132">Nasıl yapılır: birden çok dizeyi birleştirme</span><span class="sxs-lookup"><span data-stu-id="c95f5-132">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="c95f5-133">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c95f5-133">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="c95f5-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="c95f5-134">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="c95f5-135">Checked ve unchecked</span><span class="sxs-lookup"><span data-stu-id="c95f5-135">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="c95f5-136">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="c95f5-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c95f5-137">- ve-= işleçleri</span><span class="sxs-lookup"><span data-stu-id="c95f5-137">- and -= operators</span></span>](subtraction-operator.md)
