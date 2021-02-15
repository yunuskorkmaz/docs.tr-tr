---
title: Mevcut ASP.NET uygulamalarını .NET Core 'a taşıma
description: ASP.NET MVC ve Web API uygulamalarını ASP.NET Core dönüştürmeye yönelik ücretsiz kılavuz.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 36c0cdbe03fb97ae82336d53e15be2108e9c6367
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488884"
---
# <a name="porting-existing-aspnet-apps-to-net-core"></a><span data-ttu-id="bd905-103">Mevcut ASP.NET uygulamalarını .NET Core 'a taşıma</span><span class="sxs-lookup"><span data-stu-id="bd905-103">Porting Existing ASP.NET Apps to .NET Core</span></span>

![kapak resmi](./media/index/porting-existing-aspnet-apps.png)

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="bd905-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="bd905-105">PUBLISHED BY</span></span>

<span data-ttu-id="bd905-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="bd905-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="bd905-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="bd905-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="bd905-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="bd905-108">One Microsoft Way</span></span>

<span data-ttu-id="bd905-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="bd905-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="bd905-110">Telif hakkı &copy; 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bd905-110">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="bd905-111">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="bd905-111">All rights reserved.</span></span> <span data-ttu-id="bd905-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde çoğaltılamaz.</span><span class="sxs-lookup"><span data-stu-id="bd905-112">No part of this book's contents may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="bd905-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="bd905-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="bd905-114">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bd905-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="bd905-115">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="bd905-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="bd905-116">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd905-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="bd905-117">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="bd905-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="bd905-118">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="bd905-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="bd905-119">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="bd905-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="bd905-120">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="bd905-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="bd905-121">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="bd905-121">Authors:</span></span>

> <span data-ttu-id="bd905-122">**Steve "ardalış" Smith**, yazılım mimarı ve Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="bd905-122">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="bd905-123">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="bd905-123">Participants and Reviewers:</span></span>

> <span data-ttu-id="bd905-124">**Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd905-124">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="bd905-125">**Mike Rousos**, sorumlu yazılım mühendisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd905-125">**Mike Rousos**, Principal Software Engineer, .NET team, Microsoft</span></span>

> <span data-ttu-id="bd905-126">**Scott Ade**, üst düzey içerik Geliştirici, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd905-126">**Scott Addie**, Senior Content Developer, .NET team, Microsoft</span></span>

> <span data-ttu-id="bd905-127">**David çam**, üst düzey içerik Geliştirici, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd905-127">**David Pine**, Senior Content Developer, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="bd905-128">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bd905-128">Version</span></span>

<span data-ttu-id="bd905-129">Bu kılavuzda .NET Core 3,1 sürümü ile aynı teknoloji "Wave" (yani Azure ve diğer üçüncü taraf teknolojileri) coinciding ile ilişkili **.net core 3,1** ve güncelleştirmeleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd905-129">This guide covers **.NET Core 3.1** and updates related to the same technology "wave" (that is, Azure and other third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="bd905-130">.NET Core 3,1 ' den .NET 5,0 ' e (sonraki sürüm) güncelleştirme oldukça basittir ve kesinlikle .NET Framework, .NET Core 'a kadar çok daha az çaba gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bd905-130">Updating from .NET Core 3.1 to .NET 5.0 (the next version) is relatively straightforward and certainly will require substantially less effort than porting from .NET Framework to .NET Core.</span></span> <span data-ttu-id="bd905-131">.NET Framework 4. x ' ten .NET 5,0 ' e geçiş, .NET Core 3,1 ' e geçirmeye benzer.</span><span class="sxs-lookup"><span data-stu-id="bd905-131">Migrating from .NET Framework 4.x to .NET 5.0 will be similar to migrating to .NET Core 3.1.</span></span> <span data-ttu-id="bd905-132">Daha fazla bilgi için bkz. [doğru .NET Core sürümünü seçme](choose-net-core-version.md).</span><span class="sxs-lookup"><span data-stu-id="bd905-132">For more information, see [choosing the right .NET Core version](choose-net-core-version.md).</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="bd905-133">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="bd905-133">Who should use this guide</span></span>

