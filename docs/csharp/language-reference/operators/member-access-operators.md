---
title: Üye erişim işleçleri ve ifadeleri-C# başvurusu
description: Tür üyelerine erişmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 04/17/2020
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
ms.openlocfilehash: 86c8cce79e447bee638e1c5c7cb2fdbc64f630f3
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595903"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="17b35-103">Üye erişim işleçleri ve ifadeleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="17b35-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="17b35-104">Bir tür üyesine eriştiğinizde aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b35-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="17b35-105">(üye erişimi): bir ad alanının veya türün üyesine erişmek için [ `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="17b35-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="17b35-106">[(dizi öğesi veya Dizin Oluşturucu erişimi): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="17b35-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="17b35-107">[ve `?[]` null koşullu işleçler): yalnızca bir işlenen null değilse üye veya öğe erişim işlemi `?.` ](#null-conditional-operators--and-)gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="17b35-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="17b35-108">(çağırma): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="17b35-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="17b35-109">(uçtan dizin): öğe konumunun bir sıranın sonundan olduğunu göstermek için [ `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="17b35-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="17b35-110">(Aralık): dizi öğeleri aralığını almak için kullanabileceğiniz bir dizin aralığı belirtmek için [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="17b35-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="17b35-111">Üye erişim ifadesi.</span><span class="sxs-lookup"><span data-stu-id="17b35-111">Member access expression .</span></span>

<span data-ttu-id="17b35-112">Aşağıdaki örneklerde gösterildiği `.` gibi, belirteci, bir ad uzayı veya bir tür üyesine erişmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b35-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="17b35-113">Aşağıdaki `.` bir [ `using` yönerge](../keywords/using-directive.md) örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="17b35-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="17b35-114">Aşağıdaki `.` kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="17b35-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="17b35-115">Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [ `using` yönergesi](../keywords/using-directive.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="17b35-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="17b35-116">Aşağıdaki `.` kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için kullanın:</span><span class="sxs-lookup"><span data-stu-id="17b35-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="17b35-117">Ayrıca, bir `.` [genişletme yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b35-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="17b35-118">Indexer işleci []</span><span class="sxs-lookup"><span data-stu-id="17b35-118">Indexer operator []</span></span>

<span data-ttu-id="17b35-119">Köşeli parantezler `[]`, genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17b35-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="17b35-120">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="17b35-120">Array access</span></span>

<span data-ttu-id="17b35-121">Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="17b35-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="17b35-122">Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa, bir <xref:System.IndexOutOfRangeException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="17b35-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="17b35-123">Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b35-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="17b35-124">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="17b35-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="17b35-125">Dizin Oluşturucu erişimi</span><span class="sxs-lookup"><span data-stu-id="17b35-125">Indexer access</span></span>

<span data-ttu-id="17b35-126">Aşağıdaki örnek, Dizin Oluşturucu erişimini <xref:System.Collections.Generic.Dictionary%602> göstermek için .NET türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="17b35-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="17b35-127">Dizin oluşturucular, Kullanıcı tanımlı bir türün örneklerinin, dizi dizini oluşturma gibi benzer şekilde dizinlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="17b35-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="17b35-128">Tamsayı olması gereken dizi dizinlerinin aksine, Dizin Oluşturucu parametreleri herhangi bir türde olacak şekilde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="17b35-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="17b35-129">Dizin oluşturucular hakkında daha fazla bilgi için bkz. [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="17b35-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="17b35-130">[] Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="17b35-130">Other usages of []</span></span>

<span data-ttu-id="17b35-131">İşaretçi öğesi erişimi hakkında daha fazla bilgi için, [işaretçi ilgili işleçler](pointer-related-operators.md) makalesinin [işaretçi öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="17b35-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="17b35-132">Ayrıca, [öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için köşeli parantezleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b35-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="17b35-133">Null koşullu işleçler?.</span><span class="sxs-lookup"><span data-stu-id="17b35-133">Null-conditional operators ?.</span></span> <span data-ttu-id="17b35-134">'? []</span><span class="sxs-lookup"><span data-stu-id="17b35-134">and ?[]</span></span>

<span data-ttu-id="17b35-135">C# 6 ve üzeri sürümlerde kullanılabilir, null koşullu bir operatör, yalnızca o işlenenin null olmayan `?.`olarak değerlendiriliyorsa işlenen için `?[]`bir [üye erişimi](#member-access-expression-), veya [öğe erişimi](#indexer-operator-)uygular; Aksi takdirde, döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="17b35-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="17b35-136">Yani</span><span class="sxs-lookup"><span data-stu-id="17b35-136">That is,</span></span>

- <span data-ttu-id="17b35-137">Olarak `a` `null`değerlendirilirse, `a?.x` veya `a?[x]` olur. `null`</span><span class="sxs-lookup"><span data-stu-id="17b35-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="17b35-138">Null `a` olmayan `a?.x` olarak değerlendirilirse, `a?[x]` veya sonucu, sırasıyla `a.x` veya `a[x]`sonucu ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="17b35-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="17b35-139">`a.x` Ya `a[x]` da bir özel durum oluşturursa `a?.x` ya `a?[x]` da null `a`olmayan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17b35-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="17b35-140">`a` Örneğin, null olmayan bir dizi örneğidir ve `x` sınırları `a` `a?[x]` dışındaysa bir <xref:System.IndexOutOfRangeException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17b35-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="17b35-141">Null koşullu işleçler kısa devre dışı.</span><span class="sxs-lookup"><span data-stu-id="17b35-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="17b35-142">Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem dönerse `null`, zincir geri kalanı yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="17b35-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="17b35-143">Aşağıdaki `B` örnekte, olarak `A` `null` değerlendirilirse ve `C` değerlendirmesi `A` `B` durumunda hesaplanmaz: `null`</span><span class="sxs-lookup"><span data-stu-id="17b35-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="17b35-144">Aşağıdaki örnek, `?.` ve `?[]` işleçlerinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="17b35-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="17b35-145">Yukarıdaki örnek, null-koşullu bir işlemin sonucu olarak değerlendirmek için alternatif bir ifade belirtmek üzere [null birleşim işlecini `??` ](null-coalescing-operator.md) de kullanır. `null`</span><span class="sxs-lookup"><span data-stu-id="17b35-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="17b35-146">`a.x` Ya `a[x]` `T`da null yapılamayan bir değer türü ise `a?.x` veya `a?[x]` buna karşılık gelen [null atanabilir değer türüdür](../builtin-types/nullable-value-types.md) `T?`.</span><span class="sxs-lookup"><span data-stu-id="17b35-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="17b35-147">Türünde `T`bir ifadeye ihtiyacınız varsa, aşağıdaki örnekte gösterildiği gibi null birleşim işlecini `??` null koşullu ifadeye uygulayın:</span><span class="sxs-lookup"><span data-stu-id="17b35-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="17b35-148">`??` Önceki örnekte, işlecini kullanmıyorsanız, `numbers?.Length < 2` `false` ne zaman `numbers` olduğunu `null`değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="17b35-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="17b35-149">Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="17b35-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

> [!NOTE]
> <span data-ttu-id="17b35-150">C# 8 ' de, null koşullu işleçler beklenmedik bir şekilde [null-forverme işleciyle](null-forgiving.md) etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="17b35-150">In C# 8, the null-conditional operators interacts with the [null-forgiving operator](null-forgiving.md) in an unexpected way.</span></span> <span data-ttu-id="17b35-151">Örneğin, ifadesi `x?.y!.z` olarak `(x?.y)!.z`ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="17b35-151">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="17b35-152">Bu yorum `z` nedeniyle,, olsa bile `x` değerlendirilir `null`, bu da bir <xref:System.NullReferenceException>ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="17b35-152">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="17b35-153">İş parçacığı açısından güvenli temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="17b35-153">Thread-safe delegate invocation</span></span>

<span data-ttu-id="17b35-154">Bir temsilcinin `?.` null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="17b35-154">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="17b35-155">Bu kod, C# 5 veya daha önceki bir sürümünde kullanacağınız aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="17b35-155">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="17b35-156">Bu, yalnızca null `handler` olmayan bir değer çağrılmasını sağlamak için iş parçacığı açısından güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="17b35-156">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="17b35-157">Temsilci örnekleri sabit olduğu için hiçbir iş parçacığı `handler` yerel değişken tarafından başvurulan değeri değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="17b35-157">Because delegate instances are immutable, no thread can change the value referenced by the `handler` local variable.</span></span> <span data-ttu-id="17b35-158">Özellikle, başka bir iş parçacığı tarafından yürütülen `PropertyChanged` kod, olaydan abone olmaya devam eder ve `PropertyChanged` `null` `handler` çağrılır, tarafından `handler` başvurulan değer etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="17b35-158">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the value referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="17b35-159">`?.` İşleci sol taraftaki işlenenini birden çok kez değerlendirir ve null olmayan olarak doğrulandıktan sonra olarak `null` değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="17b35-159">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="17b35-160">Çağırma ifadesi ()</span><span class="sxs-lookup"><span data-stu-id="17b35-160">Invocation expression ()</span></span>

<span data-ttu-id="17b35-161">Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak `()`veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="17b35-161">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="17b35-162">Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="17b35-162">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="17b35-163">İşleci ile bir Oluşturucu çağırdığınızda parantezleri de kullanabilirsiniz. [constructor](../../programming-guide/classes-and-structs/constructors.md) [`new`](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="17b35-163">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="17b35-164">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="17b35-164">Other usages of ()</span></span>

<span data-ttu-id="17b35-165">Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamak için parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b35-165">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="17b35-166">Daha fazla bilgi için bkz. [C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="17b35-166">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="17b35-167">Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-expression), parantez de kullanır.</span><span class="sxs-lookup"><span data-stu-id="17b35-167">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="17b35-168">Bitiş işlecinden Dizin ^</span><span class="sxs-lookup"><span data-stu-id="17b35-168">Index from end operator ^</span></span>

<span data-ttu-id="17b35-169">C# 8,0 ve üzeri sürümlerde kullanılabilen `^` işleç, öğe konumunun bir dizinin sonundan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="17b35-169">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="17b35-170">Bir uzunluk `length`sırası için, `^n` bir dizi başlangıcının sonuna `length - n` kadar olan öğesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="17b35-170">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="17b35-171">Örneğin, `^1` bir sıranın son öğesine işaret eder ve `^length` dizinin ilk öğesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="17b35-171">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="17b35-172">Yukarıdaki örnekte gösterildiği gibi, ifadesi `^e` <xref:System.Index?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="17b35-172">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="17b35-173">İfadesinde `^e`, sonucu örtük olarak dönüştürülebilir `e` olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="17b35-173">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="17b35-174">Ayrıca bir dizin aralığı oluşturmak `^` için işleci [Aralık işleciyle](#range-operator-) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17b35-174">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="17b35-175">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="17b35-175">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="17b35-176">Aralık işleci..</span><span class="sxs-lookup"><span data-stu-id="17b35-176">Range operator ..</span></span>

<span data-ttu-id="17b35-177">C# 8,0 ve üzeri sürümlerde kullanılabilen `..` işleç, işlenen bir dizin aralığının başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="17b35-177">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="17b35-178">Sol işlenen bir aralığın *kapsamlı* bir başlangıcı olur.</span><span class="sxs-lookup"><span data-stu-id="17b35-178">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="17b35-179">Sağ işlenen bir aralığın *dışlamalı* bir sonu.</span><span class="sxs-lookup"><span data-stu-id="17b35-179">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="17b35-180">Her iki işlenen de, aşağıdaki örnekte gösterildiği gibi, bir sıranın başından veya sonundan bir dizin olabilir:</span><span class="sxs-lookup"><span data-stu-id="17b35-180">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="17b35-181">Yukarıdaki örnekte gösterildiği gibi, ifadesi `a..b` <xref:System.Range?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="17b35-181">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="17b35-182">`a..b`İfadesinde `a` , `b` ve sonuçları örtülü olarak veya `int` <xref:System.Index>olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17b35-182">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="17b35-183">Açık uçlu bir Aralık almak için `..` işlecin işlenenlerinden herhangi birini atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17b35-183">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="17b35-184">`a..`eşdeğerdir`a..^0`</span><span class="sxs-lookup"><span data-stu-id="17b35-184">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="17b35-185">`..b`eşdeğerdir`0..b`</span><span class="sxs-lookup"><span data-stu-id="17b35-185">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="17b35-186">`..`eşdeğerdir`0..^0`</span><span class="sxs-lookup"><span data-stu-id="17b35-186">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="17b35-187">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="17b35-187">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="17b35-188">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="17b35-188">Operator overloadability</span></span>

<span data-ttu-id="17b35-189">`.`, `()`, `^`, Ve `..` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="17b35-189">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="17b35-190">İşleci `[]` , aşırı yüklenebilir olmayan bir işleç olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="17b35-190">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="17b35-191">Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="17b35-191">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17b35-192">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="17b35-192">C# language specification</span></span>

<span data-ttu-id="17b35-193">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="17b35-193">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="17b35-194">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="17b35-194">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="17b35-195">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="17b35-195">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="17b35-196">Null-koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="17b35-196">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="17b35-197">Çağırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="17b35-197">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="17b35-198">Dizinler ve aralıklar hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="17b35-198">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17b35-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17b35-199">See also</span></span>

- [<span data-ttu-id="17b35-200">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="17b35-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="17b35-201">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="17b35-201">C# operators</span></span>](index.md)
- [<span data-ttu-id="17b35-202">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="17b35-202">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="17b35-203">:: işleci</span><span class="sxs-lookup"><span data-stu-id="17b35-203">:: operator</span></span>](namespace-alias-qualifier.md)
