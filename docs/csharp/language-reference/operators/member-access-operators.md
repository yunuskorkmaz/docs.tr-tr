---
title: Üye erişim operatörleri - C# referansı
description: Tür üyelerine erişmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 4d4bc0c192912b5fa87a8e91bc5ba0e1d4ce3598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399513"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="e5a92-103">Üye erişim operatörleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e5a92-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="e5a92-104">Bir tür üyesine erişirken aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e5a92-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="e5a92-105">(üye erişimi) : bir ad alanı nın veya bir türün üyesine erişmek için [ `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="e5a92-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="e5a92-106">[(dizi öğesi veya dizinleyici erişimi) : bir dizi öğesi veya bir tür dizinleyici erişmek için `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="e5a92-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="e5a92-107">ve (null-conditional operators) : bir üye veya eleman erişim işlemi gerçekleştirmek için sadece bir operand null olmayan [ `?.` `?[]` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="e5a92-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="e5a92-108">(çağırma) : erişilen bir yöntemi çağırmak veya bir temsilci çağırmak [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="e5a92-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="e5a92-109">(dizini sona) : eleman konumunun bir dizinin sonundan geldiğini belirtmek için [ `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="e5a92-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="e5a92-110">(aralık) : dizi öğeleri aralığı elde etmek için kullanabileceğiniz bir dizi endeks belirtmek için [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="e5a92-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="e5a92-111">Üye erişim operatörü .</span><span class="sxs-lookup"><span data-stu-id="e5a92-111">Member access operator .</span></span>

<span data-ttu-id="e5a92-112">Aşağıdaki örneklerde gösterildiği gibi, bir ad alanı nın veya bir türün üyesine erişmek için `.` belirteci kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="e5a92-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="e5a92-113">Bir `.` [ `using` yönergeörneğinin](../keywords/using-directive.md) aşağıdaki örneğinde görüldüğü gibi, ad alanı içinde iç içe bir ad alanına erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5a92-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="e5a92-114">Aşağıdaki `.` kodun gösterdiği gibi, ad alanı içindeki bir türe erişmek için nitelikli bir *ad* oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5a92-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="e5a92-115">Nitelikli adlardan isteğe bağlı olarak yararlanmak için bir [ `using` yönerge](../keywords/using-directive.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="e5a92-116">Aşağıdaki `.` kodun gösterdiği gibi, statik ve statik olmayan [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members)erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5a92-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="e5a92-117">Ayrıca bir `.` [uzantı yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5a92-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="e5a92-118">Dizinleyici operatörü []</span><span class="sxs-lookup"><span data-stu-id="e5a92-118">Indexer operator []</span></span>

<span data-ttu-id="e5a92-119">Kare ayraçlar, `[]`genellikle dizi, dizinleyici veya işaretçi öğesi erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5a92-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="e5a92-120">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="e5a92-120">Array access</span></span>

<span data-ttu-id="e5a92-121">Aşağıdaki örnek, dizi öğelerine nasıl erişilenleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="e5a92-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="e5a92-122">Bir dizi dizi dizi dizinin ilgili boyutunun sınırları <xref:System.IndexOutOfRangeException> dışında ysa, bir atılır.</span><span class="sxs-lookup"><span data-stu-id="e5a92-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="e5a92-123">Önceki örnekte de görüldüğü gibi, bir dizi türünü beyan ettiğinizde veya bir dizi örneğini anında yaptığınızda kare ayraçlar da kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e5a92-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="e5a92-124">Diziler hakkında daha fazla bilgi için [Diziler'e](../../programming-guide/arrays/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="e5a92-125">Dizinleyici erişimi</span><span class="sxs-lookup"><span data-stu-id="e5a92-125">Indexer access</span></span>

<span data-ttu-id="e5a92-126">Aşağıdaki örnek, dizinleyici erişimini göstermek için .NET <xref:System.Collections.Generic.Dictionary%602> türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="e5a92-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="e5a92-127">Dizin leyiciler, kullanıcı tanımlı bir türün örneklerini dizi dizilimi gibi benzer şekilde dizilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="e5a92-128">İntesayı olması gereken dizi dizinlerinin aksine, dizinleyici parametreleri herhangi bir türde olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="e5a92-129">Dizinleyiciler hakkında daha fazla bilgi için [bkz.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="e5a92-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e5a92-130">Diğer kullanımları []</span><span class="sxs-lookup"><span data-stu-id="e5a92-130">Other usages of []</span></span>

<span data-ttu-id="e5a92-131">İşaretçi öğesi erişimi hakkında bilgi için, Pointer ilgili [işleçler](pointer-related-operators.md) makalesinin [Pointer öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="e5a92-132">[Ayrıca öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için kare ayraçlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5a92-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="e5a92-133">Null-koşullu operatörler ?.</span><span class="sxs-lookup"><span data-stu-id="e5a92-133">Null-conditional operators ?.</span></span> <span data-ttu-id="e5a92-134">Ve? []</span><span class="sxs-lookup"><span data-stu-id="e5a92-134">and ?[]</span></span>

<span data-ttu-id="e5a92-135">C# 6 ve sonraki durumlarda, null-koşullu bir işleç [üye erişimi](#member-access-operator-), `?.`veya [eleman erişimi](#indexer-operator-), `?[]`, operand non-null değerlendirir sadece operand için işlem uygular; aksi takdirde, `null`döner .</span><span class="sxs-lookup"><span data-stu-id="e5a92-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-operator-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="e5a92-136">Yani</span><span class="sxs-lookup"><span data-stu-id="e5a92-136">That is,</span></span>

- <span data-ttu-id="e5a92-137">Eğer `a` `null`değerlendirirse , `a?.x` sonucu `a?[x]` `null`veya .</span><span class="sxs-lookup"><span data-stu-id="e5a92-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="e5a92-138">Null `a` olmayan olarak değerlendirilirse, `a?.x` sonucu `a?[x]` veya sonucu `a.x` olarak aynıdır `a[x]`veya , sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e5a92-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e5a92-139">Bir `a.x` `a[x]` özel durum atarsa `a?.x` veya bir özel durum atarsa veya `a?[x]` null `a`olmayanlar için aynı özel durumu atar.</span><span class="sxs-lookup"><span data-stu-id="e5a92-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="e5a92-140">Örneğin, null `a` olmayan bir dizi örneği `x` ise ve sınırları `a` `a?[x]` dışında ise <xref:System.IndexOutOfRangeException>, bir .</span><span class="sxs-lookup"><span data-stu-id="e5a92-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="e5a92-141">Null-conditional operatörler kısa devre vardır.</span><span class="sxs-lookup"><span data-stu-id="e5a92-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="e5a92-142">Diğer bir deyişle, koşullu üye veya öğe erişim `null`işlemleri zincirindeki bir işlem döndürürse, zincirin geri kalanı çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e5a92-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="e5a92-143">Aşağıdaki örnekte, `B` `A` aşağıdaki durumlarda `null` `C` `A` değerlendirilmiyorsa ve `B` değerlendirilmiyorsa: `null`</span><span class="sxs-lookup"><span data-stu-id="e5a92-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="e5a92-144">Aşağıdaki örnek, `?.` `?[]` işleçlerin ve işleçlerin kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e5a92-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="e5a92-145">Önceki örnek, null-koşullu bir işlemin sonucu durumunda değerlendirmek için alternatif bir ifade belirtmek için [null-coalescing işleci `??` ](null-coalescing-operator.md) `null`kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5a92-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="e5a92-146">Null-koşullu üye erişim `?.` operatörü elvis operatörü olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-146">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="e5a92-147">İş parçacığı güvenli temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="e5a92-147">Thread-safe delegate invocation</span></span>

<span data-ttu-id="e5a92-148">Bir `?.` temsilcinin geçersiz olup olmadığını denetlemek için işleci kullanın ve aşağıdaki kodun gösterdiği gibi iş parçacığı güvenli bir şekilde (örneğin, [bir olay yükselttiğinde)](../../../standard/events/how-to-raise-and-consume-events.md)çağırın:</span><span class="sxs-lookup"><span data-stu-id="e5a92-148">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="e5a92-149">Bu kod, C# 5 veya daha önce kullanacağınız aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="e5a92-149">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="e5a92-150">Çağırma operatörü ()</span><span class="sxs-lookup"><span data-stu-id="e5a92-150">Invocation operator ()</span></span>

<span data-ttu-id="e5a92-151">Bir yöntemi çağırmak `()`veya bir [method](../../programming-guide/classes-and-structs/methods.md) [temsilci](../../programming-guide/delegates/index.md)çağırmak için parantez kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-151">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="e5a92-152">Aşağıdaki örnek, bağımsız değişkenli veya bağımsız bir yöntemin nasıl çağrılmasını ve bir temsilci çağırmanın nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e5a92-152">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="e5a92-153">İşleç ile bir oluşturucu çağırırken de parantez kullanırsınız. [constructor](../../programming-guide/classes-and-structs/constructors.md) [`new`](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="e5a92-153">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e5a92-154">Diğer kullanımları ()</span><span class="sxs-lookup"><span data-stu-id="e5a92-154">Other usages of ()</span></span>

<span data-ttu-id="e5a92-155">İşlemleri bir ifadede değerlendirmek için sırasını ayarlamak için parantez ler de kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e5a92-155">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="e5a92-156">Daha fazla bilgi için [C# işleçleri'ne](index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-156">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="e5a92-157">Açık tür [dönüşümleri](type-testing-and-cast.md#cast-operator-)gerçekleştiren cast ifadeleri de parantez kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5a92-157">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="e5a92-158">Son işleç ^ dan Dizin</span><span class="sxs-lookup"><span data-stu-id="e5a92-158">Index from end operator ^</span></span>

<span data-ttu-id="e5a92-159">C# 8.0 ve daha `^` sonra kullanılabilir, işleç bir dizinin sonundan öğe konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-159">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="e5a92-160">Uzunluk dizisi `length`için, `^n` bir dizinin başlangıcından itibaren ofset `length - n` ile eleman işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e5a92-160">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="e5a92-161">Örneğin, `^1` bir dizinin son öğesini `^length` ve bir dizinin ilk öğesini işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e5a92-161">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="e5a92-162">Yukarıdaki örnekte de görüldüğü `^e` gibi, <xref:System.Index?displayProperty=nameWithType> ifade türündendir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-162">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e5a92-163">İfadede `^e`, sonucu `e` örtülü olarak dönüştürülebilir `int`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5a92-163">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="e5a92-164">Ayrıca, bir `^` dizi endeks oluşturmak için [aralık işleciyle](#range-operator-) birlikte işleci de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5a92-164">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="e5a92-165">Daha fazla bilgi için [Endeksler ve aralıklar'a](../../tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-165">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="e5a92-166">Menzil operatörü ...</span><span class="sxs-lookup"><span data-stu-id="e5a92-166">Range operator ..</span></span>

<span data-ttu-id="e5a92-167">C# 8.0 ve daha `..` sonra mevcuttur, operatör operands olarak endeksleri bir dizi başlangıç ve bitiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-167">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="e5a92-168">Sol operand bir dizi *kapsayıcı* bir başlangıçtır.</span><span class="sxs-lookup"><span data-stu-id="e5a92-168">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="e5a92-169">Sağ operand bir aralığın *özel* bir sonudur.</span><span class="sxs-lookup"><span data-stu-id="e5a92-169">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="e5a92-170">Aşağıdaki örnekte görüldüğü gibi, operandlardan biri bir dizinin başından veya sonundan itibaren olabilir:</span><span class="sxs-lookup"><span data-stu-id="e5a92-170">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="e5a92-171">Yukarıdaki örnekte de görüldüğü `a..b` gibi, <xref:System.Range?displayProperty=nameWithType> ifade türündendir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-171">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e5a92-172">İfadede `a..b`, sonuçları `a` `b` ve örtülü olarak dönüştürülebilir olmalıdır `int` ya da <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="e5a92-172">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="e5a92-173">Açık uçlu bir aralık elde etmek için `..` operatörün operands herhangi birini atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e5a92-173">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="e5a92-174">`a..`eşdeğerdir`a..^0`</span><span class="sxs-lookup"><span data-stu-id="e5a92-174">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="e5a92-175">`..b`eşdeğerdir`0..b`</span><span class="sxs-lookup"><span data-stu-id="e5a92-175">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="e5a92-176">`..`eşdeğerdir`0..^0`</span><span class="sxs-lookup"><span data-stu-id="e5a92-176">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="e5a92-177">Daha fazla bilgi için [Endeksler ve aralıklar'a](../../tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-177">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e5a92-178">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="e5a92-178">Operator overloadability</span></span>

<span data-ttu-id="e5a92-179">`.`, `()`, `^`ve `..` işleçler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e5a92-179">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="e5a92-180">Operatör `[]` ayrıca aşırı yüklenebilir olmayan bir işleç olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e5a92-180">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="e5a92-181">Dizin oluşturmayı kullanıcı tanımlı türlerle desteklemek için [dizin oluşturmayı](../../programming-guide/indexers/index.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-181">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e5a92-182">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e5a92-182">C# language specification</span></span>

<span data-ttu-id="e5a92-183">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="e5a92-183">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e5a92-184">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="e5a92-184">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="e5a92-185">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="e5a92-185">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="e5a92-186">Null koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="e5a92-186">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="e5a92-187">Çağırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e5a92-187">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="e5a92-188">Endeksler ve aralıklar hakkında daha fazla bilgi için [özellik teklif notuna](~/_csharplang/proposals/csharp-8.0/ranges.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a92-188">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a92-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a92-189">See also</span></span>

- [<span data-ttu-id="e5a92-190">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e5a92-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e5a92-191">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e5a92-191">C# operators</span></span>](index.md)
- [<span data-ttu-id="e5a92-192">?? (null-coalescing operatörü)</span><span class="sxs-lookup"><span data-stu-id="e5a92-192">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="e5a92-193">:: operatör</span><span class="sxs-lookup"><span data-stu-id="e5a92-193">:: operator</span></span>](namespace-alias-qualifier.md)
