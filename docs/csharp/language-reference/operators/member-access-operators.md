---
title: Üye erişim işleçleri- C# başvuru
description: Tür üyelerine C# erişmek için kullanabileceğiniz işleçler hakkında bilgi edinin.
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
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
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: ab69514e324c632f546957b2ddb58e073ca0154e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239256"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="cba39-103">Üye erişim işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="cba39-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="cba39-104">Bir tür üyesine eriştiğinizde aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cba39-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="cba39-105">[`.` (üye erişimi)](#member-access-operator-): bir ad alanının veya türün üyesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="cba39-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="cba39-106">[`[]` (dizi öğesi veya Dizin Oluşturucu erişimi)](#indexer-operator-): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için</span><span class="sxs-lookup"><span data-stu-id="cba39-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="cba39-107">[`?.` ve `?[]` (null-koşullu işleçler)](#null-conditional-operators--and-): yalnızca bir işlenen null değilse bir üye veya öğe erişim işlemi gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="cba39-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="cba39-108">[`()` (çağırma)](#invocation-operator-): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="cba39-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="cba39-109">[`^` (uçtan dizin)](#index-from-end-operator-): öğe konumunun bir sıranın sonundan olduğunu göstermek için</span><span class="sxs-lookup"><span data-stu-id="cba39-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="cba39-110">[`..` (Aralık)](#range-operator-): dizi öğeleri aralığını almak için kullanabileceğiniz bir dizin aralığı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="cba39-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="cba39-111">Üye erişim işleci.</span><span class="sxs-lookup"><span data-stu-id="cba39-111">Member access operator .</span></span>

<span data-ttu-id="cba39-112">Aşağıdaki örneklerde gösterildiği gibi, bir ad alanı veya tür üyesine erişmek için `.` belirtecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="cba39-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="cba39-113">Bir [`using` yönergesinin](../keywords/using-directive.md) aşağıdaki örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için `.` kullanın:</span><span class="sxs-lookup"><span data-stu-id="cba39-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="cba39-114">Aşağıdaki kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için `.` kullanın:</span><span class="sxs-lookup"><span data-stu-id="cba39-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="cba39-115">Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [`using` yönergesi](../keywords/using-directive.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="cba39-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="cba39-116">Aşağıdaki kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için `.` kullanın:</span><span class="sxs-lookup"><span data-stu-id="cba39-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="cba39-117">[Uzantı yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için `.` de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba39-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="cba39-118">Indexer işleci []</span><span class="sxs-lookup"><span data-stu-id="cba39-118">Indexer operator []</span></span>

<span data-ttu-id="cba39-119">Köşeli ayraçlar `[]`, genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cba39-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="cba39-120">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="cba39-120">Array access</span></span>

<span data-ttu-id="cba39-121">Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cba39-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="cba39-122">Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa bir <xref:System.IndexOutOfRangeException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cba39-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="cba39-123">Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba39-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="cba39-124">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="cba39-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="cba39-125">Dizin Oluşturucu erişimi</span><span class="sxs-lookup"><span data-stu-id="cba39-125">Indexer access</span></span>

<span data-ttu-id="cba39-126">Aşağıdaki örnek, Dizin Oluşturucu erişimini göstermek için .NET <xref:System.Collections.Generic.Dictionary%602> türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="cba39-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="cba39-127">Dizin oluşturucular, Kullanıcı tanımlı bir türün örneklerinin, dizi dizini oluşturma gibi benzer şekilde dizinlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cba39-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="cba39-128">Tamsayı olması gereken dizi dizinlerinin aksine, Dizin Oluşturucu parametreleri herhangi bir türde olacak şekilde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cba39-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="cba39-129">Dizin oluşturucular hakkında daha fazla bilgi için bkz. [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="cba39-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="cba39-130">[] Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="cba39-130">Other usages of []</span></span>

<span data-ttu-id="cba39-131">İşaretçi öğesi erişimi hakkında daha fazla bilgi için, [işaretçi ilgili işleçler](pointer-related-operators.md) makalesinin [işaretçi öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cba39-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="cba39-132">Ayrıca, [öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için köşeli parantezleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cba39-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="cba39-133">Null koşullu işleçler?.</span><span class="sxs-lookup"><span data-stu-id="cba39-133">Null-conditional operators ?.</span></span> <span data-ttu-id="cba39-134">'? []</span><span class="sxs-lookup"><span data-stu-id="cba39-134">and ?[]</span></span>

<span data-ttu-id="cba39-135">C# 6 ve sonrasında kullanılabilir, null koşullu bir operatör, yalnızca bu işlenen null olmayan bir değer olarak değerlendiriliyorsa, bir [üye erişimi](#member-access-operator-), `?.`ya da [öğe erişimi](#indexer-operator-), `?[]`, işlem için uygular. Aksi takdirde, `null`döndürür.</span><span class="sxs-lookup"><span data-stu-id="cba39-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-operator-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="cba39-136">Yani</span><span class="sxs-lookup"><span data-stu-id="cba39-136">That is,</span></span>

- <span data-ttu-id="cba39-137">`a` `null`değerlendirilirse, `a?.x` veya `a?[x]` sonucu `null`.</span><span class="sxs-lookup"><span data-stu-id="cba39-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="cba39-138">`a` null olmayan olarak değerlendirilirse, `a?.x` veya `a?[x]` sonucu sırasıyla `a.x` veya `a[x]`sonucuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cba39-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="cba39-139">`a.x` veya `a[x]` bir özel durum oluşturursa, `a?.x` veya `a?[x]` null olmayan `a`için aynı özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cba39-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="cba39-140">Örneğin, `a` null olmayan bir dizi örneğidir ve `x` `a`sınırlarının dışındaysa `a?[x]` <xref:System.IndexOutOfRangeException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cba39-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="cba39-141">Null koşullu işleçler kısa devre dışı.</span><span class="sxs-lookup"><span data-stu-id="cba39-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="cba39-142">Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem `null`döndürürse, zincirin geri kalanı yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="cba39-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="cba39-143">Aşağıdaki örnekte, `A` `null` değerlendirilirse `B` değerlendirilmez ve `A` veya `B` `null`olarak değerlendirilirse `C` değerlendirilmez:</span><span class="sxs-lookup"><span data-stu-id="cba39-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="cba39-144">Aşağıdaki örnek, `?.` ve `?[]` işleçlerinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="cba39-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="cba39-145">Yukarıdaki örnek ayrıca null [birleşim işlecini `??`](null-coalescing-operator.md) , null koşullu bir işlemin sonucu `null`sonucunu değerlendirmek üzere alternatif bir ifade belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cba39-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="cba39-146">Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="cba39-146">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="cba39-147">İş parçacığı açısından güvenli temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="cba39-147">Thread-safe delegate invocation</span></span>

<span data-ttu-id="cba39-148">Bir temsilcinin null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için `?.` işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="cba39-148">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="cba39-149">Bu kod, C# 5 veya daha önceki sürümlerde kullanacağınız aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="cba39-149">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="cba39-150">Çağırma işleci ()</span><span class="sxs-lookup"><span data-stu-id="cba39-150">Invocation operator ()</span></span>

<span data-ttu-id="cba39-151">Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantez, `()`kullanın.</span><span class="sxs-lookup"><span data-stu-id="cba39-151">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="cba39-152">Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="cba39-152">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="cba39-153">Ayrıca, [`new`](new-operator.md) işleçle bir [Oluşturucu](../../programming-guide/classes-and-structs/constructors.md) çağırdığınızda parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba39-153">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="cba39-154">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="cba39-154">Other usages of ()</span></span>

<span data-ttu-id="cba39-155">Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamak için parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba39-155">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="cba39-156">Daha fazla bilgi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="cba39-156">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="cba39-157">Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-operator-), parantez de kullanır.</span><span class="sxs-lookup"><span data-stu-id="cba39-157">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="cba39-158">Bitiş işlecinden Dizin ^</span><span class="sxs-lookup"><span data-stu-id="cba39-158">Index from end operator ^</span></span>

<span data-ttu-id="cba39-159">C# 8,0 ve sonraki sürümlerde kullanılabilen `^` işleci, öğe konumunun sıranın sonundan itibaren olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cba39-159">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="cba39-160">`length`bir dizi Uzunluk için, `^n` bir sıranın başından itibaren `length - n` olan öğeye işaret eder.</span><span class="sxs-lookup"><span data-stu-id="cba39-160">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="cba39-161">Örneğin `^1`, sıranın son öğesine işaret eder ve `^length` bir dizinin ilk öğesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="cba39-161">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="cba39-162">Yukarıdaki örnekte gösterildiği gibi ifade `^e` <xref:System.Index?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="cba39-162">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="cba39-163">İfade `^e`, `e` sonucu `int`örtülü olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cba39-163">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="cba39-164">Ayrıca, dizin aralığı oluşturmak için `^` işlecini [Aralık işleciyle](#range-operator-) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba39-164">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="cba39-165">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="cba39-165">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="cba39-166">Aralık işleci..</span><span class="sxs-lookup"><span data-stu-id="cba39-166">Range operator ..</span></span>

<span data-ttu-id="cba39-167">C# 8,0 ve sonraki sürümlerde kullanılabilen `..` işleci, işlenen bir dizin aralığının başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cba39-167">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="cba39-168">Sol işlenen bir aralığın *kapsamlı* bir başlangıcı olur.</span><span class="sxs-lookup"><span data-stu-id="cba39-168">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="cba39-169">Sağ işlenen bir aralığın *dışlamalı* bir sonu.</span><span class="sxs-lookup"><span data-stu-id="cba39-169">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="cba39-170">Her iki işlenen de, aşağıdaki örnekte gösterildiği gibi, bir sıranın başından veya sonundan bir dizin olabilir:</span><span class="sxs-lookup"><span data-stu-id="cba39-170">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="cba39-171">Yukarıdaki örnekte gösterildiği gibi ifade `a..b` <xref:System.Range?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="cba39-171">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="cba39-172">İfade `a..b`, `a` ve `b` sonuçları `int` veya <xref:System.Index>örtülü olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cba39-172">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="cba39-173">Açık uçlu bir Aralık almak için `..` işlecinin herhangi bir işlenenini atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cba39-173">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="cba39-174">`a..` `a..^0` eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="cba39-174">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="cba39-175">`..b` `0..b` eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="cba39-175">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="cba39-176">`..` `0..^0` eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="cba39-176">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="cba39-177">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="cba39-177">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="cba39-178">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="cba39-178">Operator overloadability</span></span>

<span data-ttu-id="cba39-179">`.`, `()`, `^`ve `..` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="cba39-179">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="cba39-180">`[]` işleci de aşırı yüklenebilir olmayan bir operatör olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cba39-180">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="cba39-181">Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="cba39-181">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cba39-182">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="cba39-182">C# language specification</span></span>

<span data-ttu-id="cba39-183">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="cba39-183">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="cba39-184">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="cba39-184">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="cba39-185">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="cba39-185">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="cba39-186">Null-koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="cba39-186">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="cba39-187">Çağırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="cba39-187">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="cba39-188">Dizinler ve aralıklar hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="cba39-188">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cba39-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cba39-189">See also</span></span>

- [<span data-ttu-id="cba39-190">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="cba39-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cba39-191">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="cba39-191">C# operators</span></span>](index.md)
- [<span data-ttu-id="cba39-192">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="cba39-192">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="cba39-193">:: işleci</span><span class="sxs-lookup"><span data-stu-id="cba39-193">:: operator</span></span>](namespace-alias-qualifier.md)
