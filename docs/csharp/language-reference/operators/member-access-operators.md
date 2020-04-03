---
title: Üye erişim işleçleri ve ifadeleri - C# başvurusu
description: Tür üyelerine erişmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 03/31/2020
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
ms.openlocfilehash: a132e527deadcffb4826c1965987fc09da470a09
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635310"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="6f61e-103">Üye erişim işleçleri ve ifadeleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6f61e-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="6f61e-104">Bir tür üyesine erişirken aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f61e-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="6f61e-105">(üye erişimi) : bir ad alanı nın veya bir türün üyesine erişmek için [ `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="6f61e-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="6f61e-106">[(dizi öğesi veya dizinleyici erişimi) : bir dizi öğesi veya bir tür dizinleyici erişmek için `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="6f61e-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="6f61e-107">ve (null-conditional operators) : bir üye veya eleman erişim işlemi gerçekleştirmek için sadece bir operand null olmayan [ `?.` `?[]` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="6f61e-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="6f61e-108">(çağırma) : erişilen bir yöntemi çağırmak veya bir temsilci çağırmak [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="6f61e-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="6f61e-109">(dizini sona) : eleman konumunun bir dizinin sonundan geldiğini belirtmek için [ `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="6f61e-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="6f61e-110">(aralık) : dizi öğeleri aralığı elde etmek için kullanabileceğiniz bir dizi endeks belirtmek için [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="6f61e-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="6f61e-111">Üye erişim ifadesi .</span><span class="sxs-lookup"><span data-stu-id="6f61e-111">Member access expression .</span></span>

<span data-ttu-id="6f61e-112">Aşağıdaki örneklerde gösterildiği gibi, bir ad alanı nın veya bir türün üyesine erişmek için `.` belirteci kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="6f61e-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="6f61e-113">Bir `.` [ `using` yönergeörneğinin](../keywords/using-directive.md) aşağıdaki örneğinde görüldüğü gibi, ad alanı içinde iç içe bir ad alanına erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="6f61e-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="6f61e-114">Aşağıdaki `.` kodun gösterdiği gibi, ad alanı içindeki bir türe erişmek için nitelikli bir *ad* oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="6f61e-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="6f61e-115">Nitelikli adlardan isteğe bağlı olarak yararlanmak için bir [ `using` yönerge](../keywords/using-directive.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="6f61e-116">Aşağıdaki `.` kodun gösterdiği gibi, statik ve statik olmayan [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members)erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="6f61e-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="6f61e-117">Ayrıca bir `.` [uzantı yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f61e-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="6f61e-118">Dizinleyici operatörü []</span><span class="sxs-lookup"><span data-stu-id="6f61e-118">Indexer operator []</span></span>

<span data-ttu-id="6f61e-119">Kare ayraçlar, `[]`genellikle dizi, dizinleyici veya işaretçi öğesi erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f61e-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="6f61e-120">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="6f61e-120">Array access</span></span>

<span data-ttu-id="6f61e-121">Aşağıdaki örnek, dizi öğelerine nasıl erişilenleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="6f61e-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="6f61e-122">Bir dizi dizi dizi dizinin ilgili boyutunun sınırları <xref:System.IndexOutOfRangeException> dışında ysa, bir atılır.</span><span class="sxs-lookup"><span data-stu-id="6f61e-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="6f61e-123">Önceki örnekte de görüldüğü gibi, bir dizi türünü beyan ettiğinizde veya bir dizi örneğini anında yaptığınızda kare ayraçlar da kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f61e-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="6f61e-124">Diziler hakkında daha fazla bilgi için [Diziler'e](../../programming-guide/arrays/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="6f61e-125">Dizinleyici erişimi</span><span class="sxs-lookup"><span data-stu-id="6f61e-125">Indexer access</span></span>

<span data-ttu-id="6f61e-126">Aşağıdaki örnek, dizinleyici erişimini göstermek için .NET <xref:System.Collections.Generic.Dictionary%602> türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="6f61e-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="6f61e-127">Dizin leyiciler, kullanıcı tanımlı bir türün örneklerini dizi dizilimi gibi benzer şekilde dizilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="6f61e-128">İntesayı olması gereken dizi dizinlerinin aksine, dizinleyici parametreleri herhangi bir türde olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="6f61e-129">Dizinleyiciler hakkında daha fazla bilgi için [bkz.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="6f61e-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="6f61e-130">Diğer kullanımları []</span><span class="sxs-lookup"><span data-stu-id="6f61e-130">Other usages of []</span></span>

<span data-ttu-id="6f61e-131">İşaretçi öğesi erişimi hakkında bilgi için, Pointer ilgili [işleçler](pointer-related-operators.md) makalesinin [Pointer öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="6f61e-132">[Ayrıca öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için kare ayraçlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="6f61e-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="6f61e-133">Null-koşullu operatörler ?.</span><span class="sxs-lookup"><span data-stu-id="6f61e-133">Null-conditional operators ?.</span></span> <span data-ttu-id="6f61e-134">Ve? []</span><span class="sxs-lookup"><span data-stu-id="6f61e-134">and ?[]</span></span>

<span data-ttu-id="6f61e-135">C# 6 ve sonraki durumlarda, null-koşullu bir işleç [üye erişimi](#member-access-expression-), `?.`veya [eleman erişimi](#indexer-operator-), `?[]`, operand non-null değerlendirir sadece operand için işlem uygular; aksi takdirde, `null`döner .</span><span class="sxs-lookup"><span data-stu-id="6f61e-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="6f61e-136">Yani</span><span class="sxs-lookup"><span data-stu-id="6f61e-136">That is,</span></span>

- <span data-ttu-id="6f61e-137">Eğer `a` `null`değerlendirirse , `a?.x` sonucu `a?[x]` `null`veya .</span><span class="sxs-lookup"><span data-stu-id="6f61e-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="6f61e-138">Null `a` olmayan olarak değerlendirilirse, `a?.x` sonucu `a?[x]` veya sonucu `a.x` olarak aynıdır `a[x]`veya , sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="6f61e-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6f61e-139">Bir `a.x` `a[x]` özel durum atarsa `a?.x` veya bir özel durum atarsa veya `a?[x]` null `a`olmayanlar için aynı özel durumu atar.</span><span class="sxs-lookup"><span data-stu-id="6f61e-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="6f61e-140">Örneğin, null `a` olmayan bir dizi örneği `x` ise ve sınırları `a` `a?[x]` dışında ise <xref:System.IndexOutOfRangeException>, bir .</span><span class="sxs-lookup"><span data-stu-id="6f61e-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="6f61e-141">Null-conditional operatörler kısa devre vardır.</span><span class="sxs-lookup"><span data-stu-id="6f61e-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="6f61e-142">Diğer bir deyişle, koşullu üye veya öğe erişim `null`işlemleri zincirindeki bir işlem döndürürse, zincirin geri kalanı çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6f61e-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="6f61e-143">Aşağıdaki örnekte, `B` `A` aşağıdaki durumlarda `null` `C` `A` değerlendirilmiyorsa ve `B` değerlendirilmiyorsa: `null`</span><span class="sxs-lookup"><span data-stu-id="6f61e-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="6f61e-144">Aşağıdaki örnek, `?.` `?[]` işleçlerin ve işleçlerin kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6f61e-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="6f61e-145">Önceki örnek, null-koşullu bir işlemin sonucu durumunda değerlendirmek için alternatif bir ifade belirtmek için [null-coalescing işleci `??` ](null-coalescing-operator.md) `null`kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f61e-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="6f61e-146">`a.x` Nullable `a[x]` değer `T`türünde `a?.x` yse veya karşılık `a?[x]` gelen [nullable değer türüne](../builtin-types/nullable-value-types.md) `T?`aitse.</span><span class="sxs-lookup"><span data-stu-id="6f61e-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="6f61e-147">Bir tür `T`ifadesine ihtiyacınız varsa, aşağıdaki örnekte `??` görüldüğü gibi null-coalescing işlecinin null koşullu ifadesine uygulayın:</span><span class="sxs-lookup"><span data-stu-id="6f61e-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="6f61e-148">Önceki örnekte, `??` işleç kullanmıyorsanız, `numbers?.Length < 2` `false` ne zaman `numbers` olduğunu `null`değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="6f61e-149">Null-koşullu üye erişim `?.` operatörü elvis operatörü olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="6f61e-150">İş parçacığı güvenli temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="6f61e-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="6f61e-151">Bir `?.` temsilcinin geçersiz olup olmadığını denetlemek için işleci kullanın ve aşağıdaki kodun gösterdiği gibi iş parçacığı güvenli bir şekilde (örneğin, [bir olay yükselttiğinde)](../../../standard/events/how-to-raise-and-consume-events.md)çağırın:</span><span class="sxs-lookup"><span data-stu-id="6f61e-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="6f61e-152">Bu kod, C# 5 veya daha önce kullanacağınız aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="6f61e-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a><span data-ttu-id="6f61e-153">Çağırma ifadesi ()</span><span class="sxs-lookup"><span data-stu-id="6f61e-153">Invocation expression ()</span></span>

<span data-ttu-id="6f61e-154">Bir yöntemi çağırmak `()`veya bir [method](../../programming-guide/classes-and-structs/methods.md) [temsilci](../../programming-guide/delegates/index.md)çağırmak için parantez kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-154">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="6f61e-155">Aşağıdaki örnek, bağımsız değişkenli veya bağımsız bir yöntemin nasıl çağrılmasını ve bir temsilci çağırmanın nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6f61e-155">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="6f61e-156">İşleç ile bir oluşturucu çağırırken de parantez kullanırsınız. [constructor](../../programming-guide/classes-and-structs/constructors.md) [`new`](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="6f61e-156">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="6f61e-157">Diğer kullanımları ()</span><span class="sxs-lookup"><span data-stu-id="6f61e-157">Other usages of ()</span></span>

<span data-ttu-id="6f61e-158">İşlemleri bir ifadede değerlendirmek için sırasını ayarlamak için parantez ler de kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f61e-158">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="6f61e-159">Daha fazla bilgi için [C# işleçleri'ne](index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-159">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="6f61e-160">Açık tür [dönüşümleri](type-testing-and-cast.md#cast-operator-)gerçekleştiren cast ifadeleri de parantez kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f61e-160">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="6f61e-161">Son işleç ^ dan Dizin</span><span class="sxs-lookup"><span data-stu-id="6f61e-161">Index from end operator ^</span></span>

<span data-ttu-id="6f61e-162">C# 8.0 ve daha `^` sonra kullanılabilir, işleç bir dizinin sonundan öğe konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-162">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="6f61e-163">Uzunluk dizisi `length`için, `^n` bir dizinin başlangıcından itibaren ofset `length - n` ile eleman işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6f61e-163">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="6f61e-164">Örneğin, `^1` bir dizinin son öğesini `^length` ve bir dizinin ilk öğesini işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6f61e-164">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="6f61e-165">Yukarıdaki örnekte de görüldüğü `^e` gibi, <xref:System.Index?displayProperty=nameWithType> ifade türündendir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-165">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="6f61e-166">İfadede `^e`, sonucu `e` örtülü olarak dönüştürülebilir `int`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f61e-166">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="6f61e-167">Ayrıca, bir `^` dizi endeks oluşturmak için [aralık işleciyle](#range-operator-) birlikte işleci de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f61e-167">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="6f61e-168">Daha fazla bilgi için [Endeksler ve aralıklar'a](../../tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-168">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="6f61e-169">Menzil operatörü ...</span><span class="sxs-lookup"><span data-stu-id="6f61e-169">Range operator ..</span></span>

<span data-ttu-id="6f61e-170">C# 8.0 ve daha `..` sonra mevcuttur, operatör operands olarak endeksleri bir dizi başlangıç ve bitiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-170">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="6f61e-171">Sol operand bir dizi *kapsayıcı* bir başlangıçtır.</span><span class="sxs-lookup"><span data-stu-id="6f61e-171">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="6f61e-172">Sağ operand bir aralığın *özel* bir sonudur.</span><span class="sxs-lookup"><span data-stu-id="6f61e-172">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="6f61e-173">Aşağıdaki örnekte görüldüğü gibi, operandlardan biri bir dizinin başından veya sonundan itibaren olabilir:</span><span class="sxs-lookup"><span data-stu-id="6f61e-173">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="6f61e-174">Yukarıdaki örnekte de görüldüğü `a..b` gibi, <xref:System.Range?displayProperty=nameWithType> ifade türündendir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-174">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="6f61e-175">İfadede `a..b`, sonuçları `a` `b` ve örtülü olarak dönüştürülebilir olmalıdır `int` ya da <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="6f61e-175">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="6f61e-176">Açık uçlu bir aralık elde etmek için `..` operatörün operands herhangi birini atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f61e-176">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="6f61e-177">`a..`eşdeğerdir`a..^0`</span><span class="sxs-lookup"><span data-stu-id="6f61e-177">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="6f61e-178">`..b`eşdeğerdir`0..b`</span><span class="sxs-lookup"><span data-stu-id="6f61e-178">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="6f61e-179">`..`eşdeğerdir`0..^0`</span><span class="sxs-lookup"><span data-stu-id="6f61e-179">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="6f61e-180">Daha fazla bilgi için [Endeksler ve aralıklar'a](../../tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-180">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6f61e-181">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="6f61e-181">Operator overloadability</span></span>

<span data-ttu-id="6f61e-182">`.`, `()`, `^`ve `..` işleçler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="6f61e-182">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="6f61e-183">Operatör `[]` ayrıca aşırı yüklenebilir olmayan bir işleç olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6f61e-183">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="6f61e-184">Dizin oluşturmayı kullanıcı tanımlı türlerle desteklemek için [dizin oluşturmayı](../../programming-guide/indexers/index.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-184">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6f61e-185">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6f61e-185">C# language specification</span></span>

<span data-ttu-id="6f61e-186">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="6f61e-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="6f61e-187">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="6f61e-187">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="6f61e-188">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="6f61e-188">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="6f61e-189">Null koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="6f61e-189">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="6f61e-190">Çağırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6f61e-190">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="6f61e-191">Endeksler ve aralıklar hakkında daha fazla bilgi için [özellik teklif notuna](~/_csharplang/proposals/csharp-8.0/ranges.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6f61e-191">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f61e-192">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f61e-192">See also</span></span>

- [<span data-ttu-id="6f61e-193">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6f61e-193">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6f61e-194">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6f61e-194">C# operators</span></span>](index.md)
- [<span data-ttu-id="6f61e-195">?? (null-coalescing operatörü)</span><span class="sxs-lookup"><span data-stu-id="6f61e-195">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="6f61e-196">:: işleci</span><span class="sxs-lookup"><span data-stu-id="6f61e-196">:: operator</span></span>](namespace-alias-qualifier.md)
