---
title: Tür-test ve dönüştürme işleçleri- C# başvuru
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
ms.openlocfilehash: 81e7678bc21529c159b8137b06b93774af0ff434
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796491"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a><span data-ttu-id="01efe-103">Tür-test ve dönüştürme işleçleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="01efe-103">Type-testing and conversion operators (C# reference)</span></span>

<span data-ttu-id="01efe-104">Tür denetimi veya tür dönüştürme gerçekleştirmek için aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="01efe-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="01efe-105">[işleç](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="01efe-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="01efe-106">[as işleci](#as-operator): çalışma zamanı türü bu türle uyumluysa bir ifadeyi açıkça belirli bir türe dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="01efe-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="01efe-107">[cast işleci ()](#cast-operator-): açık bir dönüştürme gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="01efe-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="01efe-108">[typeof işleci](#typeof-operator): bir türün <xref:System.Type?displayProperty=nameWithType> örneğini almak için</span><span class="sxs-lookup"><span data-stu-id="01efe-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="01efe-109">işleç</span><span class="sxs-lookup"><span data-stu-id="01efe-109">is operator</span></span>

<span data-ttu-id="01efe-110">`is` İşleci, bir ifade sonucunun çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="01efe-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="01efe-111">`is` Operatör 7,0 C# ' den itibaren bir ifade sonucunu bir düzene göre de sınar.</span><span class="sxs-lookup"><span data-stu-id="01efe-111">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="01efe-112">Type-Testing `is` işlecine sahip ifade aşağıdaki biçimdedir</span><span class="sxs-lookup"><span data-stu-id="01efe-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="01efe-113">, bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir. `E`</span><span class="sxs-lookup"><span data-stu-id="01efe-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="01efe-114">`E`anonim bir yöntem veya lambda ifadesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="01efe-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="01efe-115">`false` `T` `true` İfadesi, sonucu`E` null olmayan ve bir başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürmesi tarafından türe dönüştürülebileceğinden, öğesini döndürür; Aksi takdirde, döndürür. `E is T`</span><span class="sxs-lookup"><span data-stu-id="01efe-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="01efe-116">`is` İşleci Kullanıcı tanımlı dönüştürmeleri dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="01efe-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="01efe-117">Aşağıdaki örnek, bir ifade sonucunun `is` çalışma zamanı `true` türü verilen bir türden türetilse, yani türler arasında bir başvuru dönüştürmesi varsa, işlecinin döndürdüğü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="01efe-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="01efe-118">Sonraki örnekte, `is` işlecin hesap paketleme ve kutudan çıkarma dönüştürmelerinin gösterdiği ancak sayısal dönüştürmeleri düşünmeyen bir örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="01efe-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider numeric conversions:</span></span>

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="01efe-119">Dönüşümler hakkında C# daha fazla bilgi için bkz. [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="01efe-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="01efe-120">Model eşleştirme ile test türü</span><span class="sxs-lookup"><span data-stu-id="01efe-120">Type testing with pattern matching</span></span>

<span data-ttu-id="01efe-121">`is` Operatör 7,0 C# ' den itibaren bir ifade sonucunu bir düzene göre de sınar.</span><span class="sxs-lookup"><span data-stu-id="01efe-121">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="01efe-122">Özellikle, aşağıdaki biçimde tür düzenlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="01efe-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="01efe-123">, bir `v` değer döndüren bir ifade, bir tür veya tür parametresinin adıdır ve yeni bir yerel değişken türünde `T`. `T` `E`</span><span class="sxs-lookup"><span data-stu-id="01efe-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="01efe-124">Sonucu `E` null olmayan ve bir başvuru, paketleme `E is T v` veya kutudan çıkarma dönüştürmesi tarafından `T` ' e dönüştürülebiliyorsanız, ifade döner `true` ve şuna atanan sonuç `E` değeri değişken `v`.</span><span class="sxs-lookup"><span data-stu-id="01efe-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="01efe-125">Aşağıdaki örnek, `is` işleç kullanımını tür düzeniyle birlikte gösterir:</span><span class="sxs-lookup"><span data-stu-id="01efe-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="01efe-126">Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için, bkz. [deseniyle eşleme](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="01efe-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="01efe-127">as işleci</span><span class="sxs-lookup"><span data-stu-id="01efe-127">as operator</span></span>

<span data-ttu-id="01efe-128">`as` İşleci, bir ifadenin sonucunu açıkça belirli bir başvuruya veya null yapılabilir değer türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="01efe-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="01efe-129">Dönüştürme mümkün değilse, `as` işleç döndürülür. `null`</span><span class="sxs-lookup"><span data-stu-id="01efe-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="01efe-130">[Atama işlecinin ()](#cast-operator-)aksine, `as` işleç hiçbir şekilde özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="01efe-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="01efe-131">Formun ifadesi</span><span class="sxs-lookup"><span data-stu-id="01efe-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="01efe-132">, bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir, aynı sonucu şöyle üretir `E`</span><span class="sxs-lookup"><span data-stu-id="01efe-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="01efe-133">`E` hariç yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="01efe-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="01efe-134">`as` İşleci yalnızca başvuru, null yapılabilir, kutulama ve kutudan çıkarma dönüştürmelerini dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="01efe-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="01efe-135">Kullanıcı tanımlı bir dönüştürme `as` gerçekleştirmek için işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="01efe-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="01efe-136">Bunu yapmak için, [cast işlecini ()](#cast-operator-)kullanın.</span><span class="sxs-lookup"><span data-stu-id="01efe-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="01efe-137">Aşağıdaki örnek `as` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="01efe-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="01efe-138">Yukarıdaki örnekte gösterildiği gibi, dönüştürmenin başarılı olup olmadığını kontrol `as` `null` etmek için ifadesinin sonucunu karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01efe-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="01efe-139">7,0 ile C# başlayarak, dönüştürme işleminin başarılı olup olmadığını test etmek için, her iki [işleci](#type-testing-with-pattern-matching) de kullanabilirsiniz ve başarılı olursa sonucunu yeni bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="01efe-139">Starting with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="01efe-140">Cast işleci ()</span><span class="sxs-lookup"><span data-stu-id="01efe-140">Cast operator ()</span></span>

<span data-ttu-id="01efe-141">Formun `(T)E` bir atama ifadesi, ifadenin `E` sonucunun türüne `T`açık bir şekilde dönüştürülmesini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="01efe-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="01efe-142">Türünden türüne hiçbir açık dönüştürme `E` `T`yoksa, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="01efe-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="01efe-143">Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir atama ifadesi bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="01efe-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="01efe-144">Aşağıdaki örnek, açık sayısal ve başvuru dönüştürmelerini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="01efe-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="01efe-145">Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="01efe-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="01efe-146">Özel bir açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="01efe-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="01efe-147">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="01efe-147">Other usages of ()</span></span>

<span data-ttu-id="01efe-148">Ayrıca, [bir yöntemi çağırmak veya bir temsilciyi çağırmak](member-access-operators.md#invocation-operator-)için parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01efe-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="01efe-149">Diğer parantez kullanımı, bir ifadede işlemlerin değerlendirileceği sırayı belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="01efe-149">Other use of parentheses is to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="01efe-150">Daha fazla bilgi için [işleçler](../../programming-guide/statements-expressions-operators/operators.md) makalesinin [parantezler ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="01efe-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="01efe-151">Öncelik düzeyine göre sıralanan işleçlerin listesi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="01efe-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="01efe-152">typeof işleci</span><span class="sxs-lookup"><span data-stu-id="01efe-152">typeof operator</span></span>

<span data-ttu-id="01efe-153">İşleci bir tür için <xref:System.Type?displayProperty=nameWithType> örneği edinir. `typeof`</span><span class="sxs-lookup"><span data-stu-id="01efe-153">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="01efe-154">Aşağıdaki örnekte gösterildiği gibi `typeof` , işlecin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="01efe-154">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="01efe-155">`typeof` İşleci ilişkisiz genel türler ile de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01efe-155">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="01efe-156">İlişkisiz genel türün adı, tür parametrelerinin sayısından küçük olan uygun sayıda virgül içermelidir.</span><span class="sxs-lookup"><span data-stu-id="01efe-156">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="01efe-157">Aşağıdaki örnek, sınırsız bir genel türü olan `typeof` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="01efe-157">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="01efe-158">İfade, `typeof` işlecin bağımsız değişkeni olamaz.</span><span class="sxs-lookup"><span data-stu-id="01efe-158">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="01efe-159">İfade sonucunun çalışma <xref:System.Type?displayProperty=nameWithType> zamanı türünün örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="01efe-159">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of the expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="01efe-160">`typeof` İşleci ile test türü</span><span class="sxs-lookup"><span data-stu-id="01efe-160">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="01efe-161">İfade sonucunun çalışma zamanı türünün verilen bir türle tam olarak eşleşip eşleşmediğini denetlemek için işlecinikullanın.`typeof`</span><span class="sxs-lookup"><span data-stu-id="01efe-161">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="01efe-162">Aşağıdaki örnek, `typeof` işleç ve işleç [işleci](#is-operator)ile gerçekleştirilen tür denetimi arasındaki farkı gösterir:</span><span class="sxs-lookup"><span data-stu-id="01efe-162">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="01efe-163">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="01efe-163">Operator overloadability</span></span>

<span data-ttu-id="01efe-164">`is`, Veişleçleri`typeof`aşırıyüklenebilirdeğildir. `as`</span><span class="sxs-lookup"><span data-stu-id="01efe-164">The `is`, `as`, and `typeof` operators are not overloadable.</span></span>

<span data-ttu-id="01efe-165">Kullanıcı tanımlı bir tür `()` işleci aşırı yükleyemez, ancak bir atama ifadesi tarafından gerçekleştirilebilecek özel tür dönüştürmeleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="01efe-165">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="01efe-166">Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="01efe-166">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="01efe-167">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="01efe-167">C# language specification</span></span>

<span data-ttu-id="01efe-168">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="01efe-168">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="01efe-169">SIS işleci</span><span class="sxs-lookup"><span data-stu-id="01efe-169">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="01efe-170">As işleci</span><span class="sxs-lookup"><span data-stu-id="01efe-170">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="01efe-171">Atama ifadeleri</span><span class="sxs-lookup"><span data-stu-id="01efe-171">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="01efe-172">Typeof işleci</span><span class="sxs-lookup"><span data-stu-id="01efe-172">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="01efe-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01efe-173">See also</span></span>

- [<span data-ttu-id="01efe-174">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="01efe-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="01efe-175">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="01efe-175">C# operators</span></span>](index.md)
- [<span data-ttu-id="01efe-176">Nasıl yapılır: model eşleştirme ve ve olarak işleç kullanarak güvenli bir şekilde atama</span><span class="sxs-lookup"><span data-stu-id="01efe-176">How to: safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
