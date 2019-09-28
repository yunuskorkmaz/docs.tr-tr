---
title: Nullable değer türlerini kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
description: C# Null yapılabilir değer türleriyle çalışmayı öğrenin
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396168"
---
# <a name="using-nullable-value-types-c-programming-guide"></a><span data-ttu-id="f5de9-103">Nullable değer türlerini kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f5de9-103">Using nullable value types (C# Programming Guide)</span></span>

<span data-ttu-id="f5de9-104">Null yapılabilir değer türleri, `T` ve ek [null](../../language-reference/keywords/null.md) değeri olan temel bir değer türünün tüm değerlerini temsil eden türlerdir.</span><span class="sxs-lookup"><span data-stu-id="f5de9-104">Nullable value types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="f5de9-105">Daha fazla bilgi için, [Nullable değer türleri](index.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="f5de9-105">For more information, see the [Nullable value types](index.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="f5de9-106">C#8,0, Nullable başvuru türleri özelliğini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f5de9-106">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="f5de9-107">Daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="f5de9-107">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="f5de9-108">Null yapılabilir değer türleri 2 ' den C# başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5de9-108">The nullable value types are available starting with C# 2.</span></span>

<span data-ttu-id="f5de9-109">Aşağıdaki değiştirilebilir formlardan herhangi birinde null olabilen bir değer türüne başvurabilirsiniz: `Nullable<T>` veya `T?`.</span><span class="sxs-lookup"><span data-stu-id="f5de9-109">You can refer to a nullable value type in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="f5de9-110">`T` bir değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5de9-110">`T` must be a value type.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="f5de9-111">Bildirim ve atama</span><span class="sxs-lookup"><span data-stu-id="f5de9-111">Declaration and assignment</span></span>

<span data-ttu-id="f5de9-112">Bir değer türü örtük olarak karşılık gelen null yapılabilir değer türüne dönüştürülebileceğinden, bir değeri, temel alınan değer türü gibi, null olabilen bir türe atarsınız.</span><span class="sxs-lookup"><span data-stu-id="f5de9-112">As a value type can be implicitly converted to the corresponding nullable value type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="f5de9-113">@No__t-0 değerini de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5de9-113">You also can assign the `null` value.</span></span> <span data-ttu-id="f5de9-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f5de9-114">For example:</span></span>

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="f5de9-115">Null yapılabilir bir tür değeri incelemesi</span><span class="sxs-lookup"><span data-stu-id="f5de9-115">Examination of a nullable type value</span></span>

<span data-ttu-id="f5de9-116">Null yapılabilir değer türünün bir örneğini null için incelemek ve temel alınan bir türün değerini almak için aşağıdaki ReadOnly özelliklerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="f5de9-116">Use the following readonly properties to examine an instance of a nullable value type for null and retrieve a value of an underlying type:</span></span>

- <span data-ttu-id="f5de9-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>, null yapılabilir bir türün bir örneğinin temel alınan türü bir değere sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5de9-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>

- <span data-ttu-id="f5de9-118"><xref:System.Nullable%601.HasValue%2A>,  `true` ise temel alınan bir türün değerini alır.</span><span class="sxs-lookup"><span data-stu-id="f5de9-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="f5de9-119">@No__t-0 `false` ise, <xref:System.Nullable%601.Value%2A> özelliği bir <xref:System.InvalidOperationException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5de9-119">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="f5de9-120">Aşağıdaki örnekteki kod, değişkenin görüntülemeden önce bir değer içerip içermediğini sınamak için `HasValue` özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="f5de9-120">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

<span data-ttu-id="f5de9-121">Ayrıca, aşağıdaki örnekte gösterildiği gibi, null atanabilir bir değer türünün bir değişkenini `HasValue` özelliğini kullanmak yerine `null` ile karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5de9-121">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="f5de9-122">7,0 ile C# başlayarak, null olabilen bir değer türünün bir değerini incelemek ve almak için [model eşleştirmeyi](../../pattern-matching.md) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5de9-122">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable value type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="f5de9-123">Null yapılabilir bir değer türünden temel alınan bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f5de9-123">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="f5de9-124">Null olabilen bir değer türünün değerini null yapılamayan bir türe atamanız gerekiyorsa, null yapılabilir değer türünde bir değer null ise atanacak değeri belirtmek için [`??` null birleşim işlecini](../../language-reference/operators/null-coalescing-operator.md) kullanın (bunu yapmak için <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> metodunu da kullanabilirsiniz) :</span><span class="sxs-lookup"><span data-stu-id="f5de9-124">If you need to assign a value of a nullable value type to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a value of a nullable value type is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="f5de9-125">Null yapılabilir bir değer türünün değeri `null` olduğunda, temel alınan değer türünün varsayılan değeri olmalıdır <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5de9-125">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a value of a nullable value type is `null` should be the default value of the underlying value type.</span></span>

<span data-ttu-id="f5de9-126">Null olabilen bir değer türünü açık olmayan bir türe açıkça çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5de9-126">You can explicitly cast a nullable value type to a non-nullable type.</span></span> <span data-ttu-id="f5de9-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f5de9-127">For example:</span></span>

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="f5de9-128">Çalışma zamanında, null yapılabilir bir değer türünün değeri `null` ise, açık atama bir <xref:System.InvalidOperationException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5de9-128">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="f5de9-129">Null yapılamayan bir değer türü örtük olarak karşılık gelen null yapılabilir türe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f5de9-129">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>

## <a name="operators"></a><span data-ttu-id="f5de9-130">İşleçler</span><span class="sxs-lookup"><span data-stu-id="f5de9-130">Operators</span></span>

<span data-ttu-id="f5de9-131">Önceden tanımlanmış birli ve ikili işleçler ve değer türleri için mevcut herhangi bir Kullanıcı tanımlı işleç, bunlara karşılık gelen null yapılabilir türler tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5de9-131">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by corresponding nullable types.</span></span> <span data-ttu-id="f5de9-132">Bu işleçler, bir veya her iki işlenen de `null` ise `null` üretir. Aksi halde, işleç sonucu hesaplamak için kapsanan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5de9-132">These operators produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="f5de9-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f5de9-133">For example:</span></span>

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="f5de9-134">@No__t-0 türü için, önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işlenenlerden biri `null` olsa bile bir operatör değerlendirmesinin sonucu null olamaz.</span><span class="sxs-lookup"><span data-stu-id="f5de9-134">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="f5de9-135">Daha fazla bilgi için, [Boole mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f5de9-135">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="f5de9-136">İlişkisel işleçler (`<`, `>`, `<=`, `>=`) için, bir veya her iki işlenen `null` ise, sonuç `false` olur.</span><span class="sxs-lookup"><span data-stu-id="f5de9-136">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are `null`, the result is `false`.</span></span> <span data-ttu-id="f5de9-137">Belirli bir karşılaştırma (örneğin, `<=`) `false` döndürdüğünden, ters karşılaştırma (`>`) `true` döndürdüğünden Bu olduğunu varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="f5de9-137">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="f5de9-138">Aşağıdaki örnek, 10 ' un olduğunu gösterir</span><span class="sxs-lookup"><span data-stu-id="f5de9-138">The following example shows that 10 is</span></span>

- <span data-ttu-id="f5de9-139">`null` ' dan büyük veya eşit değil</span><span class="sxs-lookup"><span data-stu-id="f5de9-139">neither greater than or equal to `null`,</span></span>
- <span data-ttu-id="f5de9-140">`null` ' dan küçük.</span><span class="sxs-lookup"><span data-stu-id="f5de9-140">nor less than `null`.</span></span>

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

<span data-ttu-id="f5de9-141">Yukarıdaki örnek ayrıca, null değer alabilen iki null atanabilir değer türünün eşitlik karşılaştırmasını `true` olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f5de9-141">The above example also shows that an equality comparison of two nullable value types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="f5de9-142">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yükseltilmemiş işleçleri](~/_csharplang/spec/expressions.md#lifted-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f5de9-142">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="f5de9-143">Kutulama ve kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="f5de9-143">Boxing and unboxing</span></span>

<span data-ttu-id="f5de9-144">Null yapılabilir bir değer türü, aşağıdaki kurallara göre [kutulanır](../types/boxing-and-unboxing.md) :</span><span class="sxs-lookup"><span data-stu-id="f5de9-144">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="f5de9-145">@No__t-0 `false` döndürürse, null başvuru üretilir.</span><span class="sxs-lookup"><span data-stu-id="f5de9-145">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="f5de9-146">@No__t-0 `true` döndürürse, <xref:System.Nullable%601> ' in örneği değil, temel alınan değer türü `T` değeri kutulanır.</span><span class="sxs-lookup"><span data-stu-id="f5de9-146">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="f5de9-147">Aşağıdaki örnekte gösterildiği gibi kutulanmış değer türünü karşılık gelen null yapılabilir türe bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5de9-147">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="f5de9-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5de9-148">See also</span></span>

- [<span data-ttu-id="f5de9-149">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="f5de9-149">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="f5de9-150">' Yükseltilmemiş ' tam olarak ne anlama geliyor?</span><span class="sxs-lookup"><span data-stu-id="f5de9-150">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
