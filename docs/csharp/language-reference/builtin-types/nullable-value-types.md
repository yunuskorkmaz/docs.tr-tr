---
title: Nullable değer türleri-C# başvurusu
description: C# Nullable değer türleri ve bunların nasıl kullanılacağı hakkında bilgi edinin
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 8c3a8b997fbb8154f79dff04018cf3ea76f85d7a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537359"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="66cc3-103">Nullable değer türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="66cc3-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="66cc3-104">*Null yapılabilir bir değer türü* , `T?` temel alınan [değer türünün](value-types.md) tüm değerlerini `T` ve ek bir [null](../keywords/null.md) değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="66cc3-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="66cc3-105">Örneğin, aşağıdaki üç değerden herhangi birini bir `bool?` değişkene atayabilirsiniz: `true` , `false` veya `null` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="66cc3-106">Temel alınan değer türü `T` null yapılabilir bir değer türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="66cc3-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="66cc3-107">C# 8,0, Nullable başvuru türleri özelliğini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="66cc3-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="66cc3-108">Daha fazla bilgi için bkz. [Nullable başvuru türleri](nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="66cc3-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="66cc3-109">Nullable değer türleri C# 2 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66cc3-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="66cc3-110">Herhangi bir null yapılabilir değer türü, genel yapının bir örneğidir <xref:System.Nullable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66cc3-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="66cc3-111">Aşağıdaki her türlü değiştirilebilir formdan bir temel alınan tür ile null yapılabilir bir değer türüne başvurabilirsiniz `T` : `Nullable<T>` veya `T?` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="66cc3-112">Genellikle, temel alınan bir değer türünün tanımsız değerini temsil etmeniz gerektiğinde null yapılabilen bir değer türü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="66cc3-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="66cc3-113">Örneğin, bir Boolean veya `bool` değişken yalnızca ya da olabilir `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="66cc3-114">Ancak bazı uygulamalarda bir değişken değeri tanımsız veya eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="66cc3-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="66cc3-115">Örneğin, bir veritabanı alanı `true` veya içerebilir `false` veya hiçbir değer içeremez, yani, `NULL` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="66cc3-116">`bool?`Bu senaryodaki türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66cc3-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="66cc3-117">Bildirim ve atama</span><span class="sxs-lookup"><span data-stu-id="66cc3-117">Declaration and assignment</span></span>

<span data-ttu-id="66cc3-118">Değer türü, karşılık gelen null yapılabilir değer türüne örtük olarak dönüştürülebilir olduğundan, onun temel alınan değer türü için yaptığınız gibi, null olabilen değer türünde bir değişkene bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66cc3-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="66cc3-119">Ayrıca değeri de atayabilirsiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-119">You can also assign the `null` value.</span></span> <span data-ttu-id="66cc3-120">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66cc3-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="66cc3-121">Null olabilen bir değer türünün varsayılan değeri temsil eder `null` , diğer bir deyişle, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> özelliği işlevinin döndürdüğü bir örneğidir `false` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="66cc3-122">Null yapılabilir bir değer türünün örneğinin incelenmesi</span><span class="sxs-lookup"><span data-stu-id="66cc3-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="66cc3-123">C# 7,0 ' den başlayarak [ `is` işleci bir tür düzeniyle birlikte](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) kullanarak, için null olabilen değer türünün bir örneğini inceleyebilir `null` ve temel alınan bir türün değerini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66cc3-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="66cc3-124">Her zaman, null olabilen bir değer türü değişkeninin değerini incelemek ve almak için aşağıdaki salt okunurdur özelliklerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66cc3-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="66cc3-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> null yapılabilir bir değer türünün bir örneğinin temel alınan türünün bir değeri olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="66cc3-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="66cc3-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> ise, temel alınan bir türün değerini alır <xref:System.Nullable%601.HasValue%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="66cc3-127"><xref:System.Nullable%601.HasValue%2A>İse `false` , <xref:System.Nullable%601.Value%2A> özelliği bir oluşturur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="66cc3-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="66cc3-128">Aşağıdaki örnek, `HasValue` değişkenin görüntülemeden önce bir değer içerip içermediğini test etmek için özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="66cc3-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="66cc3-129">Ayrıca `null` `HasValue` , aşağıdaki örnekte gösterildiği gibi, null atanabilir bir değer türünün değişkenini özelliğini kullanmak yerine ile karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66cc3-129">You can also compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="66cc3-130">Null yapılabilir bir değer türünden temel alınan bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="66cc3-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="66cc3-131">Null olabilen bir değer türünün değerini null yapılamayan bir değer türü değişkenine atamak istiyorsanız, yerine atanacak değeri belirtmeniz gerekebilir `null` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="66cc3-132">Bunu yapmak için [null birleşim işlecini `??` ](../operators/null-coalescing-operator.md) kullanın ( <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> aynı amaçla yöntemini de kullanabilirsiniz):</span><span class="sxs-lookup"><span data-stu-id="66cc3-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you can also use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="66cc3-133">Yerine temel alınan değer türünün [varsayılan](default-values.md) değerini kullanmak istiyorsanız `null` <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="66cc3-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="66cc3-134">Ayrıca, aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünü null yapılamayan bir türe açıkça çevirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66cc3-134">You can also explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="66cc3-135">Çalışma zamanında, null yapılabilir bir değer türünün değeri ise `null` , açık atama bir oluşturur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="66cc3-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="66cc3-136">Null yapılamayan bir değer türü, `T` karşılık gelen null yapılabilir değer türüne örtük olarak dönüştürülebilir `T?` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="66cc3-137">Yükseltilmemiş işleçleri</span><span class="sxs-lookup"><span data-stu-id="66cc3-137">Lifted operators</span></span>

