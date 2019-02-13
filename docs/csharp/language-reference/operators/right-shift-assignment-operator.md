---
title: '>>= işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220919"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8ec36-102">>> = işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ec36-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="8ec36-103">Sağa kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="8ec36-103">The right-shift assignment operator.</span></span>

<span data-ttu-id="8ec36-104">Bir ifade kullanarak `>>=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="8ec36-104">An expression using the `>>=` operator, such as</span></span>

```csharp
x >>= y
```

<span data-ttu-id="8ec36-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="8ec36-105">is equivalent to</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="8ec36-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8ec36-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="8ec36-107">[ `>>` İşleci](right-shift-operator.md) ilk işlenenin ikinci işleneni tarafından tanımlanan bit sayısına göre sağa kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8ec36-107">The [`>>` operator](right-shift-operator.md) shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="8ec36-108">Aşağıdaki örnek, kullanımını gösterir. `>>=` işleci:</span><span class="sxs-lookup"><span data-stu-id="8ec36-108">The following example demonstrates the usage of the `>>=` operator:</span></span>

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="8ec36-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="8ec36-109">Operator overloadability</span></span>

<span data-ttu-id="8ec36-110">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [ `>>` işleci](right-shift-operator.md), sağa kaydırma atama işleci `>>=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="8ec36-110">If a user-defined type [overloads](../keywords/operator.md) the [`>>` operator](right-shift-operator.md), the right-shift assignment operator `>>=` is implicitly overloaded.</span></span> <span data-ttu-id="8ec36-111">Kullanıcı tanımlı bir türe açıkça sağa kaydırma atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="8ec36-111">A user-defined type cannot explicitly overload the right-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8ec36-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8ec36-112">C# language specification</span></span>

<span data-ttu-id="8ec36-113">Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ec36-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec36-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ec36-114">See also</span></span>

- [<span data-ttu-id="8ec36-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8ec36-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8ec36-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8ec36-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8ec36-117">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ec36-117">C# operators</span></span>](index.md)