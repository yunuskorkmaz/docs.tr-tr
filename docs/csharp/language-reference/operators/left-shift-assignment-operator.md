---
title: << = işleci - C# başvurusu
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219457"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e9237-102">\<\<= işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e9237-102">\<\<= operator (C# Reference)</span></span>

<span data-ttu-id="e9237-103">Sola kaydırma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="e9237-103">The left-shift assignment operator.</span></span>

<span data-ttu-id="e9237-104">Bir ifade kullanarak `<<=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="e9237-104">An expression using the `<<=` operator, such as</span></span>

```csharp
x <<= y
```

<span data-ttu-id="e9237-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="e9237-105">is equivalent to</span></span>

```csharp
x = x << y
```

<span data-ttu-id="e9237-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e9237-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="e9237-107">[ `<<` İşleci](left-shift-operator.md) ilk işleneni sol tarafından ikinci işleneni tarafından tanımlanan bit sayısı kadar kaydırır.</span><span class="sxs-lookup"><span data-stu-id="e9237-107">The [`<<` operator](left-shift-operator.md) shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="e9237-108">Aşağıdaki örnek, kullanımını gösterir. `<<=` işleci:</span><span class="sxs-lookup"><span data-stu-id="e9237-108">The following example demonstrates the usage of the `<<=` operator:</span></span>

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="e9237-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="e9237-109">Operator overloadability</span></span>

<span data-ttu-id="e9237-110">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [ `<<` işleci](left-shift-operator.md), sola kaydırma atama işleci `<<=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="e9237-110">If a user-defined type [overloads](../keywords/operator.md) the [`<<` operator](left-shift-operator.md), the left-shift assignment operator `<<=` is implicitly overloaded.</span></span> <span data-ttu-id="e9237-111">Kullanıcı tanımlı bir türe açıkça sola kaydırma atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e9237-111">A user-defined type cannot explicitly overload the left-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e9237-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e9237-112">C# language specification</span></span>

<span data-ttu-id="e9237-113">Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9237-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9237-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9237-114">See also</span></span>

- [<span data-ttu-id="e9237-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e9237-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e9237-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e9237-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e9237-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e9237-117">C# Operators</span></span>](index.md)
