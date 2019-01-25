---
title: Varsayılan değer ifadeleri toplama - C# Programlama Kılavuzu
ms.custom: seodec18
description: Varsayılan değer ifadeleri herhangi bir başvuru türü veya değer türü için varsayılan değer üretir.
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 8e10a5de73e8d49f1a380fb8945b98ac797ef270
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575547"
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="41252-103">Varsayılan değer ifadeleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="41252-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="41252-104">Varsayılan değer ifadesi `default(T)` bir türünün varsayılan değerini üretir `T`.</span><span class="sxs-lookup"><span data-stu-id="41252-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="41252-105">Aşağıdaki tabloda, çeşitli türleri için hangi değerlerin üretilen gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="41252-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="41252-106">Tür</span><span class="sxs-lookup"><span data-stu-id="41252-106">Type</span></span>|<span data-ttu-id="41252-107">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="41252-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="41252-108">herhangi bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="41252-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="41252-109">Sayısal değer türü</span><span class="sxs-lookup"><span data-stu-id="41252-109">Numeric value type</span></span>|<span data-ttu-id="41252-110">Sıfır</span><span class="sxs-lookup"><span data-stu-id="41252-110">Zero</span></span>|
|[<span data-ttu-id="41252-111">bool</span><span class="sxs-lookup"><span data-stu-id="41252-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="41252-112">char</span><span class="sxs-lookup"><span data-stu-id="41252-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="41252-113">enum</span><span class="sxs-lookup"><span data-stu-id="41252-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="41252-114">Değer ifade tarafından üretilen `(E)0`burada `E` numaralandırma tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="41252-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="41252-115">struct</span><span class="sxs-lookup"><span data-stu-id="41252-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="41252-116">Tüm değer tür alanları ayarlayarak üretilen değer varsayılan değerlerine ve tüm tür alanları için başvuru `null`.</span><span class="sxs-lookup"><span data-stu-id="41252-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="41252-117">Boş değer atanabilir tür</span><span class="sxs-lookup"><span data-stu-id="41252-117">Nullable type</span></span>|<span data-ttu-id="41252-118">Bir örneğin <xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız.</span><span class="sxs-lookup"><span data-stu-id="41252-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="41252-119">Varsayılan değer ifadeleri Genel sınıflar ve yöntemler özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="41252-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="41252-120">Genel türler kullanarak ortaya bir sorundur parametreli bir türde bir varsayılan değer atama `T` zaman bilmediğiniz aşağıdaki önceden:</span><span class="sxs-lookup"><span data-stu-id="41252-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="41252-121">Olmadığını `T` bir başvuru türü veya değer türü.</span><span class="sxs-lookup"><span data-stu-id="41252-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="41252-122">Varsa `T` sayısal bir değer veya bir yapı olup bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="41252-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="41252-123">Bir değişken verilen `t` parametreli bir türün `T`, deyim `t = null` yalnızca geçerli olduğundan, `T` bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="41252-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="41252-124">Atama `t = 0` yalnızca sayısal değer türleri için ancak değil yapı birimleri için çalışır.</span><span class="sxs-lookup"><span data-stu-id="41252-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="41252-125">Bu durumu çözmek için varsayılan değer ifadesi kullanın:</span><span class="sxs-lookup"><span data-stu-id="41252-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="41252-126">`default(T)` İfade Genel sınıflar ve yöntemler için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="41252-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="41252-127">Varsayılan değer ifadeleri herhangi bir yönetilen türü ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41252-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="41252-128">Bu ifadelerden herhangi biri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="41252-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="41252-129">Aşağıdaki örnekte `GenericList<T>` sınıfının nasıl kullanılacağını göstermektedir `default(T)` genel bir sınıf içinde işleci.</span><span class="sxs-lookup"><span data-stu-id="41252-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="41252-130">Daha fazla bilgi için [genel türlere giriş](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="41252-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="41252-131">Varsayılan değişmez değer ve tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="41252-131">default literal and type inference</span></span>

<span data-ttu-id="41252-132">C# 7.1, ile başlayan `default` değişmez değeri derleyici ifade türünü çıkarabilir, varsayılan değer ifadeleri toplama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41252-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="41252-133">`default` Değişmez değer üreten denk olarak aynı değeri `default(T)` burada `T` çıkarsanan tür.</span><span class="sxs-lookup"><span data-stu-id="41252-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="41252-134">Bu kod daha kısa bir türü birden çok kez bildirmek, fazlalıkları azaltarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41252-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="41252-135">`default` Değişmez değeri aşağıdaki konumlardan herhangi birinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="41252-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="41252-136">değişken başlatıcı</span><span class="sxs-lookup"><span data-stu-id="41252-136">variable initializer</span></span>
- <span data-ttu-id="41252-137">değişken ataması</span><span class="sxs-lookup"><span data-stu-id="41252-137">variable assignment</span></span>
- <span data-ttu-id="41252-138">İsteğe bağlı bir parametre için varsayılan değer bildirme</span><span class="sxs-lookup"><span data-stu-id="41252-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="41252-139">için bir yöntem çağrısı bağımsız değişken olarak değer sunuyor</span><span class="sxs-lookup"><span data-stu-id="41252-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="41252-140">deyimi (veya bir ifade bodied üye ifadesinde) döndürür</span><span class="sxs-lookup"><span data-stu-id="41252-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="41252-141">Aşağıdaki örnekte, fazla kullanımlar `default` varsayılan değer ifadesi sabit değer:</span><span class="sxs-lookup"><span data-stu-id="41252-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="41252-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41252-142">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="41252-143">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="41252-143">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="41252-144">Genel türler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="41252-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)
- [<span data-ttu-id="41252-145">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="41252-145">Generic Methods</span></span>](../generics/generic-methods.md)
- [<span data-ttu-id="41252-146">.NET içindeki genel türler</span><span class="sxs-lookup"><span data-stu-id="41252-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)
- [<span data-ttu-id="41252-147">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="41252-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
