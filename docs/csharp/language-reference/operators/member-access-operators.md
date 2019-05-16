---
title: Üye erişim işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# tür üyelerine erişmek için kullanabileceğiniz işleçler.
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
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
ms.openlocfilehash: 2c5f569b0ad68132e07b009ec9968c766bb965f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633509"
---
# <a name="member-access-operators"></a><span data-ttu-id="bba6f-103">Üye erişimi işleçleri</span><span class="sxs-lookup"><span data-stu-id="bba6f-103">Member access operators</span></span>

<span data-ttu-id="bba6f-104">Bir tür üyesi erişirken aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bba6f-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="bba6f-105">[`.` (üye erişimi) ](#member-access-operator-): bir ad alanı veya tür üyesi erişmek için</span><span class="sxs-lookup"><span data-stu-id="bba6f-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="bba6f-106">[`[]` (diziyi öğe veya dizin oluşturucu erişimi) ](#indexer-operator-): bir dizi öğesine ya da türü bir dizin oluşturucu erişmek için</span><span class="sxs-lookup"><span data-stu-id="bba6f-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="bba6f-107">[`?.` ve `?[]` (null koşullu işleçleri)](#null-conditional-operators--and-): yalnızca bir işlenen null olmayan ise bir üyesi veya öğenin erişim işlemi gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bba6f-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="bba6f-108">[`()` (çağırma) ](#invocation-operator-): erişilen bir yöntemi çağırabilir veya bir temsilci çağırmak için</span><span class="sxs-lookup"><span data-stu-id="bba6f-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="bba6f-109">Üye erişimi işleci.</span><span class="sxs-lookup"><span data-stu-id="bba6f-109">Member access operator .</span></span>

<span data-ttu-id="bba6f-110">Kullandığınız `.` aşağıdaki örneklerde gösterildiği gibi bir ad alanı veya tür, üye erişim belirteci:</span><span class="sxs-lookup"><span data-stu-id="bba6f-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="bba6f-111">Kullanım `.` iç içe geçmiş ad alanı içinde bir ad alanı, aşağıdaki örnek olarak erişmek için bir [ `using` yönergesi](../keywords/using-directive.md) gösterir:</span><span class="sxs-lookup"><span data-stu-id="bba6f-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="bba6f-112">Kullanım `.` forma bir *tam adı* aşağıdaki kodun gösterdiği gibi bir ad alanı içinde bir tür erişmek için:</span><span class="sxs-lookup"><span data-stu-id="bba6f-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="bba6f-113">Kullanan bir [ `using` yönergesi](../keywords/using-directive.md) nitelenmiş adlar kullanımı isteğe bağlı yapmak için.</span><span class="sxs-lookup"><span data-stu-id="bba6f-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="bba6f-114">Kullanım `.` erişimi [üyelerini türü](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan, aşağıdaki kodun gösterdiği olarak:</span><span class="sxs-lookup"><span data-stu-id="bba6f-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="bba6f-115">Ayrıca `.` erişmek için bir [genişletme yöntemi](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="bba6f-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="bba6f-116">Dizin Oluşturucu [] işleci</span><span class="sxs-lookup"><span data-stu-id="bba6f-116">Indexer operator []</span></span>

<span data-ttu-id="bba6f-117">Köşeli ayraçlar `[]`, genellikle dizi, dizin oluşturucu veya işaretçiyi öğe erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bba6f-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="bba6f-118">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="bba6f-118">Array access</span></span>

<span data-ttu-id="bba6f-119">Aşağıdaki örnekte, dizi öğelerinin nasıl erişileceğini gösteren:</span><span class="sxs-lookup"><span data-stu-id="bba6f-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="bba6f-120">Bir dizi dizini karşılık gelen boyutuna bir dizinin sınırları dışında ise bir <xref:System.IndexOutOfRangeException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bba6f-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="bba6f-121">Yukarıdaki örnekte gösterildiği gibi bir dizi türü bildirin veya bir dizi örneği de köşeli ayraç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba6f-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="bba6f-122">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="bba6f-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="bba6f-123">Dizinleyici erişimi</span><span class="sxs-lookup"><span data-stu-id="bba6f-123">Indexer access</span></span>

<span data-ttu-id="bba6f-124">Aşağıdaki örnek, .NET kullanır <xref:System.Collections.Generic.Dictionary%602> dizinleyici erişimi göstermek için türü:</span><span class="sxs-lookup"><span data-stu-id="bba6f-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="bba6f-125">Dizin oluşturucular dizi dizini oluşturma olarak benzer şekilde, kullanıcı tanımlı bir tür dizin örneğini olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bba6f-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="bba6f-126">Dizin oluşturucu bağımsız değişken tamsayı olması gerekir, dizi dizinleri, herhangi bir türde olması bildirilir.</span><span class="sxs-lookup"><span data-stu-id="bba6f-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="bba6f-127">Dizin oluşturucular hakkında daha fazla bilgi için bkz: [dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="bba6f-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="bba6f-128">[] İfadesinin diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="bba6f-128">Other usages of []</span></span>

<span data-ttu-id="bba6f-129">İşaretçi öğe erişimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: işaretçiyle bir dizi öğesine erişme](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="bba6f-129">For information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="bba6f-130">Köşeli ayraçlar belirtmek için de [öznitelikleri](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="bba6f-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="bba6f-131">Null koşullu işleçleri?</span><span class="sxs-lookup"><span data-stu-id="bba6f-131">Null-conditional operators ?.</span></span> <span data-ttu-id="bba6f-132">ve? []</span><span class="sxs-lookup"><span data-stu-id="bba6f-132">and ?[]</span></span>

<span data-ttu-id="bba6f-133">Kullanılabilir C# 6 ve üzeri, bir null koşullu işleci bir üye erişimi geçerlidir `?.`, ya da öğe erişimi, `?[]`, işlem için yalnızca işlenen null olmayan olarak değerlendirilirse, işleneni.</span><span class="sxs-lookup"><span data-stu-id="bba6f-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="bba6f-134">İşlenen değerlendirilirse `null`, işlecin sonucu olan `null`.</span><span class="sxs-lookup"><span data-stu-id="bba6f-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span>

<span data-ttu-id="bba6f-135">Null koşullu işleçleri short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="bba6f-135">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="bba6f-136">Diğer bir deyişle, işlemler zinciri tek bir işlemde koşullu üyesi veya bir öğenin erişim verir `null`, rest zincirinin yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bba6f-136">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="bba6f-137">Aşağıdaki örnekte, `B` uygulanamıyorsa değerlendirilmez `A` değerlendiren `null` ve `C` uygulanamıyorsa değerlendirilmez `A` veya `B` değerlendiren `null`:</span><span class="sxs-lookup"><span data-stu-id="bba6f-137">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="bba6f-138">Aşağıdaki örnek, kullanımını gösterir. `?.` ve `?[]` işleçleri:</span><span class="sxs-lookup"><span data-stu-id="bba6f-138">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="bba6f-139">Yukarıdaki örnekte ayrıca kullanımını gösterir [null birleşim işleci](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bba6f-139">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="bba6f-140">Null koşullu işleminin sonucu olması durumunda değerlendirmek için alternatif bir ifade sağlamak için null birleşim işleci kullanabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="bba6f-140">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="bba6f-141">İş parçacığı açısından güvenli temsilci çağrısı</span><span class="sxs-lookup"><span data-stu-id="bba6f-141">Thread-safe delegate invocation</span></span>

<span data-ttu-id="bba6f-142">Kullanım `?.` işleci, null olmayan bir temsilci olup olmadığını kontrol edin ve bir iş parçacığı açısından güvenli şekilde çağırmak için (örneğin, [bir olayı](../../../standard/events/how-to-raise-and-consume-events.md)) aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="bba6f-142">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="bba6f-143">Kod içinde kullanacağınız aşağıdaki koda denk olduğuna C# 5 veya daha önceki:</span><span class="sxs-lookup"><span data-stu-id="bba6f-143">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="bba6f-144">Çağırma işleci (.)</span><span class="sxs-lookup"><span data-stu-id="bba6f-144">Invocation operator ()</span></span>

<span data-ttu-id="bba6f-145">Parantez kullanın `()`çağırmak için bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) veya çağırma bir [temsilci](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="bba6f-145">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="bba6f-146">Aşağıdaki örnek, olan veya olmayan bağımsız değişkenler, bir yöntem çağrısı ve temsilci çağırma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bba6f-146">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="bba6f-147">Çağırdığınızda parantez de kullanmak bir [Oluşturucusu](../../programming-guide/classes-and-structs/constructors.md) ile bir [ `new` ](../keywords/new-operator.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="bba6f-147">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="bba6f-148">()'nin diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="bba6f-148">Other usages of ()</span></span>

<span data-ttu-id="bba6f-149">Ayrıca bir ifade işlemlerinde değerlendirilecek sırayı belirtmek için parantez kullanın.</span><span class="sxs-lookup"><span data-stu-id="bba6f-149">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="bba6f-150">Daha fazla bilgi için [ayraç ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümünü [işleçleri](../../programming-guide/statements-expressions-operators/operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="bba6f-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="bba6f-151">İşleçler, öncelik düzeyine göre sıralı listesi için bkz. [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="bba6f-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

<span data-ttu-id="bba6f-152">[Cast ifadeleri](invocation-operator.md#cast-expression), çağırmak bir dönüşüm işleci, parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba6f-152">[Cast expressions](invocation-operator.md#cast-expression), which invoke a conversion operator, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="bba6f-153">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="bba6f-153">Operator overloadability</span></span>

<span data-ttu-id="bba6f-154">`.` Ve `()` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="bba6f-154">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="bba6f-155">`[]` İşleci aşırı yüklenebilir olmayan bir işleç ayrıca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bba6f-155">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="bba6f-156">Kullanım [dizin oluşturucular](../../programming-guide/indexers/index.md) için kullanıcı tanımlı türler ile dizin oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="bba6f-156">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bba6f-157">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="bba6f-157">C# language specification</span></span>

<span data-ttu-id="bba6f-158">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="bba6f-158">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bba6f-159">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="bba6f-159">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="bba6f-160">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="bba6f-160">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="bba6f-161">Null koşullu işleci</span><span class="sxs-lookup"><span data-stu-id="bba6f-161">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="bba6f-162">Çağrı ifadeleri</span><span class="sxs-lookup"><span data-stu-id="bba6f-162">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="bba6f-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba6f-163">See also</span></span>

- [<span data-ttu-id="bba6f-164">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="bba6f-164">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bba6f-165">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bba6f-165">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bba6f-166">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="bba6f-166">C# Operators</span></span>](index.md)
- [<span data-ttu-id="bba6f-167">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="bba6f-167">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
