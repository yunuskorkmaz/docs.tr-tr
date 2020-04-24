---
title: + ve + = işleçleri-C# başvurusu
ms.date: 04/23/2020
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
ms.openlocfilehash: 18364d80b8117fd4074c2c4231eac07c76829bb3
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135743"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="a54fd-102">+ ve + = işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a54fd-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="a54fd-103">`+` Ve `+=` işleçleri yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri, [dize](../builtin-types/reference-types.md#the-string-type) türü ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a54fd-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="a54fd-104">Aritmetik `+` operatör hakkında daha fazla bilgi Için, [Aritmetik işleçler](arithmetic-operators.md) makalesinin [birli Plus ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [ek işleç +](arithmetic-operators.md#addition-operator-) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a54fd-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="a54fd-105">Dize birleştirme</span><span class="sxs-lookup"><span data-stu-id="a54fd-105">String concatenation</span></span>

<span data-ttu-id="a54fd-106">Bir veya her iki işlenen de [dize](../builtin-types/reference-types.md#the-string-type)türünde olduğunda `+` işleç, işlenenlerinin dize temsillerini birleştirir (öğesinin `null` dize temsili boş bir dizedir):</span><span class="sxs-lookup"><span data-stu-id="a54fd-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands (the string representation of `null` is an empty string):</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="a54fd-107">C# 6 ' dan itibaren [dize ilişkilendirme](../tokens/interpolated.md) , dizeleri biçimlendirmek için daha kolay bir yol sağlar:</span><span class="sxs-lookup"><span data-stu-id="a54fd-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="a54fd-108">Temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="a54fd-108">Delegate combination</span></span>

<span data-ttu-id="a54fd-109">Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türünün işlenenleri için, `+` işleci çağrıldığında, sol taraftaki işleneni çağırır ve sonra sağ işleneni çağıran yeni bir temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="a54fd-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="a54fd-110">İşlenenleri varsa `null`, `+` işleç başka bir işlenenin değerini (de olabilir `null`) döndürür.</span><span class="sxs-lookup"><span data-stu-id="a54fd-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="a54fd-111">Aşağıdaki örnek, temsilcilerin `+` işleçle nasıl birleştirilebilme gösterir:</span><span class="sxs-lookup"><span data-stu-id="a54fd-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="a54fd-112">Temsilci kaldırma işlemini gerçekleştirmek için [ `-` işlecini](subtraction-operator.md#delegate-removal)kullanın.</span><span class="sxs-lookup"><span data-stu-id="a54fd-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="a54fd-113">Temsilci türleri hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="a54fd-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="a54fd-114">Toplama atama işleci + =</span><span class="sxs-lookup"><span data-stu-id="a54fd-114">Addition assignment operator +=</span></span>

<span data-ttu-id="a54fd-115">`+=` İşlecini kullanan bir ifade, örneğin</span><span class="sxs-lookup"><span data-stu-id="a54fd-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="a54fd-116">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="a54fd-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="a54fd-117">`x` hariç yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a54fd-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="a54fd-118">Aşağıdaki örnek `+=` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a54fd-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="a54fd-119">Bir [olaya](../keywords/event.md)abone olduğunuzda `+=` bir olay işleyicisi yöntemi belirtmek için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a54fd-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="a54fd-120">Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="a54fd-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a54fd-121">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="a54fd-121">Operator overloadability</span></span>

<span data-ttu-id="a54fd-122">Kullanıcı tanımlı bir tür `+` işleci [aşırı](operator-overloading.md) yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a54fd-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="a54fd-123">İkili `+` işleç aşırı yüklendiğinde, `+=` işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a54fd-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="a54fd-124">Kullanıcı tanımlı bir tür `+=` işleci açıkça aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="a54fd-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a54fd-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a54fd-125">C# language specification</span></span>

<span data-ttu-id="a54fd-126">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [birli Plus işleci](~/_csharplang/spec/expressions.md#unary-plus-operator) ve [ekleme işleci](~/_csharplang/spec/expressions.md#addition-operator) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a54fd-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a54fd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a54fd-127">See also</span></span>

- [<span data-ttu-id="a54fd-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a54fd-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a54fd-129">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="a54fd-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="a54fd-130">Birden çok dizeyi birleştirme</span><span class="sxs-lookup"><span data-stu-id="a54fd-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="a54fd-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="a54fd-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="a54fd-132">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="a54fd-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="a54fd-133">-ve-= işleçleri</span><span class="sxs-lookup"><span data-stu-id="a54fd-133">- and -= operators</span></span>](subtraction-operator.md)
