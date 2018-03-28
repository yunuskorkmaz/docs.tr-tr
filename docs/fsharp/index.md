---
title: F# Kılavuzu
description: 'Bu kılavuz çeşitli öğrenim malzemelerini F #, .NET çalıştıran işlevsel bir programlama dili için genel bir bakış sağlar.'
author: jackfoxy
ms.author: phcart
ms.date: 03/19/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: a101233f396368c0bc25937c49f77699cb9f8cf2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="f-guide"></a><span data-ttu-id="76938-103">F# Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="76938-103">F# Guide</span></span>

<span data-ttu-id="76938-104">F # .NET üzerinde çalışan bir işlevsel programlama dilidir.</span><span class="sxs-lookup"><span data-stu-id="76938-104">F# is a functional programming language that runs on .NET.</span></span> <span data-ttu-id="76938-105">Ayrıca karışım işlevsel ve herhangi bir sorun için kolay çözümleri için nesne programlama izin vererek nesneleri için tam destek içerir.</span><span class="sxs-lookup"><span data-stu-id="76938-105">It also has full support for objects, letting you blend functional and object programming for pragmatic solutions to any problem.</span></span>

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

<span data-ttu-id="76938-106">F # kendi merkezinde üretkenlik hakkındadır.</span><span class="sxs-lookup"><span data-stu-id="76938-106">F# is about productivity at its heart.</span></span> <span data-ttu-id="76938-107">F # için araç desteği her yerden ve Gelişmiş özelliklerin tam ' dir.</span><span class="sxs-lookup"><span data-stu-id="76938-107">The tooling support for F# is ubiquitous and full of advanced features.</span></span>

## <a name="learning-f"></a><span data-ttu-id="76938-108">F # öğrenme</span><span class="sxs-lookup"><span data-stu-id="76938-108">Learning F#</span></span> #

