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
ms.openlocfilehash: 45af31d10d77f4c63b27b34595b97fdd11ef95a1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116132"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="e0e7f-103">Üye erişim işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="e0e7f-104">Bir tür üyesine eriştiğinizde aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="e0e7f-105">(üye erişimi): bir ad alanının veya türün üyesine erişmek için [ `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="e0e7f-106">[(dizi öğesi veya Dizin Oluşturucu erişimi): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="e0e7f-107">[ve (nullkoşulluişleçler):yalnızcabirişlenennulldeğilseüyeveyaöğeerişimişlemigerçekleştirmek`?[]`için `?.` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="e0e7f-108">(çağırma): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="e0e7f-109">(uçtan dizin): öğe konumunun bir sıranın sonundan olduğunu göstermek için [ `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="e0e7f-110">(Aralık): dizi öğeleri aralığını almak için kullanabileceğiniz bir dizin aralığı belirtmek için [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="e0e7f-111">Üye erişim işleci.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-111">Member access operator .</span></span>

<span data-ttu-id="e0e7f-112">Aşağıdaki örneklerde gösterildiği `.` gibi, belirteci, bir ad uzayı veya bir tür üyesine erişmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="e0e7f-113">Aşağıdaki `.` [bir yönerge`using` ](../keywords/using-directive.md) örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="e0e7f-114">Aşağıdaki `.` kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="e0e7f-115">Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [ `using` yönergesi](../keywords/using-directive.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="e0e7f-116">Aşağıdaki `.` kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için kullanın:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="e0e7f-117">Ayrıca, bir `.` [genişletme yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="e0e7f-118">Indexer işleci []</span><span class="sxs-lookup"><span data-stu-id="e0e7f-118">Indexer operator []</span></span>

<span data-ttu-id="e0e7f-119">Köşeli parantezler `[]`, genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="e0e7f-120">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="e0e7f-120">Array access</span></span>

<span data-ttu-id="e0e7f-121">Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="e0e7f-122">Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa, bir <xref:System.IndexOutOfRangeException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="e0e7f-123">Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="e0e7f-124">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0e7f-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="e0e7f-125">Dizin Oluşturucu erişimi</span><span class="sxs-lookup"><span data-stu-id="e0e7f-125">Indexer access</span></span>

<span data-ttu-id="e0e7f-126">Aşağıdaki örnek, Dizin Oluşturucu <xref:System.Collections.Generic.Dictionary%602> erişimini göstermek için .NET türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-126">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="e0e7f-127">Dizin oluşturucular, Kullanıcı tanımlı bir türün örneklerinin, dizi dizini oluşturma gibi benzer şekilde dizinlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="e0e7f-128">Tamsayı olması gereken dizi dizinlerinin aksine, Dizin Oluşturucu bağımsız değişkenleri herhangi bir türde olacak şekilde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-128">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="e0e7f-129">Dizin oluşturucular hakkında daha fazla bilgi için bkz. [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0e7f-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e0e7f-130">[] Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="e0e7f-130">Other usages of []</span></span>

<span data-ttu-id="e0e7f-131">İşaretçi öğesi erişimi hakkında daha fazla bilgi için, [işaretçi ilgili işleçler](pointer-related-operators.md) makalesinin [işaretçi öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="e0e7f-132">Ayrıca, [öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için köşeli parantezleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="e0e7f-133">Null koşullu işleçler?.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-133">Null-conditional operators ?.</span></span> <span data-ttu-id="e0e7f-134">'? []</span><span class="sxs-lookup"><span data-stu-id="e0e7f-134">and ?[]</span></span>

<span data-ttu-id="e0e7f-135">C# 6 ve sonraki sürümlerde kullanılabilir, null koşullu bir operatör, yalnızca o işlenen null olmayan `?.`bir değer olarak değerlendiriliyorsa `?[]`, bir üye erişimi, veya öğe erişimi, öğesini işleneninde uygular.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="e0e7f-136">İşlenen olarak `null`değerlendirilirse, işleci uygulamanın sonucu olur `null`.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="e0e7f-137">Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="e0e7f-138">Null koşullu işleçler kısa devre dışı.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="e0e7f-139">Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem dönerse `null`, zincir geri kalanı yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="e0e7f-140">`B` Aşağıdaki örnekte, `A` olarak `null` değerlendirilirse ve`C`değerlendirmesi `A` durumundahesaplanmaz:`null` `B`</span><span class="sxs-lookup"><span data-stu-id="e0e7f-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="e0e7f-141">Aşağıdaki örnek, `?.` ve `?[]` işleçlerinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="e0e7f-142">Yukarıdaki örnek, [null birleşim işlecinin](null-coalescing-operator.md)kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-142">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="e0e7f-143">Null-koşullu işlemin `null`sonucu olarak değerlendirmek için alternatif bir ifade sağlamak üzere null birleşim işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-143">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="e0e7f-144">İş parçacığı açısından güvenli temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="e0e7f-144">Thread-safe delegate invocation</span></span>

<span data-ttu-id="e0e7f-145">Bir temsilcinin null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için işlecinikullanın:`?.`</span><span class="sxs-lookup"><span data-stu-id="e0e7f-145">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="e0e7f-146">Bu kod, C# 5 veya daha önceki sürümlerde kullanacağınız aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-146">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="e0e7f-147">Çağırma işleci ()</span><span class="sxs-lookup"><span data-stu-id="e0e7f-147">Invocation operator ()</span></span>

<span data-ttu-id="e0e7f-148">Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak `()`veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-148">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="e0e7f-149">Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-149">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="e0e7f-150">[`new`](new-operator.md) İşleci ile bir [Oluşturucu](../../programming-guide/classes-and-structs/constructors.md) çağırdığınızda parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-150">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e0e7f-151">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="e0e7f-151">Other usages of ()</span></span>

<span data-ttu-id="e0e7f-152">Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamak için parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-152">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="e0e7f-153">Daha fazla bilgi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="e0e7f-153">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="e0e7f-154">Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-operator-), parantez de kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-154">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="e0e7f-155">Bitiş işlecinden Dizin ^</span><span class="sxs-lookup"><span data-stu-id="e0e7f-155">Index from end operator ^</span></span>

<span data-ttu-id="e0e7f-156">C# 8,0 ve sonraki sürümlerde `^` kullanılabilen işleç, öğe konumunun bir dizinin sonundan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-156">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="e0e7f-157">Bir uzunluk `length`sırası için, `^n` bir dizi başlangıcının sonuna `length - n` kadar olan öğesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-157">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="e0e7f-158">Örneğin, `^1` bir sıranın son öğesine işaret eder ve `^length` dizinin ilk öğesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-158">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="e0e7f-159">Yukarıdaki örnekte gösterildiği gibi, ifadesi `^e` <xref:System.Index?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-159">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e0e7f-160">İfadesinde `^e` `int` ,`e` sonucu örtük olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-160">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="e0e7f-161">Ayrıca bir dizin aralığı oluşturmak `^` için işlecini [Range işleciyle](#range-operator-) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-161">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="e0e7f-162">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="e0e7f-162">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="e0e7f-163">Aralık işleci..</span><span class="sxs-lookup"><span data-stu-id="e0e7f-163">Range operator ..</span></span>

<span data-ttu-id="e0e7f-164">C# 8,0 ve sonraki sürümlerde `..` kullanılabilen işleç, işlenen olarak bir dizin aralığının başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-164">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="e0e7f-165">Sol işlenen bir aralığın *kapsamlı* bir başlangıcı olur.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-165">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="e0e7f-166">Sağ işlenen bir aralığın *dışlamalı* bir sonu.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-166">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="e0e7f-167">Her iki işlenen de, aşağıdaki örnekte gösterildiği gibi, bir sıranın başından veya sonundan bir dizin olabilir:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-167">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="e0e7f-168">Yukarıdaki örnekte gösterildiği gibi, ifadesi `a..b` <xref:System.Range?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-168">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e0e7f-169">İfadesinde `a..b`, `a` `int` ve sonuçları`b` örtülü olarak veya<xref:System.Index>olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-169">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="e0e7f-170">Açık uçlu bir Aralık almak için `..` işlecin işlenenlerinden herhangi birini atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-170">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="e0e7f-171">`a..`eşdeğerdir`a..^0`</span><span class="sxs-lookup"><span data-stu-id="e0e7f-171">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="e0e7f-172">`..b`eşdeğerdir`0..b`</span><span class="sxs-lookup"><span data-stu-id="e0e7f-172">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="e0e7f-173">`..`eşdeğerdir`0..^0`</span><span class="sxs-lookup"><span data-stu-id="e0e7f-173">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="e0e7f-174">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="e0e7f-174">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e0e7f-175">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="e0e7f-175">Operator overloadability</span></span>

<span data-ttu-id="e0e7f-176">,,, Ve`..` işleçleri aşırı yüklenemez. `^` `()` `.`</span><span class="sxs-lookup"><span data-stu-id="e0e7f-176">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="e0e7f-177">İşleci `[]` , aşırı yüklenebilir olmayan bir işleç olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-177">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="e0e7f-178">Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-178">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0e7f-179">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e0e7f-179">C# language specification</span></span>

<span data-ttu-id="e0e7f-180">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="e0e7f-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e0e7f-181">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="e0e7f-181">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="e0e7f-182">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="e0e7f-182">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="e0e7f-183">Null-koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="e0e7f-183">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="e0e7f-184">Çağırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e0e7f-184">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="e0e7f-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0e7f-185">See also</span></span>

- [<span data-ttu-id="e0e7f-186">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="e0e7f-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e0e7f-187">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e0e7f-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="e0e7f-188">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="e0e7f-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="e0e7f-189">:: işleci</span><span class="sxs-lookup"><span data-stu-id="e0e7f-189">:: operator</span></span>](namespace-alias-qualifier.md)
