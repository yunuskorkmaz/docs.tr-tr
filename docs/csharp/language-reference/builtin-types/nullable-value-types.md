---
title: Nullable değer türleri - C# referans
description: C# nullable değer türleri ve bunları nasıl kullanacağı hakkında bilgi edinin
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: fcd49d7d25b0ad23363db8cb61596004b2e87a8d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738994"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="3a870-103">Nullable değer türleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3a870-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="3a870-104">*Nullable değer türü,* `T?` temel [değer türünün](value-types.md) `T` tüm değerlerini ve ek bir [null](../keywords/null.md) değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3a870-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="3a870-105">Örneğin, aşağıdaki üç değerden herhangi birini bir `bool?` değişkene atayabilirsiniz: `true`, `false`veya `null`.</span><span class="sxs-lookup"><span data-stu-id="3a870-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="3a870-106">Temel değer `T` türü, nullable değer türü kendisi olamaz.</span><span class="sxs-lookup"><span data-stu-id="3a870-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="3a870-107">C# 8.0 nullable başvuru türleri özelliğini tanıtür.</span><span class="sxs-lookup"><span data-stu-id="3a870-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="3a870-108">Daha fazla bilgi için [Nullable başvuru türlerine](nullable-reference-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3a870-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="3a870-109">Nullable değer türleri C # 2 ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a870-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="3a870-110">Herhangi bir nullable değer türü <xref:System.Nullable%601?displayProperty=nameWithType> genel yapının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="3a870-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="3a870-111">Aşağıdaki değiştirilebilir formlardan herhangi birinde altta `T` yatan bir türe sahip nullable değer türüne başvurabilirsiniz: `Nullable<T>` veya `T?`.</span><span class="sxs-lookup"><span data-stu-id="3a870-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="3a870-112">Temel değer türünün tanımlanmamış değerini temsil etmeniz gerektiğinde genellikle nullable değer türü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3a870-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="3a870-113">Örneğin, bir Boolean `bool`veya , değişken `true` sadece `false`ya da olabilir .</span><span class="sxs-lookup"><span data-stu-id="3a870-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="3a870-114">Ancak, bazı uygulamalarda değişken değer tanımsız veya eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a870-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="3a870-115">Örneğin, bir veritabanı alanı `true` `false`içerebilir veya , ya da hiç değer `NULL`içerebilir, yani.</span><span class="sxs-lookup"><span data-stu-id="3a870-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="3a870-116">Bu senaryoda `bool?` türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a870-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="3a870-117">Beyan ve atama</span><span class="sxs-lookup"><span data-stu-id="3a870-117">Declaration and assignment</span></span>

<span data-ttu-id="3a870-118">Değer türü dolaylı olarak karşılık gelen nullable değer türüne dönüştürülebilir olduğundan, bir değeri temel değer türü için yaptığınız gibi, nullable değer türündeki bir değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a870-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="3a870-119">`null` Değeri de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a870-119">You can also assign the `null` value.</span></span> <span data-ttu-id="3a870-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3a870-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="3a870-121">Nullable değer türünün varsayılan `null`değeri temsil eder , yani, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> bu `false`özelliği döndürür bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="3a870-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="3a870-122">Nullable değer türübir örneğin incelenmesi</span><span class="sxs-lookup"><span data-stu-id="3a870-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="3a870-123">C# 7.0 ile başlayarak, hem için nullable değer türü bir örnek incelemek `null` ve altta yatan bir tür bir değer almak için [ `is` bir tür desen ile işleci](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3a870-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="3a870-124">Nullable değer türü değişkeninin değerini incelemek ve almak için her zaman aşağıdaki salt okunur özelliklerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3a870-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="3a870-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>nullable değer türü bir örnek altta yatan türü bir değere sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a870-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="3a870-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>ise, <xref:System.Nullable%601.HasValue%2A> `true`temel bir türün değerini alır.</span><span class="sxs-lookup"><span data-stu-id="3a870-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="3a870-127">Ise, <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> özellik atar . <xref:System.InvalidOperationException> `false`</span><span class="sxs-lookup"><span data-stu-id="3a870-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="3a870-128">Aşağıdaki örnek, `HasValue` değişkenin görüntülemeden önce bir değer bulunup bulunmayacağını sınamak için özelliği kullanır:</span><span class="sxs-lookup"><span data-stu-id="3a870-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="3a870-129">Aşağıdaki örnekte görüldüğü gibi, `null` `HasValue` özelliği kullanmak yerine nullable değer türüdeğişkenini de karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3a870-129">You can also compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="3a870-130">Geçersiz bir değer türünden temel bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3a870-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="3a870-131">Nullable değer türü bir değer türünü nullable olmayan bir değer türü değişkenine atamak istiyorsanız, `null`''nin yerine atanacak değeri belirtmeniz gerekebilir</span><span class="sxs-lookup"><span data-stu-id="3a870-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="3a870-132">Bunu yapmak için [null-coalescing işleci `??` ](../operators/null-coalescing-operator.md) kullanın <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> (aynı amaç için de yöntemi kullanabilirsiniz):</span><span class="sxs-lookup"><span data-stu-id="3a870-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you can also use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="3a870-133">Yerine temel değer türünün [varsayılan](default-values.md) değerini kullanmak `null`istiyorsanız, <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a870-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="3a870-134">Aşağıdaki örnekte görüldüğü gibi, nullable değer türünü de açıkça nullable olmayan bir türe atabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3a870-134">You can also explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="3a870-135">Çalışma zamanında, nullable değer türünün değeri `null`ise, açık döküm <xref:System.InvalidOperationException>bir .</span><span class="sxs-lookup"><span data-stu-id="3a870-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="3a870-136">Nullable değer türü `T` dolaylı olarak karşılık gelen nullable değer `T?`türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="3a870-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="3a870-137">Kaldırılan operatörler</span><span class="sxs-lookup"><span data-stu-id="3a870-137">Lifted operators</span></span>

<span data-ttu-id="3a870-138">Önceden tanımlanmış unary ve ikili [işleçler](../operators/index.md) veya bir değer `T` türü tarafından desteklenen herhangi bir aşırı `T?`yüklü işleçleri de ilgili nullable değer türü tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3a870-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="3a870-139">Bu operatörler, aynı zamanda *kaldırılan operatörler*olarak bilinen, `null`bir veya her iki operands ise üretmek; `null` aksi takdirde, işleç sonucu hesaplamak için operands içerdiği değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a870-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="3a870-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3a870-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="3a870-141">`bool?` Türü için, önceden `&` tanımlanmış `|` ve işleçler bu bölümde açıklanan kurallara uymaz: operands biri olsa bile bir `null`operatör değerlendirme sonucu geçersiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a870-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="3a870-142">Daha fazla bilgi için [Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3a870-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="3a870-143">Karşılaştırma [işleçleri](../operators/comparison-operators.md) `<` `<=`için `>=`, `>`, , ve , `null`eğer bir `false`veya her iki operands , sonuç; aksi takdirde, operands içerdiği değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="3a870-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="3a870-144">Belirli bir karşılaştırma `<=`(örneğin, ) döndürür `false`çünkü,`>`ters `true`karşılaştırma ( ) döndürür varsaymayın .</span><span class="sxs-lookup"><span data-stu-id="3a870-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="3a870-145">Aşağıdaki örnek, 10'un</span><span class="sxs-lookup"><span data-stu-id="3a870-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="3a870-146">ne büyük ya da eşit`null`</span><span class="sxs-lookup"><span data-stu-id="3a870-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="3a870-147">ne de daha az`null`</span><span class="sxs-lookup"><span data-stu-id="3a870-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="3a870-148">Eşitlik [işleci](../operators/equality-operators.md#equality-operator-) `==`için, her iki operands `null` `true`ise , sonuç , eğer sadece `null`bir operands , sonuç; `false` aksi takdirde, operands içerdiği değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="3a870-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="3a870-149">Eşitsizlik [işleci](../operators/equality-operators.md#inequality-operator-) `!=`için , her iki `null`operands `false`ise , sonuç , eğer sadece `null`bir operands , sonuç; `true` aksi takdirde, operands içerdiği değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="3a870-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="3a870-150">İki değer türü arasında [kullanıcı tanımlı](../operators/user-defined-conversion-operators.md) bir dönüştürme varsa, aynı dönüştürme karşılık gelen nullable değer türleri arasında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a870-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="3a870-151">Boks ve unboxing</span><span class="sxs-lookup"><span data-stu-id="3a870-151">Boxing and unboxing</span></span>

<span data-ttu-id="3a870-152">Nullable değer türü `T?` örneği aşağıdaki gibi [kutulanır:](../../programming-guide/types/boxing-and-unboxing.md)</span><span class="sxs-lookup"><span data-stu-id="3a870-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="3a870-153">İade <xref:System.Nullable%601.HasValue%2A> `false`edilirse, null başvuru üretilir.</span><span class="sxs-lookup"><span data-stu-id="3a870-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="3a870-154">İade <xref:System.Nullable%601.HasValue%2A> `true`edilirse, alttaki değer türünün `T` karşılık gelen değeri <xref:System.Nullable%601>kutulanır, '' örneğini değil.</span><span class="sxs-lookup"><span data-stu-id="3a870-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="3a870-155">Aşağıdaki örnekte görüldüğü gibi, ilgili `T` nullable değer türüne `T?`bir değer türünün kutulanmış değerini açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3a870-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="3a870-156">Nullable değer türünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a870-156">How to identify a nullable value type</span></span>

<span data-ttu-id="3a870-157">Aşağıdaki örnek, bir <xref:System.Type?displayProperty=nameWithType> örneğin oluşturulmuş bir nullable değer türünü, yani <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen tür parametresi `T`olan türü temsil edip etmediğini nasıl belirleyeceklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="3a870-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="3a870-158">Örnekte görüldüğü gibi, [typeof](../operators/type-testing-and-cast.md#typeof-operator) bir <xref:System.Type?displayProperty=nameWithType> örnek oluşturmak için işleç türünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3a870-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="3a870-159">Bir örneğin boş değer türüne sahip olup olmadığını belirlemek istiyorsanız, <xref:System.Object.GetType%2A?displayProperty=nameWithType> bir <xref:System.Type> örneğin önceki kodla sınanmasını sağlamak için yöntemi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3a870-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="3a870-160">Metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> nullable değer türü örneğinde çağırdığınızda, [boxed](#boxing-and-unboxing) örnek <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="3a870-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="3a870-161">Nullable değer türünün null olmayan bir örneğinin kutulaması, temel türün <xref:System.Object.GetType%2A> bir <xref:System.Type> değerinin kutulatılabilir bir değeri ne eşdeğer olduğundan, temel değer türünü temsil eden bir örneği döndürür:</span><span class="sxs-lookup"><span data-stu-id="3a870-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="3a870-162">Ayrıca, bir örneğin nullable değer türüolup olmadığını belirlemek için [is](../operators/type-testing-and-cast.md#is-operator) işleci kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3a870-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="3a870-163">Aşağıdaki örnekte de görüldüğü gibi, nullable değer türü örneğinin türlerini `is` ve onun temel türü örneğini işleçle ayırt edemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="3a870-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="3a870-164">Bir örneğin nullable değer türüne ait olup olmadığını belirlemek için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3a870-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="3a870-165">Bu bölümde açıklanan yöntemler [geçersiz başvuru türleri](nullable-reference-types.md)durumunda geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3a870-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3a870-166">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3a870-166">C# language specification</span></span>

<span data-ttu-id="3a870-167">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="3a870-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="3a870-168">Nullable türleri</span><span class="sxs-lookup"><span data-stu-id="3a870-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="3a870-169">Kaldırılan operatörler</span><span class="sxs-lookup"><span data-stu-id="3a870-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="3a870-170">Örtülü nullable dönüşümler</span><span class="sxs-lookup"><span data-stu-id="3a870-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="3a870-171">Açık geçersiz dönüşümler</span><span class="sxs-lookup"><span data-stu-id="3a870-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="3a870-172">Kaldırılan dönüşüm operatörleri</span><span class="sxs-lookup"><span data-stu-id="3a870-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="3a870-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a870-173">See also</span></span>

- [<span data-ttu-id="3a870-174">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3a870-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3a870-175">'Kaldırdı' tam olarak ne anlama geliyor?</span><span class="sxs-lookup"><span data-stu-id="3a870-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3a870-176">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="3a870-176">Nullable reference types</span></span>](nullable-reference-types.md)
