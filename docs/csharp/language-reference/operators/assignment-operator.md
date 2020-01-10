---
title: Atama işleçleri- C# başvuru
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 19f74e6835ae555a3a38aa6ca8679948c7f290dd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712760"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="d94d2-102">Atama işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="d94d2-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="d94d2-103">Atama işleci `=`, sağ işleneninin değerini bir değişkene, [özelliğe](../../programming-guide/classes-and-structs/properties.md)veya sol tarafından verilen bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="d94d2-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="d94d2-104">Atama ifadesinin sonucu, sol işlenene atanan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d94d2-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="d94d2-105">Sağ işlenenin türü, sol işlenenin türüyle aynı veya örtülü olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d94d2-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="d94d2-106">Atama işleci `=`, doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesidir</span><span class="sxs-lookup"><span data-stu-id="d94d2-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="d94d2-107">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="d94d2-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="d94d2-108">Aşağıdaki örnek, bir yerel değişken, bir özellik ve bir Dizin Oluşturucu öğesi olan atama işlecinin kullanımını sol işlenen olarak gösterir:</span><span class="sxs-lookup"><span data-stu-id="d94d2-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="d94d2-109">ref atama işleci</span><span class="sxs-lookup"><span data-stu-id="d94d2-109">ref assignment operator</span></span>

<span data-ttu-id="d94d2-110">7,3 ' C# den başlayarak ref atama işlecini `= ref` bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenini yeniden atamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d94d2-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="d94d2-111">Aşağıdaki örnek, ref atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d94d2-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="d94d2-112">Ref atama operatörü durumunda, her iki işleneni de aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d94d2-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="d94d2-113">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="d94d2-113">Compound assignment</span></span>

<span data-ttu-id="d94d2-114">Bir ikili işleç `op`için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="d94d2-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="d94d2-115">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="d94d2-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="d94d2-116">`x` hariç, yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d94d2-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="d94d2-117">Bileşik atama [Aritmetik](arithmetic-operators.md#compound-assignment), [Boole mantıksal](boolean-logical-operators.md#compound-assignment)ve [bit düzeyinde mantıksal ve kaydırma](bitwise-and-shift-operators.md#compound-assignment) işleçleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d94d2-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="d94d2-118">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="d94d2-118">Null-coalescing assignment</span></span>

<span data-ttu-id="d94d2-119">8,0 ' C# den başlayarak, sağ işleneninin değerini yalnızca sol taraftaki işlenenin `null`olarak değerlendirdiği durumlarda sol işlenenin değerini atamak için null birleşim atama işlecini `??=` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d94d2-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="d94d2-120">Daha fazla bilgi için?? [ve?? = operatörler](null-coalescing-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="d94d2-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d94d2-121">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="d94d2-121">Operator overloadability</span></span>

<span data-ttu-id="d94d2-122">Kullanıcı tanımlı bir tür atama işlecini [aşırı yükleyemez](operator-overloading.md) .</span><span class="sxs-lookup"><span data-stu-id="d94d2-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="d94d2-123">Ancak, Kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d94d2-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="d94d2-124">Bu şekilde, Kullanıcı tanımlı bir türün değeri bir değişkene, özelliğe veya başka bir türün Dizin Oluşturucu öğesine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="d94d2-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="d94d2-125">Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d94d2-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="d94d2-126">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="d94d2-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="d94d2-127">Ancak, Kullanıcı tanımlı bir tür bir ikili işleci `op`aşırı yükle, varsa `op=` işleci de dolaylı olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d94d2-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d94d2-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d94d2-128">C# language specification</span></span>

<span data-ttu-id="d94d2-129">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d94d2-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d94d2-130">Başvuru atama işleci `= ref`hakkında daha fazla bilgi için bkz. [özellik teklifi Not](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="d94d2-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d94d2-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d94d2-131">See also</span></span>

- [<span data-ttu-id="d94d2-132">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="d94d2-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d94d2-133">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="d94d2-133">C# operators</span></span>](index.md)
- [<span data-ttu-id="d94d2-134">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d94d2-134">ref keyword</span></span>](../keywords/ref.md)
