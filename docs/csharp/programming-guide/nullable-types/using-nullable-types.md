---
title: Null yapılabilir türler kullanma C# -Programlama Kılavuzu
ms.custom: seodec18
description: C# Null yapılabilir türlerle nasıl çalışacağınızı öğrenin
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588827"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="2b662-103">Nullable türler kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2b662-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="2b662-104">Null yapılabilir türler, temel alınan bir değer türünün `T`tüm değerlerini temsil eden türlerdir ve ek bir [null](../../language-reference/keywords/null.md) değer.</span><span class="sxs-lookup"><span data-stu-id="2b662-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="2b662-105">Daha fazla bilgi için, [Nullable türler](index.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="2b662-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="2b662-106">Aşağıdaki biçimlerden birinde null yapılabilen bir türe başvurabilirsiniz: `Nullable<T>` veya. `T?`</span><span class="sxs-lookup"><span data-stu-id="2b662-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="2b662-107">Bu iki form birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b662-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="2b662-108">Bildirim ve atama</span><span class="sxs-lookup"><span data-stu-id="2b662-108">Declaration and assignment</span></span>

<span data-ttu-id="2b662-109">Bir değer türü örtük olarak karşılık gelen null yapılabilir türe dönüştürülebileceğinden, kendisine ait değer türü için yaptığınız gibi, null olabilen bir türe bir değer atarsınız.</span><span class="sxs-lookup"><span data-stu-id="2b662-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="2b662-110">Ayrıca `null` değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b662-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="2b662-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b662-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="2b662-112">Null yapılabilir bir tür değeri incelemesi</span><span class="sxs-lookup"><span data-stu-id="2b662-112">Examination of a nullable type value</span></span>

<span data-ttu-id="2b662-113">Null yapılabilir bir türün bir örneğini null için incelemek ve temel alınan bir türün değerini almak için aşağıdaki ReadOnly özelliklerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2b662-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="2b662-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>null yapılabilir bir türün bir örneğinin temel alınan türü bir değere sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b662-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="2b662-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType><xref:System.Nullable%601.HasValue%2A> ise ,`true`temel alınan bir türün değerini alır.</span><span class="sxs-lookup"><span data-stu-id="2b662-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="2b662-116"><xref:System.Nullable%601.HasValue%2A> İse ,`false`özelliği bir<xref:System.InvalidOperationException>oluşturur. <xref:System.Nullable%601.Value%2A></span><span class="sxs-lookup"><span data-stu-id="2b662-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="2b662-117">Aşağıdaki örnekteki kod, değişkenin görüntülemeden önce bir `HasValue` değer içerip içermediğini test etmek için özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="2b662-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="2b662-118">Ayrıca, aşağıdaki örnekte gösterildiği gibi, `null` `HasValue` özelliği kullanmak yerine null olabilen bir tür değişkenini karşılaştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b662-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="2b662-119">7,0 ile C# başlayarak, null yapılabilir bir türdeki değeri incelemek ve almak için [model eşleştirmeyi](../../pattern-matching.md) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b662-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="2b662-120">Null yapılabilir bir türden temel alınan bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2b662-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="2b662-121">Null olabilen bir türe null atanabilir bir tür değeri atamanız gerekiyorsa, null yapılabilir bir tür değeri null ise atanacak değeri belirtmek için [null birleşim işlecini `??` ](../../language-reference/operators/null-coalescing-operator.md) kullanın (bunu yapmak için <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> de kullanabilirsiniz):</span><span class="sxs-lookup"><span data-stu-id="2b662-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="2b662-122">Null yapılabilir bir tür değeri null olduğunda kullanılacak değer, temel alınan değer türünün varsayılan değeri olmalıdır yönteminikullanın.<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2b662-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="2b662-123">Null yapılabilir bir türü açıkça null atanamaz bir türe çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b662-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="2b662-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b662-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="2b662-125">Çalışma zamanında, null yapılabilir bir türün değeri null ise, açık atama bir <xref:System.InvalidOperationException>atar.</span><span class="sxs-lookup"><span data-stu-id="2b662-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="2b662-126">Null yapılamayan bir değer türü örtük olarak karşılık gelen null yapılabilir türe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="2b662-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="2b662-127">İşleçler</span><span class="sxs-lookup"><span data-stu-id="2b662-127">Operators</span></span>

<span data-ttu-id="2b662-128">Önceden tanımlanmış birli ve ikili işleçler ve değer türleri için mevcut olan herhangi bir Kullanıcı tanımlı işleç, null yapılabilir türler tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b662-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="2b662-129">Bu işleçler bir veya her iki işlenen de null ise null değeri üretir; Aksi halde, işleç sonucu hesaplamak için kapsanan değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b662-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="2b662-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b662-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="2b662-131">Türü için, önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işleçlerden biri null olsa bile bir operatör değerlendirmesinin sonucu null olmamalıdır. `bool?`</span><span class="sxs-lookup"><span data-stu-id="2b662-131">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span> <span data-ttu-id="2b662-132">Daha fazla bilgi için, [Boole mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2b662-132">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="2b662-133">İlişkisel`<`işleçler ( `false`, `>`, `<=`, `>=`) için, bir veya her iki işlenen de null ise sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="2b662-133">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="2b662-134">Belirli bir karşılaştırma `<=`(örneğin,) döndürdüğünden `false`, zıt karşılaştırma (`>`) işlevinin döndürdüğü `true`varsayılmayın.</span><span class="sxs-lookup"><span data-stu-id="2b662-134">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="2b662-135">Aşağıdaki örnek, 10 ' un olduğunu gösterir</span><span class="sxs-lookup"><span data-stu-id="2b662-135">The following example shows that 10 is</span></span>

- <span data-ttu-id="2b662-136">null değerinden büyük veya buna eşit değil,</span><span class="sxs-lookup"><span data-stu-id="2b662-136">neither greater than or equal to null,</span></span>
- <span data-ttu-id="2b662-137">null veya daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="2b662-137">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="2b662-138">Yukarıdaki örnek ayrıca, null olarak `true`değerlendirilen iki null yapılabilir türün eşitlik karşılaştırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b662-138">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="2b662-139">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yükseltilmemiş işleçleri](~/_csharplang/spec/expressions.md#lifted-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2b662-139">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="2b662-140">Kutulama ve kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="2b662-140">Boxing and unboxing</span></span>

<span data-ttu-id="2b662-141">Null yapılabilir bir değer türü [](../types/boxing-and-unboxing.md) , aşağıdaki kurallara göre kutulanır:</span><span class="sxs-lookup"><span data-stu-id="2b662-141">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="2b662-142"><xref:System.Nullable%601.HasValue%2A> Dönerse`false`, null başvuru üretilir.</span><span class="sxs-lookup"><span data-stu-id="2b662-142">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="2b662-143">Döndürülürse, temel alınan değer türünün `T` bir değeri kutulanır, örneği <xref:System.Nullable%601>değildir. `true` <xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="2b662-143">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="2b662-144">Aşağıdaki örnekte gösterildiği gibi kutulanmış değer türünü karşılık gelen null yapılabilir türe bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b662-144">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="2b662-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b662-145">See also</span></span>

- [<span data-ttu-id="2b662-146">Null yapılabilir türler</span><span class="sxs-lookup"><span data-stu-id="2b662-146">Nullable types</span></span>](index.md)
- [<span data-ttu-id="2b662-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2b662-147">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2b662-148">' Yükseltilmemiş ' tam olarak ne anlama geliyor?</span><span class="sxs-lookup"><span data-stu-id="2b662-148">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
