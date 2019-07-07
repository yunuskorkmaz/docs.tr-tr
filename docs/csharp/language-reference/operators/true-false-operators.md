---
title: TRUE ve false işleçleri - C# başvurusu
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 7cbfca932b5f9f8a6f658e84204da5005da5ffb8
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609832"
---
# <a name="true-and-false-operators-c-reference"></a><span data-ttu-id="8ac4b-102">TRUE ve false işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ac4b-102">true and false operators (C# reference)</span></span>

<span data-ttu-id="8ac4b-103">`true` İşleci döndürür [bool](../keywords/bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-103">The `true` operator returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span> <span data-ttu-id="8ac4b-104">`false` İşleci döndürür `bool` değer `true` işleneni kesinlikle false olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-104">The `false` operator returns the `bool` value `true` to indicate that an operand is definitely false.</span></span> <span data-ttu-id="8ac4b-105">`true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span> <span data-ttu-id="8ac4b-106">Diğer bir deyişle, her ikisi de `true` ve `false` işleci döndürebilir `bool` değer `false` aynı işlenen için.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-106">That is, both the `true` and `false` operator might return the `bool` value `false` for the same operand.</span></span> <span data-ttu-id="8ac4b-107">Bir tür iki işleç tanımlıyorsa, aynı zamanda başka bir işleç tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-107">If a type defines one of the two operators, it must also define another operator.</span></span>

> [!TIP]
> <span data-ttu-id="8ac4b-108">Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli Boole türü destekleyen veritabanları ile.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-108">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="8ac4b-109">C#sağlar `&` ve `|` ile üç değerli mantığını destekleyecek işleçleri `bool?` işlenen.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-109">C# provides the `&` and `|` operators that support the three-valued logic with the `bool?` operands.</span></span> <span data-ttu-id="8ac4b-110">Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](boolean-logical-operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-110">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="boolean-expressions"></a><span data-ttu-id="8ac4b-111">Boole ifadeleri</span><span class="sxs-lookup"><span data-stu-id="8ac4b-111">Boolean expressions</span></span>

<span data-ttu-id="8ac4b-112">Tanımlanan bir türü `true` işleci denetleyen bir koşullu deyim sonucu türü olabilir [varsa](../keywords/if-else.md), [yapmak](../keywords/do.md), [sırada](../keywords/while.md), ve [ için](../keywords/for.md) deyimleri ve [koşullu işleç `?:` ](conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8ac4b-112">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](conditional-operator.md).</span></span> <span data-ttu-id="8ac4b-113">Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8ac4b-113">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="user-defined-conditional-logical-operators"></a><span data-ttu-id="8ac4b-114">Kullanıcı tanımlı koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="8ac4b-114">User-defined conditional logical operators</span></span>

<span data-ttu-id="8ac4b-115">Bir tür ederse ile tanımlanan `true` ve `false` işleçleri [aşırı](operator-overloading.md) [mantıksal OR işlecinin](boolean-logical-operators.md#logical-or-operator-) `|` veya [mantıksal AND işleci](boolean-logical-operators.md#logical-and-operator-) `&` belirli bir şekilde [koşullu mantıksal OR işlecinin](boolean-logical-operators.md#conditional-logical-or-operator-) `||` veya [koşullu mantıksal AND işleci](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`sırayla değerlendirilir Bu türündeki işlenenler için.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-115">If a type with the defined `true` and `false` operators [overloads](operator-overloading.md) the [logical OR operator](boolean-logical-operators.md#logical-or-operator-) `|` or the [logical AND operator](boolean-logical-operators.md#logical-and-operator-) `&` in a certain way, the [conditional logical OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||` or [conditional logical AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="8ac4b-116">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8ac4b-116">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="example"></a><span data-ttu-id="8ac4b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ac4b-117">Example</span></span>

<span data-ttu-id="8ac4b-118">Aşağıdaki örnek her ikisi de tanımlayan türü sunar `true` ve `false` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-118">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="8ac4b-119">Türü ayrıca mantıksal AND işlecinin aşırı `&` şekilde, işlecin `&&` , o türündeki işlenenler için ayrıca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-119">The type also overloads the logical AND operator `&` in such a way that the operator `&&` also can be evaluated for the operands of that type.</span></span>

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

<span data-ttu-id="8ac4b-120">Short-circuiting davranışla `&&` işleci.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-120">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="8ac4b-121">Zaman `GetFuelLaunchStatus` yöntemi döndürür `LaunchStatus.Red`, sağ işleneni `&&` işleci değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-121">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the right-hand operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="8ac4b-122">Çünkü `LaunchStatus.Red` kesinlikle false'tur.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-122">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="8ac4b-123">Ardından mantıksal AND sonucunu sağ işleneninin değerini temel bağımlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-123">Then the result of the logical AND doesn't depend on the value of the right-hand operand.</span></span> <span data-ttu-id="8ac4b-124">Örnek çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8ac4b-124">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a><span data-ttu-id="8ac4b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ac4b-125">See also</span></span>

- [<span data-ttu-id="8ac4b-126">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="8ac4b-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8ac4b-127">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ac4b-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="8ac4b-128">TRUE değişmez değeri</span><span class="sxs-lookup"><span data-stu-id="8ac4b-128">true literal</span></span>](../keywords/true-literal.md)
- [<span data-ttu-id="8ac4b-129">false değişmez değeri</span><span class="sxs-lookup"><span data-stu-id="8ac4b-129">false literal</span></span>](../keywords/false-literal.md)
