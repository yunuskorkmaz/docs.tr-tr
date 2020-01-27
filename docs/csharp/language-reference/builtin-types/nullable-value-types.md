---
title: Nullable değer türleri- C# başvuru
description: Null yapılabilir C# değer türleri ve bunların nasıl kullanılacağı hakkında bilgi edinin
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 42673d16ac68bbf119e57e4c357b1b2b2a0b5c51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740939"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="27197-103">Nullable değer türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="27197-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="27197-104">Null olabilen bir değer türü `T?` temel alınan [değer `T` türünün](value-types.md) tüm değerlerini ve ek bir [null](../keywords/null.md) değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27197-104">A nullable value type `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="27197-105">Örneğin, aşağıdaki üç değerden herhangi birini bir `bool?` değişkenine atayabilirsiniz: `true`, `false`veya `null`.</span><span class="sxs-lookup"><span data-stu-id="27197-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="27197-106">Temel alınan değer türü `T`, null yapılabilir bir değer türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="27197-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="27197-107">C#8,0, Nullable başvuru türleri özelliğini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="27197-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="27197-108">Daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="27197-108">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="27197-109">Null yapılabilir değer türleri 2 ile C# başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27197-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="27197-110">Herhangi bir null yapılabilir değer türü, genel <xref:System.Nullable%601?displayProperty=nameWithType> yapısının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="27197-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="27197-111">Aşağıdaki değiştirilebilir formlardan herhangi birinde `T`, temel alınan bir tür ile null olabilen bir değer türüne başvurabilirsiniz: `Nullable<T>` veya `T?`.</span><span class="sxs-lookup"><span data-stu-id="27197-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="27197-112">Genellikle, temel alınan bir değer türünün tanımsız değerini temsil etmeniz gerektiğinde null yapılabilen bir değer türü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="27197-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="27197-113">Örneğin, bir Boolean veya `bool`, değişken yalnızca `true` ya da `false`olabilir.</span><span class="sxs-lookup"><span data-stu-id="27197-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="27197-114">Ancak bazı uygulamalarda bir değişken değeri tanımsız veya eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="27197-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="27197-115">Örneğin, bir veritabanı alanı `true` veya `false`içerebilir veya hiçbir değer içeremez, diğer bir deyişle, `NULL`.</span><span class="sxs-lookup"><span data-stu-id="27197-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="27197-116">Bu senaryodaki `bool?` türünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27197-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="27197-117">Bildirim ve atama</span><span class="sxs-lookup"><span data-stu-id="27197-117">Declaration and assignment</span></span>

<span data-ttu-id="27197-118">Değer türü, karşılık gelen null yapılabilir değer türüne örtük olarak dönüştürülebilir olduğundan, onun temel alınan değer türü için yaptığınız gibi, null olabilen değer türünde bir değişkene bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27197-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="27197-119">`null` değerini de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27197-119">You also can assign the `null` value.</span></span> <span data-ttu-id="27197-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27197-120">For example:</span></span>

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="27197-121">Null olabilen bir değer türünün varsayılan değeri `null`temsil eder, diğer bir deyişle, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> özelliği `false`döndüren bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="27197-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="27197-122">Null yapılabilir bir değer türünün örneğinin incelenmesi</span><span class="sxs-lookup"><span data-stu-id="27197-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="27197-123">7,0 ile C# başlayarak, [`is` işlecini bir tür düzeniyle birlikte](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) kullanarak `null` için null yapılabilir değer türünün bir örneğini inceleyebilir ve temel alınan bir türün değerini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27197-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="27197-124">Her zaman, null olabilen bir değer türü değişkeninin değerini incelemek ve almak için aşağıdaki salt okunurdur özelliklerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27197-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="27197-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>, null yapılabilir bir değer türünün bir örneğinin temel alınan türü bir değere sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="27197-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="27197-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>, <xref:System.Nullable%601.HasValue%2A> `true`bir temel alınan türün değerini alır.</span><span class="sxs-lookup"><span data-stu-id="27197-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="27197-127"><xref:System.Nullable%601.HasValue%2A> `false`, <xref:System.Nullable%601.Value%2A> özelliği bir <xref:System.InvalidOperationException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27197-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="27197-128">Aşağıdaki örnek, değişkenin görüntülemeden önce bir değer içerip içermediğini test etmek için `HasValue` özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="27197-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="27197-129">Ayrıca, aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünün değişkenini `HasValue` özelliğini kullanmak yerine `null` ile karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27197-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="27197-130">Null yapılabilir bir değer türünden temel alınan bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="27197-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="27197-131">Null olabilen bir değer türünün değerini null yapılamayan bir değer türü değişkenine atamak istiyorsanız, `null`yerine atanacak değeri belirtmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="27197-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="27197-132">Bunu yapmak için [null birleşim işleci `??`](../operators/null-coalescing-operator.md) kullanın (aynı amaçla <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> yöntemini de kullanabilirsiniz):</span><span class="sxs-lookup"><span data-stu-id="27197-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="27197-133">`null`yerine temel alınan değer türünün [varsayılan](default-values.md) değerini kullanmak istiyorsanız <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="27197-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="27197-134">Ayrıca, aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünü null yapılamayan bir türe açıkça çevirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27197-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

