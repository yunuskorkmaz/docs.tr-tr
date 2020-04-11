---
title: Tür-test işleçleri ve döküm ifadesi - C# referansı
description: İfade sonucunun türünü denetlemek ve gerekirse başka bir türe dönüştürmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 5a4f1d4c0c2ddd0d3967e15090d8f8c1ac42f83e
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121412"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="30434-103">Tür-test işleçleri ve döküm ifadesi (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="30434-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="30434-104">Tür denetimi veya tür dönüştürmesi gerçekleştirmek için aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30434-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="30434-105">[is operator](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir türle uyumlu olup olmadığını kontrol etmek için</span><span class="sxs-lookup"><span data-stu-id="30434-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="30434-106">[olarak işleç](#as-operator): çalışma zamanı türü bu türle uyumluysa, bir ifadeyi açıkça belirli bir türe dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="30434-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="30434-107">[cast expression](#cast-expression): açık bir dönüştürme gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="30434-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="30434-108">[typeof operator](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> bir tür için örnek elde etmek için</span><span class="sxs-lookup"><span data-stu-id="30434-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="30434-109">işleç</span><span class="sxs-lookup"><span data-stu-id="30434-109">is operator</span></span>

<span data-ttu-id="30434-110">İşleç, `is` bir ifade sonucunun çalışma zamanı türünün belirli bir türle uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="30434-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="30434-111">C# 7.0 ile `is` başlayarak, işleç de bir desen karşı bir ifade sonucu test eder.</span><span class="sxs-lookup"><span data-stu-id="30434-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="30434-112">Tür test `is` işleci ile ifade aşağıdaki formu vardır</span><span class="sxs-lookup"><span data-stu-id="30434-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="30434-113">nerede `E` bir değer döndürür `T` ve bir tür veya tür parametre adı olan bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="30434-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="30434-114">`E`anonim bir yöntem veya lambda ifade olamaz.</span><span class="sxs-lookup"><span data-stu-id="30434-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="30434-115">Sonuç `E is T` null'suz `true` `E` ise ve bir başvuru dönüştürme, bir `T` kutulama dönüştürme veya unboxing dönüştürme tarafından türe dönüştürülebilir ifade döndürür; aksi takdirde, `false`döner .</span><span class="sxs-lookup"><span data-stu-id="30434-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="30434-116">Operatör `is` kullanıcı tanımlı dönüşümleri dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="30434-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="30434-117">Aşağıdaki örnek, bir `is` ifade `true` sonucunun çalışma zamanı türü belirli bir türden türemişse işlecinin geri döndüğünü, yani türler arasında bir başvuru dönüştürmesi olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="30434-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="30434-118">Sonraki örnek, `is` işleç dikkate boks ve unboxing dönüşümleri alır ama sayısal [dönüşümleri](../builtin-types/numeric-conversions.md)dikkate almaz gösterir:</span><span class="sxs-lookup"><span data-stu-id="30434-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="30434-119">C# dönüşümleri hakkında bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="30434-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="30434-120">Desen eşleştirmeli tür testi</span><span class="sxs-lookup"><span data-stu-id="30434-120">Type testing with pattern matching</span></span>

<span data-ttu-id="30434-121">C# 7.0 ile `is` başlayarak, işleç de bir desen karşı bir ifade sonucu test eder.</span><span class="sxs-lookup"><span data-stu-id="30434-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="30434-122">Özellikle, aşağıdaki formda tür deseni destekler:</span><span class="sxs-lookup"><span data-stu-id="30434-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="30434-123">nerede `E` bir değer döndürür `T` bir ifade, bir tür veya tür `v` parametre adıdır `T`ve tür yeni bir yerel değişkendir .</span><span class="sxs-lookup"><span data-stu-id="30434-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="30434-124">Sonucu `E` null olmayan ve bir referans, kutulama veya unboxing dönüştürme `T` tarafından dönüştürülebilir, `E is T v` ifade döndürür `true` ve `E` sonucudönüştürülen `v`değeri değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="30434-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="30434-125">Aşağıdaki örnek, `is` tür deseni ile işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="30434-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="30434-126">Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için [bkz.](../keywords/is.md#pattern-matching-with-is)</span><span class="sxs-lookup"><span data-stu-id="30434-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="30434-127">operatör olarak</span><span class="sxs-lookup"><span data-stu-id="30434-127">as operator</span></span>

<span data-ttu-id="30434-128">İşleç, `as` bir ifadenin sonucunu açıkça belirli bir başvuru veya nullable değer türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="30434-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="30434-129">Dönüştürme mümkün değilse, `as` işleç `null`döndürür.</span><span class="sxs-lookup"><span data-stu-id="30434-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="30434-130">Döküm [ifadesinin](#cast-expression) `as` aksine, işleç hiçbir zaman bir özel durum atmaz.</span><span class="sxs-lookup"><span data-stu-id="30434-130">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="30434-131">Formun ifadesi</span><span class="sxs-lookup"><span data-stu-id="30434-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="30434-132">bir `E` değer döndüren ve `T` bir tür veya tür parametresinin adı olan bir ifade, aynı sonucu</span><span class="sxs-lookup"><span data-stu-id="30434-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="30434-133">`E` bunun dışında sadece bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="30434-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="30434-134">İşletici `as` yalnızca başvuru, nullable, boxing ve unboxing dönüşümleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="30434-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="30434-135">Kullanıcı tanımlı `as` bir dönüştürme gerçekleştirmek için işleci kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="30434-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="30434-136">Bunu yapmak [için,](#cast-expression)bir döküm ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="30434-136">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="30434-137">Aşağıdaki örnek, işleç `as` kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="30434-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="30434-138">Önceki örnekte de görüldüğü gibi, dönüştürmenin `as` başarılı `null` olup olmadığını denetlemek için ifadenin sonucunu karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="30434-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="30434-139">C# 7.0 ile başlayarak, hem dönüştürmenin başarılı olup olmadığını sınamak için [is işlecini](#type-testing-with-pattern-matching) kullanabilir ve başarılı olursa sonucunu yeni bir değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30434-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="30434-140">Oyuncu ifadesi</span><span class="sxs-lookup"><span data-stu-id="30434-140">Cast expression</span></span>

<span data-ttu-id="30434-141">Formun `(T)E` döküm ifadesi, ifade `E` sonucunun türe `T`açık bir şekilde dönüştürülmesini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="30434-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="30434-142">Tür `E` `T`türünden açık bir dönüştürme yoksa derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="30434-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="30434-143">Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir döküm ifadesi bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="30434-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="30434-144">Aşağıdaki örnek, açık sayısal ve başvuru dönüşümlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="30434-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="30434-145">Desteklenen açık dönüşümler hakkında bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="30434-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="30434-146">Özel bir açık veya örtülü tür dönüştürmesinin nasıl tanımlanaaçık olduğu hakkında bilgi için [Bkz. Kullanıcı tanımlı dönüştürme operatörleri.](user-defined-conversion-operators.md)</span><span class="sxs-lookup"><span data-stu-id="30434-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="30434-147">Diğer kullanımları ()</span><span class="sxs-lookup"><span data-stu-id="30434-147">Other usages of ()</span></span>

<span data-ttu-id="30434-148">Bir [yöntemi çağırmak veya bir temsilci çağırmak](member-access-operators.md#invocation-expression-)için parantez de kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="30434-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="30434-149">Parantezin diğer kullanımı, bir ifadedeki işlemleri değerlendirmek için sırasını ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="30434-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="30434-150">Daha fazla bilgi için [C# işleçleri'ne](index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30434-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="30434-151">typeof işleci</span><span class="sxs-lookup"><span data-stu-id="30434-151">typeof operator</span></span>

<span data-ttu-id="30434-152">İşleç `typeof` bir <xref:System.Type?displayProperty=nameWithType> tür için örnek alır.</span><span class="sxs-lookup"><span data-stu-id="30434-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="30434-153">Aşağıdaki örnekte `typeof` görüldüğü gibi, işlecibağımsız değişkenbir tür veya tür parametresi adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="30434-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="30434-154">İşleç'i `typeof` bağlı olmayan genel türleri ile de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30434-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="30434-155">Bağlanmamış genel türün adı, tür parametreleri sayısından bir küçük olan uygun sayıda virgül içermelidir.</span><span class="sxs-lookup"><span data-stu-id="30434-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="30434-156">Aşağıdaki örnek, `typeof` bağlı olmayan genel türü olan işleç kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="30434-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="30434-157">Bir ifade işlecinin `typeof` bir bağımsız değişkeni olamaz.</span><span class="sxs-lookup"><span data-stu-id="30434-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="30434-158">İfade sonucunun <xref:System.Type?displayProperty=nameWithType> çalışma zamanı türünü almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="30434-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="30434-159">`typeof` Operatörle tip testi</span><span class="sxs-lookup"><span data-stu-id="30434-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="30434-160">İfade `typeof` sonucunun çalışma zamanı türünün belirli bir türle tam olarak eşleşip eşleşmeyemeyişmasını denetlemek için işleci kullanın.</span><span class="sxs-lookup"><span data-stu-id="30434-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="30434-161">Aşağıdaki örnek, `typeof` işleç ile gerçekleştirilen tür denetimi ile [İşletici](#is-operator)arasındaki farkı gösterir:</span><span class="sxs-lookup"><span data-stu-id="30434-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="30434-162">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="30434-162">Operator overloadability</span></span>

<span data-ttu-id="30434-163">`is`, `as`ve `typeof` işleçler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="30434-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="30434-164">Kullanıcı tanımlı bir tür `()` işleç aşırı yükleyemez, ancak döküm ifadesi tarafından gerçekleştirilebilecek özel tür dönüşümleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="30434-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="30434-165">Daha fazla bilgi için [Bkz. Kullanıcı tanımlı dönüşüm operatörleri.](user-defined-conversion-operators.md)</span><span class="sxs-lookup"><span data-stu-id="30434-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="30434-166">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="30434-166">C# language specification</span></span>

<span data-ttu-id="30434-167">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="30434-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="30434-168">Is işleci</span><span class="sxs-lookup"><span data-stu-id="30434-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="30434-169">As operatörü</span><span class="sxs-lookup"><span data-stu-id="30434-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="30434-170">Döküm ifadeler</span><span class="sxs-lookup"><span data-stu-id="30434-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="30434-171">Operatör türü</span><span class="sxs-lookup"><span data-stu-id="30434-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="30434-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30434-172">See also</span></span>

- [<span data-ttu-id="30434-173">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="30434-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="30434-174">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="30434-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="30434-175">Desen eşleştirme ve is ve operatörler olarak kullanarak güvenli bir şekilde döküm nasıl</span><span class="sxs-lookup"><span data-stu-id="30434-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="30434-176">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="30434-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
