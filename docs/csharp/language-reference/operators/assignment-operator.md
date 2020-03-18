---
title: Atama işleçleri - C# başvurusu
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 420b41f586a6980d40cf1171eef00dad37bf5abf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399254"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="6982d-102">Atama işleçleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6982d-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="6982d-103">Atama işleci, `=` sağ el operand değerini bir değişkene, bir [özelliğe](../../programming-guide/classes-and-structs/properties.md)veya sol operand tarafından verilen bir [dizinleyici](../../programming-guide/indexers/index.md) öğeye atar.</span><span class="sxs-lookup"><span data-stu-id="6982d-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="6982d-104">Atama ifadesinin sonucu, sol operanda atanan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6982d-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="6982d-105">Sağ operand türü sol operand türü ile aynı olmalıdır veya dolaylı olarak dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="6982d-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="6982d-106">Atama işleci `=` sağ-bağşdırıcı, yani formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="6982d-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="6982d-107">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="6982d-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="6982d-108">Aşağıdaki örnek, atama işlecinin yerel bir değişken, özellik ve dizinleyici öğesi ile sol operand olarak kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6982d-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="6982d-109">ref atama operatörü</span><span class="sxs-lookup"><span data-stu-id="6982d-109">ref assignment operator</span></span>

<span data-ttu-id="6982d-110">C# 7.3 ile başlayarak, ref `= ref` atama işlecini kullanarak bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref salt yerel](../keywords/ref.md#ref-readonly-locals) değişkeni yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6982d-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="6982d-111">Aşağıdaki örnek, ref atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6982d-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="6982d-112">Ref atama işleci söz konusu olduğunda, her iki operands aynı tip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6982d-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="6982d-113">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="6982d-113">Compound assignment</span></span>

<span data-ttu-id="6982d-114">Bir ikili `op`işleç için, formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="6982d-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="6982d-115">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="6982d-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="6982d-116">`x` bunun dışında sadece bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6982d-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="6982d-117">Bileşik atama [aritmetik](arithmetic-operators.md#compound-assignment)tarafından desteklenir , [Boolean mantıksal](boolean-logical-operators.md#compound-assignment), ve [bitwise mantıksal ve kaydırma](bitwise-and-shift-operators.md#compound-assignment) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="6982d-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="6982d-118">Null-coalescing atama</span><span class="sxs-lookup"><span data-stu-id="6982d-118">Null-coalescing assignment</span></span>

<span data-ttu-id="6982d-119">C# 8.0 ile başlayarak, null-coalescing `??=` atama işleci nin sağ operand değerini sol operand'ına atamak için kullanabilirsiniz ve `null`ancak sol operand'ın değerlendirilmesi durumunda.</span><span class="sxs-lookup"><span data-stu-id="6982d-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="6982d-120">Daha fazla bilgi için, bkz [?? = işleçler](null-coalescing-operator.md) makale.</span><span class="sxs-lookup"><span data-stu-id="6982d-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6982d-121">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="6982d-121">Operator overloadability</span></span>

<span data-ttu-id="6982d-122">Kullanıcı tanımlı bir tür atama işlecinin [aşırı yüklenemez.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="6982d-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="6982d-123">Ancak, kullanıcı tanımlı bir tür, başka bir türe örtülü dönüştürme tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6982d-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="6982d-124">Bu şekilde, kullanıcı tanımlı bir türün değeri başka bir türdeki bir değişkene, bir özelliğe veya dizinleyici öğesine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="6982d-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="6982d-125">Daha fazla bilgi için [Bkz. Kullanıcı tanımlı dönüşüm operatörleri.](user-defined-conversion-operators.md)</span><span class="sxs-lookup"><span data-stu-id="6982d-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="6982d-126">Kullanıcı tanımlı bir tür, bileşik atama işlecinin aşırı yüklenemeyeceğini açıkça ifade eder.</span><span class="sxs-lookup"><span data-stu-id="6982d-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="6982d-127">Ancak, kullanıcı tanımlı bir tür bir `op`ikili `op=` işleci aşırı yüklerse , operatör, varsa, aynı zamanda örtülü olarak aşırı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6982d-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6982d-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6982d-128">C# language specification</span></span>

<span data-ttu-id="6982d-129">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6982d-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="6982d-130">Ref atama işleci `= ref`hakkında daha fazla bilgi [için, özellik teklif notuna](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6982d-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6982d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6982d-131">See also</span></span>

- [<span data-ttu-id="6982d-132">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6982d-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6982d-133">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6982d-133">C# operators</span></span>](index.md)
- [<span data-ttu-id="6982d-134">ref anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="6982d-134">ref keyword</span></span>](../keywords/ref.md)
