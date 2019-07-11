---
title: = işleci - C# başvurusu
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 1277b35723777760deebb6606ddc90bd21e654ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744111"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="936ed-102">= işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="936ed-102">= operator (C# reference)</span></span>

<span data-ttu-id="936ed-103">Atama işleci `=` , sağ işleneninin değeri bir değişkene atar bir [özelliği](../../programming-guide/classes-and-structs/properties.md), veya bir [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) , sol işlenen tarafından belirtilen öğe.</span><span class="sxs-lookup"><span data-stu-id="936ed-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="936ed-104">Atama ifadesi sol işlenen için atanan değer sonucudur.</span><span class="sxs-lookup"><span data-stu-id="936ed-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="936ed-105">Sağ işleneninin türü, sol işlenen veya örtük olarak dönüştürülebilir ona türü ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="936ed-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="936ed-106">Atama işleci sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="936ed-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="936ed-107">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="936ed-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="936ed-108">Aşağıdaki örnek, sol işlenen olarak yerel bir değişken, bir özellik ve dizin oluşturucu öğenin atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="936ed-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="936ed-109">başvuru atama işleci</span><span class="sxs-lookup"><span data-stu-id="936ed-109">ref assignment operator</span></span>

<span data-ttu-id="936ed-110">İle başlayarak C# 7.3, başvuru atama işleci kullanabileceğiniz `= ref` yeniden atamak için bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni.</span><span class="sxs-lookup"><span data-stu-id="936ed-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="936ed-111">Aşağıdaki örnek, başvuru atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="936ed-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="936ed-112">Başvuru atama işleci söz konusu olduğunda, her iki işlenenleri türünü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="936ed-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="936ed-113">Daha fazla bilgi için [özellik teklif Not](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="936ed-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="936ed-114">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="936ed-114">Compound assignment</span></span>

<span data-ttu-id="936ed-115">İkili işleç için `op`, formun bir bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="936ed-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="936ed-116">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="936ed-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="936ed-117">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="936ed-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="936ed-118">Tarafından desteklenen bileşik atama [aritmetik](arithmetic-operators.md#compound-assignment), [Boolean mantıksal](boolean-logical-operators.md#compound-assignment), ve [bit düzeyinde mantıksal and -shift ile](bitwise-and-shift-operators.md#compound-assignment) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="936ed-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="936ed-119">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="936ed-119">Operator overloadability</span></span>

<span data-ttu-id="936ed-120">Kullanıcı tanımlı bir tür atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="936ed-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="936ed-121">Ancak, kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="936ed-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="936ed-122">Bu şekilde, bir değişken, bir özellik veya dizin oluşturucu öğenin başka bir tür için kullanıcı tanımlı bir tür değeri atanabilir.</span><span class="sxs-lookup"><span data-stu-id="936ed-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="936ed-123">Daha fazla bilgi için [kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="936ed-123">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="936ed-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="936ed-124">C# language specification</span></span>

<span data-ttu-id="936ed-125">Daha fazla bilgi için [atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="936ed-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="936ed-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="936ed-126">See also</span></span>

- [<span data-ttu-id="936ed-127">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="936ed-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="936ed-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="936ed-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="936ed-129">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="936ed-129">ref keyword</span></span>](../keywords/ref.md)
