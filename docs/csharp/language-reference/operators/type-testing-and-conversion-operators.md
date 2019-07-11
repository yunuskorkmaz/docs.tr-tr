---
title: Tür test etme ve dönüştürme işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# bir ifadenin sonuç türü denetleyin ve gerekiyorsa, başka bir türe dönüştürmek için kullanabileceğiniz işleçler.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: a9e5139e6d650aa6935bff934ca25502fdc14775
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744081"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a><span data-ttu-id="a69a6-103">Tür test etme ve dönüştürme işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a69a6-103">Type-testing and conversion operators (C# reference)</span></span>

<span data-ttu-id="a69a6-104">Tür dönüşümü veya tür denetimi gerçekleştirmek için aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a69a6-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="a69a6-105">[Is işleci](#is-operator): bir ifade çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="a69a6-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="a69a6-106">[işleci olarak](#as-operator): açıkça kendi çalışma zamanı türü bu tür ile uyumlu ise bir ifade belirli bir türe dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="a69a6-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="a69a6-107">[atama işleci ()](#cast-operator-): açık bir dönüştürme gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="a69a6-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="a69a6-108">[typeof işleci](#typeof-operator): edinme <xref:System.Type?displayProperty=nameWithType> bir tür örneği</span><span class="sxs-lookup"><span data-stu-id="a69a6-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="a69a6-109">Is işleci</span><span class="sxs-lookup"><span data-stu-id="a69a6-109">is operator</span></span>

<span data-ttu-id="a69a6-110">`is` İşleci bir ifade sonucu çalışma zamanı türü belirli bir tür ile uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="a69a6-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="a69a6-111">İle başlayarak C# 7.0 `is` işleci bir ifade sonucunu belirli bir desene göre de test eder.</span><span class="sxs-lookup"><span data-stu-id="a69a6-111">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="a69a6-112">Tür testi ifadesiyle `is` işleci aşağıdaki biçime sahip</span><span class="sxs-lookup"><span data-stu-id="a69a6-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="a69a6-113">Burada `E` değer döndüren bir ifadedir ve `T` bir türü veya tür parametresi adıdır.</span><span class="sxs-lookup"><span data-stu-id="a69a6-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="a69a6-114">`E` Anonim bir yöntem veya lambda ifadesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="a69a6-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="a69a6-115">`E is T` İfade döndürür `true` varsa sonucunu `E` null olmayan ve türüne dönüştürülebilir `T` başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürme; Aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="a69a6-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="a69a6-116">`is` İşleci değil kullanıcı tanımlı dönüşümler düşünün.</span><span class="sxs-lookup"><span data-stu-id="a69a6-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="a69a6-117">Aşağıdaki örnek, gösterir `is` işleci döndürür `true` ifade sonucu çalışma zamanı türü belirtilen türünden türer, diğer bir deyişle, mevcut bir başvuru dönüştürmesi türler arasında:</span><span class="sxs-lookup"><span data-stu-id="a69a6-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="a69a6-118">Sonraki örnek, gösterir `is` işleci kutulama ve kutudan çıkarma dönüştürme dikkate alır ancak sayısal dönüşümler dikkate almaz:</span><span class="sxs-lookup"><span data-stu-id="a69a6-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider numeric conversions:</span></span>

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="a69a6-119">Hakkında bilgi için C# dönüştürmeleri bkz [dönüştürmeler](~/_csharplang/spec/conversions.md) bölüm [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a69a6-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="a69a6-120">Desen eşleştirme ile test türü</span><span class="sxs-lookup"><span data-stu-id="a69a6-120">Type testing with pattern matching</span></span>

<span data-ttu-id="a69a6-121">İle başlayarak C# 7.0 `is` işleci bir ifade sonucunu belirli bir desene göre de test eder.</span><span class="sxs-lookup"><span data-stu-id="a69a6-121">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="a69a6-122">Özellikle, aşağıdaki biçimde türü desenini destekler:</span><span class="sxs-lookup"><span data-stu-id="a69a6-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="a69a6-123">Burada `E` bir değer döndüren bir ifadedir `T` bir türü veya tür parametresi, adıdır ve `v` türünde yeni bir yerel değişken `T`.</span><span class="sxs-lookup"><span data-stu-id="a69a6-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="a69a6-124">Sonucu `E` null olmayan ve dönüştürülebilir `T` kutulama ve kutudan çıkarma, dönüştürme, bir başvuruya göre `E is T v` ifade döndürür `true` ve sonucu dönüştürülmüş değeri `E` atanır değişken `v`.</span><span class="sxs-lookup"><span data-stu-id="a69a6-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="a69a6-125">Aşağıdaki örnek, kullanımını gösterir. `is` işleç türü desen ile:</span><span class="sxs-lookup"><span data-stu-id="a69a6-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="a69a6-126">Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için bkz. [deseni ile eşleşen](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="a69a6-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="a69a6-127">operatör olarak</span><span class="sxs-lookup"><span data-stu-id="a69a6-127">as operator</span></span>

<span data-ttu-id="a69a6-128">`as` İşleci bir verilen başvuru veya null değer türü bir ifadenin sonucu açıkça dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a69a6-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="a69a6-129">Dönüştürme mümkün değilse `as` işleci döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="a69a6-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="a69a6-130">Farklı [atama işleci ()](#cast-operator-), `as` işleci hiçbir zaman bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a69a6-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="a69a6-131">Formun ifadesi</span><span class="sxs-lookup"><span data-stu-id="a69a6-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="a69a6-132">Burada `E` değer döndüren bir ifadedir ve `T` aynı sonucu üretir, bir türü veya tür parametresi adı</span><span class="sxs-lookup"><span data-stu-id="a69a6-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="a69a6-133">dışında `E` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a69a6-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="a69a6-134">`as` İşleci, yalnızca başvuru null yapılabilir, kutulama ve kutudan çıkarma dönüştürme göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="a69a6-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="a69a6-135">Kullanamazsınız `as` kullanıcı tanımlı bir dönüştürme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="a69a6-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="a69a6-136">Bunu yapmak için kullanın [atama işleci ()](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="a69a6-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="a69a6-137">Aşağıdaki örnek, kullanımını gösterir. `as` işleci:</span><span class="sxs-lookup"><span data-stu-id="a69a6-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="a69a6-138">Yukarıdaki örnekte gösterildiği gibi sonucunu karşılaştırmak gereken `as` ifadesiyle `null` dönüştürme başarılı olup olmadığını denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="a69a6-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="a69a6-139">İle başlayarak C# kullanabileceğiniz 7.0 [işleci](#type-testing-with-pattern-matching) yeni bir değişkene dönüştürme başarılı olursa ve başarılı olursa, test etmek için her ikisi de atama sonucu.</span><span class="sxs-lookup"><span data-stu-id="a69a6-139">Starting with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="a69a6-140">Atama işleci (.)</span><span class="sxs-lookup"><span data-stu-id="a69a6-140">Cast operator ()</span></span>

<span data-ttu-id="a69a6-141">Atama ifadesi formun `(T)E` ifadenin sonucu, açık bir dönüştürme gerçekleştiren `E` türüne `T`.</span><span class="sxs-lookup"><span data-stu-id="a69a6-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="a69a6-142">Açık bir dönüştürme türünden varsa `E` türüne `T`, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="a69a6-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="a69a6-143">Çalışma zamanında açık bir dönüştürme başarısız olabilir ve bir atama ifadesi bir özel durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="a69a6-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="a69a6-144">Aşağıdaki örnek, sayısal ve başvuru açık dönüştürmeler gösterir:</span><span class="sxs-lookup"><span data-stu-id="a69a6-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="a69a6-145">Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için bkz. [açık dönüştürmeler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a69a6-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="a69a6-146">Bir özel açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz: [kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a69a6-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="a69a6-147">()'nin diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="a69a6-147">Other usages of ()</span></span>

<span data-ttu-id="a69a6-148">Parantez de [bir yöntemi çağırabilir veya bir temsilcinin çağırma](member-access-operators.md#invocation-operator-).</span><span class="sxs-lookup"><span data-stu-id="a69a6-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="a69a6-149">Diğer parantez işlemleri bir ifade Değerlendirme sırasını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a69a6-149">Other use of parentheses is to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="a69a6-150">Daha fazla bilgi için [ayraç ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümünü [işleçleri](../../programming-guide/statements-expressions-operators/operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="a69a6-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="a69a6-151">İşleçler, öncelik düzeyine göre sıralı listesi için bkz. [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="a69a6-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="a69a6-152">typeof işleci</span><span class="sxs-lookup"><span data-stu-id="a69a6-152">typeof operator</span></span>

<span data-ttu-id="a69a6-153">`typeof` İşleci alır <xref:System.Type?displayProperty=nameWithType> örneği için bir tür.</span><span class="sxs-lookup"><span data-stu-id="a69a6-153">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="a69a6-154">Bağımsız değişkeninin `typeof` işleci, bir türü veya tür parametresi, adı aşağıdaki örnekte gösterildiği gibi olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a69a6-154">An argument of the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="a69a6-155">Ayrıca `typeof` işleci ile ilişkisiz genel türler.</span><span class="sxs-lookup"><span data-stu-id="a69a6-155">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="a69a6-156">İlişkisiz bir genel tür adı, türü parametre sayısı'den küçük bir virgül uygun bir sayı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="a69a6-156">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="a69a6-157">Aşağıdaki örnek, kullanımını gösterir. `typeof` ilişkisiz bir genel tür işleç:</span><span class="sxs-lookup"><span data-stu-id="a69a6-157">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="a69a6-158">Bir ifade bir bağımsız değişkeni olamaz `typeof` işleci.</span><span class="sxs-lookup"><span data-stu-id="a69a6-158">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="a69a6-159">Alınacak <xref:System.Type?displayProperty=nameWithType> kullan ifade sonucu çalışma zamanı türünün örneği <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a69a6-159">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of the expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="a69a6-160">Testi türü `typeof` işleci</span><span class="sxs-lookup"><span data-stu-id="a69a6-160">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="a69a6-161">Kullanım `typeof` ifade sonucu çalışma zamanı türü verilen tür tam olarak eşleşip eşleşmediğini anlamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="a69a6-161">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="a69a6-162">Aşağıdaki örnek tür ile gerçekleştirilen denetimi arasındaki farkı gösterir `typeof` işleci ve [işleci](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="a69a6-162">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="a69a6-163">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="a69a6-163">Operator overloadability</span></span>

<span data-ttu-id="a69a6-164">`is`, `as`, Ve `typeof` işleçleri aşırı yüklenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="a69a6-164">The `is`, `as`, and `typeof` operators are not overloadable.</span></span>

<span data-ttu-id="a69a6-165">Kullanıcı tanımlı bir tür aşırı yüklenemez `()` işleci, ancak bir atama ifadesi tarafından gerçekleştirilen özel tür dönüştürmeler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a69a6-165">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="a69a6-166">Daha fazla bilgi için [kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a69a6-166">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a69a6-167">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a69a6-167">C# language specification</span></span>

<span data-ttu-id="a69a6-168">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a69a6-168">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a69a6-169">Is işleci</span><span class="sxs-lookup"><span data-stu-id="a69a6-169">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="a69a6-170">AS işleci</span><span class="sxs-lookup"><span data-stu-id="a69a6-170">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="a69a6-171">Cast ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a69a6-171">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="a69a6-172">Typeof işleci</span><span class="sxs-lookup"><span data-stu-id="a69a6-172">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="a69a6-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a69a6-173">See also</span></span>

- [<span data-ttu-id="a69a6-174">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="a69a6-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a69a6-175">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="a69a6-175">C# operators</span></span>](index.md)
- [<span data-ttu-id="a69a6-176">Nasıl yapılır: desen eşleştirme kullanarak güvenli bir şekilde noktaya yayın ve olduğu ve işleçler</span><span class="sxs-lookup"><span data-stu-id="a69a6-176">How to: safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
