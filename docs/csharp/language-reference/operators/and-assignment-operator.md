---
title: '&amp;= İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237031"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="269f6-102">&amp;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="269f6-102">&amp;= Operator (C# Reference)</span></span>

<span data-ttu-id="269f6-103">AND atama işleci.</span><span class="sxs-lookup"><span data-stu-id="269f6-103">The AND assignment operator.</span></span>

<span data-ttu-id="269f6-104">Bir ifade kullanarak `&=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="269f6-104">An expression using the `&=` operator, such as</span></span>

```csharp
x &= y
```

<span data-ttu-id="269f6-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="269f6-105">is equivalent to</span></span>

```csharp
x = x & y
```

<span data-ttu-id="269f6-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="269f6-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="269f6-107">Tamsayı işlenenleri için [ `&` işleci](and-operator.md) hesaplar. bit düzeyinde mantıksal AND işlenenleri için; [bool](../keywords/bool.md) işlenen, mantıksal ve işlenenleri, hesaplar.</span><span class="sxs-lookup"><span data-stu-id="269f6-107">For integer operands, the [`&` operator](and-operator.md) computes the bitwise logical AND of its operands; for [bool](../keywords/bool.md) operands, it computes the logical AND of its operands.</span></span>

<span data-ttu-id="269f6-108">Aşağıdaki örnek, kullanımını gösterir. `&=` işleci:</span><span class="sxs-lookup"><span data-stu-id="269f6-108">The following example demonstrates the usage of the `&=` operator:</span></span>

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a><span data-ttu-id="269f6-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="269f6-109">Operator overloadability</span></span>

<span data-ttu-id="269f6-110">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [ `&` işleci](and-operator.md), AND atama işleci `&=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="269f6-110">If a user-defined type [overloads](../keywords/operator.md) the [`&` operator](and-operator.md), the AND assignment operator `&=` is implicitly overloaded.</span></span> <span data-ttu-id="269f6-111">Kullanıcı tanımlı bir türe açıkça AND atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="269f6-111">A user-defined type cannot explicitly overload the AND assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="269f6-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="269f6-112">C# language specification</span></span>

<span data-ttu-id="269f6-113">Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="269f6-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="269f6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="269f6-114">See also</span></span>

- [<span data-ttu-id="269f6-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="269f6-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="269f6-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="269f6-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="269f6-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="269f6-117">C# Operators</span></span>](index.md)
