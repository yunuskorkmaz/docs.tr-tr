---
title: "Sabitler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81a085ff016fb9ee8f8a13167728c37ca799920a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="2b18a-102">Sabitler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2b18a-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="2b18a-103">Derleme zamanında bilinen ve program ömrü için değiştirmeyin değişmez değerler sabittir.</span><span class="sxs-lookup"><span data-stu-id="2b18a-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="2b18a-104">Sabitler ile bildirildiğinde [const](../../../csharp/language-reference/keywords/const.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="2b18a-104">Constants are declared with the [const](../../../csharp/language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="2b18a-105">Yalnızca C# yerleşik türleri (hariç <xref:System.Object?displayProperty=nameWithType>) olarak bildirilmelidir `const`.</span><span class="sxs-lookup"><span data-stu-id="2b18a-105">Only the C# built-in types (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="2b18a-106">Yerleşik türler listesi için bkz: [yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="2b18a-106">For a list of the built-in types, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span> <span data-ttu-id="2b18a-107">Sınıflar, yapılar ve diziler dahil olmak üzere, kullanıcı tanımlı türler olamaz `const`.</span><span class="sxs-lookup"><span data-stu-id="2b18a-107">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="2b18a-108">Kullanım [readonly](../../../csharp/language-reference/keywords/readonly.md) sınıf, yapı veya çalışma zamanında (örneğin, bir kurucu) ve bundan sonra bir kez başlatılan dizi oluşturmak için değiştiricisi değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2b18a-108">Use the [readonly](../../../csharp/language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="2b18a-109">C# desteklemiyor `const` yöntemler, özellikler veya olayları.</span><span class="sxs-lookup"><span data-stu-id="2b18a-109">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="2b18a-110">Enum türü tam sayı yerleşik türleri için adlandırılmış sabitler tanımlamanızı sağlar (örneğin `int`, `uint`, `long`, vb.).</span><span class="sxs-lookup"><span data-stu-id="2b18a-110">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="2b18a-111">Daha fazla bilgi için bkz: [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="2b18a-111">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="2b18a-112">Bunlar bildirilir olarak sabit başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b18a-112">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="2b18a-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b18a-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 <span data-ttu-id="2b18a-114">Bu örnekte, sabit `months` her zaman 12 ise ve hatta sınıfı tarafından kendisini değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2b18a-114">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="2b18a-115">Aslında, derleyici karşılaştığında C# kaynak kodu sabit bir tanımlayıcı (örneğin, `months`), doğrudan bu üretir Ara dile (IL) koda hazır değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2b18a-115">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="2b18a-116">Çalışma zamanında bir sabit ile ilişkili bir değişken adresi olmadığından `const` alanları başvuruya göre geçirilemez ve l değeri bir ifade olarak yer alamaz.</span><span class="sxs-lookup"><span data-stu-id="2b18a-116">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b18a-117">DLL'ler gibi diğer kodda tanımlanan sabit değerleri başvurduğunuzda dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="2b18a-117">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="2b18a-118">DLL yeni bir sürümü sabiti için yeni bir değer tanımlıyorsa, yeni sürüm karşı derlenmiştir kadar programınızı eski değişmez değer hala tutun.</span><span class="sxs-lookup"><span data-stu-id="2b18a-118">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="2b18a-119">Aynı türde birden fazla sabitleri aynı anda örneğin bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="2b18a-119">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 <span data-ttu-id="2b18a-120">Bir sabit başlatmak için kullanılan ifade bir döngüsel başvuru oluşturmuyorsa için başka bir sabit başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="2b18a-120">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="2b18a-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b18a-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 <span data-ttu-id="2b18a-122">Sabitler işaretlenir olarak [ortak](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [içkorumalı](../../../csharp/language-reference/keywords/protected-internal.md)veya [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="2b18a-122">Constants can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="2b18a-123">Bu erişim değiştiricileri sınıfı kullanıcılarının sabiti nasıl erişebileceğinizi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2b18a-123">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="2b18a-124">Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="2b18a-124">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="2b18a-125">Bunlar değilmiş gibi sabitleri erişilir [statik](../../../csharp/language-reference/keywords/static.md) sabit değeri türündeki tüm örnekler için aynı olduğundan alanları.</span><span class="sxs-lookup"><span data-stu-id="2b18a-125">Constants are accessed as if they were [static](../../../csharp/language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="2b18a-126">Kullanmaz `static` bunları bildirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2b18a-126">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="2b18a-127">Sabit tanımlar sınıfında olmayan ifadeleri sabiti erişmek için sınıf adı, bir süre ve sabit adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b18a-127">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="2b18a-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b18a-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2b18a-129">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2b18a-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b18a-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b18a-130">See Also</span></span>  
 [<span data-ttu-id="2b18a-131">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2b18a-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2b18a-132">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="2b18a-132">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="2b18a-133">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="2b18a-133">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="2b18a-134">Türler</span><span class="sxs-lookup"><span data-stu-id="2b18a-134">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="2b18a-135">salt okunur</span><span class="sxs-lookup"><span data-stu-id="2b18a-135">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)  
 [<span data-ttu-id="2b18a-136">C# girişi bölüm bir: girişi türleri</span><span class="sxs-lookup"><span data-stu-id="2b18a-136">Immutability in C# Part One: Kinds of Immutability</span></span>](http://go.microsoft.com/fwlink/?LinkId=112379)
