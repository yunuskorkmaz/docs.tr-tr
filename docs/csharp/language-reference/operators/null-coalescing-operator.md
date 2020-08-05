---
title: ?? ve?? = işleçleri-C# başvurusu
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
ms.openlocfilehash: d3d6a5032a5b4fb7059eb93b0024fd292b74fb70
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555246"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="f7bf8-103">??</span><span class="sxs-lookup"><span data-stu-id="f7bf8-103">??</span></span> <span data-ttu-id="f7bf8-104">ve?? = işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f7bf8-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="f7bf8-105">Null birleşim işleci, yoksa `??` sol taraftaki işlenenin değerini döndürür `null` ; Aksi takdirde, sağ işleneni değerlendirir ve sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="f7bf8-106">`??`Sol işlenen, null olmayan olarak değerlendirilirse işleç sağ işlenenini değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="f7bf8-107">C# 8,0 ve üzeri sürümlerde bulunan null birleşim atama işleci, sağ işleneninin `??=` değerini yalnızca sol işlenen olarak değerlendirilirse, sol taraftaki işlenene atar `null` .</span><span class="sxs-lookup"><span data-stu-id="f7bf8-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="f7bf8-108">`??=`Sol işlenen, null olmayan olarak değerlendirilirse işleç sağ işlenenini değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="f7bf8-109">İşlecin sol işleneni `??=` bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md)veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="f7bf8-110">C# 7,3 ve önceki sürümlerde, işlecin sol işleneninin türü `??` bir [başvuru türü](../keywords/reference-types.md) veya [null olabilen bir değer türü](../builtin-types/nullable-value-types.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="f7bf8-111">C# 8,0 ' den başlayarak, bu gereksinim aşağıdaki değerle değiştirilmiştir: ve işleçlerinin sol tarafı işleneni, `??` `??=` null olamayan bir değer türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="f7bf8-112">Özellikle C# 8,0 ' den başlayarak, null birleşim işleçlerini kısıtlanmış olmayan tür parametreleriyle kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7bf8-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="f7bf8-113">Null birleştirme işleçleri doğru ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="f7bf8-114">Diğer bir deyişle, formun ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f7bf8-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="f7bf8-115">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="f7bf8-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="f7bf8-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f7bf8-116">Examples</span></span>

<span data-ttu-id="f7bf8-117">`??`Ve `??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="f7bf8-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="f7bf8-118">[Null koşullu işleçlere sahip ifadelerde?. ve? []](member-access-operators.md#null-conditional-operators--and-), `??` null koşullu işlemlere sahip ifadenin sonucu olarak değerlendirmek için alternatif bir ifade sağlamak üzere işlecini kullanabilirsiniz `null` :</span><span class="sxs-lookup"><span data-stu-id="f7bf8-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="f7bf8-119">[Null yapılabilir değer türleriyle](../builtin-types/nullable-value-types.md) çalıştığınızda ve temel alınan değer türünde bir değer sağlamanız gerekiyorsa, `??` null yapılabilir bir tür değeri olması durumunda sağlayacak değeri belirtmek için işlecini kullanın `null` :</span><span class="sxs-lookup"><span data-stu-id="f7bf8-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="f7bf8-120"><xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>Null yapılabilir bir tür değeri, `null` temel alınan değer türünün varsayılan değeri olması gerektiğinde yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="f7bf8-121">C# 7,0 ' den başlayarak [ `throw` ](../keywords/throw.md#the-throw-expression) `??` bağımsız değişken denetim kodunu daha kısa hale getirmek için işlecin sağ işleneni olarak bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f7bf8-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="f7bf8-122">Yukarıdaki örnek ayrıca bir özelliği tanımlamak için [Expression-Bodied üyelerini](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="f7bf8-123">C# 8,0 ' den başlayarak, `??=` form kodunu değiştirmek için işlecini kullanabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="f7bf8-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="f7bf8-124">aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="f7bf8-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="f7bf8-125">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="f7bf8-125">Operator overloadability</span></span>

<span data-ttu-id="f7bf8-126">İşleçler `??` ve `??=` aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f7bf8-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f7bf8-127">C# language specification</span></span>

<span data-ttu-id="f7bf8-128">İşleci hakkında daha fazla bilgi için `??` [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="f7bf8-129">İşleci hakkında daha fazla bilgi için `??=` bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="f7bf8-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7bf8-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7bf8-130">See also</span></span>

- [<span data-ttu-id="f7bf8-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f7bf8-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f7bf8-132">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f7bf8-132">C# operators and expressions</span></span>](index.md)
- <span data-ttu-id="f7bf8-133">[?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="f7bf8-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="f7bf8-134">?: işleci</span><span class="sxs-lookup"><span data-stu-id="f7bf8-134">?: operator</span></span>](conditional-operator.md)