<span data-ttu-id="27197-135">Çalışma zamanında, null yapılabilir bir değer türünün değeri `null`, açık atama bir <xref:System.InvalidOperationException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27197-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="27197-136">Null yapılamayan bir değer türü `T`, örtük olarak karşılık gelen null değer türü `T?`türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="27197-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="27197-137">Yükseltilmemiş işleçleri</span><span class="sxs-lookup"><span data-stu-id="27197-137">Lifted operators</span></span>

<span data-ttu-id="27197-138">Önceden tanımlanmış birli ve ikili işleçler veya `T` bir değer türü tarafından desteklenen aşırı yüklenmiş işleçler, karşılık gelen null yapılabilir değer türü `T?`tarafından da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="27197-138">The predefined unary and binary operators or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="27197-139">*Yükseltilmemiş işleçleri*olarak da bilinen bu işleçler, bir veya her iki işlenen de `null``null` üretir; Aksi takdirde, işleç sonucu hesaplamak için işlenenlerinin kapsanan değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="27197-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="27197-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27197-140">For example:</span></span>

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="27197-141">`bool?` türü için, önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işleçlerden biri `null`olsa bile bir operatör değerlendirmesinin sonucu null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="27197-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="27197-142">Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="27197-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="27197-143">`<`, `>`, `<=`ve `>=`[karşılaştırma işleçleri](../operators/comparison-operators.md) için, bir veya her iki işlenen de `null`, sonuç `false`olur; Aksi takdirde, kapsanan işlenen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="27197-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise the contained values of operands are compared.</span></span> <span data-ttu-id="27197-144">Belirli bir karşılaştırma (örneğin, `<=`) `false`döndürdüğünden, zıt karşılaştırma (`>`) `true`döndürdüğünü varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="27197-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="27197-145">Aşağıdaki örnek, 10 ' un olduğunu gösterir</span><span class="sxs-lookup"><span data-stu-id="27197-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="27197-146">`null` büyük veya eşit değil</span><span class="sxs-lookup"><span data-stu-id="27197-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="27197-147">`null` ve küçüktür</span><span class="sxs-lookup"><span data-stu-id="27197-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="27197-148">Yukarıdaki örnek ayrıca, `null` her ikisi de `true`değerlendirilen iki null yapılabilir değer türü örneğinin eşitlik karşılaştırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="27197-148">The preceding example also shows that an equality comparison of two nullable value type instances that are both `null` evaluates to `true`.</span></span>

<span data-ttu-id="27197-149">İki değer türü arasında [Kullanıcı tanımlı bir dönüştürme](../operators/user-defined-conversion-operators.md) varsa, aynı dönüştürme karşılık gelen null atanabilir değer türleri arasında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27197-149">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="27197-150">Kutulama ve kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="27197-150">Boxing and unboxing</span></span>

