---
title: '- ve -= işleçler - C# referans'
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 2017aade92e8d7ad2af7101a107122fa8d7b9e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847657"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="6d4c8-102">- ve -= işleçleri (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="6d4c8-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="6d4c8-103">Ve `-` `-=` işleçler yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="6d4c8-104">Aritmetik `-` işleç hakkında bilgi için, [Aritmetik işleçleri](arithmetic-operators.md) makalesinin [Unary artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [Çıkarma işleci bölümlerine](arithmetic-operators.md#subtraction-operator--) bakın.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="6d4c8-105">Temsilci kaldırma</span><span class="sxs-lookup"><span data-stu-id="6d4c8-105">Delegate removal</span></span>

<span data-ttu-id="6d4c8-106">Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türündeki operandlar `-` için işleç aşağıdaki gibi hesaplanan bir temsilci örneği döndürür:</span><span class="sxs-lookup"><span data-stu-id="6d4c8-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="6d4c8-107">Her iki operands null ve sağ operand invocation listesi sol operand çağırma listesiuygun bitişik alt listesi ise, operasyonun sonucu sağ operand'S kaldırarak elde edilen yeni bir çağırma listesi sol operand çağırma listesinden girişler.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="6d4c8-108">Sağ operand'ın listesi sol operand'ın listesinde birden çok bitişik alt listeyle eşleşiyorsa, yalnızca sağdaki en eşleşen alt liste kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="6d4c8-109">Kaldırma boş bir listeyle sonuçlanırsa, sonuç `null`.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](snippets/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="6d4c8-110">Sağ operand çağırma listesi sol operand çağırma listesi uygun bir bitişik alt listesi değilse, işlemin sonucu sol operand olduğunu.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="6d4c8-111">Örneğin, çok noktaya yayın temsilcisinin parçası olmayan bir temsilcinin kaldırılması hiçbir şey yapmaz ve değişmemiş çok noktaya yayın temsilcisiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](snippets/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="6d4c8-112">Önceki örnek, temsilci kaldırma temsilci örnekleri sırasında karşılaştırılabilen olduğunu da göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="6d4c8-113">Örneğin, özdeş [lambda ifadelerinin](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirilmesinden üretilen temsilciler eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="6d4c8-114">Temsilci eşitliği hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Temsilci eşitliği işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="6d4c8-115">Sol operand ise `null`, işlemin sonucudur. `null`</span><span class="sxs-lookup"><span data-stu-id="6d4c8-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="6d4c8-116">Eğer sağ operand ise, `null`operasyonun sonucu sol operand olduğunu.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](snippets/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="6d4c8-117">Temsilcileri birleştirmek için [ `+` işleci](addition-operator.md#delegate-combination)kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="6d4c8-118">Temsilci türleri hakkında daha fazla bilgi [için, Bkz. Temsilciler.](../../programming-guide/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="6d4c8-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="6d4c8-119">Çıkarma atama sıcadı işleci -=</span><span class="sxs-lookup"><span data-stu-id="6d4c8-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="6d4c8-120">`-=` İşleç kullanarak bir ifade, gibi</span><span class="sxs-lookup"><span data-stu-id="6d4c8-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="6d4c8-121">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="6d4c8-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="6d4c8-122">`x` bunun dışında sadece bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="6d4c8-123">Aşağıdaki örnek, işleç `-=` kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6d4c8-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](snippets/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="6d4c8-124">Ayrıca, bir `-=` [olaydan](../keywords/event.md)aboneliğinizi kaldırdığınızda kaldırmak için bir olay işleyicisi yöntemini belirtmek için işleci de kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="6d4c8-125">Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="6d4c8-125">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6d4c8-126">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="6d4c8-126">Operator overloadability</span></span>

<span data-ttu-id="6d4c8-127">Kullanıcı tanımlı bir tür `-` operatörü [aşırı yükleyebilir.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="6d4c8-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="6d4c8-128">Bir ikili `-` işleç aşırı `-=` yüklendiğinde, işleç de örtülü olarak aşırı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="6d4c8-129">Kullanıcı tanımlı bir tür `-=` operatörü açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6d4c8-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6d4c8-130">C# language specification</span></span>

<span data-ttu-id="6d4c8-131">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Unary eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator) ve [Çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d4c8-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d4c8-132">See also</span></span>

- [<span data-ttu-id="6d4c8-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6d4c8-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6d4c8-134">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6d4c8-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="6d4c8-135">Olaylar</span><span class="sxs-lookup"><span data-stu-id="6d4c8-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="6d4c8-136">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="6d4c8-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="6d4c8-137">+ ve += işleçleri</span><span class="sxs-lookup"><span data-stu-id="6d4c8-137">+ and += operators</span></span>](addition-operator.md)
