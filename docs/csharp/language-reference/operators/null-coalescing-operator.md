---
title: ?? Operator - C# başvurusu
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8ca97261b348b7813ab179abbc1f2c5f535966a1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816013"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1c7c0-103">??</span><span class="sxs-lookup"><span data-stu-id="1c7c0-103">??</span></span> <span data-ttu-id="1c7c0-104">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1c7c0-104">operator (C# Reference)</span></span>

<span data-ttu-id="1c7c0-105">Null birleşim işleci `??` değilse sol işlenenin değerini döndürür `null`; Aksi takdirde, sağ işlenen değerlendirilir ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c7c0-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="1c7c0-106">`??` İşleci sol işlenen null olmayan olarak değerlendirilirse, sağ işleneni değerlendirmek değil.</span><span class="sxs-lookup"><span data-stu-id="1c7c0-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="1c7c0-107">Null birleşim işleci sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="1c7c0-107">The null-coalescing operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ?? b ?? c
```

<span data-ttu-id="1c7c0-108">olarak değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="1c7c0-108">is evaluated as</span></span>

```csharp
a ?? (b ?? c)
```

<span data-ttu-id="1c7c0-109">`??` İşleci aşağıdaki senaryolarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="1c7c0-109">The `??` operator can be useful in the following scenarios:</span></span>

- <span data-ttu-id="1c7c0-110">İle ifadeler de [null koşullu işleçleri?. ve?] ](member-access-operators.md#null-conditional-operators--and-), null birleşim işleci ile null koşullu işlemler ifadenin sonucu olması durumunda değerlendirmek için alternatif bir ifade sağlamak için kullanabileceğiniz `null`:</span><span class="sxs-lookup"><span data-stu-id="1c7c0-110">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="1c7c0-111">İle çalıştığınızda [boş değer atanabilen değer türleri](../../programming-guide/nullable-types/index.md) ve temel alınan bir değer türünün bir değer belirtmeniz gerekiyorsa null birleşim işleci bir boş değer atanabilir bir tür değeri olması durumunda sağlamak için değeri belirtmek için kullanın `null`:</span><span class="sxs-lookup"><span data-stu-id="1c7c0-111">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="1c7c0-112">Kullanım <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemi, bir boş değer atanabilir tür değeri olduğunda kullanılacak değer `null` temel değer türünün varsayılan değeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c7c0-112">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="1c7c0-113">İle başlayarak C# kullanabileceğiniz 7.0 bir [ `throw` ifade](../keywords/throw.md#the-throw-expression) sağ işleneni, bağımsız değişken denetimi kod daha kısa yapmak için null birleşim işleci olarak:</span><span class="sxs-lookup"><span data-stu-id="1c7c0-113">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="1c7c0-114">Yukarıdaki örnekte ayrıca nasıl kullanılacağını gösterir [ifade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) bir özelliği tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="1c7c0-114">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1c7c0-115">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="1c7c0-115">Operator overloadability</span></span>

<span data-ttu-id="1c7c0-116">Null birleşim işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="1c7c0-116">The null-coalescing operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c7c0-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1c7c0-117">C# language specification</span></span>

<span data-ttu-id="1c7c0-118">Daha fazla bilgi için [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1c7c0-118">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c7c0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c7c0-119">See also</span></span>

- [<span data-ttu-id="1c7c0-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1c7c0-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1c7c0-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1c7c0-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1c7c0-122">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="1c7c0-122">C# operators</span></span>](index.md)
- <span data-ttu-id="1c7c0-123">[?. ve? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="1c7c0-123">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="1c7c0-124">?: işleci</span><span class="sxs-lookup"><span data-stu-id="1c7c0-124">?: operator</span></span>](conditional-operator.md)
