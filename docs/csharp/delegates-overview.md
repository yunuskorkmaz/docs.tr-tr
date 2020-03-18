---
title: Temsilcilere Giriş
description: Temel kavramları tanıtan ve delegeler için dil tasarımı hedeflerini tartışan bu genel bakış konusundaki temsilciler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146235"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="b5457-103">Temsilcilere Giriş</span><span class="sxs-lookup"><span data-stu-id="b5457-103">Introduction to Delegates</span></span>

<span data-ttu-id="b5457-104">Temsilciler .NET'te *geç bağlama* mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5457-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="b5457-105">Geç Bağlama, arayanın algoritmanın bir bölümünü uygulayan en az bir yöntem sağladığı bir algoritma oluşturduğunuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5457-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="b5457-106">Örneğin, bir astronomi uygulamasındaki yıldızların listesini sıralamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b5457-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="b5457-107">Bu yıldızları dünya yla olan uzaklıklarına, yıldızın büyüklüğüne ya da algılanan parlaklıklarına göre sıralamayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5457-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="b5457-108">Tüm bu durumlarda, Sıralama() yöntemi temelde aynı şeyi yapar: listedeki öğeleri bazı karşılaştırmalara göre düzenler.</span><span class="sxs-lookup"><span data-stu-id="b5457-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="b5457-109">İki yıldızı karşılaştıran kod, sıralama sıralamalarının her biri için farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b5457-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="b5457-110">Bu tür çözümler yarım yüzyıl boyunca yazılımda kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5457-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="b5457-111">C# dil temsilcisi kavramı birinci sınıf dil desteği sağlar ve kavram etrafında sınıf güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5457-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="b5457-112">Bu serinin ilerleyen saatlerinde göreceğiniz gibi, bu gibi algoritmalar için yazdığınız C# kodu tür güvenlidir ve türlerin bağımsız değişkenler ve iade türleri için eşleştirdiğinden emin olmak için dili ve derleyiciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5457-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="b5457-113">Delegeler için Dil Tasarımı Hedefleri</span><span class="sxs-lookup"><span data-stu-id="b5457-113">Language Design Goals for Delegates</span></span>

<span data-ttu-id="b5457-114">Dil tasarımcıları sonunda delege oldu özelliği için çeşitli hedefler numaralandırılmış.</span><span class="sxs-lookup"><span data-stu-id="b5457-114">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="b5457-115">Takım, geç bağlama algoritmaları için kullanılabilecek ortak bir dil yapısı istedi.</span><span class="sxs-lookup"><span data-stu-id="b5457-115">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="b5457-116">Bu, geliştiricilerin bir kavramı öğrenmesini ve aynı kavramı birçok farklı yazılım sorununda kullanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b5457-116">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="b5457-117">İkinci olarak, takım hem tek hem de çok noktaya yayın yöntemi çağrılarını desteklemek istedi.</span><span class="sxs-lookup"><span data-stu-id="b5457-117">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="b5457-118">(Çok noktaya yayın delegeleri, birden çok yöntem çağrısını birbirine zincirleyen temsilcilerdir.</span><span class="sxs-lookup"><span data-stu-id="b5457-118">(Multicast delegates are delegates that chain together multiple method calls.</span></span>
<span data-ttu-id="b5457-119">[Bu serinin daha sonra](delegate-class.md)örneklerini görürsünüz .)</span><span class="sxs-lookup"><span data-stu-id="b5457-119">You'll see examples [later in this series](delegate-class.md).)</span></span>

<span data-ttu-id="b5457-120">Ekip, temsilcilerin geliştiricilerin tüm C# yapılarından beklediği aynı tür güvenliğini desteklemelerini istedi.</span><span class="sxs-lookup"><span data-stu-id="b5457-120">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span>

<span data-ttu-id="b5457-121">Son olarak, takım, bir olay deseni, temsilcilerin veya herhangi bir geç bağlama algoritmasının çok yararlı olduğu belirli bir desen olduğunu fark etti.</span><span class="sxs-lookup"><span data-stu-id="b5457-121">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="b5457-122">Takım, temsilciler için kodun .NET olay deseni için temel oluşturabileceğinden emin olmak istedi.</span><span class="sxs-lookup"><span data-stu-id="b5457-122">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="b5457-123">Tüm bu çalışmaların sonucu C# ve .NET'teki temsilci ve olay desteğiydi.</span><span class="sxs-lookup"><span data-stu-id="b5457-123">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="b5457-124">Bu bölümdeki kalan makaleler, dil özelliklerini, kitaplık desteğini ve temsilcilerle çalışırken kullanılan yaygın deyimleri kapsayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5457-124">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="b5457-125">Anahtar kelimeyi `delegate` ve hangi kodu oluşturduğunu öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5457-125">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="b5457-126">Sınıftaki özellikler ve bu `System.Delegate` özelliklerin nasıl kullanıldığı hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5457-126">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="b5457-127">Türde güvenli temsilciler oluşturmayı ve temsilciler aracılığıyla çağrılabilecek yöntemleroluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5457-127">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="b5457-128">Lambda ifadelerini kullanarak delegeler ve etkinliklerle nasıl çalışacağınızı da öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5457-128">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="b5457-129">Delegelerin LINQ'nun yapı taşlarından biri haline geldiği yeri göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5457-129">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="b5457-130">Temsilcilerin .NET olay deseninin temelini nasıl oluşturduklarını ve nasıl farklı olduklarını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b5457-130">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="b5457-131">Genel olarak, temsilcilerin .NET'te programlamanın ayrılmaz bir parçası olduğunu ve çerçeve API'leriyle nasıl çalıştığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b5457-131">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="b5457-132">Başlayalım.</span><span class="sxs-lookup"><span data-stu-id="b5457-132">Let's get started.</span></span>

[<span data-ttu-id="b5457-133">Sonraki</span><span class="sxs-lookup"><span data-stu-id="b5457-133">Next</span></span>](delegate-class.md)
