---
title: "F # Kılavuzu"
description: "F #, .NET çalıştıran işlevsel bir programlama dili hakkında bilgi edinin."
keywords: .NET, .NET core
author: jackfoxy
ms.author: phcart
ms.date: 12/01/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 45f5d2ca794ccea7a35cf6c0bf9d58a3e6500453
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="f-guide"></a><span data-ttu-id="0fda0-104">F # Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0fda0-104">F# Guide</span></span>

<span data-ttu-id="0fda0-105">F # .NET üzerinde çalışan bir işlevsel programlama dilidir.</span><span class="sxs-lookup"><span data-stu-id="0fda0-105">F# is a functional programming language which runs on .NET.</span></span>  <span data-ttu-id="0fda0-106">Destek işlevsel programlama yapıları yanı sıra nesnesi programlama özellikleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="0fda0-106">In addition to supporting functional programming constructs, it also has object programming capabilities.</span></span>  <span data-ttu-id="0fda0-107">Bu karma nesne yönelimli özellikleriyle işlevsel programlama F # herhangi bir görev karşılamak için kolay bir dil yapar.</span><span class="sxs-lookup"><span data-stu-id="0fda0-107">This hybrid of functional programming with object-oriented capabilities makes F# a pragmatic language for accomplishing any task.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="0fda0-108">F # için yeni başladıysanız</span><span class="sxs-lookup"><span data-stu-id="0fda0-108">If You're New to F#</span></span> #

<span data-ttu-id="0fda0-109">F # için yeni başladıysanız ile başlayan [Tur, F #](tour.md) dil genel bir bakış ve bazı programlama kavramları almak için.</span><span class="sxs-lookup"><span data-stu-id="0fda0-109">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language and some of its programming concepts.</span></span>  <span data-ttu-id="0fda0-110">Visual Studio kullanıyorsanız, aynı içerik öğretici proje şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="0fda0-110">If you're using Visual Studio, the Tutorial project template contains the same content.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="0fda0-111">F # ile deneyimli varsa</span><span class="sxs-lookup"><span data-stu-id="0fda0-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="0fda0-112">F # yararlanabileceğinizi bilmek veya belirli bir dil yapısı hakkında daha fazla bilgi edinmek için bkz: [dil başvurusu](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fda0-112">If you know your way around F#, or want to learn more about a specific language construct, see the [Language Reference](language-reference/index.md).</span></span>  <span data-ttu-id="0fda0-113">Tüm F # dili özelliklerinden kapsamlı bir kılavuzdur.</span><span class="sxs-lookup"><span data-stu-id="0fda0-113">It's a thorough guide of all F# language capabilities.</span></span>

<span data-ttu-id="0fda0-114">Ayrıca, [F # Core kitaplık başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) FSharp.Core, bir parçası olan F # core kitaplık hakkında bilgi için mükemmel bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="0fda0-114">Additionally, the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is a great resource for learning about FSharp.Core, the core library which is a part of F#.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="0fda0-115">F # yazılım Foundation</span><span class="sxs-lookup"><span data-stu-id="0fda0-115">The F# Software Foundation</span></span>

<span data-ttu-id="0fda0-116">Microsoft birincil geliştirici F # dili ve kendi araç olsa da, F # Ayrıca, F # yazılım Foundation (FSSF) gibi bağımsız bir foundation tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0fda0-116">Although Microsoft is the primary developer of the F# language and its tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="0fda0-117">F # yazılım Foundation Görev yükseltmek, korumak ve F # programlama dilini ilerletmek için destek ve F # programcıları farklı ve uluslararası topluluğu büyümesini kolaylaştırmak sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="0fda0-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="0fda0-118">Daha fazla bilgi edinin ve söz konusu almak için kullanıma [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="0fda0-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="0fda0-119">Belgeler</span><span class="sxs-lookup"><span data-stu-id="0fda0-119">Documentation</span></span>

* [<span data-ttu-id="0fda0-120">Öğreticiler</span><span class="sxs-lookup"><span data-stu-id="0fda0-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="0fda0-121">[İlk sınıf değerleri olarak işlevler](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="0fda0-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="0fda0-122">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0fda0-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="0fda0-123">F # Core Kitaplık Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0fda0-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="0fda0-124">Çevrimiçi kaynaklar okuma</span><span class="sxs-lookup"><span data-stu-id="0fda0-124">Online Reading Resources</span></span>

* [<span data-ttu-id="0fda0-125">F # eğlenceli ve kar Gitbook için</span><span class="sxs-lookup"><span data-stu-id="0fda0-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="0fda0-126">F # programlama Wikibook</span><span class="sxs-lookup"><span data-stu-id="0fda0-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="0fda0-127">Video öğrenme kaynakları</span><span class="sxs-lookup"><span data-stu-id="0fda0-127">Video Learning Resources</span></span>

* [<span data-ttu-id="0fda0-128">F # serisi YouTube'da ile programlamaya giriş</span><span class="sxs-lookup"><span data-stu-id="0fda0-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="0fda0-129">F # FSharpTV seriyi giriş</span><span class="sxs-lookup"><span data-stu-id="0fda0-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="0fda0-130">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0fda0-130">Further Resources</span></span>

* [<span data-ttu-id="0fda0-131">F # kaynaklar üzerinde fsharp.org öğrenme</span><span class="sxs-lookup"><span data-stu-id="0fda0-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="0fda0-132">F # kod parçacıkları Web sitesi</span><span class="sxs-lookup"><span data-stu-id="0fda0-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="0fda0-133">F # yazılım Foundation</span><span class="sxs-lookup"><span data-stu-id="0fda0-133">F# Software Foundation</span></span>](http://fsharp.org)