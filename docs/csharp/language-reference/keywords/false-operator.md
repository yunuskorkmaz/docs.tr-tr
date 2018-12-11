---
title: false işleci (C# Başvurusu)
ms.date: 12/03/2018
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 4428d88acb08246623e2deb71a9daf7fb1cca692
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152311"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="98297-102">false işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="98297-102">false operator (C# Reference)</span></span>

<span data-ttu-id="98297-103">Döndürür [bool](bool.md) değer `true` işleneni kesinlikle false olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="98297-103">Returns the [bool](bool.md) value `true` to indicate that an operand is definitely false.</span></span> <span data-ttu-id="98297-104">Bir türü tanımlıyorsa `false` işleci, bu da tanımlamalıdır [true işleci](true-operator.md).</span><span class="sxs-lookup"><span data-stu-id="98297-104">If a type defines the `false` operator, it must also define the [true operator](true-operator.md).</span></span> <span data-ttu-id="98297-105">`true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="98297-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span>

> [!TIP]
> <span data-ttu-id="98297-106">Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli mantıksal türünü destekleyen veritabanları ile.</span><span class="sxs-lookup"><span data-stu-id="98297-106">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued logical type.</span></span> <span data-ttu-id="98297-107">Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="98297-107">For more information, see [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="98297-108">Bir türü varsa tanımlanan ile `false` işleci [aşırı](operator.md) [mantıksal AND işlecinin](../operators/and-operator.md) `&` belirli bir şekilde [koşullu mantıksal AND işlecinin](../operators/conditional-and-operator.md) `&&`, short-circuiting, olduğu değerlendirmesi yapılamıyor, o türündeki işlenenler için.</span><span class="sxs-lookup"><span data-stu-id="98297-108">If a type with the defined `false` operator [overloads](operator.md) the [logical AND operator](../operators/and-operator.md) `&` in a certain way, the [conditional logical AND operator](../operators/conditional-and-operator.md) `&&`, which is short-circuiting, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="98297-109">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="98297-109">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

<span data-ttu-id="98297-110">Aşağıdaki örnek her ikisi de tanımlayan türü sunar `true` ve `false` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="98297-110">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="98297-111">Ayrıca, mantıksal ve işlecini aşırı `&` şekilde, işlecin `&&` , o türündeki işlenenler için ayrıca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="98297-111">Moreover, it overloads the logical AND operator `&` in such a way that the operator `&&` also can be evaluated for the operands of that type.</span></span>

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

<span data-ttu-id="98297-112">Short-circuiting davranışla `&&` işleci.</span><span class="sxs-lookup"><span data-stu-id="98297-112">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="98297-113">Zaman `GetFuelLaunchStatus` yöntemi döndürür `LaunchStatus.Red`, ikinci işleneni `&&` işleci değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="98297-113">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the second operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="98297-114">Çünkü `LaunchStatus.Red` kesinlikle false'tur.</span><span class="sxs-lookup"><span data-stu-id="98297-114">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="98297-115">Ardından mantıksal AND sonucunu ikinci işlenenin değerine bağımlı değildir.</span><span class="sxs-lookup"><span data-stu-id="98297-115">Then the result of the logical AND doesn't depend on the value of the second operand.</span></span> <span data-ttu-id="98297-116">Örnek çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="98297-116">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

<span data-ttu-id="98297-117">Ayrıca dikkat koşullu ifadede [koşullu işleç `?:` ](../operators/conditional-operator.md) değil `LaunchStatus` türü.</span><span class="sxs-lookup"><span data-stu-id="98297-117">Also notice that the conditional expression in the [conditional operator `?:`](../operators/conditional-operator.md) is of the `LaunchStatus` type.</span></span> <span data-ttu-id="98297-118">Mümkün olan çünkü `LaunchStatus` tanımlar `true` işleci.</span><span class="sxs-lookup"><span data-stu-id="98297-118">That is possible, because `LaunchStatus` defines the `true` operator.</span></span> <span data-ttu-id="98297-119">Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="98297-119">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98297-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98297-120">See also</span></span>

- [<span data-ttu-id="98297-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="98297-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98297-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98297-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98297-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="98297-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="98297-124">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="98297-124">C# Operators</span></span>](../operators/index.md)
- [<span data-ttu-id="98297-125">`false` değişmez değer</span><span class="sxs-lookup"><span data-stu-id="98297-125">`false` literal</span></span>](false-literal.md)