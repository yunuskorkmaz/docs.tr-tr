---
title: / = İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286526"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ff8cb-102">/= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ff8cb-102">/= Operator (C# Reference)</span></span>

<span data-ttu-id="ff8cb-103">Bölme atama işleci.</span><span class="sxs-lookup"><span data-stu-id="ff8cb-103">The division assignment operator.</span></span>

<span data-ttu-id="ff8cb-104">Bir ifade kullanarak `/=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="ff8cb-104">An expression using the `/=` operator, such as</span></span>

```csharp
x /= y
```

<span data-ttu-id="ff8cb-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="ff8cb-105">is equivalent to</span></span>

```csharp
x = x / y
```

<span data-ttu-id="ff8cb-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ff8cb-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ff8cb-107">[Bölme işleci](division-operator.md) `/` ilk işlenenin ikinci işleneni olarak böler.</span><span class="sxs-lookup"><span data-stu-id="ff8cb-107">The [division operator](division-operator.md) `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="ff8cb-108">Tüm sayısal türler tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ff8cb-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="ff8cb-109">Aşağıdaki örnek, kullanımını gösterir. `/=` işleci:</span><span class="sxs-lookup"><span data-stu-id="ff8cb-109">The following example demonstrates the usage of the `/=` operator:</span></span>

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="ff8cb-110">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="ff8cb-110">Operator overloadability</span></span>

<span data-ttu-id="ff8cb-111">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [bölme işleci](division-operator.md) `/`, bölme atama işleci `/=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="ff8cb-111">If a user-defined type [overloads](../keywords/operator.md) the [division operator](division-operator.md) `/`, the division assignment operator `/=` is implicitly overloaded.</span></span> <span data-ttu-id="ff8cb-112">Kullanıcı tanımlı bir türe açıkça bölme atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="ff8cb-112">A user-defined type cannot explicitly overload the division assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ff8cb-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ff8cb-113">C# language specification</span></span>

<span data-ttu-id="ff8cb-114">Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ff8cb-114">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff8cb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff8cb-115">See also</span></span>

- [<span data-ttu-id="ff8cb-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ff8cb-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ff8cb-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ff8cb-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ff8cb-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ff8cb-118">C# Operators</span></span>](index.md)
