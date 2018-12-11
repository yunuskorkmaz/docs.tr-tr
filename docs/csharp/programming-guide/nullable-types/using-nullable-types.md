---
title: Boş değer atanabilir türler - kullanarak C# Programlama Kılavuzu
ms.custom: seodec18
description: C# boş değer atanabilir türler ile çalışma hakkında bilgi edinin
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: d2c6f2f78ed71558b71adcc1d4d8cc9a6f459d75
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235221"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="fee1b-103">Boş değer atanabilir türler (C# programlama Kılavuzu) kullanma</span><span class="sxs-lookup"><span data-stu-id="fee1b-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="fee1b-104">Boş değer atanabilir türler, temel alınan bir değer türünün tüm değerleri temsil eden türler `T`ve ek [null](../../language-reference/keywords/null.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="fee1b-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="fee1b-105">Daha fazla bilgi için [boş değer atanabilir türler](index.md) konu.</span><span class="sxs-lookup"><span data-stu-id="fee1b-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="fee1b-106">Aşağıdaki biçimlerden birinde boş değer atanabilir bir tür bakabilirsiniz: `Nullable<T>` veya `T?`.</span><span class="sxs-lookup"><span data-stu-id="fee1b-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="fee1b-107">İki yöntemden birini birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fee1b-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="fee1b-108">Bildirimi ve atama</span><span class="sxs-lookup"><span data-stu-id="fee1b-108">Declaration and assignment</span></span>

<span data-ttu-id="fee1b-109">Bir değer türü için karşılık gelen null olabilen türü örtük olarak dönüştürülebilir gibi kendi temel değer türü için yaptığınız gibi boş değer atanabilir bir tür için bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="fee1b-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="fee1b-110">Ayrıca atayabilirsiniz `null` değeri.</span><span class="sxs-lookup"><span data-stu-id="fee1b-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="fee1b-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fee1b-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="fee1b-112">Boş değer atanabilir tür değeri incelemesi</span><span class="sxs-lookup"><span data-stu-id="fee1b-112">Examination of a nullable type value</span></span>

<span data-ttu-id="fee1b-113">Boş değer atanabilir bir tür için null örneğini inceleyin ve bir temel türü değerini almak için aşağıdaki salt okunur özelliklerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="fee1b-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="fee1b-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> boş değer atanabilir bir tür örneği, esas türünün bir değer olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fee1b-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="fee1b-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> bir temel türü değeri varsa alır <xref:System.Nullable%601.HasValue%2A> olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="fee1b-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="fee1b-116">Varsa <xref:System.Nullable%601.HasValue%2A> olduğu `false`, <xref:System.Nullable%601.Value%2A> özelliği oluşturur bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="fee1b-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="fee1b-117">Aşağıdaki örnekte kod `HasValue` özelliği görüntülemeden önce değişken bir değer içerip içermediğini test etmek için:</span><span class="sxs-lookup"><span data-stu-id="fee1b-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="fee1b-118">Bir boş değer atanabilir tür değişken ile de karşılaştırabilirsiniz `null` kullanmak yerine `HasValue` özelliği, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="fee1b-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="fee1b-119">Kullanabileceğiniz C# 7.0 ile başlayarak, [desen eşleştirme](../../pattern-matching.md) hem incelemek ve boş değer atanabilir bir tür değerini almak için:</span><span class="sxs-lookup"><span data-stu-id="fee1b-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="fee1b-120">Bir temel türü boş değer atanabilir bir tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fee1b-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="fee1b-121">İçin alamayan bir tür boş değer atanabilir tür değer atamak ihtiyacınız varsa [null birleşim işleci `??` ](../../language-reference/operators/null-coalescing-operator.md) boş değer atanabilir tür değer null ise atanacak değeri belirtmek için (Ayrıca <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> yapmak için yöntemi ):</span><span class="sxs-lookup"><span data-stu-id="fee1b-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="fee1b-122">Kullanım <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> temel değer türünün varsayılan değeri null yapılabilir bir tür değeri null olduğunda kullanılacak değer gerekiyorsa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fee1b-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="fee1b-123">Boş değer atanabilir bir tür için alamayan bir tür açıkça çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fee1b-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="fee1b-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fee1b-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="fee1b-125">Çalışma zamanında null yapılabilir bir tür değeri null ise açık tür dönüştürme oluşturur bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="fee1b-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="fee1b-126">NULL olmayan bir değer türü için karşılık gelen null olabilen türü örtük olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fee1b-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="fee1b-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="fee1b-127">Operators</span></span>

<span data-ttu-id="fee1b-128">Ayrıca önceden tanımlanmış birli ve ikili işleçler ve değer türleri için mevcut kullanıcı tanımlı işleçler boş değer atanabilir türleri tarafından kullanılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fee1b-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="fee1b-129">Bir veya iki işlenenin null ise null değeri bu işleçlerden üretmek; Aksi takdirde, işlecin sonucu hesaplamak için kapsanan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="fee1b-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="fee1b-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fee1b-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]
  