<span data-ttu-id="bd905-134">Bu kılavuzun hedef kitlesi, ASP.NET MVC ve Web API 'SI (.NET Framework 4. x) için yazılmış mevcut uygulamalarını .NET Core 'a geçirmeye ilgilenen geliştiriciler, geliştirme müşteri adayları ve mimarlardır.</span><span class="sxs-lookup"><span data-stu-id="bd905-134">This guide's audience is developers, development leads, and architects who are interested in migrating their existing apps written for ASP.NET MVC and Web API (.NET Framework 4.x) to .NET Core.</span></span> <span data-ttu-id="bd905-135">ASP.NET Web Forms geliştiriciler bu kılavuzdan faydalanır, ancak [ASP.NET Web Forms geliştiricileri](https://docs.microsoft.com/dotnet/architecture/blazor-for-web-forms-developers/) e-book için Blazor ' i de okumalı.</span><span class="sxs-lookup"><span data-stu-id="bd905-135">ASP.NET Web Forms developers will benefit from this guide but should also read the [Blazor for ASP.NET Web Forms Developers](https://docs.microsoft.com/dotnet/architecture/blazor-for-web-forms-developers/) e-book.</span></span>

<span data-ttu-id="bd905-136">İkincil bir hedef kitle, uygulamalarını .NET Core 'a ne zaman taşıyacağınız teknik karar verme mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="bd905-136">A secondary audience is technical decision-makers planning when to move their apps to .NET Core.</span></span>

<span data-ttu-id="bd905-137">Bu kitabın hedef kitlesi, ASP.NET MVC ve Web API 'sinde çalışan büyük, mevcut uygulamalarla .NET geliştiricidir.</span><span class="sxs-lookup"><span data-stu-id="bd905-137">The target audience for this book is .NET developers with large, existing apps that run on ASP.NET MVC and Web API.</span></span> <span data-ttu-id="bd905-138">ASP.NET Web Forms oluşturulan uygulamalar bu kitabın odaklanarak .NET Framework ve .NET Core 'un karşılaştırıldığı bilgilerin büyük bir bölümü hala ilgili olabilir.</span><span class="sxs-lookup"><span data-stu-id="bd905-138">Apps built on ASP.NET Web Forms are outside of the focus of this book, though much of the information comparing .NET Framework and .NET Core may still be relevant.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="bd905-139">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="bd905-139">How you can use this guide</span></span>

<span data-ttu-id="bd905-140">Birçok okuyucunun yapması beklendiğinden, bu kitabı doğrudan okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd905-140">You can read this book straight through, as we expect many readers to do.</span></span> <span data-ttu-id="bd905-141">Bu kitapta, uygulamanızı her seferinde bağlantı noktası yapmanız gerekip gerekmediğini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd905-141">This book will provide you first with considerations for whether you should port your app at all.</span></span> <span data-ttu-id="bd905-142">Bu içerik, .NET Framework ve .NET Core arasındaki mimari farklılığı izler.</span><span class="sxs-lookup"><span data-stu-id="bd905-142">That content is followed by architectural differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="bd905-143">Buradan, büyük bir çözümü zamana göre geçirme ve gerçek bir uygulamanın bağlantı noktası oluşturma stratejilerini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bd905-143">From there, you'll learn strategies for migrating a large solution over time and how to port a real app.</span></span> <span data-ttu-id="bd905-144">Daha sonra kitap, kullanıcılara tek bir uygulama olarak görünirken farklı uygulamalar çalıştırma gereksinimini karşılayan dağıtım senaryolarını içerir.</span><span class="sxs-lookup"><span data-stu-id="bd905-144">Next, the book includes deployment scenarios that address the need to run different apps while appearing as a single app to users.</span></span> <span data-ttu-id="bd905-145">Kitap, ASP.NET MVC 'den ASP.NET Core 'e geçirilmiş gerçek uygulamaları açıklayan iki örnek olay incelemesi ile sonlanır.</span><span class="sxs-lookup"><span data-stu-id="bd905-145">The book concludes with two case studies describing real apps that have migrated from ASP.NET MVC to ASP.NET Core.</span></span>

<span data-ttu-id="bd905-146">İlk bölümde başlatmayı tercih etmeksizin, belirli kavramlar hakkında bilgi edinmek için şu bölümlerden birine başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bd905-146">Whether or not you choose to start from the first chapter, you can reference any of these chapters to learn about specific concepts:</span></span>

- [<span data-ttu-id="bd905-147">Mimari farklılıklar</span><span class="sxs-lookup"><span data-stu-id="bd905-147">Architectural differences</span></span>](architectural-differences.md)
- [<span data-ttu-id="bd905-148">Büyük çözümleri geçirme</span><span class="sxs-lookup"><span data-stu-id="bd905-148">Migrate large solutions</span></span>](migrate-large-solutions.md)
- [<span data-ttu-id="bd905-149">Örnek geçiş</span><span class="sxs-lookup"><span data-stu-id="bd905-149">Sample migration</span></span>](example-migration-eshop.md)
- [<span data-ttu-id="bd905-150">Dağıtım senaryoları</span><span class="sxs-lookup"><span data-stu-id="bd905-150">Deployment scenarios</span></span>](deployment-scenarios.md)

<span data-ttu-id="bd905-151">Bu kılavuz hem [PDF form](https://aka.ms/aspnet-porting-ebook) hem de çevrimiçi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd905-151">This guide is available both in [PDF form](https://aka.ms/aspnet-porting-ebook) and online.</span></span> <span data-ttu-id="bd905-152">Bu kavramların yaygın olarak anlaşılmasından emin olmak için bu belgeyi veya çevrimiçi sürümüne olan bağlantıları ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="bd905-152">Feel free to forward this document or links to its online version to your team to ensure a common understanding of these concepts.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="bd905-153">Geri bildiriminizi gönderin</span><span class="sxs-lookup"><span data-stu-id="bd905-153">Send your feedback</span></span>

<span data-ttu-id="bd905-154">Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı!</span><span class="sxs-lookup"><span data-stu-id="bd905-154">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="bd905-155">Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd905-155">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="bd905-156">Sonraki</span><span class="sxs-lookup"><span data-stu-id="bd905-156">Next</span></span>](introduction.md)
