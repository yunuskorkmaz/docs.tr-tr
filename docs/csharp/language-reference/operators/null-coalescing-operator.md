---
title: ?? Ve?? = işleçler - C# referans
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847319"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="1a781-103">??</span><span class="sxs-lookup"><span data-stu-id="1a781-103">??</span></span> <span data-ttu-id="1a781-104">Ve?? = işleçler (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="1a781-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="1a781-105">Null-coalescing operatör `??` sol operand değilse değerini `null`döndürür; aksi takdirde, sağ operand değerlendirir ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a781-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="1a781-106">Operatör `??` sağ operand'ı değerlendirmez ve sol operve null olmayan ı değerlendirirse.</span><span class="sxs-lookup"><span data-stu-id="1a781-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="1a781-107">C# 8.0 ve daha sonra mevcuttur, null-coalescing atama operatörü `??=` sağ operand değerini sol operand ve sadece sol operand `null`değerlendirirse atar .</span><span class="sxs-lookup"><span data-stu-id="1a781-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="1a781-108">Operatör `??=` sağ operand'ı değerlendirmez ve sol operve null olmayan ı değerlendirirse.</span><span class="sxs-lookup"><span data-stu-id="1a781-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="1a781-109">İşleticinin `??=` sol operand bir değişken, bir [özellik](../../programming-guide/classes-and-structs/properties.md)veya bir [dizinleyici](../../programming-guide/indexers/index.md) öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a781-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="1a781-110">C# 7.3 ve daha önce, `??` işleç sol operand türü bir referans [türü](../keywords/reference-types.md) veya [nullable değer türü](../builtin-types/nullable-value-types.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a781-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="1a781-111">C# 8.0 ile başlayarak, bu gereksinim aşağıdakilerle değiştirilir: sol el operand'ın türü `??` ve `??=` işleçler nullable değer türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="1a781-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="1a781-112">Özellikle, C# 8.0 ile başlayarak, sınırlandırılmamış tip parametreleri ile null-coalescing operatörleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a781-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="1a781-113">Null-coalescing operatörleri sağ-associative vardır.</span><span class="sxs-lookup"><span data-stu-id="1a781-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="1a781-114">Diğer bir şey, formun ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1a781-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="1a781-115">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="1a781-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="1a781-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1a781-116">Examples</span></span>

<span data-ttu-id="1a781-117">Ve `??` `??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="1a781-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="1a781-118">[Null-koşullu işleçleri ile ifadelerde ?. ve ?[] , null-koşullu](member-access-operators.md#null-conditional-operators--and-)işlemler ile ifade sonucu durumunda değerlendirmek için alternatif bir ifade sağlamak için `??` işleç `null`kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a781-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="1a781-119">[Nullable değer türleri](../builtin-types/nullable-value-types.md) ile çalışıyorsanız ve temel değer türünün bir `??` değer sağlaması gerektiğinde, nullable bir tür `null`değeri durumunda sağlamak için değeri belirtmek için işleci kullanın:</span><span class="sxs-lookup"><span data-stu-id="1a781-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="1a781-120">Nullable <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> türü değeri temel değer türünün varsayılan `null` değeri olduğunda kullanılacak değer varsa yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a781-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="1a781-121">C# 7.0 ile başlayarak, bağımsız değişken denetimi kodunu daha `??` kısa yapmak için operatörün sağ operand'ı olarak bir [ `throw` ifade](../keywords/throw.md#the-throw-expression) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a781-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="1a781-122">Önceki örnek, bir özelliği tanımlamak için [ifade gövdeli üyelerin](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanılacağını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a781-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="1a781-123">C# 8.0 ile başlayarak, `??=` formun kodunu değiştirmek için işleci kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="1a781-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="1a781-124">aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="1a781-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="1a781-125">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="1a781-125">Operator overloadability</span></span>

<span data-ttu-id="1a781-126">Operatörler `??` `??=` ve aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="1a781-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1a781-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1a781-127">C# language specification</span></span>

<span data-ttu-id="1a781-128">Operatör hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleştirme işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın. `??`</span><span class="sxs-lookup"><span data-stu-id="1a781-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="1a781-129">Operatör hakkında daha fazla bilgi için [özellik teklifi notuna](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)bakın. `??=`</span><span class="sxs-lookup"><span data-stu-id="1a781-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a781-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a781-130">See also</span></span>

- [<span data-ttu-id="1a781-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1a781-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1a781-132">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="1a781-132">C# operators</span></span>](index.md)
- <span data-ttu-id="1a781-133">[?. Ve? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="1a781-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="1a781-134">?: operatör</span><span class="sxs-lookup"><span data-stu-id="1a781-134">?: operator</span></span>](conditional-operator.md)
