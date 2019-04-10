---
title: Boş değer atanabilir türler - kullanarak C# Programlama Kılavuzu
ms.custom: seodec18
description: C# boş değer atanabilir türler ile çalışma hakkında bilgi edinin
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: ef7c9c18d303131b5a1c0156be820e1d475e7ec1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306657"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="67b71-103">Boş değer atanabilir türler (C# programlama Kılavuzu) kullanma</span><span class="sxs-lookup"><span data-stu-id="67b71-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="67b71-104">Boş değer atanabilir türler, temel alınan bir değer türünün tüm değerleri temsil eden türler `T`ve ek [null](../../language-reference/keywords/null.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="67b71-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="67b71-105">Daha fazla bilgi için [boş değer atanabilir türler](index.md) konu.</span><span class="sxs-lookup"><span data-stu-id="67b71-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="67b71-106">Aşağıdaki biçimlerden birinde boş değer atanabilir bir tür bakabilirsiniz: `Nullable<T>` veya `T?`.</span><span class="sxs-lookup"><span data-stu-id="67b71-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="67b71-107">İki yöntemden birini birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67b71-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="67b71-108">Bildirimi ve atama</span><span class="sxs-lookup"><span data-stu-id="67b71-108">Declaration and assignment</span></span>

<span data-ttu-id="67b71-109">Bir değer türü için karşılık gelen null olabilen türü örtük olarak dönüştürülebilir gibi kendi temel değer türü için yaptığınız gibi boş değer atanabilir bir tür için bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="67b71-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="67b71-110">Ayrıca atayabilirsiniz `null` değeri.</span><span class="sxs-lookup"><span data-stu-id="67b71-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="67b71-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="67b71-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="67b71-112">Boş değer atanabilir tür değeri incelemesi</span><span class="sxs-lookup"><span data-stu-id="67b71-112">Examination of a nullable type value</span></span>

<span data-ttu-id="67b71-113">Boş değer atanabilir bir tür için null örneğini inceleyin ve bir temel türü değerini almak için aşağıdaki salt okunur özelliklerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="67b71-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> <span data-ttu-id="67b71-114">boş değer atanabilir bir tür örneği, esas türünün bir değer olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67b71-114">indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> <span data-ttu-id="67b71-115">bir temel türü değeri varsa alır <xref:System.Nullable%601.HasValue%2A> olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="67b71-115">gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="67b71-116">Varsa <xref:System.Nullable%601.HasValue%2A> olduğu `false`, <xref:System.Nullable%601.Value%2A> özelliği oluşturur bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="67b71-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="67b71-117">Aşağıdaki örnekte kod `HasValue` özelliği görüntülemeden önce değişken bir değer içerip içermediğini test etmek için:</span><span class="sxs-lookup"><span data-stu-id="67b71-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="67b71-118">Bir boş değer atanabilir tür değişken ile de karşılaştırabilirsiniz `null` kullanmak yerine `HasValue` özelliği, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="67b71-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="67b71-119">Kullanabileceğiniz C# 7.0 ile başlayarak, [desen eşleştirme](../../pattern-matching.md) hem incelemek ve boş değer atanabilir bir tür değerini almak için:</span><span class="sxs-lookup"><span data-stu-id="67b71-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="67b71-120">Bir temel türü boş değer atanabilir bir tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="67b71-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="67b71-121">İçin alamayan bir tür boş değer atanabilir tür değer atamak ihtiyacınız varsa [null birleşim işleci `??` ](../../language-reference/operators/null-coalescing-operator.md) boş değer atanabilir tür değer null ise atanacak değeri belirtmek için (Ayrıca <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> yapmak için yöntemi ):</span><span class="sxs-lookup"><span data-stu-id="67b71-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="67b71-122">Kullanım <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> temel değer türünün varsayılan değeri null yapılabilir bir tür değeri null olduğunda kullanılacak değer gerekiyorsa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67b71-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="67b71-123">Boş değer atanabilir bir tür için alamayan bir tür açıkça çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67b71-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="67b71-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="67b71-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="67b71-125">Çalışma zamanında null yapılabilir bir tür değeri null ise açık tür dönüştürme oluşturur bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="67b71-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="67b71-126">NULL olmayan bir değer türü için karşılık gelen null olabilen türü örtük olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="67b71-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="67b71-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="67b71-127">Operators</span></span>

<span data-ttu-id="67b71-128">Ayrıca önceden tanımlanmış birli ve ikili işleçler ve değer türleri için mevcut kullanıcı tanımlı işleçler boş değer atanabilir türleri tarafından kullanılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="67b71-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="67b71-129">Bir veya iki işlenenin null ise null değeri bu işleçlerden üretmek; Aksi takdirde, işlecin sonucu hesaplamak için kapsanan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="67b71-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="67b71-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="67b71-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="67b71-131">İçin `bool?` yazın, önceden tanımlanmış `&` ve `|` işleçleri yoksa bu bölümde açıklanan kuralları izleyin: biri null olsa bile null olmayan bir işleç değerlendirme sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="67b71-131">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span> <span data-ttu-id="67b71-132">Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="67b71-132">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="67b71-133">İlişkisel işleçleri (`<`, `>`, `<=`, `>=`), bir veya iki işlenenin null ise sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="67b71-133">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="67b71-134">Çünkü varsaymayın belirli bir karşılaştırmanın (örneğin, `<=`) döndürür `false`, karşılaştırma ters (`>`) döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="67b71-134">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="67b71-135">Aşağıdaki örnek, 10 olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="67b71-135">The following example shows that 10 is</span></span>

- <span data-ttu-id="67b71-136">ne büyüktür veya eşittir null,</span><span class="sxs-lookup"><span data-stu-id="67b71-136">neither greater than or equal to null,</span></span>
- <span data-ttu-id="67b71-137">ya da null değerinden küçük.</span><span class="sxs-lookup"><span data-stu-id="67b71-137">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="67b71-138">Yukarıdaki örnek, ayrıca her ikisi de null iki boş değer atanabilir türler bir eşitlik karşılaştırması olarak değerlendirilen gösterir `true`.</span><span class="sxs-lookup"><span data-stu-id="67b71-138">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="67b71-139">Daha fazla bilgi için [yükseltilmiş işleçleri](~/_csharplang/spec/expressions.md#lifted-operators) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="67b71-139">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="67b71-140">Kutulama ve kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="67b71-140">Boxing and unboxing</span></span>

<span data-ttu-id="67b71-141">Boş değer atanabilir değer türü [Kutulu](../types/boxing-and-unboxing.md) aşağıdaki kurallar tarafından:</span><span class="sxs-lookup"><span data-stu-id="67b71-141">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="67b71-142">Varsa <xref:System.Nullable%601.HasValue%2A> döndürür `false`, null başvuru oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="67b71-142">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="67b71-143">Varsa <xref:System.Nullable%601.HasValue%2A> döndürür `true`, temel alınan değer türünde bir değer `T` Kutulu olmasıdır örneği değil <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="67b71-143">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="67b71-144">Aşağıdaki örnekte gösterildiği gibi kutulanmış değer türüne karşılık gelen boş değer atanabilir tür unbox:</span><span class="sxs-lookup"><span data-stu-id="67b71-144">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="67b71-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67b71-145">See also</span></span>

- [<span data-ttu-id="67b71-146">Boş değer atanabilir tipler</span><span class="sxs-lookup"><span data-stu-id="67b71-146">Nullable types</span></span>](index.md)
- [<span data-ttu-id="67b71-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="67b71-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="67b71-148">Tam olarak 'yükseltilmiş' ne demektir?</span><span class="sxs-lookup"><span data-stu-id="67b71-148">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
