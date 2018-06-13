---
title: Temsilciler giriş
description: Temel kavramları tanıtır ve temsilciler dil tasarım hedefleri ele bu genel bakış konusunun temsilcileri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: d42d9d10aeaa153f12933fa3a59e58719f7741e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212193"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="f5813-103">Temsilciler giriş</span><span class="sxs-lookup"><span data-stu-id="f5813-103">Introduction to Delegates</span></span>

[<span data-ttu-id="f5813-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="f5813-104">Previous</span></span>](delegates-events.md)

<span data-ttu-id="f5813-105">Temsilciler sağlayan bir *geç bağlama* .NET mekanizması.</span><span class="sxs-lookup"><span data-stu-id="f5813-105">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="f5813-106">Geç bağlama burada çağıran algoritmanın bölümü uygulayan en az bir yöntem de sağlayan bir algoritma oluşturmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f5813-106">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="f5813-107">Örneğin, yıldız astronomide uygulamada listesini sıralama göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f5813-107">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="f5813-108">Bu yıldız dünya veya yıldız ya da kendi algılanan parlaklığını büyüklüğünü kendi mesafe göre sıralamak tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5813-108">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="f5813-109">Bu durumlarda, Sort() yöntemi temelde aynı şeyi yapar: bazı karşılaştırma üzerine dayalı listesindeki öğeleri düzenler.</span><span class="sxs-lookup"><span data-stu-id="f5813-109">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="f5813-110">İki yıldız karşılaştırır kod her sıralama sıralamalarını için farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f5813-110">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="f5813-111">Bu tür çözümler için yarım bir century yazılımda kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="f5813-111">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="f5813-112">C# dili temsilci kavram, birinci sınıf dil desteği ve tür güvenliği kavramı çevresinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5813-112">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="f5813-113">Bu seri içinde anlatıldığı gibi böyle algoritmalar için yazma C# kodu güvenli türü ve dili ve türleri için bağımsız değişken eşleşen ve dönüş türleri emin olmak için derleyici kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5813-113">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="f5813-114">Temsilciler için dil tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="f5813-114">Language Design Goals for Delegates</span></span>

<span data-ttu-id="f5813-115">Dil tasarımcıları sonunda temsilciler hale geldi özelliği için çeşitli hedefleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="f5813-115">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="f5813-116">Takım herhangi geç bağlama algoritmaları için kullanılan ortak bir dil yapısı istedik.</span><span class="sxs-lookup"><span data-stu-id="f5813-116">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="f5813-117">Geliştiricilerin bir kavram öğrenmek ve bu aynı kavram arasında birçok farklı yazılım sorunlarını kullanmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5813-117">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="f5813-118">İkinci olarak, hem tek ve çok noktaya yayın yöntem çağrılarını desteklemek takım istedik.</span><span class="sxs-lookup"><span data-stu-id="f5813-118">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="f5813-119">(Çok noktaya yayın temsilcileri temsilciler birden çok yöntem birlikte zincirlenen burada içindir.</span><span class="sxs-lookup"><span data-stu-id="f5813-119">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="f5813-120">Örnekler görürsünüz [bu serideki sonraki](delegate-class.md).</span><span class="sxs-lookup"><span data-stu-id="f5813-120">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="f5813-121">Takım tüm C# yapılarını geliştiriciler beklediğiniz aynı tür güvenliği desteklemek için temsilciler istedik.</span><span class="sxs-lookup"><span data-stu-id="f5813-121">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="f5813-122">Son olarak, bir olay desen belirli bir desene olduğunu takım tanınan burada temsilcileri ya da herhangi bir geç bağlama algoritma) çok kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5813-122">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="f5813-123">Temsilciler kodunu .NET olay desenini temel sağlayabilir emin olmak takım istedik.</span><span class="sxs-lookup"><span data-stu-id="f5813-123">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="f5813-124">Tüm iş C# ve .NET temsilci ve olay desteği olduğunu sonucu.</span><span class="sxs-lookup"><span data-stu-id="f5813-124">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="f5813-125">Bu bölümdeki kalan makaleleri dil özellikleri, kitaplık desteği ve temsilciler ile çalışırken, kullanılan ortak deyimleri ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="f5813-125">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="f5813-126">Hakkında bilgi edineceksiniz `delegate` anahtar sözcüğü ve ne kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5813-126">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="f5813-127">Özellikler hakkında bilgi edineceksiniz `System.Delegate` sınıfı ve bu özellikleri nasıl kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5813-127">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="f5813-128">Türü güvenli temsilciler oluşturma ve temsilciler çağrılan yöntem oluşturulacağını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f5813-128">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="f5813-129">Lambda ifadeleri kullanarak Temsilciler ve olaylar ile çalışmaya nasıl da öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f5813-129">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="f5813-130">Burada temsilciler yapı taşları birini LINQ hale görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f5813-130">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="f5813-131">Temsilciler .NET olay düzeni için temel şeklini ve nasıl farklı bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f5813-131">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="f5813-132">Genel olarak, nasıl temsilciler .NET ile programlama ve API framework ile çalışma ayrılmaz bir parçası olan görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f5813-132">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="f5813-133">Haydi başlayalım.</span><span class="sxs-lookup"><span data-stu-id="f5813-133">Let's get started.</span></span>

[<span data-ttu-id="f5813-134">Next</span><span class="sxs-lookup"><span data-stu-id="f5813-134">Next</span></span>](delegate-class.md)
