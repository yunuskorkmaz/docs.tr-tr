---
title: '- ve-= operators - C# başvurusu'
ms.custom: seodec18
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
ms.openlocfilehash: aae10f8b03a16e55f0b26981f17585c8790e00c1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816076"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="1d1c4-102">- ve-= işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1d1c4-102">- and -= operators (C# Reference)</span></span>

<span data-ttu-id="1d1c4-103">`-` İşleci yerleşik sayısal türler tarafından desteklenir ve [temsilci](../keywords/delegate.md) türleri.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="1d1c4-104">Aritmetik hakkında bilgi için `-` işleci bkz [birli artı ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [çıkarma işleci -](arithmetic-operators.md#subtraction-operator--) bölümlerini [aritmetikişleçler](arithmetic-operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="1d1c4-105">Temsilci kaldırma</span><span class="sxs-lookup"><span data-stu-id="1d1c4-105">Delegate removal</span></span>

<span data-ttu-id="1d1c4-106">Aynı işlenenleri için [temsilci](../keywords/delegate.md) türü `-` işleci aşağıdaki gibi hesaplanır bir temsilci örneği döndürür:</span><span class="sxs-lookup"><span data-stu-id="1d1c4-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="1d1c4-107">Her iki işlenen de null olmayan ve uygun bir bitişik alt liste çağırma listenin birinci işlenenin ikinci işlenenin çağırma listesi ise, işlemin sonucunu, ikinci işlenenin ait girişlerden kaldırarak alınan yeni çağırma listesidir birinci işlenenin çağırma listesi.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="1d1c4-108">İkinci işlenenin 's listesi birinci işlenenin 's listesinde birden çok bitişik alt listelerin eşleşirse, yalnızca en sağdaki eşleşen alt liste kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="1d1c4-109">Kaldırma işlemi boş bir liste sonuçlanırsa sonucudur `null`.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="1d1c4-110">Uygun bir bitişik alt liste çağırma listenin birinci işlenenin ikinci işlenenin çağırma listesi değilse, işlemin sonucu ilk işlenen ' dir.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span> <span data-ttu-id="1d1c4-111">Örneğin, çok noktaya yayın temsilci bir parçası olmayan bir temsilci kaldırma hiçbir şey yapmaz ve değişmeden çok noktaya yayın Temsilcide sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="1d1c4-112">Yukarıdaki örnekte, temsilci sırasında temizleme temsilci örneklerini karşılaştırılır de gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="1d1c4-113">Örneğin, özdeş bir değerlendirmesinden gelen üretilen Temsilciler [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="1d1c4-114">Temsilci eşitlik hakkında daha fazla bilgi için bkz: [temsilci eşitlik işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1d1c4-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

- <span data-ttu-id="1d1c4-115">Birinci işlenenin ise `null`, işlem sonucu `null`.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-115">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="1d1c4-116">İkinci işlenen `null`, işlemi birinci işlenenin sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-116">If the second operand is `null`, the result of the operation is the first operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="1d1c4-117">Temsilciler birleştirmek için kullanın [ `+` işleci](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="1d1c4-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="1d1c4-118">Temsilci türleri hakkında daha fazla bilgi için bkz: [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="1d1c4-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="1d1c4-119">Çıkarma atama işleci-=</span><span class="sxs-lookup"><span data-stu-id="1d1c4-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="1d1c4-120">Bir ifade kullanarak `-=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="1d1c4-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="1d1c4-121">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="1d1c4-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="1d1c4-122">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-122">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="1d1c4-123">Aşağıdaki örnek, kullanımını gösterir. `-=` işleci:</span><span class="sxs-lookup"><span data-stu-id="1d1c4-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="1d1c4-124">Ayrıca `-=` abonelikten çıkma kaldırmak için bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="1d1c4-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="1d1c4-125">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="1d1c4-125">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1d1c4-126">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="1d1c4-126">Operator overloadability</span></span>

<span data-ttu-id="1d1c4-127">Kullanıcı tanımlı bir tür için [aşırı](../keywords/operator.md) `-` işleci.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-127">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="1d1c4-128">Bir ikili olduğunda `-` işleci aşırı yüklenmiş, `-=` işleci örtük olarak aşırı yüklenmiş, ayrıca.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="1d1c4-129">Kullanıcı tanımlı bir türe açıkça aşırı yüklenemez `-=` işleci.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d1c4-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1d1c4-130">C# language specification</span></span>

<span data-ttu-id="1d1c4-131">Daha fazla bilgi için [birli eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator) ve [çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator) bölümlerini [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1d1c4-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d1c4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d1c4-132">See also</span></span>

- [<span data-ttu-id="1d1c4-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1d1c4-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d1c4-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1d1c4-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d1c4-135">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="1d1c4-135">C# Operators</span></span>](index.md)
- [<span data-ttu-id="1d1c4-136">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="1d1c4-136">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="1d1c4-137">Olaylar</span><span class="sxs-lookup"><span data-stu-id="1d1c4-137">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="1d1c4-138">Checked ve unchecked</span><span class="sxs-lookup"><span data-stu-id="1d1c4-138">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="1d1c4-139">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="1d1c4-139">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="1d1c4-140">+ ve += işleçleri</span><span class="sxs-lookup"><span data-stu-id="1d1c4-140">+ and += operators</span></span>](addition-operator.md)
