---
title: '- ve-= işleçleri-C# başvurusu'
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
ms.openlocfilehash: 0475e1be74af0b367785443224cd2e737d2f7301
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555599"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="1793b-102">-ve-= işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1793b-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="1793b-103">`-`Ve `-=` işleçleri, yerleşik [integral](../builtin-types/integral-numeric-types.md) ve [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türleri ve [temsilci](../builtin-types/reference-types.md#the-delegate-type) türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1793b-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="1793b-104">Aritmetik operatör hakkında daha fazla bilgi için `-` , [Aritmetik Işleçler](arithmetic-operators.md) makalesinin [birli Plus ve eksi işleçleri](arithmetic-operators.md#unary-plus-and-minus-operators) ve [çıkarma işleci](arithmetic-operators.md#subtraction-operator--) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1793b-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="1793b-105">Temsilci kaldırma</span><span class="sxs-lookup"><span data-stu-id="1793b-105">Delegate removal</span></span>

<span data-ttu-id="1793b-106">Aynı [temsilci](../builtin-types/reference-types.md#the-delegate-type) türünün işlenenleri için, `-` işleç aşağıdaki şekilde hesaplanan bir temsilci örneği döndürür:</span><span class="sxs-lookup"><span data-stu-id="1793b-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="1793b-107">Her iki işlenen de null değilse ve sağ işlenenin çağırma listesi, sol işlenenin çağırma listesinin uygun bir bitişik alt listesi ise, işlemin sonucu, sol işlenenin çağırma listesinden sağ işlenen girişlerin kaldırılması yoluyla elde edilen yeni bir çağırma listesidir ve.</span><span class="sxs-lookup"><span data-stu-id="1793b-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="1793b-108">Sağ işlenenin listesi sol işlenenin listesindeki birden çok bitişik alt listeyle eşleşiyorsa, yalnızca en sağdaki eşleme alt listesi kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1793b-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="1793b-109">Kaldırma işlemi boş bir liste ile sonuçlanırsa sonuç olur `null` .</span><span class="sxs-lookup"><span data-stu-id="1793b-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](snippets/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="1793b-110">Sağ işlenenin çağırma listesi, sol işlenenin çağırma listesinin uygun bir bitişik alt listesi değilse, işlemin sonucu sol işlenenin bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1793b-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="1793b-111">Örneğin, çok noktaya yayın temsilcisinin parçası olmayan bir temsilciyi kaldırmak, hiçbir şey yapmaz ve değişmeyen çok noktaya yayın temsilcisine neden olur.</span><span class="sxs-lookup"><span data-stu-id="1793b-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](snippets/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="1793b-112">Yukarıdaki örnek ayrıca temsilci kaldırma temsilci örneklerinin karşılaştırıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1793b-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="1793b-113">Örneğin, aynı [lambda ifadelerinin](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirmesinden üretilen temsilciler eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="1793b-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="1793b-114">Temsilci eşitliği hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md), [eşitlik işleçleri temsilcisi](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1793b-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="1793b-115">Sol işlenen ise `null` işlemin sonucu olur `null` .</span><span class="sxs-lookup"><span data-stu-id="1793b-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="1793b-116">Sağ işlenen ise, `null` işlemin sonucu sol işlenenin bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1793b-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](snippets/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="1793b-117">Temsilcileri birleştirmek için [ `+` işlecini](addition-operator.md#delegate-combination)kullanın.</span><span class="sxs-lookup"><span data-stu-id="1793b-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="1793b-118">Temsilci türleri hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="1793b-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="1793b-119">Çıkarma atama işleci-=</span><span class="sxs-lookup"><span data-stu-id="1793b-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="1793b-120">İşlecini kullanan bir ifade `-=` , örneğin</span><span class="sxs-lookup"><span data-stu-id="1793b-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="1793b-121">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="1793b-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="1793b-122">hariç `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1793b-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="1793b-123">Aşağıdaki örnek işlecinin kullanımını gösterir `-=` :</span><span class="sxs-lookup"><span data-stu-id="1793b-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](snippets/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="1793b-124">Ayrıca, `-=` bir [olaydan](../keywords/event.md)abonelik aboneliğini kaldırdığınızda kaldırılacak olay işleyicisi yöntemini belirtmek için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1793b-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="1793b-125">Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="1793b-125">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1793b-126">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="1793b-126">Operator overloadability</span></span>

<span data-ttu-id="1793b-127">Kullanıcı tanımlı bir tür işleci [aşırı](operator-overloading.md) yükleyebilir `-` .</span><span class="sxs-lookup"><span data-stu-id="1793b-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="1793b-128">İkili `-` işleç aşırı yüklendiğinde, `-=` işleci de örtük olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1793b-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="1793b-129">Kullanıcı tanımlı bir tür işleci açıkça aşırı yüklenemez `-=` .</span><span class="sxs-lookup"><span data-stu-id="1793b-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1793b-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1793b-130">C# language specification</span></span>

<span data-ttu-id="1793b-131">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [birli eksi işleci](~/_csharplang/spec/expressions.md#unary-minus-operator) ve [çıkarma işleci](~/_csharplang/spec/expressions.md#subtraction-operator) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1793b-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1793b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1793b-132">See also</span></span>

- [<span data-ttu-id="1793b-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1793b-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1793b-134">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1793b-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="1793b-135">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="1793b-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="1793b-136">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="1793b-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="1793b-137">+ ve + = işleçleri</span><span class="sxs-lookup"><span data-stu-id="1793b-137">+ and += operators</span></span>](addition-operator.md)