<span data-ttu-id="fee1b-131">İlişkisel işleçleri (`<`, `>`, `<=`, `>=`), bir veya iki işlenenin null ise sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="fee1b-131">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="fee1b-132">Çünkü varsaymayın belirli bir karşılaştırmanın (örneğin, `<=`) döndürür `false`, karşılaştırma ters (`>`) döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="fee1b-132">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="fee1b-133">Aşağıdaki örnek, 10 olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fee1b-133">The following example shows that 10 is</span></span>

- <span data-ttu-id="fee1b-134">ne büyüktür veya eşittir null,</span><span class="sxs-lookup"><span data-stu-id="fee1b-134">neither greater than or equal to null,</span></span>
- <span data-ttu-id="fee1b-135">ya da null değerinden küçük.</span><span class="sxs-lookup"><span data-stu-id="fee1b-135">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="fee1b-136">Yukarıdaki örnek, ayrıca her ikisi de null iki boş değer atanabilir türler bir eşitlik karşılaştırması olarak değerlendirilen gösterir `true`.</span><span class="sxs-lookup"><span data-stu-id="fee1b-136">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="fee1b-137">Kutulama ve kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="fee1b-137">Boxing and unboxing</span></span>

<span data-ttu-id="fee1b-138">Boş değer atanabilir değer türü [Kutulu](../types/boxing-and-unboxing.md) aşağıdaki kurallar tarafından:</span><span class="sxs-lookup"><span data-stu-id="fee1b-138">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="fee1b-139">Varsa <xref:System.Nullable%601.HasValue%2A> döndürür `false`, null başvuru oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fee1b-139">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="fee1b-140">Varsa <xref:System.Nullable%601.HasValue%2A> döndürür `true`, temel alınan değer türünde bir değer `T` Kutulu olmasıdır örneği değil <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="fee1b-140">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="fee1b-141">Aşağıdaki örnekte gösterildiği gibi kutulanmış değer türüne karşılık gelen boş değer atanabilir tür unbox:</span><span class="sxs-lookup"><span data-stu-id="fee1b-141">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a><span data-ttu-id="fee1b-142">Bool? türü</span><span class="sxs-lookup"><span data-stu-id="fee1b-142">The bool? type</span></span>