<span data-ttu-id="76938-109">[F # Turu](tour.md) kod örnekleri çok önemli dil özelliklerine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="76938-109">[Tour of F#](tour.md) gives an overview of major language features with lots of code samples.</span></span> <span data-ttu-id="76938-110">F # için yeni ve dilinin nasıl çalıştığını için bir fikir almak istiyorsanız bu önerilir.</span><span class="sxs-lookup"><span data-stu-id="76938-110">This is recommended if you are new to F# and want to get a feel for how the language works.</span></span>

<span data-ttu-id="76938-111">[F # Visual Studio ile çalışmaya başlama](get-started/get-started-visual-studio.md) Windows olduğunuz ve tam Visual Studio IDE (Integraded geliştirme ortamı) deneyimi istiyor.</span><span class="sxs-lookup"><span data-stu-id="76938-111">[Get started with F# in Visual Studio](get-started/get-started-visual-studio.md) if you're on Windows and want the full Visual Studio IDE (Integraded Development Environment) experience.</span></span>

<span data-ttu-id="76938-112">[F # Visual Studio için Mac kullanmaya başlama](get-started/get-started-with-visual-studio-for-mac.md) üzerinde macOS olduğunuz ve Visual Studio IDE kullanmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="76938-112">[Get started with F# in Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) if you're on macOS and want to use a Visual Studio IDE.</span></span>

<span data-ttu-id="76938-113">[F # Visual Studio Code ile çalışmaya başlama](get-started/get-started-vscode.md) hafif, platformlar arası istediğiniz ve özellik dolu IDE deneyimi.</span><span class="sxs-lookup"><span data-stu-id="76938-113">[Get Started with F# in Visual Studio Code](get-started/get-started-vscode.md) if you want a lightweight, cross-platform, and feature-packed IDE experience.</span></span>

<span data-ttu-id="76938-114">[F # .NET Core CLI ile başlayın](get-started/get-started-command-line.md) komut satırı araçları kullanmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="76938-114">[Get started with F# with the .NET Core CLI](get-started/get-started-command-line.md) if you want to use command-line tools.</span></span>

<span data-ttu-id="76938-115">[F # ve Xamarin kullanmaya başlama](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) mobil programlama ile F # için.</span><span class="sxs-lookup"><span data-stu-id="76938-115">[Get started with F# and Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) for mobile programming with F#.</span></span>

## <a name="references"></a><span data-ttu-id="76938-116">Referanslar</span><span class="sxs-lookup"><span data-stu-id="76938-116">References</span></span>

<span data-ttu-id="76938-117">[F # dili başvurusu](language-reference/index.md) resmi, kapsamlı tüm F # dili özellikleri başvurudur.</span><span class="sxs-lookup"><span data-stu-id="76938-117">[F# Language Reference](language-reference/index.md) is the official, comprehensive reference for all F# language features.</span></span> <span data-ttu-id="76938-118">Her makalede söz dizimi açıklanmıştır ve kod örnekleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="76938-118">Each article explains the syntax and shows code samples.</span></span> <span data-ttu-id="76938-119">Belirli makaleleri bulmak için içindekiler tablosunda filtre çubuğunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76938-119">You can use the filter bar in the table of contents to find specific articles.</span></span>

<span data-ttu-id="76938-120">[F # Core kitaplık başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) F # Core kitaplık için API Başvurusu değil.</span><span class="sxs-lookup"><span data-stu-id="76938-120">[F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is the API reference for the F# Core Library.</span></span>


## <a name="additional-guides"></a><span data-ttu-id="76938-121">Ek kılavuzları</span><span class="sxs-lookup"><span data-stu-id="76938-121">Additional guides</span></span>

<span data-ttu-id="76938-122">[F # eğlenceli ve kar](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) F # öğrenme üzerinde kapsamlı ve çok ayrıntılı bir kitap.</span><span class="sxs-lookup"><span data-stu-id="76938-122">[F# for Fun and Profit](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) is a comprehensive and very detailed book on learning F#.</span></span> <span data-ttu-id="76938-123">F # topluluk tarafından vaftizine içeriklerini ve yazar.</span><span class="sxs-lookup"><span data-stu-id="76938-123">Its contents and author are beloved by the F# community.</span></span> <span data-ttu-id="76938-124">Hedef kitle öncelikle geliştiriciler nesne yönelimli programlama arka plana sahip olur.</span><span class="sxs-lookup"><span data-stu-id="76938-124">The target audience is primarily developers with an object oriented programming background.</span></span>

<span data-ttu-id="76938-125">[F # Wikibook programlama](https://en.wikibooks.org/wiki/F_Sharp_Programming) F # öğrenme hakkında bir wikibook değil.</span><span class="sxs-lookup"><span data-stu-id="76938-125">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) is a wikibook about learning F#.</span></span> <span data-ttu-id="76938-126">F # topluluk, bir ürün de olabilir.</span><span class="sxs-lookup"><span data-stu-id="76938-126">It is also a product of the F# community.</span></span> <span data-ttu-id="76938-127">Hedef kitle yeni F #, biraz nesne yönelimli programlama arka plan ile birden çok kişi var.</span><span class="sxs-lookup"><span data-stu-id="76938-127">The target audience is people who are new to F#, with a little bit of object oriented programming background.</span></span>

## <a name="learn-f-through-videos"></a><span data-ttu-id="76938-128">F # videolar bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="76938-128">Learn F# through videos</span></span>

<span data-ttu-id="76938-129">[F # Öğreticisi YouTube'da](https://www.youtube.com/watch?v=c7eNDJN758U) harika bir F Visual Studio kullanarak, çok sayıda harika örnekler 1,5 saat boyunca gösteren # giriş yapılır.</span><span class="sxs-lookup"><span data-stu-id="76938-129">[F# tutorial on YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) is a great introduction to F# using Visual Studio, showing lots of great examples over the course of 1.5 hours.</span></span> <span data-ttu-id="76938-130">Hedef kitle F # için yeni Visual Studio geliştiriciler ' dir.</span><span class="sxs-lookup"><span data-stu-id="76938-130">The target audience is Visual Studio developers who are new to F#.</span></span>

<span data-ttu-id="76938-131">[F # ile programlamaya giriş](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) ana düzenleyicisi olarak Visual Studio Code kullanan harika bir video serisidir.</span><span class="sxs-lookup"><span data-stu-id="76938-131">[Introduction to Programming with F#](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) is a great video series that uses Visual Studio Code as the main editor.</span></span> <span data-ttu-id="76938-132">Video serisi, herhangi bir şey başlar ve bir metin tabanlı RPG video oyun oluşturma ile biter.</span><span class="sxs-lookup"><span data-stu-id="76938-132">The video series starts from nothing and ends with building a text-based RPG video game.</span></span> <span data-ttu-id="76938-133">Hedef kitle geliştiriciler Visual Studio Code'da (veya basit bir IDE) tercih ve F # için yeni ' dir.</span><span class="sxs-lookup"><span data-stu-id="76938-133">The target audience is developers who prefer Visual Studio Code (or a lightweight IDE) and are new to F#.</span></span>

<span data-ttu-id="76938-134">[F # için geliştiriciler için Visual Studio 2017'de](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) yeni özelliklerden bazıları için F #'de Visual Studio 2017 gösteren bir video yol kullanmamaktır.</span><span class="sxs-lookup"><span data-stu-id="76938-134">[What's New in Visual Studio 2017 for F# For Developers](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) is a video course that shows some of the newer features for F# in Visual Studio 2017.</span></span> <span data-ttu-id="76938-135">Hedef kitle F # için yeni Visual Studio geliştiriciler ' dir.</span><span class="sxs-lookup"><span data-stu-id="76938-135">The target audience is Visual Studio developers who are new to F#.</span></span>

## <a name="other-useful-resources"></a><span data-ttu-id="76938-136">Diğer kullanışlı kaynaklar</span><span class="sxs-lookup"><span data-stu-id="76938-136">Other useful resources</span></span>

<span data-ttu-id="76938-137">[F # kod parçacıkları Web sitesi](http://www.fssnip.net) nasıl F mutlak başlangıç için yüksek oranda Gelişmiş parçacıkları arasında değişen #, neredeyse her şeyi yapılacağını gösteren kod parçacıkları yoğun bir kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="76938-137">The [F# Snippets Website](http://www.fssnip.net) contains a massive set of code snippets showing how to do just about anything in F#, ranging from absolute beginner to highly advanced snippets.</span></span>

<span data-ttu-id="76938-138">[F # yazılım Foundation kayma](http://fsharp.org/guides/slack/) yeni başlayanlar ve uzmanlar aynı şekilde, yüksek oranda active için harika bir yerdir ve dünyanın en iyi F # programcıları için Sohbet kullanılabilir bazıları vardır.</span><span class="sxs-lookup"><span data-stu-id="76938-138">The [F# Software Foundation Slack](http://fsharp.org/guides/slack/) is a great place for beginners and experts alike, is highly active, and has some of world's best F# programmers available for a chat.</span></span> <span data-ttu-id="76938-139">Birleştirme öneririz.</span><span class="sxs-lookup"><span data-stu-id="76938-139">We highly recommend joining.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="76938-140">F # yazılım Foundation</span><span class="sxs-lookup"><span data-stu-id="76938-140">The F# Software Foundation</span></span>

<span data-ttu-id="76938-141">Microsoft, Visual Studio Araçları ile F # dili ve birincil geliştirici olsa da, F # Ayrıca, F # yazılım Foundation (FSSF) gibi bağımsız bir foundation tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="76938-141">Although Microsoft is the primary developer of the F# language and its tools in Visual Studio, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="76938-142">F # yazılım Foundation Görev yükseltmek, korumak ve F # programlama dilini ilerletmek için destek ve F # programcıları farklı ve uluslararası topluluğu büyümesini kolaylaştırmak sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="76938-142">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="76938-143">Daha fazla bilgi edinin ve söz konusu almak için kullanıma [fsharp.org](http://fsharp.org). Katılmak ücretsizdir ve F # geliştiricileri Foundation'da ağ kaçırılması out için istemediğiniz bir şeydir!</span><span class="sxs-lookup"><span data-stu-id="76938-143">To learn more and get involved, check out [fsharp.org](http://fsharp.org). It's free to join, and the network of F# developers in the foundation is something you don't want to miss out on!</span></span>
