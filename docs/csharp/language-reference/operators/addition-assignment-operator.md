---
title: += İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: 5d48f2fe53a9bb6f781f8d35f1e0983bcaa30f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660183"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8c88b-102">+= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8c88b-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="8c88b-103">Toplama atama işleci.</span><span class="sxs-lookup"><span data-stu-id="8c88b-103">The addition assignment operator.</span></span>

<span data-ttu-id="8c88b-104">Bir ifade kullanarak `+=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="8c88b-104">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="8c88b-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="8c88b-105">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="8c88b-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8c88b-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="8c88b-107">Sayısal türlerin [Toplama işleci](addition-operator.md) `+` işlenenleri toplamını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8c88b-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="8c88b-108">Bir veya iki işlenenin türü ise [dize](../keywords/string.md), işlenenleri dize temsillerini art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="8c88b-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="8c88b-109">Temsilci türleri için `+` işleci işlenenleri birleşimi olan yeni bir temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c88b-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="8c88b-110">Ayrıca `+=` a abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="8c88b-110">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="8c88b-111">Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="8c88b-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="8c88b-112">Aşağıdaki örnek, kullanımını gösterir. `+=` işleci:</span><span class="sxs-lookup"><span data-stu-id="8c88b-112">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="8c88b-113">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="8c88b-113">Operator overloadability</span></span>

<span data-ttu-id="8c88b-114">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [Toplama işleci](addition-operator.md) `+`, toplama atama işleci `+=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="8c88b-114">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span> <span data-ttu-id="8c88b-115">Kullanıcı tanımlı bir tür toplama atama işleci açıkça aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="8c88b-115">A user-defined type cannot explicitly overload the addition assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8c88b-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8c88b-116">C# language specification</span></span>

<span data-ttu-id="8c88b-117">Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) ve [olay ataması](~/_csharplang/spec/expressions.md#event-assignment) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c88b-117">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) and [Event assignment](~/_csharplang/spec/expressions.md#event-assignment) sections of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8c88b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c88b-118">See also</span></span>

- [<span data-ttu-id="8c88b-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8c88b-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8c88b-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8c88b-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8c88b-121">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8c88b-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="8c88b-122">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8c88b-122">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="8c88b-123">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="8c88b-123">Delegates</span></span>](../../programming-guide/delegates/index.md)
