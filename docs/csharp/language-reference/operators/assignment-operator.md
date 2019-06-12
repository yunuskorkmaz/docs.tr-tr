---
title: = işleci - C# başvurusu
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 6b8f67f32287b18a9e4ac8f0fa822f6ca4919e7f
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025270"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4217c-102">= işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4217c-102">= operator (C# reference)</span></span>

<span data-ttu-id="4217c-103">Atama işleci `=` , sağ işleneninin değeri bir değişkene atar bir [özelliği](../../programming-guide/classes-and-structs/properties.md), veya bir [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) , sol işlenen tarafından belirtilen öğe.</span><span class="sxs-lookup"><span data-stu-id="4217c-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="4217c-104">Atama ifadesi sol işlenen için atanan değer sonucudur.</span><span class="sxs-lookup"><span data-stu-id="4217c-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="4217c-105">Sağ işleneninin türü, sol işlenen veya örtük olarak dönüştürülebilir ona türü ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4217c-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="4217c-106">Atama işleci sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="4217c-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="4217c-107">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="4217c-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="4217c-108">Aşağıdaki örnek, yerel bir değişken, bir özellik ve dizin oluşturucu öğenin değer atamak için atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4217c-108">The following example demonstrates the usage of the assignment operator to assign values to a local variable, a property, and an indexer element:</span></span>

[!code-csharp-interactive[assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="4217c-109">başvuru atama işleci</span><span class="sxs-lookup"><span data-stu-id="4217c-109">ref assignment operator</span></span>

<span data-ttu-id="4217c-110">İle başlayarak C# 7.3, başvuru atama işleci kullanabileceğiniz `= ref` yeniden atamak için bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4217c-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="4217c-111">Aşağıdaki örnek, başvuru atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4217c-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

<span data-ttu-id="4217c-112">Başvuru atama işleci söz konusu olduğunda, sol işlenen ve sağ işlenen türü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4217c-112">In the case of the ref assignment operator, the type of the left operand and the right operand must be the same.</span></span>

<span data-ttu-id="4217c-113">Daha fazla bilgi için [özellik teklif Not](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="4217c-113">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4217c-114">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="4217c-114">Operator overloadability</span></span>

<span data-ttu-id="4217c-115">Kullanıcı tanımlı bir tür atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="4217c-115">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="4217c-116">Ancak, kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4217c-116">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="4217c-117">Bu şekilde, bir değişken, bir özellik veya dizin oluşturucu öğenin başka bir tür için kullanıcı tanımlı bir tür değeri atanabilir.</span><span class="sxs-lookup"><span data-stu-id="4217c-117">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="4217c-118">Daha fazla bilgi için [örtük](../keywords/implicit.md) anahtar sözcüğü makalesi.</span><span class="sxs-lookup"><span data-stu-id="4217c-118">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4217c-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4217c-119">C# language specification</span></span>

<span data-ttu-id="4217c-120">Daha fazla bilgi için [basit atama](~/_csharplang/spec/expressions.md#simple-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4217c-120">For more information, see the [Simple assignment](~/_csharplang/spec/expressions.md#simple-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4217c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4217c-121">See also</span></span>

- [<span data-ttu-id="4217c-122">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="4217c-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4217c-123">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="4217c-123">C# operators</span></span>](index.md)
- [<span data-ttu-id="4217c-124">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="4217c-124">ref keyword</span></span>](../keywords/ref.md)