<span data-ttu-id="66cc3-138">Önceden tanımlanmış birli ve ikili [işleçler](../operators/index.md) ya da bir değer türü tarafından desteklenen aşırı yüklenmiş işleçler, `T` karşılık gelen Nullable değer türü tarafından da desteklenir `T?` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="66cc3-139">*Yükseltilmemiş işleçleri*olarak da bilinen bu işleçler, `null` bir veya her iki işlenen ise üretir `null` ; Aksi takdirde işleç, sonucu hesaplamak için işlenenlerinin kapsanan değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="66cc3-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="66cc3-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66cc3-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="66cc3-141">Türü için `bool?` , önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işleçlerden biri olsa bile bir operatör değerlendirmesinin sonucu null olmamalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="66cc3-142">Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66cc3-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="66cc3-143">[Karşılaştırma işleçleri](../operators/comparison-operators.md) ,, `<` `>` `<=` ve `>=` bir veya her iki işlenen ise `null` sonuç olur `false` ; Aksi takdirde, kapsanan işlenen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="66cc3-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="66cc3-144">Belirli bir karşılaştırma (örneğin, `<=` ) döndürdüğünden `false` , zıt karşılaştırma ( `>` ) işlevinin döndürdüğü varsayılmayın `true` .</span><span class="sxs-lookup"><span data-stu-id="66cc3-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="66cc3-145">Aşağıdaki örnek, 10 ' un olduğunu gösterir</span><span class="sxs-lookup"><span data-stu-id="66cc3-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="66cc3-146">Ne büyük ne de eşittir `null`</span><span class="sxs-lookup"><span data-stu-id="66cc3-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="66cc3-147">ya da küçüktür `null`</span><span class="sxs-lookup"><span data-stu-id="66cc3-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="66cc3-148">[Eşitlik işleci](../operators/equality-operators.md#equality-operator-) için, her iki işlenen de, sonuç ise, sonuç olur `==` `null` `true` `null` `false` ; Aksi takdirde, kapsanan işlenen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="66cc3-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="66cc3-149">[Eşitsizlik işleci](../operators/equality-operators.md#inequality-operator-) için, `!=` her iki işlenen de ise `null` sonuç olur `false` `null` ; Aksi takdirde, işlenen, `true` işlenen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="66cc3-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="66cc3-150">İki değer türü arasında [Kullanıcı tanımlı bir dönüştürme](../operators/user-defined-conversion-operators.md) varsa, aynı dönüştürme karşılık gelen null atanabilir değer türleri arasında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66cc3-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="66cc3-151">Kutulama ve kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="66cc3-151">Boxing and unboxing</span></span>

