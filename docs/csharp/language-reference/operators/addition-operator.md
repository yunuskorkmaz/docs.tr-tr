---
title: + ve += işleçleri - C# referansı
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
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399303"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="768e7-102">+ ve += işleçleri (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="768e7-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="768e7-103">Ve `+` `+=` işleçler yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri, [dize](../builtin-types/reference-types.md#the-string-type) türü ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="768e7-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="768e7-104">Aritmetik `+` işleç hakkında bilgi için, [Aritmetik işleçleri](arithmetic-operators.md) makalesinin [Unary artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [Ek işleci +](arithmetic-operators.md#addition-operator-) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="768e7-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="768e7-105">Dize concatenation</span><span class="sxs-lookup"><span data-stu-id="768e7-105">String concatenation</span></span>

<span data-ttu-id="768e7-106">Bir veya her iki operands tip `+` [dize](../builtin-types/reference-types.md#the-string-type)olduğunda, işleç onun operands dize gösterimleri concatenates:</span><span class="sxs-lookup"><span data-stu-id="768e7-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="768e7-107">C# 6 ile başlayarak, [string enterpolasyonu](../tokens/interpolated.md) dizeleri biçimlendirmek için daha uygun bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="768e7-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="768e7-108">Temsilci kombinasyonu</span><span class="sxs-lookup"><span data-stu-id="768e7-108">Delegate combination</span></span>

<span data-ttu-id="768e7-109">Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türündeki operandlar `+` için, işleç çağrıldığı zaman sol operand'ı çağıran ve sonra sağ operand'ı çağıran yeni bir temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="768e7-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="768e7-110">Operands herhangi biri `null`ise, `+` operatör başka bir operand değerini döndürür (aynı zamanda olabilir). `null`</span><span class="sxs-lookup"><span data-stu-id="768e7-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="768e7-111">Aşağıdaki örnek, temsilcilerin `+` işleçle nasıl birleştirilebileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="768e7-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="768e7-112">Temsilci kaldırma gerçekleştirmek için [ `-` işleci](subtraction-operator.md#delegate-removal)kullanın.</span><span class="sxs-lookup"><span data-stu-id="768e7-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="768e7-113">Temsilci türleri hakkında daha fazla bilgi [için, Bkz. Temsilciler.](../../programming-guide/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="768e7-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="768e7-114">Ek atama işleci +=</span><span class="sxs-lookup"><span data-stu-id="768e7-114">Addition assignment operator +=</span></span>

<span data-ttu-id="768e7-115">`+=` İşleç kullanarak bir ifade, gibi</span><span class="sxs-lookup"><span data-stu-id="768e7-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="768e7-116">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="768e7-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="768e7-117">`x` bunun dışında sadece bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="768e7-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="768e7-118">Aşağıdaki örnek, işleç `+=` kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="768e7-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="768e7-119">Ayrıca, bir `+=` [olaya](../keywords/event.md)abone olduğunuzda bir olay işleyicisi yöntemini belirtmek için işleci de kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="768e7-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="768e7-120">Daha fazla bilgi için [bkz: Etkinliklere abone](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)olun ve abonelikten çıkın.</span><span class="sxs-lookup"><span data-stu-id="768e7-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="768e7-121">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="768e7-121">Operator overloadability</span></span>

<span data-ttu-id="768e7-122">Kullanıcı tanımlı bir tür `+` operatörü [aşırı yükleyebilir.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="768e7-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="768e7-123">Bir ikili `+` işleç aşırı `+=` yüklendiğinde, işleç de örtülü olarak aşırı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="768e7-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="768e7-124">Kullanıcı tanımlı bir tür `+=` operatörü açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="768e7-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="768e7-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="768e7-125">C# language specification</span></span>

<span data-ttu-id="768e7-126">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Unary artı operatörü](~/_csharplang/spec/expressions.md#unary-plus-operator) ve Ek [işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="768e7-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="768e7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="768e7-127">See also</span></span>

- [<span data-ttu-id="768e7-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="768e7-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="768e7-129">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="768e7-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="768e7-130">Birden çok dize nasıl işlenir?</span><span class="sxs-lookup"><span data-stu-id="768e7-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="768e7-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="768e7-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="768e7-132">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="768e7-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="768e7-133">- ve -= operatörler</span><span class="sxs-lookup"><span data-stu-id="768e7-133">- and -= operators</span></span>](subtraction-operator.md)