<span data-ttu-id="fee1b-143">`bool?` Null olabilen türü üç farklı değer içerebilir: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), ve [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="fee1b-143">The `bool?` nullable type can contain three different values: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), and [null](../../language-reference/keywords/null.md).</span></span> <span data-ttu-id="fee1b-144">`bool?` SQL'de kullanılan Boole değişken türü gibi türüdür.</span><span class="sxs-lookup"><span data-stu-id="fee1b-144">The `bool?` type is like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="fee1b-145">Tarafından üretilen sonuçlar emin olmak için `&` ve `|` işleçleridir üç değerli Boole türü ile tutarlı SQL'de aşağıdaki önceden tanımlı operatörler sağlanır:</span><span class="sxs-lookup"><span data-stu-id="fee1b-145">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
<span data-ttu-id="fee1b-146">Bu işleçler semantiği aşağıdaki tabloda tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="fee1b-146">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="fee1b-147">x</span><span class="sxs-lookup"><span data-stu-id="fee1b-147">x</span></span>|<span data-ttu-id="fee1b-148">y</span><span class="sxs-lookup"><span data-stu-id="fee1b-148">y</span></span>|<span data-ttu-id="fee1b-149">x & y</span><span class="sxs-lookup"><span data-stu-id="fee1b-149">x&y</span></span>|<span data-ttu-id="fee1b-150">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="fee1b-150">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="fee1b-151">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-151">true</span></span>|<span data-ttu-id="fee1b-152">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-152">true</span></span>|<span data-ttu-id="fee1b-153">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-153">true</span></span>|<span data-ttu-id="fee1b-154">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-154">true</span></span>|  
|<span data-ttu-id="fee1b-155">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-155">true</span></span>|<span data-ttu-id="fee1b-156">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-156">false</span></span>|<span data-ttu-id="fee1b-157">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-157">false</span></span>|<span data-ttu-id="fee1b-158">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-158">true</span></span>|  
|<span data-ttu-id="fee1b-159">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-159">true</span></span>|<span data-ttu-id="fee1b-160">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-160">null</span></span>|<span data-ttu-id="fee1b-161">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-161">null</span></span>|<span data-ttu-id="fee1b-162">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-162">true</span></span>|  
|<span data-ttu-id="fee1b-163">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-163">false</span></span>|<span data-ttu-id="fee1b-164">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-164">true</span></span>|<span data-ttu-id="fee1b-165">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-165">false</span></span>|<span data-ttu-id="fee1b-166">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-166">true</span></span>|  
|<span data-ttu-id="fee1b-167">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-167">false</span></span>|<span data-ttu-id="fee1b-168">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-168">false</span></span>|<span data-ttu-id="fee1b-169">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-169">false</span></span>|<span data-ttu-id="fee1b-170">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-170">false</span></span>|  
|<span data-ttu-id="fee1b-171">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-171">false</span></span>|<span data-ttu-id="fee1b-172">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-172">null</span></span>|<span data-ttu-id="fee1b-173">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-173">false</span></span>|<span data-ttu-id="fee1b-174">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-174">null</span></span>|  
|<span data-ttu-id="fee1b-175">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-175">null</span></span>|<span data-ttu-id="fee1b-176">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-176">true</span></span>|<span data-ttu-id="fee1b-177">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-177">null</span></span>|<span data-ttu-id="fee1b-178">true</span><span class="sxs-lookup"><span data-stu-id="fee1b-178">true</span></span>|  
|<span data-ttu-id="fee1b-179">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-179">null</span></span>|<span data-ttu-id="fee1b-180">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-180">false</span></span>|<span data-ttu-id="fee1b-181">false</span><span class="sxs-lookup"><span data-stu-id="fee1b-181">false</span></span>|<span data-ttu-id="fee1b-182">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-182">null</span></span>|  
|<span data-ttu-id="fee1b-183">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-183">null</span></span>|<span data-ttu-id="fee1b-184">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-184">null</span></span>|<span data-ttu-id="fee1b-185">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-185">null</span></span>|<span data-ttu-id="fee1b-186">null</span><span class="sxs-lookup"><span data-stu-id="fee1b-186">null</span></span>|  

<span data-ttu-id="fee1b-187">Bu iki işleç içinde açıklanan kurallar izlemeyin Not [işleçleri](#operators) bölüm: biri null olsa bile null olmayan bir işleç değerlendirme sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="fee1b-187">Note that these two operators don't follow the rules described in the [Operators](#operators) section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fee1b-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fee1b-188">See Also</span></span>

- [<span data-ttu-id="fee1b-189">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="fee1b-189">Nullable types</span></span>](index.md)  
- [<span data-ttu-id="fee1b-190">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fee1b-190">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="fee1b-191">Tam olarak 'yükseltilmiş' ne demektir?</span><span class="sxs-lookup"><span data-stu-id="fee1b-191">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)  
