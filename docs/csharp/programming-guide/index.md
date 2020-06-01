---
title: C# Programlama Kılavuzu
ms.date: 05/02/2017
f1_keywords:
- cs.langref
helpviewer_keywords:
- reference tables [C#]
- C# language, programming guide
- Visual C#, programming concepts
- C# language, concepts
ms.assetid: ac0f23a2-6bf3-4077-be99-538ae5fd3bc5
ms.openlocfilehash: df69d895dee51f1bad1fb6164fcb18996ee3eef4
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241662"
---
# <a name="c-programming-guide"></a><span data-ttu-id="0b7f4-102">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b7f4-102">C# programming guide</span></span>

<span data-ttu-id="0b7f4-103">Bu bölüm, .NET aracılığıyla C# tarafından erişilebilen temel C# dil özellikleri ve özellikleri hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b7f4-103">This section provides detailed information on key C# language features and features accessible to C# through .NET.</span></span>  
  
 <span data-ttu-id="0b7f4-104">Bu bölümün çoğu, C# ve genel programlama kavramları hakkında bir şeyi zaten bildiğiniz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b7f4-104">Most of this section assumes that you already know something about C# and general programming concepts.</span></span> <span data-ttu-id="0b7f4-105">Programlama veya C# ile tam bir başlangıç yapıyorsanız, önceden programlama bilgisi gerekli olmayan [C# öğreticilerine](../tutorials/intro-to-csharp/index.md) veya [.net-tarayıcı öğreticisine](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1)giriş ' i ziyaret etmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b7f4-105">If you are a complete beginner with programming or with C#, you might want to visit the [Introduction to C# Tutorials](../tutorials/intro-to-csharp/index.md) or [.NET In-Browser Tutorial](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1), where no prior programming knowledge is required.</span></span>  
  
 <span data-ttu-id="0b7f4-106">Belirli anahtar sözcükler, işleçler ve Önişlemci yönergeleri hakkında daha fazla bilgi için bkz. [C# başvurusu](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b7f4-106">For information about specific keywords, operators, and preprocessor directives, see [C# Reference](../language-reference/index.md).</span></span> <span data-ttu-id="0b7f4-107">C# dil belirtimi hakkında daha fazla bilgi için bkz. [C# dil belirtimi](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="0b7f4-107">For information about the C# Language Specification, see [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>  
  
## <a name="program-sections"></a><span data-ttu-id="0b7f4-108">Program bölümleri</span><span class="sxs-lookup"><span data-stu-id="0b7f4-108">Program sections</span></span>

[<span data-ttu-id="0b7f4-109">C# programı içinde</span><span class="sxs-lookup"><span data-stu-id="0b7f4-109">Inside a C# Program</span></span>](./inside-a-program/index.md)  
  
[<span data-ttu-id="0b7f4-110">Main () ve komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0b7f4-110">Main() and Command-Line Arguments</span></span>](./main-and-command-args/index.md)  

## <a name="language-sections"></a><span data-ttu-id="0b7f4-111">Dil bölümleri</span><span class="sxs-lookup"><span data-stu-id="0b7f4-111">Language Sections</span></span>

[<span data-ttu-id="0b7f4-112">Deyimler, Ifadeler ve Işleçler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-112">Statements, Expressions, and Operators</span></span>](./statements-expressions-operators/index.md)  

 [<span data-ttu-id="0b7f4-113">Türler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-113">Types</span></span>](./types/index.md)  

 [<span data-ttu-id="0b7f4-114">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="0b7f4-114">Classes and Structs</span></span>](./classes-and-structs/index.md)  
  
 [<span data-ttu-id="0b7f4-115">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-115">Interfaces</span></span>](./interfaces/index.md)  

 [<span data-ttu-id="0b7f4-116">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-116">Delegates</span></span>](./delegates/index.md)  

 [<span data-ttu-id="0b7f4-117">Diziler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-117">Arrays</span></span>](./arrays/index.md)  
  
 [<span data-ttu-id="0b7f4-118">Dizeler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-118">Strings</span></span>](./strings/index.md)  
  
 [<span data-ttu-id="0b7f4-119">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-119">Properties</span></span>](./classes-and-structs/properties.md)  
  
 [<span data-ttu-id="0b7f4-120">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0b7f4-120">Indexers</span></span>](./indexers/index.md)  
  
 [<span data-ttu-id="0b7f4-121">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-121">Events</span></span>](./events/index.md)  
  
 [<span data-ttu-id="0b7f4-122">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-122">Generics</span></span>](./generics/index.md)  
  
 [<span data-ttu-id="0b7f4-123">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-123">Iterators</span></span>](./concepts/iterators.md)
  
 [<span data-ttu-id="0b7f4-124">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0b7f4-124">LINQ Query Expressions</span></span>](../linq/index.md)  
  
 [<span data-ttu-id="0b7f4-125">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0b7f4-125">Lambda Expressions</span></span>](./statements-expressions-operators/lambda-expressions.md)  
  
 [<span data-ttu-id="0b7f4-126">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="0b7f4-126">Namespaces</span></span>](./namespaces/index.md)  
  
 [<span data-ttu-id="0b7f4-127">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-127">Unsafe Code and Pointers</span></span>](./unsafe-code-pointers/index.md)  
  
 [<span data-ttu-id="0b7f4-128">XML belge açıklamaları</span><span class="sxs-lookup"><span data-stu-id="0b7f4-128">XML Documentation Comments</span></span>](./xmldoc/index.md)  
  
## <a name="platform-sections"></a><span data-ttu-id="0b7f4-129">Platform bölümleri</span><span class="sxs-lookup"><span data-stu-id="0b7f4-129">Platform Sections</span></span>

 [<span data-ttu-id="0b7f4-130">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="0b7f4-130">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
  
 [<span data-ttu-id="0b7f4-131">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="0b7f4-131">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
  
 [<span data-ttu-id="0b7f4-132">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b7f4-132">Attributes</span></span>](./concepts/attributes/index.md)  
  
 [<span data-ttu-id="0b7f4-133">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="0b7f4-133">Collections</span></span>](./concepts/collections.md)  
  
 [<span data-ttu-id="0b7f4-134">Özel Durumlar ve Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="0b7f4-134">Exceptions and Exception Handling</span></span>](./exceptions/index.md)  
  
 [<span data-ttu-id="0b7f4-135">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0b7f4-135">File System and the Registry (C# Programming Guide)</span></span>](./file-system/index.md)  
  
 [<span data-ttu-id="0b7f4-136">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="0b7f4-136">Interoperability</span></span>](./interop/index.md)  
  
 [<span data-ttu-id="0b7f4-137">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0b7f4-137">Reflection</span></span>](./concepts/reflection.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b7f4-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b7f4-138">See also</span></span>

- [<span data-ttu-id="0b7f4-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0b7f4-139">C# Reference</span></span>](../language-reference/index.md)
