---
title: = işleci- C# başvuru
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: f30b48fc6bd1e896658a7234a58409ea9a0f5e6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601948"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="23522-102">= işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="23522-102">= operator (C# reference)</span></span>

<span data-ttu-id="23522-103">Atama işleci `=` , sağ işleneninin değerini bir değişkene, [özelliğe](../../programming-guide/classes-and-structs/properties.md)veya kendi sol işleneni tarafından verilen bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="23522-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="23522-104">Atama ifadesinin sonucu, sol işlenene atanan değerdir.</span><span class="sxs-lookup"><span data-stu-id="23522-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="23522-105">Sağ işlenenin türü, sol işlenenin türüyle aynı veya örtülü olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23522-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="23522-106">Atama işleci, doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="23522-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="23522-107">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="23522-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="23522-108">Aşağıdaki örnek, bir yerel değişken, bir özellik ve bir Dizin Oluşturucu öğesi olan atama işlecinin kullanımını sol işlenen olarak gösterir:</span><span class="sxs-lookup"><span data-stu-id="23522-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="23522-109">ref atama işleci</span><span class="sxs-lookup"><span data-stu-id="23522-109">ref assignment operator</span></span>

<span data-ttu-id="23522-110">7,3 ' C# den başlayarak ref atama işlecini `= ref` kullanarak bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenini yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23522-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="23522-111">Aşağıdaki örnek, ref atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="23522-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="23522-112">Ref atama operatörü durumunda, her iki işleneninin türü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23522-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="23522-113">Daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="23522-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="23522-114">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="23522-114">Compound assignment</span></span>

<span data-ttu-id="23522-115">Bir ikili işleci `op`için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="23522-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="23522-116">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="23522-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="23522-117">`x` hariç yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="23522-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="23522-118">Bileşik atama [Aritmetik](arithmetic-operators.md#compound-assignment), [Boole mantıksal](boolean-logical-operators.md#compound-assignment)ve [bit düzeyinde mantıksal ve kaydırma](bitwise-and-shift-operators.md#compound-assignment) işleçleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="23522-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="23522-119">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="23522-119">Operator overloadability</span></span>

<span data-ttu-id="23522-120">Kullanıcı tanımlı bir tür atama işlecini aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="23522-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="23522-121">Ancak, Kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="23522-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="23522-122">Bu şekilde, Kullanıcı tanımlı bir türün değeri bir değişkene, özelliğe veya başka bir türün Dizin Oluşturucu öğesine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="23522-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="23522-123">Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="23522-123">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="23522-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="23522-124">C# language specification</span></span>

<span data-ttu-id="23522-125">Daha fazla bilgi için, [ C# dil belirtiminin](../language-specification/index.md) [atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="23522-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23522-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23522-126">See also</span></span>

- [<span data-ttu-id="23522-127">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="23522-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="23522-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="23522-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="23522-129">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="23522-129">ref keyword</span></span>](../keywords/ref.md)
