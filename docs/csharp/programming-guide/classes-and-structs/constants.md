---
title: Sabitler-C# Programlama Kılavuzu
description: C# ' deki sabitler, derleme zamanı değişmez değerleri, program derlendikten sonra değişmez. Yalnızca C# yerleşik türleri sabitler olabilir.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 1252e214be03f8a180fadb7667ee59f36a862040
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558432"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="d8db1-104">Sabitler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d8db1-104">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="d8db1-105">Sabitler, derleme zamanında bilinen ve programın ömrü boyunca değişmeyen sabit değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="d8db1-105">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="d8db1-106">Sabitler [const](../../language-reference/keywords/const.md) değiştiricisi ile bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8db1-106">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="d8db1-107">Yalnızca C# [yerleşik türleri](../../language-reference/builtin-types/built-in-types.md) (hariç <xref:System.Object?displayProperty=nameWithType> ) olarak bildirilebilecek `const` .</span><span class="sxs-lookup"><span data-stu-id="d8db1-107">Only the C# [built-in types](../../language-reference/builtin-types/built-in-types.md) (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="d8db1-108">Sınıflar, yapılar ve diziler dahil olmak üzere Kullanıcı tanımlı türler olamaz `const` .</span><span class="sxs-lookup"><span data-stu-id="d8db1-108">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="d8db1-109">Çalışma zamanında bir kez başlatılan bir sınıf, yapı veya dizi oluşturmak için [salt okunur](../../language-reference/keywords/readonly.md) değiştiricisini kullanın (örneğin, bir oluşturucuda) ve bundan sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="d8db1-109">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="d8db1-110">C#, `const` yöntemleri, özellikleri veya olayları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d8db1-110">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="d8db1-111">Sabit listesi türü, integral yerleşik türler (örneğin,, vb.) için adlandırılmış sabitler tanımlamanızı `int` sağlar `uint` `long` .</span><span class="sxs-lookup"><span data-stu-id="d8db1-111">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="d8db1-112">Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="d8db1-112">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="d8db1-113">Sabitler, bildirildiği için başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8db1-113">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="d8db1-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d8db1-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 <span data-ttu-id="d8db1-115">Bu örnekte, sabit `Months` her zaman 12 ' dir ve sınıfın kendisi tarafından bile değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="d8db1-115">In this example, the constant `Months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="d8db1-116">Aslında, derleyici C# kaynak kodunda bir sabit tanımlayıcıyla karşılaştığında (örneğin, `Months` ), değişmez değer değerini doğrudan ürettiği ara dil (IL) koduna koyar.</span><span class="sxs-lookup"><span data-stu-id="d8db1-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `Months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="d8db1-117">Çalışma zamanında bir sabitle ilişkili değişken adresi olmadığından, `const` alanlar başvuruya göre geçirilemez ve bir ifadede l değeri olarak görünemez.</span><span class="sxs-lookup"><span data-stu-id="d8db1-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8db1-118">Dll 'Ler gibi başka bir kodda tanımlanan sabit değerlere başvurduğunuzda dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="d8db1-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="d8db1-119">Yeni bir DLL sürümü sabit için yeni bir değer tanımlıyorsa, programınız yeni sürüme yeniden derlenene kadar eski değişmez değeri de tutar.</span><span class="sxs-lookup"><span data-stu-id="d8db1-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="d8db1-120">Aynı türden birden fazla sabit aynı anda bildirilebilecek, örneğin:</span><span class="sxs-lookup"><span data-stu-id="d8db1-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 <span data-ttu-id="d8db1-121">Bir sabiti başlatmak için kullanılan ifade, döngüsel başvuru oluşturmayan başka bir sabite başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="d8db1-121">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="d8db1-122">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d8db1-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 <span data-ttu-id="d8db1-123">Sabitler, [genel](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="d8db1-123">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="d8db1-124">Bu erişim değiştiricileri, sınıfın kullanıcılarının sabitine nasıl erişekullanabileceğinizi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d8db1-124">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="d8db1-125">Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="d8db1-125">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="d8db1-126">Sabitlere [statik](../../language-reference/keywords/static.md) alanlar gibi erişilir çünkü sabit değeri, türün tüm örnekleri için aynı.</span><span class="sxs-lookup"><span data-stu-id="d8db1-126">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="d8db1-127">`static`Bunları bildirmek için anahtar sözcüğünü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d8db1-127">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="d8db1-128">Sabiti tanımlayan sınıfta olmayan ifadeler, sabit erişim için sınıf adı, nokta ve sabitin adını kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8db1-128">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="d8db1-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d8db1-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d8db1-130">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d8db1-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8db1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8db1-131">See also</span></span>

- [<span data-ttu-id="d8db1-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d8db1-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d8db1-133">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="d8db1-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d8db1-134">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d8db1-134">Properties</span></span>](./properties.md)
- [<span data-ttu-id="d8db1-135">Türler</span><span class="sxs-lookup"><span data-stu-id="d8db1-135">Types</span></span>](../types/index.md)
- [<span data-ttu-id="d8db1-136">readonly</span><span class="sxs-lookup"><span data-stu-id="d8db1-136">readonly</span></span>](../../language-reference/keywords/readonly.md)
- [<span data-ttu-id="d8db1-137">C# bölüm bir üzerinde Imleyici kullanılabilirliği: Imleyici kullanılabilirlik çeşitleri</span><span class="sxs-lookup"><span data-stu-id="d8db1-137">Immutability in C# Part One: Kinds of Immutability</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