<span data-ttu-id="66cc3-152">Null yapılabilir değer türünün bir örneği `T?` aşağıdaki gibi [kutulanır](../../programming-guide/types/boxing-and-unboxing.md) :</span><span class="sxs-lookup"><span data-stu-id="66cc3-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="66cc3-153"><xref:System.Nullable%601.HasValue%2A>Dönerse `false` , null başvuru üretilir.</span><span class="sxs-lookup"><span data-stu-id="66cc3-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="66cc3-154">Döndürülürse <xref:System.Nullable%601.HasValue%2A> `true` , temel alınan değer türünün karşılık gelen değeri `T` kutulanır, örneği değildir <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="66cc3-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="66cc3-155">`T` `T?` Aşağıdaki örnekte gösterildiği gibi, bir değer türünün paketlenmiş değerini karşılık gelen null yapılabilir değer türüne bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66cc3-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="66cc3-156">Null yapılabilir değer türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="66cc3-156">How to identify a nullable value type</span></span>

<span data-ttu-id="66cc3-157">Aşağıdaki örnek, bir <xref:System.Type?displayProperty=nameWithType> Örneğin oluşturulmuş bir null yapılabilir değer türünü, diğer bir deyişle <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen tür parametresine sahip türü temsil edip etmediğini nasıl belirleyeceğini gösterir `T` :</span><span class="sxs-lookup"><span data-stu-id="66cc3-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="66cc3-158">Örnekte gösterildiği gibi, bir örnek oluşturmak için [typeof](../operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66cc3-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="66cc3-159">Bir örneğin, null olabilen bir değer türünde olup olmadığını anlamak istiyorsanız, <xref:System.Object.GetType%2A?displayProperty=nameWithType> <xref:System.Type> önceki kodla test edilecek bir örnek almak için yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="66cc3-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="66cc3-160"><xref:System.Object.GetType%2A?displayProperty=nameWithType>Yöntemini null yapılabilir bir değer türünün bir örneğinde çağırdığınızda, örnek olarak öğesine ayarlanır [boxed](#boxing-and-unboxing) <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="66cc3-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="66cc3-161">Null olabilen bir değer türünün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğerdir, <xref:System.Object.GetType%2A> <xref:System.Type> null olabilen bir değer türünün temel türünü temsil eden bir örnek döndürür:</span><span class="sxs-lookup"><span data-stu-id="66cc3-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="66cc3-162">Ayrıca, bir örneğin null yapılabilir değer türünde olup olmadığını anlamak için [,](../operators/type-testing-and-cast.md#is-operator) işleç kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="66cc3-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="66cc3-163">Aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türü örneği ve temel alınan tür örneğini işleçle ayırt edemezsiniz `is` :</span><span class="sxs-lookup"><span data-stu-id="66cc3-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="66cc3-164">Bir örneğin null yapılabilir bir değer türünde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66cc3-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="66cc3-165">Bu bölümde açıklanan yöntemler, [null yapılabilir başvuru türleri](nullable-reference-types.md)durumunda geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66cc3-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="66cc3-166">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="66cc3-166">C# language specification</span></span>

<span data-ttu-id="66cc3-167">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="66cc3-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="66cc3-168">Null atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="66cc3-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="66cc3-169">Yükseltilmemiş işleçleri</span><span class="sxs-lookup"><span data-stu-id="66cc3-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="66cc3-170">Örtük null yapılabilir dönüşümler</span><span class="sxs-lookup"><span data-stu-id="66cc3-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="66cc3-171">Açık boş değer atanabilir dönüşümler</span><span class="sxs-lookup"><span data-stu-id="66cc3-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="66cc3-172">Yükseltilmemiş dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="66cc3-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="66cc3-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66cc3-173">See also</span></span>

- [<span data-ttu-id="66cc3-174">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="66cc3-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="66cc3-175">' Yükseltilmemiş ' tam olarak ne anlama geliyor?</span><span class="sxs-lookup"><span data-stu-id="66cc3-175">What exactly does 'lifted' mean?</span></span>](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="66cc3-176">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="66cc3-176">Nullable reference types</span></span>](nullable-reference-types.md)
