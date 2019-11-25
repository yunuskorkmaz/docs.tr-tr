---
title: + ve + = işleçleri- C# başvuru
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
ms.openlocfilehash: e6a190e3d6e283f2ce3b1690ec2bfd15d50dfc6e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972632"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="6983c-102">+ ve + = işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="6983c-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="6983c-103">`+` ve `+=` işleçleri, yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri, [dize](../builtin-types/reference-types.md#the-string-type) türü ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6983c-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="6983c-104">Aritmetik `+` işleci hakkında daha fazla bilgi için, [Aritmetik işleçler](arithmetic-operators.md) makalesinin [birli Plus ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [ek işleç +](arithmetic-operators.md#addition-operator-) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="6983c-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="6983c-105">Dize birleştirme</span><span class="sxs-lookup"><span data-stu-id="6983c-105">String concatenation</span></span>

<span data-ttu-id="6983c-106">Bir veya her iki işlenen de [dize](../builtin-types/reference-types.md#the-string-type)türünde olduğunda, `+` işleci işlenenlerinin dize temsillerini birleştirir:</span><span class="sxs-lookup"><span data-stu-id="6983c-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="6983c-107">C# 6 ' dan başlayarak [dize ilişkilendirme](../tokens/interpolated.md) , dizeleri biçimlendirmek için daha kolay bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="6983c-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="6983c-108">Temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="6983c-108">Delegate combination</span></span>

<span data-ttu-id="6983c-109">Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türünün işlenenleri için `+` işleci, çağrıldığında sol işlenen ve sonra sağ işleneni çağıran yeni bir temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="6983c-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="6983c-110">İşlenenlerin herhangi biri `null`ise, `+` işleci başka bir işlenenin değerini döndürür (Bu da `null`olabilir).</span><span class="sxs-lookup"><span data-stu-id="6983c-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="6983c-111">Aşağıdaki örnek, temsilcilerin `+` işleçle nasıl birleştirilebilme gösterir:</span><span class="sxs-lookup"><span data-stu-id="6983c-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="6983c-112">Temsilci kaldırma işlemini gerçekleştirmek için [`-` işlecini](subtraction-operator.md#delegate-removal)kullanın.</span><span class="sxs-lookup"><span data-stu-id="6983c-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="6983c-113">Temsilci türleri hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="6983c-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="6983c-114">Toplama atama işleci + =</span><span class="sxs-lookup"><span data-stu-id="6983c-114">Addition assignment operator +=</span></span>

<span data-ttu-id="6983c-115">Gibi `+=` işlecini kullanan bir ifade</span><span class="sxs-lookup"><span data-stu-id="6983c-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="6983c-116">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="6983c-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="6983c-117">`x` hariç, yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6983c-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="6983c-118">Aşağıdaki örnek `+=` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6983c-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="6983c-119">Bir [olaya](../keywords/event.md)abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için `+=` işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6983c-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="6983c-120">Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="6983c-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6983c-121">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="6983c-121">Operator overloadability</span></span>

<span data-ttu-id="6983c-122">Kullanıcı tanımlı bir tür `+` işlecini [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6983c-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="6983c-123">İkili `+` işleci aşırı yüklendiğinde, `+=` işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6983c-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="6983c-124">Kullanıcı tanımlı bir tür `+=` işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="6983c-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6983c-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6983c-125">C# language specification</span></span>

<span data-ttu-id="6983c-126">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [birli Plus işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [ekleme işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="6983c-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6983c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6983c-127">See also</span></span>

- [<span data-ttu-id="6983c-128">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="6983c-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6983c-129">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6983c-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="6983c-130">Birden çok dizeyi birleştirme</span><span class="sxs-lookup"><span data-stu-id="6983c-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="6983c-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="6983c-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="6983c-132">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="6983c-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="6983c-133">-ve-= işleçleri</span><span class="sxs-lookup"><span data-stu-id="6983c-133">- and -= operators</span></span>](subtraction-operator.md)
