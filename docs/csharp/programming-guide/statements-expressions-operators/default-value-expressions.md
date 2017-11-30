---
title: "Varsayılan değer ifadeleri (C# programlama Kılavuzu)"
description: "Varsayılan değer ifadeleri herhangi bir başvuru türü veya değer türü için varsayılan değer üretmek"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="fdc10-103">Varsayılan değer ifadeleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fdc10-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="fdc10-104">Varsayılan değer ifadesi bir tür için varsayılan değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="fdc10-105">Varsayılan değer ifadeleri Genel sınıflar ve yöntemler özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="fdc10-106">Genel türler kullanma ortaya bir sorundur parametreli türü için varsayılan bir değer atamak nasıl `T` değil bildiğinizde aşağıdaki önceden:</span><span class="sxs-lookup"><span data-stu-id="fdc10-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="fdc10-107">Olup olmadığını `T` bir başvuru türü ya da bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="fdc10-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="fdc10-108">Varsa `T` bir değer türü sayısal bir değer veya kullanıcı tanımlı bir yapı olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="fdc10-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="fdc10-109">Bir değişken verilen `t` parametreli bir türde `T`, deyim `t = null` yalnızca geçerlidir, `T` bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="fdc10-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="fdc10-110">Atama `t = 0` yalnızca sayısal değer türleri için ancak yapılar için çalışır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="fdc10-111">Çözüm döndüren bir varsayılan değer ifadesi kullanmaktır `null` başvuru türleri (sınıf ve arabirim türlerini) ve sıfır sayısal değer türleri için.</span><span class="sxs-lookup"><span data-stu-id="fdc10-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="fdc10-112">İsteğe bağlı olarak kullanıcı tanımlı yapılar için 0 üreten sıfır bit düzeni için başlatılan yapısı döndürür veya `null` bu üye bir değer veya başvuru türünde olup olmamasına bağlı olarak her üye için.</span><span class="sxs-lookup"><span data-stu-id="fdc10-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="fdc10-113">Boş değer atanabilen değer türleri için `default` döndüren bir <xref:System.Nullable%601?displayProperty=nameWithType>, gibi herhangi bir yapı başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="fdc10-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=nameWithType>, which is initialized like any struct.</span></span>

<span data-ttu-id="fdc10-114">`default(T)` İfade Genel sınıflar ve yöntemler için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="fdc10-115">Varsayılan değer ifadeleri ile herhangi bir yönetilen türü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="fdc10-116">Bu ifadelerden herhangi biri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="fdc10-116">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="fdc10-117">Aşağıdaki örnekte `GenericList<T>` sınıfının nasıl kullanılacağını gösterir `default(T)` genel bir sınıf içinde işleci.</span><span class="sxs-lookup"><span data-stu-id="fdc10-117">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="fdc10-118">Daha fazla bilgi için bkz: [genel türler genel bakış](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="fdc10-118">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="fdc10-119">Varsayılan değişmez değer ve tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="fdc10-119">default literal and type inference</span></span>

<span data-ttu-id="fdc10-120">C# ile 7.1, başlayarak `default` değişmez değeri derleyici ifade türü çıkarımını, varsayılan değer ifadesi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-120">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="fdc10-121">`default` Değişmez değeri üretir eşdeğer olarak aynı değeri `default(T)` burada `T` oluşturulursa türüdür.</span><span class="sxs-lookup"><span data-stu-id="fdc10-121">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="fdc10-122">Bu kodu daha kısa bir türü birden çok kez bildirme artıklık azaltarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdc10-122">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="fdc10-123">`default` Değişmez değeri aşağıdaki konumlardan herhangi birinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fdc10-123">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="fdc10-124">değişken Başlatıcısı</span><span class="sxs-lookup"><span data-stu-id="fdc10-124">variable initializer</span></span>
- <span data-ttu-id="fdc10-125">değişken ataması</span><span class="sxs-lookup"><span data-stu-id="fdc10-125">variable assignment</span></span>
- <span data-ttu-id="fdc10-126">İsteğe bağlı bir parametre için varsayılan değer bildirme</span><span class="sxs-lookup"><span data-stu-id="fdc10-126">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="fdc10-127">için bir yöntem çağrısı bağımsız değişken değeri sağlama</span><span class="sxs-lookup"><span data-stu-id="fdc10-127">providing the value for a method call argument</span></span>
- <span data-ttu-id="fdc10-128">deyim (veya bir ifade bodied üye ifadesinde) döndürür</span><span class="sxs-lookup"><span data-stu-id="fdc10-128">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="fdc10-129">Aşağıdaki örnek, birçok kullanım gösterir `default` varsayılan değer ifadesi sabit değer:</span><span class="sxs-lookup"><span data-stu-id="fdc10-129">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="fdc10-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc10-130">See also</span></span>

 <span data-ttu-id="fdc10-131"><xref:System.Collections.Generic>[C# programlama kılavuzu](../index.md)</span><span class="sxs-lookup"><span data-stu-id="fdc10-131"><xref:System.Collections.Generic> [C# Programming Guide](../index.md)</span></span>  
 [<span data-ttu-id="fdc10-132">Genel türler</span><span class="sxs-lookup"><span data-stu-id="fdc10-132">Generics</span></span>](../generics/index.md)  
 [<span data-ttu-id="fdc10-133">Genel yöntemler</span><span class="sxs-lookup"><span data-stu-id="fdc10-133">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="fdc10-134">Genel türler</span><span class="sxs-lookup"><span data-stu-id="fdc10-134">Generics</span></span>](~/docs/standard/generics/index.md)  