<span data-ttu-id="27197-151">Null yapılabilir bir değer türü örneği, `T?` aşağıdaki gibi [kutulanır](../../programming-guide/types/boxing-and-unboxing.md) :</span><span class="sxs-lookup"><span data-stu-id="27197-151">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="27197-152"><xref:System.Nullable%601.HasValue%2A> `false`döndürürse, null başvuru üretilir.</span><span class="sxs-lookup"><span data-stu-id="27197-152">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="27197-153"><xref:System.Nullable%601.HasValue%2A> `true`döndürürse, temel alınan değer `T` türünün karşılık gelen değeri <xref:System.Nullable%601>örneği değil kutulanır.</span><span class="sxs-lookup"><span data-stu-id="27197-153">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="27197-154">Aşağıdaki örnekte gösterildiği gibi, bir değer türünün paketlenmiş değerini, karşılık gelen null değer türü `T?``T` bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27197-154">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="27197-155">Null yapılabilir değer türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="27197-155">How to identify a nullable value type</span></span>

<span data-ttu-id="27197-156">Aşağıdaki örnek, bir <xref:System.Type?displayProperty=nameWithType> örneğinin oluşturulmuş bir null yapılabilir değer türünü (yani, belirtilen tür parametresine sahip <xref:System.Nullable%601?displayProperty=nameWithType> türü) temsil edip etmediğini gösterir `T`:</span><span class="sxs-lookup"><span data-stu-id="27197-156">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="27197-157">Örnekte gösterildiği gibi, bir <xref:System.Type?displayProperty=nameWithType> örneği oluşturmak için [typeof](../operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="27197-157">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="27197-158">Bir örneğin, null yapılabilir bir değer türünde olup olmadığını anlamak istiyorsanız, yukarıdaki kodla test edilecek bir <xref:System.Type> örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="27197-158">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="27197-159">Null olabilen değer türünün bir örneğinde <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini çağırdığınızda, örnek <xref:System.Object>olarak [paketlenmelidir](#boxing-and-unboxing) .</span><span class="sxs-lookup"><span data-stu-id="27197-159">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="27197-160">Null olabilen bir değer türünün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğerdir <xref:System.Object.GetType%2A>, null olabilen bir değer türünün temel türünü temsil eden bir <xref:System.Type> örneği döndürür:</span><span class="sxs-lookup"><span data-stu-id="27197-160">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

<span data-ttu-id="27197-161">Ayrıca, bir örneğin null yapılabilir değer türünde olup olmadığını anlamak için [,](../operators/type-testing-and-cast.md#is-operator) işleç kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="27197-161">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="27197-162">Aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türü örneği ve temel alınan tür örneğini `is` işleçle ayırt edemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="27197-162">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="27197-163">Bir örneğin null yapılabilir bir değer türünde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27197-163">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="27197-164">Bu bölümde açıklanan yöntemler, [null yapılabilir başvuru türleri](../../nullable-references.md)durumunda geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="27197-164">The methods described in this section are not applicable in the case of [nullable reference types](../../nullable-references.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="27197-165">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="27197-165">C# language specification</span></span>

<span data-ttu-id="27197-166">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="27197-166">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="27197-167">Null yapılabilir türler</span><span class="sxs-lookup"><span data-stu-id="27197-167">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="27197-168">Yükseltilmemiş işleçleri</span><span class="sxs-lookup"><span data-stu-id="27197-168">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="27197-169">Örtük null yapılabilir dönüşümler</span><span class="sxs-lookup"><span data-stu-id="27197-169">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="27197-170">Açık boş değer atanabilir dönüşümler</span><span class="sxs-lookup"><span data-stu-id="27197-170">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="27197-171">Yükseltilmemiş dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="27197-171">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="27197-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27197-172">See also</span></span>

- [<span data-ttu-id="27197-173">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="27197-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="27197-174">' Yükseltilmemiş ' tam olarak ne anlama geliyor?</span><span class="sxs-lookup"><span data-stu-id="27197-174">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="27197-175">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="27197-175">Nullable reference types</span></span>](../../nullable-references.md)
