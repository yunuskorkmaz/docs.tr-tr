---
title: ?? ve?? = işleçler- C# başvuru
ms.custom: seodec18
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
ms.openlocfilehash: 2bd6fe3d2d283e64eebc2251416fa5234e30bdad
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739663"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="3d29a-103">??</span><span class="sxs-lookup"><span data-stu-id="3d29a-103">??</span></span> <span data-ttu-id="3d29a-104">ve?? = işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="3d29a-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="3d29a-105">Null birleşim işleci `??` `null`değilse, sol taraftaki işlenenin değerini döndürür; Aksi takdirde, sağ işleneni değerlendirir ve sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d29a-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="3d29a-106">Sol işlenen, null olmayan olarak değerlendirilirse `??` işleci sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="3d29a-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="3d29a-107">C# 8,0 ve sonraki sürümlerde bulunan null birleşim atama işleci`??=`sağ işleneninin değerini sol taraftaki işlenene yalnızca sol işlenen`null`değerlendirirken atar.</span><span class="sxs-lookup"><span data-stu-id="3d29a-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="3d29a-108">Sol işlenen, null olmayan olarak değerlendirilirse `??=` işleci sağ işleneni değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="3d29a-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="3d29a-109">`??=` işlecinin sol tarafındaki işleneni bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md)veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d29a-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="3d29a-110">C# 7,3 ve önceki sürümlerde `??` işlecinin sol işlenenin türü bir [başvuru türü](../keywords/reference-types.md) ya da [null yapılabilir bir değer türü](../builtin-types/nullable-value-types.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d29a-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="3d29a-111">8,0 ile C# başlayarak, bu gereksinim aşağıdaki değerle değiştirilmiştir:`??`ve`??=`işleçlerinin sol taraftaki işleneninin türü null yapılamayan bir değer türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="3d29a-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="3d29a-112">Özellikle, 8,0 ile C# başlayarak, null birleşim işleçlerini kısıtlanmış olmayan tür parametreleriyle kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d29a-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="3d29a-113">Null birleştirme işleçleri doğru ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d29a-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="3d29a-114">Diğer bir deyişle, formun ifadeleri</span><span class="sxs-lookup"><span data-stu-id="3d29a-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="3d29a-115">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="3d29a-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="3d29a-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3d29a-116">Examples</span></span>

<span data-ttu-id="3d29a-117">`??` ve `??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="3d29a-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="3d29a-118">[Null koşullu işleçlere sahip ifadelerde?. ve? []](member-access-operators.md#null-conditional-operators--and-), null koşullu işlemlere sahip ifadenin sonucu `null`olduğunda değerlendirmek için alternatif bir ifade sağlamak üzere `??` işlecini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d29a-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="3d29a-119">[Null yapılabilir değer türleriyle](../builtin-types/nullable-value-types.md) çalıştığınızda ve temel alınan değer türünde bir değer sağlamanız gerekiyorsa, null yapılabilir bir tür değeri `null`olduğunda sağlamak üzere değer belirtmek için `??` işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="3d29a-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="3d29a-120">Null yapılabilir bir tür değeri `null`, temel alınan değer türünün varsayılan değeri olması durumunda kullanılacak değer <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d29a-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="3d29a-121">7,0 ' C# den başlayarak bağımsız değişken denetim kodunu daha kısa hale getirmek için`??`işlecinin sağ işleneni olarak bir [`throw` ifadesini](../keywords/throw.md#the-throw-expression) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d29a-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="3d29a-122">Yukarıdaki örnek ayrıca bir özelliği tanımlamak için [Expression-Bodied üyelerini](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d29a-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="3d29a-123">8,0 ile C# başlayarak, form kodunu değiştirmek için`??=`işlecini kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="3d29a-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="3d29a-124">aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="3d29a-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="3d29a-125">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="3d29a-125">Operator overloadability</span></span>

<span data-ttu-id="3d29a-126">`??` ve `??=` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="3d29a-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d29a-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3d29a-127">C# language specification</span></span>

<span data-ttu-id="3d29a-128">`??` işleci hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3d29a-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3d29a-129">`??=` işleci hakkında daha fazla bilgi için bkz. [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="3d29a-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d29a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d29a-130">See also</span></span>

- [<span data-ttu-id="3d29a-131">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="3d29a-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3d29a-132">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="3d29a-132">C# operators</span></span>](index.md)
- <span data-ttu-id="3d29a-133">[?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="3d29a-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="3d29a-134">?: işleci</span><span class="sxs-lookup"><span data-stu-id="3d29a-134">?: operator</span></span>](conditional-operator.md)
