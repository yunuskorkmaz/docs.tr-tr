---
title: = İşleci (C# Başvurusu)
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 123674f37d17db6dcfe6ae9d45c7176bdff1eda7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149230"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="45e38-102">= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="45e38-102">= Operator (C# Reference)</span></span>

<span data-ttu-id="45e38-103">Atama işleci `=` , sağ işleneninin değeri bir değişkene atar bir [özelliği](../../programming-guide/classes-and-structs/properties.md), veya bir [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) , sol işlenen tarafından belirtilen öğe.</span><span class="sxs-lookup"><span data-stu-id="45e38-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="45e38-104">Atama ifadesi sol işlenen için atanan değer sonucudur.</span><span class="sxs-lookup"><span data-stu-id="45e38-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="45e38-105">Sağ işleneninin türü, sol işlenen veya örtük olarak dönüştürülebilir ona türü ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="45e38-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="45e38-106">Atama işleci sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="45e38-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="45e38-107">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="45e38-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="45e38-108">Aşağıdaki örnek, yerel bir değişken, bir özellik ve dizin oluşturucu öğenin değer atamak için atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="45e38-108">The following example demonstrates the usage of the assignment operator to assign values to a local variable, a property, and an indexer element:</span></span>

[!code-csharp-interactive[assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="45e38-109">başvuru atama işleci</span><span class="sxs-lookup"><span data-stu-id="45e38-109">ref assignment operator</span></span>

<span data-ttu-id="45e38-110">İle başlayarak C# 7.3, başvuru atama işleci kullanabileceğiniz `= ref` yeniden atamak için bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni.</span><span class="sxs-lookup"><span data-stu-id="45e38-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="45e38-111">Aşağıdaki örnek, başvuru atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="45e38-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

<span data-ttu-id="45e38-112">Başvuru atama işleci söz konusu olduğunda, sol işlenen ve sağ işlenen türü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="45e38-112">In the case of the ref assignment operator, the type of the left operand and the right operand must be the same.</span></span>

<span data-ttu-id="45e38-113">Daha fazla bilgi için [özellik teklif Not](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="45e38-113">For more information, see the [feature proposal note](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="45e38-114">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="45e38-114">Operator overloadability</span></span>

<span data-ttu-id="45e38-115">Kullanıcı tanımlı bir tür atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="45e38-115">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="45e38-116">Ancak, kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45e38-116">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="45e38-117">Bu şekilde, bir değişken, bir özellik veya dizin oluşturucu öğenin başka bir tür için kullanıcı tanımlı bir tür değeri atanabilir.</span><span class="sxs-lookup"><span data-stu-id="45e38-117">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="45e38-118">Daha fazla bilgi için [örtük](../keywords/implicit.md) anahtar sözcüğü makalesi.</span><span class="sxs-lookup"><span data-stu-id="45e38-118">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="45e38-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="45e38-119">C# language specification</span></span>

<span data-ttu-id="45e38-120">Daha fazla bilgi için [basit atama](~/_csharplang/spec/expressions.md#simple-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="45e38-120">For more information, see the [Simple assignment](~/_csharplang/spec/expressions.md#simple-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45e38-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45e38-121">See also</span></span>

- [<span data-ttu-id="45e38-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="45e38-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="45e38-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="45e38-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45e38-124">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="45e38-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="45e38-125">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="45e38-125">ref keyword</span></span>](../keywords/ref.md)
