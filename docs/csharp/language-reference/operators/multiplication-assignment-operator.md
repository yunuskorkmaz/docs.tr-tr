---
title: '* = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689612"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="20bd2-102">\*= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="20bd2-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="20bd2-103">Çarpma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="20bd2-103">The multiplication assignment operator.</span></span>

<span data-ttu-id="20bd2-104">Bir ifade kullanarak `*=` işleci gibi</span><span class="sxs-lookup"><span data-stu-id="20bd2-104">An expression using the `*=` operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="20bd2-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="20bd2-105">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="20bd2-106">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="20bd2-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="20bd2-107">Sayısal türlerin [ \* işleci](multiplication-operator.md) işlenenleri çarpımını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="20bd2-107">For numeric types, the [\* operator](multiplication-operator.md) computes the product of its operands.</span></span>

<span data-ttu-id="20bd2-108">Aşağıdaki örnek, kullanımını gösterir. `*=` işleci:</span><span class="sxs-lookup"><span data-stu-id="20bd2-108">The following example demonstrates the usage of the `*=` operator:</span></span>

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="20bd2-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="20bd2-109">Operator overloadability</span></span>

<span data-ttu-id="20bd2-110">Kullanıcı tanımlı bir tür ederse [aşırı](../keywords/operator.md) [çarpma işleci](multiplication-operator.md) `*`, çarpma atama işleci `*=` örtük olarak aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="20bd2-110">If a user-defined type [overloads](../keywords/operator.md) the [multiplication operator](multiplication-operator.md) `*`, the multiplication assignment operator `*=` is implicitly overloaded.</span></span> <span data-ttu-id="20bd2-111">Kullanıcı tanımlı bir türe açıkça çarpma atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="20bd2-111">A user-defined type cannot explicitly overload the multiplication assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="20bd2-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="20bd2-112">C# language specification</span></span>

<span data-ttu-id="20bd2-113">Daha fazla bilgi için [bileşik atama](~/_csharplang/spec/expressions.md#compound-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="20bd2-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20bd2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20bd2-114">See also</span></span>

- [<span data-ttu-id="20bd2-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="20bd2-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="20bd2-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="20bd2-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="20bd2-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="20bd2-117">C# Operators</span></span>](index.md)
