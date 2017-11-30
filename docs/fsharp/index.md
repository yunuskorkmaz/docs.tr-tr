---
title: "F # Kılavuzu"
description: "F # programlama dili, işlevsel programlama için birinci sınıf destek sağlar .NET için bir açık kaynak dili hakkında bilgi edinin."
keywords: .NET, .NET core
author: jackfoxy
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 4ddd77cef6cf70a63f1af81359d82eda27a01593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="f-guide"></a><span data-ttu-id="6388e-104">F # Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6388e-104">F# Guide</span></span>

<span data-ttu-id="6388e-105">F # nesne yönelimli ve kesinlik temelli programlama desteğinin yanı sıra işlevsel programlama için birinci sınıf destek sağlayan .NET için programlama dili bir platformlar arası, açık bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="6388e-105">F# is a cross-platform, open source programming language for .NET which provides first-class support for functional programming, along with support of object-oriented and imperative programming.</span></span>  <span data-ttu-id="6388e-106">Visual F # derleyici ve araç Microsoft'un uygulama ve F programlama dili, F # .NET, birinci sınıf üyesi yapma # araç kümesidir.</span><span class="sxs-lookup"><span data-stu-id="6388e-106">The Visual F# compiler and tooling are Microsoft's implementation and tooling for the F# programming language, making F# a first-class member of .NET.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="6388e-107">F # için yeni başladıysanız</span><span class="sxs-lookup"><span data-stu-id="6388e-107">If You're New to F#</span></span> #

<span data-ttu-id="6388e-108">F # için yeni başladıysanız ile başlayan [Tur, F #](tour.md) dil özetini almak için.</span><span class="sxs-lookup"><span data-stu-id="6388e-108">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language.</span></span>

<span data-ttu-id="6388e-109">Ayrıca gitmenizi önerilir [ilk sınıf değerleri olarak işlevler](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> F # ile çalışmak için gerekli olan işlevsel programlama kavramları öğrenin.</span><span class="sxs-lookup"><span data-stu-id="6388e-109">It's also recommended that you go through the [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> to learn Functional Programming concepts which are essential to working with F#.</span></span>

<span data-ttu-id="6388e-110">[Öğreticileri](tutorials/getting-started/index.md) çeşitli beceri düzeylerini ve dil özellikleri için adım adım kılavuzlar de vardır.</span><span class="sxs-lookup"><span data-stu-id="6388e-110">The [Tutorials](tutorials/getting-started/index.md) also have step-by-step guides for various skill levels and features of the language.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="6388e-111">F # ile deneyimli varsa</span><span class="sxs-lookup"><span data-stu-id="6388e-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="6388e-112">F # yararlanabileceğinizi biliyorsanız, çok sayıda kullanımda bulacaksınız [dil başvurusu](language-reference/index.md), hangi dil her yönden baştan sona, belgeleri takıma tarafından çok sayıda kod örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6388e-112">If you know your way around F#, you'll find a lot of use in the [Language Reference](language-reference/index.md), which documents each aspect of the language thoroughly, supplemented by numerous code samples.</span></span>  <span data-ttu-id="6388e-113">Ayrıca, çok sayıda kullanımda bulabilirsiniz [F # Core kitaplık başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span><span class="sxs-lookup"><span data-stu-id="6388e-113">You'll also find a lot of use in the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span></span>  <span data-ttu-id="6388e-114">F # Core kitaplık başvurusu sonunda MSDN uzağa doğru ve geçerli bu belgeleri olarak taşınır.</span><span class="sxs-lookup"><span data-stu-id="6388e-114">The F# Core Library Reference will eventually move away from MSDN and into these current docs.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="6388e-115">F # yazılım Foundation</span><span class="sxs-lookup"><span data-stu-id="6388e-115">The F# Software Foundation</span></span>

<span data-ttu-id="6388e-116">Microsoft F # dili ve Visual F # Araçları birincil geliştiricisi olsa da, F # Ayrıca, F # yazılım Foundation (FSSF) gibi bağımsız bir foundation tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6388e-116">Although Microsoft is the primary developer of the F# language and Visual F# Tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="6388e-117">F # yazılım Foundation Görev yükseltmek, korumak ve F # programlama dilini ilerletmek için destek ve F # programcıları farklı ve uluslararası topluluğu büyümesini kolaylaştırmak sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6388e-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="6388e-118">Daha fazla bilgi edinin ve söz konusu almak için kullanıma [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="6388e-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="6388e-119">Belgeler</span><span class="sxs-lookup"><span data-stu-id="6388e-119">Documentation</span></span>

* [<span data-ttu-id="6388e-120">Öğreticiler</span><span class="sxs-lookup"><span data-stu-id="6388e-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="6388e-121">[İlk sınıf değerleri olarak işlevler](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="6388e-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="6388e-122">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6388e-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="6388e-123">F # Core Kitaplık Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6388e-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="6388e-124">Çevrimiçi kaynaklar okuma</span><span class="sxs-lookup"><span data-stu-id="6388e-124">Online Reading Resources</span></span>

* [<span data-ttu-id="6388e-125">F # eğlenceli ve kar Gitbook için</span><span class="sxs-lookup"><span data-stu-id="6388e-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="6388e-126">F # programlama Wikibook</span><span class="sxs-lookup"><span data-stu-id="6388e-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="6388e-127">Video öğrenme kaynakları</span><span class="sxs-lookup"><span data-stu-id="6388e-127">Video Learning Resources</span></span>

* [<span data-ttu-id="6388e-128">F # serisi YouTube'da ile programlamaya giriş</span><span class="sxs-lookup"><span data-stu-id="6388e-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="6388e-129">F # FSharpTV seriyi giriş</span><span class="sxs-lookup"><span data-stu-id="6388e-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="6388e-130">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6388e-130">Further Resources</span></span>

* [<span data-ttu-id="6388e-131">F # kaynaklar üzerinde fsharp.org öğrenme</span><span class="sxs-lookup"><span data-stu-id="6388e-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="6388e-132">F # kod parçacıkları Web sitesi</span><span class="sxs-lookup"><span data-stu-id="6388e-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="6388e-133">F # yazılım Foundation</span><span class="sxs-lookup"><span data-stu-id="6388e-133">F# Software Foundation</span></span>](http://fsharp.org)
