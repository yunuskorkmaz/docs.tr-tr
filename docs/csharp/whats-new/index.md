---
title: C# ' - yenilikler C# Kılavuzu
description: C# dili nasıl gelişen
keywords: C#, yenilikler, en son özellikleri Roslyn
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 719fbe826b0b115b19067dbaf0d04f14e6534890
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-in-c"></a><span data-ttu-id="ea992-104">C# ' ta yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="ea992-104">What's new in C#</span></span> #

<span data-ttu-id="ea992-105">Bu sayfa C# dilinin ana her sürümdeki yeni özelliklerin bir yol haritası sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea992-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="ea992-106">Aşağıdaki bağlantılar, her sürümde eklenen önemli özellikleri hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea992-106">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea992-107">C# dili türleri ve yöntemleri dayanan bir *standart Kitaplığı* özelliklerinden bazıları için.</span><span class="sxs-lookup"><span data-stu-id="ea992-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="ea992-108">Özel durum işleme bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="ea992-108">One example is exception processing.</span></span> <span data-ttu-id="ea992-109">Her `throw` deyiminin veya ifadesinin işaretli oluşturulan nesne emin olmak için türetilen <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="ea992-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="ea992-110">Benzer şekilde, her `catch` yakalanan türü türetilmiş emin olmak için denetlenir <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="ea992-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="ea992-111">Her bir sürümü yeni gereksinimler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea992-111">Each version may add new requirements.</span></span> <span data-ttu-id="ea992-112">Eski ortamlarda en son dil özellikleri kullanmak için belirli kitaplıkları yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ea992-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="ea992-113">Bu bağımlılıklar, sayfa her belirli bir sürümü için belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ea992-113">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="ea992-114">Hakkında daha fazla bilgiyi [dil ve kitaplık arasındaki ilişkileri](relationships-between-language-and-library.md) bu bağımlılığı hakkında arka plan bilgileri için.</span><span class="sxs-lookup"><span data-stu-id="ea992-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="ea992-115">[C# 7.2](csharp-7-2.md):</span><span class="sxs-lookup"><span data-stu-id="ea992-115">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="ea992-116">Bu sayfa, C# dilinde en son özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea992-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="ea992-117">C# 7.2 şu anda kullanılabilir [Visual Studio 2017 sürüm 15,5](https://www.visualstudio.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="ea992-117">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="ea992-118">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="ea992-118">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="ea992-119">Bu sayfa, C# 7.1 özellikleri açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ea992-119">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="ea992-120">Bu özellikler eklenmiştir [Visual Studio 2017 sürüm 15.3](https://www.visualstudio.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="ea992-120">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="ea992-121">[C# 7](csharp-7.md):</span><span class="sxs-lookup"><span data-stu-id="ea992-121">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="ea992-122">Bu sayfa, C# 7'de eklenen özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea992-122">This page describes the features added in C# 7.</span></span> <span data-ttu-id="ea992-123">Bu özellikler eklenmiştir [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) ve [.NET Core 1.0](../../core/whats-new/index.md) ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="ea992-123">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="ea992-124">[C# 6](csharp-6.md):</span><span class="sxs-lookup"><span data-stu-id="ea992-124">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="ea992-125">Bu sayfayı C# 6'eklenen özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea992-125">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="ea992-126">Bu özellikler Visual Studio 2015'te .NET Core 1.0 ve Windows geliştiricileri için C# macOS ve Linux keşfetme geliştiriciler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea992-126">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="ea992-127">[Platform desteği arası](../../core/index.md):</span><span class="sxs-lookup"><span data-stu-id="ea992-127">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="ea992-128">C# .NET Core desteğini birden çok platformlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="ea992-128">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="ea992-129">Çalışırken ilgileniyorsanız C# macOS veya çok birini desteklenen Linux dağıtımları, .NET Core hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="ea992-129">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="ea992-130">Önceki Sürümler</span><span class="sxs-lookup"><span data-stu-id="ea992-130">Previous Versions</span></span>
<span data-ttu-id="ea992-131">Aşağıdaki listeler dil C# ve Visual Studio .NET önceki sürümlerinde sunulan özellikler anahtar.</span><span class="sxs-lookup"><span data-stu-id="ea992-131">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="ea992-132">Visual Studio .NET 2013:</span><span class="sxs-lookup"><span data-stu-id="ea992-132">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="ea992-133">Visual Studio'nun bu sürümü, hata düzeltmeleri, performans iyileştirmeleri ve hangi .NET derleyici Platform SDK'sı hale geldi .NET derleyici Platformu ("Roslyn") teknolojisi önizlemesini dahil<!--Link to ../roslyn/index.md-->.</span><span class="sxs-lookup"><span data-stu-id="ea992-133">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="ea992-134">C# 5, Visual Studio .NET 2012:</span><span class="sxs-lookup"><span data-stu-id="ea992-134">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="ea992-135">`Async` / `await`, ve [arayan bilgileri](../programming-guide/concepts/caller-information.md) öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="ea992-135">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="ea992-136">C# 4, Visual Studio .NET 2010:</span><span class="sxs-lookup"><span data-stu-id="ea992-136">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="ea992-137">`Dynamic`, [bağımsız değişkenleri adlı](../programming-guide/classes-and-structs/named-and-optional-arguments.md), isteğe bağlı parametreler ve genel [Kovaryans ve karşıt farkı](../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="ea992-137">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="ea992-138">C# 3, Visual Studio .NET 2008:</span><span class="sxs-lookup"><span data-stu-id="ea992-138">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="ea992-139">Nesne ve koleksiyon başlatıcıları, lambda ifadeleri, genişletme yöntemleri, anonim türler, otomatik özellikleri, yerel `var` çıkarım, yazın ve [dil tümleşik sorgu (LINQ)](../programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="ea992-139">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="ea992-140">C# 2, Visual Studio .NET 2005:</span><span class="sxs-lookup"><span data-stu-id="ea992-140">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="ea992-141">Anonim yöntemler, genel türler, boş değer atanabilir türler, Yineleyiciler/verim `static` sınıfları ve temsilciler Kovaryans ve karşıt varyansını.</span><span class="sxs-lookup"><span data-stu-id="ea992-141">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="ea992-142">C# 1.1, Visual Studio .NET 2003:</span><span class="sxs-lookup"><span data-stu-id="ea992-142">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="ea992-143">`#line`pragma ve xml belge açıklamaları.</span><span class="sxs-lookup"><span data-stu-id="ea992-143">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="ea992-144">C# 1, Visual Studio .NET 2002:</span><span class="sxs-lookup"><span data-stu-id="ea992-144">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="ea992-145">İlk sürümünü [C#](../csharp.md).</span><span class="sxs-lookup"><span data-stu-id="ea992-145">The first release of [C#](../csharp.md).</span></span>   
