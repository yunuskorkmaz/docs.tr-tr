---
title: true ve false işleçleri- C# Reference
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f65ed3b362080d7a8afe89e22bd132d1fc190b06
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552458"
---
# <a name="true-and-false-operators-c-reference"></a><span data-ttu-id="16677-102">true ve false işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="16677-102">true and false operators (C# reference)</span></span>

<span data-ttu-id="16677-103">`true` işleci, işleneninin kesinlikle doğru olduğunu göstermek için `true` [bool](../builtin-types/bool.md) değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="16677-103">The `true` operator returns the [bool](../builtin-types/bool.md) value `true` to indicate that its operand is definitely true.</span></span> <span data-ttu-id="16677-104">`false` işleci, işleneninin kesinlikle yanlış olduğunu göstermek için `bool` değer `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="16677-104">The `false` operator returns the `bool` value `true` to indicate that its operand is definitely false.</span></span> <span data-ttu-id="16677-105">`true` ve `false` işleçleri birbirini tamamlamak için garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="16677-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span> <span data-ttu-id="16677-106">Diğer bir deyişle, `true` ve `false` işlecinin her ikisi de aynı işlenen için `false` `bool` değeri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="16677-106">That is, both the `true` and `false` operator might return the `bool` value `false` for the same operand.</span></span> <span data-ttu-id="16677-107">Bir tür iki işleçten birini tanımlıyorsa, aynı zamanda başka bir işleç tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="16677-107">If a type defines one of the two operators, it must also define another operator.</span></span>

> [!TIP]
> <span data-ttu-id="16677-108">Üç değerli mantığı desteklemeniz gerekiyorsa (örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken) `bool?` türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="16677-108">Use the `bool?` type, if you need to support the three-valued logic (for example, when you work with databases that support a three-valued Boolean type).</span></span> <span data-ttu-id="16677-109">C#`bool?`işlenenleriyle üç değerli mantığı destekleyen`&`ve`|`işleçlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="16677-109">C# provides the `&` and `|` operators that support the three-valued logic with the `bool?` operands.</span></span> <span data-ttu-id="16677-110">Daha fazla bilgi için, [Boole mantıksal işleçler](boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16677-110">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="boolean-expressions"></a><span data-ttu-id="16677-111">Boole ifadeleri</span><span class="sxs-lookup"><span data-stu-id="16677-111">Boolean expressions</span></span>

<span data-ttu-id="16677-112">Tanımlı `true` işlecine sahip bir tür, [IF](../keywords/if-else.md), [Do](../keywords/do.md), [while](../keywords/while.md)ve [for](../keywords/for.md) deyimlerinde ve [koşullu işleç `?:`](conditional-operator.md)bir denetim koşullu ifadesi sonucunun türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="16677-112">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](conditional-operator.md).</span></span> <span data-ttu-id="16677-113">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Boole ifadeleri](~/_csharplang/spec/expressions.md#boolean-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16677-113">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="user-defined-conditional-logical-operators"></a><span data-ttu-id="16677-114">Kullanıcı tanımlı Koşullu mantıksal işleçler</span><span class="sxs-lookup"><span data-stu-id="16677-114">User-defined conditional logical operators</span></span>

<span data-ttu-id="16677-115">Tanımlı `true` ve [`false` işleçleriyle](operator-overloading.md) bir tür, [mantıksal veya işlecini](boolean-logical-operators.md#logical-or-operator-) `|` ya da [mantıksal ve işleç](boolean-logical-operators.md#logical-and-operator-) `&` belırlı bir şekilde, [Koşullu mantıksal or işleci](boolean-logical-operators.md#conditional-logical-or-operator-) `||` veya [ Koşullu mantıksal ve işleç](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, sırasıyla bu türün işlenenleri için değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="16677-115">If a type with the defined `true` and `false` operators [overloads](operator-overloading.md) the [logical OR operator](boolean-logical-operators.md#logical-or-operator-) `|` or the [logical AND operator](boolean-logical-operators.md#logical-and-operator-) `&` in a certain way, the [conditional logical OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||` or [conditional logical AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="16677-116">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Kullanıcı tanımlı Koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16677-116">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="example"></a><span data-ttu-id="16677-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="16677-117">Example</span></span>

<span data-ttu-id="16677-118">Aşağıdaki örnek hem `true` hem de `false` işleçlerini tanımlayan türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="16677-118">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="16677-119">Bu tür Ayrıca, mantıksal ve işleç `&` de, `&&` işlecinin bu türdeki işlenenler için değerlendirilebilecek şekilde de yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="16677-119">The type also overloads the logical AND operator `&` in such a way that the `&&` operator also can be evaluated for the operands of that type.</span></span>

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

<span data-ttu-id="16677-120">`&&` işlecinin kısa devre dışı davranışına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="16677-120">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="16677-121">`GetFuelLaunchStatus` yöntemi `LaunchStatus.Red`döndürdüğünde `&&` işlecinin sağ işleneni değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="16677-121">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the right-hand operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="16677-122">Bunun nedeni, `LaunchStatus.Red` kesinlikle false olur.</span><span class="sxs-lookup"><span data-stu-id="16677-122">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="16677-123">Sonra mantıksal ve sonucu, sağ işlenenin değerine bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="16677-123">Then the result of the logical AND doesn't depend on the value of the right-hand operand.</span></span> <span data-ttu-id="16677-124">Örneğin çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="16677-124">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a><span data-ttu-id="16677-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16677-125">See also</span></span>

- [<span data-ttu-id="16677-126">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="16677-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="16677-127">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="16677-127">C# operators</span></span>](index.md)
