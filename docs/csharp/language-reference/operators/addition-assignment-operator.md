---
title: += İşleci (C# Başvurusu)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192037"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bc852-102">+= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bc852-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="bc852-103">Toplama atama işleci.</span><span class="sxs-lookup"><span data-stu-id="bc852-103">The addition assignment operator.</span></span>

<span data-ttu-id="bc852-104">Bir ifade kullanarak `+=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="bc852-104">An expression using the `+=` operator, such as</span></span>  

```csharp
x += y
```  

<span data-ttu-id="bc852-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="bc852-105">is equivalent to</span></span>  

```csharp
x = x + y
```  

<span data-ttu-id="bc852-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bc852-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="bc852-107">Sayısal türlerin [Toplama işleci](addition-operator.md) `+` işlenenleri toplamını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bc852-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="bc852-108">Bir veya iki işlenenin türü ise [dize](../keywords/string.md), işlenenleri dize temsillerini art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="bc852-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="bc852-109">Temsilci türleri için `+` işleci işlenenleri birleşimi olan yeni bir temsilci örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc852-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="bc852-110">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [Toplama işleci](addition-operator.md) `+`, toplama atama işleci `+=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="bc852-110">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span>

<span data-ttu-id="bc852-111">Ayrıca `+=` a abone olduğunuzda bir olay işleyicisi yöntemi belirtmek için işleci bir [olay](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="bc852-111">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="bc852-112">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="bc852-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="bc852-113">Aşağıdaki örnek, kullanımını gösterir. `+=` işleci:</span><span class="sxs-lookup"><span data-stu-id="bc852-113">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a><span data-ttu-id="bc852-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc852-114">See also</span></span>

- [<span data-ttu-id="bc852-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="bc852-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bc852-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bc852-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bc852-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="bc852-117">C# Operators</span></span>](index.md)
- [<span data-ttu-id="bc852-118">Olaylar</span><span class="sxs-lookup"><span data-stu-id="bc852-118">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="bc852-119">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="bc852-119">Delegates</span></span>](../../programming-guide/delegates/index.md)
