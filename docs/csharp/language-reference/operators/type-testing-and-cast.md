---
title: Tür testi ve atama işleçleri- C# başvuru
description: Bir ifade C# sonucunun türünü denetlemek ve gerekirse başka bir türe dönüştürmek için kullanabileceğiniz işleçler hakkında bilgi edinin.
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
ms.openlocfilehash: c29833ece83e386446aaf0a5d242bda366cbfbb0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239046"
---
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="1210c-103">Tür-test ve atama işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="1210c-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="1210c-104">Tür denetimi veya tür dönüştürme gerçekleştirmek için aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1210c-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="1210c-105">[işleç](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="1210c-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="1210c-106">[as işleci](#as-operator): çalışma zamanı türü bu türle uyumluysa bir ifadeyi açıkça belirli bir türe dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1210c-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="1210c-107">[cast işleci ()](#cast-operator-): açık bir dönüştürme gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1210c-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="1210c-108">[typeof işleci](#typeof-operator): bir türün <xref:System.Type?displayProperty=nameWithType> örneğini almak için</span><span class="sxs-lookup"><span data-stu-id="1210c-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="1210c-109">işleç</span><span class="sxs-lookup"><span data-stu-id="1210c-109">is operator</span></span>

<span data-ttu-id="1210c-110">`is` işleci, bir ifade sonucunun çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1210c-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="1210c-111">C# 7,0 ' den başlayarak, `is` işleci bir düzene karşı bir ifade sonucunu da sınar.</span><span class="sxs-lookup"><span data-stu-id="1210c-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="1210c-112">Tür-test `is` işleci olan ifade aşağıdaki biçimdedir</span><span class="sxs-lookup"><span data-stu-id="1210c-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="1210c-113">Burada `E` bir değer döndüren bir ifadedir ve `T` bir türün veya bir tür parametresinin adıdır.</span><span class="sxs-lookup"><span data-stu-id="1210c-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="1210c-114">`E` anonim bir yöntem veya lambda ifadesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="1210c-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="1210c-115">`E is T` ifadesi, `E` sonucu null değilse ve bir başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürmesi tarafından `T` türüne dönüştürülebiliyorsanız `true` döndürür. Aksi takdirde, `false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="1210c-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="1210c-116">`is` işleci Kullanıcı tanımlı dönüştürmeleri dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="1210c-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="1210c-117">Aşağıdaki örnek, bir ifade sonucunun çalışma zamanı türü verilen bir türden türetilse, yani türler arasında bir başvuru dönüştürmesi varsa `is` işlecinin `true` döndürdüğünü gösterir:</span><span class="sxs-lookup"><span data-stu-id="1210c-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="1210c-118">Sonraki örnek, `is` işlecinin hesap paketleme ve kutudan çıkarma dönüştürmelerine sahip olduğunu ancak [sayısal dönüştürmeleri](../builtin-types/numeric-conversions.md)düşünmediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="1210c-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="1210c-119">Dönüşümler hakkında C# daha fazla bilgi için bkz. [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="1210c-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="1210c-120">Model eşleştirme ile test türü</span><span class="sxs-lookup"><span data-stu-id="1210c-120">Type testing with pattern matching</span></span>

<span data-ttu-id="1210c-121">C# 7,0 ' den başlayarak, `is` işleci bir düzene karşı bir ifade sonucunu da sınar.</span><span class="sxs-lookup"><span data-stu-id="1210c-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="1210c-122">Özellikle, aşağıdaki biçimde tür düzenlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="1210c-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="1210c-123">`E`, bir değer döndüren bir ifadedir, `T` bir tür ya da bir tür parametresidir ve `v` `T`türünde yeni bir yerel değişkendir.</span><span class="sxs-lookup"><span data-stu-id="1210c-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="1210c-124">`E` sonucu null değilse ve bir başvuru, paketleme veya kutudan çıkarma dönüştürmesi tarafından `T` dönüştürülebiliyorsanız, `E is T v` ifadesi `true` döndürür ve `E` sonucunun dönüştürülmüş değeri değişken `v`atanır.</span><span class="sxs-lookup"><span data-stu-id="1210c-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="1210c-125">Aşağıdaki örnek, `is` işlecinin tür düzeniyle kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1210c-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="1210c-126">Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için, bkz. [deseniyle eşleme](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="1210c-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="1210c-127">as işleci</span><span class="sxs-lookup"><span data-stu-id="1210c-127">as operator</span></span>

<span data-ttu-id="1210c-128">`as` işleci, bir ifadenin sonucunu açıkça belirli bir başvuruya veya null yapılabilir değer türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1210c-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="1210c-129">Dönüştürme mümkün değilse, `as` işleci `null`döndürür.</span><span class="sxs-lookup"><span data-stu-id="1210c-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="1210c-130">[Atama işlecinin ()](#cast-operator-)aksine, `as` işleci hiçbir şekilde özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1210c-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="1210c-131">Formun ifadesi</span><span class="sxs-lookup"><span data-stu-id="1210c-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="1210c-132">`E`, bir değer döndüren ve `T` bir tür veya tür parametresinin adı olan bir ifadedir, aynı sonucu şöyle üretir</span><span class="sxs-lookup"><span data-stu-id="1210c-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="1210c-133">`E` hariç, yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1210c-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="1210c-134">`as` işleci yalnızca başvuru, null yapılabilir, kutulama ve kutudan çıkarma dönüştürmelerini dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="1210c-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="1210c-135">Kullanıcı tanımlı bir dönüştürme gerçekleştirmek için `as` işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1210c-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="1210c-136">Bunu yapmak için, [cast işlecini ()](#cast-operator-)kullanın.</span><span class="sxs-lookup"><span data-stu-id="1210c-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="1210c-137">Aşağıdaki örnek `as` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1210c-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="1210c-138">Yukarıdaki örnekte gösterildiği gibi, dönüştürmenin başarılı olup olmadığını denetlemek için `as` ifadesinin sonucunu `null` karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1210c-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="1210c-139">7,0 ' C# den başlayarak, dönüştürmenin başarılı olup olmadığını test etmek için, her iki [işleci](#type-testing-with-pattern-matching) de kullanabilirsiniz ve başarılı olursa, sonucunu yeni bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="1210c-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="1210c-140">Cast işleci ()</span><span class="sxs-lookup"><span data-stu-id="1210c-140">Cast operator ()</span></span>

<span data-ttu-id="1210c-141">Form `(T)E` bir atama ifadesi, `T`yazmak için ifade `E` sonucunun açık bir şekilde dönüştürülmesini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1210c-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="1210c-142">`E` türünden `T`türüne açık bir dönüştürme yoksa, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="1210c-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="1210c-143">Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir atama ifadesi bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1210c-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="1210c-144">Aşağıdaki örnek, açık sayısal ve başvuru dönüştürmelerini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="1210c-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="1210c-145">Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1210c-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="1210c-146">Özel bir açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1210c-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="1210c-147">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="1210c-147">Other usages of ()</span></span>

<span data-ttu-id="1210c-148">Ayrıca, [bir yöntemi çağırmak veya bir temsilciyi çağırmak](member-access-operators.md#invocation-operator-)için parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1210c-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="1210c-149">Diğer parantez kullanımı, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamadır.</span><span class="sxs-lookup"><span data-stu-id="1210c-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="1210c-150">Daha fazla bilgi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="1210c-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="1210c-151">typeof işleci</span><span class="sxs-lookup"><span data-stu-id="1210c-151">typeof operator</span></span>

<span data-ttu-id="1210c-152">`typeof` işleci bir tür için <xref:System.Type?displayProperty=nameWithType> örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="1210c-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="1210c-153">Aşağıdaki örnekte gösterildiği gibi `typeof` işlecinin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="1210c-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="1210c-154">`typeof` işlecini ilişkisiz genel türlerle de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1210c-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="1210c-155">İlişkisiz genel türün adı, tür parametrelerinin sayısından küçük olan uygun sayıda virgül içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1210c-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="1210c-156">Aşağıdaki örnek, `typeof` işlecinin ilişkisiz genel bir tür kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1210c-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="1210c-157">İfade `typeof` işlecinin bağımsız değişkeni olamaz.</span><span class="sxs-lookup"><span data-stu-id="1210c-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="1210c-158">Bir ifade sonucunun çalışma zamanı türü <xref:System.Type?displayProperty=nameWithType> örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1210c-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="1210c-159">`typeof` işleci ile test yazın</span><span class="sxs-lookup"><span data-stu-id="1210c-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="1210c-160">İfade sonucunun çalışma zamanı türünün verilen bir türle tam olarak eşleşip eşleşmediğini denetlemek için `typeof` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1210c-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="1210c-161">Aşağıdaki örnek, `typeof` işleci ve [işleç işleci](#is-operator)ile gerçekleştirilen tür denetimi arasındaki farkı gösterir:</span><span class="sxs-lookup"><span data-stu-id="1210c-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="1210c-162">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="1210c-162">Operator overloadability</span></span>

<span data-ttu-id="1210c-163">`is`, `as`ve `typeof` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="1210c-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="1210c-164">Kullanıcı tanımlı bir tür `()` işlecini aşırı yükleyemez, ancak bir atama ifadesi tarafından gerçekleştirilebilecek özel tür dönüştürmeleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1210c-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="1210c-165">Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1210c-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1210c-166">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1210c-166">C# language specification</span></span>

<span data-ttu-id="1210c-167">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="1210c-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="1210c-168">SIS işleci</span><span class="sxs-lookup"><span data-stu-id="1210c-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="1210c-169">As işleci</span><span class="sxs-lookup"><span data-stu-id="1210c-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="1210c-170">Atama ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1210c-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="1210c-171">Typeof işleci</span><span class="sxs-lookup"><span data-stu-id="1210c-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="1210c-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1210c-172">See also</span></span>

- [<span data-ttu-id="1210c-173">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="1210c-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1210c-174">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="1210c-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="1210c-175">Desenler ve as işleçlerini kullanarak güvenli bir şekilde atama</span><span class="sxs-lookup"><span data-stu-id="1210c-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="1210c-176">.NET 'teki genel türler</span><span class="sxs-lookup"><span data-stu-id="1210c-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
