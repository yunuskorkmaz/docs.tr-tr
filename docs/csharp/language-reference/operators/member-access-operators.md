---
title: Üye erişim işleçleri- C# başvuru
description: Tür üyelerine C# erişmek için kullanabileceğiniz işleçler hakkında bilgi edinin.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
ms.openlocfilehash: 763fdb442fa0037dafd51f89badd04436e24d254
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566824"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="190a9-103">Üye erişim işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="190a9-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="190a9-104">Bir tür üyesine eriştiğinizde aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="190a9-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="190a9-105">(üye erişimi): bir ad alanının veya türün üyesine erişmek için [ `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="190a9-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="190a9-106">[(dizi öğesi veya Dizin Oluşturucu erişimi): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="190a9-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="190a9-107">[ve (nullkoşulluişleçler):yalnızcabirişlenennulldeğilseüyeveyaöğeerişimişlemigerçekleştirmek`?[]`için `?.` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="190a9-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="190a9-108">(çağırma): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="190a9-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="190a9-109">Üye erişim işleci.</span><span class="sxs-lookup"><span data-stu-id="190a9-109">Member access operator .</span></span>

<span data-ttu-id="190a9-110">Aşağıdaki örneklerde gösterildiği `.` gibi, belirteci, bir ad uzayı veya bir tür üyesine erişmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="190a9-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="190a9-111">Aşağıdaki `.` [bir yönerge`using` ](../keywords/using-directive.md) örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="190a9-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="190a9-112">Aşağıdaki `.` kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="190a9-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="190a9-113">Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [ `using` yönergesi](../keywords/using-directive.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="190a9-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="190a9-114">Aşağıdaki `.` kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için kullanın:</span><span class="sxs-lookup"><span data-stu-id="190a9-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="190a9-115">Ayrıca, bir `.` [genişletme yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190a9-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="190a9-116">Indexer işleci []</span><span class="sxs-lookup"><span data-stu-id="190a9-116">Indexer operator []</span></span>

<span data-ttu-id="190a9-117">Köşeli parantezler `[]`, genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="190a9-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="190a9-118">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="190a9-118">Array access</span></span>

<span data-ttu-id="190a9-119">Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="190a9-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="190a9-120">Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa, bir <xref:System.IndexOutOfRangeException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="190a9-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="190a9-121">Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190a9-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="190a9-122">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="190a9-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="190a9-123">Dizin Oluşturucu erişimi</span><span class="sxs-lookup"><span data-stu-id="190a9-123">Indexer access</span></span>

<span data-ttu-id="190a9-124">Aşağıdaki örnek, Dizin Oluşturucu <xref:System.Collections.Generic.Dictionary%602> erişimini göstermek için .NET türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="190a9-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="190a9-125">Dizin oluşturucular, Kullanıcı tanımlı bir türün örneklerinin, dizi dizini oluşturma gibi benzer şekilde dizinlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="190a9-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="190a9-126">Tamsayı olması gereken dizi dizinlerinin aksine, Dizin Oluşturucu bağımsız değişkenleri herhangi bir türde olacak şekilde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="190a9-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="190a9-127">Dizin oluşturucular hakkında daha fazla bilgi için bkz. [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="190a9-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="190a9-128">[] Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="190a9-128">Other usages of []</span></span>

<span data-ttu-id="190a9-129">İşaretçi öğesi erişimi hakkında daha fazla bilgi için, [işaretçi ilgili işleçler](pointer-related-operators.md) makalesinin [işaretçi öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="190a9-129">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="190a9-130">Ayrıca, [öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için köşeli parantezleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="190a9-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="190a9-131">Null koşullu işleçler?.</span><span class="sxs-lookup"><span data-stu-id="190a9-131">Null-conditional operators ?.</span></span> <span data-ttu-id="190a9-132">'? []</span><span class="sxs-lookup"><span data-stu-id="190a9-132">and ?[]</span></span>

<span data-ttu-id="190a9-133">C# 6 ve sonraki sürümlerde kullanılabilir, null koşullu bir operatör, yalnızca o işlenen null olmayan `?.`bir değer olarak değerlendiriliyorsa `?[]`, bir üye erişimi, veya öğe erişimi, öğesini işleneninde uygular.</span><span class="sxs-lookup"><span data-stu-id="190a9-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="190a9-134">İşlenen olarak `null`değerlendirilirse, işleci uygulamanın sonucu olur `null`.</span><span class="sxs-lookup"><span data-stu-id="190a9-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="190a9-135">Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="190a9-135">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="190a9-136">Null koşullu işleçler kısa devre dışı.</span><span class="sxs-lookup"><span data-stu-id="190a9-136">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="190a9-137">Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem dönerse `null`, zincir geri kalanı yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="190a9-137">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="190a9-138">`B` Aşağıdaki örnekte, `A` olarak `null` değerlendirilirse ve`C`değerlendirmesi `A` durumundahesaplanmaz:`null` `B`</span><span class="sxs-lookup"><span data-stu-id="190a9-138">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="190a9-139">Aşağıdaki örnek, `?.` ve `?[]` işleçlerinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="190a9-139">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="190a9-140">Yukarıdaki örnek, [null birleşim işlecinin](null-coalescing-operator.md)kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="190a9-140">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="190a9-141">Null-koşullu işlemin `null`sonucu olarak değerlendirmek için alternatif bir ifade sağlamak üzere null birleşim işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190a9-141">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="190a9-142">İş parçacığı açısından güvenli temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="190a9-142">Thread-safe delegate invocation</span></span>

<span data-ttu-id="190a9-143">Bir temsilcinin null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için işlecinikullanın:`?.`</span><span class="sxs-lookup"><span data-stu-id="190a9-143">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="190a9-144">Bu kod, C# 5 veya daha önceki sürümlerde kullanacağınız aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="190a9-144">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="190a9-145">Çağırma işleci ()</span><span class="sxs-lookup"><span data-stu-id="190a9-145">Invocation operator ()</span></span>

<span data-ttu-id="190a9-146">Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak `()`veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="190a9-146">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="190a9-147">Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="190a9-147">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="190a9-148">[`new`](new-operator.md) İşleci ile bir [Oluşturucu](../../programming-guide/classes-and-structs/constructors.md) çağırdığınızda parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190a9-148">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="190a9-149">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="190a9-149">Other usages of ()</span></span>

<span data-ttu-id="190a9-150">Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı belirtmek için parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190a9-150">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="190a9-151">Daha fazla bilgi için [işleçler](../../programming-guide/statements-expressions-operators/operators.md) makalesinin [parantezler ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="190a9-151">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="190a9-152">Öncelik düzeyine göre sıralanan işleçlerin listesi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="190a9-152">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

<span data-ttu-id="190a9-153">Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-operator-), parantez de kullanır.</span><span class="sxs-lookup"><span data-stu-id="190a9-153">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="190a9-154">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="190a9-154">Operator overloadability</span></span>

<span data-ttu-id="190a9-155">`.` Ve`()` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="190a9-155">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="190a9-156">İşleci `[]` , aşırı yüklenebilir olmayan bir işleç olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="190a9-156">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="190a9-157">Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="190a9-157">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="190a9-158">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="190a9-158">C# language specification</span></span>

<span data-ttu-id="190a9-159">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="190a9-159">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="190a9-160">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="190a9-160">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="190a9-161">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="190a9-161">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="190a9-162">Null-koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="190a9-162">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="190a9-163">Çağırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="190a9-163">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="190a9-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="190a9-164">See also</span></span>

- [<span data-ttu-id="190a9-165">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="190a9-165">C# reference</span></span>](../index.md)
- [<span data-ttu-id="190a9-166">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="190a9-166">C# operators</span></span>](index.md)
- [<span data-ttu-id="190a9-167">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="190a9-167">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="190a9-168">:: işleci</span><span class="sxs-lookup"><span data-stu-id="190a9-168">:: operator</span></span>](namespace-alias-qualifier.md)
