---
title: Temsilcilere giriş
description: Temel kavramları tanıtır ve temsilciler için dil tasarım hedefleri ele alınmaktadır genel bakış bölümüne temsilciler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 84e8bf8a03bd529d9c06ad049530c19daa380065
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646702"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="21a9b-103">Temsilcilere giriş</span><span class="sxs-lookup"><span data-stu-id="21a9b-103">Introduction to Delegates</span></span>

[<span data-ttu-id="21a9b-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="21a9b-104">Previous</span></span>](delegates-events.md)

<span data-ttu-id="21a9b-105">Temsilciler sağlayan bir *geç bağlama* .NET mekanizması.</span><span class="sxs-lookup"><span data-stu-id="21a9b-105">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="21a9b-106">Geç bağlama burada çağıran uygulayan algoritma parçası en az bir yöntemi de sağlayan bir algoritma oluşturmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="21a9b-106">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="21a9b-107">Örneğin, bir yıldız astronomi uygulamada listesini sıralama göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="21a9b-107">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="21a9b-108">Bu yıldız dünya ya da büyüklük yıldız ya da kendi algılanan parlaklık kendi uzaklık olarak sıralamak tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21a9b-108">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="21a9b-109">Bu durumlarda, Sort() yöntemi temelde aynı şeyi yapar: bazı karşılaştırma üzerine dayalı listesindeki öğeleri düzenler.</span><span class="sxs-lookup"><span data-stu-id="21a9b-109">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="21a9b-110">İki yıldız karşılaştıran kod her sıralama sıralamalarının için farklıdır.</span><span class="sxs-lookup"><span data-stu-id="21a9b-110">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="21a9b-111">Bu çözüm türlerini yazılımda bir yarım yüzyıl için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21a9b-111">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="21a9b-112">C# Birinci sınıf dil desteği ve tür güvenliği kavramı çevresinde dil temsilci kavramı sağlar.</span><span class="sxs-lookup"><span data-stu-id="21a9b-112">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="21a9b-113">Bu seride anlatıldığı gibi C# algoritmalar için bu tür kullanımı uyumlu ve dilinden yararlanır ve derleyicinin sağlamak türleri eşleştirmek için bağımsız değişkenler ve dönüş türleri gibi kodları.</span><span class="sxs-lookup"><span data-stu-id="21a9b-113">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="21a9b-114">Temsilciler için dil tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="21a9b-114">Language Design Goals for Delegates</span></span>

<span data-ttu-id="21a9b-115">Dil tasarımcıları sonunda temsilciler dönüştü özelliği için çeşitli hedefleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="21a9b-115">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="21a9b-116">Takım tüm geç bağlama algoritmaları için kullanılabilecek bir ortak dil yapısı istiyordu.</span><span class="sxs-lookup"><span data-stu-id="21a9b-116">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="21a9b-117">Bir kavram ve aynı bu kavramı arasında birçok farklı yazılım sorunlarını kullanmak geliştiricilerin sağlar.</span><span class="sxs-lookup"><span data-stu-id="21a9b-117">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="21a9b-118">İkinci olarak, hem tek ve çok noktaya yayın yöntem çağrıları desteklemek takım istiyordu.</span><span class="sxs-lookup"><span data-stu-id="21a9b-118">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="21a9b-119">(Birden çok yöntem çağrılarını birlikte zincire temsilciler çok noktaya yayın temsilcileri içindir.</span><span class="sxs-lookup"><span data-stu-id="21a9b-119">(Multicast delegates are delegates that chain together multiple method calls.</span></span> <span data-ttu-id="21a9b-120">Örnekler göreceksiniz [bu serideki sonraki](delegate-class.md).)</span><span class="sxs-lookup"><span data-stu-id="21a9b-120">You'll see examples [later in this series](delegate-class.md).)</span></span> 

<span data-ttu-id="21a9b-121">Takım istediği geliştiriciler tümünden beklediğiniz aynı tür güvenliği desteklemek için temsilciler C# oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21a9b-121">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="21a9b-122">Son olarak, takım temsilcileri ya da geç herhangi bir bağlama algoritma çok yararlı olduğu bir olay deseni belirli bir düzeni olduğunu tanınır.</span><span class="sxs-lookup"><span data-stu-id="21a9b-122">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="21a9b-123">Temsilciler için kod temeli için .NET olay deseni sağlayabilir takım sağlamaktı.</span><span class="sxs-lookup"><span data-stu-id="21a9b-123">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="21a9b-124">Tüm iş sonucu temsilci ve olay desteği olan C# ve .NET.</span><span class="sxs-lookup"><span data-stu-id="21a9b-124">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="21a9b-125">Bu bölümdeki diğer makaleleri dil özellikleri, kitaplık desteği ve temsilciler ile çalışırken, kullanılan ortak deyimleri ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="21a9b-125">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="21a9b-126">Hakkında bilgi edineceksiniz `delegate` anahtar sözcüğü ve hangi kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21a9b-126">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="21a9b-127">Özellikleri hakkında bilgi edineceksiniz `System.Delegate` sınıfı ve bu özelliklerden nasıl kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21a9b-127">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="21a9b-128">Tür güvenli temsilci oluşturmak nasıl ve temsilciler aracılığıyla çağrılan yöntemlerden oluşturulacağını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="21a9b-128">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="21a9b-129">Lambda ifadeleri kullanarak, temsilciler ve olaylar ile çalışma konusunda da öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="21a9b-129">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="21a9b-130">Burada temsilciler biri yapı taşlarını LINQ için haline görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="21a9b-130">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="21a9b-131">Temsilciler .NET olay deseni için temel şeklini ve nasıl farklı olduğunu öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="21a9b-131">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="21a9b-132">Genel olarak, temsilciler .NET programlama ve framework API'ları ile çalışma bütünleyici şeklini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="21a9b-132">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="21a9b-133">Haydi başlayalım.</span><span class="sxs-lookup"><span data-stu-id="21a9b-133">Let's get started.</span></span>

[<span data-ttu-id="21a9b-134">Next</span><span class="sxs-lookup"><span data-stu-id="21a9b-134">Next</span></span>](delegate-class.md)
