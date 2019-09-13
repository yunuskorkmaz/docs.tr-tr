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
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924689"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="b711a-103">??</span><span class="sxs-lookup"><span data-stu-id="b711a-103">??</span></span> <span data-ttu-id="b711a-104">ve?? = işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="b711a-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="b711a-105">Null birleşim işleci `??` , yoksa sol taraftaki işlenenin `null`değerini döndürür; Aksi takdirde, sağ işleneni değerlendirir ve sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b711a-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="b711a-106">Sol işlenen, null olmayan olarak değerlendirilirse işleçsağişleneninideğerlendirmez.`??`</span><span class="sxs-lookup"><span data-stu-id="b711a-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="b711a-107">C# 8,0 ve sonraki sürümlerde kullanılabilir, null birleşim atama işleci `??=` , sağ işleneninin değerini yalnızca sol işlenen olarak `null`değerlendirilirse, sol taraftaki işlenene atar.</span><span class="sxs-lookup"><span data-stu-id="b711a-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="b711a-108">Sol işlenen, null olmayan olarak değerlendirilirse işleçsağişleneninideğerlendirmez.`??=`</span><span class="sxs-lookup"><span data-stu-id="b711a-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="b711a-109">`??=` İşlecin sol işleneni bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md)veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b711a-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span> <span data-ttu-id="b711a-110">Null birleşim atama hakkında daha fazla bilgi için bkz. [özellik teklifi Not](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="b711a-110">For more information about null-coalescing assignment, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

<span data-ttu-id="b711a-111">C# 7,3 ve önceki sürümlerde, `??` işlecin sol işlenenin türü bir başvuru türü ya da [null yapılabilir bir değer türü](../../programming-guide/nullable-types/index.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b711a-111">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a reference type or a [nullable value type](../../programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="b711a-112">8,0 ile C# başlayarak, bu gereksinim şu değerle değiştirilmiştir: `??` ve `??=` işleçlerinin sol tarafı işleneni, null olamayan bir değer türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="b711a-112">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="b711a-113">Özellikle, C# 8,0 ve üzeri sürümlerde kısıtlanmış tür parametreleriyle null birleşim işleçlerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b711a-113">In particular, you can use the null-coalescing operators with unconstrained type parameters in C# 8.0 and later:</span></span>

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="b711a-114">Null birleştirme işleçleri doğru ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b711a-114">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="b711a-115">Diğer bir deyişle, formun ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b711a-115">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="b711a-116">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="b711a-116">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="b711a-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b711a-117">Examples</span></span>

<span data-ttu-id="b711a-118">`??` Ve`??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="b711a-118">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="b711a-119">İle ifadeler de [null koşullu işleçleri?. ve ?[]](member-access-operators.md#null-conditional-operators--and-), null birleşim işleci ile null koşullu işlemler ifadenin sonucu olması durumunda değerlendirmek için alternatif bir ifade sağlamak için kullanabileceğiniz `null`:</span><span class="sxs-lookup"><span data-stu-id="b711a-119">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="b711a-120">Null [yapılabilir değer türleriyle](../../programming-guide/nullable-types/index.md) çalışırken ve temel alınan değer türünde bir değer sağlamanız gerekiyorsa, null olabilen bir tür değeri `null`olması durumunda sağlanacak değeri belirtmek için null birleşim işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b711a-120">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="b711a-121">Null yapılabilir bir tür değeri, `null` temel alınan değer türünün varsayılan değeri olması gerektiğinde yöntemikullanın.<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b711a-121">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="b711a-122">7,0 ile C# başlayarak, bağımsız değişken denetim kodunu daha kısa hale getirmek için null birleşim işlecinin sağ işleneni olarak bir [ `throw` ifade](../keywords/throw.md#the-throw-expression) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b711a-122">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="b711a-123">Yukarıdaki örnek ayrıca bir özelliği tanımlamak için [Expression-Bodied üyelerini](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b711a-123">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="b711a-124">8,0 ile C# başlayarak, form kodunu değiştirmek için `??=` işlecini kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b711a-124">Starting with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="b711a-125">aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="b711a-125">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="b711a-126">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="b711a-126">Operator overloadability</span></span>

<span data-ttu-id="b711a-127">İşleçler `??` ve`??=` aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="b711a-127">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b711a-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b711a-128">C# language specification</span></span>

<span data-ttu-id="b711a-129">`??` İşleci hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b711a-129">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b711a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b711a-130">See also</span></span>

- [<span data-ttu-id="b711a-131">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="b711a-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b711a-132">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="b711a-132">C# operators</span></span>](index.md)
- <span data-ttu-id="b711a-133">[?. ve ?[] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="b711a-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="b711a-134">?: işleci</span><span class="sxs-lookup"><span data-stu-id="b711a-134">?: operator</span></span>](conditional-operator.md)
